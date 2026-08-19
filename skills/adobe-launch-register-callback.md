---
name: adobe-launch-register-callback
description: Register an Adobe Launch callback so a URL you host receives audit events — for example build.created — instead of polling the Reactor API.
api: Adobe Launch Reactor API
base_url: https://reactor.adobe.io
spec: openapi/adobe-launch-reactor-api-published-openapi.yml
generated: '2026-08-13'
method: generated
source: >-
  operationIds verified against openapi/adobe-launch-reactor-api-published-openapi.yml;
  delivery and retry behaviour from
  https://experienceleague.adobe.com/en/docs/experience-platform/tags/api/endpoints/callbacks
operations:
  - listCallbacks
  - createCallback
  - retrieveCallback
  - updateCallback
  - deleteCallback
mirrors: arazzo/adobe-launch-register-callback-workflow.yml
---

# Register an Adobe Launch callback

Callbacks are the Adobe Launch webhook surface. Adobe POSTs to a URL you host
when audit events happen on a property.

## Steps

1. **List what is already registered.** `listCallbacks` on
   `GET /properties/{PROPERTY_ID}/callbacks`. Callbacks are per property, so a
   multi-property org needs one per property.

2. **Create the callback.** `createCallback` on
   `POST /properties/{PROPERTY_ID}/callbacks` with two attributes:
   - `url` — the endpoint you host.
   - `subscriptions` — an array of audit event type strings.

3. **Name the events.** Event types are `{RESOURCE_TYPE}.{EVENT}`.
   `{RESOURCE_TYPE}` is one of `property`, `extension`, `data_element`, `rule`,
   `rule_component`, `library`, `build`, `environment`, `host`. `{EVENT}` is
   one of `created`, `updated`, `deleted`. So `build.created` and
   `library.updated` are the two most useful for a publishing pipeline.

4. **Adjust or remove.** `updateCallback` on `PATCH /callbacks/{CALLBACK_ID}`,
   `deleteCallback` on `DELETE /callbacks/{CALLBACK_ID}`.

## Rules of the road

- **`subscriptions` is typed as an unconstrained array of strings.** The
  published contract will not reject a typo, and neither will the API — you
  simply never receive that event. Verify by making the change and watching for
  the delivery.
- **Adobe does not sign callback deliveries.** There is no signature header, no
  shared secret and no documented verification procedure. Treat the callback as
  an untrusted trigger: use a hard-to-guess URL, and re-read the resource
  through the Reactor API before acting on it.
- **Your endpoint must answer 200 or 201.** Anything else is a failure.
- **Retries are 1 minute, 5 minutes, 30 minutes, 1 hour, 12 hours, 1 day,
  3 days — then the message is discarded.** There is no dead-letter queue. A
  consumer down for more than three days must reconcile from
  `GET /audit_events`.
- The payload shape is not published. Do not build a schema-strict parser
  around an assumed body; read the fields you need defensively and confirm
  against the audit event resource.
