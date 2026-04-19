# SMS Compliance — Twilio Verification Notes

Generated: April 2026

---

## URLs to submit to Twilio

| Field | URL |
|---|---|
| **Proof of consent (message flow / opt-in)** | `https://caparesolve.com/sms-consent` |
| **Privacy Policy** | `https://caparesolve.com/privacy` |
| **Terms and Conditions** | `https://caparesolve.com/terms` |

---

## What the new page covers

`/sms-consent` (`sms-consent/index.html`) is the primary proof-of-consent page.

It states:

- CAPA Resolve sends SMS only for transactional/security purposes: phone number verification, one-time codes, account security alerts.
- Not marketing or promotional messages.
- Consent is given by entering a mobile number in CAPA Resolve and triggering a verification/security action.
- Message frequency varies (messages only triggered by user actions).
- Standard message and data rates may apply.
- Reply **STOP** to opt out.
- Reply **HELP** for help, or email support@caparesolve.com.
- Links to Privacy Policy and Terms of Use.

---

## What was updated

| File | Change |
|---|---|
| `sms-consent/index.html` | **New page** — full transactional SMS consent disclosure |
| `privacy/index.html` | Added phone number collection note (section 2) + new SMS section (section 11) |
| `terms/index.html` | Added SMS section (section 11) |
| `index.html` | Added "Text Messaging" card to homepage trust grid |
| `compliance/index.html` | Added Text Messaging Policy to publicly available documents list |
| `sitemap.xml` | Added `/sms-consent` entry |
| All other pages (14 total) | Added "Text Messaging" link to footer Policies column |

---

## Wording assumptions

- **Message type framed as transactional only.** If CAPA later adds promotional or marketing SMS, the SMS consent page, privacy policy, and terms must be updated before doing so.
- **Opt-in method described as implicit action-based:** user enters a number and triggers a verification/security action. This is truthful for the current OTP/verification use case. If CAPA introduces a checkbox-style explicit opt-in UI, update the "How you consent" section to match.
- **support@caparesolve.com used for SMS help/opt-out.** Confirm this inbox is monitored for opt-out requests.
- **No short code or toll-free number is hardcoded** on the SMS consent page. Twilio may ask for the originating number; you can add it to the page after your toll-free number is verified.

---

## Things to verify manually before submitting

1. **Deploy the site** so `https://caparesolve.com/sms-consent` is live and publicly accessible. Twilio reviewers will visit the URL directly.
2. **Confirm the support@caparesolve.com inbox** is active and monitored for opt-out requests sent by email (as an alternative to the STOP reply).
3. **Add the originating number** to `/sms-consent` if Twilio asks you to display the number users will receive messages from (toll-free number or short code). You can add a line like: "Messages will be sent from [+1 XXX XXX XXXX]."
4. **Verify the canonical URLs** are accessible without redirect issues: `/sms-consent`, `/privacy`, `/terms`.
5. When filling in the Twilio toll-free verification form, use exactly:
   - **Message Flow / Opt-in URL:** `https://caparesolve.com/sms-consent`
   - **Privacy Policy URL:** `https://caparesolve.com/privacy`
   - **Terms of Service URL:** `https://caparesolve.com/terms`

---

## No changes needed in the main CAPA app repo

These are public website (capa-site) changes only. No changes were made to the agentic-workspace app. When the CAPA platform's phone verification UI is built, ensure it displays a clear disclosure (e.g., "By entering your number you agree to receive a verification code via SMS. Msg & data rates may apply. Reply STOP to opt out.") consistent with this public page.
