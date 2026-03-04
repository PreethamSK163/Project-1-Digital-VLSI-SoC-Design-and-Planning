# Clock Tree Synthesis & Verification
> PicoRV32a — OpenLANE Physical Design Flow

![Tool](https://img.shields.io/badge/Tool-TritonCTS-blue)
![Tool](https://img.shields.io/badge/Tool-OpenSTA-blue)
![PDK](https://img.shields.io/badge/PDK-Sky130-orange)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen)

<h2>🔍 Overview</h2>

- Built the clock distribution network using **TritonCTS** — clock buffers inserted across the picorv32a core to balance load, minimise skew, and ensure simultaneous clock arrival at all flip-flops.
- Verified CTS results using **OpenSTA** with real clock propagation model — setup and hold slack confirmed positive. Experimented with larger CTS buffers to analyse PPA trade-offs.

<h2>⚙️ Tasks Covered</h2>

| Task | Description |
|:---|:---|
| CTS Execution | TritonCTS — clock tree built, buffers inserted, skew minimised |
| CTS Verification | Post-CTS netlist and DEF inspected, skew and slack verified |
| Real Clock Timing | set_propagated_clock — setup and hold analysis with physical delays |
| OpenSTA Sign-off | Post-CTS STA with correct Sky130 library corners |
| Buffer Sizing Study | clkbuf_4 vs clkbuf_8 — PPA trade-off analysis |

<h2>📊 Key Observations</h2>

| Metric | Details |
|:---|:---|
| Tool | TritonCTS, OpenSTA |
| Clock Buffers Used | sky130_fd_sc_hd__clkbuf_1, clkbuf_4, clkbuf_8 |
| Clock Skew | Within acceptable limit — < 10% of clock period |
| Hold Slack | Positive — buffer delays naturally improved hold margin |
| Setup Slack | Positive — verified with real propagated clock model |
| Output | picorv32a.cts.def |

<h2>📝 Stage Details</h2>

**Task 1 — Running CTS using TritonCTS** &nbsp;|&nbsp; `run_cts` `TritonCTS` `clkbuf`

Executed `run_cts` — TritonCTS analysed the clock net and constructed a balanced tree structure. Root clock pin identified, flip-flops clustered by proximity, buffers inserted level by level to equalise delays. Sky130 clock buffers placed at regular intervals. Post-CTS DEF confirmed — `picorv32a.cts.def` contains clock buffer instances replacing the direct clock net connections.

**Task 2 — Verifying the CTS Run** &nbsp;|&nbsp; `OpenSTA` `report_checks` `Magic VLSI`

Loaded post-CTS netlist into OpenSTA. Verified clock buffer instances present — clkbuf hierarchy confirmed. Ran `report_checks -path_delay min_max` — insertion delay observed as positive source latency. Skew verified within limits. Hold slack confirmed positive. Opened CTS DEF in Magic — clock buffers visually identified at regular intervals across core. WNS and TNS both confirmed acceptable before routing.

**Task 3 — Timing Analysis with Real Clock** &nbsp;|&nbsp; `set_propagated_clock` `report_checks`

Switched from ideal to real clock model using `set_propagated_clock [all_clocks]`. Setup analysis — clock insertion delay to capture flip-flop accounted for, WNS confirmed positive. Hold analysis — launch and capture path delays compared, hold slack remained positive. Clock skew report inspected — transition times at leaf pins within Sky130 maximum limits. Final `report_checks -path_delay max` and `min` both clean.

**Task 4 — OpenSTA with Correct Timing Libraries** &nbsp;|&nbsp; `read_liberty` `read_verilog` `link_design`

Configured OpenSTA with exact Sky130 TT corner library — `sky130_fd_sc_hd__tt_025C_1v80.lib`. Loaded post-CTS netlist and DEF for wire RC estimation. Set units with `set_cmd_units`. Ran `report_checks -path_delay min_max -format full_clock_expanded` — slack values matched OpenLANE internal logs confirming sign-off consistency.

**Task 5 — Impact of Larger CTS Buffers** &nbsp;|&nbsp; `CTS_CLK_BUFFER_LIST` `clkbuf_4` `clkbuf_8`

Modified `CTS_CLK_BUFFER_LIST` to include clkbuf_4 and clkbuf_8 variants. Re-ran CTS — slew rate on clock pins decreased, insertion delay reduced. Clock skew improved — shallower tree with stronger buffers. Trade-offs observed — increased cell area and higher dynamic power consumption. Optimal buffer size confirmed for picorv32a PPA balance.

<h2>🖼️ Implementation Results</h2>

### Running CTS using TritonCTS
![CTS 1](1_Lab_steps_to_run_CTS_using_Triton_CTS_1.png)
![CTS 2](1_Lab_steps_to_run_CTS_using_Triton_CTS_2.png)
![CTS 3](1_Lab_steps_to_run_CTS_using_Triton_CTS_3.png)
![CTS 4](1_Lab_steps_to_run_CTS_using_Triton_CTS_4.png)
![CTS 5](1_Lab_steps_to_run_CTS_using_Triton_CTS_5.png)
![CTS 6](1_Lab_steps_to_run_CTS_using_Triton_CTS_6.png)
![CTS 7](1_Lab_steps_to_run_CTS_using_Triton_CTS_7.png)
![CTS 8](1_Lab_steps_to_run_CTS_using_Triton_CTS_8.png)
![CTS 9](1_Lab_steps_to_run_CTS_using_Triton_CTS_9.png)
![CTS 10](1_Lab_steps_to_run_CTS_using_Triton_CTS_10.png)
![CTS 11](1_Lab_steps_to_run_CTS_using_Triton_CTS_11.png)
![CTS 12](1_Lab_steps_to_run_CTS_using_Triton_CTS_12.png)
![CTS 13](1_Lab_steps_to_run_CTS_using_Triton_CTS_13.png)
![CTS 14](1_Lab_steps_to_run_CTS_using_Triton_CTS_14.png)

### Verifying the CTS Run
![Verify 1](2_Lab_steps_to_verify_cts_run_1.png)
![Verify 2](2_Lab_steps_to_verify_cts_run_2.png)
![Verify 3](2_Lab_steps_to_verify_cts_run_3.png)
![Verify 4](2_Lab_steps_to_verify_cts_run_4.png)
![Verify 5](2_Lab_steps_to_verify_cts_run_5.png)
![Verify 6](2_Lab_steps_to_verify_cts_run_6.png)
![Verify 7](2_Lab_steps_to_verify_cts_run_7.png)
![Verify 8](2_Lab_steps_to_verify_cts_run_8.png)
![Verify 9](2_Lab_steps_to_verify_cts_run_9.png)
![Verify 10](2_Lab_steps_to_verify_cts_run_10.png)
![Verify 11](2_Lab_steps_to_verify_cts_run_11.png)
![Verify 12](2_Lab_steps_to_verify_cts_run_12.png)
![Verify 13](2_Lab_steps_to_verify_cts_run_13.png)

### Timing Analysis with Real Clock
![Real Clock 1](3_Analyze_timing_with_real_clock_1.png)
![Real Clock 2](3_Analyze_timing_with_real_clock_2.png)
![Real Clock 3](3_Analyze_timing_with_real_clock_3.png)
![Real Clock 4](3_Analyze_timing_with_real_clock_4.png)
![Real Clock 5](3_Analyze_timing_with_real_clock_5.png)
![Real Clock 6](3_Analyze_timing_with_real_clock_6.png)
![Real Clock 7](3_Analyze_timing_with_real_clock_7.png)

### OpenSTA with Correct Timing Libraries
![STA 1](4_Execute_OPENSTA_with_right_timing_libraries_1.png)
![STA 2](4_Execute_OPENSTA_with_right_timing_libraries_2.png)
![STA 3](4_Execute_OPENSTA_with_right_timing_libraries_3.png)
![STA 4](4_Execute_OPENSTA_with_right_timing_libraries_4.png)
![STA 5](4_Execute_OPENSTA_with_right_timing_libraries_5.png)
![STA 6](4_Execute_OPENSTA_with_right_timing_libraries_6.png)
![STA 7](4_Execute_OPENSTA_with_right_timing_libraries_7.png)

### Impact of Larger CTS Buffers
![Buffer 1](5_Observe_impact_of_bigger_cts_buffers_1.png)
![Buffer 2](5_Observe_impact_of_bigger_cts_buffers_2.png)
![Buffer 3](5_Observe_impact_of_bigger_cts_buffers_3.png)
![Buffer 4](5_Observe_impact_of_bigger_cts_buffers_4.png)
![Buffer 5](5_Observe_impact_of_bigger_cts_buffers_5.png)
![Buffer 6](5_Observe_impact_of_bigger_cts_buffers_6.png)
![Buffer 7](5_Observe_impact_of_bigger_cts_buffers_7.png)
![Buffer 8](5_Observe_impact_of_bigger_cts_buffers_8.png)
![Buffer 9](5_Observe_impact_of_bigger_cts_buffers_9.png)
![Buffer 10](5_Observe_impact_of_bigger_cts_buffers_10.png)

<h2>🔗 Navigation</h2>

[Back to Repository Overview](../README.md) &nbsp;|&nbsp; [Previous : 05 : Timing closure](../05%20:%20Timing%20closure) &nbsp;|&nbsp; [Next : 07 : PDN](../07%20:%20PDN)
