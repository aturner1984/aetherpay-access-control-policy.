# Enterprise Access Control Policy (v2.0)

**Organization:** AetherPay Inc.  
**Document Owner:** Head of Information Security / GRC Lead  
**Effective Date:** October 2026  
**Classification:** Internal Security Document  
**Target Compliance:** NIST SP 800-53 Rev. 5 (AC / IA series), SOC 2 CC6.1/CC6.2, PCI-DSS v4.0 (Req 7 & 8), ISO 27001:2022 (A.9)  

---

## 1. Purpose & Scope
This policy establishes mandatory requirements for managing identity, authentication, and logical access across all cloud infrastructure, microservices, databases, and corporate applications operated by AetherPay Inc. This policy applies to all full-time employees, contractors, third-party vendors, and system service accounts.

---

## 2. Fundamental Access Control Principles

### 2.1 Least Privilege & Need-to-Know
Access permissions must be granted strictly based on the minimum privileges necessary to perform assigned job functions. Broad administrative access (e.g., AWS `AdministratorAccess`) is prohibited for standard daily operational accounts.

### 2.2 Role-Based Access Control (RBAC) & Single Sign-On (SSO)
All user identities must be provisioned through AetherPay's central Identity Provider (IdP / Okta). Direct local account creation on production servers or databases is strictly forbidden unless managed via automated configuration tools.

---

## 3. Authentication & Credential Standards

### 3.1 Multi-Factor Authentication (MFA)
* **Mandatory Usage:** Multi-Factor Authentication (MFA) is strictly required for **100% of human accounts** accessing AetherPay systems, cloud environments (AWS/GCP), code repositories (GitHub), and corporate applications.
* **Approved MFA Methods:** FIDO2 WebAuthn security keys or Time-based One-Time Password (TOTP) authenticator apps. SMS/voice-call authentication is prohibited due to SIM-swapping vulnerabilities.
* **Conditional Access:** Step-up MFA is enforced when logging in from new devices, unmanaged IP addresses, or untrusted geographic locations.

### 3.2 Non-Human Identity & Service Account Management
* **No Plaintext Hardcoding:** Service accounts, API tokens, and database credentials must never be embedded in source code, scripts, or configuration files.
* **Runtime Secret Injection:** Machine authentication must utilize dynamic short-lived session tokens (AWS STS / HashiCorp Vault) or IAM Roles for Service Accounts (IRSA).
* **Interactive Login Restriction:** Interactive shell or GUI login capability must be disabled for all non-human service accounts.

---

## 4. User Lifecycle Management

### 4.1 Onboarding & Provisioning
Access requests must be submitted via Jira Service Desk and require explicit sign-off from the user's direct manager and the resource owner prior to provisioning.

### 4.2 Offboarding & Deprovisioning
* **Full-Time Employees:** Accounts must be disabled immediately upon HR status change, not to exceed **2 hours** from termination time.
* **Contractors & Third Parties:** Contractor accounts are assigned a hard expiration date not exceeding 90 days, requiring quarterly managerial re-certification.

### 4.3 Periodic User Access Reviews (UAR)
GRC conducts formal User Access Reviews on a scheduled cadence:
* **Production Cloud & Financial Infrastructure:** Monthly review.
* **General SaaS & Corporate Tools:** Quarterly review.
* Inactive accounts without login activity for **30 days** are automatically disabled.

---

## 5. Policy Exceptions & Enforcement
Compliance with this policy is mandatory. Employees requiring temporary workarounds due to technical legacy constraints must submit a formal **Policy Exception Request** following the AetherPay Exception Governance Process. Unapproved policy bypasses represent security violations subject to disciplinary action.
