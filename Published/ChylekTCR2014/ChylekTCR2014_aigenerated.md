# Model Explanation: Chylek 2014 (TCR)

## One-sentence summary

TCR and CD28 co-engagement organizes Lck, Fyn, ZAP-70, phosphatases, and LAT-associated adaptors into an early phosphorylation network with both activating and inhibitory feedback.

## What the model shows

This model examines phosphorylation-site dynamics during early T-cell receptor (TCR) signaling. Three bivalent ligand types selectively crosslink CD28, TCR, or one of each, allowing comparison of pure co-stimulation, pure receptor engagement, and coupled TCR–CD28 signaling as the complexes recruit kinases, phosphatases, and LAT-associated adaptor proteins.

## Biological story

Ligands cluster CD28 and/or TCR, bringing Lck and Itk to CD28 and Fyn to TCR. Lck phosphorylates multiple TCR-chain tyrosines, creating docking sites for ZAP-70 and the phosphatase PTPN6. Activated ZAP-70 phosphorylates LAT and LCP2, enabling assembly of PLCγ1-, GRAP2-, NCK-, and WAS-containing complexes. PAG1–Csk and PTPN6-associated pathways oppose Src-family kinase activity and remove phosphate from several adaptor proteins, creating a dynamic balance rather than an irreversible activation cascade.

## Main biological players

- **TCR, CD28, and three ligand classes:** receptor/co-receptor inputs that can be engaged separately or together.
- **Lck, Fyn, Itk, and ZAP-70:** receptor-proximal kinases that establish and propagate phosphotyrosine signals.
- **PTPN6, PAG1, Csk, DOK1, and DOK2:** inhibitory or resetting regulators of kinase and adaptor phosphorylation.
- **LAT, PLCγ1, GRAP2, LCP2, NCK, and WAS:** downstream scaffolds and effectors that assemble after receptor activation.

## Mechanism in plain English

Crosslinking positions TCR and CD28 so their associated kinases can modify specific receptor-chain tyrosines. These phosphorylated sites recruit ZAP-70 and PTPN6, while CD28-associated Lck also activates Itk and helps phosphorylate bound ZAP-70. Active ZAP-70 modifies LAT at sites that separately recruit PLCγ1 and GRAP2; GRAP2 brings in LCP2, which supports NCK, WAS, and additional PLCγ1 assembly. Fyn can also reach WAS through receptor- or scaffold-associated complexes. At the same time, PAG1 recruits Csk to phosphorylate the inhibitory Lck tail, and PTPN6 removes activating phosphates from Lck, PAG1, DOK proteins, and other signaling components.

## Key modeled events

- Distinct ligands crosslink CD28 alone, TCR alone, or a TCR–CD28 pair, changing which kinases are brought into proximity.
- Lck phosphorylates several TCR-chain sites that recruit ZAP-70 or PTPN6 and thereby branch the signal into activation and negative regulation.
- Activated ZAP-70 phosphorylates LAT and LCP2, enabling assembly of PLCγ1-, GRAP2-, NCK-, and WAS-containing complexes.
- PAG1–Csk and PTPN6 pathways inhibit Lck and dephosphorylate adaptor proteins, shaping site-specific signal duration.

## What the model measures

The measurements emphasize phosphorylation of six TCR-chain tyrosine groups; activation-associated sites on ZAP-70, Lck, Itk, PTPN6, WAS, PAG1, DOK1, DOK2, PLCγ1, and LAT; the inhibitory Lck tail; and selected NCK complexes with TCR or LCP2. These readouts are designed to compare early site-specific phosphorylation and scaffold assembly rather than a later cellular phenotype.

## Expected behavior in plots

TCR phosphosites should respond most strongly when a ligand engages TCR, whereas CD28-containing complexes should enhance Lck and Itk recruitment and alter phosphorylation of ZAP-70 and downstream adaptors. ZAP-70 phosphorylation should precede or accompany LAT Y191 and PLCγ1 phosphorylation, while NCK–TCR and NCK–LCP2 complexes report two different routes into WAS-associated signaling. Inhibitory Lck Y505, PTPN6 phosphorylation, and PAG1-dependent feedback may rise alongside activation and shorten or reshape the peaks at Lck Y424 and the TCR sites.

## Caveats

This is an early signaling model centered on phosphosite kinetics and scaffold assembly; it does not extend to calcium, MAPK, transcription, or T-cell functional outcomes. Ligand classes are abstract tools for controlling TCR and CD28 crosslinking rather than a complete antigen-presentation model. Some related residues are lumped into single modeled sites, so a plotted signal may represent more than one biochemical tyrosine.
