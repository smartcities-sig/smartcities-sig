# Public Street Lighting Walkthrough

## Introduction

This walkthrough demonstrates how the Smart Cities SIG methodology was applied to analyze municipality operational material related to Public Street Lighting.

The objective of this walkthrough is not to:
- define a final technical architecture,
- prescribe a specific standards implementation,
- or define a completed semantic model.

Instead, the objective is to demonstrate how municipality operational realities can progressively evolve into:
- operational understanding,
- reusable interoperability abstractions,
- ecosystem coordination considerations,
- semantically enriched interoperability structures,
- and trustworthy Digital Twin integration thinking.

This walkthrough became one of the foundational practical examples used to shape the Smart Cities SIG methodology itself.

The walkthrough follows the three-stage methodology described in:
- [`methodology-overview.md`](./methodology-overview.md)
- [`stage-1-operational-meaning.md`](./stage-1-operational-meaning.md)
- [`stage-2-reusable-abstractions.md`](./stage-2-reusable-abstractions.md)
- [`stage-3-standards-mapping.md`](./stage-3-standards-mapping.md)

---

# Municipality Operational Reality

The lighting document is not simply asking for:
- lamp telemetry,
- isolated IoT measurements,
- or device-level monitoring.

Instead, the municipality is implicitly asking:

> What must be known about a public lighting service so that municipalities, platforms, Digital Twins, and external ecosystems can interpret the information consistently and operationally reliably?

The municipality operational objective identified in the source material was:

> Ensure public street lighting service in the most efficient possible way.

This objective immediately revealed two parallel operational viewpoints:

| Viewpoint | What It Measures | Why It Matters |
|---|---|---|
| Service-effectiveness view | Lux on street surface | Is the street adequately illuminated? |
| Cost/energy view | Lumens emitted, watts consumed, line power | What does it cost to provide the service? |

One of the earliest semantic observations emerged immediately:

- lux,
- lumens,
- and watts
are not equivalent measurements.

They represent different operational meanings and different perspectives of the service.

This distinction later became one of the foundational semantic examples of the methodology.

---

# Stage 1 — Operational Meaning Discovery

## Initial Operational Observations

The municipality material revealed concerns related to:
- operational trustworthiness,
- comparability,
- contextual interpretation,
- aggregation,
- environmental influence,
- teleoperation reliability,
- and semantic consistency.

The analysis therefore focused first on:
- understanding what the municipality was trying to achieve,
- and understanding what the operational information actually meant.

The municipality operational concerns extended beyond:
- simple telemetry collection,
- or isolated infrastructure measurements.

Instead, the municipality was implicitly describing:
- interoperability reliability challenges,
- Digital Twin trust concerns,
- and semantic interpretation problems.

---

# Operational Pain Points

The walkthrough progressively identified several real operational pain points.

| Operational Pain Point | Interoperability Meaning |
|---|---|
| Measurements may occur at the luminaire or at the cabinet/line head | Data must identify the measurement point and scope |
| Cabinet measurements may represent many luminaires | Data must describe aggregation and number of represented luminaires |
| Lux may be desired but only lumens may be available | Data must distinguish directly measured values from inferred/proxy values |
| Trees, buildings, fog, humidity, orientation, and inclination affect lighting outcomes | Context metadata is required for reliable interpretation |
| Data resolution affects comparability | Minimum precision and temporal granularity must be represented |
| Operational systems may aggregate historical data | Real-time vs historical resolution must remain explicit |
| Teleoperation depends on latency and packet loss | Network behavior becomes part of operational trustworthiness |

One of the strongest observations from the walkthrough was:

> The municipality is not only asking what data exists, but whether the data is comparable, interpretable, contextualized, and operationally trustworthy.

This became one of the central conceptual foundations of the methodology.

---

# Semantic Distinction Analysis

## Lux vs Lumens vs Watts

One of the earliest discoveries was that:
- lux,
- lumens,
- and watts
represent fundamentally different operational meanings.

| Measurement | Operational Meaning |
|---|---|
| Lux | Service outcome experienced in public space |
| Lumens | Infrastructure output behavior |
| Watts | Resource consumption |

This distinction became one of the strongest examples used throughout the methodology.

The municipality operational objective was not:
- simply to emit lumens,
- or simply to minimize watts consumed.

The real operational objective was:
- to provide effective public illumination while maintaining operational efficiency.

This distinction later influenced:
- reusable abstraction analysis,
- interoperability thinking,
- and Digital Twin interpretation considerations.

---

## Service Outcome vs Infrastructure Output

The walkthrough identified an important distinction between:
- what the municipality wants to achieve operationally,
- and what the infrastructure physically emits.

Examples:
- lumens represent infrastructure output,
- while lux at street level represents the actual public-space service outcome experienced by citizens.

This observation demonstrated that:
- infrastructure telemetry alone may not fully represent operational effectiveness.

Operational interpretation therefore requires:
- contextual understanding,
- semantic distinctions,
- and environmental awareness.

---

## Measured vs Inferred Values

The municipality material also described situations where:
- direct measurements may not be available,
- and operational values may need to be inferred.

Examples included:
- estimating lux from lumens,
- or deriving operational conditions from aggregated infrastructure measurements.

This observation introduced several important interoperability concerns:

| Semantic Distinction | Why It Matters |
|---|---|
| Direct measurement vs inferred value | Trust and interpretation differ |
| Real-time data vs historical aggregated data | Time resolution affects comparability and Digital Twin usefulness |
| Device-provided location vs installation-recorded location | Source of context metadata must remain identifiable |

The walkthrough progressively identified that:
- provenance,
- trustworthiness,
- aggregation,
- and contextual interpretation
must remain semantically distinguishable.

---

## Measurement Scope and Aggregation

The municipality material revealed that operational measurements may represent:
- individual luminaires,
- electrical cabinets,
- operational lines,
- or aggregated operational zones.

This introduced important interoperability concerns related to:
- operational scope,
- aggregation semantics,
- and interpretation reliability.

Examples included:
- cabinet measurements representing multiple luminaires,
- aggregated operational measurements,
- and grouped operational zones.

The walkthrough progressively identified that:
- operational scope must remain explicit,
- otherwise measurements may become semantically ambiguous.

---

## Environmental and Contextual Dependencies

The municipality material repeatedly emphasized that operational interpretation depends heavily on environmental and physical context.

Examples included:
- weather,
- fog,
- humidity,
- vegetation,
- nearby buildings,
- shadows,
- orientation,
- and inclination.

This observation became one of the foundational principles of the walkthrough:

> Interoperability requires contextual integrity.

The walkthrough progressively demonstrated that:
- measurements alone are insufficient,
- and operational interpretation requires contextual metadata.

For example:
- identical infrastructure outputs may produce different public-service outcomes depending on environmental conditions.

---

## Provenance and Metadata Considerations

The municipality material also introduced operational metadata and provenance concerns.

Examples included:
- management zones,
- contracts,
- maintenance responsibility,
- warranty information,
- useful life,
- installation records,
- and operational ownership.

The walkthrough identified that:
- operational meaning cannot be reliably preserved without provenance and metadata awareness.

This later influenced:
- interoperability abstraction thinking,
- Smart Data Object considerations,
- and Digital Twin trustworthiness analysis.

---

## Teleoperation and Operational Reliability

The municipality material also described concerns related to:
- teleoperation,
- latency,
- packet loss,
- and fallback operational behavior.

This demonstrated that interoperability concerns extend beyond:
- static semantic models,
- or isolated device measurements.

Operational reliability itself became an important interoperability concern.

The walkthrough therefore identified:
- operational responsiveness,
- fallback operation,
- and network reliability
as important parts of interoperability thinking.

---

# Information Exchange Requirements

The walkthrough progressively identified several interoperability-oriented information exchange requirements.

| Requirement Area | Required Information |
|---|---|
| Measurement value | Lux, lumens, watts, voltage, frequency, active/reactive power |
| Measurement time | Start or end timestamp clarity |
| Measurement scope | Individual luminaire, cabinet, line segment, group |
| Measurement quality | Precision, min/max range, temporal resolution |
| Measurement method | Direct, inferred, proxy, aggregated |
| Operational context | Weather, forecast, humidity, fog, temperature |
| Physical context | Orientation, inclination, vegetation, shadowing |
| Asset context | Management zone, contracts, warranty, useful life |
| Control context | Cabinet control, line actuation, fallback behavior |
| Network context | Latency, packet loss, teleoperation capability |

One of the strongest conclusions from this section was:

> Interoperability requires significantly more than telemetry exchange.

Reliable interoperability also requires:
- contextual interpretation,
- provenance awareness,
- operational semantics,
- and trustworthiness preservation.

---

# Stage 2 — Reusable Abstractions Emergence

As the operational analysis progressed, several reusable interoperability abstractions began to emerge.

These abstractions did not originate from:
- predefined standards,
- schemas,
- or implementation architectures.

Instead, they emerged progressively from the municipality operational analysis itself.

| Candidate Reusable Abstraction | Description |
|---|---|
| `MeasuredServiceOutcome` | Actual public-service result, such as lux on a street surface |
| `DeviceOutput` | What the luminaire emits, such as lumens |
| `EnergyConsumption` | Watts consumed, active/reactive power, voltage, frequency |
| `MeasurementPoint` | Luminaire, cabinet, line head, street surface |
| `MeasurementScope` | Single asset, line, zone, group, managed area |
| `MeasurementMethod` | Direct, inferred, proxy, aggregated |
| `TemporalResolution` | Time interval and aggregation policy |
| `OperationalContext` | Weather, fog, humidity, temperature |
| `PhysicalContext` | Orientation, vegetation, obstructions, nearby buildings |
| `AssetResponsibilityContext` | Contracts, management zones, maintenance ownership |
| `NetworkOperabilityContext` | Latency, packet loss, teleoperation reliability |
| `FallbackBehavior` | Local operation independent from intelligent control |

The walkthrough also progressively identified that many of these abstractions may later apply across multiple municipality domains, including:
- water management,
- environmental monitoring,
- waste management,
- transportation,
- and energy optimization.

This reinforced the importance of:
- reusable interoperability thinking,
- semantic consistency,
- and contextual preservation.

---

# Candidate Profile Concepts

As reusable abstractions emerged, several candidate profile concepts also became visible.

These were not treated as finalized standards profiles, but as:
- emerging interoperability realization ideas.

Examples included:

| Candidate Profile Concept | Focus Area |
|---|---|
| Public Lighting Service Outcome Profile | Lux, street-surface context, obstruction, environmental conditions |
| Public Lighting Energy Efficiency Profile | Watts, voltage, frequency, cabinet aggregation |
| Public Lighting Asset Context Profile | Asset identity, management zone, contracts, warranty |
| Public Lighting Teleoperation Readiness Profile | Latency, packet loss, operational responsiveness |
| Measurement Provenance & Quality Profile | Precision, aggregation, inference, temporal resolution |

The walkthrough demonstrated how:
- municipality operational analysis
can progressively evolve into:
- reusable interoperability profile thinking.

---

# Interoperability Validation Scenarios

The walkthrough also identified several candidate interoperability validation scenarios.

These scenarios intentionally remained:
- operational,
- ecosystem-neutral,
- and non-technology-specific.

| Scenario | Validation Intent |
|---|---|
| Luminaire reports lux and watts | Confirm service outcome and energy consumption remain semantically distinguishable |
| Cabinet reports power for a line | Confirm aggregation scope and represented luminaires remain explicit |
| Platform receives lumens but not lux | Confirm infrastructure output is not misinterpreted as service outcome |
| Historical data aggregated hourly | Confirm temporal resolution and aggregation policy remain preserved |
| Tree obstruction affects lighting | Confirm physical context metadata explains reduced lux |
| Teleoperation command issued | Confirm latency and response behavior can be characterized |
| Location comes from installation record | Confirm provenance and metadata origin remain identifiable |

This became one of the strongest practical outputs of the walkthrough:
- interoperability validation must preserve operational meaning and semantic reliability.

---

# Stage 3 — Ecosystem and Interoperability Thinking

Once the operational meaning and reusable abstractions became clearer, the walkthrough progressively evolved toward ecosystem realization thinking.

At this stage, the walkthrough did not attempt to impose:
- a single standards model,
- or a fixed technical architecture.

Instead, the walkthrough explored how different ecosystem participants may contribute interoperable realization mechanisms.

---

## OMA and Device Interoperability

The walkthrough identified that organizations such as OMA may contribute:
- device interoperability models,
- telemetry interoperability assets,
- and LwM2M object structures.

These contributions may help preserve:
- device interoperability consistency,
- operational telemetry semantics,
- and interoperability alignment.

---

## Smart Data Objects as Semantic Integration Mechanisms

The walkthrough progressively identified that Smart Data Objects may act as semantic integration mechanisms capable of carrying:
- operational meaning,
- contextual metadata,
- provenance,
- interoperability abstractions,
- and semantic consistency.

One of the strongest conclusions from the walkthrough became:

> Smart Data Objects are not merely technical schemas.
>
> They are semantic interoperability carriers.

---

## Digital Twin Consumption Perspective

The walkthrough repeatedly demonstrated that:
- trustworthy Digital Twins require semantically reliable interoperability.

The municipality operational material consistently reinforced that:
- raw telemetry alone is insufficient,
- context matters,
- provenance matters,
- and operational meaning must remain preserved.

The walkthrough therefore progressively evolved toward the following operational semantic translation model:

```text
Operational Meaning
        ↓
Reusable Interoperability Abstractions
        ↓
Semantic & Contextual Enrichment
        ↓
Smart Data Objects & Ecosystem Realization
        ↓
Digital Twin Consumption
