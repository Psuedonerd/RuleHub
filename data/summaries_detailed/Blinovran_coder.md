# Coder Model Explanation: Blinov ran

## 1. Model identity and scope

- **Model id:** `Blinov_ran`
- **Title:** Blinov ran
- **BNGL path:** `Published/Blinovran/Blinov_ran.bngl`
- **YAML path:** `Published/Blinovran/metadata.yaml`
- **Scope:** This is a compartmental Ran/cargo/RCC1 transport model. It tracks Ran-cargo complex movement between nucleus and cytoplasm, cargo phosphorylation in the cytoplasm, cargo-Ran dissociation/association in both compartments, and RCC1 binding to nuclear Ran.

## 2. BNGL block inventory

| Block | Present? | Count / role |
| --- | --- | --- |
| Compartments | Yes | 5 compartments/surfaces: `nuc`, `cyt`, `EC`, `pm`, and `nm`. |
| Parameters | Yes | Parameter block is present but empty; numeric rates are written directly in rules. |
| Molecule types | Yes | 3 molecule types: `Ran`, `C`, and `RCC1`. |
| Anchors | Yes | `RCC1(nuc)` anchor declaration. |
| Seed species | Yes | 2 numbered nuclear initial species. |
| Observables | Yes | 7 molecule-count readouts. |
| Functions | Yes | Function block is present but empty. |
| Reaction rules | Yes | 7 labeled reversible rules. |
| Actions | Inline command | One NFsim simulation command. |

## 3. Parameters, functions, and rate laws

The parameter block is empty, and there are no function definitions. All rate laws are numeric literals placed directly on reaction rules. Transport uses forward rate `2.0 * 602.0` and reverse rate `0.0`, so Ran-cargo transport is effectively one-way from nucleus to cytoplasm. Cargo phosphorylation and dephosphorylation use `10.0` and `1.0`. Ran-cargo and Ran-RCC1 binding rules use `1.0` and `100.0` for the two directions as written.

## 4. Molecule types, sites, and states

| Molecule type | Site count | Sites/components | Internal states | Binding/modification roles | Notes |
| --- | ---: | --- | --- | --- | --- |
| `Ran` | 1 | `cargo` | None | Binds cargo `C.site` or RCC1 `site`, depending on the rule context. | The single site is reused for cargo and RCC1 interactions in different compartments. |
| `C` | 4 | `site`, `Y1`, `Y2`, `Y3` | `Y1`: `u`, `p`; `Y2`: `u`, `p`; `Y3`: `u`, `p` | `site` binds Ran; `Y1`, `Y2`, and `Y3` are cargo phosphorylation-state sites. | Metadata tag `c` likely refers to cargo, but interpretation comes mainly from molecule and observable names. |
| `RCC1` | 1 | `site` | None | Binds nuclear Ran through `site`. | Anchor declaration associates RCC1 with the nucleus. |

## 5. Initial species, compartments, and setup

The model starts with 1000 nuclear Ran-cargo complexes, `@nuc:Ran(cargo!1).C(site!1,Y1~u,Y2~u,Y3~u)`, and 1000 nuclear RCC1 molecules, `@nuc:RCC1(site)`. Cargo begins unphosphorylated at all three `Y` sites. No cytoplasmic species are seeded initially; cytoplasmic Ran/cargo populations arise through transport and cytoplasmic dissociation/phosphorylation rules.

## 6. Complete reaction-rule inventory

| # | Rule label/name | Direction | Participants and sites | Rate | Modeled change | Technical meaning |
| ---: | --- | --- | --- | --- | --- | --- |
| 1 | `Transport` | Reversible syntax, effectively one-way | Bound Ran-cargo complex in `nuc` and `cyt` compartments | Forward `2.0 * 602.0`, reverse `0.0` | Moves a Ran-cargo complex from nucleus to cytoplasm | Exports bound Ran-cargo complex to the cytoplasm with no return through this rule. |
| 2 | `Ran_C_bind_cyt` | Reversible | Cytoplasmic Ran `cargo` site and cargo `C.site` | `1.0`, `100.0` | Interconverts bound cytoplasmic Ran-cargo complex and separate cytoplasmic Ran plus cargo | Allows cytoplasmic Ran-cargo dissociation and reassociation. As written, the left side is bound and the right side is free. |
| 3 | `C_p1` | Reversible state change | Cytoplasmic cargo `Y3`, regardless of binding status | `10.0`, `1.0` | Converts `Y3` between unphosphorylated and phosphorylated | Phosphorylates and dephosphorylates the third cargo modification site in the cytoplasm. |
| 4 | `C_p2` | Reversible state change | Cytoplasmic cargo `Y2`, regardless of binding status | `10.0`, `1.0` | Converts `Y2` between unphosphorylated and phosphorylated | Phosphorylates and dephosphorylates the second cargo modification site in the cytoplasm. |
| 5 | `C_p3` | Reversible state change | Cytoplasmic cargo `Y1`, regardless of binding status | `10.0`, `1.0` | Converts `Y1` between unphosphorylated and phosphorylated | Phosphorylates and dephosphorylates the first cargo modification site in the cytoplasm. |
| 6 | `Ran_RCC1_bind` | Reversible | Nuclear Ran `cargo` site and nuclear RCC1 `site` | `1.0`, `100.0` | Adds or removes a nuclear Ran-RCC1 bond | Allows RCC1 to bind nuclear Ran through the same Ran site that otherwise binds cargo. |
| 7 | `Ran_C_bind_nuc` | Reversible | Nuclear Ran `cargo` site and nuclear cargo `C.site` | `1.0`, `100.0` | Interconverts bound nuclear Ran-cargo complex and separate nuclear Ran plus cargo | Allows nuclear Ran-cargo dissociation and reassociation. As written, the left side is bound and the right side is free. |

## 7. Observables and technical readouts

| Observable | Type | Pattern / target | Technical interpretation |
| --- | --- | --- | --- |
| `Ran_cyt` | `Molecules` | Cytoplasmic Ran | Counts Ran molecules in the cytoplasm. |
| `Cargo_cyt` | `Molecules` | Cytoplasmic cargo `C` | Counts cargo molecules in the cytoplasm. |
| `RCC1_nuc` | `Molecules` | Nuclear RCC1 | Counts RCC1 molecules in the nucleus. |
| `Cargo_phosp_cyt_total` | `Molecules` | Nuclear cargo with `Y1`, `Y2`, or `Y3` phosphorylated | Despite the name, the listed patterns use `@nuc`, so this readout counts phosphorylated cargo patterns in the nucleus, not cytoplasm. |
| `Cargo_nuc` | `Molecules` | Nuclear cargo `C` | Counts cargo molecules in the nucleus. |
| `Cargo_phosp_cyt` | `Molecules` | Cytoplasmic cargo with all three phosphorylation sites marked phosphorylated/possibly bound | Counts cytoplasmic cargo matching phosphorylated-state constraints across `Y1`, `Y2`, and `Y3`. |
| `Ran_bound_cyt` | `Molecules` | Cytoplasmic Ran with `cargo` bound to something | Counts cytoplasmic Ran that remains bound through its cargo site. |

## 8. Actions and simulation workflow

The model runs `simulate_nf({t_end=>10.0,n_steps=>200})`. No network generation action is present. Because the model uses compartments, anchored RCC1, wildcard binding constraints, and NFsim-compatible syntax, the intended workflow is direct network-free simulation over 10 time units with 200 output steps.

## 9. Technical caveats and ambiguities

- The parameter and function blocks are empty; rule rates are hard-coded numeric literals.
- `Cargo_phosp_cyt_total` is named like a cytoplasmic observable but uses nuclear patterns, so downstream code should not rely on the name alone.
- The Ran `cargo` site is used for both cargo and RCC1 binding in different rules; the model relies on context and compartments rather than distinct Ran sites for these interactions.
