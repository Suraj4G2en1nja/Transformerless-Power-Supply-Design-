# Transformerless-Power-Supply-Design- (5V DC)

A compact, 2-layer through-hole PCB for a **5V DC Transformerless Power Supply** designed in KiCad. By using a capacitive dropper front-end paired with a full-wave bridge rectifier and an `LM7805` linear voltage regulator, this board steps down AC mains voltage to a regulated 5V DC output without a bulky step-down transformer.
---
<img width="1228" height="654" alt="transformerless ps" src="https://github.com/user-attachments/assets/dee8ec96-46d3-4f72-91c7-6f35330410b4" />
<img width="553" height="399" alt="image" src="https://github.com/user-attachments/assets/697de37c-8326-4366-a517-1f84aa8f972c" />

## About the Project

This **Transformerless Power Supply** converts an AC input (`J1`) into a regulated **5V DC** output (`J2`). A `2.2µF` (`225k`) film capacitor (`C4`) acts as a capacitive reactance dropper to limit current, while a `1MΩ` bleeder resistor (`R3`) safely discharges `C4` when power is removed. The stepped-down AC is rectified by a `1N4007` full-wave bridge (`D1`–`D4`), smoothed by `1000µF` (`C2`) and `0.1µF` (`C1`) capacitors, clamped via Zener stages (`D5`, `D6`, `R1`, `R2`), and regulated to a steady 5V by an `LM7805` (`U1`) with a `470µF` output filter (`C3`).

### Hardware Specifications
* **Input:** AC Mains via 2-pin 5.08mm screw terminal (`J1`)
* **Output:** Regulated 5V DC via 2-pin 5.08mm screw terminal (`J2`)
* **Regulator:** `LM7805` (TO-220-3 Vertical)
* **Indicators:** 5mm Power LED (`D7`) with `2.2kΩ` current-limiting resistor (`R4`)
* **Board:** 2-Layer PCB (`F.Cu` & `B.Cu`), 1.6 mm thickness, Through-Hole Technology (THT)

### Bill of Materials (BOM)
| Reference | Value / Part | Footprint / Package | Quantity |
| :--- | :--- | :--- | :---: |
| `U1` | LM7805 | TO-220-3 Vertical | 1 |
| `D1`–`D4` | 1N4007 | DO-41 Axial | 4 |
| `D5`, `D6` | Zener Diode | A-405 Axial | 2 |
| `D7` | LED | THT 5.0mm | 1 |
| `C4` | 225k / 2.2µF | Film Rect (`L18.0mm x W6.0mm`, P15.00mm) | 1 |
| `C2` | 1000µF | Radial Electrolytic (`D10.0mm`, P5.00mm) | 1 |
| `C3` | 470µF | Radial Electrolytic (`D10.0mm`, P3.80mm) | 1 |
| `C1` | 0.1µF | Ceramic Disc (`D4.7mm`, P5.00mm) | 1 |
| `R3` | 1MΩ | Axial THT (DIN0207) | 1 |
| `R1`, `R2` | 20kΩ | Axial THT (DIN0207) | 2 |
| `R4` | 2.2kΩ | Axial THT (DIN0207) | 1 |
| `J1`, `J2` | 2-Pin Screw Terminal | Bornier-2 (5.08mm pitch) | 2 |

---

## Applications

* **Low-Power IoT & Home Automation:** Compact 5V auxiliary supply for enclosed smart switches, relays, and sensor nodes.
* **Appliance Control Boards:** Space-constrained embedded controllers where a mains transformer is too large or costly.
* **Indicator & Standby Circuits:** Powering low-current status indicators, timers, and microcontroller logic stages.
* **Educational Use:** Demonstrating capacitive reactance current limiting, full-wave bridge rectification, and linear regulation.

---

## Skills Used

* **Schematic Capture:** Creating an ERC-compliant power supply schematic in KiCad Eeschema.
* **PCB Layout & Routing:** 2-layer component placement, manual trace routing (using 0.5 mm and 1.0 mm trace widths for power paths), and footprint assignment in KiCad Pcbnew.
* **Design Rule Checking (DRC):** Validating clearances, annular rings, and copper-to-edge rules.
* **Power Electronics Design:** Designing capacitive dropper, bleeder, rectification, and linear regulation stages.

---

## Techniques Used in the Project

* **Capacitive Reactance Current Limiting:** Utilizing `C4` (2.2µF) to drop AC mains voltage with minimal heat dissipation compared to purely resistive droppers, paired with `R3` (1MΩ) as a safety bleeder resistor.
* **Multi-Stage Filtering & Regulation:** Combining a `1N4007` bridge rectifier, bulk electrolytic (`1000µF` & `470µF`) and ceramic (`0.1µF`) decoupling, Zener clamping, and an `LM7805` linear regulator for a clean 5V rail.
* **Dual-Layer Ground Plane Pour:** Added `GND` copper zones on both `F.Cu` and `B.Cu` with thermal reliefs to improve thermal dissipation and return paths.
* **Mechanical & Silkscreen Detailing:** Included 4 corner mounting holes on `Edge.Cuts`, clear `AC` / `DC` terminal labels, custom `Ampnics` silkscreen branding/logo on `F.SilkS`, and a KiCad logo on `B.SilkS`.

---

## Repository Structure

```text
├── Transformerless power supply.kicad_pro   # KiCad project configuration
├── Transformerless power supply.kicad_sch   # Schematic file
├── Transformerless power supply.kicad_pcb   # 2-layer PCB layout
└── Transformerless power supply.kicad_prl   # KiCad project local settings
