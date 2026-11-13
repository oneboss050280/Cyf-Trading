# CYF Trading — Privacy Policy

**Status: Draft for review — not yet a verified description of production data processing**  
**Last drafted:** November 12, 2026

> This document describes intended practices. Confirm actual data collection, processors, storage locations, retention periods, and legal obligations before publication.

## 1. Who operates CYF Trading

**Data controller/business legal name:** [TO BE COMPLETED]  
**Privacy contact:** [TO BE COMPLETED]  
**Business address:** [TO BE COMPLETED]

## 2. Information we may process

Depending on the features users choose, CYF Trading may process:
- Account registration details, such as email address and user ID.
- Authentication and security events needed to protect accounts.
- Subscription identifiers, plan, status, billing dates, and payment-related metadata supplied by Stripe.
- Customer support messages and related correspondence.
- Technical and diagnostic information needed for operation and security.
- Exchange connection metadata and access tokens, only where required and explicitly authorized.

**Exact fields, analytics/cookies, and retention periods:** [AUDIT BEFORE PUBLICATION].

## 3. How information is used

Intended purposes include account authentication, delivering subscribed features, confirming membership status, responding to support requests, securing the service, detecting abuse, and meeting applicable legal obligations. Any additional use must be documented and justified before launch.

## 4. Service providers

- **Supabase:** Intended account authentication and application data storage.
- **Stripe:** Intended subscription checkout, payment processing, and recurring billing. CYF Trading does not intend to store full payment-card numbers.
- **Cloudflare:** Intended website hosting and server-side infrastructure.
- **Connected exchanges:** Users separately authorize exchange access under the exchange's own privacy terms.

**Other providers, sub-processors, international transfers, and processor agreements:** [VERIFY].

## 5. Exchange account data

Users connect their own exchange accounts. Any credentials or access tokens needed for integrations must be handled securely and with minimum permissions. Exchange withdrawal and transfer permissions must not be requested. Users should be able to revoke authorization through their exchange. **Token storage, retention, and deletion implementation:** [VERIFY].

## 6. Sharing and disclosures

Information may be shared with authorized processors to deliver the service or as legally required. CYF Trading does not intend to sell users' personal information. **Any legally defined “sale,” “sharing,” or targeted advertising practices must be assessed based on actual tracking and vendor configuration.**

## 7. Retention and deletion

Data should be retained only as long as reasonably necessary for the stated purposes and applicable legal obligations. Users should have a documented method to request access, correction, or deletion where required by law. **Retention schedule and request channel:** [TO BE COMPLETED].

## 8. Security

Intended safeguards include encryption in transit, role-based access, Supabase row-level security, secure secret management, monitoring, and restricted exchange API permissions. No online system can guarantee absolute security. These safeguards must be validated against the actual deployment.

## 9. Privacy choices and rights

Applicable rights may include access, correction, deletion, portability, and opting out of certain processing, depending on jurisdiction. **Rights request process and response time:** [TO BE COMPLETED].

## 10. Cookies and analytics

**Cookie inventory, consent requirements, and analytics providers:** [AUDIT AND COMPLETE]. Do not claim there are no cookies until the website and third-party integrations have been checked.

## 11. Children

The service is not intended for children. **Minimum age and age-verification rules:** [COMPLETE BASED ON PRODUCT AND APPLICABLE LAW].

## 12. Changes and contact

The published policy will include its effective date, material-change notification process, and verified privacy contact details.

---

**Release gate:** Validate this draft against actual data flows and applicable privacy law before publication.
