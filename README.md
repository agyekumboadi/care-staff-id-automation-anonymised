# Anonymised Care Provider — Staff ID Registration Automation

An end-to-end **staff registration + unique Staff ID** automation designed for an **anonymised care provider** workflow.

It demonstrates how to combine:
- **Google Forms** for staff registration input
- **Google Sheets** as the registration database / audit log
- **Google Apps Script** to generate and append a unique Staff ID (e.g., `UQC12345`)
- **YAMM (Yet Another Mail Merge)** to email each registrant their Staff ID
- **IFTTT** (optional) to send a push notification when a new row is added

> **Anonymisation note:** “UQC” in this repo refers to **Unidentified Quality Care (UQC)** (Anonymised Care Provider).  
> Any screenshots are shared as **implementation evidence**; ensure all organisation identifiers and personal data are removed/redacted before public sharing.

---

## Why this matters

Care and frontline services often need fast, reliable onboarding workflows that:
- prevent duplicate IDs,
- reduce manual admin work,
- keep a clear audit trail,
- and maintain basic governance controls (access levels, minimum data exposure).

This automation shows a lightweight approach using common tools many teams already have.

---

## Solution overview (workflow)

1. **Staff submits registration** via Google Form  
2. Form responses land in **Google Sheets**
3. **Apps Script** generates a unique ID and writes it into the “Staff ID” column
4. **YAMM** sends the Staff ID email only after the Staff ID field is populated
5. *(Optional)* **IFTTT** sends a mobile notification when a new row is added

---

## Key features

- **Unique Staff ID generation** (prefix + padded numeric suffix)
- **Duplicate prevention** using script properties as a lightweight key store
- **Auto-append Staff ID** to the last row of the response sheet
- **Email delivery workflow** that waits until Staff ID exists (reduces “blank ID” emails)
- **Operational visibility** via YAMM tracking
- Optional **push alerts** for new registrations

---

## Implementation evidence (screenshots)

See: [`assets/README.md`](assets/README.md)

<details>
<summary><b>Click to expand: evidence index (filenames)</b></summary>

### Apps Script (ID generation)
- `AppScript_UQC_ID1.jpeg`
- `AppScript_UQC_ID(cont).jpeg`

### Registration input + data store
- `UQC_StaffID_GoogleForms.jpeg`
- `UQC_StaffID_Data1(Anonymised).jpeg`
- `UQC_StaffID_Data2(Anonymised).jpeg`

### Email automation (YAMM)
- `Template_Email_for YAMM_to_fetch_from.jpeg`
- `UQC_StaffID_Registration_System_NotificationRules_YAMM.jpeg`
- `UQC_StaffID_Registration_System_Tracking_Report_YAMM.jpeg`

### Optional notifications (IFTTT)
- `IFTTT_Integration1.jpeg`
- `IFTTT_Integration2.jpeg`
- `IFTTT_Integration3.jpeg`

</details>

---

## Data governance & privacy (what I intentionally did)

- **Data minimisation:** only capture essentials needed for onboarding and contact.
- **Access control:** keep edit access limited to authorised admins only.
- **Redaction:** shared screenshots are anonymised; no real staff identities should be exposed.
- **Auditability:** Google Sheet provides a timestamped log of registrations and ID issuance.

---

## How the Staff ID is generated (high level)

- Generate a random number
- Pad it to a fixed length (e.g., 5 digits)
- Prefix it (e.g., `UQC`)
- Check against stored keys to avoid duplicates
- Write the final Staff ID into the last row

---

## Repo contents

- `/assets` — screenshot evidence of the workflow
- `/data` — schema notes + guidance for creating anonymised sample data

---

## Roadmap (optional enhancements)

- Replace random ID with deterministic IDs (e.g., hash-based) for stronger uniqueness guarantees
- Add role-based access controls and approval steps
- Add error handling + admin alerts for failed ID generation or failed email sends
- Add automated logging to a separate audit sheet

---

## Author

**Samuel Boadi Agyekum**  
Data Analytics & IT Security Management  
- Portfolio: https://agyekumboadi.github.io/  
- LinkedIn: https://www.linkedin.com/in/samuel-agyekum-388a82150

---

## Disclaimer

This repository is shared for **portfolio demonstration** and process-improvement evidence.  
Do not upload real staff data. Use only anonymised examples and ensure compliance with your organisation’s policies and relevant data protection laws.
