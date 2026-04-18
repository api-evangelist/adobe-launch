# Adobe Launch (Adobe Experience Platform Tags) (adobe-launch)

Adobe Launch, now known as Adobe Experience Platform Tags, is a next-generation tag management system that unifies the client-side marketing ecosystem by empowering developers to build integrations on a robust, extensible platform that partners, clients, and the broader industry can build on and contribute to.

**URL:** [Visit APIs.json URL](https://raw.githubusercontent.com/api-evangelist/adobe-launch/refs/heads/main/apis.yml)

## Scope

- **Type:** Index

## Tags

Data Collection, Edge Network, Event Forwarding, Marketing Technology, Tag Management

## Timestamps

- **Created:** 2024-01-15
- **Modified:** 2026-04-18

## APIs

### Adobe Launch Reactor API
The Reactor API allows you to programmatically manage all resources for Adobe Experience Platform Tags, including properties, data elements, rules, extensions, library builds, and environments. It follows the JSON API specification for request and response formatting.

**Human URL:** [https://experienceleague.adobe.com/en/docs/experience-platform/tags/api/overview](https://experienceleague.adobe.com/en/docs/experience-platform/tags/api/overview)

#### Tags

Automation, Data Collection, Marketing Technology, Tag Management

#### Properties

- [Documentation](https://experienceleague.adobe.com/en/docs/experience-platform/tags/api/overview)
- [APIReference](https://developer.adobe.com/experience-platform-apis/references/reactor/)
- [Authentication](https://experienceleague.adobe.com/en/docs/experience-platform/tags/api/getting-started)
- [GettingStarted](https://experienceleague.adobe.com/en/docs/experience-platform/tags/api/getting-started)
- [SDK](https://www.npmjs.com/package/@adobe/reactor-sdk)
- [ChangeLog](https://experienceleague.adobe.com/en/docs/experience-platform/release-notes/latest)
- [OpenAPI](openapi/reactor-api.yml)

### Adobe Launch Extension API
API for developing custom extensions for Adobe Experience Platform Tags, allowing developers to create integrations with third-party tools and services. Extensions are the building blocks of tags and consist of library modules and views.

**Human URL:** [https://experienceleague.adobe.com/en/docs/experience-platform/tags/extension-dev/overview](https://experienceleague.adobe.com/en/docs/experience-platform/tags/extension-dev/overview)

#### Tags

Development, Extensions, Integrations, Tag Management

#### Properties

- [Documentation](https://experienceleague.adobe.com/en/docs/experience-platform/tags/extension-dev/overview)
- [SDK](https://www.npmjs.com/package/@adobe/reactor-scaffold)
- [OpenAPI](openapi/extension-api.yml)

### Adobe Experience Platform Event Forwarding API
Event forwarding allows you to send collected event data to destinations for server-side processing using the Adobe Experience Platform Edge Network. It decreases web page weight by moving tasks from the client to Adobe servers.

**Human URL:** [https://experienceleague.adobe.com/en/docs/experience-platform/tags/event-forwarding/overview](https://experienceleague.adobe.com/en/docs/experience-platform/tags/event-forwarding/overview)

#### Tags

Data Collection, Edge Network, Event Forwarding, Server Side

#### Properties

- [Documentation](https://experienceleague.adobe.com/en/docs/experience-platform/tags/event-forwarding/overview)
- [GettingStarted](https://experienceleague.adobe.com/en/docs/experience-platform/tags/event-forwarding/getting-started)
- [OpenAPI](openapi/event-forwarding-api.yml)

### Adobe Experience Platform Data Collection API
The Data Collection APIs provide endpoints for sending data directly to the Adobe Experience Platform Edge Network, including the Edge Network API for authenticated and non-authenticated data ingestion and the Media Edge API for media tracking data.

**Human URL:** [https://developer.adobe.com/data-collection-apis/docs/](https://developer.adobe.com/data-collection-apis/docs/)

#### Tags

Analytics, Data Collection, Data Ingestion, Edge Network

#### Properties

- [Documentation](https://developer.adobe.com/data-collection-apis/docs/)
- [GettingStarted](https://developer.adobe.com/data-collection-apis/docs/getting-started/)
- [Authentication](https://developer.adobe.com/data-collection-apis/docs/getting-started/authentication)
- [OpenAPI](openapi/data-collection-api.yml)

## Common Properties

- [TermsOfService](https://www.adobe.com/legal/terms.html)
- [PrivacyPolicy](https://www.adobe.com/privacy.html)
- [Console](https://developer.adobe.com/developer-console/)
- [Portal](https://developer.adobe.com/)
- [StatusPage](https://status.adobe.com/)
- [Blog](https://medium.com/adobetech)
- [GitHubOrganization](https://github.com/adobe)
- [SignUp](https://developer.adobe.com/developer-console/)
- [Authentication](https://experienceleague.adobe.com/en/docs/experience-platform/landing/platform-apis/api-authentication)
- [ChangeLog](https://experienceleague.adobe.com/en/docs/experience-platform/release-notes/latest)
- [Features](https://experienceleague.adobe.com/en/docs/experience-platform/tags/home)
- [SDK](https://www.npmjs.com/package/@adobe/reactor-sdk)

## Capabilities

Naftiko capability definitions composing 4 APIs into 2 customer-facing workflows.

### Shared Definitions (per-API)

| File | API | Description |
|------|-----|-------------|
| [reactor.yaml](capabilities/shared/reactor.yaml) | Adobe Launch Reactor API | Core tag management for properties, rules, data elements, extensions, libraries, and builds |
| [extension.yaml](capabilities/shared/extension.yaml) | Adobe Launch Extension API | Extension package development and marketplace management |
| [event-forwarding.yaml](capabilities/shared/event-forwarding.yaml) | Adobe Experience Platform Event Forwarding API | Server-side event forwarding with secrets management |
| [data-collection.yaml](capabilities/shared/data-collection.yaml) | Adobe Experience Platform Data Collection API | Edge Network data ingestion and media tracking |

### Workflow Capabilities

| Workflow | APIs Combined | Tools | Persona |
|----------|---------------|-------|---------|
| [tag-management.yaml](capabilities/tag-management.yaml) | Reactor + Extension | 16 | Marketing Technologist / Web Developer |
| [data-collection-pipeline.yaml](capabilities/data-collection-pipeline.yaml) | Event Forwarding + Data Collection | 10 | Data Engineer |

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
