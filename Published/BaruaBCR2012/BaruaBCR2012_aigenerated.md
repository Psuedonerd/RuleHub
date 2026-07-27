# Model Explanation: Barua 2012

## One-sentence summary

Antigen and tonic B-cell receptor signaling emerge from competing Lyn/Fyn/Syk activation and Csk–PAG inhibitory control.

## What the model shows

This model follows early B-cell receptor (BCR) signaling at detailed receptor-proximal resolution. It distinguishes immunoreceptor tyrosine-based activation motif (ITAM) phosphorylation, Src-family kinase activation and autoinhibition, Syk recruitment, and assembly of the inhibitory Csk–PAG module.

## Biological story

Even without antigen, basal kinase activity can produce tonic signaling. Antigen strengthens receptor-proximal encounters, allowing Lyn and Fyn to modify the BCR and one another. Doubly phosphorylated ITAMs recruit Syk, while phosphorylated PAG recruits Csk, which places inhibitory phosphates on Lyn and Fyn.

## Main biological players

BCR Igα and Igβ chains, Lyn, Fyn, Syk, C-terminal Src kinase (Csk), and the phosphoprotein associated with glycosphingolipid-enriched microdomains (PAG/Cbp).

## Mechanism in plain English

Lyn and Fyn bind receptor ITAMs through unique or Src homology 2 (SH2) domains and phosphorylate Igα and Igβ in stages. Doubly phosphorylated Igβ captures tandem-SH2 Syk, which becomes activated by transphosphorylation. Lyn and Fyn also phosphorylate PAG. PAG uses proline-rich and phosphotyrosine sites to tether the kinases and recruit Csk; Csk then phosphorylates their inhibitory C-terminal tyrosines, opposing activation.

## Key modeled events

- Lyn and Fyn associate with BCR ITAMs and phosphorylate Igα and Igβ.
- Doubly phosphorylated Igβ recruits Syk and supports Syk activation.
- Lyn and Fyn phosphorylate one another and PAG within receptor-proximal assemblies.
- PAG recruits Csk, which imposes inhibitory phosphorylation on Lyn and Fyn.
- Constitutive dephosphorylation resets receptor, kinase, PAG, and Syk states.

## What the model measures

Readouts follow singly and doubly phosphorylated Igα/Igβ, activated and autoinhibited Lyn/Fyn, activated Syk, and PAG-bound Csk. They allow the positive receptor/Syk arm to be compared directly with inhibitory Src-family kinase control.

## Expected behavior in plots

Increasing antigen input should first increase receptor ITAM phosphorylation, followed by active Lyn/Fyn and Syk. PAG–Csk complexes and autoinhibited Src-family kinases should develop as a counter-response; strong inhibitory recruitment should reduce or cap the Syk output despite continued receptor input.

## Caveats

The model is detailed for BCR-proximal phosphorylation but stops before calcium, Ras–ERK, NF-κB, and transcriptional responses. Several tyrosine pairs are lumped into single model states.
