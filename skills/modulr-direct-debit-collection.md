---
name: Collect via Bacs Direct Debit
description: Set up a Bacs Direct Debit mandate against a Modulr account, schedule collections, and monitor collection status.
api: openapi/modulr-api.json
operations: [createMandate, createCollectionSchedule, getCollections, getMandates, cancelCollection]
---

# Collect via Bacs Direct Debit

## Auth
HMAC request signing per `authentication/modulr-authentication.yml`. Send `x-mod-version: 1` and a unique `x-mod-nonce`.

## Prerequisites
Direct Debit collections require additional onboarding — see docs "Getting started with DD collections". Bacs scheme timing rules apply.

## Steps
1. **Create the mandate** — `createMandate` (`POST /accounts/{accountId}/mandates`) with the payer's bank details and reference. For volume use `createBulkMandate` (`POST /mandates/bulk-create`).
2. **Schedule collections** — `createCollectionSchedule` (`POST /mandates/{mandateId}/collectionschedules`) to set up recurring collections against the mandate.
3. **Monitor** — `getCollections` (`GET /collections`) and `getMandates` (`GET /mandates`) to track status. Subscribe to the Direct Debit Collection Status, Unpaid Collection, and Incoming Collection webhooks (`asyncapi/modulr-webhooks.yml`).
4. **Cancel if needed** — `cancelCollection` (`POST /collections/{collectionId}/cancel`) or `cancelMandate` (`POST /mandates/{mandateId}/cancel`).

## Notes
Collections and indemnity claims (DDIC) are surfaced via webhooks; reconcile returned funds against your ledger.
