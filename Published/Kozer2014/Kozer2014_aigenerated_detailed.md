# Coder Model Explanation: Kozer 2014 EGFR tetramer recruitment model

## 1. Model identity and scope

`Kozer_2014` models epidermal growth factor (EGF)-dependent epidermal growth factor receptor (EGFR) ectodomain and cytosolic-tail assembly, receptor phosphorylation, and growth-factor-receptor-bound protein 2 (Grb2) recruitment. Sources: `Published/Kozer2014/Kozer_2014.bngl` and `Published/Kozer2014/Kozer_2014_metadata.yaml`.

## 2. BNGL block inventory

The file contains 36 parameters, 3 molecule types, 3 seed species, 16 reaction rules, 15 observables, and 2 inline actions. It has no enclosing model block, compartments, anchors, or functions. Network generation explicitly caps EGF and EGFR stoichiometry at four.

## 3. Parameters, functions, and rate laws

Scaling parameters are `NA=6.02e14`, `f=0.01`, `V=f*1.0e-12`, `cellDen=6.0e8`, and `Vo=f/cellDen`; pool sizes are `LT=3.0*NA*Vo`, `RT=0.09*NA*Vo`, and `GT=f*9.0e4`. EGF-binding groups are `K11=4.6`, `k11r=0.02`, `k11f=0.09/(NA*Vo)`; `K21=5.3`, `k21r=0.02`, `k21f=0.053/(NA*Vo)`; and `K22=0.34`, `k22r=0.2`, `k22f=0.136/(NA*Vo)`. Ectodomain crosslinking uses `L20=212`, `l20r=1.24`, `l20f=526/(NA*Vo)`; `L21=244`, `l21r=0.738`, `l21f=180/(NA*Vo)`; and `L22=18.0`, `l22r=0.272`, `l22f=9.79/(NA*Vo)`. Tail opening/closing uses `k_o=6.0`, `k_c=1.6`; tail binding uses `kaf=15.4/(NA*Vo)`, `kar=8.89`; phosphorylation uses `kp=1`, `kdp=1`; ring closure is enhanced by `chi_r=4.37e4*(NA*Vo)`. Grb2 binding uses `KDg=713`, `kmg=0.31`, and derived `kpg=(kmg/KDg)/(NA*V)`. There are no functions.

## 4. Molecule types, sites, and states

| Molecule type | Site count | Sites/components | Internal states | Anchor/allowed compartments | Binding/modification roles | Notes |
| --- | ---: | --- | --- | --- | --- | --- |
| `EGF` | 1 | `rec` | None | None | `rec` binds `EGFR.lig` | Ligand |
| `EGFR` | 4 | `back`, `lig`, `cd`, `Y` | `cd: c,o`; `Y: u,p` | None | `back` ectodomain crosslinks; `lig` binds EGF; `cd` changes conformation and binds another tail; `Y` is phosphorylated and binds Grb2 | Receptor |
| `Grb2` | 1 | `SH2` | None | None | `SH2` binds `EGFR.Y~p` | Adaptor |

## 5. Compartments, anchors, initial species, and setup

No compartments or anchors are declared. The initial mixture contains free `EGF(rec)` at `LT`, closed/unphosphorylated `EGFR(back,lig,cd~c,Y~u)` at `RT`, and free `Grb2(SH2)` at `GT`.

## 6. Complete reaction-rule inventory

**Rule-family orientation.** Rules 1–3 distinguish EGF affinity by receptor ectodomain context; rules 4–9 form or close ectodomain links; rules 10–13 open and crosslink cytosolic tails; rules 14–16 phosphorylate receptors and recruit Grb2.

| # | Direction | Participants and exact edit | Rate(s) | Technical meaning |
| ---: | --- | --- | --- | --- |
| 1 | Reversible | `EGF.rec` binds `EGFR.lig` on an otherwise `back`-free receptor | `k11f`, `k11r` | Ligand binding to non-crosslinked EGFR. |
| 2 | Reversible | `EGF.rec` binds `lig` on one member of a ligand-free `EGFR.back!1-EGFR.back!1` dimer | `k21f`, `k21r` | First ligand binding to an ectodomain dimer. |
| 3 | Reversible | A second `EGF.rec` binds the free `lig` in a singly liganded `back!2` dimer | `k22f`, `k22r` | Second ligand binding to the dimer. |
| 4 | Reversible | Two unliganded `EGFR.back` sites form bond `!1` | `l20f`, `l20r` | Ligand-free ectodomain crosslinking. |
| 5 | Reversible | Free unliganded `EGFR.back` binds `back` of an EGF-bound EGFR | `l21f`, `l21r` | Singly liganded ectodomain dimerization. |
| 6 | Reversible | `back` sites of two EGF-bound EGFR form bond `!3` | `l22f`, `l22r` | Doubly liganded ectodomain dimerization. |
| 7 | Reversible | In a four-EGFR assembly already joined through `cd` and one `back` pair, the two free, unliganded `back` sites close as bond `!1` | `chi_r*l20f`, `l20r` | Ligand-free ectodomain ring closure. |
| 8 | Reversible | The analogous free `back` pair closes when exactly one targeted receptor has `lig!+` | `chi_r*l21f`, `l21r` | Singly liganded ring closure. |
| 9 | Reversible | The analogous free `back` pair closes when both targeted receptors have `lig!+` | `chi_r*l22f`, `l22r` | Doubly liganded ring closure. |
| 10 | One-way | Ligand-bound `EGFR` changes `cd c→o` | `k_o` | EGF opens the cytosolic tail. |
| 11 | One-way | Any open tail changes `EGFR.cd o→c` | `k_c` | Ligand-independent tail closing. |
| 12 | Reversible | Two open `EGFR.cd~o` sites form bond `!1` | `kaf`, `kar` | Cytosolic-tail association. |
| 13 | Reversible | In a four-EGFR assembly already bearing two `back` bonds and one `cd` bond, the two free open `cd` sites close as bond `!4` | `chi_r*kaf`, `kar` | Tail ring closure. |
| 14 | One-way | Within a `cd~o!1` tail dimer, one receptor changes `Y u→p`; the tail bond remains | `kp` | Transphosphorylation in the associated-tail context. |
| 15 | One-way | Any receptor changes `Y p→u` | `kdp` | EGFR dephosphorylation. |
| 16 | Reversible | `Grb2.SH2` binds `EGFR.Y~p` as bond `!1` | `kpg`, `kmg` | Recruitment of Grb2 to phospho-EGFR. |

## 7. Observables and technical readouts

Molecules `EGFfree` counts unbound `EGF.rec`; `EGFRfree` counts free `EGFR.lig`; `pEGFR` counts `Y~p` whether free or bound; `Grb2_pEGFR` counts the explicit `Y~p!1-SH2!1` complex; and `Grb2Free` counts free `SH2`. Species `Clusters` sums species with exactly 1–4 EGFR; `monomer`, `dimer`, and `trimer` count exactly 1, 2, or 3 EGFR, while `tetramer` uses `EGFR>3`. Species `Grb2EGFRMonomer` counts a phospho-EGFR–Grb2 complex whose receptor `cd` and `back` are unbound. `Grb2EGFRDimer1`/`3` count back-linked dimers with one/two Grb2; `Grb2EGFRDimer2`/`4` count tail-linked dimers with one/two Grb2.

## 8. Actions and simulation workflow

`generate_network({overwrite=>1,max_stoich=>{EGF=>4,EGFR=>4}})` builds a bounded network prohibiting ligand/receptor oligomers above four copies. `simulate_ode({t_end=>120,n_steps=>100})` then integrates that network by ordinary differential equations.

## 9. Technical caveats and ambiguities

The metadata files disagree on some compatibility fields, so the BNGL is authoritative here. `Species Clusters` supplies four adjacent patterns without commas, and `EGFR>3` is nonstandard-looking cardinality syntax whose interpretation depends on the BioNetGen version. Ring-closure rules constrain a particular four-receptor topology; `chi_r` is therefore not a generic oligomerization multiplier. Pattern observables can count embeddings, not necessarily unique physical clusters.
