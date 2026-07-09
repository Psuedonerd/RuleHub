# Model Explanation: BaruaFceRI 2012

## One-sentence summary

FcεRI signaling regulated by ligand crosslinking, Lyn/Syk activation, LAT signaling, and raft localization.

## What the model shows

This model shows how multivalent ligand and hapten binding crosslink FcεRI receptors and how that receptor clustering is translated into phosphorylation of receptor chains, Syk, and LAT. It also asks how membrane raft localization changes signaling by altering phosphorylation and dephosphorylation rates.

## Biological story

The model is useful as a mechanistic sketch of how molecular interactions create a time-dependent biological response. It is not just a list of reactions: the important behavior is how binding, activation, inhibition, degradation, or transport events combine to change the abundance of active signaling states and complexes over time.

## Main biological players

FcεRI receptor, multivalent ligand or hapten, Lyn, Syk, LAT, Grb2, and raft versus non-raft localization states.

## Mechanism in plain English

Ligand binds receptor-associated antibody arms and crosslinks receptors. Lyn binds receptors and phosphorylates receptor ITAMs. Phosphorylated receptors recruit Syk, Syk becomes activated, and active Syk phosphorylates LAT. LAT recruits Grb2-containing complexes. Proteins can move between raft and non-raft environments, changing how readily they are phosphorylated or dephosphorylated.

## Key modeled events

- Ligand and hapten binding crosslink FcεRI, converting receptor occupancy into receptor clustering.
- Lyn phosphorylates receptor chains, allowing Syk recruitment and activation at the membrane.
- LAT phosphorylation and Grb2 recruitment transmit the receptor signal downstream, while raft localization changes the effective strength of phosphorylation and dephosphorylation.

## What the model measures

The readouts track receptor aggregates, phosphorylated receptor, receptor-bound Syk, phosphorylated Syk, phosphorylated LAT, and raft-associated signaling species. The model shows how receptor clustering and membrane microenvironment jointly control early FcεRI output.

## How to interpret the plots

A rising curve means that the corresponding active molecule, modified state, complex, or output is accumulating. A falling curve means it is being consumed, deactivated, degraded, released, or diluted. If two curves move in opposite directions, the model is showing a shift between biological states, such as free versus complexed receptor, inactive versus active kinase, or unmodified versus modified substrate.

## Caveats

This is an explanatory summary of the encoded mechanism, not a claim that the model is experimentally complete. When molecule names are abstract or abbreviated, the summary avoids inventing identities beyond what the model itself supports.
