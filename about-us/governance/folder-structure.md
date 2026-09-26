---
title: Folder Structure
description:
layout: web
---

# {{ $doc.title }}

This document describes the target repository structure for the Smart Cities SIG initiative.

The structure is intended to support:
- governance and program coordination,
- service Profile development,
- ecosystem collaboration,
- reusable documentation,
- and future website generation using a GitHub-native content model.

The repository is designed to centralize governance, program operations, technical work, meeting records, presentations, and supporting documentation in a single location.

The structure below represents the intended long-term organization of the repository. Folders and subfolders will be created incrementally and only as needed based on the evolution of the project, profiles, contributors, and collaboration requirements.

This approach keeps the repository lightweight during the early stages of the initiative while providing a scalable structure for future growth.

Within `methodology/` and `profiles/`, each kind of content has a single home:
- the methodology narrative lives in `core-methodology/methodology-overview.md`,
- semantic capability definitions live in `core-methodology/stage-2-semantic-capabilities.md`,
- assessment questions live in `assessment-frameworks/semantic-capability-assessment.md`,
- assessment results live in each ecosystem's assessment report,
- and service-specific material (walkthroughs, municipality operational questions, examples) lives in the Service Profile under `profiles/`.

New files should link to these homes rather than restate their content.

```text
smartcities-sig/
│
├── LICENSE
├── site.config.yml
│
├── about-us/
|   ├── about-us.md
|   ├── foundation/
|   │   ├── README.md
|   │   ├── vision.md
|   │   ├── historical-context.md
|   │   ├── ecosystem-positioning.md
|   │   ├── stakeholder-analysis.md
|   │   └── standards-landscape.md
|   |
|   └──governance/
|       ├── README.md
|       ├── charter.md
|       ├── participation-rules.md
|       ├── code-of-conduct.md
|       ├── the-way-we-work.md
|       └── folder-structure.md
|
|── community/
│   ├── CONTRIBUTING.md
│   ├── getting-started.md
│   └── participant-organizations.md
│
|── methodology/
│   ├── README.md
|   ├── core-methodology/
|   |   ├── methodology-overview.md
|   |   ├── stage-1-operational-meaning.md
|   │   ├── stage-2-semantic-capabilities.md
|   │   ├── stage-3-standards-mapping.md
|   │   └── methodology-worksheet.md
|   │
|   └── assessment-frameworks/
|       ├── README.md
|       ├── semantic-capability-assessment.md
|       ├── oma-capability-assessment.md
|       ├── oma-registry-capability-classification.md
|       └── sdm-capability-assessment.md
|
|── news/
|   ├── announcements/
|   └── outreach/
|       ├── workshops/
|       └── event-materials/
│
├── shared-models/
│   ├── measurement/
│   ├── context/
│   ├── provenance/
│   ├── temporal/
│   ├── operational-zones/
│   └── service-outcomes/
|
├── profiles/
│   ├── README.md
│   ├── lighting-vs-irrigation-comparison.md
│   ├── lighting/
|   │   ├── README.md
│   │   ├── public-lighting-walkthrough.md
│   │   ├── municipality-questions.md
│   │   ├── use-cases/
│   │   ├── mappings/
|   |   |   └── oma-smart-data-models-mapping-lighting.md
│   │   ├── semantic-model/
│   │   ├── interoperability/
|   │   ├── digital-twin/
|   |   |   ├── digital-twin-view.md
|   |   |   ├── smart-data-models-requirements.md
|   |   |   └── consumption-scenarios.md
│   │   ├── validation/
│   │   ├── references/
│   │   └── releases/
│   │
│   ├── water/
|   │   ├── README.md
│   │   ├── public-watering-walkthrough.md
│   │   ├── municipality-questions.md
│   │   ├── use-cases/
│   │   ├── mappings/
|   |   |   └── oma-smart-data-models-mapping-water.md
│   │   ├── semantic-model/
│   │   ├── interoperability/
|   │   ├── digital-twin/
|   |   |   ├── digital-twin-view.md
|   |   |   ├── smart-data-models-requirements.md
|   |   |   └── consumption-scenarios.md
│   │   ├── validation/
│   │   ├── references/
│   │   └── releases/
│   │
│   ├── cross-domain/
│   |    ├── shared-observations/
│   |    ├── reusable-patterns/
│   |    ├── common-semantics/
│   |    └── interoperability-gaps/
|   |
|   ├── shared-models/
|   │   ├── measurement/
|   │   ├── context/
|   │   ├── provenance/
|   │   ├── temporal/
|   │   ├── operational-zones/
│   └── service-outcomes/
|
├── program/
│   ├── README.md
│   ├── roadmap/
│   │   └──  release-planning.md
│   │
│   └── reports/
│       ├── progress-reports/
│       ├── retrospectives/
│       └── lessons-learned/
|
├── public/
│   └── images/
│       └──  image.png
│
|
├── meetings/
│   ├── minutes/
│   │   └── 2026/
│   └── presentations/
│
├── templates/
│   ├── README.md
│   ├── meeting-minutes-template.md
│   ├── presentation-template.md
│   └── contribution-template.md
│
├── working/
│   ├── README.md
│   ├── exploratory-analysis/
│   ├── brainstorming/
│   ├── temporary-discussions/
│   └── early-concepts/
│
└── archive/
    ├── README.md
    ├── deprecated-content/
    ├── obsolete-proposals/
    └── historical-records/
```
