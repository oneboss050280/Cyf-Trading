# CYF Trading — Security Documentation

**Status: Security requirements and implementation checklist — not a certification**  
**Last drafted:** November 12, 2026

## 1. Security model

CYF Trading is intended to be a **noncustodial** trading technology platform. Users control their own exchange accounts and funds. Stripe manages membership payments; Supabase manages user authentication and application data. No AI component may autonomously control customer funds or bypass user trade confirmation.

## 2. Authentication and authorization

- Use Supabase authentication with verified email ownership and secure password recovery.
- Protect authenticated sessions and validate identity server-side for protected actions.
- Apply least-privilege access and row-level security to user data.
- Never trust browser-provided user IDs, membership status, or role claims without verification.
- Require reauthentication for sensitive account actions where appropriate.

## 3. Exchange integrations

- Users explicitly connect their own exchange accounts via supported methods.
- Prefer scoped authorization mechanisms; use only the minimum API permissions required.
- **Do not request or enable withdrawal or transfer privileges.**
- Never expose exchange secrets in client-side code, logs, or GitHub.
- Protect tokens using approved secret storage, encryption, and access controls.
- Provide disconnect/revocation instructions and verify revoked access cannot be reused.
- Require explicit user confirmation before any trade submission; prohibit unapproved automated execution.
- Verify supported exchange and regional eligibility before enabling an integration.

## 4. Billing integrity

- Stripe secret keys and webhook signing secrets must remain server-side.
- Verify Stripe webhook signatures before processing events.
- Make event processing idempotent and resistant to retries and out-of-order delivery.
- Determine membership entitlements from verified Stripe state, not client claims.
- Prevent duplicate active subscriptions and repeated trial abuse with server-side checks.
- Enforce promotional eligibility, annual-plan restriction, and redemption limits server-side.
- Provide a tested cancellation and subscription-management workflow.
- Separate test and live Stripe environments and prevent test events from granting production access.

## 5. Database and backend

- Maintain versioned, reviewed Supabase migrations in GitHub.
- Enable and test row-level security for tables exposed to clients.
- Restrict privileged functions and service-role keys to trusted server components.
- Validate input, rate-limit abuse-prone endpoints, and avoid leaking sensitive errors.
- Separate staging from production data and secrets.

## 6. Infrastructure and secrets

- Use HTTPS/TLS for all public endpoints.
- Store secrets in provider-managed secret stores, not source code or browser bundles.
- Rotate credentials after suspected exposure or staff/access changes.
- Limit deployment and administrative access; enable MFA for administrator accounts.
- Review dependency vulnerabilities and pin/upgrade packages appropriately.
- Use least-privilege CI/CD credentials and protect production deployment paths.

## 7. Logging and incident response

- Log security-relevant events without recording passwords, payment details, or exchange tokens.
- Monitor failed authentication, suspicious billing events, and unusual API behavior.
- Maintain an incident-response procedure: identify, contain, revoke/rotate, remediate, notify when legally required, and review.
- Define a verified security contact: **[TO BE COMPLETED]**.
- Document backups, restoration tests, and recovery objectives before launch.

## 8. Release verification checklist

- [ ] Authentication and password reset tested end-to-end.
- [ ] Database access policies and privileged functions reviewed.
- [ ] Stripe live/test isolation confirmed.
- [ ] Stripe webhook verification, retry handling, and membership sync tested.
- [ ] Trial, duplicate subscription, promotion, and cancellation logic tested.
- [ ] Exchange permissions verified to exclude withdrawals/transfers.
- [ ] User approval enforced for trade submission.
- [ ] Secrets checked for accidental exposure.
- [ ] Dependency and configuration review completed.
- [ ] Incident contact, monitoring, and recovery process documented.
- [ ] Public Terms and Privacy Policy reviewed and published.

## 9. Reporting security issues

**Security contact:** [TO BE COMPLETED]. Until a verified reporting channel exists, do not claim a formal vulnerability disclosure program is operational.

---

This document is a baseline for implementation and testing. **It does not assert that any listed control is currently deployed or audited.**
