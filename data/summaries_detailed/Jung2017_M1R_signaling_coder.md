# Coder Model Explanation: Jung 2017

## 1. Model identity and scope

- **Model id:** `Jung_2017`
- **Title:** Jung 2017
- **BNGL path:** `Published/Jung2017/Jung_2017.bngl`
- **YAML path:** `Published/Jung2017/metadata.yaml`
- **Metadata description:** M1 receptor signaling
- **Scope:** This compartmental BNGL model connects extracellular agonist conversion/binding to plasma-membrane M1R, receptor phosphorylation at `S228` and `S273`, arrestin recruitment through `M1R.Arr`/`Arrestin.RLP`, MEK/ERK scaffold assembly on arrestin, PP2A-mediated pERK dephosphorylation, GRK- and CK2-mediated M1R phosphorylation, and a probe/phospho-probe reporter. There are no anchors; localization is expressed directly with `@EC`, `@PM`, and `@cytoplasm` prefixes.

## 2. BNGL block inventory

| Block | Present? | Count / role |
| --- | --- | --- |
| Parameters | Yes | 6 declared parameters for timing/control factors; many rule-rate multipliers are referenced but not declared in this file. |
| Compartments | Yes | 3 compartments: `cytoplasm`, `EC`, and `PM`. |
| Anchors | No | No anchors block; compartment constraints appear directly in patterns. |
| Molecule types | Yes | 13 molecule types. |
| Seed/species | Yes | 27 seed species, many zero-initialized complexes. |
| Observables | Yes | 20 molecule observables. |
| Functions | Yes | 2 time-gating functions: `washing_agonist()` and `off_set()`. |
| Reaction rules | Yes | 19 active rules. |
| Actions | Yes | One `generate_network` command after the model. |

## 3. Parameters, functions, and rate laws

| Parameter | Value/expression | Technical role |
| --- | --- | --- |
| `start` | `60.0` | Timing parameter, not directly referenced by an active rule. |
| `end` | `540.0` | Timing parameter, not directly referenced by an active rule. |
| `time` | `60.0` | Timing parameter, not directly referenced by an active rule. |
| `on_set` | `1.0` | Control parameter, not directly referenced by an active rule. |
| `converting_factor` | `0.0` | Control parameter, not directly referenced by an active rule. |
| `Dephos_factor` | `0.1` | Control parameter; note the rules reference lowercase `dephosphorylation_factor`, not this exact name. |

| Function | Technical interpretation |
| --- | --- |
| `washing_agonist() = (1.0 * (t > 60.0)) && (t < 540.0)` | Time window that gates agonist/M1R binding in rule `R_L_PM`; nonzero only after 60 and before 540. |
| `off_set() = 0.0 * (t > 480.0)` | Always evaluates to zero because of the leading `0.0`; it is not used by an active rule. |

Several rule rates include undeclared names (`RLpp_arrestin_binding_factor`, `negative_arrestin_binding`, `dephosphorylation_factor`, `phos_factor_PP`, `PP2A_dephos_factor`, `MEK_effect`, `GRK_binding_factor`, `RLGRK_pp_dissociation`). Those names must be supplied externally or corrected before standalone execution.

## 4. Molecule types, sites, and states

| Molecule type | Site count | Sites/components | Internal states | Anchor/allowed compartments | Binding/modification roles | Notes |
| --- | ---: | --- | --- | --- | --- | --- |
| `M1R` | 7 | `L`, `S228`, `S273`, `Arr`, `GRK`, `PP1`, `CK2` | `S228`: `u`, `p`; `S273`: `u`, `p` | Directly used at `@PM` | `L` binds `Oxo.R`; `Arr` binds `Arrestin.RLP`; `GRK`, `PP1`, `CK2` bind corresponding kinase/phosphatase `RL` sites; `S228/S273` are receptor state sites. | `PP1` site is seeded but not used by active rules. |
| `Oxo` | 1 | `R` | none | Produced at `@EC`, binds at `@PM` complex product | Binds `M1R.L`. | Agonist ligand represented separately from precursor `Oxo_EC`. |
| `Arrestin` | 3 | `RLP`, `MEK`, `PP2A` | none | Seeded at `@cytoplasm`; complexes appear at `@PM` | `RLP` binds `M1R.Arr`; `MEK` binds `MEK.Arr`; `PP2A` binds `PP2A.Arrestin`. | Acts as scaffold between receptor, MEK, and PP2A. |
| `MEK` | 2 | `Arr`, `ERK` | none | Seeded at `@cytoplasm`; scaffolded complexes at `@PM` | `Arr` binds arrestin; `ERK` binds ERK/pERK `MEK`. | Catalytic role is represented by ERK→pERK conversion in bound complex. |
| `ERK` | 4 | `MEK`, `s`, `PP2A`, `PP1` | `s`: `u` | Primarily `@cytoplasm`, also recruited to `@PM` scaffold | `MEK` binds `MEK.ERK`; `s~u` is unphosphorylated state in the ERK molecule type. | `ERK` and `pERK` are separate molecule types despite state-like names. |
| `pERK` | 4 | `MEK`, `s`, `PP2A`, `PP1` | `s`: `p` | Primarily `@cytoplasm`, also scaffolded at `@PM` | `MEK` binds scaffolded MEK; `PP2A` can bind through `PP2A.ERK`; `s~p` marks phosphorylated ERK type. | Dephosphorylation converts `pERK` molecule type to `ERK`. |
| `Oxo_EC` | 0 | none | none | `@EC` seed; one observable appears with `@cytoplasm`, likely inconsistent | Precursor/source species for `Oxo`. | Rule 8 converts it to `Oxo(R)`. |
| `PP2A` | 2 | `Arrestin`, `ERK` | none | Seeded at `@cytoplasm`; can be scaffolded at `@PM` | `Arrestin` binds arrestin; `ERK` appears bound to ERK/pERK in seed species. | Dephosphorylates pERK in rule 10. |
| `probe` | 1 | `site` | `site`: `u` | `@cytoplasm` | Reporter substrate in rule 16. | Converted to separate `phos_probe` type. |
| `phos_probe` | 1 | `Site0` | `Site0`: `p` | `@cytoplasm` | Reporter product in rule 16. | Separate molecule type rather than state transition on `probe`. |
| `GRK` | 1 | `RL` | none | `@PM` in seed/rules | `RL` binds `M1R.GRK`. | Catalyzes/marks receptor phosphorylation in rule 5. |
| `PP1` | 1 | `RL` | none | Seeded at `@cytoplasm`; one zero seed at `@PM` complex | `RL` can bind `M1R.PP1` in seed species, but no active rule uses it. | Declared/seeded but not active in rules. |
| `CK2` | 1 | `RL` | none | Seeded `@cytoplasm`; complex product at `@PM` | `RL` binds `M1R.CK2`. | Phosphorylates receptor in rule 18. |

## 5. Compartments, anchors, initial species, and setup

Compartments are `cytoplasm` (3D), `EC` (3D), and `PM` (2D). No anchors constrain molecule localization, so each rule’s `@compartment` prefixes define where reactants/products are matched. Initial species include large free `@PM:M1R`, `@EC:Oxo_EC`, cytoplasmic arrestin/MEK/ERK/PP2A/pERK/probe pools, PM-localized GRK, cytoplasmic PP1/CK2, and many zero-initialized receptor/arrestin/MEK/ERK/PP2A/GRK/CK2 complexes used as named starting states.

## 6. Complete reaction-rule inventory

**Rule-family orientation:** The model uses explicit compartment prefixes and mixed molecule-type conversion. Rules 1-3 and 6-7 build ligand/receptor/arrestin/MEK/ERK complexes by forming named site bonds. Rules 4-5 and 18 modify M1R `S228/S273`. Rules 10-12 and 15-16 convert ERK/probe molecule types while preserving catalytic/scaffold molecules on both sides.

| # | Rule label/name | Direction | Participants and sites/components | Rate/expression | Exact modeled change | Technical meaning |
| ---: | --- | --- | --- | --- | --- | --- |
| 1 | `R_L_PM` | reversible | `@EC:Oxo.R` + `@PM:M1R.L`; requires `M1R.S228~u,S273~u` | `20.0 * washing_agonist, 4.0` | Forms/releases `Oxo.R!1`–`M1R.L!1`; product complex is at `@PM`. | Moves agonist binding into a PM receptor complex only during the `washing_agonist()` time window. |
| 2 | `RLppA` | reversible | phosphorylated ligand-bound `M1R.Arr` + `Arrestin.RLP` | `1.0 * RLpp_arrestin_binding_factor, 10.0 * RLpp_arrestin_binding_factor` | Forms/releases `M1R.Arr!2`–`Arrestin.RLP!2`; `M1R.S228/S273` remain `p`. | Arrestin binds phosphorylated agonist-bound receptor. |
| 3 | `RLA` | reversible | unphosphorylated ligand-bound `M1R.Arr` + `Arrestin.RLP` | `0.24 * negative_arrestin_binding, 2.8 * negative_arrestin_binding` | Forms/releases `M1R.Arr!2`–`Arrestin.RLP!2`; `M1R.S228/S273` remain `u`. | Allows weaker/differently scaled arrestin binding to unphosphorylated receptor. |
| 4 | `DeP_RLGRK_pp` | one-way | ligand-bound `M1R.S228~p,S273~p` | `0.5 * dephosphorylation_factor` | `M1R.S228 p→u` and `M1R.S273 p→u`; `Oxo.R!1`–`M1R.L!1` remains. | Dephosphorylates both receptor sites without requiring a bound phosphatase molecule. |
| 5 | `RLGRK_pp` | one-way | `M1R.GRK!2`–`GRK.RL!2` with ligand-bound unphosphorylated receptor | `0.9 * phos_factor_PP` | `M1R.S228 u→p` and `M1R.S273 u→p`; GRK bond remains. | GRK-bound receptor is phosphorylated at both modeled receptor sites. |
| 6 | `RLppAM` | reversible | phosphorylated receptor/arrestin complex, `Arrestin.MEK` + `MEK.Arr` | `0.1, 5.0E-5` | Forms/releases `Arrestin.MEK!3`–`MEK.Arr!3`. | Recruits MEK to phosphorylated receptor-bound arrestin scaffold. |
| 7 | `RLppAME` | reversible | scaffolded `MEK.ERK` + cytoplasmic `ERK.MEK`, `ERK.s~u` | `2.0, 2.5` | Forms/releases `MEK.ERK!4`–`ERK.MEK!4`. | Adds unphosphorylated ERK to the receptor/arrestin/MEK scaffold. |
| 8 | `Oxo_conversion` | one-way | `@EC:Oxo_EC` | `50.0` | Converts `Oxo_EC()` to `Oxo(R)` at `@EC`. | Generates receptor-binding agonist from precursor/source species. |
| 9 | `RLAPP2A` | reversible | unphosphorylated receptor/arrestin complex, `Arrestin.PP2A` + `PP2A.Arrestin` | `3.0E-5, 6.0E-5` | Forms/releases `Arrestin.PP2A!3`–`PP2A.Arrestin!3`. | Recruits PP2A to an arrestin-bound unphosphorylated receptor complex. |
| 10 | `DeP_pERK_PP2A` | reversible with zero reverse | scaffolded PP2A complex + cytoplasmic `pERK.s~p` | `9.0 * PP2A_dephos_factor, 0.0` | Converts free `pERK(MEK,s~p,PP2A,PP1)` to free `ERK(MEK,s~u,PP2A,PP1)`; PP2A scaffold is unchanged. | PP2A-containing receptor/arrestin complex catalytically dephosphorylates cytoplasmic pERK. |
| 11 | `RLppAMpE` | reversible | scaffolded `MEK.ERK!4`–`ERK.MEK!4`; `ERK.s~u` | `9.0 * MEK_effect, 0.36 * MEK_effect` | Converts bound `ERK(s~u)` molecule type to bound `pERK(s~p)` while preserving `MEK.ERK!4`–`pERK.MEK!4`. | MEK scaffold phosphorylates ERK while it remains bound to the MEK site. |
| 12 | `RLppAMpE_dissociation` | reversible with zero reverse | bound `MEK.ERK!4`–`pERK.MEK!4` | `2.0, 0.0` | Releases `pERK` from `MEK.ERK`; `MEK.ERK` becomes free and pERK moves to cytoplasm. | Irreversible-in-practice release of phosphorylated ERK from scaffold because reverse rate is zero. |
| 13 | `RL_GRK` | reversible | ligand-bound unphosphorylated `M1R.GRK` + `GRK.RL` at `@PM` | `4.0 * GRK_binding_factor, 4.0` | Forms/releases `M1R.GRK!2`–`GRK.RL!2`. | Recruits GRK to ligand-bound receptor before phosphorylation. |
| 14 | `RLGRK_pp_dissociation` | reversible | phosphorylated `M1R.GRK!2`–`GRK.RL!2` | `2.0 * RLGRK_pp_dissociation, 2.0 * RLGRK_pp_dissociation` | Releases/forms `M1R.GRK!2`–`GRK.RL!2`; receptor stays phosphorylated. | Lets GRK detach after receptor phosphorylation. |
| 15 | `ERK_balancing` | reversible | cytoplasmic `ERK.s~u` and `pERK.s~p` | `0.1, 1.0` | Converts free `ERK` molecule type to free `pERK`, and reverse converts `pERK` to `ERK`. | Background ERK phosphorylation/dephosphorylation balance independent of scaffold. |
| 16 | `P_probe` | reversible | cytoplasmic `pERK.s~p`, `probe.site~u`, `phos_probe.Site0~p` | `2.0, 2.0` | Forward converts `probe(site~u)` to `phos_probe(Site0~p)` while pERK is preserved; reverse converts reporter product back. | Reporter phosphorylation/dephosphorylation proxy driven by pERK presence. |
| 17 | `RL_CK2_binding` | reversible | ligand-bound unphosphorylated `M1R.CK2` + `CK2.RL` | `5.0E-5, 1.0` | Forms/releases `M1R.CK2!2`–`CK2.RL!2`; product complex is at `@PM`. | Recruits CK2 to ligand-bound receptor. |
| 18 | `RL_CK2_phos` | one-way | `M1R.CK2!2`–`CK2.RL!2` complex | `0.01` | `M1R.S228 u→p` and `M1R.S273 u→p`; CK2 bond remains. | CK2-bound receptor is phosphorylated at both modeled receptor sites. |
| 19 | `RL_CK2_phos_dissociation` | reversible | phosphorylated `M1R.CK2!2`–`CK2.RL!2` | `10.0, 10.0` | Releases/forms `M1R.CK2!2`–`CK2.RL!2`; receptor stays phosphorylated. | CK2 can detach from phosphorylated receptor or rebind it at the same rate. |

## 7. Observables and technical readouts

The 20 `Molecules` observables report compartment-specific pools or complexes: total PM M1R, EC agonist, cytoplasmic arrestin/MEK/ERK/pERK/PP2A/PP1/CK2, receptor-arrestin states (`O0_RLPPA`, `O0_RLA`), receptor phosphorylation (`O0_RLPP`), MEK/ERK scaffolded complexes (`O0_RLPPA_M`, `O0_RLppAME`, `O0_RLppAMpE`), PP2A scaffold recruitment (`O0_RLAPP2A`), and probe/phospho-probe totals. Note that `O0_Oxo_EC_tot` targets `@cytoplasm:Oxo_EC()` even though the seed and conversion rule place `Oxo_EC` at `@EC`; that observable may be inconsistent with the intended pool.

## 8. Actions and simulation workflow

The file calls `generate_network({max_iter=>6,max_agg=>10,max_stoich=>{...},overwrite=>1})`. This generates a bounded reaction network with high stoichiometry caps for all declared molecule types. No simulation command is included.

## 9. Technical caveats and ambiguities

- Several rate-factor identifiers are undeclared locally; this is the major execution caveat.
- The model has compartments but no anchors, so compartment correctness depends entirely on each pattern’s `@` prefix.
- `ERK` and `pERK` are separate molecule types, not one molecule type with `s~u~p`; conversion rules therefore change molecule identity as well as the apparent phosphorylation state.
- `PP1` is declared and seeded but does not participate in active reaction rules.
