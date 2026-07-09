# Model Explanation: Erdem 2021

## One-sentence summary

Early insulin and IGF1 receptor signaling in MCF7 cells fit to RPPA-style signaling data.

## What the model shows

This model shows how insulin and IGF1 separately engage their receptors and activate early downstream signaling in MCF7 breast cancer cells. It includes receptor phosphorylation, downstream adaptor signaling, feedback, resensitization, and receptor recycling.

## Biological story

The model is useful as a mechanistic sketch of how molecular interactions create a time-dependent biological response. It is not just a list of reactions: the important behavior is how binding, activation, inhibition, degradation, or transport events combine to change the abundance of active signaling states and complexes over time.

## Main biological players

Insulin, IGF1, insulin receptor, IGF1 receptor, phosphorylated receptor states, IRS/adapter-like downstream species, ERK/AKT-related outputs, feedback regulators, and recycled receptors.

## Mechanism in plain English

Insulin binds insulin receptor and IGF1 binds IGF1 receptor. Ligand-bound receptors become phosphorylated and signal to downstream nodes. Feedback reactions reduce signaling after activation, while resensitization and recycling restore receptor availability. The model uses fitted rate relationships to capture measured early signaling behavior.

## Key modeled events

- Insulin and IGF1 bind their matching receptors, producing receptor phosphorylation rather than a generic growth-factor signal.
- Phosphorylated receptors drive downstream signaling outputs through adaptor-like steps calibrated to MCF7 signaling measurements.
- Feedback, resensitization, and receptor recycling allow signaling to decline and receptor responsiveness to recover.

## What the model measures

The readouts follow receptor phosphorylation and downstream signaling outputs. The model shows how two related growth-factor inputs produce receptor-specific but overlapping signaling dynamics.

## How to interpret the plots

A rising curve means that the corresponding active molecule, modified state, complex, or output is accumulating. A falling curve means it is being consumed, deactivated, degraded, released, or diluted. If two curves move in opposite directions, the model is showing a shift between biological states, such as free versus complexed receptor, inactive versus active kinase, or unmodified versus modified substrate.

## Caveats

This is an explanatory summary of the encoded mechanism, not a claim that the model is experimentally complete. When molecule names are abstract or abbreviated, the summary avoids inventing identities beyond what the model itself supports.
