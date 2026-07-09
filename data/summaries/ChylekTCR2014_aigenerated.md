# Model Explanation: Chylek 2014 (TCR)

## One-sentence summary

Early T-cell receptor phosphorylation-site dynamics and adaptor assembly.

## What the model shows

This model shows how early TCR signaling is controlled by site-specific phosphorylation, kinase and phosphatase activity, and recruitment of adaptor proteins. It is designed to represent many receptor-proximal molecular states rather than a single generic TCR activation variable.

## Biological story

The model is useful as a mechanistic sketch of how molecular interactions create a time-dependent biological response. It is not just a list of reactions: the important behavior is how binding, activation, inhibition, degradation, or transport events combine to change the abundance of active signaling states and complexes over time.

## Main biological players

TCR/CD3 signaling chains, LCK, ZAP70, PTPN6/SHP1, CSK, PAG, LAT, LCP2/SLP76, GRB2, SOS, PLCG1, and other proximal TCR adaptors.

## Mechanism in plain English

TCR engagement creates opportunities for LCK-mediated phosphorylation of receptor sites. Phosphorylated receptor motifs recruit ZAP70, which becomes activated and helps phosphorylate adaptor proteins such as LAT and LCP2. Adaptors recruit additional signaling proteins to form larger complexes. Phosphatases and inhibitory kinases counterbalance activation by removing phosphates or restraining Src-family kinase activity.

## Key modeled events

- LCK phosphorylates TCR/CD3 sites, creating docking sites for ZAP70.
- Activated ZAP70 phosphorylates adaptor proteins such as LAT and LCP2, enabling larger signaling assemblies.
- Phosphatases and inhibitory kinases oppose activation, so the model can show how site-specific phosphorylation patterns are shaped by competing enzymes.

## What the model measures

The readouts track phosphorylated receptor and adaptor sites, active kinases, phosphatase-regulated states, and assembled signaling complexes. The model shows how the pattern of phosphorylation sites controls early T-cell signaling output.

## How to interpret the plots

A rising curve means that the corresponding active molecule, modified state, complex, or output is accumulating. A falling curve means it is being consumed, deactivated, degraded, released, or diluted. If two curves move in opposite directions, the model is showing a shift between biological states, such as free versus complexed receptor, inactive versus active kinase, or unmodified versus modified substrate.

## Caveats

This is an explanatory summary of the encoded mechanism, not a claim that the model is experimentally complete. When molecule names are abstract or abbreviated, the summary avoids inventing identities beyond what the model itself supports.
