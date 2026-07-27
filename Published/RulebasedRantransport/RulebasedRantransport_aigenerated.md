# Model Explanation: Rule based Ran transport

## One-sentence summary

Ran-mediated nuclear export couples cargo phosphorylation state to RCC1-dependent release and cytoplasmic accumulation.

## What the model shows

This compact transport model follows Ran and an abstract cargo between nucleus and cytoplasm. Cargo carries three reversible phosphorylation sites, and nuclear RCC1 competes for Ran so that cargo–Ran complexes can be disassembled after transport.

## Biological story

Ran–cargo complexes move from nucleus to cytoplasm. Cargo phosphorylation is controlled in the cytoplasm, while nuclear RCC1 binds Ran and favors cargo release. The model therefore links transport direction, binding competition, and cargo modification without naming a specific cargo protein.

## Main biological players

Ran, an abstract three-site cargo, nuclear RCC1, nuclear and cytoplasmic compartments, and phosphorylated cargo states.

## Mechanism in plain English

Ran binds cargo in either compartment, but the transport step carries bound Ran toward the cytoplasm. In the nucleus, RCC1 captures Ran and competes with cargo, promoting separation. Cargo can gain or lose phosphate independently at three positions, so phosphorylation state can be compared with localization and Ran occupancy.

## Key modeled events

- Ran binds the abstract cargo and the complex is exported to the cytoplasm.
- Nuclear RCC1 binds Ran and competes with cargo for the same partner.
- Cargo is reversibly phosphorylated at three independent positions.
- Binding, release, and transport redistribute free cargo and Ran-bound cargo between compartments.

## What the model measures

Readouts track cytoplasmic Ran, nuclear and cytoplasmic cargo, phosphorylated cargo, nuclear RCC1, and cytoplasmic Ran–cargo complexes.

## Expected behavior in plots

Ran-bound cargo should transfer toward the cytoplasm, raising cytoplasmic complex and cargo readouts. Nuclear RCC1 should favor free nuclear cargo by drawing Ran away, while the phosphorylated-cargo curves reflect how modification equilibrates relative to transport.

## Caveats

The cargo is deliberately abstract, and canonical RanGTP/RanGDP nucleotide cycling is not represented explicitly. Directionality is imposed through the transport and competition scheme.
