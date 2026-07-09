# Model Explanation: Haugh2b

## One-sentence summary

Haugh2b demonstrates r 1.00.

## What the model shows

Haugh2b shows r 1.00. It is useful because it keeps attention on binding of s1 from cytosol while still connecting that step to the model readouts.

## Biological story

Haugh2b is a validation model focused on r 1.00. The biological narrative is built around binding of s1 from cytosol, with binding of s1 from membrane providing the next layer of behavior rather than a generic pathway-wide description.

## Main biological players

R, S1, S2

## Mechanism in plain English

Haugh2b begins with binding of s1 from cytosol. It then adds binding of s1 from membrane, which changes how R, S1, S2 contribute to the tutorial behavior. The third modeled step, binding of s2 from cytosol, connects the upstream event to the readouts a user would inspect after simulation.

## Key modeled events

- Binding of S1 from cytosol.
- Binding of S1 from membrane.
- Binding of S2 from cytosol.

## What the model measures

The readouts track S2 P tot, S2 P mem, R total, S1 total, S2 total. Together, these measurements show how Haugh2b moves material among its central tutorial states.

## Expected behavior in plots

For Haugh2b, inspect readouts that report binding of s1 from cytosol and compare them with readouts affected by binding of s1 from membrane. A visible delay, plateau, or separation between those outputs indicates how binding of s2 from cytosol changes the tutorial dynamics.

## Caveats

Haugh2b is primarily a validation-style example for r 1.00; it should be used to understand that encoded behavior rather than as a complete biological pathway.
