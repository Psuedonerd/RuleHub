# Model Explanation: Kozer 2014

## One-sentence summary

EGFR oligomerization and phosphorylation create cluster-dependent docking opportunities for the adaptor Grb2.

## What the model shows

This extension of an EGFR oligomerization model links receptor cluster architecture to Grb2 recruitment. It retains ligand-sensitive ectodomain and cytosolic-tail interactions, then adds reversible binding of Grb2 to phosphorylated EGFR so adaptor occupancy can be compared across monomers, distinct dimers, and larger receptor assemblies.

## Biological story

EGF promotes receptor crosslinking and active tail associations, which generate phosphorylated EGFR. Grb2 recognizes those phosphorylated receptors, and the number and arrangement of modified receptors determine whether a cluster recruits one or several adaptor molecules.

## Main biological players

EGF, EGFR, phosphorylated EGFR tails, and the SH2 adaptor Grb2.

## Mechanism in plain English

Ligand occupancy changes EGFR assembly and tail conformation. Active paired tails phosphorylate receptor tyrosines, creating binding sites for Grb2. Grb2 associates reversibly with those sites without itself driving phosphorylation. Because receptors can form several oligomeric arrangements, the model resolves adaptor recruitment to different dimer states as well as the overall clustered population.

## Key modeled events

- EGF binding and ectodomain contacts build EGFR dimers and higher-order oligomers.
- Active cytosolic tails associate and phosphorylate receptor tyrosines.
- Grb2 binds phosphorylated EGFR and dissociates reversibly.
- Distinct readouts separate Grb2 recruitment to monomeric and differently configured dimeric receptors.

## What the model measures

The model tracks free ligand and receptor, receptor cluster sizes, phosphorylated EGFR, free Grb2, total Grb2-bound receptor, and several Grb2–EGFR dimer configurations.

## Expected behavior in plots

As EGF increases, receptor clustering and phosphorylation should create more Grb2 docking sites, lowering free Grb2 while increasing Grb2-bound EGFR. Individual dimer readouts may differ because ligand occupancy and tail associations make some receptor arrangements more phosphorylation-competent than others.

## Caveats

The model ends at adaptor recruitment: it does not include SOS, Ras, ERK, receptor internalization, or Grb2-driven downstream signaling.
