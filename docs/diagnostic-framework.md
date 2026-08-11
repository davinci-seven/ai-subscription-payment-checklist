# General Payment Diagnostic Framework

Use this when an AI/SaaS subscription payment fails and the platform-specific checklist does not immediately explain why.

## 1. Identify the transaction type

First determine what is actually failing:

- first subscription payment
- renewal
- unpaid invoice
- workspace/team billing
- API billing
- app-store billing
- web checkout

Do not mix these together. The same product can have different billing systems depending on how the subscription was created.

## 2. Capture evidence before changing anything

Record:

- exact error message
- UTC timestamp
- first payment or renewal
- web/app-store/API/workspace route
- invoice or transaction ID if shown
- whether authentication appeared
- whether the bank/card issuer saw an authorization attempt

Screenshots are useful, but redact card numbers, addresses, IDs and account secrets before sharing them.

## 3. Split on issuer authorization

### Issuer saw an authorization attempt

The merchant reached the card network/issuer far enough for an authorization to appear.

Investigate:

- available balance
- tax or temporary authorization buffer
- card/daily/foreign-currency limits
- online payments
- international payments
- recurring payments
- card status and expiry
- issuer security controls
- 3D Secure or other authentication
- billing name/address/postal-code consistency

If the issuer provides a decline reason, preserve it.

### Issuer saw no authorization attempt

Do not label this an issuer decline without evidence.

The failure may be happening earlier. Possible layers include:

- billing route mismatch
- unpaid invoice or billing-profile state
- workspace/account ownership state
- account eligibility
- region/address/card consistency
- card type/BIN eligibility
- merchant-side risk checks
- checkout/session failure

This distinction is useful because repeatedly calling the bank or repeatedly replacing the card may not address the actual failure.

## 4. Change one variable at a time

Avoid changing all of these together:

- card
- billing address
- account
- region
- device/browser
- network

If five variables change and the next attempt works, you have learned almost nothing.

A cleaner sequence is:

1. Preserve the failed case.
2. Correct any obvious billing/invoice problem.
3. Retry only when there is a reason to believe something changed.
4. If testing another payment method, keep the rest of the setup stable.

## 5. Treat renewal as a separate test

A successful first charge is only evidence that the first charge worked.

For recurring subscriptions, record:

- first-charge date
- expected renewal date
- amount including tax
- balance before renewal
- whether recurring payments remain enabled
- result of the first renewal

Do not describe a payment method as "stable for renewals" based only on the signup payment.

## 6. Virtual cards: what they can and cannot prove

A virtual card can be useful for:

- separating AI/SaaS spending from a main bank card
- controlling balance and exposure
- supporting online/international recurring payments when the user's normal card does not
- testing a merchant with a small dedicated balance

A virtual card does not prove or guarantee:

- account eligibility
- region support
- merchant acceptance of that BIN/card type
- renewal success
- bypass of merchant/account risk decisions

A card that works at Merchant A may fail at Merchant B.

## 7. Escalate with useful evidence

When contacting platform support, provide:

- product and billing route
- exact error text
- UTC timestamp
- first payment/renewal/invoice context
- whether the issuer saw an authorization attempt
- invoice/transaction ID if available
- steps already tried

Do not send full card details, CVV, identity documents or account passwords unless an official, authenticated support process explicitly requires the relevant information.

## 8. Stop conditions

Stop retrying and investigate instead when:

- the exact same error repeats
- the issuer sees no authorization attempt after multiple identical submissions
- an unpaid invoice is still unresolved
- account/region eligibility is unclear
- authentication cannot complete
- the platform has explicitly rejected or restricted the payment/account

Repeated retries are not a diagnostic method.

## Safety and compliance

This project is for normal subscription/payment troubleshooting. It does not recommend fake billing details, false residency claims, account farming, chargeback abuse, cash-out use, or attempts to bypass platform reviews or restrictions.
