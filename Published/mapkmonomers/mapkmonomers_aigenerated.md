# Model Explanation: MAPK Monomers

## One-sentence summary

Monomeric Ste5 scaffolds organize sequential Ste11–Ste7–Fus3 phosphorylation without scaffold dimerization.

## What the model shows

This companion model provides the monomeric-scaffold baseline for a yeast MAPK cascade. A single Ste5 can recruit all three kinase tiers, allowing direct propagation from Ste11 through Ste7 to Fus3 while excluding scaffold–scaffold association.

## Biological story

Kinases load onto separate positions of Ste5. Scaffold-associated Ste11 is activated, passes phosphate to Ste7, and active Ste7 modifies Fus3. Each kinase can be dephosphorylated, so the output reflects productive scaffold occupancy versus resetting.

## Main biological players

Monomeric Ste5, Ste11, Ste7, Fus3, and their phosphorylated states.

## Mechanism in plain English

Ste5 independently binds Ste11, Ste7, and Fus3. Bound Ste11 becomes phosphorylated and can modify neighboring Ste7; fully active Ste7 then phosphorylates scaffold-associated Fus3. Dephosphorylation returns each kinase to its inactive form. Without Ste5 dimerization, every productive complex is organized around one scaffold molecule.

## Key modeled events

- Ste11, Ste7, and Fus3 reversibly load onto one Ste5 scaffold.
- Scaffold-bound Ste11 becomes active and phosphorylates Ste7.
- Activated Ste7 phosphorylates Fus3 on the same scaffold.
- Dephosphorylation resets Ste11, Ste7, and Fus3.

## What the model measures

Readouts distinguish total phosphorylated Fus3, free phosphorylated Fus3, scaffold-bound phosphorylated Fus3, and Fus3 in Ste5/Ste7-containing assemblies.

## Expected behavior in plots

Scaffold-associated phosphorylated Fus3 should rise as fully loaded Ste5 complexes form, with free phosphorylated Fus3 increasing as output leaves the platform. Compared with the dimeric version, no signal should be assigned to cross-scaffold organization.

## Caveats

The cascade is deliberately minimal and uses generic equal-rate phosphorylation and binding. It omits the upstream pheromone pathway and downstream transcriptional response.
