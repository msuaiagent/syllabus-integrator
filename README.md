# syllabus-integrator
### Automate Your Academic Workflows in 7 Weeks

Turn manual syllabus entry into a fully automated, production-ready AI agent that syncs your course deadlines to Google Calendar.

---

## 🎯 The Challenge

**The Problem:** Students and instructors spend hours manually copying assignment deadlines from PDFs into their calendars.

**The Solution:** An end-to-end automation pipeline that:
- Detects when a syllabus PDF is uploaded
- Extracts assignments using LLM intelligence
- Validates & deduplicates data
- Syncs everything to Google Calendar
- Logs every step and handles failures gracefully

---

## 🛠 What You'll Build

A **full-cycle engineering project** that teaches:
- Event-driven automation
- LLM prompt engineering
- API integrations
- Error handling & logging
- Production-ready systems

**No prior experience required.**

---

## 📚 Weekly Curriculum

| Week | Goal | What You'll Learn |
|------|------|-------------------|
| **1** | Set up Google Cloud APIs and trigger automation when a syllabus PDF lands in a folder | API fundamentals, authentication, event-driven systems |
| **2** | Extract text from PDFs and use an LLM to convert it into structured JSON data | LLM API integration, data extraction, JSON formatting |
| **3** | Refine prompts and validation to ensure the LLM always outputs reliable, parseable JSON | Few-shot prompting, deterministic AI behavior, schema validation |
| **4** | Loop through the JSON array and filter out junk data before it hits your calendar | Control flow, iterators, data cleaning, conditional logic |
| **5** | Push validated events to Google Calendar with deduplication to prevent duplicates | Calendar API, data mapping, idempotency, deduplication patterns |
| **6** | Build error handling, logging, and alerts so the agent gracefully survives failures | Resilience, observability, production mindset |
| **7** | Document the project as a portfolio case study and prepare it for production deployment | Technical writing, portfolio building, deployment strategies |

---

## 🚀 Quick Start

### Prerequisites
- [ ] Google Account (for Drive & Calendar)
- [ ] Automation Platform Account ([Make.com](https://make.com) recommended, or [Zapier](https://zapier.com))
- [ ] Basic comfort with APIs and JSON

### Getting Started
1. **Start with Week 1:** Open `Week1.md` and follow the step-by-step setup.
2. **Test as you go:** Each week includes verification steps.
3. **Build incrementally:** By Week 7, you'll have a fully functional agent.

```
Week1.md  → Infrastructure & Triggers
Week2.md  → Data Ingestion & LLM Setup
Week3.md  → Prompt Engineering & Validation
Week4.md  → Logic & Iterator Control
Week5.md  → Calendar API & Deployment
Week6.md  → Error Handling & Logging
Week7.md  → Portfolio Documentation
```
---

## 🐛 Troubleshooting

Each week has its own troubleshooting guide. Common issues are covered in:
- **Prompt issues?** → Week 3
- **API errors?** → Week 6
- **JSON validation?** → Week 3-4

---

**Ready to build?** Start with [Week 1](./Week1.md). 🚀
