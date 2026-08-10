# Model Explanation: Dushek 2011

## One-sentence summary

Encounter-complex control of a kinase/phosphatase modifying a substrate with many sites.

## What the model shows

This model shows how a substrate carrying many modification sites is phosphorylated and dephosphorylated through a two-step encounter mechanism. It is designed to study how repeated encounter binding and enzyme refractory periods affect multisite modification.

## Biological story

Dushek 2011 is about processivity-like behavior without assuming a permanently bound enzyme. Enzymes repeatedly enter encounter complexes with a multisite substrate, modify it, pause, and re-engage.

## Main biological players

A multisite substrate, a kinase, a phosphatase, encounter complexes, active and inactive enzyme states, and a count of modified substrate sites.

## Mechanism in plain English

Kinase or phosphatase first enters an encounter complex with the substrate. Within that temporary encounter complex, the enzyme can bind productively and modify one site. After catalysis, the enzyme becomes temporarily inactive, creating a refractory period before it can act again. The substrate state records how many sites are phosphorylated rather than treating each site as a separate named residue.

## Key modeled events

- Kinase or phosphatase first enters an encounter complex with the multisite substrate before productive catalysis occurs.
- A catalytic event changes the substrate modification count and temporarily inactivates the enzyme.
- Repeated encounter, modification, release, and reactivation events shape the distribution of substrate molecules across phosphorylation levels.

## What the model measures

The readouts track substrate molecules with different numbers of modified sites and enzyme encounter states. The model shows how enzyme rebinding and temporary inactivation shape the distribution of phosphorylation levels.

## Expected behavior in plots

Plots should show how substrate molecules distribute across modification levels. Broad distributions indicate heterogeneous multisite processing; accumulation near high modification states indicates efficient repeated modification.

## Caveats

The model compresses many individual substrate sites into a modification count, so it is best for overall multisite modification patterns rather than residue-specific biology.
