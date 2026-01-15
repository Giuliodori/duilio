# 5. Board Overview
This chapter provides a visual orientation of the main functional areas on the DUILIO F4 PCB.

## 5.1 Top-side functional blocks
The top side contains the primary user-accessible connectors and most of the high-level functional blocks. When holding the board with the silkscreen readable, the top side highlights the motor control output area, RC input/output headers, and the main communication connectors.

Central area. The control core and surrounding passive components form the logic section. This area is distinct from the edge connectors and keeps short trace runs for signal integrity.

Connector edge. Along the board edge, the external connector groups are organized by function: motor control outputs, RC I/O, general I/O, and communications. These grouped blocks allow quick visual identification when wiring.

USB and service area. The USB connector and service access points are placed near the edge for easy access when the board is installed in an enclosure.

## 5.2 Bottom-side functional blocks
The bottom side carries supporting circuitry, power conditioning components, and secondary headers. These elements are intended to limit fault propagation and improve robustness, not to replace external system-level protections.

Power regulation zone. The input conversion and filtering components are concentrated in one area to keep power routing short and reduce noise.

Secondary headers and test access. Secondary connectors and test pads are distributed along the edges, aligned with the corresponding top-side connector groups.

## 5.3 Logic vs external power separation
The board is laid out to keep logic power and external motor power clearly separated. The logic domain is concentrated around the control core and low-level connectors, while the external power interfaces are routed to the connector edge and power-conditioning area.

This separation reduces coupling from high-current paths and simplifies inspection. When holding the board, the separation is visible as a physical gap between the logic section and the external power section.

## 5.4 Safety-related hardware features
Protection components are grouped near the power entry and the external-facing connectors. This includes current protection on low-power rails and protection elements on exposed interfaces.

Status indication and service access points are placed on the top side for visibility during bring-up and diagnostics. These features allow quick confirmation of board state without probing internal circuitry.
