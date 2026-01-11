# 🏡 AI-Powered Real Estate Lead Management System

## 🚀 Overview
This project is an automated pipeline designed for a Real Estate Agency ("Lahore Property Leads Office") to eliminate manual data entry. It captures leads from Google Sheets, detects duplicates using historical data, and leverages OpenAI (GPT-4o) to generate a high-value daily executive summary email.

**Technologies Used:**
- **n8n** (Workflow Automation)
- **OpenAI API** (GPT-4o Mini for Intelligent Summaries)
- **Google Sheets** (Database & CRM)
- **Gmail** (Automated Reporting)
- **JavaScript** (Custom logic for batch deduplication)

---

## ⚙️ How It Works

### 1. Data Ingestion & Normalization
The workflow triggers daily at 10:00 AM, pulling raw lead data from a Google Sheet. It normalizes phone numbers (formatting them to `92...`) to ensure accurate matching across different input formats.

### 2. Intelligent Deduplication (The Logic)
Unlike basic filters, this workflow performs a two-layer check:
- **Historical Check:** Compares new leads against a database of previously processed customers.
- **Batch Analysis:** Uses custom JavaScript to detect if a duplicate was submitted *twice in the same day* (e.g., a user submitting the same form twice within minutes).

### 3. AI Analysis & Reporting
Valid leads are sent to an OpenAI node with a strict system prompt. The AI:
- Aggregates the stats (Total vs. New vs. Duplicates).
- Identifies market trends (e.g., "High interest in Safe City Town today").
- Formats a clean HTML email with bold key metrics.

### 4. Database Update
The Master Database is updated with the status (`New` vs `Duplicate`) and the clean data is archived for future reference.

---

## 💡 Challenges I Faced
Building the deduplication logic was tricky because sometimes a lead submits the same form twice in one minute (batch duplicates), while other times they are an old customer returning weeks later (historical duplicates). I wrote custom JavaScript to handle both scenarios simultaneously to ensure the client never receives spam.

---

## 📸 Workflow Visualization

<img width="1920" height="830" alt="image" src="https://github.com/user-attachments/assets/02f8b34d-1df7-46b7-a2f3-2338810ca887" />

---

## 📬 Final Output Example

<img width="1551" height="625" alt="image" src="https://github.com/user-attachments/assets/bff9e38a-3a73-41e6-81e9-248a4a5d5594" />

---

## 🛠️ How to Use This Workflow

1. **Import to n8n:**
   - Download the [JSON file](n8n-workflows/real-estate-lead-automation.json) from this repository.
   - In n8n, go to **Workflow** > **Import from File**.

2. **Setup Credentials:**
   - **Google Sheets:** Connect your Google Service Account.
   - **OpenAI:** Add your API Key.
   - **Gmail:** Connect your SMTP or Gmail OAuth.

3. **Configure IDs:**
   - Replace the Spreadsheet ID in the Google Sheets nodes with your own sheet.
   - Update the "To" email address in the Gmail node.

---

## 👨‍💻 Author
**Aurangzaib Gill**
*Passionate about automating business logic with AI & NoCode tools.*
