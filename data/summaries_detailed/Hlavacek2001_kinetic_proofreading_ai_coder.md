# Coder Model Explanation: Hlavacek 2001

## 1. Model identity and scope

- **Model id:** `Hlavacek_2001`
- **Title:** Hlavacek 2001
- **BNGL path:** `Published/Hlavacek2001/kinetic_proofreading_hlavacek2001.bngl`
- **YAML path:** `Published/Hlavacek2001/metadata.yaml`
- **Metadata description:** Kinetic proofreading
- **Scope:** This is a compact kinetic-proofreading model for receptor signaling. A bivalent ligand `L` uses two equivalent `r` sites to bind receptor `R(l)`, forming singly bound ligand and then receptor dimers. The ligand carries a `mod` state counter (`0` through `5`) that advances only while both ligand sites are receptor-bound. Any ligand-receptor bond dissociation resets `L.mod` to `0`.

## 2. BNGL block inventory

| Block | Present? | Count / role |
| --- | --- | --- |
| Parameters | Yes | 8 parameters for copy-number conversion, ligand/receptor totals, binding, unbinding, and proofreading modification. |
| Compartments | No | No explicit compartments. |
| Anchors | No | No anchors. |
| Molecule types | Yes | 2 molecule types: bivalent ligand `L` and receptor `R`. |
| Seed/species | Yes | 2 initial species: free ligand and free receptor. |
| Observables | Yes | 10 species observables for free pools, singly bound ligand, total dimers, and dimer modification states. |
| Functions | Yes | 4 derived readouts: `alpha`, dimer fraction, terminal fraction, receptor-terminal fraction. |
| Reaction rules | Yes | 13 concrete rules. |
| Actions | Yes | Network generation, concentration saving, ODE time course, and `koff` scan. |

## 3. Parameters, functions, and rate laws

| Parameter | Value/expression | Technical role |
| --- | --- | --- |
| `NA` | `6.02214076e23` | Avogadro constant used in concentration-to-population conversion comments. |
| `V_ref` | `1e-9` | Extracellular volume per cell. |
| `NR` | `300000` | Total receptor copy number. |
| `NL` | `602` | Total ligand copy number at the modeled concentration. |
| `kon1` | `1.661e-8` | First ligand-site receptor-capture rate; BNGL symmetry handles two equivalent `L.r` sites. |
| `kon2` | `3.333e-6` | Crosslinking rate for the second receptor binding event. |
| `koff` | `0.1` | Per-bond ligand-receptor dissociation rate. |
| `kp` | `0.4` | Unidirectional modification-step rate for fully receptor-crosslinked ligand. |

**Functions and derived readouts**

| Function | Technical interpretation |
| --- | --- |
| `alpha() = kp / (kp + 2 * koff)` | Probability-like proofreading factor: modification competes against two possible dimer bond breaks. |
| `frac_dimers() = 2 * Obs_Tot_Dimers / NR` | Fraction of receptors present in dimers. |
| `frac_term() = Obs_D5 / (Obs_Tot_Dimers + 1e-30)` | Fraction of dimers that reached terminal modification state `mod~5`; small denominator offset prevents division by zero. |
| `frac_R_term() = 2 * Obs_D5 / NR` | Fraction of all receptors in terminal dimers. |

## 4. Molecule types, sites, and states

| Molecule type | Site count | Sites/components | Internal states | Anchor/allowed compartments | Binding/modification roles | Notes |
| --- | ---: | --- | --- | --- | --- | --- |
| `L` | 3 | `r`, `r`, `mod` | `mod~0~1~2~3~4~5` | none | The two repeated `r` components are equivalent receptor-binding sites; `mod` is the proofreading counter. | `L.mod` is the implementation state for dimer progress, even though the biological interpretation is receptor modification. |
| `R` | 1 | `l` | none | none | `R.l` binds ligand site `L.r`. | Receptor has no explicit modification state; reset behavior is represented by `L.mod`. |

## 5. Compartments, anchors, initial species, and setup

- Compartments: none declared.
- Anchors: none declared.
- Initial setup: all ligand starts unbound with `mod~0`; all receptor starts free.

| Initial species/pattern | Initial amount | Setup role |
| --- | --- | --- |
| `L(r,r,mod~0)` | `NL` | Free bivalent ligand with both `r` sites open and proofreading counter at zero. |
| `R(l)` | `NR` | Free monovalent receptor with ligand-binding site `l` open. |

## 6. Complete reaction-rule inventory

**Rule-family orientation:** Rules 1-2 build ligand-receptor complexes through `L.r`/`R.l` bonds. Rules 3-8 are dissociation/reset rules: breaking `L.r!1`/`R.l!1` releases receptor and sets `L.mod` to `0`. Rules 9-13 advance `L.mod` from `0` to `5`, but only for ligands with both repeated `r` sites bound (`L(r!+,r!+)`).

| # | Rule label/name | Direction | Participants and sites/components | Rate/expression | Exact modeled change | Technical meaning |
| ---: | --- | --- | --- | --- | --- | --- |
| 1 | `Unlabeled` | one-way | `L.r` + `R.l` | `kon1` | Forms one `L.r!1`–`R.l!1` bond while `L.mod` remains `0`; the second `L.r` stays free. | Ligand capture: free bivalent ligand binds one receptor. Because `L` has two equivalent `r` sites, BioNetGen applies the symmetry factor for either site being used. |
| 2 | `Unlabeled` | one-way | free `L.r` on singly bound ligand + `R.l` | `kon2` | Forms an additional `L.r!1`–`R.l!1` bond on a ligand already carrying one receptor; `L.mod` remains `0`. | Receptor crosslinking: singly bound ligand recruits a second receptor to form a dimer scaffold capable of proofreading modification. |
| 3 | `Unlabeled` | one-way | `L.r!1`, `R.l!1`, `L.mod~0` | `koff` | Releases the ligand-receptor bond; `L.mod` stays `0`. | Dissociation of an unmodified singly/doubly bound ligand-receptor contact. No reset is visible because the counter is already zero. |
| 4 | `Unlabeled` | one-way | `L.r!1`, `R.l!1`, `L.mod~1` | `koff` | Releases `L.r!1`–`R.l!1` and resets `L.mod 1→0`. | A dimer that completed one proofreading step loses a receptor bond and immediately returns to basal ligand state. |
| 5 | `Unlabeled` | one-way | `L.r!1`, `R.l!1`, `L.mod~2` | `koff` | Releases `L.r!1`–`R.l!1` and resets `L.mod 2→0`. | Encodes proofreading loss after two completed modification steps. |
| 6 | `Unlabeled` | one-way | `L.r!1`, `R.l!1`, `L.mod~3` | `koff` | Releases `L.r!1`–`R.l!1` and resets `L.mod 3→0`. | Encodes proofreading loss after three completed modification steps. |
| 7 | `Unlabeled` | one-way | `L.r!1`, `R.l!1`, `L.mod~4` | `koff` | Releases `L.r!1`–`R.l!1` and resets `L.mod 4→0`. | Encodes proofreading loss after four completed modification steps. |
| 8 | `Unlabeled` | one-way | `L.r!1`, `R.l!1`, `L.mod~5` | `koff` | Releases `L.r!1`–`R.l!1` and resets `L.mod 5→0`. | Even terminally modified dimers lose the proofreading state when a ligand-receptor bond breaks. |
| 9 | `Unlabeled` | one-way | `L(r!+,r!+)`, `L.mod~0` | `kp` | Changes `L.mod 0→1`; both `L.r` sites must be bound. | First proofreading modification step on a receptor dimer. |
| 10 | `Unlabeled` | one-way | `L(r!+,r!+)`, `L.mod~1` | `kp` | Changes `L.mod 1→2`; both `L.r` sites remain bound. | Second proofreading modification step. |
| 11 | `Unlabeled` | one-way | `L(r!+,r!+)`, `L.mod~2` | `kp` | Changes `L.mod 2→3`; both `L.r` sites remain bound. | Third proofreading modification step. |
| 12 | `Unlabeled` | one-way | `L(r!+,r!+)`, `L.mod~3` | `kp` | Changes `L.mod 3→4`; both `L.r` sites remain bound. | Fourth proofreading modification step. |
| 13 | `Unlabeled` | one-way | `L(r!+,r!+)`, `L.mod~4` | `kp` | Changes `L.mod 4→5`; both `L.r` sites remain bound. | Terminal proofreading step producing the `Obs_D5` signaling readout. |

## 7. Observables and technical readouts

| Observable | Type | Pattern / target | Technical interpretation |
| --- | --- | --- | --- |
| `Obs_Free_L` | `Species` | `L(r,r,mod~0)` | Free ligand with both `r` sites unbound and counter zero. |
| `Obs_Free_R` | `Species` | `R(l)` | Free receptor with open `l` site. |
| `Obs_Singly_Bound` | `Species` | `L(r!+,r,mod~0)` | Ligand with one receptor bound and one `r` site free. |
| `Obs_Tot_Dimers` | `Species` | `L(r!+,r!+)` | Ligand with both `r` sites bound, regardless of modification state. |
| `Obs_D0` | `Species` | `L(r!+,r!+,mod~0)` | Dimer before any proofreading modification. |
| `Obs_D1` | `Species` | `L(r!+,r!+,mod~1)` | Dimer after one modification. |
| `Obs_D2` | `Species` | `L(r!+,r!+,mod~2)` | Dimer after two modifications. |
| `Obs_D3` | `Species` | `L(r!+,r!+,mod~3)` | Dimer after three modifications. |
| `Obs_D4` | `Species` | `L(r!+,r!+,mod~4)` | Dimer after four modifications. |
| `Obs_D5` | `Species` | `L(r!+,r!+,mod~5)` | Terminally modified dimer. |

## 8. Actions and simulation workflow

1. `generate_network({overwrite=>1})` builds the small reaction network.
2. `saveConcentrations()` requests output.
3. `resetConcentrations()` restores all-free ligand/receptor initial conditions.
4. `simulate({method=>"ode", suffix=>"ode", t_start=>0, t_end=>600, n_steps=>300})` runs the proofreading time course.
5. A second `resetConcentrations()` prepares the `koff` scan.
6. `parameter_scan({method=>"ode", parameter=>"koff", ...})` scans dissociation rate to show proofreading sensitivity.

## 9. Technical caveats and ambiguities

- The model stores modification progress on ligand `L.mod`, not on receptor `R`; this is an implementation choice for dimer state.
- The repeated `L.r` components are equivalent, so symmetry factors are part of the intended kinetics.
- There are no compartments; receptor surface context is encoded by rates and molecule naming rather than explicit membrane localization.
