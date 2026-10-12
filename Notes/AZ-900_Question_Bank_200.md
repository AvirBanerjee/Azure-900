# AZ-900: Microsoft Azure Fundamentals
## Certification Practice Question Bank

**Total Questions:** 207  
**Coverage:** Unit 1 (70) | Unit 2 (66) | Unit 3 (71)  
**Format:** Each question lists its source Unit and Topic/Section number from the course notes, so it can be traced back to exactly where it was taught.

---

## Table of Contents

### Unit 1
- Topic 1 — Cloud Fundamentals (4 questions: Q1–Q4)
- Topic 2 — CapEx vs OpEx (5 questions: Q5–Q9)
- Topic 3 — Benefits of Cloud Services (2 questions: Q10–Q11)
- Topic 4 — Economies of Scale (3 questions: Q12–Q14)
- Topic 5 — Shared Responsibility Model (5 questions: Q15–Q19)
- Topic 6 — Cloud Deployment Models (7 questions: Q20–Q26)
- Topic 7 — Service Models (IaaS/PaaS/SaaS) (8 questions: Q27–Q34)
- Topic 8 — Consumption-Based Pricing (4 questions: Q35–Q38)
- Topic 9 — High Availability (4 questions: Q39–Q42)
- Topic 10 — Scalability (4 questions: Q43–Q46)
- Topic 11 — Elasticity (4 questions: Q47–Q50)
- Topic 12 — Reliability (3 questions: Q51–Q53)
- Topic 13 — Fault Tolerance (3 questions: Q54–Q56)
- Topic 14 — Agility (2 questions: Q57–Q58)
- Topic 15 — Global Reach (2 questions: Q59–Q60)
- Topic 16 — Disaster Recovery Concepts (3 questions: Q61–Q63)
- Topic 17 — RTO and RPO (4 questions: Q64–Q67)
- Topic 18 — Azure Site Recovery (3 questions: Q68–Q70)
### Unit 2
- Topic 1 — Datacenters (2 questions: Q71–Q72)
- Topic 2 — Azure Regions (1 questions: Q73–Q73)
- Topic 2.1 — Region Pairs (3 questions: Q74–Q76)
- Topic 2.2 — Sovereign Regions (1 questions: Q77–Q77)
- Topic 3 — Availability Zones (4 questions: Q78–Q81)
- Topic 3.1 — Availability Sets (4 questions: Q82–Q85)
- Topic 4 — Resources and Resource Groups (6 questions: Q86–Q91)
- Topic 5 — Subscriptions (4 questions: Q92–Q95)
- Topic 6 — Management Groups (4 questions: Q96–Q99)
- Topic 7 — Resource Hierarchy (4 questions: Q100–Q103)
- Topic 8 — Azure Resource Manager (ARM) (4 questions: Q104–Q107)
- Topic 9 — Azure Compute Services (2 questions: Q108–Q109)
- Topic 10 — Virtual Machines (3 questions: Q110–Q112)
- Topic 10.1 — VM Scale Sets (4 questions: Q113–Q116)
- Topic 11 — App Services (4 questions: Q117–Q120)
- Topic 12 — Containers Overview (5 questions: Q121–Q125)
- Topic 13 — Azure Functions (Serverless) (4 questions: Q126–Q129)
- Topic 14 — Azure Virtual Desktop (2 questions: Q130–Q131)
- Topic 15 — Application Hosting Decision Framework (5 questions: Q132–Q136)
### Unit 3
- Topic 1 — Virtual Networks and Subnets (3 questions: Q137–Q139)
- Topic 1.2 — VNet Peering (3 questions: Q140–Q142)
- Topic 2 — VPN Gateway (2 questions: Q143–Q144)
- Topic 3 — ExpressRoute (3 questions: Q145–Q147)
- Topic 4 — Load Balancer (2 questions: Q148–Q149)
- Topic 4.1 — Application Gateway (3 questions: Q150–Q152)
- Topic 5 — Network Security Groups (NSGs) (4 questions: Q153–Q156)
- Topic 6 — Azure DNS (2 questions: Q157–Q158)
- Topic 6.1 — Azure Firewall (2 questions: Q159–Q160)
- Topic 7 — Azure Storage Types (5 questions: Q161–Q165)
- Topic 7.1 — Blob Access Tiers (4 questions: Q166–Q169)
- Topic 8 — Storage Redundancy (6 questions: Q170–Q175)
- Topic 9 — Storage Migration and Management Tools (4 questions: Q176–Q179)
- Topic 10 — Azure SQL Database (3 questions: Q180–Q182)
- Topic 11 — Cosmos DB Overview (3 questions: Q183–Q185)
- Topic 11.1 — Other Azure Database Services (1 questions: Q186–Q186)
- Topic 12 — Microsoft Entra ID (2 questions: Q187–Q188)
- Topic 12.1 — Single Sign-On (SSO) (2 questions: Q189–Q190)
- Topic 12.2 — Hybrid Identity (Microsoft Entra Connect) (2 questions: Q191–Q192)
- Topic 12.3 — External Identities (B2B/B2C) (3 questions: Q193–Q195)
- Topic 13 — Authentication Methods (3 questions: Q196–Q198)
- Topic 13.3 — Passwordless Authentication (3 questions: Q199–Q201)
- Topic 14 — Role-Based Access Control (RBAC) (6 questions: Q202–Q207)

---

# Unit 1

## Topic 1 — Cloud Fundamentals

**Q1.** Which characteristic of cloud computing allows a user to provision a virtual machine without contacting a human administrator?

- **A.** Resource pooling
- **B.** On-demand self-service **(Correct)**
- **C.** Measured service
- **D.** Broad network access

**Answer:** B — On-demand self-service  
**Explanation:** On-demand self-service means a customer can provision resources like VMs or storage automatically through a portal or API, without needing a human to approve or set it up manually.

---

**Q2.** A provider's physical resources are dynamically assigned to serve multiple customers at once. Which cloud characteristic does this describe?

- **A.** Rapid elasticity
- **B.** Measured service
- **C.** Resource pooling **(Correct)**
- **D.** On-demand self-service

**Answer:** C — Resource pooling  
**Explanation:** Resource pooling refers to the provider's infrastructure serving many customers (multi-tenancy), with resources dynamically assigned and reassigned based on demand.

---

**Q3.** Billing in Azure is based on metered usage of resources. Which core cloud characteristic does this reflect?

- **A.** Measured service **(Correct)**
- **B.** Broad network access
- **C.** Resource pooling
- **D.** On-demand self-service

**Answer:** A — Measured service  
**Explanation:** Measured service means usage is tracked/metered, and the customer is billed according to actual consumption, which is the basis of Azure's consumption-based pricing.

---

**Q4.** A college needs servers only for one week during exams and wants to avoid paying for idle hardware the rest of the year. Which cloud computing principle directly addresses this?

- **A.** Fault tolerance
- **B.** Consumption-based, on-demand provisioning **(Correct)**
- **C.** Global reach
- **D.** Shared responsibility

**Answer:** B — Consumption-based, on-demand provisioning  
**Explanation:** Cloud computing's on-demand, consumption-based model lets the college provision resources only for the week it needs them and stop paying once resources are deallocated, unlike owning hardware year-round.

---

## Topic 2 — CapEx vs OpEx

**Q5.** Which type of spending involves a large upfront investment in physical hardware that depreciates over time?

- **A.** Operational Expenditure (OpEx)
- **B.** Capital Expenditure (CapEx) **(Correct)**
- **C.** Consumption-based spending
- **D.** Elastic spending

**Answer:** B — Capital Expenditure (CapEx)  
**Explanation:** CapEx refers to upfront investment in physical assets such as servers, which are then treated as depreciating assets over several years.

---

**Q6.** A company moves from purchasing its own servers to paying a monthly Azure bill based on usage. This is a shift from:

- **A.** OpEx to CapEx
- **B.** CapEx to OpEx **(Correct)**
- **C.** Public cloud to private cloud
- **D.** PaaS to IaaS

**Answer:** B — CapEx to OpEx  
**Explanation:** Moving from owning hardware (CapEx) to an ongoing, pay-as-you-go cloud bill (OpEx) is the classic CapEx-to-OpEx shift cloud computing enables.

---

**Q7.** Which of the following is a disadvantage of the CapEx model compared to OpEx?

- **A.** It requires accurate long-term capacity forecasting before spending **(Correct)**
- **B.** It allows spending to be adjusted immediately with demand
- **C.** It avoids large upfront costs
- **D.** It is billed only for actual usage

**Answer:** A — It requires accurate long-term capacity forecasting before spending  
**Explanation:** Under CapEx, an organization must forecast future capacity needs before buying hardware; overestimating wastes money and underestimating limits growth, unlike OpEx's flexible, demand-driven spending.

---

**Q8.** A retail company scales up Azure VM instances only during a festival sale and scales back down afterward, paying only for that period. This billing approach is an example of:

- **A.** CapEx
- **B.** OpEx / consumption-based pricing **(Correct)**
- **C.** Private cloud pricing
- **D.** Fixed-cost pricing

**Answer:** B — OpEx / consumption-based pricing  
**Explanation:** Paying only for the increased usage during the sale period and nothing extra afterward is the defining feature of OpEx / consumption-based pricing.

---

**Q9.** In financial terms, how is cloud spending typically treated on a company's books compared to on-premises hardware purchases?

- **A.** As a depreciating long-term asset, same as hardware
- **B.** As a regular ongoing operating expense **(Correct)**
- **C.** As a one-time capital investment
- **D.** As an intangible asset only

**Answer:** B — As a regular ongoing operating expense  
**Explanation:** Cloud spending is typically treated as an ongoing operational expense (OpEx), rather than a long-term depreciating capital asset like purchased hardware (CapEx).

---

## Topic 3 — Benefits of Cloud Services

**Q10.** Which of the following is NOT typically listed as a core benefit of cloud computing in AZ-900?

- **A.** High Availability
- **B.** Elasticity
- **C.** Manual capacity planning **(Correct)**
- **D.** Agility

**Answer:** C — Manual capacity planning  
**Explanation:** Manual capacity planning is a drawback of traditional on-premises IT, not a cloud benefit. Cloud benefits include HA, elasticity, agility, scalability, reliability, fault tolerance, and global reach.

---

**Q11.** A company wants its application to remain accessible with minimal downtime. Which benefit are they primarily targeting?

- **A.** Global Reach
- **B.** High Availability **(Correct)**
- **C.** Economies of Scale
- **D.** CapEx reduction

**Answer:** B — High Availability  
**Explanation:** High Availability is specifically the benefit concerned with keeping a system accessible and operational with minimal downtime.

---

## Topic 4 — Economies of Scale

**Q12.** Why can Azure generally offer lower per-unit compute costs than a typical organization running its own datacenter?

- **A.** Because Azure uses cheaper, lower-quality hardware
- **B.** Because of economies of scale across millions of customers **(Correct)**
- **C.** Because Azure does not pay for electricity
- **D.** Because Azure only serves large enterprises

**Answer:** B — Because of economies of scale across millions of customers  
**Explanation:** Economies of scale means Azure's massive, shared infrastructure spreads fixed costs (power, cooling, hardware, staff) across millions of customers, lowering the cost per unit of compute far below what a single organization could achieve alone.

---

**Q13.** Economies of scale is best described as:

- **A.** The cost per unit decreasing as the scale of operation increases **(Correct)**
- **B.** The automatic scaling of VM instances with demand
- **C.** A pricing model based only on storage usage
- **D.** A security model for the cloud

**Answer:** A — The cost per unit decreasing as the scale of operation increases  
**Explanation:** Economies of scale is an economic principle: as a provider's scale increases, the fixed costs are spread over more customers, reducing the cost per unit of service.

---

**Q14.** How does economies of scale relate to Azure's consumption-based pricing?

- **A.** They are unrelated concepts
- **B.** Economies of scale is what allows Azure to offer lower consumption-based prices **(Correct)**
- **C.** Consumption-based pricing eliminates the need for economies of scale
- **D.** Economies of scale only applies to private cloud

**Answer:** B — Economies of scale is what allows Azure to offer lower consumption-based prices  
**Explanation:** Economies of scale lowers Azure's own per-unit costs, which is part of why Azure can pass on lower prices to customers through its consumption-based, pay-as-you-go pricing model.

---

## Topic 5 — Shared Responsibility Model

**Q15.** In the Shared Responsibility Model, which of the following is ALWAYS the customer's responsibility, regardless of service model?

- **A.** Physical datacenter security
- **B.** Data and identity/access management **(Correct)**
- **C.** Physical network hardware
- **D.** Physical host maintenance

**Answer:** B — Data and identity/access management  
**Explanation:** Regardless of whether the service is IaaS, PaaS, or SaaS, the customer always retains responsibility for their data, accounts, and identity/access management.

---

**Q16.** Which layer of responsibility is ALWAYS owned by the cloud provider, no matter the service model used?

- **A.** Applications
- **B.** Operating system
- **C.** Physical datacenter **(Correct)**
- **D.** Data classification

**Answer:** C — Physical datacenter  
**Explanation:** The physical datacenter, physical network, and physical hosts are always managed by Microsoft (the provider) across IaaS, PaaS, and SaaS.

---

**Q17.** A company stores data in Azure SQL Database (PaaS) and suffers a breach because an employee used a weak, reused password. Who is responsible for this failure?

- **A.** Microsoft, because it is a PaaS service
- **B.** The customer, because identity and access management is always a customer responsibility **(Correct)**
- **C.** Neither party is responsible
- **D.** Microsoft Support team

**Answer:** B — The customer, because identity and access management is always a customer responsibility  
**Explanation:** Even in PaaS, where Microsoft manages the database engine and patching, the customer always retains responsibility for identity and access management, including password policies.

---

**Q18.** As an organization moves from IaaS to SaaS, what generally happens to its share of management responsibility?

- **A.** It increases
- **B.** It stays exactly the same
- **C.** It decreases **(Correct)**
- **D.** It becomes zero in all cases

**Answer:** C — It decreases  
**Explanation:** Moving from IaaS towards SaaS shifts more of the management burden (OS, runtime, and eventually the application itself) onto the provider, decreasing the customer's responsibility.

---

**Q19.** Which of these is an example of a responsibility that shifts depending on the service model (IaaS vs PaaS vs SaaS), rather than always belonging to one party?

- **A.** Data classification
- **B.** Operating system patching **(Correct)**
- **C.** Physical security of the datacenter
- **D.** User identity

**Answer:** B — Operating system patching  
**Explanation:** OS patching is the customer's job under IaaS but becomes the provider's job under PaaS and SaaS — this is a 'shifting' responsibility, unlike data/identity (always customer) or physical infrastructure (always provider).

---

## Topic 6 — Cloud Deployment Models

**Q20.** A startup hosts its website on Azure App Service, sharing underlying hardware with other Azure customers while its data remains isolated. Which deployment model is this?

- **A.** Private cloud
- **B.** Hybrid cloud
- **C.** Public cloud **(Correct)**
- **D.** Community cloud

**Answer:** C — Public cloud  
**Explanation:** Public cloud resources are owned by the provider and shared (multi-tenant) among many customers, with each customer's data logically isolated — exactly describing this startup's App Service scenario.

---

**Q21.** A government defense agency runs its own cloud infrastructure in a secured facility not shared with any other organization. Which deployment model is this?

- **A.** Public cloud
- **B.** Private cloud **(Correct)**
- **C.** Hybrid cloud
- **D.** Multi-cloud

**Answer:** B — Private cloud  
**Explanation:** A private cloud is dedicated entirely to a single organization, whether hosted on-premises or by a third party, and is never shared with other organizations — fitting the agency's requirement.

---

**Q22.** A bank keeps customer records on-premises for regulatory reasons but runs its mobile banking app on Azure public cloud, connecting the two via a secure link. Which deployment model is this?

- **A.** Public cloud
- **B.** Private cloud
- **C.** Hybrid cloud **(Correct)**
- **D.** Sovereign cloud

**Answer:** C — Hybrid cloud  
**Explanation:** Hybrid cloud combines public and private cloud with data/applications able to move between the two through a secure connection — exactly matching the bank's mixed setup.

---

**Q23.** Which deployment model generally offers the LEAST control but the LOWEST cost due to shared economies of scale?

- **A.** Private cloud
- **B.** Hybrid cloud
- **C.** Public cloud **(Correct)**
- **D.** On-premises

**Answer:** C — Public cloud  
**Explanation:** Public cloud resources are shared among many customers (multi-tenant), which lowers cost through economies of scale, but gives the customer less control over the underlying infrastructure compared to private cloud.

---

**Q24.** Which deployment model is typically most suited to regulated industries needing full control over security and compliance posture?

- **A.** Public cloud
- **B.** Private cloud **(Correct)**
- **C.** Community cloud
- **D.** None of the above

**Answer:** B — Private cloud  
**Explanation:** Private cloud gives an organization full control and dedicated infrastructure, making it well suited for regulated industries with strict security and compliance requirements.

---

**Q25.** What is a key architectural complexity typically associated with hybrid cloud compared to public or private cloud alone?

- **A.** There is no added complexity
- **B.** Coordinating networking, identity, and data across two separate environments **(Correct)**
- **C.** Hybrid cloud cannot use any public cloud services
- **D.** Hybrid cloud has no cost benefit at all

**Answer:** B — Coordinating networking, identity, and data across two separate environments  
**Explanation:** Hybrid cloud requires coordinating networking, identity, and data consistency between the on-premises/private environment and the public cloud environment, adding architectural complexity not present in a single-model deployment.

---

**Q26.** Which statement about public cloud is TRUE?

- **A.** Only one customer at a time is served by the physical hardware
- **B.** Multiple customers share the same physical hardware, but data is logically isolated **(Correct)**
- **C.** It requires customers to own the physical datacenter
- **D.** It is always more expensive than private cloud

**Answer:** B — Multiple customers share the same physical hardware, but data is logically isolated  
**Explanation:** Public cloud is multi-tenant: many customers share underlying physical hardware, but each customer's data remains logically isolated and inaccessible to others.

---

## Topic 7 — Service Models (IaaS/PaaS/SaaS)

**Q27.** A company migrates a legacy Windows Server application 'as-is' to Azure Virtual Machines, retaining responsibility for OS patching. Which service model is this?

- **A.** SaaS
- **B.** PaaS
- **C.** IaaS **(Correct)**
- **D.** FaaS

**Answer:** C — IaaS  
**Explanation:** IaaS provides the basic building blocks (VMs, storage, networking); the customer manages everything from the OS upward, including patching — matching the 'as-is' migration scenario.

---

**Q28.** A development team deploys code to Azure App Service, and Azure automatically handles OS patching and server maintenance. Which service model is this?

- **A.** IaaS
- **B.** PaaS **(Correct)**
- **C.** SaaS
- **D.** On-premises

**Answer:** B — PaaS  
**Explanation:** PaaS means the provider manages the underlying infrastructure and OS, while the customer focuses only on deploying and managing the application and its data — matching the App Service scenario.

---

**Q29.** An organization uses Microsoft 365 for email and document collaboration, managing only user accounts and data. Which service model is this?

- **A.** IaaS
- **B.** PaaS
- **C.** SaaS **(Correct)**
- **D.** CaaS

**Answer:** C — SaaS  
**Explanation:** SaaS means the provider manages nearly the entire stack, including the application itself; the customer only manages data and user access — exactly describing Microsoft 365 usage.

---

**Q30.** In which service model does the customer retain the MOST management responsibility?

- **A.** SaaS
- **B.** PaaS
- **C.** IaaS **(Correct)**
- **D.** None — responsibility is equal across all three

**Answer:** C — IaaS  
**Explanation:** IaaS gives maximum flexibility but also maximum responsibility, since the customer manages the OS, runtime, applications, and data, with the provider only managing the physical infrastructure and virtualization.

---

**Q31.** Who is responsible for patching the operating system under the PaaS model?

- **A.** The customer
- **B.** The provider (Microsoft) **(Correct)**
- **C.** Both equally
- **D.** Neither — PaaS has no operating system

**Answer:** B — The provider (Microsoft)  
**Explanation:** Under PaaS, the provider manages the underlying infrastructure and operating system, including patching, so the customer can focus purely on application code and data.

---

**Q32.** A team wants to deploy application code without managing servers or applying OS patches, but still wants to control the application itself. Which service model fits best?

- **A.** IaaS
- **B.** PaaS **(Correct)**
- **C.** SaaS
- **D.** None of these

**Answer:** B — PaaS  
**Explanation:** PaaS is the correct fit: the provider manages servers/OS, while the customer retains control over the application code and data, without needing SaaS-level complete hand-off of the application.

---

**Q33.** Which layer of the technology stack is the customer responsible for in ALL THREE service models (IaaS, PaaS, and SaaS)?

- **A.** Operating system
- **B.** Runtime
- **C.** Data **(Correct)**
- **D.** Virtualization

**Answer:** C — Data  
**Explanation:** Data is always the customer's responsibility across IaaS, PaaS, and SaaS, consistent with the Shared Responsibility Model.

---

**Q34.** Which of these correctly orders the service models from MOST customer control to LEAST customer control?

- **A.** SaaS > PaaS > IaaS
- **B.** IaaS > PaaS > SaaS **(Correct)**
- **C.** PaaS > IaaS > SaaS
- **D.** All three offer equal control

**Answer:** B — IaaS > PaaS > SaaS  
**Explanation:** IaaS offers the most customer control (manages OS upward), PaaS less (manages app/data only), and SaaS the least (manages only data/access) — so the order from most to least control is IaaS > PaaS > SaaS.

---

## Topic 8 — Consumption-Based Pricing

**Q35.** A company runs a VM only from 9 AM to 6 PM and shuts it down overnight. Under Azure's consumption-based pricing, how is it billed?

- **A.** For 24 hours of usage regardless of shutdown
- **B.** Only for the 9 hours the VM actually ran **(Correct)**
- **C.** A flat monthly fee regardless of usage
- **D.** Nothing, because VMs are always free when off

**Answer:** B — Only for the 9 hours the VM actually ran  
**Explanation:** Consumption-based pricing meters actual usage, so the company is billed only for the hours the VM was actually running, not for the full day.

---

**Q36.** Which of these is a key characteristic of Azure's consumption-based pricing model?

- **A.** A large upfront payment is required before provisioning any resource
- **B.** Billing is metered based on actual resource usage **(Correct)**
- **C.** All services are billed at a single flat global rate
- **D.** Costs cannot be reduced once a resource is provisioned

**Answer:** B — Billing is metered based on actual resource usage  
**Explanation:** Consumption-based pricing meters usage (compute hours, GB stored, data transferred) and bills based on what was actually consumed.

---

**Q37.** What happens to billing when an Azure VM is deleted or deallocated?

- **A.** Charges continue indefinitely
- **B.** Compute charges for that resource stop accruing **(Correct)**
- **C.** The customer is charged a cancellation fee
- **D.** Billing doubles for the final month

**Answer:** B — Compute charges for that resource stop accruing  
**Explanation:** Once a resource like a VM is deleted or deallocated, Azure stops charging for the compute resource, which is a key advantage of consumption-based pricing over owning fixed hardware.

---

**Q38.** Compared to traditional IT procurement, what is a major advantage of Azure's consumption-based pricing?

- **A.** It removes the need to estimate long-term capacity in advance **(Correct)**
- **B.** It requires higher upfront investment
- **C.** It guarantees the lowest possible fixed price
- **D.** It eliminates all operational costs

**Answer:** A — It removes the need to estimate long-term capacity in advance  
**Explanation:** Because billing is tied to actual usage rather than pre-purchased capacity, organizations do not need to accurately forecast long-term capacity needs years in advance, unlike traditional procurement.

---

## Topic 9 — High Availability

**Q39.** High Availability is typically measured using which of the following?

- **A.** RTO (Recovery Time Objective)
- **B.** SLA uptime percentage **(Correct)**
- **C.** RPO (Recovery Point Objective)
- **D.** Fault domain count

**Answer:** B — SLA uptime percentage  
**Explanation:** High Availability design targets are typically expressed and measured as an SLA uptime percentage (e.g., 99.9%), published by Microsoft for many Azure services.

---

**Q40.** A hospital portal is deployed across two Availability Zones so that a power failure in one zone does not interrupt service. This primarily demonstrates:

- **A.** Economies of scale
- **B.** High Availability **(Correct)**
- **C.** CapEx reduction
- **D.** Consumption-based pricing

**Answer:** B — High Availability  
**Explanation:** Keeping the system accessible with minimal downtime despite a zone failure is the defining goal of High Availability.

---

**Q41.** Which Azure feature directly supports High Availability by distributing traffic across multiple healthy instances?

- **A.** Azure Firewall
- **B.** Load balancing **(Correct)**
- **C.** Azure Site Recovery
- **D.** Azure Data Box

**Answer:** B — Load balancing  
**Explanation:** Load balancing distributes incoming traffic across multiple instances, so a single instance failure does not cause an outage, directly supporting High Availability.

---

**Q42.** What does a published Azure SLA of '99.9% availability' represent?

- **A.** The maximum acceptable data loss
- **B.** A guaranteed uptime percentage target for a service **(Correct)**
- **C.** The number of regions a service spans
- **D.** The number of fault domains in a datacenter

**Answer:** B — A guaranteed uptime percentage target for a service  
**Explanation:** An SLA uptime percentage like 99.9% is Microsoft's guaranteed uptime commitment for a given service, used as the benchmark for High Availability design.

---

## Topic 10 — Scalability

**Q43.** An administrator manually upgrades a VM from a 2-core size to an 8-core size to handle more load. This is an example of:

- **A.** Horizontal scaling (scaling out)
- **B.** Vertical scaling (scaling up) **(Correct)**
- **C.** Elasticity
- **D.** Fault tolerance

**Answer:** B — Vertical scaling (scaling up)  
**Explanation:** Increasing the power (CPU/RAM) of an existing single resource is vertical scaling, also called 'scaling up.'

---

**Q44.** Adding more VM instances behind a load balancer to handle increased traffic is an example of:

- **A.** Vertical scaling (scaling up)
- **B.** Horizontal scaling (scaling out) **(Correct)**
- **C.** Reliability
- **D.** Global reach

**Answer:** B — Horizontal scaling (scaling out)  
**Explanation:** Increasing the NUMBER of resource instances is horizontal scaling, also called 'scaling out.'

---

**Q45.** Scalability is best defined as:

- **A.** The automatic, real-time adjustment of resources based on demand
- **B.** The capability of a system to handle increased or decreased load by adjusting resources, manually or automatically **(Correct)**
- **C.** A guarantee of zero downtime
- **D.** A specific Azure region feature

**Answer:** B — The capability of a system to handle increased or decreased load by adjusting resources, manually or automatically  
**Explanation:** Scalability describes the capability of a system to be scaled — it does not have to be automatic; it could be manually triggered or automated.

---

**Q46.** A food delivery platform's administrator manually adds three extra web servers before dinner rush and removes them after. Is this scalability, elasticity, or both?

- **A.** Only elasticity, since resources changed
- **B.** Only scalability, since a human triggered the change **(Correct)**
- **C.** Neither concept applies
- **D.** Both are irrelevant here; this is fault tolerance

**Answer:** B — Only scalability, since a human triggered the change  
**Explanation:** Because a human manually triggered the change rather than it happening automatically in response to live metrics, this demonstrates scalability (the capability to scale) rather than elasticity (automatic scaling).

---

## Topic 11 — Elasticity

**Q47.** What is the key distinguishing feature of elasticity compared to scalability?

- **A.** Elasticity only applies to storage, not compute
- **B.** Elasticity happens automatically in real time based on demand, without manual intervention **(Correct)**
- **C.** Elasticity always reduces cost to zero
- **D.** Elasticity requires a private cloud deployment

**Answer:** B — Elasticity happens automatically in real time based on demand, without manual intervention  
**Explanation:** Elasticity is specifically the AUTOMATIC scaling of resources in real time based on live demand, distinguishing it from scalability, which is simply the capability to scale (manual or automatic).

---

**Q48.** Which Azure feature automatically adds or removes VM instances based on defined metrics like CPU usage?

- **A.** Azure Autoscale **(Correct)**
- **B.** Azure Site Recovery
- **C.** Azure Firewall
- **D.** Azure Data Box

**Answer:** A — Azure Autoscale  
**Explanation:** Azure Autoscale is the feature that automatically scales resources (such as VM Scale Set instances) up or down based on metrics like CPU usage, directly implementing elasticity.

---

**Q49.** A ticket-booking site configures autoscale to add instances automatically above 70% CPU and remove them below 30% CPU, with no human involvement. This demonstrates:

- **A.** Scalability only
- **B.** Elasticity **(Correct)**
- **C.** Fault tolerance only
- **D.** Global reach

**Answer:** B — Elasticity  
**Explanation:** Because the scaling happens automatically in response to live demand without manual intervention, this is elasticity (which also demonstrates the underlying scalability capability).

---

**Q50.** During a sudden traffic spike, a system automatically provisions new instances within minutes and later scales back down overnight to save cost. What capability is this?

- **A.** Elasticity **(Correct)**
- **B.** Fault tolerance
- **C.** Global reach
- **D.** Economies of scale

**Answer:** A — Elasticity  
**Explanation:** Automatic, demand-driven scaling both up and down, without manual action, is the definition of elasticity.

---

## Topic 12 — Reliability

**Q51.** Reliability in cloud computing is best described as:

- **A.** The ability of a system to recover from failures and continue functioning correctly over time **(Correct)**
- **B.** The percentage of uptime guaranteed by an SLA
- **C.** The number of Availability Zones in a region
- **D.** The cost savings from using cloud over on-premises

**Answer:** A — The ability of a system to recover from failures and continue functioning correctly over time  
**Explanation:** Reliability focuses on a system's ability to recover from failure and continue correct operation over time, going beyond just uptime percentage.

---

**Q52.** An application uses geo-redundant storage so that if the primary region fails, data is still accessible from a secondary region. This demonstrates:

- **A.** Agility
- **B.** Reliability **(Correct)**
- **C.** Economies of scale
- **D.** CapEx

**Answer:** B — Reliability  
**Explanation:** The ability to recover and continue functioning (accessing data) after a regional failure, through built-in redundancy, is a demonstration of reliability.

---

**Q53.** Which of the following mechanisms primarily supports reliability?

- **A.** Redundancy and automated health monitoring with self-healing **(Correct)**
- **B.** A lower subscription cost
- **C.** A larger number of resource groups
- **D.** Manual capacity forecasting

**Answer:** A — Redundancy and automated health monitoring with self-healing  
**Explanation:** Reliability is supported by redundancy (duplicate copies of data/services) and automated health monitoring that can detect and replace unhealthy instances automatically.

---

## Topic 13 — Fault Tolerance

**Q54.** A payment-processing service runs three instances behind a load balancer. One instance crashes, and the load balancer automatically redirects traffic to the remaining two with no visible disruption. This demonstrates:

- **A.** Fault tolerance **(Correct)**
- **B.** Global reach
- **C.** Agility
- **D.** CapEx reduction

**Answer:** A — Fault tolerance  
**Explanation:** Continuing to operate correctly despite a component failure, without a full service interruption, is the definition of fault tolerance.

---

**Q55.** Which Azure feature contributes directly to fault tolerance by protecting against datacenter-level failure?

- **A.** Azure Functions
- **B.** Availability Zones **(Correct)**
- **C.** Azure DNS
- **D.** Azure Virtual Desktop

**Answer:** B — Availability Zones  
**Explanation:** Availability Zones, as physically separate locations with independent power/cooling within a region, protect against a full datacenter failure, directly contributing to fault tolerance.

---

**Q56.** How does fault tolerance differ from high availability?

- **A.** They are identical concepts with no difference
- **B.** Fault tolerance is a specific mechanism (continuing to operate despite component failure) that contributes to the broader goal of high availability **(Correct)**
- **C.** High availability only applies to storage, fault tolerance only to compute
- **D.** Fault tolerance guarantees zero cost

**Answer:** B — Fault tolerance is a specific mechanism (continuing to operate despite component failure) that contributes to the broader goal of high availability  
**Explanation:** Fault tolerance is a specific mechanism — the system keeps running despite a component failing — that is one of the ways high availability (minimal downtime) is actually achieved.

---

## Topic 14 — Agility

**Q57.** A developer provisions a full test environment in under an hour and deletes it once testing is complete, incurring no further cost. This demonstrates:

- **A.** Agility **(Correct)**
- **B.** Global reach
- **C.** Shared responsibility
- **D.** Economies of scale

**Answer:** A — Agility  
**Explanation:** Agility refers to the speed and flexibility of provisioning, modifying, and decommissioning resources, compared to slow traditional procurement cycles — exactly matching this scenario.

---

**Q58.** Compared to traditional on-premises procurement, cloud agility primarily provides which business benefit?

- **A.** Guaranteed zero downtime
- **B.** Faster experimentation and iteration due to reduced time/cost barriers **(Correct)**
- **C.** Elimination of all security responsibilities
- **D.** Mandatory use of a single region

**Answer:** B — Faster experimentation and iteration due to reduced time/cost barriers  
**Explanation:** Because resources can be provisioned and removed quickly and cheaply, organizations can experiment and iterate faster than they could under slow, costly traditional procurement.

---

## Topic 15 — Global Reach

**Q59.** A company deploys its app in both East US and Central India, routing users to the nearest deployment. Which benefit does this illustrate?

- **A.** Global Reach **(Correct)**
- **B.** CapEx
- **C.** Shared Responsibility
- **D.** Fault Tolerance

**Answer:** A — Global Reach  
**Explanation:** Global Reach refers to deploying resources across Microsoft's worldwide regions to place applications physically closer to end users, reducing latency — matching this scenario.

---

**Q60.** Which Azure service is commonly used alongside multi-region deployments to route users to their nearest regional deployment?

- **A.** Azure Traffic Manager / Azure Front Door **(Correct)**
- **B.** Azure Site Recovery
- **C.** Azure Data Box
- **D.** Azure Firewall

**Answer:** A — Azure Traffic Manager / Azure Front Door  
**Explanation:** Azure Traffic Manager and Azure Front Door are used to route users to the nearest or most appropriate regional deployment, supporting global reach.

---

## Topic 16 — Disaster Recovery Concepts

**Q61.** How does disaster recovery differ from high availability and fault tolerance?

- **A.** They are the same thing with different names
- **B.** DR focuses on recovering after large-scale catastrophic failures, while HA/fault tolerance prevent downtime from smaller-scale failures **(Correct)**
- **C.** DR only applies to storage services
- **D.** HA is a subset of DR with no distinct purpose

**Answer:** B — DR focuses on recovering after large-scale catastrophic failures, while HA/fault tolerance prevent downtime from smaller-scale failures  
**Explanation:** HA and fault tolerance are designed to absorb smaller-scale failures without visible downtime; DR addresses larger-scale catastrophic events (e.g., a full region outage) where some downtime or data loss may be unavoidable, focusing on recovery afterward.

---

**Q62.** Which of the following would typically trigger a disaster recovery response rather than routine fault-tolerance handling?

- **A.** A single VM instance crashing behind a load balancer
- **B.** An entire Azure region becoming unavailable **(Correct)**
- **C.** A load balancer routing around one unhealthy instance
- **D.** An Availability Set redistributing a VM reboot

**Answer:** B — An entire Azure region becoming unavailable  
**Explanation:** An entire region becoming unavailable is a large-scale catastrophic event, which is what disaster recovery strategies are specifically designed to address.

---

**Q63.** Disaster Recovery strategies are primarily concerned with:

- **A.** Preventing all possible failures from ever occurring
- **B.** Restoring access to IT systems and data after a disruptive event **(Correct)**
- **C.** Reducing the monthly Azure bill
- **D.** Choosing which deployment model to use

**Answer:** B — Restoring access to IT systems and data after a disruptive event  
**Explanation:** Disaster recovery is the set of strategies, policies, and tools used to restore access to systems and data after a disruptive event has already occurred.

---

## Topic 17 — RTO and RPO

**Q64.** RTO (Recovery Time Objective) refers to:

- **A.** The maximum acceptable amount of data loss, measured in time
- **B.** The maximum acceptable length of time a system can be down after a disaster **(Correct)**
- **C.** The percentage uptime guaranteed by an SLA
- **D.** The number of region pairs used for replication

**Answer:** B — The maximum acceptable length of time a system can be down after a disaster  
**Explanation:** RTO answers 'how long can we afford to be offline' — it is the maximum acceptable downtime after a disaster before the system must be restored.

---

**Q65.** RPO (Recovery Point Objective) refers to:

- **A.** The maximum acceptable length of downtime
- **B.** The maximum acceptable amount of data loss, measured as a period of time **(Correct)**
- **C.** The number of Availability Zones used
- **D.** The cost of a VM instance

**Answer:** B — The maximum acceptable amount of data loss, measured as a period of time  
**Explanation:** RPO answers 'how much recent data can we afford to lose' — determined by how frequently data is backed up or replicated.

---

**Q66.** An organization sets an RPO of 1 hour for its order system. What does this imply about its backup/replication frequency?

- **A.** Data must be backed up or replicated at least every hour **(Correct)**
- **B.** Data can be backed up once a year
- **C.** No backups are needed at all
- **D.** The system must recover within 1 hour

**Answer:** A — Data must be backed up or replicated at least every hour  
**Explanation:** An RPO of 1 hour means the organization can tolerate losing at most 1 hour of data, which requires backups or replication to occur at least that frequently.

---

**Q67.** Which statement about RTO/RPO targets and cost is generally TRUE?

- **A.** Lower RTO/RPO targets (near-zero downtime/data loss) generally cost more to achieve **(Correct)**
- **B.** Lower RTO/RPO targets are always free to achieve
- **C.** RTO and RPO have no relationship to cost
- **D.** Higher RTO/RPO targets always cost more

**Answer:** A — Lower RTO/RPO targets (near-zero downtime/data loss) generally cost more to achieve  
**Explanation:** Near-instant recovery (low RTO) and near-zero data loss (low RPO) typically require continuous or near-continuous replication to a secondary location, which is more expensive than less frequent backup strategies.

---

## Topic 18 — Azure Site Recovery

**Q68.** What is the primary purpose of Azure Site Recovery (ASR)?

- **A.** To provide identity and access management
- **B.** To continuously replicate workloads to a secondary location for disaster recovery failover **(Correct)**
- **C.** To host static websites
- **D.** To monitor billing and cost alerts

**Answer:** B — To continuously replicate workloads to a secondary location for disaster recovery failover  
**Explanation:** Azure Site Recovery is Microsoft's dedicated DR service, continuously replicating VMs/workloads from a primary to a secondary location so they can be failed over during an outage.

---

**Q69.** In Azure Site Recovery terminology, what is 'failback'?

- **A.** The initial replication of a VM to a secondary region
- **B.** Moving operations back to the original (primary) location after it has been restored **(Correct)**
- **C.** Permanently deleting a secondary region's VM copies
- **D.** Switching a Load Balancer to Layer 7 mode

**Answer:** B — Moving operations back to the original (primary) location after it has been restored  
**Explanation:** Failback is the process of moving operations back to the original primary location once it has been restored, after a failover had moved operations to the secondary location.

---

**Q70.** How does the configured replication frequency in Azure Site Recovery relate to RPO?

- **A.** They are unrelated
- **B.** More frequent replication directly lowers (improves) the achievable RPO **(Correct)**
- **C.** More frequent replication always worsens RPO
- **D.** Replication frequency only affects RTO, never RPO

**Answer:** B — More frequent replication directly lowers (improves) the achievable RPO  
**Explanation:** Since RPO is about how much data could be lost, more frequent replication in ASR means less data is at risk at any point, directly improving (lowering) the achievable RPO.

---

# Unit 2

## Topic 1 — Datacenters

**Q71.** What is the smallest physical unit in Azure's global infrastructure hierarchy?

- **A.** Region
- **B.** Datacenter **(Correct)**
- **C.** Availability Zone
- **D.** Resource Group

**Answer:** B — Datacenter  
**Explanation:** A datacenter is the physical facility containing servers, storage, and networking — the smallest physical unit; customers select a region, which is made up of one or more datacenters, not an individual datacenter.

---

**Q72.** Can a customer directly select which individual datacenter their resources are deployed to?

- **A.** Yes, datacenter selection is mandatory during VM creation
- **B.** No, customers select a region; Azure manages the specific datacenter placement **(Correct)**
- **C.** Only for Premium-tier subscriptions
- **D.** Only when using Availability Zones

**Answer:** B — No, customers select a region; Azure manages the specific datacenter placement  
**Explanation:** Customers choose a region during deployment; the specific physical datacenter within that region is managed and determined by Azure, not selected directly by the customer.

---

## Topic 2 — Azure Regions

**Q73.** Why might an organization choose Central India over East US for deploying an application serving mostly Indian users?

- **A.** Central India is always free of cost
- **B.** Deploying closer to users reduces latency **(Correct)**
- **C.** East US does not support virtual machines
- **D.** Region choice has no effect on performance

**Answer:** B — Deploying closer to users reduces latency  
**Explanation:** Deploying in a region geographically closer to the majority of users reduces round-trip network latency, improving application performance — this is the Global Reach principle applied to region selection.

---

## Topic 2.1 — Region Pairs

**Q74.** What is a 'region pair' in Azure?

- **A.** Two regions on opposite sides of the globe with no relationship
- **B.** Two regions within the same geography, typically at least 300 miles apart, linked for DR and staged updates **(Correct)**
- **C.** A pair of Availability Zones within one datacenter
- **D.** Two subscriptions linked for billing

**Answer:** B — Two regions within the same geography, typically at least 300 miles apart, linked for DR and staged updates  
**Explanation:** A region pair consists of two regions within the same geography, at least 300 miles apart, used by Microsoft for disaster recovery prioritization and staggered platform updates.

---

**Q75.** If East US experiences a major disaster, what does its region pairing with West US influence?

- **A.** Microsoft prioritizes restoring service in West US first **(Correct)**
- **B.** Nothing; region pairs have no operational effect
- **C.** All customer data is permanently deleted
- **D.** East US is immediately shut down forever

**Answer:** A — Microsoft prioritizes restoring service in West US first  
**Explanation:** Microsoft uses region pairing to prioritize recovery in the paired region (West US) first when a major disaster affects one region of the pair (East US).

---

**Q76.** Why does Microsoft roll out planned platform updates to only one region in a pair at a time?

- **A.** To reduce electricity costs
- **B.** To reduce the risk of both regions in a pair being affected simultaneously by an update-related issue **(Correct)**
- **C.** Because it is required by law in all countries
- **D.** To increase the price of the paired region

**Answer:** B — To reduce the risk of both regions in a pair being affected simultaneously by an update-related issue  
**Explanation:** Staggering updates across paired regions reduces the risk that an update-related problem affects both regions of a pair at the same time, protecting overall availability.

---

## Topic 2.2 — Sovereign Regions

**Q77.** What characterizes a sovereign or isolated Azure region, such as one used by a national government?

- **A.** It has unlimited free access for all customers
- **B.** It is isolated from the rest of Azure and restricted for specific compliance/national security needs **(Correct)**
- **C.** It is identical to a standard public region with no restrictions
- **D.** It cannot host any compute resources

**Answer:** B — It is isolated from the rest of Azure and restricted for specific compliance/national security needs  
**Explanation:** Sovereign/isolated regions, such as those serving government agencies, are operated separately with restricted access to meet specific regulatory or national security requirements not met by standard public regions.

---

## Topic 3 — Availability Zones

**Q78.** How many Availability Zones does a typical zone-supporting Azure region have at minimum?

- **A.** One
- **B.** Two
- **C.** Three **(Correct)**
- **D.** Five

**Answer:** C — Three  
**Explanation:** Most (though not all) Azure regions that support Availability Zones have a minimum of three physically separate zones, each with independent power, cooling, and networking.

---

**Q79.** Do all Azure regions support Availability Zones?

- **A.** Yes, every region supports them
- **B.** No, not every region supports Availability Zones **(Correct)**
- **C.** Only regions in the United States support them
- **D.** Only Premium subscriptions can use them

**Answer:** B — No, not every region supports Availability Zones  
**Explanation:** Not every Azure region supports Availability Zones, which is an important consideration when choosing a region for an HA-critical workload.

---

**Q80.** What connects the Availability Zones within a single Azure region?

- **A.** The public internet only
- **B.** High-speed, low-latency private fiber connections **(Correct)**
- **C.** Satellite links
- **D.** No connection exists between zones

**Answer:** B — High-speed, low-latency private fiber connections  
**Explanation:** Availability Zones within a region are connected via high-speed, low-latency private fiber connections, enabling fast replication and failover between them.

---

**Q81.** A company deploys VMs across three Availability Zones. A fire affects the datacenter hosting Zone 1. What happens to the application?

- **A.** The entire application goes down
- **B.** Zones 2 and 3 continue serving traffic since each zone has independent power and cooling **(Correct)**
- **C.** All zones fail simultaneously
- **D.** The application must be manually restarted in a different region

**Answer:** B — Zones 2 and 3 continue serving traffic since each zone has independent power and cooling  
**Explanation:** Because each Availability Zone has independent power, cooling, and networking, a failure in one zone does not affect the others, so Zones 2 and 3 continue operating.

---

## Topic 3.1 — Availability Sets

**Q82.** What two things does an Availability Set spread VMs across to protect against localized failure within a single datacenter?

- **A.** Regions and subscriptions
- **B.** Fault domains and update domains **(Correct)**
- **C.** Resource groups and management groups
- **D.** VNets and subnets

**Answer:** B — Fault domains and update domains  
**Explanation:** An Availability Set spreads VMs across fault domains (to protect against rack/hardware failure) and update domains (to avoid all VMs restarting together during planned maintenance).

---

**Q83.** What does a 'fault domain' in an Availability Set protect against?

- **A.** Planned maintenance reboots only
- **B.** A shared point of hardware failure, such as a rack or power source **(Correct)**
- **C.** Regional disasters
- **D.** Billing overruns

**Answer:** B — A shared point of hardware failure, such as a rack or power source  
**Explanation:** A fault domain groups hardware that shares a single point of failure (like a rack or power source); spreading VMs across fault domains ensures one hardware failure does not take down every VM.

---

**Q84.** What is the purpose of an 'update domain' in an Availability Set?

- **A.** To determine which VMs are billed together
- **B.** To ensure not all VMs are rebooted simultaneously during planned host maintenance **(Correct)**
- **C.** To define the region a VM is deployed to
- **D.** To control network security rules

**Answer:** B — To ensure not all VMs are rebooted simultaneously during planned host maintenance  
**Explanation:** Update domains determine which VMs get rebooted together during planned maintenance, ensuring Azure does not restart every VM in the set at the same time.

---

**Q85.** What is the key difference in SCOPE between an Availability Set and an Availability Zone?

- **A.** They have identical scope
- **B.** An Availability Set protects within a single datacenter; an Availability Zone protects across physically separate datacenters in a region **(Correct)**
- **C.** An Availability Zone only works for storage, not compute
- **D.** An Availability Set spans multiple regions

**Answer:** B — An Availability Set protects within a single datacenter; an Availability Zone protects across physically separate datacenters in a region  
**Explanation:** Availability Sets protect against rack/host-level failure within ONE datacenter, while Availability Zones protect against the failure of an ENTIRE datacenter by using physically separate locations within a region.

---

## Topic 4 — Resources and Resource Groups

**Q86.** How many resource groups can a single Azure resource belong to at one time?

- **A.** Zero
- **B.** Exactly one **(Correct)**
- **C.** Up to three
- **D.** Unlimited

**Answer:** B — Exactly one  
**Explanation:** Every Azure resource must belong to exactly one resource group at a time; it cannot be split across multiple groups.

---

**Q87.** What happens when a resource group is deleted?

- **A.** Only the resource group's name is removed; resources remain
- **B.** All resources inside the resource group are also deleted **(Correct)**
- **C.** Resources are automatically moved to a default resource group
- **D.** Nothing happens until resources are deleted individually first

**Answer:** B — All resources inside the resource group are also deleted  
**Explanation:** Deleting a resource group deletes ALL resources contained within it — a commonly tested and important exam point, and a frequent source of accidental data loss.

---

**Q88.** Can resources within the same resource group be located in different Azure regions?

- **A.** No, all resources in a group must be in the same region
- **B.** Yes, resources within a group can span multiple regions **(Correct)**
- **C.** Only storage resources can span regions
- **D.** Only if using a Premium subscription

**Answer:** B — Yes, resources within a group can span multiple regions  
**Explanation:** A resource group is a logical container; resources inside it can span multiple regions, since the grouping is organizational rather than geographic.

---

**Q89.** What is the primary purpose of a resource group?

- **A.** To enforce a specific pricing tier on all resources inside it
- **B.** To logically group related resources for unified management, deployment, and billing tracking **(Correct)**
- **C.** To physically co-locate hardware in one datacenter
- **D.** To replace the need for a subscription

**Answer:** B — To logically group related resources for unified management, deployment, and billing tracking  
**Explanation:** A resource group exists purely for organizational and lifecycle management purposes — grouping related resources together for deployment, management, and billing visibility.

---

**Q90.** If Role-Based Access Control (RBAC) permissions are applied at the resource group level, what happens to resources inside that group?

- **A.** They are unaffected by the resource group's permissions
- **B.** They automatically inherit the permissions applied at the resource group level **(Correct)**
- **C.** They must have permissions configured individually regardless
- **D.** Permissions can never be applied at the resource group level

**Answer:** B — They automatically inherit the permissions applied at the resource group level  
**Explanation:** RBAC permissions applied at a resource group level are automatically inherited by all resources contained within that group, consistent with the resource hierarchy's inheritance rule.

---

**Q91.** A VM, a storage account, and a virtual network are all placed in resource group 'WebApp-Prod.' What is the simplest way to delete all three together?

- **A.** Delete each resource individually in any order
- **B.** Delete the 'WebApp-Prod' resource group **(Correct)**
- **C.** Delete the subscription
- **D.** Rename the resource group

**Answer:** B — Delete the 'WebApp-Prod' resource group  
**Explanation:** Deleting the resource group itself deletes every resource contained within it in one action, which is simpler than deleting each resource individually.

---

## Topic 5 — Subscriptions

**Q92.** What is the primary purpose of an Azure subscription?

- **A.** To define a boundary for billing and resource quotas **(Correct)**
- **B.** To physically separate hardware in different datacenters
- **C.** To replace the need for resource groups
- **D.** To define a security role for a single user

**Answer:** A — To define a boundary for billing and resource quotas  
**Explanation:** An Azure subscription is a logical container for provisioning resources, and defines the boundary for billing/cost tracking and default usage quotas.

---

**Q93.** Can a single resource group span multiple subscriptions?

- **A.** Yes, always
- **B.** No, a resource group exists within exactly one subscription **(Correct)**
- **C.** Only for Enterprise Agreement customers
- **D.** Only if using Management Groups

**Answer:** B — No, a resource group exists within exactly one subscription  
**Explanation:** A resource group cannot span multiple subscriptions — it exists within exactly one subscription, which itself sits within the resource hierarchy.

---

**Q94.** A university creates separate subscriptions for its CS department and its administrative IT systems. What is the main benefit of this separation?

- **A.** It allows each department's spending to be billed and tracked completely separately **(Correct)**
- **B.** It eliminates the need for resource groups entirely
- **C.** It automatically doubles the compute quota
- **D.** It removes the need for identity management

**Answer:** A — It allows each department's spending to be billed and tracked completely separately  
**Explanation:** Using separate subscriptions creates a distinct billing and quota boundary for each department, so spending in one does not affect or mix with the other.

---

**Q95.** Which of the following is true about default limits in an Azure subscription?

- **A.** Subscriptions have no limits at all
- **B.** Azure enforces certain default limits (e.g., maximum resource groups), which can sometimes be increased via support request **(Correct)**
- **C.** Limits can never be changed under any circumstances
- **D.** Limits apply only to storage, never to compute

**Answer:** B — Azure enforces certain default limits (e.g., maximum resource groups), which can sometimes be increased via support request  
**Explanation:** Azure subscriptions have default quotas/limits (such as the number of resource groups), and these can often be increased by submitting a support request to Microsoft.

---

## Topic 6 — Management Groups

**Q96.** What is the primary purpose of a Management Group?

- **A.** To manage access, policy, and compliance across multiple subscriptions at once **(Correct)**
- **B.** To store blob data
- **C.** To replace resource groups
- **D.** To define VM sizes

**Answer:** A — To manage access, policy, and compliance across multiple subscriptions at once  
**Explanation:** Management groups sit above subscriptions in the hierarchy and allow an organization to apply policy and access controls across many subscriptions simultaneously.

---

**Q97.** Can management groups be nested within other management groups?

- **A.** No, only one level of management groups is allowed
- **B.** Yes, management groups can be nested, up to a defined depth **(Correct)**
- **C.** Only subscriptions can be nested, not management groups
- **D.** Nesting is only available in sovereign regions

**Answer:** B — Yes, management groups can be nested, up to a defined depth  
**Explanation:** Management groups can be nested inside other management groups, allowing a hierarchical organizational structure up to a defined maximum depth.

---

**Q98.** All subscriptions within a single Azure AD (Microsoft Entra ID) tenant ultimately roll up into which single top-level container?

- **A.** The default resource group
- **B.** The root management group **(Correct)**
- **C.** The primary VNet
- **D.** The billing subscription

**Answer:** B — The root management group  
**Explanation:** Every subscription within a tenant ultimately rolls up into one top-level root management group, which sits at the very top of the resource hierarchy.

---

**Q99.** An IT administrator applies a security policy at the 'Finance-Division' management group level, which contains three subscriptions. What happens?

- **A.** The policy applies only to the management group itself, not the subscriptions
- **B.** The policy automatically applies to all three subscriptions and everything beneath them **(Correct)**
- **C.** The policy must be manually reapplied to each subscription
- **D.** Management group policies never affect subscriptions

**Answer:** B — The policy automatically applies to all three subscriptions and everything beneath them  
**Explanation:** Policies applied at a management group level are automatically inherited by every subscription (and everything beneath them) contained within that management group.

---

## Topic 7 — Resource Hierarchy

**Q100.** What is the correct order of Azure's resource hierarchy, from TOP to BOTTOM?

- **A.** Resources > Resource Groups > Subscriptions > Management Groups
- **B.** Management Groups > Subscriptions > Resource Groups > Resources **(Correct)**
- **C.** Subscriptions > Management Groups > Resources > Resource Groups
- **D.** Resource Groups > Management Groups > Subscriptions > Resources

**Answer:** B — Management Groups > Subscriptions > Resource Groups > Resources  
**Explanation:** The correct top-to-bottom hierarchy is: Root Management Group > Management Groups > Subscriptions > Resource Groups > Resources, with settings inherited downward.

---

**Q101.** If a policy is applied at the Management Group level, how far down the hierarchy does it apply by default?

- **A.** Only to that management group itself
- **B.** Down to every subscription, resource group, and resource beneath it, unless overridden **(Correct)**
- **C.** Only to resource groups, not individual resources
- **D.** It never applies automatically; it must be reapplied manually at each level

**Answer:** B — Down to every subscription, resource group, and resource beneath it, unless overridden  
**Explanation:** Settings applied at a higher level automatically flow down through subscriptions, resource groups, and resources beneath it, unless explicitly overridden at a lower level.

---

**Q102.** In the resource hierarchy, which level sits directly between Management Groups and Resource Groups?

- **A.** Resources
- **B.** Subscriptions **(Correct)**
- **C.** Root Management Group
- **D.** Availability Zones

**Answer:** B — Subscriptions  
**Explanation:** The hierarchy flows: Management Groups > Subscriptions > Resource Groups > Resources — so Subscriptions sit directly between Management Groups and Resource Groups.

---

**Q103.** A cost-control policy is applied at the 'Production' management group level, which contains 'Sales-Prod' and 'Marketing-Prod' subscriptions. A VM sits inside a resource group within 'Sales-Prod.' Does the policy affect that VM?

- **A.** No, policies never reach individual resources
- **B.** Yes, because of top-down inheritance through the hierarchy **(Correct)**
- **C.** Only if the VM is manually added to the policy
- **D.** Only if the VM is in its own management group

**Answer:** B — Yes, because of top-down inheritance through the hierarchy  
**Explanation:** Because of the inheritance rule, a policy applied at the management group level flows down through the subscription and resource group to affect every resource beneath it, including that VM.

---

## Topic 8 — Azure Resource Manager (ARM)

**Q104.** What is Azure Resource Manager (ARM)?

- **A.** A billing dashboard only
- **B.** The deployment and management layer behind every interaction with Azure, regardless of tool used **(Correct)**
- **C.** A type of virtual machine
- **D.** A physical datacenter management team

**Answer:** B — The deployment and management layer behind every interaction with Azure, regardless of tool used  
**Explanation:** ARM is the underlying deployment/management engine that receives and processes every request to create, update, or delete Azure resources, no matter which interface is used.

---

**Q105.** If an administrator creates a VM using the Azure Portal, and another administrator creates a VM using Azure CLI, what do both actions have in common?

- **A.** They use completely separate, unrelated backend systems
- **B.** Both are translated into the same underlying ARM API calls **(Correct)**
- **C.** CLI deployments bypass ARM entirely
- **D.** Portal deployments bypass ARM entirely

**Answer:** B — Both are translated into the same underlying ARM API calls  
**Explanation:** Regardless of which tool is used — Portal, CLI, or PowerShell — every request goes through the same ARM API, ensuring consistent behavior and policy enforcement.

---

**Q106.** What is an ARM template primarily used for?

- **A.** Declarative, repeatable infrastructure deployment described in a JSON file **(Correct)**
- **B.** Only for billing reports
- **C.** Replacing the need for subscriptions
- **D.** Monitoring network traffic

**Answer:** A — Declarative, repeatable infrastructure deployment described in a JSON file  
**Explanation:** ARM templates are JSON files describing the desired end-state of infrastructure, enabling declarative, consistent, and repeatable deployments — an early form of Infrastructure as Code.

---

**Q107.** Why does a policy blocking a specific VM size apply consistently whether an administrator uses the Portal or the CLI to attempt deployment?

- **A.** Because the Portal and CLI are the same application
- **B.** Because both go through the same ARM API, which enforces RBAC and Azure Policy checks at deployment time **(Correct)**
- **C.** Because policies are only enforced in the Portal
- **D.** Because CLI deployments are always rejected automatically

**Answer:** B — Because both go through the same ARM API, which enforces RBAC and Azure Policy checks at deployment time  
**Explanation:** ARM enforces RBAC and Azure Policy checks at the moment any resource is created or modified, and since all tools route through the same ARM API, enforcement is consistent regardless of the tool used.

---

## Topic 9 — Azure Compute Services

**Q108.** Which compute service requires the LEAST management effort from the customer, with Azure handling nearly everything including automatic scale-to-zero?

- **A.** Virtual Machines
- **B.** App Service
- **C.** Azure Functions **(Correct)**
- **D.** Availability Sets

**Answer:** C — Azure Functions  
**Explanation:** Azure Functions (serverless) requires the customer to manage only the code itself; Azure handles provisioning, scaling (including down to zero), and infrastructure automatically.

---

**Q109.** Which compute option gives a customer the MOST control, requiring them to manage the OS and everything above it?

- **A.** Azure Functions
- **B.** Virtual Machines **(Correct)**
- **C.** App Service
- **D.** Azure Container Apps

**Answer:** B — Virtual Machines  
**Explanation:** Virtual Machines are IaaS, giving the customer full control (and full responsibility) starting from the operating system upward.

---

## Topic 10 — Virtual Machines

**Q110.** Where can a customer obtain pre-configured VM images, such as an image with SQL Server already installed?

- **A.** Azure Marketplace **(Correct)**
- **B.** Azure DNS
- **C.** Azure Firewall
- **D.** Azure Site Recovery

**Answer:** A — Azure Marketplace  
**Explanation:** The Azure Marketplace offers pre-configured VM images (e.g., with software like SQL Server pre-installed) in addition to plain OS images.

---

**Q111.** What determines the combination of CPU, RAM, and disk performance available to an Azure VM?

- **A.** The resource group it is placed in
- **B.** The VM 'size' selected during creation **(Correct)**
- **C.** The subscription tier only
- **D.** The Availability Zone chosen

**Answer:** B — The VM 'size' selected during creation  
**Explanation:** The VM 'size' is the specific combination of CPU, RAM, and disk performance characteristics the customer selects based on workload needs.

---

**Q112.** Under the IaaS model for Virtual Machines, who is responsible for OS patching?

- **A.** Microsoft, always
- **B.** The customer **(Correct)**
- **C.** Neither party — OS patching is automatic and free
- **D.** Only Microsoft Support, upon request

**Answer:** B — The customer  
**Explanation:** Consistent with IaaS responsibilities, the customer manages everything from the OS upward, including applying OS patches.

---

## Topic 10.1 — VM Scale Sets

**Q113.** Which Azure feature lets an administrator deploy a group of identical, load-balanced VMs that automatically grow or shrink in number based on demand?

- **A.** Availability Set
- **B.** VM Scale Set **(Correct)**
- **C.** Azure Firewall
- **D.** Resource Group

**Answer:** B — VM Scale Set  
**Explanation:** VM Scale Sets manage a group of identical VMs with automatic scaling, directly implementing horizontal scaling and elasticity for virtual machines.

---

**Q114.** A VM Scale Set is configured to add instances when CPU exceeds 75% and remove instances below 25%. Which Unit 1 concept does this most directly implement?

- **A.** Elasticity **(Correct)**
- **B.** CapEx
- **C.** Shared Responsibility Model
- **D.** Global Reach

**Answer:** A — Elasticity  
**Explanation:** This automatic, demand-driven scaling behavior is a direct, concrete implementation of the elasticity concept from Unit 1, applied specifically to virtual machines.

---

**Q115.** Can a VM Scale Set be configured to spread its instances across multiple Availability Zones?

- **A.** No, Scale Sets can only use a single zone
- **B.** Yes, a Scale Set can span zones within a region for added resilience **(Correct)**
- **C.** Scale Sets cannot be used with Availability Zones under any configuration
- **D.** Scale Sets automatically disable zone support

**Answer:** B — Yes, a Scale Set can span zones within a region for added resilience  
**Explanation:** VM Scale Sets can be configured to spread instances across Availability Zones, combining automatic scaling (elasticity) with protection against datacenter-level failure.

---

**Q116.** Which statement correctly distinguishes a VM Scale Set from an Availability Set?

- **A.** They are the exact same feature with different names
- **B.** A VM Scale Set automatically scales the number of VM instances with demand, while an Availability Set protects a fixed group of VMs from localized hardware failure **(Correct)**
- **C.** An Availability Set automatically scales VMs; a Scale Set does not
- **D.** Scale Sets protect against regional disasters, Availability Sets do not

**Answer:** B — A VM Scale Set automatically scales the number of VM instances with demand, while an Availability Set protects a fixed group of VMs from localized hardware failure  
**Explanation:** A VM Scale Set's primary purpose is automatic scaling of instance count based on demand, while an Availability Set's purpose is protecting a FIXED group of VMs from rack/host-level failure using fault and update domains.

---

## Topic 11 — App Services

**Q117.** Which Azure compute service is a PaaS offering specifically designed for web apps, REST APIs, and mobile backends?

- **A.** Virtual Machines
- **B.** Azure App Service **(Correct)**
- **C.** Azure Container Instances
- **D.** Availability Sets

**Answer:** B — Azure App Service  
**Explanation:** Azure App Service is the PaaS offering purpose-built for hosting web applications, REST APIs, and mobile app backends, without the customer managing servers or OS.

---

**Q118.** What is the purpose of a 'deployment slot' in Azure App Service?

- **A.** To permanently delete an application
- **B.** To allow testing a new version (e.g., staging) before swapping it into production with minimal downtime **(Correct)**
- **C.** To define the VM size used
- **D.** To configure Availability Zones

**Answer:** B — To allow testing a new version (e.g., staging) before swapping it into production with minimal downtime  
**Explanation:** Deployment slots (such as staging and production) let a team test a new version of an app before swapping it into production, enabling near-zero-downtime deployments.

---

**Q119.** In Azure App Service, who is responsible for OS patching and server maintenance?

- **A.** The customer
- **B.** Azure (the provider) **(Correct)**
- **C.** Both equally, split 50/50
- **D.** Neither; patching never happens

**Answer:** B — Azure (the provider)  
**Explanation:** Because App Service is PaaS, Azure automatically handles OS patching, server maintenance, and infrastructure scaling, letting the customer focus purely on the application.

---

**Q120.** Which languages/frameworks does Azure App Service support?

- **A.** Only .NET
- **B.** Only Python
- **C.** Multiple languages and frameworks, including .NET, Java, Node.js, Python, and PHP **(Correct)**
- **D.** Only frameworks developed by Microsoft

**Answer:** C — Multiple languages and frameworks, including .NET, Java, Node.js, Python, and PHP  
**Explanation:** Azure App Service supports a wide range of languages and frameworks, including .NET, Java, Node.js, Python, PHP, and others.

---

## Topic 12 — Containers Overview

**Q121.** What core problem do containers solve by packaging an application with all its dependencies?

- **A.** The 'it works on my machine' problem, by ensuring consistent behavior across environments **(Correct)**
- **B.** The need for any compute resources at all
- **C.** The need for identity management
- **D.** The need for networking

**Answer:** A — The 'it works on my machine' problem, by ensuring consistent behavior across environments  
**Explanation:** Containers bundle an application with its dependencies so it behaves identically everywhere it runs — on a developer's laptop, a test server, or in Azure — solving environment-inconsistency problems.

---

**Q122.** Why are containers generally more lightweight than full virtual machines?

- **A.** Containers do not require any operating system
- **B.** Containers share the host operating system's kernel rather than running a full separate OS each **(Correct)**
- **C.** Containers cannot run more than one application
- **D.** Containers always run on dedicated hardware

**Answer:** B — Containers share the host operating system's kernel rather than running a full separate OS each  
**Explanation:** Containers share the host OS kernel instead of each including a full separate operating system, making them more lightweight and faster to start than VMs.

---

**Q123.** A data science team needs to run a single short-lived 20-minute batch job as a container, without managing any VMs or orchestration. Which service fits best?

- **A.** Azure Kubernetes Service (AKS)
- **B.** Azure Container Instances (ACI) **(Correct)**
- **C.** Azure Virtual Desktop
- **D.** Availability Set

**Answer:** B — Azure Container Instances (ACI)  
**Explanation:** ACI is designed for simple, short-lived, or burst container workloads, letting the team run a single container quickly without provisioning or managing any VMs.

---

**Q124.** A team wants automatic scaling for a set of microservices without directly managing Kubernetes clusters or nodes. Which service best fits this need?

- **A.** Azure Container Instances
- **B.** Azure Container Apps **(Correct)**
- **C.** Azure Virtual Machines
- **D.** Availability Set

**Answer:** B — Azure Container Apps  
**Explanation:** Azure Container Apps runs on Kubernetes internally but exposes a simplified deployment experience, giving autoscaling for microservices without exposing direct Kubernetes cluster management.

---

**Q125.** An e-commerce company needs fine-grained control over networking, scaling rules, and cluster configuration for dozens of interdependent microservices. Which service should it use?

- **A.** Azure Container Instances
- **B.** Azure Functions
- **C.** Azure Kubernetes Service (AKS) **(Correct)**
- **D.** Azure Virtual Desktop

**Answer:** C — Azure Kubernetes Service (AKS)  
**Explanation:** AKS provides full control over Kubernetes orchestration, networking, and scaling configuration, suited for complex, production-grade multi-container applications needing that level of control.

---

## Topic 13 — Azure Functions (Serverless)

**Q126.** What does 'serverless' mean in the context of Azure Functions?

- **A.** There are no servers anywhere in the world
- **B.** The customer manages only the code; Azure handles provisioning and scaling automatically, including scaling to zero **(Correct)**
- **C.** Functions can only run once and then are deleted
- **D.** Serverless means the service is entirely free

**Answer:** B — The customer manages only the code; Azure handles provisioning and scaling automatically, including scaling to zero  
**Explanation:** Serverless means the customer writes only the function code; Azure automatically manages provisioning and scaling, including scaling down to zero instances (and zero cost) when idle.

---

**Q127.** How is Azure Functions typically billed?

- **A.** A flat monthly fee regardless of usage
- **B.** Based on actual execution time and number of executions **(Correct)**
- **C.** Based on the number of registered users
- **D.** A one-time upfront purchase

**Answer:** B — Based on actual execution time and number of executions  
**Explanation:** Azure Functions billing is based on actual execution time and the number of executions, an extreme example of consumption-based pricing, since there is no cost when idle.

---

**Q128.** An online store wants to send a confirmation email automatically whenever a new order record is added to its database, without running a dedicated always-on server. Which service fits best?

- **A.** Azure Virtual Machines
- **B.** Azure Functions **(Correct)**
- **C.** Azure Virtual Desktop
- **D.** Availability Set

**Answer:** B — Azure Functions  
**Explanation:** Azure Functions is ideal for small, event-triggered tasks like sending an email when a database record is added, running (and billing) only for the few seconds needed.

---

**Q129.** Which trigger types can initiate execution of an Azure Function?

- **A.** Only manual button clicks in the Portal
- **B.** HTTP requests, messages arriving in a queue, or a scheduled timer, among others **(Correct)**
- **C.** Only scheduled timers
- **D.** Functions cannot be triggered; they run continuously

**Answer:** B — HTTP requests, messages arriving in a queue, or a scheduled timer, among others  
**Explanation:** Azure Functions can be triggered by a variety of events, including HTTP requests, messages arriving in a queue, and scheduled timers.

---

## Topic 14 — Azure Virtual Desktop

**Q130.** What does Azure Virtual Desktop primarily provide?

- **A.** A remote, virtualized Windows desktop and app environment accessible from almost any device **(Correct)**
- **B.** A content delivery network
- **C.** A type of blob storage tier
- **D.** A DNS hosting service

**Answer:** A — A remote, virtualized Windows desktop and app environment accessible from almost any device  
**Explanation:** Azure Virtual Desktop lets users access a full Windows desktop environment and applications remotely, with computing happening in Azure rather than on the local device.

---

**Q131.** A company wants employees to securely access the same corporate desktop environment from personal laptops, with no data stored locally. Which service fits best?

- **A.** Azure Virtual Desktop **(Correct)**
- **B.** Azure Functions
- **C.** Azure Container Instances
- **D.** Azure DNS

**Answer:** A — Azure Virtual Desktop  
**Explanation:** Azure Virtual Desktop allows secure remote access to a standard corporate desktop environment from any device, with processing and storage remaining in Azure rather than on the employee's personal device.

---

## Topic 15 — Application Hosting Decision Framework

**Q132.** A scenario requires full control over the OS to migrate an existing on-premises application as-is. Which compute option is the best fit?

- **A.** Azure Functions
- **B.** Virtual Machine **(Correct)**
- **C.** Azure Container Apps
- **D.** Azure Virtual Desktop

**Answer:** B — Virtual Machine  
**Explanation:** A Virtual Machine (IaaS) gives full control over the OS and everything above it, making it the best fit for an as-is migration of an existing application.

---

**Q133.** A scenario requires running code only when triggered by an event, with zero cost when idle. Which compute option is the best fit?

- **A.** Virtual Machine
- **B.** Azure Kubernetes Service
- **C.** Azure Functions **(Correct)**
- **D.** Availability Set

**Answer:** C — Azure Functions  
**Explanation:** Azure Functions (serverless) is specifically designed for event-triggered code execution with no cost incurred while idle.

---

**Q134.** A scenario requires protecting a small, fixed group of VMs from a single rack losing power, without needing protection across multiple datacenters. Which tool fits, and why not the alternative?

- **A.** Availability Zone, because it spans multiple datacenters
- **B.** Availability Set, because it uses fault domains to protect against rack-level failure within one datacenter **(Correct)**
- **C.** VM Scale Set, because it automatically adds more VMs
- **D.** Azure Firewall, because it filters network traffic

**Answer:** B — Availability Set, because it uses fault domains to protect against rack-level failure within one datacenter  
**Explanation:** An Availability Set specifically protects against rack/hardware-level failure within a single datacenter using fault domains; an Availability Zone would be the choice only if protection against an entire datacenter failing were needed.

---

**Q135.** A scenario asks for a REST API for a mobile app, deployed quickly without managing servers or OS. Which compute option is the best fit?

- **A.** Virtual Machine
- **B.** App Service **(Correct)**
- **C.** Availability Set
- **D.** Azure Virtual Desktop

**Answer:** B — App Service  
**Explanation:** App Service (PaaS) is purpose-built for deploying web apps and REST APIs quickly, without the customer managing servers or the operating system.

---

**Q136.** A scenario calls for a fully custom Kubernetes-based deployment pipeline with complete control over orchestration. Which compute option is the best fit?

- **A.** Azure Container Instances
- **B.** Azure Kubernetes Service (AKS) **(Correct)**
- **C.** Azure Functions
- **D.** Virtual Machine Scale Set

**Answer:** B — Azure Kubernetes Service (AKS)  
**Explanation:** AKS offers full control over Kubernetes configuration and orchestration, matching a requirement for a fully custom Kubernetes-based deployment pipeline.

---

# Unit 3

## Topic 1 — Virtual Networks and Subnets

**Q137.** What is the primary purpose of an Azure Virtual Network (VNet)?

- **A.** To host DNS records
- **B.** To provide a logically isolated private network for Azure resources to communicate securely **(Correct)**
- **C.** To replace the need for a subscription
- **D.** To store blob data

**Answer:** B — To provide a logically isolated private network for Azure resources to communicate securely  
**Explanation:** A VNet is the fundamental building block for private networking in Azure, providing logical isolation so resources can communicate securely using private IP addresses.

---

**Q138.** Is a VNet scoped to a single region or can it span multiple regions directly?

- **A.** A VNet is scoped to a single region (though it can connect to VNets in other regions via peering) **(Correct)**
- **B.** A VNet always spans every Azure region automatically
- **C.** A VNet is scoped to a single subnet only
- **D.** A VNet has no regional scope at all

**Answer:** A — A VNet is scoped to a single region (though it can connect to VNets in other regions via peering)  
**Explanation:** A VNet is scoped to a single Azure region and a single subscription; connecting to VNets in other regions requires VNet Peering.

---

**Q139.** What is a subnet used for within a VNet?

- **A.** To segment a VNet's address space into smaller ranges for logically organizing and isolating groups of resources **(Correct)**
- **B.** To connect two separate subscriptions
- **C.** To replace the need for an NSG
- **D.** To host a public website directly

**Answer:** A — To segment a VNet's address space into smaller ranges for logically organizing and isolating groups of resources  
**Explanation:** A subnet is a smaller, segmented IP range within a VNet's address space, used to logically group and isolate resources (such as separating web, app, and database tiers).

---

## Topic 1.2 — VNet Peering

**Q140.** What does VNet Peering allow?

- **A.** Two VNets to communicate using private IP addresses without traversing the public internet **(Correct)**
- **B.** Two VNets to merge into a single subscription
- **C.** A VNet to bypass Azure DNS
- **D.** A VNet to automatically gain Availability Zone support

**Answer:** A — Two VNets to communicate using private IP addresses without traversing the public internet  
**Explanation:** VNet Peering connects two VNets so resources can communicate using private IP addresses over the Microsoft backbone network, without using the public internet.

---

**Q141.** VNet A is peered with VNet B, and VNet B is peered with VNet C. Can VNet A automatically communicate with VNet C?

- **A.** Yes, peering is always transitive
- **B.** No, peering is non-transitive; a direct peering between A and C would be required **(Correct)**
- **C.** Only if all three VNets are in the same region
- **D.** Only if Azure Firewall is deployed

**Answer:** B — No, peering is non-transitive; a direct peering between A and C would be required  
**Explanation:** VNet Peering is non-transitive — A being peered with B and B with C does NOT automatically allow A and C to communicate; a direct peering between A and C would be needed.

---

**Q142.** A company peers its East US production VNet with its West Europe reporting VNet. What benefit does this provide?

- **A.** The reporting service can query the production database using a private IP, without exposing either network to the public internet **(Correct)**
- **B.** It automatically creates a VPN Gateway
- **C.** It eliminates the need for subnets
- **D.** It merges both VNets into a single resource group

**Answer:** A — The reporting service can query the production database using a private IP, without exposing either network to the public internet  
**Explanation:** Global VNet Peering allows secure, private-IP communication between VNets in different regions over Microsoft's backbone network, without exposing traffic to the public internet.

---

## Topic 2 — VPN Gateway

**Q143.** What does an Azure VPN Gateway establish between an on-premises network and an Azure VNet?

- **A.** A physically dedicated private circuit with no internet involvement
- **B.** An encrypted tunnel over the public internet **(Correct)**
- **C.** A direct fiber optic cable installed by Microsoft
- **D.** A DNS-only connection

**Answer:** B — An encrypted tunnel over the public internet  
**Explanation:** A VPN Gateway creates a secure, encrypted tunnel (using IPsec/IKE) between an on-premises network and Azure, traveling over the public internet.

---

**Q144.** Compared to ExpressRoute, what is a disadvantage of using a VPN Gateway?

- **A.** It is always more expensive
- **B.** It relies on the public internet, so it doesn't offer the same guaranteed bandwidth or latency **(Correct)**
- **C.** It cannot be encrypted
- **D.** It cannot connect to any on-premises network

**Answer:** B — It relies on the public internet, so it doesn't offer the same guaranteed bandwidth or latency  
**Explanation:** Because VPN Gateway connections travel over the public internet, they do not offer the same consistent bandwidth and latency guarantees that a dedicated ExpressRoute circuit provides.

---

## Topic 3 — ExpressRoute

**Q145.** What distinguishes Azure ExpressRoute from a VPN Gateway connection?

- **A.** ExpressRoute uses a private, dedicated connection that does not traverse the public internet **(Correct)**
- **B.** ExpressRoute is cheaper than a VPN Gateway
- **C.** ExpressRoute only works within a single Availability Zone
- **D.** ExpressRoute cannot be used by large enterprises

**Answer:** A — ExpressRoute uses a private, dedicated connection that does not traverse the public internet  
**Explanation:** ExpressRoute provides a private, dedicated circuit through a connectivity provider, entirely bypassing the public internet, unlike a VPN Gateway's encrypted internet tunnel.

---

**Q146.** A bank requires guaranteed low latency and high reliability for real-time transaction processing between its on-premises datacenter and Azure, and cannot risk public internet exposure. Which connectivity option should it use?

- **A.** VPN Gateway
- **B.** ExpressRoute **(Correct)**
- **C.** Azure DNS
- **D.** VNet Peering only

**Answer:** B — ExpressRoute  
**Explanation:** ExpressRoute offers a private, dedicated circuit with consistent latency and reliability, avoiding the public internet entirely — matching the bank's mission-critical requirements.

---

**Q147.** Which of these is generally TRUE when comparing VPN Gateway and ExpressRoute?

- **A.** ExpressRoute is typically more expensive and offers more consistent performance than a VPN Gateway **(Correct)**
- **B.** VPN Gateway always has lower latency than ExpressRoute
- **C.** Both have identical cost and performance characteristics
- **D.** ExpressRoute cannot connect on-premises networks to Azure

**Answer:** A — ExpressRoute is typically more expensive and offers more consistent performance than a VPN Gateway  
**Explanation:** ExpressRoute typically costs more than a VPN Gateway but provides more predictable, consistent performance since it avoids the public internet entirely.

---

## Topic 4 — Load Balancer

**Q148.** At which OSI layer does Azure Load Balancer operate?

- **A.** Layer 7 (Application)
- **B.** Layer 4 (Transport) **(Correct)**
- **C.** Layer 2 (Data Link)
- **D.** Layer 1 (Physical)

**Answer:** B — Layer 4 (Transport)  
**Explanation:** Azure Load Balancer operates at Layer 4, distributing traffic based on IP address and port without inspecting the actual content of the traffic.

---

**Q149.** How does Azure Load Balancer detect and respond to an unresponsive backend VM instance?

- **A.** It has no way to detect instance health
- **B.** It performs health probes and automatically stops sending traffic to failed instances **(Correct)**
- **C.** It deletes the failed instance permanently
- **D.** It only checks health once per day

**Answer:** B — It performs health probes and automatically stops sending traffic to failed instances  
**Explanation:** Azure Load Balancer continuously performs health probes on backend instances, automatically routing traffic away from any instance that fails a health check.

---

## Topic 4.1 — Application Gateway

**Q150.** At which OSI layer does Azure Application Gateway operate, and what does this allow it to do?

- **A.** Layer 4; it can only route by IP and port
- **B.** Layer 7; it can route based on the content of a web request such as URL path or hostname **(Correct)**
- **C.** Layer 2; it only switches frames
- **D.** Layer 3; it only routes based on IP subnet

**Answer:** B — Layer 7; it can route based on the content of a web request such as URL path or hostname  
**Explanation:** Application Gateway operates at Layer 7 (the application layer), allowing it to make routing decisions based on the actual content of an HTTP request, such as URL path or hostname.

---

**Q151.** A retailer wants requests to '/images/*' routed to one server pool and '/checkout/*' routed to a different, more secure pool, based on URL path. Which Azure service is required?

- **A.** Azure Load Balancer, since it supports URL-based routing
- **B.** Application Gateway, since it can inspect HTTP request content **(Correct)**
- **C.** Azure DNS, since it resolves domain names
- **D.** VPN Gateway, since it handles encrypted traffic

**Answer:** B — Application Gateway, since it can inspect HTTP request content  
**Explanation:** Because this requires inspecting and routing based on the actual URL path of the HTTP request, Application Gateway (Layer 7) is needed — a standard Load Balancer (Layer 4) cannot make this decision.

---

**Q152.** Which additional security capability does Application Gateway offer that Azure Load Balancer does not?

- **A.** DNS hosting
- **B.** Web Application Firewall (WAF) **(Correct)**
- **C.** VNet Peering
- **D.** Availability Zones

**Answer:** B — Web Application Firewall (WAF)  
**Explanation:** Application Gateway includes an optional Web Application Firewall (WAF) capability to protect against common web exploits, which a standard Layer-4 Load Balancer does not offer.

---

## Topic 5 — Network Security Groups (NSGs)

**Q153.** What does a Network Security Group (NSG) rule specify?

- **A.** Source/destination IP range, port, protocol, and whether to allow or deny traffic **(Correct)**
- **B.** Only the VM size to deploy
- **C.** Only the storage redundancy option
- **D.** Only the DNS record type

**Answer:** A — Source/destination IP range, port, protocol, and whether to allow or deny traffic  
**Explanation:** NSG rules define the source/destination IP range, port, protocol, and an allow or deny action, used to filter inbound and outbound traffic.

---

**Q154.** How are NSG rules evaluated when multiple rules could apply to the same traffic?

- **A.** All matching rules are applied simultaneously
- **B.** Rules are evaluated by priority number, lowest first, and evaluation stops at the first match **(Correct)**
- **C.** Rules are evaluated alphabetically by name
- **D.** Only the last rule created is ever applied

**Answer:** B — Rules are evaluated by priority number, lowest first, and evaluation stops at the first match  
**Explanation:** NSG rules are evaluated in order of priority number, with lower numbers evaluated first; once a rule matches the traffic, evaluation stops and that rule's action is applied.

---

**Q155.** A web subnet must accept HTTP/HTTPS from the internet, while a database subnet must never be directly reachable from the internet. What is applied to achieve this?

- **A.** A single NSG applied identically to both subnets
- **B.** Separate NSGs on each subnet, with the web subnet allowing ports 80/443 and the database subnet denying direct internet inbound traffic **(Correct)**
- **C.** Azure DNS records for each subnet
- **D.** VNet Peering between the two subnets

**Answer:** B — Separate NSGs on each subnet, with the web subnet allowing ports 80/443 and the database subnet denying direct internet inbound traffic  
**Explanation:** Applying separate, appropriately scoped NSGs — one permissive for web traffic, one restrictive for the database — achieves this tiered security requirement.

---

**Q156.** To what can a Network Security Group be associated?

- **A.** Only an entire subscription
- **B.** A subnet or an individual network interface **(Correct)**
- **C.** Only a management group
- **D.** Only a storage account

**Answer:** B — A subnet or an individual network interface  
**Explanation:** NSGs can be associated with a subnet (applying to everything inside it) or with an individual network interface (applying to one specific resource).

---

## Topic 6 — Azure DNS

**Q157.** What is the primary function of Azure DNS?

- **A.** To filter network traffic based on security rules
- **B.** To host and resolve DNS domain records, translating domain names into IP addresses **(Correct)**
- **C.** To provide VPN connectivity
- **D.** To store blob data

**Answer:** B — To host and resolve DNS domain records, translating domain names into IP addresses  
**Explanation:** Azure DNS is a hosting service for DNS domains, translating human-readable domain names into IP addresses, managed using the same Azure credentials, APIs, and billing as other resources.

---

**Q158.** A company wants 'www.example.com' to point to the public IP of its Azure Load Balancer. What does it create in Azure DNS to achieve this?

- **A.** An NSG rule
- **B.** An 'A' record mapping the domain name to the IP address **(Correct)**
- **C.** A Blob Storage container
- **D.** A VNet Peering connection

**Answer:** B — An 'A' record mapping the domain name to the IP address  
**Explanation:** An 'A' record in Azure DNS maps a domain name directly to an IP address, allowing users to reach a service using a familiar domain name.

---

## Topic 6.1 — Azure Firewall

**Q159.** How does Azure Firewall differ from a Network Security Group (NSG)?

- **A.** They are identical with no functional difference
- **B.** Azure Firewall is a fully managed, centrally applied firewall-as-a-service across entire VNets, with advanced capabilities like threat intelligence filtering, while NSGs are simpler, resource/subnet-level filters **(Correct)**
- **C.** NSGs can span multiple subscriptions, but Azure Firewall cannot
- **D.** Azure Firewall only works with Blob Storage

**Answer:** B — Azure Firewall is a fully managed, centrally applied firewall-as-a-service across entire VNets, with advanced capabilities like threat intelligence filtering, while NSGs are simpler, resource/subnet-level filters  
**Explanation:** Azure Firewall provides centralized, managed, stateful firewall capabilities across an entire virtual network (or multiple VNets/subscriptions), including advanced features like threat intelligence, whereas NSGs are simpler, more localized traffic filters.

---

**Q160.** A large organization wants to centrally enforce an outbound traffic rule across many VNets and subscriptions, rather than configuring NSGs individually on every subnet. What should it deploy?

- **A.** A separate NSG per subnet only
- **B.** Azure Firewall **(Correct)**
- **C.** Azure DNS
- **D.** VPN Gateway

**Answer:** B — Azure Firewall  
**Explanation:** Azure Firewall allows centralized enforcement of traffic rules across an entire environment spanning multiple VNets and subscriptions, avoiding the need to configure NSGs individually everywhere.

---

## Topic 7 — Azure Storage Types

**Q161.** Which Azure Storage type is best suited for storing unstructured data such as images, videos, and backups?

- **A.** Table Storage
- **B.** Blob Storage **(Correct)**
- **C.** Queue Storage
- **D.** Disk Storage

**Answer:** B — Blob Storage  
**Explanation:** Blob Storage is designed for storing large amounts of unstructured data such as images, videos, documents, and backup archives.

---

**Q162.** Which Azure Storage type provides fully managed file shares accessible via the standard SMB/NFS protocol?

- **A.** Azure Files **(Correct)**
- **B.** Blob Storage
- **C.** Queue Storage
- **D.** Table Storage

**Answer:** A — Azure Files  
**Explanation:** Azure Files provides fully managed file shares accessible using the standard SMB/NFS protocol, commonly used to replace an on-premises file server.

---

**Q163.** A web application's front-end needs to pass a message to a background worker to resize an uploaded image. Which storage type is best suited for this?

- **A.** Queue Storage **(Correct)**
- **B.** Disk Storage
- **C.** Table Storage
- **D.** Blob Storage

**Answer:** A — Queue Storage  
**Explanation:** Queue Storage is designed for passing messages between application components, decoupling the front-end from the background worker process.

---

**Q164.** Which Azure Storage type provides persistent disks attached to Azure Virtual Machines?

- **A.** Disk Storage **(Correct)**
- **B.** Table Storage
- **C.** Queue Storage
- **D.** Blob Storage

**Answer:** A — Disk Storage  
**Explanation:** Disk Storage provides persistent disks used as OS disks and data disks attached to Azure Virtual Machines.

---

**Q165.** Which Azure Storage type is a NoSQL key-value store for simple structured data not requiring a full relational database?

- **A.** Table Storage **(Correct)**
- **B.** Blob Storage
- **C.** Disk Storage
- **D.** Azure Files

**Answer:** A — Table Storage  
**Explanation:** Table Storage provides a NoSQL key-value structure for simple structured data that does not need the complexity of a full relational database.

---

## Topic 7.1 — Blob Access Tiers

**Q166.** Which Blob access tier offers the LOWEST storage cost but the HIGHEST (and slowest) access cost, suited for data accessed rarely and kept for 180+ days?

- **A.** Hot
- **B.** Cool
- **C.** Archive **(Correct)**
- **D.** Premium

**Answer:** C — Archive  
**Explanation:** The Archive tier offers the lowest storage cost but the highest access cost and slowest retrieval (potentially hours), suited for long-term, rarely accessed compliance data kept 180+ days.

---

**Q167.** Which Blob access tier is best suited for data accessed frequently, such as active website content?

- **A.** Archive
- **B.** Cool
- **C.** Hot **(Correct)**
- **D.** Cold-only

**Answer:** C — Hot  
**Explanation:** The Hot tier has a higher storage cost but lower access cost, making it the right choice for frequently accessed data such as active website content.

---

**Q168.** A company moves 2–3 year old invoices it rarely needs, but wants to retrieve quickly if required, to which Blob tier?

- **A.** Hot
- **B.** Cool **(Correct)**
- **C.** Archive
- **D.** Table Storage

**Answer:** B — Cool  
**Explanation:** The Cool tier suits data accessed infrequently (kept at least 30 days) but which still needs to remain relatively quickly retrievable, unlike Archive.

---

**Q169.** What Azure feature can automate moving blobs between Hot, Cool, and Archive tiers based on age or last-access time?

- **A.** A lifecycle management policy **(Correct)**
- **B.** An NSG rule
- **C.** VNet Peering
- **D.** Azure Site Recovery

**Answer:** A — A lifecycle management policy  
**Explanation:** A lifecycle management policy automates the movement of blobs between access tiers based on criteria such as age or time since last access, without manual intervention.

---

## Topic 8 — Storage Redundancy

**Q170.** Which redundancy option keeps 3 copies of data within a single datacenter only, protecting against hardware failure but not datacenter failure?

- **A.** LRS **(Correct)**
- **B.** ZRS
- **C.** GRS
- **D.** GZRS

**Answer:** A — LRS  
**Explanation:** LRS (Locally Redundant Storage) keeps 3 copies of data within a single datacenter, protecting against hardware/rack failure but not against an entire datacenter going down.

---

**Q171.** Which redundancy option replicates data across multiple Availability Zones within one region, protecting against datacenter-level failure?

- **A.** LRS
- **B.** ZRS **(Correct)**
- **C.** GRS only
- **D.** RA-GRS only

**Answer:** B — ZRS  
**Explanation:** ZRS (Zone-Redundant Storage) keeps 3 copies across multiple Availability Zones within a single region, protecting against the failure of an entire datacenter.

---

**Q172.** Which redundancy option protects against an entire Azure region becoming unavailable by replicating data to the paired region?

- **A.** LRS
- **B.** ZRS
- **C.** GRS **(Correct)**
- **D.** None of these

**Answer:** C — GRS  
**Explanation:** GRS (Geo-Redundant Storage) keeps copies in the primary region (as LRS) plus asynchronously replicates to the paired region, protecting against a full regional failure.

---

**Q173.** What does the 'RA-' prefix (e.g., RA-GRS) specifically add compared to standard GRS?

- **A.** Nothing; it is purely a marketing term
- **B.** The ability to directly read data from the secondary region's copy, not just hold it in reserve **(Correct)**
- **C.** Faster write speeds only in the primary region
- **D.** Automatic deletion of the primary copy

**Answer:** B — The ability to directly read data from the secondary region's copy, not just hold it in reserve  
**Explanation:** The 'RA-' (Read-Access) prefix specifically means the secondary region's replicated copy can be read directly by the application, rather than only being held in reserve for failover.

---

**Q174.** A hospital needs protection against both a single datacenter failure AND an entire region failure, plus the ability to read from the secondary region if the primary is unavailable. Which redundancy option fits best?

- **A.** LRS
- **B.** ZRS
- **C.** RA-GZRS **(Correct)**
- **D.** Standard GRS without read access

**Answer:** C — RA-GZRS  
**Explanation:** RA-GZRS combines zone redundancy (protects against datacenter failure) with geo-redundancy (protects against regional failure) and adds read access to the secondary copy — matching all three requirements.

---

**Q175.** A startup storing non-critical, easily regenerated temporary cache data wants the cheapest redundancy option. Which should it choose?

- **A.** RA-GZRS
- **B.** GRS
- **C.** LRS **(Correct)**
- **D.** GZRS

**Answer:** C — LRS  
**Explanation:** LRS is the cheapest redundancy option, appropriate for data whose loss would be inconvenient but not catastrophic, such as easily regenerated temporary cache data.

---

## Topic 9 — Storage Migration and Management Tools

**Q176.** Which tool is a command-line utility for high-performance copying of data to, from, or between Azure Storage accounts?

- **A.** Azure Migrate
- **B.** AzCopy **(Correct)**
- **C.** Azure Data Box
- **D.** Azure Firewall

**Answer:** B — AzCopy  
**Explanation:** AzCopy is a command-line tool specifically designed for high-performance data copying to, from, or between Azure Storage accounts.

---

**Q177.** A company has 200 TB of archival data and determines that uploading it over the internet would take weeks. Which Azure tool is designed for this scenario?

- **A.** Azure Storage Explorer
- **B.** Azure Data Box **(Correct)**
- **C.** Azure DNS
- **D.** AzCopy

**Answer:** B — Azure Data Box  
**Explanation:** Azure Data Box is a physical, secure device shipped to an organization for offline transfer of very large volumes of data that would be impractical to move over a network connection.

---

**Q178.** Which tool provides a centralized hub for assessing and migrating on-premises servers, databases, and applications to Azure?

- **A.** Azure Migrate **(Correct)**
- **B.** AzCopy
- **C.** Azure Storage Explorer
- **D.** Azure Firewall

**Answer:** A — Azure Migrate  
**Explanation:** Azure Migrate is a centralized hub of tools specifically for assessing and migrating on-premises infrastructure (servers, databases, applications) to Azure.

---

**Q179.** Which tool provides a standalone graphical application for browsing and managing Blob, File, Queue, and Table storage?

- **A.** Azure Storage Explorer **(Correct)**
- **B.** AzCopy
- **C.** Azure Data Box
- **D.** Azure Migrate

**Answer:** A — Azure Storage Explorer  
**Explanation:** Azure Storage Explorer is a graphical application (also available within the Azure Portal) for browsing and manually managing data across Blob, File, Queue, and Table storage.

---

## Topic 10 — Azure SQL Database

**Q180.** Azure SQL Database is best described as:

- **A.** An IaaS offering requiring manual OS patching
- **B.** A fully managed PaaS relational database built on SQL Server technology **(Correct)**
- **C.** A NoSQL document database
- **D.** A file storage service

**Answer:** B — A fully managed PaaS relational database built on SQL Server technology  
**Explanation:** Azure SQL Database is a fully managed PaaS relational database, with Microsoft handling patching, backups, and infrastructure, built on Microsoft SQL Server technology.

---

**Q181.** An online banking application needs strict relational structure between accounts, transactions, and account holders, with strong consistency. Which database service fits best?

- **A.** Cosmos DB
- **B.** Azure SQL Database **(Correct)**
- **C.** Blob Storage
- **D.** Queue Storage

**Answer:** B — Azure SQL Database  
**Explanation:** Azure SQL Database is designed for highly structured, relational data with defined relationships and strong consistency guarantees, matching the banking application's needs.

---

**Q182.** Under Azure SQL Database (a PaaS offering), who is responsible for automatic backups and patching?

- **A.** The customer
- **B.** Microsoft (the provider) **(Correct)**
- **C.** A third-party vendor only
- **D.** No backups are provided

**Answer:** B — Microsoft (the provider)  
**Explanation:** Because Azure SQL Database is PaaS, Microsoft manages patching, backups, high availability, and infrastructure, consistent with the PaaS responsibility split.

---

## Topic 11 — Cosmos DB Overview

**Q183.** Which Azure database service is designed for globally distributed, low-latency NoSQL workloads?

- **A.** Azure SQL Database
- **B.** Azure Cosmos DB **(Correct)**
- **C.** Azure Files
- **D.** Disk Storage

**Answer:** B — Azure Cosmos DB  
**Explanation:** Cosmos DB is a fully managed, globally distributed NoSQL database designed for extremely low latency, high throughput, and flexible data structures at global scale.

---

**Q184.** A global gaming company needs a leaderboard system responding in milliseconds to players across multiple continents, with flexible (non-relational) data. Which database fits best?

- **A.** Azure SQL Database
- **B.** Cosmos DB **(Correct)**
- **C.** Azure Files
- **D.** Queue Storage

**Answer:** B — Cosmos DB  
**Explanation:** Cosmos DB's native global distribution and low-latency design across multiple regions makes it the right fit for a globally responsive, flexible-schema leaderboard system.

---

**Q185.** Which of the following is a key difference between Azure SQL Database and Cosmos DB?

- **A.** Azure SQL Database is NoSQL; Cosmos DB is relational
- **B.** Azure SQL Database requires a fixed schema and relational structure; Cosmos DB is schema-flexible and supports multiple NoSQL data models **(Correct)**
- **C.** They are functionally identical services
- **D.** Cosmos DB cannot scale beyond one region

**Answer:** B — Azure SQL Database requires a fixed schema and relational structure; Cosmos DB is schema-flexible and supports multiple NoSQL data models  
**Explanation:** Azure SQL Database uses a fixed relational schema (tables, rows, foreign keys), while Cosmos DB is schema-flexible, supporting multiple NoSQL data models (document, key-value, graph, column-family).

---

## Topic 11.1 — Other Azure Database Services

**Q186.** Besides Azure SQL Database and Cosmos DB, which other relational database engines does Azure offer as fully managed services?

- **A.** Only Oracle Database
- **B.** Azure Database for MySQL and Azure Database for PostgreSQL **(Correct)**
- **C.** Only IBM DB2
- **D.** None; Azure only supports SQL Server-based databases

**Answer:** B — Azure Database for MySQL and Azure Database for PostgreSQL  
**Explanation:** Azure also offers Azure Database for MySQL and Azure Database for PostgreSQL as fully managed PaaS services, for applications built around those specific open-source database engines.

---

## Topic 12 — Microsoft Entra ID

**Q187.** What is the primary function of Microsoft Entra ID (formerly Azure Active Directory)?

- **A.** Hosting DNS records
- **B.** Cloud-based identity and access management — authenticating and authorizing users **(Correct)**
- **C.** Providing blob storage
- **D.** Load balancing network traffic

**Answer:** B — Cloud-based identity and access management — authenticating and authorizing users  
**Explanation:** Microsoft Entra ID is Microsoft's cloud-based identity and access management service, used to authenticate (verify identity) and authorize (determine permissions for) users.

---

**Q188.** How does Microsoft Entra ID relate to the Azure resource hierarchy covered in Unit 2?

- **A.** It replaces the resource hierarchy entirely
- **B.** It is a tenant-level identity service that sits logically above the resource hierarchy, providing the identities that RBAC then grants permissions to **(Correct)**
- **C.** It only applies to Resource Groups, not Subscriptions
- **D.** It has no relationship to the resource hierarchy

**Answer:** B — It is a tenant-level identity service that sits logically above the resource hierarchy, providing the identities that RBAC then grants permissions to  
**Explanation:** Microsoft Entra ID operates at the tenant level, providing the user and group identities that Role-Based Access Control (RBAC) then assigns permissions to at various points in the resource hierarchy.

---

## Topic 12.1 — Single Sign-On (SSO)

**Q189.** What does Single Sign-On (SSO) allow a user to do?

- **A.** Sign in once and gain access to multiple applications without re-authenticating for each one **(Correct)**
- **B.** Create multiple separate passwords for each application
- **C.** Bypass all authentication entirely
- **D.** Share their password with other users safely

**Answer:** A — Sign in once and gain access to multiple applications without re-authenticating for each one  
**Explanation:** SSO allows a user to authenticate once with a single identity and then access multiple connected applications without needing to sign in again separately for each one.

---

**Q190.** An employee signs in once in the morning and is not prompted to log in again when opening Outlook, Teams, and a third-party project tool throughout the day. This is an example of:

- **A.** Multifactor Authentication
- **B.** Single Sign-On (SSO) **(Correct)**
- **C.** Passwordless authentication
- **D.** Role-Based Access Control

**Answer:** B — Single Sign-On (SSO)  
**Explanation:** This describes SSO: one authentication session trusted across multiple connected applications, so the user is not prompted to log in again for each one.

---

## Topic 12.2 — Hybrid Identity (Microsoft Entra Connect)

**Q191.** Which tool synchronizes an on-premises Active Directory with Microsoft Entra ID to create a hybrid identity setup?

- **A.** Azure Site Recovery
- **B.** Microsoft Entra Connect **(Correct)**
- **C.** Azure Migrate
- **D.** Azure Firewall

**Answer:** B — Microsoft Entra Connect  
**Explanation:** Microsoft Entra Connect is the tool used to synchronize on-premises Active Directory identities with Microsoft Entra ID, enabling a hybrid identity configuration.

---

**Q192.** A company with 500 existing on-premises Active Directory accounts wants employees to use the same credentials for both office login and cloud access, without recreating accounts manually. What should it deploy?

- **A.** Microsoft Entra Connect **(Correct)**
- **B.** Azure Data Box
- **C.** Azure Firewall
- **D.** VNet Peering

**Answer:** A — Microsoft Entra Connect  
**Explanation:** Microsoft Entra Connect automatically synchronizes existing on-premises AD accounts into Microsoft Entra ID, avoiding the need to manually recreate each account in the cloud.

---

## Topic 12.3 — External Identities (B2B/B2C)

**Q193.** Which Microsoft Entra External Identities feature allows an external partner to sign in using their own existing company credentials, without a new internal account being created?

- **A.** Business to Consumer (B2C)
- **B.** Business to Business (B2B) **(Correct)**
- **C.** Single Sign-On only
- **D.** Role-Based Access Control

**Answer:** B — Business to Business (B2B)  
**Explanation:** B2B (Business to Business) allows external partners, vendors, or contractors to access resources using their own organization's existing credentials, without needing a new account created for them.

---

**Q194.** A public-facing mobile app wants customers to sign in using their personal email address or a social media account. Which feature supports this?

- **A.** Business to Business (B2B)
- **B.** Business to Consumer (B2C) **(Correct)**
- **C.** Microsoft Entra Connect
- **D.** Azure Firewall

**Answer:** B — Business to Consumer (B2C)  
**Explanation:** B2C (Business to Consumer) allows a public-facing application to let customers sign in using their own preferred identity, such as a personal email or social media account.

---

**Q195.** A company wants to grant an external auditing firm access to specific financial reports using the auditors' own company email credentials. Which Microsoft Entra feature supports this scenario?

- **A.** B2C External Identities
- **B.** B2B External Identities **(Correct)**
- **C.** Microsoft Entra Connect
- **D.** Azure Site Recovery

**Answer:** B — B2B External Identities  
**Explanation:** B2B External Identities is designed exactly for this scenario — granting external organizations access using their own existing credentials, rather than creating new internal accounts.

---

## Topic 13 — Authentication Methods

**Q196.** What is a key weakness of password-only authentication?

- **A.** It requires special hardware
- **B.** Passwords can be guessed, phished, or reused across services, making them the weakest method alone **(Correct)**
- **C.** It is impossible to implement
- **D.** It cannot be used with any Azure service

**Answer:** B — Passwords can be guessed, phished, or reused across services, making them the weakest method alone  
**Explanation:** Password-only authentication is considered the weakest method on its own because passwords can be guessed, phished, or reused across multiple services, exposing the account if any one is compromised.

---

**Q197.** An employee enters the correct password and is then prompted to approve a notification on their registered phone before access is granted. What is this an example of?

- **A.** Single Sign-On
- **B.** Multifactor Authentication (MFA) **(Correct)**
- **C.** Role-Based Access Control
- **D.** B2B External Identity

**Answer:** B — Multifactor Authentication (MFA)  
**Explanation:** Requiring both a password (something known) and approval via a registered device (something possessed) is Multifactor Authentication, combining two independent verification factors.

---

**Q198.** Why is MFA generally considered more secure than password-only authentication?

- **A.** It requires only one factor, making it simpler
- **B.** Even if a password is stolen, an attacker still needs the second independent factor to gain access **(Correct)**
- **C.** MFA eliminates the need for any authentication
- **D.** MFA is only used for low-security systems

**Answer:** B — Even if a password is stolen, an attacker still needs the second independent factor to gain access  
**Explanation:** Because MFA requires two or more independent factors, a stolen password alone is not enough for an attacker to gain access — they would also need the second factor, such as a registered device.

---

## Topic 13.3 — Passwordless Authentication

**Q199.** Which of these is an example of passwordless authentication?

- **A.** Entering a username and password only
- **B.** A FIDO2 security key the user taps or plugs in to authenticate **(Correct)**
- **C.** Typing a password twice for confirmation
- **D.** Using the same password across multiple sites

**Answer:** B — A FIDO2 security key the user taps or plugs in to authenticate  
**Explanation:** A FIDO2 security key is a physical hardware key used for passwordless authentication, removing the password entirely from the sign-in process.

---

**Q200.** Which passwordless method uses biometrics (fingerprint or facial recognition) or a PIN tied to a specific device?

- **A.** Windows Hello for Business **(Correct)**
- **B.** FIDO2 security key
- **C.** Password reset policy
- **D.** Single Sign-On

**Answer:** A — Windows Hello for Business  
**Explanation:** Windows Hello for Business uses biometrics or a device-specific PIN for passwordless authentication, tying the credential to a specific device.

---

**Q201.** Why is passwordless authentication generally considered more secure AND more convenient than password-plus-MFA?

- **A.** It adds a third factor on top of MFA, making it slower
- **B.** It removes the password (the weakest link) entirely, relying instead on something the user has or is **(Correct)**
- **C.** It eliminates the need for any verification at all
- **D.** It only works for government accounts

**Answer:** B — It removes the password (the weakest link) entirely, relying instead on something the user has or is  
**Explanation:** Passwordless authentication removes passwords — the weakest and most commonly compromised factor — entirely from the process, relying instead on possession (a device/key) or inherence (biometrics), which is both more secure and more convenient.

---

## Topic 14 — Role-Based Access Control (RBAC)

**Q202.** What are the three key components of an RBAC role assignment?

- **A.** Username, password, and email
- **B.** Security Principal, Role Definition, and Scope **(Correct)**
- **C.** Region, Subscription, and VNet
- **D.** Resource Group, Storage Tier, and Redundancy

**Answer:** B — Security Principal, Role Definition, and Scope  
**Explanation:** An RBAC assignment consists of a Security Principal (who), a Role Definition (what permissions), and a Scope (where in the resource hierarchy it applies).

---

**Q203.** A junior developer is assigned the 'Reader' role on a resource group. What can they do?

- **A.** Create and modify resources, but not grant access to others
- **B.** Only view resources, without making any changes **(Correct)**
- **C.** Have full control, including granting access to others
- **D.** Delete the resource group

**Answer:** B — Only view resources, without making any changes  
**Explanation:** The 'Reader' role grants only view/read access to resources, without the ability to create, modify, or delete anything.

---

**Q204.** What distinguishes the 'Contributor' role from the 'Owner' role in RBAC?

- **A.** There is no difference between them
- **B.** Contributor can create/modify resources but cannot grant access to others; Owner can do both **(Correct)**
- **C.** Owner can only view resources; Contributor has full control
- **D.** Contributor applies only to storage accounts

**Answer:** B — Contributor can create/modify resources but cannot grant access to others; Owner can do both  
**Explanation:** Contributor allows creating and modifying resources but NOT granting access to other users; Owner has full control, including the ability to assign roles and grant access to others.

---

**Q205.** An Owner role is assigned at the subscription level. Does this automatically apply to a resource group named 'Dev-RG' within that subscription?

- **A.** No, roles never inherit across the hierarchy
- **B.** Yes, due to inheritance, the Owner role automatically applies to 'Dev-RG' and every resource inside it **(Correct)**
- **C.** Only if 'Dev-RG' is manually added to the role assignment
- **D.** Only for the Reader role, not Owner

**Answer:** B — Yes, due to inheritance, the Owner role automatically applies to 'Dev-RG' and every resource inside it  
**Explanation:** Consistent with the resource hierarchy's inheritance rule, a role assigned at the subscription level automatically applies to all resource groups and resources beneath it, including 'Dev-RG.'

---

**Q206.** What principle does RBAC follow by granting users only the minimum permissions needed for their job?

- **A.** Economies of scale
- **B.** Principle of least privilege **(Correct)**
- **C.** Elasticity
- **D.** Global reach

**Answer:** B — Principle of least privilege  
**Explanation:** RBAC follows the principle of least privilege — granting identities only the minimum permissions necessary to perform their required tasks, reducing security risk.

---

**Q207.** What is the key difference between what Microsoft Entra ID and RBAC each control?

- **A.** They control the exact same thing with no distinction
- **B.** Microsoft Entra ID answers 'who is this identity' (authentication); RBAC answers 'what can this identity do' (authorization) **(Correct)**
- **C.** RBAC manages identities; Microsoft Entra ID manages permissions
- **D.** Neither relates to security

**Answer:** B — Microsoft Entra ID answers 'who is this identity' (authentication); RBAC answers 'what can this identity do' (authorization)  
**Explanation:** Microsoft Entra ID handles authentication (verifying who a user is), while RBAC handles authorization (determining what that verified identity is permitted to do) — the two work together but serve distinct purposes.

---
