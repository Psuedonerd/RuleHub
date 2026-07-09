# Model Explanation: Hat 2016

## One-sentence summary

p53 feedback, bifurcation, and cell-fate decision behavior after DNA damage.

## What the model shows

This model shows how p53 pathway feedbacks can convert DNA damage signals into different cell-fate regimes. It includes damage sensing, p53 stabilization, Mdm2-mediated negative feedback, transcriptional outputs, and switches that can support survival or death decisions.

## Biological story

The model is useful as a mechanistic sketch of how molecular interactions create a time-dependent biological response. It is not just a list of reactions: the important behavior is how binding, activation, inhibition, degradation, or transport events combine to change the abundance of active signaling states and complexes over time.

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

## How to interpret the plots

A rising curve means that the corresponding active molecule, modified state, complex, or output is accumulating. A falling curve means it is being consumed, deactivated, degraded, released, or diluted. If two curves move in opposite directions, the model is showing a shift between biological states, such as free versus complexed receptor, inactive versus active kinase, or unmodified versus modified substrate.

## Caveats

This is an explanatory summary of the encoded mechanism, not a claim that the model is experimentally complete. When molecule names are abstract or abbreviated, the summary avoids inventing identities beyond what the model itself supports.
