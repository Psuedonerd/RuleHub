# Published YAML Feature Audit 2 — Updated Definitions

This report re-audits the same 20 same-directory `Published/` BNGL/YAML pairs from `data/yaml_feature_audit.md` using the updated block and compartment-grammar definitions. It does not modify any YAML files; proposed insertions/changes are recorded here only.

## Scope and pairing rule

- Root inspected: `Published/`
- Pairing rule: only `.bngl` files whose `metadata.yaml` is in the same directory are eligible.
- Pilot size: 20 BNGL/YAML pairs, matching the first audit.
- YAML edit policy for this pass: no YAML files were modified; this Markdown file records proposed insertions/changes only.

## Updated detection policy

### Block presence versus active block contents

- For block-based BNGL constructs, a `uses_*` boolean records whether the relevant block/construct is present, even if the block is empty.
- Active block contents are counted separately. An active entry is an uncommented, nonempty line between the `begin ...` and `end ...` delimiters.
- Example: `begin functions` followed immediately by `end functions` still proposes `uses_functions: true`, but the report records `active function entries: 0`.

### Compartment grammar definitions

- A `begin compartments` block is reported as block evidence, but it does not by itself determine either compartment-grammar boolean.
- A model may be marked true for both compartment booleans if both syntax forms are actively present.

## Field definitions

- `uses_cbngl_compartments`: `true` when uncommented CBNGL-style `Molecule(...)@Compartment` syntax is detected. This grammar places the whole molecule pattern in the named compartment.
- `uses_vcell_compartments`: `true` when uncommented VCell-style `@Compartment:Molecule(...)` syntax is detected. This grammar attaches the compartment after the molecule pattern and can appear on individual molecule patterns inside a complex.
- `uses_energy`: `true` when an energy-pattern block is present, even if empty; active entries are counted separately.
- `uses_functions`: `true` when a `begin functions` block is present and there are uncommented lines within this block; active entries are counted separately.
- `uses_moveconnected`: `true` when an uncommented `moveConnected` call is detected.
- `uses_trash_molecules`: `true` when the BNGL uses a `Trash(...)` molecule/pattern as an explicit sink species.
- `uses_anchors`: `true` when a `begin anchors` block is present, even if empty; active entries are counted separately.
- `uses_multiple_identical_sites`: `true` when a declared molecule type repeats the same component/site name within one molecule type.
- `uses_deletes_molecules`: `true` when an uncommented `DeleteMolecules` modifier/action is detected.
- `uses_exclude_include_reactants`: `true` when an uncommented `exclude_reactants` or `include_reactants` modifier is detected.
- `uses_generate_network`: `true` when an uncommented `generate_network(...)` action is detected.
- `default_sim_command`: First uncommented simulation command found in priority order: `simulate_ode`, `simulate_ssa`, `simulate_nf`, `simulate`.

## Batch summary

| Field | Detected true | Detected false | Detected null | Current YAML missing | Proposed insertions/changes |
|---|---:|---:|---:|---:|---:|
| `uses_cbngl_compartments` | 0 | 20 | 0 | 20 | 20 |
| `uses_vcell_compartments` | 9 | 11 | 0 | 20 | 20 |
| `uses_energy` | 0 | 20 | 0 | 0 | 0 |
| `uses_functions` | 13 | 7 | 0 | 0 | 0 |
| `uses_moveconnected` | 0 | 20 | 0 | 20 | 20 |
| `uses_trash_molecules` | 2 | 18 | 0 | 20 | 20 |
| `uses_anchors` | 5 | 15 | 0 | 20 | 20 |
| `uses_multiple_identical_sites` | 5 | 15 | 0 | 20 | 20 |
| `uses_deletes_molecules` | 4 | 16 | 0 | 20 | 20 |
| `uses_exclude_include_reactants` | 2 | 18 | 0 | 20 | 20 |
| `uses_generate_network` | 14 | 6 | 0 | 20 | 20 |
| `default_sim_command` | 0 | 0 | 1 | 20 | 20 |

## Audited pairs

| # | BNGL path | YAML path | Proposed updates |
|---:|---|---|---:|
| 1 | `Published/Blinovegfr/Blinov_egfr.bngl` | `Published/Blinovegfr/metadata.yaml` | 10 |
| 2 | `Published/Blinovran/Blinov_ran.bngl` | `Published/Blinovran/metadata.yaml` | 10 |
| 3 | `Published/RulebasedRantransport/Rule_based_Ran_transport.bngl` | `Published/RulebasedRantransport/metadata.yaml` | 10 |
| 4 | `Published/RulebasedRantransportdraft/Rule_based_Ran_transport_draft.bngl` | `Published/RulebasedRantransportdraft/metadata.yaml` | 10 |
| 5 | `Published/Rulebasedegfrcompart/Rule_based_egfr_compart.bngl` | `Published/Rulebasedegfrcompart/metadata.yaml` | 10 |
| 6 | `Published/Rulebasedegfrtutorial/Rule_based_egfr_tutorial.bngl` | `Published/Rulebasedegfrtutorial/metadata.yaml` | 10 |
| 7 | `Published/Jung2017/Jung_2017.bngl` | `Published/Jung2017/metadata.yaml` | 10 |
| 8 | `Published/Lang2024/Lang_2024.bngl` | `Published/Lang2024/metadata.yaml` | 10 |
| 9 | `Published/Nosbisch2022/Nosbisch_2022.bngl` | `Published/Nosbisch2022/metadata.yaml` | 10 |
| 10 | `Published/Barua2007/Barua_2007.bngl` | `Published/Barua2007/metadata.yaml` | 10 |
| 11 | `Published/An2009/An_2009.bngl` | `Published/An2009/metadata.yaml` | 10 |
| 12 | `Published/Ligon2014/Ligon_2014.bngl` | `Published/Ligon2014/metadata.yaml` | 10 |
| 13 | `Published/Zhang2023/Zhang_2023.bngl` | `Published/Zhang2023/metadata.yaml` | 10 |
| 14 | `Published/ChylekFceRI2014/ChylekFceRI_2014.bngl` | `Published/ChylekFceRI2014/metadata.yaml` | 10 |
| 15 | `Published/Dolan2015/Dolan_2015.bngl` | `Published/Dolan2015/metadata.yaml` | 10 |
| 16 | `Published/Hlavacek2001/kinetic_proofreading_hlavacek2001.bngl` | `Published/Hlavacek2001/metadata.yaml` | 10 |
| 17 | `Published/Dembo1978/blbr_dembo1978.bngl` | `Published/Dembo1978/metadata.yaml` | 10 |
| 18 | `Published/Dreisigmeyer2008/lac_operon_dreisigmeyer2008.bngl` | `Published/Dreisigmeyer2008/metadata.yaml` | 10 |
| 19 | `Published/Gardner2000/genetic_switch_gardner2000.bngl` | `Published/Gardner2000/metadata.yaml` | 10 |
| 20 | `Published/Barua2009/Barua_2009.bngl` | `Published/Barua2009/metadata.yaml` | 10 |

## Per-model findings

### 1. `Published/Blinovegfr` / `Blinov_egfr.bngl`

- BNGL: `Published/Blinovegfr/Blinov_egfr.bngl`
- YAML: `Published/Blinovegfr/metadata.yaml`
- Un-commented action commands detected: `simulate_nf`
- Block diagnostics:
  - `compartments` block present: `true`; active entries: `3`
  - `anchors` block present: `true`; active entries: `2`
  - `functions` block present: `true`; active entries: `0`
  - `energy_patterns` block present: `false`; active entries: `0`
- VCell-style compartment examples:
  - `@EC:EGF(rb)`
  - `@M:EGFR(ecd,tmd,y1068~u,y1173~u)`
  - `@Cyt:Shc(sh3,Y773~u)`
  - `@M:EGFR()`
  - `@EC:EGF()`
- CBNGL-style compartment examples: none detected.
- Multiple-identical-site evidence: none detected in molecule-type declarations.

| Field | Detected from BNGL | Current YAML value | Proposed action | Proposed value | Short rationale |
|---|---|---|---|---|---|
| `uses_cbngl_compartments` | `false` | `missing` | insert | `false` | No CBNGL-style `Molecule(...)@Compartment` patterns detected. |
| `uses_vcell_compartments` | `true` | `missing` | insert | `true` | VCell-style `@Compartment:Molecule(...)` examples detected. |
| `uses_energy` | `false` | `false` | keep | `false` | energy-pattern block is absent; active entries: 0. |
| `uses_functions` | `true` | `true` | keep | `true` | `begin functions` block is present; active entries: 0. |
| `uses_moveconnected` | `false` | `missing` | insert | `false` | No `moveConnected` call detected. |
| `uses_trash_molecules` | `false` | `missing` | insert | `false` | No `Trash(...)` molecule/pattern detected. |
| `uses_anchors` | `true` | `missing` | insert | `true` | `begin anchors` block is present; active entries: 2. |
| `uses_multiple_identical_sites` | `false` | `missing` | insert | `false` | No repeated site names found in molecule-type declarations. |
| `uses_deletes_molecules` | `false` | `missing` | insert | `false` | No `DeleteMolecules` modifier/action detected. |
| `uses_exclude_include_reactants` | `false` | `missing` | insert | `false` | No include/exclude reactants modifier detected. |
| `uses_generate_network` | `false` | `missing` | insert | `false` | No uncommented `generate_network(...)` action detected. |
| `default_sim_command` | `simulate_nf` | `missing` | insert | `simulate_nf` | Default command chosen from uncommented actions: simulate_nf. |

Proposed YAML updates:
- `uses_cbngl_compartments`: insert; proposed value `false`. Rationale: No CBNGL-style `Molecule(...)@Compartment` patterns detected.
- `uses_vcell_compartments`: insert; proposed value `true`. Rationale: VCell-style `@Compartment:Molecule(...)` examples detected.
- `uses_moveconnected`: insert; proposed value `false`. Rationale: No `moveConnected` call detected.
- `uses_trash_molecules`: insert; proposed value `false`. Rationale: No `Trash(...)` molecule/pattern detected.
- `uses_anchors`: insert; proposed value `true`. Rationale: `begin anchors` block is present; active entries: 2.
- `uses_multiple_identical_sites`: insert; proposed value `false`. Rationale: No repeated site names found in molecule-type declarations.
- `uses_deletes_molecules`: insert; proposed value `false`. Rationale: No `DeleteMolecules` modifier/action detected.
- `uses_exclude_include_reactants`: insert; proposed value `false`. Rationale: No include/exclude reactants modifier detected.
- `uses_generate_network`: insert; proposed value `false`. Rationale: No uncommented `generate_network(...)` action detected.
- `default_sim_command`: insert; proposed value `simulate_nf`. Rationale: Default command chosen from uncommented actions: simulate_nf.

### 2. `Published/Blinovran` / `Blinov_ran.bngl`

- BNGL: `Published/Blinovran/Blinov_ran.bngl`
- YAML: `Published/Blinovran/metadata.yaml`
- Un-commented action commands detected: `simulate_nf`
- Block diagnostics:
  - `compartments` block present: `true`; active entries: `5`
  - `anchors` block present: `true`; active entries: `1`
  - `functions` block present: `true`; active entries: `0`
  - `energy_patterns` block present: `false`; active entries: `0`
- VCell-style compartment examples:
  - `@nuc:Ran(cargo!1)`
  - `@nuc:RCC1(site)`
  - `@cyt:Ran()`
  - `@cyt:C()`
  - `@nuc:RCC1()`
- CBNGL-style compartment examples: none detected.
- Multiple-identical-site evidence: none detected in molecule-type declarations.

| Field | Detected from BNGL | Current YAML value | Proposed action | Proposed value | Short rationale |
|---|---|---|---|---|---|
| `uses_cbngl_compartments` | `false` | `missing` | insert | `false` | No CBNGL-style `Molecule(...)@Compartment` patterns detected. |
| `uses_vcell_compartments` | `true` | `missing` | insert | `true` | VCell-style `@Compartment:Molecule(...)` examples detected. |
| `uses_energy` | `false` | `false` | keep | `false` | energy-pattern block is absent; active entries: 0. |
| `uses_functions` | `true` | `true` | keep | `true` | `begin functions` block is present; active entries: 0. |
| `uses_moveconnected` | `false` | `missing` | insert | `false` | No `moveConnected` call detected. |
| `uses_trash_molecules` | `false` | `missing` | insert | `false` | No `Trash(...)` molecule/pattern detected. |
| `uses_anchors` | `true` | `missing` | insert | `true` | `begin anchors` block is present; active entries: 1. |
| `uses_multiple_identical_sites` | `false` | `missing` | insert | `false` | No repeated site names found in molecule-type declarations. |
| `uses_deletes_molecules` | `false` | `missing` | insert | `false` | No `DeleteMolecules` modifier/action detected. |
| `uses_exclude_include_reactants` | `false` | `missing` | insert | `false` | No include/exclude reactants modifier detected. |
| `uses_generate_network` | `false` | `missing` | insert | `false` | No uncommented `generate_network(...)` action detected. |
| `default_sim_command` | `simulate_nf` | `missing` | insert | `simulate_nf` | Default command chosen from uncommented actions: simulate_nf. |

Proposed YAML updates:
- `uses_cbngl_compartments`: insert; proposed value `false`. Rationale: No CBNGL-style `Molecule(...)@Compartment` patterns detected.
- `uses_vcell_compartments`: insert; proposed value `true`. Rationale: VCell-style `@Compartment:Molecule(...)` examples detected.
- `uses_moveconnected`: insert; proposed value `false`. Rationale: No `moveConnected` call detected.
- `uses_trash_molecules`: insert; proposed value `false`. Rationale: No `Trash(...)` molecule/pattern detected.
- `uses_anchors`: insert; proposed value `true`. Rationale: `begin anchors` block is present; active entries: 1.
- `uses_multiple_identical_sites`: insert; proposed value `false`. Rationale: No repeated site names found in molecule-type declarations.
- `uses_deletes_molecules`: insert; proposed value `false`. Rationale: No `DeleteMolecules` modifier/action detected.
- `uses_exclude_include_reactants`: insert; proposed value `false`. Rationale: No include/exclude reactants modifier detected.
- `uses_generate_network`: insert; proposed value `false`. Rationale: No uncommented `generate_network(...)` action detected.
- `default_sim_command`: insert; proposed value `simulate_nf`. Rationale: Default command chosen from uncommented actions: simulate_nf.

### 3. `Published/RulebasedRantransport` / `Rule_based_Ran_transport.bngl`

- BNGL: `Published/RulebasedRantransport/Rule_based_Ran_transport.bngl`
- YAML: `Published/RulebasedRantransport/metadata.yaml`
- Un-commented action commands detected: `generate_network`
- Block diagnostics:
  - `compartments` block present: `true`; active entries: `5`
  - `anchors` block present: `true`; active entries: `1`
  - `functions` block present: `true`; active entries: `0`
  - `energy_patterns` block present: `false`; active entries: `0`
- VCell-style compartment examples:
  - `@nuc:Ran(cargo!1)`
  - `@nuc:RCC1(site)`
  - `@cyt:Ran()`
  - `@cyt:C()`
  - `@nuc:RCC1()`
- CBNGL-style compartment examples: none detected.
- Multiple-identical-site evidence: none detected in molecule-type declarations.

| Field | Detected from BNGL | Current YAML value | Proposed action | Proposed value | Short rationale |
|---|---|---|---|---|---|
| `uses_cbngl_compartments` | `false` | `missing` | insert | `false` | No CBNGL-style `Molecule(...)@Compartment` patterns detected. |
| `uses_vcell_compartments` | `true` | `missing` | insert | `true` | VCell-style `@Compartment:Molecule(...)` examples detected. |
| `uses_energy` | `false` | `false` | keep | `false` | energy-pattern block is absent; active entries: 0. |
| `uses_functions` | `true` | `true` | keep | `true` | `begin functions` block is present; active entries: 0. |
| `uses_moveconnected` | `false` | `missing` | insert | `false` | No `moveConnected` call detected. |
| `uses_trash_molecules` | `false` | `missing` | insert | `false` | No `Trash(...)` molecule/pattern detected. |
| `uses_anchors` | `true` | `missing` | insert | `true` | `begin anchors` block is present; active entries: 1. |
| `uses_multiple_identical_sites` | `false` | `missing` | insert | `false` | No repeated site names found in molecule-type declarations. |
| `uses_deletes_molecules` | `false` | `missing` | insert | `false` | No `DeleteMolecules` modifier/action detected. |
| `uses_exclude_include_reactants` | `false` | `missing` | insert | `false` | No include/exclude reactants modifier detected. |
| `uses_generate_network` | `true` | `missing` | insert | `true` | `generate_network(...)` action detected. |
| `default_sim_command` | `generate_network` | `missing` | insert | `generate_network` | Default command chosen from uncommented actions: generate_network. |

Proposed YAML updates:
- `uses_cbngl_compartments`: insert; proposed value `false`. Rationale: No CBNGL-style `Molecule(...)@Compartment` patterns detected.
- `uses_vcell_compartments`: insert; proposed value `true`. Rationale: VCell-style `@Compartment:Molecule(...)` examples detected.
- `uses_moveconnected`: insert; proposed value `false`. Rationale: No `moveConnected` call detected.
- `uses_trash_molecules`: insert; proposed value `false`. Rationale: No `Trash(...)` molecule/pattern detected.
- `uses_anchors`: insert; proposed value `true`. Rationale: `begin anchors` block is present; active entries: 1.
- `uses_multiple_identical_sites`: insert; proposed value `false`. Rationale: No repeated site names found in molecule-type declarations.
- `uses_deletes_molecules`: insert; proposed value `false`. Rationale: No `DeleteMolecules` modifier/action detected.
- `uses_exclude_include_reactants`: insert; proposed value `false`. Rationale: No include/exclude reactants modifier detected.
- `uses_generate_network`: insert; proposed value `true`. Rationale: `generate_network(...)` action detected.
- `default_sim_command`: insert; proposed value `generate_network`. Rationale: Default command chosen from uncommented actions: generate_network.

### 4. `Published/RulebasedRantransportdraft` / `Rule_based_Ran_transport_draft.bngl`

- BNGL: `Published/RulebasedRantransportdraft/Rule_based_Ran_transport_draft.bngl`
- YAML: `Published/RulebasedRantransportdraft/metadata.yaml`
- Un-commented action commands detected: `generate_network`
- Block diagnostics:
  - `compartments` block present: `true`; active entries: `5`
  - `anchors` block present: `true`; active entries: `1`
  - `functions` block present: `true`; active entries: `0`
  - `energy_patterns` block present: `false`; active entries: `0`
- VCell-style compartment examples:
  - `@nuc:Ran(cargo!1)`
  - `@nuc:RCC1(site)`
  - `@cyt:Ran()`
  - `@cyt:C()`
  - `@nuc:RCC1()`
- CBNGL-style compartment examples: none detected.
- Multiple-identical-site evidence: none detected in molecule-type declarations.

| Field | Detected from BNGL | Current YAML value | Proposed action | Proposed value | Short rationale |
|---|---|---|---|---|---|
| `uses_cbngl_compartments` | `false` | `missing` | insert | `false` | No CBNGL-style `Molecule(...)@Compartment` patterns detected. |
| `uses_vcell_compartments` | `true` | `missing` | insert | `true` | VCell-style `@Compartment:Molecule(...)` examples detected. |
| `uses_energy` | `false` | `false` | keep | `false` | energy-pattern block is absent; active entries: 0. |
| `uses_functions` | `true` | `true` | keep | `true` | `begin functions` block is present; active entries: 0. |
| `uses_moveconnected` | `false` | `missing` | insert | `false` | No `moveConnected` call detected. |
| `uses_trash_molecules` | `false` | `missing` | insert | `false` | No `Trash(...)` molecule/pattern detected. |
| `uses_anchors` | `true` | `missing` | insert | `true` | `begin anchors` block is present; active entries: 1. |
| `uses_multiple_identical_sites` | `false` | `missing` | insert | `false` | No repeated site names found in molecule-type declarations. |
| `uses_deletes_molecules` | `false` | `missing` | insert | `false` | No `DeleteMolecules` modifier/action detected. |
| `uses_exclude_include_reactants` | `false` | `missing` | insert | `false` | No include/exclude reactants modifier detected. |
| `uses_generate_network` | `true` | `missing` | insert | `true` | `generate_network(...)` action detected. |
| `default_sim_command` | `generate_network` | `missing` | insert | `generate_network` | Default command chosen from uncommented actions: generate_network. |

Proposed YAML updates:
- `uses_cbngl_compartments`: insert; proposed value `false`. Rationale: No CBNGL-style `Molecule(...)@Compartment` patterns detected.
- `uses_vcell_compartments`: insert; proposed value `true`. Rationale: VCell-style `@Compartment:Molecule(...)` examples detected.
- `uses_moveconnected`: insert; proposed value `false`. Rationale: No `moveConnected` call detected.
- `uses_trash_molecules`: insert; proposed value `false`. Rationale: No `Trash(...)` molecule/pattern detected.
- `uses_anchors`: insert; proposed value `true`. Rationale: `begin anchors` block is present; active entries: 1.
- `uses_multiple_identical_sites`: insert; proposed value `false`. Rationale: No repeated site names found in molecule-type declarations.
- `uses_deletes_molecules`: insert; proposed value `false`. Rationale: No `DeleteMolecules` modifier/action detected.
- `uses_exclude_include_reactants`: insert; proposed value `false`. Rationale: No include/exclude reactants modifier detected.
- `uses_generate_network`: insert; proposed value `true`. Rationale: `generate_network(...)` action detected.
- `default_sim_command`: insert; proposed value `generate_network`. Rationale: Default command chosen from uncommented actions: generate_network.

### 5. `Published/Rulebasedegfrcompart` / `Rule_based_egfr_compart.bngl`

- BNGL: `Published/Rulebasedegfrcompart/Rule_based_egfr_compart.bngl`
- YAML: `Published/Rulebasedegfrcompart/metadata.yaml`
- Un-commented action commands detected: `generate_network`
- Block diagnostics:
  - `compartments` block present: `true`; active entries: `3`
  - `anchors` block present: `true`; active entries: `2`
  - `functions` block present: `true`; active entries: `0`
  - `energy_patterns` block present: `false`; active entries: `0`
- VCell-style compartment examples:
  - `@EC:EGF(rb)`
  - `@M:EGFR(ecd,tmd,y1068~u,y1173~u)`
  - `@Cyt:Shc(sh3,Y773~u)`
  - `@M:EGFR()`
  - `@EC:EGF()`
- CBNGL-style compartment examples: none detected.
- Multiple-identical-site evidence: none detected in molecule-type declarations.

| Field | Detected from BNGL | Current YAML value | Proposed action | Proposed value | Short rationale |
|---|---|---|---|---|---|
| `uses_cbngl_compartments` | `false` | `missing` | insert | `false` | No CBNGL-style `Molecule(...)@Compartment` patterns detected. |
| `uses_vcell_compartments` | `true` | `missing` | insert | `true` | VCell-style `@Compartment:Molecule(...)` examples detected. |
| `uses_energy` | `false` | `false` | keep | `false` | energy-pattern block is absent; active entries: 0. |
| `uses_functions` | `true` | `true` | keep | `true` | `begin functions` block is present; active entries: 0. |
| `uses_moveconnected` | `false` | `missing` | insert | `false` | No `moveConnected` call detected. |
| `uses_trash_molecules` | `false` | `missing` | insert | `false` | No `Trash(...)` molecule/pattern detected. |
| `uses_anchors` | `true` | `missing` | insert | `true` | `begin anchors` block is present; active entries: 2. |
| `uses_multiple_identical_sites` | `false` | `missing` | insert | `false` | No repeated site names found in molecule-type declarations. |
| `uses_deletes_molecules` | `false` | `missing` | insert | `false` | No `DeleteMolecules` modifier/action detected. |
| `uses_exclude_include_reactants` | `false` | `missing` | insert | `false` | No include/exclude reactants modifier detected. |
| `uses_generate_network` | `true` | `missing` | insert | `true` | `generate_network(...)` action detected. |
| `default_sim_command` | `generate_network` | `missing` | insert | `generate_network` | Default command chosen from uncommented actions: generate_network. |

Proposed YAML updates:
- `uses_cbngl_compartments`: insert; proposed value `false`. Rationale: No CBNGL-style `Molecule(...)@Compartment` patterns detected.
- `uses_vcell_compartments`: insert; proposed value `true`. Rationale: VCell-style `@Compartment:Molecule(...)` examples detected.
- `uses_moveconnected`: insert; proposed value `false`. Rationale: No `moveConnected` call detected.
- `uses_trash_molecules`: insert; proposed value `false`. Rationale: No `Trash(...)` molecule/pattern detected.
- `uses_anchors`: insert; proposed value `true`. Rationale: `begin anchors` block is present; active entries: 2.
- `uses_multiple_identical_sites`: insert; proposed value `false`. Rationale: No repeated site names found in molecule-type declarations.
- `uses_deletes_molecules`: insert; proposed value `false`. Rationale: No `DeleteMolecules` modifier/action detected.
- `uses_exclude_include_reactants`: insert; proposed value `false`. Rationale: No include/exclude reactants modifier detected.
- `uses_generate_network`: insert; proposed value `true`. Rationale: `generate_network(...)` action detected.
- `default_sim_command`: insert; proposed value `generate_network`. Rationale: Default command chosen from uncommented actions: generate_network.

### 6. `Published/Rulebasedegfrtutorial` / `Rule_based_egfr_tutorial.bngl`

- BNGL: `Published/Rulebasedegfrtutorial/Rule_based_egfr_tutorial.bngl`
- YAML: `Published/Rulebasedegfrtutorial/metadata.yaml`
- Un-commented action commands detected: `generate_network`
- Block diagnostics:
  - `compartments` block present: `true`; active entries: `1`
  - `anchors` block present: `false`; active entries: `0`
  - `functions` block present: `true`; active entries: `0`
  - `energy_patterns` block present: `false`; active entries: `0`
- VCell-style compartment examples:
  - `@c0:EGFR(ecd,tmd,Y1~u,Y2~u)`
  - `@c0:EGF(Site)`
  - `@c0:Grb2(sh2)`
  - `@c0:Shc(sh3,Y~p)`
  - `@c0:Shc(sh3,Y~u)`
- CBNGL-style compartment examples: none detected.
- Multiple-identical-site evidence: none detected in molecule-type declarations.

| Field | Detected from BNGL | Current YAML value | Proposed action | Proposed value | Short rationale |
|---|---|---|---|---|---|
| `uses_cbngl_compartments` | `false` | `missing` | insert | `false` | No CBNGL-style `Molecule(...)@Compartment` patterns detected. |
| `uses_vcell_compartments` | `true` | `missing` | insert | `true` | VCell-style `@Compartment:Molecule(...)` examples detected. |
| `uses_energy` | `false` | `false` | keep | `false` | energy-pattern block is absent; active entries: 0. |
| `uses_functions` | `true` | `true` | keep | `true` | `begin functions` block is present; active entries: 0. |
| `uses_moveconnected` | `false` | `missing` | insert | `false` | No `moveConnected` call detected. |
| `uses_trash_molecules` | `false` | `missing` | insert | `false` | No `Trash(...)` molecule/pattern detected. |
| `uses_anchors` | `false` | `missing` | insert | `false` | `begin anchors` block is absent; active entries: 0. |
| `uses_multiple_identical_sites` | `false` | `missing` | insert | `false` | No repeated site names found in molecule-type declarations. |
| `uses_deletes_molecules` | `false` | `missing` | insert | `false` | No `DeleteMolecules` modifier/action detected. |
| `uses_exclude_include_reactants` | `false` | `missing` | insert | `false` | No include/exclude reactants modifier detected. |
| `uses_generate_network` | `true` | `missing` | insert | `true` | `generate_network(...)` action detected. |
| `default_sim_command` | `generate_network` | `missing` | insert | `generate_network` | Default command chosen from uncommented actions: generate_network. |

Proposed YAML updates:
- `uses_cbngl_compartments`: insert; proposed value `false`. Rationale: No CBNGL-style `Molecule(...)@Compartment` patterns detected.
- `uses_vcell_compartments`: insert; proposed value `true`. Rationale: VCell-style `@Compartment:Molecule(...)` examples detected.
- `uses_moveconnected`: insert; proposed value `false`. Rationale: No `moveConnected` call detected.
- `uses_trash_molecules`: insert; proposed value `false`. Rationale: No `Trash(...)` molecule/pattern detected.
- `uses_anchors`: insert; proposed value `false`. Rationale: `begin anchors` block is absent; active entries: 0.
- `uses_multiple_identical_sites`: insert; proposed value `false`. Rationale: No repeated site names found in molecule-type declarations.
- `uses_deletes_molecules`: insert; proposed value `false`. Rationale: No `DeleteMolecules` modifier/action detected.
- `uses_exclude_include_reactants`: insert; proposed value `false`. Rationale: No include/exclude reactants modifier detected.
- `uses_generate_network`: insert; proposed value `true`. Rationale: `generate_network(...)` action detected.
- `default_sim_command`: insert; proposed value `generate_network`. Rationale: Default command chosen from uncommented actions: generate_network.

### 7. `Published/Jung2017` / `Jung_2017.bngl`

- BNGL: `Published/Jung2017/Jung_2017.bngl`
- YAML: `Published/Jung2017/metadata.yaml`
- Un-commented action commands detected: `generate_network`
- Block diagnostics:
  - `compartments` block present: `true`; active entries: `3`
  - `anchors` block present: `false`; active entries: `0`
  - `functions` block present: `true`; active entries: `2`
  - `energy_patterns` block present: `false`; active entries: `0`
- VCell-style compartment examples:
  - `@EC:Oxo_EC()`
  - `@PM:M1R(L,S228~u,S273~u,Arr,GRK,PP1,CK2)`
  - `@PM:Oxo(R!1)`
  - `@cytoplasm:Arrestin(RLP,MEK,PP2A)`
  - `@cytoplasm:ERK(MEK,s~u,PP2A,PP1)`
- CBNGL-style compartment examples: none detected.
- Multiple-identical-site evidence: none detected in molecule-type declarations.

| Field | Detected from BNGL | Current YAML value | Proposed action | Proposed value | Short rationale |
|---|---|---|---|---|---|
| `uses_cbngl_compartments` | `false` | `missing` | insert | `false` | No CBNGL-style `Molecule(...)@Compartment` patterns detected. |
| `uses_vcell_compartments` | `true` | `missing` | insert | `true` | VCell-style `@Compartment:Molecule(...)` examples detected. |
| `uses_energy` | `false` | `false` | keep | `false` | energy-pattern block is absent; active entries: 0. |
| `uses_functions` | `true` | `true` | keep | `true` | `begin functions` block is present; active entries: 2. |
| `uses_moveconnected` | `false` | `missing` | insert | `false` | No `moveConnected` call detected. |
| `uses_trash_molecules` | `false` | `missing` | insert | `false` | No `Trash(...)` molecule/pattern detected. |
| `uses_anchors` | `false` | `missing` | insert | `false` | `begin anchors` block is absent; active entries: 0. |
| `uses_multiple_identical_sites` | `false` | `missing` | insert | `false` | No repeated site names found in molecule-type declarations. |
| `uses_deletes_molecules` | `false` | `missing` | insert | `false` | No `DeleteMolecules` modifier/action detected. |
| `uses_exclude_include_reactants` | `false` | `missing` | insert | `false` | No include/exclude reactants modifier detected. |
| `uses_generate_network` | `true` | `missing` | insert | `true` | `generate_network(...)` action detected. |
| `default_sim_command` | `generate_network` | `missing` | insert | `generate_network` | Default command chosen from uncommented actions: generate_network. |

Proposed YAML updates:
- `uses_cbngl_compartments`: insert; proposed value `false`. Rationale: No CBNGL-style `Molecule(...)@Compartment` patterns detected.
- `uses_vcell_compartments`: insert; proposed value `true`. Rationale: VCell-style `@Compartment:Molecule(...)` examples detected.
- `uses_moveconnected`: insert; proposed value `false`. Rationale: No `moveConnected` call detected.
- `uses_trash_molecules`: insert; proposed value `false`. Rationale: No `Trash(...)` molecule/pattern detected.
- `uses_anchors`: insert; proposed value `false`. Rationale: `begin anchors` block is absent; active entries: 0.
- `uses_multiple_identical_sites`: insert; proposed value `false`. Rationale: No repeated site names found in molecule-type declarations.
- `uses_deletes_molecules`: insert; proposed value `false`. Rationale: No `DeleteMolecules` modifier/action detected.
- `uses_exclude_include_reactants`: insert; proposed value `false`. Rationale: No include/exclude reactants modifier detected.
- `uses_generate_network`: insert; proposed value `true`. Rationale: `generate_network(...)` action detected.
- `default_sim_command`: insert; proposed value `generate_network`. Rationale: Default command chosen from uncommented actions: generate_network.

### 8. `Published/Lang2024` / `Lang_2024.bngl`

- BNGL: `Published/Lang2024/Lang_2024.bngl`
- YAML: `Published/Lang2024/metadata.yaml`
- Un-commented action commands detected: `simulate`, `generate_network`
- Block diagnostics:
  - `compartments` block present: `true`; active entries: `1`
  - `anchors` block present: `false`; active entries: `0`
  - `functions` block present: `false`; active entries: `0`
  - `energy_patterns` block present: `false`; active entries: `0`
- VCell-style compartment examples:
  - `@cell:CCND()`
  - `@cell:CCNE(CDKN1A)`
  - `@cell:E2F(DBD,RB1,Ser332~u)`
  - `@cell:E2F(DBD,RB1,Ser332~p)`
  - `@cell:CCNA(CDKN1A)`
- CBNGL-style compartment examples: none detected.
- Multiple-identical-site evidence: none detected in molecule-type declarations.

| Field | Detected from BNGL | Current YAML value | Proposed action | Proposed value | Short rationale |
|---|---|---|---|---|---|
| `uses_cbngl_compartments` | `false` | `missing` | insert | `false` | No CBNGL-style `Molecule(...)@Compartment` patterns detected. |
| `uses_vcell_compartments` | `true` | `missing` | insert | `true` | VCell-style `@Compartment:Molecule(...)` examples detected. |
| `uses_energy` | `false` | `false` | keep | `false` | energy-pattern block is absent; active entries: 0. |
| `uses_functions` | `false` | `false` | keep | `false` | `begin functions` block is absent; active entries: 0. |
| `uses_moveconnected` | `false` | `missing` | insert | `false` | No `moveConnected` call detected. |
| `uses_trash_molecules` | `false` | `missing` | insert | `false` | No `Trash(...)` molecule/pattern detected. |
| `uses_anchors` | `false` | `missing` | insert | `false` | `begin anchors` block is absent; active entries: 0. |
| `uses_multiple_identical_sites` | `false` | `missing` | insert | `false` | No repeated site names found in molecule-type declarations. |
| `uses_deletes_molecules` | `true` | `missing` | insert | `true` | `DeleteMolecules` modifier/action detected. |
| `uses_exclude_include_reactants` | `true` | `missing` | insert | `true` | `include_reactants`/`exclude_reactants` modifier detected. |
| `uses_generate_network` | `true` | `missing` | insert | `true` | `generate_network(...)` action detected. |
| `default_sim_command` | `simulate` | `missing` | insert | `simulate` | Default command chosen from uncommented actions: simulate. |

Proposed YAML updates:
- `uses_cbngl_compartments`: insert; proposed value `false`. Rationale: No CBNGL-style `Molecule(...)@Compartment` patterns detected.
- `uses_vcell_compartments`: insert; proposed value `true`. Rationale: VCell-style `@Compartment:Molecule(...)` examples detected.
- `uses_moveconnected`: insert; proposed value `false`. Rationale: No `moveConnected` call detected.
- `uses_trash_molecules`: insert; proposed value `false`. Rationale: No `Trash(...)` molecule/pattern detected.
- `uses_anchors`: insert; proposed value `false`. Rationale: `begin anchors` block is absent; active entries: 0.
- `uses_multiple_identical_sites`: insert; proposed value `false`. Rationale: No repeated site names found in molecule-type declarations.
- `uses_deletes_molecules`: insert; proposed value `true`. Rationale: `DeleteMolecules` modifier/action detected.
- `uses_exclude_include_reactants`: insert; proposed value `true`. Rationale: `include_reactants`/`exclude_reactants` modifier detected.
- `uses_generate_network`: insert; proposed value `true`. Rationale: `generate_network(...)` action detected.
- `default_sim_command`: insert; proposed value `simulate`. Rationale: Default command chosen from uncommented actions: simulate.

### 9. `Published/Nosbisch2022` / `Nosbisch_2022.bngl`

- BNGL: `Published/Nosbisch2022/Nosbisch_2022.bngl`
- YAML: `Published/Nosbisch2022/metadata.yaml`
- Un-commented action commands detected: `generate_network`
- Block diagnostics:
  - `compartments` block present: `true`; active entries: `1`
  - `anchors` block present: `false`; active entries: `0`
  - `functions` block present: `true`; active entries: `0`
  - `energy_patterns` block present: `false`; active entries: `0`
- VCell-style compartment examples:
  - `@cell:RTK(pY)`
  - `@cell:PLCgamma1(nSH2,Tyr783~u,cSH2!1,core~inactive!1)`
  - `@cell:RTK()`
  - `@cell:PLCgamma1()`
  - `@cell:PLCgamma1(core~active!?)`
- CBNGL-style compartment examples: none detected.
- Multiple-identical-site evidence: none detected in molecule-type declarations.

| Field | Detected from BNGL | Current YAML value | Proposed action | Proposed value | Short rationale |
|---|---|---|---|---|---|
| `uses_cbngl_compartments` | `false` | `missing` | insert | `false` | No CBNGL-style `Molecule(...)@Compartment` patterns detected. |
| `uses_vcell_compartments` | `true` | `missing` | insert | `true` | VCell-style `@Compartment:Molecule(...)` examples detected. |
| `uses_energy` | `false` | `false` | keep | `false` | energy-pattern block is absent; active entries: 0. |
| `uses_functions` | `true` | `true` | keep | `true` | `begin functions` block is present; active entries: 0. |
| `uses_moveconnected` | `false` | `missing` | insert | `false` | No `moveConnected` call detected. |
| `uses_trash_molecules` | `false` | `missing` | insert | `false` | No `Trash(...)` molecule/pattern detected. |
| `uses_anchors` | `false` | `missing` | insert | `false` | `begin anchors` block is absent; active entries: 0. |
| `uses_multiple_identical_sites` | `false` | `missing` | insert | `false` | No repeated site names found in molecule-type declarations. |
| `uses_deletes_molecules` | `false` | `missing` | insert | `false` | No `DeleteMolecules` modifier/action detected. |
| `uses_exclude_include_reactants` | `false` | `missing` | insert | `false` | No include/exclude reactants modifier detected. |
| `uses_generate_network` | `true` | `missing` | insert | `true` | `generate_network(...)` action detected. |
| `default_sim_command` | `generate_network` | `missing` | insert | `generate_network` | Default command chosen from uncommented actions: generate_network. |

Proposed YAML updates:
- `uses_cbngl_compartments`: insert; proposed value `false`. Rationale: No CBNGL-style `Molecule(...)@Compartment` patterns detected.
- `uses_vcell_compartments`: insert; proposed value `true`. Rationale: VCell-style `@Compartment:Molecule(...)` examples detected.
- `uses_moveconnected`: insert; proposed value `false`. Rationale: No `moveConnected` call detected.
- `uses_trash_molecules`: insert; proposed value `false`. Rationale: No `Trash(...)` molecule/pattern detected.
- `uses_anchors`: insert; proposed value `false`. Rationale: `begin anchors` block is absent; active entries: 0.
- `uses_multiple_identical_sites`: insert; proposed value `false`. Rationale: No repeated site names found in molecule-type declarations.
- `uses_deletes_molecules`: insert; proposed value `false`. Rationale: No `DeleteMolecules` modifier/action detected.
- `uses_exclude_include_reactants`: insert; proposed value `false`. Rationale: No include/exclude reactants modifier detected.
- `uses_generate_network`: insert; proposed value `true`. Rationale: `generate_network(...)` action detected.
- `default_sim_command`: insert; proposed value `generate_network`. Rationale: Default command chosen from uncommented actions: generate_network.

### 10. `Published/Barua2007` / `Barua_2007.bngl`

- BNGL: `Published/Barua2007/Barua_2007.bngl`
- YAML: `Published/Barua2007/metadata.yaml`
- Un-commented action commands detected: `simulate_ode`, `generate_network`
- Block diagnostics:
  - `compartments` block present: `false`; active entries: `0`
  - `anchors` block present: `false`; active entries: `0`
  - `functions` block present: `false`; active entries: `0`
  - `energy_patterns` block present: `false`; active entries: `0`
- VCell-style compartment examples: none detected.
- CBNGL-style compartment examples: none detected.
- Multiple-identical-site evidence: none detected in molecule-type declarations.

| Field | Detected from BNGL | Current YAML value | Proposed action | Proposed value | Short rationale |
|---|---|---|---|---|---|
| `uses_cbngl_compartments` | `false` | `missing` | insert | `false` | No CBNGL-style `Molecule(...)@Compartment` patterns detected. |
| `uses_vcell_compartments` | `false` | `missing` | insert | `false` | No VCell-style `@Compartment:Molecule(...)` patterns detected. |
| `uses_energy` | `false` | `false` | keep | `false` | energy-pattern block is absent; active entries: 0. |
| `uses_functions` | `false` | `false` | keep | `false` | `begin functions` block is absent; active entries: 0. |
| `uses_moveconnected` | `false` | `missing` | insert | `false` | No `moveConnected` call detected. |
| `uses_trash_molecules` | `false` | `missing` | insert | `false` | No `Trash(...)` molecule/pattern detected. |
| `uses_anchors` | `false` | `missing` | insert | `false` | `begin anchors` block is absent; active entries: 0. |
| `uses_multiple_identical_sites` | `false` | `missing` | insert | `false` | No repeated site names found in molecule-type declarations. |
| `uses_deletes_molecules` | `false` | `missing` | insert | `false` | No `DeleteMolecules` modifier/action detected. |
| `uses_exclude_include_reactants` | `true` | `missing` | insert | `true` | `include_reactants`/`exclude_reactants` modifier detected. |
| `uses_generate_network` | `true` | `missing` | insert | `true` | `generate_network(...)` action detected. |
| `default_sim_command` | `simulate_ode` | `missing` | insert | `simulate_ode` | Default command chosen from uncommented actions: simulate_ode. |

Proposed YAML updates:
- `uses_cbngl_compartments`: insert; proposed value `false`. Rationale: No CBNGL-style `Molecule(...)@Compartment` patterns detected.
- `uses_vcell_compartments`: insert; proposed value `false`. Rationale: No VCell-style `@Compartment:Molecule(...)` patterns detected.
- `uses_moveconnected`: insert; proposed value `false`. Rationale: No `moveConnected` call detected.
- `uses_trash_molecules`: insert; proposed value `false`. Rationale: No `Trash(...)` molecule/pattern detected.
- `uses_anchors`: insert; proposed value `false`. Rationale: `begin anchors` block is absent; active entries: 0.
- `uses_multiple_identical_sites`: insert; proposed value `false`. Rationale: No repeated site names found in molecule-type declarations.
- `uses_deletes_molecules`: insert; proposed value `false`. Rationale: No `DeleteMolecules` modifier/action detected.
- `uses_exclude_include_reactants`: insert; proposed value `true`. Rationale: `include_reactants`/`exclude_reactants` modifier detected.
- `uses_generate_network`: insert; proposed value `true`. Rationale: `generate_network(...)` action detected.
- `default_sim_command`: insert; proposed value `simulate_ode`. Rationale: Default command chosen from uncommented actions: simulate_ode.

### 11. `Published/An2009` / `An_2009.bngl`

- BNGL: `Published/An2009/An_2009.bngl`
- YAML: `Published/An2009/metadata.yaml`
- Un-commented action commands detected: `simulate_ode`, `generate_network`
- Block diagnostics:
  - `compartments` block present: `false`; active entries: `0`
  - `anchors` block present: `false`; active entries: `0`
  - `functions` block present: `false`; active entries: `0`
  - `energy_patterns` block present: `false`; active entries: `0`
- VCell-style compartment examples: none detected.
- CBNGL-style compartment examples: none detected.
- Multiple-identical-site evidence:
  - DNA: repeated c in `DNA(A20,TNF,iNOS,IL10,IkB,c,c)`

| Field | Detected from BNGL | Current YAML value | Proposed action | Proposed value | Short rationale |
|---|---|---|---|---|---|
| `uses_cbngl_compartments` | `false` | `missing` | insert | `false` | No CBNGL-style `Molecule(...)@Compartment` patterns detected. |
| `uses_vcell_compartments` | `false` | `missing` | insert | `false` | No VCell-style `@Compartment:Molecule(...)` patterns detected. |
| `uses_energy` | `false` | `false` | keep | `false` | energy-pattern block is absent; active entries: 0. |
| `uses_functions` | `false` | `false` | keep | `false` | `begin functions` block is absent; active entries: 0. |
| `uses_moveconnected` | `false` | `missing` | insert | `false` | No `moveConnected` call detected. |
| `uses_trash_molecules` | `true` | `missing` | insert | `true` | `Trash(...)` sink molecule/pattern detected. |
| `uses_anchors` | `false` | `missing` | insert | `false` | `begin anchors` block is absent; active entries: 0. |
| `uses_multiple_identical_sites` | `true` | `missing` | insert | `true` | At least one molecule type declares a repeated site name. |
| `uses_deletes_molecules` | `false` | `missing` | insert | `false` | No `DeleteMolecules` modifier/action detected. |
| `uses_exclude_include_reactants` | `false` | `missing` | insert | `false` | No include/exclude reactants modifier detected. |
| `uses_generate_network` | `true` | `missing` | insert | `true` | `generate_network(...)` action detected. |
| `default_sim_command` | `simulate_ode` | `missing` | insert | `simulate_ode` | Default command chosen from uncommented actions: simulate_ode. |

Proposed YAML updates:
- `uses_cbngl_compartments`: insert; proposed value `false`. Rationale: No CBNGL-style `Molecule(...)@Compartment` patterns detected.
- `uses_vcell_compartments`: insert; proposed value `false`. Rationale: No VCell-style `@Compartment:Molecule(...)` patterns detected.
- `uses_moveconnected`: insert; proposed value `false`. Rationale: No `moveConnected` call detected.
- `uses_trash_molecules`: insert; proposed value `true`. Rationale: `Trash(...)` sink molecule/pattern detected.
- `uses_anchors`: insert; proposed value `false`. Rationale: `begin anchors` block is absent; active entries: 0.
- `uses_multiple_identical_sites`: insert; proposed value `true`. Rationale: At least one molecule type declares a repeated site name.
- `uses_deletes_molecules`: insert; proposed value `false`. Rationale: No `DeleteMolecules` modifier/action detected.
- `uses_exclude_include_reactants`: insert; proposed value `false`. Rationale: No include/exclude reactants modifier detected.
- `uses_generate_network`: insert; proposed value `true`. Rationale: `generate_network(...)` action detected.
- `default_sim_command`: insert; proposed value `simulate_ode`. Rationale: Default command chosen from uncommented actions: simulate_ode.

### 12. `Published/Ligon2014` / `Ligon_2014.bngl`

- BNGL: `Published/Ligon2014/Ligon_2014.bngl`
- YAML: `Published/Ligon2014/metadata.yaml`
- Un-commented action commands detected: `simulate_nf`
- Block diagnostics:
  - `compartments` block present: `false`; active entries: `0`
  - `anchors` block present: `false`; active entries: `0`
  - `functions` block present: `true`; active entries: `1`
  - `energy_patterns` block present: `false`; active entries: `0`
- VCell-style compartment examples: none detected.
- CBNGL-style compartment examples: none detected.
- Multiple-identical-site evidence: none detected in molecule-type declarations.

| Field | Detected from BNGL | Current YAML value | Proposed action | Proposed value | Short rationale |
|---|---|---|---|---|---|
| `uses_cbngl_compartments` | `false` | `missing` | insert | `false` | No CBNGL-style `Molecule(...)@Compartment` patterns detected. |
| `uses_vcell_compartments` | `false` | `missing` | insert | `false` | No VCell-style `@Compartment:Molecule(...)` patterns detected. |
| `uses_energy` | `false` | `false` | keep | `false` | energy-pattern block is absent; active entries: 0. |
| `uses_functions` | `true` | `true` | keep | `true` | `begin functions` block is present; active entries: 1. |
| `uses_moveconnected` | `false` | `missing` | insert | `false` | No `moveConnected` call detected. |
| `uses_trash_molecules` | `false` | `missing` | insert | `false` | No `Trash(...)` molecule/pattern detected. |
| `uses_anchors` | `false` | `missing` | insert | `false` | `begin anchors` block is absent; active entries: 0. |
| `uses_multiple_identical_sites` | `false` | `missing` | insert | `false` | No repeated site names found in molecule-type declarations. |
| `uses_deletes_molecules` | `true` | `missing` | insert | `true` | `DeleteMolecules` modifier/action detected. |
| `uses_exclude_include_reactants` | `false` | `missing` | insert | `false` | No include/exclude reactants modifier detected. |
| `uses_generate_network` | `false` | `missing` | insert | `false` | No uncommented `generate_network(...)` action detected. |
| `default_sim_command` | `simulate_nf` | `missing` | insert | `simulate_nf` | Default command chosen from uncommented actions: simulate_nf. |

Proposed YAML updates:
- `uses_cbngl_compartments`: insert; proposed value `false`. Rationale: No CBNGL-style `Molecule(...)@Compartment` patterns detected.
- `uses_vcell_compartments`: insert; proposed value `false`. Rationale: No VCell-style `@Compartment:Molecule(...)` patterns detected.
- `uses_moveconnected`: insert; proposed value `false`. Rationale: No `moveConnected` call detected.
- `uses_trash_molecules`: insert; proposed value `false`. Rationale: No `Trash(...)` molecule/pattern detected.
- `uses_anchors`: insert; proposed value `false`. Rationale: `begin anchors` block is absent; active entries: 0.
- `uses_multiple_identical_sites`: insert; proposed value `false`. Rationale: No repeated site names found in molecule-type declarations.
- `uses_deletes_molecules`: insert; proposed value `true`. Rationale: `DeleteMolecules` modifier/action detected.
- `uses_exclude_include_reactants`: insert; proposed value `false`. Rationale: No include/exclude reactants modifier detected.
- `uses_generate_network`: insert; proposed value `false`. Rationale: No uncommented `generate_network(...)` action detected.
- `default_sim_command`: insert; proposed value `simulate_nf`. Rationale: Default command chosen from uncommented actions: simulate_nf.

### 13. `Published/Zhang2023` / `Zhang_2023.bngl`

- BNGL: `Published/Zhang2023/Zhang_2023.bngl`
- YAML: `Published/Zhang2023/metadata.yaml`
- Un-commented action commands detected: `generate_network`
- Block diagnostics:
  - `compartments` block present: `false`; active entries: `0`
  - `anchors` block present: `false`; active entries: `0`
  - `functions` block present: `false`; active entries: `0`
  - `energy_patterns` block present: `false`; active entries: `0`
- VCell-style compartment examples: none detected.
- CBNGL-style compartment examples: none detected.
- Multiple-identical-site evidence:
  - vegf: repeated r in `vegf(r,r,nrp1bd,c~s~i~i2~r)`
  - CaM: repeated CCaM, NCaM in `CaM(NCaM,NCaM,CCaM,CCaM,CaMtargetbd)`

| Field | Detected from BNGL | Current YAML value | Proposed action | Proposed value | Short rationale |
|---|---|---|---|---|---|
| `uses_cbngl_compartments` | `false` | `missing` | insert | `false` | No CBNGL-style `Molecule(...)@Compartment` patterns detected. |
| `uses_vcell_compartments` | `false` | `missing` | insert | `false` | No VCell-style `@Compartment:Molecule(...)` patterns detected. |
| `uses_energy` | `false` | `false` | keep | `false` | energy-pattern block is absent; active entries: 0. |
| `uses_functions` | `false` | `false` | keep | `false` | `begin functions` block is absent; active entries: 0. |
| `uses_moveconnected` | `false` | `missing` | insert | `false` | No `moveConnected` call detected. |
| `uses_trash_molecules` | `true` | `missing` | insert | `true` | `Trash(...)` sink molecule/pattern detected. |
| `uses_anchors` | `false` | `missing` | insert | `false` | `begin anchors` block is absent; active entries: 0. |
| `uses_multiple_identical_sites` | `true` | `missing` | insert | `true` | At least one molecule type declares a repeated site name. |
| `uses_deletes_molecules` | `false` | `missing` | insert | `false` | No `DeleteMolecules` modifier/action detected. |
| `uses_exclude_include_reactants` | `false` | `missing` | insert | `false` | No include/exclude reactants modifier detected. |
| `uses_generate_network` | `true` | `missing` | insert | `true` | `generate_network(...)` action detected. |
| `default_sim_command` | `generate_network` | `missing` | insert | `generate_network` | Default command chosen from uncommented actions: generate_network. |

Proposed YAML updates:
- `uses_cbngl_compartments`: insert; proposed value `false`. Rationale: No CBNGL-style `Molecule(...)@Compartment` patterns detected.
- `uses_vcell_compartments`: insert; proposed value `false`. Rationale: No VCell-style `@Compartment:Molecule(...)` patterns detected.
- `uses_moveconnected`: insert; proposed value `false`. Rationale: No `moveConnected` call detected.
- `uses_trash_molecules`: insert; proposed value `true`. Rationale: `Trash(...)` sink molecule/pattern detected.
- `uses_anchors`: insert; proposed value `false`. Rationale: `begin anchors` block is absent; active entries: 0.
- `uses_multiple_identical_sites`: insert; proposed value `true`. Rationale: At least one molecule type declares a repeated site name.
- `uses_deletes_molecules`: insert; proposed value `false`. Rationale: No `DeleteMolecules` modifier/action detected.
- `uses_exclude_include_reactants`: insert; proposed value `false`. Rationale: No include/exclude reactants modifier detected.
- `uses_generate_network`: insert; proposed value `true`. Rationale: `generate_network(...)` action detected.
- `default_sim_command`: insert; proposed value `generate_network`. Rationale: Default command chosen from uncommented actions: generate_network.

### 14. `Published/ChylekFceRI2014` / `ChylekFceRI_2014.bngl`

- BNGL: `Published/ChylekFceRI2014/ChylekFceRI_2014.bngl`
- YAML: `Published/ChylekFceRI2014/metadata.yaml`
- Un-commented action commands detected: `writeXML`
- Block diagnostics:
  - `compartments` block present: `false`; active entries: `0`
  - `anchors` block present: `false`; active entries: `0`
  - `functions` block present: `false`; active entries: `0`
  - `energy_patterns` block present: `false`; active entries: `0`
- VCell-style compartment examples: none detected.
- CBNGL-style compartment examples: none detected.
- Multiple-identical-site evidence:
  - Lig: repeated hap in `Lig(hap~b~e,hap~b~e)`
  - Rec: repeated fab in `Rec(fab,fab,b_Y218~0~P,b_Y224~0~P,g_Y65_Y76~0~P)`

| Field | Detected from BNGL | Current YAML value | Proposed action | Proposed value | Short rationale |
|---|---|---|---|---|---|
| `uses_cbngl_compartments` | `false` | `missing` | insert | `false` | No CBNGL-style `Molecule(...)@Compartment` patterns detected. |
| `uses_vcell_compartments` | `false` | `missing` | insert | `false` | No VCell-style `@Compartment:Molecule(...)` patterns detected. |
| `uses_energy` | `false` | `false` | keep | `false` | energy-pattern block is absent; active entries: 0. |
| `uses_functions` | `false` | `false` | keep | `false` | `begin functions` block is absent; active entries: 0. |
| `uses_moveconnected` | `false` | `missing` | insert | `false` | No `moveConnected` call detected. |
| `uses_trash_molecules` | `false` | `missing` | insert | `false` | No `Trash(...)` molecule/pattern detected. |
| `uses_anchors` | `false` | `missing` | insert | `false` | `begin anchors` block is absent; active entries: 0. |
| `uses_multiple_identical_sites` | `true` | `missing` | insert | `true` | At least one molecule type declares a repeated site name. |
| `uses_deletes_molecules` | `true` | `missing` | insert | `true` | `DeleteMolecules` modifier/action detected. |
| `uses_exclude_include_reactants` | `false` | `missing` | insert | `false` | No include/exclude reactants modifier detected. |
| `uses_generate_network` | `false` | `missing` | insert | `false` | No uncommented `generate_network(...)` action detected. |
| `default_sim_command` | `null` | `missing` | insert | `null` | Default command chosen from uncommented actions: none. |

Proposed YAML updates:
- `uses_cbngl_compartments`: insert; proposed value `false`. Rationale: No CBNGL-style `Molecule(...)@Compartment` patterns detected.
- `uses_vcell_compartments`: insert; proposed value `false`. Rationale: No VCell-style `@Compartment:Molecule(...)` patterns detected.
- `uses_moveconnected`: insert; proposed value `false`. Rationale: No `moveConnected` call detected.
- `uses_trash_molecules`: insert; proposed value `false`. Rationale: No `Trash(...)` molecule/pattern detected.
- `uses_anchors`: insert; proposed value `false`. Rationale: `begin anchors` block is absent; active entries: 0.
- `uses_multiple_identical_sites`: insert; proposed value `true`. Rationale: At least one molecule type declares a repeated site name.
- `uses_deletes_molecules`: insert; proposed value `true`. Rationale: `DeleteMolecules` modifier/action detected.
- `uses_exclude_include_reactants`: insert; proposed value `false`. Rationale: No include/exclude reactants modifier detected.
- `uses_generate_network`: insert; proposed value `false`. Rationale: No uncommented `generate_network(...)` action detected.
- `default_sim_command`: insert; proposed value `null`. Rationale: Default command chosen from uncommented actions: none.

### 15. `Published/Dolan2015` / `Dolan_2015.bngl`

- BNGL: `Published/Dolan2015/Dolan_2015.bngl`
- YAML: `Published/Dolan2015/metadata.yaml`
- Un-commented action commands detected: `simulate_nf`
- Block diagnostics:
  - `compartments` block present: `false`; active entries: `0`
  - `anchors` block present: `false`; active entries: `0`
  - `functions` block present: `true`; active entries: `9`
  - `energy_patterns` block present: `false`; active entries: `0`
- VCell-style compartment examples: none detected.
- CBNGL-style compartment examples: none detected.
- Multiple-identical-site evidence: none detected in molecule-type declarations.

| Field | Detected from BNGL | Current YAML value | Proposed action | Proposed value | Short rationale |
|---|---|---|---|---|---|
| `uses_cbngl_compartments` | `false` | `missing` | insert | `false` | No CBNGL-style `Molecule(...)@Compartment` patterns detected. |
| `uses_vcell_compartments` | `false` | `missing` | insert | `false` | No VCell-style `@Compartment:Molecule(...)` patterns detected. |
| `uses_energy` | `false` | `false` | keep | `false` | energy-pattern block is absent; active entries: 0. |
| `uses_functions` | `true` | `true` | keep | `true` | `begin functions` block is present; active entries: 9. |
| `uses_moveconnected` | `false` | `missing` | insert | `false` | No `moveConnected` call detected. |
| `uses_trash_molecules` | `false` | `missing` | insert | `false` | No `Trash(...)` molecule/pattern detected. |
| `uses_anchors` | `false` | `missing` | insert | `false` | `begin anchors` block is absent; active entries: 0. |
| `uses_multiple_identical_sites` | `false` | `missing` | insert | `false` | No repeated site names found in molecule-type declarations. |
| `uses_deletes_molecules` | `true` | `missing` | insert | `true` | `DeleteMolecules` modifier/action detected. |
| `uses_exclude_include_reactants` | `false` | `missing` | insert | `false` | No include/exclude reactants modifier detected. |
| `uses_generate_network` | `false` | `missing` | insert | `false` | No uncommented `generate_network(...)` action detected. |
| `default_sim_command` | `simulate_nf` | `missing` | insert | `simulate_nf` | Default command chosen from uncommented actions: simulate_nf. |

Proposed YAML updates:
- `uses_cbngl_compartments`: insert; proposed value `false`. Rationale: No CBNGL-style `Molecule(...)@Compartment` patterns detected.
- `uses_vcell_compartments`: insert; proposed value `false`. Rationale: No VCell-style `@Compartment:Molecule(...)` patterns detected.
- `uses_moveconnected`: insert; proposed value `false`. Rationale: No `moveConnected` call detected.
- `uses_trash_molecules`: insert; proposed value `false`. Rationale: No `Trash(...)` molecule/pattern detected.
- `uses_anchors`: insert; proposed value `false`. Rationale: `begin anchors` block is absent; active entries: 0.
- `uses_multiple_identical_sites`: insert; proposed value `false`. Rationale: No repeated site names found in molecule-type declarations.
- `uses_deletes_molecules`: insert; proposed value `true`. Rationale: `DeleteMolecules` modifier/action detected.
- `uses_exclude_include_reactants`: insert; proposed value `false`. Rationale: No include/exclude reactants modifier detected.
- `uses_generate_network`: insert; proposed value `false`. Rationale: No uncommented `generate_network(...)` action detected.
- `default_sim_command`: insert; proposed value `simulate_nf`. Rationale: Default command chosen from uncommented actions: simulate_nf.

### 16. `Published/Hlavacek2001` / `kinetic_proofreading_hlavacek2001.bngl`

- BNGL: `Published/Hlavacek2001/kinetic_proofreading_hlavacek2001.bngl`
- YAML: `Published/Hlavacek2001/metadata.yaml`
- Un-commented action commands detected: `simulate`, `generate_network`
- Block diagnostics:
  - `compartments` block present: `false`; active entries: `0`
  - `anchors` block present: `false`; active entries: `0`
  - `functions` block present: `true`; active entries: `4`
  - `energy_patterns` block present: `false`; active entries: `0`
- VCell-style compartment examples: none detected.
- CBNGL-style compartment examples: none detected.
- Multiple-identical-site evidence:
  - L: repeated r in `L(r,r,mod~0~1~2~3~4~5)`

| Field | Detected from BNGL | Current YAML value | Proposed action | Proposed value | Short rationale |
|---|---|---|---|---|---|
| `uses_cbngl_compartments` | `false` | `missing` | insert | `false` | No CBNGL-style `Molecule(...)@Compartment` patterns detected. |
| `uses_vcell_compartments` | `false` | `missing` | insert | `false` | No VCell-style `@Compartment:Molecule(...)` patterns detected. |
| `uses_energy` | `false` | `false` | keep | `false` | energy-pattern block is absent; active entries: 0. |
| `uses_functions` | `true` | `true` | keep | `true` | `begin functions` block is present; active entries: 4. |
| `uses_moveconnected` | `false` | `missing` | insert | `false` | No `moveConnected` call detected. |
| `uses_trash_molecules` | `false` | `missing` | insert | `false` | No `Trash(...)` molecule/pattern detected. |
| `uses_anchors` | `false` | `missing` | insert | `false` | `begin anchors` block is absent; active entries: 0. |
| `uses_multiple_identical_sites` | `true` | `missing` | insert | `true` | At least one molecule type declares a repeated site name. |
| `uses_deletes_molecules` | `false` | `missing` | insert | `false` | No `DeleteMolecules` modifier/action detected. |
| `uses_exclude_include_reactants` | `false` | `missing` | insert | `false` | No include/exclude reactants modifier detected. |
| `uses_generate_network` | `true` | `missing` | insert | `true` | `generate_network(...)` action detected. |
| `default_sim_command` | `simulate` | `missing` | insert | `simulate` | Default command chosen from uncommented actions: simulate. |

Proposed YAML updates:
- `uses_cbngl_compartments`: insert; proposed value `false`. Rationale: No CBNGL-style `Molecule(...)@Compartment` patterns detected.
- `uses_vcell_compartments`: insert; proposed value `false`. Rationale: No VCell-style `@Compartment:Molecule(...)` patterns detected.
- `uses_moveconnected`: insert; proposed value `false`. Rationale: No `moveConnected` call detected.
- `uses_trash_molecules`: insert; proposed value `false`. Rationale: No `Trash(...)` molecule/pattern detected.
- `uses_anchors`: insert; proposed value `false`. Rationale: `begin anchors` block is absent; active entries: 0.
- `uses_multiple_identical_sites`: insert; proposed value `true`. Rationale: At least one molecule type declares a repeated site name.
- `uses_deletes_molecules`: insert; proposed value `false`. Rationale: No `DeleteMolecules` modifier/action detected.
- `uses_exclude_include_reactants`: insert; proposed value `false`. Rationale: No include/exclude reactants modifier detected.
- `uses_generate_network`: insert; proposed value `true`. Rationale: `generate_network(...)` action detected.
- `default_sim_command`: insert; proposed value `simulate`. Rationale: Default command chosen from uncommented actions: simulate.

### 17. `Published/Dembo1978` / `blbr_dembo1978.bngl`

- BNGL: `Published/Dembo1978/blbr_dembo1978.bngl`
- YAML: `Published/Dembo1978/metadata.yaml`
- Un-commented action commands detected: `simulate`
- Block diagnostics:
  - `compartments` block present: `false`; active entries: `0`
  - `anchors` block present: `false`; active entries: `0`
  - `functions` block present: `false`; active entries: `0`
  - `energy_patterns` block present: `false`; active entries: `0`
- VCell-style compartment examples: none detected.
- CBNGL-style compartment examples: none detected.
- Multiple-identical-site evidence:
  - L: repeated r in `L(r,r)`
  - R: repeated l in `R(l,l)`

| Field | Detected from BNGL | Current YAML value | Proposed action | Proposed value | Short rationale |
|---|---|---|---|---|---|
| `uses_cbngl_compartments` | `false` | `missing` | insert | `false` | No CBNGL-style `Molecule(...)@Compartment` patterns detected. |
| `uses_vcell_compartments` | `false` | `missing` | insert | `false` | No VCell-style `@Compartment:Molecule(...)` patterns detected. |
| `uses_energy` | `false` | `false` | keep | `false` | energy-pattern block is absent; active entries: 0. |
| `uses_functions` | `false` | `false` | keep | `false` | `begin functions` block is absent; active entries: 0. |
| `uses_moveconnected` | `false` | `missing` | insert | `false` | No `moveConnected` call detected. |
| `uses_trash_molecules` | `false` | `missing` | insert | `false` | No `Trash(...)` molecule/pattern detected. |
| `uses_anchors` | `false` | `missing` | insert | `false` | `begin anchors` block is absent; active entries: 0. |
| `uses_multiple_identical_sites` | `true` | `missing` | insert | `true` | At least one molecule type declares a repeated site name. |
| `uses_deletes_molecules` | `false` | `missing` | insert | `false` | No `DeleteMolecules` modifier/action detected. |
| `uses_exclude_include_reactants` | `false` | `missing` | insert | `false` | No include/exclude reactants modifier detected. |
| `uses_generate_network` | `false` | `missing` | insert | `false` | No uncommented `generate_network(...)` action detected. |
| `default_sim_command` | `simulate` | `missing` | insert | `simulate` | Default command chosen from uncommented actions: simulate. |

Proposed YAML updates:
- `uses_cbngl_compartments`: insert; proposed value `false`. Rationale: No CBNGL-style `Molecule(...)@Compartment` patterns detected.
- `uses_vcell_compartments`: insert; proposed value `false`. Rationale: No VCell-style `@Compartment:Molecule(...)` patterns detected.
- `uses_moveconnected`: insert; proposed value `false`. Rationale: No `moveConnected` call detected.
- `uses_trash_molecules`: insert; proposed value `false`. Rationale: No `Trash(...)` molecule/pattern detected.
- `uses_anchors`: insert; proposed value `false`. Rationale: `begin anchors` block is absent; active entries: 0.
- `uses_multiple_identical_sites`: insert; proposed value `true`. Rationale: At least one molecule type declares a repeated site name.
- `uses_deletes_molecules`: insert; proposed value `false`. Rationale: No `DeleteMolecules` modifier/action detected.
- `uses_exclude_include_reactants`: insert; proposed value `false`. Rationale: No include/exclude reactants modifier detected.
- `uses_generate_network`: insert; proposed value `false`. Rationale: No uncommented `generate_network(...)` action detected.
- `default_sim_command`: insert; proposed value `simulate`. Rationale: Default command chosen from uncommented actions: simulate.

### 18. `Published/Dreisigmeyer2008` / `lac_operon_dreisigmeyer2008.bngl`

- BNGL: `Published/Dreisigmeyer2008/lac_operon_dreisigmeyer2008.bngl`
- YAML: `Published/Dreisigmeyer2008/metadata.yaml`
- Un-commented action commands detected: `simulate`, `generate_network`
- Block diagnostics:
  - `compartments` block present: `false`; active entries: `0`
  - `anchors` block present: `false`; active entries: `0`
  - `functions` block present: `true`; active entries: `12`
  - `energy_patterns` block present: `false`; active entries: `0`
- VCell-style compartment examples: none detected.
- CBNGL-style compartment examples: none detected.
- Multiple-identical-site evidence: none detected in molecule-type declarations.

| Field | Detected from BNGL | Current YAML value | Proposed action | Proposed value | Short rationale |
|---|---|---|---|---|---|
| `uses_cbngl_compartments` | `false` | `missing` | insert | `false` | No CBNGL-style `Molecule(...)@Compartment` patterns detected. |
| `uses_vcell_compartments` | `false` | `missing` | insert | `false` | No VCell-style `@Compartment:Molecule(...)` patterns detected. |
| `uses_energy` | `false` | `false` | keep | `false` | energy-pattern block is absent; active entries: 0. |
| `uses_functions` | `true` | `true` | keep | `true` | `begin functions` block is present; active entries: 12. |
| `uses_moveconnected` | `false` | `missing` | insert | `false` | No `moveConnected` call detected. |
| `uses_trash_molecules` | `false` | `missing` | insert | `false` | No `Trash(...)` molecule/pattern detected. |
| `uses_anchors` | `false` | `missing` | insert | `false` | `begin anchors` block is absent; active entries: 0. |
| `uses_multiple_identical_sites` | `false` | `missing` | insert | `false` | No repeated site names found in molecule-type declarations. |
| `uses_deletes_molecules` | `false` | `missing` | insert | `false` | No `DeleteMolecules` modifier/action detected. |
| `uses_exclude_include_reactants` | `false` | `missing` | insert | `false` | No include/exclude reactants modifier detected. |
| `uses_generate_network` | `true` | `missing` | insert | `true` | `generate_network(...)` action detected. |
| `default_sim_command` | `simulate` | `missing` | insert | `simulate` | Default command chosen from uncommented actions: simulate. |

Proposed YAML updates:
- `uses_cbngl_compartments`: insert; proposed value `false`. Rationale: No CBNGL-style `Molecule(...)@Compartment` patterns detected.
- `uses_vcell_compartments`: insert; proposed value `false`. Rationale: No VCell-style `@Compartment:Molecule(...)` patterns detected.
- `uses_moveconnected`: insert; proposed value `false`. Rationale: No `moveConnected` call detected.
- `uses_trash_molecules`: insert; proposed value `false`. Rationale: No `Trash(...)` molecule/pattern detected.
- `uses_anchors`: insert; proposed value `false`. Rationale: `begin anchors` block is absent; active entries: 0.
- `uses_multiple_identical_sites`: insert; proposed value `false`. Rationale: No repeated site names found in molecule-type declarations.
- `uses_deletes_molecules`: insert; proposed value `false`. Rationale: No `DeleteMolecules` modifier/action detected.
- `uses_exclude_include_reactants`: insert; proposed value `false`. Rationale: No include/exclude reactants modifier detected.
- `uses_generate_network`: insert; proposed value `true`. Rationale: `generate_network(...)` action detected.
- `default_sim_command`: insert; proposed value `simulate`. Rationale: Default command chosen from uncommented actions: simulate.

### 19. `Published/Gardner2000` / `genetic_switch_gardner2000.bngl`

- BNGL: `Published/Gardner2000/genetic_switch_gardner2000.bngl`
- YAML: `Published/Gardner2000/metadata.yaml`
- Un-commented action commands detected: `simulate`, `generate_network`
- Block diagnostics:
  - `compartments` block present: `false`; active entries: `0`
  - `anchors` block present: `false`; active entries: `0`
  - `functions` block present: `true`; active entries: `2`
  - `energy_patterns` block present: `false`; active entries: `0`
- VCell-style compartment examples: none detected.
- CBNGL-style compartment examples: none detected.
- Multiple-identical-site evidence: none detected in molecule-type declarations.

| Field | Detected from BNGL | Current YAML value | Proposed action | Proposed value | Short rationale |
|---|---|---|---|---|---|
| `uses_cbngl_compartments` | `false` | `missing` | insert | `false` | No CBNGL-style `Molecule(...)@Compartment` patterns detected. |
| `uses_vcell_compartments` | `false` | `missing` | insert | `false` | No VCell-style `@Compartment:Molecule(...)` patterns detected. |
| `uses_energy` | `false` | `false` | keep | `false` | energy-pattern block is absent; active entries: 0. |
| `uses_functions` | `true` | `true` | keep | `true` | `begin functions` block is present; active entries: 2. |
| `uses_moveconnected` | `false` | `missing` | insert | `false` | No `moveConnected` call detected. |
| `uses_trash_molecules` | `false` | `missing` | insert | `false` | No `Trash(...)` molecule/pattern detected. |
| `uses_anchors` | `false` | `missing` | insert | `false` | `begin anchors` block is absent; active entries: 0. |
| `uses_multiple_identical_sites` | `false` | `missing` | insert | `false` | No repeated site names found in molecule-type declarations. |
| `uses_deletes_molecules` | `false` | `missing` | insert | `false` | No `DeleteMolecules` modifier/action detected. |
| `uses_exclude_include_reactants` | `false` | `missing` | insert | `false` | No include/exclude reactants modifier detected. |
| `uses_generate_network` | `true` | `missing` | insert | `true` | `generate_network(...)` action detected. |
| `default_sim_command` | `simulate` | `missing` | insert | `simulate` | Default command chosen from uncommented actions: simulate. |

Proposed YAML updates:
- `uses_cbngl_compartments`: insert; proposed value `false`. Rationale: No CBNGL-style `Molecule(...)@Compartment` patterns detected.
- `uses_vcell_compartments`: insert; proposed value `false`. Rationale: No VCell-style `@Compartment:Molecule(...)` patterns detected.
- `uses_moveconnected`: insert; proposed value `false`. Rationale: No `moveConnected` call detected.
- `uses_trash_molecules`: insert; proposed value `false`. Rationale: No `Trash(...)` molecule/pattern detected.
- `uses_anchors`: insert; proposed value `false`. Rationale: `begin anchors` block is absent; active entries: 0.
- `uses_multiple_identical_sites`: insert; proposed value `false`. Rationale: No repeated site names found in molecule-type declarations.
- `uses_deletes_molecules`: insert; proposed value `false`. Rationale: No `DeleteMolecules` modifier/action detected.
- `uses_exclude_include_reactants`: insert; proposed value `false`. Rationale: No include/exclude reactants modifier detected.
- `uses_generate_network`: insert; proposed value `true`. Rationale: `generate_network(...)` action detected.
- `default_sim_command`: insert; proposed value `simulate`. Rationale: Default command chosen from uncommented actions: simulate.

### 20. `Published/Barua2009` / `Barua_2009.bngl`

- BNGL: `Published/Barua2009/Barua_2009.bngl`
- YAML: `Published/Barua2009/metadata.yaml`
- Un-commented action commands detected: `simulate_ode`, `generate_network`
- Block diagnostics:
  - `compartments` block present: `false`; active entries: `0`
  - `anchors` block present: `false`; active entries: `0`
  - `functions` block present: `false`; active entries: `0`
  - `energy_patterns` block present: `false`; active entries: `0`
- VCell-style compartment examples: none detected.
- CBNGL-style compartment examples: none detected.
- Multiple-identical-site evidence: none detected in molecule-type declarations.

| Field | Detected from BNGL | Current YAML value | Proposed action | Proposed value | Short rationale |
|---|---|---|---|---|---|
| `uses_cbngl_compartments` | `false` | `missing` | insert | `false` | No CBNGL-style `Molecule(...)@Compartment` patterns detected. |
| `uses_vcell_compartments` | `false` | `missing` | insert | `false` | No VCell-style `@Compartment:Molecule(...)` patterns detected. |
| `uses_energy` | `false` | `false` | keep | `false` | energy-pattern block is absent; active entries: 0. |
| `uses_functions` | `false` | `false` | keep | `false` | `begin functions` block is absent; active entries: 0. |
| `uses_moveconnected` | `false` | `missing` | insert | `false` | No `moveConnected` call detected. |
| `uses_trash_molecules` | `false` | `missing` | insert | `false` | No `Trash(...)` molecule/pattern detected. |
| `uses_anchors` | `false` | `missing` | insert | `false` | `begin anchors` block is absent; active entries: 0. |
| `uses_multiple_identical_sites` | `false` | `missing` | insert | `false` | No repeated site names found in molecule-type declarations. |
| `uses_deletes_molecules` | `false` | `missing` | insert | `false` | No `DeleteMolecules` modifier/action detected. |
| `uses_exclude_include_reactants` | `false` | `missing` | insert | `false` | No include/exclude reactants modifier detected. |
| `uses_generate_network` | `true` | `missing` | insert | `true` | `generate_network(...)` action detected. |
| `default_sim_command` | `simulate_ode` | `missing` | insert | `simulate_ode` | Default command chosen from uncommented actions: simulate_ode. |

Proposed YAML updates:
- `uses_cbngl_compartments`: insert; proposed value `false`. Rationale: No CBNGL-style `Molecule(...)@Compartment` patterns detected.
- `uses_vcell_compartments`: insert; proposed value `false`. Rationale: No VCell-style `@Compartment:Molecule(...)` patterns detected.
- `uses_moveconnected`: insert; proposed value `false`. Rationale: No `moveConnected` call detected.
- `uses_trash_molecules`: insert; proposed value `false`. Rationale: No `Trash(...)` molecule/pattern detected.
- `uses_anchors`: insert; proposed value `false`. Rationale: `begin anchors` block is absent; active entries: 0.
- `uses_multiple_identical_sites`: insert; proposed value `false`. Rationale: No repeated site names found in molecule-type declarations.
- `uses_deletes_molecules`: insert; proposed value `false`. Rationale: No `DeleteMolecules` modifier/action detected.
- `uses_exclude_include_reactants`: insert; proposed value `false`. Rationale: No include/exclude reactants modifier detected.
- `uses_generate_network`: insert; proposed value `true`. Rationale: `generate_network(...)` action detected.
- `default_sim_command`: insert; proposed value `simulate_ode`. Rationale: Default command chosen from uncommented actions: simulate_ode.
