# AACT NOW 2026 • Official Touch 10 Ambassador & Staff Intake Portal

High-speed, responsive, bilingual civic relational intake application designed for the **Advocacy Alliance Center of Texas (AACT NOW)**.

---

## 🌟 Overview & Architecture

This portal serves as the front-end intake tier for AACT NOW's 2026 civic engagement campaigns across Hidalgo, Cameron, Starr, and Willacy counties:

```
+-----------------------------------------------------------+
|               Replit Web Tier (Frontend SPA)              |
|                                                           |
|  [Tab 1: Public Touch 10]       [Tab 2: Staff Station]   |
|  - 10-contact intake form       - 338 Ambassador search   |
|  - English / Spanish toggle     - 10-key keyboard flow    |
|  - Phone auto-formatting        - Shift batch receipts    |
|                                                           |
|             Firestore REST (intake_submissions)           |
+-----------------------------+-----------------------------+
                              | (JSON payload)
                              v
+-----------------------------------------------------------+
|          AACT Data Engine (Local / GCP Cloud Run)         |
|  - core/firestore_intake_sync_daemon.py                   |
|  - Cross-references 735k registered Quad-County voters    |
|  - Generates 5-tab Excel Action Workbooks + SMS queues    |
|  - Syncs to Google Drive: _AACT_Working_Now               |
+-----------------------------------------------------------+
```

---

## 🚀 Key Features

### 1. Public Ambassador Touch 10 Form
* Mobile-first responsive layout for volunteers and community ambassadors.
* Direct collection of up to 10 relational contacts (friends, family, neighbors, co-workers).
* Automatic phone masking `(956) XXX-XXXX` and address cleanup.
* Instant bilingual toggle (**English / Español**).

### 2. Staff & Intern Proxy Intake Station
* **Passcode Protected**: Unlocks with staff passcode (Default: `AACT2026`).
* **Pre-Seeded Ambassador Autocomplete**: Instant search across all **338 active ambassadors** from STC, DHR Health, Lone Star National Bank, Cantu Construction, LUPE, etc. Selecting an ambassador auto-populates their email, phone, and organization.
* **10-Key Speed Navigation**: Tab and Enter keys move through rows rapidly for high-speed transcription of physical paper cards.
* **Batch Accountability**: Auto-generates unique batch IDs (`SUB-YYYYMMDD-XXXX`) and keeps an in-shift counter of batches and contacts transcribed.
* **Double Redundancy**: Submits directly to Google Cloud Firestore (`intake_submissions`) while automatically exporting a CSV Action Workbook backup.

### 3. Civic Pulse Dashboard
* Real-time aggregate nonpartisan metrics (Voters Mobilized, Active Ambassadors, Partner Institutions, Early Ballots Cast).
* Quad-county voter turnout velocity bars.
* 100% Zero PII public transparency.

---

## 🔐 Staff Access Passcode

The Staff Proxy Station is protected by an operational gate.
* **Default Passcode**: `AACT2026`
* To change the passcode, update line 465 in `index.html`.

---

## 🌐 Custom Domain Setup (intake.aactnow.org)

In Replit:
1. Navigate to **Deployments** -> **Custom Domains**.
2. Enter `intake.aactnow.org` or `touch10.aactnow.org`.
3. Add the provided CNAME record to your DNS manager (Cloudflare, GoDaddy, Google Domains).
4. Replit automatically provisions free SSL/HTTPS certificates.

---

## 📄 License & Compliance

* **501(c)(3) Nonpartisan Compliance**: Strictly nonpartisan civic data collection.
* **Document ID**: AACT-SOP-ENG-2026-V3.
