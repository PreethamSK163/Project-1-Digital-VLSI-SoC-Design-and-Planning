# Congestion Aware Standard Cell Placement
> PicoRV32a — OpenLANE Physical Design Flow

![Tool](https://img.shields.io/badge/Tool-RePlAce-blue)
![Tool](https://img.shields.io/badge/Tool-OpenDP-blue)
![PDK](https://img.shields.io/badge/PDK-Sky130-orange)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen)

<h2>🔍 Overview</h2>

- Executed `run_placement` to perform congestion-aware global placement using **RePlAce** followed by detailed placement and legalisation using **OpenDP**.
- All standard cells placed into legal site rows with exact coordinates — placement DEF generated and verified.

<h2>⚙️ Tasks Covered</h2>

| Task | Description |
|:---|:---|
| Global Placement | RePlAce — HPWL minimisation, congestion-aware cell spreading |
| Detailed Placement | OpenDP — legalisation, overlap elimination, row alignment |
| DEF Verification | Placement DEF confirmed with legal cell coordinates |

<h2>📊 Key Observations</h2>

| Metric | Details |
|:---|:---|
| Tool | RePlAce (Global), OpenDP (Detailed) |
| Placement Strategy | Congestion-aware — routing resource headroom maintained |
| HPWL | Progressively decreased during optimisation iterations |
| Overflow | Reduced below 0.1 — confirming even cell distribution |
| Output | picorv32a.placement.def |

<h2>📝 Stage Details</h2>

**Global Placement** &nbsp;|&nbsp; `RePlAce` `HPWL` `Overflow`

`run_placement` executed — RePlAce treated cells as continuous distribution and spread across core area. Wire length minimised iteratively through HPWL optimisation. Congestion-aware spreading ensured sufficient routing resources remain available. Overflow metric monitored — optimisation continued until below acceptable threshold.

**Detailed Placement & Legalisation** &nbsp;|&nbsp; `OpenDP` `Site Rows`

OpenDP performed detailed placement — all cells snapped to legal site row coordinates. Power rail alignment enforced. Overlaps fully eliminated. Every standard cell assigned a fixed, valid (x, y) coordinate on the silicon grid. Placement DEF generated at `results/placement/picorv32a.placement.def`.

<h2>🖼️ Implementation Results</h2>

### Congestion-Aware Placement
![Placement 1](1_Congestion_aware_placement_using_RePIAce_1.png)
![Placement 2](1_Congestion_aware_placement_using_RePIAce_2.png)
![Placement 3](1_Congestion_aware_placement_using_RePIAce_3.png)
![Placement 4](1_Congestion_aware_placement_using_RePIAce_4.png)
![Placement 5](1_Congestion_aware_placement_using_RePIAce_5.png)

<h2>🔗 Navigation</h2>

[Back to Repository Overview](../README.md) &nbsp;|&nbsp; [Previous : 02 : Floorplan](../02%20:%20Floorplan) &nbsp;|&nbsp; [Next : 04 : Custom cell](../04%20:%20Custom%20cell)
