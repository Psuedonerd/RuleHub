# Model Explanation: Jung 2017

## One-sentence summary

Agonist-driven M1 receptor phosphorylation organizes arrestin-dependent ERK activation and phosphatase-mediated signal reversal.

## What the model shows

This model follows oxotremorine engagement of the M1 muscarinic receptor at the plasma membrane, receptor phosphorylation, arrestin recruitment, and assembly of a MEK–ERK signaling complex. It also represents receptor and ERK dephosphorylation, making it useful for examining how a transient agonist exposure can create and then terminate an ERK response.

## Biological story

An extracellular agonist is converted into receptor-binding Oxo and activates membrane M1R. GRK or CK2 phosphorylates the occupied receptor, arrestin binds the modified receptor, and arrestin recruits MEK and ERK. PP1 acts on the receptor, whereas PP2A acts through arrestin to oppose ERK phosphorylation.

## Main biological players

M1 muscarinic receptor, oxotremorine/Oxo, arrestin, GRK, CK2, PP1, PP2A, MEK, ERK, phosphorylated ERK, and a phosphorylation probe.

## Mechanism in plain English

Oxo binds M1R and allows receptor-directed kinases to modify two regulatory serines. Phosphorylated receptor captures arrestin, which serves as a platform for MEK and ERK; ERK on this platform is converted to phosphorylated ERK and can dissociate. PP1 removes receptor phosphorylation, while arrestin-bound PP2A converts phosphorylated ERK back to ERK. A timed agonist function limits receptor stimulation to a defined exposure window.

## Key modeled events

- Oxo binds membrane M1R and promotes receptor phosphorylation by GRK or CK2.
- Arrestin recognizes occupied receptor states and recruits MEK and ERK into a membrane-associated signaling assembly.
- MEK promotes ERK phosphorylation, whereas PP2A reverses that modification.
- PP1 dephosphorylates M1R, weakening the phosphorylated receptor–arrestin state.

## What the model measures

Readouts distinguish total receptor and agonist, phosphorylated receptor complexes, arrestin-containing assemblies, free and phosphorylated ERK, PP2A recruitment, and conversion of a phosphorylation probe.

## Expected behavior in plots

During agonist exposure, phosphorylated M1R and arrestin–MEK–ERK complexes should accumulate before phosphorylated ERK and the phosphorylated probe increase. When stimulation ends, receptor dephosphorylation and PP2A activity should reduce those complexes and shift the ERK readout back toward its unphosphorylated form.

## Caveats

The pathway is a focused receptor–arrestin–ERK module. It does not represent the broader G-protein and second-messenger branches normally associated with M1 receptors.
