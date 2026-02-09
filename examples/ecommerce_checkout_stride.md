# STRIDE Example: Ecommerce Checkout and Payment Flow

**Owner:** Product Security Team
**Date:** 2026-02-08
**Reviewer:** Security Architect

## 1. System Description
This model covers checkout for card payments, including cart review, payment tokenization, and order confirmation.

## 2. Data Flow
* **Sources:** Customer browser, payment gateway webhook
* **Destinations:** Checkout API, payment processor, order database, notification service
* **Trust Boundaries:** Public internet, PCI-scoped payment segment, internal application network

## 3. STRIDE Analysis

| Threat Category | Description | Applicable? | Mitigation Strategy | Ticket ID |
| :--- | :--- | :--- | :--- | :--- |
| **S**poofing | Fraudster reuses stolen sessions to place unauthorized orders. | Yes | Step-up auth for risky purchases, re-auth for card changes | PAY-101 |
| **T**ampering | Cart total or line items altered between client and server. | Yes | Server-side price calculation, signed cart state, integrity checks | PAY-102 |
| **R**epudiation | User denies confirming payment. | Yes | Signed order events, immutable audit trail, payment intent IDs | PAY-103 |
| **I**nformation Disclosure | Exposure of PAN or billing details in logs or traces. | Yes | Tokenization, log masking, strict PCI data retention controls | PAY-104 |
| **D**enial of Service | Bot traffic floods checkout endpoints and blocks purchases. | Yes | WAF, queue backpressure, per-IP and per-account rate limits | PAY-105 |
| **E**levation of Privilege | User accesses admin-only refund endpoints. | Yes | RBAC/ABAC enforcement, policy tests, endpoint-level authorization | PAY-106 |

## 4. Security Requirements
1. Do not persist raw card data; use processor tokens only.
2. Enforce idempotency keys on order creation and payment confirmation.
3. Alert on anomalies: failed payments, velocity spikes, refund abuse.
4. Run quarterly tabletop exercises for payment abuse scenarios.
