# SyllabusToCalendarAgent

---

# 🧠 AI Club — Week 1

## Infrastructure Setup & API Foundations

---

## 🎯 Goal of Week 1

By the end of this week, you will have:

* A **Google Cloud Project** enabled for API access.
* **Google Drive & Calendar API** credentials configured.
* An automation workspace ([Make.com/Zapier](https://www.google.com/search?q=https%3A%2F%2FMake.com%2FZapier)) initialized.
* A "Trigger" mechanism established to watch for syllabus uploads.
* A foundational understanding of **Event-Driven Automation**.

---

## ✅ Step 0 — Prepare Your Environment (Required)

Before doing *anything else*, ensure you have the following:

* **Google Account**: Use the same one you intend to use for your calendar.
* **Automation Account**:
👉 [https://www.make.com/](https://www.make.com/) OR [https://zapier.com/](https://zapier.com/)
* Make.com is **highly recommended** over Zapier for the sake of this project, due to cost efficiency.

---

## ✅ Step 1 — Set Up Your Google Drive Folder

You need a dedicated space for your syllabus files to trigger the pipeline.

1. Open Google Drive.
2. Create a new folder named:
`AI-Agent-Syllabus-Sync`
3. Upload a sample PDF syllabus into this folder.

---

## ✅ Step 2 — Configure Google Cloud API Access

To allow your automation tool to "see" your files and "write" to your calendar, you need proper API access.

1. Go to the [Google Cloud Console](https://console.cloud.google.com/).
2. Create a new Project named:
`Syllabus-Agent-Prod`
3. Navigate to **APIs & Services > Library**.
4. Enable the following APIs:
* **Google Drive API**
* **Google Calendar API**
* Click here to learn what an API is: https://www.geeksforgeeks.org/software-testing/what-is-an-api/


---

## ✅ Step 3 — Automation Tool Integration

Connect your Google account to your automation platform (Make or Zapier).

1. **Create a new scenario/zap**.
2. **Trigger Event**: Choose "Google Drive - New File in Folder."
3. **Authentication**: Select the account you just configured and point the trigger to the `AI-Agent-Syllabus-Sync` folder.
4. **Test**: Trigger the automation by ensuring it correctly detects the file you uploaded in Step 1.

---

## 🧩 Step 4 — Initial Payload Handling

You need to ensure the automation is capturing the file metadata.

* Verify that your automation tool is receiving the **File ID** and **File Name** from the trigger.
* *Note*: If you are using Make.com, ensure you have the "Download File" module ready for next week’s LLM ingestion.

---

## 🔧 Step 5 — Verify & Document

Things to check:

* Does the automation trigger instantly when you drop a file into the folder?
* Are you able to see the metadata (File Name/Size/ID) in your automation logs?
* Is your Google Calendar accessible by the integration?

---

## 📦 What You Should Have by the End

* ✅ Google Cloud Project enabled
* ✅ Dedicated Drive folder for triggers
* ✅ Automation tool connected to your Google Suite
* ✅ Successful "New File" trigger test

---

## 🔜 What’s Next (Week 2 Preview)

Next week:

* **Data Ingestion**: Converting PDF content into raw text.
* **Payload Handling**: Sending the text to an LLM.
* **Prompt Engineering**: Refining the executive assistant prompt for clean JSON output.

---
