---
name: explain-rulehub-model-detailed
description: Generate standardized, technical RuleHub explanations from a same-directory BNGL/YAML pair. Use for detailed summaries that interpret model structure, grouped parameters and rules, molecule sites and states, observables, setup, simulation workflow, and model-specific caveats without copying BNGL blocks.
---

# Explain RuleHub Model in Detail

## Purpose

Write a detailed, technically accurate Markdown explanation of one RuleHub BNGL model and its same-directory metadata. The explanation is an interpretive guide for modelers and curators, not a transcription of the source.

Optimize for usefulness:

- Explain what constructs do in this particular model.
- Prefer concise grouping when many entries share a mechanism.
- Preserve site- and state-level accuracy without pasting BNGL patterns.
- Avoid boilerplate, repeated sentence frames, raw declaration lists, and code-block dumps.
- Use the word **Detailed**, not **Coder**, in the document title.

## Reset Rule: Treat Every Model as New

Discard assumptions and prose from previous summaries before starting another model.

- Derive meanings only from the target directory's metadata, BNGL, comments, and nearby notes.
- Do not assume that an abbreviation has the same meaning across models.
- Do not infer an organism, cell type, residue identity, localization, or experimental claim that local files do not establish.
- Do not reuse stock descriptions of parameters, rules, observables, workflows, or caveats.
- Report unresolved meanings briefly in Section 9 instead of inventing them.

## Required Inputs

Read local files in this order:

1. The target directory's metadata YAML.
2. The same-directory BNGL file.
3. Same-directory README files or notes, if present.
4. Comments in the BNGL, especially comments adjacent to parameters, functions, molecule types, rules, observables, and actions.

A valid pair requires the BNGL and YAML to be in the same directory. Never inherit metadata from a parent directory. Do not treat `metadata_aigenerated.yaml` as the source metadata unless the user explicitly requests it.

## Analyze Before Writing

Build a private inventory before drafting:

- active BNGL blocks and their counts;
- parameter families and the constructs that consume them;
- every active function and its dependencies;
- every declared molecule type, site, repeated site, and internal state;
- compartments, anchors, and biologically important initial pools;
- active reaction-rule families and the exact site/state/bond changes within them;
- every active observable and what it measures;
- active actions and their execution order.

Ignore blank lines and comments when counting. Never include disabled/commented rules, observables, functions, or actions as active model behavior.

## BNGL Interpretation Rules

Apply these rules internally even when the final summary groups constructs:

- Distinguish molecule types from their components. A component named `CK2` is not a `CK2` molecule unless that molecule actually occurs in the pattern.
- Treat bond labels as local identifiers. Explain the two sites connected or released; do not burden the reader with bond numbers unless a number is necessary to distinguish topology.
- Record exact internal-state changes in readable form, such as `IKK.st: n → a`.
- Distinguish reversible association from one-way catalysis, creation, degradation, transport, or state conversion.
- Identify source `0`, sink `0`, `Trash`, `Sink`, `DeleteMolecules`, population species, catalytic carry-through, and compartment changes when they affect interpretation.
- Treat anchors as localization constraints on molecules or complexes.
- Distinguish molecule-count observables from species-count observables and remember that pattern matches may count embeddings rather than unique complexes.
- Explain extended constructs such as compartments, anchors, population maps, local functions, energy patterns, or conditional rates only when they occur.

## Required Markdown Structure

Use exactly these headings unless the user requests another structure:

```markdown
# Detailed Model Explanation: <specific model title>

## 1. Model overview

## 2. BNGL block inventory

## 3. Parameters, functions, and rate laws

## 4. Molecule types, sites, and states

## 5. Compartments, anchors, initial species, and setup

## 6. Reaction-rule inventory

## 7. Observables and technical readouts

## 8. Actions and simulation workflow

## 9. Technical caveats and ambiguities
```

## Section Requirements

### 1. Model overview

Describe the model's big-picture purpose and mechanism in about two sentences.

- Say what system or abstraction is modeled.
- Identify the principal input, mechanistic flow, and output or decision when supported locally.
- Do not list file paths, metadata fields, provenance, or a separate model id.
- Do not restate the title as a sentence.

### 2. BNGL block inventory

Give one concise paragraph or a compact table stating which blocks are present and their useful counts. Cover parameters, molecule types, species/seeds, functions, rules, observables, actions, compartments, and anchors when present.

- Keep this section short.
- If anchors exist, state their count and general localization purpose only; reserve details for Section 5.
- Do not explain individual parameters, rules, or observables here.

### 3. Parameters, functions, and rate laws

Begin with one or two sentences explaining the parameter namespace and rate-law style. Then use concise tables rather than prose blocks or copied declarations.

Use this parameter table:

| Parameter group or names | Function in this model |
| --- | --- |

Parameter guidance:

- Group parameters that share a mechanistic role, such as initial pools, association/dissociation pairs, phosphorylation, transport, transcription, degradation, or simulation control.
- Name every important parameter or a clearly defined range/family. Do not hide unrelated parameters in a vague “other” group.
- Explain what each group controls in this model and where it acts.
- Include numerical values only when they are essential to understanding a scale, switch, asymmetry, initial condition, or unusual behavior.
- Do not paste source comments or reproduce the parameter block.
- Explain algebraic, conditional, multiplicative, saturation, local, or observable-dependent rate laws in words.

If functions are present, add a separate table:

| Function | Inputs/dependencies | Meaning and use in this model |
| --- | --- | --- |

For every active function, explain what it computes, what controls it, and which rules or outputs use it. If no functions exist, say so in one sentence without adding an empty table.

### 4. Molecule types, sites, and states

Account for every declared molecule type, but group closely related types when this improves brevity and does not hide site or state differences.

Use exactly this table:

| Molecule type(s) | Site count | Sites/components | Internal states | Anchor/allowed compartments | Explanation |
| --- | ---: | --- | --- | --- | --- |

- Count and name all declared components, including repeated components.
- List all declared internal-state alternatives.
- State anchor or allowed-compartment constraints when present; otherwise use “None.”
- Use the final column for one brief, model-specific explanation of the molecule's role.
- Do not include a separate Notes column.
- Do not paste declarations into the explanation column.
- If the model lacks a molecule-types block, identify effective players from active species/rules and explicitly mark that inference as a caveat.

### 5. Compartments, anchors, initial species, and setup

Explain the starting configuration in concise prose, using a short list only if it improves readability.

- Describe compartment hierarchy, sizes, and movement only when relevant to model behavior.
- Explain each anchor localization or group closely related anchors by compartment.
- Identify the important initial pools and their starting states: stimulus, receptor, enzymes, substrates, scaffolds, feedback regulators, or zero-initialized outputs.
- Include initial amounts only when needed to understand stoichiometry, scale, an absent stimulus, or an important imbalance.
- Do not enumerate every seed merely because it exists.
- Never paste seed-species or anchor declarations.

### 6. Reaction-rule inventory

This section is the main mechanistic map. Explain rules verbally at site/state level; do not reproduce complete BNGL patterns.

For small models, use one row per active rule. For medium or large models, group adjacent rules only when they implement the same mechanism and differ predictably by site, state, occupancy, ligand count, or family member. Every active rule must still be accounted for by an individual number or an explicit number range/list.

Before the table, add a short, model-specific **Rule-family orientation** paragraph when the model has multiple families. Explain the sequence or relationship among those families; do not use a generic description of how to read a table.

Use exactly this five-column table:

| Rule number(s) | Direction | Involved molecules/sites | Exact modeled change and rate logic | Role within the model |
| ---: | --- | --- | --- | --- |

Table requirements:

- **Rule number(s):** use source order. A grouped row must enumerate the covered rules with a range or explicit list.
- **Direction:** state reversible, one-way, or mixed if a grouped family genuinely contains both; split the group if “mixed” would obscure behavior.
- **Involved molecules/sites:** list true molecule participants and the sites or states required for the rule to match. Do not list components as molecules.
- **Exact modeled change and rate logic:** verbally name the bond created/released, state transition, creation/removal event, localization change, or catalytic carry-through. Identify the applicable rate name or explain the full rate expression when its algebra changes behavior. Do not paste a BNGL rule.
- **Role within the model:** explain why the rule or family exists, how it advances or restrains the mechanism, and how it relates to nearby rules when useful.

Grouping rules:

- Group repetitive rules when a single precise row can state the shared mechanism and enumerate all varying sites, states, occupancies, or family members.
- Do not group rules that differ in direction, biological role, product semantics, localization, catalytic behavior, or materially different rate logic.
- For a grouped family, explicitly map rule numbers to their variants, for example: “12–15 target `l1`–`l4`, respectively.”
- Never replace interpretation with phrases such as “binding-pattern rewrite,” “see the pattern,” “same as above,” or “forms the explicitly site-matched bond.”
- Avoid repeated functional descriptions. Each row must add information specific to its rule or family.
- Omit local bond numbers unless topology cannot be explained without them.

### 7. Observables and technical readouts

Explain every active observable, grouping closely related readouts when that is clearer.

Use this table:

| Observable(s) | Type | What is measured | Technical interpretation |
| --- | --- | --- | --- |

- Name every observable covered by each row.
- State molecule-count, species-count, population, or other type.
- Summarize the measured state, complex, localization, or family verbally; do not paste observable patterns.
- Explain how the readout should be interpreted and note double-counting or embedding behavior when relevant.

### 8. Actions and simulation workflow

Use two or three sentences describing how the model is run and what the workflow produces.

- State the simulation method and essential duration/phase structure.
- Mention network generation, equilibration, stimulus changes, scans, continuation, exports, or bounded stoichiometry only when active.
- Explain the execution order when it affects interpretation.
- Do not list or paste action commands.
- Do not use reusable boilerplate; describe this model's actual workflow.

### 9. Technical caveats and ambiguities

Use a short model-specific list or paragraph. Include only caveats that materially affect interpretation or execution, such as:

- ambiguous abbreviations or conflicting local metadata;
- abstract or lumped species that should not be overinterpreted;
- missing molecule-type declarations;
- pattern-match versus unique-complex counting;
- parser-sensitive syntax or unsupported extensions;
- bounded networks or commented-out rule families that alter scope;
- arbitrary/tutorial rate choices;
- uncertain biological mapping explicitly present in local files.

Do not add generic caveats that could be attached to any BNGL model.

## Anti-Clutter and Anti-Boilerplate Rules

- Never paste a parameter, species, rule, observable, function, or action block.
- Do not include source paths in the generated summary.
- Do not repeat the same interpretation across multiple rule rows.
- Do not make every row follow the same empty sentence template.
- Do not create long prose paragraphs when a grouped table is clearer.
- Do not create a table merely to restate syntax.
- Prefer fewer, information-rich rows over exhaustive repetition, while explicitly accounting for all active rules and observables.
- Preserve technical precision through names of molecules, sites, states, directions, and meaningful rate logic—not through copied code.

## JSON Index Requirements

Create or update a JSON index only when requested. Use fields such as:

```json
{
  "model_id": "...",
  "title": "...",
  "bngl_path": "...",
  "yaml_path": "...",
  "markdown_path": "...",
  "audience": "technical",
  "summary": "...",
  "molecule_type_count": 0,
  "reaction_rule_count": 0,
  "reaction_rule_group_count": 0,
  "observable_count": 0,
  "uses_anchors": false,
  "anchor_count": 0,
  "key_constructs": ["..."],
  "all_active_rules_accounted_for": true
}
```

Keep the JSON summary short. Do not duplicate Markdown tables in JSON.

## Quality Checklist

Before finalizing, verify:

- The explanation is based only on the target model's local BNGL, same-directory YAML, and nearby local notes.
- The title begins `Detailed Model Explanation`, not `Coder Model Explanation`.
- Section 1 is about two interpretive sentences and contains no source listing.
- Section 2 is concise and its counts match active BNGL content.
- Section 3 groups parameters by model-specific function, explains rate-law style, and explains every active function without copied declarations.
- Section 4 accounts for every molecule type, component, repeated site, state, and anchor using the required six-column table.
- Section 5 explains spatial setup and important initial pools without dumping seeds.
- Section 6 uses the required five columns, contains no full BNGL rules, and accounts for every active rule individually or through an explicit, justified group.
- Every rule row names the true molecules/sites, exact verbal edit, direction, meaningful rate logic, and model-specific role.
- Grouped rules explicitly identify all rule numbers and all varying sites/states/occupancies.
- Section 7 accounts for every active observable and explains its type and interpretation without copied patterns.
- Section 8 is a two- or three-sentence account of the actual execution workflow.
- Section 9 contains only model-specific caveats.
- No section contains reusable boilerplate, copied source blocks, generic fallback language, or unnecessary provenance.
