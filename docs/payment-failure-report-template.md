# Payment Failure Report Template

Use this template when comparing cases, opening a GitHub issue or asking for help publicly.

Redact sensitive information before posting.

```text
Product:
Billing route: web / Apple / Google Play / API / workspace-team / other
Country/region of account:
Card-issuing country:
Payment type: first payment / renewal / unpaid invoice / other
Approximate amount and currency:
Exact error message:
UTC timestamp of attempt:
Did 3D Secure/authentication appear? yes / no / unknown
Did the bank/card issuer see an authorization attempt? yes / no / unknown
If yes, what status/reason did the issuer show?
Was this payment method previously successful with this same merchant? yes / no
If yes, was it only the first charge or has a renewal also succeeded?
What changed since the last successful payment?
What have you already tried?
```

## Do not include

- full card number
- CVV
- full billing address
- passport/identity-document images
- API keys
- passwords
- session cookies
- recovery codes
- unredacted screenshots containing sensitive account data

## Why this format helps

The two most useful facts are usually:

1. what billing route is actually being used; and
2. whether the issuer saw an authorization attempt.

Those two facts separate many superficially similar "card declined" reports into different troubleshooting paths.
