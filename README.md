# CYF Trading

**Control Your Future.**

CYF Trading is a noncustodial trading technology platform being developed to provide market information, trading tools, and user-controlled workflows.

## Our Mission

Give people accessible tools to understand markets and make their own trading decisions while retaining control of their funds and accounts.

## Core Principles

- **Your funds stay yours.** CYF Trading does not take custody of customer funds.
- **You make the decisions.** Any AI-generated analysis or trade suggestion is informational; the user must explicitly approve any action.
- **No guaranteed results.** Trading involves risk, including possible loss of capital. CYF Trading does not promise profits or provide personalized investment advice.
- **Security first.** Authentication, payment verification, authorization, and auditability must be validated before public release.
- **Transparent billing.** Subscription terms, trial conditions, renewals, and cancellation options must be clearly disclosed.

## Connect Your Own Exchange Account

CYF Trading users add and connect **their own existing accounts at supported third-party cryptocurrency exchanges**, such as **Coinbase, Kraken, Binance, and Binance.US**, subject to integration availability, exchange restrictions, and regional eligibility. CYF Trading does not create exchange accounts for users, hold customer deposits, or act as custodian of customer assets.

- Users are responsible for opening, maintaining, and verifying their exchange accounts and complying with the exchange's requirements.
- The listed exchanges are **planned connection options**, not a claim that their integrations are currently active.
- Any exchange connection must be explicitly authorized by the user through the exchange's supported connection method.
- Where API credentials are required, connections should use the minimum permissions necessary. **Withdrawal and transfer permissions must not be requested or enabled.**
- Exchange credentials and tokens must be protected using appropriate secure storage and access controls; they must never be committed to this repository or exposed in browser code.
- Users can disconnect their exchange integration and revoke access through their exchange account.
- Market analysis and trade suggestions do not authorize execution. Any trade action requires the user's explicit confirmation.
- Supported exchanges and actual connection capabilities will be documented only after integration and security testing.

## Planned Platform

- Responsive website for mobile, tablet, and desktop
- Secure account registration, email verification, sign-in, and password recovery
- Market dashboards, charts, and analysis tools
- User-directed trading workflows through separately authorized third-party integrations
- Membership management and customer support
- Clearly published Terms, Privacy, Refund, and Risk disclosures

These features are **planned**, not claims that the services are currently live or operational.

## Intended Technology

- **GitHub:** Source control
- **Cloudflare:** Website hosting and server-side endpoints
- **Supabase:** Authentication and application data
- **Stripe:** Subscription billing
- **TradingView:** Market charting where appropriate

Integrations must be implemented, tested, and verified before being described as production-ready.

## Membership Billing and User Accounts

- **Stripe handles membership subscriptions and associated membership fees**, including checkout, payment processing, recurring billing, and payment-method management. CYF Trading does not store customers' credit card details.
- **Supabase handles CYF Trading user accounts**, including registration, authentication, email verification, password recovery, and user profile data.
- Membership status and access permissions are synchronized securely between verified Stripe billing events and Supabase. A successful checkout alone must not grant access until the subscription state is verified.
- Users manage their own exchange accounts separately. Supabase authentication and Stripe membership billing do not give CYF Trading custody of exchange funds.
- The billing and account integrations are planned and must be implemented and tested before production launch.

## Membership Plans (Proposed)

- Monthly: **$10/month**
- Annual: **$75/year**
- Seven-day free trial, subject to eligibility and clear checkout disclosures
- Founding-member promotion: first 100 eligible annual members may receive a **$50 first year**, renewing at **$75/year**, subject to published terms and verified eligibility controls

Pricing and promotional terms must be checked against the live checkout configuration before launch.

## Development Status

**Fresh repository — initial project documentation.**

No production implementation, deployed website, billing integration, or live trading capability is established by this README. Development and release readiness must be verified separately.

## Terms and Conditions

Before public launch, CYF Trading will publish clear, accessible Terms and Conditions describing membership eligibility, pricing, free trials, renewals, cancellation, acceptable use, service availability, third-party exchange connections, user responsibilities, dispute procedures, and limitations of liability. Customers must be able to review the terms before subscribing. Trading involves risk, and no profit or performance outcome is guaranteed.

## Privacy Policy

Before collecting production user data, CYF Trading will publish a Privacy Policy describing the personal information collected, why it is used, the roles of Supabase and Stripe, exchange-connection data, retention and deletion practices, security safeguards, user privacy choices, and contact information. Payment-card details are processed by Stripe rather than stored by CYF Trading. Actual data practices must be verified against the deployed implementation and applicable laws before publication.

## Security Documentation

CYF Trading will maintain security documentation covering:

- Authentication, email verification, secure password recovery, session management, and access control through Supabase.
- Database row-level security, least-privilege roles, and server-side authorization checks.
- Stripe webhook signature verification, billing-event idempotency, subscription entitlement validation, and fraud/duplicate-trial controls.
- Secure exchange authorization and API credential handling; never request withdrawal or transfer privileges.
- Encryption in transit, secure handling of secrets, credential rotation, and no secrets in source control or client-side code.
- Logging, monitoring, incident response, backup/recovery procedures, and vulnerability remediation.
- Dependency reviews, testing, and production-release security checks.

Detailed policies and procedures will be maintained as separate documents and linked here when approved. These sections describe requirements, **not completed security certifications or assurances**.

## Release Requirements

1. Build and review responsive UI and accessible account flows.
2. Implement authentication and secure session handling.
3. Implement server-side billing, signed Stripe webhooks, trial eligibility, duplicate-subscription prevention, and customer cancellation.
4. Apply and version database migrations; verify row-level security and least-privilege access.
5. Publish and review legal disclosures and customer support contact details.
6. Test the complete signup-to-subscription lifecycle in a safe test environment.
7. Keep real-money trading disabled until external integrations, permissions, and safety controls are independently validated.

## Important Disclaimer

CYF Trading supplies software and information, not guarantees of financial outcomes. Users remain responsible for their decisions. Markets determine results.

---

**CYF Trading — Control Your Future.**
