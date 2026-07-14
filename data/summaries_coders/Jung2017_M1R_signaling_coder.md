# Coder Model Explanation: Jung 2017

## 1. Model identity and scope

- **Model id:** `Jung_2017`
- **Title:** Jung 2017
- **BNGL path:** `Published/Jung2017/Jung_2017.bngl`
- **YAML path:** `Published/Jung2017/metadata.yaml`
- **Metadata description:** M1 receptor signaling
- **Scope:** A compartmental M1 muscarinic receptor signaling model in which extracellular oxotremorine binds plasma-membrane M1R, receptor phosphorylation controls arrestin recruitment, arrestin scaffolds MEK/ERK/PP2A, and ERK phosphorylation is tracked through pERK and probe readouts.

## 2. BNGL block inventory

| Block | Present? | Count / role |
| --- | --- | --- |
| Parameters | Yes | 6 parameter entries. |
| Compartments | Yes | 3 compartment entries. |
| Anchors | No | 0 anchor entries. |
| Molecule types | Yes | 13 molecule type entries. |
| Seed/species | Yes | 27 initial species entries. |
| Observables | Yes | 20 observable entries. |
| Functions | Yes | 2 function entries. |
| Reaction rules | Yes | 19 reaction rules. |
| Actions | Yes | 1 active action or inline execution commands. |

## 3. Parameters, functions, and rate laws

The parameter table is complete for this small model and preserves source comments when available.

| Parameter | Value/expression | Role / source comment |
| --- | --- | --- |
| `start` | `60.0` | kinetic or model-control parameter |
| `end` | `540.0` | kinetic or model-control parameter |
| `time` | `60.0` | kinetic or model-control parameter |
| `on_set` | `1.0` | kinetic or model-control parameter |
| `converting_factor` | `0.0` | kinetic or model-control parameter |
| `Dephos_factor` | `0.1` | kinetic or model-control parameter |

**Functions and derived rates**

| Function | Technical interpretation |
| --- | --- |
| `washing_agonist()	=	(1.0 * (t > 60.0)) && (t < 540.0)` | derived rate/readout expression used by rules, observables, or simulation output |
| `off_set()	=	0.0 * (t > 480.0)` | derived rate/readout expression used by rules, observables, or simulation output |

## 4. Molecule types, sites, and states

| Molecule type | Site count | Sites/components | Internal states | Anchor/allowed compartments | Binding/modification roles | Notes |
| --- | ---: | --- | --- | --- | --- | --- |
| `M1R` | 7 | L, S228~u~p, S273~u~p, Arr, GRK, PP1, CK2 | S228: u, p; S273: u, p | none | binding/modification candidate sites: L, S228, S273, Arr, GRK, PP1, CK2 |  |
| `Oxo` | 1 | R | none declared | none | binding/modification candidate sites: R |  |
| `Arrestin` | 3 | RLP, MEK, PP2A | none declared | none | binding/modification candidate sites: RLP, PP2A |  |
| `MEK` | 2 | Arr, ERK | none declared | none | binding/modification candidate sites: Arr, ERK |  |
| `ERK` | 4 | MEK, s~u, PP2A, PP1 | s: u | none | binding/modification candidate sites: PP2A, PP1 |  |
| `pERK` | 4 | MEK, s~p, PP2A, PP1 | s: p | none | binding/modification candidate sites: PP2A, PP1 |  |
| `Oxo_EC` | 0 | none | none declared | none | no explicit binding/modification site role beyond whole-molecule abundance |  |
| `PP2A` | 2 | Arrestin, ERK | none declared | none | binding/modification candidate sites: Arrestin, ERK |  |
| `probe` | 1 | site~u | site: u | none | binding/modification candidate sites: site |  |
| `phos_probe` | 1 | Site0~p | Site0: p | none | binding/modification candidate sites: Site0 |  |
| `GRK` | 1 | RL | none declared | none | binding/modification candidate sites: RL |  |
| `PP1` | 1 | RL | none declared | none | binding/modification candidate sites: RL |  |
| `CK2` | 1 | RL | none declared | none | binding/modification candidate sites: RL |  |

## 5. Compartments, anchors, initial species, and setup

- Compartments: cytoplasm	3	1; EC	3	1; PM	2	1.

- Anchors: none declared.

| Initial species/pattern | Initial amount | Setup role |
| --- | --- | --- |
| `1 @EC:Oxo_EC()` | `100.0` | starting species pool for this pattern |
| `2 @PM:M1R(L,S228~u,S273~u,Arr,GRK,PP1,CK2)` | `3500.0` | starting species pool for this pattern |
| `3 @PM:Oxo(R!1).M1R(L!1,S228~u,S273~u,Arr,GRK,PP1,CK2)` | `0.0` | starting species pool for this pattern |
| `4 @cytoplasm:Arrestin(RLP,MEK,PP2A)` | `15.0` | starting species pool for this pattern |
| `5 @PM:Oxo(R!1).M1R(L!1,S228~p,S273~p,Arr!2,GRK,PP1,CK2).Arrestin(RLP!2,MEK,PP2A)` | `0.0` | starting species pool for this pattern |
| `6 @PM:Oxo(R!1).M1R(L!1,S228~p,S273~p,Arr!2,GRK,PP1,CK2).Arrestin(RLP!2,MEK!3,PP2A).MEK(Arr!3,ERK)` | `0.0` | starting species pool for this pattern |
| `7 @cytoplasm:ERK(MEK,s~u,PP2A,PP1)` | `1.0` | starting species pool for this pattern |
| `8 @cytoplasm:MEK(Arr,ERK)` | `1.0` | starting species pool for this pattern |
| `9 @cytoplasm:PP2A(Arrestin,ERK)` | `5.0` | starting species pool for this pattern |
| `10 @cytoplasm:pERK(MEK,s~p,PP2A,PP1)` | `0.1` | starting species pool for this pattern |
| `11 @PM:Oxo(R!1).M1R(L!1,S228~p,S273~p,Arr!2,GRK,PP1,CK2).Arrestin(RLP!2,MEK!3,PP2A).MEK(Arr!3,ERK!4).ERK(MEK!4,s~u,PP2A,PP1)` | `0.0` | starting species pool for this pattern |
| `12 @PM:Oxo(R!1).M1R(L!1,S228~p,S273~p,Arr!2,GRK,PP1,CK2).Arrestin(RLP!2,MEK!3,PP2A).MEK(Arr!3,ERK!4).pERK(MEK!4,s~p,PP2A,PP1)` | `0.0` | starting species pool for this pattern |
| `13 @PM:Oxo(R!1).M1R(L!1,S228~u,S273~u,Arr!2,GRK,PP1,CK2).Arrestin(RLP!2,MEK,PP2A)` | `0.0` | starting species pool for this pattern |
| `14 @PM:Oxo(R!1).M1R(L!1,S228~u,S273~u,Arr!2,GRK,PP1,CK2).Arrestin(RLP!2,MEK,PP2A!3).PP2A(Arrestin!3,ERK)` | `0.0` | starting species pool for this pattern |
| `15 @cytoplasm:probe(site~u)` | `5.0` | starting species pool for this pattern |
| `16 @cytoplasm:phos_probe(Site0~p)` | `5.0` | starting species pool for this pattern |
| `17 @PM:GRK(RL)` | `10.0` | starting species pool for this pattern |
| `18 @PM:Oxo(R!1).M1R(L!1,S228~u,S273~u,Arr,GRK!2,PP1,CK2).GRK(RL!2)` | `0.0` | starting species pool for this pattern |
| `19 @PM:Oxo(R!1).M1R(L!1,S228~p,S273~p,Arr,GRK!2,PP1,CK2).GRK(RL!2)` | `0.0` | starting species pool for this pattern |
| `20 @PM:Oxo(R!1).M1R(L!1,S228~p,S273~p,Arr,GRK,PP1,CK2)` | `0.0` | starting species pool for this pattern |
| `21 @PM:Oxo(R!1).M1R(L!1,S228~u,S273~u,Arr!2,GRK,PP1,CK2).Arrestin(RLP!2,MEK,PP2A!3).PP2A(Arrestin!3,ERK!4).pERK(MEK,s~p,PP2A!4,PP1)` | `0.0` | starting species pool for this pattern |
| `22 @PM:Oxo(R!1).M1R(L!1,S228~u,S273~u,Arr!2,GRK,PP1,CK2).Arrestin(RLP!2,MEK,PP2A!3).PP2A(Arrestin!3,ERK!4).ERK(MEK,s~u,PP2A!4,PP1)` | `0.0` | starting species pool for this pattern |
| `23 @PM:Oxo(R!1).M1R(L!1,S228~u,S273~u,Arr,GRK,PP1!2,CK2).PP1(RL!2)` | `0.0` | starting species pool for this pattern |
| `24 @cytoplasm:PP1(RL)` | `1.0` | starting species pool for this pattern |
| `25 @cytoplasm:CK2(RL)` | `1.0` | starting species pool for this pattern |
| `26 @PM:Oxo(R!1).M1R(L!1,S228~u,S273~u,Arr,GRK,PP1,CK2!2).CK2(RL!2)` | `0.0` | starting species pool for this pattern |
| `27 @PM:Oxo(R!1).M1R(L!1,S228~p,S273~p,Arr,GRK,PP1,CK2!2).CK2(RL!2)` | `0.0` | starting species pool for this pattern |

## 6. Complete reaction-rule inventory

The source contains **19** reaction rules. Every concrete rule is listed below.

| # | Rule label/name | Direction | Participants and sites/components | Rate/expression | Modeled change | Rule pattern | Technical meaning |
| ---: | --- | --- | --- | --- | --- | --- | --- |
| 1 | `R_L_PM` | reversible | M1R, Oxo | `20.0 * washing_agonist, 4.0` | binding-pattern rewrite | `@EC:Oxo(R) + @PM:M1R(L,S228~u,S273~u,Arr,GRK,PP1,CK2) <-> @PM:Oxo(R!1).M1R(L!1,S228~u,S273~u,Arr,GRK,PP1,CK2)` | Reversibly forms binding contacts among M1R, Oxo through M1R.L, Oxo.R. Rate/expression: 20.0 * washing_agonist, 4.0. |
| 2 | `RLppA` | reversible | Arrestin, M1R, Oxo | `1.0 * RLpp_arrestin_binding_factor, 10.0 * RLpp_arrestin_binding_factor` | binding-pattern rewrite | `@PM:Oxo(R!1).M1R(L!1,S228~p,S273~p,Arr,GRK,PP1,CK2) + @cytoplasm:Arrestin(RLP,MEK,PP2A) <-> @PM:Oxo(R!1).M1R(L!1,S228~p,S273~p,Arr!2,GRK,PP1,CK2).Arrestin(RLP!2,MEK,PP2A)` | Reversibly forms binding contacts among Arrestin, M1R, Oxo through Arrestin.RLP, M1R.Arr. Rate/expression: 1.0 * RLpp_arrestin_binding_factor, 10.0 * RLpp_arrestin_binding_factor. |
| 3 | `RLA` | reversible | Arrestin, M1R, Oxo | `0.24 * negative_arrestin_binding, 2.8 * negative_arrestin_binding` | binding-pattern rewrite | `@PM:Oxo(R!1).M1R(L!1,S228~u,S273~u,Arr,GRK,PP1,CK2) + @cytoplasm:Arrestin(RLP,MEK,PP2A) <-> @PM:Oxo(R!1).M1R(L!1,S228~u,S273~u,Arr!2,GRK,PP1,CK2).Arrestin(RLP!2,MEK,PP2A)` | Reversibly forms binding contacts among Arrestin, M1R, Oxo through Arrestin.RLP, M1R.Arr. Rate/expression: 0.24 * negative_arrestin_binding, 2.8 * negative_arrestin_binding. |
| 4 | `DeP_RLGRK_pp` | one-way | M1R, Oxo | `0.5 * dephosphorylation_factor` | internal-state conversion/modification | `@PM:Oxo(R!1).M1R(L!1,S228~p,S273~p,Arr,GRK,PP1,CK2) -> @PM:Oxo(R!1).M1R(L!1,S228~u,S273~u,Arr,GRK,PP1,CK2)` | Updates internal state(s) on M1R, Oxo: M1R.S228 p→u, M1R.S273 p→u. Rate/expression: 0.5 * dephosphorylation_factor. |
| 5 | `RLGRK_pp` | one-way | GRK, M1R, Oxo | `0.9 * phos_factor_PP` | internal-state conversion/modification | `@PM:Oxo(R!1).M1R(L!1,S228~u,S273~u,Arr,GRK!2,PP1,CK2).GRK(RL!2) -> @PM:Oxo(R!1).M1R(L!1,S228~p,S273~p,Arr,GRK!2,PP1,CK2).GRK(RL!2)` | Updates internal state(s) on GRK, M1R, Oxo: M1R.S228 u→p, M1R.S273 u→p. Rate/expression: 0.9 * phos_factor_PP. |
| 6 | `RLppAM` | reversible | Arrestin, M1R, MEK, Oxo | `0.1, 5.0E-5` | binding-pattern rewrite | `@PM:Oxo(R!1).M1R(L!1,S228~p,S273~p,Arr!2,GRK,PP1,CK2).Arrestin(RLP!2,MEK,PP2A) + @cytoplasm:MEK(Arr,ERK) <-> @PM:Oxo(R!1).M1R(L!1,S228~p,S273~p,Arr!2,GRK,PP1,CK2).Arrestin(RLP!2,MEK!3,PP2A).MEK(Arr!3,ERK)` | Reversibly forms binding contacts among Arrestin, M1R, MEK, Oxo through Arrestin.MEK, MEK.Arr. Rate/expression: 0.1, 5.0E-5. |
| 7 | `RLppAME` | reversible | Arrestin, ERK, M1R, MEK, Oxo | `2.0, 2.5` | binding-pattern rewrite | `@PM:Oxo(R!1).M1R(L!1,S228~p,S273~p,Arr!2,GRK,PP1,CK2).Arrestin(RLP!2,MEK!3,PP2A).MEK(Arr!3,ERK) + @cytoplasm:ERK(MEK,s~u,PP2A,PP1) <-> @PM:Oxo(R!1).M1R(L!1,S228~p,S273~p,Arr!2,GRK,PP1,CK2).Arrestin(RLP!2,MEK!3,PP2A).MEK(Arr!3,ERK!4).ERK(MEK!4,s~u,PP2A,PP1)` | Reversibly forms binding contacts among Arrestin, ERK, M1R, MEK, Oxo through ERK.MEK, MEK.ERK. Rate/expression: 2.0, 2.5. |
| 8 | `Oxo_conversion` | one-way | Oxo, Oxo_EC | `50.0` | stoichiometric pattern rewrite | `@EC:Oxo_EC() -> @EC:Oxo(R)` | Produces Oxo while retaining or consuming Oxo_EC. Rate/expression: 50.0. |
| 9 | `RLAPP2A` | reversible | Arrestin, M1R, Oxo, PP2A | `3.0E-5, 6.0E-5` | binding-pattern rewrite | `@PM:Oxo(R!1).M1R(L!1,S228~u,S273~u,Arr!2,GRK,PP1,CK2).Arrestin(RLP!2,MEK,PP2A) + @cytoplasm:PP2A(Arrestin,ERK) <-> @PM:Oxo(R!1).M1R(L!1,S228~u,S273~u,Arr!2,GRK,PP1,CK2).Arrestin(RLP!2,MEK,PP2A!3).PP2A(Arrestin!3,ERK)` | Reversibly forms binding contacts among Arrestin, M1R, Oxo, PP2A through Arrestin.PP2A, PP2A.Arrestin. Rate/expression: 3.0E-5, 6.0E-5. |
| 10 | `DeP_pERK_PP2A` | reversible | Arrestin, ERK, M1R, Oxo, PP2A, pERK | `9.0 * PP2A_dephos_factor, 0.0` | stoichiometric pattern rewrite | `@PM:Oxo(R!1).M1R(L!1,S228~u,S273~u,Arr!2,GRK,PP1,CK2).Arrestin(RLP!2,MEK,PP2A!3).PP2A(Arrestin!3,ERK) + @cytoplasm:pERK(MEK,s~p,PP2A,PP1) <-> @PM:Oxo(R!1).M1R(L!1,S228~u,S273~u,Arr!2,GRK,PP1,CK2).Arrestin(RLP!2,MEK,PP2A!3).PP2A(Arrestin!3,ERK) + @cytoplasm:ERK(MEK,s~u,PP2A,PP1)` | Produces ERK while retaining or consuming Arrestin, M1R, Oxo, PP2A, pERK. Rate/expression: 9.0 * PP2A_dephos_factor, 0.0. |
| 11 | `RLppAMpE` | reversible | Arrestin, ERK, M1R, MEK, Oxo, pERK | `9.0 * MEK_effect, 0.36 * MEK_effect` | binding-pattern rewrite | `@PM:Oxo(R!1).M1R(L!1,S228~p,S273~p,Arr!2,GRK,PP1,CK2).Arrestin(RLP!2,MEK!3,PP2A).MEK(Arr!3,ERK!4).ERK(MEK!4,s~u,PP2A,PP1) <-> @PM:Oxo(R!1).M1R(L!1,S228~p,S273~p,Arr!2,GRK,PP1,CK2).Arrestin(RLP!2,MEK!3,PP2A).MEK(Arr!3,ERK!4).pERK(MEK!4,s~p,PP2A,PP1)` | Reversibly forms binding contacts among Arrestin, ERK, M1R, MEK, Oxo, pERK through pERK.MEK. Rate/expression: 9.0 * MEK_effect, 0.36 * MEK_effect. |
| 12 | `RLppAMpE_dissociation` | reversible | Arrestin, M1R, MEK, Oxo, pERK | `2.0, 0.0` | binding-pattern rewrite | `@PM:Oxo(R!1).M1R(L!1,S228~p,S273~p,Arr!2,GRK,PP1,CK2).Arrestin(RLP!2,MEK!3,PP2A).MEK(Arr!3,ERK!4).pERK(MEK!4,s~p,PP2A,PP1) <-> @PM:Oxo(R!1).M1R(L!1,S228~p,S273~p,Arr!2,GRK,PP1,CK2).Arrestin(RLP!2,MEK!3,PP2A).MEK(Arr!3,ERK) + @cytoplasm:pERK(MEK,s~p,PP2A,PP1)` | Reversibly releases binding contacts among Arrestin, M1R, MEK, Oxo, pERK by freeing MEK.ERK, pERK.MEK. Rate/expression: 2.0, 0.0. |
| 13 | `RL_GRK` | reversible | GRK, M1R, Oxo | `4.0 * GRK_binding_factor, 4.0` | binding-pattern rewrite | `@PM:Oxo(R!1).M1R(L!1,S228~u,S273~u,Arr,GRK,PP1,CK2) + @PM:GRK(RL) <-> @PM:Oxo(R!1).M1R(L!1,S228~u,S273~u,Arr,GRK!2,PP1,CK2).GRK(RL!2)` | Reversibly forms binding contacts among GRK, M1R, Oxo through GRK.RL, M1R.GRK. Rate/expression: 4.0 * GRK_binding_factor, 4.0. |
| 14 | `RLGRK_pp_dissociation` | reversible | GRK, M1R, Oxo | `2.0 * RLGRK_pp_dissociation, 2.0 * RLGRK_pp_dissociation` | binding-pattern rewrite | `@PM:Oxo(R!1).M1R(L!1,S228~p,S273~p,Arr,GRK!2,PP1,CK2).GRK(RL!2) <-> @PM:Oxo(R!1).M1R(L!1,S228~p,S273~p,Arr,GRK,PP1,CK2) + @PM:GRK(RL)` | Reversibly releases binding contacts among GRK, M1R, Oxo by freeing GRK.RL, M1R.GRK. Rate/expression: 2.0 * RLGRK_pp_dissociation, 2.0 * RLGRK_pp_dissociation. |
| 15 | `ERK_balancing` | reversible | ERK, pERK | `0.1, 1.0` | stoichiometric pattern rewrite | `@cytoplasm:ERK(MEK,s~u,PP2A,PP1) <-> @cytoplasm:pERK(MEK,s~p,PP2A,PP1)` | Produces pERK while retaining or consuming ERK. Rate/expression: 0.1, 1.0. |
| 16 | `P_probe` | reversible | pERK, phos_probe, probe | `2.0, 2.0` | stoichiometric pattern rewrite | `@cytoplasm:pERK(MEK,s~p,PP2A,PP1) + @cytoplasm:probe(site~u) <-> @cytoplasm:pERK(MEK,s~p,PP2A,PP1) + @cytoplasm:phos_probe(Site0~p)` | Produces phos_probe while retaining or consuming pERK, probe. Rate/expression: 2.0, 2.0. |
| 17 | `RL_CK2_binding` | reversible | CK2, M1R, Oxo | `5.0E-5, 1.0` | binding-pattern rewrite | `@PM:Oxo(R!1).M1R(L!1,S228~u,S273~u,Arr,GRK,PP1,CK2) + @cytoplasm:CK2(RL) <-> @PM:Oxo(R!1).M1R(L!1,S228~u,S273~u,Arr,GRK,PP1,CK2!2).CK2(RL!2)` | Reversibly forms binding contacts among CK2, M1R, Oxo through CK2.RL, M1R.CK2. Rate/expression: 5.0E-5, 1.0. |
| 18 | `RL_CK2_phos` | one-way | CK2, M1R, Oxo | `0.01` | internal-state conversion/modification | `@PM:Oxo(R!1).M1R(L!1,S228~u,S273~u,Arr,GRK,PP1,CK2!2).CK2(RL!2) -> @PM:Oxo(R!1).M1R(L!1,S228~p,S273~p,Arr,GRK,PP1,CK2!2).CK2(RL!2)` | Updates internal state(s) on CK2, M1R, Oxo: M1R.S228 u→p, M1R.S273 u→p. Rate/expression: 0.01. |
| 19 | `RL_CK2_phos_dissociation` | reversible | CK2, M1R, Oxo | `10.0, 10.0` | binding-pattern rewrite | `@PM:Oxo(R!1).M1R(L!1,S228~p,S273~p,Arr,GRK,PP1,CK2!2).CK2(RL!2) <-> @PM:Oxo(R!1).M1R(L!1,S228~p,S273~p,Arr,GRK,PP1,CK2) + @cytoplasm:CK2(RL)` | Reversibly releases binding contacts among CK2, M1R, Oxo by freeing CK2.RL, M1R.CK2. Rate/expression: 10.0, 10.0. |

## 7. Observables and technical readouts

| Observable | Type | Pattern / target | Technical interpretation |
| --- | --- | --- | --- |
| `O0_M1R_tot` | `Molecules` | `@PM:M1R(L,S228,S273,Arr,GRK,PP1,CK2)` | counts molecule-pattern matches |
| `O0_Oxo_EC` | `Molecules` | `@EC:Oxo(R)` | counts molecule-pattern matches |
| `O0_Arrestin` | `Molecules` | `@cytoplasm:Arrestin(RLP,MEK,PP2A)` | counts molecule-pattern matches |
| `O0_RLPPA` | `Molecules` | `@PM:Oxo(R!1).M1R(L!1,S228~p,S273~p,Arr!2,GRK,PP1,CK2).Arrestin(RLP!2,MEK,PP2A)` | counts molecule-pattern matches |
| `O0_MEK` | `Molecules` | `@cytoplasm:MEK(Arr,ERK)` | counts molecule-pattern matches |
| `O0_ERK` | `Molecules` | `@cytoplasm:ERK(MEK,s~u,PP2A,PP1)` | counts molecule-pattern matches |
| `O0_pERK` | `Molecules` | `@cytoplasm:pERK(MEK,s~p,PP2A,PP1)` | counts molecule-pattern matches |
| `O0_RLPPA_M` | `Molecules` | `@PM:Oxo(R!1).M1R(L!1,S228~p,S273~p,Arr!2,GRK,PP1,CK2).Arrestin(RLP!2,MEK!3,PP2A).MEK(Arr!3,ERK)` | counts molecule-pattern matches |
| `O0_RLPP` | `Molecules` | `@PM:Oxo(R!1).M1R(L!1,S228~p,S273~p,Arr,GRK,PP1,CK2)` | counts molecule-pattern matches |
| `O0_RLA` | `Molecules` | `@PM:Oxo(R!1).M1R(L!1,S228~u,S273~u,Arr!2,GRK,PP1,CK2).Arrestin(RLP!2,MEK,PP2A)` | counts molecule-pattern matches |
| `O0_Oxo_EC_tot` | `Molecules` | `@cytoplasm:Oxo_EC()` | counts molecule-pattern matches |
| `O0_PP2A_tot` | `Molecules` | `@cytoplasm:PP2A(Arrestin,ERK)` | counts molecule-pattern matches |
| `O0_RLAPP2A` | `Molecules` | `@PM:Oxo(R!1).M1R(L!1,S228~u,S273~u,Arr!2,GRK,PP1,CK2).Arrestin(RLP!2,MEK,PP2A!3).PP2A(Arrestin!3,ERK)` | counts molecule-pattern matches |
| `O0_RLppAME` | `Molecules` | `@PM:Oxo(R!1).M1R(L!1,S228~p,S273~p,Arr!2,GRK,PP1,CK2).Arrestin(RLP!2,MEK!3,PP2A).MEK(Arr!3,ERK!4).ERK(MEK!4,s~u)` | counts molecule-pattern matches |
| `O0_RLppAMpE` | `Molecules` | `@PM:Oxo(R!1).M1R(L!1,S228~p,S273~p,Arr!2,GRK,PP1,CK2).Arrestin(RLP!2,MEK!3,PP2A).MEK(Arr!3,ERK!4).pERK(MEK!4,s~p)` | counts molecule-pattern matches |
| `O0_probe_tot` | `Molecules` | `@cytoplasm:probe()` | counts molecule-pattern matches |
| `O0_phos_probe_tot` | `Molecules` | `@cytoplasm:phos_probe()` | counts molecule-pattern matches |
| `O0_GRK_tot` | `Molecules` | `@EC:GRK()` | counts molecule-pattern matches |
| `O0_PP1_tot` | `Molecules` | `@cytoplasm:PP1()` | counts molecule-pattern matches |
| `O0_CK2_tot` | `Molecules` | `@cytoplasm:CK2()` | counts molecule-pattern matches |

## 8. Actions and simulation workflow

1. `generate_network({max_iter=>6,max_agg=>10,max_stoich=>{M1R=>100,Oxo=>100,Arrestin=>100,MEK=>100,ERK=>100,pERK=>100,Oxo_EC=>100,PP2A=>100,probe=>100,phos_probe=>100,GRK=>100,PP1=>100,CK2=>100},overwrite=>1})` — active execution command in the actions block

## 9. Technical caveats and ambiguities

- The model declares explicit EC, PM, and cytoplasm compartments but no anchors block; localization is written directly on seed species, observables, and rule patterns with @compartment prefixes.

- Several rate expressions reference factors such as RLpp_arrestin_binding_factor, phos_factor_PP, and MEK_effect that are not declared in the visible parameters block; this should be checked before execution.

- The metadata says bng2_compatible is false, consistent with the compartment annotations and web-simulator style syntax.
