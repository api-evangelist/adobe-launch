---
name: adobe-launch-install-extension
description: Find an Adobe Launch extension package and install it on a property, then confirm which rule components it makes available.
api: Adobe Launch Reactor API
base_url: https://reactor.adobe.io
spec: openapi/adobe-launch-reactor-api-published-openapi.yml
generated: '2026-08-13'
method: generated
source: operationIds verified against openapi/adobe-launch-reactor-api-published-openapi.yml (Adobe-published contract)
operations:
  - listExtensionPackages
  - retrieveExtensionPackage
  - retrieveExtensionPackageVersion
  - createExtension
  - listExtensions
  - retrievePackageForExtension
  - reviseExtension
mirrors: arazzo/adobe-launch-install-extension-workflow.yml
---

# Install an Adobe Launch extension

Extension *packages* are global to the platform. Extension *instances* belong
to one property. Installing means creating an instance from a package.

## Steps

1. **Find the package.** `listExtensionPackages` on
   `GET /extension_packages`, filtered by name:
   `?filter[name]=EQ adobe-analytics` (URI-encode it). Keep the `id`.

2. **Check its versions.** `retrieveExtensionPackageVersion` on
   `GET /extension_packages/{EXTENSION_PACKAGE_ID}/versions` tells you what is
   actually available, which matters when the package has a private release
   alongside a public one.

3. **Install it.** `createExtension` on
   `POST /properties/{PROPERTY_ID}/extensions`, referencing the extension
   package in `relationships.extension_package`. The `settings` attribute
   carries whatever configuration that package requires — read it off the
   package's own descriptor, not from memory.

4. **Confirm.** `listExtensions` on
   `GET /properties/{PROPERTY_ID}/extensions`. The installed extension's
   `delegate_descriptor_id` values are what rule components and data elements
   will reference. Nothing you build can name a delegate from an extension that
   is not installed on that property.

5. **Update settings later** with `reviseExtension` on
   `PATCH /extensions/{EXTENSION_ID}`. Note the verb: revising creates a new
   revision, so the previous configuration stays addressable through
   `listExtensionRevisions`.

## Rules of the road

- A privately released package needs an extension package usage authorization
  before a company can install it —
  `createExtensionPackageUsageAuthorization` on
  `POST /extension_packages/{EXTENSION_PACKAGE_ID}/extension_package_usage_authorizations`.
  Without it, step 3 returns 403 even though step 1 found the package.
- Installing an extension changes nothing in the browser until the extension is
  added to a library and that library is built. See
  `adobe-launch-publish-library`.
- No idempotency key. Before retrying step 3, call `listExtensions` and check.
