# Model Explanation: Blinov 2006

## One-sentence summary

EGF receptor signaling through ligand binding, receptor aggregation, receptor phosphorylation, and Shc adaptor recruitment.

## What the model shows

This model shows the earliest combinatorial events after EGF stimulation: ligand binds EGFR, receptors aggregate, receptors phosphorylate one another, and phosphorylated receptor sites recruit Shc and downstream adaptor complexes.

## Biological story

The model is useful as a mechanistic sketch of how molecular interactions create a time-dependent biological response. It is not just a list of reactions: the important behavior is how binding, activation, inhibition, degradation, or transport events combine to change the abundance of active signaling states and complexes over time.

## Main biological players

EGF ligand, EGFR receptor, Shc, Grb2, SOS, and phosphorylated receptor docking sites.

## Mechanism in plain English

EGF binds EGFR and promotes receptor aggregation. Aggregated receptors phosphorylate each other on tyrosine sites. Different phosphorylated sites have different abilities to recruit Shc or adaptor complexes. Shc itself can be phosphorylated, creating additional docking opportunities for Grb2 and SOS. Dephosphorylation reactions reverse receptor and Shc activation.

## Key modeled events

- EGF binding creates ligand-bound EGFR complexes that can aggregate with other receptors.
- Aggregated receptors phosphorylate one another on docking sites, creating binding platforms for adaptor proteins.
- Shc recruitment, Shc phosphorylation, and Grb2/SOS assembly connect receptor phosphorylation to downstream signaling.

## What the model measures

The readouts follow ligand-bound receptor, receptor aggregates, phosphorylated receptor sites, Shc recruitment, Shc phosphorylation, and Grb2/SOS adaptor complexes. The model shows how EGFR activation is converted into adaptor assembly.

## How to interpret the plots

A rising curve means that the corresponding active molecule, modified state, complex, or output is accumulating. A falling curve means it is being consumed, deactivated, degraded, released, or diluted. If two curves move in opposite directions, the model is showing a shift between biological states, such as free versus complexed receptor, inactive versus active kinase, or unmodified versus modified substrate.

## Caveats

This is an explanatory summary of the encoded mechanism, not a claim that the model is experimentally complete. When molecule names are abstract or abbreviated, the summary avoids inventing identities beyond what the model itself supports.
