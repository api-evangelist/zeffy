# Zeffy (zeffy)

Zeffy is a 100% free fundraising platform for nonprofits (formerly Simplyk, based in Montreal) - donation forms, event ticketing, peer-to-peer campaigns, memberships, e-commerce, and donor management - with no platform fees, no transaction fees, and no credit-card fees. Zeffy is funded entirely by optional tips left by donors at checkout. It exposes a **free public REST API** that gives organization admins **read-only** access to their **Payments**, **Contacts**, and **Campaigns** data, plus outbound **webhooks** that POST payment details to a configured URL when a payment is completed.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/zeffy/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/zeffy/refs/heads/main/apis.yml)

## Access Model

- **Base URL:** `https://api.zeffy.com/api/v1`
- **Auth:** Per-organization API key generated under **Settings → Integrations**, sent as `Authorization: Bearer YOUR_API_KEY`.
- **Read-only:** You can pull data out but cannot create or modify records through the API.
- **Pagination:** Cursor-based (`has_more`, `next_cursor`).
- **Rate limit:** 100 requests per minute per API key (HTTP `429` on exceed). HTTPS only.

The list endpoints (`GET /payments`, `GET /contacts`, `GET /campaigns`), base URL, Bearer auth, cursor pagination, and rate limit are confirmed from Zeffy's public documentation. The get-by-id paths and per-resource query parameters in the OpenAPI are **honestly modeled** from documented capabilities (looking up a specific payment, looking up a person by ID or email, filtering payments by currency/status/type/contact/campaign/date range), not copied from the interactive reference, which requires a Zeffy account.

## Pricing

Zeffy is **100% free** for nonprofits - no platform, transaction, or credit-card fees, and no per-request API charges. Zeffy sustains itself through **optional donor tips** at checkout (on average roughly 2 of 3 donors leave a tip). There are no paid API tiers.

## Tags

- Fundraising
- Nonprofit
- Donations
- Payments
- Donor Management
- Free
- Webhooks

## Timestamps

- **Created:** 2026-07-05
- **Modified:** 2026-07-05

## APIs

### Zeffy Payments API

Read-only access to an organization's transactions. List all payments or look up a specific payment, filtering by currency, status, type (online, manual, or imported), contact, campaign, or date range. Each payment includes line items, refund details, buyer info, and a link to the tax receipt.

- **Human URL:** [https://support.zeffy.com/get-started-with-the-zeffy-api-yourg](https://support.zeffy.com/get-started-with-the-zeffy-api-yourg)
- **Base URL:** `https://api.zeffy.com/api/v1`

#### Properties

- [Documentation](https://www.zeffy.com/integration/api)
- [API Reference](https://support.zeffy.com/get-started-with-the-zeffy-api-yourg)
- [OpenAPI](openapi/zeffy-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)

### Zeffy Contacts API

Read-only access to an organization's donor and supporter list. Retrieve the full contact list or look up a specific person by ID or email. Each contact includes giving history, total contributions, address, and communication preferences.

- **Human URL:** [https://support.zeffy.com/get-started-with-the-zeffy-api-yourg](https://support.zeffy.com/get-started-with-the-zeffy-api-yourg)
- **Base URL:** `https://api.zeffy.com/api/v1`

#### Properties

- [Documentation](https://www.zeffy.com/integration/api)
- [API Reference](https://support.zeffy.com/get-started-with-the-zeffy-api-yourg)
- [OpenAPI](openapi/zeffy-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)

### Zeffy Campaigns API

Read-only access to an organization's donation forms, events, and other campaign types. List campaigns or look up a specific campaign to see titles, descriptions, goals, dates, occurrences, and how much has been raised.

- **Human URL:** [https://support.zeffy.com/get-started-with-the-zeffy-api-yourg](https://support.zeffy.com/get-started-with-the-zeffy-api-yourg)
- **Base URL:** `https://api.zeffy.com/api/v1`

#### Properties

- [Documentation](https://www.zeffy.com/integration/api)
- [API Reference](https://support.zeffy.com/get-started-with-the-zeffy-api-yourg)
- [OpenAPI](openapi/zeffy-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)

### Zeffy Webhooks

Outbound webhooks configured under **Settings → Integrations**. When a payment is completed, Zeffy sends an HTTP POST with the full payment details to the organization's configured URL, enabling thank-you workflows, CRM/accounting sync, and internal notifications. This is Zeffy-to-consumer HTTP notification, not an inbound API surface.

- **Human URL:** [https://support.zeffy.com/get-started-with-the-zeffy-api-yourg](https://support.zeffy.com/get-started-with-the-zeffy-api-yourg)

#### Properties

- [Documentation](https://www.zeffy.com/integration/api)
- [API Reference](https://support.zeffy.com/get-started-with-the-zeffy-api-yourg)

## Common Properties

- [LinkedIn](https://www.linkedin.com/company/zeffy)
- [Website](https://www.zeffy.com)
- [Documentation](https://www.zeffy.com/integration/api)
- [Plans](plans/zeffy-plans-pricing.yml)
- [Rate Limits](rate-limits/zeffy-rate-limits.yml)
- [Fin Ops](finops/zeffy-finops.yml)
- [Blog](https://www.zeffy.com/blog)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
