# Model Explanation: Mukhopadhyay 2013

## One-sentence summary

Ordered phosphorylation of three TCR ζ-chain ITAMs controls progressive recruitment and retention of ZAP-70.

## What the model shows

This model isolates enzymatic modification of a substrate representing the TCR ζ chain. A kinase and phosphatase move three ITAMs through unphosphorylated, singly phosphorylated, and doubly phosphorylated states in sequence, while ZAP-70 binds fully modified ITAMs with position-dependent stability.

## Biological story

A kinase begins at the first ITAM and adds two phosphates before modification proceeds to the second and third. A phosphatase can reverse each step. Fully phosphorylated motifs become docking sites for ZAP-70, and later ITAMs retain ZAP-70 more strongly in the parameterization.

## Main biological players

TCR ζ-chain substrate with three ITAMs, a kinase, a phosphatase, and ZAP-70.

## Mechanism in plain English

The kinase transiently binds an available ITAM and adds phosphates one at a time. Modification is ordered: downstream ITAMs become substrates only after earlier motifs are fully modified. The phosphatase removes those phosphates through corresponding intermediate states. ZAP-70 recognizes any doubly phosphorylated ITAM, but its dissociation rate depends on which motif is occupied.

## Key modeled events

- The kinase adds two phosphates sequentially to ITAM 1.
- After ITAM 1 is complete, phosphorylation advances through ITAM 2 and then ITAM 3.
- A phosphatase reverses every phosphorylation step.
- ZAP-70 binds doubly phosphorylated ITAMs with motif-specific residence times.

## What the model measures

Readouts count bound ZAP-70 and seven successive ζ-chain phosphorylation classes, from no phosphorylation through complete double phosphorylation of all three ITAMs.

## Expected behavior in plots

The phosphorylation classes should progress in order, with early states appearing before the fully modified state. Bound ZAP-70 should rise as doubly phosphorylated ITAMs accumulate and may persist preferentially on the motif with the slowest dissociation.

## Caveats

The kinase and phosphatase are generic, and receptor ligation, Lck regulation, membrane localization, and downstream ZAP-70 signaling are outside this focused ITAM-processing model.
