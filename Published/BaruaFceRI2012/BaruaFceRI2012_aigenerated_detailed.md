# Detailed Model Explanation: Barua 2012 FcεRI raft-partitioning model

## 1. Model overview

This model examines FcεRI signaling while explicitly distinguishing raft-localized and nonraft molecular states. Ligand-crosslinked receptors recruit Lyn and Syk, drive receptor, Syk, and LAT phosphorylation, and recruit Grb2, while reversible raft partitioning changes encounter rates and protects raft-localized phosphoproteins from dephosphorylation.

## 2. BNGL block inventory

The model contains 49 parameters, six molecule types, nine initial species, 50 active reaction rules, and four molecule-count observables. It has no compartments, anchors, functions, or embedded actions; raft localization is encoded as an internal molecular state rather than a BNGL compartment.

## 3. Parameters, functions, and rate laws

The model represents one of `N = 8000` raft-sized fractions of a cell, so several copy numbers and association rates are divided or multiplied by `N`. Rules use mass-action kinetics, with algebraic parameters defining raft-entry rates, scaled membrane association, and reduced dephosphorylation inside rafts.

| Parameter group or names | Function in this model |
| --- | --- |
| `LigT`, `RecT`, `LynT`, `SykT`, `LATT`, `GrbT`, `N` | Set ligand and protein pools in the simulated raft-sized fraction; receptor, Lyn, Syk, LAT, and Grb2 totals are scaled by `N`. |
| `kon`, `kx`, `koff` | Govern first-arm ligand capture, second-arm receptor crosslinking, and bond dissociation. `kx` is multiplied by `N` to represent a membrane-confined second encounter. |
| `kon_h`, `koff_h` | Parameterize monovalent hapten competition, but the hapten species, seed, and rule are commented out and inactive. |
| `lf`, `lr1`, `lr2` | Control Lyn binding to unphosphorylated receptor β through its unique domain or to phosphorylated β through SH2; the SH2 bond has the slower off-rate. |
| `sf`, `sr`; `gf`, `gr` | Set Syk binding to receptor γ phosphotyrosine and Grb2 binding to phosphorylated LAT. |
| `plb1_o/d`, `plb2_o/d`; `plg1_o/d`, `plg2_o/d` | Specify Lyn-mediated β- and γ-site phosphorylation for unique-domain- or SH2-bound Lyn in raft (`o`) and nonraft (`d`) states. Raft catalytic rates are fivefold higher. |
| `pss1`, `pss2`, `psl` | Control Syk transphosphorylation by inactive or activated Syk and phosphorylation of LAT by receptor-bound Syk. |
| `db`, `dg`, `ds`, `dl`, `z` | Set β, γ, Syk, and LAT dephosphorylation outside rafts; raft rules multiply these rates by the protection coefficient `z = 0.1`. |
| `f`, `Tau`, `Phi_r`, `Phi_d`, `Phi_l`, `Phi_t` | Define raft area fraction, mean lifetime, and partition preferences for receptor monomers, receptor dimers, Lyn, and LAT. |
| `r_o`/`r_d`, `rdimer_o`/`rdimer_d`, `l_o`/`l_d`, `t_o`/`t_d` | Derived entry/exit rates for receptor monomers, receptor dimers, Lyn-containing complexes, and LAT. Their different partition coefficients make dimers, Lyn, and LAT favor the raft state more strongly than receptor monomers. |

There are no active functions; all algebraic scaling is evaluated in the parameter block.

## 4. Molecule types, sites, and states

| Molecule type(s) | Site count | Sites/components | Internal states | Anchor/allowed compartments | Explanation |
| --- | ---: | --- | --- | --- | --- |
| `L` | 2 | two repeated `l` sites | None | None | Bivalent ligand that first binds one FcεRI and then crosslinks a second receptor in the same raft state. |
| `FCR` | 4 | `s`, `a`, `b`, `g` | `s`: nonraft `d`, raft `o`; `b`, `g`: unphosphorylated `Y`, phosphorylated `pY` | None | Lumped FcεRI receptor carrying a ligand site, β and γ signaling sites, and an explicit raft-location state. |
| `Lyn` | 3 | `s`, `U`, `SH2` | `s`: `d`, `o` | None | Src-family kinase that binds receptor β through different domains and phosphorylates neighboring receptors. |
| `Syk` | 2 | `tSH2`, `a` | `a`: `Y`, `pY` | None | Binds phosphorylated receptor γ and undergoes activation-loop transphosphorylation. |
| `LAT` | 2 | `s`, `p` | `s`: `d`, `o`; `p`: `Y`, `pY` | None | Raft-partitioning Syk substrate whose phosphorylation creates a Grb2 docking site. |
| `Grb2` | 1 | `SH2` | None | None | Downstream adaptor recruited to phosphorylated LAT; no later Grb2-mediated reactions are modeled. |

## 5. Compartments, anchors, initial species, and setup

No BNGL compartments or anchors are used. Instead, receptor, Lyn, and LAT carry `s~d` or `s~o`, denoting nonraft and raft states, and rules move whole matched complexes between them. Free receptor is initially divided according to the receptor-monomer partition coefficient, whereas Lyn and LAT use their own stronger raft preferences; Syk and Grb2 have no location state. Ligand begins free, and all receptor, Syk, and LAT phosphorylation variables begin unphosphorylated.

## 6. Reaction-rule inventory

**Rule-family orientation.** Rules 1–9 assemble receptor and adaptor complexes, rules 10–30 create and remove phosphorylation in state-matched signaling assemblies, and rules 31–50 move free molecules and increasingly complex receptor assemblies between nonraft and raft states.

| Rule number(s) | Direction | Involved molecules/sites | Exact modeled change and rate logic | Role within the model |
| ---: | --- | --- | --- | --- |
| 1 | Reversible | Receptor `a`; either ligand `l` arm | Creates the first receptor–ligand bond at `kon` and releases it at `koff`, without constraining receptor raft state. | Captures ligand from solution and prepares a singly occupied ligand for crosslinking. |
| 2–3 | Reversible | Second receptor `a`; free ligand arm; matched receptor `s` state | Adds a second receptor at `kx` or removes it at `koff`; rule 2 handles two nonraft receptors and rule 3 two raft receptors. | Produces signaling receptor dimers without allowing a crosslink to span the two modeled membrane states. |
| 4–7 | Reversible | Receptor β; Lyn `U` or `SH2`; matched `s` states | Rules 4/6 recruit Lyn `U` to unphosphorylated β in nonraft/raft states; rules 5/7 recruit Lyn SH2 to phosphorylated β. All use `lf`, with domain-specific release `lr1` or `lr2`. | Loads Lyn through a phosphorylation-dependent switch in binding mode. |
| 8 | Reversible | Receptor γ pY; Syk `tSH2` | Creates or releases the receptor–Syk bond at `sf` and `sr`. | Couples γ phosphorylation to Syk recruitment. |
| 9 | Reversible | LAT pY; Grb2 `SH2` | Creates or releases the LAT–Grb2 bond at `gf` and `gr`. | Makes phosphorylated LAT the terminal adaptor-recruitment output. |
| 10–17 | One-way | Crosslinked receptors; β or γ sites; receptor-bound Lyn `U` or `SH2` | Rules 10–13 phosphorylate β or γ in rafts; rules 14–17 repeat the same unique-domain/SH2 variants outside rafts. Each maps to its matching `plb...` or `plg...` rate, with raft rates fivefold higher. | Encodes faster Lyn catalysis in raft-localized receptor dimers. |
| 18–19 | One-way | Two Syk molecules; target Syk activation site `a` | An unphosphorylated Syk phosphorylates a partner at `pss1` (18), while an already phosphorylated Syk uses the faster `pss2` rate (19). | Generates positive reinforcement in the Syk activation state. |
| 20–21 | One-way | Receptor-bound Syk; LAT `p`; matched receptor/LAT `s` state | Catalytically changes LAT from `Y` to `pY`; rule 20 acts outside rafts and rule 21 inside, both at `psl`. | Transfers receptor/Syk activity to the LAT adaptor layer. |
| 22–25 | One-way | Receptor β or γ phosphosite and receptor `s` state | Rules 22–23 dephosphorylate nonraft β/γ at `db`/`dg`; rules 24–25 act in rafts at `z × db`/`z × dg`. | Gives raft-localized receptor phosphotyrosines tenfold protection from removal. |
| 26–28 | One-way | Syk activation site `a`; optionally receptor γ bond | Rule 26 dephosphorylates receptor-bound nonraft Syk at `ds`, rule 27 raft-bound Syk at `z × ds`, and rule 28 free Syk at `ds`. | Extends raft protection to Syk only while it remains attached to a raft-state receptor. |
| 29–30 | One-way | LAT `p` and `s` | Removes LAT phosphorylation at `dl` outside rafts and `z × dl` inside rafts. | Makes the LAT output longer-lived in the raft state. |
| 31–34 | Reversible | Receptor `s`, β state, and optional one-arm ligand bond | Moves free or singly ligand-bound receptor between `d` and `o` at receptor-monomer rates; rules 31/33 cover β~Y and 32/34 β~pY. | Partitions monomeric receptor independently of its phosphorylation and ligand occupancy. |
| 35–39 | Reversible | Lyn `s`; optionally receptor β and one-arm ligand | Moves free Lyn or a monomeric receptor–Lyn complex between states at `l_o`/`l_d`; rules 36/38 cover unique-domain complexes and 37/39 SH2 complexes, without/with ligand. | Applies Lyn's strong raft preference to the whole complex it occupies. |
| 40–42 | Reversible | Crosslinked receptor dimer; receptor β states | Moves ligand-crosslinked dimers with zero, one, or two phosphorylated β sites between states at `rdimer_o`/`rdimer_d`. | Gives receptor dimers a distinct raft partition coefficient while preserving dimer topology. |
| 43–49 | Reversible | Crosslinked receptor dimer with one or two Lyn molecules; β phosphorylation/binding mode | Moves the complete dimer–Lyn assembly at `l_o`/`l_d`; rules 43–46 cover one Lyn across β-state combinations, and 47–49 cover two Lyn molecules. | Prevents localization changes from breaking signaling complexes and lets Lyn determine their raft preference. |
| 50 | Reversible | LAT `s` | Switches LAT between nonraft and raft states at `t_o`/`t_d`, regardless of phosphorylation or Grb2 occupancy. | Supplies raft-localized LAT substrate for rule 21 and protects its phosphorylated product through rule 30. |

## 7. Observables and technical readouts

| Observable(s) | Type | What is measured | Technical interpretation |
| --- | --- | --- | --- |
| `pBeta`, `pGamma` | Molecule count | FcεRI molecules with phosphorylated β or γ, whether the site is bound. | Receptor-site outputs pooled across raft and nonraft states; a receptor phosphorylated at both sites contributes to both readouts. |
| `pSyk` | Molecule count | Phosphorylated Syk specifically while its tandem-SH2 site is receptor-bound. | Excludes free phosphorylated Syk, so it measures active receptor-associated Syk rather than total pSyk. |
| `pLAT` | Molecule count | LAT with its signaling site phosphorylated, bound or free and in either membrane state. | Integrates Syk-dependent production and location-dependent dephosphorylation into one downstream readout. |

## 8. Actions and simulation workflow

The BNGL file contains no active actions, so it defines the model but does not itself generate a network or run a trajectory. The metadata lists ODE simulation, implying that an external workflow must generate the network and select integration duration and sampling.

## 9. Technical caveats and ambiguities

- Rafts are abstract internal states, not physical compartments; a transition rewrites all explicitly matched members of a complex to the same state.
- The model represents one `1/N` cell fraction, and several rates are deliberately rescaled by `N`; using it as a full-cell model requires coordinated changes rather than only multiplying outputs.
- A hapten parameter pair and hapten reaction are present only in comments. Because no `Hap` molecule type or seed is active, competitive monovalent inhibition is not part of this model instance.
- The source has no actions and is marked incompatible with both BNG2 and NFsim in metadata; its intended ODE workflow requires external orchestration and parser validation.
