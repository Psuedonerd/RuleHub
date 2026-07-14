# Model Explanation: Erdem 2021

## One-sentence summary

Early insulin and IGF1 receptor signaling in MCF7 cells fit to RPPA-style signaling data.

## What the model shows

This model shows how insulin and IGF1 separately engage their receptors and activate early downstream signaling in MCF7 breast cancer cells. It includes receptor phosphorylation, downstream adaptor signaling, feedback, resensitization, and receptor recycling.

## Biological story

Erdem 2021 is a receptor-family signaling comparison in MCF7 cells. Insulin and IGF1 engage related receptors, produce receptor phosphorylation, and feed downstream outputs while feedback and recycling shape signal duration.

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

## Expected behavior in plots

Plots should compare insulin-receptor and IGF1-receptor phosphorylation with downstream signals. Recovery or decline after an initial peak suggests feedback, resensitization, or receptor recycling.

## Caveats

The model is fitted to early signaling behavior in a specific cellular context, so interpretation should not be generalized to every cell type without refitting or validation.
