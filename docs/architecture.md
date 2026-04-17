# WebFormAnalyzer — Architecture Overview

## Problem Statement

AMOS™ includes many form templates originally designed and distributed as PDF files. When these templates need to be digitized for in-app data collection, they are currently re-built manually inside jQuery FormBuilder — a slow, error-prone process with output that is not structured for BI consumption.

**WebFormAnalyzer** automates this conversion pipeline:

```
PDF Form Template  →  Field Extraction  →  SurveyJS JSON Schema  →  Live Preview / Edit
```

---

## High-Level Data Flow

```
1. User uploads a PDF form template
         ↓
2. Analyzer Engine parses the PDF
   - Detects form fields (text, checkbox, dropdown, date, signature...)
   - Infers layout (columns, sections, headers)
   - Identifies embedded images
         ↓
3. SurveyJS JSON schema is generated automatically
         ↓
4a. Live preview via SurveyJS Form Library (jQuery)
4b. Optional manual refinement via Survey Creator
         ↓
5. Schema saved to DB  →  Form served to end users in AMOS™
         ↓
6. Submitted responses stored as structured JSON in DB
         ↓
7. BI tools (Power BI, Tableau, SQL) query response tables directly
```

---

## Module Descriptions

### PDF Upload Component
- Accepts a PDF file via drag-and-drop or file picker
- Passes the file to the Analyzer Engine
- Libraries under evaluation: `pdf.js` (Mozilla, client-side), `PyMuPDF` (server-side)

### Analyzer Engine
The core logic of the project. Responsible for:
1. Parsing the PDF structure (text blocks, field annotations, layout grid)
2. Detecting form field types (inputs, checkboxes, dropdowns, dates, signatures)
3. Inferring multi-column layout and section boundaries
4. Mapping detected fields to SurveyJS question types
5. Generating a valid SurveyJS JSON schema

### SurveyJS Form Preview
- Uses **SurveyJS Form Library** (MIT) to render the generated JSON schema
- Allows the user to test the form before saving or deploying

### Survey Creator Editor *(optional)*
- Uses **SurveyJS Survey Creator** (commercial) to allow manual refinement via drag-and-drop
- Not required for the core conversion pipeline

### Backend / DB
- Stores JSON schemas and form responses
- Technology-agnostic (Node.js, Python, .NET — any backend works)
- AMOS™ integration: schemas stored in AMOS DB, responses appended to AMOS data tables

---

## SurveyJS Question Type Mapping

| PDF Field Type | SurveyJS Question Type |
|---|---|
| Text input (single line) | `text` |
| Text area (multi-line) | `comment` |
| Checkbox | `boolean` or `checkbox` |
| Radio group | `radiogroup` |
| Dropdown / Select | `dropdown` |
| Date field | `text` (inputType: date) |
| Number / Integer | `text` (inputType: number) |
| Signature | `signaturepad` |
| Image / Logo | `image` |
| Section header | `html` |
| Table / Matrix | `matrix` or `matrixdropdown` |

---

## Technology Stack (Proposed)

| Layer | Technology |
|---|---|
| PDF parsing | `pdf.js` (client-side) or `PyMuPDF` (server-side) |
| Schema generation | JavaScript / TypeScript |
| Form rendering | SurveyJS Form Library (jQuery wrapper) |
| Form builder UI | SurveyJS Survey Creator |
| Backend (optional) | Node.js / Express or Python / FastAPI |
| Database | PostgreSQL / MSSQL (AMOS-compatible) |
| BI output | Direct SQL tables from JSON responses |
