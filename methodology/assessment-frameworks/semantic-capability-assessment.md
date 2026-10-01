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

The Semantic Capability Assessment Framework (SCAF) is the assessment method used in [Stage 3 — Standards & Ecosystem Mapping](/methodology/core-methodology/stage-3-standards-mapping.md).

It asks, for each of the semantic capabilities defined in [Stage 2 — Semantic Capabilities](/methodology/core-methodology/stage-2-semantic-capabilities.md), whether an ecosystem's existing specifications can supply the information a Digital Twin needs to answer municipality operational questions.

This document contains the assessment **questions** only:
- capability definitions live in [Stage 2](/methodology/core-methodology/stage-2-semantic-capabilities.md),
- service-specific municipality operational questions live in each Service Profile,
- and assessment **results** live in the [ecosystem assessment reports](#ecosystem-assessments).

Its purpose is **not** to define new interoperability standards, Smart Data Models, Digital Twin architectures, or implementation approaches. The framework is technology-neutral: each participating ecosystem remains responsible for deciding how the capabilities should be represented within its own architecture and specifications.

For how SCAF fits into the methodology as a whole, see the [Methodology Overview](/methodology/core-methodology/methodology-overview.md).

---

# Purpose

Municipalities operate services.

Standards represent devices.

Smart Data Models organize semantic information.

Digital Twins consume information to support monitoring, analytics, simulation, and operational decision-making.

These communities often work independently, despite ultimately supporting the same municipality services.

The purpose of this framework is to give these communities a common reference for evaluating interoperability from the municipality perspective rather than from the perspective of individual technologies.

Instead of asking:

> *How should this information be represented?*

this framework first asks:

> *What semantic capability is required for a Digital Twin to answer municipality operational questions?*

Only after those capabilities have been identified should implementation approaches be evaluated.

---

# Scope

This framework may be applied to any Service Domain, including:

- Public Lighting
- Water Distribution
- Irrigation
- Waste Management
- Environmental Monitoring
- Transportation
- Parking
- Public Safety
- Future Smart Cities SIG Service Profiles

The semantic capabilities and the assessment questions below are the same for every Service Domain. Only the municipality operational questions change from one service to another, and those are maintained by each Service Profile:

- [Public Lighting — Municipality Operational Questions](/profiles/lighting/municipality-questions.md)
- [Water Management & Irrigation — Municipality Operational Questions](/profiles/water/municipality-questions.md)

---

# How to Use this Framework

Each semantic capability is evaluated from four complementary perspectives.

## 1. Municipality Operational Questions

Identify the operational questions municipalities expect Digital Twins to answer, from the relevant Service Profile.

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

# Ecosystem Assessments

Each ecosystem records its answers to the questions below in its own report. Results are not copied into this framework.

| Ecosystem | Assessment report | Service Domains covered |
|---|---|---|
| OMA LwM2M | [OMA Semantic Capability Assessment](./oma-capability-assessment.md), with the resource-by-resource [OMA LwM2M Registry Capability Classification](./oma-registry-capability-classification.md) | Public Lighting; Water Management & Irrigation |
| Smart Data Models | [Smart Data Models Semantic Capability Assessment](./sdm-capability-assessment.md) | Catalogue-wide |
| Digital Twin | Not yet assessed | — |

---

# 1. Domain Semantics

## 1.1 Service Outcome

**Definition:** [Stage 2 — Service Outcome](/methodology/core-methodology/stage-2-semantic-capabilities.md#service-outcome) · **Municipality questions:** [Public Lighting](/profiles/lighting/municipality-questions.md#service-outcome), [Water Management & Irrigation](/profiles/water/municipality-questions.md#service-outcome)

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

## 1.2 Infrastructure Output

**Definition:** [Stage 2 — Infrastructure Output](/methodology/core-methodology/stage-2-semantic-capabilities.md#infrastructure-output) · **Municipality questions:** [Public Lighting](/profiles/lighting/municipality-questions.md#infrastructure-output), [Water Management & Irrigation](/profiles/water/municipality-questions.md#infrastructure-output)

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

## 1.3 Resource Consumption

**Definition:** [Stage 2 — Resource Consumption](/methodology/core-methodology/stage-2-semantic-capabilities.md#resource-consumption) · **Municipality questions:** [Public Lighting](/profiles/lighting/municipality-questions.md#resource-consumption), [Water Management & Irrigation](/profiles/water/municipality-questions.md#resource-consumption)

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


# 2. Observation Semantics

## 2.1 Observation Point

**Definition:** [Stage 2 — Observation Point](/methodology/core-methodology/stage-2-semantic-capabilities.md#observation-point) · **Municipality questions:** [Public Lighting](/profiles/lighting/municipality-questions.md#observation-point), [Water Management & Irrigation](/profiles/water/municipality-questions.md#observation-point)

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

## 2.2 Observation Scope

**Definition:** [Stage 2 — Observation Scope](/methodology/core-methodology/stage-2-semantic-capabilities.md#observation-scope) · **Municipality questions:** [Public Lighting](/profiles/lighting/municipality-questions.md#observation-scope), [Water Management & Irrigation](/profiles/water/municipality-questions.md#observation-scope)

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

## 2.3 Observation Method

**Definition:** [Stage 2 — Observation Method](/methodology/core-methodology/stage-2-semantic-capabilities.md#observation-method) · **Municipality questions:** [Public Lighting](/profiles/lighting/municipality-questions.md#observation-method), [Water Management & Irrigation](/profiles/water/municipality-questions.md#observation-method)

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

## 2.4 Temporal Semantics

**Definition:** [Stage 2 — Temporal Semantics](/methodology/core-methodology/stage-2-semantic-capabilities.md#temporal-semantics) · **Municipality questions:** [Public Lighting](/profiles/lighting/municipality-questions.md#temporal-semantics), [Water Management & Irrigation](/profiles/water/municipality-questions.md#temporal-semantics)

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


# 3. Interpretation Semantics

## 3.1 Provenance

**Definition:** [Stage 2 — Provenance](/methodology/core-methodology/stage-2-semantic-capabilities.md#provenance) · **Municipality questions:** [Public Lighting](/profiles/lighting/municipality-questions.md#provenance), [Water Management & Irrigation](/profiles/water/municipality-questions.md#provenance)

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

## 3.2 Measurement Quality

**Definition:** [Stage 2 — Measurement Quality](/methodology/core-methodology/stage-2-semantic-capabilities.md#measurement-quality) · **Municipality questions:** [Public Lighting](/profiles/lighting/municipality-questions.md#measurement-quality), [Water Management & Irrigation](/profiles/water/municipality-questions.md#measurement-quality)

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

## 3.3 Operational Context

**Definition:** [Stage 2 — Operational Context](/methodology/core-methodology/stage-2-semantic-capabilities.md#operational-context) · **Municipality questions:** [Public Lighting](/profiles/lighting/municipality-questions.md#operational-context), [Water Management & Irrigation](/profiles/water/municipality-questions.md#operational-context)

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

## 3.4 Physical Context

**Definition:** [Stage 2 — Physical Context](/methodology/core-methodology/stage-2-semantic-capabilities.md#physical-context) · **Municipality questions:** [Public Lighting](/profiles/lighting/municipality-questions.md#physical-context), [Water Management & Irrigation](/profiles/water/municipality-questions.md#physical-context)

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


# 4. Operational Semantics

## 4.1 Asset Management Context

**Definition:** [Stage 2 — Asset Management Context](/methodology/core-methodology/stage-2-semantic-capabilities.md#asset-management-context) · **Municipality questions:** [Public Lighting](/profiles/lighting/municipality-questions.md#asset-management-context), [Water Management & Irrigation](/profiles/water/municipality-questions.md#asset-management-context)

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

## 4.2 Network Operability

**Definition:** [Stage 2 — Network Operability](/methodology/core-methodology/stage-2-semantic-capabilities.md#network-operability) · **Municipality questions:** [Public Lighting](/profiles/lighting/municipality-questions.md#network-operability), [Water Management & Irrigation](/profiles/water/municipality-questions.md#network-operability)

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

## 4.3 Fallback Behaviour

**Definition:** [Stage 2 — Fallback Behaviour](/methodology/core-methodology/stage-2-semantic-capabilities.md#fallback-behaviour) · **Municipality questions:** [Public Lighting](/profiles/lighting/municipality-questions.md#fallback-behaviour), [Water Management & Irrigation](/profiles/water/municipality-questions.md#fallback-behaviour)

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

# Expected Outcome

Applying this framework should enable ecosystem participants to:

- Identify which semantic capabilities are already supported by existing specifications.
- Identify semantic capabilities requiring additional discussion or future enhancements.
- Improve interoperability between device standards, Smart Data Models, and Digital Twin ecosystems.
- Preserve municipality operational meaning across standards and semantic models.
- Support the development of semantically consistent Digital Twins capable of monitoring, analysing, simulating, and operating municipality services.
