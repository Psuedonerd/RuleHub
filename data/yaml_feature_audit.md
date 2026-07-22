# Published YAML Feature Audit — Pilot Batch

This report audits 20 same-directory `Published/` BNGL/YAML pairs without editing any YAML files. It compares static BNGL feature detection against the currently present YAML values and lists proposed insertions or changes for the requested metadata fields.

## Scope and pairing rule

- Root inspected: `Published/`
- Pairing rule: only `.bngl` files whose `metadata.yaml` is in the same directory are eligible.
- Pilot size: 20 BNGL/YAML pairs.
- YAML edit policy for this pass: no YAML files were modified; this Markdown file records proposed insertions/changes only.

## Detection definitions

- `uses_cbngl_compartments`: `true` when an uncommented `begin compartments` block or compartment-prefixed pattern such as `@cyt:A()` is detected.
- `uses_vcell_compartments`: `true` when VCell-style anchor semantics are detected through an uncommented `begin anchors` block.
- `uses_energy`: `true` when an uncommented energy-pattern block is detected.
- `uses_functions`: `true` when an uncommented `begin functions` block contains entries.
- `uses_moveconnected`: `true` when an uncommented `moveConnected` call is detected.
- `uses_trash_molecules`: `true` when the BNGL uses a `Trash(...)` molecule/pattern as an explicit sink species.
- `uses_anchors`: `true` when an uncommented `begin anchors` block is detected.
- `uses_multiple_identical_sites`: `true` when a declared molecule type repeats the same component/site name within one molecule type.
- `uses_deletes_molecules`: `true` when an uncommented `DeleteMolecules` modifier/action is detected.
- `uses_exclude_include_reactants`: `true` when an uncommented `exclude_reactants` or `include_reactants` modifier is detected.
- `uses_generate_network`: `true` when an uncommented `generate_network(...)` action is detected.
- `default_sim_command`: First uncommented simulation command found in priority order: `simulate_ode`, `simulate_ssa`, `simulate_nf`, `simulate`; if no simulation is present but `generate_network(...)` is present, propose `generate_network`; otherwise propose `null`.

## Batch summary

| Field | Detected true | Detected false | Detected null | Current YAML missing | Proposed insertions/changes |
|---|---:|---:|---:|---:|---:|
| `uses_cbngl_compartments` | 9 | 11 | 0 | 20 | 20 |
| `uses_vcell_compartments` | 5 | 15 | 0 | 20 | 20 |
| `uses_energy` | 0 | 20 | 0 | 0 | 0 |
| `uses_functions` | 6 | 14 | 0 | 0 | 7 |
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
| 1 | `Published/Blinovegfr/Blinov_egfr.bngl` | `Published/Blinovegfr/metadata.yaml` | 11 |
| 2 | `Published/Blinovran/Blinov_ran.bngl` | `Published/Blinovran/metadata.yaml` | 11 |
| 3 | `Published/RulebasedRantransport/Rule_based_Ran_transport.bngl` | `Published/RulebasedRantransport/metadata.yaml` | 11 |
| 4 | `Published/RulebasedRantransportdraft/Rule_based_Ran_transport_draft.bngl` | `Published/RulebasedRantransportdraft/metadata.yaml` | 11 |
| 5 | `Published/Rulebasedegfrcompart/Rule_based_egfr_compart.bngl` | `Published/Rulebasedegfrcompart/metadata.yaml` | 11 |
| 6 | `Published/Rulebasedegfrtutorial/Rule_based_egfr_tutorial.bngl` | `Published/Rulebasedegfrtutorial/metadata.yaml` | 11 |
| 7 | `Published/Jung2017/Jung_2017.bngl` | `Published/Jung2017/metadata.yaml` | 10 |
| 8 | `Published/Lang2024/Lang_2024.bngl` | `Published/Lang2024/metadata.yaml` | 10 |
| 9 | `Published/Nosbisch2022/Nosbisch_2022.bngl` | `Published/Nosbisch2022/metadata.yaml` | 11 |
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
- Compartments block entries detected: `3`
- Anchor entries detected: `2`
- Multiple-identical-site evidence: none detected in molecule-type declarations.

| Field | Detected from BNGL | Current YAML value | Proposed action | Proposed value |
|---|---|---|---|---|
| `uses_cbngl_compartments` | `true` | `missing` | insert | `true` |
| `uses_vcell_compartments` | `true` | `missing` | insert | `true` |
| `uses_energy` | `false` | `false` | keep | `false` |
| `uses_functions` | `false` | `true` | change from True | `false` |
| `uses_moveconnected` | `false` | `missing` | insert | `false` |
| `uses_trash_molecules` | `false` | `missing` | insert | `false` |
| `uses_anchors` | `true` | `missing` | insert | `true` |
| `uses_multiple_identical_sites` | `false` | `missing` | insert | `false` |
| `uses_deletes_molecules` | `false` | `missing` | insert | `false` |
| `uses_exclude_include_reactants` | `false` | `missing` | insert | `false` |
| `uses_generate_network` | `false` | `missing` | insert | `false` |
| `default_sim_command` | `simulate_nf` | `missing` | insert | `simulate_nf` |

Proposed YAML updates:
- `uses_cbngl_compartments`: insert; proposed value `true`.
- `uses_vcell_compartments`: insert; proposed value `true`.
- `uses_functions`: change from True; proposed value `false`.
- `uses_moveconnected`: insert; proposed value `false`.
- `uses_trash_molecules`: insert; proposed value `false`.
- `uses_anchors`: insert; proposed value `true`.
- `uses_multiple_identical_sites`: insert; proposed value `false`.
- `uses_deletes_molecules`: insert; proposed value `false`.
- `uses_exclude_include_reactants`: insert; proposed value `false`.
- `uses_generate_network`: insert; proposed value `false`.
- `default_sim_command`: insert; proposed value `simulate_nf`.

### 2. `Published/Blinovran` / `Blinov_ran.bngl`

- BNGL: `Published/Blinovran/Blinov_ran.bngl`
- YAML: `Published/Blinovran/metadata.yaml`
- Un-commented action commands detected: `simulate_nf`
- Compartments block entries detected: `5`
- Anchor entries detected: `1`
- Multiple-identical-site evidence: none detected in molecule-type declarations.

| Field | Detected from BNGL | Current YAML value | Proposed action | Proposed value |
|---|---|---|---|---|
| `uses_cbngl_compartments` | `true` | `missing` | insert | `true` |
| `uses_vcell_compartments` | `true` | `missing` | insert | `true` |
| `uses_energy` | `false` | `false` | keep | `false` |
| `uses_functions` | `false` | `true` | change from True | `false` |
| `uses_moveconnected` | `false` | `missing` | insert | `false` |
| `uses_trash_molecules` | `false` | `missing` | insert | `false` |
| `uses_anchors` | `true` | `missing` | insert | `true` |
| `uses_multiple_identical_sites` | `false` | `missing` | insert | `false` |
| `uses_deletes_molecules` | `false` | `missing` | insert | `false` |
| `uses_exclude_include_reactants` | `false` | `missing` | insert | `false` |
| `uses_generate_network` | `false` | `missing` | insert | `false` |
| `default_sim_command` | `simulate_nf` | `missing` | insert | `simulate_nf` |

Proposed YAML updates:
- `uses_cbngl_compartments`: insert; proposed value `true`.
- `uses_vcell_compartments`: insert; proposed value `true`.
- `uses_functions`: change from True; proposed value `false`.
- `uses_moveconnected`: insert; proposed value `false`.
- `uses_trash_molecules`: insert; proposed value `false`.
- `uses_anchors`: insert; proposed value `true`.
- `uses_multiple_identical_sites`: insert; proposed value `false`.
- `uses_deletes_molecules`: insert; proposed value `false`.
- `uses_exclude_include_reactants`: insert; proposed value `false`.
- `uses_generate_network`: insert; proposed value `false`.
- `default_sim_command`: insert; proposed value `simulate_nf`.

### 3. `Published/RulebasedRantransport` / `Rule_based_Ran_transport.bngl`

- BNGL: `Published/RulebasedRantransport/Rule_based_Ran_transport.bngl`
- YAML: `Published/RulebasedRantransport/metadata.yaml`
- Un-commented action commands detected: `generate_network`
- Compartments block entries detected: `5`
- Anchor entries detected: `1`
- Multiple-identical-site evidence: none detected in molecule-type declarations.

| Field | Detected from BNGL | Current YAML value | Proposed action | Proposed value |
|---|---|---|---|---|
| `uses_cbngl_compartments` | `true` | `missing` | insert | `true` |
| `uses_vcell_compartments` | `true` | `missing` | insert | `true` |
| `uses_energy` | `false` | `false` | keep | `false` |
| `uses_functions` | `false` | `true` | change from True | `false` |
| `uses_moveconnected` | `false` | `missing` | insert | `false` |
| `uses_trash_molecules` | `false` | `missing` | insert | `false` |
| `uses_anchors` | `true` | `missing` | insert | `true` |
| `uses_multiple_identical_sites` | `false` | `missing` | insert | `false` |
| `uses_deletes_molecules` | `false` | `missing` | insert | `false` |
| `uses_exclude_include_reactants` | `false` | `missing` | insert | `false` |
| `uses_generate_network` | `true` | `missing` | insert | `true` |
| `default_sim_command` | `generate_network` | `missing` | insert | `generate_network` |

Proposed YAML updates:
- `uses_cbngl_compartments`: insert; proposed value `true`.
- `uses_vcell_compartments`: insert; proposed value `true`.
- `uses_functions`: change from True; proposed value `false`.
- `uses_moveconnected`: insert; proposed value `false`.
- `uses_trash_molecules`: insert; proposed value `false`.
- `uses_anchors`: insert; proposed value `true`.
- `uses_multiple_identical_sites`: insert; proposed value `false`.
- `uses_deletes_molecules`: insert; proposed value `false`.
- `uses_exclude_include_reactants`: insert; proposed value `false`.
- `uses_generate_network`: insert; proposed value `true`.
- `default_sim_command`: insert; proposed value `generate_network`.

### 4. `Published/RulebasedRantransportdraft` / `Rule_based_Ran_transport_draft.bngl`

- BNGL: `Published/RulebasedRantransportdraft/Rule_based_Ran_transport_draft.bngl`
- YAML: `Published/RulebasedRantransportdraft/metadata.yaml`
- Un-commented action commands detected: `generate_network`
- Compartments block entries detected: `5`
- Anchor entries detected: `1`
- Multiple-identical-site evidence: none detected in molecule-type declarations.

| Field | Detected from BNGL | Current YAML value | Proposed action | Proposed value |
|---|---|---|---|---|
| `uses_cbngl_compartments` | `true` | `missing` | insert | `true` |
| `uses_vcell_compartments` | `true` | `missing` | insert | `true` |
| `uses_energy` | `false` | `false` | keep | `false` |
| `uses_functions` | `false` | `true` | change from True | `false` |
| `uses_moveconnected` | `false` | `missing` | insert | `false` |
| `uses_trash_molecules` | `false` | `missing` | insert | `false` |
| `uses_anchors` | `true` | `missing` | insert | `true` |
| `uses_multiple_identical_sites` | `false` | `missing` | insert | `false` |
| `uses_deletes_molecules` | `false` | `missing` | insert | `false` |
| `uses_exclude_include_reactants` | `false` | `missing` | insert | `false` |
| `uses_generate_network` | `true` | `missing` | insert | `true` |
| `default_sim_command` | `generate_network` | `missing` | insert | `generate_network` |

Proposed YAML updates:
- `uses_cbngl_compartments`: insert; proposed value `true`.
- `uses_vcell_compartments`: insert; proposed value `true`.
- `uses_functions`: change from True; proposed value `false`.
- `uses_moveconnected`: insert; proposed value `false`.
- `uses_trash_molecules`: insert; proposed value `false`.
- `uses_anchors`: insert; proposed value `true`.
- `uses_multiple_identical_sites`: insert; proposed value `false`.
- `uses_deletes_molecules`: insert; proposed value `false`.
- `uses_exclude_include_reactants`: insert; proposed value `false`.
- `uses_generate_network`: insert; proposed value `true`.
- `default_sim_command`: insert; proposed value `generate_network`.

### 5. `Published/Rulebasedegfrcompart` / `Rule_based_egfr_compart.bngl`

- BNGL: `Published/Rulebasedegfrcompart/Rule_based_egfr_compart.bngl`
- YAML: `Published/Rulebasedegfrcompart/metadata.yaml`
- Un-commented action commands detected: `generate_network`
- Compartments block entries detected: `3`
- Anchor entries detected: `2`
- Multiple-identical-site evidence: none detected in molecule-type declarations.

| Field | Detected from BNGL | Current YAML value | Proposed action | Proposed value |
|---|---|---|---|---|
| `uses_cbngl_compartments` | `true` | `missing` | insert | `true` |
| `uses_vcell_compartments` | `true` | `missing` | insert | `true` |
| `uses_energy` | `false` | `false` | keep | `false` |
| `uses_functions` | `false` | `true` | change from True | `false` |
| `uses_moveconnected` | `false` | `missing` | insert | `false` |
| `uses_trash_molecules` | `false` | `missing` | insert | `false` |
| `uses_anchors` | `true` | `missing` | insert | `true` |
| `uses_multiple_identical_sites` | `false` | `missing` | insert | `false` |
| `uses_deletes_molecules` | `false` | `missing` | insert | `false` |
| `uses_exclude_include_reactants` | `false` | `missing` | insert | `false` |
| `uses_generate_network` | `true` | `missing` | insert | `true` |
| `default_sim_command` | `generate_network` | `missing` | insert | `generate_network` |

Proposed YAML updates:
- `uses_cbngl_compartments`: insert; proposed value `true`.
- `uses_vcell_compartments`: insert; proposed value `true`.
- `uses_functions`: change from True; proposed value `false`.
- `uses_moveconnected`: insert; proposed value `false`.
- `uses_trash_molecules`: insert; proposed value `false`.
- `uses_anchors`: insert; proposed value `true`.
- `uses_multiple_identical_sites`: insert; proposed value `false`.
- `uses_deletes_molecules`: insert; proposed value `false`.
- `uses_exclude_include_reactants`: insert; proposed value `false`.
- `uses_generate_network`: insert; proposed value `true`.
- `default_sim_command`: insert; proposed value `generate_network`.

### 6. `Published/Rulebasedegfrtutorial` / `Rule_based_egfr_tutorial.bngl`

- BNGL: `Published/Rulebasedegfrtutorial/Rule_based_egfr_tutorial.bngl`
- YAML: `Published/Rulebasedegfrtutorial/metadata.yaml`
- Un-commented action commands detected: `generate_network`
- Compartments block entries detected: `1`
- Anchor entries detected: `0`
- Multiple-identical-site evidence: none detected in molecule-type declarations.

| Field | Detected from BNGL | Current YAML value | Proposed action | Proposed value |
|---|---|---|---|---|
| `uses_cbngl_compartments` | `true` | `missing` | insert | `true` |
| `uses_vcell_compartments` | `false` | `missing` | insert | `false` |
| `uses_energy` | `false` | `false` | keep | `false` |
| `uses_functions` | `false` | `true` | change from True | `false` |
| `uses_moveconnected` | `false` | `missing` | insert | `false` |
| `uses_trash_molecules` | `false` | `missing` | insert | `false` |
| `uses_anchors` | `false` | `missing` | insert | `false` |
| `uses_multiple_identical_sites` | `false` | `missing` | insert | `false` |
| `uses_deletes_molecules` | `false` | `missing` | insert | `false` |
| `uses_exclude_include_reactants` | `false` | `missing` | insert | `false` |
| `uses_generate_network` | `true` | `missing` | insert | `true` |
| `default_sim_command` | `generate_network` | `missing` | insert | `generate_network` |

Proposed YAML updates:
- `uses_cbngl_compartments`: insert; proposed value `true`.
- `uses_vcell_compartments`: insert; proposed value `false`.
- `uses_functions`: change from True; proposed value `false`.
- `uses_moveconnected`: insert; proposed value `false`.
- `uses_trash_molecules`: insert; proposed value `false`.
- `uses_anchors`: insert; proposed value `false`.
- `uses_multiple_identical_sites`: insert; proposed value `false`.
- `uses_deletes_molecules`: insert; proposed value `false`.
- `uses_exclude_include_reactants`: insert; proposed value `false`.
- `uses_generate_network`: insert; proposed value `true`.
- `default_sim_command`: insert; proposed value `generate_network`.

### 7. `Published/Jung2017` / `Jung_2017.bngl`

- BNGL: `Published/Jung2017/Jung_2017.bngl`
- YAML: `Published/Jung2017/metadata.yaml`
- Un-commented action commands detected: `generate_network`
- Compartments block entries detected: `3`
- Anchor entries detected: `0`
- Multiple-identical-site evidence: none detected in molecule-type declarations.

| Field | Detected from BNGL | Current YAML value | Proposed action | Proposed value |
|---|---|---|---|---|
| `uses_cbngl_compartments` | `true` | `missing` | insert | `true` |
| `uses_vcell_compartments` | `false` | `missing` | insert | `false` |
| `uses_energy` | `false` | `false` | keep | `false` |
| `uses_functions` | `true` | `true` | keep | `true` |
| `uses_moveconnected` | `false` | `missing` | insert | `false` |
| `uses_trash_molecules` | `false` | `missing` | insert | `false` |
| `uses_anchors` | `false` | `missing` | insert | `false` |
| `uses_multiple_identical_sites` | `false` | `missing` | insert | `false` |
| `uses_deletes_molecules` | `false` | `missing` | insert | `false` |
| `uses_exclude_include_reactants` | `false` | `missing` | insert | `false` |
| `uses_generate_network` | `true` | `missing` | insert | `true` |
| `default_sim_command` | `generate_network` | `missing` | insert | `generate_network` |

Proposed YAML updates:
- `uses_cbngl_compartments`: insert; proposed value `true`.
- `uses_vcell_compartments`: insert; proposed value `false`.
- `uses_moveconnected`: insert; proposed value `false`.
- `uses_trash_molecules`: insert; proposed value `false`.
- `uses_anchors`: insert; proposed value `false`.
- `uses_multiple_identical_sites`: insert; proposed value `false`.
- `uses_deletes_molecules`: insert; proposed value `false`.
- `uses_exclude_include_reactants`: insert; proposed value `false`.
- `uses_generate_network`: insert; proposed value `true`.
- `default_sim_command`: insert; proposed value `generate_network`.

### 8. `Published/Lang2024` / `Lang_2024.bngl`

- BNGL: `Published/Lang2024/Lang_2024.bngl`
- YAML: `Published/Lang2024/metadata.yaml`
- Un-commented action commands detected: `simulate`, `generate_network`
- Compartments block entries detected: `1`
- Anchor entries detected: `0`
- Multiple-identical-site evidence: none detected in molecule-type declarations.

| Field | Detected from BNGL | Current YAML value | Proposed action | Proposed value |
|---|---|---|---|---|
| `uses_cbngl_compartments` | `true` | `missing` | insert | `true` |
| `uses_vcell_compartments` | `false` | `missing` | insert | `false` |
| `uses_energy` | `false` | `false` | keep | `false` |
| `uses_functions` | `false` | `false` | keep | `false` |
| `uses_moveconnected` | `false` | `missing` | insert | `false` |
| `uses_trash_molecules` | `false` | `missing` | insert | `false` |
| `uses_anchors` | `false` | `missing` | insert | `false` |
| `uses_multiple_identical_sites` | `false` | `missing` | insert | `false` |
| `uses_deletes_molecules` | `true` | `missing` | insert | `true` |
| `uses_exclude_include_reactants` | `true` | `missing` | insert | `true` |
| `uses_generate_network` | `true` | `missing` | insert | `true` |
| `default_sim_command` | `simulate` | `missing` | insert | `simulate` |

Proposed YAML updates:
- `uses_cbngl_compartments`: insert; proposed value `true`.
- `uses_vcell_compartments`: insert; proposed value `false`.
- `uses_moveconnected`: insert; proposed value `false`.
- `uses_trash_molecules`: insert; proposed value `false`.
- `uses_anchors`: insert; proposed value `false`.
- `uses_multiple_identical_sites`: insert; proposed value `false`.
- `uses_deletes_molecules`: insert; proposed value `true`.
- `uses_exclude_include_reactants`: insert; proposed value `true`.
- `uses_generate_network`: insert; proposed value `true`.
- `default_sim_command`: insert; proposed value `simulate`.

### 9. `Published/Nosbisch2022` / `Nosbisch_2022.bngl`

- BNGL: `Published/Nosbisch2022/Nosbisch_2022.bngl`
- YAML: `Published/Nosbisch2022/metadata.yaml`
- Un-commented action commands detected: `generate_network`
- Compartments block entries detected: `1`
- Anchor entries detected: `0`
- Multiple-identical-site evidence: none detected in molecule-type declarations.

| Field | Detected from BNGL | Current YAML value | Proposed action | Proposed value |
|---|---|---|---|---|
| `uses_cbngl_compartments` | `true` | `missing` | insert | `true` |
| `uses_vcell_compartments` | `false` | `missing` | insert | `false` |
| `uses_energy` | `false` | `false` | keep | `false` |
| `uses_functions` | `false` | `true` | change from True | `false` |
| `uses_moveconnected` | `false` | `missing` | insert | `false` |
| `uses_trash_molecules` | `false` | `missing` | insert | `false` |
| `uses_anchors` | `false` | `missing` | insert | `false` |
| `uses_multiple_identical_sites` | `false` | `missing` | insert | `false` |
| `uses_deletes_molecules` | `false` | `missing` | insert | `false` |
| `uses_exclude_include_reactants` | `false` | `missing` | insert | `false` |
| `uses_generate_network` | `true` | `missing` | insert | `true` |
| `default_sim_command` | `generate_network` | `missing` | insert | `generate_network` |

Proposed YAML updates:
- `uses_cbngl_compartments`: insert; proposed value `true`.
- `uses_vcell_compartments`: insert; proposed value `false`.
- `uses_functions`: change from True; proposed value `false`.
- `uses_moveconnected`: insert; proposed value `false`.
- `uses_trash_molecules`: insert; proposed value `false`.
- `uses_anchors`: insert; proposed value `false`.
- `uses_multiple_identical_sites`: insert; proposed value `false`.
- `uses_deletes_molecules`: insert; proposed value `false`.
- `uses_exclude_include_reactants`: insert; proposed value `false`.
- `uses_generate_network`: insert; proposed value `true`.
- `default_sim_command`: insert; proposed value `generate_network`.

### 10. `Published/Barua2007` / `Barua_2007.bngl`

- BNGL: `Published/Barua2007/Barua_2007.bngl`
- YAML: `Published/Barua2007/metadata.yaml`
- Un-commented action commands detected: `simulate_ode`, `generate_network`
- Compartments block entries detected: `0`
- Anchor entries detected: `0`
- Multiple-identical-site evidence: none detected in molecule-type declarations.

| Field | Detected from BNGL | Current YAML value | Proposed action | Proposed value |
|---|---|---|---|---|
| `uses_cbngl_compartments` | `false` | `missing` | insert | `false` |
| `uses_vcell_compartments` | `false` | `missing` | insert | `false` |
| `uses_energy` | `false` | `false` | keep | `false` |
| `uses_functions` | `false` | `false` | keep | `false` |
| `uses_moveconnected` | `false` | `missing` | insert | `false` |
| `uses_trash_molecules` | `false` | `missing` | insert | `false` |
| `uses_anchors` | `false` | `missing` | insert | `false` |
| `uses_multiple_identical_sites` | `false` | `missing` | insert | `false` |
| `uses_deletes_molecules` | `false` | `missing` | insert | `false` |
| `uses_exclude_include_reactants` | `true` | `missing` | insert | `true` |
| `uses_generate_network` | `true` | `missing` | insert | `true` |
| `default_sim_command` | `simulate_ode` | `missing` | insert | `simulate_ode` |

Proposed YAML updates:
- `uses_cbngl_compartments`: insert; proposed value `false`.
- `uses_vcell_compartments`: insert; proposed value `false`.
- `uses_moveconnected`: insert; proposed value `false`.
- `uses_trash_molecules`: insert; proposed value `false`.
- `uses_anchors`: insert; proposed value `false`.
- `uses_multiple_identical_sites`: insert; proposed value `false`.
- `uses_deletes_molecules`: insert; proposed value `false`.
- `uses_exclude_include_reactants`: insert; proposed value `true`.
- `uses_generate_network`: insert; proposed value `true`.
- `default_sim_command`: insert; proposed value `simulate_ode`.

### 11. `Published/An2009` / `An_2009.bngl`

- BNGL: `Published/An2009/An_2009.bngl`
- YAML: `Published/An2009/metadata.yaml`
- Un-commented action commands detected: `simulate_ode`, `generate_network`
- Compartments block entries detected: `0`
- Anchor entries detected: `0`
- Multiple-identical-site evidence:
  - DNA: repeated c in `DNA(A20,TNF,iNOS,IL10,IkB,c,c)`

| Field | Detected from BNGL | Current YAML value | Proposed action | Proposed value |
|---|---|---|---|---|
| `uses_cbngl_compartments` | `false` | `missing` | insert | `false` |
| `uses_vcell_compartments` | `false` | `missing` | insert | `false` |
| `uses_energy` | `false` | `false` | keep | `false` |
| `uses_functions` | `false` | `false` | keep | `false` |
| `uses_moveconnected` | `false` | `missing` | insert | `false` |
| `uses_trash_molecules` | `true` | `missing` | insert | `true` |
| `uses_anchors` | `false` | `missing` | insert | `false` |
| `uses_multiple_identical_sites` | `true` | `missing` | insert | `true` |
| `uses_deletes_molecules` | `false` | `missing` | insert | `false` |
| `uses_exclude_include_reactants` | `false` | `missing` | insert | `false` |
| `uses_generate_network` | `true` | `missing` | insert | `true` |
| `default_sim_command` | `simulate_ode` | `missing` | insert | `simulate_ode` |

Proposed YAML updates:
- `uses_cbngl_compartments`: insert; proposed value `false`.
- `uses_vcell_compartments`: insert; proposed value `false`.
- `uses_moveconnected`: insert; proposed value `false`.
- `uses_trash_molecules`: insert; proposed value `true`.
- `uses_anchors`: insert; proposed value `false`.
- `uses_multiple_identical_sites`: insert; proposed value `true`.
- `uses_deletes_molecules`: insert; proposed value `false`.
- `uses_exclude_include_reactants`: insert; proposed value `false`.
- `uses_generate_network`: insert; proposed value `true`.
- `default_sim_command`: insert; proposed value `simulate_ode`.

### 12. `Published/Ligon2014` / `Ligon_2014.bngl`

- BNGL: `Published/Ligon2014/Ligon_2014.bngl`
- YAML: `Published/Ligon2014/metadata.yaml`
- Un-commented action commands detected: `simulate_nf`
- Compartments block entries detected: `0`
- Anchor entries detected: `0`
- Multiple-identical-site evidence: none detected in molecule-type declarations.

| Field | Detected from BNGL | Current YAML value | Proposed action | Proposed value |
|---|---|---|---|---|
| `uses_cbngl_compartments` | `false` | `missing` | insert | `false` |
| `uses_vcell_compartments` | `false` | `missing` | insert | `false` |
| `uses_energy` | `false` | `false` | keep | `false` |
| `uses_functions` | `true` | `true` | keep | `true` |
| `uses_moveconnected` | `false` | `missing` | insert | `false` |
| `uses_trash_molecules` | `false` | `missing` | insert | `false` |
| `uses_anchors` | `false` | `missing` | insert | `false` |
| `uses_multiple_identical_sites` | `false` | `missing` | insert | `false` |
| `uses_deletes_molecules` | `true` | `missing` | insert | `true` |
| `uses_exclude_include_reactants` | `false` | `missing` | insert | `false` |
| `uses_generate_network` | `false` | `missing` | insert | `false` |
| `default_sim_command` | `simulate_nf` | `missing` | insert | `simulate_nf` |

Proposed YAML updates:
- `uses_cbngl_compartments`: insert; proposed value `false`.
- `uses_vcell_compartments`: insert; proposed value `false`.
- `uses_moveconnected`: insert; proposed value `false`.
- `uses_trash_molecules`: insert; proposed value `false`.
- `uses_anchors`: insert; proposed value `false`.
- `uses_multiple_identical_sites`: insert; proposed value `false`.
- `uses_deletes_molecules`: insert; proposed value `true`.
- `uses_exclude_include_reactants`: insert; proposed value `false`.
- `uses_generate_network`: insert; proposed value `false`.
- `default_sim_command`: insert; proposed value `simulate_nf`.

### 13. `Published/Zhang2023` / `Zhang_2023.bngl`

- BNGL: `Published/Zhang2023/Zhang_2023.bngl`
- YAML: `Published/Zhang2023/metadata.yaml`
- Un-commented action commands detected: `generate_network`
- Compartments block entries detected: `0`
- Anchor entries detected: `0`
- Multiple-identical-site evidence:
  - vegf: repeated r in `vegf(r,r,nrp1bd,c~s~i~i2~r)`
  - CaM: repeated CCaM, NCaM in `CaM(NCaM,NCaM,CCaM,CCaM,CaMtargetbd)`

| Field | Detected from BNGL | Current YAML value | Proposed action | Proposed value |
|---|---|---|---|---|
| `uses_cbngl_compartments` | `false` | `missing` | insert | `false` |
| `uses_vcell_compartments` | `false` | `missing` | insert | `false` |
| `uses_energy` | `false` | `false` | keep | `false` |
| `uses_functions` | `false` | `false` | keep | `false` |
| `uses_moveconnected` | `false` | `missing` | insert | `false` |
| `uses_trash_molecules` | `true` | `missing` | insert | `true` |
| `uses_anchors` | `false` | `missing` | insert | `false` |
| `uses_multiple_identical_sites` | `true` | `missing` | insert | `true` |
| `uses_deletes_molecules` | `false` | `missing` | insert | `false` |
| `uses_exclude_include_reactants` | `false` | `missing` | insert | `false` |
| `uses_generate_network` | `true` | `missing` | insert | `true` |
| `default_sim_command` | `generate_network` | `missing` | insert | `generate_network` |

Proposed YAML updates:
- `uses_cbngl_compartments`: insert; proposed value `false`.
- `uses_vcell_compartments`: insert; proposed value `false`.
- `uses_moveconnected`: insert; proposed value `false`.
- `uses_trash_molecules`: insert; proposed value `true`.
- `uses_anchors`: insert; proposed value `false`.
- `uses_multiple_identical_sites`: insert; proposed value `true`.
- `uses_deletes_molecules`: insert; proposed value `false`.
- `uses_exclude_include_reactants`: insert; proposed value `false`.
- `uses_generate_network`: insert; proposed value `true`.
- `default_sim_command`: insert; proposed value `generate_network`.

### 14. `Published/ChylekFceRI2014` / `ChylekFceRI_2014.bngl`

- BNGL: `Published/ChylekFceRI2014/ChylekFceRI_2014.bngl`
- YAML: `Published/ChylekFceRI2014/metadata.yaml`
- Un-commented action commands detected: `writeXML`
- Compartments block entries detected: `0`
- Anchor entries detected: `0`
- Multiple-identical-site evidence:
  - Lig: repeated hap in `Lig(hap~b~e,hap~b~e)`
  - Rec: repeated fab in `Rec(fab,fab,b_Y218~0~P,b_Y224~0~P,g_Y65_Y76~0~P)`

| Field | Detected from BNGL | Current YAML value | Proposed action | Proposed value |
|---|---|---|---|---|
| `uses_cbngl_compartments` | `false` | `missing` | insert | `false` |
| `uses_vcell_compartments` | `false` | `missing` | insert | `false` |
| `uses_energy` | `false` | `false` | keep | `false` |
| `uses_functions` | `false` | `false` | keep | `false` |
| `uses_moveconnected` | `false` | `missing` | insert | `false` |
| `uses_trash_molecules` | `false` | `missing` | insert | `false` |
| `uses_anchors` | `false` | `missing` | insert | `false` |
| `uses_multiple_identical_sites` | `true` | `missing` | insert | `true` |
| `uses_deletes_molecules` | `true` | `missing` | insert | `true` |
| `uses_exclude_include_reactants` | `false` | `missing` | insert | `false` |
| `uses_generate_network` | `false` | `missing` | insert | `false` |
| `default_sim_command` | `null` | `missing` | insert | `null` |

Proposed YAML updates:
- `uses_cbngl_compartments`: insert; proposed value `false`.
- `uses_vcell_compartments`: insert; proposed value `false`.
- `uses_moveconnected`: insert; proposed value `false`.
- `uses_trash_molecules`: insert; proposed value `false`.
- `uses_anchors`: insert; proposed value `false`.
- `uses_multiple_identical_sites`: insert; proposed value `true`.
- `uses_deletes_molecules`: insert; proposed value `true`.
- `uses_exclude_include_reactants`: insert; proposed value `false`.
- `uses_generate_network`: insert; proposed value `false`.
- `default_sim_command`: insert; proposed value `null`.

### 15. `Published/Dolan2015` / `Dolan_2015.bngl`

- BNGL: `Published/Dolan2015/Dolan_2015.bngl`
- YAML: `Published/Dolan2015/metadata.yaml`
- Un-commented action commands detected: `simulate_nf`
- Compartments block entries detected: `0`
- Anchor entries detected: `0`
- Multiple-identical-site evidence: none detected in molecule-type declarations.

| Field | Detected from BNGL | Current YAML value | Proposed action | Proposed value |
|---|---|---|---|---|
| `uses_cbngl_compartments` | `false` | `missing` | insert | `false` |
| `uses_vcell_compartments` | `false` | `missing` | insert | `false` |
| `uses_energy` | `false` | `false` | keep | `false` |
| `uses_functions` | `true` | `true` | keep | `true` |
| `uses_moveconnected` | `false` | `missing` | insert | `false` |
| `uses_trash_molecules` | `false` | `missing` | insert | `false` |
| `uses_anchors` | `false` | `missing` | insert | `false` |
| `uses_multiple_identical_sites` | `false` | `missing` | insert | `false` |
| `uses_deletes_molecules` | `true` | `missing` | insert | `true` |
| `uses_exclude_include_reactants` | `false` | `missing` | insert | `false` |
| `uses_generate_network` | `false` | `missing` | insert | `false` |
| `default_sim_command` | `simulate_nf` | `missing` | insert | `simulate_nf` |

Proposed YAML updates:
- `uses_cbngl_compartments`: insert; proposed value `false`.
- `uses_vcell_compartments`: insert; proposed value `false`.
- `uses_moveconnected`: insert; proposed value `false`.
- `uses_trash_molecules`: insert; proposed value `false`.
- `uses_anchors`: insert; proposed value `false`.
- `uses_multiple_identical_sites`: insert; proposed value `false`.
- `uses_deletes_molecules`: insert; proposed value `true`.
- `uses_exclude_include_reactants`: insert; proposed value `false`.
- `uses_generate_network`: insert; proposed value `false`.
- `default_sim_command`: insert; proposed value `simulate_nf`.

### 16. `Published/Hlavacek2001` / `kinetic_proofreading_hlavacek2001.bngl`

- BNGL: `Published/Hlavacek2001/kinetic_proofreading_hlavacek2001.bngl`
- YAML: `Published/Hlavacek2001/metadata.yaml`
- Un-commented action commands detected: `simulate`, `generate_network`
- Compartments block entries detected: `0`
- Anchor entries detected: `0`
- Multiple-identical-site evidence:
  - L: repeated r in `L(r,r,mod~0~1~2~3~4~5)`

| Field | Detected from BNGL | Current YAML value | Proposed action | Proposed value |
|---|---|---|---|---|
| `uses_cbngl_compartments` | `false` | `missing` | insert | `false` |
| `uses_vcell_compartments` | `false` | `missing` | insert | `false` |
| `uses_energy` | `false` | `false` | keep | `false` |
| `uses_functions` | `true` | `true` | keep | `true` |
| `uses_moveconnected` | `false` | `missing` | insert | `false` |
| `uses_trash_molecules` | `false` | `missing` | insert | `false` |
| `uses_anchors` | `false` | `missing` | insert | `false` |
| `uses_multiple_identical_sites` | `true` | `missing` | insert | `true` |
| `uses_deletes_molecules` | `false` | `missing` | insert | `false` |
| `uses_exclude_include_reactants` | `false` | `missing` | insert | `false` |
| `uses_generate_network` | `true` | `missing` | insert | `true` |
| `default_sim_command` | `simulate` | `missing` | insert | `simulate` |

Proposed YAML updates:
- `uses_cbngl_compartments`: insert; proposed value `false`.
- `uses_vcell_compartments`: insert; proposed value `false`.
- `uses_moveconnected`: insert; proposed value `false`.
- `uses_trash_molecules`: insert; proposed value `false`.
- `uses_anchors`: insert; proposed value `false`.
- `uses_multiple_identical_sites`: insert; proposed value `true`.
- `uses_deletes_molecules`: insert; proposed value `false`.
- `uses_exclude_include_reactants`: insert; proposed value `false`.
- `uses_generate_network`: insert; proposed value `true`.
- `default_sim_command`: insert; proposed value `simulate`.

### 17. `Published/Dembo1978` / `blbr_dembo1978.bngl`

- BNGL: `Published/Dembo1978/blbr_dembo1978.bngl`
- YAML: `Published/Dembo1978/metadata.yaml`
- Un-commented action commands detected: `simulate`
- Compartments block entries detected: `0`
- Anchor entries detected: `0`
- Multiple-identical-site evidence:
  - L: repeated r in `L(r,r)`
  - R: repeated l in `R(l,l)`

| Field | Detected from BNGL | Current YAML value | Proposed action | Proposed value |
|---|---|---|---|---|
| `uses_cbngl_compartments` | `false` | `missing` | insert | `false` |
| `uses_vcell_compartments` | `false` | `missing` | insert | `false` |
| `uses_energy` | `false` | `false` | keep | `false` |
| `uses_functions` | `false` | `false` | keep | `false` |
| `uses_moveconnected` | `false` | `missing` | insert | `false` |
| `uses_trash_molecules` | `false` | `missing` | insert | `false` |
| `uses_anchors` | `false` | `missing` | insert | `false` |
| `uses_multiple_identical_sites` | `true` | `missing` | insert | `true` |
| `uses_deletes_molecules` | `false` | `missing` | insert | `false` |
| `uses_exclude_include_reactants` | `false` | `missing` | insert | `false` |
| `uses_generate_network` | `false` | `missing` | insert | `false` |
| `default_sim_command` | `simulate` | `missing` | insert | `simulate` |

Proposed YAML updates:
- `uses_cbngl_compartments`: insert; proposed value `false`.
- `uses_vcell_compartments`: insert; proposed value `false`.
- `uses_moveconnected`: insert; proposed value `false`.
- `uses_trash_molecules`: insert; proposed value `false`.
- `uses_anchors`: insert; proposed value `false`.
- `uses_multiple_identical_sites`: insert; proposed value `true`.
- `uses_deletes_molecules`: insert; proposed value `false`.
- `uses_exclude_include_reactants`: insert; proposed value `false`.
- `uses_generate_network`: insert; proposed value `false`.
- `default_sim_command`: insert; proposed value `simulate`.

### 18. `Published/Dreisigmeyer2008` / `lac_operon_dreisigmeyer2008.bngl`

- BNGL: `Published/Dreisigmeyer2008/lac_operon_dreisigmeyer2008.bngl`
- YAML: `Published/Dreisigmeyer2008/metadata.yaml`
- Un-commented action commands detected: `simulate`, `generate_network`
- Compartments block entries detected: `0`
- Anchor entries detected: `0`
- Multiple-identical-site evidence: none detected in molecule-type declarations.

| Field | Detected from BNGL | Current YAML value | Proposed action | Proposed value |
|---|---|---|---|---|
| `uses_cbngl_compartments` | `false` | `missing` | insert | `false` |
| `uses_vcell_compartments` | `false` | `missing` | insert | `false` |
| `uses_energy` | `false` | `false` | keep | `false` |
| `uses_functions` | `true` | `true` | keep | `true` |
| `uses_moveconnected` | `false` | `missing` | insert | `false` |
| `uses_trash_molecules` | `false` | `missing` | insert | `false` |
| `uses_anchors` | `false` | `missing` | insert | `false` |
| `uses_multiple_identical_sites` | `false` | `missing` | insert | `false` |
| `uses_deletes_molecules` | `false` | `missing` | insert | `false` |
| `uses_exclude_include_reactants` | `false` | `missing` | insert | `false` |
| `uses_generate_network` | `true` | `missing` | insert | `true` |
| `default_sim_command` | `simulate` | `missing` | insert | `simulate` |

Proposed YAML updates:
- `uses_cbngl_compartments`: insert; proposed value `false`.
- `uses_vcell_compartments`: insert; proposed value `false`.
- `uses_moveconnected`: insert; proposed value `false`.
- `uses_trash_molecules`: insert; proposed value `false`.
- `uses_anchors`: insert; proposed value `false`.
- `uses_multiple_identical_sites`: insert; proposed value `false`.
- `uses_deletes_molecules`: insert; proposed value `false`.
- `uses_exclude_include_reactants`: insert; proposed value `false`.
- `uses_generate_network`: insert; proposed value `true`.
- `default_sim_command`: insert; proposed value `simulate`.

### 19. `Published/Gardner2000` / `genetic_switch_gardner2000.bngl`

- BNGL: `Published/Gardner2000/genetic_switch_gardner2000.bngl`
- YAML: `Published/Gardner2000/metadata.yaml`
- Un-commented action commands detected: `simulate`, `generate_network`
- Compartments block entries detected: `0`
- Anchor entries detected: `0`
- Multiple-identical-site evidence: none detected in molecule-type declarations.

| Field | Detected from BNGL | Current YAML value | Proposed action | Proposed value |
|---|---|---|---|---|
| `uses_cbngl_compartments` | `false` | `missing` | insert | `false` |
| `uses_vcell_compartments` | `false` | `missing` | insert | `false` |
| `uses_energy` | `false` | `false` | keep | `false` |
| `uses_functions` | `true` | `true` | keep | `true` |
| `uses_moveconnected` | `false` | `missing` | insert | `false` |
| `uses_trash_molecules` | `false` | `missing` | insert | `false` |
| `uses_anchors` | `false` | `missing` | insert | `false` |
| `uses_multiple_identical_sites` | `false` | `missing` | insert | `false` |
| `uses_deletes_molecules` | `false` | `missing` | insert | `false` |
| `uses_exclude_include_reactants` | `false` | `missing` | insert | `false` |
| `uses_generate_network` | `true` | `missing` | insert | `true` |
| `default_sim_command` | `simulate` | `missing` | insert | `simulate` |

Proposed YAML updates:
- `uses_cbngl_compartments`: insert; proposed value `false`.
- `uses_vcell_compartments`: insert; proposed value `false`.
- `uses_moveconnected`: insert; proposed value `false`.
- `uses_trash_molecules`: insert; proposed value `false`.
- `uses_anchors`: insert; proposed value `false`.
- `uses_multiple_identical_sites`: insert; proposed value `false`.
- `uses_deletes_molecules`: insert; proposed value `false`.
- `uses_exclude_include_reactants`: insert; proposed value `false`.
- `uses_generate_network`: insert; proposed value `true`.
- `default_sim_command`: insert; proposed value `simulate`.

### 20. `Published/Barua2009` / `Barua_2009.bngl`

- BNGL: `Published/Barua2009/Barua_2009.bngl`
- YAML: `Published/Barua2009/metadata.yaml`
- Un-commented action commands detected: `simulate_ode`, `generate_network`
- Compartments block entries detected: `0`
- Anchor entries detected: `0`
- Multiple-identical-site evidence: none detected in molecule-type declarations.

| Field | Detected from BNGL | Current YAML value | Proposed action | Proposed value |
|---|---|---|---|---|
| `uses_cbngl_compartments` | `false` | `missing` | insert | `false` |
| `uses_vcell_compartments` | `false` | `missing` | insert | `false` |
| `uses_energy` | `false` | `false` | keep | `false` |
| `uses_functions` | `false` | `false` | keep | `false` |
| `uses_moveconnected` | `false` | `missing` | insert | `false` |
| `uses_trash_molecules` | `false` | `missing` | insert | `false` |
| `uses_anchors` | `false` | `missing` | insert | `false` |
| `uses_multiple_identical_sites` | `false` | `missing` | insert | `false` |
| `uses_deletes_molecules` | `false` | `missing` | insert | `false` |
| `uses_exclude_include_reactants` | `false` | `missing` | insert | `false` |
| `uses_generate_network` | `true` | `missing` | insert | `true` |
| `default_sim_command` | `simulate_ode` | `missing` | insert | `simulate_ode` |

Proposed YAML updates:
- `uses_cbngl_compartments`: insert; proposed value `false`.
- `uses_vcell_compartments`: insert; proposed value `false`.
- `uses_moveconnected`: insert; proposed value `false`.
- `uses_trash_molecules`: insert; proposed value `false`.
- `uses_anchors`: insert; proposed value `false`.
- `uses_multiple_identical_sites`: insert; proposed value `false`.
- `uses_deletes_molecules`: insert; proposed value `false`.
- `uses_exclude_include_reactants`: insert; proposed value `false`.
- `uses_generate_network`: insert; proposed value `true`.
- `default_sim_command`: insert; proposed value `simulate_ode`.
