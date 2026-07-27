# Model Explanation: MAPK Dimers

## One-sentence summary

Dimerization of Ste5 scaffolds changes how the Ste11–Ste7–Fus3 kinase cascade assembles and phosphorylates Fus3.

## What the model shows

This model examines a yeast MAPK cascade on a scaffold that can dimerize. Each Ste5 recruits Ste11, Ste7, and Fus3, while scaffold–scaffold association creates larger assemblies that can redistribute the spatial relationships among the kinase tiers.

## Biological story

Ste5 captures the three kinases and can pair with another Ste5. Scaffold-bound Ste11 becomes active, phosphorylates nearby Ste7, and activated Ste7 phosphorylates Fus3. Constitutive dephosphorylation competes with this scaffold-supported relay.

## Main biological players

Ste5 scaffold dimers, Ste11, Ste7, Fus3, and phosphorylated forms of all three kinases.

## Mechanism in plain English

Ste5 molecules reversibly dimerize and independently recruit each kinase. Ste11 is activated on a scaffold; active Ste11 modifies scaffold-associated Ste7, and modified Ste7 activates associated Fus3. Phosphate removal continually resets each tier. Fus3 can therefore be phosphorylated while free or while participating in different scaffold-containing assemblies.

## Key modeled events

- Ste5 scaffolds reversibly dimerize.
- Ste11, Ste7, and Fus3 bind dedicated positions on Ste5.
- Activated Ste11 phosphorylates Ste7, which then phosphorylates Fus3.
- Dephosphorylation opposes each kinase tier.

## What the model measures

Readouts separate total phosphorylated Fus3, free phosphorylated Fus3, scaffold-associated phosphorylated Fus3, and Fus3 associated with Ste5 or Ste7-containing assemblies.

## Expected behavior in plots

Phosphorylated Fus3 should rise as loaded Ste5 assemblies form. Scaffold-associated Fus3 should respond before or alongside the total signal, while free phosphorylated Fus3 reflects release; dimerization may retain more output in larger scaffold assemblies than the monomeric counterpart.

## Caveats

The model uses uniform rates and no upstream pheromone input. It is best interpreted as a scaffold-architecture comparison, not a calibrated reconstruction of the full yeast mating pathway.
