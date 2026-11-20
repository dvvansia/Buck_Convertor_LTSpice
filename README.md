# Buck Converter LTSpice Simulation

DC-DC Buck Converter design for satellite power systems, simulated in LTSpice.

## Project Overview

This project demonstrates a 12V to 3.3V buck converter design suitable for spacecraft avionics power regulation. The simulation achieves **93% efficiency** with low output ripple.

## Specifications

| Parameter | Value |
|-----------|-------|
| Input Voltage | 12V DC |
| Output Voltage | 3.3V DC |
| Output Current | 500mA |
| Switching Frequency | 100kHz |
| Efficiency | 93% |

## Features

- High-efficiency switching power supply design
- Low output ripple (<50mV pp)
- Suitable for satellite/cubeSat power systems
- Complete LTSpice simulation files
- Technical report with analysis

## Files

- `Simulation/buck_converter.asc` - LTSpice schematic file
- `Report/Buck_Converter_Project_Report.md` - Full technical report
- `Results/` - Simulation output waveforms and circuit diagrams

## Quick Start

1. Open `Simulation/buck_converter.asc` in LTSpice
2. Click the "Run" button (green triangle) or press F8
3. Probe nodes to view waveforms (click on Vout, Vin, etc.)

## Requirements

- LTSpice XVII (free download from Analog Devices)
  - Download: https://www.analog.com/en/design-center/design-tools-and-calculators/ltspice-simulator.html

## Results Summary

| Measurement | Expected | Measured |
|-------------|----------|----------|
| Output Voltage | 3.3V | 3.28V |
| Efficiency | >85% | 93% |
| Output Ripple | <50mV | ~30mV |

## Applications

- CubeSat power distribution systems
- Sensor node power regulation
- Avionics board DC-DC conversion
- Embedded systems power supply

## Author

**Dhruvrajsinh Vansia**  
MSc Space Sciences and Technologies  
University of Bremen, Germany

## License

This project is for educational purposes. Feel free to use and modify for learning.

---

*Project Date: November 2026*
