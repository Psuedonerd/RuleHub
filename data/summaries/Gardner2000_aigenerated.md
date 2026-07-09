# Model Explanation: Gardner 2000

## One-sentence summary

A bistable genetic toggle switch made from two mutually repressing gene products.

## What the model shows

This model shows how two genes that repress each other can create a memory-like switch. Depending on the starting condition, one gene product remains high while the other remains low, or the reverse state is maintained.

## Biological story

The model is useful as a mechanistic sketch of how molecular interactions create a time-dependent biological response. It is not just a list of reactions: the important behavior is how binding, activation, inhibition, degradation, or transport events combine to change the abundance of active signaling states and complexes over time.

## Main biological players

Two abstract gene products, mutual repression, cooperative promoter control, and first-order degradation.

## Mechanism in plain English

Each gene product inhibits production of the other. Because repression is cooperative, intermediate states can be unstable: a small bias toward one product pushes the system toward a stable state dominated by that product. Degradation prevents unbounded accumulation and sets the time scale.

## Key modeled events

- Each gene product represses production of the other, creating mutual antagonism.
- Cooperative repression makes intermediate states unstable, so the system tends to commit to one dominant gene-expression state.
- Protein degradation prevents unlimited accumulation and helps set the time scale for switching or maintenance.

## What the model measures

The readouts track the two gene-product levels. The model shows bistability: two stable expression states separated by an unstable boundary.

## How to interpret the plots

A rising curve means that the corresponding active molecule, modified state, complex, or output is accumulating. A falling curve means it is being consumed, deactivated, degraded, released, or diluted. If two curves move in opposite directions, the model is showing a shift between biological states, such as free versus complexed receptor, inactive versus active kinase, or unmodified versus modified substrate.

## Caveats

This is an explanatory summary of the encoded mechanism, not a claim that the model is experimentally complete. When molecule names are abstract or abbreviated, the summary avoids inventing identities beyond what the model itself supports.
