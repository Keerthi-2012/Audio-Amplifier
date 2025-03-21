# Audio Amplifier

## Overview
This project implements a multi-stage audio amplifier designed to provide high-quality audio amplification with minimal distortion. The amplifier is specifically designed for the audible frequency range (20Hz to 20kHz) with a total gain of 500 and output power of 1.5W.

## Specifications
- **Supply Voltage:** 0 to 5V
- **Input Signal:** 10-40mV (peak-to-peak)
- **Total System Gain:** 500 (Pre-amp and Gain stage)
- **Frequency Response:** 20Hz to 20kHz (Audible Range)
- **Output Power:** 1.5W
- **Load Impedance:** 10Ω
- **Filter Design:** Non-attenuating for input signal
- **Power Amplifier:** No voltage gain (only current/power gain)

## Architecture

The amplifier consists of four main stages:

1. **Pre-amplifier Stage**
2. **Main Gain Stage**
3. **Filter Stage**
4. **Power Amplifier Stage**

### 1. Pre-amplifier Stage
A common-emitter differential amplifier providing:
- High input impedance to prevent loading the microphone
- Good noise rejection capability
- Initial voltage amplification
- CMRR (Common-Mode Rejection Ratio) optimization

#### Implementation Details:
- Two NPN BJTs in active mode configuration
- Differential inputs with options for single-ended or differential operation
- Biasing with current source using resistor network
- Input and output impedance carefully calibrated

### 2. Gain Stage
A Common Emitter (CE) amplifier providing:
- Majority of the voltage gain
- AC coupling to block DC components
- Biasing for optimal transistor operation

#### Implementation Details:
- Input capacitor (C₁) for DC blocking
- Output capacitor (C₂) for AC coupling to next stage
- Biasing resistors (RB₁, RB₂) forming voltage divider
- Stability factor optimization for minimal thermal runaway risk

### 3. Filter Stage
An active bandpass filter:
- Ensures only the audible frequency range passes through
- Minimizes harmonic distortion
- Provides buffer between gain and power stages

#### Implementation Details:
- Active low-pass filter configuration
- Cutoff frequency set above 20kHz
- Components selected for minimal phase distortion

### 4. Power Amplifier
A Class AB power amplifier:
- Provides necessary current gain to drive 10Ω load
- 1.5W output power capability
- Minimal crossover distortion
- No voltage gain (as specified)

#### Implementation Details:
- Complementary NPN and PNP transistors
- Biasing resistors (R₁, R₂, RB₁, RB₂) for proper class AB operation
- Capacitive coupling (C₁, C₂) to minimize base current
- Symmetrical design for balanced operation

## Performance Analysis

### Total Harmonic Distortion (THD)
- Calculated using FFT analysis
- Formula: THD = √(∑Vₙ_RMS²)/Vf_RMS
- Minimization techniques:
  - Proper biasing of all transistor stages
  - Filtering of higher harmonics
  - RC filtering network optimization

### Slew Rate
- Defines maximum output voltage change rate
- Critical for accurate reproduction of high-frequency signals
- Optimization achieved through:
  - Minimizing capacitive impedances
  - Proper bias current selection
  - Component selection for high-frequency operation

### Required Tools
1. Circuit simulation software (LTspice)
2. Digital Storage Oscilloscope and function generator for testing
3. Multimeter for basic measurements

### Build Process
1. Verify individual stage operations using simulation
2. Assemble and test pre-amplifier stage
3. Add gain stage and verify combined performance
4. Integrate filter stage and test frequency response
5. Add power amplifier stage and verify full system performance
6. Measure and optimize for THD and slew rate

## Testing Procedures
1. DC operating point verification
2. Gain and frequency response measurement
3. THD measurement at different frequencies
4. Power output measurement
5. Temperature stability testing
6. Slew rate measurement


Achieved a total gain of 450 and operated effectively in the frequency range of 100 Hz to 15 kHz. Supported an input voltage range of 10-20mV peak-to-peak (Vpp).Delivered an output power of 1.5W, operating with a power supply of ±5V
