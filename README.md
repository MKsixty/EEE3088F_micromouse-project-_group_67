# EEE3088F_micromouse-project-_group_67

Overview

This repository contains the design files, documentation, and testing results for the sensor subsystem of a Micromouse robot, developed as part of the EEE3088F course at the University of Cape Town. The sensor board is designed as a custom PCB inspired by the UCLA Micromouse project but tailored through specific design decisions to meet project requirements and ensure optimal performance. Its primary role is to provide reliable wall detection on the front, left, and right sides of the Micromouse to enable autonomous maze navigation.

Design Summary

Emitters & Detectors: Uses IR333C infrared LEDs and TEFT4300 phototransistors, chosen for their closely matched wavelength (≈940 nm) for fast response and accurate detection.

Emitter Circuit: Powered by the 3.7 V LiPo battery, with 47 Ω current-limiting resistors ensuring ~70 mA drive for strong radiant intensity. 4.7 μF bypass capacitors filter noise on the LED supply.

Switching: Implemented with MMBF170 N-channel MOSFETs driven by STM32L476 PWM GPIOs. Gate resistors (100 Ω) and pulldowns (47 kΩ) ensure safe and stable operation.

Receiver Circuit: Uses a voltage divider (470 Ω & 1.5 kΩ) to keep outputs <3.3 V for STM32 ADC compatibility. A unity-gain buffer with LM324 op-amp protects ADC inputs from noise and spikes.

Form Factor: PCB dimensions ≤70 mm × 30 mm, cost-effective, and compatible with standard JLCPCB manufacturing limits.

Failure Management: Includes test points, through-hole components for easy rework, and jumper options to adjust resistor networks if needed.

Features

Accurate wall detection at up to 15 cm.

PWM-controlled IR switching for power efficiency.

Designed for direct integration with the STM32L476 processor board via a 14×2 pin header.

Supports three independent sensor channels (front, left, right).

Repository Contents

PCB design files and schematics.

Component datasheets (IR333C, TEFT4300, LM324, MOSFETs).

Integration code for STM32L476 (sensor readout and PWM control).

Project report, test logs, and acceptance test procedures.

Testing

The board underwent short-circuit checks, current consumption tests, PWM switching validation, and functional wall-detection tests. Issues such as LED orientation errors and interference between sensors were identified and mitigated using jumper reconfiguration and potential PWM timing adjustments in firmware.

Future Improvements

Implement time-multiplexed PWM driving to reduce crosstalk between sensors.

Optimize current draw to meet <100 mA power efficiency target.

Explore improved ADC filtering for cleaner sensor output.
