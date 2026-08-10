# Published YAML Feature Audit 3

## Introduction

This audit checks the same 20 same-directory `Published/` BNGL/YAML pairs used in the earlier reports, using the finalized `metadata_auditing` skill. Each selected BNGL file was compared against its same-directory target YAML. Audited YAML copies were created inside the corresponding model folders using `<original-yaml-stem>_audited.yaml`; original YAML files were not overwritten.

## Detection definitions

- VCell compartments are detected only from active `@Compartment:Molecule(...)` syntax.
- CBNGL compartments are detected only from active `Molecule(...)@Compartment` syntax.
- A `begin compartments` block is reported in diagnostics but does not directly set either compartment field.
- Empty blocks have active entries `0` and do not make block-based fields true.
- `uses_functions`, `uses_anchors`, and `uses_energy` require at least one uncommented, nonempty active entry inside the corresponding block.
- `default_sim_command` is the first active command among `simulate_ode`, `simulate_ssa`, `simulate_nf`, and `simulate`; if none are active, it is `null`.

## Batch summary

| Field | Detected true | Detected false | Detected null | Current YAML missing | Proposed insertions | Proposed changes | Manual review |
| --- | ---: | ---: | ---: | ---: | ---: | ---: | ---: |
| `uses_cbngl_compartments` | 0 | 20 | 0 | 20 | 20 | 0 | 0 |
| `uses_vcell_compartments` | 9 | 11 | 0 | 20 | 20 | 0 | 0 |
| `uses_energy` | 0 | 20 | 0 | 0 | 0 | 0 | 0 |
| `uses_functions` | 6 | 14 | 0 | 0 | 0 | 7 | 0 |
| `uses_moveconnected` | 0 | 20 | 0 | 20 | 20 | 0 | 0 |
| `uses_trash_molecules` | 2 | 18 | 0 | 20 | 20 | 0 | 0 |
| `uses_anchors` | 5 | 15 | 0 | 20 | 20 | 0 | 0 |
| `uses_multiple_identical_sites` | 5 | 15 | 0 | 20 | 20 | 0 | 0 |
| `uses_deletes_molecules` | 4 | 16 | 0 | 20 | 20 | 0 | 0 |
| `uses_exclude_include_reactants` | 2 | 18 | 0 | 20 | 20 | 0 | 0 |
| `uses_generate_network` | 14 | 6 | 0 | 20 | 20 | 0 | 0 |
| `default_sim_command` | 12 | 0 | 8 | 20 | 20 | 0 | 0 |

## Audited pairs

| # | BNGL path | YAML audited | Audited YAML output | Proposed updates | Manual review? |
| ---: | --- | --- | --- | ---: | --- |
| 1 | `Published/Blinovegfr/Blinov_egfr.bngl` | `Published/Blinovegfr/metadata.yaml` | `Published/Blinovegfr/metadata_audited.yaml` | 11 | no |
| 2 | `Published/Blinovran/Blinov_ran.bngl` | `Published/Blinovran/metadata.yaml` | `Published/Blinovran/metadata_audited.yaml` | 11 | no |
| 3 | `Published/RulebasedRantransport/Rule_based_Ran_transport.bngl` | `Published/RulebasedRantransport/metadata.yaml` | `Published/RulebasedRantransport/metadata_audited.yaml` | 11 | no |
| 4 | `Published/RulebasedRantransportdraft/Rule_based_Ran_transport_draft.bngl` | `Published/RulebasedRantransportdraft/metadata.yaml` | `Published/RulebasedRantransportdraft/metadata_audited.yaml` | 11 | no |
| 5 | `Published/Rulebasedegfrcompart/Rule_based_egfr_compart.bngl` | `Published/Rulebasedegfrcompart/metadata.yaml` | `Published/Rulebasedegfrcompart/metadata_audited.yaml` | 11 | no |
| 6 | `Published/Rulebasedegfrtutorial/Rule_based_egfr_tutorial.bngl` | `Published/Rulebasedegfrtutorial/metadata.yaml` | `Published/Rulebasedegfrtutorial/metadata_audited.yaml` | 11 | no |
| 7 | `Published/Jung2017/Jung_2017.bngl` | `Published/Jung2017/metadata.yaml` | `Published/Jung2017/metadata_audited.yaml` | 10 | no |
| 8 | `Published/Lang2024/Lang_2024.bngl` | `Published/Lang2024/metadata.yaml` | `Published/Lang2024/metadata_audited.yaml` | 10 | no |
| 9 | `Published/Nosbisch2022/Nosbisch_2022.bngl` | `Published/Nosbisch2022/metadata.yaml` | `Published/Nosbisch2022/metadata_audited.yaml` | 11 | no |
| 10 | `Published/Barua2007/Barua_2007.bngl` | `Published/Barua2007/metadata.yaml` | `Published/Barua2007/metadata_audited.yaml` | 10 | no |
| 11 | `Published/An2009/An_2009.bngl` | `Published/An2009/metadata.yaml` | `Published/An2009/metadata_audited.yaml` | 10 | no |
| 12 | `Published/Ligon2014/Ligon_2014.bngl` | `Published/Ligon2014/metadata.yaml` | `Published/Ligon2014/metadata_audited.yaml` | 10 | no |
| 13 | `Published/Zhang2023/Zhang_2023.bngl` | `Published/Zhang2023/metadata.yaml` | `Published/Zhang2023/metadata_audited.yaml` | 10 | no |
| 14 | `Published/ChylekFceRI2014/ChylekFceRI_2014.bngl` | `Published/ChylekFceRI2014/metadata.yaml` | `Published/ChylekFceRI2014/metadata_audited.yaml` | 10 | no |
| 15 | `Published/Dolan2015/Dolan_2015.bngl` | `Published/Dolan2015/metadata.yaml` | `Published/Dolan2015/metadata_audited.yaml` | 10 | no |
| 16 | `Published/Hlavacek2001/kinetic_proofreading_hlavacek2001.bngl` | `Published/Hlavacek2001/metadata.yaml` | `Published/Hlavacek2001/metadata_audited.yaml` | 10 | no |
| 17 | `Published/Dembo1978/blbr_dembo1978.bngl` | `Published/Dembo1978/metadata.yaml` | `Published/Dembo1978/metadata_audited.yaml` | 10 | no |
| 18 | `Published/Dreisigmeyer2008/lac_operon_dreisigmeyer2008.bngl` | `Published/Dreisigmeyer2008/metadata.yaml` | `Published/Dreisigmeyer2008/metadata_audited.yaml` | 10 | no |
| 19 | `Published/Gardner2000/genetic_switch_gardner2000.bngl` | `Published/Gardner2000/metadata.yaml` | `Published/Gardner2000/metadata_audited.yaml` | 10 | no |
| 20 | `Published/Barua2009/Barua_2009.bngl` | `Published/Barua2009/metadata.yaml` | `Published/Barua2009/metadata_audited.yaml` | 10 | no |

## Per-model findings

### 1. `Blinovegfr`

- Block diagnostics:
  - `compartments`: present `true`; active entries `3`
  - `anchors`: present `true`; active entries `2`
  - `functions`: present `true`; active entries `0`
  - `energy patterns`: present `false`; active entries `0`
- VCell-style compartment example: `@EC:EGF(rb)`
- CBNGL-style compartment example: `none detected`

| Field | Detected from BNGL | Current YAML value | Proposed action | Proposed value | Short rationale |
| --- | --- | --- | --- | --- | --- |
| `uses_cbngl_compartments` | `false` | `missing` | insert | `false` | No CBNGL suffix syntax found. |
| `uses_vcell_compartments` | `true` | `missing` | insert | `true` | VCell syntax example found. |
| `uses_energy` | `false` | `false` | keep | `false` | energy active entries = 0. |
| `uses_functions` | `false` | `true` | change | `false` | functions active entries = 0. |
| `uses_moveconnected` | `false` | `missing` | insert | `false` | No active moveConnected call found. |
| `uses_trash_molecules` | `false` | `missing` | insert | `false` | No active Trash pattern found. |
| `uses_anchors` | `true` | `missing` | insert | `true` | anchors active entries = 2. |
| `uses_multiple_identical_sites` | `false` | `missing` | insert | `false` | No repeated molecule-type site detected. |
| `uses_deletes_molecules` | `false` | `missing` | insert | `false` | No active DeleteMolecules found. |
| `uses_exclude_include_reactants` | `false` | `missing` | insert | `false` | No include/exclude reactants modifier found. |
| `uses_generate_network` | `false` | `missing` | insert | `false` | No active generate_network action found. |
| `default_sim_command` | `simulate_nf` | `missing` | insert | `simulate_nf` | First active simulation command is simulate_nf. |

### 2. `Blinovran`

- Block diagnostics:
  - `compartments`: present `true`; active entries `5`
  - `anchors`: present `true`; active entries `1`
  - `functions`: present `true`; active entries `0`
  - `energy patterns`: present `false`; active entries `0`
- VCell-style compartment example: `@nuc:Ran(cargo!1)`
- CBNGL-style compartment example: `none detected`

| Field | Detected from BNGL | Current YAML value | Proposed action | Proposed value | Short rationale |
| --- | --- | --- | --- | --- | --- |
| `uses_cbngl_compartments` | `false` | `missing` | insert | `false` | No CBNGL suffix syntax found. |
| `uses_vcell_compartments` | `true` | `missing` | insert | `true` | VCell syntax example found. |
| `uses_energy` | `false` | `false` | keep | `false` | energy active entries = 0. |
| `uses_functions` | `false` | `true` | change | `false` | functions active entries = 0. |
| `uses_moveconnected` | `false` | `missing` | insert | `false` | No active moveConnected call found. |
| `uses_trash_molecules` | `false` | `missing` | insert | `false` | No active Trash pattern found. |
| `uses_anchors` | `true` | `missing` | insert | `true` | anchors active entries = 1. |
| `uses_multiple_identical_sites` | `false` | `missing` | insert | `false` | No repeated molecule-type site detected. |
| `uses_deletes_molecules` | `false` | `missing` | insert | `false` | No active DeleteMolecules found. |
| `uses_exclude_include_reactants` | `false` | `missing` | insert | `false` | No include/exclude reactants modifier found. |
| `uses_generate_network` | `false` | `missing` | insert | `false` | No active generate_network action found. |
| `default_sim_command` | `simulate_nf` | `missing` | insert | `simulate_nf` | First active simulation command is simulate_nf. |

### 3. `RulebasedRantransport`

- Block diagnostics:
  - `compartments`: present `true`; active entries `5`
  - `anchors`: present `true`; active entries `1`
  - `functions`: present `true`; active entries `0`
  - `energy patterns`: present `false`; active entries `0`
- VCell-style compartment example: `@nuc:Ran(cargo!1)`
- CBNGL-style compartment example: `none detected`

| Field | Detected from BNGL | Current YAML value | Proposed action | Proposed value | Short rationale |
| --- | --- | --- | --- | --- | --- |
| `uses_cbngl_compartments` | `false` | `missing` | insert | `false` | No CBNGL suffix syntax found. |
| `uses_vcell_compartments` | `true` | `missing` | insert | `true` | VCell syntax example found. |
| `uses_energy` | `false` | `false` | keep | `false` | energy active entries = 0. |
| `uses_functions` | `false` | `true` | change | `false` | functions active entries = 0. |
| `uses_moveconnected` | `false` | `missing` | insert | `false` | No active moveConnected call found. |
| `uses_trash_molecules` | `false` | `missing` | insert | `false` | No active Trash pattern found. |
| `uses_anchors` | `true` | `missing` | insert | `true` | anchors active entries = 1. |
| `uses_multiple_identical_sites` | `false` | `missing` | insert | `false` | No repeated molecule-type site detected. |
| `uses_deletes_molecules` | `false` | `missing` | insert | `false` | No active DeleteMolecules found. |
| `uses_exclude_include_reactants` | `false` | `missing` | insert | `false` | No include/exclude reactants modifier found. |
| `uses_generate_network` | `true` | `missing` | insert | `true` | Active generate_network action found. |
| `default_sim_command` | `null` | `missing` | insert | `null` | No active simulation command found. |

### 4. `RulebasedRantransportdraft`

- Block diagnostics:
  - `compartments`: present `true`; active entries `5`
  - `anchors`: present `true`; active entries `1`
  - `functions`: present `true`; active entries `0`
  - `energy patterns`: present `false`; active entries `0`
- VCell-style compartment example: `@nuc:Ran(cargo!1)`
- CBNGL-style compartment example: `none detected`

| Field | Detected from BNGL | Current YAML value | Proposed action | Proposed value | Short rationale |
| --- | --- | --- | --- | --- | --- |
| `uses_cbngl_compartments` | `false` | `missing` | insert | `false` | No CBNGL suffix syntax found. |
| `uses_vcell_compartments` | `true` | `missing` | insert | `true` | VCell syntax example found. |
| `uses_energy` | `false` | `false` | keep | `false` | energy active entries = 0. |
| `uses_functions` | `false` | `true` | change | `false` | functions active entries = 0. |
| `uses_moveconnected` | `false` | `missing` | insert | `false` | No active moveConnected call found. |
| `uses_trash_molecules` | `false` | `missing` | insert | `false` | No active Trash pattern found. |
| `uses_anchors` | `true` | `missing` | insert | `true` | anchors active entries = 1. |
| `uses_multiple_identical_sites` | `false` | `missing` | insert | `false` | No repeated molecule-type site detected. |
| `uses_deletes_molecules` | `false` | `missing` | insert | `false` | No active DeleteMolecules found. |
| `uses_exclude_include_reactants` | `false` | `missing` | insert | `false` | No include/exclude reactants modifier found. |
| `uses_generate_network` | `true` | `missing` | insert | `true` | Active generate_network action found. |
| `default_sim_command` | `null` | `missing` | insert | `null` | No active simulation command found. |

### 5. `Rulebasedegfrcompart`

- Block diagnostics:
  - `compartments`: present `true`; active entries `3`
  - `anchors`: present `true`; active entries `2`
  - `functions`: present `true`; active entries `0`
  - `energy patterns`: present `false`; active entries `0`
- VCell-style compartment example: `@EC:EGF(rb)`
- CBNGL-style compartment example: `none detected`

| Field | Detected from BNGL | Current YAML value | Proposed action | Proposed value | Short rationale |
| --- | --- | --- | --- | --- | --- |
| `uses_cbngl_compartments` | `false` | `missing` | insert | `false` | No CBNGL suffix syntax found. |
| `uses_vcell_compartments` | `true` | `missing` | insert | `true` | VCell syntax example found. |
| `uses_energy` | `false` | `false` | keep | `false` | energy active entries = 0. |
| `uses_functions` | `false` | `true` | change | `false` | functions active entries = 0. |
| `uses_moveconnected` | `false` | `missing` | insert | `false` | No active moveConnected call found. |
| `uses_trash_molecules` | `false` | `missing` | insert | `false` | No active Trash pattern found. |
| `uses_anchors` | `true` | `missing` | insert | `true` | anchors active entries = 2. |
| `uses_multiple_identical_sites` | `false` | `missing` | insert | `false` | No repeated molecule-type site detected. |
| `uses_deletes_molecules` | `false` | `missing` | insert | `false` | No active DeleteMolecules found. |
| `uses_exclude_include_reactants` | `false` | `missing` | insert | `false` | No include/exclude reactants modifier found. |
| `uses_generate_network` | `true` | `missing` | insert | `true` | Active generate_network action found. |
| `default_sim_command` | `null` | `missing` | insert | `null` | No active simulation command found. |

### 6. `Rulebasedegfrtutorial`

- Block diagnostics:
  - `compartments`: present `true`; active entries `1`
  - `anchors`: present `false`; active entries `0`
  - `functions`: present `true`; active entries `0`
  - `energy patterns`: present `false`; active entries `0`
- VCell-style compartment example: `@c0:EGFR(ecd,tmd,Y1~u,Y2~u)`
- CBNGL-style compartment example: `none detected`

| Field | Detected from BNGL | Current YAML value | Proposed action | Proposed value | Short rationale |
| --- | --- | --- | --- | --- | --- |
| `uses_cbngl_compartments` | `false` | `missing` | insert | `false` | No CBNGL suffix syntax found. |
| `uses_vcell_compartments` | `true` | `missing` | insert | `true` | VCell syntax example found. |
| `uses_energy` | `false` | `false` | keep | `false` | energy active entries = 0. |
| `uses_functions` | `false` | `true` | change | `false` | functions active entries = 0. |
| `uses_moveconnected` | `false` | `missing` | insert | `false` | No active moveConnected call found. |
| `uses_trash_molecules` | `false` | `missing` | insert | `false` | No active Trash pattern found. |
| `uses_anchors` | `false` | `missing` | insert | `false` | anchors active entries = 0. |
| `uses_multiple_identical_sites` | `false` | `missing` | insert | `false` | No repeated molecule-type site detected. |
| `uses_deletes_molecules` | `false` | `missing` | insert | `false` | No active DeleteMolecules found. |
| `uses_exclude_include_reactants` | `false` | `missing` | insert | `false` | No include/exclude reactants modifier found. |
| `uses_generate_network` | `true` | `missing` | insert | `true` | Active generate_network action found. |
| `default_sim_command` | `null` | `missing` | insert | `null` | No active simulation command found. |

### 7. `Jung2017`

- Block diagnostics:
  - `compartments`: present `true`; active entries `3`
  - `anchors`: present `false`; active entries `0`
  - `functions`: present `true`; active entries `2`
  - `energy patterns`: present `false`; active entries `0`
- VCell-style compartment example: `@EC:Oxo_EC()`
- CBNGL-style compartment example: `none detected`

| Field | Detected from BNGL | Current YAML value | Proposed action | Proposed value | Short rationale |
| --- | --- | --- | --- | --- | --- |
| `uses_cbngl_compartments` | `false` | `missing` | insert | `false` | No CBNGL suffix syntax found. |
| `uses_vcell_compartments` | `true` | `missing` | insert | `true` | VCell syntax example found. |
| `uses_energy` | `false` | `false` | keep | `false` | energy active entries = 0. |
| `uses_functions` | `true` | `true` | keep | `true` | functions active entries = 2. |
| `uses_moveconnected` | `false` | `missing` | insert | `false` | No active moveConnected call found. |
| `uses_trash_molecules` | `false` | `missing` | insert | `false` | No active Trash pattern found. |
| `uses_anchors` | `false` | `missing` | insert | `false` | anchors active entries = 0. |
| `uses_multiple_identical_sites` | `false` | `missing` | insert | `false` | No repeated molecule-type site detected. |
| `uses_deletes_molecules` | `false` | `missing` | insert | `false` | No active DeleteMolecules found. |
| `uses_exclude_include_reactants` | `false` | `missing` | insert | `false` | No include/exclude reactants modifier found. |
| `uses_generate_network` | `true` | `missing` | insert | `true` | Active generate_network action found. |
| `default_sim_command` | `null` | `missing` | insert | `null` | No active simulation command found. |

### 8. `Lang2024`

- Block diagnostics:
  - `compartments`: present `true`; active entries `1`
  - `anchors`: present `false`; active entries `0`
  - `functions`: present `false`; active entries `0`
  - `energy patterns`: present `false`; active entries `0`
- VCell-style compartment example: `@cell:CCND()`
- CBNGL-style compartment example: `none detected`

| Field | Detected from BNGL | Current YAML value | Proposed action | Proposed value | Short rationale |
| --- | --- | --- | --- | --- | --- |
| `uses_cbngl_compartments` | `false` | `missing` | insert | `false` | No CBNGL suffix syntax found. |
| `uses_vcell_compartments` | `true` | `missing` | insert | `true` | VCell syntax example found. |
| `uses_energy` | `false` | `false` | keep | `false` | energy active entries = 0. |
| `uses_functions` | `false` | `false` | keep | `false` | functions active entries = 0. |
| `uses_moveconnected` | `false` | `missing` | insert | `false` | No active moveConnected call found. |
| `uses_trash_molecules` | `false` | `missing` | insert | `false` | No active Trash pattern found. |
| `uses_anchors` | `false` | `missing` | insert | `false` | anchors active entries = 0. |
| `uses_multiple_identical_sites` | `false` | `missing` | insert | `false` | No repeated molecule-type site detected. |
| `uses_deletes_molecules` | `true` | `missing` | insert | `true` | Active DeleteMolecules found. |
| `uses_exclude_include_reactants` | `true` | `missing` | insert | `true` | Active include/exclude reactants modifier found. |
| `uses_generate_network` | `true` | `missing` | insert | `true` | Active generate_network action found. |
| `default_sim_command` | `simulate` | `missing` | insert | `simulate` | First active simulation command is simulate. |

### 9. `Nosbisch2022`

- Block diagnostics:
  - `compartments`: present `true`; active entries `1`
  - `anchors`: present `false`; active entries `0`
  - `functions`: present `true`; active entries `0`
  - `energy patterns`: present `false`; active entries `0`
- VCell-style compartment example: `@cell:RTK(pY)`
- CBNGL-style compartment example: `none detected`

| Field | Detected from BNGL | Current YAML value | Proposed action | Proposed value | Short rationale |
| --- | --- | --- | --- | --- | --- |
| `uses_cbngl_compartments` | `false` | `missing` | insert | `false` | No CBNGL suffix syntax found. |
| `uses_vcell_compartments` | `true` | `missing` | insert | `true` | VCell syntax example found. |
| `uses_energy` | `false` | `false` | keep | `false` | energy active entries = 0. |
| `uses_functions` | `false` | `true` | change | `false` | functions active entries = 0. |
| `uses_moveconnected` | `false` | `missing` | insert | `false` | No active moveConnected call found. |
| `uses_trash_molecules` | `false` | `missing` | insert | `false` | No active Trash pattern found. |
| `uses_anchors` | `false` | `missing` | insert | `false` | anchors active entries = 0. |
| `uses_multiple_identical_sites` | `false` | `missing` | insert | `false` | No repeated molecule-type site detected. |
| `uses_deletes_molecules` | `false` | `missing` | insert | `false` | No active DeleteMolecules found. |
| `uses_exclude_include_reactants` | `false` | `missing` | insert | `false` | No include/exclude reactants modifier found. |
| `uses_generate_network` | `true` | `missing` | insert | `true` | Active generate_network action found. |
| `default_sim_command` | `null` | `missing` | insert | `null` | No active simulation command found. |

### 10. `Barua2007`

- Block diagnostics:
  - `compartments`: present `false`; active entries `0`
  - `anchors`: present `false`; active entries `0`
  - `functions`: present `false`; active entries `0`
  - `energy patterns`: present `false`; active entries `0`
- VCell-style compartment example: `none detected`
- CBNGL-style compartment example: `none detected`

| Field | Detected from BNGL | Current YAML value | Proposed action | Proposed value | Short rationale |
| --- | --- | --- | --- | --- | --- |
| `uses_cbngl_compartments` | `false` | `missing` | insert | `false` | No CBNGL suffix syntax found. |
| `uses_vcell_compartments` | `false` | `missing` | insert | `false` | No VCell prefix syntax found. |
| `uses_energy` | `false` | `false` | keep | `false` | energy active entries = 0. |
| `uses_functions` | `false` | `false` | keep | `false` | functions active entries = 0. |
| `uses_moveconnected` | `false` | `missing` | insert | `false` | No active moveConnected call found. |
| `uses_trash_molecules` | `false` | `missing` | insert | `false` | No active Trash pattern found. |
| `uses_anchors` | `false` | `missing` | insert | `false` | anchors active entries = 0. |
| `uses_multiple_identical_sites` | `false` | `missing` | insert | `false` | No repeated molecule-type site detected. |
| `uses_deletes_molecules` | `false` | `missing` | insert | `false` | No active DeleteMolecules found. |
| `uses_exclude_include_reactants` | `true` | `missing` | insert | `true` | Active include/exclude reactants modifier found. |
| `uses_generate_network` | `true` | `missing` | insert | `true` | Active generate_network action found. |
| `default_sim_command` | `simulate_ode` | `missing` | insert | `simulate_ode` | First active simulation command is simulate_ode. |

### 11. `An2009`

- Block diagnostics:
  - `compartments`: present `false`; active entries `0`
  - `anchors`: present `false`; active entries `0`
  - `functions`: present `false`; active entries `0`
  - `energy patterns`: present `false`; active entries `0`
- VCell-style compartment example: `none detected`
- CBNGL-style compartment example: `none detected`

| Field | Detected from BNGL | Current YAML value | Proposed action | Proposed value | Short rationale |
| --- | --- | --- | --- | --- | --- |
| `uses_cbngl_compartments` | `false` | `missing` | insert | `false` | No CBNGL suffix syntax found. |
| `uses_vcell_compartments` | `false` | `missing` | insert | `false` | No VCell prefix syntax found. |
| `uses_energy` | `false` | `false` | keep | `false` | energy active entries = 0. |
| `uses_functions` | `false` | `false` | keep | `false` | functions active entries = 0. |
| `uses_moveconnected` | `false` | `missing` | insert | `false` | No active moveConnected call found. |
| `uses_trash_molecules` | `true` | `missing` | insert | `true` | Active Trash pattern found. |
| `uses_anchors` | `false` | `missing` | insert | `false` | anchors active entries = 0. |
| `uses_multiple_identical_sites` | `true` | `missing` | insert | `true` | Repeated molecule-type site detected. |
| `uses_deletes_molecules` | `false` | `missing` | insert | `false` | No active DeleteMolecules found. |
| `uses_exclude_include_reactants` | `false` | `missing` | insert | `false` | No include/exclude reactants modifier found. |
| `uses_generate_network` | `true` | `missing` | insert | `true` | Active generate_network action found. |
| `default_sim_command` | `simulate_ode` | `missing` | insert | `simulate_ode` | First active simulation command is simulate_ode. |

### 12. `Ligon2014`

- Block diagnostics:
  - `compartments`: present `false`; active entries `0`
  - `anchors`: present `false`; active entries `0`
  - `functions`: present `true`; active entries `1`
  - `energy patterns`: present `false`; active entries `0`
- VCell-style compartment example: `none detected`
- CBNGL-style compartment example: `none detected`

| Field | Detected from BNGL | Current YAML value | Proposed action | Proposed value | Short rationale |
| --- | --- | --- | --- | --- | --- |
| `uses_cbngl_compartments` | `false` | `missing` | insert | `false` | No CBNGL suffix syntax found. |
| `uses_vcell_compartments` | `false` | `missing` | insert | `false` | No VCell prefix syntax found. |
| `uses_energy` | `false` | `false` | keep | `false` | energy active entries = 0. |
| `uses_functions` | `true` | `true` | keep | `true` | functions active entries = 1. |
| `uses_moveconnected` | `false` | `missing` | insert | `false` | No active moveConnected call found. |
| `uses_trash_molecules` | `false` | `missing` | insert | `false` | No active Trash pattern found. |
| `uses_anchors` | `false` | `missing` | insert | `false` | anchors active entries = 0. |
| `uses_multiple_identical_sites` | `false` | `missing` | insert | `false` | No repeated molecule-type site detected. |
| `uses_deletes_molecules` | `true` | `missing` | insert | `true` | Active DeleteMolecules found. |
| `uses_exclude_include_reactants` | `false` | `missing` | insert | `false` | No include/exclude reactants modifier found. |
| `uses_generate_network` | `false` | `missing` | insert | `false` | No active generate_network action found. |
| `default_sim_command` | `simulate_nf` | `missing` | insert | `simulate_nf` | First active simulation command is simulate_nf. |

### 13. `Zhang2023`

- Block diagnostics:
  - `compartments`: present `false`; active entries `0`
  - `anchors`: present `false`; active entries `0`
  - `functions`: present `false`; active entries `0`
  - `energy patterns`: present `false`; active entries `0`
- VCell-style compartment example: `none detected`
- CBNGL-style compartment example: `none detected`

| Field | Detected from BNGL | Current YAML value | Proposed action | Proposed value | Short rationale |
| --- | --- | --- | --- | --- | --- |
| `uses_cbngl_compartments` | `false` | `missing` | insert | `false` | No CBNGL suffix syntax found. |
| `uses_vcell_compartments` | `false` | `missing` | insert | `false` | No VCell prefix syntax found. |
| `uses_energy` | `false` | `false` | keep | `false` | energy active entries = 0. |
| `uses_functions` | `false` | `false` | keep | `false` | functions active entries = 0. |
| `uses_moveconnected` | `false` | `missing` | insert | `false` | No active moveConnected call found. |
| `uses_trash_molecules` | `true` | `missing` | insert | `true` | Active Trash pattern found. |
| `uses_anchors` | `false` | `missing` | insert | `false` | anchors active entries = 0. |
| `uses_multiple_identical_sites` | `true` | `missing` | insert | `true` | Repeated molecule-type site detected. |
| `uses_deletes_molecules` | `false` | `missing` | insert | `false` | No active DeleteMolecules found. |
| `uses_exclude_include_reactants` | `false` | `missing` | insert | `false` | No include/exclude reactants modifier found. |
| `uses_generate_network` | `true` | `missing` | insert | `true` | Active generate_network action found. |
| `default_sim_command` | `null` | `missing` | insert | `null` | No active simulation command found. |

### 14. `ChylekFceRI2014`

- Block diagnostics:
  - `compartments`: present `false`; active entries `0`
  - `anchors`: present `false`; active entries `0`
  - `functions`: present `false`; active entries `0`
  - `energy patterns`: present `false`; active entries `0`
- VCell-style compartment example: `none detected`
- CBNGL-style compartment example: `none detected`

| Field | Detected from BNGL | Current YAML value | Proposed action | Proposed value | Short rationale |
| --- | --- | --- | --- | --- | --- |
| `uses_cbngl_compartments` | `false` | `missing` | insert | `false` | No CBNGL suffix syntax found. |
| `uses_vcell_compartments` | `false` | `missing` | insert | `false` | No VCell prefix syntax found. |
| `uses_energy` | `false` | `false` | keep | `false` | energy active entries = 0. |
| `uses_functions` | `false` | `false` | keep | `false` | functions active entries = 0. |
| `uses_moveconnected` | `false` | `missing` | insert | `false` | No active moveConnected call found. |
| `uses_trash_molecules` | `false` | `missing` | insert | `false` | No active Trash pattern found. |
| `uses_anchors` | `false` | `missing` | insert | `false` | anchors active entries = 0. |
| `uses_multiple_identical_sites` | `true` | `missing` | insert | `true` | Repeated molecule-type site detected. |
| `uses_deletes_molecules` | `true` | `missing` | insert | `true` | Active DeleteMolecules found. |
| `uses_exclude_include_reactants` | `false` | `missing` | insert | `false` | No include/exclude reactants modifier found. |
| `uses_generate_network` | `false` | `missing` | insert | `false` | No active generate_network action found. |
| `default_sim_command` | `null` | `missing` | insert | `null` | No active simulation command found. |

### 15. `Dolan2015`

- Block diagnostics:
  - `compartments`: present `false`; active entries `0`
  - `anchors`: present `false`; active entries `0`
  - `functions`: present `true`; active entries `9`
  - `energy patterns`: present `false`; active entries `0`
- VCell-style compartment example: `none detected`
- CBNGL-style compartment example: `none detected`

| Field | Detected from BNGL | Current YAML value | Proposed action | Proposed value | Short rationale |
| --- | --- | --- | --- | --- | --- |
| `uses_cbngl_compartments` | `false` | `missing` | insert | `false` | No CBNGL suffix syntax found. |
| `uses_vcell_compartments` | `false` | `missing` | insert | `false` | No VCell prefix syntax found. |
| `uses_energy` | `false` | `false` | keep | `false` | energy active entries = 0. |
| `uses_functions` | `true` | `true` | keep | `true` | functions active entries = 9. |
| `uses_moveconnected` | `false` | `missing` | insert | `false` | No active moveConnected call found. |
| `uses_trash_molecules` | `false` | `missing` | insert | `false` | No active Trash pattern found. |
| `uses_anchors` | `false` | `missing` | insert | `false` | anchors active entries = 0. |
| `uses_multiple_identical_sites` | `false` | `missing` | insert | `false` | No repeated molecule-type site detected. |
| `uses_deletes_molecules` | `true` | `missing` | insert | `true` | Active DeleteMolecules found. |
| `uses_exclude_include_reactants` | `false` | `missing` | insert | `false` | No include/exclude reactants modifier found. |
| `uses_generate_network` | `false` | `missing` | insert | `false` | No active generate_network action found. |
| `default_sim_command` | `simulate_nf` | `missing` | insert | `simulate_nf` | First active simulation command is simulate_nf. |

### 16. `Hlavacek2001`

- Block diagnostics:
  - `compartments`: present `false`; active entries `0`
  - `anchors`: present `false`; active entries `0`
  - `functions`: present `true`; active entries `4`
  - `energy patterns`: present `false`; active entries `0`
- VCell-style compartment example: `none detected`
- CBNGL-style compartment example: `none detected`

| Field | Detected from BNGL | Current YAML value | Proposed action | Proposed value | Short rationale |
| --- | --- | --- | --- | --- | --- |
| `uses_cbngl_compartments` | `false` | `missing` | insert | `false` | No CBNGL suffix syntax found. |
| `uses_vcell_compartments` | `false` | `missing` | insert | `false` | No VCell prefix syntax found. |
| `uses_energy` | `false` | `false` | keep | `false` | energy active entries = 0. |
| `uses_functions` | `true` | `true` | keep | `true` | functions active entries = 4. |
| `uses_moveconnected` | `false` | `missing` | insert | `false` | No active moveConnected call found. |
| `uses_trash_molecules` | `false` | `missing` | insert | `false` | No active Trash pattern found. |
| `uses_anchors` | `false` | `missing` | insert | `false` | anchors active entries = 0. |
| `uses_multiple_identical_sites` | `true` | `missing` | insert | `true` | Repeated molecule-type site detected. |
| `uses_deletes_molecules` | `false` | `missing` | insert | `false` | No active DeleteMolecules found. |
| `uses_exclude_include_reactants` | `false` | `missing` | insert | `false` | No include/exclude reactants modifier found. |
| `uses_generate_network` | `true` | `missing` | insert | `true` | Active generate_network action found. |
| `default_sim_command` | `simulate` | `missing` | insert | `simulate` | First active simulation command is simulate. |

### 17. `Dembo1978`

- Block diagnostics:
  - `compartments`: present `false`; active entries `0`
  - `anchors`: present `false`; active entries `0`
  - `functions`: present `false`; active entries `0`
  - `energy patterns`: present `false`; active entries `0`
- VCell-style compartment example: `none detected`
- CBNGL-style compartment example: `none detected`

| Field | Detected from BNGL | Current YAML value | Proposed action | Proposed value | Short rationale |
| --- | --- | --- | --- | --- | --- |
| `uses_cbngl_compartments` | `false` | `missing` | insert | `false` | No CBNGL suffix syntax found. |
| `uses_vcell_compartments` | `false` | `missing` | insert | `false` | No VCell prefix syntax found. |
| `uses_energy` | `false` | `false` | keep | `false` | energy active entries = 0. |
| `uses_functions` | `false` | `false` | keep | `false` | functions active entries = 0. |
| `uses_moveconnected` | `false` | `missing` | insert | `false` | No active moveConnected call found. |
| `uses_trash_molecules` | `false` | `missing` | insert | `false` | No active Trash pattern found. |
| `uses_anchors` | `false` | `missing` | insert | `false` | anchors active entries = 0. |
| `uses_multiple_identical_sites` | `true` | `missing` | insert | `true` | Repeated molecule-type site detected. |
| `uses_deletes_molecules` | `false` | `missing` | insert | `false` | No active DeleteMolecules found. |
| `uses_exclude_include_reactants` | `false` | `missing` | insert | `false` | No include/exclude reactants modifier found. |
| `uses_generate_network` | `false` | `missing` | insert | `false` | No active generate_network action found. |
| `default_sim_command` | `simulate` | `missing` | insert | `simulate` | First active simulation command is simulate. |

### 18. `Dreisigmeyer2008`

- Block diagnostics:
  - `compartments`: present `false`; active entries `0`
  - `anchors`: present `false`; active entries `0`
  - `functions`: present `true`; active entries `12`
  - `energy patterns`: present `false`; active entries `0`
- VCell-style compartment example: `none detected`
- CBNGL-style compartment example: `none detected`

| Field | Detected from BNGL | Current YAML value | Proposed action | Proposed value | Short rationale |
| --- | --- | --- | --- | --- | --- |
| `uses_cbngl_compartments` | `false` | `missing` | insert | `false` | No CBNGL suffix syntax found. |
| `uses_vcell_compartments` | `false` | `missing` | insert | `false` | No VCell prefix syntax found. |
| `uses_energy` | `false` | `false` | keep | `false` | energy active entries = 0. |
| `uses_functions` | `true` | `true` | keep | `true` | functions active entries = 12. |
| `uses_moveconnected` | `false` | `missing` | insert | `false` | No active moveConnected call found. |
| `uses_trash_molecules` | `false` | `missing` | insert | `false` | No active Trash pattern found. |
| `uses_anchors` | `false` | `missing` | insert | `false` | anchors active entries = 0. |
| `uses_multiple_identical_sites` | `false` | `missing` | insert | `false` | No repeated molecule-type site detected. |
| `uses_deletes_molecules` | `false` | `missing` | insert | `false` | No active DeleteMolecules found. |
| `uses_exclude_include_reactants` | `false` | `missing` | insert | `false` | No include/exclude reactants modifier found. |
| `uses_generate_network` | `true` | `missing` | insert | `true` | Active generate_network action found. |
| `default_sim_command` | `simulate` | `missing` | insert | `simulate` | First active simulation command is simulate. |

### 19. `Gardner2000`

- Block diagnostics:
  - `compartments`: present `false`; active entries `0`
  - `anchors`: present `false`; active entries `0`
  - `functions`: present `true`; active entries `2`
  - `energy patterns`: present `false`; active entries `0`
- VCell-style compartment example: `none detected`
- CBNGL-style compartment example: `none detected`

| Field | Detected from BNGL | Current YAML value | Proposed action | Proposed value | Short rationale |
| --- | --- | --- | --- | --- | --- |
| `uses_cbngl_compartments` | `false` | `missing` | insert | `false` | No CBNGL suffix syntax found. |
| `uses_vcell_compartments` | `false` | `missing` | insert | `false` | No VCell prefix syntax found. |
| `uses_energy` | `false` | `false` | keep | `false` | energy active entries = 0. |
| `uses_functions` | `true` | `true` | keep | `true` | functions active entries = 2. |
| `uses_moveconnected` | `false` | `missing` | insert | `false` | No active moveConnected call found. |
| `uses_trash_molecules` | `false` | `missing` | insert | `false` | No active Trash pattern found. |
| `uses_anchors` | `false` | `missing` | insert | `false` | anchors active entries = 0. |
| `uses_multiple_identical_sites` | `false` | `missing` | insert | `false` | No repeated molecule-type site detected. |
| `uses_deletes_molecules` | `false` | `missing` | insert | `false` | No active DeleteMolecules found. |
| `uses_exclude_include_reactants` | `false` | `missing` | insert | `false` | No include/exclude reactants modifier found. |
| `uses_generate_network` | `true` | `missing` | insert | `true` | Active generate_network action found. |
| `default_sim_command` | `simulate` | `missing` | insert | `simulate` | First active simulation command is simulate. |

### 20. `Barua2009`

- Block diagnostics:
  - `compartments`: present `false`; active entries `0`
  - `anchors`: present `false`; active entries `0`
  - `functions`: present `false`; active entries `0`
  - `energy patterns`: present `false`; active entries `0`
- VCell-style compartment example: `none detected`
- CBNGL-style compartment example: `none detected`

| Field | Detected from BNGL | Current YAML value | Proposed action | Proposed value | Short rationale |
| --- | --- | --- | --- | --- | --- |
| `uses_cbngl_compartments` | `false` | `missing` | insert | `false` | No CBNGL suffix syntax found. |
| `uses_vcell_compartments` | `false` | `missing` | insert | `false` | No VCell prefix syntax found. |
| `uses_energy` | `false` | `false` | keep | `false` | energy active entries = 0. |
| `uses_functions` | `false` | `false` | keep | `false` | functions active entries = 0. |
| `uses_moveconnected` | `false` | `missing` | insert | `false` | No active moveConnected call found. |
| `uses_trash_molecules` | `false` | `missing` | insert | `false` | No active Trash pattern found. |
| `uses_anchors` | `false` | `missing` | insert | `false` | anchors active entries = 0. |
| `uses_multiple_identical_sites` | `false` | `missing` | insert | `false` | No repeated molecule-type site detected. |
| `uses_deletes_molecules` | `false` | `missing` | insert | `false` | No active DeleteMolecules found. |
| `uses_exclude_include_reactants` | `false` | `missing` | insert | `false` | No include/exclude reactants modifier found. |
| `uses_generate_network` | `true` | `missing` | insert | `true` | Active generate_network action found. |
| `default_sim_command` | `simulate_ode` | `missing` | insert | `simulate_ode` | First active simulation command is simulate_ode. |
