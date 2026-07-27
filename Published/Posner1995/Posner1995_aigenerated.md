# Model Explanation: Posner 1995

## One-sentence summary

Bivalent ligand and receptor form chains that can reversibly close into cyclic dimers, producing a prozone-sensitive aggregate response.

## What the model shows

This aggregation model adds a specific ring-closure route to otherwise linear bivalent ligand–receptor chains. It can distinguish chain bonds from ring bonds and therefore asks when a four-member cyclic dimer dominates over open aggregates across ligand doses.

## Biological story

Ligand captures receptor and uses its second arm to crosslink another receptor. Repetition extends alternating chains. A particular two-ligand/two-receptor chain can close into a ring, and that ring can reopen; excess ligand eventually saturates receptor sites and suppresses crosslinking.

## Main biological players

Bivalent ligand, bivalent receptor, chain bonds, ring bonds, open chains, and a cyclic two-ligand/two-receptor complex.

## Mechanism in plain English

Free ligand binds receptor, then tethered ligand recruits receptor from a separate complex to extend a chain. Bond dissociation shortens or separates chains. When the ends of the specified four-member chain meet, they form a cyclic dimer; an explicit opening process restores the chain. Distinct bond states ensure ring opening is treated separately from ordinary chain breakup.

## Key modeled events

- Ligand capture creates the first ligand–receptor bond.
- A free ligand arm crosslinks an additional receptor to grow an open chain.
- A two-ligand/two-receptor chain closes reversibly into a cyclic dimer.
- High ligand occupancy can block crosslinking and create a bell-shaped dose response.

## What the model measures

Measurements include free ligand and receptor, total bonds, free sites, and the cyclic dimer population.

## Expected behavior in plots

At intermediate ligand dose, bond formation and cyclic dimers should be favored. Very low ligand gives little capture, whereas high ligand saturates receptors independently and suppresses bridging, so the cyclic-dimer or crosslinking response should show a prozone-like maximum.

## Caveats

Only one ring size is allowed, and larger cyclic structures are excluded. The model addresses aggregation physics rather than receptor signaling or cellular secretion.
