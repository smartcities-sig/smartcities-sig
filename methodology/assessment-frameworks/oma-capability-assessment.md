---
title: OMA Semantic Capability Assessment for Digital Twin Interoperability
description: >
  An evidence-based assessment of the information that OMA LwM2M Objects
  and Resources contribute to Smart Data Models and Digital Twins supporting
  municipality operational objectives.
layout: doc
---

# {{ $doc.title }}

## Purpose

This report assesses the minimum semantic information that OMA LwM2M devices and edge controllers need to provide so that their information can be integrated into Smart Data Models without losing operational meaning.

The final municipality operational questions are answered by a Digital Twin, not by an individual LwM2M Object. The intended information chain is:

```text
Municipality Operational Question
                │
                ▼
Required Operational Information
                │
                ▼
OMA Device and Edge Contribution
                │
                ▼
LwM2M Objects and Resources
                │
                ▼
Smart Data Model Mapping and Enrichment
                │
                ▼
Digital Twin Interpretation
                │
                ▼
Municipality Operational Answer
```

OMA is therefore not expected to represent all municipality context or answer municipality questions independently. OMA is expected to provide explicit, interoperable telemetry, locally required configuration, and device-level metadata and relationships. Smart Data Models add municipality context and preserve the OMA contribution for use by Digital Twins.

---

# Assessment Baseline and Scope

This report uses the following source revisions:

- Smart Cities SIG semantic framework branch: `smartcities-sig/assesment-framework`
- Semantic framework commit: `8ad0acce94fdb7e5abed6b887a52d05543d111ef`
- OMA LwM2M Registry branch: `lwm2m-registry/prod`
- OMA LwM2M Registry commit: `02f68c93a2238b552aea481bb22aea6d49615839`

The assessment is currently limited to:

- Public Lighting
- Water Management and Irrigation

Only current Object definitions in the root of the [LwM2M Registry](https://github.com/OpenMobileAlliance/lwm2m-registry) are assessed. Definitions in `version_history` are excluded. A Resource is treated as reusable only when it is present in [`Common.xml`](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/Common.xml).

The following Object Source classifications are used:

- **Source 0** — Object defined by OMA.
- **Source 1** — Object originally defined by another organization. IPSO and uCIFI Objects retain Source 1 and their original Owner even though these Object families are now maintained by OMA.
- **Source 2** — Private Object. A private Object may provide implementation evidence, but a generally interoperable OMA capability normally requires a new Source 0 definition.

New Objects based on IPSO or uCIFI work are expected to use Source 0. Final normative design and Object ID allocation remain the responsibility of the OMA Smart Cities Working Group.

---

# How to Read This Assessment

Each Question for OMA is assessed using the same structure. Public Lighting and Water Management/Irrigation are evaluated separately, followed by findings shared across both domains.

## Municipality Operational Need

Explains why the information is required and which Municipality Operational Questions depend on it. This section describes the final operational purpose, not a responsibility assigned exclusively to OMA.

## Required OMA Contribution

Defines the minimum information that an LwM2M device or edge controller must provide so that the information can be integrated into a Smart Data Model without losing its meaning.

The OMA contribution is classified as:

- **Telemetry** — Information observed or reported by a device.
- **Configuration or operational intent** — Information supplied to a device because it is required for local operation.
- **Metadata and relationships** — Information identifying what was observed and how it relates to other local entities.

Externally supplied information belongs in Smart Data Models unless a device needs that information for local operation.

## Existing Object and Resource Evidence

Lists current Registry Objects and Resources that may provide the required information. Each entry identifies:

- Object ID and Object name
- Resource ID and Resource name
- Source and Owner
- Mandatory or optional status
- Whether the Resource is defined in [`Common.xml`](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/Common.xml)
- The part of the semantic requirement it supports

Inclusion as evidence does not automatically mean that the complete semantic capability is supported.

## Coverage Assessment

Evaluates how completely the current Registry supports the required OMA contribution. The available classifications are:

- **Existing OMA coverage** — The required capability is adequately represented by an OMA-defined mechanism.
- **Existing coverage requiring clarification or extension** — Relevant Objects or Resources exist, but semantics, relationships, mandatory status, or interoperability constraints are incomplete.
- **New OMA capability required** — No adequate standardized mechanism exists.
- **Outside OMA responsibility but must remain linkable** — The information belongs in another ecosystem, but OMA information must provide identifiers or relationships that allow integration.

Optional Resources are treated as conditional coverage. Co-location of Objects on the same LwM2M Client is treated as indirect or ambiguous unless an explicit relationship is provided.

## Missing Semantics

Identifies information that cannot be represented explicitly and interoperably using the current Objects and Resources. This may include missing controlled terminology, relationships, observation context, provenance, method classification, scope, aggregation information, or mandatory profile requirements.

## Smart Data Model Responsibility

Identifies context that should be represented or added by the corresponding Smart Data Model rather than by an LwM2M device. Examples include municipality service objectives, policies, compliance thresholds, geographic and administrative relationships, service areas, infrastructure topology, cross-device aggregation, and the final determination of whether a municipality objective was achieved.

This section also identifies which OMA identifiers and relationships must be preserved during mapping.

## Recommendation to the OMA Smart Cities Working Group

Translates the assessment into an actionable semantic requirement or plausible implementation option. Recommendations may include:

- Clarifying an existing Object or Resource
- Making an optional Resource required by a Smart Cities profile
- Defining a controlled vocabulary
- Adding reusable Resources
- Extending an existing Object
- Defining a new Source 0 Object
- Leaving information to Smart Data Models while ensuring that it remains linkable

Recommendations do not allocate Object IDs or prescribe the final normative design.

## Evidence Conventions

The following abbreviations are used in evidence tables:

- **M** — Mandatory Resource in the consuming Object.
- **O** — Optional Resource in the consuming Object; coverage is conditional.
- **Reusable** — The Resource is defined in [`Common.xml`](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/Common.xml).
- **Object-specific** — The Resource is not defined in [`Common.xml`](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/Common.xml).

A Resource may be mandatory without being reusable, or reusable without being mandatory. Mandatory status is determined by the consuming Object definition.

Free-text Resources do not provide sufficient cross-vendor semantics unless a controlled vocabulary or profile governs their values.

---

# Semantic Capability 1: Service Outcome

## Capability Purpose

Service Outcome represents the real-world result that a municipality intends to deliver, independently of how the underlying infrastructure behaves.

For Public Lighting, the outcome includes the illumination experienced on a road, pavement, pedestrian area, or other public space. For Water Management and Irrigation, the outcome includes water delivered at the required flow, pressure, level, quality, or soil/root-zone condition.

The municipality-level classification of an observation as a service outcome normally belongs in a Smart Data Model. OMA must provide sufficiently explicit observations and relationships so that the classification can be made without guessing from Object identity or Client co-location.

## Overall Capability Conclusion

**Existing coverage requiring clarification or extension.**

The Registry can report most of the physical measurements required to evaluate service outcomes. It does not consistently describe:

- The observation point or feature being observed
- How the observation relates to an infrastructure asset or service endpoint
- Whether the value was measured, estimated, inferred, predicted, simulated, proxy-derived, or aggregated
- The distinction between a service-related observation and infrastructure output
- Which municipality objective, policy, or service area applies

The last item normally belongs in a Smart Data Model. The first four require additional or clarified OMA semantics when they are known by the device or edge controller.

---

# OMA Question 1

> Which existing LwM2M Objects and Resources represent the service outcome?

## Public Lighting

### Municipality Operational Need

Municipalities need to determine whether streets and public spaces are adequately illuminated, identify under- or over-illuminated areas, and evaluate whether lighting objectives are achieved.

### Required OMA Contribution

**Telemetry**

- Illuminance value
- Unit
- Measurement timestamp
- Measurement quality when available

**Metadata and relationships**

- Identity of the observing sensor
- Observation point, such as luminaire, pole, road surface, pavement, or pedestrian area
- Feature or local asset represented by the observation

No municipality lighting policy needs to be stored by the device unless it is required for local control.

### Existing Object and Resource Evidence

| Object | Resource evidence | Source / Owner | Requirement status | Reuse | Assessment |
|---|---|---|---|---|---|
| [`3301`](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/3301.xml) Illuminance | `3301/5700` Sensor Value | 1 / IPSO Alliance | M | Reusable | Direct illuminance measurement. It does not identify the observation point or represented public space. |
| [`3301`](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/3301.xml) Illuminance | `3301/5701` Sensor Units | 1 / IPSO Alliance | O | Reusable | Conditional unit metadata. |
| [`3301`](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/3301.xml) Illuminance | `3301/5518` Timestamp | 1 / IPSO Alliance | O | Reusable | Conditional measurement time. |
| [`3301`](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/3301.xml) Illuminance | `3301/6042` Measurement Quality Indicator; `3301/6049` Measurement Quality Level | 1 / IPSO Alliance | O | Reusable | Conditional measurement quality. |
| [`3301`](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/3301.xml) Illuminance | `3301/5750` Application Type | 1 / IPSO Alliance | O | Reusable | Free text can describe a use case, but cannot reliably establish road-surface or pedestrian-area semantics. |
| [`3392`](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/3392.xml) oA Logical Illuminance Sensor | `3392/404` Sensor Value | 1 / OpenAIS | M | Object-specific | Direct illuminance reading in lux. |
| [`3392`](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/3392.xml) oA Logical Illuminance Sensor | `3392/909` Executing Object | 1 / OpenAIS | M | Object-specific | Core Link to an executing Object Instance. Provides an explicit relationship, but not a general observed-feature model. |
| [`3398`](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/3398.xml) oA Physical Illuminance Sensor | `3398/908` Mounting Location | 1 / OpenAIS | M | Object-specific | Site-specific free-text mounting location. The definition is building-oriented and lacks a controlled vocabulary. |
| [`3300`](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/3300.xml) Generic Sensor | `3300/5700` Sensor Value; `3300/5750` Application Type | 1 / IPSO Alliance | M value; O application type | Reusable | Generic fallback. Semantically weaker than Object 3301 because the observed property depends on free text and optional units. |
| [`509`](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/509.xml) Measurement Metadata | `509/0` Linked Sensor | 0 / OMA | M | Object-specific | Source 0 foundation for linking metadata to a sensor Object Instance. It does not identify observation point, observed feature, or method. |

### Coverage Assessment

**Existing coverage requiring clarification or extension.**

Illuminance values are directly represented. Supporting units, timestamp, and quality are optional. No general OMA mechanism states whether the measurement was taken at the luminaire, at a reference plane, or on the road surface.

### Missing Semantics

- Controlled Public Lighting observation-point terminology
- Explicit observed-feature relationship
- Explicit relationship between logical observation and the public-space entity represented
- Profile requirement for timestamp, units, and quality metadata

### Smart Data Model Responsibility

The Smart Data Model should represent:

- Road, street, pavement, pedestrian area, or public-space identity
- Municipality lighting objective and applicable standard
- Required illumination range
- Spatial aggregation and compliance determination

The mapping must preserve sensor identity, observation point, value, unit, timestamp, and quality.

### Recommendation to the OMA Smart Cities Working Group

Retain Object 3301 as the primary illuminance measurement Object. Define a standardized observation-point and observed-feature relationship, potentially by extending Source 0 Object 509 or by defining reusable metadata Resources. Define a Public Lighting profile that makes required contextual Resources mandatory when they are needed for interoperable service-outcome assessment.

## Water Management and Irrigation

### Municipality Operational Need

Municipalities need to determine whether water reaches its intended location, whether consumers receive adequate pressure, whether plants receive sufficient irrigation, and whether the required water service outcome is achieved.

### Required OMA Contribution

**Telemetry**

- Water flow, accumulated volume, pressure, level, soil moisture, and relevant water-quality measurements
- Unit, timestamp, and quality
- Interval or aggregation information when the reported value is not instantaneous

**Metadata and relationships**

- Observation point, such as pump outlet, valve, pipeline, consumer delivery point, irrigation zone, soil layer, or root zone
- Observed medium or feature
- Relationship to a locally known asset or service endpoint

### Existing Object and Resource Evidence

| Object | Resource evidence | Source / Owner | Requirement status | Reuse | Assessment |
|---|---|---|---|---|---|
| [`3300`](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/3300.xml) Generic Sensor | `3300/5700` Sensor Value; `3300/5701` Units; `3300/5750` Application Type | 1 / IPSO Alliance | M value; O units and application type | Reusable | Generic fallback. The measured property depends on optional free text. |
| [`3320`](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/3320.xml) Percentage | `3320/5700` Sensor Value; `3320/5750` Application Type | 1 / IPSO Alliance | M value; O application type | Reusable | Can carry soil-moisture percentage, but soil moisture and root-zone semantics are not standardized. |
| [`3323`](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/3323.xml) Pressure | `3323/5700` Sensor Value | 1 / IPSO Alliance | M | Reusable | Direct pressure measurement. The network or consumer observation point is absent. |
| [`3319`](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/3319.xml) Depth | `3319/5700` Sensor Value | 1 / IPSO Alliance | M | Reusable | Can represent water depth or level when deployment context supplies the meaning. |
| [`3346`](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/3346.xml) Rate | `3346/5700` Sensor Value | 1 / IPSO Alliance | M | Reusable | Can represent water flow rate. The medium and observation point are not explicit. |
| [`3303`](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/3303.xml) Temperature | `3303/5700` Sensor Value | 1 / IPSO Alliance | M | Reusable | Supports water temperature when it is part of the required service outcome. |
| [`3325`](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/3325.xml) Concentration | `3325/5700` Sensor Value | 1 / IPSO Alliance | M | Reusable | Generic constituent concentration; the constituent requires additional semantics. |
| [`3326`](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/3326.xml) Acidity | `3326/5700` Sensor Value | 1 / IPSO Alliance | M | Reusable | Direct acidity measurement. |
| [`3327`](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/3327.xml) Conductivity | `3327/5700` Sensor Value | 1 / IPSO Alliance | M | Reusable | Direct conductivity measurement. |
| [`3424`](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/3424.xml) Water Meter | `3424/1` Cumulated Water Volume | 1 / uCIFI | M | Object-specific | Strong delivered-volume evidence when the meter is located at a delivery point. The delivery-point relationship is absent. |
| [`3424`](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/3424.xml) Water Meter | `3424/7` Minimum Flow Rate; `3424/8` Maximum Flow Rate | 1 / uCIFI | O | Object-specific | Conditional extrema; no mandatory current flow value. |
| [`3426`](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/3426.xml) Water Quality Sensor | `3426/1-14` water-quality measurements | 1 / uCIFI | O | Object-specific | Broad water-quality coverage, but no individual measurement is mandatory. |
| [`3427`](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/3427.xml) Pressure Monitoring Sensor | `3427/1` Pressure | 1 / uCIFI | M | Object-specific | Strong water-specific pressure measurement. Its position in the network is unspecified. |
| [`3445`](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/3445.xml) Stream Gauge | `3445/1` Water Level; `3445/2` Volumetric Discharge | 1 / uCIFI | M level; O discharge | Object-specific | Supports water level and conditional discharge. The represented location is absent. |
| `10266` Water Flow Readings | `10266/6029` Latest Payload | 2 / South East Water Corporation | M | Reusable | Private interval-data precedent. The payload is opaque and lacks a general aggregation-method declaration. |
| `10269` Pressure Readings | `10269/6029` Latest Payload | 2 / South East Water Corporation | M | Reusable | Private interval pressure precedent. |
| `10487` Water Level Readings | `10487/6029` Latest Payload | 2 / South East Water Corporation | M | Reusable | Private interval water-level precedent. |
| `10507` Electrical Conductivity Readings | `10507/6029` Latest Payload | 2 / South East Water Corporation | M | Reusable | Private interval conductivity precedent. |
| [`509`](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/509.xml) Measurement Metadata | `509/0` Linked Sensor | 0 / OMA | M | Object-specific | Source 0 sensor-metadata link foundation; observation point and observed feature remain absent. |

The interval Objects also use reusable Resources such as `6000` Interval Period, `6003` Interval Collection Start Time, `6004` Oldest Recorded Interval, and `6006` Latest Recorded Interval. These provide temporal context but do not fully describe the aggregation function or observation point.

### Coverage Assessment

**Existing coverage requiring clarification or extension.**

Most physical quantities are available through IPSO and uCIFI Objects now maintained by OMA. Root-zone soil moisture remains semantically weak because it depends on Object 3320 plus optional free-text Application Type. Private Source 2 Objects demonstrate interval-data patterns but do not constitute general Source 0 OMA coverage.

### Missing Semantics

- Standardized soil-moisture and root-zone representation
- Controlled Water/Irrigation observation-point terminology
- Explicit observed-medium and observed-feature relationships
- Link from a measurement to a consumer delivery point, irrigation zone, soil layer, or root zone
- General aggregation function for interval values
- Mandatory contextual metadata profile

### Smart Data Model Responsibility

The Smart Data Model should represent:

- Water network and irrigation topology
- Consumer, service area, irrigation zone, plant, and root-zone identity
- Required pressure, volume, moisture, and water-quality objectives
- Municipality policy and compliance determination
- Cross-device and geographic aggregation

The mapping must preserve measurement identity, observation point, value, unit, timestamp, quality, and interval semantics.

### Recommendation to the OMA Smart Cities Working Group

Use existing IPSO and uCIFI measurement Objects where their physical quantity semantics are sufficient. Define controlled observation-point and observed-feature relationships. Standardize soil-moisture/root-zone semantics. Use the Source 2 interval Objects as implementation evidence, but define a Source 0 pattern if generalized interval observations are adopted by OMA.

## Shared Cross-Domain Finding

The Registry represents physical quantities more effectively than it represents their operational role. The Smart Data Model should classify an observation as a municipality service outcome. OMA should make that classification possible by exposing explicit observation point, observed feature, timestamp, units, quality, and method metadata.

---

# OMA Question 2

> How is the distinction maintained between service outcome and infrastructure output?

## Public Lighting

### Municipality Operational Need

A municipality must distinguish inadequate road or pedestrian-area illumination from normal luminaire operation. A luminaire may be switched on and operating at its commanded dimming level while the public space remains under-illuminated.

### Required OMA Contribution

**Telemetry**

- Illuminance at the relevant observation point
- Luminaire operating state and output-related telemetry

**Metadata and relationships**

- Explicit relationship between the illuminance observation, its observation point, and the relevant lighting asset when known locally

### Existing Object and Resource Evidence

| Semantic role | Object and Resource | Source / Owner | Assessment |
|---|---|---|---|
| Service-outcome candidate | `3301/5700` Illuminance Sensor Value | 1 / IPSO Alliance | Measures illuminance but does not state whether it represents a road surface or the luminaire environment. |
| Service-outcome candidate | `3392/404` Illuminance Sensor Value | 1 / OpenAIS | Logical illuminance observation. |
| Logical/physical link | `3392/909` Executing Object | 1 / OpenAIS | Explicit Core Link, but limited to the OpenAIS Object model. |
| Infrastructure behaviour | `3311/5850` On/Off — M; `3311/5851` Dimmer — O | 1 / IPSO Alliance | Describes control state rather than achieved illumination. |
| Infrastructure behaviour | `3416/3` Dimming Level — M; `3416/2` Command in Action — O | 1 / uCIFI | Describes lamp-controller behaviour. |
| Infrastructure capability | `3417/4` Nominal Light Output — O | 1 / uCIFI | Describes nominal luminaire output in lumens, not observed public-space illuminance. |

### Coverage Assessment

**Existing coverage requiring clarification or extension.**

Separate sensor and controller Objects create a structural distinction, but no general relationship states which illuminance observation results from which luminaire or which public space it represents. Client co-location is ambiguous.

### Missing Semantics

- Explicit observation-to-asset relationship
- Explicit observation-point relationship
- Controlled distinction between luminaire output and public-space illuminance

### Smart Data Model Responsibility

The Smart Data Model should classify road-surface or public-space illuminance as the service outcome and relate it to lighting assets, roads, and applicable objectives.

### Recommendation to the OMA Smart Cities Working Group

Do not infer service outcome from Object ID or Client co-location. Define a standard relationship from measurement metadata to the observed lighting asset and observation point.

## Water Management and Irrigation

### Municipality Operational Need

A municipality must distinguish water delivered to a consumer or root zone from the behaviour of pumps, valves, tanks, and pipelines. An open valve does not prove that sufficient water reached its intended destination.

### Required OMA Contribution

**Telemetry**

- Outcome-related flow, volume, pressure, level, or soil moisture
- Pump, valve, and discharge state when locally observable

**Metadata and relationships**

- Explicit relationship between an observation, its observation point, and the relevant local infrastructure asset or endpoint

### Existing Object and Resource Evidence

| Semantic role | Object and Resource | Source / Owner | Assessment |
|---|---|---|---|
| Service-outcome candidate | `3323/5700` Pressure | 1 / IPSO Alliance | Could represent consumer pressure or infrastructure pressure; the point is unspecified. |
| Service-outcome candidate | `3427/1` Pressure | 1 / uCIFI | Water-specific pressure, but network location is absent. |
| Service-outcome candidate | `3320/5700` Percentage | 1 / IPSO Alliance | Could represent soil moisture, but the property and root-zone location are not standardized. |
| Service-outcome candidate | `3424/1` Cumulated Water Volume | 1 / uCIFI | Could represent delivered volume if the meter is at the service endpoint. |
| Infrastructure behaviour | `3425/2` Irrigation Valve Status; `3425/4` Command in Action | 1 / uCIFI | Describes valve behaviour; both Resources are optional. |
| Infrastructure configuration | `10498/0` Discharge Level; `10498/2` Discharge Volume | 2 / South East Water Corporation | Private configured discharge intent, not proof of delivered outcome. |

### Coverage Assessment

**Indirect or ambiguous.**

The same Pressure Object can describe consumer pressure, pump outlet pressure, pipeline pressure, or valve-adjacent pressure. Object identity does not establish its operational role.

### Missing Semantics

- Observation point and network role
- Explicit link between measurement and local asset or endpoint
- Standard soil/root-zone relationship
- Delivered-versus-commanded distinction for water volume

### Smart Data Model Responsibility

The Smart Data Model should classify observations as consumer service, irrigation outcome, or infrastructure behaviour using network topology, service-area relationships, and municipality objectives.

### Recommendation to the OMA Smart Cities Working Group

Define explicit observation-point and observed-feature relationships. Preserve the distinction between actuator command, actual actuator state, infrastructure measurement, and endpoint outcome measurement.

## Shared Cross-Domain Finding

The municipality-level concept of Service Outcome normally belongs in the Smart Data Model. OMA does not need to add a universal `Service Outcome` flag if it exposes the observation point, observed feature, and relevant local asset relationships needed for deterministic classification.

---

# OMA Question 3

> How are measured, estimated, inferred, predicted, or aggregated service outcomes represented?

## Public Lighting

### Municipality Operational Need

A municipality must know whether illuminance was directly measured or derived from luminaire characteristics, simulation, historical information, or an analytical model. Different methods have different levels of authority for compliance and operational decisions.

### Required OMA Contribution

**Telemetry**

- Observed or derived value

**Metadata and relationships**

- Observation method
- Source observations when locally available
- Aggregation function and interval when calculated locally
- Local model identity or version when operationally relevant

### Existing Object and Resource Evidence

| Method | Evidence | Source / Owner | Assessment |
|---|---|---|---|
| Measured | Reusable `5700` Sensor Value used by Object 3301 | 1 / IPSO Alliance | The Common Resource definition explicitly describes a measured sensor value. |
| Logical observation | `3392/404` Sensor Value and `3392/909` Executing Object | 1 / OpenAIS | Links a logical value to an executing Object but does not classify the production method. |
| Virtual or derived | `3464/1-4` Integer, Float, Boolean, and String Values | 1 / uCIFI | All optional. The Object can hold virtual values but does not state whether they are estimated, inferred, predicted, or simulated. |

### Coverage Assessment

- **Measured:** Existing coverage.
- **Estimated, inferred, predicted, simulated, or proxy-derived:** New OMA capability required.
- **Aggregated:** No general Public Lighting representation identified.

### Missing Semantics

- Controlled observation-method vocabulary
- Derivation and source-observation relationships
- Aggregation function and window
- Model identity for locally generated values

### Smart Data Model Responsibility

The Smart Data Model should carry external model provenance, simulation lineage, and analytical workflow information. OMA should report such information only when the value is calculated locally or affects local operation.

### Recommendation to the OMA Smart Cities Working Group

Define reusable observation-method metadata. Consider extending Source 0 Object 509 so that method metadata can be linked to an existing sensor Object Instance.

## Water Management and Irrigation

### Municipality Operational Need

A municipality must distinguish measured soil moisture, pressure, flow, and water quality from estimates, forecasts, model-derived irrigation needs, and time-aggregated readings.

### Required OMA Contribution

**Telemetry**

- Measured or derived value
- Time interval when the value represents a period

**Metadata and relationships**

- Observation method
- Aggregation function
- Prediction horizon or forecast validity when generated locally
- Source observations or local model identifier when operationally relevant

### Existing Object and Resource Evidence

| Method | Evidence | Source / Owner | Assessment |
|---|---|---|---|
| Measured | Reusable `5700` Sensor Value in Objects 3300, 3319, 3320, 3323, 3325, 3326, 3327, and 3346 | 1 / IPSO Alliance | Explicit measured-value semantics. |
| Measured | Object-specific measurements in Objects 3424, 3426, 3427, and 3445 | 1 / uCIFI | Domain-specific measured values. |
| Virtual or derived | `3464/1-4` Virtual Sensor values | 1 / uCIFI | Method and derivation are unspecified. |
| Interval aggregation | `10266/6000-6029`, `10269/6000-6029`, `10487/6000-6029`, and `10507/6000-6029` | 2 / South East Water Corporation | Private precedent. Interval width and temporal boundaries exist, but aggregation function is not generally explicit. |

### Coverage Assessment

- **Measured:** Existing coverage.
- **Aggregated:** Private precedent requiring generalization.
- **Estimated, inferred, predicted, simulated, or proxy-derived:** New OMA capability required.

### Missing Semantics

- Controlled observation-method vocabulary
- Aggregation function, including sum, mean, minimum, maximum, or other method
- Prediction horizon and validity interval
- Link to local source observations or model

### Smart Data Model Responsibility

The Smart Data Model should represent externally generated forecasts, irrigation recommendations, analytical lineage, and model provenance. OMA should represent locally generated predictions or recommendations when they affect device operation.

### Recommendation to the OMA Smart Cities Working Group

Use the Source 2 interval Objects as implementation evidence, but create a Source 0 generalized mechanism if OMA standardizes interval observations. Define reusable observation-method and aggregation metadata.

## Shared Cross-Domain Finding

Measured values are well represented. The principal cross-domain gap is the absence of standardized method metadata. Method must not be inferred from an Object name such as `Virtual Sensor`.

---

# OMA Question 4

> How is the observation location represented?

## Public Lighting

### Municipality Operational Need

Illuminance measured inside a luminaire, at the pole, or on a road surface has different operational meaning. Municipality comparisons require the actual observation point and represented public space.

### Required OMA Contribution

**Telemetry**

- Coordinates or local position when measured or configured on the device

**Metadata and relationships**

- Type of observation point
- Link between observation, sensor, and observation point
- Link to a locally known observed asset or feature

### Existing Object and Resource Evidence

| Object and Resource | Source / Owner | Requirement status | Reuse | Assessment |
|---|---|---|---|---|
| `6/0` Latitude; `6/1` Longitude; `6/5` Timestamp | 0 / OMA | M | Object-specific | Represents Client location and location time, not necessarily measurement location. |
| `3336/6051` Numeric Latitude; `3336/6052` Numeric Longitude | 1 / IPSO Alliance | M | Reusable | Represents sensor/device position but has no general link to Object 3301. |
| `3398/908` Mounting Location | 1 / OpenAIS | M | Object-specific | Explicit site-specific free text; no controlled Public Lighting terminology. |
| `3392/909` Executing Object | 1 / OpenAIS | M | Object-specific | Links a logical illuminance sensor to an executing Object. |
| `509/0` Linked Sensor | 0 / OMA | M | Object-specific | Links measurement metadata to a sensor but not to an observation point. |

### Coverage Assessment

**Existing coverage requiring clarification or extension.**

Location can describe the Client or sensor, but not reliably the road surface, reference plane, or public-space feature represented by the observation.

### Missing Semantics

- Controlled Public Lighting observation-point type
- Link from measurement to observation point
- Distinction between device location and represented-feature location

### Smart Data Model Responsibility

The Smart Data Model should relate the OMA observation point to a road, street, pavement, pedestrian area, or public-space entity.

### Recommendation to the OMA Smart Cities Working Group

Define observation-point metadata separately from generic Client location. Provide an explicit link from measurement metadata to the observation point.

## Water Management and Irrigation

### Municipality Operational Need

Pressure at a pump differs from pressure at a consumer. Soil moisture near the surface differs from moisture at root depth. Flow at a valve differs from water delivered to an irrigation zone.

### Required OMA Contribution

**Telemetry**

- Coordinates, depth, or local position when known by the device

**Configuration or operational intent**

- Sensor offset or locally required installation geometry

**Metadata and relationships**

- Observation-point type
- Link to local pipeline, valve, meter, tank, soil layer, root zone, or endpoint when known locally

### Existing Object and Resource Evidence

| Object and Resource | Source / Owner | Requirement status | Reuse | Assessment |
|---|---|---|---|---|
| `6/0-1` Latitude and Longitude | 0 / OMA | M | Object-specific | Client location, not a general observation-point relationship. |
| `3336/6051-6052` Numeric Latitude and Longitude | 1 / IPSO Alliance | M | Reusable | Sensor/device position without a link to the water observation. |
| `10502/3-4` Tank GPS Longitude and Latitude | 2 / South East Water Corporation | M | Object-specific | Private tank-specific precedent. |
| `10502/1` Sensor Offset | 2 / South East Water Corporation | M | Object-specific | Private precedent for locally required sensor geometry. |
| `509/0` Linked Sensor | 0 / OMA | M | Object-specific | Source 0 link to a sensor, but no observation-point or observed-feature link. |

### Coverage Assessment

**Existing coverage requiring extension.**

The Registry can represent coordinates and some private installation metadata, but cannot generally identify consumer delivery point, network position, soil layer, or root zone.

### Missing Semantics

- Controlled Water/Irrigation observation-point type
- Soil depth and root-zone semantics
- Network-position and consumer-endpoint relationships
- Distinction between device location and represented location

### Smart Data Model Responsibility

The Smart Data Model should relate the OMA observation point to the municipal water network, irrigation topology, consumer, service area, plant, and root zone.

### Recommendation to the OMA Smart Cities Working Group

Define reusable observation-point and observed-feature relationships. Use private Object 10502 as implementation evidence for installation metadata, but standardize any general capability as Source 0.

## Shared Cross-Domain Finding

Generic Client location is insufficient for outcome interpretation. OMA needs to distinguish sensor location, observation point, and represented-feature location. The Smart Data Model then maps those identifiers into municipality geography and topology.

---

# OMA Question 5

> Which additional capabilities, if any, would improve representation of municipality service outcomes?

## Public Lighting

### Municipality Operational Need

Municipalities need interoperable illuminance observations that can be mapped to roads and public spaces and distinguished from luminaire output.

### Required OMA Contribution

- Controlled lighting observation-point semantics
- Explicit observation-to-point and observation-to-asset relationships
- Method, timestamp, unit, and quality metadata
- Locally required threshold or target only when used for autonomous operation

### Existing Object and Resource Evidence

Objects 3301, 3392, 3398, 3416, and 3417 collectively demonstrate the value, sensor, controller, physical-device, and luminaire-asset concepts. Object 509 provides a Source 0 measurement-metadata foundation. No single composition connects all concepts using reusable, cross-domain relationships.

### Coverage Assessment

**New OMA capability required for standardized relationships and method metadata. Existing Objects should be reused for physical quantities.**

### Missing Semantics

- Road-surface, pavement, pedestrian-area, pole, cabinet, and luminaire observation-point vocabulary
- Observed-feature and relevant-asset links
- Observation method and aggregation metadata
- Public Lighting profile requirements for optional measurement context

### Smart Data Model Responsibility

The Smart Data Model owns municipality geography, policy, required illumination, service areas, and compliance results.

### Recommendation to the OMA Smart Cities Working Group

1. Retain Object 3301 for illuminance.
2. Extend Object 509 or define reusable metadata Resources for observation point, observed feature, method, and aggregation.
3. Define a Public Lighting profile that constrains observation-point terms and requires appropriate timestamp, unit, and quality information.
4. Ensure measurements can be linked to Objects 3416 and 3417 when that relationship is locally known.

## Water Management and Irrigation

### Municipality Operational Need

Municipalities need outcome observations associated with consumer delivery points, irrigation zones, soil/root conditions, and relevant water-network locations.

### Required OMA Contribution

- Controlled water and irrigation observation-point semantics
- Standard soil-moisture/root-zone representation
- Explicit relationships to local assets and service endpoints
- Observation method and generalized interval/aggregation metadata
- Locally required targets, schedules, or thresholds only when needed for autonomous operation

### Existing Object and Resource Evidence

IPSO and uCIFI Objects provide most physical quantities. Source 2 South East Water Corporation Objects provide interval-observation and installation precedents. Object 509 provides a Source 0 link from metadata to a sensor but lacks the required observation context.

### Coverage Assessment

**Existing coverage requiring extension, plus new Source 0 capabilities for generalized metadata and interval observations.**

### Missing Semantics

- Standard soil-moisture and root-zone model
- Consumer endpoint, network position, soil layer, and irrigation-zone observation-point vocabulary
- Observed-feature and local-asset relationships
- Generalized aggregation function and observation method
- Water/Irrigation profile requirements for optional context

### Smart Data Model Responsibility

The Smart Data Model owns network topology, consumer and service-area relationships, plant requirements, municipal objectives, policies, and final service evaluation.

### Recommendation to the OMA Smart Cities Working Group

1. Reuse existing IPSO and uCIFI physical-quantity Objects.
2. Standardize soil-moisture/root-zone semantics.
3. Extend Object 509 or define reusable Source 0 metadata for observation point, observed feature, method, and aggregation.
4. Generalize the useful interval-data pattern demonstrated by Source 2 Objects into Source 0 if adopted by OMA.
5. Define a Water/Irrigation profile that makes necessary context mandatory.

## Shared Cross-Domain Recommendation

The OMA Smart Cities Working Group should consider a reusable Source 0 measurement-context pattern with the following semantic capabilities:

- Linked sensor
- Observation point
- Observed feature
- Relevant local asset or endpoint
- Observation method
- Aggregation function and interval
- Source observations when locally available
- Prediction horizon for locally generated predictions
- Timestamp, units, and measurement quality profile requirements

Municipality objectives, policies, service-area definitions, topology, and final service-outcome evaluation should remain outside OMA unless required for local device operation. OMA must provide stable identifiers and relationships that allow Smart Data Models to add that context without ambiguity.

---

# Service Outcome Disposition Summary

| Classification | Finding |
|---|---|
| Existing OMA coverage | Source 0 Location Object 6 and Measurement Metadata Object 509 provide useful foundations. |
| Existing coverage requiring clarification or extension | IPSO and uCIFI Objects provide most required physical measurements, but observation context and relationships are incomplete. |
| New OMA capability required | Observation-point and observed-feature relationships, observation-method classification, generalized aggregation semantics, and standardized soil-moisture/root-zone semantics. |
| Outside OMA responsibility but must remain linkable | Municipality objectives, policies, geographic service areas, infrastructure topology, plant requirements, consumer relationships, cross-device aggregation, and final outcome evaluation. |

---

# Semantic Capability 2: Infrastructure Output

## Capability Purpose

Infrastructure Output represents how the lighting infrastructure itself is behaving, independently of whether the resulting public-space illumination is adequate. It covers the light actually produced or commanded by a luminaire, the operating state of its control gear, and the anomalies that the infrastructure can detect about itself.

## Overall Capability Conclusion

**Existing OMA coverage, with clarification required for asset association.**

The uCIFI outdoor-lighting Objects maintained by OMA provide strong, purpose-built coverage of dimming level, color temperature, and control-gear operating state, including a rich set of alarm conditions. The main gap is not the availability of infrastructure telemetry, but the absence of a general, reusable relationship that formally binds a given output measurement to the luminaire asset and pole it belongs to, beyond co-location on the same LwM2M Client.

The uCIFI water Objects (Water Meter, Irrigation Valve, Pressure Monitoring Sensor) show the same pattern for the Water Management and Irrigation domain: pressure and valve-position telemetry are available and, in the case of Object 3425, already distinguish commanded, command-in-action, and measured status in the same three-tier pattern used by Object 3416 for lighting. The main gaps are the absence of a mandatory current flow-rate Resource in the Water Meter Object and the absence of a water-specific asset-identity Object comparable to the Luminaire Asset Object used for lighting.

---

# OMA Question 1

> Which existing LwM2M Objects and Resources represent infrastructure output?

## Public Lighting

### Municipality Operational Need

Municipalities need to know how much light each luminaire is actually producing or has been commanded to produce, independently of whether the resulting street illumination is adequate, so that infrastructure behaviour can be monitored, optimized, and maintained.

### Required OMA Contribution

**Telemetry**

- Dimming level and, when supported, color temperature actually applied by the luminaire
- Electrical quantities that characterize the light source output (voltage, current, active/apparent power at the control-gear output)

**Configuration or operational intent**

- Default dimming level and default color temperature applied when no schedule or manual override is active

### Existing Object and Resource Evidence

| Object | Resource evidence | Source / Owner | Requirement status | Reuse | Assessment |
|---|---|---|---|---|---|
| [`3416`](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/3416.xml) Outdoor Lamp Controller | `3416/3` Dimming level | 1 / uCIFI | M | Object-specific | Direct measured dimming level (0–100%) applied by the controller. |
| [`3416`](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/3416.xml) Outdoor Lamp Controller | `3416/40` Actual light color temperature | 1 / uCIFI | O | Object-specific | Conditional measured color temperature output. |
| [`3416`](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/3416.xml) Outdoor Lamp Controller | `3416/44` Light source voltage; `3416/45` Light source current; `3416/46` Light source active power | 1 / uCIFI | O | Object-specific | Electrical output measured at the control-gear output, describing the light source behaviour rather than the public-space result. |
| [`3311`](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/3311.xml) Light Control | `3311/5850` On/Off; `3311/5851` Dimmer | 1 / IPSO Alliance | M On/Off; O Dimmer | Reusable | Generic IPSO fallback representation of luminaire state; weaker than Object 3416 for street-lighting semantics. |
| [`3417`](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/3417.xml) Luminaire Asset | `3417/4` Nominal light output; `3417/7` Nominal input power | 1 / uCIFI | O | Object-specific | Nameplate capacity, not an observed output; useful as the reference against which actual output is compared. |
| [`3418`](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/3418.xml) Electrical Monitor | `3418/4` Active power; `3418/35` Dimming level | 1 / uCIFI | O | Object-specific | Instantaneous electrical power drawn by the luminaire, explicitly correlated with the dimming level in effect at the time of measurement (`3418/35`), giving an independent electrical-side corroboration of the output reported by Object 3416. |
| [`3418`](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/3418.xml) Electrical Monitor | `3418/1` Voltage; `3418/2` Current; `3418/5` Power factor | 1 / uCIFI | O | Object-specific | Supplementary electrical characteristics of the light source output, overlapping with the light-source electrical Resources already exposed by `3416/44-46` but measured from the metering side of the circuit rather than the control-gear side. |

### Coverage Assessment

**Existing OMA coverage.** Object 3416 directly and mandatorily reports the dimming level, and optionally reports color temperature and electrical quantities at the light-source output. Object 3418 complements this with an independent, metering-side view of instantaneous electrical output, explicitly tied to the dimming level in effect (`3418/35`), which allows infrastructure output to be corroborated from two separate measurement points on the same luminaire. This is purpose-built infrastructure output telemetry; note that Object 3418's cumulative energy Resources (e.g. `3418/6` Cumulated active energy) are addressed separately under Semantic Capability 3: Resource Consumption, since they describe consumption rather than instantaneous output.

### Missing Semantics

- No explicit relationship tagging a given output measurement instance as "infrastructure output" versus "service outcome" when both a 3416 or 3418 instance and a 3301 illuminance instance exist on the same Client.
- No Resource formally states that a given `3418` Instance and a given `3416` Instance are measuring the same physical luminaire, beyond co-location on the same Client (the same linked-asset gap already identified in the Overall Capability Conclusion).

### Smart Data Model Responsibility

The Smart Data Model should keep infrastructure output entities (luminaire, lamp) clearly separate from service-outcome entities (road, public space) and should be the layer that performs the comparison between commanded/produced output and observed illumination.

### Recommendation to the OMA Smart Cities Working Group

Retain Object 3416 as the primary infrastructure-output Object for street lighting. Document explicitly, in a Public Lighting profile, that Resources in 3416 represent infrastructure behaviour and must not be interpreted as service outcome.

## Water Management and Irrigation

### Municipality Operational Need

Municipalities need to know the actual opening level of an irrigation valve, the actual pressure maintained at a monitored point in the distribution network, and the actual delivered flow, independently of whether the resulting irrigation or consumer service outcome is adequate, so that network and irrigation infrastructure behaviour can be monitored and maintained.

### Required OMA Contribution

**Telemetry**

- Actual valve opening level achieved by an irrigation valve
- Measured water pressure at the monitored point
- Current or recent flow-rate extrema at the meter

**Configuration or operational intent**

- Default valve status applied when the device is powered on

### Existing Object and Resource Evidence

| Object | Resource evidence | Source / Owner | Requirement status | Reuse | Assessment |
|---|---|---|---|---|---|
| [`3425`](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/3425.xml) Irrigation Valve | `3425/2` Status | 1 / uCIFI | O | Object-specific | Direct measured valve opening level (0–100%) actually achieved, the water-domain analogue of the measured Dimming level in Object 3416. |
| `3425` Irrigation Valve | `3425/3` Command; `3425/4` Command in action | 1 / uCIFI | O | Object-specific | The same Command / Command-in-action / measured-status three-tier pattern already identified in Object 3416, explicitly accounting for LPWAN propagation delay between a sent command and the value actually applied. |
| [`3427`](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/3427.xml) Pressure Monitoring Sensor | `3427/1` Pressure | 1 / uCIFI | M | Object-specific | Mandatory measured water pressure output at the monitored point in the distribution network. |
| [`3424`](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/3424.xml) Water Meter | `3424/7` Minimum flow rate; `3424/8` Maximum flow rate | 1 / uCIFI | O | Object-specific | Flow-rate extrema recorded since the last metering value; the closest available proxy to an instantaneous delivered-flow output, since no direct current flow-rate Resource is defined. |
| `3424` Water Meter | `3424/1` Cumulated water volume | 1 / uCIFI | M | Object-specific | Cumulative delivered volume; addressed separately under Semantic Capability 3: Resource Consumption, mirroring the same cumulative/instantaneous split already noted for Object 3418. |

### Coverage Assessment

**Existing coverage requiring clarification or extension.** Object 3427 mandatorily reports measured pressure, and Object 3425 already separates commanded, command-in-action, and measured valve status. Object 3424 has no mandatory, direct current flow-rate Resource; min/max flow-rate extrema are the only available proxy for instantaneous delivered flow.

### Missing Semantics

- No mandatory or optional "current flow rate" Resource in Object 3424; instantaneous delivered-flow output must be inferred from optional min/max extrema or derived from successive cumulative-volume readings.
- No Resource formally states that a given `3424`, `3425`, and `3427` Instance describe the same irrigation zone or network segment, beyond co-location on the same Client (the same linked-asset gap identified for lighting).

### Smart Data Model Responsibility

The Smart Data Model should derive instantaneous flow by differentiating successive cumulative-volume readings when no direct flow Resource is reported, and should correlate meter, valve, and pressure-sensor Instances into a single irrigation zone or network-segment entity.

### Recommendation to the OMA Smart Cities Working Group

Add a current flow-rate Resource to Object 3424, consistent with the direct "last or current" measurement pattern already used by `3427/1` Pressure. Extend the linked-asset relationship recommended for Public Lighting (Question 3) to also bind 3424, 3425, and 3427 Instances to a common irrigation zone or network segment.

---

# OMA Question 2

> How are operating states represented?

## Public Lighting

### Municipality Operational Need

Municipalities need to know whether a luminaire is operating normally, degraded, or failed, so that maintenance can be planned and outages can be distinguished from dimming decisions.

### Required OMA Contribution

**Telemetry**

- Boolean or enumerated fault indicators for the lamp, control gear, and relay
- A reason code narrowing down the type of failure when available

### Existing Object and Resource Evidence

| Object | Resource evidence | Source / Owner | Requirement status | Reuse | Assessment |
|---|---|---|---|---|---|
| [`3416`](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/3416.xml) Outdoor Lamp Controller | `3416/5` Lamp failure; `3416/6` Lamp failure reason | 1 / uCIFI | O | Object-specific | Boolean failure flag plus a bitmask reason (open circuit, short circuit, thermal derating, thermal shutdown). |
| [`3416`](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/3416.xml) Outdoor Lamp Controller | `3416/7` Control gear failure; `3416/8` Control gear failure reason | 1 / uCIFI | O | Object-specific | DALI/0–10V-derived control-gear failure with a DiiA-aligned reason bitmask. |
| [`3416`](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/3416.xml) Outdoor Lamp Controller | `3416/9` Relay failure; `3416/10` Day burner; `3416/11` Cycling failure; `3416/12` Control gear communication failure | 1 / uCIFI | O | Object-specific | Additional discrete operating-state anomalies (relay stuck, lamp on when it should be off, excessive switching, DALI bus silence). |
| [`3416`](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/3416.xml) Outdoor Lamp Controller | `3416/21` Control gear temperature; `3416/22` Control gear thermal derating; `3416/25` Control gear thermal shutdown | 1 / uCIFI | O | Object-specific | Thermal operating-state indicators with associated counters (`3416/23`, `3416/26`). |
| [`3416`](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/3416.xml) Outdoor Lamp Controller | `3416/65` Lamp max operating hours exceeded | 1 / uCIFI | O | Object-specific | End-of-life operating-state indicator, driven by a configurable threshold (`3416/64`). |

### Coverage Assessment

**Existing OMA coverage.** Object 3416 provides one of the most granular operating-state models in the Registry for any Smart Cities domain, covering lamp, control gear, relay, and thermal states, each with optional reason codes.

### Missing Semantics

- All operating-state Resources are optional; a Public Lighting profile does not yet mandate a minimum subset for interoperable fault reporting.
- No controlled severity or urgency classification distinguishes a minor derating event from a lamp failure requiring dispatch.

### Smart Data Model Responsibility

The Smart Data Model should convert raw operating-state flags into work-order-ready maintenance events, associating them with asset ownership, warranty, and crew assignment.

### Recommendation to the OMA Smart Cities Working Group

Define a Public Lighting profile that makes a minimum operating-state subset (lamp failure, control gear failure, relay failure) mandatory for interoperable fault detection across vendors.

## Water Management and Irrigation

### Municipality Operational Need

Municipalities need to know whether a water meter, irrigation valve, or pressure sensor is operating normally, degraded, or failed, so that leaks, fraud, and valve malfunctions can be distinguished from a legitimate drop in demand or pressure.

### Required OMA Contribution

**Telemetry**

- Boolean or enumerated anomaly indicators for leaks, back flow, blockage, fraud, and hammer effect
- An indicator that a configured schedule cannot be executed by an irrigation valve

### Existing Object and Resource Evidence

| Object | Resource evidence | Source / Owner | Requirement status | Reuse | Assessment |
|---|---|---|---|---|---|
| [`3424`](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/3424.xml) Water Meter | `3424/9` Leak suspected; `3424/10` Leak detected | 1 / uCIFI | O | Object-specific | Two-stage leak indication, from a lower-confidence suspicion to a confirmed detection. |
| `3424` Water Meter | `3424/11` Back flow detected; `3424/12` Blocked meter; `3424/13` Fraud detected | 1 / uCIFI | O | Object-specific | Additional discrete anomaly flags covering network and meter-integrity conditions. |
| [`3427`](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/3427.xml) Pressure Monitoring Sensor | `3427/3` Leak detected; `3427/4` Hammer effect detected | 1 / uCIFI | O | Object-specific | Pressure-side leak confirmation, independent of the meter-side indication in Object 3424, plus a water-hammer anomaly specific to pressurized pipelines. |
| [`3425`](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/3425.xml) Irrigation Valve | `3425/6` Invalid scheduler | 1 / uCIFI | O | Object-specific | Indicates that an assigned scheduler cannot be executed or is unsupported by the valve, an operating-state anomaly specific to autonomous irrigation control. |

### Coverage Assessment

**Existing OMA coverage.** The combination of Objects 3424 and 3427 provides complementary, two-sided leak detection (meter-side and pressure-side) plus fraud, blockage, and back-flow indicators, and Object 3425 reports scheduler-execution failures.

### Missing Semantics

- All anomaly Resources are optional; no Water/Irrigation profile currently mandates a minimum subset for interoperable fault reporting.
- Unlike Object 3416's bitmask failure-reason Resources, none of the water anomaly flags carry an accompanying reason code to narrow down the root cause.

### Smart Data Model Responsibility

The Smart Data Model should convert raw anomaly flags into work-order-ready maintenance events, associating them with asset ownership and crew assignment, and should correlate meter-side and pressure-side leak indications into a single leak event.

### Recommendation to the OMA Smart Cities Working Group

Define a Water/Irrigation profile that makes a minimum anomaly subset (leak detected, invalid scheduler) mandatory, and consider adding a reason/bitmask Resource to the water anomaly flags, analogous to the failure-reason Resources already defined in Object 3416.

---

# OMA Question 3

> How are output measurements associated with the corresponding assets?

## Public Lighting

### Municipality Operational Need

Municipalities need to know which physical luminaire, pole, or cabinet produced a given output measurement in order to route maintenance and to associate output history with a specific piece of equipment.

### Required OMA Contribution

**Metadata and relationships**

- Identifier linking a controller instance to the physical luminaire asset it drives
- Manufacturer and nameplate identity of that asset

### Existing Object and Resource Evidence

| Object | Resource evidence | Source / Owner | Requirement status | Reuse | Assessment |
|---|---|---|---|---|---|
| [`3410`](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/3410.xml) Device Extension | `3410/4` Asset identifier | 1 / uCIFI | O | Object-specific | Free-text identifier of the asset (e.g. luminaire) controlled by the device; the association depends on consistent population by the installer. |
| [`3417`](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/3417.xml) Luminaire Asset | `3417/1` Asset GTIN; `3417/13` Luminaire identification; `3417/14` Luminaire identification number | 1 / uCIFI | M GTIN; O identification | Object-specific | Manufacturer-assigned identity of the luminaire, but no Resource formally links a specific `3417` Instance to the `3416` Instance that controls it other than co-location on the same Client. |

### Coverage Assessment

**Existing coverage requiring clarification or extension.** Identity Resources exist in Objects 3410 and 3417, but there is no dedicated, generalized Resource that links a `3416` or `3418` measurement Instance to its corresponding `3417` Luminaire Asset Instance.

### Missing Semantics

- A reusable "linked asset" relationship, e.g. Core Link pattern, applicable to measurement and control Objects.

### Smart Data Model Responsibility

The Smart Data Model should maintain the authoritative asset register (pole, luminaire, cabinet) and resolve the device-to-asset relationship into a stable Digital Twin entity graph.

### Recommendation to the OMA Smart Cities Working Group

Generalize the Core Link output-reference pattern into a reusable "linked asset" Resource that measurement and control Objects such as 3416 and 3418 can adopt.

## Water Management and Irrigation

### Municipality Operational Need

Municipalities need to know which physical water meter, irrigation valve, or pressure sensor produced a given output measurement in order to route maintenance and to associate output history with a specific piece of network or irrigation equipment.

### Required OMA Contribution

**Metadata and relationships**

- Identifier linking a meter, valve, or pressure-sensor Instance to the physical asset it represents
- Manufacturer and nameplate identity of that asset

### Existing Object and Resource Evidence

| Object | Resource evidence | Source / Owner | Requirement status | Reuse | Assessment |
|---|---|---|---|---|---|
| [`3410`](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/3410.xml) Device Extension | `3410/4` Asset identifier | 1 / uCIFI | O | Object-specific | Same generic free-text asset-identifier Resource used for Public Lighting; reusable for a water meter, valve, or pressure-sensor Instance when the Client also exposes Object 3410. |
| [`3424`](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/3424.xml) Water Meter | `3424/3` Type of meter | 1 / uCIFI | O | Object-specific | Free-text meter-type description; identifies a category of equipment, not a specific physical asset instance. |

### Coverage Assessment

**Existing coverage requiring clarification or extension.** Unlike Public Lighting, which has a dedicated Luminaire Asset Object (3417) with a mandatory GTIN, the Water Management and Irrigation domain has no equivalent water-specific asset-identity Object; the only available mechanism is the generic, optional, free-text Asset identifier in Object 3410.

### Missing Semantics

- No dedicated water/irrigation asset-identity Object (GTIN, manufacturer, year of manufacture) comparable to the Luminaire Asset Object used for lighting.
- No Resource formally links a `3424`, `3425`, or `3427` Instance to the pipe, zone, or parcel it is installed on.

### Smart Data Model Responsibility

The Smart Data Model should maintain the authoritative asset register for meters, valves, and pressure sensors (make, model, installation location, network segment) since OMA does not currently define a water-specific nameplate Object.

### Recommendation to the OMA Smart Cities Working Group

Evaluate whether a water-specific asset Object, patterned on the Luminaire Asset Object, is warranted; in the meantime, document that Object 3410 Asset identifier is the generic cross-domain mechanism and ensure it is consistently populated for water and irrigation equipment.

---

# OMA Question 4

> Which additional capabilities, if any, would improve representation of infrastructure behaviour?

## Public Lighting

### Required OMA Contribution

- A reusable linked-asset relationship (see Question 3)
- A profile-level minimum mandatory operating-state subset (see Question 2)
- A controlled severity/urgency classification for operating-state anomalies

### Coverage Assessment

**Existing coverage requiring extension.** The underlying telemetry is strong; the missing pieces are profiling and relationship generalization rather than new measurement Resources.

### Smart Data Model Responsibility

Severity triage, maintenance prioritization, and cross-asset comparison belong in the Smart Data Model / Digital Twin layer.

### Recommendation to the OMA Smart Cities Working Group

Prioritize a Public Lighting profile over new Object definitions: the Registry's infrastructure-output vocabulary is already rich, but it is under-constrained by mandatory status and relationship generalization.

## Water Management and Irrigation

### Required OMA Contribution

- A mandatory current flow-rate Resource in Object 3424 (see Question 1)
- A minimum mandatory anomaly subset across Objects 3424, 3425, and 3427 (see Question 2)
- A reusable linked-asset relationship binding meter, valve, and pressure-sensor Instances (see Question 1)
- Evaluation of a dedicated water/irrigation asset-identity Object (see Question 3)

### Coverage Assessment

**Existing coverage requiring extension.** Pressure and anomaly telemetry are strong; the main gaps are a missing current flow-rate Resource in Object 3424 and the absence of a water-specific asset-identity Object, in addition to the same profiling and relationship-generalization gaps identified for lighting.

### Smart Data Model Responsibility

Severity triage, maintenance prioritization, and cross-asset comparison belong in the Smart Data Model / Digital Twin layer, as for Public Lighting.

### Recommendation to the OMA Smart Cities Working Group

Add a current flow-rate Resource to Object 3424 as a genuine telemetry gap; otherwise prioritize profiling and the shared linked-asset relationship over new Object definitions.

---

# Infrastructure Output Disposition Summary

| Classification | Finding |
|---|---|
| Existing OMA coverage | Object 3416 dimming level, color temperature, and a rich operating-state/alarm model; Object 3418 electrical output at the light source; Object 3427 mandatory pressure and Object 3425's Command/Command-in-action/Status pattern; broad leak, fraud, and back-flow anomaly flags across Objects 3424 and 3427. |
| Existing coverage requiring clarification or extension | Asset-linking between controller, meter, and luminaire or water-asset Instances; mandatory profile subset for fault reporting in both domains. |
| New OMA capability required | A current flow-rate Resource for Object 3424; otherwise a reusable linked-asset relationship and profiling are sufficient for both domains. |
| Outside OMA responsibility but must remain linkable | Maintenance prioritization, work-order generation, and comparison against service outcome. |

---

# Semantic Capability 3: Resource Consumption

## Capability Purpose

Resource Consumption represents the energy consumed to deliver the public lighting service, independently of the light output achieved or the service outcome experienced. It supports efficiency analysis, energy budgeting, and the evaluation of dimming or maintenance strategies against their energy impact.

## Overall Capability Conclusion

**Existing OMA coverage.**

The uCIFI electrical Objects maintained by OMA (Electrical Monitor, Single-Phase Electrical Meter, Three-Phase Electrical Meter Complement) provide mature, Zhaga/D4i-aligned energy measurement at both the single light-point level and the cabinet/feeder level. The main clarification required is how a single light-point measurement should be aggregated into cabinet, zone, or municipality totals, which is a Smart Data Model responsibility, and how consumption should be explicitly linked to the service outcome it supports.

The uCIFI Water Meter Object provides a directly analogous mandatory cumulative-consumption Resource, in m3 rather than Wh, but has no equivalent of Object 3422's linked-instance aggregation pattern for combining multiple meters into a network-segment or zone total.

---

# OMA Question 1

> Which existing LwM2M Objects and Resources represent resource consumption?

## Public Lighting

### Municipality Operational Need

Municipalities need to know how much energy is required to provide the public lighting service, at the level of an individual luminaire, a cabinet, or a zone, in order to manage energy budgets and evaluate efficiency programs.

### Required OMA Contribution

**Telemetry**

- Cumulated active, reactive, and apparent energy
- Instantaneous active, reactive, and apparent power
- Voltage, current, frequency, and power factor supporting energy quality analysis

### Existing Object and Resource Evidence

| Object | Resource evidence | Source / Owner | Requirement status | Reuse | Assessment |
|---|---|---|---|---|---|
| [`3418`](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/3418.xml) Electrical Monitor | `3418/6` Cumulated active energy; `3418/30` Reactive energy; `3418/36` Apparent Energy | 1 / uCIFI | O | Object-specific | Single light-point cumulative energy since last reset (`3418/7` Energy reset). |
| [`3418`](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/3418.xml) Electrical Monitor | `3418/4` Active power; `3418/29` Reactive power; `3418/37` Apparent Power | 1 / uCIFI | O | Object-specific | Instantaneous power at the individual luminaire. |
| [`3421`](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/3421.xml) Single-Phase Electrical Meter | `3421/25` Active energy import (+A) Un | 1 / uCIFI | M | Object-specific | Mandatory cumulative active-energy import at a single-phase feeder (e.g. lighting cabinet circuit). |
| [`3421`](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/3421.xml) Single-Phase Electrical Meter | `3421/16` Active power+ (QI+QIV) | 1 / uCIFI | M | Object-specific | Mandatory instantaneous active power import. |
| [`3422`](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/3422.xml) Three-Phase Electrical Meter Complement | `3422/17` Active energy import Un; `3422/8` Total active power import on the 3 lines | 1 / uCIFI | M | Object-specific | Mandatory cumulative and instantaneous active energy/power across all three lines of a cabinet feeder, combined with three associated `3421` Instances (`3422/36-38` L1/L2/L3 Meter Instance). |

### Coverage Assessment

**Existing OMA coverage.** Energy and power are represented at both the single light-point scale (3418) and the feeder/cabinet scale (3421, 3422), covering single-phase and three-phase installations.

### Missing Semantics

- No explicit Resource states whether a given energy value supports the lighting service outcome versus other loads sharing the same cabinet.

### Smart Data Model Responsibility

The Smart Data Model should aggregate consumption across luminaires, cabinets, and zones, and associate it with the illumination service outcome it supports.

### Recommendation to the OMA Smart Cities Working Group

No new Objects are required. Reuse 3418, 3421, and 3422 as the standard consumption Objects for Public Lighting profiles.

## Water Management and Irrigation

### Municipality Operational Need

Municipalities need to know how much water is delivered through an individual meter, in order to manage network losses, consumer billing, and irrigation budgets.

### Required OMA Contribution

**Telemetry**

- Cumulated delivered water volume
- Flow-rate extrema supporting consumption-pattern analysis

### Existing Object and Resource Evidence

| Object | Resource evidence | Source / Owner | Requirement status | Reuse | Assessment |
|---|---|---|---|---|---|
| [`3424`](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/3424.xml) Water Meter | `3424/1` Cumulated water volume | 1 / uCIFI | M | Object-specific | Mandatory cumulative delivered volume since last reset (`3424/2` Cumulated water meter value reset), the direct water-domain analogue of `3418/6` Cumulated active energy. |
| `3424` Water Meter | `3424/4` Cumulated pulse value; `3424/6` Pulse ratio | 1 / uCIFI | O | Object-specific | Alternate raw-pulse representation of the same cumulative consumption, convertible to volume via the pulse ratio; a redundancy pattern not present in the electrical Objects. |
| `3424` Water Meter | `3424/7` Minimum flow rate; `3424/8` Maximum flow rate | 1 / uCIFI | O | Object-specific | Flow-rate extrema since the last metering value, supporting consumption-pattern analysis in the absence of an instantaneous flow Resource (see Semantic Capability 2, Question 1). |

### Coverage Assessment

**Existing OMA coverage.** Object 3424 provides a mandatory, unit-consistent cumulative-volume Resource directly analogous to `3418/6`, plus a redundant pulse-based representation not found in the electrical Objects.

### Missing Semantics

- No explicit Resource states whether a given 3424 Instance's volume supports an irrigation service outcome versus another use (e.g. a shared distribution-network connection), mirroring the same gap already identified for electrical consumption.

### Smart Data Model Responsibility

The Smart Data Model should aggregate consumption across meters, zones, and parcels, and associate it with the irrigation service outcome it supports, consistent with the `WaterConsumptionObserved` mapping already identified for Object 3424.

### Recommendation to the OMA Smart Cities Working Group

No new Objects are required. Reuse Object 3424 as the standard consumption Object for Water Management and Irrigation profiles, consistent with the role played by 3418/3421/3422 for Public Lighting.

---

# OMA Question 2

> Can energy, water, fuel, or battery usage be represented consistently?

## Public Lighting

### Required OMA Contribution

Consistent units and consistent semantics (import/export, instantaneous vs. cumulative) across single light-point and feeder-level measurements.

### Existing Object and Resource Evidence

| Object | Resource evidence | Source / Owner | Assessment |
|---|---|---|---|
| [`3418`](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/3418.xml) Electrical Monitor | `3418/6` Cumulated active energy (Wh) | 1 / uCIFI | Consistent unit and semantics with 3421/3422. |
| [`3421`](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/3421.xml) Single-Phase Electrical Meter | `3421/25` Active energy import (Wh); `3421/26` Active energy export (Wh) | 1 / uCIFI | Explicit import/export distinction, more granular than 3418. |
| [`3422`](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/3422.xml) Three-Phase Electrical Meter Complement | `3422/17` Active energy import Un (Wh) | 1 / uCIFI | Same unit and naming convention as 3421, confirming cross-object consistency. |
| [`3`](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/3.xml) Device | `3/9` Battery Level | 0 / OMA | Percentage-based battery usage; consistent for battery-powered auxiliary sensors but not the light source itself, which is normally mains-powered. |

### Coverage Assessment

**Existing OMA coverage.** All three uCIFI electrical Objects share the same unified-rate energy naming convention (`Un`) and Wh/varh/VAh units, so values are consistently representable and comparable across scales.

### Missing Semantics

None specific to unit or semantic consistency; only cross-object aggregation guidance is missing (Smart Data Model responsibility).

### Smart Data Model Responsibility

Aggregation and normalization across mixed single-phase/three-phase deployments.

### Recommendation to the OMA Smart Cities Working Group

None required beyond continuing to require the unified-rate (`Un`) naming convention in any future electrical metering Object.

## Water Management and Irrigation

### Existing Object and Resource Evidence

| Object | Resource evidence | Source / Owner | Assessment |
|---|---|---|---|
| [`3424`](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/3424.xml) Water Meter | `3424/1` Cumulated water volume (m3) | 1 / uCIFI | A single, consistent volumetric unit, directly comparable across meter Instances and distinct from the electrical Wh/varh/VAh family of units. |
| `3424` Water Meter | `3424/7-8` Minimum/Maximum flow rate (m3/s) | 1 / uCIFI | Consistent SI-derived flow unit, enabling direct comparison with any future instantaneous flow-rate Resource (see Semantic Capability 2, Question 1). |

### Coverage Assessment

**Existing OMA coverage.** Water volume and flow-rate units are internally consistent within Object 3424; cross-domain consistency with energy/fuel/battery usage is not required, since water is a distinct resource type with its own SI-derived unit family.

### Missing Semantics

None specific to unit or semantic consistency within the water domain.

### Smart Data Model Responsibility

Normalizing water, energy, and other resource-consumption types into a common municipal resource-budgeting view.

### Recommendation to the OMA Smart Cities Working Group

None required; continue using m3 and m3/s consistently in any future water-metering Resource.

---

# OMA Question 3

> Are electrical measurements sufficiently complete for operational efficiency analysis?

## Public Lighting

### Existing Object and Resource Evidence

| Object | Resource evidence | Source / Owner | Assessment |
|---|---|---|---|
| [`3421`](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/3421.xml) Single-Phase Electrical Meter | `3421/13` Instantaneous Power Factor; `3421/1` Voltage; `3421/6` Current | 1 / uCIFI | Mandatory power-quality Resources sufficient for efficiency analysis. |
| [`3418`](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/3418.xml) Electrical Monitor | `3418/5` Power factor; `3418/35` Dimming level | 1 / uCIFI | Power factor associated with the dimming level in effect at the time of measurement, enabling efficiency-vs-dimming analysis. |
| [`3421`](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/3421.xml) Single-Phase Electrical Meter | `3421/37-52` power-failure and voltage-sag/swell counters | 1 / uCIFI | Power-quality event counters that support root-cause analysis of consumption anomalies. |

### Coverage Assessment

**Existing OMA coverage.** The combination of power factor, voltage, current, and dimming-level association (Resource 3418/35) is sufficient for operational efficiency analysis at the light-point level.

### Missing Semantics

None material; efficiency benchmarking across assets is a Smart Data Model analytics function, not a device semantic gap.

### Smart Data Model Responsibility

Benchmarking efficiency across luminaires, cabinets, and time periods.

### Recommendation to the OMA Smart Cities Working Group

None required.

## Water Management and Irrigation

### Existing Object and Resource Evidence

| Object | Resource evidence | Source / Owner | Assessment |
|---|---|---|---|
| [`3424`](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/3424.xml) Water Meter | `3424/9-13` Leak suspected/detected, back flow, blocked meter, fraud detected | 1 / uCIFI | Anomaly flags supporting root-cause analysis of consumption irregularities, the water-domain analogue of the voltage-sag/swell counters in Object 3421. |
| [`3427`](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/3427.xml) Pressure Monitoring Sensor | `3427/1` Pressure | 1 / uCIFI | Mandatory pressure context supporting efficiency and network-loss analysis alongside delivered volume. |

### Coverage Assessment

**Existing OMA coverage.** The combination of cumulative volume, flow-rate extrema, pressure, and anomaly flags is sufficient for operational efficiency analysis at the meter level; no electrical-style power-factor equivalent exists for water, but none is operationally required.

### Missing Semantics

None material; benchmarking efficiency across meters and zones is a Smart Data Model analytics function, not a device semantic gap.

### Smart Data Model Responsibility

Benchmarking consumption efficiency and network loss across meters, zones, and time periods.

### Recommendation to the OMA Smart Cities Working Group

None required.

---

# OMA Question 4

> Can resource consumption be associated with the asset, group, cabinet, zone, or service outcome it supports?

## Public Lighting

### Existing Object and Resource Evidence

| Object | Resource evidence | Source / Owner | Assessment |
|---|---|---|---|
| [`3418`](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/3418.xml) Electrical Monitor | Object scope is intrinsically a single light point | 1 / uCIFI | Scope is implicit in Object identity, not stated by a Resource. |
| [`3421`](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/3421.xml) Single-Phase Electrical Meter | Object scope is intrinsically a single-phase feeder circuit (e.g. a lighting cabinet circuit serving many luminaires) | 1 / uCIFI | Scope is implicit in Object identity, one level above 3418; a `3421` Instance is the constituent unit that 3422 references explicitly (see below), but nothing in 3421 itself states which luminaires are wired to that circuit. |
| [`3422`](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/3422.xml) Three-Phase Electrical Meter Complement | `3422/36-38` L1/L2/L3 Meter Instance | 1 / uCIFI | Explicit Resource linking the cabinet-level three-phase Object to its three constituent single-phase `3421` meter Instances; this is the strongest example of scope linkage in the Registry, and it demonstrates that 3421 and 3422 are already designed to compose across scopes. |
| [`3410`](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/3410.xml) Device Extension | `3410/4` Asset identifier | 1 / uCIFI | Optional free-text link from the metering device to the asset/zone it serves. |

### Coverage Assessment

**Existing coverage requiring clarification or extension.** Object 3422 demonstrates that explicit scope linkage between related meter Instances is achievable within OMA, referencing its constituent 3421 Instances by design, but no equivalent mechanism links an individual 3418 Instance to the 3421 feeder circuit it is wired into, or to the illuminance service outcome the consumption ultimately supports.

### Missing Semantics

- A generalization of the 3422-to-3421 linked-instance pattern (`36-38`) to other scope relationships, such as light point (3418) to feeder circuit (3421), or feeder circuit to zone.

### Smart Data Model Responsibility

Zone, group, and service-outcome association of consumption values.

### Recommendation to the OMA Smart Cities Working Group

Generalize the linked-meter-instance pattern demonstrated by Object 3422 so it can express additional scope relationships beyond three-phase composition.

## Water Management and Irrigation

### Existing Object and Resource Evidence

| Object | Resource evidence | Source / Owner | Assessment |
|---|---|---|---|
| [`3424`](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/3424.xml) Water Meter | Object scope is intrinsically a single meter | 1 / uCIFI | Scope is implicit in Object identity, with no equivalent of the 3422 linked-instance pattern to aggregate several meters into a network segment or irrigation zone. |
| [`3410`](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/3410.xml) Device Extension | `3410/4` Asset identifier | 1 / uCIFI | Optional free-text link from the metering device to the asset/zone it serves, shared with Public Lighting. |

### Coverage Assessment

**Existing coverage requiring clarification or extension.** Unlike the electrical domain, the water domain has no Object analogous to 3422 that explicitly names constituent meter Instances; association with a zone, parcel, or service outcome relies entirely on the generic, optional Asset identifier.

### Missing Semantics

- A linked-meter-instance pattern for Object 3424, analogous to `3422/36-38`, to express that several meters together serve a given irrigation zone or network segment.

### Smart Data Model Responsibility

Zone, parcel, and service-outcome association of water consumption values.

### Recommendation to the OMA Smart Cities Working Group

Extend the same linked-instance generalization recommended for Object 3422 (Question 4, Public Lighting) to also cover Object 3424, so that water consumption can be explicitly scoped to a zone or network segment.

---

# Resource Consumption Disposition Summary

| Classification | Finding |
|---|---|
| Existing OMA coverage | Objects 3418, 3421, and 3422 provide consistent, unit-aligned energy and power measurements from light-point to cabinet scale; Object 3424 provides an analogous mandatory cumulative-volume Resource for water, with redundant pulse-based representation and rich anomaly flags. |
| Existing coverage requiring clarification or extension | Generalizing the 3422 linked-meter-instance pattern to other scope relationships, including Object 3424. |
| New OMA capability required | None identified. |
| Outside OMA responsibility but must remain linkable | Zone/group aggregation, efficiency benchmarking, and association with service outcome, for both energy and water consumption. |

---

# Semantic Capability 4: Observation Point

## Capability Purpose

Observation Point identifies where a measurement physically or logically originates, for example at the luminaire's control gear, at a cabinet feeder, or at the LwM2M Client itself, independently of the asset being described.

## Overall Capability Conclusion

**Existing coverage requiring clarification or extension.**

The Registry represents device/Client location precisely through Object 6, but it does not generally distinguish the observation point of an individual measurement Resource from the location of the Client that hosts it. This mirrors the finding already documented for Service Outcome (OMA Question 4).

The same gap applies to the Water Management and Irrigation domain, and is more pronounced there since no water-specific asset Object comparable to the Luminaire Asset Object (3417) exists to anchor a meter, valve, or pressure sensor Instance to a physical location beyond Client co-location.

---

# OMA Question 1

> Which existing Objects identify the observation point?

## Public Lighting

### Municipality Operational Need

Municipalities need to know whether a given electrical or dimming measurement originates from the luminaire, the cabinet feeder, or another point in the network, in order to interpret it correctly.

### Required OMA Contribution

**Telemetry**

- Coordinates or local position when measured or configured on the device

**Metadata and relationships**

- Type of observation point (luminaire, pole, cabinet)
- Link between the observation and the observation point

### Existing Object and Resource Evidence

| Object and Resource | Source / Owner | Requirement status | Reuse | Assessment |
|---|---|---|---|---|
| [`6`](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/6.xml)`/0` Latitude; `6/1` Longitude | 0 / OMA | M | Object-specific | Represents Client location; a 3416/3418 Instance co-located on the same Client inherits this location by association only. |
| `3417/1` Asset GTIN; `3417/13` Luminaire identification | 1 / uCIFI | M GTIN | Object-specific | Identifies the physical asset, but not a location or observation-point type. |
| `3410/4` Asset identifier | 1 / uCIFI | O | Object-specific | Free-text identifier that could encode a pole or cabinet reference, but with no controlled vocabulary. |

### Coverage Assessment

**Existing coverage requiring clarification or extension.** Location Object 6 and Asset identifiers exist, but there is no reusable, controlled observation-point type (luminaire vs. cabinet vs. feeder) analogous to the gap already identified for Service Outcome.

### Missing Semantics

- Controlled observation-point vocabulary for street-lighting equipment (luminaire, pole, cabinet, feeder)

### Smart Data Model Responsibility

The Smart Data Model should relate the OMA-reported Client/asset identity to the specific pole, cabinet, or street segment in municipality geography.

### Recommendation to the OMA Smart Cities Working Group

Reuse the same observation-point/observed-feature extension already recommended for Service Outcome (extending Object 509 or defining reusable metadata) so that it also covers infrastructure-output and consumption Objects such as 3416, 3418, 3421, and 3422.

## Water Management and Irrigation

### Municipality Operational Need

Municipalities need to know whether a given pressure, flow, or valve-position measurement originates from a specific meter chamber, valve pit, or network node, in order to interpret it correctly and route maintenance.

### Required OMA Contribution

**Metadata and relationships**

- Type of observation point (meter chamber, valve pit, network node)
- Link between the observation and the observation point

### Existing Object and Resource Evidence

| Object and Resource | Source / Owner | Requirement status | Reuse | Assessment |
|---|---|---|---|---|
| [`6`](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/6.xml)`/0` Latitude; `6/1` Longitude | 0 / OMA | M | Object-specific | Represents Client location; a 3424/3425/3427 Instance co-located on the same Client inherits this location by association only. |
| `3424/3` Type of meter | 1 / uCIFI | O | Object-specific | Free-text meter-type description, not a location or observation-point type. |
| `3410/4` Asset identifier | 1 / uCIFI | O | Object-specific | Free-text identifier that could encode a chamber or pit reference, but with no controlled vocabulary, shared with Public Lighting. |

### Coverage Assessment

**Existing coverage requiring clarification or extension.** The gap is identical to Public Lighting, and sharper, since the water domain has no equivalent of the Luminaire Asset Object (3417) to anchor physical-asset identity at all (see Semantic Capability 2, Question 3).

### Missing Semantics

- Controlled observation-point vocabulary for water and irrigation equipment (meter chamber, valve pit, network node, parcel).

### Smart Data Model Responsibility

The Smart Data Model should relate the OMA-reported Client/asset identity to the specific chamber, pit, or parcel in municipality or network geography.

### Recommendation to the OMA Smart Cities Working Group

Extend the same observation-point/observed-feature mechanism recommended for Public Lighting (Question 1) to cover Objects 3424, 3425, and 3427.

---

# OMA Question 2

> Can observation points be represented independently from asset identity?

## Public Lighting

### Existing Object and Resource Evidence

| Object and Resource | Source / Owner | Assessment |
|---|---|---|
| `6/0-1` Latitude/Longitude | 0 / OMA | Tied to the Client, not to an independent observation-point concept. |
| [`3417`](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/3417.xml) Luminaire Asset | Asset identity Resources | 1 / uCIFI | Identifies the asset, conflating asset identity and (implicitly) its location. |

### Coverage Assessment

**Existing coverage requiring extension.** Currently, observation point and asset identity are not modeled as independent concepts; location is a property of the Client, and asset identity is a property of the Luminaire Asset Object, with no explicit third concept for "point of observation."

### Missing Semantics

- A standalone observation-point concept, distinct from both Client location and asset identity.

### Smart Data Model Responsibility

Digital Twins should model observation point as a distinct, queryable attribute separate from asset identity.

### Recommendation to the OMA Smart Cities Working Group

Same recommendation as Question 1: a reusable observation-point Resource, independent from both Location (6) and Luminaire Asset (3417).

## Water Management and Irrigation

### Existing Object and Resource Evidence

| Object and Resource | Source / Owner | Assessment |
|---|---|---|
| `6/0-1` Latitude/Longitude | 0 / OMA | Tied to the Client, not to an independent observation-point concept. |
| `3424/3` Type of meter | 1 / uCIFI | Identifies a category of equipment, conflating (at best) asset type with location, with no independent observation-point concept. |

### Coverage Assessment

**Existing coverage requiring extension.** As for Public Lighting, observation point and asset identity are not modeled as independent concepts; the gap is sharper here since there is no water-specific asset Object at all.

### Missing Semantics

- A standalone observation-point concept, distinct from both Client location and the generic Asset identifier.

### Recommendation to the OMA Smart Cities Working Group

Same recommendation as for Public Lighting: a reusable observation-point Resource, independent from Location (6) and from whatever asset-identity mechanism is adopted for water equipment (see Semantic Capability 2, Question 3).

---

# OMA Question 3

> Can multiple observation points be associated with the same infrastructure asset?

## Public Lighting

### Existing Object and Resource Evidence

| Object and Resource | Source / Owner | Assessment |
|---|---|---|
| [`3418`](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/3418.xml) Electrical Monitor and `3416` Outdoor Lamp Controller co-located on the same Client | 1 / uCIFI | Multiple Object Instances can coexist on one Client (e.g. one luminaire with both a controller and an electrical monitor), but no Resource states that they observe the same physical asset from different points. |

### Coverage Assessment

**Indirect or ambiguous.** Co-location on the same Client is the only available signal; it is not an explicit relationship.

### Missing Semantics

- Explicit cross-Object relationship confirming that two Object Instances on the same Client refer to the same physical luminaire.

### Smart Data Model Responsibility

Should be possibly done at higher level, using Client identity as the correlation key until a native OMA relationship exists.

### Recommendation to the OMA Smart Cities Working Group

Consider a lightweight "co-observed asset" Core Link Resource so that multiple Object Instances describing the same physical luminaire can declare that relationship explicitly rather than relying on Client co-location.

## Water Management and Irrigation

### Existing Object and Resource Evidence

| Object and Resource | Source / Owner | Assessment |
|---|---|---|
| [`3427`](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/3427.xml) Pressure Monitoring Sensor and [`3425`](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/3425.xml) Irrigation Valve co-located on the same Client | 1 / uCIFI | Multiple Object Instances can coexist on one Client (e.g. a valve assembly with an integrated pressure sensor), but no Resource states that they observe the same physical asset from different points, mirroring the 3416/3418 co-location finding for Public Lighting. |

### Coverage Assessment

**Indirect or ambiguous.** Co-location on the same Client is the only available signal, as for Public Lighting.

### Missing Semantics

- Explicit cross-Object relationship confirming that two Object Instances on the same Client refer to the same physical valve or network node.

### Recommendation to the OMA Smart Cities Working Group

Extend the same "co-observed asset" Core Link Resource recommended for Public Lighting to Objects 3424, 3425, and 3427.

---

# OMA Question 4

> Which additional capabilities would improve observation point representation?

## Public Lighting

### Required OMA Contribution

A more human-readable, controlled observation-point description would complement the existing lat/lon/alt-only Location Object.

### Coverage Assessment

**New OMA capability required** for a controlled, human-readable observation-point vocabulary; **existing coverage** for raw geographic coordinates.

### Smart Data Model Responsibility

Human-readable address and place-name enrichment (e.g. "Pl. Mayor, 1, 28231 Las Rozas de Madrid, Madrid, Spain") belongs in the Smart Data Model, built from the OMA-provided coordinates.

### Recommendation to the OMA Smart Cities Working Group

Do not attempt to standardize human-readable addressing within OMA; instead, ensure that Location Object 6 coordinates remain reliably populated and linkable so that Smart Data Models can perform reverse-geocoding.

## Water Management and Irrigation

### Recommendation to the OMA Smart Cities Working Group

Same recommendation as for Public Lighting: rely on Location Object 6 coordinates and Smart Data Model reverse-geocoding for human-readable addressing of water and irrigation equipment.

---

# Observation Point Disposition Summary

| Classification | Finding |
|---|---|
| Existing OMA coverage | Location Object 6 for Client-level coordinates; asset identity Resources in 3410 and 3417; `3424/3` Type of meter as a weak category signal. |
| Existing coverage requiring clarification or extension | No controlled observation-point vocabulary or explicit point-to-asset relationship, for either Public Lighting or Water Management and Irrigation; the gap is sharper for water, which lacks a 3417-equivalent asset Object. |
| New OMA capability required | Controlled observation-point type and a co-observed-asset relationship, applicable to both domains. |
| Outside OMA responsibility but must remain linkable | Human-readable addressing and place-name enrichment. |

---

# Semantic Capability 5: Observation Scope

## Capability Purpose

Observation Scope describes whether a measurement represents a single luminaire, a cabinet feeder, or a larger group of assets.

## Overall Capability Conclusion

**Existing OMA coverage, expressed through Object identity rather than an explicit scope Resource.**

For Water Management and Irrigation, scope is similarly implicit in Object identity (a single meter, valve, or sensor), but without any analogue of the 3422 linked-instance aggregation pattern, making cross-meter scope composition a clearer gap than for Public Lighting.

---

# OMA Question 1

> Can Objects indicate the operational scope represented by a measurement?

## Public Lighting

### Municipality Operational Need

Municipalities need to know whether an energy or electrical-quality measurement represents one luminaire or an entire cabinet feeder serving many luminaires, so that KPIs are not miscalculated by mixing scopes.

### Required OMA Contribution

**Metadata and relationships**

- Implicit or explicit indication of how many assets are represented by a measurement

### Existing Object and Resource Evidence

| Object | Resource evidence | Source / Owner | Assessment |
|---|---|---|---|
| [`3418`](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/3418.xml) Electrical Monitor | Object identity | 1 / uCIFI | Scope is a single light point/luminaire, by Object design. |
| [`3421`](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/3421.xml) Single-Phase Electrical Meter | Object identity | 1 / uCIFI | Scope is a single electrical line, typically a lighting cabinet circuit serving many luminaires. |
| [`3422`](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/3422.xml) Three-Phase Electrical Meter Complement | `3422/36-38` L1/L2/L3 Meter Instance | 1 / uCIFI | Scope is explicitly the aggregate of three named `3421` Instances, one of the few cases where scope composition is Resource-explicit rather than purely implied by Object identity. |

### Coverage Assessment

**Existing coverage requiring clarification or extension.** Scope is mostly implicit in Object choice (3418 vs. 3421 vs. 3422); only the three-phase composition is made explicit through Resources 36–38.

### Missing Semantics

- A general, explicit scope Resource (e.g. number of luminaires represented) is not defined; the three-phase pattern is domain-specific and not generalized.

### Smart Data Model Responsibility

The Smart Data Model should record how many and which luminaires are served by each cabinet feeder and Instance.

### Recommendation to the OMA Smart Cities Working Group

Document, in a Public Lighting profile, that Object identity determines scope (3418 = single luminaire, 3421/3422 = cabinet feeder), and consider generalizing the 3422 linked-instance pattern for other scope compositions.

## Water Management and Irrigation

### Municipality Operational Need

Municipalities need to know whether a volume or pressure measurement represents a single meter, valve, or sensor, or an aggregate of several serving the same irrigation zone or network segment, so that KPIs are not miscalculated by mixing scopes.

### Existing Object and Resource Evidence

| Object | Resource evidence | Source / Owner | Assessment |
|---|---|---|---|
| [`3424`](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/3424.xml) Water Meter; [`3425`](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/3425.xml) Irrigation Valve; [`3427`](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/3427.xml) Pressure Monitoring Sensor | Object identity | 1 / uCIFI | Scope is a single meter, valve, or sensor by Object design; none of the three Objects defines a linked-instance Resource comparable to `3422/36-38`. |

### Coverage Assessment

**Existing coverage requiring clarification or extension.** Scope is entirely implicit in Object choice; unlike the electrical domain, there is no water-domain equivalent of the 3422 three-phase composition pattern to make an aggregate scope explicit.

### Missing Semantics

- A general, explicit scope Resource (e.g. number of meters/valves represented) is not defined for water Objects, and no domain-specific composition pattern exists either.

### Smart Data Model Responsibility

The Smart Data Model should record how many and which meters, valves, or sensors are associated with each irrigation zone or network segment.

### Recommendation to the OMA Smart Cities Working Group

Document, in a Water/Irrigation profile, that Object identity determines scope (3424/3425/3427 = single asset), and extend the same scope-generalization recommended for Public Lighting (reusing the 3422 linked-instance pattern) to water Objects.

---

# OMA Question 2

> Can aggregated observations identify the represented assets?

## Public Lighting

### Existing Object and Resource Evidence

| Object | Resource evidence | Source / Owner | Assessment |
|---|---|---|---|
| [`3422`](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/3422.xml) Three-Phase Electrical Meter Complement | `3422/36-38` L1/L2/L3 Meter Instance | 1 / uCIFI | The only Object in the Public Lighting evidence base that names the constituent Instances it aggregates. |
| [`3421`](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/3421.xml) Single-Phase Electrical Meter (multiple Instances on a cabinet Client) | Object identity only | 1 / uCIFI | Individual feeder circuits are distinguished by Instance number, but nothing states which luminaires are wired to each circuit. |

### Coverage Assessment

**Indirect or ambiguous**, except for the 3422 three-phase composition pattern, which is explicit.

### Missing Semantics

- A general mechanism to list the luminaires represented by a cabinet-level measurement.

### Smart Data Model Responsibility

Should be possibly done at higher level, in the network/asset topology model.

### Recommendation to the OMA Smart Cities Working Group

Generalize the 3422 linked-instance approach as the reusable pattern for any future aggregated-scope Object.

## Water Management and Irrigation

### Existing Object and Resource Evidence

| Object | Resource evidence | Source / Owner | Assessment |
|---|---|---|---|
| [`3424`](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/3424.xml) Water Meter (multiple Instances on a network-segment Client) | Object identity only | 1 / uCIFI | Individual meters are distinguished by Instance number, but nothing states which parcel or zone each Instance serves. |

### Coverage Assessment

**Indirect or ambiguous.** No water Object names the constituent Instances it aggregates, a weaker position than the 3422 three-phase composition pattern already available for Public Lighting.

### Missing Semantics

- A general mechanism to list the meters, valves, or sensors represented by a zone- or network-segment-level measurement.

### Recommendation to the OMA Smart Cities Working Group

When the 3422 linked-instance approach is generalized into a reusable pattern (as recommended in Question 1), apply it to Object 3424 as a first adopter outside Public Lighting.

---

# OMA Question 3

> How is aggregation represented?

## Public Lighting

### Existing Object and Resource Evidence

| Object | Resource evidence | Source / Owner | Assessment |
|---|---|---|---|
| [`3422`](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/3422.xml) Three-Phase Electrical Meter Complement | `3422/8` Total active power import on the 3 lines; `3422/17` Active energy import Un | 1 / uCIFI | Explicit sum-of-three-lines aggregation, with the aggregation function stated in the Resource description ("Sum Li Active power+"). |

### Coverage Assessment

**Existing coverage requiring clarification or extension.** A concrete sum-based aggregation exists for the three-phase case; a general-purpose aggregation-function Resource (sum, mean, min, max) for arbitrary lighting measurements does not exist.

### Missing Semantics

- General aggregation-function metadata usable for any lighting Resource, not only the three-phase power sum.

### Smart Data Model Responsibility

Cross-asset and cross-zone aggregation (e.g. total energy per district).

### Recommendation to the OMA Smart Cities Working Group

Provide a template for a general aggregation-metadata Resource applicable across Objects.

## Water Management and Irrigation

### Existing Object and Resource Evidence

No matching Object or Resource was identified; Object 3424 has no equivalent of `3422/8` Total active power import on the 3 lines, and no aggregation-function metadata.

### Coverage Assessment

**New OMA capability required.** Unlike the electrical domain, the water domain has no example of explicit, Resource-level aggregation to build on.

### Missing Semantics

- Aggregation-function metadata (sum, mean, min, max) for combining multiple water meter or pressure sensor Instances into a zone-level figure.

### Smart Data Model Responsibility

Cross-meter and cross-zone aggregation (e.g. total water delivered per irrigation district).

### Recommendation to the OMA Smart Cities Working Group

When a general aggregation-metadata Resource is defined (as recommended in Question 1 for Public Lighting), ensure it is equally applicable to Object 3424, since water has no existing aggregation example of its own to draw on.

---

# OMA Question 4

> Which additional capabilities would improve scope representation?

## Public Lighting

### Coverage Assessment

**New OMA capability required** for a general, explicit scope/aggregation Resource; **existing coverage** for the specific three-phase composition case.

### Recommendation to the OMA Smart Cities Working Group

Generalize the patterns already present in Objects 3422 and 7 (linked Instances; collection window) into reusable, cross-Object scope and aggregation metadata.

## Water Management and Irrigation

### Recommendation to the OMA Smart Cities Working Group

Apply the same reusable scope and aggregation metadata, once generalized from Objects 3422 and 7, to Objects 3424, 3425, and 3427, since the water domain currently has no comparable pattern of its own.

---

# Observation Scope Disposition Summary

| Classification | Finding |
|---|---|
| Existing OMA coverage | Object identity conveys implicit scope (3418 = luminaire, 3421/3422 = cabinet; 3424/3425/3427 = single water asset); Object 3422 makes three-phase composition explicit. |
| Existing coverage requiring clarification or extension | General aggregation-function and represented-asset-list metadata for both domains. |
| New OMA capability required | Reusable scope/aggregation Resource generalized from the 3422 and Connectivity Statistics patterns, applicable to water Objects as well, which currently have no composition example of their own. |
| Outside OMA responsibility but must remain linkable | Zone and district-level aggregation and topology, for both energy and water networks. |

---

# Semantic Capability 6: Observation Method

## Capability Purpose

Observation Method describes whether a lighting-related value was measured, estimated, inferred, or configured, so that Digital Twins can weigh its authority appropriately.

## Overall Capability Conclusion

**Existing coverage limited to measured values; new OMA capability required for other methods.**

Object 3425 (Irrigation Valve) reproduces the same Command / Command-in-action / measured-Status three-tier pattern already identified in Object 3416, giving the Water Management and Irrigation domain the same partial coverage and the same generalization gap.

---

# OMA Question 1

> How are different observation methods represented?

## Public Lighting

### Municipality Operational Need

Municipalities need to know whether a dimming level or energy value was directly measured by the control gear or configured/commanded, since a commanded value does not guarantee the corresponding physical output actually occurred.

### Required OMA Contribution

**Metadata and relationships**

- Explicit distinction between a measured value and a commanded/configured value

### Existing Object and Resource Evidence

| Method | Evidence | Source / Owner | Assessment |
|---|---|---|---|
| Measured | `3416/3` Dimming level ("measured on the outdoor lamp controller") | 1 / uCIFI | Description explicitly states the value is measured, not commanded. |
| Commanded / configured | `3416/1` Command; `3416/4` Default dimming level | 1 / uCIFI | Explicitly a command sent to the controller, structurally distinct from the measured Resource 3. |
| Command in action | `3416/2` Command in action | 1 / uCIFI | An intermediate method: the actual command applied after LPWAN or control-gear adjustment, explicitly distinguished by description from both the sent command and the measured dimming level. |
| Measured (electrical) | `3418/4` Active power; `3421/16` Active power+ | 1 / uCIFI | Measured Resources with no method Resource attached; method is only inferable from the Object's description text, not a queryable Resource. |

### Coverage Assessment

**Existing coverage requiring clarification or extension.** Object 3416 is unusual in that it already distinguishes three method-like concepts by Resource design (Command, Command in action, Dimming level), but this three-tier pattern is specific to 3416 and is not a general, reusable observation-method Resource applicable to other Objects such as 3418.

### Missing Semantics

- A general, reusable observation-method Resource (measured / commanded / estimated / predicted) applicable outside the specific 3416 pattern.

### Smart Data Model Responsibility

Externally generated predictions (e.g. predicted energy savings from a dimming policy) belong in the Smart Data Model.

### Recommendation to the OMA Smart Cities Working Group

Recognize the Command / Command-in-action / measured-value pattern in Object 3416 as a useful model, and generalize it into reusable observation-method metadata for other measurement Objects such as 3418.

## Water Management and Irrigation

### Municipality Operational Need

Municipalities need to know whether an irrigation valve's reported position was directly measured, commanded, or is the value actually applied after network propagation, since a commanded value does not guarantee the corresponding physical valve movement actually occurred.

### Existing Object and Resource Evidence

| Method | Evidence | Source / Owner | Assessment |
|---|---|---|---|
| Measured | `3425/2` Status ("actual level of opening of the valve") | 1 / uCIFI | Description explicitly states the value is measured, not commanded, directly mirroring `3416/3` Dimming level. |
| Commanded / configured | `3425/3` Command; `3425/1` Default status | 1 / uCIFI | Explicitly a command sent to the valve, structurally distinct from the measured Status Resource. |
| Command in action | `3425/4` Command in action | 1 / uCIFI | An intermediate method: the actual value applied after LPWAN propagation, explicitly distinguished by description from both the sent Command and the measured Status, reproducing the exact three-tier pattern of Object 3416. |
| Measured (pressure) | `3427/1` Pressure | 1 / uCIFI | Measured Resource with no method Resource attached, the same gap already identified for `3418/4` Active power. |

### Coverage Assessment

**Existing coverage requiring clarification or extension.** Object 3425 independently reproduces the same three-tier Command/Command-in-action/measured pattern as Object 3416, confirming this is a reusable design idiom across uCIFI Objects rather than a one-off; it remains specific to these two Objects and is not a general, reusable observation-method Resource.

### Missing Semantics

- A general, reusable observation-method Resource (measured / commanded / estimated / predicted) applicable outside the specific 3416 and 3425 patterns, such as for `3427/1` Pressure.

### Smart Data Model Responsibility

Externally generated predictions (e.g. predicted irrigation demand from a soil-moisture model) belong in the Smart Data Model.

### Recommendation to the OMA Smart Cities Working Group

Recognize that Objects 3416 and 3425 independently converge on the same Command/Command-in-action/measured-value pattern, and generalize it into reusable observation-method metadata applicable across both Public Lighting and Water Management and Irrigation Objects.

---

# OMA Question 2

> Can measured values be distinguished from inferred values?

## Public Lighting

### Existing Object and Resource Evidence

| Object | Resource evidence | Source / Owner | Assessment |
|---|---|---|---|
| [`3416`](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/3416.xml) Outdoor Lamp Controller | `3416/41` Virtual power output | 1 / uCIFI | Explicitly a configured percentage of nominal power ("the light source should be set when Command is set to 100%"), i.e. a derived/configured setpoint, not a direct measurement; however, nothing marks it as such in a machine-readable way beyond the textual description. |

### Coverage Assessment

**New OMA capability required.** The distinction currently relies on reading Resource descriptions rather than querying a method flag.

### Missing Semantics

- Machine-readable method flag, rather than reliance on human-readable Resource descriptions.

### Recommendation to the OMA Smart Cities Working Group

Add a queryable observation-method Resource so that clients do not need to hard-code Resource-specific knowledge to infer method.

## Water Management and Irrigation

### Existing Object and Resource Evidence

| Object | Resource evidence | Source / Owner | Assessment |
|---|---|---|---|
| [`3424`](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/3424.xml) Water Meter | `3424/7-8` Minimum/Maximum flow rate | 1 / uCIFI | Explicitly an extremum computed since the last metering value, i.e. a derived statistic rather than a direct instantaneous measurement; nothing marks it as such beyond the textual description, the same gap already identified for `3416/41` Virtual power output. |

### Coverage Assessment

**New OMA capability required.** As with Public Lighting, the distinction between a direct measurement and a derived statistic relies on reading Resource descriptions rather than querying a method flag.

### Recommendation to the OMA Smart Cities Working Group

Same recommendation as for Public Lighting: add a queryable observation-method Resource applicable across both domains.

---

# OMA Question 3

> Can prediction or simulation results be represented?

## Public Lighting

### Coverage Assessment

**New OMA capability required.** No Object in the Public Lighting evidence base represents a predicted or simulated value (e.g. predicted lamp end-of-life date, beyond the simple threshold-based `3416/64`/`3416/65` end-of-life alarm, which is threshold-triggered rather than model-predicted).

### Smart Data Model Responsibility

Predictive maintenance models and simulated illumination results belong in the Smart Data Model / Digital Twin layer.

### Recommendation to the OMA Smart Cities Working Group

No device-side change is required unless a controller performs local prediction; if it does, reuse the same observation-method metadata recommended in Question 1.

## Water Management and Irrigation

### Coverage Assessment

**New OMA capability required.** No Object in the Water Management and Irrigation evidence base represents a predicted or simulated value; leak and anomaly detection in Objects 3424 and 3427 are threshold- or rule-triggered rather than model-predicted, the same pattern already identified for Public Lighting's end-of-life alarms.

### Smart Data Model Responsibility

Predictive maintenance models and simulated irrigation-demand results belong in the Smart Data Model / Digital Twin layer.

### Recommendation to the OMA Smart Cities Working Group

No device-side change is required; if a controller performs local prediction, reuse the same observation-method metadata recommended in Question 1.

---

# OMA Question 4

> Which additional capabilities would improve observation method representation?

## Public Lighting

### Recommendation to the OMA Smart Cities Working Group

Generalize the Command / Command-in-action / measured-value pattern from Object 3416 into a reusable observation-method Resource for use across Objects 3416, 3418, 3421, and 3422.

## Water Management and Irrigation

### Recommendation to the OMA Smart Cities Working Group

Generalize the same Command / Command-in-action / measured-value pattern, independently confirmed by Object 3425, into a reusable observation-method Resource for use across Objects 3424, 3425, and 3427 as well.

---

# Observation Method Disposition Summary

| Classification | Finding |
|---|---|
| Existing OMA coverage | Object 3416 already distinguishes command, command-in-action, and measured dimming level by Resource design; Object 3425 independently reproduces the identical three-tier pattern for valve position. |
| Existing coverage requiring clarification or extension | The 3416/3425 pattern is not generalized to other Objects (3418, 3427) or expressed as a queryable method flag. |
| New OMA capability required | Reusable, cross-Object observation-method Resource covering both domains; no representation of predicted/simulated values in either domain. |
| Outside OMA responsibility but must remain linkable | Predictive maintenance and simulation models, for both lighting and irrigation. |

---

# Semantic Capability 7: Temporal Semantics

## Capability Purpose

Temporal Semantics describe the time basis of a lighting observation: whether it is instantaneous, cumulative since a reset, or collected over a defined window.

## Overall Capability Conclusion

**Existing OMA coverage for instantaneous timestamps; existing coverage requiring clarification for aggregation windows.**

The same Timestamp/Fractional Timestamp Common Resources are consistently present on Objects 3424, 3425, and 3427, but none of the three water Objects defines a measurement-period Resource comparable to `3421/24`.

---

# OMA Question 1

> Which temporal characteristics are currently represented?

## Public Lighting

### Municipality Operational Need

Municipalities need to know whether an energy or dimming value represents the current instant, a value accumulated since the last reset, or a value collected over a defined statistics window.

### Required OMA Contribution

**Telemetry**

- Timestamp of the measurement, with sub-second precision when relevant

### Existing Object and Resource Evidence

| Object and Resource | Source / Owner | Requirement status | Reuse | Assessment |
|---|---|---|---|---|
| `3416/5518` Timestamp; `3418/5518` Timestamp; `3421/5518` Timestamp; `3422/5518` Timestamp | 1 / uCIFI (Common Resource) | O | Reusable | Consistent timestamp Resource across all uCIFI lighting Objects. |
| `3416/6050`; `3418/6050`; `3421/6050`; `3422/6050` Fractional Timestamp | 1 / uCIFI (Common Resource) | O | Reusable | Sub-second precision available consistently across the same Objects. |
| `3418/6` Cumulated active energy; `3418/7` Energy reset | 1 / uCIFI | O | Object-specific | Explicitly cumulative "since last energy counter reset," a distinct temporal semantic from an instantaneous value. |
| `3421/24` Measurement period of Instantaneous value | 1 / uCIFI | O | Object-specific | Explicitly declares the averaging period underlying an "instantaneous" value. |

### Coverage Assessment

**Existing OMA coverage.** Timestamp and fractional timestamp are consistently available (as Common Resources) across all relevant lighting Objects, and cumulative-since-reset semantics are explicit.

### Missing Semantics

None material for point-in-time and cumulative-since-reset semantics.

### Smart Data Model Responsibility

Time-series storage, historical comparison, and forecasting.

### Recommendation to the OMA Smart Cities Working Group

None required; continue mandating Timestamp availability through Common.xml.

## Water Management and Irrigation

### Municipality Operational Need

Municipalities need to know whether a volume, pressure, or valve-position value represents the current instant or a value accumulated since the last reset.

### Existing Object and Resource Evidence

| Object and Resource | Source / Owner | Requirement status | Reuse | Assessment |
|---|---|---|---|---|
| `3424/5518`; `3425/5518`; `3427/5518` Timestamp | 1 / uCIFI (Common Resource) | O | Reusable | Consistent timestamp Resource across all three water Objects, identical to the lighting pattern. |
| `3424/6050`; `3425/6050`; `3427/6050` Fractional Timestamp | 1 / uCIFI (Common Resource) | O | Reusable | Sub-second precision available consistently across the same Objects. |
| `3424/1` Cumulated water volume; `3424/2` Cumulated water meter value reset | 1 / uCIFI | M / O | Object-specific | Explicitly cumulative "since last reset," the direct water-domain analogue of `3418/6-7`. |

### Coverage Assessment

**Existing OMA coverage.** Timestamp and fractional timestamp are consistently available across all three water Objects examined, and cumulative-since-reset semantics are explicit in Object 3424.

### Missing Semantics

None material for point-in-time and cumulative-since-reset semantics.

### Smart Data Model Responsibility

Time-series storage, historical comparison, and forecasting.

### Recommendation to the OMA Smart Cities Working Group

None required; continue mandating Timestamp availability through Common.xml for water Objects as well.

---

# OMA Question 2

> Can observation intervals remain explicit?

## Public Lighting

### Existing Object and Resource Evidence

| Object and Resource | Source / Owner | Assessment |
|---|---|---|
| `3421/24` Measurement period of Instantaneous value | 1 / uCIFI | Explicit interval Resource, in seconds. |
| Connectivity Statistics `7/8` Collection Period | 0 / OMA | Explicit interval Resource applicable to statistics collection, demonstrating a general OMA pattern beyond lighting-specific Objects. |

### Coverage Assessment

**Existing OMA coverage** where the Object defines an explicit interval Resource (3421, Connectivity Statistics); **existing coverage requiring extension** for Objects such as 3418 that do not define one.

### Missing Semantics

- No interval Resource in Object 3418 for its instantaneous power values.

### Recommendation to the OMA Smart Cities Working Group

Add a Measurement period Resource to Object 3418, consistent with the pattern already present in Object 3421.

## Water Management and Irrigation

### Existing Object and Resource Evidence

No matching Resource was identified; Objects 3424, 3425, and 3427 define no equivalent of `3421/24` Measurement period of Instantaneous value.

### Coverage Assessment

**Existing coverage requiring extension.** None of the three water Objects defines an explicit interval Resource, a gap that will become directly relevant once a current flow-rate Resource is added to Object 3424 (see Semantic Capability 2, Question 1).

### Missing Semantics

- No interval Resource for the Pressure (`3427/1`), Status (`3425/2`), or any future current flow-rate Resource in Object 3424.

### Recommendation to the OMA Smart Cities Working Group

Add a Measurement period Resource to Objects 3424 and 3427, consistent with the pattern already present in Object 3421, and include it alongside the current flow-rate Resource recommended for Object 3424.

---

# OMA Question 3

> Can aggregation periods be represented?

## Public Lighting

### Existing Object and Resource Evidence

| Object and Resource | Source / Owner | Assessment |
|---|---|---|
| Connectivity Statistics `7/6` Start; `7/7` Stop; `7/8` Collection Period | 0 / OMA | Explicit start/stop/period pattern for a bounded collection window. |
| `3418/7` Energy reset | 1 / uCIFI | Marks the start of a new cumulative period but does not record its duration or scheduled end. |

### Coverage Assessment

**Existing coverage requiring clarification or extension.** The Connectivity Statistics pattern is a strong template, but it is not reused by the electrical/lighting Objects for defining bounded aggregation windows.

### Missing Semantics

- Aggregation-window metadata for cumulative energy counters (3418, 3421, 3422), beyond a bare reset event.

### Recommendation to the OMA Smart Cities Working Group

Reuse the Connectivity Statistics start/stop/period pattern for energy and power Objects.

## Water Management and Irrigation

### Existing Object and Resource Evidence

| Object and Resource | Source / Owner | Assessment |
|---|---|---|
| `3424/2` Cumulated water meter value reset | 1 / uCIFI | Marks the start of a new cumulative period but does not record its duration or scheduled end, the same gap already identified for `3418/7`. |

### Coverage Assessment

**Existing coverage requiring clarification or extension.** As for Public Lighting, the Connectivity Statistics start/stop/period pattern is a strong template that is not reused by Object 3424 for defining bounded aggregation windows.

### Missing Semantics

- Aggregation-window metadata for the cumulative water-volume counter, beyond a bare reset event.

### Recommendation to the OMA Smart Cities Working Group

Reuse the Connectivity Statistics start/stop/period pattern for Object 3424 as well, consistent with the recommendation already made for the electrical Objects.

---

# OMA Question 4

> Which additional capabilities would improve temporal semantics?

## Public Lighting

### Recommendation to the OMA Smart Cities Working Group

Add a Measurement period Resource to Object 3418 and consider a shared aggregation-window pattern (modelled on Connectivity Statistics) reusable across electrical Objects.

## Water Management and Irrigation

### Recommendation to the OMA Smart Cities Working Group

Add a Measurement period Resource to Objects 3424 and 3427, and extend the shared aggregation-window pattern (modelled on Connectivity Statistics) to Object 3424 as well.

---

# Temporal Semantics Disposition Summary

| Classification | Finding |
|---|---|
| Existing OMA coverage | Timestamp and Fractional Timestamp consistently available across lighting and water Objects; explicit measurement period in Object 3421; explicit collection window in Connectivity Statistics; explicit cumulative-since-reset semantics in Objects 3418 and 3424. |
| Existing coverage requiring clarification or extension | Objects 3418, 3424, and 3427 lack a measurement-period Resource; no shared aggregation-window pattern reused across electrical or water Objects. |
| New OMA capability required | None; generalization of existing patterns is sufficient for both domains. |
| Outside OMA responsibility but must remain linkable | Historical time-series analytics and forecasting. |

---

# Semantic Capability 8: Provenance

## Capability Purpose

Provenance identifies where a lighting observation or command originated: the luminaire's own sensor, the control cabinet, an external control-room override, or an asset-management system.

## Overall Capability Conclusion

**Existing coverage requiring clarification or extension.**

OMA Data Model instances implemented by street-lighting devices normally refer only to raw infrastructure telemetry generated by the device itself; externally supplied information (control-room commands, asset-management updates) is only partially distinguishable from device-native telemetry.

The Water Management and Irrigation domain shares the same gap and is weaker in one respect: Object 3425 (Irrigation Valve) has no equivalent of `3416/54` Manual override active, so even the partial provenance signal available for lighting commands is absent for irrigation valve commands.

---

# OMA Question 1

> Which existing Objects and Resources identify the origin of observations?

## Public Lighting

### Municipality Operational Need

Municipalities need to know whether a dimming change resulted from the device's own schedule, a manual override from a control room, or an externally supplied command, in order to audit and troubleshoot lighting behaviour.

### Required OMA Contribution

**Metadata and relationships**

- Indication of whether a value was device-generated or externally supplied
- Indication of whether a command originated from a schedule, a manual override, or a direct write

### Existing Object and Resource Evidence

| Object and Resource | Source / Owner | Assessment |
|---|---|---|
| `3416/54` Manual override active | 1 / uCIFI | Indicates that a manually supplied override, rather than the autonomous schedule, is currently determining device behaviour, a partial provenance signal. |
| `3416/2` Command in action | 1 / uCIFI | Description explicitly notes the value "could have been set by a manual override command, a scheduled action (e.g. control program) or any other mechanism," but does not expose which one applied via a dedicated Resource. |
| `3` Device | `3/0` Manufacturer; `3/2` Serial Number | 0 / OMA | Identifies the reporting device itself, i.e. the technical origin of any telemetry hosted by that Client, but not the origin of a specific command. |

### Coverage Assessment

**Existing coverage requiring clarification or extension.** Manual-override active status is the closest OMA gets to explicit provenance for lighting commands; the exact source of the "Command in action" value is described in prose but not exposed as a discrete, queryable Resource.

### Missing Semantics

- A discrete provenance/source Resource for `Command in action`, distinguishing schedule-, override-, or direct-write origin.

### Smart Data Model Responsibility

Attribution of externally supplied commands to a specific control-room operator, work order, or asset-management transaction.

### Recommendation to the OMA Smart Cities Working Group

Add a discrete "command source" enumeration Resource to Object 3416, distinguishing schedule, manual override, and direct write, complementing the existing Manual override active flag.

## Water Management and Irrigation

### Municipality Operational Need

Municipalities need to know whether an irrigation valve's position resulted from its assigned scheduler, a manual override, or a direct write, in order to audit and troubleshoot irrigation behaviour.

### Existing Object and Resource Evidence

| Object and Resource | Source / Owner | Assessment |
|---|---|---|
| `3425/5` Scheduler ID | 1 / uCIFI | Identifies which scheduler(s) are assigned to the valve's Command, a partial provenance signal naming the autonomous source, but not distinguishing it from a manual direct write to `3425/3` Command. |
| `3425/4` Command in action | 1 / uCIFI | Description notes the value may differ from the sent Command on slow LPWAN networks, but does not expose whether the Command originated from a scheduler or a manual write. |

### Coverage Assessment

**Existing coverage requiring clarification or extension.** Object 3425 is weaker than Object 3416 for provenance: it has no equivalent of `3416/54` Manual override active, so there is no boolean signal at all distinguishing scheduler-driven from manually commanded valve positions, only the Scheduler ID assignment itself.

### Missing Semantics

- A discrete provenance/source Resource for `Command in action`, as already identified for Object 3416.
- Unlike Object 3416, Object 3425 lacks any override-active indicator; adding one would bring it to parity with the lighting domain.

### Smart Data Model Responsibility

Attribution of externally supplied irrigation commands to a specific control-room operator, work order, or asset-management transaction.

### Recommendation to the OMA Smart Cities Working Group

Add the same discrete "command source" enumeration Resource recommended for Object 3416 to Object 3425, and additionally add an override-active indicator to Object 3425 so it reaches parity with the partial provenance signal already available in Object 3416.

---

# OMA Question 2

> Can device-generated information be distinguished from externally supplied information?

## Public Lighting

### Existing Object and Resource Evidence

| Object and Resource | Source / Owner | Assessment |
|---|---|---|
| `3416/54` Manual override active | 1 / uCIFI | Distinguishes "externally driven" behaviour (override) from "device autonomous" behaviour (schedule), but only as a boolean, not as a rich provenance model. |

### Coverage Assessment

**Existing coverage requiring extension.** A binary distinction exists for lighting commands; no equivalent exists for measured telemetry, which is always assumed to be device-generated.

### Missing Semantics

- Provenance metadata for telemetry values consumed from an external sensor bus (e.g. DALI Memory Bank sourced values such as `3416/21` Control gear temperature) versus values measured directly by the LwM2M Client.

### Recommendation to the OMA Smart Cities Working Group

Clarify, in a Public Lighting profile, which Resources are expected to be locally measured versus retrieved from an external bus (DALI/Zhaga D4i), since this affects trust and latency assumptions.

## Water Management and Irrigation

### Existing Object and Resource Evidence

| Object and Resource | Source / Owner | Assessment |
|---|---|---|
| `3425/5` Scheduler ID; `3425/3` Command | 1 / uCIFI | Both Resources are read/write, with no Resource distinguishing whether the current Command value was set by the identified scheduler or by a separate manual write. |

### Coverage Assessment

**Existing coverage requiring extension**, and weaker than Public Lighting since no boolean override-active distinction exists at all for Object 3425.

### Missing Semantics

- Provenance metadata distinguishing scheduler-driven from manually written Command values in Object 3425, and for telemetry values retrieved from an external sensor bus in Objects 3424 and 3427.

### Recommendation to the OMA Smart Cities Working Group

Extend the Question 1 recommendation (command-source Resource and override-active indicator) to Object 3425, and clarify, in a Water/Irrigation profile, which Resources are expected to be locally measured versus bus-relayed.

---

# OMA Question 3

> Can provenance remain associated with observations throughout their lifecycle?

## Public Lighting

### Coverage Assessment

**Existing coverage requiring extension.** The Manual override active flag is only valid while the override is in effect; once a scheduled default value resumes, there is no historical record, within the Object itself, of which command was in effect at a past point in time (beyond the Timestamp of the current Command in action value).

### Smart Data Model Responsibility

Historical provenance logging and audit trails.

### Recommendation to the OMA Smart Cities Working Group

None beyond the Question 1 recommendation; historical provenance is better addressed by the Smart Data Model / Digital Twin's own event log.

## Water Management and Irrigation

### Coverage Assessment

**Existing coverage requiring extension.** As for Public Lighting, there is no historical record, within Object 3425 itself, of which command source was in effect at a past point in time, beyond the Timestamp of the current Command in action value; the absence of an override-active flag makes this gap more acute, since even the current state is only partially inferable.

### Smart Data Model Responsibility

Historical provenance logging and audit trails for irrigation commands.

### Recommendation to the OMA Smart Cities Working Group

None beyond the Question 1 recommendation; historical provenance is better addressed by the Smart Data Model / Digital Twin's own event log.

---

# OMA Question 4

> Which additional capabilities would improve provenance representation?

## Public Lighting

### Recommendation to the OMA Smart Cities Working Group

Add a discrete command-source Resource to Object 3416, complementing Manual override active, and clarify in a Public Lighting profile which Resources are locally measured versus bus-relayed.

## Water Management and Irrigation

### Recommendation to the OMA Smart Cities Working Group

Add a discrete command-source Resource and an override-active indicator to Object 3425, bringing it to parity with Object 3416, and clarify in a Water/Irrigation profile which Resources are locally measured versus bus-relayed.

---

# Provenance Disposition Summary

| Classification | Finding |
|---|---|
| Existing OMA coverage | Manufacturer/Serial Number identify the reporting device; Manual override active partially signals lighting command provenance; Scheduler ID identifies the autonomous source assigned to an irrigation valve's Command. |
| Existing coverage requiring clarification or extension | No discrete command-source Resource in either domain; no distinction between locally measured and bus-relayed telemetry; Object 3425 additionally lacks any override-active indicator, unlike Object 3416. |
| New OMA capability required | Command-source enumeration Resource for Objects 3416 and 3425; an override-active indicator for Object 3425. |
| Outside OMA responsibility but must remain linkable | Historical provenance/audit logging tied to control-room operators and work orders, for both lighting and irrigation commands. |

---

# Semantic Capability 9: Measurement Quality

## Capability Purpose

Measurement Quality describes how reliable a lighting-related observation is, supporting confidence-weighted operational decisions.

## Overall Capability Conclusion

**Existing OMA coverage.**

The Measurement Quality Indicator and Measurement Quality Level Common Resources are already defined and consistently made available across the street-lighting Objects examined in this assessment.

For Water Management and Irrigation, the same Common Resource pair is available on Objects 3424 and 3427, but notably absent from Object 3425 (Irrigation Valve), which defines no quality Resources at all.

---

# OMA Question 1

> Which quality characteristics can accompany observations?

## Public Lighting

### Municipality Operational Need

Municipalities need to know whether an energy, dimming, or connectivity measurement can be trusted before using it for billing, maintenance dispatch, or compliance reporting.

### Required OMA Contribution

**Metadata and relationships**

- A quality indicator and quality level accompanying each measurement

### Existing Object and Resource Evidence

| Object and Resource | Source / Owner | Requirement status | Reuse | Assessment |
|---|---|---|---|---|
| `3416/6042` Measurement Quality Indicator; `3416/6049` Measurement Quality Level | 0 / OMA (Common Resource) | O | Reusable | Available on the Outdoor Lamp Controller. |
| `3418/6042`; `3418/6049` | 0 / OMA (Common Resource) | O | Reusable | Available on the Electrical Monitor. |
| `3421/6042`; `3421/6049` | 0 / OMA (Common Resource) | O | Reusable | Available on the Single-Phase Electrical Meter. |
| `3422/6042`; `3422/6049` | 0 / OMA (Common Resource) | O | Reusable | Available on the Three-Phase Electrical Meter Complement. |
| `3447/6042`; `3447/6049`; `3448/6042`; `3448/6049` | 0 / OMA (Common Resource) | O | Reusable | Available on the LPWAN Mesh Connectivity and Statistics Objects, extending quality semantics to network measurements as well. |

### Coverage Assessment

**Existing OMA coverage.** The Common Resource pair (6042/6049) is consistently defined across every uCIFI Object examined in this assessment, from lighting control to electrical metering to LPWAN mesh statistics.

### Missing Semantics

- All quality Resources are optional; devices may omit them entirely, and no Public Lighting profile currently mandates their presence.

### Smart Data Model Responsibility

Translating a numeric quality level into a municipality-facing confidence category (e.g. "billing grade," "indicative only").

### Recommendation to the OMA Smart Cities Working Group

Consider making Measurement Quality Indicator mandatory within a Public Lighting profile for energy Resources used in billing or compliance reporting.

## Water Management and Irrigation

### Municipality Operational Need

Municipalities need to know whether a water volume, pressure, or valve-position measurement can be trusted before using it for billing, leak-response dispatch, or compliance reporting.

### Existing Object and Resource Evidence

| Object and Resource | Source / Owner | Requirement status | Reuse | Assessment |
|---|---|---|---|---|
| `3424/6042` Measurement Quality Indicator; `3424/6049` Measurement Quality Level | 0 / OMA (Common Resource) | O | Reusable | Available on the Water Meter. |
| `3427/6042`; `3427/6049` | 0 / OMA (Common Resource) | O | Reusable | Available on the Pressure Monitoring Sensor. |
| `3425` Irrigation Valve | No Measurement Quality Indicator or Level Resource defined | 1 / uCIFI | — | Not applicable | Unlike every other Object examined in this assessment, Object 3425 does not expose the Common Resource pair at all, even though it reports a measured Status value. |

### Coverage Assessment

**Existing coverage requiring clarification or extension.** The Common Resource pair (6042/6049) is available on Objects 3424 and 3427, consistent with the broader Registry pattern, but Object 3425 is a genuine outlier in omitting it entirely.

### Missing Semantics

- Object 3425 defines no Measurement Quality Indicator or Level Resource, unlike every other Object examined in this assessment, including its closest structural analogue, Object 3416.

### Smart Data Model Responsibility

Translating a numeric quality level into a municipality-facing confidence category (e.g. "billing grade," "indicative only").

### Recommendation to the OMA Smart Cities Working Group

Add the Measurement Quality Indicator and Measurement Quality Level Common Resources to Object 3425, closing the one identified gap in an otherwise consistent Registry-wide pattern; consider making the Indicator mandatory within a Water/Irrigation profile for volume Resources used in billing.

---

# OMA Question 2

> Can confidence or uncertainty be represented?

## Public Lighting

### Existing Object and Resource Evidence

| Object and Resource | Source / Owner | Assessment |
|---|---|---|
| `6049` Measurement Quality Level (0–100) | 0 / OMA | A graded confidence scale, with 100 meaning full quality-check pass and 0 meaning the measurement should be rejected. |

### Coverage Assessment

**Existing OMA coverage.** The 0–100 quality level Resource functions as a confidence score.

### Missing Semantics

No numerical uncertainty/error-margin Resource (e.g. ± value) exists; only a qualitative pass/fail-oriented scale is defined.

### Recommendation to the OMA Smart Cities Working Group

Evaluate whether energy-metering profiles need a dedicated numerical uncertainty Resource beyond the existing 0–100 quality level, particularly for billing-grade metering.

## Water Management and Irrigation

### Coverage Assessment

**Existing OMA coverage** for Objects 3424 and 3427, via the same 0–100 Measurement Quality Level Resource; **not available** for Object 3425 pending the Question 1 recommendation.

### Missing Semantics

Same as Public Lighting: no numerical uncertainty/error-margin Resource exists; only a qualitative pass/fail-oriented scale is defined where the Common Resource pair is present at all.

### Recommendation to the OMA Smart Cities Working Group

Same as Public Lighting: evaluate whether water-metering profiles need a dedicated numerical uncertainty Resource, once the Question 1 gap in Object 3425 is closed.

---

# OMA Question 3

> Can incomplete observations be identified?

## Public Lighting

### Existing Object and Resource Evidence

| Object and Resource | Source / Owner | Assessment |
|---|---|---|
| `6042` Measurement Quality Indicator, value 0 (UNCHECKED) | 0 / OMA | Indicates that no quality checks were performed or applicable, distinguishing an unchecked value from a validated one. |

### Coverage Assessment

**Existing OMA coverage.** The device may report only the subset of Resources that are available; optional Resources being absent is itself a signal of incompleteness recognizable by any LwM2M client.

### Recommendation to the OMA Smart Cities Working Group

None required; the existing optional-Resource model already supports this.

## Water Management and Irrigation

### Coverage Assessment

**Existing OMA coverage** for Objects 3424 and 3427, via the same optional-Resource model; Object 3425 provides no quality signal at all until the Question 1 gap is closed, so incompleteness of its Status Resource cannot currently be flagged.

### Recommendation to the OMA Smart Cities Working Group

Closing the Question 1 gap in Object 3425 would also resolve this finding.

---

# OMA Question 4

> Which additional capabilities would improve quality representation?

## Public Lighting

### Recommendation to the OMA Smart Cities Working Group

Consider a Public Lighting profile requirement making quality indicator mandatory for billing/compliance-relevant Resources, and evaluate a supplementary numerical uncertainty Resource for metering use cases.

## Water Management and Irrigation

### Recommendation to the OMA Smart Cities Working Group

Add the Measurement Quality Indicator and Measurement Quality Level Common Resources to Object 3425 as the priority action for this capability; otherwise mirror the Public Lighting recommendations for a mandatory-quality profile requirement and a supplementary numerical uncertainty Resource.

---

# Measurement Quality Disposition Summary

| Classification | Finding |
|---|---|
| Existing OMA coverage | Measurement Quality Indicator (6042) and Level (6049) consistently defined across lighting, electrical, LPWAN mesh, Water Meter (3424), and Pressure Monitoring Sensor (3427) Objects. |
| Existing coverage requiring clarification or extension | Quality Resources are optional; no profile currently mandates them. |
| New OMA capability required | Add the Measurement Quality Indicator/Level Common Resource pair to Object 3425, which uniquely omits it; possible supplementary numerical uncertainty Resource for metering. |
| Outside OMA responsibility but must remain linkable | Translating quality levels into municipality-facing trust categories. |

---

# Semantic Capability 10: Operational Context

## Capability Purpose

Operational Context describes conditions such as electrical line quality or weather that influence lighting service behaviour without being part of the lighting infrastructure itself.

## Overall Capability Conclusion

**Existing coverage requiring clarification or extension.**

Electrical line-quality context is well covered by the Electrical Monitor and electrical meter Objects. Environmental context relies on generic IPSO/uCIFI environmental sensor Objects that are not natively linked to a specific lighting installation.

For Water Management and Irrigation, the same generic environmental sensor Objects (notably Temperature, Humidity, and Rain Gauge) are directly relevant operational context for irrigation scheduling, with the same linking gap.

---

# OMA Question 1

> Which operational context can be directly observed?

## Public Lighting

### Municipality Operational Need

Municipalities need to know whether poor lighting service, a nuisance alarm, or unusual energy consumption is caused by electrical supply problems or weather conditions, rather than by the luminaire itself.

### Required OMA Contribution

**Telemetry**

- Supply voltage and frequency quality indicators
- Locally relevant environmental measurements (temperature, humidity, rainfall, wind) when available on the same infrastructure

### Existing Object and Resource Evidence

| Object | Resource evidence | Source / Owner | Assessment |
|---|---|---|---|
| [`3418`](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/3418.xml) Electrical Monitor | `3418/20-23` Low/High voltage threshold and flags | 1 / uCIFI | Direct operational-context signal distinguishing a supply-quality problem from a luminaire fault. |
| [`3421`](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/3421.xml) Single-Phase Electrical Meter | `3421/41-53` voltage sag/swell/cut counters and thresholds | 1 / uCIFI | Rich power-quality event context at the cabinet feeder. |
| [`3303`](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/3303.xml) Temperature; [`3304`](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/3304.xml) Humidity | 1 / IPSO Alliance | Generic environmental sensors that can be co-deployed on lighting poles/cabinets to provide ambient context. |
| [`3446`](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/3446.xml) Rain Gauge; [`3449`](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/3449.xml) Anemometer | 1 / uCIFI | Rainfall and wind context relevant to visibility and lighting demand. |
| [`3432`](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/3432.xml) Traffic Counter | 1 / uCIFI | Traffic-related operational context sometimes co-located with street lighting poles. |
| [`3450`](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/3450.xml) Wet Bulb Globe Temperature | 1 / uCIFI | Heat-stress context, occasionally co-deployed on lighting infrastructure. |

### Coverage Assessment

**Existing coverage requiring clarification or extension.** Electrical line-quality context is object-specific and strong (3418, 3421). Environmental context relies on generic sensor Objects with no native relationship to the specific luminaire or cabinet they contextualize, beyond Client co-location.

### Missing Semantics

- Explicit relationship linking an environmental sensor Instance to the specific lighting asset(s) it contextualizes.

### Smart Data Model Responsibility

Correlating weather/traffic context with lighting service performance at the street or zone level.

### Recommendation to the OMA Smart Cities Working Group

Reuse the same observation-point/linked-asset extension recommended for Service Outcome (OMA Question 1) to connect environmental sensor Instances to the lighting assets they contextualize.

## Water Management and Irrigation

### Municipality Operational Need

Municipalities need to know whether recent or forecast rainfall, soil temperature, or ambient humidity should influence an irrigation schedule, and whether a pressure drop is caused by a distribution-network condition rather than the monitored segment itself.

### Required OMA Contribution

**Telemetry**

- Rainfall accumulation relevant to irrigation-skip decisions
- Soil or ambient temperature and humidity when available on the same infrastructure

### Existing Object and Resource Evidence

| Object | Resource evidence | Source / Owner | Assessment |
|---|---|---|---|
| [`3446`](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/3446.xml) Rain Gauge | Rainfall accumulation | 1 / uCIFI | Directly relevant operational context for irrigation scheduling, enabling rain-skip logic to avoid watering during or after rainfall. |
| [`3303`](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/3303.xml) Temperature; [`3304`](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/3304.xml) Humidity | Sensor Value (5700) | 1 / IPSO Alliance | Generic environmental sensors already mapped, in the Water Management reference mapping, to `AgriParcelRecord` soilTemperature and relativeHumidity, supporting irrigation-demand estimation. |
| [`3427`](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/3427.xml) Pressure Monitoring Sensor | `3427/1` Pressure | 1 / uCIFI | A pressure drop recorded at a network node is itself operational context for interpreting a downstream valve or meter reading, independent of the local asset's own condition. |

### Coverage Assessment

**Existing coverage requiring clarification or extension.** Rainfall, temperature, and humidity sensors are generic Objects with no native relationship to the specific meter, valve, or parcel they contextualize, the same gap already identified for Public Lighting.

### Missing Semantics

- Explicit relationship linking an environmental sensor Instance (Rain Gauge, Temperature, Humidity) to the specific irrigation zone or parcel it contextualizes.

### Smart Data Model Responsibility

Correlating rainfall and soil-condition context with irrigation scheduling and water-consumption performance at the parcel or zone level.

### Recommendation to the OMA Smart Cities Working Group

Extend the same observation-point/linked-asset mechanism recommended for Public Lighting to connect Rain Gauge, Temperature, and Humidity sensor Instances to the irrigation zones or parcels they contextualize.

---

# OMA Question 2

> Can external operational context be associated with observations?

## Public Lighting

### Coverage Assessment

**Existing coverage requiring extension**, as described above.

### Smart Data Model Responsibility

Should be possibly done at higher level, joining weather-service or traffic data with lighting telemetry.

### Recommendation to the OMA Smart Cities Working Group

No new Object required; rely on the linked-asset relationship recommended across this assessment.

## Water Management and Irrigation

### Coverage Assessment

**Existing coverage requiring extension**, as described above.

### Smart Data Model Responsibility

Should be possibly done at higher level, joining weather-service rainfall forecasts or soil-condition data with irrigation telemetry.

### Recommendation to the OMA Smart Cities Working Group

No new Object required; rely on the same linked-asset relationship recommended across this assessment.

---

# OMA Question 3

> Which additional capabilities would improve operational context representation?

## Public Lighting

### Recommendation to the OMA Smart Cities Working Group

Extend the linked-asset relationship (recommended for Observation Point and Service Outcome) to environmental sensor Objects so that operational context can be formally associated with the lighting asset it affects.

## Water Management and Irrigation

### Recommendation to the OMA Smart Cities Working Group

Extend the same linked-asset relationship to Rain Gauge, Temperature, and Humidity sensor Objects so that rainfall and soil-condition context can be formally associated with the irrigation zone or parcel it affects.

---

# Operational Context Disposition Summary

| Classification | Finding |
|---|---|
| Existing OMA coverage | Electrical line-quality context via Objects 3418 and 3421; a broad set of environmental sensor Objects (3303, 3304, 3432, 3446, 3449, 3450) available for co-deployment with lighting or irrigation infrastructure; pressure context via Object 3427. |
| Existing coverage requiring clarification or extension | No native relationship linking an environmental sensor Instance to the specific lighting or irrigation asset it contextualizes. |
| New OMA capability required | Linked-asset relationship (shared with Observation Point), applicable to both domains. |
| Outside OMA responsibility but must remain linkable | Weather-service, rainfall-forecast, and traffic-data correlation with lighting and irrigation performance. |

---

# Semantic Capability 11: Physical Context

## Capability Purpose

Physical Context describes environmental features (trees, buildings, terrain) that affect why identical luminaires may produce different illumination results in different locations.

## Overall Capability Conclusion

**Outside OMA responsibility but must remain linkable.**

This capability is not well covered by the existing Data Model and should be managed at higher levels, using OMA-provided location and asset identifiers as the join key.

The same conclusion applies to Water Management and Irrigation: soil type, pipe material and depth, and terrain affecting pressure and infiltration are outside OMA responsibility but must remain linkable via Location (6) and the water equipment's asset identifier.

---

# OMA Question 1

> Which physical context can be directly represented?

## Public Lighting

### Municipality Operational Need

Municipalities need to know whether reduced street illumination is caused by a luminaire problem or by physical obstructions such as tree canopy growth.

### Required OMA Contribution

None; the Registry provides no Resource describing vegetation, buildings, terrain, or shadowing, and none is expected at the device level.

### Existing Object and Resource Evidence

No matching Object or Resource was identified in the lighting-relevant Registry Objects examined in this assessment.

### Coverage Assessment

Outside OMA responsibility but must remain linkable.

### Missing Semantics

Not applicable; this information is not expected to be device-observable.

### Smart Data Model Responsibility

GIS-sourced vegetation, building, and terrain data should be associated with the OMA-reported luminaire location (Object 6) and asset identity (Object 3417).

### Recommendation to the OMA Smart Cities Working Group

No OMA action required; ensure Location Object 6 remains reliably populated so Smart Data Models can join it with external GIS physical-context data.

## Water Management and Irrigation

### Municipality Operational Need

Municipalities need to know whether a pressure anomaly or irrigation underperformance is caused by soil type, pipe material and depth, or terrain, rather than by the meter, valve, or sensor itself.

### Required OMA Contribution

None; the Registry provides no Resource describing soil type, pipe material, terrain, or elevation profile, and none is expected at the device level.

### Existing Object and Resource Evidence

No matching Object or Resource was identified in the water-relevant Registry Objects examined in this assessment.

### Coverage Assessment

Outside OMA responsibility but must remain linkable.

### Smart Data Model Responsibility

GIS-sourced soil, pipe-network, and terrain data should be associated with the OMA-reported meter/valve/sensor location (Object 6) and asset identifier (`3410/4`).

### Recommendation to the OMA Smart Cities Working Group

No OMA action required; ensure Location Object 6 remains reliably populated so Smart Data Models can join it with external GIS and pipe-network data.

---

# OMA Question 2

> Should physical context be supplied by external systems?

## Public Lighting

### Coverage Assessment

Outside OMA responsibility but must remain linkable.

### Recommendation to the OMA Smart Cities Working Group

Confirm, in a Public Lighting profile, that physical/environmental-obstruction context is explicitly out of scope for LwM2M Objects and is a Smart Data Model / GIS responsibility.

## Water Management and Irrigation

### Coverage Assessment

Outside OMA responsibility but must remain linkable.

### Recommendation to the OMA Smart Cities Working Group

Confirm, in a Water/Irrigation profile, that soil, pipe-network, and terrain context is explicitly out of scope for LwM2M Objects and is a Smart Data Model / GIS responsibility.

---

# OMA Question 3

> Which additional capabilities would improve physical context representation?

## Public Lighting

### Recommendation to the OMA Smart Cities Working Group

None; no device-side capability is needed. Ensure location and asset identifiers remain the stable join key for external physical-context data.

## Water Management and Irrigation

### Recommendation to the OMA Smart Cities Working Group

None; no device-side capability is needed. Ensure Location (6) and the water equipment's asset identifier remain the stable join key for external soil, pipe-network, and terrain data.

---

# Physical Context Disposition Summary

| Classification | Finding |
|---|---|
| Existing OMA coverage | None. |
| Existing coverage requiring clarification or extension | Not applicable. |
| New OMA capability required | None. |
| Outside OMA responsibility but must remain linkable | Vegetation, building, terrain, and shadow data for lighting, joined via Location (6) and Luminaire Asset (3417); soil, pipe-network, and terrain data for water, joined via Location (6) and Asset identifier (`3410/4`). |

---

# Semantic Capability 12: Asset Management Context

## Capability Purpose

Asset Management Context represents ownership, maintenance responsibility, warranty, and lifecycle information associated with lighting infrastructure.

## Overall Capability Conclusion

**Existing coverage requiring clarification or extension.**

Devices expose useful lifecycle-adjacent information (operating hours, installation date, manufacturer identity), but ownership, contracts, and warranty terms are expected to be managed at higher levels.

Water Management and Irrigation equipment shares the same generic Device Extension (3410) lifecycle Resources, but has no equivalent of the Luminaire Asset Object (3417) for manufacturer-level identity, nor of Object 3416's operating-hours and end-of-life threshold Resources.

---

# OMA Question 1

> Which existing Objects and Resources represent asset management information?

## Public Lighting

### Municipality Operational Need

Municipalities need to know who owns and maintains each luminaire, when it was installed, and how close it is to end of life, to plan maintenance and replacement budgets.

### Required OMA Contribution

**Metadata and relationships**

- Manufacturer and model identity
- Installation date
- Cumulative operating hours and end-of-life thresholds

### Existing Object and Resource Evidence

| Object | Resource evidence | Source / Owner | Requirement status | Reuse | Assessment |
|---|---|---|---|---|---|
| [`3`](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/3.xml) Device | `3/0` Manufacturer; `3/1` Model Number; `3/2` Serial Number | 0 / OMA | O | Reusable | Identity of the controlling device itself. |
| [`3410`](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/3410.xml) Device Extension | `3410/4` Asset identifier; `3410/5` Installation date; `3410/9` Device operating hours | 1 / uCIFI | O | Object-specific | Directly supports installation-date and operating-hours lifecycle tracking. |
| [`3410`](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/3410.xml) Device Extension | `3410/7` Maintenance | 1 / uCIFI | O | Object-specific | Boolean flag indicating the device is currently in maintenance mode. |
| [`3417`](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/3417.xml) Luminaire Asset | `3417/1` Asset GTIN; `3417/2` Year of manufacture; `3417/3` Week of manufacture | 1 / uCIFI | M GTIN; O year/week | Object-specific | Manufacturer-level lifecycle identity of the physical luminaire, independent of the controlling device. |
| [`3416`](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/3416.xml) Outdoor Lamp Controller | `3416/15` Lamp operating hours; `3416/56` Driver operating hours; `3416/64` Lamp max operating hours threshold; `3416/65` Lamp max operating hours exceeded | 1 / uCIFI | O | Object-specific | Direct end-of-life prediction support based on cumulative operating time and a configurable threshold. |

### Coverage Assessment

**Existing coverage requiring clarification or extension.** Devices expose a meaningful subset of lifecycle information (installation date, operating hours, end-of-life threshold, manufacturer identity), but ownership, responsible organization, contracts, and warranty terms have no corresponding Resources and are expected to be supplied externally.

### Missing Semantics

- No Resource for ownership, responsible organization, contract, or warranty status.

### Smart Data Model Responsibility

Ownership, responsible organization, maintenance contracts, warranty status, and remaining useful-life estimation should be maintained by the Smart Data Model, keyed to the OMA-reported Asset GTIN/identifier.

### Recommendation to the OMA Smart Cities Working Group

Retain Objects 3410 and 3417 as the standard source of installation date, operating hours, and manufacturer identity; do not attempt to standardize ownership or contractual information within OMA.

## Water Management and Irrigation

### Municipality Operational Need

Municipalities need to know who owns and maintains each meter, valve, or pressure sensor, when it was installed, and how close it is to end of life, to plan maintenance and replacement budgets.

### Existing Object and Resource Evidence

| Object | Resource evidence | Source / Owner | Requirement status | Reuse | Assessment |
|---|---|---|---|---|---|
| [`3410`](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/3410.xml) Device Extension | `3410/4` Asset identifier; `3410/5` Installation date; `3410/9` Device operating hours | 1 / uCIFI | O | Reusable | Same generic installation-date and operating-hours lifecycle tracking used for Public Lighting, directly reusable for a water meter, valve, or pressure-sensor Client. |
| [`3410`](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/3410.xml) Device Extension | `3410/7` Maintenance | 1 / uCIFI | O | Reusable | Boolean flag indicating the device is currently in maintenance mode. |
| `3424` Water Meter; `3425` Irrigation Valve; `3427` Pressure Monitoring Sensor | No manufacturer-level asset identity, operating-hours, or end-of-life threshold Resources | 1 / uCIFI | — | Not applicable | Unlike Object 3416 (`3416/15,56,64,65`) and Object 3417 (`3417/1-3`), none of the three water Objects exposes a device-reported wear counter, end-of-life threshold, or manufacturer-level nameplate identity of its own. |

### Coverage Assessment

**Existing coverage requiring clarification or extension.** The generic Device Extension (3410) is directly reusable for water equipment, but the domain-specific lifecycle depth available for lighting (via 3416 and 3417) has no counterpart for meters, valves, or pressure sensors.

### Missing Semantics

- No water-specific asset Object comparable to 3417 for manufacturer-level identity (see also Semantic Capability 2, Question 3).
- No operating-hours or end-of-life threshold Resource in Objects 3424, 3425, or 3427, comparable to `3416/15,56,64,65`.

### Smart Data Model Responsibility

Ownership, responsible organization, maintenance contracts, warranty status, and remaining useful-life estimation should be maintained by the Smart Data Model, keyed to the OMA-reported Asset identifier (`3410/4`) pending resolution of the asset-identity gap.

### Recommendation to the OMA Smart Cities Working Group

Retain Object 3410 as the standard source of installation date and operating hours for water equipment; evaluate whether a water-specific asset Object (per Semantic Capability 2, Question 3) and operating-hours/end-of-life Resources, patterned on Object 3416, are warranted for meters, valves, and pressure sensors.

---

# OMA Question 2

> Which management information belongs within LwM2M Objects?

## Public Lighting

### Coverage Assessment

Installation date, operating hours, maintenance-mode flag, and manufacturer identity are appropriately represented within LwM2M Objects (3410, 3416, 3417), since a device can observe or be configured with this information directly.

### Recommendation to the OMA Smart Cities Working Group

None required; the current allocation between device-observable lifecycle data (OMA) and administrative/contractual data (Smart Data Model) is appropriate.

## Water Management and Irrigation

### Coverage Assessment

Installation date, operating hours, and maintenance-mode flag are appropriately represented within LwM2M Object 3410 for water equipment, since a device can observe or be configured with this information directly, consistent with Public Lighting.

### Recommendation to the OMA Smart Cities Working Group

None required; the current allocation is appropriate for water equipment as well.

---

# OMA Question 3

> Which information should remain external to device models?

## Public Lighting

### Coverage Assessment

Ownership, responsible organization, maintenance contracts, and warranty status should remain external, since a device cannot observe or verify this information.

### Smart Data Model Responsibility

Should be possibly complemented at higher levels, keyed by Asset GTIN (`3417/1`) and Asset identifier (`3410/4`).

## Water Management and Irrigation

### Coverage Assessment

Ownership, responsible organization, maintenance contracts, and warranty status should remain external for water equipment as well, since a device cannot observe or verify this information.

### Smart Data Model Responsibility

Should be possibly complemented at higher levels, keyed by Asset identifier (`3410/4`), pending resolution of the water-specific asset-identity gap identified in Question 1.

---

# OMA Question 4

> Can external asset management information remain associated with device observations?

## Public Lighting

### Coverage Assessment

**Existing coverage requiring extension.** The Asset GTIN and Asset identifier Resources provide a usable join key, but there is no formal OMA mechanism guaranteeing that external asset-management records remain consistently linked over the device's lifecycle (e.g. after a device replacement on the same pole).

### Recommendation to the OMA Smart Cities Working Group

Clarify, in a Public Lighting profile, that Asset GTIN and Asset identifier are expected to persist across device replacement events, so that Smart Data Models can maintain continuity of the asset record.

## Water Management and Irrigation

### Coverage Assessment

**Existing coverage requiring extension.** The generic Asset identifier (`3410/4`) provides a usable join key, but, absent a water-specific asset Object, it is the only one, making continuity across device replacement even more dependent on correct external record-keeping than for Public Lighting.

### Recommendation to the OMA Smart Cities Working Group

Clarify, in a Water/Irrigation profile, that the Asset identifier is expected to persist across device replacement events, and prioritize the Question 1 recommendation for a water-specific asset Object to bring continuity practice to parity with Public Lighting.

---

# Asset Management Context Disposition Summary

| Classification | Finding |
|---|---|
| Existing OMA coverage | Installation date, operating hours, maintenance flag (3410), reusable for both lighting and water equipment; manufacturer identity, year/week of manufacture (3417), lamp/driver operating hours and end-of-life threshold (3416), specific to lighting. |
| Existing coverage requiring clarification or extension | Persistence of Asset GTIN/identifier across device replacement, for both domains; water equipment additionally lacks any manufacturer-level asset identity or operating-hours/end-of-life Resource of its own. |
| New OMA capability required | None identified for Public Lighting; evaluate a water-specific asset Object and operating-hours/end-of-life Resources for Objects 3424, 3425, and 3427. |
| Outside OMA responsibility but must remain linkable | Ownership, responsible organization, maintenance contracts, and warranty status, for both lighting and water assets. |

---

# Semantic Capability 13: Network Operability

## Capability Purpose

Network Operability describes the communication conditions that determine whether a luminaire can currently be remotely monitored or controlled.

## Overall Capability Conclusion

**Existing OMA coverage.**

Connectivity Monitoring, Connectivity Statistics, and the uCIFI LPWAN Mesh Objects together provide a detailed communication-quality and failure model, and the Device object's Error Code Resource explicitly distinguishes a connectivity failure from other device error types.

These Objects are bearer-level and domain-independent, so the same coverage applies directly to a Water Management and Irrigation Client hosting Objects 3424, 3425, or 3427, with no domain-specific adaptation required.

---

# OMA Question 1

> Which existing Objects and Resources represent communication characteristics?

## Public Lighting

### Municipality Operational Need

Municipalities need to know whether a lighting asset can currently be remotely controlled, and whether an apparent fault is caused by a communication problem rather than the luminaire itself.

### Required OMA Contribution

**Telemetry**

- Signal quality, connection status, and communication error counters

### Existing Object and Resource Evidence

| Object | Resource evidence | Source / Owner | Requirement status | Reuse | Assessment |
|---|---|---|---|---|---|
| [`4`](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/4.xml) Connectivity Monitoring | `4/2` Radio Signal Strength; `4/3` Link Quality | 0 / OMA | M signal strength; O link quality | Reusable | Generic bearer-agnostic signal-quality Resources. |
| [`4`](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/4.xml) Connectivity Monitoring | `4/0` Network Bearer; `4/1` Available Network Bearer | 0 / OMA | M | Reusable | Identifies the transport technology in use and available, relevant when a lighting cabinet gateway supports multiple bearers. |
| [`7`](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/7.xml) Connectivity Statistics | `7/2` Tx Data; `7/3` Rx Data; `7/8` Collection Period | 0 / OMA | O | Reusable | Traffic-volume statistics over a bounded collection window. |
| [`3447`](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/3447.xml) LPWAN Mesh Connectivity | `3447/3` Status; `3447/4` Connection Errors; `3447/30` Received Signal Strength Indication; `3447/29` Signal to noise ratio | 1 / uCIFI | M status; O others | Object-specific | Mesh-specific connectivity status and RF quality tailored to 802.15.4-based street-lighting mesh deployments. |
| [`3448`](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/3448.xml) LPWAN Mesh Statistics | `3448/4` Tx Discarded packets; `3448/9` Rx Malformed Packets; `3448/11` Rx duplicate Packets | 1 / uCIFI | O | Object-specific | Detailed mesh-network error statistics collected over a Start/Stop window (`3448/28-29`). |

### Coverage Assessment

**Existing OMA coverage.** Both cellular/generic (Objects 4, 7) and mesh-specific (Objects 3447, 3448) communication characteristics are well represented, spanning signal quality, error counters, and traffic volumes.

### Missing Semantics

None material; the main opportunity is profiling which subset is mandatory for a Public Lighting deployment using LPWAN mesh.

### Smart Data Model Responsibility

Translating raw connectivity metrics into an operational-readiness status (e.g. "remotely controllable now: yes/no").

### Recommendation to the OMA Smart Cities Working Group

Define, in a Public Lighting profile, a minimum mandatory subset of Objects 4 or 3447 depending on the transport technology used.

## Water Management and Irrigation

### Municipality Operational Need

Municipalities need to know whether a water meter, irrigation valve, or pressure sensor can currently be remotely monitored or controlled, and whether an apparent fault is caused by a communication problem rather than the equipment itself.

### Existing Object and Resource Evidence

| Object | Resource evidence | Source / Owner | Requirement status | Reuse | Assessment |
|---|---|---|---|---|---|
| [`4`](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/4.xml) Connectivity Monitoring | `4/2` Radio Signal Strength; `4/3` Link Quality | 0 / OMA | M signal strength; O link quality | Reusable | Generic bearer-agnostic signal-quality Resources, equally applicable to a water/irrigation Client. |
| [`3447`](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/3447.xml) LPWAN Mesh Connectivity; [`3448`](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/3448.xml) LPWAN Mesh Statistics | `3447/3` Status; `3447/4` Connection Errors; `3448/4,9,11` packet-error counters | 1 / uCIFI | M status; O others | Object-specific | Mesh-specific connectivity status and error statistics, equally applicable where water or irrigation equipment shares the same 802.15.4-based mesh deployment as street lighting. |

### Coverage Assessment

**Existing OMA coverage.** The same bearer-level Objects used for Public Lighting apply directly to Water Management and Irrigation Clients, with no domain-specific gap.

### Missing Semantics

None material.

### Smart Data Model Responsibility

Translating raw connectivity metrics into an operational-readiness status for irrigation and metering equipment.

### Recommendation to the OMA Smart Cities Working Group

Extend the same minimum mandatory connectivity-monitoring subset recommended for Public Lighting to a Water/Irrigation profile, depending on the transport technology used.

---

# OMA Question 2

> Can communication quality be monitored?

## Public Lighting

### Coverage Assessment

**Existing OMA coverage.** Yes: `4/2` Radio Signal Strength, `3447/29-31` signal-to-noise ratio, RSSI, and noise floor all support continuous communication-quality monitoring.

### Recommendation to the OMA Smart Cities Working Group

None required.

## Water Management and Irrigation

### Coverage Assessment

**Existing OMA coverage.** The same bearer-level signal-quality Resources (`4/2`, `3447/29-31`) apply directly to water and irrigation equipment.

### Recommendation to the OMA Smart Cities Working Group

None required.

---

# OMA Question 3

> Can communication failures be distinguished from device failures?

## Public Lighting

### Existing Object and Resource Evidence

| Failure category | Object and Resource | Source / Owner | Assessment |
|---|---|---|---|
| Communication failure | `3447/4` Connection Errors; `3447/6` Error Counter; `3448` Tx/Rx discard and malformed-packet counters | 1 / uCIFI | Explicitly scoped to the mesh communication layer. |
| Communication failure (generic) | `3` Device `3/11` Error Code = 7 ("IP connectivity failure") | 0 / OMA | The Device object's own enumerated Error Code explicitly includes an IP connectivity failure value, distinct from other device errors. |
| Device intrinsic failure | `3/11` Error Code = 1 ("Low battery power"), 5 ("Out of memory"), 8 ("Peripheral malfunction") | 0 / OMA | Distinct, non-communication error categories in the same enumeration. |
| Device external asset failure | `3416/5` Lamp failure; `3416/7` Control gear failure | 1 / uCIFI | Asset-level failure indicators, structurally separate from both Device Error Code and connectivity Objects. |

### Coverage Assessment

**Existing OMA coverage.** The combination of the Device object's Error Code enumeration (which explicitly separates "IP connectivity failure" from other device error types) and the dedicated connectivity/mesh Objects provides a three-way distinction: communication failure, device intrinsic failure, and external asset failure.

### Missing Semantics

None material.

### Recommendation to the OMA Smart Cities Working Group

None required; document this three-way distinction explicitly in a Public Lighting profile for implementer clarity.

## Water Management and Irrigation

### Existing Object and Resource Evidence

| Failure category | Object and Resource | Source / Owner | Assessment |
|---|---|---|---|
| Communication failure | `3447/4` Connection Errors; `3448` Tx/Rx discard and malformed-packet counters | 1 / uCIFI | Explicitly scoped to the mesh communication layer, equally applicable to a water/irrigation Client. |
| Communication failure (generic) | `3/11` Error Code = 7 ("IP connectivity failure") | 0 / OMA | Same Device object Error Code enumeration applies regardless of the hosted application-layer Object. |
| Device external asset failure | `3424/9-13` leak/back-flow/blockage/fraud flags; `3427/3-4` leak/hammer-effect flags; `3425/6` Invalid scheduler | 1 / uCIFI | Asset-level anomaly indicators, structurally separate from both Device Error Code and connectivity Objects, mirroring the role of `3416/5,7` for lighting. |

### Coverage Assessment

**Existing OMA coverage.** The same three-way distinction (communication failure, device intrinsic failure, external asset failure) already identified for Public Lighting applies directly to water and irrigation equipment, using Objects 3424, 3425, and 3427 in place of 3416.

### Recommendation to the OMA Smart Cities Working Group

None required; document the same three-way distinction in a Water/Irrigation profile for implementer clarity.

---

# OMA Question 4

> Which additional capabilities would improve representation of network operability?

## Public Lighting

### Recommendation to the OMA Smart Cities Working Group

Define a minimum mandatory connectivity-monitoring subset per transport technology in a Public Lighting profile; no new Objects are required.

## Water Management and Irrigation

### Recommendation to the OMA Smart Cities Working Group

Define the same minimum mandatory connectivity-monitoring subset per transport technology in a Water/Irrigation profile; no new Objects are required.

---

# Network Operability Disposition Summary

| Classification | Finding |
|---|---|
| Existing OMA coverage | Objects 4, 7, 3447, and 3448 cover signal quality, traffic statistics, and mesh-specific error counters for any LwM2M Client, including water and irrigation equipment; Device Error Code explicitly separates connectivity failure from other error types. |
| Existing coverage requiring clarification or extension | No mandatory minimum subset defined per transport technology, for either domain. |
| New OMA capability required | None identified. |
| Outside OMA responsibility but must remain linkable | Translating raw metrics into an operational-readiness status for Digital Twins, for both lighting and water/irrigation equipment. |

---

# Semantic Capability 14: Fallback Behaviour

## Capability Purpose

Fallback Behaviour describes how a luminaire behaves autonomously when normal supervisory communication is unavailable, including local schedules and manual overrides.

## Overall Capability Conclusion

**Existing OMA coverage.**

The Program Scheduler family (3452–3457), combined with the manual-override Resources in Object 3416, provides one of the most complete autonomous and override-behaviour models in the Registry.

Object 3425 (Irrigation Valve) is explicitly designed to plug into the same Program Scheduler family via its `3425/5` Scheduler ID Resource, so the Fallback Behaviour model already described for Public Lighting applies directly to irrigation with no new Objects required; the main gap is that Object 3425 lacks a manual-override mechanism as well-defined as `3416`'s.

---

# OMA Question 1

> Which existing Objects and Resources represent fallback behaviour?

## Public Lighting

### Municipality Operational Need

Municipalities need assurance that street lighting continues operating safely and predictably if communication with the control platform is lost.

### Required OMA Contribution

**Configuration or operational intent**

- A locally stored default schedule and default operating values
- A manual-override mechanism with a bounded duration

### Existing Object and Resource Evidence

| Object | Resource evidence | Source / Owner | Requirement status | Reuse | Assessment |
|---|---|---|---|---|---|
| [`3416`](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/3416.xml) Outdoor Lamp Controller | `3416/4` Default dimming level; `3416/55` Default Light color temperature | 1 / uCIFI | O | Object-specific | Values applied autonomously "when no schedule nor manual override command is active." |
| [`3416`](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/3416.xml) Outdoor Lamp Controller | `3416/1` Command; `3416/50` Manual override start time; `3416/51` Manual override end time; `3416/53` Manual override default duration; `3416/54` Manual override active | 1 / uCIFI | M command; O others | Object-specific | Bounded manual-override mechanism that automatically expires and reverts to schedule/default. |
| [`3452`](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/3452.xml) Program Scheduler | `3452/1` State; `3452/2` Priority; `3452/3` Calendar Rules; `3452/4` Program Function; `3452/6-7` Output Instances/Targets | 1 / uCIFI | M | Object-specific | Full autonomous multi-program scheduling model with priority-based conflict resolution. |
| [`3453`](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/3453.xml) Calendar Rule | `3453/2` Start Date; `3453/3` End Date; `3453/4` Date Rule | 1 / uCIFI | O | Object-specific | Defines when a given schedule applies across the year, supporting seasonal fallback schedules. |
| [`3454`](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/3454.xml) Program Function | `3454/1` Run Condition; `3454/4-5` Time Input/Output Array | 1 / uCIFI | M | Object-specific | Defines the astronomical/time-based or sensor-based control logic executed locally, without supervisory involvement. |
| [`3457`](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/3457.xml) Program Manager | `3457/11` Error Conditions; `3457/13` Supported Capabilities | 1 / uCIFI | M | Object-specific | Reports scheduling-engine health and capabilities (e.g. astronomical events, calendar support), relevant to verifying fallback readiness. |

### Coverage Assessment

**Existing OMA coverage.** The Program Scheduler family provides a comprehensive, locally executable autonomous control model, and Object 3416 provides a well-defined, time-bounded manual-override mechanism that reverts automatically.

### Missing Semantics

None material for the autonomous/override behaviour itself.

### Smart Data Model Responsibility

Municipality-level policy defining which schedule should apply, and audit of when fallback behaviour was actually in effect.

### Recommendation to the OMA Smart Cities Working Group

Retain the Program Scheduler family and Object 3416 manual-override Resources as the reference fallback-behaviour model for Public Lighting profiles.

## Water Management and Irrigation

### Municipality Operational Need

Municipalities need assurance that irrigation continues operating on its configured schedule, and that a valve reverts to a safe default position, if communication with the control platform is lost.

### Required OMA Contribution

**Configuration or operational intent**

- A locally stored default valve position
- A locally executable irrigation schedule, reusing the same scheduling engine as Public Lighting

### Existing Object and Resource Evidence

| Object | Resource evidence | Source / Owner | Requirement status | Reuse | Assessment |
|---|---|---|---|---|---|
| [`3425`](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/3425.xml) Irrigation Valve | `3425/1` Default status | 1 / uCIFI | O | Object-specific | Default valve opening level "applied when the device is powered ON," the irrigation-domain analogue of `3416/4` Default dimming level. |
| `3425` Irrigation Valve | `3425/5` Scheduler ID | 1 / uCIFI | O | Object-specific | Identifiers of the schedulers assigned to the valve's Command, a direct, explicit reference into the same Program Scheduler family (3452–3457) used by Public Lighting, confirming the schedule framework is designed to be reused across domains rather than being lighting-specific. |
| [`3452`](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/3452.xml) Program Scheduler; [`3453`](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/3453.xml) Calendar Rule; [`3454`](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/3454.xml) Program Function; [`3457`](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/3457.xml) Program Manager | `3452/6-7` Output Instances/Targets able to reference a `3425` Instance | 1 / uCIFI | M | Object-specific | The same autonomous multi-program scheduling model, including priority-based conflict resolution and seasonal calendar rules, applies unchanged when its output target is an irrigation valve rather than a lamp controller. |
| `3425` Irrigation Valve | `3425/6` Invalid scheduler | 1 / uCIFI | O | Object-specific | Signals when an assigned scheduler cannot be executed, relevant to verifying fallback readiness, the irrigation-domain counterpart of `3457/11` Error Conditions. |

### Coverage Assessment

**Existing OMA coverage.** Object 3425 is explicitly designed to be driven by the same Program Scheduler family already assessed for Public Lighting, so the autonomous fallback model requires no new Objects; a Default status Resource provides a safe power-on value, directly mirroring `3416/4`.

### Missing Semantics

- Object 3425 has no equivalent of `3416/50-54` (manual override start/end time, default duration, and active flag); a manual override to 3425 relies solely on writing `3425/3` Command with no bounded-duration or active-flag mechanism.

### Smart Data Model Responsibility

Municipality-level policy defining which irrigation schedule should apply, and audit of when fallback behaviour was actually in effect.

### Recommendation to the OMA Smart Cities Working Group

Retain the Program Scheduler family and Object 3425's Scheduler ID linkage as the reference fallback-behaviour model for Water/Irrigation profiles; extend Object 3425 with bounded manual-override Resources (start time, end time, default duration, active flag) analogous to `3416/50-54`, which it currently lacks.

---

# OMA Question 2

> Can autonomous operating modes be represented?

## Public Lighting

### Coverage Assessment

**Existing OMA coverage.** Yes — the Program Scheduler/Calendar Rule/Program Function/Program Manager Object family is purpose-built for this, including priority-based conflict resolution (`3452/2`) and compound-operation composition (`3452/8`).

### Recommendation to the OMA Smart Cities Working Group

None required.

## Water Management and Irrigation

### Coverage Assessment

**Existing OMA coverage.** Yes — the same Program Scheduler/Calendar Rule/Program Function/Program Manager Object family drives Object 3425 via its Scheduler ID Resource, including the same priority-based conflict resolution and compound-operation composition available for lighting.

### Recommendation to the OMA Smart Cities Working Group

None required.

---

# OMA Question 3

> Can transitions between normal and fallback operation be identified?

## Public Lighting

### Existing Object and Resource Evidence

| Object and Resource | Source / Owner | Assessment |
|---|---|---|
| `3416/54` Manual override active | 1 / uCIFI | Directly indicates whether an override (a form of externally supervised behaviour) is currently in effect versus autonomous schedule execution. |
| `3457/11` Error Conditions (bit 0: "No valid program") | 1 / uCIFI | Indicates when the scheduling engine itself cannot execute a program, a relevant transition into a degraded/undefined state. |

### Coverage Assessment

**Existing coverage requiring clarification or extension.** The schedule is active 24/7 by design, so the only observable transition is the start/end of a manual override; there is no explicit Resource distinguishing "normal supervisory operation" from "loss of communication with the supervisory platform" as two separate states, since the schedule keeps running autonomously in both cases by design.

### Missing Semantics

- An explicit "supervisory link active" indicator, separate from Manual override active, to distinguish loss-of-communication fallback from intentional local autonomous operation.

### Smart Data Model Responsibility

Correlating Connectivity Monitoring/Statistics (Objects 4, 7, 3447) status with Program Scheduler activity to infer whether the current autonomous behaviour is due to a communication loss or normal design.

### Recommendation to the OMA Smart Cities Working Group

Consider clarifying, in a Public Lighting profile, that "supervisory link active" should be derived by correlating Connectivity Monitoring/Mesh status (Objects 4, 3447) with Program Scheduler state, since the Program Scheduler alone does not need to record this distinction.

## Water Management and Irrigation

### Existing Object and Resource Evidence

| Object and Resource | Source / Owner | Assessment |
|---|---|---|
| `3425/6` Invalid scheduler | 1 / uCIFI | Indicates when the assigned scheduler cannot be executed, a relevant transition into a degraded state, the irrigation-domain counterpart of `3457/11` Error Conditions. |

### Coverage Assessment

**Existing coverage requiring clarification or extension.** Object 3425 has no equivalent of `3416/54` Manual override active at all (see Question 1), so unlike Public Lighting, there is currently no explicit Resource distinguishing manually commanded operation from autonomous scheduler execution for irrigation valves.

### Missing Semantics

- A manual-override-active indicator for Object 3425 (see Question 1).
- The same "supervisory link active" gap identified for Public Lighting, since the scheduler runs autonomously regardless of supervisory connectivity.

### Smart Data Model Responsibility

Correlating Connectivity Monitoring/Statistics status with Program Scheduler activity for irrigation valves, mirroring the approach recommended for Public Lighting.

### Recommendation to the OMA Smart Cities Working Group

Once a manual-override-active Resource is added to Object 3425 (Question 1), apply the same "supervisory link active" correlation approach recommended for Public Lighting to Water/Irrigation profiles.

---

# OMA Question 4

> Which additional capabilities would improve fallback behaviour representation?

## Public Lighting

### Recommendation to the OMA Smart Cities Working Group

No new Objects are required. Document, in a Public Lighting profile, the correlation pattern between connectivity status and scheduler state described in Question 3.

## Water Management and Irrigation

### Recommendation to the OMA Smart Cities Working Group

No new Program Scheduler family Objects are required; add bounded manual-override Resources to Object 3425 (Question 1) and document, in a Water/Irrigation profile, the same correlation pattern between connectivity status and scheduler state described in Question 3.

---

# Fallback Behaviour Disposition Summary

| Classification | Finding |
|---|---|
| Existing OMA coverage | Program Scheduler family (3452–3457) for autonomous operation, reused unchanged by Object 3425 via its Scheduler ID Resource; Object 3416 manual-override mechanism with bounded duration and automatic reversion; Object 3425 Default status for a safe power-on value. |
| Existing coverage requiring clarification or extension | No explicit "supervisory link active" indicator separate from Manual override active, for either domain; Object 3425 additionally lacks any bounded manual-override mechanism comparable to `3416/50-54`. |
| New OMA capability required | Bounded manual-override Resources (start time, end time, default duration, active flag) for Object 3425; otherwise correlation with Connectivity Monitoring/Mesh status is sufficient for both domains. |
| Outside OMA responsibility but must remain linkable | Municipality policy defining applicable schedules and audit of fallback periods, for both lighting and irrigation. |

---

# Public Lighting Semantic Capability Assessment Summary

The table below consolidates the disposition of all fourteen semantic capabilities defined in the [Semantic Capability Assessment Framework](./semantic-capability-assessment.md), evaluated from the OMA point of view for the Public Lighting domain.

| # | Semantic Capability | Disposition |
|---|---|---|
| 1 | Service Outcome | Existing coverage requiring clarification or extension |
| 2 | Infrastructure Output | Existing OMA coverage |
| 3 | Resource Consumption | Existing OMA coverage |
| 4 | Observation Point | Existing coverage requiring clarification or extension |
| 5 | Observation Scope | Existing coverage requiring clarification or extension |
| 6 | Observation Method | New OMA capability required |
| 7 | Temporal Semantics | Existing OMA coverage |
| 8 | Provenance | Existing coverage requiring clarification or extension |
| 9 | Measurement Quality | Existing OMA coverage |
| 10 | Operational Context | Existing coverage requiring clarification or extension |
| 11 | Physical Context | Outside OMA responsibility but must remain linkable |
| 12 | Asset Management Context | Existing coverage requiring clarification or extension |
| 13 | Network Operability | Existing OMA coverage |
| 14 | Fallback Behaviour | Existing OMA coverage |

Across all fourteen capabilities, the recurring pattern is that the uCIFI Objects maintained by OMA already provide rich, purpose-built telemetry and control Resources for Public Lighting. The most common gap is not missing measurement capability, but the absence of a small number of reusable, cross-Object relationship and metadata patterns — a linked-asset/observation-point relationship, a generalized observation-method Resource, and a generalized aggregation-window Resource — that, if standardized once, would close most of the "requiring clarification or extension" findings above.
