# Threat Model: [Feature Name]

**Owner:** [Name]
**Date:** [YYYY-MM-DD]
**Reviewer:** [Security Team/Peer]

## 1. System Description
[Briefly describe the feature. Include a link to the architecture diagram or draw.io file.]

## 2. Data Flow
* **Sources:** [Where data comes from, e.g., User Input]
* **Destinations:** [Where data goes, e.g., SQL Database]
* **Trust Boundaries:** [e.g., Internet vs Internal Network]

## 3. STRIDE Analysis

| Threat Category | Description | Applicable? | Mitigation Strategy | Ticket ID |
| :--- | :--- | :--- | :--- | :--- |
| **S**poofing | Can an attacker impersonate a user or system? | Yes/No | [e.g., Implement MFA] | Jira-101 |
| **T**ampering | Can data be modified in transit or at rest? | Yes/No | [e.g., TLS 1.3, HMAC signatures] | Jira-102 |
| **R**epudiation | Can a user deny performing an action? | Yes/No | [e.g., Centralized Audit Logs] | |
| **I**nformation Disclosure | Can sensitive data be exposed? | Yes/No | [e.g., Field-level encryption] | |
| **D**enial of Service | Can the system be made unavailable? | Yes/No | [e.g., Rate limiting, CDNs] | |
| **E**levation of Privilege | Can a user gain unauthorized access? | Yes/No | [e.g., RBAC checks] | |

## 4. Security Requirements
1. [Requirement 1]
2. [Requirement 2]