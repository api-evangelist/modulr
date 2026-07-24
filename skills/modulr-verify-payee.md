---
name: Verify a payee (CoP / VoP)
description: Run Confirmation of Payee and Verification of Payee account-name checks before sending a payment to reduce misdirected-payment and APP fraud.
api: openapi/modulr-api.json
operations: [createOutboundCop, createOutboundVop]
---

# Verify a payee (CoP / VoP)

## Auth
HMAC request signing per `authentication/modulr-authentication.yml`. Send `x-mod-version: 1` and a unique `x-mod-nonce`.

## Steps
1. **Confirmation of Payee (UK)** — `createOutboundCop` (`POST /account-name-check`) with the payee name, sort code, and account number. The response indicates a match / close match / no match so you can warn the user before sending.
2. **Verification of Payee (SEPA/EU)** — `createOutboundVop` (`POST /verify-payee`) for EU payee verification.
3. **Act on the result** — proceed to `sendPayment` only after handling a non-match; surface close-match names to the user for confirmation.

## Notes
CoP/VoP are fraud controls, not payment guarantees. Combine with the idempotency + error-handling rules in `conventions/modulr-conventions.yml` when you subsequently send.
