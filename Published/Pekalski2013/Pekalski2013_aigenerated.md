# Model Explanation: Pekalski 2013

## One-sentence summary

Autocrine TNF–NF-κB signaling generates spontaneous inflammatory pulses restrained by IκBα and A20 feedback.

## What the model shows

This model couples tumor necrosis factor (TNF) secretion to its own receptor pathway. NF-κB means nuclear factor kappa B, IKK is IκB kinase, and IκBα is the inhibitor that retains NF-κB outside the nucleus.

## Biological story

Basal fluctuations activate TNF receptor 1, which drives an IKK kinase cascade. IKK removes IκBα and releases NF-κB. Nuclear NF-κB induces TNF, IκBα, and A20; secreted TNF reinforces receptor signaling, while IκBα and A20 terminate it.

## Main biological players

TNF and TNFR1, IKKK, IKK, NF-κB, IκBα, A20, their transcripts, and stochastic gene switches.

## Mechanism in plain English

Receptor activation propagates through IKKK to IKK. IKK phosphorylates IκBα, causing inhibitor loss and nuclear NF-κB entry. NF-κB switches target genes on, producing new TNF plus two inhibitors. Extracellular TNF closes a positive autocrine loop; newly synthesized IκBα and A20 impose delayed negative feedback.

## Key modeled events

- TNFR1 activates the IKKK–IKK cascade.
- IKK removes IκBα and releases NF-κB.
- NF-κB induces TNF, IκBα, and A20 genes.
- Secreted TNF reinforces receptor activation.
- IκBα and A20 terminate each inflammatory episode.

## What the model measures

Readouts include receptor and kinase states, nuclear and cytoplasmic NF-κB, NF-κB–IκBα complexes, extracellular and intracellular TNF, and A20/IκBα transcripts and proteins.

## Expected behavior in plots

A spontaneous receptor event can generate an IKK pulse followed by nuclear NF-κB. TNF feedback may amplify that episode, while delayed IκBα and A20 should drive recovery and create separated pulses rather than sustained maximal activity.

## Caveats

The pulse mechanism is a reduced single-cell regulatory system. Tissue cytokine transport, immune-cell diversity, and many TNF targets are omitted.
