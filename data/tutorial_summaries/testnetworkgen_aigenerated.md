# Model Explanation: test_network_gen

## One-sentence summary

fceri model with network generation.

## What the model shows

test_network_gen shows fceri model with network generation. It is useful because it keeps attention on ligand receptor binding while still connecting that step to the model readouts.

## Biological story

test_network_gen is a validation model focused on fceri model with network generation. The biological narrative is built around ligand receptor binding, with constitutive lyn receptor binding providing the next layer of behavior rather than a generic pathway-wide description.

## Main biological players

Lig, Lyn, Syk, Rec

## Mechanism in plain English

test_network_gen begins with ligand receptor binding. It then adds constitutive lyn receptor binding, which changes how Lig, Lyn, Syk, Rec contribute to the tutorial behavior. The third modeled step, transphosphorylation of beta by constitutive lyn, connects the upstream event to the readouts a user would inspect after simulation.

## Key modeled events

- Ligand receptor binding.
- Constitutive Lyn receptor binding.
- Transphosphorylation of beta by constitutive Lyn.

## What the model measures

The readouts include LynFree, RecMon, RecDim, RecPbeta, RecPgamma, RecSyk, and additional related outputs. They show how test_network_gen distributes molecules among active, inactive, bound, free, or product-like states.

## Expected behavior in plots

For test_network_gen, inspect readouts that report ligand receptor binding and compare them with readouts affected by constitutive lyn receptor binding. A visible delay, plateau, or separation between those outputs indicates how transphosphorylation of beta by constitutive lyn changes the tutorial dynamics.

## Caveats

test_network_gen is primarily a validation-style example for fceri model with network generation; it should be used to understand that encoded behavior rather than as a complete biological pathway.
