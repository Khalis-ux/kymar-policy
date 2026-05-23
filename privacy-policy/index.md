---
title: Privacy Policy
---

# Privacy Policy — Kymar

_Last updated: 23 May 2026_

Kymar ("the app", "we") is designed to be **private by default**. We do not
collect, sell, or share personal information. This document explains
what data the app handles, where it lives, and the few cases where you
can opt in to send something off your device.

## Summary

| Category | Collected? | Stored where | Shared? |
|---|---|---|---|
| Practice stats (accuracy, streaks, attempts) | Yes | On-device + your private iCloud (opt-in) | No |
| Your name / display picture | Only if you sign in with Apple | Keychain on-device | No |
| Microphone audio | Only when a pitch / mic drill is active | Never persisted | No |
| Crash + diagnostic reports | Only if you turn ON "Upload diagnostics on launch" | Sent to our error tracker (Sentry) | Sentry only |
| Ads, tracking pixels, analytics | **None** | — | — |
| Contacts, photos, location, health | **Not requested** | — | — |

## Data the app handles

### 1. Practice data (local-first)

Every exercise you complete is stored locally in `UserDefaults` and used
to drive the Stats tab, achievements, and spaced-repetition queue. It
includes:

- module the round was in (Intervals / Chords / Scales / etc.)
- whether the answer was correct
- timestamp
- in some modules: which interval/chord/scale was the target and which
  you picked, so we can show per-category accuracy

This data **never leaves your device** unless you separately enable
iCloud sync from the You tab.

### 2. iCloud sync (opt-in)

When you turn ON "iCloud sync" in the You tab, your practice stats and
spaced-repetition queue are synced to your **private CloudKit container
(`iCloud.app.kymar`)**, which lives in your own iCloud account. We
cannot read it. Apple cannot read it. Other Kymar users cannot read it.
It exists so a fresh install on a second device picks up where you left
off.

Turn it OFF at any time to stop syncing; existing data on iCloud is
removed at our next sync attempt.

### 3. Sign in with Apple (opt-in)

If you tap "Connect your Apple account" in the You tab, we ask Apple
for the display name and (relay) email associated with your Apple ID.
Both are stored **only in the iOS Keychain on your device** so the
Profile section can show your name. We do not transmit either field to
any server.

Sign out at any time to remove these from the Keychain.

### 4. Microphone

The Pitch tool and a few interval / scale exercises optionally let you
sing or whistle into the microphone for real-time pitch detection. We
**never record** the audio — we read the live samples to compute a
frequency, then discard them. iOS displays the orange "microphone in
use" indicator while a drill is active.

### 5. Crash + diagnostic reports (opt-in)

By default, Kymar captures crash and hang reports via Apple's MetricKit
and keeps them **only on your device** (You → Diagnostics shows the
count). They never leave the phone.

If you turn ON "Upload diagnostics on launch", reports are sent on the
next app launch to our error tracker (Sentry, EU region —
`o4511437337853952.ingest.de.sentry.io`). Before sending we **scrub
filesystem paths** so user names and container UUIDs are replaced with
generic placeholders. The reports contain:

- stack traces
- iOS / device model
- app version
- breadcrumb trail of the last ~100 user-visible actions
  (categorised: "module", "tab", "audio", "purchase" — no PII)

These help us fix crashes faster. You can turn the toggle off at any
time, or tap "Clear reports" to delete everything locally.

### 6. In-app purchases

When you buy Kymar Pro, the transaction is handled entirely by Apple's
StoreKit. We receive only the entitlement status (Pro or not). We
never see your Apple ID, payment method, or transaction history.

## What we do NOT collect

- ❌ Tracking or advertising IDs
- ❌ Analytics frameworks (Firebase, Mixpanel, Amplitude, etc.)
- ❌ Behavioural / session recording
- ❌ Location
- ❌ Contacts, photos, calendar
- ❌ HealthKit data
- ❌ Social-media identifiers
- ❌ Any third-party SDKs that "phone home" by default

## Your rights

Since the only data that ever leaves your device is the opt-in
diagnostic report — and even that is scrubbed and contains no
personally identifying information — there is effectively nothing to
"request access to" or "be forgotten" under GDPR / CCPA. Every state
the app keeps on your device can be cleared from You → Reset
everything.

If you have specific concerns, email us at the address in our [Support
page](https://khalis-ux.github.io/kymar-policy/support) and we will
help in good faith.

## Children

Kymar is rated 4+ and contains no advertising, no third-party links,
and no user-generated content. Parents can let kids practise ear
training freely.

## Changes

If we change this policy we will:

1. Update the "Last updated" date at the top.
2. Show an in-app notice on the next launch ("Privacy policy updated
   — review").
3. Keep the diff in our public Git history.

We will not silently expand what data we collect.

## Contact

For privacy questions: open the Support page link from inside the app
(You → Help → Support) or email **hello@kymar.app**.
