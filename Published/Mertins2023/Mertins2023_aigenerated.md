# Model Explanation: Mertins 2023

## One-sentence summary

DNA damage couples PARP-dependent repair chemistry to p53-driven Bax expression and caspase activation.

## What the model shows

This model joins two DNA-damage responses: PARP recruitment and substrate PARylation at breaks, and a p53–Bax apoptotic module. It also represents competitive PARP inhibition, allowing repair-associated occupancy to be related to Bax availability and caspase activation.

## Biological story

DNA double-strand breaks recruit both p53 and PARP. Active PARP consumes NAD to modify XRCC1, while PARG reverses that modification; an inhibitor competes at the PARP NAD pocket and releases PARP from DNA. Bound p53 promotes Bax expression, and Bax can overcome BclXL restraint to activate caspases.

## Main biological players

DNA double-strand breaks, p53, PARP, NAD, XRCC1, PARG, PARP inhibitor, Bax, BclXL, Bad, AKT, 14-3-3, and caspase.

## Mechanism in plain English

p53 and PARP compete for damage-associated binding. PARP uses NAD to PARylate XRCC1, and PARG removes the modification; inhibitor binding blocks the NAD pocket. Damage-bound p53 increases Bax mRNA, which produces Bax protein. BclXL sequesters Bax, while Bad competes for BclXL and AKT-controlled Bad phosphorylation shifts that competition. Free Bax activates procaspase, and active caspase reinforces activation.

## Key modeled events

- DNA breaks recruit p53 and activate PARP.
- PARP uses NAD to modify XRCC1, while PARG reverses the modification.
- A PARP inhibitor occupies the substrate pocket and displaces PARP from damage.
- p53 induces Bax, and free Bax promotes caspase activation against BclXL restraint.

## What the model measures

Readouts follow Bax mRNA, free Bax, active caspase, DNA-bound p53, and inhibitor-bound PARP.

## Expected behavior in plots

PARP–inhibitor complexes should increase with inhibitor exposure as productive PARP engagement falls. DNA-bound p53 should drive a delayed Bax-mRNA rise, followed by free Bax and then active caspase; strong BclXL sequestration can separate Bax production from caspase activation.

## Caveats

The model combines repair and apoptosis modules at a coarse level and contains inconsistent initial-quantity names that require curation before quantitative interpretation.
