---
title: Smart Cities SIG Methodology Pattern
description: Provides a structured approach for analyzing and documenting smart city services.
layout: doc
---

# {{ $doc.title }}

## 1. Service outcome (what we really care about)
Define the ideal end state for people or assets, not for devices. Think through what the digital twin should show.

Example pattern:

“The target area meets or exceeds the minimum [service metric] required by the reference standard, ideally measured directly where the service is actually delivered.”

Questions to fill in:

- What is the real‑world effect we want to guarantee?

- Where should it be measured physically (surface, roots, lane, bin, bay, etc.)?

## 2. Context that modulates the outcome
List environmental and operational conditions that change when or how much the system should act.

Clarify that context:

Refines default actions and handles edge cases.

Does not replace a direct outcome measurement when it’s available.

Questions to fill in:

- Which weather, usage, or environmental conditions change the need to act?

- When you do have direct outcome measurements, how does context only tweak the behavior?

## 3. Primary physical quantity
Identify the core physical quantity that best represents the service outcome.

Keep device‑centric quantities in a supporting role.

Questions to fill in:

-- What single physical quantity best represents “service delivered” at the right place?

-- Which related quantities describe device behavior or cost, not the outcome itself?

## 4. Direct vs inferred measurement
Separate direct measurements (observed at the outcome or close to it) from inferred/derived values (calculated from other signals, models, or proxies).

Make the method explicit (measured / estimated / predicted / synthetic).

Questions to fill in:

- What do you measure directly at or near the outcome?

- What do you infer from other variables, curves, or models?

- How do you flag each value as measured vs inferred vs predicted vs synthetic?

## 5. Observation level (where in the system you “look”)
Describe at which system level measurements are taken and at which level the service is evaluated.

Common levels:

Device, component, segment/trunk, zone, site, city.

Questions to fill in:

- At what level do you usually measure (device, cabinet, sector, zone…)?

- At what level do you actually evaluate the service outcome for people or assets?

## 6. Typical raw data available
Enumerate the raw signals and events that the infrastructure usually exposes:

Physical measurements, states, events, identifiers, timestamps.

Keep it technology‑neutral but realistic.

Questions to fill in:

- What raw measurements do devices and platforms typically provide? Consider devices available in the market.

- Which states/events are observable (on/off, fault, mode, level…)?

## 7. Minimum metadata for comparability
Define the mandatory metadata required to compare data across:

Vendors, deployments, cities, and time.

Always include:

- Value type: measured / estimated / predicted / synthetic.

- Unit of measure.

- Time semantics: instant vs interval (start, end, resolution).

- Space semantics: what the value applies to (asset, segment, zone).

- Method: sensor, model, allocation rule, aggregation rule.

- Data quality: precision, completeness, availability, consistency.

Questions to fill in:

- What do I need to know about a value so that two cities can safely compare it?
- How do I document the “how it was obtained” in a machine‑readable way?
- How could magnitudes with different margins and varying precisions be compared

## 8. Typical KPIs (built from raw data)
Define service‑oriented KPIs using the raw data and metadata above.

Make clear that:

- KPIs aggregate over time and/or space.

- KPI trust depends on knowing which parts are measured vs inferred and their quality.

Questions to fill in:

- Which KPIs would a city manager or operator actually track for this service?

- For each KPI, what’s the aggregation window, scope, and mix of measured vs inferred inputs?

## 9. Mapping to Smart Data Models
Pick the closest NGSI entities and properties for this service:

- Device/entity types.

- Outcome‑related attributes (the ones you really care about).

- Operational/cost attributes (supporting).

Add extensions only when the core model does not cover the key outcome.

Questions to fill in:

- Which existing Smart Data Models best fit this service?

- Which properties represent:

- Outcome measurements.

- Operational signals.

- Cost/energy/resources.

## 10. Mapping to SAREF (and SAREF extensions) (more ontologies to be considered)
Use SAREF’s measurement pattern:

- saref:Device, saref:Sensor, saref:Actuator.

- saref:Measurement that saref:relatesToProperty some domain property.

Choose domain vocabularies:

- SAREF4CITY, SAREF4AGRI, SAREF4ENVI, etc.

Questions to fill in:

- What are the domain properties (e.g. illuminance, soil moisture, fill level, occupancy) this service observes or acts upon?

- How do you represent:

- Device roles.

Measurements (value, unit, time, location).

Methods and quality, in a way that stays consistent across domains?
