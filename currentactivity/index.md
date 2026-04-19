---
title: Privacy Policy — Current Activity
---

# Privacy Policy — Current Activity

**Last updated:** April 19, 2026

**Developer:** KaKooApps  
**App:** Current Activity  
**Package:** com.kakoo.apps.currentactivity

---

## Overview

Current Activity is a developer utility that displays the foreground app's name, package name, and activity class in real time via a floating overlay and/or a persistent notification.

## Data Collection

**Current Activity does not collect, transmit, store, or share any personal data.**

Specifically:

- **No analytics or tracking SDKs** are included.
- **No crash reporting services** are integrated.
- **No network requests** are made by the app. The app has no internet-dependent functionality.
- **No user accounts** are required or supported.
- **No advertising SDKs** are included.

## Data Stored on Device

The following data is stored **locally on your device only** and is never transmitted:

| Data | Purpose | Storage |
|------|---------|---------|
| Display preferences (overlay opacity, toggle states) | Remember your settings between sessions | Android DataStore (app-private) |
| Activity history (last 50 entries) | Show recently viewed activities in-app | In-memory only; cleared when the service stops |
| Excluded package list | Skip apps you don't want tracked | Android DataStore (app-private) |

All locally stored data is deleted when you uninstall the app or clear app data.

## Permissions

| Permission | Why it's needed |
|------------|----------------|
| **Usage Access** (`PACKAGE_USAGE_STATS`) | To detect which app and activity is currently in the foreground |
| **Display over other apps** (`SYSTEM_ALERT_WINDOW`) | To show the floating overlay on top of other apps |
| **Notifications** (`POST_NOTIFICATIONS`) | To display activity info in the notification bar |
| **Foreground Service** | To keep the activity-detection service running reliably |
| **Boot Completed** (`RECEIVE_BOOT_COMPLETED`) | To auto-start the service after a device reboot (only if enabled by the user) |

None of these permissions are used to collect or transmit data.

## Third-Party Services

Current Activity does not use any third-party services, libraries, or SDKs that collect data.

## Children's Privacy

Current Activity is a developer tool not directed at children under 13. It does not collect any personal information from anyone, including children.

## Changes to This Policy

If this policy is updated, the revised version will be posted here with an updated date. Continued use of the app constitutes acceptance of any changes.

## Contact

If you have questions about this privacy policy, contact us at:

**Email:** kakooapps@gmail.com

---

© 2026 KaKooApps. All rights reserved.
