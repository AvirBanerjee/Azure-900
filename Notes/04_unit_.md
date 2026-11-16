# AZ-900: Microsoft Azure Fundamentals
## Unit 4 — Security, Governance, and Compliance

**Course Outcome Covered:** CO4 — Explain Azure security, governance and compliance mechanisms.

**Note on scope:** The syllabus lists Azure Security Concepts, Zero Trust Principles, Multifactor Authentication, Conditional Access, Azure Policy, Resource Locks, Tagging, Compliance Offerings, and Microsoft Purview Overview. 


**Prerequisites used in this unit:** Shared Responsibility Model (Unit 1, Section 5), Resource Hierarchy and Resource Groups (Unit 2, Sections 4–7), Azure Resource Manager (Unit 2, Section 8), NSGs, Azure Firewall and Application Gateway WAF (Unit 3), Microsoft Entra ID, authentication methods, and RBAC (Unit 3, Sections 12–14).

---

# PART A — AZURE SECURITY CONCEPTS

## 1. Azure Security Concepts

**Cloud security** is the set of policies, controls, and technologies used to protect data, applications, and infrastructure in the cloud. Security in Azure is a **shared effort** between Microsoft and the customer (Unit 1, Section 5).

### 1.1 Security Responsibility Recap

| Responsibility | IaaS | PaaS | SaaS |
|---|---|---|---|
| Physical datacenter, network, and hosts | Microsoft | Microsoft | Microsoft |
| Operating system and patching | Customer | Microsoft | Microsoft |
| Network controls (NSG rules, firewalls) | Customer | Shared | Microsoft |
| Applications | Customer | Customer | Microsoft |
| Identity and access management | Customer | Customer | Customer |
| Data and its classification | Customer | Customer | Customer |
| Endpoints (devices used to reach the cloud) | Customer | Customer | Customer |

**Key rule:** Data, identity, and endpoints are always the customer's responsibility. Microsoft secures the cloud infrastructure; the customer secures what they put in it and who can access it.

### 1.2 The CIA Triad

Security goals are commonly described by three properties:

| Property | Meaning | Azure example |
|---|---|---|
| **Confidentiality** | Only authorized parties can read data | RBAC, encryption of storage, MFA |
| **Integrity** | Data is not altered by unauthorized parties | Resource locks, access control on write operations |
| **Availability** | Data and services are accessible when needed | Availability Zones, redundancy, load balancing (Units 1–3) |

### 1.3 Defense in Depth (AZ-900 Add-on)

**Defense in depth** is a layered security strategy. Instead of relying on one protection, several independent layers are used, so that if one layer is breached, the next layer still protects the data. The goal is to slow an attacker down and limit the damage.

**The seven layers (outermost to innermost):**

| Layer | What it protects against | Azure features from this course |
|---|---|---|
| 1. Physical security | Physical access to datacenters | Microsoft-managed datacenters (always the provider's responsibility) |
| 2. Identity and access | Unauthorized sign-in and excess permissions | Microsoft Entra ID, MFA, Conditional Access, RBAC |
| 3. Perimeter | Large-scale attacks from outside the network | Edge protections such as DDoS protection |
| 4. Network | Unauthorized communication between resources | NSGs, Azure Firewall, subnet segmentation, VNet design |
| 5. Compute | Exposed or unpatched servers | Patching VMs, limiting open management ports |
| 6. Application | Insecure application code and web attacks | Secure coding, Web Application Firewall on Application Gateway |
| 7. Data | Theft or exposure of stored information | Encryption, access control, storage redundancy and backup |

**Example:**
An attacker steals an employee's password. Because the company uses defense in depth, the identity layer (MFA) stops the sign-in. Even if it had not, the network layer (an NSG on the database subnet that only accepts traffic from the web subnet) would block direct access to the database, and encryption at the data layer would protect the stored records.

### 1.4 Microsoft Defender for Cloud (AZ-900 Add-on)

**Microsoft Defender for Cloud** is a cloud-native security service that gives **security posture management** and **threat protection** for workloads in Azure, on-premises, and other cloud providers.

| Capability | Meaning |
|---|---|
| **Security posture management** | Continuously assesses resources against security best practices, produces prioritized **recommendations**, and calculates a **Secure Score**, a percentage showing how well the environment is secured |
| **Workload threat protection** | Detects and alerts on threats against resources such as VMs, storage accounts, databases, and containers |
| **Multi-environment coverage** | Covers Azure, on-premises servers, and other clouds |
| **Regulatory compliance view** | Shows how resources measure against compliance standards (see Section 10) |

**Example:**
Defender for Cloud scans a subscription and reports that a VM has a management port open to the internet and that a storage account allows public access. The Secure Score is low and a prioritized list of fixes is shown. After the team closes the port and restricts the storage account, the Secure Score rises.

### 1.5 Other Azure Security Services to Recognize (AZ-900 Add-on)

| Service | Purpose |
|---|---|
| Azure DDoS Protection | Protects public-facing resources from distributed denial-of-service attacks (perimeter layer) |
| Azure Key Vault | Securely stores secrets, keys, and certificates so they are not placed in application code |
| Azure Firewall / NSG | Network traffic filtering (Unit 3, Sections 5 and 6.1) |

**Exam Tip:** When a question asks which tool gives a **Secure Score and recommendations** for the whole environment, the answer is Microsoft Defender for Cloud.

---

# PART B — ZERO TRUST

## 2. Zero Trust Principles

**Zero Trust** is a security model that assumes **no user, device, application, or network location is trusted by default**, even inside the corporate network. Every access request is verified before it is allowed. The short form is: **"never trust, always verify."**

### 2.1 Traditional Perimeter Model vs Zero Trust

| Aspect | Traditional (perimeter) model | Zero Trust model |
|---|---|---|
| Trust assumption | Anything inside the corporate network is trusted | Nothing is trusted by default, wherever it is |
| Main defense | A strong network boundary (firewall) | Identity and continuous verification on every request |
| Access scope | Broad access once inside | Minimal, task-specific access |
| Response to a breach | Attackers can move freely once inside | Damage is contained by segmentation and monitoring |
| Fit for cloud and remote work | Poor, because users and data are outside the boundary | Good, because verification does not depend on location |

### 2.2 The Three Guiding Principles

| Principle | Meaning | How it is applied in Azure |
|---|---|---|
| **Verify explicitly** | Always authenticate and authorize using all available signals: identity, location, device health, application, and risk | Microsoft Entra ID, MFA, Conditional Access |
| **Use least privilege access** | Give users only the access they need, for the time they need it | RBAC with the narrowest role and scope (Unit 3, Section 14) |
| **Assume breach** | Design as if an attacker is already inside; limit the blast radius, segment, encrypt, and monitor | Subnet segmentation with NSGs, Azure Firewall, encryption, Defender for Cloud |

### 2.3 Zero Trust Pillars (AZ-900 Add-on)

Zero Trust is applied across six areas, sometimes called pillars:

| Pillar | Example control |
|---|---|
| Identities | MFA and Conditional Access for every user |
| Endpoints (devices) | Only compliant, managed devices may access resources |
| Applications | Access to each application is verified and limited |
| Data | Classify, label, and encrypt sensitive data |
| Infrastructure | Harden and monitor VMs, containers, and services |
| Network | Segment networks, filter traffic, avoid implicit trust between subnets |

**Example:**
An employee in the office tries to open a sensitive application. Under a perimeter model, being on the office network is enough. Under Zero Trust, the system still verifies the identity with MFA, checks that the laptop is compliant, and grants only the role needed for that application, with no extra access to unrelated systems.

**Exam Tip:** "Verify explicitly, least privilege, assume breach" are the three principles. A question describing "do not trust a request just because it comes from the internal network" is describing Zero Trust.

---

# PART C — IDENTITY PROTECTION

## 3. Multifactor Authentication (MFA)

**Multifactor Authentication (MFA)** requires a user to prove their identity using **two or more independent factors** before access is granted. Passwords alone are the weakest control because they can be guessed, phished, or reused (Unit 3, Section 13).

### 3.1 The Three Factor Categories

| Category | Meaning | Examples |
|---|---|---|
| **Something you know** | A secret the user remembers | Password, PIN |
| **Something you have** | A physical item the user possesses | Phone with an authenticator app, hardware security key |
| **Something you are** | A biometric characteristic | Fingerprint, face recognition |

**Important:** MFA means factors from **different categories**. Two passwords are not MFA, because both are "something you know."

### 3.2 How MFA Works in Microsoft Entra ID

1. The user enters their username and password (first factor).
2. Entra ID asks for a second verification, such as approving a notification in the Microsoft Authenticator app.
3. Access is granted only if both succeed.

**Why it matters:** If an attacker steals or guesses the password, they still cannot sign in without the second factor. MFA blocks the large majority of account-compromise attacks that rely on stolen passwords.

### 3.3 MFA Verification Methods

| Method | Description |
|---|---|
| Microsoft Authenticator app | Push notification to approve (with number matching), or a one-time code |
| FIDO2 security key | Physical USB/NFC key used to authenticate |
| Windows Hello for Business | Biometric or device-bound PIN |
| OATH hardware or software tokens | Generate time-based one-time codes |
| SMS or voice call | A code or call to the registered phone; convenient but considered less secure than the app or a security key |

**Number matching (AZ-900 Add-on):** To reduce "MFA fatigue" attacks, where an attacker repeatedly triggers approval prompts hoping the user taps "Approve" by mistake, the Authenticator app requires the user to type the number shown on the sign-in screen.

**Example:**
An employee signs in with the correct password and is prompted to approve a sign-in on the registered phone. The login screen shows the number 47, and the employee must enter 47 in the Authenticator app. A remote attacker who only has the stolen password cannot complete the sign-in.

### 3.4 Security Defaults (AZ-900 Add-on)

**Security defaults** are a set of free, preconfigured identity security settings in Microsoft Entra ID, designed to protect organizations that have no dedicated security team.

They:
- Require all users to register for MFA.
- Require administrators to use MFA.
- Block legacy authentication protocols that cannot do MFA.
- Require MFA for privileged activities, such as accessing the Azure management tools.

**Key facts:**
- They are on by default for new tenants and need no paid license.
- They cannot be mixed with Conditional Access. An organization that wants finer control **turns security defaults off** and uses Conditional Access instead (Section 4).

### 3.5 Self-Service Password Reset (SSPR) (AZ-900 Add-on)

**Self-Service Password Reset** lets users reset or unlock their own password without calling the help desk, after proving their identity using registered methods such as the Authenticator app or a verification code. It reduces help-desk load while keeping the reset itself secured by verification.

### 3.6 MFA vs Passwordless (Link to Unit 3)

| Approach | Password used? | Security level |
|---|---|---|
| Password only | Yes | Weakest |
| Password + MFA | Yes, plus a second factor | Strong |
| Passwordless (Windows Hello, Authenticator passwordless, FIDO2 key) | No | Strongest and most convenient |

**Exam Tip:** MFA is **authentication** (who are you). It does not decide what the user may do. That is the job of RBAC (authorization).

---

## 4. Conditional Access

**Conditional Access** is a feature of Microsoft Entra ID that uses **if-then policies** at sign-in to decide whether to allow access, require additional verification, or block. It is the practical engine for the Zero Trust principle "verify explicitly."

### 4.1 Structure of a Conditional Access Policy

| Part | Meaning | Examples |
|---|---|---|
| **Signals (the "if")** | Information collected about the sign-in attempt | User or group, location (IP address), device state, application being accessed, sign-in risk |
| **Decision (the "then")** | The result applied when the signals match | **Block** access, or **grant** access with requirements |
| **Grant controls** | Requirements that must be met to allow access | Require MFA, require a compliant device, require a password change |
| **Session controls** | Limits that apply during the session | Limit how long a session lasts, restrict what can be done in the app |

### 4.2 Key Facts

- Conditional Access policies are evaluated **after the first factor (usually the password) is completed**. It is not a first line of defense that replaces authentication.
- It requires a paid Microsoft Entra ID plan (**Entra ID P1** or higher). Basic MFA through security defaults is free.
- A new policy can first be run in **report-only mode**, which shows what would have happened without enforcing it. This avoids locking out users by mistake.
- Policies can target specific users, groups, applications, and locations, so different groups can get different rules.

### 4.3 Example Policies

| Scenario | Policy |
|---|---|
| Remote access | If a user signs in from outside the corporate network, then require MFA |
| Risky location | If a user signs in from a country where the company has no staff, then block access |
| Admins | If a user signs in to the Azure management portal as an administrator, then always require MFA |
| Unmanaged devices | If a user signs in from a personal device, then limit access to sensitive applications |

**Example:**
A company creates a policy: "If any user signs in from outside the corporate network, then require MFA." A sales employee working from a café is prompted for MFA, while the same employee in the office is not. A second policy blocks all sign-ins from a country where the company has no staff.

### 4.4 Security Defaults vs Conditional Access (Exam Comparison)

| Feature | Security Defaults | Conditional Access |
|---|---|---|
| Cost | Free | Requires Entra ID P1 or higher |
| Customization | None, a fixed set of protections | Fully customizable if-then policies |
| Typical user | Small organizations without a security team | Organizations needing granular control |
| Can both be used together | No, security defaults must be off when Conditional Access is used | |

### 4.5 MFA vs Conditional Access vs RBAC

| Feature | Question it answers |
|---|---|
| MFA | "Is this person really who they claim to be?" |
| Conditional Access | "Under what **conditions** (where, which device, how risky) should this sign-in be allowed, and what extra proof is needed?" |
| RBAC | "Once signed in, **what can** this person do, and where?" |

**Exam Tip:** MFA is one of the grant controls that Conditional Access can require. They work together, but Conditional Access is the policy engine and MFA is the verification step.

---

# PART D — GOVERNANCE

## 5. Azure Policy

**Azure Policy** is a governance service used to **create, assign, and manage rules that enforce standards on Azure resources and assess their compliance**. It checks the **properties of resources** against the organization's rules.

### 5.1 Key Concepts

| Concept | Meaning |
|---|---|
| **Policy definition** | A single rule written as a condition and an effect, for example "Allowed locations" or "Allowed virtual machine sizes" |
| **Initiative (policy set)** | A group of related policy definitions assigned together to achieve one goal, such as a regulatory standard |
| **Assignment** | Applying a definition or initiative to a **scope** (management group, subscription, resource group). It is inherited down the resource hierarchy (Unit 2, Section 7) |
| **Parameters** | Values that make a definition reusable, such as the list of allowed regions |
| **Exclusion** | A scope inside the assignment that is exempted |
| **Compliance state** | Whether each resource is compliant or non-compliant with the assigned policies |

Azure provides many **built-in** definitions, and custom definitions can be written (as JSON).

### 5.2 Policy Effects

| Effect | Behavior |
|---|---|
| **Deny** | Blocks the creation or update of a resource that violates the rule |
| **Audit** | Allows the resource but records it as non-compliant |
| **AuditIfNotExists** | Audits when a related resource that should exist is missing |
| **Append / Modify** | Adds or changes properties (such as tags) on the resource |
| **DeployIfNotExists** | Automatically deploys a related resource if it is missing |
| **Disabled** | The rule is turned off |

### 5.3 How Evaluation Works

- When a resource is **created or updated**, ARM (Unit 2, Section 8) checks the request against the assigned policies before the resource is created. A Deny effect stops the request.
- Existing resources are checked when a policy is assigned and during a regular compliance scan roughly once a day.
- **Existing non-compliant resources are flagged, not deleted.** The administrator can fix them manually or run a **remediation task** for effects such as Modify and DeployIfNotExists.
- Azure Policy applies **even to users with the Owner role**, because it controls resource properties, not user permissions.

### 5.4 Common Built-in Policies

| Policy | Purpose |
|---|---|
| Allowed locations | Restrict resources to approved regions (for example, India regions only) |
| Allowed virtual machine size SKUs | Restrict which VM sizes can be created |
| Require a tag and its value | Force every resource to carry a required tag |
| Inherit a tag from the resource group | Copy a tag from the resource group to resources that lack it |
| Not allowed resource types | Block certain services entirely |

**Example:**
A company assigns the built-in "Allowed locations" policy at the subscription level, permitting only India regions. A developer with the Contributor role then attempts to create a VM in a region outside India. ARM evaluates the request, the policy returns a Deny effect, and the deployment fails with a policy-violation error, even though RBAC would have allowed the developer to create VMs.

### 5.5 Practical Link (Experiment 9: Create and apply Azure Policy to restrict resource deployment)

1. In the Azure Portal open **Policy**, then **Definitions**, and search for "Allowed locations."
2. Select **Assign**, choose the scope (a subscription or a test resource group), and select the permitted regions as parameters.
3. Create the assignment and wait a few minutes for it to take effect.
4. Try to create a resource (for example, a storage account) in a region not on the list.
5. Observe the deployment being blocked with a policy-violation message, then open **Policy > Compliance** to see the assignment's state.
6. Remove the assignment afterwards to avoid blocking later labs.

---

## 6. Resource Locks

A **resource lock** prevents accidental **deletion or modification** of Azure resources, regardless of the user's permissions.

### 6.1 Lock Types

| Lock Type | Effect |
|---|---|
| **CanNotDelete** (shown as "Delete" in the Portal) | Authorized users can read and modify the resource, but cannot delete it |
| **ReadOnly** | Authorized users can only read the resource; they cannot modify or delete it |

### 6.2 Key Facts

- A lock applies to **all users and roles**, including Owners. To change or delete a locked resource, the lock must first be removed.
- Locks can be set at the subscription, resource group, or resource level, and are **inherited** by all child resources. The most restrictive lock applies.
- Only users with the **Owner** or **User Access Administrator** role (or equivalent permissions) can create or delete locks.
- Locks apply to **management-plane operations** (actions through ARM, such as delete or update of the resource). They do **not** stop actions inside the resource. For example, a lock on a storage account does not prevent deleting blobs, and a lock on a SQL Database does not prevent changing rows inside it.
- A ReadOnly lock can block actions that seem harmless. For example, starting or restarting a VM can be blocked by a ReadOnly lock, because those operations are write operations at the management level.

### 6.3 Locks and Resource Group Deletion

In Unit 2, Section 4, it was noted that deleting a resource group deletes every resource inside it. A **CanNotDelete lock on the resource group** is the standard protection against that accident.

**Example:**
The "WebApp-Prod" resource group holds a production VM, a storage account, and a virtual network. An administrator applies a CanNotDelete lock to the resource group. Later, a team member with the Contributor role tries to delete the group, and Azure refuses the request until the lock is removed by someone who has permission to manage locks.

---

## 7. Tagging

A **tag** is a **name-value pair** attached to a resource, resource group, or subscription to organize and describe it. Tags are metadata. They do not change how the resource works.

### 7.1 Common Uses

| Use | Example tags |
|---|---|
| Organization and ownership | `Owner = Rahul`, `Department = Finance` |
| Environment identification | `Environment = Production` / `Development` |
| Application grouping | `Application = StudentPortal` |
| Cost tracking (covered in Unit 5) | `CostCenter = CC-104` |
| Automation and governance | Policies and scripts that act on resources with a given tag |

### 7.2 Key Facts (Frequently Tested)

- Each resource, resource group, or subscription can have up to **50** tag name-value pairs.
- Tag **names are not case-sensitive** and tag **values are case-sensitive**.
- **Tags are NOT automatically inherited.** A tag on a resource group does not automatically appear on the resources inside it.
- To apply tags consistently:
  - Use Azure Policy: **"Require a tag and its value"** (Deny effect) forces a tag at creation, and **"Inherit a tag from the resource group"** (Modify effect) copies it.
  - Apply tags in templates or scripts at deployment time.
- Some resource types do not support tags.
- Tags help **find** resources across resource groups, for example all resources with `Environment = Production` in every group.

**Example:**
A company has VMs, databases, and storage accounts spread over eight resource groups. It tags every resource with `Environment` and `Owner`. An administrator can now search for every resource tagged `Environment = Development`, even though they sit in different groups, and review them for deletion. A policy requiring the `Owner` tag makes any new resource without it fail to deploy.

---

## 8. Azure Policy vs RBAC vs Resource Locks vs Tags (AZ-900 Add-on)

These governance features are often confused because several of them limit what can happen in Azure.

| Feature | Question it answers | Focus | Example |
|---|---|---|---|
| **RBAC** (Unit 3) | "What can this **user** do?" | User actions (authorization) | A Reader cannot create VMs |
| **Azure Policy** | "What **state** may resources be in?" | Resource properties and compliance | VMs may only be created in India regions, even by an Owner |
| **Resource Lock** | "Can this resource be **deleted or changed** at all?" | Protection from accidental change | A production resource group cannot be deleted until the lock is removed |
| **Tag** | "How is this resource **labeled**?" | Organization and reporting (no enforcement by itself) | `Environment = Production` |

**Scenario combining all four:**
A user with the Contributor role (RBAC allows creating resources) tries to deploy a VM in a disallowed region. RBAC permits the action, but Azure Policy denies it. The same user then tries to delete the production resource group. RBAC permits that too, but a CanNotDelete lock blocks it. A "Require tag" policy also ensures every new resource carries an `Owner` tag, so the administrator can later find who created each resource.

**Exam Tip:** If the question is about **who** may perform an action, think RBAC. If it is about **what resources are allowed to look like**, think Policy. If it is about **preventing accidental deletion**, think locks.

---

## 9. Cloud Adoption Framework (AZ-900 Add-on)

The **Microsoft Cloud Adoption Framework for Azure** is a collection of guidance, best practices, and tools that helps an organization plan and carry out its move to the cloud, with governance as one of its parts.

| Phase | Purpose |
|---|---|
| Strategy | Define business justification and goals for moving to the cloud |
| Plan | Create an adoption plan aligned to those goals, including skills and workload inventory |
| Ready | Prepare the environment, including the landing zone where workloads will run |
| Adopt | Migrate existing workloads and build or modernize new ones |
| Govern | Set up governance: policies, cost control, compliance |
| Manage | Operate the environment: monitoring, operations, resilience |

**Note on Azure Blueprints:** Older AZ-900 question banks describe Azure Blueprints as a way to package ARM templates, policy assignments, and role assignments into a repeatable environment definition. Microsoft has announced the retirement of Azure Blueprints, and the current exam focuses on Azure Policy, locks, and tags. Know the term for older material, but do not teach it as the recommended approach.

---

# PART E — COMPLIANCE

## 10. Compliance Offerings

**Compliance** means meeting the legal, regulatory, and industry standards that apply to an organization, such as rules about data privacy and financial security. Microsoft provides evidence that Azure meets many such standards, and gives customers tools to prove their own compliance.

### 10.1 Compliance Offerings in Azure

Azure holds a large portfolio of certifications and attestations, covering global, industry, regional, and government standards. Examples include:

| Type | Examples |
|---|---|
| Global security standards | ISO/IEC 27001 and related ISO standards, SOC 1, SOC 2, SOC 3 |
| Payment industry | PCI DSS |
| Healthcare | HIPAA |
| Privacy law support | GDPR (European Union) |
| Government | FedRAMP (United States) |

The full, current list is published in **Azure compliance documentation**, searchable by standard, industry, and region.

### 10.2 Compliance Resources from Microsoft

| Resource | What it provides |
|---|---|
| **Microsoft Trust Center** | Information about how Microsoft approaches security, privacy, compliance, and transparency |
| **Service Trust Portal (STP)** (AZ-900 Add-on) | Audit reports, certifications, and compliance documents (for example, ISO and SOC reports) that customers can download for their own auditors |
| **Compliance Manager** (AZ-900 Add-on) | A tool that provides assessments against regulatory standards, a compliance score, and recommended actions to improve it. It is part of Microsoft Purview |
| **Microsoft Privacy Statement** | Explains what personal data Microsoft processes, how, and why |
| **Online Services Terms and Data Protection Addendum** | Contractual commitments on how Microsoft handles customer data |
| **Azure Policy regulatory compliance** | Built-in initiatives mapped to standards, showing which resources comply (Section 5) |

### 10.3 Special Compliance Regions

Some standards require data and operations to stay inside a specific country or government environment. Azure offers **sovereign or isolated regions**, such as Azure Government and a China region operated by a local partner (Unit 2, Section 2.2), with restricted access and their own compliance coverage.

### 10.4 Compliance Is Also a Shared Responsibility

**Microsoft's certification does not make the customer compliant automatically.** Azure being certified for a standard means the platform meets the standard. The customer must still configure their own resources, access, and data handling correctly.

**Example:**
A hospital must show that its patient data platform meets HIPAA requirements. The compliance officer downloads Microsoft's audit reports from the Service Trust Portal to prove that the Azure platform is audited. The hospital then uses Compliance Manager to assess its own configuration, and Azure Policy to enforce that data is stored only in approved regions.

**Exam Tip:** If a question asks where to find Microsoft's **audit reports and certifications** for an auditor, the answer is the **Service Trust Portal**. If it asks for a **compliance score and assessments** for the organization's own environment, the answer is **Compliance Manager**.

---

## 11. Microsoft Purview Overview

**Microsoft Purview** is a family of data governance, data security, and risk and compliance solutions. It helps an organization **understand, govern, and protect its data wherever it lives**: on-premises, in multiple clouds, and in SaaS applications.

### 11.1 Why It Is Needed

Organizations store data across databases, file shares, Blob Storage, and SaaS applications. Without a clear view, they cannot answer: What data do we have? Where is it? How sensitive is it? Who can access it? Does it meet regulatory requirements?

### 11.2 Main Solution Areas

| Area | Purpose | Examples |
|---|---|---|
| **Data governance** | Discover, catalog, and understand data across the organization | **Data Map** (scans and classifies data sources), **Unified Catalog** (searchable inventory of data assets), **data lineage** (where data came from and how it moved) |
| **Data security** | Protect sensitive data | **Sensitivity labels** (classify and protect documents and data), **Data Loss Prevention (DLP)** (prevent sensitive data being shared inappropriately), Insider Risk Management |
| **Risk and compliance** | Meet regulatory and legal requirements | **Compliance Manager**, **eDiscovery** (find data for legal cases), **Audit** (record user and admin activity), data lifecycle management (retention and deletion rules) |

### 11.3 Key Points for AZ-900

- Purview provides a **unified** view across on-premises, multicloud, and SaaS data, not just Azure.
- It helps with **governance** (knowing the data) and **compliance** (proving requirements are met).
- Purview works with the other Unit 4 tools. Policy and Defender for Cloud protect and assess resources, while Purview focuses on the **data itself**.

**Example:**
A university stores student records in Azure SQL Database, documents in Blob Storage, and exam files on an on-premises server. It uses Microsoft Purview to scan these sources, discover where personal student data is stored, and classify it as sensitive. Sensitivity labels then protect the documents, and Compliance Manager helps the university show an auditor that it handles student data according to privacy rules.

**Exam Tip:** A scenario describing "discover, classify, and govern data across on-premises and multiple clouds" points to Microsoft Purview. Do not confuse it with Defender for Cloud, which assesses and protects **resources and workloads**, not data inventory.

---

## Unit 4 Summary (Quick Revision)

**Security Concepts**
- Security is shared: data, identity, and endpoints are always the customer's responsibility; the physical infrastructure is always Microsoft's.
- **Defense in depth** has seven layers: Physical, Identity and access, Perimeter, Network, Compute, Application, Data.
- **Microsoft Defender for Cloud:** security posture management, Secure Score, recommendations, and threat protection across Azure, on-premises, and other clouds.

**Zero Trust**
- "Never trust, always verify." Three principles: **verify explicitly**, **use least privilege access**, **assume breach**.
- Replaces the perimeter assumption that everything inside the network is trusted.

**MFA and Conditional Access**
- MFA needs factors from **different** categories: know, have, are. It blocks most attacks that use stolen passwords.
- **Security defaults:** free, fixed protections (MFA for all, MFA for admins, block legacy authentication). **Self-Service Password Reset** lets users reset their own passwords.
- **Conditional Access:** if-then sign-in policies (signals, then block or grant with requirements). Applied after the first factor, requires Entra ID P1 or higher, and can run in report-only mode. It cannot be used together with security defaults.

**Governance**
- **Azure Policy:** enforces rules on **resource properties**; effects include Deny, Audit, Modify, DeployIfNotExists; evaluates existing resources and flags, not deletes, non-compliant ones; applies even to Owners.
- **Resource Locks:** CanNotDelete and ReadOnly; apply to all users including Owners; inherited; only affect management-plane operations.
- **Tagging:** name-value metadata, up to 50 per resource; **not inherited** by default (use Policy to enforce or inherit).
- **RBAC** controls what users can do; **Policy** controls what resources may look like; **Locks** prevent accidental deletion or change; **Tags** organize.
- **Cloud Adoption Framework:** Strategy, Plan, Ready, Adopt, Govern, Manage.

**Compliance**
- Azure holds many certifications (ISO 27001, SOC, PCI DSS, HIPAA, FedRAMP, and more); details live in Azure compliance documentation.
- **Service Trust Portal:** audit reports for auditors. **Compliance Manager:** compliance score and assessments. **Trust Center** and **Privacy Statement:** security and privacy information.
- Microsoft's certification does not make the customer automatically compliant.
- **Microsoft Purview:** unified data governance, data security, and compliance across on-premises, multicloud, and SaaS data.

---

## Practice Questions (Self-Check)

1. In the Shared Responsibility Model, which three areas are always the customer's responsibility regardless of service model?
2. Name the seven layers of defense in depth and give one Azure feature from Units 1–3 for three of them.
3. What does the Secure Score in Microsoft Defender for Cloud represent, and what does the service do besides scoring?
4. State the three principles of Zero Trust. Explain how a traditional perimeter model differs from Zero Trust.
5. Why are a password and a PIN together not considered multifactor authentication?
6. An attacker has stolen an employee's password. Explain how MFA stops the attack, and what "number matching" adds.
7. What are security defaults, and why can they not be used together with Conditional Access?
8. Describe the structure of a Conditional Access policy (signals, decisions, grant controls) using the example "require MFA when signing in from outside the corporate network."
9. Why is report-only mode useful when introducing a new Conditional Access policy?
10. A user with the Contributor role tries to create a VM in a region that an Azure Policy forbids. Will the deployment succeed? Explain which feature decides.
11. What happens to resources that already violate a newly assigned Azure Policy? Are they deleted?
12. Distinguish the CanNotDelete lock from the ReadOnly lock. Does a lock stop a user with the Owner role?
13. A CanNotDelete lock is placed on a storage account. Can a user still delete blobs inside it? Why or why not?
14. A tag is applied to a resource group. Do the resources inside it automatically have the tag? How can this be made automatic?
15. Using a scenario, explain the difference between RBAC, Azure Policy, and resource locks.
16. Where would an organization download Microsoft's audit reports for an external auditor, and which tool gives it a compliance score for its own environment?
17. Does Azure's ISO 27001 certification mean the customer's own application is automatically ISO 27001 compliant? Explain.
18. A company needs to discover and classify sensitive data stored in Azure SQL Database, Blob Storage, and an on-premises file server. Which Azure service is designed for this, and how does it differ from Defender for Cloud?

*(Answers to be discussed in class. Practical sessions map to Experiment 7 (Entra ID users and RBAC permissions, with MFA and Conditional Access discussed alongside) and Experiment 9 (create and apply Azure Policy).)*