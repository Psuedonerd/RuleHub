# Model Explanation: Blinov 2006

## One-sentence summary

EGF receptor signaling through ligand binding, receptor aggregation, receptor phosphorylation, and Shc adaptor recruitment.

## What the model shows

This model shows the earliest combinatorial events after EGF stimulation: ligand binds EGFR, receptors aggregate, receptors phosphorylate one another, and phosphorylated receptor sites recruit Shc and downstream adaptor complexes.

## Biological story

Blinov 2006 follows EGFR from ligand binding to adaptor recruitment. The biological story is how receptor clustering creates phosphorylated docking sites that pull Shc, Grb2, and SOS into signaling-competent complexes.

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

## Expected behavior in plots

Plots should show ligand-bound receptor and receptor phosphorylation rising before Shc and Grb2/SOS-containing complexes. Loss of phosphorylation or adaptor complexes indicates dephosphorylation and complex turnover.

## Caveats

This is an early EGFR signaling model. It should not be read as a complete Ras/MAPK pathway simulation unless downstream modules are explicitly represented by readouts.
