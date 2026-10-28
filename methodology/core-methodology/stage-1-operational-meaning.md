---
title: Stage 1 — Operational Meaning
description: How the Smart Cities SIG captures what a municipality is actually trying to achieve before any standards are considered.
layout: doc
---

# Research Methodology

## Introduction

Stage 1 captures the real operational meaning behind municipality requirements, in the municipality's own terms. It applies the methodology's [Meaning Before Standards](/methodology/core-methodology/methodology-overview.md#meaning-before-standards) principle: no standards mapping, schema design, or architecture discussion happens until the operational intent is understood.

Municipality operational documents often contain:
- implicit assumptions,
- mixed technical and operational concepts,
- local terminology,
- incomplete contextual information,
- and operational concerns that are not immediately visible as interoperability requirements.

Stage 1 is carried out in two complementary ways. **Workshops** with the different verticals of a municipality identify, validate, and prioritize needs. It is recommended that the user stories and the entity sketch, the structured material the later stages require, be worked on by small technical groups, starting from those needs.

**Input:** municipality operational material, interviews, and workshops.
**Output:** user stories, each with the questions the Digital Twin must answer; an entity sketch, including the relationships between its entities; operational objectives, operational pain points, semantic distinctions, contextual dependencies, and information held by other units; a register of requirements; and interoperability-relevant observations — the input to [Stage 2 — Semantic Capabilities](/methodology/core-methodology/stage-2-semantic-capabilities.md).

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

# Workshop-Based Needs Elicitation

Workshops with the different verticals of a municipality (for example lighting, mobility, or parks) are the way Stage 1 moves from an open situation, in which it is not yet clear what is needed, to a set of validated, prioritized needs worked through in detail. The approach is thematic-agnostic and can be applied to any service domain.

It is organized around one idea: **each step produces a concrete result, and that result is the only input of the next step.** The work narrows from the broad to the specific, and it is always possible to explain where each conclusion comes from.

The process consists of two consecutive workshops:

| Workshop | Question it answers | Starts from | Result it delivers |
|---|---|---|---|
| **1st Workshop** | What needs and opportunities exist, before thinking about solutions? | The service domain to be explored. | A list of needs, grouped into categories and described in terms of what is to be achieved. |
| **2nd Workshop** | Do these needs reflect what was collected? Which are the most important? What is needed to satisfy them? | Exclusively the list of needs from the 1st Workshop. | Needs that are validated, prioritized, and grounded, with the limits of what was covered. |

## Guiding Principles

- **One result per step.** Each workshop ends in a defined, verifiable product. The next workshop starts from that product, not from general impressions.
- **Need before solution.** Solutions are not discussed until needs are validated and prioritized. If they come up during the debate, they are recorded but not analyzed.
- **Voting is not deciding.** A vote measures interest. The decision about what is worked on next is a separate step, which may take into account the time and functionality of the workshop, and is recorded as such.
- **What was said is not what was agreed.** What was commented on in the room is always distinguished from what the group agreed or decided.
- **Traceability.** Each need keeps its identifier across workshops, so it is possible to know whether it was validated, modified, discarded, or appeared later.
- **Attribution by profile.** Opinions are attributed to roles or groups, not to individual people.
- **Record the limits.** What there was no time to work on, or remained pending, is documented, so that later steps know what is covered and what is not.

## 1st Workshop: Identifying Needs

A needs-and-opportunities mapping session. Its purpose is to collect what the service needs before defining how to solve it, distinguishing current problems from possibilities for improvement.

- **Starts from:** the service domain to be explored.
- **Participants:** diverse profiles of the service: managers, operators, technical specialists, and innovation and integration profiles.
- **How it works:** a script of open questions organized in blocks: what is to be achieved, which conditions and resources are needed, and which ideas emerge. Each person contributes in writing (post-its), followed by a group discussion.
- **Subsequent treatment:** what was written is transcribed literally, and each contribution is classified by level: *objective* (what is pursued), *decision* (what someone must be able to decide), *capability* (what the service must be able to do), or *data* (the information that feeds it). A fifth level, the technology solution, is left out of the analysis. Similar needs are grouped into broad categories.
- **Result:** a list of needs grouped into categories, each described as "what I want" together with its development, accompanied by a detail report and an executive summary.
- **Feeds the 2nd Workshop:** the list of needs is the only starting material of the 2nd Workshop.

## 2nd Workshop: Validate, Prioritize, and Ground

The 2nd Workshop does not look for solutions. It filters the result of the 1st Workshop through three consecutive dynamics, each working only with what the previous one left.

### Dynamic 1 · Validation

- **Question:** Do these needs reflect what was collected in the previous workshop?
- **How it works:** each category is presented. Every participant reads it, notes what does not reflect what was collected (nuances, doubts, absences), and the observations are shared. People who did not attend the 1st Workshop may join.
- **Result:** validated needs, with nuances and new contributions recorded.
- **Feeds:** prioritization. This is the set that is voted on.

### Dynamic 2 · Prioritization

- **Question:** Which are the most important?
- **How it works:** free voting by category, with post-its in the room and by chat or voice remotely. Each participant explains their choice.
- **Result:** a vote count per category, showing where interest concentrates, and the decision, taken separately, on which category is worked on next.
- **Feeds:** grounding. Only the chosen category is explored in detail. The others are identified as next points of interest.

### Dynamic 3 · Grounding

- **Question:** What is needed to satisfy them, who must be involved, and how?
- **How it works:** for each need in the chosen category, the group works on a board: what the current situation is, which preconditions are needed, and which dependencies exist. No solutions or specific technologies are selected.
- **Result:** for each need worked on, a map of what is needed to satisfy it, together with the list of what there was no time to address.

**Result of the 2nd Workshop:** needs that are validated, prioritized, and grounded, indicating which categories were worked on and which remain pending.

## Documenting and Returning Each Workshop

After each workshop, three products are generated:

- **Information download.** The full material of the workshop, what was planned versus what actually happened, and the doubts and limitations of the material.
- **Executive summary.** Clear, high-level messages: what was validated, what was prioritized, and which problems arise, without technical detail or names of people.
- **Detail report.** The detailed account of the workshop, open to review and comments before the result is considered closed.

---

# Working in Small Groups

The audience of a workshop is not the right one for defining user stories in the format required by the later stages. Workshops bring together diverse profiles and are well suited to collecting, validating, and prioritizing needs, but writing well-formed user stories and deriving an entity sketch from them requires more time, more precision, and often technical knowledge. **It is therefore recommended that the user stories and the entity sketch be worked on by small technical groups**, starting from the needs validated and prioritized in the workshops.

Who participates in these conversations has to be decided according to the definition needed in each case: the profiles required to describe a given need properly will differ from one need or category to another.

In summary, the workshops produce the raw material (validated and prioritized needs), and the small technical groups turn it into the user stories and entity sketch that Stage 1 delivers to Stage 2. What happens after the 2nd Workshop beyond this work is still to be defined.

---

# User Stories

In small groups, the municipality's representatives describe, in their own words, the problems they want to solve and what a solution would let them do, starting from the needs validated in the workshops. Each need is written down as a **user story**, structured so that the people involved, the actions, the conditions, and the purpose can be picked out of it.

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

These questions should be handled through **consultation with the small groups**, rather than by convening a new workshop. The exact route depends on the information needed: the gap detected determines who needs to be consulted and how. Both who participates and the size of the group should be assessed according to the information needed.

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

## Discussing Solutions Too Early
Solutions and technologies that come up during workshops are recorded but not analyzed until needs have been validated and prioritized.

## Mixing What Was Said with What Was Agreed
Comments made in the room are not the same as decisions taken by the group. Votes measure interest; the decision on what to work on next is recorded separately.

## Writing User Stories in a Broad Workshop
A workshop with diverse profiles is not the right setting to define user stories in the format the later stages need. This is done in small groups.

Starting from existing standards is the most common pitfall of all; see [Meaning Before Standards](/methodology/core-methodology/methodology-overview.md#meaning-before-standards).

---

# Public Street Lighting Example

The [Public Street Lighting walkthrough](/profiles/lighting/public-lighting-walkthrough.md) (section *Stage 1 — Operational Meaning Discovery*) shows this stage in practice: distinguishing lux, lumens, and watts; separating service outcome from infrastructure output; recognizing inferred versus measured values; identifying environmental dependencies such as fog, vegetation, and building shadows; and surfacing concerns about latency, packet loss, and teleoperation reliability. The walkthrough predates user stories and the entity sketch, and does not yet include them.
