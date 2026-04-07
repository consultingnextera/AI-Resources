# API Design Checklist

Use this when designing or reviewing REST or GraphQL APIs before going to production. The checklist covers endpoints, authentication, versioning, error handling, rate limiting, and documentation to catch common pitfalls early.

---

**Two ways to use this:**
- **Paste the whole file into an LLM** — it will interview you and fill out the template at the bottom
- **Copy just the template** — scroll to the bottom and fill it in yourself

---

## LLM Instructions

Act as an API architect. Review the user's API design against best practices for REST/GraphQL endpoints, error handling, authentication, and operations.

**SECTION 1 — Endpoint Design**

- What are the main resource types in your API? (users, products, orders, etc.)
- For each resource, what CRUD operations do you need? (create, read, update, delete)
- Are your endpoints RESTful? Do they use nouns (not verbs) in the URL? (/products, not /getProducts)
- Do you have nested resources that make sense semantically? (e.g., /users/:id/orders)

**SECTION 2 — Authentication & Authorization**

- What authentication method will you use? (API keys, OAuth 2.0, JWT, mTLS, etc.)
- How will you enforce authorization? (user role, resource ownership, scope-based)
- Is sensitive data protected from unauthorized access? Can one user see another user's data?
- How do you handle token expiration and refresh?

**SECTION 3 — Versioning & Backwards Compatibility**

- Are you planning to version your API? (URL path, header, or parameter)
- How will you communicate breaking changes to clients?
- Can you add new fields without breaking existing clients?
- What's your deprecation timeline for old API versions?

**SECTION 4 — Error Handling & Status Codes**

- Do you have a standardized error response format?
- Are you using appropriate HTTP status codes? (200, 201, 204, 400, 401, 403, 404, 429, 500, etc.)
- Does each error response include an error code, message, and actionable details?
- How do you handle validation errors? (missing fields, invalid types, etc.)

**SECTION 5 — Rate Limiting & Quotas**

- Do you have rate limits? (requests per second, per minute, per day)
- How do you communicate rate limits to clients? (response headers)
- What happens when a client exceeds the limit? (queue, reject, prioritize)
- Do different clients have different quota tiers?

**SECTION 6 — Documentation & Discoverability**

- Is your API documented? (OpenAPI/Swagger, GraphQL schema, etc.)
- Do you have example requests and responses for each endpoint?
- Is there a changelog for API updates?
- Do you provide SDKs or client libraries?

Review each section and flag gaps or risks.

---

## Template

Copy the block below — paste it into a new file and fill it in.

````markdown
# API Design Review: [API NAME]

**Date:** [DATE] | **Type:** [REST / GRAPHQL] | **Status:** [READY / NEEDS WORK]

## Endpoint Coverage
| Resource | Create | Read | Update | Delete | Notes |
|----------|--------|------|--------|--------|-------|
| [NAME] | [YES/NO] | [YES/NO] | [YES/NO] | [YES/NO] | [DESCRIPTION] |
| [NAME] | [YES/NO] | [YES/NO] | [YES/NO] | [YES/NO] | [DESCRIPTION] |

## Authentication & Authorization
- **Method:** [API_KEY / OAUTH / JWT / OTHER]
- **Authorization model:** [ROLE_BASED / RESOURCE_OWNER / SCOPE_BASED]
- **Token expiry:** [TIME]
- **Status:** [IMPLEMENTED / PLANNED]

## Versioning Strategy
- **Versioning approach:** [URL_PATH / HEADER / PARAMETER / NOT_PLANNED]
- **Current version:** [VERSION]
- **Deprecation policy:** [DESCRIPTION or "NOT DEFINED"]

## Error Handling
- **Status codes:** [201 CREATED / 400 BAD_REQUEST / 401 UNAUTHORIZED / 429 RATE_LIMITED / ...]
- **Error response format:** [STANDARD / CUSTOM]
- **Example error:** [JSON STRUCTURE or DESCRIPTION]

## Rate Limiting
- **Enabled:** [YES / NO]
- **Limit:** [REQUESTS / TIME]
- **Tier model:** [SINGLE / MULTIPLE TIERS]
- **Communication method:** [HEADERS / DOCUMENTATION]

## Documentation
- **Format:** [OPENAPI / GRAPHQL_SCHEMA / MARKDOWN / MISSING]
- **Examples:** [YES / NO]
- **Changelog:** [YES / NO]
- **SDKs:** [AVAILABLE / PLANNED / NOT APPLICABLE]

## Gaps & Action Items
- [ ] [ITEM]
- [ ] [ITEM]
- [ ] [ITEM]
````

---

> Adapted from [awesome-chatgpt-prompts](https://github.com/f/awesome-chatgpt-prompts) (CC0) | **consulting.nextera@gmail.com** | [nexteraconsult.com/ai](https://nexteraconsult.com/ai)
