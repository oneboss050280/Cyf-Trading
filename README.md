# CYF Trading

**Control Your Future.**

CYF Trading is a noncustodial trading technology platform under development, designed to provide market information, analytical tools, AI-assisted analysis, and user-controlled trading workflows. Customers retain ownership and control of their exchange accounts and assets.

**Document:** README Version 2.2 — approved architecture requirements (November 13, 2026). This document does not certify that planned features are operational.

## 1. Company Overview

**Mission:** Provide accessible, transparent trading technology that helps customers understand financial markets and make informed decisions while maintaining control of their assets.

**Vision:** Build a secure, responsive platform combining market information, analytical tools, exchange connectivity, and AI-assisted decision support.

**Control Your Future** means customers—not CYF Trading or AI—make the final trading decisions.

## 2. Core Principles

- **Noncustodial:** Customer funds remain in customer-owned exchange accounts. CYF Trading does not hold, transfer, or withdraw them.
- **Customer authorization:** Every trading action requires explicit customer approval.
- **AI-assisted analysis:** AI provides information and suggestions, not independent authority over funds or accounts.
- **Transparent pricing:** Subscription costs, renewals, and cancellation terms must be disclosed before purchase.
- **Security and privacy:** Account access, personal information, and exchange credentials require verified protections.
- **No guaranteed returns:** CYF Trading does not guarantee profits or investment performance.
- **Customer independence:** Users control their exchange connections, subscriptions, and account preferences.

## 3. Platform Features and Navigation

The website will be mobile-first and responsive across desktop, tablet, and smartphone screens. The Midnight theme uses charcoal/black backgrounds and violet accents `#7C6FFF` and `#6450F0`; animations must respect reduced-motion preferences.

**Primary navigation:** Dashboard | Markets | Trade | Portfolio | Support | Account

**Public authentication controls:** Clearly visible **Login** and **Sign Up** buttons. After authentication, the interface must show the signed-in account state and provide **Logout**.

- **Dashboard:** Account activity, market information, portfolio summaries, and trading tools.
- **Markets:** Market information, asset details, price charts, and planned TradingView charting.
- **Trade:** Review and explicitly confirm user-authorized orders before submission.
- **Portfolio:** Supported holdings, balances, positions, and transaction history obtained through authorized connections.
- **Support:** Technical and account assistance, AI customer support, and human escalation. Support AI cannot modify funds or execute trades.
- **Account:** Centralized authenticated settings for profile and security, **AI trading settings**, **exchange accounts**, membership and billing, notifications, privacy, account deletion, security incident reporting, and logout.

Mobile navigation must not overflow horizontally. Login, Sign Up, and Account access must remain easy to find.

These are requirements for planned features, not claims of deployment or production readiness.

## 4. Technology Architecture

| Technology | Intended responsibility |
| --- | --- |
| GitHub | Source control, version history, and documentation |
| Cloudflare | Website hosting and server-side endpoints |
| Supabase | Authentication, profiles, application data, and access control |
| Stripe | Membership checkout, payments, and recurring billing |
| TradingView | Market charting and visualization |
| Exchange APIs | Customer-authorized exchange connectivity and approved trade submission |

Privileged operations must remain server-side. Secrets and access tokens must never be embedded in browser code or committed to repositories.

## 5. User Registration and Authentication

Supabase is the intended account authentication and application identity system. Supabase Auth owns password hashes; application profile tables must not duplicate password fields. Mandatory identity verification through a vetted KYC provider is required before access to live trading features. KYC states include `not_started`, `pending`, `verified`, `rejected`, and `requires_review`. Do not store raw identity documents unless strictly required and lawfully justified.

- Email-based registration, verification, and secure password creation.
- Clearly labeled Login and Sign Up controls with meaningful error messages.
- Secure sessions, logout, and server-side authorization.
- A visible **Forgot Password** link with secure, expiring reset links.
- Profile management, account recovery, and protection against unauthorized access.
- Subscription-gated features enabled only after verified membership entitlement; a checkout redirect or browser-provided status alone is insufficient.

## 6. Exchange Account Connections

Customers connect their **own existing** accounts at planned third-party exchanges: **Coinbase, Kraken, Binance, and Binance.US**. Availability depends on region, exchange rules, technical support, and completed integration testing.

- Each connection requires explicit user authorization through a supported method.
- Use only minimum necessary API permissions.
- **Withdrawal and transfer permissions must never be requested or enabled.**
- Protect tokens and credentials from browser exposure, repositories, and logs.
- Customers retain control of exchange accounts and assets.
- Every proposed trade requires separate, explicit user confirmation.

Exchange integrations must not be described as live until tested and verified.

## 7. Membership Plans and Stripe Billing

| Membership | Price |
| --- | --- |
| Monthly | **$10 per month** |
| Annual | **$75 per year** |

**No free trials. No promotions.** Billing begins immediately upon successful subscription initiation, with the charge and renewal terms disclosed before purchase.

Stripe is responsible for subscription checkout, payment processing, recurring billing, payment-method management, and billing records. CYF Trading does not store full payment-card numbers.

Billing implementation must:
- Verify Stripe webhook signatures and process retries idempotently.
- Prevent duplicate active subscriptions.
- Validate membership state server-side and synchronize entitlements with Supabase.
- Disclose price, renewal schedule, and any applicable taxes or fees.
- Offer functioning subscription management and cancellation.
- Ensure no free-trial or promotional discounts are offered in live checkout.

The live Stripe configuration must be checked against this policy before launch.

## 8. Account Management and Membership Cancellation

The **Account** tab is the centralized customer settings area.

### Profile and security
View and update supported personal details, authentication settings, sessions, and recovery options.

### AI trading settings
Users can manage available AI analysis features, analysis and notification preferences, suggested-trade review, and supported activity history. **Enabling AI does not authorize autonomous execution.** AI may not independently trade, transfer or withdraw assets, or bypass explicit confirmation.

### Exchange accounts
View linked exchanges, connection status, permissions, and available disconnect/reconnect controls.

### Membership and billing
View the plan, subscription status, renewal date, and Stripe-supported payment management. Provide **Manage Subscription** and **Cancel Membership** actions, stop future renewals when canceled, and show cancellation confirmation and any remaining paid access.

### Notifications and preferences
Manage available market alerts, account notifications, security alerts, and display preferences.

### Privacy and account deletion
Provide an accessible deletion request process, verify ownership, explain deletion/retention, address active subscriptions and exchange connections, and confirm completion. Closing an account must not leave undisclosed recurring charges.

All flows require implementation and end-to-end testing.

## 9. Exchange Reconnection and Access Revocation

Customers must be able to:
- View active, disconnected, expired, and revoked exchange connections.
- Disconnect integrations and receive instructions for revoking authorization at the exchange.
- Invalidate or delete locally held tokens on disconnection, subject to applicable retention rules.
- Prevent revoked or expired credentials from authorizing API requests or trades.
- Reconnect only through fresh, explicit authorization.
- Receive clear connection status and error messages.

Reconnection must never request withdrawal or transfer permissions.

## 10. Security Architecture and Incident Reporting

Required controls include secure authentication and sessions, Supabase row-level security, least-privilege server authorization, signed Stripe webhook verification, secure exchange credential storage, HTTPS/TLS, environment isolation, protected secrets, logging, monitoring, vulnerability management, backups, and restricted administrative access.

Customers must be able to report unauthorized access, suspicious logins, unexpected exchange connections or trades, possible data exposure, billing security concerns, and application vulnerabilities.

Incident procedures must cover triage, investigation, containment, revocation, remediation, and legally required notifications. **Verified security reporting contact: to be established before launch.**

See [Security Documentation](docs/SECURITY.md). These are requirements, not verified certifications or claims of completed controls.

## 11. Legal and Policy Documentation

Detailed documents are maintained separately:

- [Terms and Conditions](docs/TERMS_AND_CONDITIONS.md)
- [Privacy Policy](docs/PRIVACY_POLICY.md)
- [Security Documentation](docs/SECURITY.md)

**Additional required policies:** Refund Policy, Trading Risk Disclosure, verified business/support contact details, and effective dates.

These documents are drafts and require review against actual practices and applicable law. **The Terms draft currently contains outdated trial and promotional language and must be updated before publication.** Public-facing policies must be accessible before customers subscribe.

## 12. Development Status and Roadmap

This repository is a fresh source-control foundation with project documentation and draft policies. Existing external infrastructure must be audited separately; this README does not prove any production feature is operational.

1. **Foundation:** Repository, architecture, documentation, and environments.
2. **User interface:** Responsive navigation, dashboard, markets, trade, portfolio, support, and Account settings.
3. **Authentication:** Supabase registration, verification, recovery, sessions, and account management.
4. **Membership billing:** Stripe checkout, webhooks, entitlement sync, cancellation, and billing management.
5. **Exchange integrations:** Authorized connections, restricted permissions, revocation, and user-approved trades.
6. **Quality assurance and launch:** Security tests, legal review, deployment verification, monitoring, and controlled release.

Each phase must be verified before being marked complete.

## 13. Production Launch Requirements

- [ ] Responsive desktop, tablet, and mobile layouts tested.
- [ ] Dashboard, Markets, Trade, Portfolio, Support, and Account navigation verified.
- [ ] Login and Sign Up controls functional.
- [ ] Supabase registration, email verification, password recovery, and logout tested.
- [ ] Account settings and deletion workflows tested.
- [ ] Stripe $10 monthly and $75 annual subscriptions verified.
- [ ] **Free trials and promotions disabled in live checkout.**
- [ ] Stripe webhook signatures, retry handling, and membership synchronization tested.
- [ ] Duplicate active subscriptions prevented.
- [ ] Subscription cancellation and renewal handling tested.
- [ ] AI settings and explicit trade approval restrictions tested.
- [ ] Exchange connection, disconnection, reconnection, and revocation tested.
- [ ] Exchange withdrawal and transfer permissions excluded.
- [ ] Supabase security policies, production secrets, and environment isolation reviewed.
- [ ] Security incident reporting and support contacts established.
- [ ] Terms, Privacy, Refund, and Risk policies reviewed and published.
- [ ] Production deployment, monitoring, and recovery procedures verified.

Real-money trading and unverified AI automation must remain disabled until applicable safety and operational controls have passed testing.

## 14A. Approved Production Architecture — November 13, 2026

**Status:** Approved specification, not a claim of completed implementation.

### System boundaries
- **Cloudflare Pages:** Responsive Midnight PWA with Dashboard, Markets, Trade, Portfolio, Support, and Account; public Login and Sign Up.
- **Cloudflare Workers:** Authenticated API gateway, server-side trade authorization, market-feed proxy/WebSocket coordination, Stripe checkout and webhook handlers.
- **Supabase:** Auth, PostgreSQL, row-level security, user profiles, membership entitlements, exchange metadata, trade approval records, audit logs.
- **Stripe:** $10 monthly / $75 annual recurring plans, **no trial or promotion**, customer portal, signed webhook event reconciliation.
- **Dedicated market-data/exchange provider:** Real-time prices, order books, and approved order submission. Stripe, GitHub, Supabase, and Cloudflare are not primary exchange price feeds.
- **KYC provider:** Server-verified identity status; restrict access to live trading until verified. Account, billing, support, and verification remain accessible when trading is locked.

### Core data model
- `profiles`: `user_id` (Supabase Auth foreign key), `email`, `created_at`. No application-managed password hashes.
- `kyc_verifications`: `user_id`, `provider_reference`, `status`, `verified_at`, `updated_at`; provider webhook verified server-side.
- `subscriptions`: `user_id`, `stripe_customer_id`, `stripe_subscription_id`, `plan`, `status`, `current_period_end`.
- `exchange_connections`: `id`, `user_id`, `exchange`, `status`, `permissions`, `secret_reference`, `revoked_at`; credentials encrypted and isolated from clients.
- `portfolios`: `user_id`, `asset_symbol`, `quantity`, `average_buy_price`, `source_exchange`, `last_synced_at`.
- `market_data`: `symbol`, `current_price`, `percent_change_24h`, `source`, `last_updated`; timestamps and stale-feed warnings required.
- `trade_suggestions`: `id`, `user_id`, `exchange_connection_id`, `symbol`, `side`, `quantity`, `order_type`, `limit_price`, `expires_at`, `status`.
- `trade_approvals`: `id`, `suggestion_id`, `user_id`, `decision`, `approved_order_hash`, `approved_at`, `expires_at`, `consumed_at`.
- `trades`: `id`, `user_id`, `suggestion_id`, `exchange_order_id`, `idempotency_key`, `status`, `created_at`.
- `webhook_events`: `provider`, `event_id` (unique per provider), `processed_at`, `status`.
- `audit_logs`: `actor_id`, `action`, `target_id`, `timestamp`, `metadata` (redacted).

### Trade execution invariant
1. AI generates a non-executable proposal; the UI shows exact exchange, asset, side, quantity, order type, price constraints, fees estimate, and expiration.
2. User explicitly chooses **Yes** or **No** for that specific immutable proposal; no default approval or unattended execution.
3. Backend revalidates authenticated session, verified KYC, active subscription, exchange permissions, proposal expiry, unchanged order hash, market constraints, and one-time approval.
4. A transactional state transition consumes the approval once; an idempotent order-submission worker submits only the approved parameters.
5. Rejected, expired, edited, replayed, or unauthorized proposals **must never** reach the exchange. Retry/reconciliation must not duplicate orders.
6. Exchange API credentials must have **no withdrawal or transfer scope**. AI and support agents cannot call the order-submission path without a fresh, user-specific approval.

### Security and reliability acceptance criteria
- Supabase RLS denies cross-user access; privileged service keys only in server secrets.
- Stripe and KYC webhooks have verified signatures, deduplication, replay resistance, and auditable state transitions.
- KYC provider selection and retention/legal obligations reviewed before collecting identity information.
- Market stream reconnects with backoff, timestamps, stale-data warnings, and reduced-motion support.
- Billing cancellation and account deletion are accessible independently of trading eligibility.
- Separate staging/production credentials and databases; no real orders in staging.
- End-to-end tests cover rejection, approval expiry, double-click/replay, concurrent approvals, revoked credentials, stale prices, webhook retries, and payment failure.
- Production live trading remains **disabled** until all gates, legal review, and end-to-end tests are completed.

## 14. Risk Disclosures and Important Disclaimer

CYF Trading provides software, trading technology, and market information. It does not custody customer assets, guarantee investment returns, or provide individualized investment advice.

Trading cryptocurrencies and other financial assets involves substantial risk, including possible loss of all invested capital. Customers remain responsible for their exchange accounts, trading decisions, and compliance with applicable laws and third-party exchange requirements.

AI-generated information supports customer decision-making; it does not independently authorize financial transactions.

**We provide the tools. Customers control the decisions. The market determines the results.**

---

**CYF Trading — Control Your Future.**
