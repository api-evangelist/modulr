---
name: Issue and manage a card
description: Issue a virtual or physical card against a Modulr account, activate it, and retrieve secure card details via a tokenized flow.
api: openapi/modulr-api.json
operations: [createCard, createPhysicalCard, activateCard, createShareSecureDetails, generateCardHolderToken, blockCard]
---

# Issue and manage a card

## Auth
HMAC request signing per `authentication/modulr-authentication.yml`. Send `x-mod-version: 1` and a unique `x-mod-nonce` per request.

## Steps
1. **Issue a virtual card** — `createCard` (`POST /accounts/{accountId}/cards`) against a funded account. For a physical card use `createPhysicalCard` (`POST /accounts/{accountId}/physical-cards`).
2. **Activate** — `activateCard` (`POST /cards/{cardId}/activate`) when the cardholder receives/enables the card.
3. **Retrieve secure (PCI) card details** — mint a cardholder token with `generateCardHolderToken` (`POST /cards/{cardId}/secure-details-token`), then set up a secure-details share via `createShareSecureDetails` (`POST /cards/{cardId}/share-secure-details`). This keeps PAN/CVV handling PCI-compliant. See docs "PCI - Retrieve secure card details".
4. **Risk controls** — `blockCard` (`POST /cards/{cardId}/block`) to temporarily disable authorisations; `suspendCard`/`cancelCard`/`expireCard` for stronger states.

## Testing
Use the sandbox **Card Simulator** operations (authorisations, settlements, chargebacks) to drive card lifecycle and decline scenarios. See `sandbox/modulr-sandbox.yml` and decline reasons in `errors/modulr-decline-codes.yml`.
