---
title: Privacy Policy — Catchyu
---

# Privacy Policy — Catchyu

**Last updated:** April 28, 2026

**Developer:** KaKooApps
**App:** Catchyu - Auto Responder
**Package:** com.kakoo.apps.catchyu

---

## Overview

Catchyu is an auto-reply app that automatically responds to incoming messages on WhatsApp, Telegram, Signal, Messenger, Instagram, Viber, LINE, and other messaging apps. It uses Android's Notification Listener Service to read notifications and send replies on your behalf.

Catchyu is a **local-first** app. All your data stays on your device by default. Network features (AI replies, webhooks, analytics) only activate when **you** turn them on.

## Data Collection

**Catchyu does not collect, transmit, or share personal data by default.**

Specifically:

- **No user accounts** are required or supported.
- **No advertising SDKs** are included.
- **No data is sent to our servers** — we do not operate any server that receives your message content or contact data.
- **No contacts, SMS, call logs, location, camera, or microphone** data is accessed.
- **No Android ID, Advertising ID, IMEI, or Google account name** is collected.

## Data Accessed via Notifications

Catchyu uses Android's `NotificationListenerService` to read incoming notifications from messaging apps you select. For each notification, the app extracts:

| Data | Purpose |
|------|---------|
| Sender name | To display in leads and match rules |
| Message text | To match keywords and generate replies |
| Contact identifier (phone number, if exposed) | To track leads and prevent duplicate replies |
| Source app package name | To apply app-specific rules |
| Timestamp | To log message history |

This data is stored **locally on your device only** and is never transmitted unless you enable optional network features (see below).

## Data Stored on Device

| Data | Purpose | Storage |
|------|---------|---------|
| Auto-reply rules and keywords | Core auto-reply functionality | Room database (app-private) |
| Leads and message history | Lead management and chat timeline | Room database (app-private) |
| Reply templates and notes | Reusable reply content | Room database (app-private) |
| Blocked-contact list | Prevent replies to specific contacts | Room database (app-private) |
| App preferences (theme, language, toggles) | Remember your settings | Android DataStore (app-private) |
| AI API key (if provided) | Send AI-generated replies | Android DataStore (app-private) |

All locally stored data is deleted when you uninstall the app or clear app data. Android Auto Backup and device transfer are **disabled** — your data is not included in Google Drive backups.

## Permissions

| Permission | Why it's needed |
|------------|----------------|
| **Notification Listener** (`BIND_NOTIFICATION_LISTENER_SERVICE`) | To read notifications and send auto-replies — the app's core function |
| **Internet** (`INTERNET`) | Used only when you enable AI replies, webhooks, or the optional Firebase build |
| **Notifications** (`POST_NOTIFICATIONS`) | To show in-app notifications (e.g. "New lead captured") |
| **Billing** (`com.android.vending.BILLING`) | To process Google Play in-app purchases for Pro features |

None of these permissions are used to collect or transmit data without your explicit action.

## When Data Leaves Your Device (Optional Features)

Data is transmitted off your device **only** in these user-initiated scenarios:

### AI-Generated Replies (off by default)
If you enable AI replies and provide an API key, the sender name, message text, your system prompt, and model selection are sent via HTTPS to the AI provider you chose (OpenAI or Google Gemini). Their privacy policies apply:
- OpenAI: https://openai.com/policies/privacy-policy
- Google Gemini: https://policies.google.com/privacy

### Webhooks (off by default)
If you configure a webhook URL on a rule, Catchyu sends an HTTPS request to **your** specified URL containing the sender name, message, and reply. Only HTTPS is allowed.

### Google Play Billing
Purchase tokens are exchanged with Google Play's servers when you buy Pro features. We do not receive your payment details. See https://policies.google.com/privacy.

### Firebase Analytics & Crashlytics (build-dependent)
Some builds include Firebase Analytics (anonymous app-open/screen-view events) and Crashlytics (crash stack traces). No message content, contact data, or personally identifying information is sent. If `google-services.json` is not bundled, Firebase is fully disabled.

## Data Retention

- **On your device:** Data persists until you delete it or uninstall the app.
- **AI providers:** Subject to OpenAI / Google Gemini retention policies.
- **Webhook recipients:** You control what your endpoint does with the data.
- **Firebase:** Analytics retained 14 months; crash reports retained 90 days.

## Children's Privacy

Catchyu is a productivity tool intended for users **13 years and older**. It does not knowingly collect personal information from children under 13. If you believe a child has used the app, contact us and we will assist with deletion.

## Your Rights

Because data is stored locally, you can exercise the following rights directly in the app:

- **Access:** View your data on any screen (Leads, Rules, Templates, Notes).
- **Export:** Use CSV export in Leads to copy your data.
- **Delete:** Delete any record from its detail screen, or use "Clear all" in Settings.
- **Withdraw consent:** Disable the notification listener in Android Settings, or uninstall the app.

## Security

- Local data lives in the app's private sandbox, inaccessible to other apps.
- Auto Backup is disabled to prevent accidental cloud copying.
- All optional network calls use HTTPS. Cleartext HTTP is blocked.

## Changes to This Policy

If this policy is updated, the revised version will be posted here with an updated date. Material changes will be highlighted in-app or in Play Store release notes.

## Contact

If you have questions about this privacy policy, contact us at:

**Email:** kakooapps@gmail.com

---

© 2026 KaKooApps. All rights reserved.
