# Digital VLSI SoC Design & Planning
> RTL-to-GDSII Physical Design Implementation of PicoRV32a RISC-V Processor

![Status](https://img.shields.io/badge/Status-Completed-brightgreen)
![Tool](https://img.shields.io/badge/Tool-OpenLANE-blue)
![PDK](https://img.shields.io/badge/PDK-Sky130-orange)
![Language](https://img.shields.io/badge/Language-Verilog%20HDL-purple)
![Program](https://img.shields.io/badge/Program-NASSCOM%20FutureSkills%20Prime-red)
![License](https://img.shields.io/badge/License-Apache%202.0-blue)

<h2>🔍 Overview</h2>

- Complete **RTL-to-GDSII** physical design implementation of the **PicoRV32a RISC-V processor** using the **OpenLANE** automated EDA flow on the **Google SkyWater 130nm (Sky130)** open-source PDK.

- The project covers the full digital design flow from RTL synthesis through to fabrication-ready GDSII generation — including integration of a **custom-designed standard cell (sky130_vsdinv)**, timing closure via ECOs, and post-route parasitic extraction.

<h2>🛠️ Tools & Technology Stack</h2>

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

<h2>⚙️ Complete Design Flow</h2>

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

<h2>📊 Key Results</h2>

| Metric | Value |
|---|---|
| Design | PicoRV32a RISC-V Processor |
| Technology Node | 130nm (Sky130 PDK) |
| Clock Period | 24.73 ns |
| Clock Frequency | 40.44 MHz |
| Total Cell Count | 17,108 |
| Chip Area | 181,510.33 µm² |
| Die Area | 731.18 × 741.90 µm |
| Core Area | 719.90 × 718.08 µm |
| Metal Layers | 6 — li1, met1, met2, met3, met4, met5 |
| Custom Cell Integrated | sky130_vsdinv (Custom Inverter) |
| Post-Synthesis WNS | 0.00 ns |
| Post-Synthesis TNS | 0.00 ns |
| Routing | Global (FastRoute) + Detailed (TritonRoute) |
| Parasitic Extraction | SPEF extracted post-route |
| DRC Violations | 0 |
| LVS Status | Clean |
| GDSII | Generated — Fabrication Ready |

## 📁Repository Structure
```
📁 Project-DigitalVLSI-SoC-Design-Planning
├── 📁 01 : Synthesis          → RTL synthesis, netlist, cell mapping
├── 📁 02 : Floorplan          → Floorplan, IO placement, Magic layout
├── 📁 03 : Placement          → Congestion-aware placement
├── 📁 04 : Custom cell        → sky130_vsdinv design, SPICE, LEF
├── 📁 05 : Timing closure     → Slack fixing, OpenSTA, ECO
├── 📁 06 : CTS                → CTS run, verification, real clock
├── 📁 07 : PDN                → Power distribution network
├── 📁 08 : Routing            → TritonRoute global and detailed routing
├── 📁 09 : GDSII              → SPEF extraction, final GDSII
└── 📄 README.md
```
<h2>📝 Stage Details</h2>

**01 — Synthesis** &nbsp;|&nbsp; `Yosys` `ABC` `OpenSTA`

RTL synthesised using **Yosys** with technology mapping to Sky130 standard cells via ABC. OpenLANE environment initialised, design hierarchy verified, and synthesis reports analysed for cell utilisation, area, and initial timing slack. Gate-level netlist generated as foundation for physical implementation.
> 📁 [View Implementation Results](./01%20:%20Synthesis)

**02 — Floorplan** &nbsp;|&nbsp; `OpenROAD` `Magic`

Die area and core utilisation defined. Standard cell rows generated and aligned with Sky130 routing tracks. IO pins placed and verified. Layout opened in **Magic** for visual inspection of row orientation, spacing, and pin accessibility.
> 📁 [View Implementation Results](./02%20:%20Floorplan)

**03 — Placement** &nbsp;|&nbsp; `OpenROAD` `RePlAce`

Congestion-aware global placement using **RePlAce**. Standard cells placed and legalised within core area. Placement density and routing resource availability verified before proceeding to CTS.
> 📁 [View Implementation Results](./03%20:%20Placement)

**04 — Custom Standard Cell** &nbsp;|&nbsp; `Magic` `Ngspice` `Sky130`

Custom inverter cell **sky130_vsdinv** designed from scratch in **Magic** following Sky130 DRC rules. SPICE netlist extracted and simulated using **Ngspice**. Timing characterised using Sky130 Liberty files. LEF extracted and integrated into OpenLANE flow — verified post-synthesis and post-CTS.
> 📁 [View Implementation Results](./04%20:%20Custom%20cell)

**05 — Timing Closure** &nbsp;|&nbsp; `OpenSTA` `ECO`

Post-synthesis timing violations identified using **OpenSTA**. Setup slack resolved through synthesis strategy tuning — SYNTH_STRATEGY, SYNTH_BUFFERING, SYNTH_SIZING parameters adjusted. Manual ECOs performed by cell upsizing on critical paths. TNS and WNS verified toward zero before CTS.
> 📁 [View Implementation Results](./05%20:%20Timing%20closure)

**06 — Clock Tree Synthesis** &nbsp;|&nbsp; `TritonCTS` `OpenSTA`

Clock tree built using **TritonCTS**. Clock buffers inserted to balance load and minimise skew across all flip-flops. Buffer drive strength experimented — impact on slew, skew, area, and power analysed. Real clock propagation model applied and hold slack verified post-CTS.
> 📁 [View Implementation Results](./06%20:%20CTS)

**07 — Power Distribution Network** &nbsp;|&nbsp; `OpenROAD` `Magic`

PDN generated using `gen_pdn`. Power rings, straps, and standard cell rails built across die. Via connectivity verified at all strap intersections. Custom inverter rail connectivity confirmed in Magic. Design prepared for signal routing with full power integrity.
> 📁 [View Implementation Results](./07%20:%20PDN)

**08 — Routing** &nbsp;|&nbsp; `FastRoute` `TritonRoute`

Global routing performed using **FastRoute** — approximate paths planned across G-cell grid. Detailed routing completed using **TritonRoute** — exact metal shapes and vias placed with full DRC compliance. Iterative optimisation passes reduced violations to zero.
> 📁 [View Implementation Results](./08%20:%20Routing)

**09 — GDSII Generation** &nbsp;|&nbsp; `SPEF Extractor` `Magic` `Netgen`

Post-route parasitic extraction performed using **SPEF Extractor** — RC wire data generated for all nets. Final sign-off STA executed with real parasitics — setup and hold slack both positive. GDSII streamed out using **Magic** — fabrication-ready layout verified DRC-clean.
> 📁 [View Implementation Results](./09%20:%20GDSII)

<h2>📚 References</h2>

| **Custom Cell Design** | [vsdstdcelldesign by Nickson Jose](https://github.com/nickson-jose/vsdstdcelldesign) |
|:---|:---|
| **PDK** | [Google SkyWater Sky130 PDK](https://github.com/google/skywater-pdk) |
| **EDA Flow** | [OpenLANE by efabless](https://github.com/efabless/openlane) |


<h2>🤝 Connect</h2>

| **Author** | Preetham SK |
|:---|:---|
| **Program** | NASSCOM FutureSkills Prime — VSD (VLSI System Design) |
| **LinkedIn** | [linkedin.com/in/preethamsk16](https://www.linkedin.com/in/preethamsk16) |
| **GitHub** | [github.com/PreethamSK163](https://github.com/PreethamSK163) |
| **Email** | preethamsk163@gmail.com |
