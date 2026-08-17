# AZ-900: Microsoft Azure Fundamentals
## Unit 1 — Cloud Computing Fundamentals

**Course Outcome Covered:** CO1 — Explain cloud computing concepts and service models.

---

## 1. What is Cloud Computing

Cloud computing is the delivery of computing services — servers, storage, databases, networking, software, analytics — over the internet ("the cloud"). Instead of owning physical hardware, an organization rents computing resources from a cloud provider (such as Microsoft Azure, AWS, or Google Cloud) and pays only for what it uses.

**Traditional (On-Premises) Model:**
- Organization buys physical servers, storage, and networking equipment.
- Requires a dedicated data center, power, cooling, and IT staff to maintain hardware.
- Capital Expenditure (CapEx): large upfront investment before any use.

**Cloud Model:**
- Organization rents compute, storage, and networking from a provider.
- Provider owns and maintains the physical hardware.
- Operational Expenditure (OpEx): pay-as-you-go, no large upfront investment.

**Exam Tip:** AZ-900 frequently tests the difference between CapEx and OpEx. Remember: Cloud computing shifts spending from CapEx to OpEx.

---

## 2. Benefits of Cloud Services

| Benefit | Explanation | Example |
|---|---|---|
| High Availability | Systems remain accessible with minimal downtime | An e-commerce site stays online during a regional outage because Azure routes traffic to another datacenter |
| Scalability | Ability to increase or decrease resources to meet demand | Adding more VM instances during a flash sale |
| Elasticity | Automatic scaling up or down based on real-time load | Auto-scaling a web app during traffic spikes and scaling back down at night |
| Agility | Faster deployment of resources | Spinning up a new VM in minutes instead of weeks of procurement |
| Fault Tolerance | System continues to operate even if a component fails | Data replicated across multiple storage nodes |
| Disaster Recovery | Ability to restore operations after a major failure | Failing over to a secondary Azure region after a datacenter fire |
| Global Reach | Deploy applications close to users worldwide | Hosting a web app in both the US and India regions to reduce latency |

**Distinguishing Scalability vs Elasticity (common exam confusion point):**
- **Scalability** = the *capability* of a system to handle increased load (can be manual or automatic).
- **Elasticity** = the *automatic* process of scaling resources up or down dynamically based on demand.

---

## 3. Economies of Scale

Cloud providers operate massive datacenters serving millions of customers. Because costs (hardware, power, cooling, staff) are spread across many customers, the per-unit cost of computing is lower than what a single organization would pay to run its own datacenter. This is called **economies of scale**, and it is the underlying economic reason cloud services are generally cheaper than on-premises infrastructure at scale.

---

## 4. Consumption-Based Pricing Model

Azure primarily uses a **consumption-based (pay-as-you-go)** pricing model.

**Key characteristics:**
- Pay only for the resources consumed (compute hours, storage used, data transferred).
- No upfront hardware cost.
- Ability to stop paying when a resource is deleted or deallocated.

**Example:**
A company deploys a virtual machine for a 3-day marketing campaign. Instead of purchasing a physical server, it pays only for the 3 days of VM usage, then deletes the VM. Cost is tied directly to usage duration.

**Contrast with Traditional IT:**
| Traditional IT | Cloud (Consumption-Based) |
|---|---|
| Pay upfront for hardware regardless of use | Pay only for what is used |
| Difficult to predict future capacity needs | Scale resources as needed |
| Idle hardware still costs money | Idle/unused resources can be deallocated to stop billing |

---

## 5. Shared Responsibility Model

Security and management responsibilities are **divided between the cloud provider and the customer**. The exact split depends on the service model used (IaaS, PaaS, or SaaS).

**General Rule:**
- The **cloud provider** is always responsible for the physical infrastructure: datacenters, physical security, physical network, and physical hosts.
- The **customer** is always responsible for their **data**, **accounts**, and **identities**, regardless of service model.
- Responsibility for everything in between (operating system, applications, network controls) shifts depending on which service model is used.

**Example:**
- In **IaaS**, the customer manages the operating system, applications, and data; Azure manages the physical infrastructure.
- In **SaaS**, Azure manages almost everything except the customer's data and user access.

---

## 6. Cloud Deployment Models

### 6.1 Public Cloud
- Resources are owned and operated by a third-party cloud provider (e.g., Microsoft Azure) and delivered over the internet.
- Shared infrastructure among multiple customers (multi-tenant), though data is logically isolated.
- No capital expenditure for hardware; provider handles maintenance.

**Example:** A startup hosts its website using Azure App Service, sharing underlying physical hardware with other Azure customers, but its data is fully isolated.

### 6.2 Private Cloud
- Cloud infrastructure dedicated entirely to a single organization.
- Can be hosted on-premises or by a third party, but resources are not shared with other organizations.
- Offers greater control over security and compliance.

**Example:** A government defense agency runs its own private cloud within its own datacenter to meet strict data sovereignty requirements.

### 6.3 Hybrid Cloud
- Combination of public and private cloud, allowing data and applications to move between the two.
- Useful for organizations with regulatory requirements or legacy systems that cannot fully move to the cloud.

**Example:** A bank keeps sensitive customer records in a private cloud on-premises but runs its customer-facing mobile app on Azure public cloud, connecting both through a secure network link.

**Comparison Table:**

| Model | Ownership | Control | Cost | Use Case |
|---|---|---|---|---|
| Public | Cloud provider | Lower control, provider-managed | Lower upfront cost | General business apps, websites |
| Private | Organization (or dedicated third party) | Full control | Higher cost | Regulated industries, sensitive data |
| Hybrid | Mixed | Balanced | Balanced | Gradual cloud migration, compliance needs |

---

## 7. Cloud Service Models: IaaS, PaaS, SaaS

Cloud services are delivered in three primary models, each offering a different balance between what the provider manages and what the customer manages.

### 7.1 Infrastructure as a Service (IaaS)
- Provider supplies the basic building blocks: virtual machines, storage, networking.
- Customer manages operating systems, runtime, applications, and data.
- Offers the most control and flexibility, but also the most management responsibility.

**Example:** A company deploys Windows Server virtual machines on Azure to host a legacy application it previously ran in its own datacenter, migrating it "as-is" without rewriting the application.

### 7.2 Platform as a Service (PaaS)
- Provider manages the underlying infrastructure and operating system.
- Customer focuses only on developing, deploying, and managing applications and data.

**Example:** A development team uses Azure App Service to deploy a web application. They upload their code, and Azure automatically handles the OS patching, server maintenance, and scaling infrastructure.

### 7.3 Software as a Service (SaaS)
- Provider manages nearly everything, including the application itself.
- Customer only manages their data and user access.

**Example:** An organization uses Microsoft 365 (Outlook, Word, Teams) for its employees. Microsoft manages the application, servers, and infrastructure entirely; the organization only manages user accounts and its own data.

**Responsibility Comparison Table:**

| Layer | IaaS | PaaS | SaaS |
|---|---|---|---|
| Data | Customer | Customer | Customer |
| Applications | Customer | Customer | Provider |
| Runtime | Customer | Provider | Provider |
| Operating System | Customer | Provider | Provider |
| Virtualization | Provider | Provider | Provider |
| Servers/Storage/Networking | Provider | Provider | Provider |
| Physical Datacenter | Provider | Provider | Provider |

**Exam Tip:** A common AZ-900 question style gives a scenario ("a company wants to rent a virtual machine and manage its own OS updates") and asks which service model it describes. Match the scenario to how much control vs. management burden the customer has.

---

## 8. High Availability, Scalability, Elasticity, Reliability

These terms are related but distinct, and AZ-900 often tests the difference between them.

- **High Availability (HA):** Design goal to keep an application running and accessible with minimal downtime, typically measured by an uptime percentage (e.g., 99.9%).
- **Scalability:** The capability to handle increased or decreased demand by adding/removing resources — can be **vertical** (scaling up, i.e., increasing the size/power of a resource) or **horizontal** (scaling out, i.e., adding more instances of a resource).
- **Elasticity:** Automatically scaling resources up or down in response to real-time demand, without manual intervention.
- **Reliability:** The ability of a system to recover from failures and continue functioning correctly over time.

**Example combining these concepts:**
An online ticket booking platform uses horizontal scaling (adding more web server instances) during a major concert ticket release. Azure's autoscale feature detects the traffic spike and automatically adds instances (elasticity), keeping the site available (high availability) even under sudden load, and the system is designed to automatically recover if any single instance fails (reliability).

---

## 9. Disaster Recovery Concepts

**Disaster Recovery (DR)** refers to the strategies and tools used to restore access to IT infrastructure and data after a disruptive event (natural disaster, hardware failure, cyberattack).

**Key Terms:**
- **RTO (Recovery Time Objective):** The maximum acceptable time to restore a system after a failure.
- **RPO (Recovery Point Objective):** The maximum acceptable amount of data loss, measured in time (e.g., data as of the last 15 minutes).

**Example:**
An organization sets an RPO of 1 hour and an RTO of 4 hours for its order management system. This means data can be backed up hourly (accepting up to 1 hour of data loss in a disaster), and the system must be fully restored within 4 hours of an outage.

**How Azure supports DR:**
- Geo-redundant storage (data replicated to a secondary region).
- Azure Site Recovery (replicates VMs to another region for failover).
- Availability Zones (physically separate locations within an Azure region to protect against datacenter-level failures).

---

## Unit 1 Summary (Quick Revision)

- Cloud computing shifts IT spending from CapEx to OpEx and uses a consumption-based pricing model.
- Key benefits: high availability, scalability, elasticity, agility, fault tolerance, disaster recovery, global reach.
- Economies of scale allow cloud providers to offer lower per-unit costs.
- Shared Responsibility Model: customer always owns data and identity; provider always owns physical infrastructure; everything else depends on service model.
- Deployment models: Public (shared, provider-owned), Private (dedicated, single organization), Hybrid (mix of both).
- Service models: IaaS (most customer control), PaaS (provider manages OS/runtime), SaaS (provider manages almost everything).
- Scalability = capability to handle load; Elasticity = automatic scaling in response to demand.
- DR concepts: RTO (time to recover), RPO (acceptable data loss).

---

## Practice Questions (Self-Check)

1. A company wants to avoid managing physical servers but still wants full control over the operating system and installed software. Which service model should they choose?
2. What is the key difference between scalability and elasticity?
3. In the shared responsibility model, who is always responsible for data classification and access management, regardless of service model?
4. A bank must keep customer data on-premises due to regulation but wants to run its customer app in the cloud. Which deployment model fits this requirement?
5. Define RTO and RPO with an example each.

*(Answers to be discussed in class / covered in practical session mapped to Experiment 1 and Experiment 2.)*