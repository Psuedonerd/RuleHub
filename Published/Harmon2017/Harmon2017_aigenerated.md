# Model Explanation: Harmon 2017

## One-sentence summary

Repeated antigen pulses activate an FcεRI–Syk–PIP3 degranulation pathway whose second response is restrained by the inducible SHIP1 cofactor X.

## What the model shows

This model shows how the interval between two antigen challenges can change FcεRI responsiveness. It focuses on a compact positive arm in which receptor-bound Syk produces PIP3 and a delayed negative arm in which receptor signaling activates X, allowing SHIP1 to clear PIP3 before a later challenge.

## Biological story

Antigen binds FcεRI and promotes phosphorylation of the receptor's β and γ signaling chains. The γ chain recruits Syk, which builds the PIP3 signal that drives degranulation, while the β chain recruits SHIP1. Receptor activity also turns X into an active cofactor; once X joins SHIP1, the complex removes PIP3. X can switch off or be degraded, allowing sensitivity to recover during sufficiently long antigen-free intervals.

## Main biological players

- **Antigen and FcεRI:** the stimulus and its receptor, with β- and γ-chain phosphorylation represented together.
- **Syk:** the receptor-recruited kinase that produces the positive PIP3 signal.
- **SHIP1 and X:** a two-input inhibitory module; SHIP1 must be receptor-associated and X-bound to provide induced PIP3 clearance.
- **PIP3:** the central signaling intermediate balancing Syk-dependent production and phosphatase-dependent removal.
- **Degranulation reporter:** a finite intracellular pool converted to an output state by PIP3.

## Mechanism in plain English

Antigen occupancy phosphorylates FcεRI and opens separate docking sites for Syk and SHIP1. Recruited Syk continuously produces PIP3, and PIP3 converts the degranulation reporter into its released-output state. In parallel, phosphorylated receptor activates X; active X binds receptor-associated SHIP1 and enables it to consume PIP3. Basal PIP3 degradation, X deactivation, and X degradation determine how rapidly the circuit loses memory of the first pulse and how strongly it responds when antigen returns.

## Key modeled events

- Antigen binds FcεRI, and the occupied receptor becomes phosphorylated on its β and γ signaling chains.
- Syk binds the phosphorylated γ chain and produces PIP3, which drives accumulation of the degranulation output.
- SHIP1 binds the phosphorylated β chain, while receptor signaling independently converts X into its active form.
- Active X joins receptor-bound SHIP1, creating an induced PIP3-clearing complex that can suppress a later antigen response.

## What the model measures

The readouts distinguish total and free antigen, bound and free receptor, phosphorylated and unphosphorylated receptor, recruited Syk, fully assembled SHIP1–X complexes, and the total PIP3 pool. Additional measurements separate total X, free active X, SHIP1-bound X, and accumulated degranulation, making it possible to relate recovery of the inhibitory cofactor to the response to a second pulse.

## Expected behavior in plots

During the first five-minute antigen pulse, receptor occupancy and phosphorylation should increase, followed by recruited Syk, PIP3, and degranulation. Active X and SHIP1–X complexes provide a delayed opposing response, so PIP3 need not simply track receptor occupancy. After antigen withdrawal, receptor signaling and PIP3 should subside while X deactivates or is degraded. A short wash interval should retain more inhibitory memory and produce a more restrained second degranulation response than a long wash interval, whereas the 120- and 240-minute conditions allow more recovery before rechallenge.

## Caveats

Antigen is treated as a fixed bath concentration rather than a depletable molecular pool. FcεRI β and γ phosphorylation switch together, Syk activity is represented by receptor recruitment, and X is an abstract fitted cofactor rather than an identified molecule. Degranulation is represented by conversion of a finite reporter pool and is reset before each second-pulse comparison.
