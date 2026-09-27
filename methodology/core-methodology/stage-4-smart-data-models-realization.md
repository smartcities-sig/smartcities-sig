---
title: Stage 4 — Smart Data Models Realization
description: How the Smart Cities SIG brings independent ecosystem assessment results together into Smart Data Models that Digital Twins can consume.
layout: doc
---

# {{ $doc.title }}

## Introduction

The purpose of Stage 4 is to bring the ecosystem assessment results produced during Stage 3 together into Smart Data Models, so that the [semantic capabilities](/methodology/core-methodology/stage-2-semantic-capabilities.md) become concretely realizable and consumable by Digital Twins.

At this stage:
- operational meaning has already been captured,
- the semantic capabilities have already been defined,
- semantic distinctions have already been analyzed,
- and ecosystem participants have already assessed their own interoperability assets.

Each of those assessments is produced independently, from the vantage point of a single organization or ecosystem.

Stage 4 is the stage where those independent results are reconciled into a single coherent realization picture.

This stage intentionally avoids:
- becoming a platform specification,
- becoming a schema design exercise,
- and prescribing a single implementation technology.

The detailed definition of this stage is still under development by the Smart Cities SIG. This document is a draft overview intended to support that discussion.

**Input:** the semantic capabilities from [Stage 2](/methodology/core-methodology/stage-2-semantic-capabilities.md) and the ecosystem assessment reports from [Stage 3](/methodology/core-methodology/stage-3-standards-mapping.md).
**Output:** converged Smart Data Model realization, with residual gaps recorded.

For the methodology as a whole, see the [Methodology Overview](/methodology/core-methodology/methodology-overview.md).

---

# Purpose of Stage 4

Stage 4 exists to answer the following questions:

- How do assessment results from different organizations converge into a coherent semantic picture?
- Where should each semantic capability be realized?
- What remains unrepresented once every ecosystem contribution has been accounted for?
- How is operational meaning preserved through realization?
- How does the result remain reusable across municipalities and domains?
- How is the result made consumable by Digital Twins?

This stage progressively transforms:
- independent ecosystem assessment results

into:
- converged Smart Data Model realization.

---

# Why Convergence Matters

No single organization assesses the whole interoperability picture.

Device standards organizations assess what their objects can carry, semantic model ecosystems assess what their structures can represent, and platform contributors assess what they can consume.

Every one of these assessments may be internally complete while remaining partial with respect to the municipality operational question.

Without a convergence stage:
- assessments remain parallel and unreconciled,
- semantic gaps remain invisible because no participant owns them,
- the same capability may be realized inconsistently by different contributors,
- and Digital Twin consumption remains unreliable despite correct individual contributions.

Convergence is therefore not an administrative step. It is where interoperability actually becomes observable.

---

# What Stage 4 Operates On

Stage 4 does not begin from municipality material.

Stage 4 operates on:
- the [semantic capabilities](/methodology/core-methodology/stage-2-semantic-capabilities.md) defined in Stage 2,
- the ecosystem assessment results produced during Stage 3,
- the semantic gaps and responsibilities recorded in those assessments,
- and the contextual and provenance requirements preserved from Stage 1.

These inputs are produced independently, and may arrive in different states of completeness or with differing conclusions about the same capability.

Stage 4 therefore treats incompleteness and disagreement as normal working conditions rather than as blocking issues.

---

# Smart Data Models as the Convergence Point

Smart Data Models are one of the primary mechanisms through which operational meaning, contextual metadata, provenance information, and semantic consistency are conveyed into Digital Twin ecosystems. They are treated not as isolated technical schemas but as semantically enriched structures that preserve operational intent across ecosystem boundaries.

Stage 4 treats Smart Data Models as the structure in which convergence is expressed.

Smart Data Models are suited to this role because they carry:
- telemetry together with the context required to interpret it,
- provenance describing how information was obtained,
- relationships linking entities across domains,
- and structures that Digital Twin platforms already consume.

A Smart Data Model is therefore not the endpoint of the methodology. It is where contributions from several ecosystems are assembled into something a Digital Twin can use without losing the operational meaning captured during Stage 1.

---

# Semantic Assembly for Smart City Digital Twins

<img width="1672" height="941" alt="image" src="https://github.com/user-attachments/assets/bf2e0d31-2550-4abc-92ad-9cf195f6d318" />

*Figure — Collaborative Semantic Assembly for Smart City Digital Twins*

Operational pain points identified by municipalities drive the collaborative standards gap analysis of Stage 3, across organizations such as the Open Mobile Alliance, the FIWARE Foundation, academia, and other standards ecosystems. Stage 4 assembles the results.

Reusable atomic semantic components — such as OMA Objects and Resources — are evaluated, harmonized, and assembled into contextual Smart Data Models. These combine telemetry, metadata, operational context, and semantic relationships into interoperable structures that can be reused across smart city domains including public lighting, water management, mobility, environment, and energy.

The outcome is a set of contextualized Smart Data Models consumable by Digital Twins.

---

# Mapping to Smart Data Models and Ontologies

After the Stage 3 assessments, each Service Domain is mapped onto the semantic models that will carry it into Digital Twins. The [lighting vs irrigation comparison](/profiles/lighting-vs-irrigation-comparison.md) shows a worked example of both mappings.

## Smart Data Models

Pick the closest NGSI entities and properties for the service:
- device and entity types,
- outcome-related attributes (the ones the municipality really cares about),
- and operational and cost attributes (supporting).

Add extensions only when the core model does not cover the key outcome.

Questions to answer:
- Which existing Smart Data Models best fit this service?
- Which properties represent outcome measurements, operational signals, and cost, energy, or resource consumption?

## SAREF and Other Ontologies

Use SAREF's measurement pattern:
- `saref:Device`, `saref:Sensor`, `saref:Actuator`,
- and `saref:Measurement` that `saref:relatesToProperty` some domain property.

Choose domain vocabularies such as SAREF4CITY, SAREF4AGRI, or SAREF4ENVI. Further ontologies are still to be considered.

Questions to answer:
- What are the domain properties (for example, illuminance, soil moisture, fill level, occupancy) this service observes or acts upon?
- How are device roles, measurements (value, unit, time, location), methods, and quality represented consistently across domains?

---

# Convergence Activities

The following activities are expected to characterize Stage 4 work. Their detailed definition remains open.

## Reconciling Assessment Results

Assessment results from different ecosystems are compared for each semantic capability, so that agreement, partial coverage, and disagreement become explicit.

## Assigning Realization Responsibility

Each semantic capability is associated with the ecosystem or ecosystems best positioned to realize it, recognizing that some capabilities may be realized jointly.

## Identifying Residual Gaps

Capabilities that no assessed contribution covers are recorded as residual gaps, together with the operational consequence of leaving them unrealized.

## Expressing the Result as Smart Data Models

The reconciled picture is expressed as Smart Data Model structures, including the contextual and provenance information required for correct interpretation.

## Preserving Traceability

Each realization decision remains traceable back through the semantic capabilities to the municipality operational meaning from which it originated.

---

# Where the Work Takes Place

This document defines what Stage 4 is. It does not contain the results of Stage 4.

The convergence work itself is recorded elsewhere in this repository:
- the per-ecosystem assessment reports, listed in the [Ecosystem Assessments](/methodology/assessment-frameworks/semantic-capability-assessment.md#ecosystem-assessments) table,
- the concrete OMA-to-Smart-Data-Models mappings in each Service Profile (for example, [Public Lighting](/profiles/lighting/mappings/oma-smart-data-models-mapping-lighting.md)),
- and the domain walkthroughs that demonstrate the methodology end to end.

This separation is deliberate. The stage documents describe the methodology and remain stable, while assessment and mapping material evolves continuously as ecosystem contributions arrive.

---

# Open Questions for SIG Discussion

The following questions remain open and are expected to shape the final definition of this stage.

- Is the unit of convergence the semantic capability, the Service Profile, or both?
- What constitutes sufficient coverage for a capability to be considered realized?
- How are conflicting assessment conclusions reconciled, and by whom?
- How are residual gaps routed back to the originating standards organization?
- What validation confirms that operational meaning survived realization?
- How are converged results maintained as ecosystem assessments are updated?

---

# Common Stage 4 Pitfalls

Several risks may appear during Smart Data Model realization activities.

## Schema-First Convergence
Beginning from model structure rather than from assessed semantic capability may reintroduce the premature standards thinking that earlier stages avoided (see [Meaning Before Standards](/methodology/core-methodology/methodology-overview.md#meaning-before-standards)).

## Losing Traceability to Operational Meaning
A realization that cannot be traced back to a municipality operational objective may be technically valid and operationally irrelevant.

## Treating Absence of Coverage as Absence of Need
A capability that no ecosystem currently realizes remains a real municipality requirement and should be recorded as a gap rather than silently dropped.

## Single-Ecosystem Convergence
Converging around the assets of one ecosystem reduces the result to that ecosystem's existing coverage.

## Premature Closure
Declaring convergence complete before assessment results are sufficiently mature may embed provisional conclusions into reusable models.

---

# Public Street Lighting Example

The [Public Street Lighting walkthrough](/profiles/lighting/public-lighting-walkthrough.md) does not yet have a Stage 4 section. Its Stage 3 section, the [OMA assessment](/methodology/assessment-frameworks/oma-capability-assessment.md), the [Smart Data Models assessment](/methodology/assessment-frameworks/sdm-capability-assessment.md), and the [lighting mapping](/profiles/lighting/mappings/oma-smart-data-models-mapping-lighting.md) provide the inputs that Stage 4 convergence would work on.

For Public Street Lighting, Stage 4 would include:
- reconciling what device-level objects report against what contextual models must carry,
- determining where illumination service outcome is realized as distinct from infrastructure output,
- determining where environmental context such as fog, vegetation, and shadows is carried,
- recording provenance so that inferred and directly measured values remain distinguishable,
- and identifying which capabilities remain unrealized by any assessed contribution.

Smart Data Models in the street lighting domain, such as those describing streetlight assets and their operational context, are the natural realization target. The specific reference models are indicative and remain pending confirmation by the SIG.

---

# Relationship to Previous Stages

Without the assessment results produced during Stage 3, convergence has nothing to reconcile. Without the operational meaning and semantic capabilities preserved during Stages 1 and 2, convergence loses the traceability that makes realization verifiable.

The outputs of Stage 4 become the inputs to Digital Twin consumption. For how the four stages fit together, see the [Methodology Overview](/methodology/core-methodology/methodology-overview.md#core-methodology).
