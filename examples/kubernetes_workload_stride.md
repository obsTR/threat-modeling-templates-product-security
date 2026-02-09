# STRIDE Example: Kubernetes Workload Deployment Pipeline

**Owner:** Cloud Security Team
**Date:** 2026-02-08
**Reviewer:** DevSecOps Lead

## 1. System Description
This model covers CI/CD to Kubernetes, including image build, registry publish, and deployment rollout.

## 2. Data Flow
- **Sources:** Git commits, CI runners, container registry events
- **Destinations:** Artifact registry, Kubernetes API server, runtime clusters
- **Trust Boundaries:** Developer workstation, CI environment, cluster control plane

## 3. STRIDE Analysis

| Threat Category | Description | Applicable? | Mitigation Strategy | Ticket ID |
| :--- | :--- | :--- | :--- | :--- |
| **S**poofing | Malicious actor pushes code using compromised developer identity. | Yes | SSO with hardware-backed MFA and signed commits | K8S-101 |
| **T**ampering | Image altered between build and deploy. | Yes | Image signing (Sigstore/cosign), admission policy verification | K8S-102 |
| **R**epudiation | Operator denies manual change in production cluster. | Yes | API audit logs and GitOps drift detection | K8S-103 |
| **I**nformation Disclosure | Secrets leak via CI logs or container env dumps. | Yes | Secret managers, ephemeral credentials, log scrubbing | K8S-104 |
| **D**enial of Service | Misconfigured deployment causes cluster-wide outage. | Yes | Progressive delivery, pod disruption budgets, rollback automation | K8S-105 |
| **E**levation of Privilege | Pod escapes or over-privileged service account abused. | Yes | Pod security standards, seccomp, least-privilege RBAC | K8S-106 |

## 4. Security Requirements
1. Block unsigned container images at admission.
2. Enforce namespace isolation and network policies by default.
3. Rotate CI and cluster credentials automatically with short TTL.
