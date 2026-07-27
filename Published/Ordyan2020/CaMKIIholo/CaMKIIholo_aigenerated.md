# Model Explanation: Ordyan 2020 CaMKII holoenzyme

## One-sentence summary

Calcium-loaded calmodulin activates a multimeric CaMKII holoenzyme whose autophosphorylation stores and erases signaling history.

## What the model shows

This model follows calcium/calmodulin-dependent protein kinase II (CaMKII) as a holoenzyme rather than isolated subunits. Calmodulin (CaM), neurogranin, and protein phosphatase 1 (PP1) control activation and memory-like phosphorylation.

## Biological story

Calcium binds the N- and C-terminal lobes of CaM. Loaded CaM leaves neurogranin, binds CaMKII subunits, and exposes kinase activity. Neighboring active subunits phosphorylate Thr286, supporting persistent activity, while Ser306 phosphorylation and PP1 promote shutoff.

## Main biological players

Calcium, CaM, neurogranin, CaMKII holoenzyme subunits, Thr286, Ser306, and PP1.

## Mechanism in plain English

Calcium loads CaM in multiple steps and changes its affinity for neurogranin and CaMKII. Bound CaM activates subunits within the ring-like holoenzyme. Adjacent active subunits autophosphorylate Thr286, allowing activity to outlast the calcium pulse; competing Ser306 modification and PP1 dephosphorylation reset the complex.

## Key modeled events

- Calcium loads both lobes of calmodulin.
- Calcium-loaded CaM disengages from neurogranin and binds CaMKII.
- Neighboring active CaMKII subunits phosphorylate Thr286.
- Ser306 phosphorylation restricts CaM rebinding.
- PP1 removes activating phosphorylation.

## What the model measures

Readouts distinguish CaM calcium-loading states, CaM-bound CaMKII forms, phosphorylation states, and holoenzyme activation across the simulated pulse protocol.

## Expected behavior in plots

Calcium-loaded CaM should rise immediately with a calcium pulse, followed by CaM-bound kinase and Thr286 phosphorylation. Thr286 activity may persist after free calcium falls, whereas PP1 should drive slower recovery; neurogranin-bound CaM should change oppositely to available CaM.

## Caveats

The model resolves many biochemical states but represents one idealized holoenzyme population. Synaptic geometry, diffusion, and other CaMKII substrates are not included.
