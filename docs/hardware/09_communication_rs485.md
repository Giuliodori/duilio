# 9. Communication Interfaces

This chapter describes the public hardware-facing communication interfaces of DUILIO F4.
It does not publish private protocol implementation details.

## 9.1 Public communication paths

The board can participate in a system through several hardware-facing paths:

- USB for bench setup, service, and configuration workflows
- host-side serial connection for embedded controllers such as Raspberry Pi
- RS485 for distributed node topologies
- I2C for supported short-distance peripherals

The actual operational role of each interface depends on the selected firmware profile and integration strategy.

## 9.2 RS485 overview

RS485 is the preferred public field-bus style interface when multiple boards or remote nodes must share a differential communication link in a noisy environment.

Public integration rules:

- use twisted pair for A and B
- keep a common ground reference between nodes
- terminate according to topology and cable length
- avoid star wiring with long branches

## 9.3 RS485 installation notes

RS485 mistakes that commonly cause failures include:

- missing shared ground
- swapped A/B lines
- duplicate termination at multiple points
- no termination where the topology requires it
- routing the bus close to high-current switching paths without care

RS485 signal lines are not power lines.
Do not inject external voltage into them.

## 9.4 Host serial connection

DUILIO F4 provides a host-side serial path intended for direct integration with devices such as Raspberry Pi or other embedded hosts.
This path should be wired with the correct TX/RX orientation and a valid common reference.

Practical rules:

- verify TX and RX are crossed correctly
- confirm logic-level compatibility
- do not confuse serial pins with the 5 V power path
- review the power tree separately from the communication wiring

## 9.5 I2C overview

The board includes public I2C connector groups for supported peripherals and sensor integrations.
These buses are intended for short-distance logic-level communication.

Practical rules:

- keep cable length short
- verify device voltage compatibility
- avoid excessive pull-up duplication
- maintain a clean shared ground reference

## 9.6 Public documentation scope

This manual documents the electrical-facing integration view only.
Detailed message structure, firmware-side protocol logic, and private implementation notes are intentionally excluded from the public repository.
