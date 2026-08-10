# Detailed Model Explanation: Blinov EGFR signaling model

## 1. Model overview

This compact model follows extracellular EGF binding, membrane EGFR dimerization, phosphorylation of EGFR Y1068 and Y1173, and recruitment and phosphorylation of cytosolic Shc. It is a spatially constrained rule-based model intended for direct network-free simulation rather than a comprehensive EGFR pathway.

## 2. BNGL block inventory

The model contains three compartments, four molecule types, two anchors, three seed species, ten reaction rules, eight molecule-count observables, and one network-free simulation action. The parameter and function blocks are present but empty; all kinetic constants are written directly on the rules.

## 3. Parameters, functions, and rate laws

There is no named parameter namespace. Each rule uses a numeric mass-action rate, with two values for reversible association/state-change rules and one value for irreversible phosphorylation or dephosphorylation.

| Parameter group or names | Function in this model |
| --- | --- |
| EGF–EGFR binding rates `0.003`, `0.06` | Set ligand capture and release at the receptor extracellular domain. |
| EGFR dimerization rates `0.001`, `0.01` | Set formation and dissociation of the transmembrane-domain bond between two ligand-occupied receptors. |
| EGFR phosphorylation rate `0.01` | Independently converts Y1068 or Y1173 from unphosphorylated to phosphorylated, but only for dimerized receptors. |
| EGFR dephosphorylation rate `4.505` | Removes phosphorylation from either Y1068 or Y1173 regardless of dimer occupancy. |
| Shc recruitment rates `0.045`/`0.6` and `4.5e-4`/`0.3` | Recruit unphosphorylated or phosphorylated Shc, respectively, to EGFR pY1173. The hundredfold lower on-rate for phosphorylated Shc makes its rebinding much weaker. |
| Shc state-change rates `3.0`, `0.03`; cytosolic dephosphorylation `0.005` | Drive Shc toward phosphorylation while receptor-bound, allow the reverse bound-state transition, and slowly reset released cytosolic Shc. |

There are no active functions; no rate depends on an observable or a computed expression.

## 4. Molecule types, sites, and states

| Molecule type(s) | Site count | Sites/components | Internal states | Anchor/allowed compartments | Explanation |
| --- | ---: | --- | --- | --- | --- |
| `EGFR` | 4 | `ecd`, `tmd`, `y1068`, `y1173` | `y1068`, `y1173`: `u`, `p` | Anchored to `M` | Membrane receptor whose extracellular site binds EGF, transmembrane site dimerizes, and two tyrosines report receptor activation. |
| `EGF` | 1 | `rb` | None | Allowed in `EC` and `M` | Soluble ligand that starts extracellularly and becomes membrane-localized as part of an EGFR complex. |
| `Shc` | 2 | `sh3`, `Y773` | `Y773`: `u`, `p` | None; seeded in `Cyt` | Cytosolic adaptor recruited to EGFR pY1173 and phosphorylated while receptor-bound. |
| `Grb2` | 2 | `sh2`, `sos` | None | None | Declared downstream adaptor, but it has no seed, rule, or observable and therefore does not participate in this model instance. |

## 5. Compartments, anchors, initial species, and setup

`EC` and `Cyt` are three-dimensional compartments and `M` is a two-dimensional membrane; all have unit size, with no explicit parent hierarchy. EGFR is constrained to the membrane, while EGF may occur extracellularly or in a membrane complex. The initial pools are 680 extracellular EGF molecules, 602 unbound and unphosphorylated membrane EGFR molecules, and 150 unphosphorylated cytosolic Shc molecules; Grb2 has no initial population.

## 6. Reaction-rule inventory

**Rule-family orientation.** Rules 1–2 assemble ligand-bound EGFR dimers, rules 3–6 turn over the two receptor phosphotyrosines, and rules 7–10 couple EGFR pY1173 to Shc recruitment and phosphorylation.

| Rule number(s) | Direction | Involved molecules/sites | Exact modeled change and rate logic | Role within the model |
| ---: | --- | --- | --- | --- |
| 1 | Reversible | EGF `rb`; EGFR `ecd` and free `tmd` | Creates or releases an EGF–EGFR extracellular-domain bond at `0.003` forward and `0.06` reverse; the complex is membrane-localized. | Supplies ligand-occupied receptors that are eligible for dimerization. |
| 2 | Reversible | Two ligand-bound EGFR molecules; each `tmd` | Creates or releases a bond between the two transmembrane sites at `0.001` and `0.01`. Distinct reactant labels ensure two receptor instances are joined. | Forms the signaling-competent EGFR dimer. |
| 3, 6 | One-way | EGFR Y1173 (rule 3) or Y1068 (rule 6) | Changes the selected site from `p` to `u` at `4.505`, without requiring dimerization. | Rapidly terminates receptor phosphosite occupancy. |
| 4–5 | One-way | Dimerized EGFR `tmd`; Y1068 (rule 4) or Y1173 (rule 5) | Changes the selected site from `u` to `p` at `0.01` while preserving the dimer bond. | Converts receptor dimerization into two independent phosphorylation outputs. |
| 7 | Reversible | EGFR pY1173; unphosphorylated Shc `sh3`/Y773 | Creates or releases the pY1173–Shc recruitment bond at `0.045` and `0.6`. | Brings inactive Shc to activated receptor. |
| 8 | Reversible | EGFR-bound Shc Y773 | Changes Y773 between `u` and `p` while leaving Shc attached, with phosphorylation favored by rates `3.0` versus `0.03`. | Makes receptor occupancy catalytically activate Shc. |
| 9 | One-way | Free cytosolic Shc pY773 | Changes Y773 from `p` to `u` at `0.005`. | Slowly resets phosphorylated Shc after it leaves the receptor. |
| 10 | Reversible | EGFR pY1173; phosphorylated Shc `sh3` | Recruits or releases already-phosphorylated Shc at `4.5e-4` and `0.3`. | Allows Shc product rebinding but makes it less favorable than recruitment of inactive Shc. |

## 7. Observables and technical readouts

| Observable(s) | Type | What is measured | Technical interpretation |
| --- | --- | --- | --- |
| `EGFR_tot` | Molecule count | All membrane EGFR molecules. | Conserved receptor-pool readout across free, ligand-bound, dimerized, and Shc-bound forms. |
| `EGF_EC` | Molecule count | EGF molecules located in the extracellular compartment. | Falls when EGF becomes part of a membrane-localized receptor complex and rises on release. |
| `Shc_cyt` | Molecule count | Shc molecules located in the cytosol. | Excludes receptor-bound membrane Shc and therefore reports the free adaptor pool. |
| `Dimers` | Molecule count | Membrane EGFR molecules whose `tmd` site is bonded. | Counts receptor molecules in dimers, so one EGFR dimer contributes two matched EGFR molecules rather than one complex. |
| `Y1068_phosp`, `Y1173_phosp` | Molecule count | EGFR phosphorylated at the named site, whether that site is bound or free. | Site-specific receptor outputs; a doubly phosphorylated receptor contributes to both observables. |
| `Total_phosp` | Molecule count | Sum of matches to EGFR pY1068 and EGFR pY1173. | Counts phosphorylated sites rather than uniquely phosphorylated receptors; a receptor phosphorylated at both sites contributes twice. |
| `ShcP_Cyt` | Molecule count | Cytosolic Shc phosphorylated at Y773. | Measures released phospho-Shc, not the receptor-bound phosphorylated pool. |

## 8. Actions and simulation workflow

The model is simulated directly with NFsim for 120 time units, recording 240 steps. It does not explicitly generate a reaction network, equilibrate, change parameters, or export structures before the network-free trajectory.

## 9. Technical caveats and ambiguities

- The metadata says `uses_functions: true`, but the active functions block is empty; the model uses only literal numeric rates.
- The README and metadata disagree about BNG2 compatibility, while the model also uses compartments, anchors, match-once labels, and `simulate_nf`; execution should be checked with the intended BioNetGen/NFsim version.
- Grb2 is declared but absent from seeds and rules, so the model stops at Shc phosphorylation rather than continuing into a Grb2/SOS branch.
- The site name `Shc.Y773` is retained as written; its biological residue mapping is not independently established by the local files.
