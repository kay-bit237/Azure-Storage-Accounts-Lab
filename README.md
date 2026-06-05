# Microsoft Azure — Storage Accounts Implementation

> **Domain:** Cloud Infrastructure & Data Management | **Platform:** Microsoft Azure | **Level:** Foundational

---

## Executive Summary

This project documents the creation and configuration of Azure Storage Accounts as part of a structured Microsoft Azure cloud training program. The exercise explored how cloud storage works beneath the surface — covering redundancy models, availability options, security configurations, and data durability — demonstrating that storage infrastructure is far more strategic than it first appears.

---

## Objectives

- Provision and configure Azure Storage Accounts within a cloud environment
- Understand the role of storage as the backbone of cloud data infrastructure
- Evaluate redundancy and availability options to ensure data durability
- Apply baseline security configurations to protect stored data
- Recognize how foundational storage decisions impact long-term cloud architecture

---

## Environment & Technologies

| Component | Description |
|---|---|
| **Microsoft Azure** | Cloud hosting and administration platform |
| **Azure Storage Accounts** | Scalable cloud storage for files, images, backups, and application data |
| **Azure Portal** | Web-based interface used for provisioning and configuration |
| **Redundancy Models** | LRS, ZRS, GRS, GZRS — controlling availability and durability of stored data |

---

## What is an Azure Storage Account?

An Azure Storage Account is the foundational unit of cloud storage in Microsoft Azure. It serves as a centralized container for storing virtually any type of data — files, images, backups, logs, and application data — in a secure, scalable, and highly available environment.

What makes it more than "just storage" is the control it gives you:
- **You define how available your data should be** — choosing between local, zone, or geo-redundant storage
- **You define how durable it should be** — built-in redundancy protects data even in the event of hardware or regional failures
- **You control who can access it** — security settings at the account level govern exposure of sensitive information

---

## Implementation

### Phase 1 — Storage Account Provisioning

A new Storage Account was created in the Azure Portal with the following configurations:

| Setting | Value |
|---|---|
| **Subscription** | Azure Training Subscription |
| **Resource Group** | Lab-ResourceGroup |
| **Storage Account Name** | Defined per lab requirements |
| **Region** | Selected based on proximity and availability |
| **Performance Tier** | Standard |
| **Redundancy** | Locally Redundant Storage (LRS) |

---

### Phase 2 — Redundancy & Availability Configuration

#### What is Redundancy?
Redundancy means Azure automatically makes **multiple copies of your data** to protect it from being lost if something fails — whether that's a hard drive, a building, or an entire region. The redundancy model you choose at provisioning time directly determines how resilient your data is.

---

#### 🟢 LRS — Locally Redundant Storage
- **What it does:** Makes **3 copies** of your data within the **same datacenter**
- **Think of it as:** 3 USB drives stored in the same room
- **Protected against:** Individual hard drive or server failure
- **NOT protected against:** Fire, flood, or power outage affecting the entire building
- **Best for:** Dev/test environments, non-critical data
- **Cost:** $ — Cheapest option

---

#### 🔵 ZRS — Zone Redundant Storage
- **What it does:** Makes **3 copies** spread across **3 different availability zones** in the same region
- **Think of it as:** 3 USB drives stored in 3 different buildings in the same city
- **Protected against:** One entire datacenter or availability zone going down
- **Best for:** Applications requiring high availability and uptime
- **Cost:** $$ — Mid-range

---

#### 🟡 GRS — Geo Redundant Storage
- **What it does:** Makes **6 copies** — 3 in your primary region and 3 in a **completely different region** (e.g. East US → West US)
- **Think of it as:** 3 USB drives in New York AND 3 USB drives in California
- **Protected against:** An entire region going down due to natural disaster or major outage
- **Best for:** Business-critical data that must survive regional failures
- **Cost:** $$$ — Higher

---

#### 🔴 GZRS — Geo-Zone Redundant Storage
- **What it does:** Combines ZRS + GRS — copies spread across **multiple zones AND multiple regions**
- **Think of it as:** The best of both worlds — zone resilience plus geographic separation
- **Protected against:** Both zone-level and region-level failures
- **Best for:** Enterprise-critical data requiring maximum durability
- **Cost:** $$$$ — Most expensive

---

#### Redundancy Comparison

| Model | Copies | Location | Best For | Cost |
|---|---|---|---|---|
| **LRS** | 3 | Same datacenter | Dev/test | $ |
| **ZRS** | 3 | 3 zones, same region | High availability | $$ |
| **GRS** | 6 | 2 different regions | Business-critical | $$$ |
| **GZRS** | 6+ | Zones + 2 regions | Maximum durability | $$$$ |

---

### Phase 3 — Security Configuration

Baseline security settings were reviewed and applied to protect stored data:

| Security Setting | Configuration | Purpose |
|---|---|---|
| **Secure Transfer Required** | Enabled | Enforces HTTPS for all data transfers |
| **Blob Public Access** | Disabled | Prevents unauthorized public access to data |
| **Minimum TLS Version** | TLS 1.2 | Ensures encrypted, up-to-date communication |
| **Storage Account Key Access** | Reviewed | Controls programmatic access to the account |

---

## Key Observations

**Storage is strategic, not just operational.**
The redundancy model selected at creation time directly determines how resilient your data is to failures — a decision that cannot be changed easily after deployment.

**Small configurations have large downstream impact.**
Disabling public blob access or enforcing secure transfer may seem minor, but these settings are the difference between a secure environment and an exposed one.

**Cloud storage maps directly to real-world security concerns.**
Misconfigured storage accounts are one of the most common causes of cloud data breaches — making this foundational knowledge critical for any security professional.

---

## Security Relevance for SOC Analysts

As a SOC Analyst, understanding Azure Storage is directly relevant to threat detection and incident response:

| Scenario | SOC Relevance |
|---|---|
| Public blob access enabled | Data exposure risk — potential misconfiguration alert |
| Unusual storage access patterns | Indicator of compromise or data exfiltration |
| Disabled secure transfer | Unencrypted data in transit — compliance violation |
| Excessive key usage | Potential credential abuse or unauthorized access |
| LRS used for sensitive data | Business continuity risk — flag as a security finding |

---

## 📸 Screenshots

### Storage Account Created
![Storage Account Overview](assets/storage-account-overview.png)

### Redundancy Configuration
![Redundancy Settings](assets/redundancy-settings.png)

### Security Settings
![Security Configuration](assets/security-settings.png)

---

## Key Takeaways

- Azure Storage Accounts are the backbone of cloud data infrastructure — not a peripheral service
- Redundancy models must be chosen deliberately based on availability and recovery requirements
- Security configurations at the storage layer are critical to preventing data exposure
- For SOC professionals, storage misconfigurations are a high-priority detection area in cloud environments
- Every configuration decision made today has architectural and security implications tomorrow

---

## Skills Demonstrated

`Microsoft Azure` `Azure Storage Accounts` `Cloud Infrastructure` `Data Redundancy`
`Cloud Security` `Security Configuration` `Azure Portal` `LRS / ZRS / GRS / GZRS`
`NIST 800-53` `ISO 27001`

---
