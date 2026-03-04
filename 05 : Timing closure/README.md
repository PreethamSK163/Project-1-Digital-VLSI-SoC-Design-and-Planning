# Post-Synthesis Timing Closure & ECO
> PicoRV32a — OpenLANE Physical Design Flow

![Tool](https://img.shields.io/badge/Tool-OpenSTA-blue)
![Tool](https://img.shields.io/badge/Tool-Yosys-blue)
![PDK](https://img.shields.io/badge/PDK-Sky130-orange)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen)

<h2>🔍 Overview</h2>

- Resolved post-synthesis timing violations by tuning OpenLANE synthesis configuration parameters — SYNTH_STRATEGY, SYNTH_BUFFERING, SYNTH_SIZING — and performing iterative OpenSTA analysis to drive slack toward zero.
- Performed manual Engineering Change Orders (ECOs) by replacing critical undersized cells with stronger drive-strength versions, achieving TNS and WNS closure without full re-synthesis.

<h2>⚙️ Tasks Covered</h2>

| Task | Description |
|:---|:---|
| Synthesis Configuration | SYNTH_STRATEGY, SYNTH_BUFFERING, SYNTH_SIZING tuned for timing |
| OpenSTA Analysis | Post-synthesis STA — fanout, capacitance, critical path inspection |
| Setup Violation Reduction | SYNTH_MAX_FANOUT adjusted, cell upsizing, logic restructuring |
| Timing ECO | Manual cell replacement via replace_cell — slack closure without re-synthesis |

<h2>📊 Key Observations</h2>

| Metric | Details |
|:---|:---|
| Tool | OpenSTA, Yosys, ABC |
| Violation Type Targeted | Setup — WNS and TNS reduction |
| Strategy Applied | SYNTH_STRATEGY delay-focused, buffering and sizing enabled |
| ECO Method | replace_cell — local cell upsizing on critical path |
| Custom Cell Verified | sky130_vsdinv mapped and timing-verified |
| Final Status | TNS → 0, WNS → positive before CTS |

<h2>📝 Stage Details</h2>

**Task 1 — Configuring Synthesis to Fix Slack** &nbsp;|&nbsp; `SYNTH_STRATEGY` `SYNTH_BUFFERING` `SYNTH_SIZING`

Identified negative WNS in initial STA report. Updated OpenLANE variables — SYNTH_STRATEGY set to delay-priority, SYNTH_BUFFERING enabled for weak signal reinforcement, SYNTH_SIZING enabled for gate upsizing. Re-ran synthesis — ABC performed iterative cell swapping and buffer insertion. Fresh STA report confirmed slack improvement. Custom sky130_vsdinv verified as mapped in the optimised netlist.

**Task 2 — OpenSTA Post-Synthesis Timing Analysis** &nbsp;|&nbsp; `OpenSTA` `report_checks` `SDC`

Invoked standalone OpenSTA environment. Loaded Sky130 Liberty files, optimised netlist, and SDC constraints. Generated detailed timing report — line-by-line gate and interconnect delay breakdown. Identified high-fanout pins and nets exceeding capacitance limits. Determined buffer insertion points for manual ECO.

**Task 3 — Optimising Synthesis to Reduce Setup Violations** &nbsp;|&nbsp; `SYNTH_MAX_FANOUT` `Cell Upsizing` `Logic Flattening`

Lowered SYNTH_MAX_FANOUT to force buffer splitting on high-load nets. Enabled drive-strength 2 and drive-strength 4 cell variants. Logic flattening applied to reduce levels between flip-flops. Re-ran synthesis and monitored ABC pass — gate delay and net delay both decreased. Verified setup violations eliminated and netlist integrity maintained.

**Task 4 — Basic Timing ECO** &nbsp;|&nbsp; `replace_cell` `write_verilog` `OpenSTA`

Used `report_checks` to isolate specific path with negative slack. Identified undersized buffer or inverter driving excessive load. Executed `replace_cell <instance> <stronger_cell>` — local fix without global re-synthesis. Re-ran `report_checks -through <net>` — slack turned positive. Saved updated netlist with `write_verilog`. Final TNS verified toward zero across full picorv32a design.

<h2>🖼️ Implementation Results</h2>

### Configuring Synthesis to Fix Slack
![Slack 1](1_Configure_synthesis_setting_to_fix_slack_1.png)
![Slack 2](1_Configure_synthesis_setting_to_fix_slack_2.png)
![Slack 3](1_Configure_synthesis_setting_to_fix_slack_3.png)
![Slack 4](1_Configure_synthesis_setting_to_fix_slack_4.png)
![Slack 5](1_Configure_synthesis_setting_to_fix_slack_5.png)
![Slack 6](1_Configure_synthesis_setting_to_fix_slack_6.png)
![Slack 7](1_Configure_synthesis_setting_to_fix_slack_7.png)
![Slack 8](1_Configure_synthesis_setting_to_fix_slack_8.png)
![Slack 9](1_Configure_synthesis_setting_to_fix_slack_9.png)
![Slack 10](1_Configure_synthesis_setting_to_fix_slack_10.png)
![Slack 11](1_Configure_synthesis_setting_to_fix_slack_11.png)
![Slack 12](1_Configure_synthesis_setting_to_fix_slack_12.png)
![Slack 13](1_Configure_synthesis_setting_to_fix_slack_13.png)

### OpenSTA Post-Synthesis Timing Analysis
![STA 1](2_OpenSTA_for_post_synth_timing_analysis_1.png)
![STA 2](2_OpenSTA_for_post_synth_timing_analysis_2.png)
![STA 3](2_OpenSTA_for_post_synth_timing_analysis_3.png)
![STA 4](2_OpenSTA_for_post_synth_timing_analysis_4.png)
![STA 5](2_OpenSTA_for_post_synth_timing_analysis_5.png)
![STA 6](2_OpenSTA_for_post_synth_timing_analysis_6.png)
![STA 7](2_OpenSTA_for_post_synth_timing_analysis_7.png)
![STA 8](2_OpenSTA_for_post_synth_timing_analysis_8.png)

### Optimising Synthesis to Reduce Setup Violations
![Opt 1](3_Optimize_synthesis_to_reduce_step_violation_1.png)
![Opt 2](3_Optimize_synthesis_to_reduce_step_violation_2.png)
![Opt 3](3_Optimize_synthesis_to_reduce_step_violation_3.png)
![Opt 4](3_Optimize_synthesis_to_reduce_step_violation_4.png)
![Opt 5](3_Optimize_synthesis_to_reduce_step_violation_5.png)
![Opt 6](3_Optimize_synthesis_to_reduce_step_violation_6.png)
![Opt 7](3_Optimize_synthesis_to_reduce_step_violation_7.png)
![Opt 8](3_Optimize_synthesis_to_reduce_step_violation_8.png)
![Opt 9](3_Optimize_synthesis_to_reduce_step_violation_9.png)
![Opt 10](3_Optimize_synthesis_to_reduce_step_violation_10.png)

### Timing ECO
![ECO 1](4_Basic_timing_eco_1.png)
![ECO 2](4_Basic_timing_eco_2.png)

<h2>🔗 Navigation</h2>

[Back to Repository Overview](../README.md) &nbsp;|&nbsp; [Previous : 04 : Custom cell](../04%20:%20Custom%20cell) &nbsp;|&nbsp; [Next : 06 : CTS](../06%20:%20CTS)
