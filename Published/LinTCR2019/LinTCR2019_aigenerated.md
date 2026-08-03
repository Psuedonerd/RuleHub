# Model Explanation: Lin TCR 2019

## One-sentence summary

pMHC-triggered T-cell receptor signaling balances Lck/ZAP activation, a MEK–ERK cascade, and inhibitory SHP feedback.

## What the model shows

This model links ligand binding at the T-cell receptor to kinase recruitment, receptor phosphorylation, ZAP activation, and downstream MEK–ERK signaling. An SHP-dependent inhibitory branch competes with productive signaling, allowing transient activation and negative regulation to emerge from the same receptor complex.

## Biological story

pMHC engages TCR and recruits Lck. Lck phosphorylates the receptor and ZAP, ZAP activates MEK, and MEK activates ERK. Lck can also activate SHP, which returns to receptor complexes and disrupts productive phosphorylation; ligand dissociation resets receptor-associated states.

## Main biological players

pMHC, TCR, Lck, ZAP, MEK, ERK, SHP, and phosphorylated receptor complexes.

## Mechanism in plain English

Ligand-bound TCR captures Lck and becomes phosphorylated. ZAP associates with and is activated near the receptor, then transfers the signal to MEK and ERK. In parallel, SHP becomes phosphorylated and can bind receptor complexes, where it promotes inhibitory resetting. Dephosphorylation and pMHC dissociation remove kinase activity and separate the complex.

## Key modeled events

- pMHC binds TCR and enables recruitment of Lck.
- Lck phosphorylates TCR and ZAP to launch the kinase cascade.
- Activated ZAP phosphorylates MEK, which in turn phosphorylates ERK.
- Activated SHP returns to receptor complexes and opposes productive signaling.

## What the model measures

The reported quantities emphasize unphosphorylated and phosphorylated MEK, with additional model functions summarizing scaled populations used to compare simulation strategies.

## Expected behavior in plots

After receptor engagement, phosphorylated MEK should rise only after Lck and ZAP activation. SHP feedback and ligand dissociation should limit that rise, producing either a peak or a restrained plateau rather than unchecked activation; unphosphorylated MEK should change in the opposite direction.

## Caveats

This is a compact signaling-and-feedback model used partly to study stochastic scaling. It does not represent the full T-cell activation program, calcium signaling, transcription, or cell fate.
