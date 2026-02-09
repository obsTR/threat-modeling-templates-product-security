# PASTA Risk Analysis: [Feature Name]

**Owner:** [Name]
**Date:** [YYYY-MM-DD]
**Reviewer:** [Security Team/Peer]

## Stage 1: Define Business Objectives
- [What business outcome does this feature support?]
- [What is the impact of compromise?]

## Stage 2: Define Technical Scope
- **In-Scope Components:** [APIs, services, data stores, third-party systems]
- **Out-of-Scope Components:** [Anything excluded from this assessment]

## Stage 3: Application Decomposition
- **Entry Points:** [User login form, API gateway, admin console]
- **Data Flows:** [How data moves between components]
- **Trust Boundaries:** [Internet, VPC, internal network, privileged zones]

## Stage 4: Threat Analysis
| Threat | Attack Vector | Affected Component | Existing Controls |
| :--- | :--- | :--- | :--- |
| [Threat 1] | [How attacker executes it] | [Component] | [Control] |
| [Threat 2] | [How attacker executes it] | [Component] | [Control] |

## Stage 5: Vulnerability Analysis
| Vulnerability | Severity | Evidence | Owner |
| :--- | :--- | :--- | :--- |
| [Weak session management] | [High/Med/Low] | [Test result, design gap, CVE] | [Team/Role] |

## Stage 6: Attack Modeling & Simulation
- **Likely Attack Paths:** [Describe top attack chains]
- **Assumptions:** [List attacker capabilities and constraints]
- **Validation Method:** [Manual review, tabletop, penetration test]

## Stage 7: Risk & Mitigation Plan
| Risk | Likelihood | Impact | Priority | Mitigation | Ticket ID |
| :--- | :--- | :--- | :--- | :--- | :--- |
| [Credential stuffing] | [High/Med/Low] | [High/Med/Low] | [P1/P2/P3] | [Rate limit + MFA] | [Jira-201] |

## Sign-off
- **Engineering Lead:** [Name]
- **Security Lead:** [Name]
- **Decision:** [Approved / Changes Required]