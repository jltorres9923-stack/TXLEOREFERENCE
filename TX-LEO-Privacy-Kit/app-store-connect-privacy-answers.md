# App Store Connect — App Privacy Questionnaire Answers

**App:** TX LEO — Texas Law Enforcement Reference
**Architecture:** Fully offline, no backend, no third-party SDKs, StoreKit 2 only

Use these answers in **App Store Connect → Your App → App Privacy → Get Started**.

---

## The Short Answer

> **"Do you or your third-party partners collect data from this app?"**
>
> # → Answer: **NO** ("Data Not Collected")

That's it. One click, done. Your privacy nutrition label will display as **"Data Not Collected"** — the best possible label an app can have.

---

## Why "No" Is the Correct Answer

Apple defines "collect" as transmitting data **off the device** in a way that **you (the developer) or your partners can access**. Walk through each feature of TX LEO:

| Feature | Off-device? | Accessible to you? | Counts as "collected"? |
|---|---|---|---|
| Favorites (UserDefaults / local files) | No — stays on device | No | **No** |
| Bundled reference content (penal codes, etc.) | No — ships with the app | N/A | **No** |
| StoreKit 2 subscription/entitlement | Handled by Apple | You never see payment data | **No** |
| Crash reports via Xcode Organizer | Apple collects, user opt-in | Aggregated by Apple | **No** * |
| App Analytics in App Store Connect | Apple collects, user opt-in | Aggregated by Apple | **No** * |

\* Apple's own guidance: data collected by Apple through the user's opt-in device analytics setting (and surfaced to you in App Store Connect / Xcode Organizer) is disclosed under **Apple's** privacy policy, not yours. You are not required to declare it, and it does not need to appear on your label.

Because you have **no networking code, no backend, and no third-party SDKs**, there is nothing that transmits data to anywhere you can access. "Data Not Collected" is accurate and defensible.

---

## Other Fields You'll Fill In Nearby

### Privacy Policy URL (App Information → App Privacy section)
Required for every app. Host `privacy-policy.html` from this kit and paste the URL, e.g.:
`https://yourdomain.com/txleo/privacy`

### Terms of Use (EULA) — REQUIRED for auto-renewing subscriptions
Apple rejects subscription apps that don't provide this. Two options:

1. **Easiest:** Use Apple's Standard EULA. In your **App Description** or promotional text, you don't need to do anything — but you MUST link Terms of Use and Privacy Policy **inside the app's paywall screen** (see below).
2. **Custom (recommended, included in this kit):** Host `terms-of-use.html` and paste its URL into **App Store Connect → App Information → License Agreement** (or add the link in your app description).

### In-App Paywall Requirements (App Review Guideline 3.1.2)
Your paywall/subscription screen **must display**:
- Subscription title and length (e.g., "TX LEO Pro — Monthly")
- Price and price per unit
- A functional link to your **Privacy Policy**
- A functional link to your **Terms of Use (EULA)**

This is the #1 rejection reason for subscription apps — put both links directly on the paywall view, not buried in Settings.

---

## If You Ever Add These Later, Your Answers Change

| If you add... | Label impact |
|---|---|
| Any third-party analytics (Firebase, Mixpanel, Amplitude, TelemetryDeck) | Must declare Usage Data / Identifiers |
| RevenueCat | Must declare Purchase History (linked via app user ID varies by config) |
| A backend / accounts / sync | Must declare whatever you store server-side |
| Crash SDK (Sentry, Crashlytics) | Must declare Diagnostics |
| AdMob or any ads | Must declare Identifiers + tracking; ATT prompt required |

Update the label **before** shipping the build that adds the SDK.
