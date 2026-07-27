# Model Explanation: Notch

## One-sentence summary

Notch maturation and DSL-triggered cleavage release ICN to assemble a nuclear ICN–CSL–MAML complex.

## What the model shows

This sketch follows the core spatial sequence of Notch signaling from receptor processing in the ER and Golgi to ligand engagement at the membrane and transcription-complex assembly in the nucleus. It emphasizes movement and complex formation rather than detailed enzymology.

## Biological story

Notch and its intracellular domain mature together through the secretory pathway with OFUT1, Fringe, and Furin represented as processing factors. Membrane DSL engagement triggers cleavage, freeing ICN to enter the nucleus and recruit CSL and MAML.

## Main biological players

Notch receptor, intracellular Notch domain (ICN), OFUT1, Fringe, Furin, DSL ligand, CSL, and MAML.

## Mechanism in plain English

OFUT1 accompanies receptor movement from ER to Golgi, and Fringe/Furin accompany maturation to the membrane. DSL binds mature Notch. Subsequent cleavage separates ICN from the membrane receptor and assigns ICN to the nucleus. Nuclear ICN binds CSL, then recruits MAML to form the three-component signaling complex associated with transcriptional activation.

## Key modeled events

- Notch and ICN mature from ER through Golgi to the membrane.
- DSL binds membrane Notch.
- Ligand-dependent cleavage releases ICN for nuclear entry.
- Nuclear ICN binds CSL and recruits MAML into a ternary complex.

## What the model measures

Two readouts report the Notch–ICN precursor complex and the nuclear ICN–CSL–MAML complex. They mark receptor maturation versus the final nuclear signaling assembly.

## Expected behavior in plots

The precursor complex should be consumed as processing and cleavage proceed, whereas the nuclear ternary complex should appear later after membrane ligand engagement and ICN release. Its delayed accumulation is the clearest signature of completed signaling.

## Caveats

Processing, cleavage, and transport are lumped into coarse steps, and spatial effects are not calculated. The model does not include target-gene transcription or pathway feedback.
