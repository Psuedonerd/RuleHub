# Model Explanation: Chylek 2014 (TCR)

## One-sentence summary

Early T-cell receptor phosphorylation-site dynamics and adaptor assembly.

## What the model shows

This model shows how early TCR signaling is controlled by site-specific phosphorylation, kinase and phosphatase activity, and recruitment of adaptor proteins. It is designed to represent many receptor-proximal molecular states rather than a single generic TCR activation variable.

## Biological story

Chylek TCR 2014 is a phosphorylation-site dynamics model. It asks how early TCR signaling emerges from many site-specific phosphorylation and dephosphorylation events rather than from a simple receptor on/off switch.

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

## Expected behavior in plots

Plots should be read as a map of signaling-site occupancy. Rising phosphorylated TCR, ZAP70, LAT, or LCP2 states indicate assembly of a productive T-cell signaling platform; inhibitory states show pathway restraint.

## Caveats

The model is strongest for early receptor-proximal TCR events. It should not be interpreted as a complete T-cell activation, cytokine production, or proliferation model.
