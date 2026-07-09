# Model Explanation: Creamer 2012

## One-sentence summary

Creamer 2012 demonstrates initial values.

## What the model shows

Creamer 2012 shows initial values. It is useful because it keeps attention on egf binding to an egfr monomer while still connecting that step to the model readouts.

## Biological story

Creamer 2012 is a tutorial model focused on initial values. The biological narrative is built around egf binding to an egfr monomer, with hrg binding to an erbb3 monomer providing the next layer of behavior rather than a generic pathway-wide description.

## Main biological players

EGF, HRG, EGFR, ErbB2, ErbB3, ErbB4, p52Shc1, Grb2, Sos1, Gab1, PI3K, PIP3

## Mechanism in plain English

Creamer 2012 begins with egf binding to an egfr monomer. It then adds hrg binding to an erbb3 monomer, which changes how EGF, HRG, EGFR, ErbB2, ErbB3, ErbB4 contribute to the tutorial behavior. The third modeled step, hrg binding to an erbb4 monomer, connects the upstream event to the readouts a user would inspect after simulation.

## Key modeled events

- EGF binding to an EGFR monomer.
- HRG binding to an ErbB3 monomer.
- HRG binding to an ErbB4 monomer.

## What the model measures

The readouts include EGFREGFR, EGFRErbB2, EGFRErbB3, EGFRErbB4, ErbB2ErbB2, ErbB2ErbB3, and additional related outputs. They show how Creamer 2012 distributes molecules among active, inactive, bound, free, or product-like states.

## Expected behavior in plots

For Creamer 2012, inspect readouts that report egf binding to an egfr monomer and compare them with readouts affected by hrg binding to an erbb3 monomer. A visible delay, plateau, or separation between those outputs indicates how hrg binding to an erbb4 monomer changes the tutorial dynamics.

## Caveats

Creamer 2012 is intentionally instructional, so it focuses on initial values and leaves out many biological details that would distract from the tutorial concept.
