# Model Explanation: Cheemalavagu 2024

## One-sentence summary

IL-6 and IL-10 JAK/STAT signaling with STAT activation and SOCS-mediated inhibition.

## What the model shows

This model shows how IL-6 and IL-10 receptor systems activate JAK kinases and STAT transcription factors while SOCS proteins inhibit parts of the pathway. It captures pathway crosstalk because shared JAK/STAT machinery can be engaged by distinct cytokine receptors.

## Biological story

Cheemalavagu JAK/STAT is a cytokine-crosstalk story. IL-6 and IL-10 use receptor/JAK assemblies to activate STATs, while SOCS proteins form inducible brakes that can reshape subsequent signaling.

## Main biological players

IL-6, IL-10, their receptors, JAK1, JAK2, STAT1, STAT3, SOCS1, and SOCS3.

## Mechanism in plain English

Cytokines bind their receptors, receptor complexes recruit JAK proteins, and JAK-bound complexes phosphorylate STAT1 or STAT3. Phosphorylated STATs leave receptor complexes and represent activated transcription-factor output. SOCS proteins bind JAK- or receptor-associated complexes and reduce further STAT activation.

## Key modeled events

- IL-6 and IL-10 first assemble receptor complexes that can recruit JAK kinases.
- JAK-associated receptor complexes phosphorylate STAT1 or STAT3, producing the activated transcription-factor signal.
- SOCS proteins bind pathway components and inhibit further signaling, creating cytokine-induced negative regulation.

## What the model measures

The readouts track cytokine-receptor complexes, phosphorylated STAT1 and STAT3, inhibited receptor/JAK complexes, and SOCS-associated states. The model shows how cytokine stimulation can be amplified through STAT phosphorylation and restrained by inducible inhibitors.

## Expected behavior in plots

Plots should compare phosphorylated STAT1/STAT3 with SOCS-associated inhibition. STAT activation followed by SOCS buildup suggests a pulse-like response with delayed negative regulation.

## Caveats

The model focuses on JAK/STAT activation and inhibition. It does not automatically describe all transcriptional genes downstream of STAT1 or STAT3.
