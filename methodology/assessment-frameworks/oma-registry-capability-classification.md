---
title: OMA LwM2M Registry Capability Classification
description: Every resource in the OMA LwM2M Registry classified against the Smart Cities SIG semantic capabilities.
layout: web
---

# {{ $doc.title }}

## Introduction

This page classifies every resource in the OMA LwM2M Registry against the
[semantic capabilities](/methodology/core-methodology/stage-2-semantic-capabilities.md) defined in Stage 2, so you can
see directly which capabilities OMA can supply today and where the gaps are.

It is resource-by-resource evidence supporting the [OMA Semantic Capability Assessment](./oma-capability-assessment.md),
which answers the [assessment questions](./semantic-capability-assessment.md) capability by capability and documents
the assessment baseline and scope. For where this fits in the methodology, see the
[Methodology Overview](/methodology/core-methodology/methodology-overview.md).

> **Status:** The classifications in the tables below are a working analysis, not a finalized SIG position. Entries
> flagged `Candidate Capability`, and object range 3410–3429, have not yet had a group review pass. The **Confidence**
> column records the classifier's confidence in each call; its scoring scale is not yet documented. Treat this as a
> draft for discussion, not a settled answer.

## Objects Semantic Capability

Every object-specific resource in the OMA LwM2M Registry, classified against the semantic capabilities, with a
confidence score and a note explaining the call. *Working analysis — not yet reviewed by the group.*

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
    title: "Semantic Category"
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
    title: Category
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
