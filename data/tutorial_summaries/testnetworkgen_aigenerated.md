# Model Explanation: test_network_gen

## One-sentence summary

test_network_gen demonstrates fceri model with network generation.

## What the model shows

test_network_gen shows fceri model with network generation by focusing on ligand receptor binding. The tutorial connects that event to readouts that make the modeled behavior visible.

## Biological story

test_network_gen is a validation model centered on fceri model with network generation. Its narrative moves from ligand receptor binding to constitutive lyn receptor binding, so the model teaches a specific mechanism rather than a broad pathway survey.

## Main biological players

Lig, Lyn, Syk, Rec

## Mechanism in plain English

test_network_gen uses Lig, Lyn, Syk, Rec as the main actors. First, ligand receptor binding. Next, constitutive lyn receptor binding. Finally, transphosphorylation of beta by constitutive lyn, which is what links the mechanism to the plotted readouts.

## Key modeled events

- Ligand receptor binding.
- Constitutive Lyn receptor binding.
- Transphosphorylation of beta by constitutive Lyn.

## What the model measures

The readouts track LynFree, RecMon, RecDim, RecPbeta, RecPgamma, RecSyk, RecSykPS, SykTest. These measurements are useful for seeing whether ligand receptor binding changes the amount of free, bound, active, inactive, product-like, or complexed material.

## Expected behavior in plots

For test_network_gen, compare readouts connected to ligand receptor binding with readouts connected to constitutive lyn receptor binding. Separation between those curves indicates that the tutorial mechanism is changing the system in stages rather than all at once.

## Caveats

test_network_gen is scoped to fceri model with network generation. It should be read as a focused tutorial or validation example, not as a comprehensive biological pathway model.
