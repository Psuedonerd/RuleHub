# Model Explanation: Harmon 2017

## One-sentence summary

History-dependent FcεRI mast-cell responses to pulsed antigen stimulation.

## What the model shows

This model shows why mast cells can respond differently to repeated antigen pulses depending on the time since the previous pulse. Fast Syk activation and slower Ship1-associated negative regulation create memory of recent stimulation.

## Biological story

The model is useful as a mechanistic sketch of how molecular interactions create a time-dependent biological response. It is not just a list of reactions: the important behavior is how binding, activation, inhibition, degradation, or transport events combine to change the abundance of active signaling states and complexes over time.

## Main biological players

FcεRI-IgE receptor, multivalent antigen, Syk, Ship1, cofactor X, PIP3, degranulation output, and pulse/wash antigen input.

## Mechanism in plain English

Antigen binds and crosslinks FcεRI, producing a rapid Syk-positive signal. A slower Ship1/X negative branch develops and affects PIP3 signaling. Degranulation integrates these signals. If pulses arrive close together, the inhibitory branch can dominate and reduce the second response; if pulses are separated longer, the system can become primed for a larger response.

## Key modeled events

- Antigen pulses rapidly create a Syk-positive FcεRI activation signal.
- A slower Ship1/X negative branch changes PIP3 signaling and stores information about recent stimulation.
- Short pulse intervals can yield desensitization, while longer intervals can permit priming and stronger degranulation.

## What the model measures

The readouts track receptor stimulation, Syk activity, Ship1/X negative signaling, PIP3, and degranulation. The model shows desensitization or priming depending on pulse timing.

## How to interpret the plots

A rising curve means that the corresponding active molecule, modified state, complex, or output is accumulating. A falling curve means it is being consumed, deactivated, degraded, released, or diluted. If two curves move in opposite directions, the model is showing a shift between biological states, such as free versus complexed receptor, inactive versus active kinase, or unmodified versus modified substrate.

## Caveats

This is an explanatory summary of the encoded mechanism, not a claim that the model is experimentally complete. When molecule names are abstract or abbreviated, the summary avoids inventing identities beyond what the model itself supports.
