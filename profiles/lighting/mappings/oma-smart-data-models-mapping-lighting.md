---
title: OMA Smart Data Models Mapping for Lighting
description: Mapping between OMA LwM2M Objects and FIWARE Smart Data Models for smart lighting.
layout: doc
---

# {{ $doc.title }}

- [**Reference Document**](https://groups.io/g/smartcities-sig/files/Discussion/2026/20260513-especificacion%20de%20caso%20de%20uso%20lighting%20v0.1.docx)  

## Quantities to be measured

- [ ] Light on the surface of the streets. (would require a separate illuminance sensor)
- [ ] Lumens emitted by the luminaire (can be done by extending OMA data model)
- [x] Watts consumed
- [x] Time at which it was measured (time of completion, or start)
- [ ] Color temperature
- [ ] Weather at that time (out of scope)
- [ ] Weather forecast at that time (out of scope)
- [x] Mains voltage and frequency. Stability.
- [x] Active power, reactive power…
- [ ] Additional features: existence of additional elements connected to that branch.
- [x] Location (not always provided by the device itself, but captured during installation)



## Measurement conditions

- In each luminaire with Zagha connector
- At the head of the line (show how many luminaires are on it)
- Type of lighting fixtures (pedestrian zone or vehicles)



## Data Models


- Outdoor Lamp Controller (OMA) Object [#3416](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/3416.xml)

- Electrical Monitor (OMA) Object [#3418](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/3418.xml)

- Illuminance (OMA) Object [#3301](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/3301.xml)

- Presence (OMA) Object [#3302](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/3302.xml)

- Traffic Counter (OMA) Object [#3432](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/3432.xml)

- Street Light (Smart Data Models) Object [#Streetlight](https://github.com/smart-data-models/dataModel.Streetlighting/blob/master/Streetlight/doc/spec.md)

## Mappable information

| OMA Objects                    | OMA Resources                       | Smart Data Model Entities | Smart Data Model Properties |
| ------------------------------ | ----------------------------------- | ------------------------- | --------------------------- |
| Location (6)                   | Latitude (1)                        | Streetlight               | location                    |
| Location (6)                   | Longitude (2)                       | Streetlight               | location                    |
| Outdoor Lamp Controller (3416) | Command in action                   | Streetlight               | powerState                  |
| Outdoor Lamp Controller (3416) | Timestamp (5518)                    | Streetlight               | observationDateTime         |
| Outdoor Lamp Controller (3416) | Lamp ON timestamp (17)              | Streetlight               | dateLastSwitchingOn         |
| Outdoor Lamp Controller (3416) | TODO                                | Streetlight               | dateLastSwitchingOff        |
| Outdoor Lamp Controller (3416) | Actual light color temperature (40) | TODO                      | TODO                        |
| Electrical Monitor (3418)      | Active power (4)                    | Streetlight               | powerConsumtpion            |
| Electrical Monitor (3418)      | Cumulated active energy (6)         | Streetlight               | lifetimePowerConsumption    |
| Electrical Monitor (3418)      | Power factor (5)                    | Streetlight               | powerFactor                 |
| Electrical Monitor (3418)      | Supply current (2)                  | Streetlight               | current                     |
| Electrical Monitor (3418)      | Supply voltage (1)                  | Streetlight               | voltage                     |
| Illuminance (3301)             | Sensor Value (5700)                 | Streetlight               | illuminanceLevel            |

It seems there is no possibility of control over dimming, but that could be absolutely acceptable. This also explains why the vast majority of the resources are related to the Electrical Monitor (3418) and not to the Outdoor Lamp Controller (3416)
The nominal lamp output in lumen at 100% dimming should be added to the OMA Data Model
The color temperature is not currently present in the Smart Data Model



## Tests

- [uCIFI-OMA-ETS-Conformance-Smart-City-V1_0-20250416-D_full.html](https://www.md2html-tool.com/docs/OpenMobileAlliance/scwg-ETS-conformance-for-Smart-City/Dev/656f03f/ETS/uCIFI-OMA-ETS-Conformance-Smart-City-V1_0-20250416-D_full.html)



## Data Models

Single-phase electrical meter (OMA) Object [#3421](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/3421.xml)

Three-phase electrical meter complement (OMA) Object [#3422](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/3422.xml)

Cabinet Controller Status (OMA) Object [#600](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/600.xml)

Cabinet Controller Manager (OMA) Object [#601](https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/601.xml)

StreetlightControlCabinet (Smart Data Models) Object [#StreetlightControlCabinet](https://github.com/smart-data-models/dataModel.Streetlighting/blob/master/StreetlightControlCabinet/doc/spec.md)

## Mappable information

| OMA Objects                                    | OMA Resources                                   | Smart Data Model Entities | Smart Data Model Properties                            |
| ---------------------------------------------- | ----------------------------------------------- | ------------------------- | ------------------------------------------------------ |
| Location (6)                                   | Latitude (1)                                    | StreetlightControlCabinet | location                                               |
| Location (6)                                   | Longitude (2)                                   | StreetlightControlCabinet | location                                               |
| Single-phase electrical meter (3421)           | Active power export (17)                        | StreetlightControlCabinet | activePowerR<br />activePowerS<br />activePowerT       |
| Single-phase electrical meter (3421)           | Frequency (11)                                  | StreetlightControlCabinet | frequency                                              |
| Single-phase electrical meter (3421)           | Instantaneous Power Factor (13)                 | StreetlightControlCabinet | powerFactorR<br />powerFactorS<br />powerFactorT       |
| Single-phase electrical meter (3421)           | Reactive power export (19)                      | StreetlightControlCabinet | reactivePowerR<br />reactivePowerS<br />reactivePowerT |
| Single-phase electrical meter (3421)           | Voltage (1)                                     | StreetlightControlCabinet | voltageR<br />voltageS<br />voltageT                   |
| Three-phase electrical meter complement (3422) | Active energy export Un (18)                    | StreetlightControlCabinet | energyConsumed                                         |
| Three-phase electrical meter complement (3422) | Reactive energy export Un (22)                  | StreetlightControlCabinet | reactiveEnergyConsumed                                 |
| Three-phase electrical meter complement (3422) | Total active power export on the 3 lines (9)    | StreetlightControlCabinet | totalActivePower                                       |
| Three-phase electrical meter complement (3422) | Total reactive power import on the 3 lines (10) | StreetlightControlCabinet | totalReactivePower                                     |

Cabinet controller mapping may be somehow complex. Various data models have been defined over the years, with different level of details.