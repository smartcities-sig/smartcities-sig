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

**Input:** municipality operational material.
**Output:** operational objectives, operational pain points, semantic distinctions, contextual dependencies, and interoperability-relevant observations — the input to [Stage 2 — Semantic Capabilities](/methodology/core-methodology/stage-2-semantic-capabilities.md).

For the methodology as a whole, see the [Methodology Overview](/methodology/core-methodology/methodology-overview.md). For a fill-in template covering this stage, see the [Methodology Worksheet](/methodology/core-methodology/methodology-worksheet.md).

---

# Purpose of Stage 1

Stage 1 exists to answer the following questions:

- What is the municipality actually trying to achieve?
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

Starting from existing standards is the most common pitfall of all; see [Meaning Before Standards](/methodology/core-methodology/methodology-overview.md#meaning-before-standards).

---

# Public Street Lighting Example

The [Public Street Lighting walkthrough](/profiles/lighting/public-lighting-walkthrough.md) (section *Stage 1 — Operational Meaning Discovery*) shows this stage in practice: distinguishing lux, lumens, and watts; separating service outcome from infrastructure output; recognizing inferred versus measured values; identifying environmental dependencies such as fog, vegetation, and building shadows; and surfacing concerns about latency, packet loss, and teleoperation reliability.
