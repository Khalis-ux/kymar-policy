---
title: Privacy Policy
---

# Privacy Policy — Kymar

_Last updated: 23 May 2026_

This policy mirrors the App Store **Privacy Labels** you see on
Kymar's listing — same data, same wording, no surprises.

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
| Rewarded video ads (Google AdMob) | Yes — IDFA when ATT allowed, anonymous device signals otherwise | Sent to Google AdMob | Google AdMob (ad attribution) |
| Anonymous usage stats | Only if you turn ON "Share anonymous usage stats" | Sent to our Cloudflare Worker | We host it (no third party) |
| Other tracking pixels, analytics SDKs | **None** | — | — |
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

### 7. Anonymous usage stats (opt-in)

By default, Kymar collects engagement events **locally on your device**
in a ring buffer (last 1,000 events): which module you opened, when
you completed a quiz, when you tapped Pro CTAs. This drives the
Insights panel in the You tab — none of it leaves your phone unless
you opt in below.

If you turn ON **"Share anonymous usage stats"** in the You tab, the
ring buffer is periodically POSTed to our Cloudflare Worker at
`kymar-analytics.vittoriocwork.workers.dev`. The payload contains:

- A random `installId` (UUID generated on first launch, never tied to
  your Apple ID, name, email, IDFA, or any persistent device identifier)
- App version, iOS version, locale
- Event names from a fixed enum (`module_open`, `quiz_complete`,
  `paywall_shown`, `purchase_attempt`, etc.) with an optional module
  ID and integer value

It does **not** contain:

- Your name, email, Apple ID, profile picture
- Audio recordings, microphone samples, or anything you typed
- IDFA or any persistent identifier other than the install-scoped UUID
- Practice content (answers, intervals, chord names, your composer
  progressions)

We use this to answer "which modules are people sticking with?" and
"where does the funnel drop off?" — the kind of questions that drive
product roadmap, not advertising. The data is **not** shared with any
third party (the Worker is ours), is **not** combined with data from
other apps, and is **not** used for tracking in Apple's definition
(no cross-app linking, no data broker, no ad targeting).

Turn the toggle OFF at any time. The next "Reset everything" in the
You tab also rotates the `installId` so any further uploads start
under a fresh anonymous identity with no continuity to the old one.

### 8. Rewarded video ads (Google AdMob)

Free users can choose to watch a short rewarded video to temporarily
unlock a Pro feature (one sampler instrument for 30 minutes, or the
detailed breakdown of a single quiz session). Ads are loaded and shown
by **Google Mobile Ads SDK**. Pro users see no ads.

When a rewarded video loads, Google receives:

- **Device IDFA (Identifier for Advertisers)** — only if you grant
  permission via Apple's App Tracking Transparency prompt. If you tap
  "Ask App Not to Track" (or have tracking globally off in
  Settings → Privacy → Tracking), the IDFA is replaced with all-zeros
  and Google falls back to **SKAdNetwork** for anonymous attribution.
- **Ad interaction data** — ad request, impression, completion, and
  reward-earned events tagged with the same IDFA / SKAdNetwork token.
- **Device model, OS version, screen size, language, coarse location
  (city-level, derived from IP)** — standard ad-serving context.
- **App version + bundle ID** — `app.kymar` so Google can verify the
  request comes from Kymar.

**This data IS linked to your device identity** (via IDFA when ATT is
granted) **and IS used for tracking** in Apple's definition: Google
combines Kymar's ad signals with data from thousands of other apps in
the AdMob network to serve more relevant ads and measure attribution.
This is the standard ad-network business model. Apple's privacy label
on Kymar's listing reflects this explicitly under "Data Used to Track
You" → Identifiers, Usage Data.

Google's privacy policy:
<https://policies.google.com/privacy>.

You can opt out of personalised ads at any time in
**Settings → Privacy & Security → Apple Advertising → Personalised
Ads** (system-wide) or by revoking Kymar's tracking permission in
**Settings → Privacy → Tracking → Kymar**. Rewarded video will still
work — only the ad targeting becomes anonymous (SKAdNetwork-only
attribution, no IDFA).

The only sure way to stop ad data collection entirely is to upgrade
to **Pro** (You tab → Upgrade), which removes all ads.

## What we do NOT collect

- ❌ Third-party analytics frameworks (Firebase, Mixpanel, Amplitude, etc.)
- ❌ Behavioural / session recording (no replay tools)
- ❌ Precise location (GPS / Wi-Fi triangulation)
- ❌ Contacts, photos, calendar
- ❌ HealthKit data
- ❌ Social-media identifiers
- ❌ Any third-party SDKs other than Google Mobile Ads (rewarded video only) and Sentry (opt-in crash reporting only); the opt-in usage stats go to our own Cloudflare Worker, not a third party

## App Store Privacy Labels (alignment with this policy)

For transparency, these are the App Store labels you'll see on Kymar's
listing and exactly which features they correspond to in this policy:

### Data Used to Track You

- **Identifiers** (Device ID / IDFA) → AdMob rewarded video — section 8
- **Usage Data** (Advertising Data) → AdMob impression / completion events — section 8

### Data Linked to You

Same two categories as above. We declare them "linked" because IDFA is
linked to the device by design.

### Data Not Linked to You

- **Diagnostics** (Crash + Performance + Other Diagnostic Data) →
  opt-in Sentry crash reports — section 5
- **Usage Data** (Product Interaction) → opt-in Cloudflare Worker
  analytics with anonymous installId — section 7

## Your rights

Under GDPR / CCPA you can request: a copy of the data we have about
you, deletion of that data, or restriction of processing. For Kymar
specifically:

- **Sentry crash reports** — turn off the upload toggle in You →
  Diagnostics. Tap "Clear reports" to wipe everything locally.
- **Anonymous usage stats** — turn off the toggle in You → Privacy.
  Tap "Reset everything" in You → Data to rotate the `installId` so
  any further uploads start fresh with no continuity to the old data.
- **AdMob ad data** — revoke tracking in iOS Settings → Privacy →
  Tracking → Kymar to switch to anonymous SKAdNetwork-only, or
  upgrade to Pro to remove ads entirely.
- **Practice data + Apple sign-in info** — never leaves your device
  (unless you opt in to iCloud sync, which uses your own private
  CloudKit container). "Reset everything" in the You tab clears it.

If you have specific concerns, email us at the address in our [Support
page](https://khalis-ux.github.io/kymar-policy/support) and we will
help in good faith.

## Children

Kymar is rated 4+. It contains **rewarded video ads** served by
Google AdMob that the user must explicitly choose to watch to
temporarily unlock a Pro feature — never auto-playing, never
interstitial, never banner. Pro removes all ads.

We do not knowingly request tracking permission from users under 13,
and Apple's App Tracking Transparency framework already gates the
prompt at the OS level. Kymar contains no user-generated content,
no third-party social links, no in-app browser, and no chat.

If your child uses Kymar and you'd prefer they never see rewarded
ads, configure **Screen Time → Content & Privacy Restrictions →
Allow Changes → Advertising → Don't Allow Changes** with tracking
denied — Kymar's rewarded prompt will still appear but the ad serve
will fall back to anonymous attribution.

## Changes

If we change this policy we will:

1. Update the "Last updated" date at the top.
2. Show an in-app notice on the next launch ("Privacy policy updated
   — review").
3. Keep the diff in our public Git history.

We will not silently expand what data we collect.

## Contact

For privacy questions: open the Support page link from inside the app
(You → Help & support → Help & guide) or
[open a GitHub issue](https://github.com/Khalis-ux/kymar-ios/issues/new).
A direct email (`hello@kymar.app`) will replace the GitHub channel once
the domain is registered.
