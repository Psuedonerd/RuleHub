# Model Explanation: Hlavacek 2001

## One-sentence summary

Kinetic proofreading by receptor dimers that must survive sequential modification steps.

## What the model shows

This model shows how signaling can discriminate between ligands by requiring a receptor complex to remain intact through several irreversible modification steps. Short-lived complexes tend to fall apart before reaching the final signaling state.

## Biological story

The model is useful as a mechanistic sketch of how molecular interactions create a time-dependent biological response. It is not just a list of reactions: the important behavior is how binding, activation, inhibition, degradation, or transport events combine to change the abundance of active signaling states and complexes over time.

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

## How to interpret the plots

A rising curve means that the corresponding active molecule, modified state, complex, or output is accumulating. A falling curve means it is being consumed, deactivated, degraded, released, or diluted. If two curves move in opposite directions, the model is showing a shift between biological states, such as free versus complexed receptor, inactive versus active kinase, or unmodified versus modified substrate.

## Caveats

This is an explanatory summary of the encoded mechanism, not a claim that the model is experimentally complete. When molecule names are abstract or abbreviated, the summary avoids inventing identities beyond what the model itself supports.
