# STRIDE Example: Internal Admin Portal

**Owner:** Platform Security
**Date:** 2026-02-08
**Reviewer:** Senior Security Engineer

## 1. System Description
This model covers an internal admin portal used by support and operations teams to manage users, orders, and feature flags.

## 2. Data Flow
* **Sources:** Corporate SSO, support staff actions, internal APIs
* **Destinations:** Admin API, user profile store, audit log pipeline
* **Trust Boundaries:** Corporate network, production control plane, privileged admin zone

## 3. STRIDE Analysis

| Threat Category | Description | Applicable? | Mitigation Strategy | Ticket ID |
| :--- | :--- | :--- | :--- | :--- |
| **S**poofing | Attacker steals an employee session cookie. | Yes | SSO with phishing-resistant MFA, device posture checks | ADM-101 |
| **T**ampering | Unauthorized modification of feature flags or user roles. | Yes | Signed change requests, dual approval for sensitive actions | ADM-102 |
| **R**epudiation | Staff denies making a privileged change. | Yes | Tamper-evident audit logs tied to SSO identity | ADM-103 |
| **I**nformation Disclosure | Admin views PII without business justification. | Yes | Just-in-time access grants, field masking, purpose binding | ADM-104 |
| **D**enial of Service | Portal unavailable during incident response. | Yes | Multi-region failover and break-glass runbooks | ADM-105 |
| **E**levation of Privilege | Support role escalates to super-admin capabilities. | Yes | Least privilege roles, segregation of duties, policy-as-code | ADM-106 |

## 4. Security Requirements
1. Require just-in-time access for privileged operations.
2. Enforce two-person approval for role escalation and data exports.
3. Review privileged access logs weekly with anomaly detection alerts.
