# Public Lighting

##  Service Outcome

### Questions for OMA

- Which existing LwM2M Objects and Resources represent the service outcome?
  - If we limit the service outcome as the illuminance level observed on street, it should be mappable with an Illuminance sensor (3301), providing a Sensor Value (5700) measurement
- How is the distinction maintained between service outcome and infrastructure output?
  - OMA Data Model being implemented by devices normally refers to raw infrastructure output
- How are measured, estimated, inferred, predicted, or aggregated service outcomes represented?
  - OMA Data Model being implemented by devices normally refers to measured values
- How is the observation location represented?
  - Each device may have an associated Location object (6) with geographical position (e.g. 40.4931241,-3.8769922), despite not all device may provide such information
  - Location should be complemented at higher level in a more descriptive and user-friendly way  (e.g. Pl. Mayor, 1, 28231 Las Rozas de Madrid, Madrid, Spain)
- Which additional capabilities, if any, would improve representation of municipality service outcomes?

## Infrastructure Output

### Questions for OMA

- Which existing LwM2M Objects and Resources represent infrastructure output?
  - Infrastructure output is normally related to energy measurements being provided by the Electrical Monitor (3418)
    - Supply voltage (1)
    - Supply current (2)
    - Active Power (4)
    - Power factor (5)
    - Cumulated active energy (6)
    - Dimming Level (35)
- How are operating states represented?
  - The basic state is represented by the Dimming Level (0-100), representing the light level associated with the luminaire
  - In addition, a color temperature could be provided as well
  - Alarms can be provided to identify possible problems (Lamp failure, Control gear failure, ...)
- How are output measurements associated with the corresponding assets?
  - A separate Luminaire Asset (3417) object is provided, containing descriptions being provided by the asset manufacturer (mostly read only)
- Which additional capabilities, if any, would improve representation of infrastructure behaviour?

## Resource Consumption

### Questions for OMA

- Which existing LwM2M Objects and Resources represent resource consumption?
  - Electrical Monitor (3418)
    - Cumulated active energy (6)
    - Reactive energy (30)
    - Apparent Energy (36)
- Can energy, water, fuel, or battery usage be represented consistently?
  - Yes, normally lighting devices are equipped with Control Gears capable of consistently measuring energy consumption as per Zhaga / D4i standard
- Are electrical measurements sufficiently complete for operational efficiency analysis?
  - Yes, normally lighting devices are equipped with Control Gears capable of consistently measuring energy consumption as per Zhaga / D4i standard
- Can resource consumption be associated with the asset, group, cabinet, zone, or service outcome it supports?
  - When performed by the Electrical Monitor it represent a single light point, but similar measurements are provided within the Single Phase Electrical Meter and the Three-Phase Electrical Meter Complement
- Which additional capabilities would improve resource consumption representation?

## Observation Point

### Questions for OMA

- Which existing Objects identify the observation point?
  - The location object provides a way to differentiate the various observation points with great precision, but lack the human readable representation, being limited to lat/lon/alt format
- Can observation points be represented independently from asset identity?
  - The location object is currently associated to the device performing the measurement
- Can multiple observation points be associated with the same infrastructure asset?
  - The mapping shall be possibly done at higher level
- Which additional capabilities would improve observation point representation?
  - A more human readable format / description

## Observation Scope

### Questions for OMA

- Can Objects indicate the operational scope represented by a measurement?
  - Different objects are used for different scopes: Electrical Monitor vs Single Phase Electrical Meter and Three-Phase Electrical Meter Complement
- Can aggregated observations identify the represented assets?
  - The mapping shall be possibly done at higher level
- How is aggregation represented?
  - The mapping shall be possibly done at higher level
- Which additional capabilities would improve scope representation?

## Observation Method

### Questions for OMA

- How are different observation methods represented?
  - Current Data Model is only limited to measured values, when not explicitly stated
- Can measured values be distinguished from inferred values?
  - See above
- Can prediction or simulation results be represented?
  - See above
- Which additional capabilities would improve observation method representation?

## Temporal Semantics

### Questions for OMA

- Which temporal characteristics are currently represented?
  - Each measurement is associated with a timestamp, representing a specific time instant, even when dispatched at a later time
  - Data can be normally provided either periodically or upon meaningful change of any value being monitored
- Can observation intervals remain explicit?
  - If stated in the data model
- Can aggregation periods be represented?
  - If stated in the data model 
- Which additional capabilities would improve temporal semantics?

## Provenance

### Questions for OMA

- Which existing Objects and Resources identify the origin of observations?
  - OMA Data Model being implemented by devices only refers to raw infrastructure output
- Can device-generated information be distinguished from externally supplied information?
  - The mapping shall be possibly done at higher level
- Can provenance remain associated with observations throughout their lifecycle?
  - See above
- Which additional capabilities would improve provenance representation?

## Measurement Quality

### Questions for OMA

- Which quality characteristics can accompany observations?
  - Measurement Quality Indicator (6042)
  - Measurement Quality Level (6049)
- Can confidence or uncertainty be represented?
  - See above
- Can incomplete observations be identified?
  - The device may report only the subset of information that is available
- Which additional capabilities would improve quality representation?

## Operational Context

### Questions for OMA

- Which operational context can be directly observed?
  - Normally limited to electrical line quality (Voltage, Frequency)
  - OMA Data Model also provides coverage for a bunch of environmental measurements
    - Rain Gauge, Anemometer, Humidity, Temperature, Traffic, Heat Stroke
- Can external operational context be associated with observations?
  - The mapping shall be possibly done at higher level
- Which additional capabilities would improve operational context representation?

## Physical Context

### Questions for OMA

- Which physical context can be directly represented?
  - This is indeed not well covered by existing Data Model
- Should physical context be supplied by external systems?
  - The mapping shall be possibly done at higher level
- Which additional capabilities would improve physical context representation?

## Asset Management Context

### Questions for OMA

- Which existing Objects and Resources represent asset management information?
  - Device (3)
  - Device Extension (3410)
  - Outdoor Lamp Controller (3416)
  - Luminaire Asset (3417)
  
  The Outdoor Lamp Controller, in particular, would allow to monitor the lamp operating hours (thus allowing to predict the end of life approaching)
- Which management information belongs within LwM2M Objects?
  - See above
- Which information should remain external to device models?
  - The information should be possibly complemented at higher levels
- Can external asset management information remain associated with device observations?
  - To be managed at higher levels
- Which additional capabilities would improve asset management representation?

## Network Operability

### Questions for OMA

- Which existing Objects and Resources represent communication characteristics?
  - Connectivity Monitoring (4)
  - Connectivity Statistics (7)
  - LPWAN Mesh Connectivity (3447)
  - LPWAN Mesh Statistics (3448)
- Can communication quality be monitored?
  - Yes
- Can communication failures be distinguished from device failures?
  - Communication failures: can be recorded by connectivity statistics
  - Device intrinsic failures: exposed via Error Flag in Device object 3
  - Device external asset failures: exposed via alarm resources in object 3416
- Which additional capabilities would improve representation of network operability?

## Fallback Behaviour

### Questions for OMA

- Which existing Objects and Resources represent fallback behaviour?
  - Manual Override resources in Outdoor Lamp Controller object 3416
- Can autonomous operating modes be represented?
  - Schedule Framework is exactly designed to provide device autonomous operation
- Can transitions between normal and fallback operation be identified?
  - The schedule is active 24/7, so the only possible transiction is a manual override, that would take precedence for a limited amount of time
- Which additional capabilities would improve fallback behaviour representation?
