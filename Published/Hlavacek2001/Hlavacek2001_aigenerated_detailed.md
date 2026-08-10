# Detailed Model Explanation: Hlavacek 2001 kinetic-proofreading model

## 1. Model overview

This model implements kinetic proofreading for a symmetric bivalent ligand that sequentially captures two monovalent receptors. Only ligand-crosslinked receptor dimers advance through five irreversible modification stages, while dissociation of either receptor resets the ligand counter, favoring long-lived complexes over rapidly dissociating ones.

## 2. BNGL block inventory

The model contains eight parameters, two molecule types, two seed species, 13 reaction rules, ten species-count observables, four active functions, and actions for network generation, ODE simulation, and a logarithmic dissociation-rate scan. It uses no compartments or anchors.

## 3. Parameters, functions, and rate laws

All reaction rules use mass-action kinetics in molecule counts and seconds. The bimolecular ligand-capture constant is converted using a reference extracellular volume, whereas receptor crosslinking is parameterized as a population-based surface encounter.

| Parameter group or names | Function in this model |
| --- | --- |
| `NA`, `V_ref` | Convert concentration-based ligand capture into a per-molecule-pair rate for an extracellular volume of `10^-9` L per cell. |
| `NR`, `NL` | Set the initial pools to 300,000 receptors and 602 ligand molecules, corresponding locally to a 1 nM ligand condition. |
| `kon1` | Controls capture of the first receptor by either of the ligand's equivalent sites; BioNetGen's site symmetry supplies the multiplicity of two. |
| `kon2` | Controls binding of a second free receptor to singly occupied ligand, thereby forming the signaling dimer. |
| `koff` | Applies independently to either ligand–receptor bond and resets the modification counter after dissociation. |
| `kp` | Advances a fully crosslinked ligand through each of the five proofreading stages at the same first-order rate. |

| Function | Inputs/dependencies | Meaning and use in this model |
| --- | --- | --- |
| `alpha()` | `kp`, `koff` | Computes the probability-like factor `kp/(kp + 2*koff)` that a dimer modifies before either of its two bonds breaks; terminal completion scales as its fifth power under the stated proofreading interpretation. |
| `frac_dimers()` | `Obs_Tot_Dimers`, `NR` | Reports the fraction of the receptor pool residing in ligand-centered dimers, counting two receptors per dimer. |
| `frac_term()` | `Obs_D5`, `Obs_Tot_Dimers` | Reports the terminally modified fraction of existing dimers; the tiny denominator offset prevents division by zero. |
| `frac_R_term()` | `Obs_D5`, `NR` | Reports the fraction of all receptors that are members of terminal dimers. |

## 4. Molecule types, sites, and states

| Molecule type(s) | Site count | Sites/components | Internal states | Anchor/allowed compartments | Explanation |
| --- | ---: | --- | --- | --- | --- |
| `L` | 3 | two repeated `r` sites; `mod` | `mod`: `0`, `1`, `2`, `3`, `4`, `5` | None | Symmetric bivalent ligand that centers the receptor dimer and stores its shared proofreading-stage counter. |
| `R` | 1 | `l` | None | None | Monovalent receptor captured by either ligand site; receptor state is represented entirely by its ligand complex and the ligand's modification counter. |

## 5. Compartments, anchors, initial species, and setup

The model is spatially implicit and has no anchors. It starts with 602 free ligands in modification state 0 and 300,000 free receptors, creating a receptor-rich regime in which first binding and surface crosslinking have distinct rate constants. No complexes or modified dimers are seeded, so every proofreading trajectory begins with ligand capture.

## 6. Reaction-rule inventory

**Rule-family orientation.** Rules 1–2 assemble the singly and doubly receptor-bound ligand. Rules 3–8 implement bond loss with complete modification reset, and rules 9–13 advance intact dimers through the five proofreading stages.

| Rule number(s) | Direction | Involved molecules/sites | Exact modeled change and rate logic | Role within the model |
| ---: | --- | --- | --- | --- |
| 1 | One-way | Free ligand `r` sites in `mod~0`; receptor `l` | Creates one ligand–receptor bond at `kon1`. Either equivalent ligand site can match, giving the appropriate symmetry factor. | Produces the singly occupied intermediate from solution. |
| 2 | One-way | Singly occupied ligand's free `r`; free receptor `l` | Creates the second ligand–receptor bond at `kon2` while keeping `mod~0`. | Forms the receptor dimer required for proofreading progression. |
| 3–8 | One-way | One ligand `r`–receptor `l` bond; ligand `mod` state 0–5, respectively | Breaks a matched bond at `koff`, releases one receptor, and changes the ligand counter to `0` for every starting stage. In a dimer, either of two bonds can match, producing the `2*koff` competition represented in `alpha()`. | Makes any premature dissociation erase accumulated proofreading progress rather than preserve a partially activated complex. |
| 9–13 | One-way | Ligand with both `r` sites bound; `mod` states 0→1→2→3→4→5 | Each rule increments the counter by one at `kp` without altering either receptor bond; rules 9–13 implement the five consecutive transitions. | Creates the delay that discriminates complexes by lifetime and defines state 5 as terminal activation. |

## 7. Observables and technical readouts

| Observable(s) | Type | What is measured | Technical interpretation |
| --- | --- | --- | --- |
| `Obs_Free_L`, `Obs_Free_R` | Species count | Completely free state-0 ligand and free receptor species. | Track depletion of the two starting pools as complexes form. |
| `Obs_Singly_Bound` | Species count | State-0 ligand with one occupied and one free receptor-binding site. | Counts the crosslinking intermediate; repeated equivalent sites may introduce symmetry/embedding considerations in generated species accounting. |
| `Obs_Tot_Dimers` | Species count | Ligand with both receptor-binding sites occupied, regardless of modification stage. | Denominator for terminal yield and basis for the receptor-in-dimers function. |
| `Obs_D0`, `Obs_D1`, `Obs_D2`, `Obs_D3`, `Obs_D4`, `Obs_D5` | Species count | Intact receptor dimers at each successive ligand modification state. | Resolves progression through the proofreading chain; `Obs_D5` is the terminal signaling-competent population. |

## 8. Actions and simulation workflow

The workflow generates a nine-species, 14-reaction network, saves and resets the initial concentrations, and runs a deterministic ODE trajectory for 600 seconds with 300 steps. It then resets again and scans `koff` logarithmically from 0.001 to 1.0 across 30 points, integrating each condition to 1000 seconds to expose how complex lifetime controls dimer completion.

## 9. Technical caveats and ambiguities

- The folder and file use “2001,” while comments also cite a 2002 mathematical treatment; the summary retains the repository's model name rather than choosing between publication labels.
- Modification states 1–5 are abstract proofreading events that may stand for phosphorylation, recruitment, or other steps; they are not assigned to specific molecules or residues.
- Association is encoded as one-way rules and dissociation as separate reset rules, so the reverse of crosslinking is not a simple topology-only reversal.
- Observables are species counts, whereas functions translate those species into receptor fractions; these should not be interpreted as direct unique-molecule observables without the stated factors of two.
