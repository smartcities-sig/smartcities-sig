---
title: Folder Structure
description:
layout: web
---

# {{ $doc.title }}

This document describes the target repository structure for the Smart Cities SIG initiative.

The structure is intended to support:
- governance and program coordination,
- technical profile development,
- ecosystem collaboration,
- reusable documentation,
- and future website generation using a GitHub-native content model.

The repository is designed to centralize governance, program operations, technical work, meeting records, presentations, and supporting documentation in a single location.

The structure below represents the intended long-term organization of the repository. Folders and subfolders will be created incrementally and only as needed based on the evolution of the project, profiles, contributors, and collaboration requirements.

This approach keeps the repository lightweight during the early stages of the initiative while providing a scalable structure for future growth.

```text
smartcities-sig/
│
├── README.md
├── LICENSE
├── CONTRIBUTING.md
├── site.config.yml
│
├── governance/
│   ├── README.md
│   ├── charter.md
│   ├── participation-agreement.md
│   ├── code-of-conduct.md
│   └── the-way-we-work.md
│
├── program/
│   ├── README.md
│   ├── roadmap/
│   │   └──  release-planning.md
│   │
│   ├── meetings/
│   │   ├── minutes/
│   │   │   └── 2026/
│   │   └── presentations/
│   │
│   ├── communications/
│   │   ├── announcements/
│   │   ├── outreach/
│   │   ├── workshops/
│   │   └── event-materials/
│   │
│   └── reports/
│       ├── progress-reports/
│       ├── retrospectives/
│       └── lessons-learned/
│
├── foundation/
│   ├── README.md
│   ├── vision.md
│   ├── historical-context.md
│   ├── ecosystem-positioning.md
│   ├── stakeholder-analysis.md
│   └── standards-landscape.md
│   
|── community/
│   ├── README.md
│   └── onboarding/
│   |   ├── getting-started.md
│   |   └── tooling-access.md
|   |
│   └── participant-organizations/
│
|── methodology/
│   ├── README.md
|   ├── core-methodology/
|   |   ├── methodology-overview.md
|   |   ├── stage-1-operational-meaning.md
|   │   ├── stage-2-reusable-abstractions.md
|   │   └── stage-3-standards-mapping.md
|   │
|   ├── supporting-concepts/
|   │   ├── semantic-distinctions.md
|   │   ├── context-and-provenance.md
|   │   ├── inferred-vs-measured-values.md
|   │   └── interoperability-validation-thinking.md
|   │
|   ├── digital-twin-integration/
|   │   ├── digital-twin-consumption-model.md
|   │   └── smart-data-models-as-context-carriers.md
|   └── examples/
|       ├── lighting/
|       └── water/
│
├── shared-models/
│   ├── measurement/
│   ├── context/
│   ├── provenance/
│   ├── temporal/
│   ├── operational-zones/
│   └── service-outcomes/
│
├── domains/
│   ├── README.md
│   ├── lighting/
|   │   ├── README.md
│   │   ├── public-lighting-walkthrough.md
│   │   ├── use-cases/
│   │   ├── analysis/
│   │   ├── semantic-model/
│   │   ├── interoperability/
|   │   ├── digital-twin/
|   |   |   ├── digital-twin-view.md
|   |   |   ├── smart-data-object-requirements.md
|   |   |   └── consumption-scenarios.md
│   │   ├── validation/
│   │   ├── references/
│   │   └── releases/
│   │
│   ├── water/
|   │   ├── README.md
│   │   ├── public-watering-walkthrough.md
│   │   ├── use-cases/
│   │   ├── analysis/
│   │   ├── semantic-model/
│   │   ├── interoperability/
|   │   ├── digital-twin/
|   |   |   ├── digital-twin-view.md
|   |   |   ├── smart-data-object-requirements.md
|   |   |   └── consumption-scenarios.md
│   │   ├── validation/
│   │   ├── references/
│   │   └── releases/
│   │
│   └── cross-domain/
│       ├── shared-observations/
│       ├── reusable-patterns/
│       ├── common-semantics/
│       └── interoperability-gaps/
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
│   ├── README.md
    ├── deprecated-content/
    ├── obsolete-proposals/
    └── historical-records/
```
