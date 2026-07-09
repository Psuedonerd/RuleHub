# Explain RuleHub Model

## Purpose

Use this skill to write a polished, biologist-facing Markdown explanation of an existing RuleHub model. The reader is a biologist, curator, student, or domain scientist who wants to understand what the model *shows biologically*, not how BNGL syntax works.

The output must be a readable explanatory article. It should explain the biological story, the major players, the key modeled events, what the model measures, and the expected behavior of this specific model in plots. It must avoid exposing the reader to implementation details unless those details are needed for website integration outside the prose.

## Required Inputs

Before writing, read the model files in this order:

1. The model `metadata.yaml` or `.yaml` file.
2. The model `.bngl` file.
3. Any nearby `README.md` or other local documentation.
4. Comments inside the BNGL file, especially title, description, reference, pathway notes, reaction-family comments, and observable/readout comments.

Use local repository files only. Do not rely on raw GitHub URLs.

If more than one BNGL file is present for a model, choose the file that metadata identifies when possible. If the choice is ambiguous, resolve it before writing or record the chosen file only in machine-readable JSON, not in the biologist-facing prose.

## Core Writing Principle

Write what the model shows, not what the code says.

Good summary prose sounds like:

> This model shows how LPS is assembled with CD14 and MD2 before activating TLR4, how adaptor arms route the signal to TAK1 and IKK, and how A20 and IkB feedback restrain NF-kB-driven inflammatory output.

Bad summary prose sounds like:

> The local BNGL file has seed species, observables, and reaction rules where `TLR4(TRAM)` binds `TRIF`.

Never make the biologist wade through raw BNGL syntax, file logistics, implementation notes, or long rule lists.

## Strict Prohibitions for Markdown Summaries

Do **not** include any of the following in the Markdown prose:

- Raw BNGL patterns, such as molecule-site syntax, bond labels, state syntax, arrows, or rate expressions.
- Code fences containing model code.
- Long lists of every reaction rule.
- Phrases such as “local model,” “local metadata,” “BNGL file,” “YAML file,” “seed species,” “observables,” or “reaction rules.”
- File paths, unless the user explicitly asks for file-path documentation inside the Markdown. Paths belong in JSON, not the reader-facing summary.
- Generic filler such as “the model encodes molecular species, initial conditions, observables, and rules.”
- Unsupported biological claims, organisms, cell types, or experimental conclusions not implied by metadata, comments, molecule names, or local documentation.

The Markdown may use important molecule names, pathway names, protein names, ligand names, and biological state names. These names should be plain text, not raw syntax dumps.

## Required Markdown Structure

Use this structure exactly for each generated Markdown summary:

```markdown
# Model Explanation: <title>

## One-sentence summary

## What the model shows

## Biological story

## Main biological players

## Mechanism in plain English

## Key modeled events

## What the model measures

## Expected behavior in plots

## Caveats
```

### Section-by-section requirements

#### `# Model Explanation: <title>`

Use the clean model title from metadata when available. If metadata is sparse, use a readable title inferred from the directory or BNGL title comment.

#### `## One-sentence summary`

Write one specific sentence naming the biological process and the central modeled behavior. Avoid “uses BNGL,” “encodes,” or “contains.”

Good:

> Beta-catenin control by the Axin/APC/GSK3/CK1 destruction complex.

Bad:

> This model represents beta-catenin using BNGL rules.

#### `## What the model shows`

Write one paragraph explaining the model’s biological purpose. State the central mechanism and why the model is useful. This should be specific enough that a biologist can tell this model apart from another model in the same pathway.

#### `## Biological story`

Write a short conceptual paragraph that connects the model to a biological narrative: stimulus, assembly, modification, feedback, degradation, transport, gene expression, phenotype, or other response. Avoid implementation details.

#### `## Main biological players`

List the major molecules, complexes, variables, or pathway modules in readable biological language. Do not list every minor species. Do not include sites in BNGL syntax. It is acceptable to name important domains or residues in prose when biologically meaningful, such as SH2 domains, ITAMs, phosphorylation sites, or receptor arms.

#### `## Mechanism in plain English`

Explain the causal mechanism in one detailed paragraph. Use concrete verbs: binds, recruits, phosphorylates, dephosphorylates, activates, inhibits, releases, degrades, imports, exports, transcribes, translates, recycles, or dilutes.

This section should say what happens and why it matters. It must not be a raw rule translation.

#### `## Key modeled events`

Include exactly three to five bullets. Each bullet should describe one important modeled event or event family in plain English.

Rules for these bullets:

- Select only the most biologically important events.
- Prefer event families over exhaustive lists.
- Mention direction and consequence when clear.
- Mention important molecules by name.
- Do not include raw syntax, arrows, rate constants, or parameter names unless the parameter name is biologically meaningful to the reader.

Good:

- Beta-catenin binds APC and Axin, placing it into the destruction-complex environment.
- CK1 and GSK3 phosphorylate beta-catenin in sequence, converting it into a form that is removed more rapidly.
- When beta-catenin is degraded, APC and Axin partners are released so the scaffold can participate in another cycle.

Bad:

- `bCat(ARM34) + AXIN(b) <-> bCat(ARM34!1).AXIN(b!1)`.

#### `## What the model measures`

Describe the plotted or tracked biological quantities. Use “readouts” or “measurements,” not “observables.” Explain what a biologist would see: active kinase, phosphorylated substrate, receptor complex, transcriptional output, degraded product, clustered polymer, pathway activity, and so on.

#### `## Expected behavior in plots`

Write model-specific plot guidance. Do not use reusable boilerplate about rising or falling curves. Say which particular readouts should rise, fall, peak, lag, oppose each other, or remain abstract for this model, and why. Avoid promising a specific trajectory unless the model comments or mechanism support it.

#### `## Caveats`

State limitations briefly. Examples:

- The summary explains the encoded mechanism; it does not validate experimental correctness.
- Some molecule names are abstract, so identities are not invented.
- The model is a compact demonstration rather than a complete pathway model.

Do not use this section to discuss local files or implementation logistics.

## JSON Index Requirements

When the user asks for a JSON index, write a clean machine-readable file such as `data/ai_summaries.json`.

Each entry should include:

```json
{
  "model_id": "...",
  "title": "...",
  "bngl_path": "...",
  "yaml_path": "...",
  "markdown_path": "...",
  "summary": "...",
  "key_events": ["...", "...", "..."]
}
```

JSON may include file paths because it is for site integration. Markdown summaries should not include those paths unless explicitly requested.

The JSON `summary` should match the Markdown one-sentence summary. The JSON `key_events` should match the bullets in `## Key modeled events` or be a clean subset of them.

## Workflow

1. Read metadata first and record the clean title, id, category, source hints, and short description.
2. Read the BNGL comments before interpreting mechanisms; comments often contain the best biological description.
3. Identify the main biological players from molecule declarations, comments, and metadata tags.
4. Identify the central mechanism: binding/assembly, activation, modification, feedback, degradation, transport, transcription, or other biological process.
5. Identify three to five key modeled events. These should be selective and biologically meaningful, not exhaustive.
6. Identify the model readouts and translate them into biological measurements.
7. Write the Markdown in the required structure.
8. Review the Markdown and remove raw syntax, file-path prose, implementation jargon, and generic filler.
9. If producing JSON, verify every referenced Markdown path exists and every entry has the required fields.

## Same-directory Pairing Rule

When tabulating or selecting models, pair a `.bngl` file with a YAML file only when the `.bngl` and `metadata.yaml` are in the same directory. Do not count inherited ancestor metadata pairs. If a directory has one `metadata.yaml` and multiple `.bngl` files in that same directory, each `.bngl` may be treated as a same-directory BNGL/YAML pair. Nested subdirectory `.bngl` files require their own same-directory `metadata.yaml` to count.

## Anti-Boilerplate Requirements

Every generated Markdown file must be specific from top to bottom. Never copy a generic paragraph across models. In particular:

- `## Biological story` must name the specific model or pathway and describe its unique narrative.
- `## Expected behavior in plots` must name the model-specific readouts or behaviors to compare.
- `## Caveats` must identify the specific scope limitation of that model.
- Repeated stock phrases are allowed only for headings, not for section bodies.
- If two summaries have identical section-body text outside headings, rewrite them.

## Quality Checklist

Before finalizing, verify all of the following:

- The summary is specific to this model, not reusable generic text.
- The reader can understand what the model shows without knowing BNGL.
- The mechanism section contains biological verbs and causal flow.
- The key modeled events include a few important modeled events without becoming a full rule dump.
- The readouts section explains what plotted quantities mean biologically.
- The biological story, expected plot behavior, and caveats are unique to the model and not copied boilerplate.
- The Markdown contains no raw BNGL syntax, arrows, bond labels, file paths, or local-file logistics.
- The Markdown avoids the words “observables,” “seed species,” and “reaction rules.”
- The JSON is valid and points to existing Markdown files.
