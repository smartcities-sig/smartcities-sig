---
title: Smart Cities SIG Glossary
description: The terms defined or consistently used across the Smart Cities SIG methodology.
layout: doc
---

# {{ $doc.title }}

This glossary collects the terms defined or consistently used across the Smart Cities SIG methodology documents, in alphabetical order, with one meaning per term.

It is the single place where these terms are defined; other pages link here instead of redefining them. The one exception is the 14 semantic capabilities: their definitions are owned by [Stage 2 — Semantic Capabilities](/methodology/core-methodology/stage-2-semantic-capabilities.md), and their entries here repeat Stage 2's definition word for word. A term added before SIG review is marked *Status: Proposed* until the SIG accepts it. An *Avoid* line lists earlier or ambiguous wording that should not be used for the term. A term no longer in use is marked *Deprecated* and names the term to use instead.

---

### Action / Event

In the entity sketch, an **action** is invoked on an entity or triggered by it (for example, dimming a streetlight); an **event** is emitted by an entity (for example, a lamp failure). Stage 2 does not classify them; it classifies the property rows derived from them, and how they are represented is an open question for Stage 4.

### Aggregated

An Observation Method value: a value obtained by combining several underlying observations into one. What is combined is recorded separately: across assets or locations by Observation Scope, across time by Temporal Semantics.

### Asset Management Context

Operational management information associated with infrastructure assets throughout their lifecycle. Defined in [Stage 2](/methodology/core-methodology/stage-2-semantic-capabilities.md#asset-management-context).

### Candidate

A Smart Data Model that Stage 3 finds for an entity type of the entity sketch, or an OMA object that it finds for one of its properties, before Stage 4 has checked that they fit. A candidate is not yet a mapping.
*Status: Proposed*
_Avoid_: mapping (for an unchecked candidate)

### Capability Assessment Matrix

*Deprecated — use Ecosystem Assessment.* A table, formerly part of the Semantic Capability Assessment Framework, that recorded each ecosystem's results per capability; it was removed because its results disagreed with the ecosystem reports.

### Companion Capability

A semantic capability that a sub-observation also carries for context, in addition to its one Primary Capability. Used when classifying ecosystem material in Stage 3.

### Contextual Metadata

The circumstances of a measurement (weather, vegetation, schedules, maintenance zones) that must stay attached to it for it to be read correctly. It is not a semantic capability: Operational Context and Physical Context carry it.

### Convergence

The Stage 4 work of reconciling the independent Ecosystem Assessments into Smart Data Models: comparing results per capability, matching candidates, assigning realization responsibility, and recording Residual Gaps, with every decision traceable to the municipality's operational meaning.

### Digital Twin

The software representation of municipal infrastructure and services that consumes operational data for monitoring, analytics, simulation, and decisions. In the methodology it is the consumer of the output, not an ecosystem assessed in Stage 3.

### Digital Twin Operator

The team, in the municipality or contracted by it, that runs the city's Digital Twin. In Stage 1 it reviews each Digital Twin Question and is a unit that open questions can be addressed to.
*Status: Proposed*

### Digital Twin Question

A question the municipality will ask its Digital Twin in order to meet an operational need, raised by a department in Stage 1 in its own words and with no capability label. Every user story has at least one; once the Digital Twin Operators accept it, it is a Municipality Operational Question.
*Status: Proposed*

### Domain Semantics

One of the four semantic categories: what the municipality ultimately cares about — the service delivered, the infrastructure providing it, and the resources it consumes. Groups Service Outcome, Infrastructure Output, and Resource Consumption.

### Ecosystem Assessment

A report that evaluates one ecosystem (for example, OMA LwM2M or Smart Data Models) against the Semantic Capability Assessment Framework. It is the only place where that ecosystem's results are recorded.
_Avoid_: Capability Assessment Matrix

### Ecosystem Coordination / Ecosystem Realization

The Stage 3 work of aligning how ecosystem participants — standards bodies, Smart Data Model communities, FIWARE, vendors, universities — contribute to realizing the semantic capabilities, without imposing a single implementation. Which ecosystem realizes each capability is decided in Stage 4 (see Convergence).

### Entity Sketch

The Stage 1 summary of the entity types the user stories mention, each with its properties, actions, events, and relationships, in the municipality's own words and with no standard names. Stage 2 classifies its properties; Stage 3 looks for candidate Smart Data Models for its entity types.
_Avoid_: entity model, data model (for the Stage 1 output)

### Estimated

An Observation Method value: a value calculated from other measured quantities of the same system with a known formula or specification (for example, illuminance computed from luminaire data and geometry).

### Fallback Behaviour

The autonomous behaviour of infrastructure when normal communications or supervisory control become unavailable. Defined in [Stage 2](/methodology/core-methodology/stage-2-semantic-capabilities.md#fallback-behaviour).

### FIWARE

An open-source ecosystem in which the Smart Data Models catalogue originated. In the methodology it contributes Smart Data Model practices.

### Inferred

An Observation Method value: a value deduced from indirect or correlated evidence rather than calculated for the quantity itself (for example, soil moisture inferred from rainfall history and an evapotranspiration model).

### Infrastructure Output

The physical output produced by infrastructure assets while delivering a municipality service — how the infrastructure behaves, not whether the municipality objective has been achieved. Defined in [Stage 2](/methodology/core-methodology/stage-2-semantic-capabilities.md#infrastructure-output).
_Avoid_: Infrastructure Behavior (as the capability name)

### Interoperability

The ability of systems, standards, and data models from different ecosystems to exchange municipal operational information and interpret it correctly, without losing its meaning.

### Interoperability Profile

A named set of semantic requirements that an ecosystem makes mandatory for a Service Domain — for example, an OMA Public Lighting Interoperability Profile that requires timestamp, unit, and quality Resources.
_Avoid_: profile (unqualified), candidate profile concept

### Interpretation Semantics

One of the four semantic categories: how observations should be understood and trusted — their trustworthiness conditions, following the Trustworthiness viewpoint of ISO/IEC 30141. Groups Provenance, Measurement Quality, Operational Context, and Physical Context.

### ISO/IEC 30141

The international standard for an IoT Reference Architecture. The four semantic categories follow the viewpoint-and-view structure of its Clause 6 (2024 edition).

### LwM2M (Lightweight Machine to Machine)

OMA's device management and data model protocol for constrained IoT devices, whose Objects and Resources are assessed in Stage 3.

### Meaning Before Standards

The central principle of the methodology: operational meaning is captured before any standard, schema, or architecture is chosen, so standard data names enter only in Stage 3. Stated once in the Methodology Overview and applied in every stage.
_Avoid_: premature standardization (as a separately defined idea per stage)

### Measured

An Observation Method value: a value obtained by directly sensing the target quantity itself, with no transformation, model, forecast, or substitute variable. The other Observation Method values are defined by contrast with it.

### Measurement Quality

The quality characteristics of an observation: its accuracy, precision, reliability, completeness, and uncertainty. Defined in [Stage 2](/methodology/core-methodology/stage-2-semantic-capabilities.md#measurement-quality).

### Methodology Worksheet

A fill-in template that supports the Stage 2 analysis of a Service Domain by asking, step by step, the questions that surface each capability. It predates the Stage 1 Package and is to be revised after the Stage 1 evaluation.

### Model-derived

An Observation Method value: a value produced by applying a computational or analytical model to input data, rather than read from a sensor.

### Municipality Operational Question

A Digital Twin Question that the Digital Twin Operators have accepted. Stage 2 keys it by semantic capability, it is kept in the Service Profile, and Stage 4 checks the Smart City Profile against it.
*Status: Proposed* (the Digital Twin Operator review)

### Municipality Operational Reality

The starting point of the methodology: a municipality's actual operational conditions, needs, and constraints, before any semantic or interoperability analysis. It is broader than the needs a municipality states, because it also includes the constraints, context, and existing systems it may not state.
_Avoid_: municipality operational needs (for the starting point as a whole)

### Need

A statement of what a municipal department wants, as the department gave it (for example, one row of a workshop table); it is never edited. One need gives one or more user stories, a requirement, or both.
*Status: Proposed*
_Avoid_: calling a need a user story, theme

### Network Operability

The communication characteristics that influence remote monitoring and control. Defined in [Stage 2](/methodology/core-methodology/stage-2-semantic-capabilities.md#network-operability).

### NGSI-LD

The ETSI standard information model and API for context information, based on JSON-LD, in which Smart Data Models are expressed.
*Status: Proposed*

### Observation

The raw, possibly compound fact being classified: in Stage 2, a property row of the entity sketch; in Stage 3, a statement in ecosystem material.

### Observation Method

The method used to produce an observation. Defined in [Stage 2](/methodology/core-methodology/stage-2-semantic-capabilities.md#observation-method). Its values are Measured, Proxy Measurement, Estimated, Inferred, Predicted, Simulated, Model-derived, and Aggregated.

### Observation Point

The physical or logical location where an observation originates — where the information was obtained, independently of the asset being monitored. Defined in [Stage 2](/methodology/core-methodology/stage-2-semantic-capabilities.md#observation-point).

### Observation Scope

The assets, operational area, or population that an observation represents — what the observation applies to, rather than where it was collected. Defined in [Stage 2](/methodology/core-methodology/stage-2-semantic-capabilities.md#observation-scope).

### Observation Semantics

One of the four semantic categories: how operational information is observed — where it originates, what it represents, how it is obtained, and its time basis. Groups Observation Point, Observation Scope, Observation Method, and Temporal Semantics.

### OMA (Open Mobile Alliance)

The standards organization whose device interoperability standards (see LwM2M) the SIG assesses in Stage 3.

### OMA Registry Capability Classification

The resource-by-resource classification of the OMA LwM2M Registry against the 14 semantic capabilities. It is evidence for the OMA Ecosystem Assessment, not a definition of the capabilities.
_Avoid_: Semantic Capability Reference (for this page)

### Operational Context

Dynamic operating conditions that influence service behaviour and the interpretation of observations. Defined in [Stage 2](/methodology/core-methodology/stage-2-semantic-capabilities.md#operational-context).
_Avoid_: Contextual Abstraction, Contextual Metadata (as a capability name)

### Operational Evidence

The statements a respondent makes in Stage 1 that explain the user stories and entity-sketch rows, kept in the respondent's words and linked to them. Each statement is an evidence item of one of five kinds: objective, pain point, distinction, context, or held elsewhere (information another unit or a manufacturer holds).
*Status: Proposed*
_Avoid_: summary, notes, findings, observations

### Operational Meaning

What a municipality actually needs to know or do, and why, in its own terms, captured in Stage 1 before any standard is considered.

### Operational Semantic Translation Model

The overall model of how municipality operational reality is transformed through the four stages into output a Digital Twin can consume, with later stages sending questions back to earlier ones.

### Operational Semantics

One of the four semantic categories: how infrastructure is operated and managed throughout its lifecycle — responsibility, communications, and resilience. Groups Asset Management Context, Network Operability, and Fallback Behaviour; how it applies to the entity sketch is still under discussion.

### Pain Point (Operational Pain Point)

A specific operational difficulty, inconsistency, or piece of unreliable or incomparable information in a municipal service. In Stage 1 it is recorded as an Operational Evidence item of kind *pain point*.

### Physical Context

Static physical characteristics of the environment that influence service outcomes. Defined in [Stage 2](/methodology/core-methodology/stage-2-semantic-capabilities.md#physical-context).
_Avoid_: Contextual Abstraction, Contextual Metadata (as a capability name)

### Predicted

An Observation Method value: a value describing a future state, produced by a forecasting technique (for example, water demand predicted from weather forecasts). It differs from the other values mainly by looking forward in time.

### Primary Capability

The one semantic capability a sub-observation is fundamentally about. Used when classifying ecosystem material in Stage 3.

### Proof of Concept

A programme activity, outside the four stages, that validates a Smart City Profile in a real deployment and feeds its lessons back into Stage 1.
_Avoid_: Stage 5, Stage 6

### Property Fact

One of the eight things Stage 1 asks about each entity-sketch property: (a) the thing it belongs to, (b) its role, (c) where it is known, (d) how it is known today, by whom, how often and how old, (e) what makes it good or bad and who sets that, (f) the circumstances that change how it is read, (g) what is decided or done with it, and (h) what goes wrong today. A property is complete when every fact is answered or routed to a named unit as an open question.
*Status: Proposed*
_Avoid_: property profile, card, evidence

### Provenance

The origin of an observation or piece of operational information. Defined in [Stage 2](/methodology/core-methodology/stage-2-semantic-capabilities.md#provenance).

### Proxy Measurement

An Observation Method value: a different quantity, measured directly, reported as a stand-in for the target quantity (for example, luminaire input current for light output).

### Requirement

A need that says how the system should be built, which means to use, how data should be handled, or what systems must exchange, rather than what someone needs to know or do about a thing. Stage 1 keeps requirements in a register, linked to the user stories or entity-sketch rows they relate to; how Stage 2 treats them is an open SIG question (OI-019).
*Status: Proposed*
_Avoid_: technical story, non-functional story

### Residual Gap

A semantic capability that no assessed ecosystem contribution covers. Stage 4 records it with the operational consequence of leaving it unrealized; it is never silently dropped.

### Resource Consumption

The resources consumed while delivering the municipality service. Defined in [Stage 2](/methodology/core-methodology/stage-2-semantic-capabilities.md#resource-consumption).

### Reusable Interoperability Abstraction

*Deprecated — use Semantic Capability.* Earlier name for what Stage 2 produces.

### SAREF (Smart Applications REFerence ontology)

An ETSI standard ontology for describing IoT devices and their measurements, with domain extensions such as SAREF4CITY. Stage 4 considers it next to Smart Data Models; its place in the Smart City Profile is still under discussion.
*Status: Proposed*

### SDO (Standards Development Organization)

A body that develops and maintains technical standards. Stage 3 uses "other SDOs and alliances" for standards bodies beyond OMA that may contribute domain-specific assets.

### Semantic Capability

One dimension of meaning needed to interpret municipal operational data correctly — what it represents, where it comes from, how much it can be trusted, or how it should be acted on. The SIG defines 14, grouped into 4 semantic categories, in Stage 2, which classifies each entity-sketch property against them.
_Avoid_: reusable interoperability abstraction, abstraction type, `ServiceOutcomeMeasurement`-style abstraction names

### Semantic Capability Assessment Framework (SCAF)

The technology-neutral set of questions, per semantic capability, that Stage 3 asks of each ecosystem to find whether its specifications preserve that capability. It holds questions only; its Digital Twin questions are the Stage 4 acceptance check of a Smart City Profile.

### Semantic Category

One of the four groupings of the 14 semantic capabilities — Domain, Observation, Interpretation, and Operational Semantics — following Clause 6 of ISO/IEC 30141. "Domain Semantics" names a category, not a Service Domain.
_Avoid_: semantic domain, domain (for the grouping)

### Semantic Distinction

A difference between two measurements or concepts that look related but have different operational meanings (for example, service outcome vs infrastructure output, or measured vs inferred values). In Stage 1 it is recorded as an Operational Evidence item of kind *distinction*.

### Semantic Domain

*Deprecated — use Semantic Category.* Renamed because "domain" clashed with Service Domain.

### Semantic Drift

A Stage 3 pitfall in which ecosystem realization approaches fail to preserve the operational meaning identified earlier, so the municipality's intent is lost in implementation.

### Service Domain

A municipal service area analysed by the methodology, such as Public Lighting or Water Management & Irrigation. Not to be confused with Domain Semantics, which is a semantic category.
_Avoid_: domain (unqualified), use case, Smart Water Metering (for the current water scope)

### Service Outcome

The actual outcome experienced by people, infrastructure, or the environment — what the municipality is trying to achieve, independently of how the underlying infrastructure operates. Defined in [Stage 2](/methodology/core-methodology/stage-2-semantic-capabilities.md#service-outcome).

### Service Profile

The working material the SIG keeps for one Service Domain under `profiles/<domain>/`: its walkthrough, municipality operational questions, and OMA-to-Smart-Data-Models mappings. Not to be confused with an Interoperability Profile or with the Smart City Profile.
_Avoid_: profile (unqualified)

### Simulated

An Observation Method value: a value produced by running a model of the system to reproduce a real, hypothetical, or counterfactual scenario.

### Smart City Profile

The SIG's implementation-ready deliverable for one Service Domain, produced in Stage 4: the converged Smart Data Model realization (including new models drafted where none fitted), a catalogue of the OMA objects that can feed it, the required metadata, and the Residual Gaps. It is validated in a Proof of Concept.
_Avoid_: profile (unqualified), Service Profile (for the deliverable)

### Smart Data Model

An open data model, from the catalogue that originated in FIWARE, that combines telemetry, metadata, operational context, and relationships so that information stays interoperable and consumable by Digital Twins. Stage 4 expresses the realized capabilities as Smart Data Models.

### Smart Data Object

*Deprecated — use Smart Data Model.* Used in earlier versions in the same sense.

### Stage 1 — Operational Meaning

The first methodology stage. It turns municipality needs, collected in workshops or interviews, into a Stage 1 Package in the municipality's own words, before any standard is considered.

### Stage 1 Package

Everything Stage 1 produces for one Service Domain in one municipality: user stories with their Digital Twin Questions, the entity sketch, Operational Evidence, the register of requirements, open questions per unit, the collection log and session notes, and one Stage 2 Brief per user story.
*Status: Proposed*

### Stage 2 — Semantic Capabilities

The second methodology stage. It classifies each property of the entity sketch against the 14 semantic capabilities, which it defines and maintains independently of any standard.
_Avoid_: Reusable Interoperability Abstractions (as a stage name)

### Stage 2 Brief

A document generated from the Stage 1 Package for one user story, listing every entity-sketch row the story touches with all its facts, sources, and linked evidence, requirements, and open questions. It is Stage 2's input for that story and holds no capability names.
*Status: Proposed*

### Stage 3 — Standards & Ecosystem Mapping

The third methodology stage. It assesses each ecosystem against the Semantic Capability Assessment Framework and finds candidate Smart Data Models for the entity types and candidate OMA objects for the classified properties.

### Stage 4 — Smart Data Models Realization

The fourth methodology stage. It reconciles the Stage 3 results into the Smart City Profile for each Service Domain; its detailed definition is still under development by the SIG.
_Avoid_: Stage 3 "mapping" (for the Smart Data Models and ontology mapping step)

### Sub-observation

A piece of a compound observation, split so that it is fundamentally about one Primary Capability. Used when classifying ecosystem material in Stage 3.

### Temporal Semantics

The time basis of an observation and its use in KPIs and simulation. Defined in [Stage 2](/methodology/core-methodology/stage-2-semantic-capabilities.md#temporal-semantics).

### Trustworthiness Conditions

The conditions under which an observation can be relied on — its provenance, quality, and operational and physical context. A descriptive label for the Interpretation Semantics category.

### User Story

A Stage 1 statement of a need in the words of whoever has it, following a fixed pattern: a type of user, an action, the conditions, and the benefit ("<type of user> want to <action> under <conditions> so that <benefit>"). A good story is specific, measurable, achievable, relevant, and testable, and the benefit points to the Service Outcome.
