
# 01 : Synthesis
> RTL to Gate-Level Netlist — PicoRV32a on Sky130 PDK

![Tool](https://img.shields.io/badge/Tool-Yosys-blue)
![Tool](https://img.shields.io/badge/Tool-ABC-blue)
![PDK](https://img.shields.io/badge/PDK-Sky130-orange)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen)

<h2>🔍 Overview</h2>

- Initialised the **OpenLANE** environment with the **SkyWater 130nm PDK (sky130A)** and prepared the `picorv32a` design for RTL-to-GDSII flow.
- Performed **logic synthesis** using Yosys and ABC — converting behavioural Verilog into an optimised gate-level netlist mapped to Sky130 standard cells.

<h2>⚙️ Tasks Covered</h2>

| Task | Description |
|:---|:---|
| PDK & Directory Setup | Explored sky130A libs.ref and libs.tech structure |
| Design Preparation | Merged Technology LEF and Cell LEFs, initialised runs directory |
| Logic Synthesis | RTL → gate-level netlist using Yosys |
| Technology Mapping | Optimised cell mapping using ABC with sky130_fd_sc_hd library |
| Synthesis Analysis | Cell count, chip area, flop ratio, critical path analysis |

<h2>📊 Key Observations</h2>

| Metric | Details |
|:---|:---|
| Design | PicoRV32a RISC-V Processor |
| Standard Cell Library | sky130_fd_sc_hd (High Density) |
| Metal Layers Verified | 6 layers — li1 through met5 |
| Gate-Level Netlist | Generated — picorv32a.synthesis.v |
| Flop Ratio | ~10–15% (balanced pipelined architecture) |

<h2>📝 Stage Details</h2>

**Task 1 — PDK Directory Structure** &nbsp;|&nbsp; `sky130A` `libs.ref` `libs.tech`

Explored the SkyWater 130nm PDK organisation. Studied `libs.ref` for timing (`.lib`), abstract layout (`.lef`), and geometric layout (`.gds`, `.mag`). Studied `libs.tech` for tool-specific configurations. Verified the `sky130_fd_sc_hd` standard cell library hierarchy.

**Task 2 — Design Preparation** &nbsp;|&nbsp; `OpenLANE` `prep` `LEF Merge`

Initialised OpenLANE Docker environment and started interactive Tcl session. Executed `prep` command — merged Technology LEF and Cell LEFs into a unified file. Confirmed timestamped runs directory created. Verified clock period overrides and target density in config.tcl. All 6 metal layers confirmed active.

**Task 3 — Logic Synthesis & Functional Mapping** &nbsp;|&nbsp; `Yosys` `ABC` `sky130_fd_sc_hd`

Converted RTL Verilog to gate-level netlist using Yosys. ABC performed technology mapping and logic minimisation — redundant gates removed, drive strengths optimised. All cells sourced from sky130_fd_sc_hd library. Synthesis statistics report generated — cell types, total count, and chip area verified.

**Task 4 — Characterising Synthesis Results** &nbsp;|&nbsp; `OpenSTA` `Timing Reports`

Gate-level netlist verified in results/synthesis/. Flop ratio calculated — sequential vs combinational logic density confirmed balanced. Pre-layout STA performed — setup slack positive, confirming design meets target clock frequency. Critical path identified for future ECO planning.

<h2>🖼️ Implementation Results</h2>

### PDK Directory Structure
![Directory 1](1_Directory_structure_and_%20details_1.png)
![Directory 2](1_Directory_structure_and_%20details_2.png)
![Directory 3](1_Directory_structure_and_%20details_3.png)
![Directory 4](1_Directory_structure_and_%20details_4.png)

### Design Preparation
![Prep 1](2_Design_preparation_step_1.png)
![Prep 2](2_Design_preparation_step_2.png)
![Prep 3](2_Design_preparation_step_3.png)
![Prep 4](2_Design_preparation_step_4.png)
![Prep 5](2_Design_preparation_step_5.png)
![Prep 6](2_Design_preparation_step_6.png)
![Prep 7](2_Design_preparation_step_7.png)
![Prep 8](2_Design_preparation_step_8.png)
![Prep 9](2_Design_preparation_step_9.png)
![Prep 10](2_Design_preparation_step_10.png)

### Logic Synthesis & Functional Mapping
![Synthesis 1](3_Logic_Synthesis_and_%20Functional_%20Mapping_1.png)
![Synthesis 2](3_Logic_Synthesis_and_%20Functional_%20Mapping_2.png)
![Synthesis 3](3_Logic_Synthesis_and_%20Functional_%20Mapping_3.png)
![Synthesis 4](3_Logic_Synthesis_and_%20Functional_%20Mapping_4.png)
![Synthesis 5](3_Logic_Synthesis_and_%20Functional_%20Mapping_5.png)
![Synthesis 6](3_Logic_Synthesis_and_%20Functional_%20Mapping_6.png)
![Synthesis 7](3_Logic_Synthesis_and_%20Functional_%20Mapping_7.png)
![Synthesis 8](3_Logic_Synthesis_and_%20Functional_%20Mapping_8.png)
![Synthesis 9](3_Logic_Synthesis_and_%20Functional_%20Mapping_9.png)

### Characterising Synthesis Results
![Analysis 1](4_Characterizing_and_Analyzing_Synthesis_Results_1.png)
![Analysis 2](4_Characterizing_and_Analyzing_Synthesis_Results_2.png)
![Analysis 3](4_Characterizing_and_Analyzing_Synthesis_Results_3.png)
![Analysis 4](4_Characterizing_and_Analyzing_Synthesis_Results_4.png)
![Analysis 5](4_Characterizing_and_Analyzing_Synthesis_Results_5.png)
![Analysis 6](4_Characterizing_and_Analyzing_Synthesis_Results_6.png)
![Analysis 7](4_Characterizing_and_Analyzing_Synthesis_Results_7.png)
![Analysis 8](4_Characterizing_and_Analyzing_Synthesis_Results_8.png)
![Analysis 9](4_Characterizing_and_Analyzing_Synthesis_Results_9.png)

<h2>🔗 Navigation</h2>

[Back to Repository Overview](../README.md) &nbsp;|&nbsp; [Next : 02 : Floorplan](../02%20:%20Floorplan)
