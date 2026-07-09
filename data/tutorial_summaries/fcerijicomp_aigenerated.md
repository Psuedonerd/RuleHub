# Model Explanation: fceri_ji_comp

## One-sentence summary

fceri_ji_comp demonstrates ligand receptor binding.

## What the model shows

fceri_ji_comp shows ligand receptor binding. It is useful because it keeps attention on ligand receptor binding while still connecting that step to the model readouts.

## Biological story

fceri_ji_comp is a validation model focused on ligand receptor binding. The biological narrative is built around ligand receptor binding, with constitutive lyn receptor binding providing the next layer of behavior rather than a generic pathway-wide description.

## Main biological players

Lig, Lyn, Syk, Rec

## Mechanism in plain English

fceri_ji_comp begins with ligand receptor binding. It then adds constitutive lyn receptor binding, which changes how Lig, Lyn, Syk, Rec contribute to the tutorial behavior. The third modeled step, transphosphorylation of beta by constitutive lyn, connects the upstream event to the readouts a user would inspect after simulation.

## Key modeled events

- Ligand receptor binding.
- Constitutive Lyn receptor binding.
- Transphosphorylation of beta by constitutive Lyn.

## What the model measures

The readouts include LynFree, RecMon, RecDim, RecPbeta, RecPgamma, RecSyk, and additional related outputs. They show how fceri_ji_comp distributes molecules among active, inactive, bound, free, or product-like states.

## Expected behavior in plots

For fceri_ji_comp, inspect readouts that report ligand receptor binding and compare them with readouts affected by constitutive lyn receptor binding. A visible delay, plateau, or separation between those outputs indicates how transphosphorylation of beta by constitutive lyn changes the tutorial dynamics.

## Caveats

fceri_ji_comp is primarily a validation-style example for ligand receptor binding; it should be used to understand that encoded behavior rather than as a complete biological pathway.
