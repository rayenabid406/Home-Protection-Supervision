# Home Electrical Protection & Supervision (Proteus Simulation)

A circuit-level design and simulation for real-time AC voltage/current 
monitoring with automatic overload protection, built and verified in 
**Proteus** (`homeprotectionsupervisionV2.pdsprj`).

> **Note:** This is a simulation/circuit-design project, not a built 
> physical device. It demonstrates the sensing, threshold-detection, and 
> protection logic at the schematic level, verified through Proteus's 
> simulated fault injection rather than on physical hardware.

## What It Does

Monitors AC voltage and current in real time and reacts to two fault 
conditions — overvoltage (OV) and overcurrent (OC) — with both a local 
alert (LCD, LED, buzzer) and an automatic protective action (relay 
disconnects the load).

## System Architecture

```
Voltage: AC line → Step-down transformer → Voltage divider → RC filter → Arduino A0
Current: AC line → ACS712 Hall-effect sensor → Arduino A1
                              │
                    RMS calculation (V, I, P)
                              │
                  Compare against OV/OC thresholds
                    ┌─────────┴─────────┐
                Normal                Fault
                  │                     │
          LCD shows V/I/P      LED + buzzer alert
                              Relay disconnects load
```

## Hardware (as simulated)

| Component | Role |
|---|---|
| Arduino UNO | Processing + decision logic |
| ACS712 | AC current sensing (Hall-effect) |
| Voltage transformer + divider + RC filter | AC voltage sensing, scaled and smoothed for ADC |
| 16x2 LCD | Live voltage/current/power display |
| LEDs + buzzer | OV/OC alert indicators |
| Electromechanical relay | Automatic load disconnection on fault |

## Fault Handling

- **Overvoltage / overcurrent detection**: RMS voltage and current are 
  computed from sampled ADC readings and compared against fixed safety 
  thresholds.
- **Relay trip**: on either fault, the relay opens to disconnect the load 
  before alerting — protection takes priority over notification, since a 
  buzzer with no reaction is worthless if the hardware is already at risk.

## Simulated Verification

- Overvoltage and overcurrent conditions injected in Proteus to confirm 
  detection and relay trip behavior
- Confirmed the RMS calculation tracked expected values under simulated 
  fault conditions

## Screenshots

- `Normal Operation.png` — LCD display under normal voltage/current
- `Auto-open-of-relay-contact-when-OC.png` — relay trip on simulated overcurrent

## Limitations & Next Steps

- Not yet built on physical hardware — real-world ADC noise, transformer 
  ripple, and relay switching transients aren't captured by the simulation
- No datalogging or remote monitoring — planned future direction if this 
  moves to a physical build
- Fixed thresholds only — no calibration routine for different installations

## Stack

Arduino UNO, ACS712, Proteus (schematic capture + simulation)
