# Cursor Pro Payment Checklist

Use this before trying another card for Cursor Pro.

## Check billing state first

- Check whether there is an unpaid invoice.
- Confirm whether billing is individual or workspace/team billing.
- Confirm which workspace/account owns the subscription.
- Pay outstanding invoices before starting a new checkout.

## Capture the failure

- Save the exact error text and UTC time.
- Note whether this is a first payment, renewal or payment of an existing invoice.
- Check whether the bank/card dashboard saw an authorization attempt.
- Stop repeated submissions while diagnosing the failure.

## If the issuer saw the attempt

Check:

- card supports online recurring payments
- international payment settings are enabled if required
- balance and limits are sufficient
- billing details are accurate
- bank/card dashboard shows no security block
- authentication can complete

## If the issuer saw nothing

Do not assume the bank declined the card.

Possible layers include an unpaid invoice, workspace/account billing state, merchant risk checks, card eligibility, billing-detail mismatch or a checkout/session failure before issuer authorization.

- Re-check invoice and workspace billing state.
- Change one variable at a time.
- Keep the exact error and timestamp.
- Use official support if the same failure persists without an issuer-side authorization attempt.

## If testing a virtual card

- Use a small balance first.
- Do not assume success on another AI merchant predicts Cursor acceptance.
- Track the renewal date and invoice behavior.
- Confirm at least one renewal before relying on the payment method long term.

Related guide: https://aipaymentfix.com/guides/cursor-payment-not-working/

No card can guarantee approval. Do not use fake billing details, false residency information or repeated card rotation to bypass a platform decision.
