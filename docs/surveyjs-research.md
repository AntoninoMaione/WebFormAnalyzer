# SurveyJS — Evaluation Notes

## Overview

SurveyJS is a family of open-source JavaScript libraries for building, rendering, and managing forms entirely within your own infrastructure. It is being evaluated as a replacement for jQuery FormBuilder within the AMOS™ platform.

**Official site:** https://surveyjs.io  
**GitHub:** https://github.com/surveyjs

---

## Component Breakdown

### 1. Survey Creator (Form Builder)
A self-hosted, no-code drag-and-drop form builder. Generates JSON schemas automatically. Used by administrators to design forms.

- Drag-and-drop interface
- CSS Theme Editor
- GUI for conditional logic and form branching
- Supports repeating sections, calculated fields, custom validators
- **License:** Commercial (per developer seat)

### 2. Form Library (Renderer)
Loads a JSON schema from the database and renders it as an interactive HTML form inside any JS application.

- MIT licensed — free for commercial use
- Supports React, Angular, Vue, Knockout, **jQuery** (via Knockout wrapper)
- Interacts with any backend via REST API

### 3. Dashboard
Visualizes collected form responses with interactive charts and tables. Useful for basic in-app analytics.

### 4. PDF Generator
Renders any SurveyJS form as a downloadable PDF (both editable and read-only).

---

## How It Works

```
[Survey Creator] → JSON schema saved to DB
        ↓
[Form Library]  → Loads schema, renders HTML form to end user
        ↓
[User submits]  → JSON response saved to DB
        ↓
[BI / Analytics] → Query DB directly (Power BI, Tableau, SQL, etc.)
```

SurveyJS never touches your data. All schemas and responses are stored on your own servers.

---

## Key Strengths for AMOS Use Case

### Multi-column layouts
SurveyJS supports panel-based layouts where fields can be arranged in 2, 3, or 4 columns — a native limitation in jQuery FormBuilder.

### Image embedding
Forms can include image elements, logo headers, and visual instructions — useful for technical inspection forms in maritime operations.

### BI-ready output
Each form submission is stored as a flat or nested JSON object, mappable to relational DB tables. Any BI tool can consume this directly.

### jQuery compatibility
The Form Library supports jQuery via a Knockout wrapper. Existing AMOS jQuery pages can embed SurveyJS forms with minimal refactoring.

### Self-hosted & GDPR compliant
No data leaves the customer's environment. Fully compatible with maritime enterprise security policies.

---

## Licensing Summary

| Component | License | Notes |
|---|---|---|
| Form Library | MIT | Free, including commercial use |
| Survey Creator | Commercial | Required for the drag-and-drop builder UI |
| Dashboard | Commercial | Optional analytics component |
| PDF Generator | Commercial | Optional |

For AMOS integration, at minimum the **Form Library (MIT)** is needed for rendering, and **Survey Creator (commercial)** for the in-app form design tool. Pricing is per developer seat.

---

## References

- https://surveyjs.io/try/jquery — jQuery integration demo
- https://surveyjs.io/open-source — Open-source overview
- https://surveyjs.io/features — Full feature list
- https://github.com/surveyjs/survey-library — Form Library GitHub
- https://github.com/surveyjs/survey-creator — Survey Creator GitHub
