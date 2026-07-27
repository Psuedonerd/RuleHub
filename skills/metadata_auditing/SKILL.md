---
name: metadata-auditing
description: Audit RuleHub BNGL feature metadata. Use when checking one or more same-directory BNGL/YAML model pairs; always create a brief Markdown audit under data/ and a metadata_aigenerated.yaml file in every audited model directory.
---

# Audit RuleHub metadata

Produce both deliverables for every audit:

1. One brief Markdown report under `data/`.
2. One `metadata_aigenerated.yaml` in every audited model directory.

Never run in report-only mode. Never overwrite the source YAML.

## Select inputs

Use only local files. Pair each `.bngl` file with metadata from the same directory; never inherit metadata from another directory.

Choose the source YAML in this order:

1. A file named by the user.
2. The model-specific `*_metadata.yaml` supplied by a collaborator.
3. `metadata.yaml`.

Do not use an existing `metadata_aigenerated.yaml` as the source. If several candidates remain, do not choose silently; note the ambiguity in the report and identify the file that requires confirmation.

For a multi-BNGL directory, audit the user-selected model. If none is selected, audit each BNGL separately only when each has an unambiguous model-specific YAML; otherwise request review in the report rather than combining evidence across models.

## Audit fields

Audit these fields under `compatibility:`:

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
default_sim_command: string | null
```

## Analyze BNGL

### Preprocess active content

Before detecting features:

- Ignore blank lines and full-line comments.
- Strip trailing comments before analyzing a line.
- Ignore commented-out blocks, entries, rules, observables, actions, and modifiers.
- Treat a block entry as active only when it is uncommented and nonempty between the matching `begin` and `end` lines.
- Do not count block delimiters as entries.
- Inspect the complete BNGL file; do not infer a feature from metadata, filenames, or tags.

### Detect compartment grammar

Set compartment booleans from active species-pattern syntax, not from the presence of a `begin compartments` block:

- Set `uses_vcell_compartments: true` for active compartment-prefix syntax: `@Compartment:Molecule(...)`.
- Set `uses_cbngl_compartments: true` for active molecule-suffix syntax: `Molecule(...)@Compartment`.
- Set both fields to `true` if both syntaxes occur.
- Set either field to `false` when its syntax does not occur, even if a compartments block exists.

Take care not to confuse compartment suffixes with molecule-site state or bond syntax. A compartments block defines compartments but does not prove either pattern grammar is used.

### Detect block-based features

Empty or comment-only blocks are false. Require at least one active entry:

- `uses_functions`: an active entry inside `begin functions`.
- `uses_anchors`: an active entry inside `begin anchors`.
- `uses_energy`: an active entry inside an energy-pattern block.

Only count active entries when resolving ambiguity or justifying a review item; do not place routine block diagnostics in the audit.

### Detect other features

- `uses_moveconnected`: an active `moveConnected` call.
- `uses_trash_molecules`: an active `Trash(...)` molecule or pattern used as a sink.
- `uses_multiple_identical_sites`: a molecule-type declaration repeats a component name within that molecule, such as `L(r,r)`.
- `uses_deletes_molecules`: an active `DeleteMolecules` modifier or action.
- `uses_exclude_include_reactants`: an active `include_reactants` or `exclude_reactants` modifier.
- `uses_generate_network`: an active `generate_network(...)` action.

Match complete BNGL identifiers case-sensitively where BNGL syntax is case-sensitive. Do not treat prose in comments or similarly named identifiers as evidence.

### Detect the default simulation command

Choose the first active command in this priority order and store its command name: `simulate_ode`, `simulate_ssa`, `simulate_nf`, `simulate`.

### Handle uncertainty

Mark a value ambiguous only when active BNGL syntax cannot be classified confidently. Search the relevant active block or construct again before doing so. Do not use ambiguity as a substitute for inspecting the model.

## Create the YAML files

For every audited model, copy the selected source metadata to same-directory `metadata_aigenerated.yaml`, then set every detected audit field to the detected value. If `compatibility:` is absent, create it.

- Insert missing false values without requesting review.
- Insert missing true values and flag them for review.
- Apply any change to an existing value and flag it for review.
- If detection is genuinely ambiguous, preserve the source value when present; otherwise use `null` only where the schema permits it. Flag the ambiguity for review.
- Preserve all unaudited content, ordering, quoting, and structure as closely as practical.

Treat a missing boolean as effectively false when deciding whether review is needed, but still write the explicit detected boolean to `metadata_aigenerated.yaml`.

Preserve identity, citation, source, playground, and all other unaudited metadata. Keep the source file's ordering, quoting, and formatting as closely as practical. Validate the completed YAML and ensure it contains only one `compatibility:` mapping and one instance of each audited key.

## Write the brief audit

Use a descriptive filename under `data/`. Keep the report focused on what a programmer must review. Do not include detection definitions, pairing lists, tables, block diagnostics, compartment examples, unchanged values, or evidence dumps.

Start with only a compact batch summary:

```markdown
# <Audit title>

Audited <N> models and created <N> `metadata_aigenerated.yaml` files. Inserted <N> missing values; <N> items require review.
```

Then add one heading per model. Keep all information for that model under its heading:

```markdown
## ModelName

- Inserted false: `field_a`, `field_b`.
- Review insertion: `field_c: true` — <short evidence>.
- Review change: `field_d: true` → `false` — <short evidence>.
- Review ambiguity: `field_e` — <what is unclear>.
```

Apply these brevity rules:

- Omit any bullet type that does not apply.
- Group all routine false insertions into one bullet.
- Give each inserted true, changed value, or ambiguity one short review bullet.
- Include an active-entry count only when it directly explains a reviewed anchors/functions/energy decision.
- If a model has no false insertions and nothing requires review, write `- No review required.`
- Do not explain that missing fields imply false.
- Mention the source YAML only when its selection is ambiguous or otherwise requires review.

## Verify

Before finishing, confirm:

- every audited model has a same-directory `metadata_aigenerated.yaml`;
- every boolean audit field is present and agrees with active BNGL content;
- `default_sim_command` agrees with the active command when one is detected;
- source YAML files remain unchanged;
- report totals match the generated files and reported bullets;
- only inserted true values, changes to existing values, and ambiguities are marked for review;
- the report contains no tables or diagnostic sections.
