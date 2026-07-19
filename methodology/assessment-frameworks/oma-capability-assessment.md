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

This report assesses the minimum semantic information that OMA LwM2M devices
and edge controllers need to provide so that their information can be
integrated into Smart Data Models without losing operational meaning.

The final municipality operational questions are answered by a Digital Twin,
not by an individual LwM2M Object. The intended information chain is:

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

OMA is therefore not expected to represent all municipality context or answer
municipality questions independently. OMA is expected to provide explicit,
interoperable telemetry, locally required configuration, and device-level
metadata and relationships. Smart Data Models add municipality context and
preserve the OMA contribution for use by Digital Twins.

---

# Assessment Baseline and Scope

This report uses the following source revisions:

- Smart Cities SIG semantic framework branch:
  `smartcities-sig/assesment-framework`
- Semantic framework commit:
  `8ad0acce94fdb7e5abed6b887a52d05543d111ef`
- OMA LwM2M Registry branch:
  `lwm2m-registry/prod`
- OMA LwM2M Registry commit:
  `02f68c93a2238b552aea481bb22aea6d49615839`

The assessment is currently limited to:

- Public Lighting
- Water Management and Irrigation

Only current Object definitions in the root of the LwM2M Registry are
assessed. Definitions in `version_history` are excluded. A Resource is treated
as reusable only when it is present in `Common.xml`.

The following Object Source classifications are used:

- **Source 0** — Object defined by OMA.
- **Source 1** — Object originally defined by another organization. IPSO and
  uCIFI Objects retain Source 1 and their original Owner even though these
  Object families are now maintained by OMA.
- **Source 2** — Private Object. A private Object may provide implementation
  evidence, but a generally interoperable OMA capability normally requires a
  new Source 0 definition.

New Objects based on IPSO or uCIFI work are expected to use Source 0. Final
normative design and Object ID allocation remain the responsibility of the OMA
Smart Cities Working Group.

---

# How to Read This Assessment

Each Question for OMA is assessed using the same structure. Public Lighting
and Water Management/Irrigation are evaluated separately, followed by findings
shared across both domains.

## Municipality Operational Need

Explains why the information is required and which Municipality Operational
Questions depend on it. This section describes the final operational purpose,
not a responsibility assigned exclusively to OMA.

## Required OMA Contribution

Defines the minimum information that an LwM2M device or edge controller must
provide so that the information can be integrated into a Smart Data Model
without losing its meaning.

The OMA contribution is classified as:

- **Telemetry** — Information observed or reported by a device.
- **Configuration or operational intent** — Information supplied to a device
  because it is required for local operation.
- **Metadata and relationships** — Information identifying what was observed
  and how it relates to other local entities.

Externally supplied information belongs in Smart Data Models unless a device
needs that information for local operation.

## Existing Object and Resource Evidence

Lists current Registry Objects and Resources that may provide the required
information. Each entry identifies:

- Object ID and Object name
- Resource ID and Resource name
- Source and Owner
- Mandatory or optional status
- Whether the Resource is defined in `Common.xml`
- The part of the semantic requirement it supports

Inclusion as evidence does not automatically mean that the complete semantic
capability is supported.

## Coverage Assessment

Evaluates how completely the current Registry supports the required OMA
contribution. The available classifications are:

- **Existing OMA coverage** — The required capability is adequately
  represented by an OMA-defined mechanism.
- **Existing coverage requiring clarification or extension** — Relevant
  Objects or Resources exist, but semantics, relationships, mandatory status,
  or interoperability constraints are incomplete.
- **New OMA capability required** — No adequate standardized mechanism exists.
- **Outside OMA responsibility but must remain linkable** — The information
  belongs in another ecosystem, but OMA information must provide identifiers
  or relationships that allow integration.

Optional Resources are treated as conditional coverage. Co-location of Objects
on the same LwM2M Client is treated as indirect or ambiguous unless an explicit
relationship is provided.

## Missing Semantics

Identifies information that cannot be represented explicitly and
interoperably using the current Objects and Resources. This may include missing
controlled terminology, relationships, observation context, provenance,
method classification, scope, aggregation information, or mandatory profile
requirements.

## Smart Data Model Responsibility

Identifies context that should be represented or added by the corresponding
Smart Data Model rather than by an LwM2M device. Examples include municipality
service objectives, policies, compliance thresholds, geographic and
administrative relationships, service areas, infrastructure topology,
cross-device aggregation, and the final determination of whether a municipality
objective was achieved.

This section also identifies which OMA identifiers and relationships must be
preserved during mapping.

## Recommendation to the OMA Smart Cities Working Group

Translates the assessment into an actionable semantic requirement or plausible
implementation option. Recommendations may include:

- Clarifying an existing Object or Resource
- Making an optional Resource required by a Smart Cities profile
- Defining a controlled vocabulary
- Adding reusable Resources
- Extending an existing Object
- Defining a new Source 0 Object
- Leaving information to Smart Data Models while ensuring that it remains
  linkable

Recommendations do not allocate Object IDs or prescribe the final normative
design.

## Evidence Conventions

The following abbreviations are used in evidence tables:

- **M** — Mandatory Resource in the consuming Object.
- **O** — Optional Resource in the consuming Object; coverage is conditional.
- **Reusable** — The Resource is defined in `Common.xml`.
- **Object-specific** — The Resource is not defined in `Common.xml`.

A Resource may be mandatory without being reusable, or reusable without being
mandatory. Mandatory status is determined by the consuming Object definition.

Free-text Resources do not provide sufficient cross-vendor semantics unless a
controlled vocabulary or profile governs their values.

---

# Semantic Capability 1: Service Outcome

## Capability Purpose

Service Outcome represents the real-world result that a municipality intends
to deliver, independently of how the underlying infrastructure behaves.

For Public Lighting, the outcome includes the illumination experienced on a
road, pavement, pedestrian area, or other public space. For Water Management
and Irrigation, the outcome includes water delivered at the required flow,
pressure, level, quality, or soil/root-zone condition.

The municipality-level classification of an observation as a service outcome
normally belongs in a Smart Data Model. OMA must provide sufficiently explicit
observations and relationships so that the classification can be made without
guessing from Object identity or Client co-location.

## Overall Capability Conclusion

**Existing coverage requiring clarification or extension.**

The Registry can report most of the physical measurements required to evaluate
service outcomes. It does not consistently describe:

- The observation point or feature being observed
- How the observation relates to an infrastructure asset or service endpoint
- Whether the value was measured, estimated, inferred, predicted, simulated,
  proxy-derived, or aggregated
- The distinction between a service-related observation and infrastructure
  output
- Which municipality objective, policy, or service area applies

The last item normally belongs in a Smart Data Model. The first four require
additional or clarified OMA semantics when they are known by the device or edge
controller.

---

# OMA Question 1

> Which existing LwM2M Objects and Resources represent the service outcome?

## Public Lighting

### Municipality Operational Need

Municipalities need to determine whether streets and public spaces are
adequately illuminated, identify under- or over-illuminated areas, and evaluate
whether lighting objectives are achieved.

### Required OMA Contribution

**Telemetry**

- Illuminance value
- Unit
- Measurement timestamp
- Measurement quality when available

**Metadata and relationships**

- Identity of the observing sensor
- Observation point, such as luminaire, pole, road surface, pavement, or
  pedestrian area
- Feature or local asset represented by the observation

No municipality lighting policy needs to be stored by the device unless it is
required for local control.

### Existing Object and Resource Evidence

| Object | Resource evidence | Source / Owner | Requirement status | Reuse | Assessment |
|---|---|---|---|---|---|
| `3301` Illuminance | `3301/5700` Sensor Value | 1 / IPSO Alliance | M | Reusable | Direct illuminance measurement. It does not identify the observation point or represented public space. |
| `3301` Illuminance | `3301/5701` Sensor Units | 1 / IPSO Alliance | O | Reusable | Conditional unit metadata. |
| `3301` Illuminance | `3301/5518` Timestamp | 1 / IPSO Alliance | O | Reusable | Conditional measurement time. |
| `3301` Illuminance | `3301/6042` Measurement Quality Indicator; `3301/6049` Measurement Quality Level | 1 / IPSO Alliance | O | Reusable | Conditional measurement quality. |
| `3301` Illuminance | `3301/5750` Application Type | 1 / IPSO Alliance | O | Reusable | Free text can describe a use case, but cannot reliably establish road-surface or pedestrian-area semantics. |
| `3392` oA Logical Illuminance Sensor | `3392/404` Sensor Value | 1 / OpenAIS | M | Object-specific | Direct illuminance reading in lux. |
| `3392` oA Logical Illuminance Sensor | `3392/909` Executing Object | 1 / OpenAIS | M | Object-specific | Core Link to an executing Object Instance. Provides an explicit relationship, but not a general observed-feature model. |
| `3398` oA Physical Illuminance Sensor | `3398/908` Mounting Location | 1 / OpenAIS | M | Object-specific | Site-specific free-text mounting location. The definition is building-oriented and lacks a controlled vocabulary. |
| `3300` Generic Sensor | `3300/5700` Sensor Value; `3300/5750` Application Type | 1 / IPSO Alliance | M value; O application type | Reusable | Generic fallback. Semantically weaker than Object 3301 because the observed property depends on free text and optional units. |
| `509` Measurement Metadata | `509/0` Linked Sensor | 0 / OMA | M | Object-specific | Source 0 foundation for linking metadata to a sensor Object Instance. It does not identify observation point, observed feature, or method. |

### Coverage Assessment

**Existing coverage requiring clarification or extension.**

Illuminance values are directly represented. Supporting units, timestamp, and
quality are optional. No general OMA mechanism states whether the measurement
was taken at the luminaire, at a reference plane, or on the road surface.

### Missing Semantics

- Controlled Public Lighting observation-point terminology
- Explicit observed-feature relationship
- Explicit relationship between logical observation and the public-space entity
  represented
- Profile requirement for timestamp, units, and quality metadata

### Smart Data Model Responsibility

The Smart Data Model should represent:

- Road, street, pavement, pedestrian area, or public-space identity
- Municipality lighting objective and applicable standard
- Required illumination range
- Spatial aggregation and compliance determination

The mapping must preserve sensor identity, observation point, value, unit,
timestamp, and quality.

### Recommendation to the OMA Smart Cities Working Group

Retain Object 3301 as the primary illuminance measurement Object. Define a
standardized observation-point and observed-feature relationship, potentially
by extending Source 0 Object 509 or by defining reusable metadata Resources.
Define a Public Lighting profile that makes required contextual Resources
mandatory when they are needed for interoperable service-outcome assessment.

## Water Management and Irrigation

### Municipality Operational Need

Municipalities need to determine whether water reaches its intended location,
whether consumers receive adequate pressure, whether plants receive sufficient
irrigation, and whether the required water service outcome is achieved.

### Required OMA Contribution

**Telemetry**

- Water flow, accumulated volume, pressure, level, soil moisture, and relevant
  water-quality measurements
- Unit, timestamp, and quality
- Interval or aggregation information when the reported value is not
  instantaneous

**Metadata and relationships**

- Observation point, such as pump outlet, valve, pipeline, consumer delivery
  point, irrigation zone, soil layer, or root zone
- Observed medium or feature
- Relationship to a locally known asset or service endpoint

### Existing Object and Resource Evidence

| Object | Resource evidence | Source / Owner | Requirement status | Reuse | Assessment |
|---|---|---|---|---|---|
| `3300` Generic Sensor | `3300/5700` Sensor Value; `3300/5701` Units; `3300/5750` Application Type | 1 / IPSO Alliance | M value; O units and application type | Reusable | Generic fallback. The measured property depends on optional free text. |
| `3320` Percentage | `3320/5700` Sensor Value; `3320/5750` Application Type | 1 / IPSO Alliance | M value; O application type | Reusable | Can carry soil-moisture percentage, but soil moisture and root-zone semantics are not standardized. |
| `3323` Pressure | `3323/5700` Sensor Value | 1 / IPSO Alliance | M | Reusable | Direct pressure measurement. The network or consumer observation point is absent. |
| `3319` Depth | `3319/5700` Sensor Value | 1 / IPSO Alliance | M | Reusable | Can represent water depth or level when deployment context supplies the meaning. |
| `3346` Rate | `3346/5700` Sensor Value | 1 / IPSO Alliance | M | Reusable | Can represent water flow rate. The medium and observation point are not explicit. |
| `3303` Temperature | `3303/5700` Sensor Value | 1 / IPSO Alliance | M | Reusable | Supports water temperature when it is part of the required service outcome. |
| `3325` Concentration | `3325/5700` Sensor Value | 1 / IPSO Alliance | M | Reusable | Generic constituent concentration; the constituent requires additional semantics. |
| `3326` Acidity | `3326/5700` Sensor Value | 1 / IPSO Alliance | M | Reusable | Direct acidity measurement. |
| `3327` Conductivity | `3327/5700` Sensor Value | 1 / IPSO Alliance | M | Reusable | Direct conductivity measurement. |
| `3424` Water Meter | `3424/1` Cumulated Water Volume | 1 / uCIFI | M | Object-specific | Strong delivered-volume evidence when the meter is located at a delivery point. The delivery-point relationship is absent. |
| `3424` Water Meter | `3424/7` Minimum Flow Rate; `3424/8` Maximum Flow Rate | 1 / uCIFI | O | Object-specific | Conditional extrema; no mandatory current flow value. |
| `3426` Water Quality Sensor | `3426/1-14` water-quality measurements | 1 / uCIFI | O | Object-specific | Broad water-quality coverage, but no individual measurement is mandatory. |
| `3427` Pressure Monitoring Sensor | `3427/1` Pressure | 1 / uCIFI | M | Object-specific | Strong water-specific pressure measurement. Its position in the network is unspecified. |
| `3445` Stream Gauge | `3445/1` Water Level; `3445/2` Volumetric Discharge | 1 / uCIFI | M level; O discharge | Object-specific | Supports water level and conditional discharge. The represented location is absent. |
| `10266` Water Flow Readings | `10266/6029` Latest Payload | 2 / South East Water Corporation | M | Reusable | Private interval-data precedent. The payload is opaque and lacks a general aggregation-method declaration. |
| `10269` Pressure Readings | `10269/6029` Latest Payload | 2 / South East Water Corporation | M | Reusable | Private interval pressure precedent. |
| `10487` Water Level Readings | `10487/6029` Latest Payload | 2 / South East Water Corporation | M | Reusable | Private interval water-level precedent. |
| `10507` Electrical Conductivity Readings | `10507/6029` Latest Payload | 2 / South East Water Corporation | M | Reusable | Private interval conductivity precedent. |
| `509` Measurement Metadata | `509/0` Linked Sensor | 0 / OMA | M | Object-specific | Source 0 sensor-metadata link foundation; observation point and observed feature remain absent. |

The interval Objects also use reusable Resources such as `6000` Interval
Period, `6003` Interval Collection Start Time, `6004` Oldest Recorded Interval,
and `6006` Latest Recorded Interval. These provide temporal context but do not
fully describe the aggregation function or observation point.

### Coverage Assessment

**Existing coverage requiring clarification or extension.**

Most physical quantities are available through IPSO and uCIFI Objects now
maintained by OMA. Root-zone soil moisture remains semantically weak because it
depends on Object 3320 plus optional free-text Application Type. Private Source
2 Objects demonstrate interval-data patterns but do not constitute general
Source 0 OMA coverage.

### Missing Semantics

- Standardized soil-moisture and root-zone representation
- Controlled Water/Irrigation observation-point terminology
- Explicit observed-medium and observed-feature relationships
- Link from a measurement to a consumer delivery point, irrigation zone, soil
  layer, or root zone
- General aggregation function for interval values
- Mandatory contextual metadata profile

### Smart Data Model Responsibility

The Smart Data Model should represent:

- Water network and irrigation topology
- Consumer, service area, irrigation zone, plant, and root-zone identity
- Required pressure, volume, moisture, and water-quality objectives
- Municipality policy and compliance determination
- Cross-device and geographic aggregation

The mapping must preserve measurement identity, observation point, value,
unit, timestamp, quality, and interval semantics.

### Recommendation to the OMA Smart Cities Working Group

Use existing IPSO and uCIFI measurement Objects where their physical quantity
semantics are sufficient. Define controlled observation-point and
observed-feature relationships. Standardize soil-moisture/root-zone semantics.
Use the Source 2 interval Objects as implementation evidence, but define a
Source 0 pattern if generalized interval observations are adopted by OMA.

## Shared Cross-Domain Finding

The Registry represents physical quantities more effectively than it represents
their operational role. The Smart Data Model should classify an observation as
a municipality service outcome. OMA should make that classification possible
by exposing explicit observation point, observed feature, timestamp, units,
quality, and method metadata.

---

# OMA Question 2

> How is the distinction maintained between service outcome and infrastructure
> output?

## Public Lighting

### Municipality Operational Need

A municipality must distinguish inadequate road or pedestrian-area
illumination from normal luminaire operation. A luminaire may be switched on
and operating at its commanded dimming level while the public space remains
under-illuminated.

### Required OMA Contribution

**Telemetry**

- Illuminance at the relevant observation point
- Luminaire operating state and output-related telemetry

**Metadata and relationships**

- Explicit relationship between the illuminance observation, its observation
  point, and the relevant lighting asset when known locally

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

Separate sensor and controller Objects create a structural distinction, but no
general relationship states which illuminance observation results from which
luminaire or which public space it represents. Client co-location is ambiguous.

### Missing Semantics

- Explicit observation-to-asset relationship
- Explicit observation-point relationship
- Controlled distinction between luminaire output and public-space illuminance

### Smart Data Model Responsibility

The Smart Data Model should classify road-surface or public-space illuminance
as the service outcome and relate it to lighting assets, roads, and applicable
objectives.

### Recommendation to the OMA Smart Cities Working Group

Do not infer service outcome from Object ID or Client co-location. Define a
standard relationship from measurement metadata to the observed lighting asset
and observation point.

## Water Management and Irrigation

### Municipality Operational Need

A municipality must distinguish water delivered to a consumer or root zone
from the behaviour of pumps, valves, tanks, and pipelines. An open valve does
not prove that sufficient water reached its intended destination.

### Required OMA Contribution

**Telemetry**

- Outcome-related flow, volume, pressure, level, or soil moisture
- Pump, valve, and discharge state when locally observable

**Metadata and relationships**

- Explicit relationship between an observation, its observation point, and
  the relevant local infrastructure asset or endpoint

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

The same Pressure Object can describe consumer pressure, pump outlet pressure,
pipeline pressure, or valve-adjacent pressure. Object identity does not
establish its operational role.

### Missing Semantics

- Observation point and network role
- Explicit link between measurement and local asset or endpoint
- Standard soil/root-zone relationship
- Delivered-versus-commanded distinction for water volume

### Smart Data Model Responsibility

The Smart Data Model should classify observations as consumer service,
irrigation outcome, or infrastructure behaviour using network topology,
service-area relationships, and municipality objectives.

### Recommendation to the OMA Smart Cities Working Group

Define explicit observation-point and observed-feature relationships. Preserve
the distinction between actuator command, actual actuator state, infrastructure
measurement, and endpoint outcome measurement.

## Shared Cross-Domain Finding

The municipality-level concept of Service Outcome normally belongs in the
Smart Data Model. OMA does not need to add a universal `Service Outcome` flag if
it exposes the observation point, observed feature, and relevant local asset
relationships needed for deterministic classification.

---

# OMA Question 3

> How are measured, estimated, inferred, predicted, or aggregated service
> outcomes represented?

## Public Lighting

### Municipality Operational Need

A municipality must know whether illuminance was directly measured or derived
from luminaire characteristics, simulation, historical information, or an
analytical model. Different methods have different levels of authority for
compliance and operational decisions.

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
- **Estimated, inferred, predicted, simulated, or proxy-derived:** New OMA
  capability required.
- **Aggregated:** No general Public Lighting representation identified.

### Missing Semantics

- Controlled observation-method vocabulary
- Derivation and source-observation relationships
- Aggregation function and window
- Model identity for locally generated values

### Smart Data Model Responsibility

The Smart Data Model should carry external model provenance, simulation
lineage, and analytical workflow information. OMA should report such
information only when the value is calculated locally or affects local
operation.

### Recommendation to the OMA Smart Cities Working Group

Define reusable observation-method metadata. Consider extending Source 0
Object 509 so that method metadata can be linked to an existing sensor Object
Instance.

## Water Management and Irrigation

### Municipality Operational Need

A municipality must distinguish measured soil moisture, pressure, flow, and
water quality from estimates, forecasts, model-derived irrigation needs, and
time-aggregated readings.

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
- **Estimated, inferred, predicted, simulated, or proxy-derived:** New OMA
  capability required.

### Missing Semantics

- Controlled observation-method vocabulary
- Aggregation function, including sum, mean, minimum, maximum, or other method
- Prediction horizon and validity interval
- Link to local source observations or model

### Smart Data Model Responsibility

The Smart Data Model should represent externally generated forecasts,
irrigation recommendations, analytical lineage, and model provenance. OMA
should represent locally generated predictions or recommendations when they
affect device operation.

### Recommendation to the OMA Smart Cities Working Group

Use the Source 2 interval Objects as implementation evidence, but create a
Source 0 generalized mechanism if OMA standardizes interval observations.
Define reusable observation-method and aggregation metadata.

## Shared Cross-Domain Finding

Measured values are well represented. The principal cross-domain gap is the
absence of standardized method metadata. Method must not be inferred from an
Object name such as `Virtual Sensor`.

---

# OMA Question 4

> How is the observation location represented?

## Public Lighting

### Municipality Operational Need

Illuminance measured inside a luminaire, at the pole, or on a road surface has
different operational meaning. Municipality comparisons require the actual
observation point and represented public space.

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

Location can describe the Client or sensor, but not reliably the road surface,
reference plane, or public-space feature represented by the observation.

### Missing Semantics

- Controlled Public Lighting observation-point type
- Link from measurement to observation point
- Distinction between device location and represented-feature location

### Smart Data Model Responsibility

The Smart Data Model should relate the OMA observation point to a road, street,
pavement, pedestrian area, or public-space entity.

### Recommendation to the OMA Smart Cities Working Group

Define observation-point metadata separately from generic Client location.
Provide an explicit link from measurement metadata to the observation point.

## Water Management and Irrigation

### Municipality Operational Need

Pressure at a pump differs from pressure at a consumer. Soil moisture near the
surface differs from moisture at root depth. Flow at a valve differs from water
delivered to an irrigation zone.

### Required OMA Contribution

**Telemetry**

- Coordinates, depth, or local position when known by the device

**Configuration or operational intent**

- Sensor offset or locally required installation geometry

**Metadata and relationships**

- Observation-point type
- Link to local pipeline, valve, meter, tank, soil layer, root zone, or endpoint
  when known locally

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

The Registry can represent coordinates and some private installation metadata,
but cannot generally identify consumer delivery point, network position, soil
layer, or root zone.

### Missing Semantics

- Controlled Water/Irrigation observation-point type
- Soil depth and root-zone semantics
- Network-position and consumer-endpoint relationships
- Distinction between device location and represented location

### Smart Data Model Responsibility

The Smart Data Model should relate the OMA observation point to the municipal
water network, irrigation topology, consumer, service area, plant, and root
zone.

### Recommendation to the OMA Smart Cities Working Group

Define reusable observation-point and observed-feature relationships. Use
private Object 10502 as implementation evidence for installation metadata, but
standardize any general capability as Source 0.

## Shared Cross-Domain Finding

Generic Client location is insufficient for outcome interpretation. OMA needs
to distinguish sensor location, observation point, and represented-feature
location. The Smart Data Model then maps those identifiers into municipality
geography and topology.

---

# OMA Question 5

> Which additional capabilities, if any, would improve representation of
> municipality service outcomes?

## Public Lighting

### Municipality Operational Need

Municipalities need interoperable illuminance observations that can be mapped
to roads and public spaces and distinguished from luminaire output.

### Required OMA Contribution

- Controlled lighting observation-point semantics
- Explicit observation-to-point and observation-to-asset relationships
- Method, timestamp, unit, and quality metadata
- Locally required threshold or target only when used for autonomous operation

### Existing Object and Resource Evidence

Objects 3301, 3392, 3398, 3416, and 3417 collectively demonstrate the value,
sensor, controller, physical-device, and luminaire-asset concepts. Object 509
provides a Source 0 measurement-metadata foundation. No single composition
connects all concepts using reusable, cross-domain relationships.

### Coverage Assessment

**New OMA capability required for standardized relationships and method
metadata. Existing Objects should be reused for physical quantities.**

### Missing Semantics

- Road-surface, pavement, pedestrian-area, pole, cabinet, and luminaire
  observation-point vocabulary
- Observed-feature and relevant-asset links
- Observation method and aggregation metadata
- Public Lighting profile requirements for optional measurement context

### Smart Data Model Responsibility

The Smart Data Model owns municipality geography, policy, required illumination,
service areas, and compliance results.

### Recommendation to the OMA Smart Cities Working Group

1. Retain Object 3301 for illuminance.
2. Extend Object 509 or define reusable metadata Resources for observation
   point, observed feature, method, and aggregation.
3. Define a Public Lighting profile that constrains observation-point terms and
   requires appropriate timestamp, unit, and quality information.
4. Ensure measurements can be linked to Objects 3416 and 3417 when that
   relationship is locally known.

## Water Management and Irrigation

### Municipality Operational Need

Municipalities need outcome observations associated with consumer delivery
points, irrigation zones, soil/root conditions, and relevant water-network
locations.

### Required OMA Contribution

- Controlled water and irrigation observation-point semantics
- Standard soil-moisture/root-zone representation
- Explicit relationships to local assets and service endpoints
- Observation method and generalized interval/aggregation metadata
- Locally required targets, schedules, or thresholds only when needed for
  autonomous operation

### Existing Object and Resource Evidence

IPSO and uCIFI Objects provide most physical quantities. Source 2 South East
Water Corporation Objects provide interval-observation and installation
precedents. Object 509 provides a Source 0 link from metadata to a sensor but
lacks the required observation context.

### Coverage Assessment

**Existing coverage requiring extension, plus new Source 0 capabilities for
generalized metadata and interval observations.**

### Missing Semantics

- Standard soil-moisture and root-zone model
- Consumer endpoint, network position, soil layer, and irrigation-zone
  observation-point vocabulary
- Observed-feature and local-asset relationships
- Generalized aggregation function and observation method
- Water/Irrigation profile requirements for optional context

### Smart Data Model Responsibility

The Smart Data Model owns network topology, consumer and service-area
relationships, plant requirements, municipal objectives, policies, and final
service evaluation.

### Recommendation to the OMA Smart Cities Working Group

1. Reuse existing IPSO and uCIFI physical-quantity Objects.
2. Standardize soil-moisture/root-zone semantics.
3. Extend Object 509 or define reusable Source 0 metadata for observation point,
   observed feature, method, and aggregation.
4. Generalize the useful interval-data pattern demonstrated by Source 2 Objects
   into Source 0 if adopted by OMA.
5. Define a Water/Irrigation profile that makes necessary context mandatory.

## Shared Cross-Domain Recommendation

The OMA Smart Cities Working Group should consider a reusable Source 0
measurement-context pattern with the following semantic capabilities:

- Linked sensor
- Observation point
- Observed feature
- Relevant local asset or endpoint
- Observation method
- Aggregation function and interval
- Source observations when locally available
- Prediction horizon for locally generated predictions
- Timestamp, units, and measurement quality profile requirements

Municipality objectives, policies, service-area definitions, topology, and
final service-outcome evaluation should remain outside OMA unless required for
local device operation. OMA must provide stable identifiers and relationships
that allow Smart Data Models to add that context without ambiguity.

---

# Service Outcome Disposition Summary

| Classification | Finding |
|---|---|
| Existing OMA coverage | Source 0 Location Object 6 and Measurement Metadata Object 509 provide useful foundations. |
| Existing coverage requiring clarification or extension | IPSO and uCIFI Objects provide most required physical measurements, but observation context and relationships are incomplete. |
| New OMA capability required | Observation-point and observed-feature relationships, observation-method classification, generalized aggregation semantics, and standardized soil-moisture/root-zone semantics. |
| Outside OMA responsibility but must remain linkable | Municipality objectives, policies, geographic service areas, infrastructure topology, plant requirements, consumer relationships, cross-device aggregation, and final outcome evaluation. |
