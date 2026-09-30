# AetherPay Inc. Access Control Policy & Governance Exception Workflow

[![Framework: NIST SP 800-53](https://img.shields.io/badge/Framework-NIST%20SP%20800--53%20Rev.%205-blue)](https://csrc.nist.gov/publications/detail/sp/800-53/rev-5/final)
[![Compliance: PCI-DSS v4.0 & SOC 2](https://img.shields.io/badge/Compliance-PCI--DSS%20v4.0%20%7C%20SOC%202-green)](#)
[![Status: Complete](https://img.shields.io/badge/Status-Complete-brightgreen)](#)

## Executive Summary
This repository forms **Project 2** of the GRC portfolio for **AetherPay Inc.**, a hypothetical cloud-native FinTech processing $500M+ annually. 

This project demonstrates two core day-to-day responsibilities of a Senior GRC Analyst:
1. **Policy Modernization:** Updating legacy security policies to align with modern cloud security baselines, mandatory MFA, and strict IAM lifecycle standards.
2. **Policy Exception Governance:** Evaluating real-world business exception requests, quantifying operational risk, mandating technical compensating controls, and establishing formal approval guardrails.

---

## 📁 Repository Architecture
├── README.md                           # Main project overview & executive context
├── policy/
│   ├── Access_Control_Policy_v2.0.md   # Modernized policy document with cloud/MFA standards
│   └── Policy_Changelog.md            # Redline summary & framework crosswalk
└── exceptions/
├── Policy_Exception_Process.md     # Governance workflow & review criteria
└── Exception_EXP-104.md            # Real-world exception case study & risk assessment

---

## 🎯 Key Highlights & Deliverables

### 1. Modernized Policy Document (`policy/Access_Control_Policy_v2.0.md`)
* Establishes mandatory MFA (FIDO2/TOTP), centralized SSO, and strict 2-hour termination offboarding SLAs.
* Enforces dynamic runtime secret injection (IRSA/Vault) for non-human identities to prevent hardcoded credential leakage.

### 2. Policy Revision Changelog (`policy/Policy_Changelog.md`)
* Summarizes legacy (2022) vs. modernized (2026) standards.
* Crosswalks policy requirements directly to **NIST SP 800-53 Rev. 5**, **PCI-DSS v4.0**, **SOC 2 CC series**, and **ISO 27001**.

### 3. Policy Exception Governance (`exceptions/Policy_Exception_Process.md`)
* Defines a clear approval authority matrix based on Residual Risk levels.
* Mandates hard 90-day sunset dates and compensating controls for all temporary policy bypasses.

### 4. Real-World Exception Case Study (`exceptions/Exception_EXP-104.md`)
* Evaluates an engineering request to bypass MFA for a legacy clearinghouse SFTP service account (`EXP-104`).
* Applies a **$5 \times 5$ Risk Evaluation**, mandates **IP whitelisting & least privilege IAM scoping** as compensating controls, and recalculates residual risk ($12 \rightarrow 3.0\ \text{LOW}$).

---

## 🛠️ How to Review This Repository
1. Read the **[Modernized Access Control Policy](policy/Access_Control_Policy_v2.0.md)** for enterprise security standards.
2. Inspect the **[Policy Changelog](policy/Policy_Changelog.md)** to review framework alignment.
3. Examine **[Exception EXP-104](exceptions/Exception_EXP-104.md)** to see how GRC balances security guardrails with business enablement.
