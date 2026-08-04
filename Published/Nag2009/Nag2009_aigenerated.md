# Model Explanation: Nag 2009

## One-sentence summary

FcεRI activation phosphorylates LAT and drives multivalent LAT–Grb2–SOS1 crosslinking.

## What the model shows

This model connects early FcεRI/Syk signaling to assembly of a LAT-centered adaptor network. Ligand aggregates receptors, receptor-associated Syk becomes phosphorylated, active Syk modifies LAT, and phosphorylated LAT recruits Grb2 and bivalent SOS1 to build larger signaling complexes.

## Biological story

Multivalent ligand brings FcεRI receptors together and enables Syk recruitment and activation. Active Syk phosphorylates LAT, creating docking sites for Grb2. Grb2 then links LAT to SOS1, whose two Grb2-binding positions allow LAT-containing assemblies to crosslink.

## Main biological players

Multivalent ligand, FcεRI receptor, Syk, LAT, Grb2, and SOS1.

## Mechanism in plain English

Ligand first aggregates receptors. Receptor phosphorylation creates Syk-binding sites, and neighboring kinases promote Syk activation. Active Syk modifies LAT. Grb2 binds phosphorylated LAT through its SH2 domain and binds SOS1 through its SH3 domain; because SOS1 can engage two Grb2 molecules, repeated recruitment creates crosslinked LAT assemblies. Dephosphorylation and reversible binding oppose assembly.

## Key modeled events

- Ligand crosslinks FcεRI and creates receptor-associated Syk complexes.
- Syk is activated within receptor aggregates and phosphorylates LAT.
- Grb2 docks on phosphorylated LAT and recruits SOS1.
- Bivalent SOS1 links Grb2-bound LAT molecules into larger assemblies.

## What the model measures

Readouts distinguish several receptor–Syk activation states together with free, bound, and phosphorylated LAT, free Grb2, and free SOS1.

## Expected behavior in plots

Receptor–Syk complexes should rise first after ligand aggregation. Phosphorylated LAT should follow, accompanied by loss of free Grb2 and SOS1 as LAT-centered assemblies form. The timing between receptor activation and LAT occupancy exposes the handoff from FcεRI to the adaptor layer.

## Caveats

The model emphasizes LAT crosslinking and omits many parallel FcεRI outputs. Several possible aggregate measurements are not explicitly reported, so network size is inferred through component depletion and LAT states.
