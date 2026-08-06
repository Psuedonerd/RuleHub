# Model Explanation: Blinov egfr

## One-sentence summary

EGF-driven EGFR dimerization creates two phosphorylated receptor docking sites and recruits Shc for receptor-associated phosphorylation.

## What the model shows

This compact epidermal growth factor receptor (EGFR) model isolates the earliest steps between extracellular EGF binding and adaptor phosphorylation. It is useful for comparing ligand occupancy, receptor dimer formation, phosphorylation of EGFR Y1068 and Y1173, and phosphorylation of the cytoplasmic adaptor Shc without adding a larger downstream kinase cascade.

## Biological story

Extracellular EGF binds membrane-localized EGFR and enables ligand-bound receptors to dimerize. Dimerization permits phosphorylation at Y1068 and Y1173. Phosphorylated Y1173 recruits Shc from the cytoplasm, after which Shc can be phosphorylated while receptor-bound and can later return to an unphosphorylated cytoplasmic form. Receptor and adaptor phosphatase activity continually opposes these activating steps.

## Main biological players

- **EGF:** the extracellular ligand that initiates receptor assembly.
- **EGFR:** the membrane receptor whose dimerization exposes Y1068 and Y1173 to phosphorylation.
- **Shc:** a cytoplasmic adaptor recruited to phosphorylated Y1173 and modified after recruitment.
- **Grb2:** a declared adaptor with SH2 and SOS-associated regions, although it does not participate in the active mechanism summarized here.

## Mechanism in plain English

EGF binds EGFR at the cell membrane, and two ligand-occupied receptors associate through their transmembrane regions. The dimerized receptors acquire phosphorylation at Y1068 and Y1173, while rapid dephosphorylation continuously removes both marks. Unphosphorylated Shc binds phosphorylated Y1173 and becomes phosphorylated in the receptor complex; phosphorylated Shc can also rebind Y1173, but with different binding kinetics. Once free in the cytoplasm, phosphorylated Shc is gradually dephosphorylated, limiting the duration of the adaptor signal.

## Key modeled events

- Extracellular EGF binds membrane EGFR and creates ligand-occupied receptors.
- Ligand-bound EGFR molecules dimerize, enabling phosphorylation of Y1068 and Y1173.
- Shc is recruited specifically through phosphorylated Y1173 and becomes phosphorylated while associated with EGFR.
- Receptor and Shc dephosphorylation oppose signaling and restore unmodified forms.

## What the model measures

The readouts track total membrane EGFR, extracellular EGF, total cytoplasmic Shc, receptor dimers, phosphorylation at EGFR Y1068 and Y1173, the combined abundance of both receptor phosphosites, and phosphorylated cytoplasmic Shc. Together these measurements separate ligand availability, receptor assembly, receptor activation, and adaptor activation.

## Expected behavior in plots

EGF engagement should be followed by accumulation of EGFR dimers and then phosphorylation at Y1068 and Y1173. Because both receptor sites are opposed by the same strong dephosphorylation process, their signals may be transient or remain low unless dimer formation continues. Shc phosphorylation should depend most directly on phosphorylated Y1173 and may lag behind the receptor phosphosite signal; free phosphorylated Shc should subsequently decline as it is dephosphorylated in the cytoplasm.

## Caveats

The model stops at Shc phosphorylation and does not propagate the signal into Ras, MAPK, PI3K, or transcriptional responses. Grb2 is named as a possible pathway component but is neither initially supplied nor used in the modeled events. Compartment placement distinguishes extracellular ligand, membrane receptor complexes, and cytoplasmic Shc, but it is not a spatial diffusion model.
