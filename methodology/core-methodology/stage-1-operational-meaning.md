---
title: Stage 1 — Operational Meaning
description: How the Smart Cities SIG captures what a municipality is actually trying to achieve before any standards are considered.
layout: doc
---

# {{ $doc.title }}

## Introduction

Stage 1 captures the real operational meaning behind municipality requirements, in the municipality's own terms. It applies the methodology's [Meaning Before Standards](/methodology/core-methodology/methodology-overview.md#meaning-before-standards) principle: no standards mapping, schema design, or architecture discussion happens until the operational intent is understood.

Municipality operational documents often contain:
- implicit assumptions,
- mixed technical and operational concepts,
- local terminology,
- incomplete contextual information,
- and operational concerns that are not immediately visible as interoperability requirements.

**Input:** municipality operational material, interviews, and workshops.
**Output:** user stories, an entity sketch, operational objectives, operational pain points, semantic distinctions, contextual dependencies, and interoperability-relevant observations — the input to [Stage 2 — Semantic Capabilities](/methodology/core-methodology/stage-2-semantic-capabilities.md).

For the methodology as a whole, see the [Methodology Overview](/methodology/core-methodology/methodology-overview.md). For a fill-in template covering this stage, see the [Methodology Worksheet](/methodology/core-methodology/methodology-worksheet.md).

---

# Purpose of Stage 1

Stage 1 exists to answer the following questions:

- What is the municipality actually trying to achieve?
- Who needs to do what, under which conditions, and why?
- Which things does the municipality talk about, and what does it say about them?
- What operational problem is being solved?
- What do the measurements and operational concepts really mean?
- What assumptions are implicitly present?
- What contextual information affects interpretation?
- What interoperability risks are already visible?

Municipalities do not usually describe problems using interoperability terminology. They describe operational frustrations, service objectives, maintenance realities, environmental conditions, accountability concerns, performance expectations, and infrastructure limitations. Stage 1 turns that material into operational understanding without losing its meaning.

---

# Typical Municipality Operational Inputs

Stage 1 may analyze different forms of municipality operational material, including:

- operational use cases,
- reports,
- specifications,
- deployment documentation,
- procurement material,
- presentations,
- maintenance observations,
- operational procedures,
- or workshop discussions.

The material may contain measurements, environmental conditions, operational constraints, device information, contextual metadata, and operational expectations. It may also be incomplete, inconsistent, multilingual, or semantically ambiguous.

---

# User Stories

Stage 1 starts by asking the municipality's representatives to describe, in their own words, the problems they want to solve and what a solution would let them do. Each need is written down as a **user story** that follows a fixed pattern, so that the people involved, the actions, the conditions, and the purpose can be picked out of it.

The SIG has not yet fixed the pattern. Two forms are being tested in municipality workshops:

- third person: *<type of user> want to <action> under <conditions> so that <they can achieve a benefit or value>*,
- first person, in the Agile style: *As a <type of user>, I want to <action> when <conditions>, so that <I can achieve a benefit or value>*.

For example: *Night-shift maintenance crews want to see which streetlights on their route fall below the minimum illuminance, under fog or heavy rain, so that they can repair first where pedestrians are at risk.*

Good user stories are:
- specific, measurable, achievable, relevant, and testable,
- written in the municipality's language, not in the language of a standard or a device,
- and as many and as fine-grained as the municipality can give.

The benefit a story ends with usually names the [Service Outcome](/methodology/core-methodology/stage-2-semantic-capabilities.md#service-outcome) the municipality cares about.

---

# Entity Sketch

Once enough user stories are collected, they are analysed systematically to identify:
- the **types of entities** the municipality talks about, such as a streetlight, a street segment, or a park zone,
- and, for each entity type:
  - the **properties** that characterize it,
  - the **actions** invoked on it or triggered by it,
  - and the **events** it emits.

The result is an **entity sketch**: a structured summary of what the stories say, still in the municipality's words. It is not a data model, and it does not use the names of any standard. Actions and events are recorded even though not every ecosystem can represent them yet; how they are represented is decided in [Stage 4](/methodology/core-methodology/stage-4-smart-data-models-realization.md#open-questions-for-sig-discussion).

[Stage 2](/methodology/core-methodology/stage-2-semantic-capabilities.md#classifying-observations) examines each property of the sketch that can be observed.

---

# Returning to the Municipality

Stage 1 is revisited as the later stages progress. Stage 2 may find a property that cannot be observed as described, and Stage 3 may find properties or needs the municipality did not mention. These come back to Stage 1 as questions for the municipality, and the user stories and the entity sketch are updated with its answers. See [how the stages fit together](/methodology/core-methodology/methodology-overview.md#core-methodology).

---

# Key Operational Questions

The following questions guide the Stage 1 analysis process.

## Operational Objectives
- What service is the municipality trying to provide?
- What operational outcome matters?
- What defines operational success?

## Operational Pain Points
- What operational difficulties are visible?
- What inconsistencies exist?
- What information is currently unreliable or difficult to compare?

## Measurements and Meaning
- What measurements are being described?
- What do these measurements actually represent operationally?
- Are the measurements directly measured or inferred?

## Contextual Dependencies
- What environmental or operational conditions affect interpretation?
- What contextual information is required to correctly understand the data?

## Operational Scope
- Is the information local, aggregated, inferred, or distributed?
- What physical or operational area does the information represent?

---

# Semantic Distinction Discovery

One of the most important activities in Stage 1 is identifying semantic distinctions.

Different measurements or operational concepts may appear technically related while actually representing very different operational meanings.

Examples may include:
- service outcome vs infrastructure output,
- measured vs inferred values,
- operational efficiency vs service effectiveness,
- individual asset measurements vs aggregated operational measurements.

These distinctions are what Stage 2 later generalizes into semantic capabilities.

---

# Context and Provenance Analysis

Operational meaning cannot be separated from context.

Stage 1 therefore records:
- environmental and operational conditions, such as weather, nearby vegetation, humidity, visibility conditions, or operational scheduling,
- location provenance and installation metadata,
- aggregation conditions and measurement scope,
- whether data was directly measured, inferred from another source, manually configured, or operationally estimated,
- and operational assumptions.

Stage 2 classifies these findings against capabilities such as [Provenance](/methodology/core-methodology/stage-2-semantic-capabilities.md#provenance), [Operational Context](/methodology/core-methodology/stage-2-semantic-capabilities.md#operational-context), and [Physical Context](/methodology/core-methodology/stage-2-semantic-capabilities.md#physical-context).

---

# Common Stage 1 Pitfalls

## Treating All Measurements Equally
Different measurements may represent different operational viewpoints, different levels of trust, or different semantic meanings.

## Ignoring Context
Operational data without context may become misleading, incomparable, or operationally unreliable.

## Ignoring Operational Assumptions
Municipality material may contain implicit operational assumptions that are not explicitly documented.

## Describing Devices Instead of the Service
User stories and the entity sketch describe what the people who run the service need, not the devices or the network that supply it. How the infrastructure itself is operated is captured separately, by the [Operational Semantics](/methodology/core-methodology/stage-2-semantic-capabilities.md#operational-semantics) capabilities.

Starting from existing standards is the most common pitfall of all; see [Meaning Before Standards](/methodology/core-methodology/methodology-overview.md#meaning-before-standards).

---

# Public Street Lighting Example

The [Public Street Lighting walkthrough](/profiles/lighting/public-lighting-walkthrough.md) (section *Stage 1 — Operational Meaning Discovery*) shows this stage in practice: distinguishing lux, lumens, and watts; separating service outcome from infrastructure output; recognizing inferred versus measured values; identifying environmental dependencies such as fog, vegetation, and building shadows; and surfacing concerns about latency, packet loss, and teleoperation reliability. The walkthrough predates user stories and the entity sketch, and does not yet include them.
