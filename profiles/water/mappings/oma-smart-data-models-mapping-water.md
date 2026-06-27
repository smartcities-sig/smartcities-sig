---
title: OMA Smart Data Models Mapping for Water
description: Mapping between OMA LwM2M Objects and FIWARE Smart Data Models for smart water management.
layout: doc
---

# {{ $doc.title }}

- [**Reference Document**](https://groups.io/g/smartcities-sig/files/Discussion/2026/20260513-especificacion%20de%20caso%20de%20uso%20water%20v0.1.docx)  

## Quantities to be measured

- [X] Volume per unit of time (or during a time period indicated as the second value). Specify whether liters or cubic meters.
- [X] Time at which it was measured (time of completion, or start)
- [ ] Temperature, pH and other environmental soil parameters
- [ ] Weather at that time
- [ ] Weather forecast at that time
- [ ] Water pressure
- [ ] Additional characteristics of the water: recycled or potable…



## Data Models

- Water meter (OMA) Object [#3424](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/3424.xml)
    -The water pressure could be possibly added to the OMA Data Model

- Water quality sensor (OMA) Object [#3426](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/3426.xml)

- [WaterConsumptionObserved (Smart Data Models)](https://github.com/smart-data-models/dataModel.WaterConsumption/blob/master/WaterConsumptionObserved/doc/spec.md)

- [WaterDistributionNetwork (Smart Data Models)](https://github.com/smart-data-models/dataModel.WaterDistribution/blob/master/WaterDistributionNetwork/doc/spec.md)



## Mappable information

| OMA                               | FIWARE                                       |
| --------------------------------- | -------------------------------------------- |
| Latitude (6/1) Longitude (6/2)    | location                                     |
| Cumulated water volume (3424/1)   | waterConsumption                             |
| Timestamp (3424/5518)             | observationDateTime                          |
| Minimum  flow rate (3424/7)       | minFlow                                      |
| Maximum  flow rate (3424/8)       | maxFlow                                      |
| Leak  detected (3424/10)          | alarmStopsLeaks                              |
| Fraud detected (3424/13)          | moduleTampered                               |
| pH (3426/1 - WaterQuality object) | pHTSA                                        |
| *TODO*                            | waterPressure  (in WaterDistributionNetwork) |


### Tests

 - [OMA-ETS-uCIFI-Test-Cases-Smart-Water](https://github.com/OpenMobileAlliance/scwg-ETS-conformance-for-Smart-City/blob/Dev/ETS/uCIFI-Test-Cases-Smart-Water.md)
