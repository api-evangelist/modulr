---
name: Set up and execute a Variable Recurring Payment
description: Create an Open Banking VRP consent, confirm funds, and initiate recurring account-to-account payments under the consent.
api: openapi/modulr-api.json
operations: [initiateConsentCreation, confirmFunds, initiateVrpPayment, getVrpPayment, getVrpConsent, revokeVrpConsent]
---

# Set up and execute a Variable Recurring Payment (VRP)

## Auth
HMAC request signing per `authentication/modulr-authentication.yml`. Send `x-mod-version: 1` and a unique `x-mod-nonce`.

## Steps
1. **Create the consent** — `initiateConsentCreation` (`POST /vrp-consents`) with the consent parameters (payer, limits, validity). The payer authorises via their ASPSP. Capture the consent id.
2. **Confirm funds** (optional) — `confirmFunds` (`POST /vrp-consents/{consentId}/funds-confirmation`) to check sufficient funds before initiating.
3. **Initiate a payment** — `initiateVrpPayment` (`POST /vrp`) referencing the authorised consent. **Use a fresh `x-mod-nonce`** per payment.
4. **Track** — `getVrpPayment` (`GET /vrp/{vrpPaymentId}`) for payment status and `getVrpConsent` (`GET /vrp-consents/{consentId}`) for consent state.
5. **Revoke** — `revokeVrpConsent` (`DELETE /vrp-consents/{consentId}`) when the recurring arrangement ends.

## Notes
Covers both sweeping (consumer) VRP and commercial VRP (cVRP). Amounts must stay within the authorised consent limits or the payment is rejected. See idempotency + error handling in `conventions/modulr-conventions.yml`.
