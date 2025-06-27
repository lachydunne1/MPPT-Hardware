# MPPT Hardware Module

This repository documents the design and usage of a custom-built Maximum Power Point Tracking (MPPT) hardware system. It is designed to optimise energy harvesting from solar panels or other variable power sources into a battery or power management system.

## Features

- **Input Voltage Range:** Up to 48 V
- **Output Current:** ~10 A
- **Switching Frequency:** ~100 kHz
- **Converter Topology:** Buck
- **Microcontroller:** ESP32
- **Gate Driver:** IRS2184
- **MPPT Algorithm:** Perturb & Observe (P&O)
- **Protection:** PTC Resettable Fuse, Overvoltage, Undervoltage, Reverse Polarity
- **Monitoring:** I²C/SPI/ADC-ready headers for sensor integration
- **Thermal Design:** Ground pour, compact layout, lots of thermal vias

## Board Layout

- Power stage on **top layer** (inductor, MOSFETs, etc.)
- Low-power control circuitry on **bottom layer*
- **Isolated ground plane** between top and bottom layers
- Screw mounts mechanically isolated or grounded as required

## Installation

1. Solder all components as per the schematic and BOM.
2. Flash ESP32-s3 devboard with your MPPT control firmware, or firmware available from one of my repos.
3. Connect input (solar panel) and output (battery/load).
4. Use a serial monitor or dashboard to observe telemetry.

## Usage

- Ensure input voltage is within design limits.
- Tune MPPT loop parameters if using custom firmware.
- Monitor system temperatures—add heatsinking if operating near thermal limits.

## Notes

- Thermal performance is limited by the SOT-23-6 package used (LMR51610).
- Max output current is regulated by design—not continuous current capability of the IC.
- Consider upgrading to a higher power topology if output current requirements grow.

- Testing has not yet been completed. This PCB is the first after initial breadboard prototype.

## License

MIT License – See [LICENSE](LICENSE) file for details.
