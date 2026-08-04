# Modulr (modulr)

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

Modulr is a United Kingdom-based embedded payments and Banking-as-a-Service platform that lets businesses and software platforms open programmable eMoney accounts and move money automatically via a single API. As a licensed e-money institution and direct participant in the UK Faster Payments and Bacs schemes (with SEPA reach in the EU through its Dutch entity), Modulr provides the accounts, payment rails, card issuing, and Open Banking connectivity that fintechs, payroll providers, lenders, marketplaces, and accounting and travel platforms embed into their own products.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/modulr/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/modulr/refs/heads/main/apis.yml)

## Tags

- Payments
- United Kingdom
- Banking-as-a-Service
- Embedded Finance
- Payment Processing
- Account-to-Account
- Open Banking
- Faster Payments
- Card Issuing
- Direct Debit
- Confirmation of Payee
- Variable Recurring Payments

## Timestamps

- **Created:** 2026-07-24
- **Modified:** 2026-07-24

## API Posture

Modulr is API-native. It publishes a public developer portal on ReadMe at [modulr.readme.io](https://modulr.readme.io/) with getting-started guides, an [API reference](https://modulr.readme.io/reference), a changelog, and a self-serve sandbox. A single downloadable **OpenAPI 3.1.0** definition ("Modulr API", v1.0 — 171 paths / 207 operations across 26 tags) was harvested verbatim from the ReadMe API registry that powers the reference pages and is stored at [`openapi/modulr-api.json`](openapi/modulr-api.json). Authentication is API-key based (Authorization header) with HMAC request signing; a short-lived bearer token is used for secure PCI card-detail retrieval. Transport is REST/HTTPS with an extensive webhook/notification layer. No public GraphQL, gRPC, Postman collection, or AsyncAPI document was found.

- **Sandbox base URL:** `https://api-sandbox.modulrfinance.com/api-sandbox-token` (declared in the spec)
- **Production base URL:** `https://api.modulrfinance.com` (live; HTTP 403 without credentials)

## APIs

### Modulr Accounts API

Create, retrieve, edit, block/unblock and close programmable eMoney accounts, manage access groups and account rules, and read balances.

- **Human URL:** [https://modulr.readme.io/docs/account](https://modulr.readme.io/docs/account)
- **Base URL:** `https://api.modulrfinance.com`
- [OpenAPI](openapi/modulr-api.json)

### Modulr Payments API

Outbound, inbound, bulk, batch and future-dated payments over UK Faster Payments and Bacs, plus international SWIFT payments, with transaction retrieval and reconciliation.

- **Human URL:** [https://modulr.readme.io/docs/payments-2](https://modulr.readme.io/docs/payments-2)
- **Base URL:** `https://api.modulrfinance.com`
- [OpenAPI](openapi/modulr-api.json)

### Modulr Cards API

Issue and manage virtual and physical cards, including tokenization, PIN management, card controls, transactions, secure card-detail retrieval and bulk card operations.

- **Human URL:** [https://modulr.readme.io/reference](https://modulr.readme.io/reference)
- **Base URL:** `https://api.modulrfinance.com`
- [OpenAPI](openapi/modulr-api.json)

### Modulr Direct Debits API

UK Bacs Direct Debit mandates and collections, outbound mandate operations and indemnity claims for recurring collection use cases.

- **Human URL:** [https://modulr.readme.io/reference](https://modulr.readme.io/reference)
- **Base URL:** `https://api.modulrfinance.com`
- [OpenAPI](openapi/modulr-api.json)

### Modulr Customers API

Create and verify customers, run KYC/KYB onboarding, manage associates and tax identifiers, and upload supporting documents for compliance.

- **Human URL:** [https://modulr.readme.io/docs/customer](https://modulr.readme.io/docs/customer)
- **Base URL:** `https://api.modulrfinance.com`
- [OpenAPI](openapi/modulr-api.json)

### Modulr Payee Verification API

Confirmation of Payee (CoP) and Verification of Payee (VoP) account name checking to reduce misdirected-payment and APP fraud risk before payments are sent.

- **Human URL:** [https://modulr.readme.io/reference](https://modulr.readme.io/reference)
- **Base URL:** `https://api.modulrfinance.com`
- [OpenAPI](openapi/modulr-api.json)

### Modulr Payment Initiation API

Open Banking Payment Initiation Services (PIS) — immediate account-to-account payments and standing orders from a payer's bank account through connected ASPSPs.

- **Human URL:** [https://modulr.readme.io/reference](https://modulr.readme.io/reference)
- **Base URL:** `https://api.modulrfinance.com`
- [OpenAPI](openapi/modulr-api.json)

### Modulr Variable Recurring Payments API

Consumer and commercial Variable Recurring Payments (VRP) — manage consents and execute recurring account-to-account payments under Open Banking.

- **Human URL:** [https://modulr.readme.io/reference](https://modulr.readme.io/reference)
- **Base URL:** `https://api.modulrfinance.com`
- [OpenAPI](openapi/modulr-api.json)

### Modulr Notifications API

Partner- and customer-level webhook subscriptions for account, payment, customer, compliance and Direct Debit events, and retrieval of failed webhook deliveries.

- **Human URL:** [https://modulr.readme.io/docs/notifications-1](https://modulr.readme.io/docs/notifications-1)
- **Base URL:** `https://api.modulrfinance.com`
- [OpenAPI](openapi/modulr-api.json)

## Common Properties

- [Website](https://www.modulrfinance.com/)
- [Developer Portal](https://modulr.readme.io/)
- [Documentation](https://modulr.readme.io/docs/intro)
- [API Reference](https://modulr.readme.io/reference)
- [Getting Started](https://modulr.readme.io/docs/getting-started)
- [Authentication](https://modulr.readme.io/docs/authentication)
- [GitHub Organization](https://github.com/Modulr-finance)
- [LinkedIn](https://www.linkedin.com/company/modulr-finance)
- [Status Page](https://status.modulrfinance.com/)
- [Help Center](https://knowledge.modulrfinance.com/knowledge-hub)
- [Changelog](https://modulr.readme.io/changelog)
- [Pricing](https://www.modulrfinance.com/pricing)
- [Blog](https://www.modulrfinance.com/blog)
- [Privacy Policy](https://www.modulrfinance.com/privacy-policy)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
