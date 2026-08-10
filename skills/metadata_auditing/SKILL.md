---
name: metadata-auditing
description: Audit RuleHub BNGL feature and citation metadata. Use when checking one or more model directories or same-directory BNGL/YAML pairs, creating source-derived *_metadata_aigenerated.yaml files, and writing a concise Markdown audit under data/.
---

# Audit RuleHub metadata

Produce both deliverables for every audit:

1. One concise Markdown report under `data/`.
2. One source-derived `*_metadata_aigenerated.yaml` for every auditable BNGL/YAML pair.

Never overwrite a source YAML. Permit a report-only result only when a directory cannot be audited because its BNGL or source YAML is missing, and report that blockage explicitly.

## Follow the schema

Treat the repository-root `metadata-schema.yaml` as authoritative for section placement, field names, types, enum values, and formatting. Read it before editing metadata and consult it whenever uncertain. Do not relocate schema fields based on existing files that use an older layout.

This workflow audits `features` and `citation`, not compatibility support. Preserve `compatibility` unchanged. Do not audit or infer `citation.doi`; preserve an existing DOI unchanged.

## Process models independently

Audit one model completely before starting the next:

1. Record the exact folder, BNGL file, source YAML, and model identifier.
2. Collect evidence only for that model.
3. Resolve its features and citation, compare its original citation, write its generated YAML, and draft its report section.
4. Clear the prior model's candidate papers, identifiers, PMID, rationale, and notes before opening the next model.

Never reuse a citation because two folders share an author or year. Disambiguate similar identifiers exactly—for example, treat `BaruaBCR2012` and `BaruaFceRI2012` as separate models and independently follow each model's own listing and paper link. Before accepting a paper, verify that its title, model name, pathway, or distinctive model content matches the current folder; a generic author/year match is insufficient.

## Select inputs and name outputs

Pair each `.bngl` file with metadata from the same directory; never inherit metadata from another directory. Choose the source YAML in this order:

1. A file named by the user.
2. The model-specific `*_metadata.yaml` supplied by a collaborator (for example, `An_2009_metadata.yaml` for `An2009`).

Do not use `metadata.yaml` or any `*_aigenerated.yaml` as a source. Do not count generated files as candidates. If several candidates remain at the same priority, do not choose silently; report the ambiguity and identify the files requiring confirmation.

Append `_aigenerated` to the selected source stem:

```text
An_2009_metadata.yaml -> An_2009_metadata_aigenerated.yaml
```

The output must remain in the source YAML's directory and must reveal which source it copies.

## Audit feature fields

Audit these fields under top-level `features:` exactly as defined by `metadata-schema.yaml`:

```yaml
features:
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
  default_sim_command: ode | ssa | nf | pla | hybrid | molclustpy | vcell
```

Never write these fields under `compatibility`. If `features:` is absent, create it. If audited feature keys incorrectly exist under `compatibility`, do not duplicate them there; write the audited values under `features` and report the legacy placement for review.

### Preprocess active BNGL content

- Inspect the complete BNGL file; do not infer features from metadata, filenames, or tags.
- Ignore blank lines and full-line comments.
- Strip trailing comments before analyzing a line.
- Ignore commented-out blocks, entries, rules, observables, actions, and modifiers.
- Treat a block entry as active only when it is uncommented and nonempty between matching `begin` and `end` lines.
- Do not count block delimiters as entries.

### Detect compartment grammar

Set compartment booleans from active species-pattern syntax, not merely from a `begin compartments` block:

- `uses_vcell_compartments: true` for active prefix syntax: `@Compartment:Molecule(...)`.
- `uses_cbngl_compartments: true` for active suffix syntax: `Molecule(...)@Compartment`.
- Set both to `true` if both syntaxes occur; otherwise set each absent syntax to `false`.

Do not confuse suffixes with molecule-site state or bond syntax. A compartment declaration alone proves neither pattern grammar.

### Detect block and construct features

Require at least one active entry; empty or comment-only blocks are false:

- `uses_functions`: entry inside `begin functions`.
- `uses_anchors`: entry inside `begin anchors`.
- `uses_energy`: entry inside an energy-pattern block.
- `uses_moveconnected`: `moveConnected` call.
- `uses_trash_molecules`: `Trash(...)` molecule or sink pattern.
- `uses_multiple_identical_sites`: repeated component name in one molecule-type declaration, such as `L(r,r)`.
- `uses_deletes_molecules`: `DeleteMolecules` modifier or action.
- `uses_exclude_include_reactants`: `include_reactants` or `exclude_reactants` modifier.
- `uses_generate_network`: `generate_network(...)` action.

Match complete identifiers case-sensitively where BNGL syntax is case-sensitive. Do not treat comments or similarly named identifiers as evidence.

### Detect the default simulation command

Use the first active simulation action, but store the schema enum value rather than the BNGL function name:

- `simulate_ode(...)` -> `ode`
- `simulate_ssa(...)` -> `ssa`
- `simulate_nf(...)` -> `nf`
- other supported actions -> the corresponding `metadata-schema.yaml` enum

Do not write `simulate`, `simulate_ode`, or another function name into `default_sim_command`. If a generic `simulate(...)` does not establish one supported method, preserve a valid source value or leave the field unset as the schema permits, and report the ambiguity.

Mark a value ambiguous only after rechecking the relevant active syntax. Do not use ambiguity as a substitute for inspecting the model.

## Audit citations

Every generated YAML must contain or update:

```yaml
citation:
  year: "YYYY"
  pmid: "PubMed ID"
  # Use url instead of pmid only when no PMID can be established.
  reference: "Author, Year"
```

Follow the reference formats in `metadata-schema.yaml`: `Author, Year` for one author, `Author & Author, Year` for two, and `Author et al., Year` for three or more. Require a four-digit `year`, a `reference`, and either `pmid` or `url`. Prefer `pmid` and store digits only. Use an article-specific journal, preprint, or website URL only if no PMID can be established. Ignore DOI for audit purposes and preserve it unchanged.

### Establish citation evidence in strict order

Use these sources in order and stop at the first source that identifies the model's paper reliably. Record only that highest-priority successful source in the rationale; do not write combined boilerplate such as “BNGLViz/BioNetGen listings.”

1. **BNGLViz examples:** Open [BNGLViz examples](https://bnglviz.github.io/examples.html), match the exact model/folder identity, and follow its outbound paper link.
2. **BioNetGen applications:** Use [BioNetGen applications](https://bionetgen.org/applications) only if BNGLViz does not reliably identify the paper, then follow its outbound paper link.
3. **Same-directory evidence:** Inspect the BNGL header, `README.md`, and other descriptive files. Inspect a potentially relevant RTF, PDF, text, or similar artifact before moving on, and name the decisive artifact in the rationale.
4. **Independent literature search:** Search PubMed or the web only when the first three sources do not identify a paper, or when their reliable paper URL does not supply a PMID. Treat author/year-only search matches cautiously and verify the paper against model-specific content.

Do not take shortcuts from a similar model, shared author, broad pathway, or search snippet. Open the actual listing link or paper record and check the title/authors before writing the reference. If both BNGLViz and BioNetGen list a model, use BNGLViz alone as provenance. If BNGLViz identifies the paper and links directly to PubMed, take the PMID from that link and say so plainly.

### Resolve PMID and warnings

- If the decisive listing links to PubMed, use that PMID. Rationale example: “PMID taken from the PubMed link on the BNGLViz entry for `BaruaBCR_2012`.”
- If the decisive source identifies an exact paper but links elsewhere, search PubMed by its exact title and authors. A matching PubMed result is corroboration of established source evidence and does **not** require a warning merely because PubMed was searched.
- If the BNGL header or another same-directory artifact identifies the exact paper, a matching PMID found from that title does **not** require a warning; state both the local evidence and PubMed provenance succinctly.
- If steps 1–3 fail and an independent search supplies the candidate paper, label the reference and PMID as low-confidence guesses requiring review and explain the model-specific match.
- If no PMID exists or can be established, write the best article-specific `url`, include the source link and a linked PubMed title/author search in the report, and warn that the PMID is unresolved.

Never invent a PMID or claim a paper discusses a model feature without checking the paper record. A URL is a fallback, not a reason to skip PubMed.

### Compare against the original citation

First establish the audited citation independently using the sequence above. Then inspect the selected original model-specific YAML's `citation:` mapping, if present, and compare its `reference` and `pmid` with the audited values.

- Report whether each present original value agrees.
- Report every mismatch explicitly, showing `original -> audited` and the evidence supporting the audited value.
- Treat a mismatch as requiring review; do not silently preserve or overwrite it.
- If the source YAML has no `citation:` mapping, skip this comparison.
- If only one of `reference` or `pmid` exists, compare that value and audit the missing field normally.

The original YAML is comparison evidence, not authority and not a substitute for the ordered source search.

### Write citation rationales

Report the value and provenance for every audited citation. The year needs no separate rationale beyond its source. Give PMID, URL, and reference separate, short, model-specific rationales:

- Name exactly one decisive source—the highest-priority successful source.
- For the reference, state how that source identifies this exact model/paper.
- For the PMID, state where the identifier came from; do not repeat the reference rationale.
- Add one brief corroborating detail only when needed to disambiguate the model.
- Never use generic claims such as “the record matches the model” without naming the identifying title, model ID, pathway, or distinctive content actually checked.

## Add contributors

Ensure every generated YAML contains this schema-compliant top-level list:

```yaml
contributors:
  - name: Vishnu Mukku
  - name: Codex
```

If `contributors` already exists, preserve unrelated contributors and add any missing required names without duplication. `Vishnu Mukku` identifies the person running these audits; `Codex` identifies the auditing/generating agent.

## Create generated YAML

Copy the selected source to the derived same-directory output, then:

- write every detected feature under exactly one top-level `features` mapping;
- write required citation values under exactly one top-level `citation` mapping;
- add the required contributors;
- insert missing false feature values without requesting review;
- flag inserted true values, changes to existing values, and genuine ambiguities for review;
- preserve all unaudited identity, compatibility, source, playground, DOI, contributors, ordering, quoting, and formatting as closely as practical.

Treat a missing boolean as effectively false when deciding whether review is needed, but still write every audited boolean explicitly. Validate the completed YAML and confirm each audited key occurs once.

## Write the audit report

Start with a compact summary:

```markdown
# <Audit title>

Audited <N> models and created <N> `*_metadata_aigenerated.yaml` files. Inserted <N> missing values; <N> items require review.
```

Add one heading per model and keep all its information together:

```markdown
## ModelName

- Inserted false: `field_a`, `field_b`.
- Review insertion: `field_c: true` — <short active BNGL evidence>.
- Review change: `field_d: true` -> `false` — <short active BNGL evidence>.
- Review ambiguity: `field_e` — <what remains unclear>.
- Citation year: `YYYY`.
- Citation reference: `<reference>` — <one decisive source and exact model-paper match>.
- Citation PMID: `12345678` — <where PMID came from>; [PubMed](https://pubmed.ncbi.nlm.nih.gov/12345678/).
- Citation comparison: original `reference` and `pmid` agree with the audited values.
- Citation mismatch: `pmid`: `<original>` -> `<audited>` — <audited evidence>; **review required**.
- Citation URL: [source](<URL>) — <source and match>; **warning: PMID unresolved**; [PubMed search](<query URL>).
```

Omit bullet types that do not apply. Group routine false insertions. Give each inserted true, changed value, ambiguity, citation mismatch, or low-confidence citation one short review bullet. Always include concise citation provenance, but do not count routine high-confidence citation evidence as review. Do not include tables, pairing lists, unchanged feature values, evidence dumps, or generic boilerplate. Mention source selection only when ambiguous.

## Verify

Before finishing, confirm:

- each model was processed independently and similar model names were not conflated;
- every audited model has a same-directory output derived from its selected `*_metadata.yaml`;
- no `metadata.yaml` or generated YAML was used as a source;
- every feature field is under `features`, occurs once, and agrees with active BNGL content;
- no audited feature was added under `compatibility`;
- `default_sim_command` uses a current schema enum value;
- every generated YAML has the required contributors;
- every generated YAML has a four-digit citation year, formatted reference, and either a digits-only PMID or working fallback URL;
- each citation uses the highest-priority successful source and has non-boilerplate rationales;
- source-YAML `reference` and `pmid` values were compared when its `citation` mapping existed, and every mismatch is reported;
- unresolved or independently guessed citations are warned and counted for review, while source-established PubMed lookups are not falsely warned;
- source YAML files remain unchanged;
- report totals match generated files, insertions, and review bullets.
