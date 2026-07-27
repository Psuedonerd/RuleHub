# Model Explanation: Blinov 2006

## One-sentence summary

EGF-driven EGFR aggregation creates phosphotyrosine docking routes that assemble Shc–Grb2–SOS signaling complexes.

## What the model shows

This model describes the earliest combinatorial stages of epidermal growth factor receptor (EGFR) signaling. Epidermal growth factor (EGF) binds EGFR, receptors aggregate and phosphorylate one another, and two receptor phosphotyrosines support direct or Shc-mediated recruitment of Grb2 and Son of Sevenless (SOS).

## Biological story

Ligand occupancy brings receptors together. Receptor phosphorylation creates distinct docking sites: one can recruit Grb2 directly, while another recruits Shc. Phosphorylated Shc adds a second route to Grb2–SOS assembly, allowing several molecular complexes to carry the same downstream exchange factor.

## Main biological players

EGF, EGFR, the Shc adaptor, growth factor receptor-bound protein 2 (Grb2), SOS, receptor tyrosines Y1068 and Y1148, and Shc Y317.

## Mechanism in plain English

EGF binds receptor and promotes EGFR aggregation. Neighboring receptors phosphorylate Y1068 and Y1148. Grb2 binds phosphorylated Y1068 through its SH2 domain and recruits SOS through an SH3 interaction. Shc binds phosphorylated Y1148, becomes phosphorylated at Y317, and then captures Grb2–SOS. Dephosphorylation and reversible adaptor binding dismantle these routes.

## Key modeled events

- EGF binds EGFR and promotes receptor aggregation.
- Aggregated receptors phosphorylate Y1068 and Y1148.
- Grb2 binds Y1068 directly and recruits SOS.
- Shc binds Y1148, becomes phosphorylated at Y317, and creates an alternate Grb2–SOS platform.
- Dephosphorylation and dissociation turn over receptor and adaptor complexes.

## What the model measures

Readouts include receptor dimers, total receptor phosphorylation, Shc phosphorylation, direct receptor–Grb2/SOS complexes, receptor–Shc complexes, Shc–Grb2/SOS complexes, and total EGFR, Shc, Grb2, and SOS pools.

## Expected behavior in plots

Receptor dimers and phosphotyrosines should rise before adaptor assemblies. Direct Y1068–Grb2–SOS complexes may appear sooner, while the Shc-mediated route should lag because it requires Shc recruitment and phosphorylation; both should decline as receptor and Shc phosphates turn over.

## Caveats

The model ends at SOS recruitment and does not explicitly follow Ras nucleotide exchange, the MAP kinase cascade, receptor internalization, or transcription.
