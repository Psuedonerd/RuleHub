# Model Explanation: Gardner 2000

## One-sentence summary

A bistable genetic toggle switch made from two mutually repressing gene products.

## What the model shows

This model shows how two genes that repress each other can create a memory-like switch. Depending on the starting condition, one gene product remains high while the other remains low, or the reverse state is maintained.

## Biological story

Gardner 2000 is a gene-circuit memory model. Two mutually repressing gene products create alternative stable expression states, so history and starting conditions matter.

## Main biological players

Two abstract gene products, mutual repression, cooperative promoter control, and first-order degradation.

## Mechanism in plain English

Each gene product inhibits production of the other. Because repression is cooperative, intermediate states can be unstable: a small bias toward one product pushes the system toward a stable state dominated by that product. Degradation prevents unbounded accumulation and sets the time scale.

## Key modeled events

- Each gene product represses production of the other, creating mutual antagonism.
- Cooperative repression makes intermediate states unstable, so the system tends to commit to one dominant gene-expression state.
- Protein degradation prevents unlimited accumulation and helps set the time scale for switching or maintenance.

## What the model measures

The readouts track the two gene-product levels. The model shows bistability: two stable expression states separated by an unstable boundary.

## Expected behavior in plots

Plots should show one gene product becoming high while the other stays low. If trajectories starting from different initial states settle into different endpoints, the toggle is acting bistably.

## Caveats

The model is intentionally abstract and dimensionless; the two gene products represent a circuit design rather than a full natural regulatory locus.
