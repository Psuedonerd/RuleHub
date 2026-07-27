# Detailed Model Explanation: Kozer 2014 EGFR tetramer recruitment model

## 1. Model identity and scope

`Kozer_2014` models epidermal growth factor (EGF)-dependent epidermal growth factor receptor (EGFR) ectodomain and cytosolic-tail assembly, receptor phosphorylation, and growth-factor-receptor-bound protein 2 (Grb2) recruitment. Sources: `Published/Kozer2014/Kozer_2014.bngl` and `Published/Kozer2014/Kozer_2014_metadata.yaml`.

## 2. BNGL block inventory

The file contains 36 parameters, 3 molecule types, 3 seed species, 16 reaction rules, 15 observables, and 2 inline actions. It has no enclosing model block, compartments, anchors, or functions. Network generation explicitly caps EGF and EGFR stoichiometry at four.

## 3. Parameters, functions, and rate laws

Parameters are grouped by the receptor context they control:

- **Count and volume conversion:** `NA = 6.02e14`, `f = 0.01`, `V = f*1.0e-12`, `cellDen = 6.0e8`, and `Vo = f/cellDen` convert reported concentrations and per-cell counts into simulation molecule numbers.
- **Initial pools:** `LT = 3.0*NA*Vo` for EGF, `RT = 0.09*NA*Vo` for EGFR, and `GT = f*9.0e4` for Grb2.
- **EGF binding by ectodomain context**
  - Non-crosslinked receptor: `K11 = 4.6`, `k11f = 0.09/(NA*Vo)`, `k11r = 0.02`.
  - First ligand on a receptor dimer: `K21 = 5.3`, `k21f = 0.053/(NA*Vo)`, `k21r = 0.02`.
  - Second ligand on a receptor dimer: `K22 = 0.34`, `k22f = 0.136/(NA*Vo)`, `k22r = 0.2`.
- **EGFR ectodomain crosslinking**
  - Two ligand-free receptors: `L20 = 212`, `l20f = 526/(NA*Vo)`, `l20r = 1.24`.
  - One liganded receptor: `L21 = 244`, `l21f = 180/(NA*Vo)`, `l21r = 0.738`.
  - Two liganded receptors: `L22 = 18.0`, `l22f = 9.79/(NA*Vo)`, `l22r = 0.272`.
- **Cytosolic-tail behavior:** ligand-driven opening uses `k_o = 6.0`; closing uses `k_c = 1.6`; open-tail association/dissociation uses `kaf = 15.4/(NA*Vo)`, `kar = 8.89`.
- **Phosphorylation:** `kp = 1` phosphorylates EGFR in an associated-tail pair; `kdp = 1` removes that modification.
- **Ring closure:** `chi_r = 4.37e4*(NA*Vo)` multiplies forward rates for an intracomplex closing edge, where the partners are already held in one tetramer.
- **Grb2 recruitment:** `KDg = 713` and `kmg = 0.31` define the dissociation scale; the association rate is derived as `kpg = (kmg/KDg)/(NA*V)`.

There is no functions block.

## 4. Molecule types, sites, and states

| Molecule type | Site count | Sites/components | Internal states | Anchor/allowed compartments | Binding/modification roles | Notes |
| --- | ---: | --- | --- | --- | --- | --- |
| `EGF` | 1 | `rec` | None | None | `rec` binds `EGFR.lig` | Ligand |
| `EGFR` | 4 | `back`, `lig`, `cd`, `Y` | `cd: c,o`; `Y: u,p` | None | `back` ectodomain crosslinks; `lig` binds EGF; `cd` changes conformation and binds another tail; `Y` is phosphorylated and binds Grb2 | Receptor |
| `Grb2` | 1 | `SH2` | None | None | `SH2` binds `EGFR.Y~p` | Adaptor |

## 5. Compartments, anchors, initial species, and setup

No compartments or anchors are declared. The initial mixture contains free `EGF(rec)` at `LT`, closed/unphosphorylated `EGFR(back,lig,cd~c,Y~u)` at `RT`, and free `Grb2(SH2)` at `GT`.

## 6. Complete reaction-rule inventory

**Rule-family orientation.** Rules 1–9 distinguish ligand-dependent ectodomain association and ring closure. Rules 10–13 open and pair cytosolic tails. Rules 14–16 convert tail pairing into phosphorylation and Grb2 recruitment. The table separates prerequisites, the actual edit, kinetics, and the consequence so topology is readable without reproducing whole BNGL patterns.

| # | Direction | Participants and required context | Bond or state change | Rate(s) | Implementation consequence |
| ---: | --- | --- | --- | --- | --- |
| 1 | Reversible | EGF `rec`; monomeric EGFR `lig` with free `back` | Create/remove `rec–lig` | `k11f`; `k11r` | Ligand occupancy of a receptor not ectodomain-crosslinked. |
| 2 | Reversible | EGF; ligand-free EGFR within a ligand-free `back` dimer | Create/remove `rec–lig` on one dimer member | `k21f`; `k21r` | Adds the first ligand to a preformed ectodomain dimer. |
| 3 | Reversible | EGF; singly liganded EGFR `back` dimer | Create/remove `rec–lig` on the second receptor | `k22f`; `k22r` | Completes ligand occupancy of the dimer. |
| 4 | Reversible | two ligand-free EGFR molecules | Create/remove `back–back` | `l20f`; `l20r` | Forms a ligand-free ectodomain dimer. |
| 5 | Reversible | one ligand-free and one EGF-bound EGFR | Create/remove `back–back` | `l21f`; `l21r` | Forms a singly liganded ectodomain dimer. |
| 6 | Reversible | two EGF-bound EGFR molecules | Create/remove `back–back` | `l22f`; `l22r` | Forms a doubly liganded ectodomain dimer. |
| 7 | Reversible | four-EGFR assembly already tethered through tail and one ectodomain pair; target receptors unliganded | Close/open the remaining `back–back` edge | `chi_r*l20f`; `l20r` | Closes a ligand-free ectodomain ring; `chi_r` represents the high local encounter rate. |
| 8 | Reversible | same four-receptor topology; one target receptor ligand-bound | Close/open remaining `back–back` edge | `chi_r*l21f`; `l21r` | Closes a singly liganded ectodomain ring. |
| 9 | Reversible | same topology; both target receptors ligand-bound | Close/open remaining `back–back` edge | `chi_r*l22f`; `l22r` | Closes a doubly liganded ectodomain ring. |
| 10 | One-way | ligand-bound EGFR | `cd`: `c→o` | `k_o` | Ligand occupancy exposes the cytosolic-tail association state. |
| 11 | One-way | any EGFR with open tail | `cd`: `o→c` | `k_c` | Returns the tail to its closed conformation independently of ligand. |
| 12 | Reversible | two EGFR molecules with `cd~o` | Create/remove `cd–cd` | `kaf`; `kar` | Associates two open cytosolic tails. |
| 13 | Reversible | four-EGFR assembly with two ectodomain edges and one tail edge | Close/open the second `cd–cd` edge | `chi_r*kaf`; `kar` | Completes the cytosolic-tail ring within a preassembled tetramer. |
| 14 | One-way | two receptors joined through open `cd` sites; one has `Y~u` | `Y`: `u→p`; tail bond retained | `kp` | Implements phosphorylation in trans across an associated tail pair. |
| 15 | One-way | any phosphorylated EGFR | `Y`: `p→u` | `kdp` | Erases the Grb2 docking state regardless of oligomer context. |
| 16 | Reversible | Grb2 `SH2`; EGFR `Y~p` | Create/remove `SH2–Y~p` | `kpg`; `kmg` | Loads or unloads Grb2 on phosphorylated receptor. |

## 7. Observables and technical readouts

Molecules `EGFfree` counts unbound `EGF.rec`; `EGFRfree` counts free `EGFR.lig`; `pEGFR` counts `Y~p` whether free or bound; `Grb2_pEGFR` counts the explicit `Y~p!1-SH2!1` complex; and `Grb2Free` counts free `SH2`. Species `Clusters` sums species with exactly 1–4 EGFR; `monomer`, `dimer`, and `trimer` count exactly 1, 2, or 3 EGFR, while `tetramer` uses `EGFR>3`. Species `Grb2EGFRMonomer` counts a phospho-EGFR–Grb2 complex whose receptor `cd` and `back` are unbound. `Grb2EGFRDimer1`/`3` count back-linked dimers with one/two Grb2; `Grb2EGFRDimer2`/`4` count tail-linked dimers with one/two Grb2.

## 8. Actions and simulation workflow

`generate_network({overwrite=>1,max_stoich=>{EGF=>4,EGFR=>4}})` builds a bounded network prohibiting ligand/receptor oligomers above four copies. `simulate_ode({t_end=>120,n_steps=>100})` then integrates that network by ordinary differential equations.

## 9. Technical caveats and ambiguities

The metadata files disagree on some compatibility fields, so the BNGL is authoritative here. `Species Clusters` supplies four adjacent patterns without commas, and `EGFR>3` is nonstandard-looking cardinality syntax whose interpretation depends on the BioNetGen version. Ring-closure rules constrain a particular four-receptor topology; `chi_r` is therefore not a generic oligomerization multiplier. Pattern observables can count embeddings, not necessarily unique physical clusters.
