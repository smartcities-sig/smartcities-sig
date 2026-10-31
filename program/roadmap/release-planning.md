---
title: Release Planning
description:
layout: web
---

# {{ $doc.title }}

This document defines the high-level execution roadmap, milestones, and expected deliverables for the Smart Cities SIG PoC initiative between May 2026 and the Proof of Concept phase in 2027. Phases 2, 3 and 5 follow the [four stages of the methodology](/methodology/core-methodology/methodology-overview.md); dates after November 2026 are indicative until the group agrees them.

The purpose of this plan is to provide participants, contributors, and future stakeholders with a clear understanding of:
- the planned phases of execution,
- major objectives and deliverables,
- expected validation milestones,
- and the timeline leading to the Smart City Expo World Congress 2026 showcase.

The roadmap is intentionally lightweight and iterative, reflecting the Proof of Concept nature of the initiative while maintaining focus on interoperability, reusable outputs, and ecosystem collaboration.

```mermaid
gantt
    title Smart Cities SIG Timeline and Expected Milestones
    dateFormat  YYYY-MM-DD
    axisFormat  %b %Y

    section Phase 1 — Initiative Foundation
    SIG operational setup                         :p1a, 2026-05-01, 2026-06-30
    Participation rules                          :p1b, 2026-05-01, 2026-06-30
    Governance model                             :p1c, 2026-05-01, 2026-06-30
    Communication infrastructure                 :p1d, 2026-05-01, 2026-06-30
    GitHub setup                                 :p1e, 2026-05-01, 2026-06-30
    Community engagement                         :p1f, 2026-05-15, 2026-06-30
    Select initial municipal domains             :p1g, 2026-06-01, 2026-06-30

    section Phase 2 — Operational Semantics Engineering (Stages 1–2)
    Municipal operational needs capture          :p2a, 2026-06-01, 2026-08-31
    Operational semantics definition             :p2b, 2026-06-15, 2026-08-31
    Semantic capability identification           :p2c, 2026-06-15, 2026-08-31
    Reusable semantic capability model            :p2d, 2026-06-15, 2026-08-31
    Second domain assessment kickoff              :milestone, p2e, 2026-08-31, 0d

    section Phase 3 — Standards Capability Assessment (Stage 3)
    Public Lighting domain assessment             :p3a, 2026-08-01, 2026-10-31
    Assessment methodology validation             :p3b, 2026-08-01, 2026-10-31
    Water and Irrigation domain assessment        :p3c, 2026-08-15, 2026-10-31
    OMA semantic capability assessment            :p3d, 2026-08-15, 2026-10-31
    Smart Data Models assessment                  :p3d, 2026-08-15, 2026-10-31
    Cross-organization capability assessment      :p3d, 2026-08-15, 2026-10-31
    Gap analysis and standards recommendations    :p3e, 2026-10-01, 2026-10-31

    section Phase 4 — Knowledge Sharing and Community Adoption
    Semantic capabilities and municipality questions :p4a, 2026-10-16, 2026-10-31
    OMA and Smart Data Models assessment reports  :p4b, 2026-10-16, 2026-10-31
    Assessment findings and lessons learned       :p4c, 2026-10-16, 2026-10-31
    Future domains and community roadmap           :p4d, 2026-11-01, 2026-11-30
    Smart City Expo World Congress                 :milestone, p4e, 2026-11-05, 0d

    section Phase 5 — Smart Data Models Realization (Stage 4)
    Public Lighting Smart City Profile            :p5a, 2026-11-15, 2027-02-28
    Water and Irrigation Smart City Profile       :p5b, 2026-12-01, 2027-03-31

    section Phase 6 — Proof of Concept Validation
    Proof of Concept deployments                  :p6a, 2027-03-01, 2027-06-30
```

### Phase Summary and Key Milestones

<table>
  <caption><strong>Phase Summary and Key Milestones</strong></caption>
  <thead>
    <tr>
      <th>Phase</th>
      <th>Timeline</th>
      <th>Main Objective</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Phase 1 — Initiative Foundation</td>
      <td>May–June 2026</td>
      <td>Establish the governance, participation model, collaboration infrastructure, community, and initial municipal domains for the Smart Cities SIG.</td>
    </tr>
    <tr>
      <td>Phase 2 — Operational Semantics Engineering</td>
      <td>June–August 2026</td>
      <td>Capture municipal operational needs, define their operational semantics, and organize them into reusable semantic capabilities.</td>
    </tr>
    <tr>
      <td>Phase 3 — Standards Capability Assessment</td>
      <td>August–October 2026</td>
      <td>Apply and validate the methodology through domain and cross-standard assessments, identify interoperability gaps, and formulate recommendations for standards organizations.</td>
    </tr>
    <tr>
      <td>Phase 4 — Knowledge Sharing and Community Adoption</td>
      <td>October–November 2026</td>
      <td>Publish the semantic capabilities, the municipality questions, the OMA and Smart Data Models assessment reports, findings, and recommendations, and present the initiative at Smart City Expo World Congress.</td>
    </tr>
    <tr>
      <td>Phase 5 — Smart Data Models Realization</td>
      <td>November 2026–Q1 2027 (indicative)</td>
      <td>Consolidate the Stage 3 results into a Smart City Profile for each Service Domain, checked against the Digital Twin questions, with residual gaps recorded.</td>
    </tr>
    <tr>
      <td>Phase 6 — Proof of Concept Validation</td>
      <td>2027 (indicative)</td>
      <td>Validate the Smart City Profiles in real deployments and feed the lessons back into Stage 1.</td>
    </tr>
  </tbody>
</table>

## Status (31 October 2026)

What has been built so far and what is still missing, stage by stage. This table is updated as the work progresses.

| Stage | Built so far | Still missing |
|---|---|---|
| 1 — Operational Meaning | [Stage 1 method](/methodology/core-methodology/stage-1-operational-meaning.md) and [worksheet](/methodology/core-methodology/methodology-worksheet.md); Stage 1 sections in the [lighting](/profiles/lighting/public-lighting-walkthrough.md) and [water](/profiles/water/public-watering-walkthrough.md) walkthroughs; Madrid workshops held | User stories and entity sketches in the walkthroughs, from the Madrid workshop output; the user-story pattern |
| 2 — Semantic Capabilities | The [14 semantic capabilities](/methodology/core-methodology/stage-2-semantic-capabilities.md) in 4 categories; municipality questions for [lighting](/profiles/lighting/municipality-questions.md) and [water](/profiles/water/municipality-questions.md) | The group decision on how Operational Semantics applies to the entity sketch |
| 3 — Standards & Ecosystem Mapping | The [assessment framework](/methodology/assessment-frameworks/semantic-capability-assessment.md); the [OMA assessment](/methodology/assessment-frameworks/oma-capability-assessment.md) and [registry classification](/methodology/assessment-frameworks/oma-registry-capability-classification.md); the [Smart Data Models assessment](/methodology/assessment-frameworks/sdm-capability-assessment.md) | A Smart Data Models assessment as detailed as the OMA one; assessments of other standards organizations |
| 4 — Smart Data Models Realization | The [Stage 4 method](/methodology/core-methodology/stage-4-smart-data-models-realization.md) (draft); early OMA – Smart Data Models mappings for [lighting](/profiles/lighting/mappings/oma-smart-data-models-mapping-lighting.md) and [water](/profiles/water/mappings/oma-smart-data-models-mapping-water.md) | Answers to the Stage 4 open questions; the Smart City Profile for each Service Domain |
| Proof of Concept | — | Everything: planned for Phase 6 |
