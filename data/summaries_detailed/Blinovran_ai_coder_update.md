# Coder Model Explanation: Blinov ran

## 1. Model identity and scope

- **Model id:** `Blinov_ran`
- **Title:** Blinov ran
- **Metadata description:** Ran GTPase cycle
- **Local BNGL path:** `Published/Blinovran/Blinov_ran.bngl`
- **Local YAML path:** `Published/Blinovran/metadata.yaml`

This is a compact NFsim-oriented compartmental rule-based model for Ran/cargo/RCC1 localization. It does not explicitly encode Ran nucleotide states; instead, the executable logic centers on a Ran molecule with one cargo-binding component, a cargo-like molecule `C` with one Ran/RCC1 contact site plus three reversible modification sites, and nuclear RCC1 as an anchored molecule. The model uses VCell-style compartment prefixes such as `@nuc:Ran(...)` and `@cyt:C(...)`, plus an anchors block that constrains `RCC1` to the nucleus.

## 2. BNGL block inventory

| BNGL construct | Present? | Active entries | Technical contribution |
| --- | --- | ---: | --- |
| `begin compartments` | yes | 5 | Declares five compartments: three 3D compartments (`nuc`, `cyt`, `EC`) and two 2D compartments (`pm`, `nm`), all with size value `1`. |
| `begin parameters` | yes | 0 | The parameter block is present but empty; all rule rates are literal numeric expressions. |
| `begin molecule types` | yes | 3 | Declares `Ran`, `C`, and `RCC1` with their sites/states. |
| `begin anchors` | yes | 1 | Declares `RCC1(nuc)`, constraining RCC1-containing species/complexes to the nuclear compartment under VCell-style spatial semantics. |
| `begin seed species` | yes | 2 | Starts with a nuclear Ran-C complex and free nuclear RCC1. |
| `begin observables` | yes | 7 | Tracks cytosolic Ran, cytosolic cargo, nuclear RCC1, nuclear/cytosolic cargo, phosphorylated cargo patterns, and cytosolic bound Ran. |
| `begin functions` | yes | 0 | The functions block is present but empty; `uses_functions` should remain true under block-presence metadata semantics even though no active functions are defined. |
| `begin reaction rules` | yes | 7 | Defines transport, Ran-C association/dissociation in cytoplasm and nucleus, cargo phosphorylation-state toggles, and nuclear Ran-RCC1 binding. |
| Inline actions | yes | 1 | Runs `simulate_nf({t_end=>10.0,n_steps=>200})`. |

Parser note: this model uses **VCell-style compartment-prefix grammar**, e.g. `@nuc:Ran(...)` and `@cyt:C(...)`. It does not use the CBNGL-style suffix grammar `Molecule(...)@Compartment`.

## 3. Parameters, functions, and rate laws

The `parameters` block is present but empty. The `functions` block is also present but empty. Therefore, all active rates are written directly in the reaction-rule rows rather than through named parameters or functions.

| Rate expression | Where used | Technical interpretation |
| --- | --- | --- |
| `2.0 * 602.0, 0.0` | `Transport` | Forward transport of a bound Ran pattern from nucleus to cytoplasm has rate `1204.0`; the reverse rate is zero, so the reversible arrow is syntactically present but dynamically one-way under these values. |
| `1.0, 100.0` | `Ran_C_bind_cyt`, `Ran_RCC1_bind`, `Ran_C_bind_nuc` | Each of these rules is written with a bound complex on the left and separated molecules on the right. The first number applies left-to-right dissociation; the second applies right-to-left association. |
| `10.0, 1.0` | `C_p1`, `C_p2`, `C_p3` | Each cargo modification site toggles from unmodified to phosphorylated at rate `10.0` and from phosphorylated to unmodified at rate `1.0`. |

No named algebraic functions, parameter scans, or rate-law functions are defined.

## 4. Molecule types, sites, and states

| Molecule type | Site count | Sites/components | Internal states | Anchor/allowed compartments | Binding/modification roles | Notes |
| --- | ---: | --- | --- | --- | --- | --- |
| `Ran` | 1 | `cargo` | none | Not anchored. Explicitly appears in `nuc` and `cyt` patterns. | `cargo` binds either `C.site` or `RCC1.site` depending on the rule. | The model name references Ran GTPase, but the BNGL does not declare GDP/GTP or active/inactive Ran states. |
| `C` | 4 | `site`, `Y1`, `Y2`, `Y3` | `Y1: u,p`; `Y2: u,p`; `Y3: u,p` | Not anchored. Seeded in the nuclear Ran-C complex and later appears in nuclear/cytosolic rules and readouts. | `site` binds `Ran.cargo`; `Y1`, `Y2`, and `Y3` are independently reversible modification sites. | `C` is named only abstractly in the BNGL/YAML; it behaves like cargo with three phosphorylation-like state sites, but the file does not name a specific cargo protein. |
| `RCC1` | 1 | `site` | none | Anchored to `nuc` by `RCC1(nuc)`. | `site` binds `Ran.cargo` in the nuclear Ran-RCC1 rule. | Because of the anchor, RCC1-containing species should be interpreted as nuclear-localized rather than freely transported. |

There are no repeated identical site names in these molecule-type declarations.

## 5. Compartments, anchors, initial species, and setup

### Compartments

| Compartment | Dimension value | Size value | Role in this model |
| --- | ---: | ---: | --- |
| `nuc` | 3 | 1 | Nuclear volume where the model starts Ran-C and RCC1 and where nuclear binding/unbinding rules occur. |
| `cyt` | 3 | 1 | Cytosolic volume where transported/bound Ran, cargo, and cargo modification readouts are tracked. |
| `EC` | 3 | 1 | Declared but not used by any active species, observable, or rule pattern in this file. |
| `pm` | 2 | 1 | Declared membrane-like compartment, unused by active patterns in this file. |
| `nm` | 2 | 1 | Declared nuclear-membrane-like compartment, unused by active patterns in this file. |

### Anchors

| Anchor declaration | Technical meaning |
| --- | --- |
| `RCC1(nuc)` | RCC1 is constrained to the nuclear compartment. The nuclear Ran-RCC1 binding rule should therefore be read as nuclear-localized by construction, and RCC1-containing complexes should not be interpreted as freely cytosolic. |

### Initial species

| Initial species | Initial amount | Technical meaning |
| --- | ---: | --- |
| `@nuc:Ran(cargo!1).C(site!1,Y1~u,Y2~u,Y3~u)` | 1000.0 | The model starts with a nuclear Ran-C complex. `Ran.cargo` is bonded to `C.site`; all three cargo modification sites start unmodified. |
| `@nuc:RCC1(site)` | 1000.0 | The model starts with free nuclear RCC1, consistent with the `RCC1(nuc)` anchor. |

No initial cytosolic Ran, free cargo, or Ran-RCC1 complex is seeded directly; those states are produced through the reaction rules.

## 6. Complete reaction-rule inventory

The source contains **7** reaction rules. The table below preserves one row per rule and identifies the exact sites, state changes, compartment placement, and rate direction.

### Rule-family orientation

Rules 1, 2, 6, and 7 are compartmental binding/transport rules involving `Ran.cargo`, `C.site`, or `RCC1.site`. Rules 3-5 are independent reversible state toggles on the three cargo sites `Y3`, `Y2`, and `Y1` in the cytoplasm. Because the model uses VCell-style compartment prefixes, compartment movement is represented by changing prefixes such as `@nuc:Ran(...)` to `@cyt:Ran(...)`, rather than by suffix annotations.

| # | Rule label | Direction | Participants and affected sites | Exact modeled change | Rate expression | Technical meaning |
| ---: | --- | --- | --- | --- | --- | --- |
| 1 | `Transport` | reversible syntax, effectively one-way | Bound `Ran` pattern; `Ran.cargo!+`; compartments `nuc` and `cyt` | Changes a bound Ran pattern from `@nuc:Ran(cargo!+)` to `@cyt:Ran(cargo!+)`; the `cargo!+` constraint requires Ran's `cargo` site to already be bound to some partner, but the partner is not named in the pattern. | `2.0 * 602.0, 0.0` | Implements export-like movement of bound Ran from nucleus to cytoplasm. The reverse arrow exists syntactically, but the zero reverse rate prevents cytoplasm-to-nucleus movement through this rule. A coder should note that only the Ran pattern is explicitly compartment-prefixed in the rule; movement of the connected partner depends on the compartmental semantics applied to the bound complex. |
| 2 | `Ran_C_bind_cyt` | reversible | `Ran.cargo` and `C.site` in `cyt` | Left-to-right releases the cytosolic `Ran.cargo!1`-`C.site!1` bond; right-to-left forms the same bond between free cytosolic Ran and free cytosolic C. | `1.0, 100.0` | Controls cytosolic Ran-C association state. Despite the rule name containing `bind`, the written left-to-right direction is dissociation and the reverse direction is association. |
| 3 | `C_p1` | reversible | Cytosolic `C`; site `Y3`; optional bond status `!?` preserved | Toggles `C.Y3` from `u` to `p` left-to-right and from `p` to `u` right-to-left in `cyt`; the `!?` marker means the rule does not require a specific binding state at `Y3`. | `10.0, 1.0` | Implements reversible modification of the cargo `Y3` site in the cytoplasm without changing `C.site`, `Y1`, `Y2`, or compartment placement. |
| 4 | `C_p2` | reversible | Cytosolic `C`; site `Y2`; optional bond status `!?` preserved | Toggles `C.Y2` from `u` to `p` left-to-right and from `p` to `u` right-to-left in `cyt`; binding status at `Y2` is not constrained. | `10.0, 1.0` | Implements reversible modification of the cargo `Y2` site in the cytoplasm independently of the other cargo modification sites. |
| 5 | `C_p3` | reversible | Cytosolic `C`; site `Y1`; optional bond status `!?` preserved | Toggles `C.Y1` from `u` to `p` left-to-right and from `p` to `u` right-to-left in `cyt`; binding status at `Y1` is not constrained. | `10.0, 1.0` | Implements reversible modification of the cargo `Y1` site in the cytoplasm independently of `Y2` and `Y3`. The rule label `C_p3` refers to the third listed phosphorylation rule, not to site `Y3`. |
| 6 | `Ran_RCC1_bind` | reversible | Nuclear `Ran.cargo` and nuclear `RCC1.site`; RCC1 is anchored to `nuc` | Left-to-right forms a `Ran.cargo!1`-`RCC1.site!1` bond in `nuc`; right-to-left releases that bond back to free nuclear Ran and free nuclear RCC1. | `1.0, 100.0` | Implements nuclear Ran-RCC1 association/dissociation. The `RCC1(nuc)` anchor makes the product complex nuclear-localized by construction and prevents interpreting RCC1 as a freely cytosolic binding partner. |
| 7 | `Ran_C_bind_nuc` | reversible | Nuclear `Ran.cargo` and nuclear `C.site` | Left-to-right releases the nuclear `Ran.cargo!1`-`C.site!1` bond; right-to-left forms the same bond between free nuclear Ran and free nuclear C. | `1.0, 100.0` | Controls nuclear Ran-C association state. This rule can generate free nuclear cargo from the seeded nuclear Ran-C complex and can re-form the nuclear complex. |

## 7. Observables and technical readouts

| Observable | Type | Pattern counted | Technical interpretation |
| --- | --- | --- | --- |
| `Ran_cyt` | `Molecules` | `@cyt:Ran()` | Counts cytosolic Ran pattern matches, regardless of whether `Ran.cargo` is bound. |
| `Cargo_cyt` | `Molecules` | `@cyt:C()` | Counts cytosolic cargo `C`, regardless of `site`, `Y1`, `Y2`, or `Y3` states. |
| `RCC1_nuc` | `Molecules` | `@nuc:RCC1()` | Counts nuclear RCC1, including free and Ran-bound RCC1 patterns under the nuclear anchor. |
| `Cargo_phosp_cyt_total` | `Molecules` | `@nuc:C(Y1~p!?)`, `@nuc:C(Y2~p!?)`, `@nuc:C(Y3~p!?)` | Despite the name containing `cyt`, the patterns are nuclear `@nuc:C(...)` patterns. The observable counts nuclear cargo matches with each phosphorylated site pattern and may count the same molecule multiple times if several listed patterns match. |
| `Cargo_nuc` | `Molecules` | `@nuc:C()` | Counts nuclear cargo regardless of whether it is bound to Ran or which modification states it carries. |
| `Cargo_phosp_cyt` | `Molecules` | `@cyt:C(Y1~p!?,Y2~p!?,Y3~p!?)` | Counts cytosolic cargo molecules whose `Y1`, `Y2`, and `Y3` sites are all in the phosphorylated state; the optional bond markers do not impose specific bonds at those sites. |
| `Ran_bound_cyt` | `Molecules` | `@cyt:Ran(cargo!+)` | Counts cytosolic Ran whose `cargo` site is bound to some partner, without requiring that the partner be explicitly named in the observable. |

## 8. Actions and simulation workflow

The only executable action after `end model` is:

```bngl
simulate_nf({t_end=>10.0,n_steps=>200})
```

This requests an NFsim simulation from time `0` to `10.0` with `200` output steps. There is no explicit `generate_network(...)` action in this file, consistent with the metadata's `simulation_methods: ["nf"]` and `nfsim_compatible: true`.

## 9. Technical caveats and ambiguities

- The metadata description says “Ran GTPase cycle,” but the BNGL molecule type `Ran(cargo)` has no declared nucleotide state site. The model should therefore not be read as an explicit GDP/GTP cycle implementation.
- `C` is an abstract cargo-like molecule name in the local files. The model defines its binding and modification behavior, but does not identify a specific biological cargo protein.
- The `functions` block is empty but present. Under the updated metadata-audit rule, this still supports `uses_functions: true`; under executable-rate interpretation, there are no active functions.
- The observable `Cargo_phosp_cyt_total` has a name suggesting cytosolic cargo phosphorylation, but its patterns are nuclear `@nuc:C(...)` patterns.
- The model declares unused compartments `EC`, `pm`, and `nm`; these may reflect a broader VCell compartment template rather than active biology in this compact file.
- The `Transport` rule uses `Ran(cargo!+)` without naming the bound partner. A coder should verify the target simulator's treatment of connected compartmental complexes before assuming exactly which partner species move with Ran.
- The file uses VCell-style compartment-prefix syntax and an anchors block. These constructs may require VCell-aware parsing and should not be reduced to plain non-spatial BNGL without checking localization semantics.
