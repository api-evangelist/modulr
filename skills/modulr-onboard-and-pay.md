---
name: Onboard a customer and make a payment
description: Create and verify a Modulr customer, open an eMoney account, save a beneficiary, verify the payee, and send a Faster Payments payment.
api: openapi/modulr-api.json
operations: [createCustomer, createAccount, createBeneficiary, createOutboundCop, sendPayment, getPayments]
---

# Onboard a customer and make a payment

Use the Modulr API to onboard a customer, fund/open an account, and send an outbound payment safely.

## Auth
- Production uses **HMAC request signing**. Set `Date` (RFC 7231 GMT), a unique `x-mod-nonce`, and an `Authorization: Signature ...` header (hmac-sha1 over `date` + `x-mod-nonce`). See `authentication/modulr-authentication.yml`.
- Sandbox may use the token base URL `https://api-sandbox.modulrfinance.com/api-sandbox-token/` with the raw API Key.
- Send `x-mod-version: 1`.

## Steps
1. **Create the customer** — `createCustomer` (`POST /customers`) with KYC/KYB details. Capture the returned customer id (e.g. `C0…`).
2. **Open an account** — `createAccount` (`POST /customers/{customerId}/accounts`) to open a programmable eMoney account for the customer. Capture the account id.
3. **Save the payee** — `createBeneficiary` (`POST /customers/{customerId}/beneficiaries`) with the destination sort code + account number.
4. **Confirm the payee** — `createOutboundCop` (`POST /account-name-check`) to run Confirmation of Payee before sending, reducing misdirected-payment/APP-fraud risk.
5. **Send the payment** — `sendPayment` (`POST /payments`) from the source account to the beneficiary. **Set a fresh `x-mod-nonce`**; add an `externalReference` for reconciliation.
6. **Reconcile** — `getPayments` (`GET /payments`) or subscribe to the Outbound Payments webhook. A 2xx with status `VALIDATED` is not final — poll until `PROCESSED` or handle error states.

## Idempotency & retries
- To safely retry a failed POST (timeout/5xx), **reuse the same `x-mod-nonce`** and set `x-mod-retry: true`. Modulr returns the original response for a seen nonce for **48 hours**.
- Only send with a **new nonce** if you have confirmed the prior request did not process. See `conventions/modulr-conventions.yml` and `errors/modulr-problem-types.yml`.
