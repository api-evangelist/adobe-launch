---
name: adobe-launch-publish-library
description: Take an Adobe Launch library through the publishing flow — assemble its resources, submit, approve, build, and poll the asynchronous build to completion.
api: Adobe Launch Reactor API
base_url: https://reactor.adobe.io
spec: openapi/adobe-launch-reactor-api-published-openapi.yml
generated: '2026-08-13'
method: generated
source: operationIds verified against openapi/adobe-launch-reactor-api-published-openapi.yml (Adobe-published contract)
operations:
  - listLibraries
  - createLibrary
  - addLibraryRules
  - addDataElement
  - addExtension
  - updateLibraryRelationship
  - updateLibrary
  - createBuild
  - getBuild
  - listLibraryBuilds
mirrors: arazzo/adobe-launch-publish-library-workflow.yml
---

# Publish an Adobe Launch library

Nothing you create in a property reaches a browser until it is in a library,
that library is built, and the build is delivered to an environment's host.
This is that flow.

## Steps

1. **Create or find the library.** `createLibrary` on
   `POST /properties/{PROPERTY_ID}/libraries`, or `listLibraries` filtered by
   state: `?filter[state]=EQ development` (URI-encoded as
   `filter%5Bstate%5D=EQ%20development`).

2. **Put resources in it.** Libraries take resources through *relationship*
   routes, not through the library body:
   - `addLibraryRules` — `POST /libraries/{LIBRARY_ID}/relationships/rules`
   - `addDataElement` — `POST /libraries/{LIBRARY_ID}/relationships/data_elements`
   - `addExtension` — `POST /libraries/{LIBRARY_ID}/relationships/extensions`

   Each takes JSON:API resource identifier objects (`{"type": ..., "id": ...}`),
   not full resources. This is the single most common Reactor mistake: PATCHing
   the library itself will not add anything to it.

3. **Bind an environment.** `updateLibraryRelationship` on
   `PATCH /libraries/{LIBRARY_ID}/relationships/environment`. A build has
   nowhere to go without this. If the property has no environment yet, run
   `adobe-launch-provision-environment` first.

4. **Move it through the states.** `updateLibrary` on
   `PATCH /libraries/{LIBRARY_ID}`, setting `meta.action`. The flow is
   `development -> submitted -> approved -> published`. Approval and publishing
   require the corresponding rights on the product profile; a credential
   without them gets a 403, not a validation error.

5. **Build it.** `createBuild` on `POST /libraries/{LIBRARY_ID}/builds`.
   **This is asynchronous.** The response is a build resource, not a finished
   artifact.

6. **Poll the build.** `getBuild` on `GET /builds/{BUILD_ID}` until its status
   attribute settles. Poll — do **not** retry `createBuild`. There is no
   idempotency key, so a retry queues a second build of the same library.

## Rules of the road

- Use `listLibraryBuilds` (`GET /libraries/{LIBRARY_ID}/builds`) to see build
  history rather than assuming the last build you created is the current one.
- Republishing an already-successful build is a separate operation,
  `republishBuild` — see `adobe-launch-republish-build`.
- Poll with exponential backoff and jitter. There are no rate-limit headers to
  read, and Adobe documents that a 500 may indicate throttling.
- Every state change emits `library.updated` and `build.created` audit events,
  which is the natural thing for a callback to subscribe to instead of polling.
  See `adobe-launch-register-callback`.
