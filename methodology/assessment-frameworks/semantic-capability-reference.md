---
title: Semantic Capability Reference
description: null
layout: doc
---

# {{ $doc.title }}

## Introduction


## Semantic Capability Reference

::EhEmbed
---
download: true
dataUrl: iframe/semantic-capabilities-reference.html
---
::

## Objects Semantic Capability

::EhDynamicTable
---
dataUrl: "https://github.com/elastic-hub/engineering/blob/main/smartcities-sig/methodology/assessment-frameworks/lwm2m-registry-capability-mapping.json"
transformRawData: lwm2m_registry_capability_mapping
header: "**LwM2M Registry Capability Mapping**"
perPage: 10
columns:
  - name: "object_id"
    title: "Object ID"
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
    filter: true
    filterOrder: 1
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
    filter: true
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
dataUrl: iframe/municipal-invitation.html
---
::
