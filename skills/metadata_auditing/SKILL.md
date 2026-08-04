---
name: metadata-auditing
description: Audit RuleHub BNGL feature, citation, and collection metadata. Use when checking one or more model directories or same-directory BNGL/YAML pairs; select collaborator-curated YAML first, create source-derived *_aigenerated.yaml copies, and write a brief Markdown audit under data/.
---

# Audit RuleHub metadata

Produce both deliverables for every audit:

1. One brief Markdown report under `data/`.
2. One source-derived `*_aigenerated.yaml` for every auditable BNGL/YAML pair.

Never overwrite a source YAML. A report-only result is allowed only for a directory that cannot be audited because its BNGL or source YAML is missing; report that blockage explicitly.

## Select inputs

Use local files for model pairing and BNGL feature analysis. Citation lookup may use the internet as described below. Pair each `.bngl` file with metadata from the same directory; never inherit metadata from another directory.

Choose the source YAML in this order:

1. A file named by the user.
2. The model-specific `*_metadata.yaml` supplied by a collaborator (e.g., `An_2009_metadata.yaml` for the An2009 folder).
3. `metadata.yaml`.

The collaborator-curated model-specific file takes precedence over `metadata.yaml` whenever both exist. Do not use any `*_aigenerated.yaml` as a source or count it as a source YAML. If several candidates remain at the same priority, do not choose silently; note the ambiguity in the report and identify the files requiring confirmation.

Name the generated copy from the selected source name:

- `metadata.yaml` → `metadata_aigenerated.yaml`
- `*_metadata.yaml` → `*_metadata_aigenerated.yaml` (e.g., `An_2009_metadata.yaml` → `An_2009_metadata_aigenerated.yaml`)

For a collaborator-curated `*_metadata.yaml`, append `_aigenerated` to the part of the file name preceding the `.yaml`, as shown above. Do not force every output to be named `metadata_aigenerated.yaml`; the output name must reveal which source YAML it copies.

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

Also audit the top-level `citation:` mappings as specified below. Do not audit or infer `citation.doi` in this workflow; preserve an existing DOI unchanged.

## Audit citations

Every generated YAML must contain or update:

```yaml
citation:
  year: "YYYY"
  pmid: "PubMed ID"
  # Use url instead of pmid only when no PMID can be established.
  reference: "Author et al., Journal, Year, Volume, Pages"
```

Require a four-digit `year`, a `reference`, and either `pmid` or `url`. Prefer `pmid`; store only the identifier, not a PubMed link. Store a journal, preprint, or website link in `url` only when a PMID remains unavailable. Do not add, update, or remove `doi` during this audit.

Verify existing citation values with the same process; do not treat a pre-existing `citation` mapping as authoritative. Insert missing required fields and update incorrect ones. When a PMID is established, populate `pmid`; a verified existing URL may remain as supplemental metadata.

### Find citation evidence

Use the following sources in strict order. Stop when a model-to-paper match and all required citation values are adequately supported; otherwise continue to the next source.

1. Open [BNGLViz examples](https://bnglviz.github.io/examples.html). Match the model's name/year or folder name to a listed paper, then open links within the page to obtain the year, PMID or URL, and full reference.
2. Open [BioNetGen applications](https://bionetgen.org/applications). Apply the same name/year matching and follow the page's paper links.
3. Inspect same-directory `README.md` and other descriptive files. If an RTF, PDF, text file, or similar artifact may contain citation data, name that artifact in the report and inspect it before proceeding.
4. Only when the first three sources fail, infer a candidate reference from the model name, year, title, pathway, molecule names, and source comments. Clearly label this as a low-confidence guess requiring review.

Internet access is allowed and expected for steps 1, 2, and unresolved PubMed searches. Do not stop at a listing page when its outbound paper, journal, or PubMed links can establish the citation.

### Handle missing PubMed IDs

When a matched source provides a paper URL but no PMID:

1. Add a warning to the audit report.
2. Search PubMed by title, authors, journal, and year.
3. If found, write `pmid` and include a clickable PubMed link in the report.
4. If still unresolved, write the source `url`, retain the warning, include both the source link and a linked PubMed title/author search in the report, and explicitly request PMID review.

Never invent a PMID. A URL is a fallback, not a reason to skip the PubMed search.

### Report citation rationale

Report the value and evidence for every audited citation. The year needs no separate rationale beyond its source. PMID, URL, and reference each require a short model-specific justification that states:

- where the value came from
- how the model was matched to the paper (for example, folder/model name and year)
- brief corroborating detail(s) when needed, such as a paper title naming the pathway or a paper/model sharing a distinctive molecule.

Keep each rationale to one sentence. A useful level of detail is: “BioNetGen applications lists `Lin_2009`; its paper title concerns ERK, which is also a named molecule in the matched model.” Do not use generic statements.

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

For every auditable pair, copy the selected source metadata to the same-directory output name derived under **Select inputs**, then set every detected compatibility field, required citation field, and supported collection field to its audited value. If `compatibility:` or `citation:` is absent, create it.

- Insert missing false values without requesting review.
- Insert missing true values and flag them for review.
- Apply any change to an existing value and flag it for review.
- If detection is genuinely ambiguous, preserve the source value when present; otherwise use `null` only where the schema permits it. Flag the ambiguity for review.
- Preserve all unaudited content, ordering, quoting, and structure as closely as practical.

Treat a missing boolean as effectively false when deciding whether review is needed, but still write the explicit detected boolean to the generated YAML.

Preserve identity, source, playground, DOI, and all other unaudited metadata. Keep the source file's ordering, quoting, and formatting as closely as practical. Validate the completed YAML and ensure it contains only one mapping for each of `compatibility`, `citation`, and `collection` and one instance of each audited key.

## Write the brief audit

Use a descriptive filename under `data/`. Keep the report focused on what a programmer must review. Do not include detection definitions, pairing lists, tables, block diagnostics, compartment examples, unchanged values, or evidence dumps.

Start with only a compact batch summary:

```markdown
# <Audit title>

Audited <N> models and created <N> `*_aigenerated.yaml` files. Inserted <N> missing values; <N> items require review; <N> directories were blocked.
```

Then add one heading per model. Keep all information for that model under its heading:

```markdown
## ModelName

- Inserted false: `field_a`, `field_b`.
- Review insertion: `field_c: true` — <short evidence>.
- Review change: `field_d: true` → `false` — <short evidence>.
- Review ambiguity: `field_e` — <what is unclear>.
- Citation year: `YYYY`.
- Citation PMID: `12345678` — <source and model-to-paper match>; [PubMed](https://pubmed.ncbi.nlm.nih.gov/12345678/).
- Citation URL: [source](<URL>) — <source and model-to-paper match>; **warning: PMID unresolved**; [PubMed search](<query URL>).
- Citation reference: `<reference>` — <source and model-to-paper match>.
- Collection insertion: `count: N` — directory contains N BNGL files; <classification evidence or review warning>.
- Blocking warning: <missing BNGL/source YAML or unresolved pairing>.
```

Apply these brevity rules:

- Omit any bullet type that does not apply.
- Group all routine false insertions into one bullet.
- Give each inserted true, changed value, or ambiguity one short review bullet.
- Include an active-entry count only when it directly explains a reviewed anchors/functions/energy decision.
- If a model has no compatibility/collection changes or warnings beyond its required citation bullets, omit `- No review required.`; the citation bullets already document the completed audit.
- Do not explain that missing fields imply false.
- Mention the source YAML only when its selection is ambiguous or otherwise requires review.
- Always include the concise citation bullets; citation provenance is not an evidence dump.
- Use a `Citation URL` bullet instead of `Citation PMID` only after the required PubMed search fails, and include the missing-PMID warning in that bullet.
- Include collection and blocking bullets only when they apply.

## Verify

Before finishing, confirm:

- every auditable pair or collection has its same-directory source-derived `*_aigenerated.yaml`;
- every generated filename is derived from the selected source YAML stem;
- every boolean audit field is present and agrees with active BNGL content;
- `default_sim_command` agrees with the active command when one is detected;
- every generated YAML contains a four-digit citation year, a reference, and either PMID or fallback URL;
- every PMID contains only digits and every URL is a working link;
- every citation PMID/URL/reference has a concise source-and-match rationale in the report;
- every source that lacked a PMID has a warning; a resolved PMID has a direct PubMed link, while an unresolved PMID has both a linked PubMed search and the fallback source URL in the report;
- every multi-BNGL/single-source-YAML directory has a reported collection insertion with the correct BNGL count;
- missing-BNGL, missing-source-YAML, ambiguous pairing, and unpaired-file cases are reported and excluded from completed-audit totals;
- source YAML files remain unchanged;
- report totals match the generated files and reported bullets;
- review totals count inserted true compatibility values, changes to existing values, low-confidence or unresolved citation evidence, collection uncertainties, warnings, and ambiguities; routine high-confidence citation evidence is reported but not counted as requiring review;
- the report contains no tables or diagnostic sections.
