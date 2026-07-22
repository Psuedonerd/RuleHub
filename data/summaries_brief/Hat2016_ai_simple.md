# Model Explanation: Hat 2016

## One-sentence summary

p53 feedback, bifurcation, and cell-fate decision behavior after DNA damage.

## What the model shows

This model shows how p53 pathway feedbacks can convert DNA damage signals into different cell-fate regimes. It includes damage sensing, p53 stabilization, Mdm2-mediated negative feedback, transcriptional outputs, and switches that can support survival or death decisions.

## Biological story

Hat 2016 treats p53 as a feedback-driven decision system. DNA damage does not simply raise p53; feedback loops can create thresholds, oscillations, or high-p53 regimes associated with different fates.

## Main biological players

DNA damage, repair modules, p53, Mdm2, ATM/ATR-like damage signaling, p53 target genes, pro-survival and pro-death regulatory branches.

## Mechanism in plain English

DNA damage activates upstream signaling that stabilizes p53. p53 drives transcription of regulators, including negative-feedback components such as Mdm2 and other fate-associated outputs. Feedback loops create nonlinear behavior, so gradual parameter changes can shift the system between low-p53 survival-like states, oscillatory responses, or high-p53 cell-death-associated states.

## Key modeled events

- DNA damage activates upstream signaling that stabilizes and elevates p53.
- p53 induces regulators such as Mdm2 and other target genes, creating both negative feedback and fate-related outputs.
- Feedback and threshold effects allow the same pathway to support low-p53, oscillatory, or high-p53 response regimes.

## What the model measures

The readouts track p53, Mdm2, damage, repair, and selected p53 target outputs. The model shows how feedback architecture can create thresholds and alternative cell-fate outcomes.

## Expected behavior in plots

Plots should compare DNA damage, p53, Mdm2, and target outputs. Oscillations, sustained high p53, or return to baseline indicate different feedback regimes in the modeled cell-fate landscape.

## Caveats

The model summarizes a p53 decision network and depends on selected switches and parameters; it is not a complete molecular inventory of all p53 biology.
