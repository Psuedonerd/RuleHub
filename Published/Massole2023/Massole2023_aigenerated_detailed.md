# Coder Model Explanation: Massole 2023

## 1. Model identity and scope

- **Metadata id/title:** `Massole_2023` / Massole 2023.
- **Declared purpose:** Epo receptor signaling; the metadata categorizes it as signaling and tags it as published.
- **Inputs:** `Published/Massole2023/Massole_2023.bngl` and `Published/Massole2023/metadata.yaml`.
- **Scope:** a minimal, irreversible assembly model involving four abstractly named molecule types. The file itself does not define what `_EO_`, `_EG_`, `_PERYT_`, `_PO_`, `epo`, or `oh` abbreviate, so their biological identities must not be inferred beyond the metadata's Epo-related description.

## 2. BNGL block inventory

| Construct | Count | Technical role |
| --- | ---: | --- |
| Model wrapper | 1 | Encloses the complete model. |
| Parameters | 0 | Every rule uses the literal rate `1.0`. |
| Compartments / anchors | 0 / 0 | No localization constraints. |
| Molecule types | 4 | `_EO_`, `_EG_`, `_PERYT_`, and `_PO_`. |
| Initial species | 4 | One free pool of each molecule type. |
| Reaction rules | 6 | Four cross-type contacts and two same-type contacts. |
| Observables / functions | 0 / 0 | No named outputs or derived rate logic. |
| Actions | 0 | No network generation or simulation command is supplied. |

## 3. Parameters, functions, and rate laws

There is no parameter block and no function block. All six one-way bimolecular rules use the literal mass-action rate `1.0`. Consequently, the source offers no named rate namespace, forward/reverse distinction, or parameter-level way to vary one contact independently of the others.

## 4. Molecule types, sites, and states

| Molecule type | Site count | Sites/components | Internal states | Anchor/allowed compartments | Binding/modification roles | Notes |
| --- | ---: | --- | --- | --- | --- | --- |
| `_EO_` | 2 | `epo`, `oh` | `oh~0~1` | None | `epo` binds an `oh` site on `_EG_` or `_PERYT_`; `oh` changes `0→1` and, when in state `1`, can bind another `_EO_.epo`. | Names are undefined. |
| `_EG_` | 2 | `oh`, `oh` | Each repeated `oh` is declared only in state `p`. | None | Either equivalent `oh` can bind `_EO_.epo` or `_PO_.epo`. | Repeats `oh` twice; matches can carry symmetry multiplicity. |
| `_PERYT_` | 4 | `oh`, `oh`, `oh`, `oh` | Each repeated `oh` is declared only in state `p`. | None | Any equivalent `oh` can bind `_EO_.epo` or `_PO_.epo`. | Four identical component names create a higher-valence pattern. |
| `_PO_` | 2 | `epo`, `oh` | `oh~0~1` | None | Mirrors `_EO_`: `epo` binds `_EG_`/`_PERYT_`; activated `oh~1` binds another `_PO_.epo`. | Names are undefined. |

## 5. Compartments, anchors, initial species, and setup

No compartments or anchors occur. Initial pools are `_PERYT_` = 1,140, `_EO_` with `oh~0` = 580, `_PO_` with `oh~0` = 70,907, and `_EG_` = 27,373. All repeated `_EG_` and `_PERYT_` `oh` sites start in state `p` and unbound. Both `_EO_` and `_PO_` start with free `epo`, inactive `oh~0`, and no preassembled complexes.

## 6. Complete reaction-rule inventory

All rules are unlabeled, irreversible, and use rate `1.0`.

| # | Direction and participants | Exact site/state/bond edit | Rate | Technical interpretation |
| ---: | --- | --- | --- | --- |
| 1 | `_EG_` + `_EO_` → complex | Forms `_EG_.oh–_EO_.epo`; simultaneously changes `_EO_.oh 0→1`. | `1.0` | An `_EG_` repeated `oh~p` site captures `_EO_.epo` and activates the separate `_EO_.oh` flag. |
| 2 | `_EG_` + `_PO_` → complex | Forms `_EG_.oh–_PO_.epo`; changes `_PO_.oh 0→1`. | `1.0` | Same `_EG_` contact logic applied to `_PO_`. |
| 3 | `_PERYT_` + `_EO_` → complex | Forms `_PERYT_.oh–_EO_.epo`; changes `_EO_.oh 0→1`. | `1.0` | Any of four equivalent `_PERYT_.oh~p` sites can activate and bind `_EO_`. |
| 4 | `_PERYT_` + `_PO_` → complex | Forms `_PERYT_.oh–_PO_.epo`; changes `_PO_.oh 0→1`. | `1.0` | Any equivalent `_PERYT_.oh~p` site can activate and bind `_PO_`. |
| 5 | `_EO_` + `_EO_` → dimer | First `_EO_.epo` binds the second `_EO_.oh~1`; the first reactant is constrained to `oh~0` but remains `oh~0`, while the second must already be `oh~1`. | `1.0` | Creates an irreversible heterostate `_EO_` pair; this rule does not itself activate the first `_EO_`. |
| 6 | `_PO_` + `_PO_` → dimer | First `_PO_.epo` binds the second `_PO_.oh~1`; first reactant remains `oh~0`, second is required in `oh~1`. | `1.0` | `_PO_` analogue of rule 5. |

## 7. Observables and technical readouts

No observable block is present. A simulation would expose only species-level output unless observables were added. Useful additions would separately count free/activated `_EO_` and `_PO_`, occupied `_EG_` and `_PERYT_` sites, and the two same-type dimer classes.

## 8. Actions and simulation workflow

There is no action block and no inline command. The metadata advertises ODE compatibility, but the source does not call network generation or an ODE simulation. A caller must choose network-generation limits, simulation duration, steps, and outputs.

## 9. Technical caveats and ambiguities

The biological expansions of all abbreviated molecule/site names are absent. Repeated identical `oh` sites create symmetry-sensitive match multiplicities. Every rule is irreversible and has the same literal rate, and no output is defined. Rules 5 and 6 also require a previously activated partner but do not modify the inactive partner's `oh~0` state, a detail that should be checked against the intended assembly mechanism.
