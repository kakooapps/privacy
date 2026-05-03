---
title: Privacy Policy — Catchyu
---

# Catchyu — Privacy Policy

**Effective date:** 19 April 2026
**Last updated:** 3 May 2026

This Privacy Policy describes how the **Catchyu** Android application (the "App"), published by **KaKoo Apps**, handles your information.

We designed Catchyu to be a **local-first** auto-reply tool. By default, all of your data stays on your device. Network features (AI replies, webhooks, optional analytics) only activate when **you** turn them on.

---

## 1. Who we are

- **App name:** Catchyu
- **Package name:** `com.kakoo.apps.catchyu`
- **Publisher:** KaKoo Apps, Chennai, Tamil Nadu, India
- **Contact:** privacy@kakooapps.com

---

## 2. Data the App accesses

### 2.1 Notifications from messaging apps
Catchyu uses Android's `NotificationListenerService` to read incoming notifications from messaging apps you select (WhatsApp, WhatsApp Business, Telegram, Signal, Facebook Messenger, Instagram, Viber, LINE, and any custom apps you add).

For each notification, the App extracts:
- the sender name shown in the notification
- the message text shown in the notification
- the contact identifier (phone number) if Android exposes it
- the package name of the source app (e.g. `com.whatsapp`)
- the timestamp the notification was posted

The App **does not** access your contacts, SMS messages, call logs, accounts, or device identifiers.

### 2.2 Data you create inside the App
- Auto-reply rules and keywords
- Reply templates
- Notes
- Custom variables
- Custom app entries
- Blocked-contact list
- App preferences (theme, language, business hours, toggles, etc.)
- AI API key (only if you choose to use the AI feature)

### 2.3 Permissions requested
| Permission | Why |
|---|---|
| `BIND_NOTIFICATION_LISTENER_SERVICE` | Required to read notifications and send auto-replies. This is the App's core function. |
| `INTERNET` | Used **only** when you enable AI replies, webhooks, or the optional Firebase build. |
| `POST_NOTIFICATIONS` | To show you in-app notifications (e.g. "New lead captured"). |
| `com.android.vending.BILLING` | To process Google Play in-app purchases for Pro features. |
| `ACCESS_NETWORK_STATE` | To detect network connectivity changes for billing state refresh. |

The App does **not** request permission to read your contacts, SMS, call logs, location, camera, microphone, or storage outside its own sandbox.

---

## 3. How data is stored

All App data is stored **locally on your device**, inside the App's private sandbox storage:

- A Room (SQLite) database for leads, rules, messages, reply logs, blocked contacts, templates, notes, custom apps, custom variables.
- An Android DataStore for preferences and the AI API key (if you set one).

We have **disabled Android Auto Backup and Device-Transfer** for this data (see `data_extraction_rules.xml`). Your leads, messages, and API keys are **not** included in automatic Google Drive backups or device-to-device transfer.

However, if you use the optional **Google Drive Backup** feature (Pro only), you can manually back up and restore your data — see Section 4.6.

---

## 4. When data leaves your device

Catchyu transmits data off your device **only** in these explicit, user-initiated scenarios:

### 4.1 AI-generated replies (optional, off by default)
If you enable AI replies and provide an API key, then for each rule you mark "use AI", the following is sent over HTTPS to the provider you chose:

- Your API key (in an HTTP header)
- The system prompt you configured for the rule
- The sender name and message text from the matched notification
- The model name you selected (e.g. `gpt-3.5-turbo`)

Supported providers and endpoints:
- **OpenAI** — `https://api.openai.com/v1/chat/completions`
- **Google Gemini** — `https://generativelanguage.googleapis.com/v1beta/models/...:generateContent`

These providers are independent third parties governed by their own privacy policies:
- OpenAI: https://openai.com/policies/privacy-policy
- Google Gemini: https://policies.google.com/privacy

If you do not enable AI, **nothing** is sent to either provider.

### 4.2 Webhooks (optional, off by default)
If you configure a webhook URL on a rule, then when that rule fires, Catchyu sends an HTTPS request to the URL **you specified**, containing:

```json
{
  "event": "auto_reply",
  "sender_phone": "...",
  "sender_name": "...",
  "message": "incoming message text",
  "reply": "the reply Catchyu sent",
  "rule_id": 123,
  "timestamp": 1700000000000
}
```

Plain HTTP webhooks are rejected; only HTTPS is allowed. You control the destination — we do not see or store webhook payloads on our servers (we have no servers).

### 4.3 Google Play Billing
When you purchase a Pro subscription or the lifetime upgrade, the Google Play Billing Library exchanges purchase tokens with Google Play's servers. We do not receive your payment details. See https://policies.google.com/privacy.

### 4.4 Firebase Analytics & Crashlytics (optional, build-time)
Some distributions of the App include **Firebase Analytics** and **Firebase Crashlytics** (Google services).

If included, the App sends the following to Google:
- Anonymous app-open events
- Anonymous screen-view events (no message or contact content)
- Crash stack traces and device/OS metadata when the App crashes

We do **not** send your name, email, contact list, message content, or any personally identifying information through Firebase.

If `google-services.json` is not bundled with the build you installed, Firebase is fully disabled and **no** analytics or crash data is transmitted. Google's privacy policy: https://firebase.google.com/support/privacy.

### 4.5 Tasker integration (local only)
If you enable Tasker integration, Catchyu communicates with the Tasker app on your device through Android intents. **No network traffic** is involved.

### 4.6 Google Drive Backup (optional, Pro only)
If you are a Pro subscriber and choose to sign in with Google, Catchyu can back up your app data to your **personal Google Drive** account.

**What is backed up:**
- Auto-reply rules, templates, notes, custom variables, custom apps
- Leads and message history
- Blocked contacts and reply logs
- App settings and preferences (theme, language, business hours, etc.)

**How it works:**
- Catchyu uses **Google Sign-In** with the `drive.appdata` scope, which grants access **only** to a hidden app-specific folder in your Google Drive — Catchyu cannot see or access any other files in your Drive.
- Backup data is serialized as a single JSON file (`catchyu_backup.json`) and uploaded over HTTPS.
- All data is stored in **your own Google account**, not on our servers.
- Your Google email address is displayed in the app solely to confirm which account is connected. We do **not** store, transmit, or log your email address.

**How to delete your backup:**
- Open Settings → Backup → Sign Out (removes app access and disconnects your Google account)
- Or visit [myaccount.google.com/permissions](https://myaccount.google.com/permissions) → revoke Catchyu's access (Google will remove the app data folder)
- Or uninstall the app (the backup file remains in your Drive until you revoke access)

Google's privacy policy applies to data stored in Google Drive: https://policies.google.com/privacy

---

## 5. What we do **not** do

- We do **not** sell or share your personal data with advertisers or data brokers.
- We do **not** access your phone contacts, SMS, call logs, location, camera, or microphone.
- We do **not** collect or transmit your Android ID, Advertising ID, IMEI, or FCM token.
- If you use Google Drive Backup, your Google email is displayed in-app for confirmation only — it is **not** stored, logged, or sent to our servers.
- We do **not** operate any server that receives your message content or contact data. (AI providers, webhooks, and Google Drive are third parties of your choice.)

---

## 6. Data retention

- **On your device:** Data persists until you delete it (per-record delete, "Clear all" actions, or uninstalling the App).
- **Google Drive Backup:** If you used the optional backup feature, the backup file remains in your Google Drive until you sign out from the app or revoke Catchyu's access at [myaccount.google.com/permissions](https://myaccount.google.com/permissions).
- **AI providers:** Subject to OpenAI / Google Gemini retention policies. Review their policies for details.
- **Webhook recipients:** You control what your webhook endpoint does with the payload.
- **Firebase Analytics:** Default Google Analytics retention applies (currently 14 months, configurable by us).
- **Firebase Crashlytics:** Crash reports are retained per Google's policy (currently 90 days for unprocessed crashes).

---

## 7. Children

Catchyu is a productivity tool intended for users **13 years and older**. We do not knowingly collect data from children under 13. If you believe a child has used the App, contact us and we will assist with deletion.

---

## 8. Your rights

Because data is stored locally on your device, you can exercise the following rights at any time directly inside the App:

- **Access:** Open any screen (Leads, Rules, Templates, Notes) to view your data.
- **Export:** Use the CSV export feature in Leads to copy your data.
- **Correction / deletion:** Edit or delete any record from its detail screen, or use "Clear all" actions in Settings.
- **Withdraw consent:** Disable the notification listener in Android Settings, or uninstall the App, to stop all processing.
- **Revoke Google access:** Go to Settings → Backup → Sign Out, or visit [myaccount.google.com/permissions](https://myaccount.google.com/permissions) to revoke Catchyu's access to your Google Drive.

If you live in the EU/UK (GDPR), India (DPDP Act), California (CCPA), or another jurisdiction with data-protection law, you also have rights to lodge a complaint with your local supervisory authority.

To request information about data we hold (we generally hold none — see Section 4), email us at privacy@kakooapps.com.

---

## 9. Security

- Local data lives in the App's private sandbox, inaccessible to other apps.
- Auto Backup is disabled to prevent accidental cloud copying of leads, rules, messages, and API keys.
- All optional network calls (AI, webhooks) use HTTPS. Cleartext HTTP is blocked in the App's network security configuration.
- We cannot guarantee absolute security; please use device-level protections (lock screen, encryption) and keep your AI API keys private.

---

## 10. Changes to this policy

We may update this policy when the App's behavior changes. Material changes will be highlighted in-app or in the Play Store release notes. The "Last updated" date above will reflect the latest revision.

---

## 11. Contact

Questions or requests:

- Email: privacy@kakooapps.com
- Publisher: KaKoo Apps, Chennai, Tamil Nadu, India

---

*This policy was last reviewed on 3 May 2026.*
