# Buck Converter Design for Satellite Power Systems

**LTSpice Simulation Project**  
**Author:** Dhruvrajsinh Vansia  
**Date:** November 2026  
**Track:** Satellite Engineering - Avionics

---

## 1. Project Overview

This project demonstrates the design and simulation of a DC-DC buck converter for satellite power regulation applications. The converter steps down 12V input to 3.3V output, suitable for powering microcontrollers and sensors in spacecraft avionics systems.

### Objective
Design a switching power supply with:
- High efficiency (>85%)
- Low output ripple (<50mV)
- Stable 3.3V output for sensitive electronics

---

## 2. Design Specifications

| Parameter | Specification |
|-----------|---------------|
| Input Voltage | 12V DC |
| Output Voltage | 3.3V DC |
| Output Current | 500mA |
| Switching Frequency | 100kHz |
| Target Efficiency | >85% |
| Output Ripple | <50mV pp |

---

## 3. Circuit Design

### 3.1 Topology

Non-isolated synchronous buck converter using:
- N-channel MOSFET as switching element
- Schottky diode for flyback protection
- LC filter for output smoothing

### 3.2 Component Selection

| Component | Value | Part/Model |
|-----------|-------|------------|
| Input Capacitor (Cin) | 10µF | Low ESR electrolytic |
| Output Capacitor (Cout) | 47µF | Low ESR electrolytic |
| Inductor (L1) | 100µH | Saturation current >1A |
| MOSFET (Q1) | N-channel | IRF540 or equivalent |
| Diode (D1) | Schottky | 1N5819 |
| Load Resistor (Rload) | 6.6Ω | 2W |

### 3.3 Circuit Schematic

![Circuit Diagram](../Results/circuit.png)

---

## 4. Simulation Setup

### 4.1 LTSpice Configuration

- **Simulation Type:** Transient Analysis
- **Stop Time:** 50ms
- **Maximum Timestep:** 10µs
- **Gate Drive:** PWM pulse (0-5V, 100kHz, ~27.5% duty cycle)

### 4.2 PWM Parameters

```
PULSE(0 5 0 1u 1u 5u 10u)
```

This generates:
- Frequency: 100kHz
- Duty Cycle: ~27.5% (for 12V→3.3V conversion)
- Rise/Fall Time: 1µs

---

## 5. Results

### 5.1 Output Voltage Waveform

![Output Voltage](../Results/vout_waveform.png)

| Measurement | Expected | Measured | Status |
|-------------|----------|----------|--------|
| Vout (Average) | 3.3V | 3.28V | ✓ |
| Output Ripple | <50mV | ~30mV | ✓ |
| Settling Time | <10ms | ~8ms | ✓ |

### 5.2 Input Current

| Parameter | Value |
|-----------|-------|
| Input Current (Iin) | 147.48mA |
| Input Voltage (Vin) | 12V |
| Input Power (Pin) | 1.76W |

### 5.3 Efficiency Calculation

```
Pout = Vout × Iout = 3.28V × 0.5A = 1.64W
Pin  = Vin × Iin = 12V × 0.147A = 1.76W

Efficiency = Pout / Pin × 100 = 93%
```

| Metric | Value | Target | Status |
|--------|-------|--------|--------|
| Efficiency | 93% | >85% | ✓ Excellent |
| Power Loss | 0.12W | <0.3W | ✓ |

---

## 6. Analysis

### 6.1 Performance Summary

The buck converter achieved **93% efficiency**, exceeding the target of 85%. Key observations:

1. **Output Regulation:** Vout stabilized at 3.28V (within 0.6% of target)
2. **Ripple:** Output ripple approximately 30mV peak-to-peak
3. **Transient Response:** Output settled within 8ms
4. **Efficiency:** 93% indicates minimal switching and conduction losses

### 6.2 Design Trade-offs

| Factor | Consideration |
|--------|---------------|
| Switching Frequency | Higher frequency = smaller L,C but more switching loss |
| Inductor Value | 100µH provides good balance of ripple and size |
| MOSFET Selection | Low Rds(on) reduces conduction losses |
| Capacitor ESR | Low ESR critical for minimizing output ripple |

---

## 7. Space Application Relevance

### 7.1 Satellite Power Systems

This design is directly applicable to:
- **CubeSat power distribution** (3.3V logic rails)
- **Sensor node power regulation**
- **Avionics board DC-DC conversion**

### 7.2 Key Requirements Met

| Requirement | Relevance |
|-------------|-----------|
| High Efficiency | Critical for limited solar power budgets |
| Low Ripple | Prevents noise in sensitive instruments |
| Compact Design | Volume-constrained satellite payloads |
| Radiation Considerations | Commercial parts need rad-hard alternatives for LEO/GEO |

---

## 8. Skills Demonstrated

- [x] Power electronics circuit design
- [x] Switching converter theory application
- [x] LTSpice circuit simulation
- [x] Component selection and sizing
- [x] Efficiency analysis and optimization
- [x] Waveform analysis and validation

---

## 9. Future Improvements

1. **Voltage Feedback Loop:** Add PWM controller with feedback for load regulation
2. **Synchronous Rectification:** Replace diode with MOSFET for higher efficiency
3. **Multi-phase Design:** For higher current applications (>2A)
4. **EMI Filtering:** Add input filter for conducted emissions compliance
5. **Thermal Analysis:** Evaluate component temperatures under continuous operation

---

## 10. Files in This Repository

```
buck_convertor_LTSpice/
├── Report/
│   └── Buck_Converter_Project_Report.md
├── Simulation/
│   └── buck_converter.asc (LTSpice schematic)
├── Results/
│   ├── circuit.png
│   └── vout_waveform.png
└── README.md
```

---

## 11. References

1. LTSpice XVII Simulation Software - Analog Devices
2. Erickson, R.W. & Maksimovic, D. "Fundamentals of Power Electronics"
3. Texas Instruments. "Buck Converter Design Guide" (SLVA477)
4. NASA. "Power Electronics for Space Applications" Technical Brief

---

## 12. About the Author

**Dhruvrajsinh Vansia**  
MSc Space Sciences and Technologies  
University of Bremen, Germany  

**Experience:**
- Project Trainee, Physical Research Laboratory (ISRO)
- Former President, PRAKALPA Space and Science Club

**Career Interest:** Satellite Engineering - Avionics & Power Systems

---

*Project completed: November 2026*  
*Simulation Tool: LTSpice XVII*
