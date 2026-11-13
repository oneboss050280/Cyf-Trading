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
