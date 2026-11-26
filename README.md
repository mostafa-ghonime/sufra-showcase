# Sufra (سفرة): case study

Arabic-first food and nutrition companion for Android, built with Flutter and Firebase. The source code is private (client work). This page covers the product and the engineering.

## What it does
- Meal logging by search, barcode scan, voice and photo, with calorie and macro values
- Water and weight tracking, daily and weekly stats, PDF report (Arabic and English)
- Meal planning, shopping list, reminders, Ramadan mode
- AI coach with goals and daily steps, chatting in Egyptian Arabic
- Light and dark themes, glass-style UI, full RTL support

## Architecture
- Flutter app with a feature-first structure (`app / core / data / features / services / l10n`)
- State management with Cubit (BLoC pattern); repository layer over REST and the Firebase SDKs
- Firebase Auth (email/password and Google), Cloud Firestore with per-user security rules, Firebase Cloud Messaging
- Two serverless Cloudflare Workers as the AI gateway, one for food-photo analysis and one for the coach. Keys stay server-side; the app authenticates with its Firebase ID token
- Offline-first: local caches and a queued ledger, so logging works on a bad network and syncs afterwards
- Auth-aware routing: a signed-out session lands on login; sign-out unlinks the push token and clears the device Google account

## AI
- Food-photo analysis: a vision model on Cloudflare Workers AI behind the worker. The user consents per photo, and results are mapped to structured food data for calorie and macro values
- AI coach: an open LLM (Gemma) on a separate worker, answering in Egyptian Arabic with access to the user's app data (meals, water, weight, goals) for personal guidance
- Model evaluation: benchmarked several open models (Llama, Mistral, Gemma) for Arabic dialect quality and food accuracy before choosing; turned down a free hosted tier whose terms allowed content review, on privacy grounds
- Cost ceiling by design: free-tier quotas that stop requests instead of billing

## Security and privacy
- HTTPS-only networking; cleartext traffic and cloud auto-backup disabled on Android
- No passwords, tokens or credentials stored by the app; nothing sensitive in logs
- Timeouts on all auth calls, double-tap and duplicate-request guards, mapped rate-limit and network error messages
- Per-user Firestore security rules; per-photo consent before any image leaves the device

## Quality
- Unit, widget and responsive layout tests; golden renders verified in Arabic dark and English light
- OTP-style verification-code input with paste support and Arabic-Indic digit handling
- Full RTL Arabic/English localization; light and dark glass design system; animations built by hand, no animation packages

## Screens
Screenshots coming soon.

## Contact
Mostafa Ghonime · mostafaghonime1@gmail.com
