# Model Explanation: Hlavacek 1999

## One-sentence summary

Steric crowding progressively reduces the ability of a 20-valent ligand to recruit additional cell-surface receptors as its occupancy increases.

## What the model shows

This model isolates how receptor footprint and ligand geometry can limit multivalent binding even when many nominal sites remain unoccupied. It follows the distribution of ligands carrying one through twenty receptor contacts and compares low-valence aggregates with highly occupied structures.

## Biological story

A ligand arrives from solution and forms its first receptor contact at the cell surface. Additional receptors can then join, but each bound receptor covers part of the ligand and obstructs nearby positions. As crowding increases, the number of geometrically accessible sites falls faster than the simple count of unused sites. Receptors can also detach one at a time, so the occupancy distribution reflects a balance among ligand supply, free-receptor depletion, steric exclusion, and contact loss.

## Main biological players

- **Multivalent ligand:** an abstract particle with a maximum of twenty receptor contacts.
- **Cell-surface receptors:** an implicit conserved pool depleted as ligand occupancy grows.
- **Free ligand:** an implicit solution pool depleted when ligands acquire their first surface contact.
- **Steric insertion factors:** occupancy-specific accessibility terms determined by the receptor footprint on the ligand surface.
- **Ligand occupancy classes:** twenty populations representing ligands with one through twenty attached receptors.

## Mechanism in plain English

The first receptor–ligand contact transfers ligand from the implicit free pool into the singly bound surface population. Each later binding event increases the ligand's occupancy by one and requires both an available free receptor and a geometrically accessible position. The accessibility penalty becomes stronger as the ligand fills, so high-occupancy states are harder to reach than they would be if all unused sites remained equivalent. Any existing receptor contact may dissociate, making highly occupied ligands lose contacts more frequently because they have more bonds that can break.

## Key modeled events

- Free ligand and free receptor combine to create the first surface-bound ligand population.
- Additional receptors bind sequentially, moving ligands through occupancy classes from one contact toward twenty.
- Steric exclusion reduces the effective number of available positions at each successive occupancy level.
- Receptor contacts dissociate individually, returning ligands to the next-lower occupancy class or, from the singly bound state, to the implicit free pool.

## What the model measures

The primary readouts are the normalized populations of ligands with exactly one through twenty attached receptors and the total amount of surface-bound ligand. Weighted combinations of those populations determine the remaining free-receptor fraction. Two aggregate measurements summarize the fraction of receptors in complexes with at least two contacts and the fraction in complexes with at least ten contacts.

## Expected behavior in plots

The singly bound population should appear first and feed progressively higher occupancy classes. Low- and intermediate-valence classes should accumulate more readily than near-saturated classes because receptor depletion and steric exclusion both oppose continued binding. The fraction of receptors in complexes with at least two contacts should rise earlier and to a larger value than the fraction in complexes with at least ten contacts. The high-valence measure is therefore the more sensitive indicator of the receptor-footprint penalty.

## Caveats

The model uses normalized, dimensionless densities rather than literal molecular counts. Receptors and physical ligand sites are not represented individually; ligands with the same occupancy are treated as equivalent regardless of the spatial arrangement of their contacts. The steric penalty is based on a particular circular-footprint approximation, so it captures excluded-area effects without resolving an explicit three-dimensional ligand geometry.
