# Zeffy (zeffy)

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

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
