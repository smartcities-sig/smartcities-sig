## Smart Lighting: mapping between OMA LwM2M Objects and FIWARE Smart Data Models

**Reference Document**
[https://groups.io/g/smartcities-sig/files/Discussion/2026/20260513-especificacion%20de%20caso%20de%20uso%20lighting%20v0.1.docx](https://groups.io/g/smartcities-sig/files/Discussion/2026/20260513-especificacion de caso de uso lighting v0.1.docx)


**Quantities to be measured**

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



**Measurement conditions**

- In each luminaire with Zagha connector
- At the head of the line (show how many luminaires are on it)
- Type of lighting fixtures (pedestrian zone or vehicles)



**Data Models**


Outdoor Lamp Controller (OMA)
https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/3416.xml

Electrical Monitor (OMA)
https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/3418.xml

Street Light (Smart Data Models)
https://github.com/smart-data-models/dataModel.Streetlighting/blob/master/Streetlight/doc/spec.md



**Mappable information**

| OMA                                                | FIWARE                   |
| -------------------------------------------------- | ------------------------ |
| Latitude (6/1) Longitude (6/2)                     | location                 |
| Command in action (3416/2) Dimming level (3418/35) | powerState               |
| Timestamp (3418/5518)                              | observationDateTime      |
| Active power (3418/4)                              | powerConsumtpion         |
| Cumulated active energy (3418/6)                   | lifetimePowerConsumption |
| Power factor (3418/5)                              | powerFactor              |
| Supply current (3418/2)                            | current                  |
| Supply voltage (3418/1)                            | voltage                  |
| Lamp ON timestamp                                  | dateLastSwitchingOn      |
| Actual light color temperature (3416/40)           | *TODO*                   |
| *TODO*                                             | dateLastSwitchingOff     |
| *TODO*                                             | illuminanceLevel         |



It seems there is no possibility of control over dimming, but that could be absolutely acceptable. This also explains why the vast majority of the resources are related to the Electrical Monitor (3418) and not to the Outdoor Lamp Controller (3416)
The nominal lamp output in lumen at 100% dimming should be added to the OMA Data Model
The color temperature is not currently present in the Smart Data Model



**Tests**
https://github.com/OpenMobileAlliance/scwg-ETS-conformance-for-Smart-City/blob/Dev/ETS/uCIFI-Test-Cases-Smart-Lighting.md



**Data Models**

Single-phase electrical mete (OMA)
https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/3421.xml

Three-phase electrical meter complement (OMA)
https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/3422.xml

Cabinet Controller Status (OMA)
https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/600.xml

Cabinet Controller Manager (OMA)
https://github.com/OpenMobileAlliance/lwm2m-registry/blob/prod/601.xml

StreetlightControlCabinet (Smart Data Models)
https://github.com/smart-data-models/dataModel.Streetlighting/blob/master/StreetlightControlCabinet/doc/spec.md



**Mappable information**

| OMA                                                  | FIWARE                                                 |
| ---------------------------------------------------- | ------------------------------------------------------ |
| Latitude (6/1) Longitude (6/2)                       | location                                               |
| Active power export (3421/x/17)                      | activePowerR<br />activePowerS<br />activePowerT       |
| Active energy export Un (3422/18)                    | energyConsumed                                         |
| Frequency (3421/11)                                  | frequency                                              |
| Instantaneous Power Factor (3421/x/13)               | powerFactorR<br />powerFactorS<br />powerFactorT       |
| Reactive energy export Un (3422/22)                  | reactiveEnergyConsumed                                 |
| Reactive power export (3421/x/19)                    | reactivePowerR<br />reactivePowerS<br />reactivePowerT |
| Total active power export on the 3 lines (3422/9)    | totalActivePower                                       |
| Total reactive power import on the 3 lines (3422/10) | totalReactivePower                                     |
| Voltage (3421/x/1)                                   | voltageR<br />voltageS<br />voltageT                   |

Cabinet controller mapping may be somehow complex. Various data models have been defined over the years, with different level of details.