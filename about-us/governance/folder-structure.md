---
title: Folder Structure
description:
layout: web
---

# {{ $doc.title }}

This document describes the current structure of the Smart Cities SIG repository and the few additions that are planned.

Folders are created only when there is content for them. Planned additions are listed separately below the tree, and each one is tied to a stage of the [methodology](/methodology/core-methodology/methodology-overview.md) or to the [release plan](/program/roadmap/release-planning.md).

Within `methodology/` and `profiles/`, each kind of content has a single home:
- the methodology narrative lives in `core-methodology/methodology-overview.md`,
- semantic capability definitions live in `core-methodology/stage-2-semantic-capabilities.md`,
- assessment questions live in `assessment-frameworks/semantic-capability-assessment.md`,
- assessment results live in each ecosystem's assessment report,
- and service-specific material (walkthroughs, municipality operational questions, examples) lives in the Service Profile under `profiles/`.

New files should link to these homes rather than restate their content.

## Current structure

```text
smartcities-sig/
│
├── LICENSE
│
├── about-us/                      Why the SIG exists and how it is governed
│   ├── about-us.md
│   ├── foundation/
│   │   ├── vision.md
│   │   └── ecosystem-positioning.md
│   └── governance/
│       ├── charter.md
│       ├── participation-rules.md
│       ├── code-of-conduct.md
│       ├── the-way-we-work.md
│       └── folder-structure.md
│
├── community/                     How to join and contribute
│   ├── CONTRIBUTING.md
│   ├── getting-started.md
│   └── participant-organizations.md
│
├── methodology/                   How the work is done
│   ├── core-methodology/          The four stages
│   │   ├── methodology-overview.md
│   │   ├── stage-1-operational-meaning.md
│   │   ├── stage-2-semantic-capabilities.md
│   │   ├── stage-3-standards-mapping.md
│   │   ├── stage-4-smart-data-models-realization.md
│   │   └── methodology-worksheet.md
│   └── assessment-frameworks/     Stage 3: the method and its results
│       ├── semantic-capability-assessment.md      (method)
│       ├── oma-capability-assessment.md           (results)
│       ├── oma-registry-capability-classification.md  (results, appendix)
│       └── sdm-capability-assessment.md           (results)
│
├── profiles/                      The methodology applied to each Service Domain
│   ├── lighting-vs-irrigation-comparison.md
│   ├── lighting/
│   │   ├── public-lighting-walkthrough.md
│   │   ├── municipality-questions.md
│   │   └── mappings/
│   │       └── oma-smart-data-models-mapping-lighting.md
│   └── water/
│       ├── public-watering-walkthrough.md
│       ├── municipality-questions.md
│       └── mappings/
│           └── oma-smart-data-models-mapping-water.md
│
├── program/                       When: phases, milestones, status
│   └── roadmap/
│       ├── release-planning.md
│       └── Key-Milestones.md
│
├── news/                          Announcements and articles
│   ├── news.md
│   ├── social-media.md
│   └── articles/
│
├── publications/                  Published releases
│   └── v1_0/
│
└── public/                        Images and embedded pages
    ├── images/
    └── iframe/                    Training lessons on the semantic capabilities
```

## Planned additions

| Addition | Purpose | When |
|---|---|---|
| `profiles/<domain>/smart-city-profile.md` | The Smart City Profile for each Service Domain, the Stage 4 deliverable, started from the domain's OMA – Smart Data Models mapping | Phase 5 |
| `profiles/<domain>/validation/` | Proof of Concept results for each Service Domain | Phase 6 |
| `profiles/<new-domain>/` | A new Service Domain, with the same files as lighting and water | When the group adds a domain |

Content that would restate the semantic capabilities, such as shared measurement, context, provenance or temporal models, belongs in [Stage 2](/methodology/core-methodology/stage-2-semantic-capabilities.md), not in separate folders.
