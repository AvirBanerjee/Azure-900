# AZ-900: Microsoft Azure Fundamentals
## Unit 3 — Networking, Storage, Databases, and Identity Fundamentals

**Course Outcome Covered:** CO3 — Identify Azure compute, storage, networking and identity services.

**Note on scope:** The syllabus lists Virtual Networks and Subnets, VPN Gateway, ExpressRoute, Load Balancer, DNS, Azure Storage Types, Storage Redundancy, Azure SQL Database, Cosmos DB Overview, Microsoft Entra ID, Authentication Methods, and Role-Based Access Control. The actual AZ-900 exam objectives this unit maps to — **"Describe Azure compute and networking services"** (networking half), **"Describe Azure storage services,"** and **"Describe Azure identity, access, and security"** (identity half) — additionally and explicitly test: **VNet Peering, Network Security Groups, Application Gateway, Azure Firewall, Blob Access Tiers, the full Storage Redundancy comparison (LRS/ZRS/GRS/GZRS/RA-GRS), Storage Migration Tools (AzCopy, Storage Explorer, Azure Migrate, Data Box), Single Sign-On, Hybrid Identity (Microsoft Entra Connect), and External Identities (B2B/B2C).** All of these are included below and marked **(AZ-900 Add-on)** wherever they extend beyond the syllabus wording.

---

# PART A — NETWORKING

## 1. Virtual Networks (VNets) and Subnets

An **Azure Virtual Network (VNet)** is the fundamental building block for private networking in Azure. It is a logically isolated network within Azure where resources (VMs, App Services with VNet integration, databases) can communicate securely with each other, with the internet, and with on-premises networks.

**Key characteristics:**
- A VNet is scoped to a single region and a single subscription (though it can be connected to VNets in other regions via peering — Section 1.2).
- Resources inside the same VNet can communicate with each other by default, using private IP addresses, without traffic ever leaving the Microsoft network.
- A VNet's address space is defined using CIDR notation (e.g., 10.0.0.0/16).

### 1.1 Subnets
A **subnet** is a smaller, segmented range of IP addresses within a VNet's address space. Subnets are used to logically organize and isolate groups of resources within the same VNet.

**Example:**
A company creates a VNet with address space 10.0.0.0/16 for its three-tier web application. It divides this into three subnets: 10.0.1.0/24 for web servers, 10.0.2.0/24 for application servers, and 10.0.3.0/24 for database servers. This segmentation allows the company to apply different security rules to each tier — for instance, only the web subnet needs to accept traffic directly from the internet.

### 1.2 VNet Peering (AZ-900 Add-on)

**VNet Peering** connects two Virtual Networks together, allowing resources in each VNet to communicate with each other using private IP addresses, as if they were part of the same network — without traffic passing over the public internet.

**Key facts:**
- Peered VNets can be in the same region or different regions (global peering).
- Traffic between peered VNets travels over the Microsoft backbone network, not the public internet, giving low latency and high security.
- Peering is non-transitive — if VNet A is peered with VNet B, and VNet B is peered with VNet C, VNet A cannot automatically communicate with VNet C unless a direct peering is also configured between A and C.

**Example:**
A company has a VNet in East US hosting its production application and a separate VNet in West Europe hosting a regional reporting service. It configures global VNet peering between the two, allowing the reporting service to securely query the production database using a private IP address, without exposing either network to the public internet.

---

## 2. VPN Gateway

An **Azure VPN Gateway** is a specific type of virtual network gateway used to send encrypted traffic between an Azure VNet and an on-premises location (or between two Azure VNets) over the public internet.

**Key characteristics:**
- Establishes a secure, encrypted tunnel (using IPsec/IKE protocols) across the public internet.
- Commonly used for hybrid cloud scenarios, connecting an organization's on-premises network to its Azure resources.
- Lower cost than ExpressRoute (Section 3), but relies on the public internet, so it does not offer the same guaranteed bandwidth or latency.

**Example:**
A mid-sized company wants to connect its office network to its Azure VNet so employees can access cloud-hosted file servers as though they were on the local office network. It deploys a VPN Gateway to create a Site-to-Site VPN connection between its office router and Azure, encrypting all traffic that passes between the two over the internet.

---

## 3. ExpressRoute

**Azure ExpressRoute** is a service that creates a **private, dedicated connection** between an on-premises network and Azure, using a connectivity provider rather than the public internet.

**Key characteristics:**
- Does not traverse the public internet at all — traffic travels over a private, dedicated circuit.
- Offers higher reliability, lower and more consistent latency, and higher bandwidth than a VPN Gateway connection.
- Significantly more expensive than a VPN Gateway, and typically used by larger enterprises with mission-critical connectivity needs.

**Comparison: VPN Gateway vs ExpressRoute (a frequently tested exam point):**

| Feature | VPN Gateway | ExpressRoute |
|---|---|---|
| Connection path | Encrypted tunnel over public internet | Private, dedicated circuit (no internet) |
| Latency/reliability | Variable (depends on internet conditions) | Consistent and predictable |
| Cost | Lower | Higher |
| Setup complexity | Simple, self-service | Requires a connectivity provider |
| Best suited for | Small/medium businesses, lower-sensitivity workloads | Large enterprises, mission-critical or compliance-sensitive workloads |

**Example:**
A large bank requires guaranteed low latency and high reliability for its real-time transaction processing system connecting its on-premises datacenter to Azure, and cannot risk exposure to the public internet. It uses ExpressRoute. In contrast, a small business connecting its single branch office to Azure for occasional file access uses a VPN Gateway, since it does not need the same guaranteed performance and wants to minimize cost.

---

## 4. Load Balancer

**Azure Load Balancer** distributes incoming network traffic across multiple backend resources (such as VM instances), ensuring no single instance is overwhelmed and improving both availability and performance.

**Key characteristics:**
- Operates at Layer 4 (the transport layer — TCP/UDP) of the OSI model, meaning it distributes traffic based on IP address and port, without inspecting the actual content of the traffic (e.g., it does not read URLs).
- Continuously performs health probes on backend instances, automatically routing traffic away from any instance that fails a health check.
- Directly implements fault tolerance (Unit 1) for groups of VMs or VM Scale Set instances.

**Example:**
An e-commerce application runs on three VM instances behind an Azure Load Balancer. If one instance becomes unresponsive, the Load Balancer's health probe detects this and automatically stops sending traffic to it, redirecting all requests to the two remaining healthy instances — directly implementing the fault tolerance concept from Unit 1 at the networking level.

### 4.1 Application Gateway (AZ-900 Add-on)

**Azure Application Gateway** is also a load balancer, but it operates at **Layer 7** (the application layer) of the OSI model, meaning it can make routing decisions based on the actual content of a web request — such as the URL path or the hostname.

**Key distinction from Azure Load Balancer (common exam confusion point):**

| Feature | Azure Load Balancer | Application Gateway |
|---|---|---|
| OSI Layer | Layer 4 (Transport) | Layer 7 (Application) |
| Routing decisions based on | IP address and port | URL path, hostname, HTTP headers |
| Can inspect web traffic content | No | Yes |
| Additional capability | — | Web Application Firewall (WAF) to protect against common web exploits |

**Example:**
An online retailer wants requests to "/images/*" routed to one set of servers and requests to "/checkout/*" routed to a different, more tightly secured set of servers, based on the URL path itself. A standard Load Balancer cannot make this decision since it only looks at IP and port — Application Gateway is required because it can inspect the actual HTTP request content.

---

## 5. Network Security Groups (NSGs) (AZ-900 Add-on)

A **Network Security Group (NSG)** is a basic firewall-like feature used to filter network traffic to and from Azure resources within a VNet, based on a set of inbound and outbound security rules.

**Key characteristics:**
- Rules specify: source/destination IP range, port, protocol, and whether to allow or deny the traffic.
- NSGs can be associated with a subnet (applying to everything inside it) or with an individual network interface (applying to one specific resource).
- Rules are evaluated by priority number — lower numbers are evaluated first, and once a rule matches, evaluation stops.
- By default, Azure includes some baseline rules (e.g., allowing traffic within the VNet, allowing outbound internet access, denying all other inbound traffic by default).

**Example:**
A company's web server subnet needs to accept HTTP/HTTPS traffic (ports 80/443) from the internet, but its database subnet should never be directly reachable from the internet at all. The administrator applies an NSG to the web subnet allowing inbound traffic on ports 80 and 443 from any source, and a separate, more restrictive NSG to the database subnet that only allows inbound traffic on the database port from the web subnet's IP range specifically — denying all other inbound traffic by default.

---

## 6. Azure DNS

**Azure DNS** is a hosting service for DNS (Domain Name System) domains, allowing Azure to translate human-readable domain names (such as www.example.com) into IP addresses, and to manage an organization's DNS records using the same credentials, APIs, and billing as its other Azure resources.

**Key characteristics:**
- Supports hosting a custom domain's DNS records directly within Azure.
- Benefits from Azure's global network of DNS name servers for fast DNS resolution worldwide.
- Commonly used alongside other Azure services (e.g., pointing a custom domain to an App Service or a Load Balancer's public IP).

**Example:**
A company owns the domain "example.com" and wants it to point to its Azure-hosted web application. It uses Azure DNS to host the domain's DNS zone and creates an "A" record mapping "www.example.com" to the public IP address of its Azure Load Balancer, allowing users typing the familiar domain name to reach the application.

### 6.1 Azure Firewall (AZ-900 Add-on)

**Azure Firewall** is a managed, cloud-based network security service that protects an entire VNet by filtering traffic based on centrally defined rules, operating at a broader scope than an NSG.

**Brief distinction from NSGs:** An NSG is a simpler, resource- or subnet-level traffic filter; Azure Firewall is a fully managed, stateful firewall-as-a-service applied centrally across an entire virtual network, offering more advanced capabilities such as threat intelligence-based filtering and centralized logging across multiple VNets and subscriptions.

**Example:**
A large organization with many VNets across multiple subscriptions deploys a single Azure Firewall to centrally enforce outbound traffic rules (e.g., "no VM may access any domain outside an approved list") across its entire Azure environment, rather than configuring NSGs individually on every subnet.

---

# PART B — STORAGE

## 7. Azure Storage Types

An **Azure Storage Account** is the top-level container for all Azure Storage services. Within a storage account, Azure offers several distinct storage types, each designed for a different kind of data.

| Storage Type | What It Stores | Typical Use Case |
|---|---|---|
| **Blob Storage** | Unstructured data (files, images, videos, backups) | Serving website content, storing documents, backup archives |
| **Disk Storage** | Persistent disks attached to Azure Virtual Machines | OS disks and data disks for VMs |
| **File Storage (Azure Files)** | Fully managed file shares accessible via the standard SMB/NFS protocol | Replacing an on-premises file server, shared application config files |
| **Queue Storage** | Messages for communication between application components | Decoupling application components (e.g., a web app queuing a task for a background worker) |
| **Table Storage** | NoSQL key-value structured data | Simple structured data not requiring a full relational database |

**Example:**
A photo-sharing application stores uploaded user images in **Blob Storage**, stores the operating system disk for its backend processing VM in **Disk Storage**, and uses **Queue Storage** to pass a message from the web front-end to a background worker whenever a new image needs to be resized and compressed.

### 7.1 Blob Access Tiers (AZ-900 Add-on)

Within Blob Storage specifically, Azure offers **access tiers** that balance storage cost against access/retrieval cost, since the syllabus's "Azure Storage Types" line does not explicitly call these out but they are a core, frequently tested AZ-900 topic.

| Access Tier | Storage Cost | Access Cost | Best Suited For |
|---|---|---|---|
| **Hot** | Higher | Lower | Data accessed frequently (active website content) |
| **Cool** | Lower | Higher | Data accessed infrequently, kept for at least 30 days (short-term backups) |
| **Archive** | Lowest | Highest (and slow — can take hours to retrieve) | Data rarely accessed, kept for at least 180 days (long-term compliance archives) |

**Example:**
A company stores its current year's customer invoices in the **Hot** tier since staff access them regularly. Invoices from 2–3 years ago are moved to the **Cool** tier, since they are rarely needed but must remain quickly retrievable if requested. Invoices older than 7 years, kept only for legal compliance and almost never accessed, are moved to the **Archive** tier, accepting a multi-hour retrieval delay in exchange for the lowest possible storage cost. This tiering strategy is often automated using a **lifecycle management policy**, which moves blobs between tiers automatically based on age or last-access time.

---

## 8. Storage Redundancy

**Storage redundancy** determines how many copies of data are kept, and where, to protect against hardware failure, datacenter failure, or regional disaster. The syllabus's "Storage Redundancy" line is expanded here into the full set of options Azure actually offers, since AZ-900 tests the complete comparison, not just the general concept.

| Redundancy Option | Copies | Where Copies Are Stored | Protects Against |
|---|---|---|---|
| **LRS** (Locally Redundant Storage) | 3 copies | Within a single datacenter | Hardware failure (disk/rack) |
| **ZRS** (Zone-Redundant Storage) | 3 copies | Across multiple Availability Zones in one region | Datacenter-level failure |
| **GRS** (Geo-Redundant Storage) | 6 copies (3 local + 3 in paired region) | Primary region (LRS) + asynchronously replicated to the paired region | Entire region failure |
| **GZRS** (Geo-Zone-Redundant Storage) | 6 copies | Primary region (ZRS) + asynchronously replicated to the paired region | Zone failure AND region failure together |
| **RA-GRS / RA-GZRS** (Read-Access variants) | Same as GRS/GZRS | Same as GRS/GZRS, but the secondary region's copy is readable | Same as above, plus allows reading data even if the primary region is unavailable |

**Key exam distinctions:**
- LRS is the cheapest but offers the least protection — it does not protect against an entire datacenter going down.
- ZRS protects against datacenter failure but keeps all copies within one region (relevant if a region has zone support).
- GRS/GZRS protect against an entire region going down, by replicating to the paired region (directly connects to Region Pairs, Unit 2).
- The "RA-" prefix (Read-Access) specifically means the secondary copy can be read directly by the application, not just held in reserve for a failover.

**Example:**
A startup storing non-critical temporary cache data chooses **LRS**, since the data's loss would be inconvenient but not catastrophic, and LRS is the cheapest option. A hospital storing patient records chooses **RA-GZRS**, since it needs protection against both a single datacenter failure (zone redundancy) and an entire region failure (geo-redundancy), while also wanting the ability to read data from the secondary region if the primary region becomes temporarily unavailable.

---

## 9. Storage Migration and Management Tools (AZ-900 Add-on)

AZ-900 explicitly tests awareness of the tools used to move data into and manage data within Azure Storage, which the syllabus does not name individually.

| Tool | Purpose |
|---|---|
| **AzCopy** | A command-line tool for high-performance copying of data to, from, or between Azure Storage accounts |
| **Azure Storage Explorer** | A standalone graphical application (and a feature within the Azure Portal) for browsing and managing Blob, File, Queue, and Table storage |
| **Azure Migrate** | A centralized hub of tools to assess and migrate on-premises servers, databases, and applications to Azure |
| **Azure Data Box** | A physical, secure device shipped to an organization to transfer very large volumes of data to Azure offline, used when the data is too large to move efficiently over a network connection |

**Example:**
A company with 200 TB of archival data decides that uploading it over its internet connection would take weeks. It orders an **Azure Data Box**, copies the data onto the physical device locally, and ships it back to Microsoft, who uploads the data directly into the company's storage account — avoiding the network bottleneck entirely. For its ongoing day-to-day smaller transfers, the company's developers use **AzCopy** scripts, while its IT administrators use **Azure Storage Explorer** to browse and manage files manually when needed.

---

## 10. Azure SQL Database

**Azure SQL Database** is a fully managed **Platform as a Service (PaaS)** relational database, built on Microsoft SQL Server technology, used for structured, relational data with defined schemas and relationships.

**Key characteristics:**
- Microsoft manages patching, backups, high availability, and infrastructure — consistent with the PaaS responsibility split from Unit 1.
- Supports standard SQL querying, transactions, and relational table structures (rows, columns, foreign keys).
- Offers built-in features such as automatic backups, point-in-time restore, and automatic scaling of compute resources.

**Example:**
An online banking application needs to store customer account details, transaction histories, and maintain strict relationships between accounts, transactions, and account holders, with strong consistency guarantees. It uses Azure SQL Database, since the data is highly structured and relational, and the application benefits from Azure automatically handling backups and patching.

---

## 11. Cosmos DB Overview

**Azure Cosmos DB** is a fully managed, globally distributed **NoSQL** database service, designed for applications that need extremely low latency, high throughput, and flexible (non-relational) data structures, often at a global scale.

**Key characteristics:**
- Supports multiple NoSQL data models (document, key-value, graph, column-family) through different APIs.
- Offers **global distribution** — data can be automatically replicated across any number of Azure regions, with very low read/write latency guaranteed worldwide.
- Designed for horizontal scalability — Cosmos DB can handle massive, elastic workloads by adding more distributed capacity rather than scaling up a single server.

**Comparison: Azure SQL Database vs Cosmos DB (a frequent exam scenario question):**

| Feature | Azure SQL Database | Cosmos DB |
|---|---|---|
| Data model | Relational (tables, rows, schema) | NoSQL (document, key-value, graph, etc.) |
| Best suited for | Structured data with clear relationships | Flexible/semi-structured data, global-scale apps |
| Global distribution | Limited (region-based) | Native, multi-region, low-latency by design |
| Schema | Fixed schema required | Schema-flexible |

**Example:**
A global gaming company building a leaderboard and player-profile system that must respond in milliseconds to players across North America, Europe, and Asia simultaneously chooses **Cosmos DB**, since it needs globally distributed, low-latency reads and writes, and player profile data does not require strict relational structure. A separate internal HR system managing structured employee records with strict relationships between departments, salaries, and managers uses **Azure SQL Database** instead.

### 11.1 Other Azure Database Services (AZ-900 Add-on)

Beyond the two databases named in the syllabus, AZ-900 also expects awareness that Azure offers fully managed versions of other popular open-source relational databases: **Azure Database for MySQL** and **Azure Database for PostgreSQL**. These follow the same PaaS philosophy as Azure SQL Database — Microsoft manages patching, backups, and infrastructure — but are used specifically for applications already built around the MySQL or PostgreSQL engines rather than SQL Server.

---

# PART C — IDENTITY

## 12. Microsoft Entra ID

**Microsoft Entra ID** (formerly Azure Active Directory / Azure AD) is Microsoft's cloud-based **identity and access management** service. It is used to authenticate (verify identity) and authorize (determine permissions for) users accessing Azure resources, Microsoft 365, and other connected applications.

**Key characteristics:**
- Manages user accounts, groups, and the credentials used to sign in.
- Distinct from Azure resources themselves — Microsoft Entra ID is a tenant-level identity service that sits logically above the resource hierarchy from Unit 2, providing the identities that RBAC (Section 14) then grants permissions to.
- Supports integration with thousands of third-party Software as a Service (SaaS) applications for centralized sign-in.

**Example:**
A company uses Microsoft Entra ID to manage all employee accounts. When an employee joins, an account is created once in Microsoft Entra ID, and that single identity is then used to sign into Microsoft 365, the company's Azure resources, and several third-party SaaS tools the company has integrated — rather than the employee needing separate usernames and passwords for each system.

### 12.1 Single Sign-On (SSO) (AZ-900 Add-on)

**Single Sign-On (SSO)** allows a user to sign in once with a single identity and gain access to multiple applications and resources without needing to re-authenticate for each one separately.

**Example:**
An employee signs into their laptop in the morning using their Microsoft Entra ID credentials. Throughout the day, they open Outlook, Teams, and a company-approved third-party project management tool, and are not prompted to log in again for any of them, because all three applications trust the same Microsoft Entra ID sign-in session.

### 12.2 Hybrid Identity — Microsoft Entra Connect (AZ-900 Add-on)

Many organizations have an existing **on-premises Active Directory** (a traditional, server-based directory service) and want to extend those same identities into the cloud rather than creating entirely separate cloud-only accounts. **Microsoft Entra Connect** is the tool used to synchronize on-premises Active Directory identities with Microsoft Entra ID, creating a **hybrid identity** setup.

**Example:**
A company with 500 employees already has an on-premises Active Directory managing logins for its internal office network. Rather than recreating 500 accounts manually in the cloud, it deploys Microsoft Entra Connect, which synchronizes each existing on-premises account into Microsoft Entra ID automatically, so employees can use the same username and password for both their office computer login and their cloud application access.

### 12.3 External Identities (AZ-900 Add-on)

Microsoft Entra **External Identities** allow an organization to securely grant access to people outside its own organization:
- **Business to Business (B2B):** Allows external partners, vendors, or contractors to sign in to an organization's resources using their own existing credentials from their own company, rather than needing a separate account created for them.
- **Business to Consumer (B2C):** Allows a public-facing application to let customers sign in using their own preferred identity (a social media account, an email address) rather than an organizational account.

**Example:**
A company collaborating with an external auditing firm uses **B2B** to grant the auditors access to specific financial reports in Azure using the auditors' own company email credentials, without creating new internal accounts for them. Separately, that same company's public customer-facing mobile app uses **B2C** to let ordinary customers sign up and log in using their personal email address or a social media account.

---

## 13. Authentication Methods

**Authentication** is the process of proving a user's identity is genuine before granting access. Microsoft Entra ID supports several authentication methods, with a strong emphasis — heavily tested on AZ-900 — on moving beyond passwords alone.

### 13.1 Password-Based Authentication
The traditional method — a username combined with a secret password. Considered the weakest method on its own, since passwords can be guessed, phished, or reused across services.

### 13.2 Multifactor Authentication (MFA)
Requires a user to verify their identity using **two or more** independent factors, typically combining something the user knows (a password) with something the user has (a phone, a hardware token) or something the user is (a fingerprint).

**Example:**
An employee logs in with their correct username and password, but is then prompted to approve a notification sent to the Microsoft Authenticator app on their registered phone before access is granted. Even if an attacker had stolen the employee's password, they would not be able to complete the second factor without also having physical access to the employee's phone.

### 13.3 Passwordless Authentication (AZ-900 Add-on)

Passwordless authentication removes the password from the sign-in process entirely, relying instead on something the user has and something the user is (or knows), which is both more secure and more convenient than password-plus-MFA.

| Method | How It Works |
|---|---|
| **Windows Hello for Business** | Uses biometrics (fingerprint, facial recognition) or a PIN tied to a specific device |
| **Microsoft Authenticator app (passwordless sign-in)** | User approves a sign-in prompt on their registered phone instead of typing a password |
| **FIDO2 security keys** | A physical USB or NFC hardware key that the user plugs in or taps to authenticate |

**Example:**
An organization rolling out passwordless authentication issues FIDO2 security keys to its IT administrators handling the most sensitive systems. Instead of typing a password, an administrator inserts their physical security key and verifies with a fingerprint, removing the password entirely as a point of attack.

---

## 14. Role-Based Access Control (RBAC)

**Role-Based Access Control (RBAC)** is the system Azure uses to manage **what an authenticated identity is allowed to do** (authorization), by assigning roles to users, groups, or applications at a specific scope within the resource hierarchy (Unit 2, Section 7).

**Key components of an RBAC assignment:**
- **Security Principal:** Who is being granted access (a user, a group, or an application identity).
- **Role Definition:** What permissions are being granted (e.g., "Reader" can only view resources, "Contributor" can create and modify resources but not grant access to others, "Owner" can do everything including granting access to others).
- **Scope:** Where the permission applies — a management group, a subscription, a resource group, or an individual resource, directly reflecting the resource hierarchy from Unit 2.

**Key facts:**
- RBAC follows the principle of **least privilege** — users should be granted only the minimum permissions needed to do their job.
- Permissions assigned at a higher scope (e.g., a resource group) are automatically inherited by everything beneath it (consistent with the inheritance rule from Unit 2, Section 7).
- RBAC answers "what can this identity do," while Microsoft Entra ID (Section 12) answers "who is this identity" — the two work together but serve different purposes.

**Example:**
A company assigns a junior developer the **Reader** role at the "Dev-RG" resource group scope, allowing them to view resources but not change anything. A senior developer is assigned the **Contributor** role at the same scope, allowing them to create and modify resources within that resource group, but not to grant other people access to it. Only the IT administrator is assigned the **Owner** role at the subscription level, allowing them full control, including the ability to assign roles to others — and because of inheritance, the Owner role at the subscription level automatically applies to "Dev-RG" and every resource inside it as well.

---

## Unit 3 Summary (Quick Revision)

**Networking:**
- **VNets/Subnets** provide private, isolated networking; **VNet Peering** connects separate VNets privately without using the public internet.
- **VPN Gateway** = encrypted tunnel over the public internet; **ExpressRoute** = private dedicated circuit, no internet, higher cost and reliability.
- **Load Balancer** (Layer 4, IP/port-based) vs **Application Gateway** (Layer 7, URL/content-based, includes WAF).
- **NSGs** filter traffic at the subnet/NIC level; **Azure Firewall** provides centralized, managed filtering across entire VNets.
- **Azure DNS** hosts and resolves domain names for Azure-hosted resources.

**Storage:**
- **Storage Types:** Blob (unstructured), Disk (VM disks), File (SMB/NFS shares), Queue (messaging), Table (NoSQL key-value).
- **Blob Access Tiers:** Hot (frequent access) → Cool (infrequent, 30+ days) → Archive (rare, 180+ days, slow retrieval).
- **Redundancy:** LRS (single datacenter) → ZRS (zones in one region) → GRS (geo-replicated to paired region) → GZRS (zones + geo) → RA- variants (secondary copy is readable).
- **Migration/Management Tools:** AzCopy (CLI copying), Storage Explorer (GUI browsing), Azure Migrate (assessment/migration hub), Data Box (offline bulk transfer).
- **Azure SQL Database** (relational, PaaS) vs **Cosmos DB** (NoSQL, globally distributed, low-latency); MySQL/PostgreSQL also available as managed services.

**Identity:**
- **Microsoft Entra ID** manages identity and access centrally; supports **SSO** (one login, many apps).
- **Microsoft Entra Connect** synchronizes on-premises Active Directory with the cloud for **hybrid identity**.
- **External Identities**: B2B (partners use their own credentials), B2C (customers use social/email identities).
- **Authentication methods** range from passwords → MFA (two or more factors) → passwordless (Windows Hello, Authenticator app, FIDO2 keys).
- **RBAC** controls authorization (what an identity can do) via Security Principal + Role Definition + Scope, inheriting down the resource hierarchy from Unit 2.

---

## Practice Questions (Self-Check)

1. Explain the difference between a VPN Gateway and ExpressRoute. Which would a mission-critical enterprise workload typically use, and why?
2. What is the key difference between Azure Load Balancer and Application Gateway, in terms of which OSI layer they operate at and what routing decisions they can make?
3. A web subnet needs to accept internet traffic on ports 80/443, while a database subnet must never be directly reachable from the internet. Which Azure feature enforces this, and how?
4. List the five Azure Storage types and give one example use case for each.
5. Explain the difference between the Hot, Cool, and Archive blob access tiers, including an example scenario for each.
6. Compare LRS, ZRS, and GRS in terms of what each protects against. Which would best suit a hospital's patient records, and why?
7. When would an organization choose Azure SQL Database over Cosmos DB, and vice versa?
8. What is the difference between Microsoft Entra ID and Role-Based Access Control — i.e., what question does each one answer?
9. Explain passwordless authentication and name two methods Microsoft Entra ID supports for it.
10. A company wants external auditors to access specific reports using their own company credentials, without creating new internal accounts. Which Microsoft Entra feature supports this?

*(Answers to be discussed in class / covered in practical session mapped to Experiment 4, Experiment 5, and Experiment 7.)*