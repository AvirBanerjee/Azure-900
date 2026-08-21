# AZ-900: Microsoft Azure Fundamentals
## Unit 1 — Cloud Computing Fundamentals

**Course Outcome Covered:** CO1 — Explain cloud computing concepts and service models.

---

## 1. Cloud Fundamentals

Cloud computing is the delivery of computing services over the internet — compute power, storage, databases, networking, analytics, and software — from a provider such as Microsoft Azure, instead of from hardware owned and run by the organization itself.

In the traditional model, an organization buys physical servers, installs them in its own datacenter (or a rented one), and hires staff to maintain them. Every part of the stack — power supply, cooling, physical security, hardware replacement, patching, networking — is the organization's responsibility.

In the cloud model, the provider owns and operates the physical datacenters. The organization "rents" resources over the internet, consuming exactly the amount of compute, storage, or networking it needs, when it needs it, and gives it back when it no longer needs it.

**Core characteristics of cloud computing (as defined for AZ-900):**
- **On-demand self-service:** A user can provision resources (e.g., a virtual machine) without needing to call a human administrator.
- **Broad network access:** Resources are available over the internet from many types of devices.
- **Resource pooling:** The provider's physical resources serve multiple customers, dynamically assigned as needed.
- **Rapid elasticity:** Resources can be scaled up or down quickly, sometimes automatically.
- **Measured service:** Usage is metered, so customers are billed based on actual consumption.

**Example:**
A college wants to host an online examination portal for one week during exam season. On-premises, it would need to buy servers capable of handling peak load for that one week, and those servers would sit mostly idle for the remaining 51 weeks. On Azure, the college provisions web servers only for that week, pays for that week's usage, and deallocates the resources afterward.

---

## 2. CapEx vs OpEx

This is one of the most fundamental economic concepts behind why organizations move to the cloud, and it is frequently tested on AZ-900.

### 2.1 Capital Expenditure (CapEx)
- Upfront spending on physical infrastructure (servers, networking equipment, datacenter facilities).
- Treated as a long-term investment; the asset depreciates in value over years.
- Requires accurate long-term forecasting of capacity needs — buying too much wastes money, buying too little limits growth.
- Typically requires approval cycles, procurement, and large one-time budgets.

### 2.2 Operational Expenditure (OpEx)
- Spending on services on an ongoing, as-you-go basis (e.g., a monthly Azure bill).
- No large upfront investment; cost is spread over time and tied to actual usage.
- Easier to adjust — if demand drops, spending drops with it.
- Treated as a regular business expense rather than a long-term asset.

**Comparison Table:**

| Aspect | CapEx (On-Premises) | OpEx (Cloud) |
|---|---|---|
| Payment timing | Large upfront cost | Pay-as-you-go, ongoing |
| Financial treatment | Asset that depreciates | Operating expense |
| Forecasting risk | High — must predict capacity years ahead | Low — scale as actual demand changes |
| Flexibility | Low — hardware is fixed once purchased | High — resources adjusted anytime |
| Ownership | Organization owns the hardware | Organization owns nothing physical |

**Example:**
A retail company expects a 3x spike in website traffic during a festival sale. Under CapEx, it would need to buy enough servers year-round to handle that peak, most of which sit unused the rest of the year. Under OpEx (cloud), it scales up Azure resources for the sale period, pays only for that increased usage, and scales back down afterward — converting a fixed yearly cost into a variable cost tied to actual need.

**Exam Tip:** If a question describes "no upfront cost, pay only for what you use," the answer is OpEx / consumption-based pricing, not CapEx.

---

## 3. Benefits of Cloud Services (Overview)

Cloud computing offers several advantages over traditional on-premises IT. The core benefits tested in AZ-900 are: **High Availability, Scalability, Elasticity, Reliability, Fault Tolerance, Agility, and Global Reach.** Each is significant enough to be covered in its own dedicated section later in this unit (Sections 9–15). At a high level:

| Benefit | One-line meaning |
|---|---|
| High Availability | The system stays accessible with minimal downtime |
| Scalability | The system can handle more or less load by adjusting resources |
| Elasticity | Resources scale automatically in response to real-time demand |
| Reliability | The system recovers from failures and keeps working correctly |
| Fault Tolerance | The system keeps running even when a component fails |
| Agility | Resources can be provisioned and changed quickly |
| Global Reach | Applications can be deployed close to users anywhere in the world |

---

## 4. Economies of Scale

Cloud providers such as Microsoft operate datacenters at a massive global scale, serving millions of customers simultaneously. Because the fixed costs of building and running a datacenter (land, power infrastructure, cooling systems, networking backbone, specialized staff) are spread across an enormous customer base, the **cost per unit of compute or storage becomes far lower** than what any single organization could achieve running its own datacenter.

This principle — cost per unit decreasing as scale increases — is called **economies of scale**, and it is the fundamental economic reason cloud services can be offered more cheaply than most organizations could achieve on their own.

**Example:**
Microsoft can negotiate bulk hardware pricing, build custom energy-efficient cooling systems, and employ specialized security teams across all its datacenters at once. A single mid-sized company trying to replicate this for its own on-premises datacenter would pay dramatically more per server, because it cannot spread those fixed costs across millions of customers the way Microsoft can.

**Consequence for customers:** Because of economies of scale, Azure can pass on lower prices, which is part of why consumption-based pricing (Section 8) is financially attractive compared to building equivalent infrastructure in-house.

---

## 5. Shared Responsibility Model

Security and operational responsibility in the cloud is **divided between the cloud provider (Microsoft) and the customer.** Neither party is responsible for everything — the split depends on which service model (IaaS, PaaS, or SaaS) is being used.

**Constants regardless of service model:**
- The **customer** is always responsible for: their **data**, **endpoints** (devices accessing the cloud), their **account and identities**, and managing access permissions.
- The **provider** is always responsible for: the **physical datacenter**, **physical network**, and **physical hosts** (the underlying hardware).

**Everything in between** — operating system, network controls, applications, identity infrastructure — shifts responsibility depending on the service model chosen, which is covered in detail in Section 7.

**Example:**
If a company stores customer records in an Azure SQL Database (a PaaS offering) and an employee's weak password leads to a data breach, the company (customer) is responsible — because identity and access management is always a customer responsibility, even though Microsoft manages the underlying database engine, patching, and infrastructure.

**Why this matters for AZ-900:** Exam questions often present a security incident scenario and ask "whose responsibility is this?" The answer depends on identifying whether the failure occurred in a layer the customer controls (data, identity, applications in IaaS) or a layer the provider controls (physical security, host infrastructure).

---

## 6. Cloud Deployment Models

### 6.1 Public Cloud
Resources are owned and operated entirely by a third-party provider (e.g., Microsoft) and made available to any customer over the internet. Multiple customers share the same underlying physical hardware (multi-tenant), though each customer's data is logically isolated and inaccessible to others.

- No capital expenditure on hardware.
- Provider handles all maintenance, updates, and physical security.
- Highest scalability and reach, but least control over the underlying hardware.

**Example:** A small startup hosts its customer-facing website using Azure App Service. It shares physical servers with other Azure customers behind the scenes, but has no visibility into or access to any other customer's resources.

### 6.2 Private Cloud
Cloud infrastructure used exclusively by a single organization, whether hosted in the organization's own datacenter or by a third party on dedicated hardware. Not shared with other organizations.

- Full control over configuration, security policy, and compliance posture.
- Higher cost since economies of scale benefits are reduced or lost.
- Common in industries with strict regulatory or data sovereignty requirements.

**Example:** A defense or intelligence agency runs a private cloud within its own secured facility so that no infrastructure is ever shared with external customers, satisfying strict national security requirements.

### 6.3 Hybrid Cloud
Combines public and private cloud, with data and applications able to move between the two through a secure connection. Common for organizations transitioning to the cloud gradually, or with workloads that must legally remain on-premises.

- Allows sensitive workloads to stay private while less sensitive workloads use public cloud scale and cost benefits.
- Adds architectural complexity — networking, identity, and data must be coordinated across both environments.

**Example:** A bank stores core customer financial records in a private cloud on-premises to meet regulatory data residency laws, while running its public-facing mobile banking app on Azure public cloud, connecting the two through Azure ExpressRoute or a VPN Gateway.

**Comparison Table:**

| Model | Infrastructure Owner | Control Level | Typical Cost | Best Suited For |
|---|---|---|---|---|
| Public | Cloud provider | Lower | Lower (shared economies of scale) | Startups, general web apps, variable workloads |
| Private | Organization / dedicated third party | Highest | Higher | Regulated industries, sensitive/classified data |
| Hybrid | Mixed | Balanced | Balanced | Gradual migration, regulatory + scalability needs together |

---

## 7. Cloud Service Models: IaaS, PaaS, SaaS

The three service models describe **how much of the technology stack the customer manages versus how much the provider manages.** As you move from IaaS to SaaS, provider responsibility increases and customer responsibility decreases.

### 7.1 Infrastructure as a Service (IaaS)
The provider supplies the fundamental building blocks — virtual machines, storage, virtual networks — over the internet. The customer manages everything from the operating system upward: OS installation and patching, runtime, applications, and data.

- Maximum flexibility and control.
- Maximum management responsibility and effort for the customer.
- Closest equivalent to traditional on-premises infrastructure, just rented instead of owned.

**Example:** A company migrates its legacy Windows Server application "as-is" to Azure Virtual Machines. It still has to patch the OS, install antivirus software, and manage backups, but no longer owns or maintains physical hardware.

### 7.2 Platform as a Service (PaaS)
The provider manages the underlying infrastructure and the operating system. The customer focuses purely on developing and deploying application code and managing application data.

- Reduces management overhead significantly compared to IaaS.
- Faster development cycles — no OS patching or server configuration needed.
- Slightly less control over the underlying environment than IaaS.

**Example:** A development team deploys a web application using Azure App Service. They upload their application code; Azure automatically handles server provisioning, OS patching, and load balancing, letting developers focus only on the application itself.

### 7.3 Software as a Service (SaaS)
The provider manages nearly the entire stack, including the application software itself. The customer only manages their own data and controls who has access to it.

- Minimal management responsibility for the customer.
- Least control over customization of the underlying application/platform.
- Fastest to adopt — typically ready to use immediately after subscription.

**Example:** An organization uses Microsoft 365 for email, document editing, and collaboration. Microsoft manages the application, servers, and all underlying infrastructure. The organization only manages its user accounts, permissions, and the data it stores within the service.

**Full Responsibility Comparison (On-Premises included for contrast):**

| Layer | On-Premises | IaaS | PaaS | SaaS |
|---|---|---|---|---|
| Data | Customer | Customer | Customer | Customer |
| Applications | Customer | Customer | Customer | Provider |
| Runtime | Customer | Customer | Provider | Provider |
| Operating System | Customer | Customer | Provider | Provider |
| Virtualization | Customer | Provider | Provider | Provider |
| Servers / Storage / Networking | Customer | Provider | Provider | Provider |
| Physical Datacenter | Customer | Provider | Provider | Provider |

**Exam Tip:** AZ-900 typically presents a scenario ("a team wants to deploy code without managing servers or OS patching") and asks which model it describes. Identify how much of the stack the customer explicitly wants to avoid managing — that tells you the service model (in this example: PaaS, since OS/server management is being avoided but application control is retained).

---

## 8. Consumption-Based Pricing

Azure primarily uses a **consumption-based (pay-as-you-go) pricing model**, which is the practical, billing-level expression of the OpEx concept from Section 2.

**Key characteristics:**
- Billing is metered — customers pay for exact resource usage (compute hours, GB of storage, GB of data transferred, number of transactions).
- No cost is incurred for resources not provisioned or after they are deleted/deallocated.
- Removes the need to estimate long-term capacity in advance; resources can be adjusted as actual demand becomes clear.
- Different Azure services may bill by different units — e.g., VMs by the hour/second of compute time, storage by GB per month, bandwidth by GB transferred.

**Example:**
A company runs a data-processing virtual machine only during working hours (9 AM–6 PM) and shuts it down overnight. Because Azure bills based on actual VM runtime, the company pays only for the 9 hours of active use each day, rather than paying for 24 hours of capacity as it would if the hardware were owned outright.

**Contrast with traditional procurement:**

| Traditional IT Procurement | Azure Consumption-Based Pricing |
|---|---|
| Pay full price upfront regardless of eventual usage | Pay only for resources actually consumed |
| Idle hardware still incurs full cost | Idle/deallocated resources can stop incurring compute charges |
| Capacity planning errors are costly and hard to reverse | Capacity can be adjusted up or down at any time |

---

## 9. High Availability (HA)

High Availability is a design objective: keeping a system operational and accessible to users with minimal, ideally near-zero, unplanned downtime. It is typically expressed as a percentage of uptime over a period of time, e.g., "99.9% availability."

**How Azure enables HA:**
- **Availability Zones** — physically separate locations within an Azure region, each with independent power, cooling, and networking, so failure in one zone does not take down the application.
- **Load balancing** — distributing incoming traffic across multiple instances so no single instance failure causes an outage.
- **Service Level Agreements (SLAs)** — Microsoft publishes guaranteed uptime percentages for many Azure services, which is what HA design targets are measured against.

**Example:**
A hospital's patient records portal is deployed across two Availability Zones within an Azure region. If one zone experiences a power failure, traffic automatically continues to be served from the second zone, keeping the portal available with no interruption to healthcare staff.

---

## 10. Scalability

Scalability is the **capability** of a system to handle an increase (or decrease) in workload by adjusting the amount of resources allocated to it. It does not necessarily happen automatically — it describes the system's ability to be scaled, whether manually or automatically.

**Two directions of scaling:**
- **Vertical scaling (scaling up/down):** Increasing or decreasing the power (CPU, RAM) of an existing resource — e.g., upgrading a VM from a 2-core to an 8-core size.
- **Horizontal scaling (scaling out/in):** Increasing or decreasing the *number* of resource instances — e.g., adding more VM instances behind a load balancer.

**Example:**
An online food delivery platform anticipates higher order volume during dinner hours. An administrator manually adds three additional web server instances before 6 PM (scaling out) and removes them after 10 PM. This is scalability being exercised — the system has the capability to handle more load, even though a human triggered the change.

---

## 11. Elasticity

Elasticity is closely related to scalability but specifically refers to the **automatic** scaling of resources up or down in real time, based on actual demand, without manual intervention.

**Key distinction from scalability:** Scalability is the *capability*; elasticity is the *automated behavior* of exercising that capability in response to live demand.

**How Azure enables elasticity:**
- **Azure Autoscale** — automatically adds or removes instances of a resource (such as VM Scale Sets or App Service instances) based on defined metrics like CPU usage or request count.

**Example:**
A ticket-booking website configures Azure Autoscale to add web server instances automatically whenever average CPU usage crosses 70%, and to remove instances automatically once usage falls below 30%. During a sudden rush when concert tickets go on sale, the system scales out within minutes without any administrator action, then scales back in overnight to reduce cost — this automatic behavior is elasticity.

---

## 12. Reliability

Reliability is the ability of a system to **recover from failures and continue to function correctly** over time. It focuses on consistent, correct operation and resilience against disruption, rather than just raw uptime percentage.

**How Azure supports reliability:**
- **Redundancy** — keeping duplicate copies of data or services so a single failure does not cause data loss or downtime.
- **Backup and restore capabilities.**
- **Automated health monitoring and self-healing** — Azure can detect an unhealthy VM instance and automatically replace it.

**Example:**
An Azure-hosted application uses geo-redundant storage, meaning data is automatically copied to a secondary Azure region. If the primary region experiences a major failure, the application can still access the data from the secondary region, demonstrating reliability through built-in recovery capability.

---

## 13. Fault Tolerance

Fault Tolerance is the ability of a system to **continue operating correctly even when one or more of its components fail**, without a full service interruption. It is a specific mechanism that contributes to both high availability and reliability.

**How Azure enables fault tolerance:**
- **Availability Zones** protect against datacenter-level failure.
- **Data replication** (e.g., multiple copies of a storage blob) ensures that failure of one storage node does not cause data loss.
- **Load balancers** automatically redirect traffic away from a failed instance to healthy ones.

**Example:**
An e-commerce checkout system runs three identical instances of its payment-processing service behind a load balancer. If one instance crashes due to a software bug, the load balancer detects the failure and routes all incoming checkout requests to the remaining two healthy instances — customers experience no visible disruption. This is fault tolerance in action.

---

## 14. Agility

Agility refers to the speed and flexibility with which an organization can provision, configure, modify, or decommission cloud resources, compared to the slow procurement cycles of traditional on-premises IT.

**Example:**
A startup needs a new development and testing environment for a project. On-premises, this could take weeks to procure hardware, rack it, and configure it. On Azure, a developer provisions a full test environment — VMs, networking, storage — in under an hour, and can delete it entirely once testing is complete, incurring no further cost.

**Business impact:** Agility allows organizations to experiment, fail fast, and iterate faster, since the cost and time barrier to trying something new is drastically reduced compared to traditional procurement.

---

## 15. Global Reach

Global Reach refers to the ability to deploy applications and services across Microsoft's worldwide network of Azure regions, placing resources physically closer to end users to reduce latency and meet regional data residency requirements.

**Example:**
A company with customers in both the United States and India deploys its web application in both the East US Azure region and the Central India Azure region. Users in each location are routed (via a service such as Azure Traffic Manager or Azure Front Door) to the nearest deployment, resulting in faster load times than if the application were hosted from a single region on the other side of the world.

---

## 16. Disaster Recovery Concepts

**Disaster Recovery (DR)** is the set of strategies, policies, and tools used to restore access to IT systems and data after a disruptive event — natural disaster, hardware failure, cyberattack, or human error. Where reliability and fault tolerance focus on preventing or absorbing failure, disaster recovery focuses on **what happens after** a major failure has already occurred, and how quickly and completely normal operation can be restored.

**Why DR is distinct from HA/fault tolerance:** High availability and fault tolerance are designed to prevent visible downtime from smaller-scale failures (e.g., one VM instance crashing). Disaster recovery addresses larger-scale catastrophic events (e.g., an entire region becoming unavailable) where some level of downtime or data loss may be unavoidable, and the goal shifts to minimizing and recovering from that impact as fast as possible.

---

## 17. RTO and RPO

These two metrics define the acceptable limits of downtime and data loss in a disaster recovery plan, and are central to designing any DR strategy.

### 17.1 Recovery Time Objective (RTO)
The **maximum acceptable length of time** a system can be down after a disaster before it must be restored. It answers the question: "How long can we afford to be offline?"

### 17.2 Recovery Point Objective (RPO)
The **maximum acceptable amount of data loss**, measured as a period of time. It answers the question: "How much recent data can we afford to lose?" — determined by how frequently data is backed up or replicated.

**Example:**
An organization sets an RTO of 4 hours and an RPO of 1 hour for its order management system.
- RTO of 4 hours means the system must be fully operational again within 4 hours of a disaster being declared.
- RPO of 1 hour means data must be backed up/replicated at least every hour, so that in the worst case, only the last hour of transactions could be lost.

If this same organization instead required near-zero data loss (RPO of a few minutes) and near-instant recovery (RTO of a few minutes), it would need continuous or near-continuous data replication to a secondary region, at significantly higher cost — illustrating that lower RTO/RPO targets generally mean higher cost and complexity.

---

## 18. Azure Site Recovery

**Azure Site Recovery (ASR)** is Microsoft's dedicated disaster recovery service, used to keep applications running and reachable during outages by continuously replicating workloads (typically virtual machines) from a primary location to a secondary location.

**How it works:**
- ASR continuously replicates VMs and their disks from a primary Azure region (or on-premises datacenter) to a secondary Azure region.
- In the event of an outage in the primary location, ASR performs a **failover**, bringing up the replicated VMs in the secondary region so the application continues running with minimal interruption.
- Once the primary location is restored, ASR can perform a **failback**, moving operations back to the original location.
- ASR supports orchestrated recovery plans, allowing multiple VMs and dependent resources to fail over together in a defined sequence, rather than individually.

**Relationship to RTO/RPO:**
- The frequency of replication configured in ASR directly determines the achievable RPO — more frequent replication means less potential data loss.
- The speed and automation of the failover process determines the achievable RTO — a well-orchestrated ASR recovery plan reduces the time needed to bring systems back online.

**Example:**
A company hosts its critical inventory management VMs in the East US region. It configures Azure Site Recovery to continuously replicate these VMs to the West US region. When a major outage affects East US, the company triggers a failover through ASR, and the inventory system becomes available from West US within minutes — meeting its predefined RTO — while ASR's continuous replication ensures only a few minutes of data are at risk, meeting its predefined RPO. Once East US is restored, the company uses failback to move operations home.

---

## Unit 1 Summary (Quick Revision)

- **Cloud Fundamentals:** On-demand, internet-delivered compute/storage/networking, replacing owned physical infrastructure.
- **CapEx vs OpEx:** Cloud shifts spending from large upfront investment (CapEx) to ongoing, usage-based spending (OpEx).
- **Benefits:** HA, Scalability, Elasticity, Reliability, Fault Tolerance, Agility, Global Reach — each a distinct concept, covered individually.
- **Economies of Scale:** Massive provider scale lowers per-unit cost, enabling cheaper consumption-based pricing.
- **Shared Responsibility Model:** Customer always owns data/identity; provider always owns physical infrastructure; the middle layers shift by service model.
- **Deployment Models:** Public (shared, provider-owned), Private (dedicated, single organization), Hybrid (mix, connected).
- **Service Models:** IaaS (most customer control/effort) → PaaS (provider manages OS/runtime) → SaaS (provider manages almost everything).
- **Consumption-Based Pricing:** Pay only for metered, actual usage; no cost for unused or deallocated resources.
- **HA:** Minimal downtime, measured via SLA uptime percentage.
- **Scalability:** Capability to add/remove resources (vertical or horizontal), manual or automatic.
- **Elasticity:** Automatic scaling in real time based on live demand (Azure Autoscale).
- **Reliability:** Ability to recover from failure and keep functioning correctly (redundancy, backups).
- **Fault Tolerance:** Continues operating despite a component failure (Availability Zones, replication, load balancing).
- **Agility:** Speed of provisioning/changing resources compared to traditional procurement.
- **Global Reach:** Deploying closer to users worldwide across Azure regions for lower latency.
- **Disaster Recovery:** Restoring operations after a catastrophic event; distinct from HA/fault tolerance, which handle smaller-scale failures.
- **RTO/RPO:** RTO = maximum acceptable downtime; RPO = maximum acceptable data loss (time-based).
- **Azure Site Recovery:** Microsoft's DR service — continuous replication, failover, and failback between primary and secondary locations, directly determining achievable RTO/RPO.

---

## Practice Questions (Self-Check)

1. Explain, with an example, why cloud computing is described as converting CapEx into OpEx.
2. What is the difference between economies of scale and consumption-based pricing? How are they related?
3. In the Shared Responsibility Model, which two areas remain the customer's responsibility no matter which service model is used?
4. A bank must keep customer records on-premises for regulatory reasons but wants to run its customer app in the cloud. Which deployment model fits, and why?
5. Distinguish between scalability and elasticity using a real-world example for each.
6. What is the difference between reliability and fault tolerance? Can a system be fault tolerant but not reliable, or vice versa?
7. Define RTO and RPO. If an organization has a very low tolerance for data loss, which metric does that primarily affect, and how would Azure Site Recovery's configuration reflect that?
8. Explain how Azure Site Recovery achieves both failover and failback, and how these relate to disaster recovery as opposed to high availability.

*(Answers to be discussed in class / covered in practical session mapped to Experiment 1 and Experiment 2.)*