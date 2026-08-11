# ChatGPT Plus Payment Checklist

Use this before trying another card for ChatGPT Plus.

## Identify the billing route

- If subscribed through ChatGPT web checkout, manage billing through the web account.
- If subscribed through Apple, manage the payment method through Apple.
- If subscribed through Google Play, manage the payment method through Google Play.
- Do not troubleshoot an app-store subscription as if it were a web-card checkout.

## Capture the failure

- Save the exact error text and UTC time.
- Note whether this is the first subscription attempt or a renewal.
- Check whether the bank/card dashboard saw an authorization attempt.
- Stop repeated retries while diagnosing the failure.

## If the issuer saw an authorization attempt

Check:

- card is active
- balance covers subscription, tax and any authorization buffer
- international online payments are enabled
- recurring payments are enabled
- daily/foreign-currency limits are sufficient
- bank app shows no security block
- billing name/address/postal code are accurate
- CVV and expiry are correct
- 3D Secure or other authentication can complete

## If the issuer saw nothing

Do not automatically conclude that the bank declined the card.

Possible layers include the checkout/billing route, account or billing-profile state, card eligibility, region/address consistency, merchant risk checks or a session/checkout failure before issuer authorization.

- Re-check the billing route.
- Keep account and billing details accurate and consistent.
- Change one variable at a time.
- Use official support if the same error persists with no issuer-side authorization attempt.

## If testing a virtual card

- Start with a small balance.
- Do not assume a card that works for another AI merchant will work here.
- Avoid repeated failed retries or rapid card rotation.
- Track the renewal date.
- Confirm at least one renewal before relying on the card long term.

Related guide: https://aipaymentfix.com/guides/chatgpt-card-declined/

No card can guarantee approval. Do not use false billing details, false residency information or VPNs to misrepresent location or bypass a platform review.
