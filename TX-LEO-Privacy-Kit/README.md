# TX LEO — App Store Connect Privacy Kit

Everything needed for the privacy/legal side of your App Store submission.

## What's in this folder

| File | Purpose |
|---|---|
| `privacy-policy.html` | Host this. Paste its URL into App Store Connect → App Privacy → Privacy Policy URL. |
| `privacy-policy.md` | Markdown source (for your repo / future edits). |
| `terms-of-use.html` | Host this. Required because you have an auto-renewing subscription. |
| `terms-of-use.md` | Markdown source. |
| `app-store-connect-privacy-answers.md` | Exact answers for the App Privacy questionnaire (spoiler: "Data Not Collected"). |

## Submission checklist

1. **Host both HTML files** — any static host works (Vercel, GitHub Pages, your existing Next.js site). Suggested paths: `/txleo/privacy` and `/txleo/terms`.
2. **App Store Connect → App Privacy** → answer **"No"** to data collection → label shows **Data Not Collected**. (See `app-store-connect-privacy-answers.md` for why this is correct.)
3. **App Store Connect → App Information** → paste the Privacy Policy URL.
4. **Terms of Use:** either paste your hosted terms URL as a link in the app description, or upload custom EULA text under App Information → License Agreement.
5. **In-app paywall (Guideline 3.1.2 — #1 rejection trap):** the subscription screen must show subscription name, duration, price, AND tappable links to both the Privacy Policy and Terms of Use. Add two `Link()` views at the bottom of your StoreKit paywall pointing at the hosted URLs.
6. If you later add any SDK that phones home (RevenueCat, TelemetryDeck, etc.), update the privacy label **before** submitting that build.

## Note

These documents are solid boilerplate for a no-data-collection indie app, but I'm not a lawyer — if you want them bulletproof, have an attorney glance over the Terms of Use.
