---
title: Smart Cities SIG Methodology Worksheet
description: A fill-in template for analysing a municipal Service Domain in Stages 1 and 2 of the Smart Cities SIG methodology.
layout: doc
---

# {{ $doc.title }}

This worksheet is the practical template for analysing a Service Domain — public lighting, irrigation, waste collection, parking, and so on — during [Stage 1](/methodology/core-methodology/stage-1-operational-meaning.md) and [Stage 2](/methodology/core-methodology/stage-2-semantic-capabilities.md).

Each step names the [semantic capabilities](/methodology/core-methodology/stage-2-semantic-capabilities.md) it feeds. The capabilities are defined only in Stage 2; this worksheet asks the questions that surface them for a specific service. For a filled-in example, see the [lighting vs irrigation comparison](/profiles/lighting-vs-irrigation-comparison.md).

---

## 0. User stories and entities

*Feeds: [Service Outcome](/methodology/core-methodology/stage-2-semantic-capabilities.md#service-outcome); the entities and properties it identifies are examined in the steps that follow*

Collect [user stories](/methodology/core-methodology/stage-1-operational-meaning.md#user-stories) from the people who run the service, in their own words, then draw up the [entity sketch](/methodology/core-methodology/stage-1-operational-meaning.md#entity-sketch).

Example pattern:

> "<type of user> want to <action> under <conditions> so that <they can achieve a benefit or value>."

Questions to fill in:
- Who needs to do what, under which conditions, and why?
- Which types of entities do the stories mention?
- For each entity type, which properties, actions, and events do the stories mention?

## 1. Service outcome (what we really care about)

*Feeds: [Service Outcome](/methodology/core-methodology/stage-2-semantic-capabilities.md#service-outcome)*

Define the ideal end state for people or assets, not for devices. Think through what the Digital Twin should show.

Example pattern:

> "The target area meets or exceeds the minimum [service metric] required by the reference standard, ideally measured directly where the service is actually delivered."

Questions to fill in:
- What is the real-world effect we want to guarantee?
- Where should it be measured physically (surface, roots, lane, bin, bay, etc.)?

## 2. Context that modulates the outcome

*Feeds: [Operational Context](/methodology/core-methodology/stage-2-semantic-capabilities.md#operational-context), [Physical Context](/methodology/core-methodology/stage-2-semantic-capabilities.md#physical-context)*

List the environmental and operational conditions that change when or how much the system should act. Context refines default actions and handles edge cases; it does not replace a direct outcome measurement when one is available.

Questions to fill in:
- Which weather, usage, or environmental conditions change the need to act?
- When you do have direct outcome measurements, how does context only adjust the behaviour?

## 3. Primary physical quantity

*Feeds: [Service Outcome](/methodology/core-methodology/stage-2-semantic-capabilities.md#service-outcome), [Infrastructure Output](/methodology/core-methodology/stage-2-semantic-capabilities.md#infrastructure-output), [Resource Consumption](/methodology/core-methodology/stage-2-semantic-capabilities.md#resource-consumption)*

Identify the core physical quantity that best represents the service outcome. Keep device-centric quantities in a supporting role.

Questions to fill in:
- What single physical quantity best represents "service delivered" at the right place?
- Which related quantities describe device behaviour (infrastructure output) or cost (resource consumption), rather than the outcome itself?

## 4. Direct vs inferred measurement

*Feeds: [Observation Method](/methodology/core-methodology/stage-2-semantic-capabilities.md#observation-method)*

Separate direct measurements (observed at or close to the outcome) from inferred or derived values (calculated from other signals, models, or proxies), and make the method explicit for every value.

Questions to fill in:
- What do you measure directly at or near the outcome?
- What do you infer from other variables, curves, or models?
- How do you flag each value's observation method?

## 5. Observation level (where in the system you "look")

*Feeds: [Observation Point](/methodology/core-methodology/stage-2-semantic-capabilities.md#observation-point), [Observation Scope](/methodology/core-methodology/stage-2-semantic-capabilities.md#observation-scope)*

Describe at which system level measurements are taken, and at which level the service is evaluated. Common levels: device, component, segment or trunk, zone, site, city.

Questions to fill in:
- At what level do you usually measure (device, cabinet, sector, zone…)?
- At what level do you actually evaluate the service outcome for people or assets?

## 6. Typical raw data available

*Feeds: [Infrastructure Output](/methodology/core-methodology/stage-2-semantic-capabilities.md#infrastructure-output), [Resource Consumption](/methodology/core-methodology/stage-2-semantic-capabilities.md#resource-consumption), [Network Operability](/methodology/core-methodology/stage-2-semantic-capabilities.md#network-operability)*

Enumerate the raw signals and events the infrastructure usually exposes: physical measurements, states, events, identifiers, and timestamps. Keep it technology-neutral but realistic.

Questions to fill in:
- What raw measurements do devices and platforms typically provide? Consider devices available on the market.
- Which states and events are observable (on/off, fault, mode, level…)?

## 7. Minimum metadata for comparability

Define the metadata required to compare data across vendors, deployments, cities, and time. For every value, record:

| Metadata | Capability |
|---|---|
| Value type and method (measured, estimated, predicted, synthetic…; sensor, model, allocation or aggregation rule) | [Observation Method](/methodology/core-methodology/stage-2-semantic-capabilities.md#observation-method) |
| Unit of measure | — |
| Time: instant vs interval (start, end, resolution) | [Temporal Semantics](/methodology/core-methodology/stage-2-semantic-capabilities.md#temporal-semantics) |
| Space: what the value applies to (asset, segment, zone) | [Observation Scope](/methodology/core-methodology/stage-2-semantic-capabilities.md#observation-scope) |
| Source of the value | [Provenance](/methodology/core-methodology/stage-2-semantic-capabilities.md#provenance) |
| Data quality: precision, completeness, availability, consistency | [Measurement Quality](/methodology/core-methodology/stage-2-semantic-capabilities.md#measurement-quality) |

Questions to fill in:
- What do I need to know about a value so that two cities can safely compare it?
- How do I document how it was obtained in a machine-readable way?
- How can magnitudes with different margins and precisions be compared?

## 8. Typical KPIs (built from raw data)

Define service-oriented KPIs from the raw data and metadata above. KPIs aggregate over time and/or space, and KPI trust depends on knowing which inputs are measured versus inferred and their quality.

Questions to fill in:
- Which KPIs would a city manager or operator actually track for this service?
- For each KPI, what are the aggregation window, the scope, and the mix of measured and inferred inputs?

---

## Next: mapping to semantic models

Mapping the service onto Smart Data Models and SAREF is part of Stage 4; see [Mapping to Smart Data Models and Ontologies](/methodology/core-methodology/stage-4-smart-data-models-realization.md#mapping-to-smart-data-models-and-ontologies).
