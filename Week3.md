# 🧠 AI Club — Week 3

## Prompt Engineering & Debugging the LLM Step

---

## 🎯 Goal of Week 3

By the end of this week, you will have:

* Configured an LLM module that returns a **valid JSON array** every time.
* Written a **System prompt** that forces deterministic, non-conversational output.
* Debugged common failures: wrong model, bad mappings, token limits, and empty inputs.
* Learned to read a module's **input bundle** before blaming the prompt.

---

## ✅ Step 1 — Choose a Chat Model

Not every model in Make.com's Groq list can extract data.

1. Open the LLM module (Groq, OpenAI, or Claude) and click the **Model** dropdown.
2. Pick a **chat model** such as `openai/gpt-oss-120b`, `openai/gpt-oss-20b`, or `llama-3.3-70b-versatile`.
3. **Avoid** models with names like `prompt-guard`, `whisper`, or `orpheus`. These are safety classifiers or audio models and cannot follow extraction instructions.

**Lesson learned:** A `[400]` error about message length on a `prompt-guard` model was caused by the model choice, not the syllabus size.

---

## ✅ Step 2 — Set the Role to System

1. In the **Messages** section, set **Role** to **System** for your instructions.
2. Use **User** only for the syllabus text, if you split them into two messages.

**Lesson learned:** Setting the role to **Assistant** tells the model that your instructions are its own previous reply, which produces unreliable output.

---

## ✅ Step 3 — The Extraction Prompt

Paste the instructions into the Content field, then map the syllabus text as the last line.


Use this refined, high-performance prompt in your LLM module:

📌 **The Syllabus-to-JSON Schema Prompt**

```text
SYSTEM:
You are an expert data extraction agent. Your goal is to convert unstructured academic syllabus text into a structured JSON array.

RULES:
- Extract all graded components: assignments, quizzes, exams, projects.
- Date Format: Use ISO 8601 (YYYY-MM-DD). If year is missing, assume 2026.
- If a date is a range, use the end date.
- Do NOT include conversational text.
- Do NOT include markdown formatting (like ```json).
- If an item lacks a date, skip it.

SCHEMA:
[
  {
    "EventName": "string",
    "DueDate": "YYYY-MM-DD",
    "Description": "string (include weight e.g., 10%)"
  }
]

FEW-SHOT EXAMPLES:
Input: "Final Exam is on Dec 12th"
Output: [{"EventName": "Final Exam", "DueDate": "2026-12-12", "Description": ""}]

Input: "Homework 1 due Sep 5"
Output: [{"EventName": "Homework 1", "DueDate": "2026-09-05", "Description": ""}]
```

Then, on the line after `SYLLABUS TEXT:`, insert the syllabus pill (for example, **Body1** from Tools). Do not type placeholder text such as `[MAP EXTRACTED TEXT HERE]` if a pill is already there. Both would be sent.

---

## 🔧 Step 4 — Debugging Common Errors

| Error | Likely cause | Fix |
|---|---|---|
| `[400]` "reduce the length of the messages" | Model is a classifier, or the input is too long | Switch to a chat model. decrease input size and combine with two chat calls |
| `[413]` "Request too large … TPM" | Input plus output exceeds the per-minute token limit | Lower Max Tokens, use a smaller model, split the text, or upgrade the tier |
| Output is `[]` | Empty or wrong input reached the model | Open the LLM bundle and confirm the syllabus text appears after `SYLLABUS TEXT:` |
| Output contains the word `substring` or other code | A formula for text splitting/other was typed as plain text | Insert functions with the mapping panel's function picker |
| Output includes ```` ```json ```` | Prompt allowed markdown | Repeat the "no markdown code blocks" rule and keep the role as System |

**Lesson learned:** When an output is wrong, check the **input bundle** of the failing module first. Most of this week's failures came from what was sent in, not from what the model returned.

---

## ✅ Step 5 — Handling Token Limits on the Free Tier

1. Check the **Max Tokens** field and set it to about **1500**. JSON output for a syllabus is short.
2. If a `[413]` error persists, the input text is too large for one request on the free tier.
3. Choose one of these options:
   * **Upgrade the Groq tier**, the simplest fix that keeps one request per syllabus.
   * **Split the text** into two halves in a Tools module, send each half to the LLM, and merge the two JSON lists before the iterator.

---

## ✅ Step 6 — Validation Checklist

Before moving to Week 4, confirm the following:

* The Tools output (if used) contains real syllabus text, not formulas or placeholders.
* The LLM module's input bundle shows the syllabus text after `SYLLABUS TEXT:`.
* The LLM output starts with `[` and ends with `]`, with no markdown or extra sentences.
* Each object has only the keys `EventName`, `DueDate`, and `Description`.

---

## 📦 What You Should Have by the End

* ✅ A chat model (not a classifier) selected in the LLM module
* ✅ Role set to System, with one syllabus pill and no leftover placeholders
* ✅ A JSON array output that parses cleanly
* ✅ A plan for token limits (Max Tokens lowered, plus an upgrade or split)

---

## 🔜 What's Next (Week 4 Preview)

Next week:

* **Logic & Iterator Control**: Taking the JSON array and processing each event as its own calendar item.

---