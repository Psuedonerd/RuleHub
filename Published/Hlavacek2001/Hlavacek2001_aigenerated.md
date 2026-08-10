# Model Explanation: Hlavacek 2001

## One-sentence summary

A bivalent ligand must keep two receptors crosslinked long enough to complete five sequential proofreading steps, making terminal signaling strongly dependent on complex lifetime.

## What the model shows

This model demonstrates kinetic proofreading in receptor aggregation. Two ligands that form similar numbers of receptor dimers can produce very different terminal signals if their dissociation rates differ, because every dimer must survive five consecutive modification steps before reaching the fully activated state.

## Biological story

A symmetric ligand first captures one monovalent receptor and then recruits a second receptor to form a dimer. The intact dimer progresses through five abstract modifications that can represent phosphorylation, kinase recruitment, adaptor assembly, or related maturation events. If either receptor separates before completion, all accumulated progress is lost and the remaining ligand complex returns to the unmodified state.

## Main biological players

- **Bivalent ligand:** carries two equivalent receptor-binding arms and the shared proofreading-stage counter.
- **Monovalent receptor:** binds one ligand arm and participates in singly bound or dimeric complexes.
- **Partially modified dimers:** intact complexes at stages zero through four of the proofreading sequence.
- **Terminal dimers:** complexes that retain both receptors through all five modifications.
- **Dissociation rate:** the scanned ligand-quality variable that competes with proofreading progression.

## Mechanism in plain English

Free ligand captures one receptor and then crosslinks a second. Once both arms are occupied, the complex advances one stage at a time at a common modification rate. At every stage, either ligand–receptor bond can break; that event releases a receptor and resets the ligand's modification history to zero. Consequently, slow-dissociating complexes are disproportionately likely to reach stage five, while rapidly dissociating complexes repeatedly restart before producing the terminal signal.

## Key modeled events

- A free bivalent ligand captures one receptor, creating the intermediate required for surface crosslinking.
- The second ligand arm captures another receptor and creates the dimer that can enter the proofreading sequence.
- Intact dimers advance irreversibly through five modification stages without changing receptor occupancy.
- Dissociation of either receptor at any stage erases all modifications and returns the ligand complex to the basal state.

## What the model measures

The measurements include free ligand, free receptor, singly occupied ligand, total receptor dimers, and the abundance of dimers at each modification stage from zero through five. Derived readouts report the fraction of receptors in dimers, the fraction of dimers reaching the terminal stage, the fraction of all receptors in terminal dimers, and the proofreading competition between modification and two possible bond-breaking events.

## Expected behavior in plots

After mixing, free ligand and receptor should be redistributed into singly bound complexes and dimers. The stage-zero dimer population appears before later stages, and stages one through five should show progressively delayed occupancy. In the dissociation-rate scan, low dissociation rates should preserve dimers long enough to enrich the terminal stage, whereas increasing dissociation should reduce the terminal fraction much more sharply than it reduces early or total dimer formation. The terminal yield therefore provides the clearest ligand-lifetime discrimination.

## Caveats

The five modification stages are deliberately abstract and are not assigned to particular residues or signaling proteins. All stages share one progression rate, and any bond loss causes complete rather than partial reset. The model captures the logic of proofreading but not downstream messenger production, receptor trafficking, or a detailed biochemical pathway. The model is labeled 2001, while its scientific description also draws on a 2002 mathematical treatment.
