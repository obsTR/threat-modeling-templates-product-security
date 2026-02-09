# PASTA Example: Cloud File Storage and Sharing

**Owner:** Collaboration Product Team
**Date:** 2026-02-08
**Reviewer:** Security Architect

## Stage 1: Define Business Objectives
- Enable secure file upload, storage, and sharing for enterprise customers.
- Protect confidentiality, integrity, and tenant isolation requirements.

## Stage 2: Define Technical Scope
- **In-Scope Components:** Upload API, object storage, metadata DB, sharing links service, malware scanner.
- **Out-of-Scope Components:** Desktop client sync internals and third-party BI exports.

## Stage 3: Application Decomposition
- **Entry Points:** Upload endpoint, signed URL generation, public share-link endpoint.
- **Data Flows:** User upload -> API -> scanning queue -> object storage -> retrieval via signed URL.
- **Trust Boundaries:** Internet clients, application layer, storage control plane.

## Stage 4: Threat Analysis
| Threat | Attack Vector | Affected Component | Existing Controls |
| :--- | :--- | :--- | :--- |
| Malicious file delivery | Upload executable disguised as benign document | Upload pipeline | Malware scanning and MIME validation |
| Share-link enumeration | Brute force of predictable public links | Sharing service | Long random tokens and access limits |

## Stage 5: Vulnerability Analysis
| Vulnerability | Severity | Evidence | Owner |
| :--- | :--- | :--- | :--- |
| Overly long signed URL TTL | High | Architecture review identified 7-day default | Platform Team |
| Missing object-level auth checks on metadata API | Critical | Pen-test finding in tenant boundary tests | Storage API Team |

## Stage 6: Attack Modeling & Simulation
- **Likely Attack Paths:** Enumerate links -> exfiltrate files -> lateral movement via shared accounts.
- **Assumptions:** Attacker has internet access and no privileged credentials.
- **Validation Method:** Abuse-case tabletop and targeted API penetration test.

## Stage 7: Risk & Mitigation Plan
| Risk | Likelihood | Impact | Priority | Mitigation | Ticket ID |
| :--- | :--- | :--- | :--- | :--- | :--- |
| Tenant data exposure | Medium | High | P1 | Enforce object-level auth in all read paths | FILE-201 |
| Malware distribution | Medium | High | P1 | Block download until asynchronous scan completes | FILE-202 |
| Link abuse | High | Medium | P2 | CAPTCHA and throttling for anonymous downloads | FILE-203 |

## Sign-off
- **Engineering Lead:** [Name]
- **Security Lead:** [Name]
- **Decision:** Changes Required before release
