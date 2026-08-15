# SevaPOS License & Remote Configuration

This repository serves as a lightweight remote configuration and license management service for pre-release builds of the **SevaPOS** Android application.

## Overview

The SevaPOS app queries this repository via raw HTTP GET requests (`raw.githubusercontent.com`) on launch to verify device license status, remote kill-switch states, and trial allocations without requiring a heavy backend infrastructure.

## Directory Structure

```text
.
├── licenses/
│   ├── SAMPLE_DEVICE_ID.json   # Device-specific overrides
│   └── .gitkeep
└── README.md

```

## License JSON Schema

Each device license file inside `/licenses/` is named using the target device's unique `ANDROID_ID` (`<DEVICE_ID>.json`).

```json
{
  "device_id": "a1b2c3d4e5f67890",
  "enabled": true,
  "expires_at_epoch": 1789500000000,
  "notes": "Tester - Beta Group A"
}

```

### Schema Parameters

| Parameter | Type | Description |
| --- | --- | --- |
| `device_id` | String | Unique hardware `ANDROID_ID` of the user's device. |
| `enabled` | Boolean | Remote kill-switch flag (`true` allows access, `false` revokes access). |
| `expires_at_epoch` | Long | Expiration timestamp in milliseconds since Unix epoch (UTC). |
| `notes` | String | Optional metadata for tracking ownership or release group. |

---

*Note: This repository contains public configuration data only. No sensitive application source code or personal data is stored here.*

```

<FollowUp label="Want to know how to calculate Unix epoch timestamps easily for setting custom expiration dates?" query="How do I quickly generate Unix epoch timestamps in milliseconds for testing different expiration dates?"/>

```
