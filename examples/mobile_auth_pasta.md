# PASTA Example: Mobile Authentication Service

**Owner:** Mobile Platform Team
**Date:** 2026-02-08
**Reviewer:** Product Security Manager

## Stage 1: Define Business Objectives
- Provide secure, low-friction mobile login for iOS and Android.
- Maintain account integrity while keeping login success rate high.

## Stage 2: Define Technical Scope
- **In-Scope Components:** Mobile apps, auth API, token service, identity provider, telemetry.
- **Out-of-Scope Components:** Marketing site, unrelated backend services.

## Stage 3: Application Decomposition
- **Entry Points:** Login endpoint, refresh token endpoint, MFA challenge endpoint.
- **Data Flows:** Credentials and device signals to auth API, token issuance to client, logs to SIEM.
- **Trust Boundaries:** Untrusted mobile devices, internet edge, protected backend network.

## Stage 4: Threat Analysis
| Threat | Attack Vector | Affected Component | Existing Controls |
| :--- | :--- | :--- | :--- |
| Credential stuffing | Automated login attempts using leaked credentials | Auth API | Rate limiting, breached password checks |
| Token replay | Intercepted token reused from compromised device | Token validation service | Short token TTL, binding to device signals |

## Stage 5: Vulnerability Analysis
| Vulnerability | Severity | Evidence | Owner |
| :--- | :--- | :--- | :--- |
| Weak lockout thresholds | High | Brute force simulation exceeded thresholds | Identity Team |
| Excessive auth error detail | Medium | Error responses differentiate account existence | API Team |

## Stage 6: Attack Modeling & Simulation
- **Likely Attack Paths:** Stuffed credentials -> account takeover -> payout abuse.
- **Assumptions:** Attacker has leaked credentials and commodity bot infrastructure.
- **Validation Method:** Threat workshop and red-team login abuse scenario.

## Stage 7: Risk & Mitigation Plan
| Risk | Likelihood | Impact | Priority | Mitigation | Ticket ID |
| :--- | :--- | :--- | :--- | :--- | :--- |
| Account takeover | High | High | P1 | Risk-based MFA + behavioral analytics | MOB-201 |
| Session hijack | Medium | High | P1 | Refresh token rotation + revocation API | MOB-202 |
| SMS OTP bypass | Medium | Medium | P2 | Add app-based authenticator and anti-phishing checks | MOB-203 |

## Sign-off
- **Engineering Lead:** [Name]
- **Security Lead:** [Name]
- **Decision:** Approved with mitigation tracking
