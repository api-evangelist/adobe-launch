---
name: adobe-launch-bootstrap-property
description: Create a new Adobe Launch (Experience Platform Tags) property under a company and give it a first data element and rule, using the Reactor API.
api: Adobe Launch Reactor API
base_url: https://reactor.adobe.io
spec: openapi/adobe-launch-reactor-api-published-openapi.yml
generated: '2026-08-13'
method: generated
source: operationIds verified against openapi/adobe-launch-reactor-api-published-openapi.yml (Adobe-published contract)
operations:
  - listCompanies
  - createProperty
  - createDataElement
  - createRule
  - createRuleComponent
  - listExtensions
mirrors: arazzo/adobe-launch-bootstrap-property-rule-workflow.yml
---

# Bootstrap an Adobe Launch property

Stand up a tag property from nothing: find the company, create the property,
add a data element, add a rule, and attach a component to that rule.

## Before you start

Every request needs three headers. Missing any one of them returns a 403 with
an Adobe error code, not a helpful message.

```
Authorization: Bearer {ACCESS_TOKEN}
x-api-key: {CLIENT_ID}
x-gw-ims-org-id: {ORG_ID}
Accept: application/vnd.api+json;revision=1
Content-Type: application/vnd.api+json
```

`{ACCESS_TOKEN}` comes from an OAuth Server-to-Server credential in Adobe
Developer Console and expires after 24 hours. JWT credentials stopped working
on 2025-01-01. See `scopes/adobe-launch-scopes.yml`.

## Steps

1. **Find the company.** Call `listCompanies`. Almost every organization has
   exactly one. Keep its `id` as `{COMPANY_ID}`.

2. **Create the property.** Call `createProperty` on
   `POST /companies/{COMPANY_ID}/properties`. The `platform` attribute decides
   what kind of property you get — `web` or `mobile` for client-side tags,
   `edge` for an event forwarding property. Keep the returned `id` as
   `{PROPERTY_ID}`; it is prefixed `PR`.

3. **Check what extensions are installed.** Call `listExtensions` on the new
   property. Adobe installs a Core extension automatically, and its rule
   components are what you will reference in step 5. If you need something
   else, run the `adobe-launch-install-extension` skill first.

4. **Create a data element.** Call `createDataElement` on
   `POST /properties/{PROPERTY_ID}/data_elements`. A data element is a named
   pointer to a value — it needs a `delegate_descriptor_id` naming the
   extension module that resolves it, plus the settings that module expects.

5. **Create a rule.** Call `createRule` on
   `POST /properties/{PROPERTY_ID}/rules`. A bare rule does nothing; it is a
   container.

6. **Add a component to the rule.** Call `createRuleComponent` on
   `POST /rules/{RULE_ID}/rule_components`. Every component names a
   `delegate_descriptor_id` from an installed extension and declares whether it
   is an event, a condition or an action.

## Rules of the road

- **There is no idempotency key.** Retrying step 2 after a timeout creates a
  second property. Before retrying any create, list with a filter first:
  `?filter[name]=EQ My Property` (URI-encode it —
  `filter%5Bname%5D=EQ%20My%20Property`).
- Nothing you create here is live yet. Resources only reach a browser once
  they are added to a library, built, and published — see
  `adobe-launch-publish-library`.
- Every step above writes an audit event. If a callback is registered on the
  property it will fire. See `asyncapi/adobe-launch-webhooks.yml`.
- The API returns no 429 and no rate-limit headers. Back off on 5xx; Adobe
  documents that a 500 may itself indicate throttling.
