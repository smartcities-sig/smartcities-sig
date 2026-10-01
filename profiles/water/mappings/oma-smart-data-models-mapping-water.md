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
- [x] Temperature, pH and other environmental soil parameters
- [ ] Weather at that time
- [ ] Weather forecast at that time
- [x] Water pressure
- [ ] Additional characteristics of the water: recycled or potable…



## Data Models

- Temperature (OMA) Object [#3303](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/3303.xml)
- Humidity (OMA) Object [#3304](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/3304.xml)
- Water meter (OMA) Object [#3424](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/3424.xml)
- Irrigation valve (OMA) [#3425](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/3425.xml)
- Water quality sensor (OMA) Object [#3426](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/3426.xml)
- Pressure monitoring sensor (OMA) [#3427](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/3427.xml)
- [WaterConsumptionObserved (Smart Data Models)](https://github.com/smart-data-models/dataModel.WaterConsumption/blob/master/WaterConsumptionObserved/doc/spec.md)
- [WaterDistributionNetwork (Smart Data Models)](https://github.com/smart-data-models/dataModel.WaterDistribution/blob/master/WaterDistributionNetwork/doc/spec.md)
- [AgriParcelRecord (Smart Data Model)](https://github.com/smart-data-models/dataModel.Agrifood/blob/master/AgriParcelRecord/doc/spec.md)
- [WeatherObserved  (Smart Data Model)](https://github.com/smart-data-models/dataModel.Weather/blob/master/WeatherObserved/doc/spec.md)



## Mappable information

| OMA Objects                       | OMA Resources              | Smart Data Model Entities | Smart Data Model Properties |
| --------------------------------- | -------------------------- | ------------------------- | --------------------------- |
| Location (6)                      | Latitude (1)               | WaterConsumptionObserved  | location                    |
| Location (6)                      | Longitude (2)              | WaterConsumptionObserved  | location                    |
| Water meter (3424)                | Cumulated water volume (1) | WaterConsumptionObserved  | waterConsumption            |
| Water meter (3424)                | Timestamp (5518)           | WaterConsumptionObserved  | observationDateTime         |
| Water meter (3424)                | Minimum  flow rate (7)     | WaterConsumptionObserved  | minFlow                     |
| Water meter (3424)                | Maximum  flow rate (8)     | WaterConsumptionObserved  | maxFlow                     |
| Water meter (3424)                | Leak  detected (10)        | WaterConsumptionObserved  | alarmStopsLeaks             |
| Water meter (3424)                | Fraud detected (13)        | WaterConsumptionObserved  | moduleTampered              |
| Water quality sensor (3426)       | pH (1)                     | WaterConsumptionObserved  | pHTSA                       |
| Water quality sensor (3426)       | Salinity (11)              | AgriParcelRecord          | soilSalinity                |
| Temperature (3303)                | Sensor Value (5700)        | AgriParcelRecord          | soilTemperature             |
| Humidity (3304)                   | Sensor Value (5700)        | AgriParcelRecord          | relativeHumidity            |
| Pressure monitoring sensor (3427) | Pressure (1)               | WaterDistributionNetwork  | waterPressure               |
| Irrigation valve (3425)           | Status (2)                 | TODO                      |                             |


### Tests

 - [OMA-ETS-uCIFI-Test-Cases-Smart-Water](https://github.com/OpenMobileAlliance/scwg-ETS-conformance-for-Smart-City/blob/Dev/ETS/uCIFI-Test-Cases-Smart-Water.md)
