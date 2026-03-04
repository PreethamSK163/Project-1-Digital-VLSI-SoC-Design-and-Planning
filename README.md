# Digital VLSI SoC Design & Planning
> RTL-to-GDSII Physical Design Implementation of PicoRV32a RISC-V Processor

![Status](https://img.shields.io/badge/Status-Completed-brightgreen)
![Tool](https://img.shields.io/badge/Tool-OpenLANE-blue)
![PDK](https://img.shields.io/badge/PDK-Sky130-orange)
![Language](https://img.shields.io/badge/Language-Verilog%20HDL-purple)
![Program](https://img.shields.io/badge/Program-NASSCOM%20FutureSkills%20Prime-red)

---

## Overview

Complete **RTL-to-GDSII** physical design implementation of the **PicoRV32a RISC-V processor** using the **OpenLANE** automated EDA flow on the **Google SkyWater 130nm (Sky130)** open-source PDK.

The project covers the full digital design flow from RTL synthesis through to fabrication-ready GDSII generation — including integration of a **custom-designed standard cell (sky130_vsdinv)**, timing closure via ECOs, and post-route parasitic extraction.

---

## Tools & Technology Stack

| Category | Tool / Technology |
|---|---|
| Flow Manager | OpenLANE |
| PDK | Sky130 (sky130A) |
| Design | PicoRV32a RISC-V Core |
| Synthesis | Yosys + ABC |
| Static Timing Analysis | OpenSTA |
| Placement & CTS | OpenROAD, TritonCTS |
| Routing | TritonRoute |
| Layout & DRC | Magic VLSI |
| Parasitic Extraction | SPEF Extractor |
| SPICE Simulation | Ngspice |
| LVS | Netgen |
| HDL | Verilog |
| OS | Ubuntu Linux |

---

## Complete Design Flow

| Stage | Tool | Description | Status |
|---|---|---|---|
| RTL Synthesis | Yosys + ABC | Verilog → gate-level netlist, cell mapping | ✅ Complete |
| Floorplan & Power | OpenROAD | Die area, core utilisation, IO placement | ✅ Complete |
| Placement | OpenROAD | Standard cell placement, congestion optimisation | ✅ Complete |
| Custom Cell Design | Magic, Ngspice | sky130_vsdinv — layout, SPICE, LEF extraction | ✅ Complete |
| Timing ECO | OpenSTA | Setup/hold fixing, cell upsizing, slack closure | ✅ Complete |
| Clock Tree Synthesis | TritonCTS | Clock insertion, skew minimisation, buffer sizing | ✅ Complete |
| Power Distribution | OpenROAD | PDN — rings, straps, standard cell rails | ✅ Complete |
| Routing | TritonRoute | Global + detailed routing, DRC compliance | ✅ Complete |
| Parasitic Extraction | SPEF Extractor | Post-route RC parasitics for sign-off STA | ✅ Complete |
| Sign-off STA | OpenSTA | Setup and hold verified with real clock model | ✅ Complete |
| GDSII Generation | Magic | Final layout — fabrication ready | ✅ Complete |

---

## Key Results

| Metric | Value |
|---|---|
| Design | PicoRV32a RISC-V Processor |
| Technology Node | 130nm (Sky130 PDK) |
| Custom Cell Integrated | sky130_vsdinv (Custom Inverter) |
| Routing | Global (FastRoute) + Detailed (TritonRoute) |
| Parasitic Extraction | SPEF extracted post-route |
| DRC Violations | 0 |
| LVS Status | Clean |
| GDSII | Generated — Fabrication Ready |

---

## Repository Structure
```
📁 Project-DigitalVLSI-SoC-Design-Planning
│
├── 📁 synthesis          → RTL synthesis, netlist, cell mapping screenshots
├── 📁 floorplan          → Floorplan, IO placement, Magic layout screenshots
├── 📁 placement          → Congestion-aware placement screenshots
├── 📁 custom-cell        → sky130_vsdinv design, SPICE, LEF, characterisation
├── 📁 timing-closure     → Slack fixing, OpenSTA analysis, ECO screenshots
├── 📁 cts                → CTS run, verification, real clock analysis screenshots
├── 📁 pdn                → Power distribution network screenshots
├── 📁 routing            → TritonRoute global and detailed routing screenshots
├── 📁 gdsii              → Post-route STA, SPEF extraction, final GDSII screenshots
└── 📄 README.md
```

---

## Stage Highlights

### 1. Synthesis
RTL synthesised using Yosys with technology mapping to Sky130 standard cells via ABC. Synthesis reports analysed for cell utilisation, area, and initial timing slack.

![Synthesis](./synthesis/3_Logic_Synthesis_and_Functional_Mapping_1.png)

### 2. Floorplan
Die area defined, IO pins placed, standard cell rows aligned with Sky130 routing tracks. Layout verified in Magic.

![Floorplan](./floorplan/3_Review_floorplan_layout_in_magic_1.png)

### 3. Placement
Congestion-aware placement using RePlAce. Cell density and routing resources verified before CTS.

![Placement](./placement/4_Congestion_aware_placement_using_RePIAce_1.png)

### 4. Custom Standard Cell — sky130_vsdinv
Custom inverter designed from scratch in Magic, simulated with Ngspice, characterised using Sky130 timing libraries, and integrated into the OpenLANE flow via LEF extraction.

![Custom Cell](./custom-cell/4_Lab_step_to_creat_std_layout_1.png)

### 5. Timing Closure
Setup violations resolved through synthesis parameter tuning, manual ECOs, and cell upsizing. OpenSTA used for detailed path analysis.

![Timing ECO](./timing-closure/7_Basic_timing_eco_1.png)

### 6. Clock Tree Synthesis
TritonCTS built the clock distribution network. Buffer sizing optimised for PPA trade-off. Real clock timing verified with propagated clock model.

![CTS](./cts/8_Lab_steps_to_run_CTS_using_Triton_CTS_1.png)

### 7. Power Distribution Network
PDN generated with power rings, straps, and standard cell rails. Custom inverter power connectivity verified in Magic.

![PDN](./pdn/1_Build_power_distribution_network_1.png)

### 8. Routing
Global and detailed routing completed using TritonRoute. DRC-clean routing achieved after iterative optimisation passes.

![Routing](./routing/3_Basics_of_global_and_detail_routing_and_configure_TritonRoute_1.png)

### 9. GDSII Generation
Post-route SPEF extracted, final STA verified with real RC parasitics. GDSII generated using Magic — fabrication ready.

![GDSII](./gdsii/4_Post_Route_Parasitic_Extraction_and_Final_GDSII_Generation_6.png)

---

## About

This project was completed as part of the **NASSCOM FutureSkills Prime** program on advanced VLSI physical design using industry-standard open-source EDA tools.

| | |
|---|---|
| **Author** | Preetham SK |
| **Program** | NASSCOM FutureSkills Prime |
| **Institution** | Vellore Institute of Technology, Chennai |
| **Email** | preethamsk163@gmail.com |
| **LinkedIn** | [linkedin.com/in/preethamsk16](https://www.linkedin.com/in/preethamsk16) |
| **GitHub** | [github.com/PreethamSK163](https://github.com/PreethamSK163) |
