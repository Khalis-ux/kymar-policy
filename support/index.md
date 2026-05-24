---
title: Support
---

# Kymar — Support

Welcome. If something isn't working or you have an idea, this page is
where to start.

## Get in touch

**[Open an issue on GitHub](https://github.com/Khalis-ux/kymar-site/issues/new)** — every report is read and triaged. Bug reports and feature requests both welcome there. A GitHub account is free; sign-up takes ~30 seconds.

_We're setting up a regular email (`hello@kymar.app`) once the domain is registered; in the meantime GitHub Issues is the fastest channel._

For bugs, please include:

- iOS version (Settings → General → About → Software Version)
- iPhone / iPad model
- App version (You → bottom of the page)
- What you were doing when it happened
- Optionally: tap "Share diagnostic report" in You → Diagnostics and
  attach the file. It's path-scrubbed and contains no personal data —
  it just lists the stack trace and recent action breadcrumbs.

## Quick fixes

**The audio cuts out mid-exercise**
iOS gives priority to phone calls / Siri / alarms over our audio. When
they end, tap Play again. If audio stays silent after re-launching the
app, check that your phone isn't in silent mode and that Bluetooth
isn't pointing audio at a disconnected device.

**My streak reset and I practised yesterday**
A "day" rolls over at midnight local time. If you practised after
midnight one day and not at all the next calendar day, the streak
breaks. We don't have a grace period in v1.

**I bought Pro on another device — how do I unlock here?**
You tab → "Restore purchases". StoreKit will re-check your Apple ID's
entitlements and unlock Pro on this device. Make sure you're signed
into the same Apple ID.

**My stats don't appear on my other device**
Stats only sync if you turn ON "iCloud sync" in the You tab on both
devices, and you're signed into the same iCloud account. The sync
uses your private CloudKit container — we never see the data.

**The MIDI keyboard doesn't trigger answers**
MIDI input is a Pro feature. After unlocking Pro, the You tab shows a
"MIDI input · X connected" line when the keyboard is detected. If it
shows 0, try unplugging + reconnecting the USB cable, or re-pairing
Bluetooth.

**Live Activity doesn't show in Dynamic Island**
Dynamic Island is hardware-only on iPhone 14 Pro and later. On older
iPhones you'll still see the live activity on the lock screen. On
iPads there is no Live Activity at all.

**A drill keeps generating the same patterns**
Check You → Settings → randomness is on by default. If you're in
Rhythm trainer specifically, the generator avoids consecutive
repetitions; if you see one regardless, please share the screenshot
with the diagnostic report.

## Common requests we already plan to ship

- More songs in Name That Song
- Convolution reverb in the Timbre module
- Daily Challenge mode rotating across all modules
- Triplet rest support in Rhythm
- Apple Watch companion for the metronome

If you want one of these prioritised, tell us — we triage by request
volume.

## Feature requests

We read every issue. Be specific: what skill are you trying to train,
what's missing from the current modules, what would the perfect
exercise look like. The more concrete, the more likely it ships.

## Refunds

Refunds are handled by Apple, not by us. Open the App Store on your
phone → tap your profile in the top-right → Purchase History → tap the
purchase → "Report a Problem". You typically have 90 days. We have no
way to issue a refund directly.

## Privacy

[Privacy policy](/kymar-policy/privacy-policy/)
