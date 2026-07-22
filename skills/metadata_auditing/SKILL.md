---
name: metadata_auditing
description: Audit RuleHub BNGL/YAML metadata feature fields, write concise Markdown audit reports, and create same-directory audited YAML copies with corrected feature values.
---

# RuleHub Metadata Auditing

## Purpose

Use this skill to audit RuleHub BNGL/YAML model metadata against the local BNGL source. The audit has two deliverables when requested:

1. A concise Markdown audit summary under `data/`.
2. Audited YAML copies inside each audited model folder.

## Required Inputs and Pairing Rule

Read local repository files only. Never rely on GitHub raw URLs or inherited ancestor metadata.

A valid audit pair is a `.bngl` file and one target YAML file in the **same directory**.

- Do not pair a BNGL file with YAML from a parent, child, or sibling directory.
- If a directory has multiple same-directory `.bngl` files and one target YAML file, each `.bngl` may be audited as a separate BNGL/YAML pair if the user requests pair-level auditing.

## YAML Target Selection

For each model directory, choose the YAML file to audit using this priority:

1. If the user explicitly names a YAML file, audit that file.
2. Else, if a nonstandard metadata-like YAML exists, especially a file matching `*_metadata.yaml`, audit that collaborator-updated YAML.
3. Else, audit the standard `metadata.yaml`.

If both `metadata.yaml` and one or more nonstandard metadata-like YAML files are present, state which YAML file was audited. Do not silently merge values across YAML files.

## Audited YAML Output Rule

When the user asks for audited YAML files, create a new YAML file in the **same model folder** as the audited source YAML.

Name the audited file:

```text
<original-yaml-stem>_audited.yaml
```

Examples:

| Source YAML | Audited YAML |
| --- | --- |
| `metadata.yaml` | `metadata_audited.yaml` |
| `An_2009_metadata.yaml` | `An_2009_metadata_audited.yaml` |
| `Dolan_2015_metadata.yaml` | `Dolan_2015_metadata_audited.yaml` |

Rules:

- Do not overwrite the original YAML unless the user explicitly asks.
- Do not write audited YAML files under `data/`, `data/summaries/`, `data/summaries_coders/`, or any central output folder.
- Preserve unrelated YAML content, ordering, quoting style, and nested structure as much as practical.
- Insert or update audited fields in the existing `compatibility:` mapping unless the repository has an explicitly different convention for the target file.
- If the target YAML is malformed or ambiguous, do not guess silently; record `manual review` in the audit report.

## Fields to Audit

Audit these fields unless the user gives a different list:

```yaml
uses_cbngl_compartments: boolean
uses_vcell_compartments: boolean
uses_energy: boolean
uses_functions: boolean
uses_moveconnected: boolean
uses_trash_molecules: boolean
uses_anchors: boolean
uses_multiple_identical_sites: boolean
uses_deletes_molecules: boolean
uses_exclude_include_reactants: boolean
uses_generate_network: boolean
default_sim_command:
```

## BNGL Preprocessing

Before detection:

- Ignore blank lines.
- Ignore full-line comments.
- Ignore disabled/commented-out rules, blocks, observables, actions, and modifiers.
- Treat an active entry as an uncommented, nonempty line inside a BNGL block.
- Report block presence separately from active entry count.

## Detection Definitions

### Compartments

Compartment compatibility is determined by BNGL grammar.

- `uses_vcell_compartments`: `true` when active BNGL patterns use VCell-style compartment-prefix syntax:

  ```text
  @Compartment:Molecule(...)
  ```

  Example: `@EC:EGF(rb)`.

- `uses_cbngl_compartments`: `true` when active BNGL patterns use CBNGL-style molecule-suffixed compartment syntax:

  ```text
  Molecule(...)@Compartment
  ```

  Example: `SARM(b)@Cyt`.

- A `begin compartments` block must be reported in block diagnostics, but it does not by itself make either compartment field true.
- If both syntaxes appear actively in one BNGL file, set both fields to `true` and add a short mixed-syntax rationale.

### Block-based fields

Empty blocks do **not** make feature booleans true.

For block-based fields, set the field to `true` only when the relevant block contains at least one active, uncommented, nonempty entry.

Examples:

```bngl
begin functions
end functions
```

means:

```yaml
uses_functions: false
```

but the report should still record:

```text
functions block present: true; active entries: 0
```

Apply this active-entry rule to:

- `uses_functions`: true only if the `begin functions` block has at least one active function entry.
- `uses_anchors`: true only if the `begin anchors` block has at least one active anchor entry.
- `uses_energy`: true only if an energy-pattern block exists and has at least one active energy entry.

### Other feature fields

- `uses_moveconnected`: true when an uncommented `moveConnected` call is detected.
- `uses_trash_molecules`: true when an active `Trash(...)` molecule or pattern is detected.
- `uses_multiple_identical_sites`: true when any molecule type declaration repeats the same site/component name within one molecule type, such as `L(r,r)`.
- `uses_deletes_molecules`: true when an uncommented `DeleteMolecules` modifier/action is detected.
- `uses_exclude_include_reactants`: true when an uncommented `include_reactants` or `exclude_reactants` modifier is detected.
- `uses_generate_network`: true when an uncommented `generate_network(...)` action is detected.
- `default_sim_command`: choose the first active simulation command in this priority order: `simulate_ode`, `simulate_ssa`, `simulate_nf`, `simulate`.

## Markdown Audit Report Requirements

Create the audit report under `data/` unless the user specifies another location.

The report must include these sections:

```markdown
# <descriptive audit title>

## Introduction

## Detection definitions

## Batch summary

## Audited pairs

## Per-model findings
```

### Introduction

Write a short, polished introduction explaining:

- the audit root or batch,
- the same-directory pairing rule,
- whether YAML files were modified or only proposed changes were recorded,
- whether audited YAML copies were created.

### Detection definitions

State the exact definitions used for each field, especially:

- VCell syntax: `@Compartment:Molecule(...)`.
- CBNGL syntax: `Molecule(...)@Compartment`.
- Empty block handling: empty blocks have zero active entries and do not make block-based fields true.
- `begin compartments` is diagnostic evidence only, not direct compartment-compatibility evidence.

### Batch summary

Include a compact table with one row per audited field:

| Field | Detected true | Detected false | Detected null | Current YAML missing | Proposed insertions | Proposed changes | Manual review |
| --- | ---: | ---: | ---: | ---: | ---: | ---: | ---: |

### Audited pairs

Include one row per pair:

| # | BNGL path | YAML audited | Audited YAML output | Proposed updates | Manual review? |
| ---: | --- | --- | --- | ---: | --- |

If this is report-only mode, use `not created` for the audited YAML output.

### Per-model findings

Keep each per-model section short. Do not include model-summary prose or long evidence lists.

Each per-model finding should include only:

1. **Block diagnostics**: block present yes/no and active entry count for key blocks.
2. **Compartment syntax example**: one VCell-style example if present and one CBNGL-style example if present. If none are present, say none detected.
3. **Results table** with detected value, current YAML value, proposed action, proposed value, and short rationale.

Use this table:

| Field | Detected from BNGL | Current YAML value | Proposed action | Proposed value | Short rationale |
| --- | --- | --- | --- | --- | --- |

Allowed proposed actions:

- `keep`
- `insert`
- `change`
- `manual review`

Do not repeat every compartment pattern, every block line, every rule, or every observable in the per-model finding. Include only the information needed to justify metadata-field decisions.

## Audited YAML Content Requirements

When creating audited YAML copies:

- Start from the selected target YAML content.
- Insert missing audited fields under `compatibility:`.
- Change inaccurate audited field values to the detected values.
- Preserve fields not being audited.
- Preserve existing metadata identity fields such as `id`, `name`, `description`, `source`, and `playground`.
- If `compatibility:` is absent, create it in a reasonable location near existing model-level metadata.
- Record every insertion/change in the Markdown report.
- If a value cannot be determined confidently, do not invent it; keep or insert a conservative value only if instructed, and mark the row `manual review`.

## Quality Checklist

Before finalizing, verify:

- Every audited BNGL/YAML pair is same-directory.
- The correct target YAML was chosen, including collaborator `*_metadata.yaml` files when present.
- Audited YAML copies, if created, are inside the corresponding model folders and named `<original-yaml-stem>_audited.yaml`.
- Empty blocks are reported with active entries `0` and do not make block-based fields true.
- VCell and CBNGL compartment fields are based on grammar examples, not block presence.
- Per-model findings are concise and do not contain long repeated evidence lists.
- The report includes introduction, definitions, batch summary, audited pairs, and per-model findings.
- The report distinguishes insertions, changes, keeps, and manual-review cases.
- No original YAML file is overwritten unless explicitly requested.
