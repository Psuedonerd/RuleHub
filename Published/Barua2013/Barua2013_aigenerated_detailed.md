# Coder Model Explanation: Barua 2013 beta-catenin destruction model

## 1. Model identity and scope

Despite conflicting legacy metadata text, `Barua_2013.bngl` explicitly models beta-catenin (`bCat`) binding to APC and AXIN, recruitment of GSK3b and CK1a, phosphorylation, synthesis, degradation-state conversion, and release from destruction-complex partners. Sources: `Published/Barua2013/Barua_2013.bngl` and `Published/Barua2013/Barua_2013_metadata.yaml`.

## 2. BNGL block inventory

The file contains 25 parameters, 7 molecule types, 7 initial species, 29 reaction rules, 5 observables, and 2 inline actions. It uses `begin species` rather than `begin seed species`; there are no model delimiters, compartments, anchors, functions, or energy patterns.

## 3. Parameters, functions, and rate laws

Pools are `BCATtot=11000`, `APCtot=31540`, `AXINtot=3154`, `GSKtot=31540`, and `CK1atot=31540`. Reversible binding pairs are APC 15-aa–bCat `kf1_bap=3.17e-6`/`kr1_bap=0.273`, phospho-APC 20-aa–bCat `kf2_bap=3.17e-6`/`kr2_bap=0.0015`, AXIN–bCat `kf_ba=3.17e-6`/`kr_ba=0.227`, APC–AXIN `kf_apa=3.17e-6`/`kr_apa=0.1`, GSK3b–AXIN `kf_ga=3.17e-6`/`kr_ga=0.065`, and CK1a–AXIN `kf_ca=3.17e-6`/`kr_ca=0.1`. Modification rates are `kpb=0.05`, `kmpb=0.0012`, `kp=0.05`, and `kmp=0.05`; bCat degradation-state changes use `kdb1=0.0000428` and `kdb2=0.00428`; synthesis uses `ksb=4.0`. `chi=3154000` multiplies association rates for intracomplex closure. Five dissociation rules use literal rate `1000`. There are no functions.

## 4. Molecule types, sites, and states

| Molecule type | Site count | Sites/components | Internal states | Anchor/allowed compartments | Binding/modification roles | Notes |
| --- | ---: | --- | --- | --- | --- | --- |
| `AXIN` | 4 | `rgs`, `gid`, `b`, `e` | None | None | Binds APC, GSK3b, bCat, CK1a respectively | Scaffold |
| `GSK3b` | 1 | `a` | None | None | Binds `AXIN.gid`; catalyzes contextual phosphorylation patterns | Kinase |
| `APC` | 3 | `a15`, `a20`, `s` | `a20: U,P` | None | `a15` and phospho-`a20` bind bCat; `s` binds AXIN | Destruction-complex component |
| `bCat` | 5 | `s33s37`, `s45`, `ARM34`, `ARM59`, `ss` | `s33s37: U,P`; `s45: U,P`; `ss: l,d` | None | Two phosphosites, AXIN/APC-binding ARM regions, live/degraded status | Beta-catenin |
| `CK1a` | 1 | `e` | None | None | Binds `AXIN.e`; catalyzes contextual S45 phosphorylation | Kinase |
| `dead` | 0 | None | None | None | Seeded at zero but unused by rules | Nullary marker |
| `I` | 0 | None | None | None | Catalytic source carried through synthesis | Nullary source |

## 5. Compartments, anchors, initial species, and setup

No compartments or anchors are present. Free pools seed live, unphosphorylated bCat; unphosphorylated APC; AXIN; GSK3b; and CK1a at their total parameters. `I` is seeded at 1 and acts as a conserved source catalyst; `dead` is seeded at zero and never appears in a rule. The bCat seed contains a doubled comma after `s45~U`, a parser-sensitive typo.

## 6. Complete reaction-rule inventory

**Rule-family orientation.** Rules 1–13 enumerate free association and intracomplex closure among bCat, APC, and AXIN. Rules 14–18 recruit kinases and phosphorylate substrates; rules 19–24 reverse modifications, synthesize bCat, and mark it degraded; rules 25–29 release partners from degraded bCat, including unusual connected-product variants.

| # | Direction | Exact modeled edit | Rate(s) |
| ---: | --- | --- | --- |
| 1 | Reversible | `bCat.ARM59` binds `APC.a15` as `!1` while `bCat.ss~l` | `kf1_bap`, `kr1_bap` |
| 2 | Reversible | In an AXIN–APC–bCat complex, free `bCat.ARM59` closes onto `APC.a15` as `!3` | `chi*kf1_bap`, `kr1_bap` |
| 3 | Reversible | In an APC–bCat complex already linked at `ARM34-a20~P`, free `ARM59` closes onto `APC.a15` as `!2` | `chi*kf1_bap`, `kr1_bap` |
| 4 | Reversible | Live `bCat.ARM34` binds phosphorylated `APC.a20~P` as `!1` | `kf2_bap`, `kr2_bap` |
| 5 | Reversible | In an `ARM59-a15` complex, free `ARM34` closes onto `APC.a20~P` as `!2` | `chi*kf2_bap`, `kr2_bap` |
| 6 | Reversible | Live `bCat.ARM34` binds `AXIN.b` as `!1` | `kf_ba`, `kr_ba` |
| 7 | Reversible | In an APC-linked complex, free `bCat.ARM34` closes onto `AXIN.b` as `!3` | `chi*kf_ba`, `kr_ba` |
| 8 | Reversible | `APC.s` with `a20~U` binds `AXIN.rgs` as `!1` | `kf_apa`, `kr_apa` |
| 9 | Reversible | `APC.s` with free `a20~P` binds `AXIN.rgs` as `!1` | `kf_apa`, `kr_apa` |
| 10 | Reversible | `APC.s` with bound `a20~P!+` binds `AXIN.rgs` as `!1` | `kf_apa`, `kr_apa` |
| 11 | Reversible | In an unphosphorylated APC–bCat–AXIN assembly, `APC.s` closes onto `AXIN.rgs` as `!3` | `chi*kf_apa`, `kr_apa` |
| 12 | Reversible | The same closure occurs with free `APC.a20~P` | `chi*kf_apa`, `kr_apa` |
| 13 | Reversible | The same closure occurs with bound `APC.a20~P!+` | `chi*kf_apa`, `kr_apa` |
| 14 | Reversible | `GSK3b.a` binds `AXIN.gid` as `!1` | `kf_ga`, `kr_ga` |
| 15 | Reversible | `AXIN.e` binds `CK1a.e` as `!1` | `kf_ca`, `kr_ca` |
| 16 | One-way | In a complex containing CK1a, live bCat changes `s45 U→P`; topology is preserved | `kpb` |
| 17 | One-way | In a complex containing GSK3b, live bCat with `s45~P` changes `s33s37 U→P` | `kpb` |
| 18 | One-way | APC associated in a complex with GSK3b changes `a20 U→P` | `kp` |
| 19 | One-way | Live bCat changes `s45 P→U` | `kmpb` |
| 20 | One-way | Live bCat changes `s33s37 P→U` | `kmpb` |
| 21 | One-way | APC in an AXIN-containing complex changes `a20 P→U` | `kmp` |
| 22 | One-way | Conserved `I` produces live, unphosphorylated, unbound bCat; `I` remains on both sides | `ksb` |
| 23 | One-way | Live bCat with `s33s37~U` changes `ss l→d` | `kdb1` |
| 24 | One-way | Live bCat with `s33s37~P` changes `ss l→d` | `kdb2` |
| 25 | One-way | Degraded bCat releases its `ARM59!1-a15!1` bond, yielding separate bCat and APC | `1000` |
| 26 | One-way | The same `ARM59-a15` bond is removed but bCat and APC remain in one connected product pattern through unspecified other links | `1000` |
| 27 | One-way | Degraded bCat releases its `ARM34!1-APC.a20~P!1` bond into separate products | `1000` |
| 28 | One-way | Degraded bCat releases its `ARM34!1-AXIN.b!1` bond into separate products | `1000` |
| 29 | One-way | The `ARM34-AXIN.b` bond is removed while bCat and AXIN remain in one connected product pattern through unspecified other links | `1000` |

## 7. Observables and technical readouts

Molecules `bcat_tot` counts live (`ss~l`) bCat. `bCat_pS45` and `bCat_pS33S37` count live bCat phosphorylated at the named sites. `APC_p20a` counts phosphorylated `APC.a20~P` whether unbound or bound (`!?`). Species `BCat_Axin` counts complete species containing the explicit live `bCat.ARM34!1-AXIN.b!1` complex.

## 8. Actions and simulation workflow

`generate_network` overwrites the network and caps `APC`, `AXIN`, and `bCat` at one copy per species. `simulate_ode` runs to `t_end=250000` with 2500 steps, sparse integration, `rtol=1e-8`, and an apparent misspelling `atoll=>1e-08`.

## 9. Technical caveats and ambiguities

The detailed metadata description (“JAK2-SH2B signaling”) and tags conflict with both the BNGL and the simpler metadata, which identify beta-catenin destruction; this explanation follows the model. Kinases in rules 16–18 appear only as unconstrained members of the same connected complex—no catalytic binding-site edit occurs in those rules. The connected product forms in rules 26 and 29 rely on other unspecified bonds to retain connectivity. The doubled comma in the seed, `atoll` action key, nullary molecule syntax, and bounded `max_stoich` map may require parser-specific handling.
