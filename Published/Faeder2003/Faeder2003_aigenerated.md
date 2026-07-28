# Model Explanation: Faeder 2003

## One-sentence summary

Ligand-crosslinked high-affinity immunoglobulin E receptors recruit Lyn and Syk to initiate a phosphorylation cascade.

## What the model shows

This model captures proximal FcεRI signaling, where FcεRI means the high-affinity receptor for immunoglobulin E. It connects receptor aggregation to β- and γ-chain phosphorylation, Syk recruitment, and kinase activation.

## Biological story

A bivalent ligand brings receptors together. Constitutively associated Lyn starts receptor phosphorylation, newly phosphorylated sites recruit more Lyn and Syk, and kinases in the aggregate reinforce activation until phosphatases reverse it.

## Main biological players

Bivalent ligand, FcεRI, Lyn tyrosine kinase, Syk tyrosine kinase, receptor β and γ chains, and kinase activation-loop states.

## Mechanism in plain English

Ligand first binds and crosslinks receptors. Lyn associated with one receptor phosphorylates a neighboring receptor, creating Src homology 2 (SH2) docking sites. Lyn binds phosphorylated β chains, while tandem-SH2 Syk binds phosphorylated γ chains. Clustered kinases then phosphorylate Syk and additional receptor sites; dephosphorylation limits the signal.

## Key modeled events

- Ligand binds FcεRI and crosslinks receptors.
- Lyn phosphorylates receptor β and γ chains within aggregates.
- Phosphorylated γ chains recruit Syk, which becomes activated by transphosphorylation.
- Phosphatase activity returns receptor and Syk sites toward their basal state.

## What the model measures

Readouts distinguish free Lyn, receptor monomers and dimers, phosphorylated β and γ chains, receptor-bound Syk, and activated receptor-bound Syk.

## Expected behavior in plots

Receptor dimers should rise before receptor phosphorylation. Phosphorylated γ chains should then recruit Syk, with activated Syk appearing after the bound-Syk curve; strong dephosphorylation should cap or reverse these increases.

## Caveats

The model stops at early FcεRI kinase events and does not include LAT adaptors, calcium release, degranulation, or gene expression.
