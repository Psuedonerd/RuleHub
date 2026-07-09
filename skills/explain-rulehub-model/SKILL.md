# Explain RuleHub Model

## Purpose

Use this skill to generate a plain-English, biologically meaningful Markdown summary of an existing RuleHub BNGL model and its YAML metadata. The target reader is a biologist, curator, student, or domain scientist who may understand the biological system but does not know BNGL syntax or rule-based modeling.

The summary must explain what the model is trying to represent, what the major molecules are, what their binding sites or internal states mean, and what each reaction rule says in ordinary biological language.

This skill is for explanation only, and necessitates easily understandable yet comprehensive explanations free of jargon and syntax. It does not judge whether the model is biologically correct, verify simulation results, or add unsupported mechanistic claims.

## Required Inputs

Use all available repository files for the model, especially:

1. The model `.bngl` file.
2. The model `metadata.yaml` or `.yaml` file.
3. Any local `README.md`, comments in the BNGL file, citations, PubMed IDs, source URLs, visualization links, simulation links, or category metadata.

If multiple BNGL or YAML files are present, identify which files you used and state any ambiguity.

## Core Obligations

The generated explanation must do all of the following:

- Explain the biological purpose of the model in plain English.
- Explain the main molecules in plain English, not only by listing BNGL symbols.
- Explain sites, bonds, compartments, and internal states in plain English whenever they appear.
- Explain every important reaction rule as a biological event, not as raw code.
- Translate BNGL bond notation into words. For example:
  - `!0`, `!1`, and similar labels mean that the marked sites are connected by the same bond.
  - `A(a!0).B(b!0)` means molecule `A` is bound at site `a` to molecule `B` at site `b`.
  - `A(a) + B(b) -> A(a!0).B(b!0)` means molecule A binds molecule B.
  - `A(a!0).B(b!0) -> A(a) + B(b)` means the complex dissociates.
  - `A(a) + B(b) <-> A(a!0).B(b!0) kf, kr` means the binding is reversible, with the forward association rate given by `kf` and the reverse dissociation rate given by `kr`.
- Mention rate parameters in words when they are attached to reaction rules.
- Explain observables as measurements: what is counted or tracked during simulation.
- Explain likely simulation behavior only as a cautious interpretation based on the model structure and observables.
- Clearly flag uncertainty, missing metadata, unclear biological identities, or rule meanings that cannot be inferred from the files. However, do not inject uncertainty into explanations if the behavior is certain or mentioning of uncertainty would cloud overall meaning.

## What Not To Do

Do not:

- Output only a syntactic paraphrase of BNGL code.
- Leave reaction rules unexplained because they look repetitive or technical.
- Assume readers know what BNGL terms such as seed species, observables, molecule types, components, internal states, or bonds mean.
- Invent biological roles, pathways, cell types, organisms, experimental results, or literature context that are not present in the model files or metadata.
- Claim that a simulation will definitely show a result unless that result is explicitly encoded or documented.
- Over-focus on file logistics at the expense of explaining the model biology.
- Dump raw BNGL blocks unless a short quoted fragment is necessary to disambiguate a rule.

## BNGL Interpretation Guide

When reading the BNGL file, interpret the following constructs before writing the explanation.

### Molecule types

Molecule type declarations define the kinds of molecular objects in the model and the sites or states they can have.

Explain each major molecule as follows:

- State the BNGL name.
- Give the likely biological meaning if metadata, comments, or naming make it clear.
- Describe each important site in plain English.
- Describe internal states in words. For example, `Y~U~P` may mean a tyrosine site can be unphosphorylated (`U`) or phosphorylated (`P`) if the file or naming supports that interpretation.
- If a name or state is ambiguous, say so rather than guessing.

### Seed species

Seed species define the model's initial molecular population or starting condition.

Explain seed species as the starting mixture, such as free receptors, ligands, enzymes, substrates, complexes, or molecules in specific modification states. Include initial amounts when they help the reader understand what the model starts with.

### Bonds and complexes

BNGL uses matching bond labels to show connected sites. Explain this explicitly when complexes appear.

Use language like:

- "The `!0` labels indicate that these two sites are connected by the same bond."
- "This pattern represents A bound through its `a` site to B through its `b` site."
- "A missing bond label means the site is free in this pattern."
- "A site with `!?` or wildcard-style notation can match a bound site without specifying the exact partner, if such notation appears."

### Reaction rules

Reaction rules describe classes of biochemical events. For each important rule or rule family, explain:

1. The rule name, if present.
2. The reactants in biological words.
3. The products in biological words.
4. Whether the rule is binding, unbinding, reversible binding, phosphorylation, dephosphorylation, synthesis, degradation, transport, conformational/state change, catalysis, complex assembly, or another event type.
5. Which sites, states, or bonds change.
6. Which rate parameter controls the event.
7. Whether the rule applies to a specific molecule state or a family of matching molecular patterns.

Preferred style for binding rules:

- "Molecule A binds molecule B: A uses site `a`, B uses site `b`, and the shared `!0` bond label indicates that those two sites become connected. The forward association rate is `k1`; the reverse dissociation rate is `k2` if the rule is reversible."

Preferred style for modification rules:

- "Enzyme E changes substrate S at site `y` from state `U` to state `P`, which likely represents phosphorylation if supported by the names or comments. This event occurs with rate `kp`."

If a model contains many highly repetitive rules, group obvious rule families, but still explain the biological event represented by each family and list the rule names or patterns included in that family.

### Observables

Observables define what the simulation records.

For each observable, explain:

- The observable name.
- Whether it counts molecules, species, complexes, states, or patterns.
- The biological quantity it approximates, such as free ligand, bound receptor, phosphorylated protein, active complex, degraded product, or total molecule amount.
- Any caveat about pattern matching if the observable may include multiple complexes or states.

### Actions and simulations

If the BNGL file contains actions such as network generation or simulation commands, explain them briefly:

- State whether the model appears intended for deterministic, stochastic, network-free, or other simulation modes when this is clear from the actions.
- State what outputs would likely be plotted based on the observables.
- Do not overinterpret numerical trajectories without actual simulation results.

## Workflow

1. Read the YAML metadata before the BNGL file.
2. Record the title, model name, category, source/reference, PubMed ID, author/provenance, compatibility fields, and links if present.
3. Read comments in the BNGL file because they often define abbreviations, biological context, or rule intent.
4. Parse the BNGL blocks in this order:
   - `parameters`
   - `molecule types`
   - `seed species`
   - `observables`
   - `reaction rules`
   - `functions`, compartments, energy patterns, population maps, or actions if present
5. Build a small glossary that maps BNGL symbols to biological names when possible.
6. Translate reaction rules into verbal biological events using the BNGL interpretation guide above.
7. Write the explanation in the required Markdown format.
8. Re-check the final answer against the BNGL file to ensure that important molecules, rules, observables, and caveats were not omitted.

## Output Format

Return one Markdown document suitable for saving as an automated RuleHub model summary. Most likely, the author name and year will be known, so name the file {Author Name}_{Year Created}_aigenerated.md. If prompted by the user, add to a JSON file, fixing the requisite information in said file.

Use exactly this top-level structure:

```markdown
# Model Explanation: <model title or BNGL file name>

## 1. One-sentence summary

## 2. Biological meaning

## 3. Main molecules, sites, and states

## 4. Initial conditions and model setup

## 5. Reaction rules in plain English

## 6. Observables and expected simulation output

## 7. Metadata, source, and compatibility

## 8. Caveats or missing information
```

## Section Requirements

### 1. One-sentence summary

Give one clear sentence describing the model's biological focus and main process.

### 2. Biological meaning

Explain what biological system or mechanism the model represents. Use the metadata, comments, and molecule names. If the biological context is sparse, say what can be inferred and what cannot.

### 3. Main molecules, sites, and states

Use bullets or a table. For each major molecule, include:

- BNGL name.
- Plain-English identity or likely role.
- Important sites/components.
- Important internal states.
- How the molecule participates in bonds or reactions.

Define BNGL notation here in beginner-friendly terms when it first appears. Include a short explanation that matching `!0`, `!1`, etc. labels mark sites that are connected by a bond.

### 4. Initial conditions and model setup

Summarize the seed species and starting amounts in plain English. Explain whether molecules start free, bound, modified, unmodified, active, inactive, inside a compartment, or otherwise configured, if this is encoded.

### 5. Reaction rules in plain English

This is the most important section. Explain the model's reaction rules as biological events.

Use one bullet per rule or per clearly defined rule family. Each bullet should include:

- Rule name, if present.
- Plain-English event description.
- Sites/states/bonds that change.
- Rate parameter names and what they control.
- Reversibility, if present.

Example wording:

- "`bind_AB`: Molecule A binds molecule B. A uses site `a`, B uses site `b`, and the shared `!0` label means those two sites are connected in the complex. This interaction is reversible: `k_on` controls formation of the complex, while `k_off` controls dissociation back into free A and free B."

### 6. Observables and expected simulation output

Explain every observable in plain English. Then briefly describe what simulation plots would show, based only on the observables and rules.

### 7. Metadata, source, and compatibility

Summarize title, category, source/reference, PubMed ID, author/provenance, compatibility, and relevant links when present. State when fields are missing.

### 8. Caveats or missing information

List limitations, ambiguities, missing metadata, unclear molecule identities, unexplained parameters, or assumptions made during interpretation.

## Style Requirements

- Write for biologists, not BNGL experts.
- Use short paragraphs and concrete verbs such as binds, releases, phosphorylates, dephosphorylates, activates, inactivates, synthesizes, degrades, transports, or changes state.
- Keep BNGL names visible in backticks so readers can connect the explanation to the source model.
- Define technical terms briefly the first time they appear.
- Prefer "likely represents" or "appears to represent" when inferring from names.
- Be specific about rates: say which parameter controls which direction or event whenever the rule provides that information.
- Be complete but concise enough for automated summaries across many RuleHub models.
