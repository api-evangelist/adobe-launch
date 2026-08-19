---
name: adobe-launch-provision-environment
description: Create a host and an environment on an Adobe Launch property so builds have somewhere to be delivered, and read back the install snippet.
api: Adobe Launch Reactor API
base_url: https://reactor.adobe.io
spec: openapi/adobe-launch-reactor-api-published-openapi.yml
generated: '2026-08-13'
method: generated
source: operationIds verified against openapi/adobe-launch-reactor-api-published-openapi.yml (Adobe-published contract)
operations:
  - listHosts
  - createHost
  - listEnvironments
  - createEnvironment
  - retrieveEnvironment
  - retrieveEnvironmentHost
  - retrieveHostRelationship
mirrors: arazzo/adobe-launch-provision-environment-workflow.yml
---

# Provision an Adobe Launch host and environment

A build has to land somewhere. That somewhere is an *environment*, and an
environment delivers through a *host*.

## Steps

1. **Check for an existing host.** `listHosts` on
   `GET /properties/{PROPERTY_ID}/hosts`.

2. **Create one if needed.** `createHost` on
   `POST /properties/{PROPERTY_ID}/hosts`. The `type_of` attribute chooses
   between Adobe-managed CDN delivery and a customer-managed SFTP target. SFTP
   hosts carry credentials; Adobe-managed hosts do not.

3. **Create the environment.** `createEnvironment` on
   `POST /properties/{PROPERTY_ID}/environments`, referencing the host in
   `relationships.host`. The `stage` attribute is `development`, `staging` or
   `production`. A property normally has one of each.

4. **Read back the delivery details.** `retrieveEnvironment` on
   `GET /environments/{ENVIRONMENT_ID}` returns the library URL and the install
   snippets for that environment. This is what goes into the page — one
   environment, one URL, and the contents of that URL change every time a
   library bound to it is built.

5. **Confirm the host binding.** `retrieveEnvironmentHost` on
   `GET /environments/{ENVIRONMENT_ID}/host`, or
   `retrieveHostRelationship` on
   `GET /environments/{ENVIRONMENT_ID}/relationships/host` if you only want the
   resource identifier.

## Rules of the road

- The environment is what a library binds to before it can build. If
  `adobe-launch-publish-library` step 3 has nothing to bind, come here first.
- Deleting an environment that a published library points at breaks delivery
  for everyone loading that URL. There is no soft delete and no Sunset header
  warning consumers.
- No idempotency key: list before you retry a create.
