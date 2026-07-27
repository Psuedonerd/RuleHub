# Model Explanation: Posner 2004

## One-sentence summary

Negatively cooperative anti-IgE binding drives occupancy and linear crosslinking of bivalent IgE–FcεRI receptors.

## What the model shows

This model represents the monoclonal anti-IgE antibody 23G3 binding to two epitopes on receptor-bound IgE. It distinguishes first-site binding from reduced-affinity second-site binding and permits unbounded linear crosslinking, supporting equilibrium dose-response analysis under negative cooperativity.

## Biological story

Each bivalent 23G3 ligand can bind an epitope on an IgE–FcεRI receptor and use its second arm to recruit another receptor. Once one receptor epitope is occupied, the second epitope binds less favorably. Reversible binding redistributes receptors among free, singly occupied, and crosslinked states.

## Main biological players

Bivalent 23G3 anti-IgE antibody, bivalent IgE–FcεRI receptor units, free epitopes, and linear receptor–ligand chains.

## Mechanism in plain English

A free antibody arm captures a receptor epitope. Its remaining arm can crosslink another receptor, extending an alternating chain. Receptor occupancy reduces affinity at the other receptor epitope, representing negative cooperativity. Every contact can dissociate, allowing equilibrium occupancy to respond continuously to antibody concentration.

## Key modeled events

- 23G3 binds any available IgE epitope on a receptor unit.
- The second antibody arm recruits another receptor and extends a linear chain.
- Occupancy of one receptor epitope reduces binding at the other.
- Reversible dissociation returns ligand and receptor sites to the free pools.

## What the model measures

Readouts follow total antibody, occupancy of each receptor epitope, and fully free receptor. Together they define the fraction of available IgE sites engaged over an antibody concentration scan.

## Expected behavior in plots

Bound-epitope fractions should rise with 23G3 concentration and approach saturation, while free receptor falls. Negative cooperativity should broaden or flatten the transition compared with independent sites, and the two symmetric receptor-site curves should overlap.

## Caveats

Ring formation and secretory signaling are not represented. The model treats receptor–IgE units and antibody arms symmetrically and focuses on equilibrium binding rather than cell activation.
