---
title: Smart Data Models Semantic Capability Assessment
description: >
  An assessment of how well the Smart Data Models (FIWARE) framework preserves the semantic capabilities required by municipality Digital Twins, evaluated against the Smart Cities SIG Semantic Capability
  Assessment Framework.
layout: doc
---

# {{ $doc.title }}

## Purpose

This report assesses how the Smart Data Models (SDM) framework represents the semantic capabilities identified by the Smart Cities SIG's
[Semantic Capability Assessment Framework](./semantic-capability-assessment.md).
It is the Smart Data Models counterpart to the [OMA Semantic Capability Assessment](./oma-capability-assessment.md): where that report evaluates what OMA LwM2M devices and edge controllers can contribute, this report evaluates whether the Smart Data Models entities and attributes that receive that contribution can preserve its meaning.

Sources consulted for this assessment: [smartdatamodels.org](https://smartdatamodels.org), the [smart-data-models GitHub organization](https://github.com/smart-data-models),
and the `sdm_translator` project.

---

## General Findings by Semantic Category

Before assessing each of the 14 capabilities individually, some general observations apply across the whole framework:

- **Domain semantics.** "Domain" has a different meaning in Smart Data Models than in this framework: it is simply a group of subjects gathered under a common industry area (for example, Weather, Water, Device). A subject —
  and the data models within it — can belong to more than one domain.
- **Observation semantics.** The observation method is not, in general, a first-class attribute in Smart Data Models. Some models do carry a `source` attribute (several data models under the `Device` subject use it,
  typically as a URL) that points to where the observation came from.
- **Interpretation semantics.** The description of each attribute is expected  to state how it should be interpreted. Many attributes carry a `units` descriptor, and a few specific models include metrology attributes, but   neither practice is applied consistently across the catalogue.
- **Operational semantics.** Smart Data Models generally do not capture information about how a model is meant to be used — only which attributes are required. The usual recommendation is to require only `id` and `type`. Larger sets of required attributes only appear when a model is derived directly from an existing standard or ontology.

---

## Domain Semantics

### Service Outcome

Service outcome is treated as a use-case perspective: it is defined by the use cases that motivate a data model and, where necessary, described in the definitions of the relevant attributes rather than in a dedicated attribute
or entity.

### Infrastructure Output

Units and other descriptors of infrastructure output belong in the attribute definitions. Smart Data Models provide a specific `units` clause for attributes so that the unit of measurement can be declared explicitly.

### Resource Consumption

Multiple data models exist for assessing consumption. There is a general `Consumption` subject/data model, and domain-specific models such as `WaterConsumptionObserved` in the Water domain.

---

## Observation Semantics

### Observation Point

Two complementary approaches are available: the physical location — most Smart Data Models expose a location using one of six ways of describing geographic scope (point, line, polygon, and their multi-instance variants) —
and a reference to the originating device or sensor. Some models, such as `DeviceMeasurement`, include an explicit relationship to the device the measurement comes from.

### Observation Scope

The most common case is that a measurement is an instantaneous value.
However, some models — such as `CrowdFlowObserved` and `ElectricVehicleMobility` — represent an average over a period, and several attributes ending in `TSA` (instant, maximum, minimum, and average) exist to
capture that scope explicitly.

### Observation Method

Support for observation method depends entirely on the specific data model — for example, `WeatherObserved` and `WeatherForecast` — rather than being a capability provided consistently across the catalogue.

### Temporal Semantics

Some data models include explicit start and end periods for a measurement, for example `KeyPerformanceIndicator`.

---

## Interpretation Semantics

### Provenance

Provenance is usually implemented as a relationship attribute pointing to another object in the system, rather than as a dedicated provenance
attribute.

### Measurement Quality

`accuracy` is an attribute used across several data models, including `SimulationScenario`, `StateMessage`, `DataQualityAssessment`, `AreaEnvironmentForecast`, `DeviceForecast`, `Geolocation`, `KeyVessel`, and
`MeasurementValue`.

### Operational Context

Operational context needs to be implemented through specific attributes and is usually represented via a relationship to an observation — for example, in `WeatherObserved`.

### Physical Context

Physical context is generally implemented through the geolocation attributes present in most data models, which support point, line, and polygon geometries, as well as multiple instances of each.

---

## Operational Semantics

### Asset Management Context

An `owner` attribute — an array of references — is present in the majority
of data models.

### Network Operability

Network operability is only present in some data models under the IT subject. Where present, it can be included via a relationship attribute pointing to the observation.

### Fallback Behaviour

It is not clear whether fallback behaviour is represented in any form in Smart Data Models today.

---

## Summary

| Semantic Capability | Smart Data Models Assessment |
|---|---|
| Service Outcome | Use-case perspective; described in attribute definitions where necessary rather than a dedicated attribute. |
| Infrastructure Output | Covered via attribute definitions and an explicit `units` clause. |
| Resource Consumption | Covered by a general `Consumption` data model and domain-specific models (e.g., `WaterConsumptionObserved`). |
| Observation Point | Covered via geolocation (six representation types) plus device/sensor relationships (e.g., `DeviceMeasurement`). |
| Observation Scope | Instant by default; average/aggregate scope supported in specific models via `TSA`-suffixed attributes. |
| Observation Method | Model-dependent; no general attribute (e.g., `WeatherObserved`, `WeatherForecast`). |
| Temporal Semantics | Supported in specific models via explicit start/end period attributes (e.g., `KeyPerformanceIndicator`). |
| Provenance | Implemented via relationship attributes to other objects, not a dedicated attribute. |
| Measurement Quality | Supported via an `accuracy` attribute in several, but not all, data models. |
| Operational Context | Requires specific attributes; usually a relationship to an observation (e.g., `WeatherObserved`). |
| Physical Context | Covered via geolocation attributes present in most data models. |
| Asset Management Context | Covered via an `owner` attribute (array of references) present in most data models. |
| Network Operability | Only present in some IT-subject data models, via a relationship to the observation. |
| Fallback Behaviour | Not currently represented; no evidence identified. |

---

## Recommendation

Extend the Capability Assessment Matrix in the
[Semantic Capability Assessment Framework](./semantic-capability-assessment.md#capability-assessment-matrix)
with the findings above, and prioritize discussion on the capabilities with
weakest or least consistent coverage: **Observation Method**, **Fallback
Behaviour**, and **Network Operability**.
