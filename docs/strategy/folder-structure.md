## Folder Structure

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
│   ├── charter.md
│   ├── participation-agreement.md
│   ├── the-way-we-work.md
│   └── code-of-conduct.md
│
├── program/
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
├── docs/
│   ├── strategy/
│   │   ├── vision.md
│   │   ├── ecosystem-positioning.md
│   │   ├── folder-structure.md
│   │   └── historical-context.md
│   │
│   ├── ecosystem/
│   │   ├── oma-positioning.md
│   │   ├── madrid-positioning.md
│   │   ├── academia-perspectives.md
│   │   ├── vendor-perspectives.md
│   │   └── standards-landscape.md
│   │
│   └── contributors/
│       ├── organizations/
│       │   ├── madrid-digital-office.md
│       │   ├── smart-data-objects.md
│       │   └── oma.md
│       │
│       └── onboarding/
│           ├── getting-started.md
│           └── tooling-access.md
│
├── methodology/
│   ├── README.md
│   │
│   ├── operational-analysis/
│   │   ├── municipality-operational-reverse-engineering-methodology.md
│   │   ├── operational-requirement-decomposition.md
│   │   ├── semantic-analysis-guidelines.md
│   │   ├── interoperability-abstraction-methodology.md
│   │   └── contextual-metadata-analysis.md
│   │
│   ├── profile-development/
│   │   ├── profile-development-methodology.md
│   │   ├── profile-lifecycle.md
│   │   ├── profile-authoring-guidelines.md
│   │   ├── profile-review-process.md
│   │   └── profile-versioning-strategy.md
│   │
│   ├── interoperability-validation/
│   │   ├── validation-methodology.md
│   │   ├── interoperability-test-design.md
│   │   ├── semantic-validation-guidelines.md
│   │   └── operational-scenario-validation.md
│   │
│   ├── semantic-governance/
│   │   ├── semantic-governance-principles.md
│   │   ├── terminology-management.md
│   │   ├── provenance-and-context.md
│   │   └── interoperability-semantics-principles.md
│   │
│   └── templates/
│       ├── municipality-analysis-template.md
│       ├── semantic-analysis-template.md
│       ├── profile-template.md
│       └── validation-template.md
│
├── shared-models/
│   ├── README.md
│   │
│   ├── measurement/
│   ├── context/
│   ├── provenance/
│   ├── temporal/
│   ├── operational-zones/
│   ├── service-outcomes/
│   └── governance/
│
├── profiles/
│   ├── lighting/
│   │   ├── README.md
│   │   ├── use-cases/
│   │   ├── analysis/
│   │   ├── semantic-model/
│   │   ├── interoperability/
│   │   ├── validation/
│   │   ├── references/
│   │   └── releases/
│   │
│   ├── water/
│   │   ├── README.md
│   │   ├── use-cases/
│   │   ├── analysis/
│   │   ├── semantic-model/
│   │   ├── interoperability/
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
│   ├── meeting-minutes-template.md
│   ├── presentation-template.md
│   └── contribution-template.md
│
├── working/
│   ├── exploratory-analysis/
│   ├── brainstorming/
│   ├── temporary-discussions/
│   └── early-concepts/
│
└── archive/
    ├── deprecated-content/
    ├── obsolete-proposals/
    └── historical-records/
```
