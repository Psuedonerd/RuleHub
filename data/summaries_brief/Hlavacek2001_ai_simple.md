# Model Explanation: Hlavacek 2001

## One-sentence summary

Kinetic proofreading by receptor dimers that must survive sequential modification steps.

## What the model shows

This model shows how signaling can discriminate between ligands by requiring a receptor complex to remain intact through several irreversible modification steps. Short-lived complexes tend to fall apart before reaching the final signaling state.

## Biological story

Hlavacek 2001 is a kinetic-discrimination model. Receptor dimers must stay intact long enough to pass through several modification steps, making signaling disproportionately sensitive to ligand lifetime.

## Main biological players

Bivalent ligand, monovalent receptors, receptor dimers, sequential modification counter, and dissociation reset.

## Mechanism in plain English

A bivalent ligand binds two receptors to form a signaling dimer. The dimer then progresses through a chain of modification steps. If either receptor-ligand bond breaks before the final step, the complex loses its accumulated progress and returns to an unmodified state. Longer-lived ligand-receptor interactions therefore generate more fully processed signaling complexes.

## Key modeled events

- A bivalent ligand forms a receptor dimer that can begin a sequence of signaling modifications.
- The dimer must remain intact through multiple steps to reach the terminal signaling state.
- If either receptor bond breaks too early, accumulated progress is reset, allowing long-lived ligand complexes to signal disproportionately well.

## What the model measures

The readouts track dimers at each modification stage and the terminally modified signaling state. The model shows exponential-like discrimination between weak and strong ligand binding.

## Expected behavior in plots

Plots should show early dimer states feeding later modified states. Strong ligands should populate terminal states much more effectively than weak ligands that dissociate and reset.

## Caveats

The model idealizes proofreading as sequential modification with reset on dissociation; real pathways may include additional branches or partial memory.
