# Access Control Policy — Revision Changelog & Framework Crosswalk

**Document Reference:** Access Control Policy v1.0 (Legacy 2022) $\rightarrow$ v2.0 (Modernized 2026)  
**Author:** Senior GRC Analyst  

---

## 1. Executive Summary of Changes
The Access Control Policy was updated to reflect AetherPay’s transition to a multi-tenant cloud-native AWS architecture and compliance requirements for PCI-DSS v4.0. Major changes include mandatory SSO/MFA enforcement, explicit service account credential rules, and formal offboarding SLAs.

---

## 2. Detailed Change Comparison Table

| Policy Section | Legacy Policy (v1.0 - 2022) | Modernized Policy (v2.0 - 2026) | Primary Driver / Justification |
| :--- | :--- | :--- | :--- |
| **Authentication** | Passwords required (min 8 chars); MFA optional for internal network. | Mandatory MFA (FIDO2/TOTP) for 100% of human access. SMS prohibited. | NIST SP 800-63B / PCI-DSS v4.0 Req 8.4.2 |
| **Service Accounts** | Long-lived API keys permitted with manager sign-off. | Hardcoded credentials prohibited. Mandatory dynamic runtime secret injection. | Mitigate credential leaks in GitHub (Risk R-101) |
| **User Provisioning** | Email requests approved by IT Helpdesk lead. | Centralized SSO via Okta; manager + resource owner dual sign-off. | SOC 2 Trust Services Criteria CC6.1 |
| **Offboarding SLA** | Access revoked within 24–48 hours of HR notification. | Automated deprovisioning within **2 hours** of termination. | Prevent unauthorized access by departed contractors |
| **Access Reviews** | Annual manual spreadsheet reviews. | Monthly reviews for cloud/prod; quarterly reviews for SaaS. | ISO 27001 A.9.2.5 / SOC 2 CC6.2 |

---

## 3. Framework Control Crosswalk
[ Access Control Policy v2.0 Section ] ───► [ NIST SP 800-53 Rev. 5 ] ───► [ PCI-DSS v4.0 ] ───► [ SOC 2 TSC ]
Section 2.1 (Least Privilege)         ───► AC-6                     ───► Req 7.1.1       ───► CC6.1
Section 3.1 (Mandatory MFA)            ───► IA-2 (1), IA-2 (2)       ───► Req 8.4.2       ───► CC6.1
Section 3.2 (Service Account Secrets)  ───► IA-5 (1), SC-28           ───► Req 8.2.2       ───► CC6.1
Section 4.2 (2-Hour Offboarding)       ───► PS-4, AC-2 (3)           ───► Req 8.2.6       ───► CC6.2
Section 4.3 (User Access Reviews)      ───► AC-2 (2)                  ───► Req 7.2.2       ───► CC6.2
