---
name: pdf-architect
description: >
  Expert skill for reading PDFs, extracting structured data, processing forms, and handling scanned documents.
  Use this skill whenever the user uploads or references a PDF — especially when they want to extract tables,
  fill out or identify form fields, read scanned images, or convert PDF content into clean structured formats
  (Markdown, CSV, key-value pairs). Trigger even for simple requests like "read this PDF", "get the data from
  this file", or "what's in this document" — this skill improves accuracy and output quality in all PDF workflows.
---

# PDF Architect

A structured skill for high-accuracy PDF reading, table extraction, form processing, and OCR interpretation.

---

## Core Workflow

Always follow this four-step sequence:

1. **Review** — Scan the document structure: page count, layout type (text, table, scanned image, form), and overall content.
2. **Extract** — Pull out the relevant content based on the user's goal.
3. **Format** — Convert extracted content into the cleanest usable format (Markdown, CSV, Key-Value, plain text).
4. **Verify** — Flag ambiguous values, low-confidence OCR results, or incomplete fields for user confirmation.

---

## Extraction Rules

### Tables
- Always prioritize identifying tabular data first.
- Convert tables to **clean Markdown** by default.
- If the user needs to do further processing (e.g., import to Excel), offer **CSV format** as an alternative.
- Preserve column headers exactly as they appear. If headers are missing, infer them from context and label them clearly (e.g., `[Inferred: Item]`).

### Raw Text
- Extract paragraph by paragraph. Do not reformat unless asked.
- If the PDF has multi-column layout, read column by column (left to right).

### Mixed Content
- For pages with both text and tables, extract them separately and label each block (e.g., `[Section: Summary]`, `[Table: Financial Data]`).

---

## Form Processing

1. Identify all form fields (labeled inputs, checkboxes, dropdowns, signature lines).
2. Present detected fields as `Key: Value` pairs.
3. If fields are blank, mark them as `Key: [EMPTY]`.
4. Before assuming the user wants to fill them, ask:
   > "I found [X] form fields. Do you want to fill them in, extract the current values, or both?"

---

## OCR Logic (Scanned PDFs)

For scanned images or non-selectable text:
- Perform character-by-character interpretation using visual context.
- If a character is ambiguous (e.g., `0` vs `O`, `1` vs `l`), provide the **most likely interpretation** and append a confidence note:
  > `[OCR: "O3B" — low confidence, possibly "038"]`
- Never silently guess. Always surface uncertainty.
- If image quality is too poor for reliable reading, state that clearly and suggest the user provide a higher-resolution version.

---

## Output Formatting Defaults

| Content Type | Default Format |
|---|---|
| Tables | Markdown table |
| Lists | Markdown bullets |
| Forms | Key: Value pairs |
| Raw paragraphs | Plain text |
| Numeric data | Preserve original formatting |

Always ask before switching formats unless the user specifies one upfront.

---

## Notes

- If the PDF is password-protected or corrupted, report it immediately with a clear message.
- For large PDFs (10+ pages), confirm with the user which pages or sections to focus on before extracting everything.
- If the document contains both Arabic/Urdu and English text (common in UAE documents), flag it and extract both languages separately.
