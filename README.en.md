# AI Subscription Payment Checklist

[简体中文](README.md) | **English**

A practical, public troubleshooting library for failed AI subscription payments.

The goal is simple: diagnose the failure before blindly trying another card.

The primary audience is Chinese-speaking users dealing with cross-border AI/SaaS billing friction, while the troubleshooting framework is useful anywhere payment routes, issuer restrictions, regional availability, account state, or recurring billing can cause failures.

Covers ChatGPT Plus, Claude Pro, Cursor Pro, OpenAI API, Grok and similar AI/SaaS billing problems.

## Start here

When a payment fails, do these in order:

1. **Identify the billing route** — web checkout, Apple App Store, Google Play, workspace/team billing or API billing.
2. **Capture the exact failure** — save the error text, UTC time, invoice/transaction ID if shown, and whether this is a first payment or renewal.
3. **Check whether the issuer saw an authorization attempt.**
4. **If the issuer saw it** — investigate balance, limits, recurring/international payment settings, security blocks and authentication.
5. **If the issuer saw nothing** — do not assume the bank declined it. The rejection may be happening earlier in the merchant/account/billing path.
6. **Change one variable at a time** — repeated card rotation creates noise and makes the real cause harder to identify.

## The most useful diagnostic split

### Bank/card issuer saw an authorization attempt

Start with the issuer side:

- available balance and tax/authorization buffer
- online/international/recurring payment settings
- daily or foreign-currency limits
- security blocks
- 3D Secure or other authentication
- billing details and card status

### Bank/card issuer saw no authorization attempt

Treat this as a different class of failure.

Possible layers include:

- wrong billing route
- unpaid invoice or billing-profile state
- account or merchant risk checks
- region/address/card eligibility mismatch
- card type or BIN not accepted by the merchant
- checkout/session problems before authorization

This is a diagnostic hypothesis, not proof of the root cause. Save the evidence and use the platform's official support path if the same failure persists.

## Platform checklists

| Product | Checklist | Useful first question |
|---|---|---|
| ChatGPT Plus | [checklists/chatgpt-plus.md](checklists/chatgpt-plus.md) | Web, Apple or Google Play billing? |
| Claude Pro | [checklists/claude-pro.md](checklists/claude-pro.md) | Is the account/region eligible and is recurring international payment enabled? |
| Cursor Pro | [checklists/cursor-pro.md](checklists/cursor-pro.md) | Is there an unpaid invoice or workspace billing state? |
| OpenAI API | [checklists/openai-api.md](checklists/openai-api.md) | Is this API billing rather than ChatGPT billing, and did the issuer see an authorization? |
| Grok | [checklists/grok.md](checklists/grok.md) | Web or app-store billing, and did the issuer see an authorization? |

## Common failure patterns

| Pattern | What it can mean | First action |
|---|---|---|
| Card declined and issuer saw the attempt | Issuer block, insufficient balance/limit, authentication or card restriction | Check issuer app/support and exact authorization result |
| Card declined but issuer saw nothing | Failure may be before issuer authorization | Check billing route, account/billing state, region/card eligibility and platform support |
| Renewal failed after a successful first payment | Balance, expiry, recurring restriction or changed merchant risk decision | Check renewal date, balance and recurring payment settings |
| API billing rejected | API-specific billing/account state, spending limit, card eligibility or risk checks | Inspect the API billing page and capture the exact failure |
| Cursor unpaid invoice | Existing invoice or workspace billing state | Resolve the outstanding invoice before a new checkout |
| Region-related failure | Unsupported route, issuer restriction or account/billing mismatch | Confirm official availability and keep account/card details accurate |

## Rules that save time

- A card working for one AI merchant does **not** prove it will work for another.
- A successful first charge does **not** prove renewal will work next month.
- Do not repeatedly submit the same failed payment while diagnosing it.
- Do not change card, account, region, address and network all at once. You lose the evidence trail.
- Keep screenshots/error text, UTC timestamps and transaction/invoice IDs when available.
- No card can guarantee approval.

## When a virtual card may help

A virtual card can be useful when:

- your bank blocks international AI subscriptions
- you want a separate low-balance card for recurring AI tools
- you need tighter spending controls
- your main card does not support online recurring payments

It may **not** solve the problem when:

- the account or billing profile is the issue
- the billing route is wrong
- the platform does not support the account/region/payment route
- the card BIN/type is rejected
- authentication or address verification fails
- an unpaid invoice is blocking checkout

Use a virtual card as a controlled payment method, not a guaranteed workaround.

## Testing a new payment method

For normal subscription use:

1. Start with a small balance.
2. Test one merchant first.
3. Record the first successful charge.
4. Track the renewal date.
5. Confirm renewal behavior before relying on the card long term.
6. Understand fees, refund/withdrawal path and support before keeping a larger balance.

## Share a failure without leaking sensitive data

Use [docs/payment-failure-report-template.md](docs/payment-failure-report-template.md) when comparing cases or opening an issue.

Never post:

- full card number
- CVV
- full billing address
- identity documents
- API keys
- account passwords or recovery codes

## Project links

- Troubleshooting guides: https://aipaymentfix.com/
- Chinese virtual-card notes/resources: https://info.vcardvirtual.cc/
- X / build notes: https://x.com/davinci_seven

This repository is a public reference project associated with **@davinci_seven / 达芬七**. It is meant to turn recurring payment-support questions into reusable, searchable checklists instead of one-off social posts.

## VCard / partner disclosure

VCard is one virtual-card option I test and may promote for normal AI subscription use cases. I may earn compensation from some partner signups.

That relationship does not change the diagnostic order in this repo: **diagnose first, compare options second, test small third.** Payment success is never guaranteed.

## What this repo does not recommend

- fake billing details
- false residency claims
- VPN use to misrepresent location or bypass a platform review
- account farming
- repeated card rotation to evade a merchant decision
- chargeback abuse
- cash-out activity
- large deposits before testing

If a service officially does not support your location, this repository is for diagnosing that limitation and finding compliant alternatives — not for bypassing the platform's regional restrictions.

## More detail

- [General diagnostic framework](docs/diagnostic-framework.md)
- [Payment failure report template](docs/payment-failure-report-template.md)

## License

MIT
