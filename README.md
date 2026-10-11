<div align="center">

#  Invoice Parser Agent

### Automate invoice extraction, record-keeping and stakeholder alerts end to end.

![n8n](https://img.shields.io/badge/Built%20with-n8n-EA4B71?style=for-the-badge&logo=n8n&logoColor=white)
![OpenAI](https://img.shields.io/badge/AI-OpenAI-412991?style=for-the-badge&logo=openai&logoColor=white)
![Google Drive](https://img.shields.io/badge/Trigger-Google%20Drive-4285F4?style=for-the-badge&logo=googledrive&logoColor=white)
![Google Sheets](https://img.shields.io/badge/Database-Google%20Sheets-34A853?style=for-the-badge&logo=googlesheets&logoColor=white)
![Gmail](https://img.shields.io/badge/Notify-Gmail-EA4335?style=for-the-badge&logo=gmail&logoColor=white)

</div>

---

## 📌 Overview

Manual invoice entry is slow, repetitive and error-prone. This project is an **event-driven automation pipeline** built with **n8n** that removes the manual work completely.

The moment a new invoice PDF lands in a Google Drive folder the agent reads it uses **OpenAI** to extract the key financial details logs them into **Google Sheets**, and sends a professional notification email through **Gmail**, all within seconds and with zero human input.

---

## ✨ Key Features

| Feature | Description |
|---|---|
| ⚡ **Event-Driven Trigger** | Starts automatically when a new PDF is created in a watched Google Drive folder. |
| 📑 **PDF Text Extraction** | Converts PDF content to clean text using n8n's built-in extractor, with no external tools required. |
| 🤖 **AI Information Extraction** | OpenAI parses semi-structured invoice text into structured fields such as invoice number, client or sender details, due date, and amounts. |
| 🗂️ **Automatic Record Keeping** | Every processed invoice is appended as a new row in Google Sheets. |
| 📧 **Smart Email Notifications** | A second AI step drafts a formal email, which Gmail sends to billing or stakeholders. |

---

## 🏗️ Architecture & Workflow

```mermaid
flowchart TD
    A[📂 Google Drive Trigger<br/>New PDF detected] --> B[⬇️ Download File]
    B --> C[📄 Extract from File<br/>PDF → Text]
    C --> D[🧠 Information Extractor<br/>+ OpenAI Chat Model]
    D --> E[📊 Append Row in Google Sheets]
    E --> F[✍️ Message a Model<br/>OpenAI drafts email]
    F --> G[📧 Send a Message<br/>Gmail]
    G --> H[🏁 No Operation]

    style A fill:#4285F4,color:#fff,stroke:#2b5fb4
    style D fill:#412991,color:#fff,stroke:#2b1a63
    style E fill:#34A853,color:#fff,stroke:#237a3b
    style F fill:#412991,color:#fff,stroke:#2b1a63
    style G fill:#EA4335,color:#fff,stroke:#b3281d
```

### Step-by-Step

1. **Google Drive Trigger**: watches a folder and fires on every new file.
2. **Download File**: fetches the uploaded invoice as binary data.
3. **Extract from File**: turns the PDF into raw text.
4. **Information Extractor**: powered by an OpenAI Chat Model, it returns the invoice data in a strict, structured format.
5. **Append Row in Sheet**: stores the extracted data in Google Sheets.
6. **Message a Model**: generates a polished notification email using the extracted details.
7. **Send a Message (Gmail)**: delivers the email to the relevant recipients.
8. **No Operation**: clean end of the workflow.

---

## 🧰 Tech Stack

- **Automation Platform:** n8n
- **AI Models:** OpenAI (Chat Model + Message a Model)
- **Storage & Trigger:** Google Drive, Google Sheets
- **Notifications:** Gmail

---

## ⚙️ Setup Guide

### Prerequisites
- An [n8n](https://n8n.io) account (cloud or self-hosted)
- An OpenAI API key
- A Google account with Drive, Sheets, and Gmail access

### Installation

1. **Import the workflow**
   Open n8n, click **Import from File**, and select the exported workflow `.json`.

2. **Connect your credentials**
   - Google Drive (OAuth2)
   - Google Sheets (OAuth2)
   - Gmail (OAuth2)
   - OpenAI (API key)

3. **Configure the nodes**
   - Set the **watched folder** in the Google Drive Trigger.
   - Choose your **spreadsheet and sheet** in the Append Row node.
   - Set the **recipient email** in the Gmail node.

4. **Activate**
   Toggle the workflow to **Active**, then upload a sample invoice PDF to test it.

---

## 📊 Sample Output

After each upload, the Google Sheet receives a new row like this:

| Invoice No. | Client / Sender | Due Date | Amount |
|---|---|---|---|
| INV-1001 | Example Co. | 2026-10-30 | 1,250.00 |

> 💡 Add a screenshot of your workflow here: `![Workflow](./assets/workflow.png)`

---

## 🔮 Future Improvements

- [ ] Support for scanned invoices and images (OCR)
- [ ] Duplicate invoice detection
- [ ] Error handling with failure alerts
- [ ] Slack / WhatsApp notifications
- [ ] Dashboard for spending analytics

---

## 👩‍💻 Author

**Hamna Asif**
Full-Stack Developer · UI/UX Designer · AI Specialist

[![GitHub](https://img.shields.io/badge/GitHub-Hamna--Asif05-181717?style=flat-square&logo=github)](https://github.com/Hamna-Asif05)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-hamna--asif5-0A66C2?style=flat-square&logo=linkedin&logoColor=white)](https://linkedin.com/in/hamna-asif5)

---

<div align="center">

⭐ If you found this project useful, please give it a star!

</div>
