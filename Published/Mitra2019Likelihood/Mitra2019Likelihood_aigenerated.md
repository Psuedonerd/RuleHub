# Model Explanation: Mitra 2019 degranulation ground truth

## One-sentence summary

Antigen-driven FcεRI signaling produces PIP3 and SHIP1-dependent control of mast-cell degranulation.

## What the model shows

This ground-truth model connects immunoglobulin E receptor signaling to secretion. FcεRI is the high-affinity immunoglobulin E receptor, PIP3 is phosphatidylinositol-3,4,5-trisphosphate, and SHIP1 is an inositol phosphatase.

## Biological story

Multivalent antigen crosslinks IgE-bound receptor, recruits and activates Syk, and creates docking sites for SHIP1. Lipid signaling shifts a regulatory switch that controls release of a β-hexosaminidase-like secretion marker.

## Main biological players

DNP antigen, IgE–FcεRI receptor, Syk, SHIP1, PIP3, a regulatory switch, and a secreted degranulation marker.

## Mechanism in plain English

Antigen clusters receptors and enables receptor phosphorylation. Syk binds and becomes active in these complexes. SHIP1 is recruited through phosphotyrosine contacts and modulates PIP3-associated signaling. The balance of kinase and phosphatase activity controls a downstream switch, which transfers reporter material from an intracellular to secreted state.

## Key modeled events

- Antigen crosslinks IgE-bound FcεRI.
- Clustered receptors recruit and activate Syk.
- SHIP1 engagement modulates PIP3-dependent signaling.
- The downstream switch controls secretion of the degranulation reporter.

## What the model measures

The principal readout is secreted β-hexosaminidase, a proxy for degranulation; internal states also capture receptor, kinase, phosphatase, lipid, and switch activation.

## Expected behavior in plots

Receptor/Syk activation should precede PIP3-dependent switch activation. Secreted reporter should rise after that signaling delay and accumulate, while stronger SHIP1 restraint should reduce or postpone release.

## Caveats

The parameters were designated as fitting ground truth. The secretion marker is a proxy, and granule fusion and calcium dynamics are not represented explicitly.
