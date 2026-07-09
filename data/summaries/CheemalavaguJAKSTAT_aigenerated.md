# Model Explanation: Cheemalavagu 2024

## One-sentence summary

IL-6 and IL-10 JAK/STAT signaling with STAT activation and SOCS-mediated inhibition.

## What the model shows

This model shows how IL-6 and IL-10 receptor systems activate JAK kinases and STAT transcription factors while SOCS proteins inhibit parts of the pathway. It captures pathway crosstalk because shared JAK/STAT machinery can be engaged by distinct cytokine receptors.

## Biological story

The model is useful as a mechanistic sketch of how molecular interactions create a time-dependent biological response. It is not just a list of reactions: the important behavior is how binding, activation, inhibition, degradation, or transport events combine to change the abundance of active signaling states and complexes over time.

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

## How to interpret the plots

A rising curve means that the corresponding active molecule, modified state, complex, or output is accumulating. A falling curve means it is being consumed, deactivated, degraded, released, or diluted. If two curves move in opposite directions, the model is showing a shift between biological states, such as free versus complexed receptor, inactive versus active kinase, or unmodified versus modified substrate.

## Caveats

This is an explanatory summary of the encoded mechanism, not a claim that the model is experimentally complete. When molecule names are abstract or abbreviated, the summary avoids inventing identities beyond what the model itself supports.
