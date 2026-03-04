# Power Distribution Network Generation
> PicoRV32a — OpenLANE Physical Design Flow

![Tool](https://img.shields.io/badge/Tool-OpenROAD-blue)
![Tool](https://img.shields.io/badge/Tool-Magic%20VLSI-blue)
![PDK](https://img.shields.io/badge/PDK-Sky130-orange)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen)

<h2>🔍 Overview</h2>

- Generated the Power Distribution Network using `gen_pdn` — power rings, straps, and standard cell rails built across the die to ensure stable power delivery to every cell including the custom inverter sky130_vsdinv.
- Verified via connectivity from power strap down to standard cell rail level — design confirmed ready for signal routing with full power integrity.

<h2>⚙️ Tasks Covered</h2>

| Task | Description |
|:---|:---|
| PDN Generation | Power rings, straps, and standard cell rails built using gen_pdn |
| Power Strap to Cell Verification | Connectivity verified from strap level down to standard cell rails |

<h2>📊 Key Observations</h2>

| Metric | Details |
|:---|:---|
| Tool | OpenROAD, Magic VLSI |
| PDN Command | gen_pdn |
| Power Structure | Rings → Straps → Standard Cell Rails |
| Via Connectivity | Verified at all strap intersections |
| Custom Cell Power | sky130_vsdinv rail connectivity confirmed |
| Output | PDN integrated into picorv32a.def |

<h2>📝 Stage Details</h2>

**Task 1 — Power Distribution Network Generation** &nbsp;|&nbsp; `gen_pdn` `OpenROAD` `Power Rings`

Executed `gen_pdn` — power rings generated around the core boundary for VDD and GND. Power straps laid across the die at regular intervals connecting rings to internal regions. Standard cell rails generated horizontally across all cell rows — VDD and GND rails aligned to Sky130 track grid. Via connectivity verified at all strap-to-ring and strap-to-rail intersections. PDN confirmed complete with no connectivity errors.

**Task 2 — Power Strap to Standard Cell Verification** &nbsp;|&nbsp; `Magic VLSI` `Power Rails`

Verified power delivery path from strap level down to individual standard cell rails. Confirmed VDD and GND rails reach every cell row including rows containing the custom sky130_vsdinv inverter. Metal layer assignments verified — power straps on met4/met5, cell rails on met1/li1. Design confirmed power-complete and ready for signal routing.

<h2>🖼️ Implementation Results</h2>

### Power Distribution Network Generation
![PDN 1](1_Build_power_distribution_network_1.png)
![PDN 2](1_Build_power_distribution_network_2.png)

### Power Strap to Standard Cell Verification
![Strap 1](2_Lab_step_from_power_strap_to_tdc_cell_1.png)

<h2>🔗 Navigation</h2>

[Back to Repository Overview](../README.md) &nbsp;|&nbsp; [Previous : 06 : CTS](../06%20:%20CTS) &nbsp;|&nbsp; [Next : 08 : Routing](../08%20:%20Routing)
