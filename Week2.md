# 🧠 AI Club — Week 2

## Data Ingestion & LLM Payload Handling

---

## 🎯 Goal of Week 2

By the end of this week, you will have:

* Extracted raw text from a PDF file within your automation pipeline.
* Configured the LLM "Brain" (OpenAI/Anthropic) to receive this text as a payload.
* Established a structured prompt to convert syllabus data into JSON.
* Successfully generated and viewed a valid JSON output from your automation logs.

---

## ✅ Step 1 — PDF-to-Text Ingestion

To process the syllabus, you must extract its content into a string your LLM can read.

1. Add a **Google Drive — Download File** module to your scenario.
2. Add a **PDF — Extract Text** module (or use the built-in PDF parser in your automation tool).
3. **Test**: Run the scenario and check the "Output" data. Ensure you see the full text of your syllabus in the logs.

---

## ✅ Step 2 — Configure the LLM Module

Now, connect your automation tool to the LLM.

1. Add the **Groq** module (you can also use OpenAI or Anthropic, but these will not be free).
2. Select the "Create a Completion" or "Chat" action.
3. Go to Groq.com (or the LLM of your choice) and create a free API key. 
5. Choose your model (e.g., `llama-3.1-8b-instant` or `claude-3-5-sonnet`).
6. Map the **extracted text** from Step 1 into the "User Message" or "Prompt" field.

---

## 🧩 Step 3 — The Syllabus-to-JSON Prompt (IMPORTANT)

Paste this system/user prompt into your LLM module to ensure consistent data structure.

📌 **The Syllabus-to-JSON Prompt**

```text
You are an executive assistant. Extract all assignments, quizzes, projects, and exams from this syllabus text. 

STRICT RULES:
- Format the output strictly as a JSON list.
- Use only these keys: 
  - "EventName"
  - "DueDate" (Strict YYYY-MM-DD format)
  - "Description" (Include assignment weight, e.g., 15% of grade)
- If a date is missing, omit the entry.
- Do NOT include any markdown code blocks (like ```json).
- Output ONLY the raw JSON list.

SYLLABUS TEXT:
[MAP EXTRACTED TEXT HERE]

```

---

## ✅ Step 4 — Execution & Verification

1. **Run the scenario** manually with your test syllabus.
2. **Review the output**: Open the "Execution Log" for the LLM module.
3. **Verify**: Does the output look like a clean list of objects?

*Example of expected output:*

```json
[
  {"EventName": "Midterm Exam", "DueDate": "2026-10-15", "Description": "20% of grade"},
  {"EventName": "Final Project", "DueDate": "2026-12-10", "Description": "30% of grade"}
]

```

---

## 🔧 Step 5 — Troubleshooting Common Issues

* **"I see markdown (```json) in my output"**: Add "Do not wrap in markdown" to your prompt instructions.
* **"The LLM is hallucinating dates"**: Ensure the syllabus text was correctly extracted in Step 1.
* **"JSON parsing failed"**: Check for trailing commas or unescaped characters in the prompt output.

---

## 📦 What You Should Have by the End

* ✅ Raw text extraction from PDF
* ✅ LLM module configured and authenticated
* ✅ Structured prompt implemented
* ✅ Valid JSON output displayed in logs

---

## 🔜 What’s Next (Week 3 Preview)

Next week:

* **JSON Array Splitting**: Turning a single list into individual actions.
* **Calendar API Mapping**: Sending data to Google Calendar.
* **Automated Reminders**: Adding logic for notification timing.

---
