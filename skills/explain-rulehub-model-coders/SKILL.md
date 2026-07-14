---
name: explain-rulehub-model-coders
description: Generate technical RuleHub BNGL/YAML model explanations for experienced coders, modelers, and curators. Use when asked to create or review coder-facing summaries with complete molecule type/site/state inventories, every BNGL reaction rule, parameters, functions, observables, compartments, anchors, actions, source paths, or JSON index entries for RuleHub models.
---

# Explain RuleHub Model for Coders

## Purpose

Use this skill to write a technical, coder-facing Markdown explanation of a RuleHub BNGL model and its same-directory metadata. The reader already understands code and modeling concepts, but still needs a careful map from BNGL constructs to model behavior.

This skill is not the biologist-facing summary style. It should expose BNGL-relevant structure, identify every molecule type and every reaction rule, and explain how the model is assembled without dumping unreadable code.

## Reset Rule: Treat Every Model as New

Before reading a model, deliberately discard assumptions from previous models and previous generated summaries.

- Do not assume an abbreviation has the same meaning in two models. For example, `Ca` may mean calcium in one model and a named abstract species in another unless the current metadata, comments, or molecule names establish it.
- Do not reuse paragraph templates, caveats, event descriptions, or interpretations from another summary.
- Do not infer organism, cell type, compartment, residue identity, experimental conclusion, or biological role unless this model's local files support it.
- If a name is abstract or ambiguous, say so in the technical caveats instead of inventing meaning.

## Required Inputs

Read local repository files only, in this order:

1. The same-directory `metadata.yaml` or `.yaml` file.
2. The target `.bngl` file.
3. Nearby same-directory `README.md`, notes, or comments if present.
4. BNGL comments, especially comments near molecule types, parameters, rules, observables, and actions.

When selecting or tabulating models, pair a `.bngl` file with a YAML file only when both files are in the same directory. Never count inherited ancestor metadata as a match. If one same-directory metadata file accompanies multiple same-directory `.bngl` files, each BNGL file may be a separate pair.

## BNGL Grammar-Aware Reading Guide

Use the BNGL grammar as a parsing checklist. Identify these constructs before writing:

- Model delimiters and blocks: `begin model`, `end model`, `begin parameters`, `begin compartments`, `begin anchors`, `begin molecule types`, `begin species` or `begin seed species`, `begin observables`, `begin functions`, `begin reaction rules`, and `begin actions`.
- Molecule patterns: molecule name, component/site list, internal states marked by state alternatives, binding markers, and optional compartments.
- Anchors: when a `begin anchors` block is present, record each molecule-to-compartment constraint such as `RCC1(nuc)` or `EGF(M,EC)`. Treat anchors as localization constraints on molecule types, not as reaction rules or binding sites.
- Components/sites: count every declared component in each molecule type; record repeated sites separately when the declaration repeats a component name.
- Internal states: record every state alternative for each site, including unmodified/modified, active/inactive, nucleotide-bound, or abstract states when declared.
- Bonds: interpret explicit bond labels, unspecified bonds, and “bound to something” patterns as binding constraints, not as molecule names.
- Reaction rules: distinguish unidirectional and reversible rules, rule labels, reactant patterns, product patterns, rate expressions, functions used as rates, and state/bond/component changes. For compartmental rules involving anchored molecules, explain whether product locations are constrained by the anchor declarations.
- Observables: distinguish molecule-count and species-count readouts, and explain each pattern being counted.
- Functions and actions: record algebraic functions, generated networks, simulations, scans, parameter changes, and output commands.

If a model uses extended constructs such as compartments, anchors, population maps, energy patterns, local functions, or conditional/structured syntax, add a parser note explaining how those constructs affect interpretation.

## Required Markdown Structure

Use this structure exactly unless the user requests a different format:

```markdown
# Coder Model Explanation: <title>

## 1. Model identity and scope

## 2. BNGL block inventory

## 3. Parameters, functions, and rate laws

## 4. Molecule types, sites, and states

## 5. Compartments, anchors, initial species, and setup

## 6. Complete reaction-rule inventory

## 7. Observables and technical readouts

## 8. Actions and simulation workflow

## 9. Technical caveats and ambiguities
```

### 1. Model identity and scope

Include the title, model id if available, biological or tutorial purpose, and the local source paths. Because this is coder-facing, file paths are allowed.

### 2. BNGL block inventory

List which BNGL blocks are present and what each block contributes. Include counts for parameters, compartments, anchors, molecule types, initial species, observables, functions, reaction rules, and actions when practical. If anchors are present, summarize their molecule-to-compartment constraints in this inventory.

### 3. Parameters, functions, and rate laws

Explain the parameter namespace and rate-law style.

- Include all parameters for small and medium models.
- For very large models, group parameters by role, but still mention any parameter directly used by a reaction rule, function, or action.
- Explain functions as executable model logic: what they compute, what variables they depend on, and where they are used.
- Do not describe a parameter as biologically meaningful unless comments, metadata, or its name support that interpretation.

### 4. Molecule types, sites, and states

This section must be exhaustive for molecule types. Include every declared molecule type relevant to the BNGL model.

Use a table with these columns when possible:

| Molecule type | Site count | Sites/components | Internal states | Anchor/allowed compartments | Binding/modification roles | Notes |
| --- | ---: | --- | --- | --- | --- | --- |

Rules for this section:

- Count every declared site/component in the molecule type.
- List every site name.
- List every declared internal state for each site.
- Identify apparent binding sites, modification sites, catalytic sites, localization sites, or abstract flags based only on the current model.
- If a molecule appears in the anchors block, include its anchor/allowed compartment(s) in the molecule table and use those constraints when explaining compartmental rules.
- If molecule types are absent and the model relies on species declarations only, say so and infer the effective players from species/rule patterns with a caution.

### 5. Compartments, anchors, initial species, and setup

Summarize spatial setup before initial species.

- Include compartment definitions and compartment placement if present.
- If an anchors block is present, list every anchored molecule and its allowed or constrained compartment(s). Explain that anchors constrain the localization of species or complexes containing that molecule.
- Include initial species names/patterns when needed to understand starting state.
- Explain initial abundance classes: ligand/receptor pools, enzymes, substrates, scaffolds, anchored membrane or nuclear molecules, compartments, abstract tutorial species, or zero-initialized outputs.
- Keep this concise; do not paste long species blocks verbatim.

### 6. Complete reaction-rule inventory

This section must cover every reaction rule in the BNGL file. Do not select only “key” rules.

Use a table or numbered list with one entry per rule. Each entry must include:

- Rule number and rule label/name if present.
- A short original rule reference or compact pattern summary when useful for coders.
- Direction: reversible or one-way.
- Participants and sites/components involved.
- Exact modeled change: binding, unbinding, state change, phosphorylation/dephosphorylation, synthesis, degradation, transport, catalysis, conformational switching, complex formation, or abstract transition.
- Rate parameter or rate expression.
- Plain-English technical meaning.

If a rule is generated by a repeated family or macro-like structure, still preserve one row per concrete rule in the file. You may group adjacent rows under a shared subheading only if every individual rule remains visible and explained.

### 7. Observables and technical readouts

Explain every observable/readout.

For each readout, include:

- Observable name.
- Observable type if clear, such as molecule count or species count.
- Pattern or target being counted, summarized compactly.
- Technical interpretation: what model state, complex, modification, population, or abstract quantity this readout reports.

### 8. Actions and simulation workflow

Explain every action block command or inline action command that affects execution.

Mention network generation, ODE/SSA/NFsim simulation, scans, parameter changes, output file generation, visualization commands, and continuation commands. Explain what a coder should expect the workflow to produce.

### 9. Technical caveats and ambiguities

Make caveats specific to this model. Examples:

- Ambiguous molecule abbreviations in this file.
- Rules with abstract species that should not be overinterpreted biologically.
- Missing molecule type declarations.
- Readouts that count pattern matches rather than unique complexes.
- Rate constants that appear tutorial-like or arbitrary.
- Large combinatorial rule families where generated species are not enumerated in the source.
- VCell-augmented compartment/anchor constructs that may not be supported by every standalone BioNetGen or NFsim workflow.

Do not use generic caveats that could apply to every BNGL model.

## JSON Index Requirements

When producing or appending to a JSON index, use coder-friendly fields such as:

```json
{
  "model_id": "...",
  "title": "...",
  "bngl_path": "...",
  "yaml_path": "...",
  "markdown_path": "...",
  "audience": "coders",
  "summary": "...",
  "molecule_type_count": 0,
  "reaction_rule_count": 0,
  "observable_count": 0,
  "uses_anchors": false,
  "anchor_count": 0,
  "key_constructs": ["..."],
  "rule_inventory_in_markdown": true
}
```

The JSON summary should be short and specific. The Markdown carries the full rule inventory; avoid duplicating long rule tables in JSON unless the user explicitly requests it.

## Quality Checklist

Before finalizing, verify all of the following:

- The explanation is based only on this model's local BNGL, same-directory YAML, and nearby local notes.
- Every declared molecule type appears in the molecule table.
- Every molecule type has a site count and a list of all declared sites/components.
- Every declared internal state is recorded.
- Every reaction rule in the BNGL reaction-rule block appears in the complete rule inventory.
- Every rule explanation states the participants, sites/components affected, direction, rate, and modeled change.
- Every observable/readout appears and is explained.
- Every function, compartment, anchor, and action is addressed if present.
- Ambiguous names are flagged rather than guessed.
- No section body is reusable boilerplate from another model.
- Counts in the Markdown match the BNGL blocks, including anchor count when an anchors block is present.
