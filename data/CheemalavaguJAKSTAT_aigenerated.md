# Model Explanation: Cheemalavagu 2024

## 1. One-sentence summary

This model represents jak-stat signaling using BNGL rules for the molecules and interactions encoded in `Cheemalavagu_JAK_STAT.bngl`.

## 2. Biological meaning

The metadata describes this model as **JAK-STAT signaling** and places it in the `other` category. Tags provided by the repository are: `published`, `literature`, `signaling`, `cheemalavagu`, `jak`, `stat`, `l1`, `il6r`, `gp130`, `l2`, `il10r1`, `il10r2`, `jak1`, `jak2`. Based on the local BNGL file, the model encodes molecular species, initial conditions, observables, and reaction rules that together define the biological or biochemical process named by the model. When names are abbreviated, the explanation below keeps the BNGL names visible rather than inventing unsupported identities.

## 3. Main molecules, sites, and states

In BNGL, molecule declarations define the allowed molecular objects and their sites. A site may bind another molecule, carry an internal state after `~`, or both. Matching bond labels such as `!0` or `!1` mean the marked sites are connected by the same bond; for example, `A(a!0).B(b!0)` means `A` is bound through `a` to `B` through `b`.

- `L1(il6r)`: A declared molecular object. Components inside parentheses are binding, recognition, modification, or bookkeeping sites; states after `~` are internal alternatives such as active/inactive or modified/unmodified when the model names make that interpretation clear.
- `IL6R(l1,gp130,jak1,socs3,stat)`: A declared molecular object. Components inside parentheses are binding, recognition, modification, or bookkeeping sites; states after `~` are internal alternatives such as active/inactive or modified/unmodified when the model names make that interpretation clear.
- `GP130(il6r,jak2,socs3,stat)`: A declared molecular object. Components inside parentheses are binding, recognition, modification, or bookkeeping sites; states after `~` are internal alternatives such as active/inactive or modified/unmodified when the model names make that interpretation clear.
- `L2(il10r1)`: A declared molecular object. Components inside parentheses are binding, recognition, modification, or bookkeeping sites; states after `~` are internal alternatives such as active/inactive or modified/unmodified when the model names make that interpretation clear.
- `IL10R1(l2,il10r2,jak1,stat)`: A declared molecular object. Components inside parentheses are binding, recognition, modification, or bookkeeping sites; states after `~` are internal alternatives such as active/inactive or modified/unmodified when the model names make that interpretation clear.
- `IL10R2(il10r1)`: A declared molecular object. Components inside parentheses are binding, recognition, modification, or bookkeeping sites; states after `~` are internal alternatives such as active/inactive or modified/unmodified when the model names make that interpretation clear.
- `JAK1(rec,socs1)`: A declared molecular object. Components inside parentheses are binding, recognition, modification, or bookkeeping sites; states after `~` are internal alternatives such as active/inactive or modified/unmodified when the model names make that interpretation clear.
- `JAK2(gp130)`: A declared molecular object. Components inside parentheses are binding, recognition, modification, or bookkeeping sites; states after `~` are internal alternatives such as active/inactive or modified/unmodified when the model names make that interpretation clear.
- `SOCS3(il6r,gp130)`: A declared molecular object. Components inside parentheses are binding, recognition, modification, or bookkeeping sites; states after `~` are internal alternatives such as active/inactive or modified/unmodified when the model names make that interpretation clear.
- `SOCS1(jak1)`: A declared molecular object. Components inside parentheses are binding, recognition, modification, or bookkeeping sites; states after `~` are internal alternatives such as active/inactive or modified/unmodified when the model names make that interpretation clear.
- `PTP3()`: A declared molecular object. Components inside parentheses are binding, recognition, modification, or bookkeeping sites; states after `~` are internal alternatives such as active/inactive or modified/unmodified when the model names make that interpretation clear.
- `PTP1()`: A declared molecular object. Components inside parentheses are binding, recognition, modification, or bookkeeping sites; states after `~` are internal alternatives such as active/inactive or modified/unmodified when the model names make that interpretation clear.
- `S3(Y~0~P)`: A declared molecular object. Components inside parentheses are binding, recognition, modification, or bookkeeping sites; states after `~` are internal alternatives such as active/inactive or modified/unmodified when the model names make that interpretation clear.
- `S1(Y~0~P)`: A declared molecular object. Components inside parentheses are binding, recognition, modification, or bookkeeping sites; states after `~` are internal alternatives such as active/inactive or modified/unmodified when the model names make that interpretation clear.

## 4. Initial conditions and model setup

Seed species define the starting mixture for simulation. Numeric values at the end of a seed-species line are the starting amounts or concentrations used by the model.

- `L1(il6r) L1_0`: Initial species or starting amount. Molecules listed without matching `!` bond labels begin free; matching labels indicate an initial complex.
- `IL6R(l1,gp130,jak1,socs3,stat) IL6R_0`: Initial species or starting amount. Molecules listed without matching `!` bond labels begin free; matching labels indicate an initial complex.
- `GP130(il6r,jak2,socs3,stat) GP130_0`: Initial species or starting amount. Molecules listed without matching `!` bond labels begin free; matching labels indicate an initial complex.
- `L2(il10r1) L2_0`: Initial species or starting amount. Molecules listed without matching `!` bond labels begin free; matching labels indicate an initial complex.
- `IL10R1(l2,il10r2,jak1,stat) IL10R1_0`: Initial species or starting amount. Molecules listed without matching `!` bond labels begin free; matching labels indicate an initial complex.
- `IL10R2(il10r1) IL10R2_0`: Initial species or starting amount. Molecules listed without matching `!` bond labels begin free; matching labels indicate an initial complex.
- `JAK1(rec,socs1) JAK1_0`: Initial species or starting amount. Molecules listed without matching `!` bond labels begin free; matching labels indicate an initial complex.
- `JAK2(gp130) JAK2_0`: Initial species or starting amount. Molecules listed without matching `!` bond labels begin free; matching labels indicate an initial complex.
- `SOCS3(il6r,gp130) SOCS3_0`: Initial species or starting amount. Molecules listed without matching `!` bond labels begin free; matching labels indicate an initial complex.
- `SOCS1(jak1) SOCS1_0`: Initial species or starting amount. Molecules listed without matching `!` bond labels begin free; matching labels indicate an initial complex.
- `PTP3() PTP3_0`: Initial species or starting amount. Molecules listed without matching `!` bond labels begin free; matching labels indicate an initial complex.
- `PTP1() PTP1_0`: Initial species or starting amount. Molecules listed without matching `!` bond labels begin free; matching labels indicate an initial complex.
- `S3(Y~0) S3_0`: Initial species or starting amount. Molecules listed without matching `!` bond labels begin free; matching labels indicate an initial complex.
- `S1(Y~0) S1_0`: Initial species or starting amount. Molecules listed without matching `!` bond labels begin free; matching labels indicate an initial complex.

Important parameters parsed from the model include:

- `il6_il6r_binding 1`
- `il6_il6r_unbinding 1`
- `il6r_gp130_binding 1`
- `il6r_gp130_unbinding 1`
- `il6_complex_jak1_binding 1`
- `il6_complex_jak1_unbinding 1`
- `il6_complex_jak2_binding 1`
- `il6_complex_jak2_unbinding 1`
- `SOCS3_il6r_binding 1`
- `SOCS3_il6r_unbinding 1`
- `SOCS3_gp130_binding 1`
- `SOCS3_gp130_unbinding 1`
- `il6_jak1_med_STAT3_act 1`
- `il6_jak1_med_STAT1_act 1`
- `il6_jak2_med_STAT3_act 1`
- `il6_jak2_med_STAT1_act 1`
- `il10_il10r1_binding 1`
- `il10_il10r1_unbinding 1`
- `il10r1_il10r2_binding 1`
- `il10r1_il10r2_unbinding 1`

Additional functions or formulas parsed from the model:

- No functions block was found.

Actions or simulation commands parsed from the model:

- `generate_network({overwrite=>1})`: BNGL action or simulation command. It controls model execution, such as network generation, deterministic ODE simulation, stochastic simulation, or output writing, depending on the command name and arguments.
- `writeMexfile({t_start=>0,t_end=>90,n_steps=>91,atol=>1e-10})`: BNGL action or simulation command. It controls model execution, such as network generation, deterministic ODE simulation, stochastic simulation, or output writing, depending on the command name and arguments.

## 5. Reaction rules in plain English

Reaction rules describe event classes rather than single molecular collisions. Each rule below is translated from the local BNGL syntax into plain language. Rate names are reported exactly as encoded in the rule.

- `unnamed rule`: Binding or complex formation. In words, the reactant pattern `IL6R(l1,gp130,jak1,socs3,stat) + L1(il6r)` is converted to `IL6R(l1!1,gp130,jak1,socs3,stat).L1(il6r!1)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `il6_il6r_binding, il6_il6r_unbinding`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `IL6R(l1!1,gp130,jak1,socs3,stat).L1(il6r!1) + GP130(il6r,jak2,socs3,stat)` is converted to `IL6R(l1!1,gp130!2,jak1,socs3,stat).L1(il6r!1).GP130(il6r!2,jak2,socs3,stat)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `il6r_gp130_binding, il6r_gp130_unbinding`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `IL6R(l1!1,gp130!2,jak1,socs3,stat).L1(il6r!1).GP130(il6r!2) + JAK1(rec,socs1)` is converted to `IL6R(l1!1,gp130!2,jak1!3,socs3,stat).L1(il6r!1).GP130(il6r!2).JAK1(rec!3,socs1)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `il6_complex_jak1_binding, il6_complex_jak1_unbinding`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `IL6R(l1!1,gp130!2).L1(il6r!1).GP130(il6r!2,jak2,socs3,stat) + JAK2(gp130)` is converted to `IL6R(l1!1,gp130!2).L1(il6r!1).GP130(il6r!2,jak2!4,socs3,stat).JAK2(gp130!4)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `il6_complex_jak2_binding, il6_complex_jak2_unbinding`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `IL6R(l1!1,gp130!2,jak1!3,socs3,stat).L1(il6r!1).GP130(il6r!2).JAK1(rec!3,socs1) + SOCS3(il6r,gp130)` is converted to `IL6R(l1!1,gp130!2,jak1!3,socs3!5,stat).L1(il6r!1).GP130(il6r!2).JAK1(rec!3,socs1).SOCS3(il6r!5,gp130)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `SOCS3_il6r_binding, SOCS3_il6r_unbinding`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `IL6R(l1!1,gp130!2).L1(il6r!1).GP130(il6r!2,jak2!4,socs3,stat).JAK2(gp130!4) + SOCS3(il6r,gp130)` is converted to `IL6R(l1!1,gp130!2).L1(il6r!1).GP130(il6r!2,jak2!4,socs3!6,stat).JAK2(gp130!4).SOCS3(il6r,gp130!6)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `SOCS3_gp130_binding, SOCS3_gp130_unbinding`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `IL6R(l1!1,gp130!2,jak1!3,socs3,stat).L1(il6r!1).GP130(il6r!2).JAK1(rec!3,socs1) + SOCS1(jak1)` is converted to `IL6R(l1!1,gp130!2,jak1!3,socs3,stat).L1(il6r!1).GP130(il6r!2).JAK1(rec!3,socs1!7).SOCS1(jak1!7)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `SOCS1_jak1_binding, SOCS1_jak1_unbinding`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `IL6R(l1!1,gp130!2,jak1!3,socs3,stat).L1(il6r!1).GP130(il6r!2).JAK1(rec!3,socs1) + S3(Y~0)` is converted to `IL6R(l1!1,gp130!2,jak1!3,socs3,stat!8).L1(il6r!1).GP130(il6r!2).JAK1(rec!3,socs1).S3(Y~P!8)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `il6_jak1_med_STAT3_act`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `IL6R(l1!1,gp130!2,jak1!3,socs3,stat!8).L1(il6r!1).GP130(il6r!2).JAK1(rec!3,socs1).S3(Y~P!8)` is converted to `IL6R(l1!1,gp130!2,jak1!3,socs3,stat).L1(il6r!1).GP130(il6r!2).JAK1(rec!3,socs1) + S3(Y~P)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `pSTAT3_rec_dissoc`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `IL6R(l1!1,gp130!2,jak1!3,socs3,stat).L1(il6r!1).GP130(il6r!2).JAK1(rec!3,socs1) + S1(Y~0)` is converted to `IL6R(l1!1,gp130!2,jak1!3,socs3,stat!9).L1(il6r!1).GP130(il6r!2).JAK1(rec!3,socs1).S1(Y~P!9)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `il6_jak1_med_STAT1_act`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `IL6R(l1!1,gp130!2,jak1!3,socs3,stat!9).L1(il6r!1).GP130(il6r!2).JAK1(rec!3,socs1).S1(Y~P!9)` is converted to `IL6R(l1!1,gp130!2,jak1!3,socs3,stat).L1(il6r!1).GP130(il6r!2).JAK1(rec!3,socs1) + S1(Y~P)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `pSTAT1_rec_dissoc`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `IL6R(l1!1,gp130!2).L1(il6r!1).GP130(il6r!2,jak2!4,socs3,stat).JAK2(gp130!4) + S3(Y~0)` is converted to `IL6R(l1!1,gp130!2).L1(il6r!1).GP130(il6r!2,jak2!4,socs3,stat!10).JAK2(gp130!4).S3(Y~P!10)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `il6_jak2_med_STAT3_act`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `IL6R(l1!1,gp130!2).L1(il6r!1).GP130(il6r!2,jak2!4,socs3,stat!10).JAK2(gp130!4).S3(Y~P!10)` is converted to `IL6R(l1!1,gp130!2).L1(il6r!1).GP130(il6r!2,jak2!4,socs3,stat).JAK2(gp130!4) + S3(Y~P)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `pSTAT3_rec_dissoc`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `IL6R(l1!1,gp130!2).L1(il6r!1).GP130(il6r!2,jak2!4,socs3,stat).JAK2(gp130!4) + S1(Y~0)` is converted to `IL6R(l1!1,gp130!2).L1(il6r!1).GP130(il6r!2,jak2!4,socs3,stat!11).JAK2(gp130!4).S1(Y~P!11)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `il6_jak2_med_STAT1_act`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `IL6R(l1!1,gp130!2).L1(il6r!1).GP130(il6r!2,jak2!4,socs3,stat!11).JAK2(gp130!4).S1(Y~P!11)` is converted to `IL6R(l1!1,gp130!2).L1(il6r!1).GP130(il6r!2,jak2!4,socs3,stat).JAK2(gp130!4) + S1(Y~P)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `pSTAT1_rec_dissoc`.
- `unnamed rule`: Binding or complex formation. In words, the reactant pattern `IL10R1(l2,il10r2,jak1,stat) + L2(il10r1)` is converted to `IL10R1(l2!1,il10r2,jak1,stat).L2(il10r1!1)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `il10_il10r1_binding, il10_il10r1_unbinding`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `IL10R1(l2!1,il10r2,jak1,stat).L2(il10r1!1) + IL10R2(il10r1)` is converted to `IL10R1(l2!1,il10r2!2,jak1,stat).L2(il10r1!1).IL10R2(il10r1!2)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `il10r1_il10r2_binding, il10r1_il10r2_unbinding`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `IL10R1(l2!1,il10r2!2,jak1,stat).L2(il10r1!1).IL10R2(il10r1!2) + JAK1(rec,socs1)` is converted to `IL10R1(l2!1,il10r2!2,jak1!3,stat).L2(il10r1!1).IL10R2(il10r1!2).JAK1(rec!3,socs1)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `il10_complex_jak1_binding, il10_complex_jak1_unbinding`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `IL10R1(l2!1,il10r2!2,jak1!3,stat).L2(il10r1!1).IL10R2(il10r1!2).JAK1(rec!3,socs1) + SOCS1(jak1)` is converted to `IL10R1(l2!1,il10r2!2,jak1!3,stat).L2(il10r1!1).IL10R2(il10r1!2).JAK1(rec!3,socs1!4).SOCS1(jak1!4)`. The double arrow means the event is reversible. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `SOCS1_jak1_binding, SOCS1_jak1_unbinding`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `IL10R1(l2!1,il10r2!2,jak1!3,stat).L2(il10r1!1).IL10R2(il10r1!2).JAK1(rec!3,socs1) + S3(Y~0)` is converted to `IL10R1(l2!1,il10r2!2,jak1!3,stat!5).L2(il10r1!1).IL10R2(il10r1!2).JAK1(rec!3,socs1).S3(Y~P!5)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `il10_jak1_med_STAT3_act`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `IL10R1(l2!1,il10r2!2,jak1!3,stat!5).L2(il10r1!1).IL10R2(il10r1!2).JAK1(rec!3,socs1).S3(Y~P!5)` is converted to `IL10R1(l2!1,il10r2!2,jak1!3,stat).L2(il10r1!1).IL10R2(il10r1!2).JAK1(rec!3,socs1) + S3(Y~P)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `pSTAT3_rec_dissoc`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `IL10R1(l2!1,il10r2!2,jak1!3,stat).L2(il10r1!1).IL10R2(il10r1!2).JAK1(rec!3,socs1) + S1(Y~0)` is converted to `IL10R1(l2!1,il10r2!2,jak1!3,stat!6).L2(il10r1!1).IL10R2(il10r1!2).JAK1(rec!3,socs1).S1(Y~P!6)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `il10_jak1_med_STAT1_act`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `IL10R1(l2!1,il10r2!2,jak1!3,stat!6).L2(il10r1!1).IL10R2(il10r1!2).JAK1(rec!3,socs1).S1(Y~P!6)` is converted to `IL10R1(l2!1,il10r2!2,jak1!3,stat).L2(il10r1!1).IL10R2(il10r1!2).JAK1(rec!3,socs1) + S1(Y~P)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `pSTAT1_rec_dissoc`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `PTP3() + S3(Y~P)` is converted to `PTP3() + S3(Y~0)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `PTP_med_STAT3_deact`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `PTP1() + S1(Y~P)` is converted to `PTP1() + S1(Y~0)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `PTP_med_STAT1_deact`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `S3(Y~P)` is converted to `S3(Y~P) + SOCS3(il6r,gp130)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `STAT3_SOCS3_ind`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `S3(Y~P)` is converted to `S3(Y~P) + SOCS1(jak1)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `STAT3_SOCS1_ind`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `S1(Y~P)` is converted to `S1(Y~P) + SOCS3(il6r,gp130)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `STAT1_SOCS3_ind`.
- `unnamed rule`: Biochemical transformation or interaction. In words, the reactant pattern `S1(Y~P)` is converted to `S1(Y~P) + SOCS1(jak1)`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `STAT1_SOCS1_ind`.
- `unnamed rule`: Removal or degradation-like event. In words, the reactant pattern `SOCS3(il6r,gp130)` is converted to `0`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `SOCS3_degrad`.
- `unnamed rule`: Removal or degradation-like event. In words, the reactant pattern `SOCS1(jak1)` is converted to `0`. Sites marked with matching `!` bond labels are connected in the resulting complex; sites without those labels are free or unspecified in that pattern. The listed rate parameter(s) are `SOCS1_degrad`.

## 6. Observables and expected simulation output

Observables specify what the simulator records. They do not by themselves prove a biological outcome; they identify quantities that can be plotted or analyzed after running the model.

- `Molecules total_pS3 IL6R(l1!1,gp130!2,jak1!3,socs3,stat!8).L1(il6r!1).GP130(il6r!2).JAK1(rec!3,socs1).S3(Y~P!8),S3(Y~P),IL6R(l1!1,gp130!2).L1(il6r!1).GP130(il6r!2,jak2!4,socs3,stat!10).JAK2(gp130!4).S3(Y~P!10),IL10R1(l2!1,il10r2!2,jak1!3,stat!5).L2(il10r1!1).IL10R2(il10r1!2).JAK1(rec!3,socs1).S3(Y~P!5)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.
- `Molecules total_pS1 IL6R(l1!1,gp130!2,jak1!3,socs3,stat!9).L1(il6r!1).GP130(il6r!2).JAK1(rec!3,socs1).S1(Y~P!9),S1(Y~P),IL6R(l1!1,gp130!2).L1(il6r!1).GP130(il6r!2,jak2!4,socs3,stat!11).JAK2(gp130!4).S1(Y~P!11),IL10R1(l2!1,il10r2!2,jak1!3,stat!6).L2(il10r1!1).IL10R2(il10r1!2).JAK1(rec!3,socs1).S1(Y~P!6)`: A simulation measurement. `Molecules` observables count matching molecule patterns, and `Species` observables count matching molecular complexes/species.

Based on these observables and rules, simulation output would likely track how the named free molecules, complexes, or internal states change over time under the encoded rates and starting amounts.

## 7. Metadata, source, and compatibility

- Model id: `Cheemalavagu_JAK_STAT`
- Title/name: `Cheemalavagu 2024`
- Category: `other`
- Source origin: `published`
- Original repository: `bionetgen-web-simulator`
- Original format: `bngl`
- Source path in metadata: `published-models/literature/Cheemalavagu_JAK_STAT.bngl`
- BNGL file used locally: `Published/CheemalavaguJAKSTAT/Cheemalavagu_JAK_STAT.bngl`
- YAML file used locally: `Published/CheemalavaguJAKSTAT/metadata.yaml`
- Compatibility: bng2 compatible = `true`, NFsim compatible = `false`, simulation methods = `['ode']`
- Playground visibility: visible = `true`, featured = `false`, difficulty = `intermediate`

## 8. Caveats or missing information

- No contributor field was present in the parsed metadata.
- This explanation is generated from local metadata and BNGL syntax; it does not validate biological correctness or simulation results.
