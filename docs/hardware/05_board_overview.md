# 5. Board Overview

This chapter provides a user-facing orientation of the main functional areas on the DUILIO F4 PCB.
It is intended to help identify connector groups and installation-relevant zones without exposing the complete private design package.

## 5.1 Top-side functional blocks
The top side contains the user-facing connector groups and the most frequently accessed service points.

Main areas visible from the top side:

- control and logic core around the MCU section
- motor driver control connectors
- RC input and RC output areas
- host and service access, including USB and SWD
- field I/O and communication connectors

This grouping is intended to reduce wiring errors and make installation easier when the board is mounted in an enclosure or machine frame.

## 5.2 Bottom-side functional blocks
The bottom side carries supporting circuitry, power-conditioning sections, and secondary elements related to distribution, filtering, and board service.

These areas support robustness and integration, but they do not replace correct external protection, current limiting, or machine-level safety measures.

## 5.3 Logic vs external power separation
The layout keeps logic and field interfacing clearly separated from external motor power.
This is a key architectural point of DUILIO F4:

- the board generates and supervises control signals
- external drivers generate motor power
- motor current must not be routed through the board

This separation improves inspection, integration clarity, and noise management in real installations.

## 5.4 Safety-related hardware features
Protection-related components are concentrated near power entry and user-facing interfaces.
These include rail protection, interface protection, and service-oriented access points used during commissioning and troubleshooting.

Status indication and service access are intentionally exposed so the integrator can verify board state without relying on hidden test fixtures.

## 5.5 Mechanical drawing and dimensions

The following drawing provides overall dimensions and mounting references for enclosure design and mechanical integration.

![DUILIO F4 mechanical drawing](../images/duilio_f4_drawing.svg)
