# RuleHub Database Visibility Metadata

## Purpose

Set `compatibility.database_visible: false` for RuleHub model folders that
use only a generic `metadata.yaml` and do not have a model-specific
`NAME_metadata.yaml`.

These models are displayed by the RuleHub website with the `NO YAML!`
indicator because they do not have a model-specific metadata file. These models should have `compatibility.database_visible: false` so that they are excluded from the database-visible results while retaining their generic `metadata.yaml` for other RuleHub purposes.

## When to use this skill

Use this workflow when working on RuleHub model metadata and a model folder
contains:

- one or more `.bngl` files;
- a generic `metadata.yaml`; and
- no model-specific `NAME_metadata.yaml`.

The absence of a model-specific metadata file is the criterion for this
workflow. Do not use the number of BNGL files alone as the criterion.

For example:

    Published/ExampleModel/
    ├── model_a.bngl
    ├── model_b.bngl
    └── metadata.yaml

should be treated as a database-invisible model.

In contrast:

    Published/ExampleModel/
    ├── model_a.bngl
    ├── model_b.bngl
    └── ExampleModel_metadata.yaml

has model-specific metadata and should not be modified by this workflow
merely because it contains multiple BNGL files.

## Required change

For every qualifying `metadata.yaml`, ensure that it contains:

    compatibility:
      database_visible: false

If `compatibility.database_visible` already exists and is `true`, change it
to `false`.

If `compatibility.database_visible` is missing, add it with the value `false`.

If `compatibility` does not exist, create the `compatibility` mapping and add:

    compatibility:
      database_visible: false

Preserve all other metadata fields and values.

## Do not

- Do not delete `metadata.yaml`.
- Do not create a `NAME_metadata.yaml` merely to make the model database-visible.
- Do not modify BNGL files.
- Do not change the model's `id`, `name`, `description`, `tags`, `citation`, or any other metadata fields. The only permitted metadata change is adding or updating `compatibility.database_visible`.
- Do not change `database_visible` for a folder that has an appropriate
  model-specific `NAME_metadata.yaml`.
- Do not assume that having multiple BNGL files alone means that
  `database_visible` must be false.
- Do not modify `_aigenerated.yaml` files as part of this workflow.
- Do not remove or overwrite existing metadata unnecessarily.

## Identifying model-specific metadata

A model-specific metadata file is a `NAME_metadata.yaml` file located in the same model folder as the BNGL file(s), where `NAME` is something other than the literal `metadata`.

For example:

    Hlavacek2018Elephant_metadata.yaml
    28-mapk_metadata.yaml

are model-specific metadata files.

The generic fallback file is:

    metadata.yaml

## Relationship to RuleHub's website

RuleHub's website currently handles metadata sources approximately as follows:

1. Prefer `NAME_metadata.yaml`.
2. Otherwise fall back to `metadata.yaml`.
3. Otherwise keep the model without YAML metadata.

When only `metadata.yaml` is available, the website indicates that there is
no model-specific YAML link by displaying `NO YAML!`.

The purpose of `compatibility.database_visible: false` is separate from the
website's `NO YAML!` display. It prevents the corresponding metadata row from
being included in the database-visible results.

Do not change the website's `NO YAML!` behavior as part of this skill unless
the task explicitly requests a change to the website code.

## Validation

After making changes:

1. Confirm that every qualifying model has:

       compatibility:
         database_visible: false

2. Confirm that models with model-specific `NAME_metadata.yaml` files were
   not modified by this workflow.

3. Confirm that no BNGL files were modified.

4. Confirm that all other metadata fields in modified files remain unchanged.

5. If possible, verify that the RuleHub website's database visibility filter
   excludes the affected model rows.

## Example

Before:

    id: example_model
    name: Example Model
    description: Example BNGL model

    compatibility:
      bng2_compatible: true
      nfsim_compatible: false
      simulation_methods: ["ode"]

After:

    id: example_model
    name: Example Model
    description: Example BNGL model

    compatibility:
      database_visible: false
      bng2_compatible: true
      nfsim_compatible: false
      simulation_methods: ["ode"]

Only `compatibility.database_visible` should be added or changed.
