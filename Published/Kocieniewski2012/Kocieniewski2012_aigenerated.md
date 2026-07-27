# Model Explanation: Kocieniewski 2012

## One-sentence summary

A three-tier MAP kinase cascade uses a shared scaffold to coordinate sequential MAP3K, MAP2K, and MAPK activation.

## What the model shows

This compact scaffold model asks how colocalizing three kinase tiers changes productive signaling. MAP3K, MAP2K, and MAPK can each occupy a dedicated position on the scaffold, and phosphorylation proceeds when the required upstream and downstream kinases share that platform.

## Biological story

An activating input switches MAP3K on. Active MAP3K phosphorylates scaffold-bound MAP2K, and doubly phosphorylated MAP2K then phosphorylates scaffold-bound MAPK. Constitutive dephosphorylation competes with this relay, while completed MAPK can leave the scaffold.

## Main biological players

MAP3K, MAP2K, MAPK, and a three-position scaffold.

## Mechanism in plain English

The scaffold independently captures each kinase tier. Once active MAP3K and MAP2K are neighbors, MAP3K modifies both MAP2K regulatory residues. Fully modified MAP2K similarly modifies the two MAPK residues. Each kinase can lose phosphate groups away from productive complexes, so output depends on the balance between scaffold-assisted phosphorylation, dissociation, and dephosphorylation.

## Key modeled events

- MAP3K switches from inactive to active in response to a constant input.
- The scaffold recruits MAP3K, MAP2K, and MAPK through separate docking positions.
- Active scaffold-bound MAP3K phosphorylates MAP2K at two residues.
- Fully phosphorylated MAP2K phosphorylates scaffold-bound MAPK, which can then be released.

## What the model measures

The two readouts count productive scaffold chains containing activated MAP2K together with either phosphorylated MAPK or active MAP3K. They report assembly of the middle-to-output and input-to-middle portions of the cascade.

## Expected behavior in plots

The active-MAP3K/MAP2K chain should appear as the cascade is engaged, followed by the MAP2K/MAPK chain as phosphorylation propagates downstream. Strong dephosphorylation or rapid scaffold release should limit the persistence of both complexes.

## Caveats

Despite its metadata description, the represented mechanism is a generic scaffolded MAPK cascade rather than an explicit actin network. The kinase names are tier labels, not a complete named cellular pathway.
