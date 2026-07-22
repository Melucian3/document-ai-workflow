# Document AI Workflow

## Case Study

This project implements an automated document processing workflow using **n8n** and **Google Gemini Document AI**.

The workflow receives a document through a Webhook, extracts key information using AI, normalizes the extracted values, validates critical fields, and returns a structured JSON response.

---

## Workflow

The workflow performs the following steps:

1. Receive a PDF or image through a Webhook.
2. Convert the Base64 file into a valid document.
3. Analyze the document using Google Gemini.
4. Extract:
   - Document ID
   - Total amount
   - Date
5. Normalize:
   - Numbers without currency symbols.
   - Dates in YYYY-MM-DD format.
6. Validate required fields.
7. Return:
   - Success response if all fields exist.
   - Error response if any required field is missing.

---

## Technologies

- n8n
- Google Gemini
- Webhook
- JavaScript
- PowerShell (testing)

---

## Credentials

Configure the following credentials before running the workflow:

- GEMINI_API_KEY
- Webhook URL

Do not include real API keys in this repository.

---

## Example Output

Successful response:

```json
{
  "id_documento": "0002-00001234",
  "total": 60000,
  "fecha": "2026-07-22"
}
```

Error response:

```json
{
  "error": true,
  "mensaje": "Documento inválido, corrupto o con campos críticos incompletos"
}
```
