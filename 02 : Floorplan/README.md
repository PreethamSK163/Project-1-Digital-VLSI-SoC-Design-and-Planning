# Floorplanning & IO Placement
> PicoRV32a — OpenLANE Physical Design Flow

![Tool](https://img.shields.io/badge/Tool-OpenROAD-blue)
![Tool](https://img.shields.io/badge/Tool-Magic%20VLSI-blue)
![PDK](https://img.shields.io/badge/PDK-Sky130-orange)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen)

<h2>🔍 Overview</h2>

- Executed `run_floorplan` to define die area, core utilisation, IO pin placement, and physical-only cell insertion — generating the floorplan DEF for the PicoRV32a design.
- Verified floorplan configuration files, inspected the merged LEF, performed visual validation of the physical layout in **Magic VLSI**, and revised IO pin placement modes using ioplacer.

<h2>⚙️ Tasks Covered</h2>

| Task | Description |
|:---|:---|
| Floorplan Execution | Die/core area, utilisation factor, IO placement, tap/decap insertion |
| Configuration Review | config.tcl, sky130 library paths, merged LEF verification |
| Magic Visualisation | Floorplan DEF loaded in Magic — rows, pins, metal layers verified |
| IO Placer Revision | IO pin placement mode revised and verified post-modification |

<h2>📊 Key Observations</h2>

| Metric | Details |
|:---|:---|
| Tool | OpenROAD, ioplacer |
| Utilisation Factor | 35% — routing congestion headroom maintained |
| IO Pin Placement | Distributed along die boundary — met2/met3 layers |
| Physical Cells Inserted | Tap cells, decoupling capacitors |
| IO Placer Mode | Revised pin distribution mode verified post-change |
| Output | picorv32a.floorplan.def |

<h2>📝 Stage Details</h2>

**Task 1 — Floorplan Execution** &nbsp;|&nbsp; `run_floorplan` `OpenROAD` `ioplacer`

Executed `run_floorplan` — die and core area boundaries calculated from utilisation factor and aspect ratio settings. IO pins distributed along die boundary using ioplacer with met2/met3 layer assignments. Tap cells and decoupling capacitors inserted for substrate integrity and power stability. Site rows generated for standard cell placement alignment.

**Task 2 — Configuration & Library Review** &nbsp;|&nbsp; `config.tcl` `LEF` `Liberty`

Reviewed design configuration hierarchy — `config.tcl` and `sky130_fd_sc_hd_config.tcl` verified for clock period, utilisation, and aspect ratio overrides. Merged LEF confirmed in `tmp/` directory — combines Technology LEF and Cell LEF. Liberty timing file `sky130_fd_sc_hd__tt_025C_1v80.lib` confirmed linked for Typical-Typical corner analysis.

**Task 3 — Floorplan Visualisation in Magic** &nbsp;|&nbsp; `Magic VLSI` `DEF`

Floorplan DEF loaded into Magic. Die and core boundaries visually verified. Standard cell rows confirmed horizontally aligned. IO pins verified along die boundary with correct spacing. Tap cells and decap cells confirmed present. Metal layer assignments validated — horizontal pins on met2, vertical on met3.

**Task 4 — IO Placer Revision** &nbsp;|&nbsp; `ioplacer` `FP_IO_MODE`

IO pin placement mode revised by modifying `FP_IO_MODE` configuration parameter. Floorplan re-executed with updated settings — pin distribution pattern changed and verified in Magic. Confirmed that ioplacer correctly applied the revised mode without affecting core area or standard cell rows.

<h2>🖼️ Implementation Results</h2>

### Floorplan Execution
![Floorplan 1](1_Steps_to_run_floorplan_using_openlane_1.png)
![Floorplan 2](1_Steps_to_run_floorplan_using_openlane_2.png)
![Floorplan 3](1_Steps_to_run_floorplan_using_openlane_3.png)
![Floorplan 4](1_Steps_to_run_floorplan_using_openlane_4.png)
![Floorplan 5](1_Steps_to_run_floorplan_using_openlane_5.png)
![Floorplan 6](1_Steps_to_run_floorplan_using_openlane_6.png)
![Floorplan 7](1_Steps_to_run_floorplan_using_openlane_7.png)
![Floorplan 8](1_Steps_to_run_floorplan_using_openlane_8.png)
![Floorplan 9](1_Steps_to_run_floorplan_using_openlane_9.png)
![Floorplan 10](1_Steps_to_run_floorplan_using_openlane_10.png)

### Configuration & Library Review
![Review 1](2_Review_floorplan_files_1.png)
![Review 2](2_Review_floorplan_files_2.png)
![Review 3](2_Review_floorplan_files_3.png)
![Review 4](2_Review_floorplan_files_4.png)
![Review 5](2_Review_floorplan_files_5.png)
![Review 6](2_Review_floorplan_files_6.png)
![Review 7](2_Review_floorplan_files_7.png)
![Review 8](2_Review_floorplan_files_8.png)
![Review 9](2_Review_floorplan_files_9.png)
![Review 10](2_Review_floorplan_files_10.png)
![Review 11](2_Review_floorplan_files_11.png)

### Floorplan Visualisation in Magic
![Magic 1](3_Review_floorplan_layout_in_magic_1.png)
![Magic 2](3_Review_floorplan_layout_in_magic_2.png)
![Magic 3](3_Review_floorplan_layout_in_magic_3.png)
![Magic 4](3_Review_floorplan_layout_in_magic_4.png)
![Magic 5](3_Review_floorplan_layout_in_magic_5.png)
![Magic 6](3_Review_floorplan_layout_in_magic_6.png)

### IO Placer Revision
![IO 1](4_IO_Placer revision_1.png)
![IO 2](4_IO_Placer revision_2.png)
![IO 3](4_IO_Placer revision_3.png)
![IO 4](4_IO_Placer revision_4.png)
![IO 5](4_IO_Placer revision_5.png)
![IO 6](4_IO_Placer revision_6.png)
![IO 7](4_IO_Placer revision_7.png)
![IO 8](4_IO_Placer revision_8.png)
![IO 9](4_IO_Placer revision_9.png)
![IO 10](4_IO_Placer revision_10.png)

<h2>🔗 Navigation</h2>

[Back to Repository Overview](../README.md) &nbsp;|&nbsp; [Previous : 01 : Synthesis](../01%20:%20Synthesis) &nbsp;|&nbsp; [Next : 03 : Placement](../03%20:%20Placement)
