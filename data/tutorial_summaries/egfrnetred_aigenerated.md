# Model Explanation: egfr_net_red

## One-sentence summary

Reduced state space version of EGFR NET.model with equivalent ODE dynamics.

## What the model shows

egfr_net_red shows reduced state space version of egfr net.model with equivalent ode dynamics. It is useful because it keeps attention on ligand receptor binding while still connecting that step to the model readouts.

## Biological story

egfr_net_red is a validation model focused on reduced state space version of egfr net.model with equivalent ode dynamics. The biological narrative is built around ligand receptor binding, with transphosphorylation of egfr by rtk providing the next layer of behavior rather than a generic pathway-wide description.

## Main biological players

egf, egfr_1, egfr_2, egfr_3, Grb2, Shc, Sos

## Mechanism in plain English

egfr_net_red begins with ligand receptor binding. It then adds transphosphorylation of egfr by rtk, which changes how egf, egfr_1, egfr_2, egfr_3, Grb2, Shc contribute to the tutorial behavior. The third modeled step, strong differences are seen for r g s in comparison with path model, connects the upstream event to the readouts a user would inspect after simulation.

## Key modeled events

- Ligand receptor binding.
- Transphosphorylation of egfr by RTK.
- Strong differences are seen for R G S in comparison with path model.

## What the model measures

The readouts include Dimers, Sos act, RP, Shc Grb, Shc Grb Sos, R Grb2, and additional related outputs. They show how egfr_net_red distributes molecules among active, inactive, bound, free, or product-like states.

## Expected behavior in plots

For egfr_net_red, inspect readouts that report ligand receptor binding and compare them with readouts affected by transphosphorylation of egfr by rtk. A visible delay, plateau, or separation between those outputs indicates how strong differences are seen for r g s in comparison with path model changes the tutorial dynamics.

## Caveats

egfr_net_red is primarily a validation-style example for reduced state space version of egfr net.model with equivalent ode dynamics; it should be used to understand that encoded behavior rather than as a complete biological pathway.
