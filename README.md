# WebFormAnalyzer

A tool to analyze PDF forms and convert them into **SurveyJS-compatible JSON schemas** — ready to render, edit, and feed into any BI platform.

## Project Goal

AMOS™ (SpecTec fleet management software) currently uses **jQuery FormBuilder** for in-app form creation. While functional for simple use cases, it has significant limitations for production-grade forms:

- No native multi-column layout support
- Cannot embed images within form templates
- Data output is not natively structured for BI consumption

This project explores replacing jQuery FormBuilder with **SurveyJS** and builds a companion utility — **WebFormAnalyzer** — that converts existing PDF-based form templates into SurveyJS JSON schemas automatically.

## Why SurveyJS?

| Feature | jQuery FormBuilder | SurveyJS |
|---|---|---|
| Drag & drop builder | ✅ | ✅ |
| Multi-column layout | ❌ | ✅ |
| Embedded images | ❌ | ✅ |
| Conditional logic | Limited | ✅ Full GUI |
| JSON schema output | ❌ | ✅ |
| BI-ready structured data | ❌ | ✅ |
| Self-hosted | ✅ | ✅ |
| jQuery compatible | ✅ | ✅ (via wrapper) |
| GDPR / HIPAA compliant | N/A | ✅ |
| Commercial license needed | MIT | Creator only |

## Repository Structure

```
WebFormAnalyzer/
├── docs/                   # Project documentation
│   ├── architecture.md     # System architecture overview
│   ├── surveyjs-research.md# SurveyJS evaluation notes
│   └── roadmap.md          # Development roadmap
├── demo/                   # Demo application (Phase 2)
│   ├── pdf-analyzer/       # PDF upload + field extraction module
│   └── surveyjs-preview/   # SurveyJS form renderer + editor
├── samples/                # Sample PDF forms and output JSON schemas
│   ├── input/              # Source PDF templates
│   └── output/             # Generated SurveyJS JSON schemas
└── README.md
```

## Roadmap Summary

See [`docs/roadmap.md`](docs/roadmap.md) for the full plan.

| Phase | Goal | Status |
|---|---|---|
| 1 | Research & Evaluation | 🟡 In progress |
| 2 | Demo App (PDF → SurveyJS) | ⬜ Not started |
| 3 | AMOS Integration Design | ⬜ Not started |
| 4 | Production Deployment | ⬜ Not started |

## License

Maintained by SpecTec / Antonino Maione. See individual component licenses for third-party dependencies.
