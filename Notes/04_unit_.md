# AZ-900: Microsoft Azure Fundamentals
## Unit 4 — Cost Management, Governance, Management Tools, Monitoring, and Security

**Exam Domain Covered:** Describe Azure management and governance (approximately 30–35% of the AZ-900 exam), together with the remaining items of Describe Azure identity, access, and security (Conditional Access, Zero Trust, defense in depth, Microsoft Defender for Cloud).

**Note on scope:** Units 1–3 covered the cloud concepts domain and the architecture and services domain in full, plus Microsoft Entra ID, authentication methods, and RBAC. This unit completes the AZ-900 blueprint. It covers cost management tools, governance and compliance features, Azure management tools, monitoring tools, and the security fundamentals the exam tests. Topics that go beyond a typical syllabus wording but are explicitly tested on AZ-900 are marked **(AZ-900 Add-on)**.

**Prerequisites used in this unit:** Resource hierarchy and Resource Groups (Unit 2, Sections 4–7), Azure Resource Manager (Unit 2, Section 8), Autoscale (Unit 1, Section 11), Availability Zones and Region Pairs (Unit 2), Microsoft Entra ID, MFA and RBAC (Unit 3, Sections 12–14).

---

# PART A — COST MANAGEMENT

## 1. Factors That Affect Azure Costs

Azure uses consumption-based pricing (Unit 1, Section 8), so the bill is the sum of many metered usage items. The exam expects you to know which factors change the price of a resource.

| Factor | How it affects cost | Example |
|---|---|---|
| **Resource type** | Each resource type is billed by different meters, and the configuration chosen changes the rate | A larger VM size costs more per hour than a smaller one; a storage account using GRS costs more than one using LRS |
| **Consumption (usage)** | Pay for what is used: compute hours, GB stored, number of transactions | A VM that runs 9 hours a day is billed for 9 hours, not 24 |
| **Maintenance** | Resources that are left running or provisioned but idle still cost money | A forgotten test VM that is stopped but not deallocated, or an unattached managed disk, continues to cost |
| **Geography (region)** | The same resource has different prices in different regions because local infrastructure and operating costs differ | A VM in one region can be cheaper than the same VM size in another region |
| **Network traffic (bandwidth)** | Data moving into Azure (inbound) is generally free; data leaving Azure (outbound) to the internet or between regions is charged | Serving large video files from Blob Storage to users incurs outbound transfer charges |
| **Subscription type** | Pay-as-you-go, Enterprise Agreement, and Cloud Solution Provider subscriptions can have different pricing terms and discounts | An enterprise with an agreement may get negotiated rates |
| **Azure Marketplace** | Third-party products from the Marketplace are billed according to the publisher's pricing, in addition to the underlying Azure resources | A pre-configured Marketplace VM image with licensed software adds a software charge on top of the VM compute cost |

**Example:**
A company deploys the same web application in two regions. Both VMs use the same size, but the East US deployment costs less per hour than the one in a region with higher local operating costs. In addition, the second deployment is configured with GRS storage and serves heavy outbound traffic, so its storage and bandwidth charges are also higher. Region, redundancy choice, and outbound data transfer together explain the difference in the monthly bill.

**Exam Tip:** Questions often ask which action reduces cost. Typical correct answers are: choose a cheaper region where latency and data-residency rules allow, shut down (deallocate) unused VMs, select the right storage redundancy and access tier, and reduce outbound data transfer.

---

## 2. Azure Pricing Calculator

The **Azure Pricing Calculator** is a free, web-based tool used to **estimate the cost of Azure services before deploying them**.

**How it works:**
- The user adds Azure products (VMs, App Service, storage, databases) to an estimate.
- For each product the user selects options such as region, size or tier, redundancy, and expected usage (for example, hours per month).
- The calculator produces an estimated monthly cost and allows the estimate to be saved, shared, or exported.

**Key point:** The Pricing Calculator is about **future costs of new Azure workloads**. It does not read actual spending.

**Example:**
A team plans to run an App Service plan, an Azure SQL Database, and a storage account with GRS redundancy. Before creating any resource, it adds all three to the Pricing Calculator, selects the planned region and tiers, and exports an estimate to include in the project budget request.

---

## 3. Total Cost of Ownership (TCO) Calculator

The **TCO Calculator** estimates the **cost savings of migrating on-premises workloads to Azure** by comparing the cost of running the workloads on-premises with the cost of running them in Azure over a chosen time frame (such as 1, 3, or 5 years).

**How it works:**
- The user describes the current on-premises environment: servers (physical or virtual), databases, storage, and network.
- The user can adjust assumptions such as power, cooling, IT labor, and hardware costs.
- The calculator produces a side-by-side comparison of on-premises cost versus Azure cost, showing the estimated savings. This reflects the CapEx-to-OpEx shift from Unit 1, Section 2.

**Note:** Azure Migrate (Unit 3, Section 9) also offers a business-case capability that builds a similar cost comparison from an inventory discovered in the actual environment. AZ-900 still tests the TCO Calculator concept.

**Pricing Calculator vs TCO Calculator (a frequent exam distinction):**

| Feature | Pricing Calculator | TCO Calculator |
|---|---|---|
| Question it answers | "How much will this Azure workload cost?" | "How much will we save by moving from on-premises to Azure?" |
| Input | Azure services and configuration the user plans to use | The existing on-premises infrastructure |
| Output | Estimated Azure cost | On-premises cost vs Azure cost over time, with savings |
| Typical user moment | Planning a new deployment | Building the business case for migration |

**Example:**
A university runs 40 on-premises servers in its own datacenter and is deciding whether to migrate. It enters the server counts, storage, and network details into the TCO Calculator, which shows the estimated three-year cost of staying on-premises against the estimated cost on Azure. After the decision is made, the team uses the Pricing Calculator to estimate the exact Azure services it will deploy.

---

## 4. Azure Cost Management + Billing

**Microsoft Cost Management** (within **Cost Management + Billing**) is the tool used to **monitor, analyze, and control the actual spending on Azure resources** after they are deployed.

**Key capabilities:**
- **Cost analysis:** Break down actual spending by resource, resource group, subscription, service, location, or tag.
- **Budgets:** Set a spending limit for a scope (such as a subscription or resource group) for a period.
- **Alerts:** Notify users by email or action when spending reaches defined percentages of a budget, or when a forecast shows the budget will be exceeded.
- **Recommendations:** Surface cost-saving suggestions, such as resizing or shutting down underused VMs (the same cost recommendations are surfaced by Azure Advisor, Section 15).

**Important exam point:** A budget **does not stop resources or block spending by default**. It sends notifications. Stopping resources automatically requires extra automation that is triggered by the alert.

**Example:**
A department sets a monthly budget of a fixed amount on its Dev subscription, with alerts at 80 percent and 100 percent. When actual spending reaches 80 percent, the department's administrators receive an email. Using cost analysis grouped by resource group, they find that one forgotten test VM is responsible for most of the overrun and delete it.

---

## 5. Cost-Saving Options (AZ-900 Add-on)

AZ-900 practice scenarios regularly ask for the way to lower the cost of a given workload.

| Option | What it is | Best suited for |
|---|---|---|
| **Azure Reservations (Reserved Instances)** | Commit to using a specific resource (such as a VM size) for **1 or 3 years** in exchange for a significant discount compared to pay-as-you-go | Steady, predictable, always-on workloads |
| **Azure Savings Plan for compute** | Commit to a fixed hourly spend on compute for 1 or 3 years, applied flexibly across eligible compute services | Compute usage that is predictable in amount but changes in type or region |
| **Azure Spot Virtual Machines** | Use Azure's unused capacity at a deep discount, with the risk that Azure can evict the VM when it needs the capacity back | Interruptible work such as batch processing or testing |
| **Azure Hybrid Benefit** | Use existing on-premises Windows Server or SQL Server licenses that have Software Assurance (or qualifying subscriptions) on Azure to avoid paying for the license again | Organizations migrating licensed software from on-premises |

**Example:**
A company runs a database VM continuously all year. Because the workload is predictable, it purchases a 3-year reservation for that VM size instead of paying pay-as-you-go rates. The same company already owns Windows Server licenses with Software Assurance, so it also applies Azure Hybrid Benefit to avoid paying for the Windows license a second time. For its nightly data-processing job, which can safely restart if interrupted, it uses Spot VMs.

---

## 6. Tags

A **tag** is a **name-value pair** that can be attached to Azure resources, resource groups, and subscriptions to organize them logically.

**Common uses:**
- Cost tracking: group spending by department, project, or environment in Cost Management (for example, `Department = Finance`, `Environment = Production`).
- Operations: identify owners, applications, or automation scope.
- Governance: used with Azure Policy to require or audit specific tags.

**Key facts (frequently tested):**
- A resource can have multiple tags, up to a defined limit per resource.
- **Tags are NOT automatically inherited.** Applying a tag to a resource group does not automatically apply it to the resources inside the group. Inheritance can be achieved by using Azure Policy (a policy that copies or appends the tag from the resource group) or the tag-inheritance setting in Cost Management.
- Tags do not change how a resource functions. They are metadata only.

**Example:**
A company tags every resource with `CostCenter` and `Environment`. In Cost Management, an administrator groups the cost analysis by the `CostCenter` tag and sees exactly how much each department spent across several resource groups, even though the resources belong to different groups.

---

# PART B — GOVERNANCE AND COMPLIANCE

## 7. Azure Policy

**Azure Policy** is a governance service used to **create, assign, and manage rules that enforce standards on Azure resources and assess their compliance**. It checks the **properties of resources** against the organization's rules.

**Key concepts:**
- **Policy definition:** A single rule that states a condition and an effect. Examples: "Allowed locations," "Allowed VM sizes," "Require a tag on resources."
- **Initiative (policy set):** A collection of related policy definitions grouped to achieve a single goal, for example a regulatory standard.
- **Assignment:** Applying a definition or initiative to a **scope** (management group, subscription, resource group). Assignments are inherited down the resource hierarchy (Unit 2, Section 7).
- **Effects (what the policy does):**

| Effect | Behavior |
|---|---|
| Deny | Blocks creation or update of a resource that violates the rule |
| Audit | Allows the resource but records it as non-compliant |
| Append / Modify | Adds or changes properties (such as tags) on the resource |
| DeployIfNotExists | Deploys a related resource if it is missing |

- **Compliance:** Azure Policy evaluates both new and **existing** resources, and shows a compliance dashboard. Existing non-compliant resources are flagged and can be remediated; they are not automatically deleted.

**Example:**
A company assigns the built-in "Allowed locations" policy at the subscription level, permitting only India regions. A developer then attempts to create a VM in another region. ARM (Unit 2, Section 8) evaluates the request against the policy and rejects it with a "Deny" effect, even though the developer has the Contributor role on the resource group.

---

## 8. Resource Locks

A **resource lock** prevents accidental **deletion or modification** of Azure resources, regardless of the user's permissions.

**Two lock types:**

| Lock Type | Effect |
|---|---|
| **CanNotDelete** (Delete) | Authorized users can read and modify the resource, but cannot delete it |
| **ReadOnly** | Authorized users can only read the resource; they cannot modify or delete it |

**Key facts:**
- A lock applies to **all users and roles**, including users with the Owner role. To delete or change a locked resource, the lock must first be removed (by a user who has permission to manage locks).
- Locks can be applied at the subscription, resource group, or resource level, and are **inherited** by everything beneath that scope.
- Locks protect against accidental changes made through the management plane (for example, from the Portal or CLI). They are not a replacement for backup or for access control.

**Example:**
The "WebApp-Prod" resource group (Unit 2, Section 4) holds a production VM, storage account, and virtual network. An administrator applies a CanNotDelete lock to the resource group. Later, someone tries to delete the resource group, and Azure refuses the request until the lock is removed. This protects against the accidental cascade deletion described in Unit 2.

---

## 9. Azure Policy vs RBAC vs Resource Locks (Exam Comparison)

These three features are often confused because all of them restrict what can happen in Azure.

| Feature | Question it answers | Focus | Example |
|---|---|---|---|
| **RBAC** (Unit 3) | "What can this **user** do?" | User actions (authorization) | A junior developer has the Reader role and cannot create VMs |
| **Azure Policy** | "What state are **resources** allowed to be in?" | Resource properties and compliance | VMs can only be created in approved regions, even for an Owner |
| **Resource Lock** | "Can this resource be **deleted or changed** at all?" | Protection from accidental deletion or change | A production resource group cannot be deleted until the lock is removed |

**Scenario that combines all three:**
A user with the Contributor role (RBAC allows creating resources) tries to deploy a VM in a disallowed region. RBAC permits the action, but Azure Policy denies it. In another case, the same user tries to delete the production resource group. RBAC permits it, but a CanNotDelete lock blocks it.

---

## 10. Cloud Adoption Framework (AZ-900 Add-on)

The **Microsoft Cloud Adoption Framework for Azure** is a collection of documentation, guidance, best practices, and tools that helps an organization plan and carry out its move to the cloud.

**Phases (in order):**

| Phase | Purpose |
|---|---|
| Strategy | Define business justification and goals for moving to the cloud |
| Plan | Create an adoption plan aligned to those goals, including skills and workload inventory |
| Ready | Prepare the environment, including the landing zone where workloads will run |
| Adopt | Migrate existing workloads and build or modernize new ones |
| Govern | Set up governance (policies, cost control, compliance) |
| Manage | Operate the cloud environment (monitoring, operations, resilience) |

**Note on Azure Blueprints:** Older AZ-900 question banks refer to Azure Blueprints as a way to package ARM templates, policy assignments, and role assignments into a repeatable environment definition. Microsoft has announced the retirement of Azure Blueprints, and the current exam objectives focus on Azure Policy, locks, and tags instead. Know the term for older material, but do not teach it as the recommended approach.

---

## 11. Microsoft Purview and Compliance Resources (AZ-900 Add-on)

### 11.1 Microsoft Purview
**Microsoft Purview** is a family of data governance, risk, and compliance solutions that helps an organization **understand, govern, and protect its data across on-premises, multicloud, and SaaS environments**.

Main ideas for AZ-900:
- **Data governance:** Discover and catalog data sources and see where data lives and how it flows.
- **Compliance solutions:** Help an organization meet regulatory requirements. This includes **Compliance Manager**, which provides assessments and a compliance score against regulatory standards.

**Example:**
A hospital stores patient data across Azure SQL Database, Blob Storage, and an on-premises file server. It uses Microsoft Purview to discover and catalog where sensitive data is stored, so it can apply the right protection and prove to auditors that it knows where regulated data lives.

### 11.2 Trust and Privacy Resources

| Resource | What it provides |
|---|---|
| **Microsoft Trust Center** | Information about how Microsoft approaches security, privacy, and compliance |
| **Service Trust Portal** | Audit reports, certifications, and compliance documentation (such as ISO and SOC reports) that customers can download for their own auditors |
| **Microsoft Privacy Statement** | Explains what personal data Microsoft processes, how, and why |
| **Compliance offerings documentation** | Lists the regulations and standards Azure supports, by industry and region |

**Example:**
A bank's auditor asks for evidence that Azure meets a specific security standard. The bank's compliance officer downloads the relevant audit report from the Service Trust Portal and attaches it to the audit file.

---

# PART C — AZURE MANAGEMENT TOOLS

## 12. Azure Portal, Cloud Shell, Azure CLI, and Azure PowerShell

Azure resources can be managed through several interfaces. All of them call the same **Azure Resource Manager API** (Unit 2, Section 8), so the result and policy enforcement are the same.

| Tool | What it is | Typical use |
|---|---|---|
| **Azure Portal** | Web-based graphical interface | Exploring, learning, creating and managing resources visually |
| **Azure Cloud Shell** | Browser-based, authenticated shell inside the Portal (or a browser tab) offering **Bash** or **PowerShell**, with common tools pre-installed | Running commands without installing anything locally |
| **Azure CLI** | Cross-platform command-line tool using `az` commands, available on Windows, macOS, and Linux | Scripting and automation, especially for users who prefer Bash-style commands |
| **Azure PowerShell** | PowerShell module with Azure cmdlets (for example, `New-AzVM`), also cross-platform | Scripting and automation for users who prefer PowerShell |

**Key facts:**
- Cloud Shell needs a storage account (an Azure Files share) to keep files between sessions, which ties back to Azure Files in Unit 3, Section 7.
- Azure CLI and Azure PowerShell are installed on a local machine, while Cloud Shell needs no local installation.
- Command-line tools are preferred over the Portal when tasks must be repeated, automated, or run at scale.

**Example:**
An administrator needs to create 20 identical resource groups, each tagged with its project name. Clicking through the Portal 20 times would be slow and error-prone. Instead the administrator writes a short script using Azure CLI in Cloud Shell, and the 20 groups are created in one run.

---

## 13. Azure Arc (AZ-900 Add-on)

**Azure Arc** extends Azure management and governance to resources that are **outside Azure**, such as servers in an on-premises datacenter, servers in other cloud providers, and Kubernetes clusters.

**How it works:**
- Arc projects the external resources into Azure Resource Manager, so they appear in the Portal as Azure resources.
- Once projected, familiar Azure tools can be applied to them: tags, Azure Policy, RBAC, and monitoring.

**Connection to Unit 1:** Azure Arc is a practical tool for **hybrid cloud** (Unit 1, Section 6.3), because it gives one management experience across the on-premises and cloud parts of the environment.

**Example:**
A company keeps 30 Windows servers in its own datacenter while running other workloads in Azure. By connecting the on-premises servers through Azure Arc, the company can assign the same Azure Policy, tags, and RBAC to all servers, and see them in the same Azure Portal view as its Azure VMs.

---

## 14. Infrastructure as Code: ARM Templates and Bicep

**Infrastructure as Code (IaC)** means defining infrastructure in files that are deployed by tools, rather than created by hand. The same files can be stored in version control and reused.

**Benefits:**
- **Consistency:** Every deployment produces the same result.
- **Repeatability:** The same file can create development, test, and production environments.
- **Speed and agility:** Environments are created in minutes (Unit 1, Section 14).
- **Documentation and version history:** The file is the record of what was deployed.

| Option | Description |
|---|---|
| **ARM templates** | JSON files describing the desired end-state of Azure resources (introduced in Unit 2, Section 8). Declarative: the template states what should exist, and ARM works out how to create it |
| **Bicep** | A simpler, more readable declarative language for Azure that is **compiled into an ARM template** before deployment |

**Example:**
A team stores a Bicep file describing a resource group's VM, virtual network, and storage account. Deploying the file to a test subscription and then a production subscription gives two identical environments. When the team changes the file and redeploys, Azure updates the existing resources to match, instead of creating duplicates.

---

# PART D — MONITORING

## 15. Azure Advisor

**Azure Advisor** is a free, personalized recommendation service that **analyzes the existing Azure resources and configuration and suggests ways to improve them**.

**Recommendations are grouped into five categories:**

| Category | Typical recommendation |
|---|---|
| **Reliability** | Use Availability Zones or an Availability Set for a single critical VM |
| **Security** | Fix a security issue flagged by Microsoft Defender for Cloud |
| **Performance** | Upgrade an overloaded resource to a larger size |
| **Cost** | Resize or shut down underused VMs |
| **Operational Excellence** | Improve process, deployment, and management practices |

**Example:**
Advisor reports that a production VM has had very low CPU usage for weeks and recommends resizing it to a smaller size, which would lower the monthly cost. In the same view it recommends placing another critical single-instance VM in an Availability Zone for better reliability.

---

## 16. Azure Service Health

**Azure Service Health** keeps users informed about the health of the Azure services, regions, and resources they depend on. It has three parts:

| Component | Scope | Purpose |
|---|---|---|
| **Azure Status** | Global, public | Shows the overall health of Azure services and regions worldwide |
| **Service Health** | Personalized to the user's subscriptions, regions, and services | Tracks service issues, planned maintenance, health advisories, and security advisories that affect the user's own environment |
| **Resource Health** | Individual resources | Shows whether a specific resource (such as one VM) is available, unavailable, or degraded, and why |

**Key point:** Service Health tells about problems in the Azure platform. It does not diagnose problems that originate inside the customer's own application.

**Example:**
An application running in an Azure region becomes slow. The operations team first checks Resource Health for their VM and sees that it is available. They then check Service Health and find an ongoing service issue in that region. Instead of spending hours debugging their application, they know the cause is a platform issue and notify users.

---

## 17. Azure Monitor

**Azure Monitor** is a platform that **collects, analyzes, and acts on telemetry** from Azure resources, applications, and on-premises environments.

**Key components:**

| Component | Purpose |
|---|---|
| **Metrics** | Numerical measurements collected at regular intervals, such as CPU percentage or request count; suited to near-real-time monitoring |
| **Logs (Log Analytics)** | Detailed event and diagnostic data stored in a Log Analytics workspace and queried with a query language called KQL |
| **Alerts** | Notify people or trigger automated action when a condition is met, using **action groups** to define who is notified and what happens |
| **Application Insights** | Application performance monitoring for web applications, such as response times, failures, and dependencies |
| **Dashboards and workbooks** | Visualize metrics and logs together |

**Connection to earlier units:** Azure Autoscale (Unit 1, Section 11; VM Scale Sets in Unit 2) makes its scaling decisions from Azure Monitor metrics such as average CPU usage.

**Azure Monitor vs Service Health vs Advisor (exam comparison):**

| Tool | Focus |
|---|---|
| Azure Monitor | Performance and behavior of the **customer's** resources and applications |
| Azure Service Health | Health of the **Azure platform** and services themselves |
| Azure Advisor | **Recommendations** to improve reliability, security, performance, cost, and operations |

**Example:**
A company's App Service web app shows occasional slow responses. The team uses Azure Monitor metrics to see response time rising whenever CPU use passes 80 percent. They create an alert that sends an email through an action group at 80 percent CPU, and use Application Insights to find the slow requests. Later they enable autoscale using the same CPU metric.

---

# PART E — SECURITY FUNDAMENTALS

## 18. Defense in Depth (AZ-900 Add-on)

**Defense in depth** is a layered security strategy. Instead of relying on one protection, several layers are used so that if one layer is breached, the next layer still protects the data.

**The seven layers (outermost to innermost):**

| Layer | Protects against | Azure examples covered in this course |
|---|---|---|
| 1. Physical security | Physical access to datacenters | Microsoft-managed datacenters (always the provider's responsibility, Unit 1, Section 5) |
| 2. Identity and access | Unauthorized sign-in and excess permissions | Microsoft Entra ID, MFA, RBAC (Unit 3) |
| 3. Perimeter | Large-scale network attacks from outside | Edge protections such as DDoS protection |
| 4. Network | Unauthorized network communication | NSGs, Azure Firewall, VNet segmentation (Unit 3) |
| 5. Compute | Vulnerable or exposed servers | Securing VMs, patching, limiting open ports |
| 6. Application | Insecure application code | Secure development, web application firewall (Application Gateway WAF, Unit 3) |
| 7. Data | Exposure or theft of stored data | Encryption, storage redundancy and access control |

**Example:**
An attacker steals an employee's password. Because the company uses defense in depth, MFA (identity layer) stops the sign-in. If the attacker had bypassed that, the NSG (network layer) allows access to the database subnet only from the web subnet, and encryption (data layer) protects the stored records.

---

## 19. Zero Trust (AZ-900 Add-on)

**Zero Trust** is a security model that assumes **no user, device, or network location is trusted by default**, even inside the corporate network. Every access request is checked.

**Three guiding principles:**

| Principle | Meaning |
|---|---|
| **Verify explicitly** | Always authenticate and authorize using all available signals (identity, location, device health, risk) |
| **Use least privilege access** | Give only the minimum access needed (RBAC in Unit 3), and only for the time needed |
| **Assume breach** | Design as if an attacker is already inside: limit the blast radius, segment networks, and monitor continuously |

**Example:**
An employee in the office tries to open a sensitive application. Under a traditional model, being on the office network is enough. Under Zero Trust, the system still verifies the user's identity with MFA, checks that the laptop is compliant, and grants only the role needed for that application.

---

## 20. Conditional Access (AZ-900 Add-on)

**Conditional Access** is a feature of Microsoft Entra ID that uses **if-then policies** to decide, at sign-in time, whether to grant access, require extra verification, or block. It is the practical engine behind Zero Trust's "verify explicitly."

**How a policy works:**
- **Signals (the "if"):** user or group, location, device state, application being accessed, and sign-in risk.
- **Decisions (the "then"):** block access, grant access, or grant access only if a requirement is met, such as completing MFA or using a compliant device.

**Key facts:**
- Conditional Access is applied **after** the first factor (such as a password) is completed.
- It requires a paid Microsoft Entra ID plan (Entra ID P1 or higher).

**Example:**
A company creates a policy: "If a user signs in from outside the corporate network, then require MFA. If a user signs in from a high-risk location, then block." A sales employee working from a café is prompted for MFA, while the same employee in the office is not.

---

## 21. Microsoft Defender for Cloud (AZ-900 Add-on)

**Microsoft Defender for Cloud** is a cloud-native security service that provides **security posture management** and **threat protection** for workloads in Azure, on-premises, and other clouds.

**Main capabilities:**

| Capability | Meaning |
|---|---|
| **Security posture management** | Continuously assesses resources against security best practices, produces prioritized **recommendations**, and calculates a **Secure Score** that shows how well the environment is secured |
| **Workload threat protection** | Detects and alerts on threats against resources such as VMs, storage accounts, databases, and containers |
| **Multi-environment coverage** | Works across Azure, on-premises (through Azure Arc), and other cloud providers |

**Example:**
Defender for Cloud scans a subscription and reports that a VM has a management port open to the internet and that a storage account allows public access. It shows a low Secure Score and a prioritized list of fixes. After the team applies the recommendations, the Secure Score rises.

---

# PART F — SERVICE LEVEL AGREEMENTS AND SERVICE LIFECYCLE

## 22. Service Level Agreements (SLAs)

A **Service Level Agreement (SLA)** is Microsoft's commitment for the **uptime and connectivity** of an Azure service, expressed as a percentage (introduced under High Availability, Unit 1, Section 9).

**Key facts:**
- Each Azure service has its own SLA, and the percentage depends on the configuration. A single-instance VM with standard disks has a lower SLA than VMs deployed across Availability Zones.
- If Microsoft fails to meet the SLA, the customer can claim **service credits**. This is a bill credit, not compensation for business loss.
- Higher availability configurations cost more.

**Approximate downtime allowed per year:**

| SLA | Allowed downtime per year |
|---|---|
| 99% | About 3.65 days |
| 99.9% | About 8.76 hours |
| 99.95% | About 4.38 hours |
| 99.99% | About 52.6 minutes |
| 99.999% | About 5.26 minutes |

### 22.1 Composite SLAs

When an application depends on several services **in series** (all must work), the **composite SLA** is the **product** of the individual SLAs, so it is **lower** than any single one.

**Example:**
A web app (99.95 percent SLA) depends on a database (99.99 percent SLA).
Composite SLA = 0.9995 × 0.9999 = 0.99940005, which is approximately **99.94 percent**.

When the same service is deployed **redundantly** (either copy can serve the request), the combined availability is **higher**:
Combined = 1 − (1 − 0.999) × (1 − 0.999) = 0.999999, which is **99.9999 percent**.

**Exam Tip:** More dependent services in series lower the composite SLA. Adding redundant copies, for example across Availability Zones (Unit 2, Section 3), raises it.

---

## 23. Service Lifecycle: Preview and General Availability

New Azure features and services pass through lifecycle stages:

| Stage | Description | SLA |
|---|---|---|
| **Private preview** | Limited to selected customers by invitation | Not covered |
| **Public preview** | Available to all customers to try, for testing and feedback; features can change | Generally **not** covered by an SLA and not recommended for production |
| **General Availability (GA)** | Released for production use | Covered by the service's SLA |

**Example:**
A team wants to use a new Azure feature that is in public preview. The feature works in testing, but because preview services typically do not carry an SLA, the team waits until the feature reaches General Availability before using it in production. They follow Azure Updates to track when this happens.

---

## Unit 4 Summary (Quick Revision)

**Cost Management**
- **Cost factors:** resource type, consumption, maintenance (idle resources), region, outbound bandwidth, subscription type, Marketplace.
- **Pricing Calculator:** estimates the cost of **new Azure workloads**. **TCO Calculator:** compares **on-premises vs Azure** cost to show savings. **Cost Management:** analyzes **actual spending**, sets budgets and alerts; budgets do not stop spending by default.
- **Cost-saving options:** Reservations (1 or 3 years), Savings Plan, Spot VMs (can be evicted), Azure Hybrid Benefit (reuse existing licenses).
- **Tags:** name-value metadata for organization and cost tracking; **not inherited** by default.

**Governance and Compliance**
- **Azure Policy:** enforces rules on **resource properties** (allowed locations, allowed sizes, required tags); effects include Deny, Audit, Modify, DeployIfNotExists; evaluates existing resources as well.
- **Resource Locks:** CanNotDelete and ReadOnly; apply to all users including Owners; inherited down the hierarchy.
- **RBAC vs Policy vs Locks:** RBAC controls what **users** can do; Policy controls what **resources** may look like; Locks prevent **deletion or change**.
- **Cloud Adoption Framework:** Strategy, Plan, Ready, Adopt, Govern, Manage. Azure Blueprints is being retired.
- **Microsoft Purview** for data governance and compliance; **Service Trust Portal** for audit reports; Trust Center and Privacy Statement for security and privacy information.

**Management Tools**
- Portal (graphical), Cloud Shell (browser-based Bash or PowerShell), Azure CLI (`az`), Azure PowerShell (cmdlets); all go through ARM.
- **Azure Arc** projects on-premises and other-cloud servers and Kubernetes into Azure for unified management.
- **IaC:** ARM templates (JSON, declarative) and **Bicep** (simpler language that compiles to ARM templates).

**Monitoring**
- **Azure Advisor:** recommendations in five categories (Reliability, Security, Performance, Cost, Operational Excellence).
- **Azure Service Health:** Azure Status (global), Service Health (your subscriptions), Resource Health (single resource).
- **Azure Monitor:** metrics, logs (Log Analytics), alerts with action groups, Application Insights; feeds Autoscale.

**Security**
- **Defense in depth:** Physical, Identity and access, Perimeter, Network, Compute, Application, Data.
- **Zero Trust:** verify explicitly, use least privilege access, assume breach.
- **Conditional Access:** if-then sign-in policies in Entra ID (signals and decisions), requires Entra ID P1 or higher.
- **Microsoft Defender for Cloud:** security posture management, Secure Score, recommendations, and threat protection across Azure, on-premises, and other clouds.

**SLAs and Lifecycle**
- SLA is an uptime percentage with service credits as the remedy; composite SLA for dependent services is the **product** (lower); redundancy raises availability.
- Lifecycle: Private preview, Public preview (usually no SLA), General Availability (SLA applies).

---

## Practice Questions (Self-Check)

1. List four factors that affect the cost of an Azure resource and give an example of each.
2. What is the difference between the Pricing Calculator and the TCO Calculator? Which would a company use first when deciding whether to migrate from on-premises, and which afterward?
3. A department's budget in Cost Management reaches 100 percent. Are its resources stopped automatically? Explain.
4. Explain Azure Reservations, Spot VMs, and Azure Hybrid Benefit, and give a workload suited to each.
5. A tag is applied to a resource group. Will the VMs inside it automatically have the tag? How could the tag be applied to them automatically?
6. Explain the difference between Azure RBAC, Azure Policy, and resource locks using a scenario in which a user with the Contributor role tries to delete a production resource group.
7. What does the Deny effect do in an Azure Policy? What happens to resources that already violate a newly assigned policy?
8. Distinguish the CanNotDelete lock from the ReadOnly lock. Does a lock stop a user with the Owner role?
9. Explain what Azure Arc does and how it relates to the hybrid cloud deployment model.
10. What is the relationship between ARM templates and Bicep?
11. Name the five categories of Azure Advisor recommendations, and say which Azure tool shows the health of a single VM.
12. Distinguish Azure Monitor, Azure Service Health, and Azure Advisor using a scenario of a slow application.
13. List the seven layers of defense in depth and match one tool from earlier units to three of the layers.
14. State the three principles of Zero Trust. How does Conditional Access support the "verify explicitly" principle?
15. What is the Secure Score in Microsoft Defender for Cloud?
16. A web app with a 99.95 percent SLA depends on a database with a 99.99 percent SLA. Calculate the composite SLA. Why is it lower than either individual SLA?
17. Why should a production workload not depend on a service that is in public preview?

*(Answers to be discussed in class and used as the basis for the Unit 4 question bank extension.)*
