# Model Explanation: Harmon 2017

## One-sentence summary

History-dependent FcεRI mast-cell responses to pulsed antigen stimulation.

## What the model shows

This model shows why mast cells can respond differently to repeated antigen pulses depending on the time since the previous pulse. Fast Syk activation and slower Ship1-associated negative regulation create memory of recent stimulation.

## Biological story

Harmon 2017 is a signaling-history model. The same antigen pulse can produce different mast-cell responses depending on how much fast positive signaling and slower negative regulation remain from earlier stimulation.

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

## Expected behavior in plots

Plots should be read across pulse timing. Close pulses should reveal residual inhibition and desensitization, while longer gaps can allow recovery or priming before the next degranulation response.

## Caveats

The model is tailored to pulsed FcεRI stimulation and fitted response behavior; it should not be treated as a universal model of every mast-cell stimulus.
