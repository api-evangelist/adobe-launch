# Adobe Launch (adobe-launch)

Adobe Launch, now known as Adobe Experience Platform Tags, is a next-generation tag management system that unifies the client-side marketing ecosystem by empowering developers to build integrations on a robust, extensible platform that partners, clients, and the broader industry can build on and contribute to.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/adobe-launch/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/adobe-launch/refs/heads/main/apis.yml)

## Scope

- **Type:** Index

## Tags

- Data Collection
- Edge Network
- Event Forwarding
- Marketing Technology
- Tag Management

## Timestamps

- **Created:** 2024-01-15
- **Modified:** 2026-05-19

## APIs

### Adobe Launch Reactor API

The Reactor API allows you to programmatically manage all resources for Adobe Experience Platform Tags, including properties, data elements, rules, extensions, library builds, and environments. It follows the JSON API specification for request and response formatting.

- **Human URL:** [https://experienceleague.adobe.com/en/docs/experience-platform/tags/api/overview](https://experienceleague.adobe.com/en/docs/experience-platform/tags/api/overview)
- **Base URL:** `https://reactor.adobe.io`

#### Tags

- Automation
- Data Collection
- Marketing Technology
- Tag Management

#### Properties

- [Documentation](https://experienceleague.adobe.com/en/docs/experience-platform/tags/api/overview)
- [API Reference](https://developer.adobe.com/experience-platform-apis/references/reactor/)
- [Authentication](https://experienceleague.adobe.com/en/docs/experience-platform/tags/api/getting-started)
- [Getting Started](https://experienceleague.adobe.com/en/docs/experience-platform/tags/api/getting-started)
- [SDK](https://www.npmjs.com/package/@adobe/reactor-sdk)
- [Changelog](https://experienceleague.adobe.com/en/docs/experience-platform/release-notes/latest)
- [OpenAPI](openapi/reactor-api.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/reactor-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/reactor-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)
- [JSON Schema](json-schema/property.json) — [JSON Schema](https://json-schema.org/specification)
- [JSON Schema](json-schema/rule.json) — [JSON Schema](https://json-schema.org/specification)
- [JSON Schema](json-schema/data-element.json) — [JSON Schema](https://json-schema.org/specification)
- [JSON Schema](json-schema/extension.json) — [JSON Schema](https://json-schema.org/specification)
- [JSON Schema](json-schema/library.json) — [JSON Schema](https://json-schema.org/specification)
- [JSON Schema](json-schema/build.json) — [JSON Schema](https://json-schema.org/specification)
- [JSON-LD](json-ld/context.jsonld) — [JSON-LD](https://www.w3.org/TR/json-ld11/)

### Adobe Launch Extension API

API for developing custom extensions for Adobe Experience Platform Tags, allowing developers to create integrations with third-party tools and services. Extensions are the building blocks of tags and consist of library modules and views.

- **Human URL:** [https://experienceleague.adobe.com/en/docs/experience-platform/tags/extension-dev/overview](https://experienceleague.adobe.com/en/docs/experience-platform/tags/extension-dev/overview)
- **Base URL:** `https://reactor.adobe.io`

#### Tags

- Development
- Extensions
- Integrations
- Tag Management

#### Properties

- [Documentation](https://experienceleague.adobe.com/en/docs/experience-platform/tags/extension-dev/overview)
- [SDK](https://www.npmjs.com/package/@adobe/reactor-scaffold)
- [SDK](https://www.npmjs.com/package/@adobe/reactor-sandbox)
- [OpenAPI](openapi/extension-api.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/extension-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/extension-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)
- [JSON Schema](json-schema/extension.json) — [JSON Schema](https://json-schema.org/specification)
- [JSON-LD](json-ld/context.jsonld) — [JSON-LD](https://www.w3.org/TR/json-ld11/)

### Adobe Experience Platform Event Forwarding API

Event forwarding allows you to send collected event data to destinations for server-side processing using the Adobe Experience Platform Edge Network. It decreases web page weight by moving tasks from the client to Adobe servers.

- **Human URL:** [https://experienceleague.adobe.com/en/docs/experience-platform/tags/event-forwarding/overview](https://experienceleague.adobe.com/en/docs/experience-platform/tags/event-forwarding/overview)
- **Base URL:** `https://reactor.adobe.io`

#### Tags

- Data Collection
- Edge Network
- Event Forwarding
- Server Side

#### Properties

- [Documentation](https://experienceleague.adobe.com/en/docs/experience-platform/tags/event-forwarding/overview)
- [Getting Started](https://experienceleague.adobe.com/en/docs/experience-platform/tags/event-forwarding/getting-started)
- [OpenAPI](openapi/event-forwarding-api.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/event-forwarding-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/event-forwarding-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)
- [JSON-LD](json-ld/context.jsonld) — [JSON-LD](https://www.w3.org/TR/json-ld11/)

### Adobe Experience Platform Data Collection API

The Data Collection APIs provide endpoints for sending data directly to the Adobe Experience Platform Edge Network, including the Edge Network API for authenticated and non-authenticated data ingestion and the Media Edge API for media tracking data.

- **Human URL:** [https://developer.adobe.com/data-collection-apis/docs/](https://developer.adobe.com/data-collection-apis/docs/)
- **Base URL:** `https://edge.adobedc.net`

#### Tags

- Analytics
- Data Collection
- Data Ingestion
- Edge Network

#### Properties

- [Documentation](https://developer.adobe.com/data-collection-apis/docs/)
- [Getting Started](https://developer.adobe.com/data-collection-apis/docs/getting-started/)
- [Authentication](https://developer.adobe.com/data-collection-apis/docs/getting-started/authentication)
- [OpenAPI](openapi/data-collection-api.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/data-collection-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/data-collection-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)
- [JSON-LD](json-ld/context.jsonld) — [JSON-LD](https://www.w3.org/TR/json-ld11/)

## Common Properties

- [Arazzo Workflows](arazzo/) — [Arazzo Specification](https://spec.openapis.org/arazzo/latest.html)
- [Terms of Service](https://www.adobe.com/legal/terms.html)
- [Privacy Policy](https://www.adobe.com/privacy.html)
- [Console](https://developer.adobe.com/developer-console/)
- [Portal](https://developer.adobe.com/)
- [Status Page](https://status.adobe.com/)
- [Blog](https://medium.com/adobetech)
- [Blog R S S](https://medium.com/feed/adobetech)
- [GitHub Organization](https://github.com/adobe)
- [Sign Up](https://developer.adobe.com/developer-console/)
- [Authentication](https://experienceleague.adobe.com/en/docs/experience-platform/landing/platform-apis/api-authentication)
- [Changelog](https://experienceleague.adobe.com/en/docs/experience-platform/release-notes/latest)
- [Features](https://experienceleague.adobe.com/en/docs/experience-platform/tags/home)
- [Use Cases](https://experienceleague.adobe.com/en/docs/experience-platform/tags/home)
- [Integrations](https://experienceleague.adobe.com/en/docs/experience-platform/tags/home)
- [SDK](https://www.npmjs.com/package/@adobe/reactor-sdk)
- [SDK](https://www.npmjs.com/package/@adobe/reactor-scaffold)
- [SDK](https://www.npmjs.com/package/@adobe/reactor-sandbox)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
