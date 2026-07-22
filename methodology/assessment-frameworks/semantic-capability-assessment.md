---
title: Semantic Capability Assessment Framework for Digital Twin Interoperability
description: >
  A technology-neutral assessment framework for evaluating whether
  interoperability standards, Smart Data Models, and Digital Twin
  ecosystems preserve the semantic capabilities required to support
  municipality operational objectives.
layout: doc
---

# {{ $doc.title }}

## Introduction

The Smart Cities SIG methodology identifies municipality operational needs before considering standards, semantic models, or implementation technologies.

This document adopts a reference-architecture approach consistent with the viewpoint-and-view structure defined in Clause 6 of ISO/IEC 30141:2024.



During Stage 1, municipality operational material is analyzed to understand the operational objectives, constraints, and information required to successfully operate a municipal service.

During Stage 2, these operational observations are progressively generalized into reusable semantic capabilities that can be applied across multiple municipal domains.

This document builds directly upon those semantic capabilities.

Its purpose is **not** to define new interoperability standards, Smart Data Models, Digital Twin architectures, or implementation approaches.

Instead, it provides a common engineering framework that allows standards organizations, Smart Data Model communities, Digital Twin initiatives, and other ecosystem participants to evaluate whether their existing specifications preserve the semantic capabilities required to support municipality operational objectives.

The framework intentionally remains technology-neutral.

Each participating ecosystem remains responsible for deciding how these capabilities should be represented within its own architecture and specifications.

---

# Purpose

Municipalities operate services.

Standards represent devices.

Smart Data Models organize semantic information.

Digital Twins consume information to support monitoring, analytics, simulation, and operational decision-making.

These communities often work independently, despite ultimately supporting the same municipality services.

The purpose of this framework is to establish a common semantic reference that enables these communities to evaluate interoperability from the municipality perspective rather than from the perspective of individual technologies.

Instead of asking:

> *How should this information be represented?*

this framework first asks:

> *What semantic capability is required for a Digital Twin to answer municipality operational questions?*

Only after those capabilities have been identified should implementation approaches be evaluated.

---

# Scope

This framework may be applied to any municipality service, including:

- Public Lighting
- Water Distribution
- Irrigation
- Waste Management
- Environmental Monitoring
- Transportation
- Parking
- Public Safety
- Future Smart Cities SIG profiles

The semantic capabilities defined in this document are intentionally reusable across domains.

Only the municipality operational questions change from one service to another.

---

# Relationship to the Smart Cities SIG Methodology

This framework builds directly upon the Smart Cities SIG methodology.

```text
Municipality Operational Reality
                │
                ▼
Stage 1
Operational Meaning
                │
                ▼
Stage 2
Reusable Semantic Capabilities
                │
                ▼
Semantic Capability Assessment Framework
                │
                ▼
Standards & Ecosystem Assessment
                │
        ┌───────┴────────┐
        ▼                ▼
     OMA LwM2M     Smart Data Models
        │                │
        └───────┬────────┘
                ▼
      Digital Twin Interoperability
```

The framework therefore acts as the bridge between semantic analysis and ecosystem realization.

---

# How to Use this Framework

Each semantic capability is evaluated from four complementary perspectives.

## 1. Municipality Operational Questions

Identify the operational questions municipalities expect Digital Twins to answer.

These questions provide the operational justification for the semantic capability.

## 2. Questions for OMA

Evaluate whether existing OMA LwM2M Objects and Resources can represent the required semantic capability.

The objective is not to redesign existing Objects, but to understand whether the capability is already supported or whether additional discussion may be required.

## 3. Questions for Smart Data Models

Evaluate whether existing Smart Data Models can preserve the semantic capability while remaining interoperable across municipalities and Digital Twin platforms.

## 4. Digital Twin Questions

Evaluate whether a Digital Twin consuming the available information can successfully answer the municipality operational questions.

If not, identify which semantic information is missing and which ecosystem may be best positioned to provide it.

---

# Semantic Capability Assessment Framework

The semantic capabilities are organized into four categories.

**1. Domain Semantics**

Domain Semantics aligns primarily with the Business and Usage viewpoints of ISO/IEC 30141, as these viewpoints describe the intended service outcomes, stakeholder needs, and the interaction between IoT systems and the physical entities supporting municipal services.

Describes **what the municipality ultimately cares about** by defining the service being delivered, the infrastructure providing it, and the resources consumed to achieve the desired outcome.

- **Service Outcome** — Defines the real-world outcome the municipality intends to achieve.
- **Infrastructure Output** — Describes the physical behavior and outputs produced by infrastructure assets.
- **Resource Consumption** — Represents the resources consumed to deliver the municipal service.

**2. Observation Semantics**

Observation Semantics aligns mainly with the Foundational IoT and Functional viewpoints, since ISO/IEC 30141 treats sensing, connectivity, data handling, and the abstract functions of IoT systems as core architectural concerns.

Describes **how operational information is observed** by defining where observations originate, what they represent, how they are obtained, and their temporal characteristics.

- **Observation Point** — Identifies where an observation originates.
- **Observation Scope** — Defines the assets or area represented by an observation.
- **Observation Method** — Specifies how an observation was produced.
- **Temporal Semantics** — Describes the time basis associated with an observation.

**3. Interpretation Semantics**

Interpretation Semantics aligns primarily with the Trustworthiness viewpoint of ISO/IEC 30141, as it provides the context, provenance, quality, and descriptive information required for the consistent interpretation of observations across heterogeneous IoT systems.

Describes **how observations should be understood and trusted** by providing the context, provenance, and quality required for meaningful operational interpretation.

- **Provenance** — Identifies the origin of operational information.
- **Measurement Quality** — Describes the reliability and uncertainty of observations.
- **Operational Context** — Represents operating conditions that influence service behavior.
- **Physical Context** — Describes environmental characteristics that affect service outcomes.

**4. Operational Semantics**

Operational Semantics aligns primarily with the Functional and Construction viewpoints of ISO/IEC 30141, as these viewpoints describe how IoT capabilities are organized, implemented, and operated to support real-world municipal services.

Describes **how municipal infrastructure is operated and managed** throughout its lifecycle, including operational responsibility, communications, and resilience.

- **Asset Management Context** — Represents lifecycle and operational management information for assets.
- **Network Operability** — Describes communication conditions affecting remote operation.
- **Fallback Behaviour** — Defines how infrastructure behaves when normal communications or supervisory control are unavailable.

Each semantic capability follows the same structure to facilitate consistent evaluation across ecosystems.

---

# Domain Semantics

Domain semantics describe **what municipalities ultimately care about**.

They distinguish the operational service being delivered from the behaviour of the infrastructure providing that service.

---

## 1. Service Outcome


Governed by: Foundational IoT viewpoint (6.2), Business viewpoint (6.3), Usage viewpoint (6.4), Functional viewpoint (6.5), Trustworthiness viewpoint (6.6).

Model kind: Municipality service semantics – domain outcome model.

Purpose: Describe what service the municipality intends to deliver (lighting, water, irrigation, etc.), independently of how the underlying IoT infrastructure behaves, and how this outcome is evaluated, represented and trusted in an IoT-based architecture.


### Municipality Operational Questions

#### Public Lighting

- Is this street adequately illuminated for pedestrians and vehicles?
- Are lighting levels compliant with the applicable municipality policies or lighting standards?
- Which streets or public spaces are currently under-illuminated or over-illuminated?
- Has the municipality's public lighting service objective been achieved?

#### Water Management & Irrigation

- Is the required amount of water reaching the intended location?
- Are plants, trees, or landscaped areas receiving sufficient irrigation?
- Are consumers receiving the required water pressure and level of service?
- Which areas are currently under-watered, over-watered, or experiencing inadequate service?
- Has the municipality's water service objective been achieved?

### Description

Represents the actual outcome experienced by people, infrastructure, or the environment.

The Service Outcome represents **what the municipality is trying to achieve**, independently of how the underlying infrastructure operates.

Examples include:

- Street illuminance measured at road surface level.
- Soil moisture available at root level.
- Water pressure delivered to consumers.

### Why It Is Required

Digital Twins must determine whether municipality objectives are being achieved.

Infrastructure telemetry alone cannot determine service success.

The distinction between infrastructure behaviour and service outcome is therefore fundamental for trustworthy interoperability.

### Questions for OMA

- Which existing LwM2M Objects and Resources represent the service outcome?
- How is the distinction maintained between service outcome and infrastructure output?
- How are measured, estimated, inferred, predicted, or aggregated service outcomes represented?
- How is the observation location represented?
- Which additional capabilities, if any, would improve representation of municipality service outcomes?

### Questions for Smart Data Models

- Which existing entities and properties represent the service outcome?
- How is the distinction maintained between service outcome and infrastructure behaviour?
- How are provenance and quality information associated with the service outcome?
- How can Digital Twins discover service outcomes consistently across municipalities?
- Which extensions, if any, would improve semantic interoperability?

### Digital Twin Questions

- Can the Digital Twin determine whether the municipality service objective has been achieved?
- Can the Digital Twin distinguish poor service outcomes from normal infrastructure operation?
- Can service outcomes from different municipalities be meaningfully compared?
- Which semantic information is required to support reliable simulations and operational decision-making?

---

## 2. Infrastructure Output

Governed by: Foundational IoT viewpoint (6.2), Functional viewpoint (6.5), Trustworthiness viewpoint (6.6), Construction viewpoint (6.7).

View purpose and model kind
Model kind: Municipality service semantics – infrastructure behaviour model.

Purpose: Describe how the IoT infrastructure behaves (physical outputs) when providing a municipal service, distinguishing it from the service outcome and relating it to components and construction patterns.


### Municipality Operational Questions

#### Public Lighting

- How much light is each luminaire producing?
- Is each luminaire operating according to its configured settings?
- Has the light output degraded over time?
- Is poor street illumination caused by reduced luminaire output or by environmental conditions?

#### Water Management & Irrigation

- How much water is being delivered by each pump or valve?
- Are pumps, valves, and irrigation controllers operating as expected?
- Is reduced water delivery caused by infrastructure behaviour or by downstream conditions?
- Are assets performing within their expected operating ranges?

### Description

Represents the physical output produced by infrastructure assets while delivering a municipality service.

Infrastructure Output describes **how the infrastructure behaves**, not whether the municipality objective has been achieved.

Examples include:

- Lumens emitted by a luminaire.
- Pump flow rate.
- Valve opening percentage.
- Motor speed.

### Why It Is Required

Municipality service outcomes and infrastructure behaviour represent different operational concepts.

Maintaining this distinction enables Digital Twins to diagnose operational issues, optimize infrastructure performance, and avoid incorrectly interpreting infrastructure telemetry as evidence of successful service delivery.

### Questions for OMA

- Which existing LwM2M Objects and Resources represent infrastructure output?
- How are operating states represented?
- How are output measurements associated with the corresponding assets?
- Which additional capabilities, if any, would improve representation of infrastructure behaviour?

### Questions for Smart Data Models

- Which entities and properties represent infrastructure output?
- How is infrastructure behaviour kept separate from service outcomes?
- Can multiple infrastructure outputs be represented consistently for complex assets?
- Which semantic enhancements would improve interoperability?

### Digital Twin Questions

- Can the Digital Twin distinguish infrastructure behaviour from municipality service outcomes?
- Can infrastructure degradation be identified before service quality is affected?
- Can infrastructure performance be analysed independently from environmental influences?

---

## 3. Resource Consumption

Governed by: Business viewpoint (6.3), Functional viewpoint (6.5), Trustworthiness viewpoint (6.6), Construction viewpoint (6.7).

View purpose and model kind
Model kind: Municipality service semantics – resource efficiency model.

Purpose: Describe the resources consumed by the IoT system to achieve a service outcome (energy, water, etc.) and how this relates to efficiency, cost, and solution design.

### Municipality Operational Questions

#### Public Lighting

- How much energy is required to provide the public lighting service?
- Which luminaires, cabinets, streets, or zones consume the most energy?
- Can energy consumption be reduced without reducing lighting quality?
- Are energy savings actually preserving the required service outcome?

#### Water Management & Irrigation

- How much water, energy, or other resources are consumed to deliver the service?
- Which pumps, valves, zones, or irrigation areas consume the most resources?
- Can water or energy consumption be reduced without degrading the service outcome?
- Are efficiency improvements causing under-watering, pressure loss, or reduced service quality?

### Description

Represents the resources consumed while delivering the municipality service.

Examples include:

- Energy
- Water
- Fuel
- Battery usage
- Active power
- Reactive power
- Voltage
- Frequency

### Why It Is Required

Operational efficiency requires separating service quality from resource consumption.

A municipality needs to understand not only whether the service outcome was achieved, but also the resources required to achieve it.

### Questions for OMA

- Which existing LwM2M Objects and Resources represent resource consumption?
- Can energy, water, fuel, or battery usage be represented consistently?
- Are electrical measurements sufficiently complete for operational efficiency analysis?
- Can resource consumption be associated with the asset, group, cabinet, zone, or service outcome it supports?
- Which additional capabilities would improve resource consumption representation?

### Questions for Smart Data Models

- Which entities and properties represent resource consumption?
- Can resource consumption remain independent from service outcome and infrastructure output?
- Can consumption be aggregated consistently across assets, zones, and time periods?
- Can resource consumption be associated with the service outcome it supports?
- Which semantic enhancements would improve interoperability?

### Digital Twin Questions

- Can the Digital Twin determine how much resource consumption was required to achieve the service outcome?
- Can the Digital Twin compare service quality against resource consumption?
- Can the Digital Twin identify inefficient assets, zones, or operating conditions?
- Can the Digital Twin optimize resource consumption while preserving service quality?

---

# Observation Semantics

Observation semantics describe **how observations are obtained, interpreted, and compared**.

Municipality services rarely depend on isolated measurements.

Instead, operational decisions require understanding:

- where an observation was made,
- what portion of the system it represents,
- how it was obtained,
- and over what period it applies.

Without these semantic capabilities, observations that appear identical may represent fundamentally different operational realities.

---

## 4. Observation Point

Governed by: Foundational IoT viewpoint (6.2), Usage viewpoint (6.4), Functional viewpoint (6.5), Trustworthiness viewpoint (6.6).

View purpose and model kind
Model kind: Observation semantics – location-of-observation model.

Purpose: Describe where the observations originate within the IoT system and the municipal environment (sensor, street surface, root, etc.) and how this affects their use and interpretation.



### Municipality Operational Questions

#### Public Lighting

- Where was this measurement taken?
- Was the observation made at the luminaire, cabinet, line head, or street surface?
- Can measurements taken at different observation points be safely compared?
- Does this observation represent what citizens experience or what the infrastructure reports?

#### Water Management & Irrigation

- Where was this measurement taken?
- Was the observation collected at the pump, valve, pipeline, irrigation controller, or root zone?
- Does the observation represent the infrastructure or the delivered service?
- Can measurements collected at different points in the network be compared?

### Description

Represents the physical or logical location where an observation originates.

The Observation Point identifies **where the information was obtained**, independently of the asset being monitored.

Examples include:

- Luminaire
- Cabinet
- Line head
- Street surface
- Pump
- Valve
- Pipeline
- Root zone
- Weather station

### Why It Is Required

Measurements originating from different observation points often represent different operational meanings.

A Digital Twin must understand where an observation was collected before comparing it with other observations or using it for simulation.

### Questions for OMA

- Which existing Objects identify the observation point?
- Can observation points be represented independently from asset identity?
- Can multiple observation points be associated with the same infrastructure asset?
- Which additional capabilities would improve observation point representation?

### Questions for Smart Data Models

- Which entities or properties identify the observation point?
- Can observation points remain explicit throughout information exchange?
- Can observation points be associated with Digital Twin entities?
- Which semantic improvements would improve interoperability?

### Digital Twin Questions

- Can the Digital Twin determine where every observation originated?
- Can observations from different points be interpreted correctly?
- Can simulation models distinguish infrastructure measurements from service measurements?

---

## 5. Observation Scope


Governed by: Foundational IoT viewpoint (6.2), Business viewpoint (6.3), Usage viewpoint (6.4), Functional viewpoint (6.5), Trustworthiness viewpoint (6.6).

Model kind: Observation semantics – coverage-of-observation model.

Purpose: Describe which part of the system or municipality each observation covers (asset, group, street, zone, district, entire municipality).


### Municipality Operational Questions

#### Public Lighting

- Does this observation represent one luminaire or an entire street?
- How many luminaires are represented by this value?
- Does this measurement represent an operational zone or the entire municipality?
- Can observations with different coverage be compared?

#### Water Management & Irrigation

- Does this observation represent one irrigation valve or an entire irrigation zone?
- Does this measurement represent one pressure sensor or the entire distribution network?
- What geographical or operational area does this observation represent?
- Can aggregated observations be compared with local measurements?

### Description

Represents the operational area or population represented by an observation.

Observation Scope identifies **what the observation applies to**, rather than where it was collected.

Examples include:

- Single asset
- Group of assets
- Cabinet
- Street
- Irrigation zone
- District
- Entire municipality

### Why It Is Required

Measurements representing different operational scopes should not be compared without understanding their coverage.

Digital Twins require explicit scope information to perform meaningful analytics and simulation.

### Questions for OMA

- Can Objects indicate the operational scope represented by a measurement?
- Can aggregated observations identify the represented assets?
- How is aggregation represented?
- Which additional capabilities would improve scope representation?

### Questions for Smart Data Models

- Can operational scope be represented independently?
- Can aggregation boundaries remain explicit?
- Can Digital Twins discover the represented operational area?
- Which semantic improvements would improve interoperability?

### Digital Twin Questions

- Can the Digital Twin determine what portion of the municipality is represented by each observation?
- Can aggregated observations be compared with individual asset measurements?
- Can operational KPIs be calculated consistently across different observation scopes?

---

## 6. Observation Method

Governed by: Functional viewpoint (6.5), Trustworthiness viewpoint (6.6).

Model kind: Observation semantics – method-of-production model.

Purpose: Describe how each observation (measured, estimated, predicted, simulated, aggregated, proxy) is obtained and its impact on functionality and trustworthiness.


### Municipality Operational Questions

#### Public Lighting

- Was this value directly measured or estimated?
- Was this lighting level calculated from luminaire characteristics?
- Is this observation based on a sensor, a model, or historical data?
- Can this information be trusted for operational decisions?

#### Water Management & Irrigation

- Was soil moisture measured or estimated?
- Was water demand predicted using weather forecasts?
- Is this irrigation recommendation model-generated?
- How was this observation produced?

### Description

Represents the method used to obtain an observation.

Examples include:

- Measured
- Estimated
- Inferred
- Predicted
- Aggregated
- Simulated
- Model-derived
- Proxy measurement

### Why It Is Required

Operational trust depends upon understanding how information was produced.

Different observation methods imply different levels of confidence and different operational uses.

### Questions for OMA

- How are different observation methods represented?
- Can measured values be distinguished from inferred values?
- Can prediction or simulation results be represented?
- Which additional capabilities would improve observation method representation?

### Questions for Smart Data Models

- Can observation methods accompany every observation?
- Can Digital Twins distinguish measured information from model-derived information?
- Can provenance remain associated with observation methods?
- Which semantic improvements would improve interoperability?

### Digital Twin Questions

- Can the Digital Twin distinguish measured observations from estimated or predicted values?
- Can simulations account for different observation methods?
- Can confidence in operational decisions be adjusted according to observation method?

---

## 7. Temporal Semantics

Governed by: Business viewpoint (6.3), Functional viewpoint (6.5), Trustworthiness viewpoint (6.6).

Model kind: Observation semantics – time-basis model.

Purpose: Describe the temporal characteristics of observations (point in time, interval, aggregation window, historical data, forecast) and their use in KPIs and simulation.


### Municipality Operational Questions

#### Public Lighting

- Does this observation represent the current situation or an historical average?
- What period of time does this observation cover?
- Were these measurements aggregated?
- Can observations collected at different times be compared?

#### Water Management & Irrigation

- Does this soil moisture value represent current conditions or a daily average?
- Does this irrigation recommendation apply now or tomorrow?
- What observation interval was used?
- Can historical observations be compared with forecast information?

### Description

Represents the temporal characteristics of an observation.

Examples include:

- Instantaneous
- Observation interval
- Sampling period
- Aggregation window
- Historical observation
- Forecast
- Prediction horizon

### Why It Is Required

Operational interpretation depends heavily upon time semantics.

Observations representing different temporal characteristics should not be compared without understanding their time basis.

### Questions for OMA

- Which temporal characteristics are currently represented?
- Can observation intervals remain explicit?
- Can aggregation periods be represented?
- Which additional capabilities would improve temporal semantics?

### Questions for Smart Data Models

- Can temporal semantics remain explicit?
- Can forecast and historical observations be represented consistently?
- Can aggregation windows be preserved?
- Which semantic improvements would improve interoperability?

### Digital Twin Questions

- Can the Digital Twin correctly interpret the time basis of every observation?
- Can historical, current, and predicted observations coexist?
- Can simulations correctly use observations with different temporal characteristics?

---

# Interpretation Semantics

Interpretation semantics describe the additional information required to correctly understand, compare, and trust observations.

Measurements alone rarely provide sufficient information for operational decision-making.

To become operationally meaningful, observations must be accompanied by information describing:

- where the information originated,
- how trustworthy it is,
- under which operating conditions it was obtained,
- and which physical conditions influenced the observed result.

These semantic capabilities enable Digital Twins to interpret observations consistently across municipalities, infrastructure vendors, and interoperability ecosystems.

---

## 8. Provenance

Governed by: Functional viewpoint (6.5), Trustworthiness viewpoint (6.6).

Model kind: Interpretation semantics – source-of-information model.

Purpose: Describe the source of observations and operational information (device, control room, external service, human operator, twin, predictive model).



### Municipality Operational Questions

#### Public Lighting

- Where did this information originate?
- Was this observation generated by the luminaire, the control cabinet, an external platform, or manually entered?
- Can the source of this information be trusted?
- Can different information sources be distinguished?

#### Water Management & Irrigation

- Was this observation generated by a sensor, a supervisory system, a weather service, or an irrigation controller?
- Can the origin of irrigation recommendations be identified?
- Can externally supplied information be distinguished from locally measured observations?
- Which organization or system is responsible for this information?

### Description

Represents the origin of an observation or piece of operational information.

Examples include:

- Device sensor
- Control cabinet
- Weather service
- GIS platform
- Installation records
- Asset management system
- Human operator
- Digital Twin
- Predictive model

### Why It Is Required

Operational decisions depend upon understanding where information originated.

Observations with different provenance may have different levels of trust, authority, and operational applicability.

### Questions for OMA

- Which existing Objects and Resources identify the origin of observations?
- Can device-generated information be distinguished from externally supplied information?
- Can provenance remain associated with observations throughout their lifecycle?
- Which additional capabilities would improve provenance representation?

### Questions for Smart Data Models

- Which entities and properties represent provenance?
- Can provenance remain associated with observations during information exchange?
- Can Digital Twins discover provenance consistently?
- Which semantic enhancements would improve interoperability?

### Digital Twin Questions

- Can the Digital Twin determine where every observation originated?
- Can observations be filtered according to their provenance?
- Can operational decisions consider the trustworthiness of different information sources?

---

## 9. Measurement Quality

Governed by: Trustworthiness viewpoint (6.6), Functional viewpoint (6.5).

Model kind: Interpretation semantics – quality-of-observation model.

Purpose: represent accuracy, precision, reliability, completeness, uncertainty, etc., by linking them to functions and reliability.


### Municipality Operational Questions

#### Public Lighting

- How reliable is this observation?
- Can this value be trusted for operational decisions?
- Is the data complete and sufficiently accurate?
- Can observations with different quality levels be compared?

#### Water Management & Irrigation

- Is this soil moisture observation sufficiently accurate?
- Is the irrigation recommendation based on reliable information?
- Are there missing or incomplete observations?
- Can operational decisions account for varying levels of confidence?

### Description

Represents the quality characteristics associated with an observation.

Examples include:

- Accuracy
- Precision
- Confidence
- Completeness
- Consistency
- Availability
- Resolution
- Uncertainty

### Why It Is Required

Digital Twins require information about observation quality to support reliable monitoring, analytics, simulation, and operational decision-making.

### Questions for OMA

- Which quality characteristics can accompany observations?
- Can confidence or uncertainty be represented?
- Can incomplete observations be identified?
- Which additional capabilities would improve quality representation?

### Questions for Smart Data Models

- Which entities and properties represent measurement quality?
- Can quality information remain associated with observations?
- Can Digital Twins evaluate observation quality consistently?
- Which semantic enhancements would improve interoperability?

### Digital Twin Questions

- Can the Digital Twin evaluate the quality of every observation?
- Can operational decisions consider different confidence levels?
- Can simulations account for observation uncertainty?

---

## 10. Operational Context

Governed by: Business viewpoint (6.3), Usage viewpoint (6.4), Functional viewpoint (6.5), Trustworthiness viewpoint (6.6).

Model kind: Interpretation semantics – operational-conditions model.

Purpose: Describe operating conditions (weather, traffic, occupancy, seasonality) that affect service and observations.




### Municipality Operational Questions

#### Public Lighting

- Are weather conditions affecting the lighting service?
- Is poor illumination caused by fog, rain, humidity, or other operational conditions?
- Should lighting behaviour change because operating conditions have changed?
- Are current operating conditions significantly different from normal conditions?

#### Water Management & Irrigation

- Has recent rainfall reduced irrigation requirements?
- Should irrigation schedules change because of weather forecasts?
- Are current environmental conditions affecting water demand?
- Are operational conditions influencing service performance?

### Description

Represents operational conditions that influence the interpretation of observations.

Examples include:

- Weather
- Rainfall
- Humidity
- Temperature
- Wind
- Traffic
- Occupancy
- Seasonal conditions

### Why It Is Required

The same infrastructure behaviour may produce different service outcomes under different operating conditions.

Operational context enables Digital Twins to correctly interpret those differences.

### Questions for OMA

- Which operational context can be directly observed?
- Can external operational context be associated with observations?
- Which additional capabilities would improve operational context representation?

### Questions for Smart Data Models

- Which entities and properties represent operational context?
- Can operational context remain independent from device telemetry?
- Can contextual information remain associated with observations?
- Which semantic enhancements would improve interoperability?

### Digital Twin Questions

- Can the Digital Twin interpret observations according to current operating conditions?
- Can simulations incorporate operational context?
- Can operational decisions automatically adapt to changing conditions?

---

## 11. Physical Context

Governed by: Foundational IoT viewpoint (6.2), Usage viewpoint (6.4), Functional viewpoint (6.5), Trustworthiness viewpoint (6.6).

Model kind: Interpretation semantics – physical-environment model.

Purpose:  Describe the physical environment (buildings, trees, terrain, orientation, shadows) and its impact on service outcomes.



### Municipality Operational Questions

#### Public Lighting

- Are trees, buildings, or other obstructions reducing street illumination?
- Is the physical environment affecting the lighting service?
- Would the same luminaire produce different results in another location?
- Are shadows or terrain affecting the observed lighting levels?

#### Water Management & Irrigation

- Are soil characteristics affecting irrigation effectiveness?
- Is terrain influencing water distribution?
- Are vegetation, slopes, or physical obstacles affecting water delivery?
- Would identical infrastructure produce different results in another location?

### Description

Represents physical characteristics of the environment that influence service outcomes.

Examples include:

- Buildings
- Trees
- Vegetation
- Terrain
- Slopes
- Orientation
- Inclination
- Shadows
- Surface materials

### Why It Is Required

Physical context explains why identical infrastructure behaviour may produce different operational outcomes.

Without physical context, observations may be interpreted incorrectly.

### Questions for OMA

- Which physical context can be directly represented?
- Should physical context be supplied by external systems?
- Which additional capabilities would improve physical context representation?

### Questions for Smart Data Models

- Which entities and properties represent physical context?
- Can physical context remain associated with observations?
- Can Digital Twins consistently discover environmental influences?
- Which semantic enhancements would improve interoperability?

### Digital Twin Questions

- Can the Digital Twin understand how the physical environment influences service outcomes?
- Can simulations include physical environmental effects?
- Can operational decisions distinguish infrastructure problems from environmental influences?

---

# Operational Semantics

Operational semantics describe the operational information required to safely, reliably, and efficiently manage municipal infrastructure throughout its lifecycle.

While Domain, Observation, and Interpretation Semantics explain **what is being observed** and **how observations should be interpreted**, Operational Semantics provide the information required to operate, maintain, and control infrastructure assets.

These semantic capabilities enable Digital Twins to support operational planning, maintenance, resilience, remote operation, and lifecycle management.

---

## 12. Asset Management Context

Governed by: Business viewpoint (6.3), Functional viewpoint (6.5), Trustworthiness viewpoint (6.6), Construction viewpoint (6.7).

Model kind: Operational semantics – asset-lifecycle model.

Purpose: represent ownership, responsible management, contracts, warranties, maintenance history, useful life, life cycle, etc.



### Municipality Operational Questions

#### Public Lighting

- Who owns this lighting asset?
- Which organization is responsible for maintaining it?
- Which operational zone manages this asset?
- Is the luminaire still under warranty?
- Which maintenance contract applies?
- What is the expected remaining useful life?
- When was this asset last maintained or replaced?

#### Water Management & Irrigation

- Who owns this pump, valve, or irrigation controller?
- Which organization is responsible for maintaining it?
- Which irrigation zone or water district manages this asset?
- Is the equipment still under warranty?
- Which maintenance contract applies?
- What is the expected remaining useful life?
- When was this asset last inspected or serviced?

### Description

Represents operational management information associated with infrastructure assets throughout their lifecycle.

Examples include:

- Ownership
- Responsible organization
- Operational zone
- Maintenance responsibility
- Contracts
- Warranty
- Lifecycle stage
- Installation date
- Maintenance history
- Remaining useful life

### Why It Is Required

Municipal infrastructure is managed throughout its operational lifecycle.

Digital Twins require operational management information to support maintenance planning, asset optimization, lifecycle analysis, and accountability.

### Questions for OMA

- Which existing Objects and Resources represent asset management information?
- Which management information belongs within LwM2M Objects?
- Which information should remain external to device models?
- Can external asset management information remain associated with device observations?
- Which additional capabilities would improve asset management representation?

### Questions for Smart Data Models

- Which entities and properties represent asset management information?
- Can lifecycle information remain associated with assets?
- Can maintenance and ownership information be represented consistently?
- Which semantic enhancements would improve interoperability?

### Digital Twin Questions

- Can the Digital Twin determine who is responsible for every asset?
- Can maintenance history and lifecycle information be incorporated into operational decisions?
- Can asset replacement, maintenance, and investment planning be supported?

---

## 13. Network Operability

Governed by: Functional viewpoint (6.5), Trustworthiness viewpoint (6.6), Construction viewpoint (6.7).

Model kind: Operational semantics – communication-conditions model.

Purpose: Describe network availability, connectivity, latency, packet loss, signal quality, and communication reliability, as outlined in Annex C (network connectivity, network management, and operation).


### Municipality Operational Questions

#### Public Lighting

- Can this lighting asset currently be remotely controlled?
- Is network performance affecting teleoperation?
- Are communication failures preventing reliable operation?
- Can communication problems be distinguished from equipment failures?

#### Water Management & Irrigation

- Can pumps, valves, or irrigation controllers currently be remotely operated?
- Is communication reliability affecting operational control?
- Can communication failures delay irrigation or water management operations?
- Can network issues be distinguished from infrastructure failures?

### Description

Represents the communication characteristics that influence remote monitoring and control.

Examples include:

- Network availability
- Connectivity status
- Latency
- Packet loss
- Signal quality
- Communication reliability
- Communication technology

### Why It Is Required

Operational decisions increasingly depend upon reliable communication.

Digital Twins require awareness of communication conditions to correctly interpret observations and determine whether remote operation is feasible.

### Questions for OMA

- Which existing Objects and Resources represent communication characteristics?
- Can communication quality be monitored?
- Can communication failures be distinguished from device failures?
- Which additional capabilities would improve representation of network operability?

### Questions for Smart Data Models

- Which entities and properties represent communication characteristics?
- Can communication information remain associated with infrastructure assets?
- Can Digital Twins evaluate operational readiness using communication information?
- Which semantic enhancements would improve interoperability?

### Digital Twin Questions

- Can the Digital Twin determine whether assets are currently reachable?
- Can communication failures be distinguished from infrastructure failures?
- Can operational decisions account for communication limitations?

---

## 14. Fallback Behaviour

Governed by: Business viewpoint (6.3), Functional viewpoint (6.5), Trustworthiness viewpoint (6.6), Construction viewpoint (6.7).

Model kind: Operational semantics – resilience and autonomous behaviour model.

Purpose: Describe autonomous behavior in the event of a loss of communication or unexpected conditions (local schedules, autonomous control, safe modes, emergency, manual override).


### Municipality Operational Questions

#### Public Lighting

- What happens if communication with the lighting infrastructure is lost?
- Will the lighting continue operating safely?
- Does the infrastructure automatically switch to a predefined operating schedule?
- Can emergency operating modes be identified?

#### Water Management & Irrigation

- What happens if communication with irrigation controllers or pumps is lost?
- Will irrigation continue safely?
- Does the infrastructure automatically switch to local control?
- Can emergency or safe operating modes be identified?

### Description

Represents the autonomous behaviour of infrastructure when normal communications or supervisory control become unavailable.

Examples include:

- Local schedules
- Autonomous control
- Safe operating mode
- Emergency operating mode
- Manual override
- Local decision making

### Why It Is Required

Municipal infrastructure must continue operating safely during communication failures or unexpected operational conditions.

Digital Twins require knowledge of fallback behaviour to correctly simulate infrastructure resilience and predict operational outcomes.

### Questions for OMA

- Which existing Objects and Resources represent fallback behaviour?
- Can autonomous operating modes be represented?
- Can transitions between normal and fallback operation be identified?
- Which additional capabilities would improve fallback behaviour representation?

### Questions for Smart Data Models

- Which entities and properties represent fallback behaviour?
- Can autonomous operating strategies remain associated with assets?
- Can Digital Twins discover fallback operating modes consistently?
- Which semantic enhancements would improve interoperability?

### Digital Twin Questions

- Can the Digital Twin predict how infrastructure will behave during communication failures?
- Can simulations incorporate autonomous operating modes?
- Can operational resilience be evaluated before failures occur?
- Can emergency operating scenarios be realistically simulated?

---

# Capability Assessment Matrix

> **Editorial Note**
>
> This matrix is included in this document to illustrate how the Semantic Capability Assessment Framework is intended to be applied.
>
> As the Smart Cities SIG develops domain-specific profiles (for example, Public Lighting, Water Management & Irrigation, Waste Management, and Transportation), this matrix is expected to be moved into separate profile-specific assessment documents.
>
> Each profile will use this common framework to assess the extent to which existing standards, Smart Data Models, and Digital Twin ecosystems support the semantic capabilities identified in this document.
>
> Keeping the assessment separate from the framework will allow each profile to evolve independently while preserving a single, authoritative definition of the semantic capabilities.

The following matrix provides a common assessment worksheet for ecosystem participants.

Each participating ecosystem should evaluate its existing specifications against the semantic capabilities described in this document.

The resulting assessments may be discussed collaboratively within the Smart Cities SIG and used to identify opportunities for improving interoperability across standards, semantic models, and Digital Twin platforms.

| Semantic Capability | OMA Assessment | Smart Data Models Assessment | Digital Twin Assessment | Recommendations |
|---------------------|----------------|------------------------------|-------------------------|-----------------|
| Service Outcome | **Public Lighting**<br />The measurements would need to be complemented with Illuminance value from external sensor<br />3301 - Illuminance | | | |
| Infrastructure Output | **Public Lighting**<br />Dimming Level is the main output value that would be monitored (also color temperature may be provided). Alarms would allow to promptly identify problems<br />3416 - Outdoor Lamp Controller<br />3418 - Electrical Monitor | | | |
| Resource Consumption | **Public Lighting**<br />Electrical Monitor provides a good amount of resources for single lamp consumption, whilst Single Phase and Three Phase Electrical Meters would be used to map Cabinet Controllers<br />3418 - Electrical Monitor<br />3421 - Single-Pahse Electrical Meter<br />3422 - Three-Phase Electrical Meter Complement | | | |
| Observation Point | **Public Lighting**<br />Location object can be used to identify specific observation point<br />6 - Location | | | |
| Observation Scope | **Public Lighting**<br />Intrinsic in the object type (Electrical Monitor vs Single Phase and Three Phase Electrical Meters)<br />3418 - Electrical Monitor<br />3421 - Single-Pahse Electrical Meter<br />3422 - Three-Phase Electrical Meter Complement | | | |
| Observation Method | **Public Lighting**<br />Current Data Model is only limited to measured values, when not explicitly stated | | | |
| Temporal Semantics | **Public Lighting**<br />Each measurement is associated with a timestamp, representing a specific time instant, even when dispatched at a later time Data can be normally provided either periodically or upon meaningful change of any value being monitored<br />5518 - Timestamp | | | |
| Provenance | **Public Lighting**<br />OMA Data Model being implemented by devices only refers to raw infrastructure output.  Externally supplied information may be complemented at higher levels | | | |
| Measurement Quality | **Public Lighting**<br />Measurements include a Quality Indicator (6042) and a  Measurement Quality Level (6049). The device may report only the subset of information that is available <br />6042 - Quality Indicator<br />6049 - Quality Level | | | |
| Operational Context | **Public Lighting**<br />Normally limited to electrical line quality (Voltage, Frequency) OMA Data Model also provides coverage for a bunch of environmental measurements  Rain Gauge, Anemometer, Humidity, Temperature, Traffic, Heat Stroke<br />3418 - Electrical Monitor<br />3303 - Temperature<br />3304 - Humidity<br />3432 - Traffic Counter<br />3446 - Rain Gauge<br />3449 - Anemometer<br />3450 - Wet Bulb Globe Temperature | | | |
| Physical Context | **Public Lighting**<br />This is indeed not well covered by existing Data Model and may be possibly managed at higher levels | | | |
| Asset Management Context | **Public Lighting**<br />Devices may expose certain number of asset context in various objects (Device, Device Extension, Luminaire Asset), but may be complemented with further information being managed at higher levels<br />3 - Device<br />3410 - Device Extensions<br />3417 - Luminaire Asset | | | |
| Network Operability | **Public Lighting**<br />Various objects may provide statistic information and connection status, alongside device failures and alarm reporting<br />4 - Connectivity Monitoring<br />7 - Connectivity Statistics<br />3447 - LPWAN Mesh Connectivity<br />3448 - LPWAN Mesh Statistics | | | |
| Fallback Behaviour | **Public Lighting**<br />Schedule Framework is designed to allow for device autonomous operation, where manual operations can take precedence for a limited amount of time<br />3452 - Program Scheduler<br />3453 - Calendar Rule<br />3454 - Program Function<br />3457 - Program Manager | | | |



---

# Expected Outcome

The completion of this assessment framework should enable ecosystem participants to:

- Identify which semantic capabilities are already supported by existing specifications.
- Identify semantic capabilities requiring additional discussion or future enhancements.
- Improve interoperability between device standards, Smart Data Models, and Digital Twin ecosystems.
- Preserve municipality operational meaning across standards and semantic models.
- Support the development of semantically consistent Digital Twins capable of monitoring, analysing, simulating, and operating municipality services.

This framework is intended to be reusable across multiple municipality domains, including Public Lighting, Water Management & Irrigation, Waste Management, Transportation, Environmental Monitoring, Parking, and future Smart Cities SIG profiles.

---

# Expected Outcome

The completion of this assessment framework should enable ecosystem participants to:

- Identify which semantic capabilities are already supported by existing specifications.
- Identify semantic capabilities that require additional discussion or future enhancements.
- Improve interoperability between device standards, Smart Data Models, and Digital Twin ecosystems.
- Preserve municipality operational meaning across standards and semantic models.
- Support the development of semantically consistent Digital Twins capable of monitoring, analysing, simulating, and operating municipality services.

This framework is intended to be reusable across multiple municipality domains,
including public lighting, water management, irrigation, waste management,
transportation, environmental monitoring, parking, and future Smart Cities SIG
profiles.
