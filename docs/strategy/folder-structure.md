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
│   │   ├── scope-and-objectives.md
│   │   ├── collaboration-model.md
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
│           ├── contributor-guide.md
│           ├── participation-process.md
│           └── tooling-access.md
│
├── profiles/
│   ├── lighting/
│   │   ├── profile.yml
│   │   ├── README.md
│   │   ├── use-cases/
│   │   ├── requirements/
│   │   ├── mappings/
│   │   ├── device-profiles/
│   │   ├── validation/
│   │   ├── test-cases/
│   │   ├── presentations/
│   │   ├── references/
│   │   ├── drafts/
│   │   └── approved/
│   │
│   └── water/
│       ├── profile.yml
│       ├── README.md
│       ├── use-cases/
│       ├── requirements/
│       ├── mappings/
│       ├── device-profiles/
│       ├── validation/
│       ├── test-cases/
│       ├── presentations/
│       ├── references/
│       ├── drafts/
│       └── approved/
│
├── templates/
│   ├── profile-template.md
│   ├── use-case-template.md
│   ├── meeting-minutes-template.md
│   ├── validation-report-template.md
│   └── mapping-template.md
│
├── working/
│   ├── exploratory-analysis/
│   ├── brainstorming/
│   ├── early-mappings/
│   └── temporary-discussions/
│
└── archive/
    ├── deprecated-content/
    ├── obsolete-proposals/
    └── historical-records/
```
