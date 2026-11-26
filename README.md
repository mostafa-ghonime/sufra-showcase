# Sufra (سفرة): case study

Arabic-first food and nutrition companion for Android, built with Flutter and Firebase. The source code is private (client work). This page covers the product and the engineering.

## What it does
- Meal logging by search, barcode scan, voice and photo, with calorie and macro values
- Water and weight tracking, daily and weekly stats, PDF report (Arabic and English)
- Meal planning, shopping list, reminders, Ramadan mode
- Coaching section with goals and daily steps
- Light and dark themes, glass-style UI, full RTL support

## Engineering
- Flutter with a feature-first structure (`app / core / data / features / services / l10n`)
- Firebase Auth and Firestore with per-user security rules
- Server-side workers for the AI features, so no keys ship inside the app
- Test suite across features: unit, widget and responsive layout tests

## Screens
Screenshots coming soon.

## Contact
Mostafa Ghonime · mostafaghonime1@gmail.com
