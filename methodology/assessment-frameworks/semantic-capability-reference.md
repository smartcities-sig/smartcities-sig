---
title: Semantic Capability Reference
description: null
layout: web
---

# {{ $doc.title }}

## Introduction

A raw registry value doesn't answer a municipality's question by itself — a lux reading only means something once you
know where it was taken, how it was produced, and what it's supposed to represent. The Smart Cities SIG closes that
gap in three stages:

- **Stage 1 — Operational Meaning**: captures what a municipality is actually trying to accomplish, in its own terms.
- **Stage 2 — Reusable Abstractions**: generalizes that into a standards-independent taxonomy of 14 semantic capabilities.
- **Stage 3 — Standards & Ecosystem Mapping**: checks which standards ecosystems — starting here with OMA LwM2M — can actually supply the information each capability needs.

This page shows the output of Stages 2 and 3 for OMA LwM2M. The **Semantic Capability Reference** below is Stage 2's
taxonomy: the 14 capabilities every registry resource is classified against, and how to apply them. The **Objects
Semantic Capability** and **Common Resources Capability Reference** tables that follow are Stage 3's assessment:
every resource in the OMA LwM2M Registry, classified against those capabilities, so you can see directly what OMA can
currently supply today and where the gaps are. The full assessment methodology — baseline revisions, scope, and
confidence scoring — is documented in `oma-capability-assessment.md`.

> **Status:** The classifications in the tables below are a working analysis, not a finalized SIG position. Entries
> flagged `Candidate Capability`, and object range 3410–3429, have not yet had a group review pass. Treat this as a
> draft for discussion, not a settled answer.

Want to contribute your own city's operational questions to Stage 1? See the invitation at the bottom of this page.

## Semantic Capability Reference

Stage 2 output — the 14 reusable capabilities everything below is classified against.

::EhEmbed
---
download: true
dataUrl: /iframe/semantic-capabilities-reference.html
---
::

## Objects Semantic Capability

Stage 3 assessment: every object-specific resource in the OMA LwM2M Registry, classified against the capabilities
above, with a confidence score and a note explaining the call. *Working analysis — not yet reviewed by the group.*

::EhDynamicTable
---
dataUrl: "https://github.com/elastic-hub/engineering/blob/main/smartcities-sig/methodology/assessment-frameworks/lwm2m-registry-capability-mapping.json"
transformRawData: lwm2m_registry_capability_mapping
header: "**LwM2M Registry Capability Mapping**"
perPage: 10
columns:
  - name: "object_id"
    title: "Object ID"
    filter: true
    filterOrder: 1    
    query: true
    sortable: true
    type: text
  - name: "object_name"
    title: "Object"
    filter: true
    filterOrder: 2
    query: true
    sortable: true
    type: text
  - name: "object_owner"
    title: "Owner"
    filter: false
    filterOrder: 3
    query: true
    sortable: true
    type: text
  - name: "resource_id"
    title: "Res. ID"
    query: true
    sortable: true
    type: text
  - name: "resource_name"
    title: "Resource"
    query: true
    sortable: true
    type: text
  - name: "resource_description"
    title: "Description"
    query: true
    sortable: false
    wrap: true
    type: text
  - name: "resource_source"
    title: "Source"
    filter: false
    filterOrder: 3
    sortable: true
    pill: true
    type: text
  - name: "semantic_domain"
    title: "Semantic Domain"
    filter: true
    filterOrder: 4
    query: true
    sortable: true
    pill: true
    type: text
  - name: "semantic_capability"
    title: "Semantic Capability"
    filter: true
    filterOrder: 5
    query: true
    sortable: true
    pill: true
    type: text
  - name: "companion_capabilities"
    title: "Companion Capabilities"
    filter: true
    filterOrder: 6
    query: true
    sortable: false
    wrap: true
    type: list
  - name: "confidence"
    title: "Confidence"
    filter: true
    filterOrder: 7
    sortable: true
    pill: true
    type: text
  - name: "note"
    title: "Note"
    query: true
    sortable: false
    wrap: true
    type: text
---
::



## Common Resources Capability Reference

OMA's reusable `Common.xml` resources (IDs 4000–6057), assessed separately from object-specific resources above.
Some classify consistently regardless of host object; others are context-dependent — their capability depends on
what the containing object measures. *Working analysis — not yet reviewed by the group.*

::EhDynamicTable
---
dataUrl: https://github.com/elastic-hub/engineering/blob/main/smartcities-sig/methodology/assessment-frameworks/common-resources-capability-reference.json
transformRawData: common_resources
perPage: 10
header: "**OMA LwM2M Common Resources**"
columns:
  - name: resource_id
    title: ID
    filter: false
    query: true
    hide: false
    sortable: true
    type: text
  - name: resource_name
    title: Resource
    filter: false
    query: true
    hide: false
    sortable: true
    type: text
  - name: stability
    title: Stability
    filter: true
    query: true
    hide: false
    sortable: true
    type: text
    pill: true
  - name: semantic_domain
    title: Domain
    filter: true
    query: true
    hide: false
    sortable: true
    type: text
  - name: semantic_capability
    title: Capability
    filter: true
    query: true
    hide: false
    sortable: true
    type: text
  - name: usage_count
    title: Uses
    filter: false
    query: false
    hide: false
    sortable: true
    type: text
  - name: used_by_object_ids
    title: Used By
    filter: false
    query: true
    hide: false
    sortable: false
    type: list
  - name: submitter
    title: Submitter
    filter: true
    query: true
    hide: false
    sortable: true
    type: text
  - name: resource_description
    title: Description
    filter: false
    query: true
    hide: false
    sortable: false
    type: text
    wrap: true
  - name: note
    title: Note
    filter: false
    query: true
    hide: true
    sortable: false
    type: text
---
::


## Municipality Invitation

::EhEmbed
---
download: true
dataUrl: /iframe/municipal-invitation.html
---
::
