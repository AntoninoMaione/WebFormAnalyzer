# WebFormAnalyzer — Development Roadmap

## Phase 1 — Research & Evaluation *(current)*

**Goal:** Validate the technical approach before building anything.

- [x] Evaluate SurveyJS as a replacement for jQuery FormBuilder
- [x] Define project structure and architecture
- [x] Document SurveyJS components, licensing, and integration path
- [ ] Evaluate PDF parsing libraries (`pdf.js` vs `PyMuPDF` vs `pdfminer`)
- [ ] Identify reference PDF form templates (AMOS inspection forms, checklists)
- [ ] Confirm SurveyJS commercial license model with SpecTec procurement

**Deliverable:** Architecture document + research notes (this repository)

---

## Phase 2 — Proof of Concept (Demo App)

**Goal:** Build a working end-to-end prototype in the browser.

### 2.1 — PDF Upload & Field Detection
- [ ] Implement PDF upload component (drag-and-drop)
- [ ] Integrate `pdf.js` for client-side PDF parsing
- [ ] Detect and extract form fields from PDF annotations
- [ ] Detect layout structure (columns, sections, headers)

### 2.2 — JSON Schema Generation
- [ ] Map detected fields to SurveyJS question types
- [ ] Generate a valid SurveyJS JSON schema automatically
- [ ] Handle multi-column panels in the schema
- [ ] Handle embedded images in the schema

### 2.3 — SurveyJS Preview & Edit
- [ ] Integrate SurveyJS Form Library (jQuery version) for live preview
- [ ] Integrate Survey Creator for manual schema refinement
- [ ] Export final JSON schema to file or clipboard

**Deliverable:** Single-page demo app (HTML/JS) in `demo/` folder

---

## Phase 3 — AMOS Integration Design

**Goal:** Define the integration path for AMOS™ production deployment.

- [ ] Map SurveyJS JSON schema storage to AMOS DB schema
- [ ] Design REST API endpoints for schema CRUD
- [ ] Design form response storage (flat table structure for BI)
- [ ] Define user roles: form designer vs. form user
- [ ] Pilot with 2–3 real AMOS form templates
- [ ] Performance and security review

**Deliverable:** Integration specification document

---

## Phase 4 — Production

**Goal:** Replace jQuery FormBuilder in AMOS™ with the SurveyJS-based solution.

- [ ] Deploy SurveyJS Form Library in AMOS frontend
- [ ] Deploy Survey Creator for admin users
- [ ] Migrate existing jQuery FormBuilder forms to SurveyJS JSON
- [ ] Connect response tables to BI dashboards
- [ ] User training and documentation

---

## Timeline (Indicative)

| Phase | Target |
|---|---|
| Phase 1 — Research | Q2 2026 |
| Phase 2 — Demo App | Q3 2026 |
| Phase 3 — Integration Design | Q3–Q4 2026 |
| Phase 4 — Production | Q4 2026 – Q1 2027 |
