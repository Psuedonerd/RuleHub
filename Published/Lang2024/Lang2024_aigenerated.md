# Model Explanation: Lang 2024

## One-sentence summary

An E2F–RB1 transcriptional switch coordinates cyclin accumulation, mitotic regulators, and cell-cycle progression.

## What the model shows

This model connects the retinoblastoma protein RB1 and E2F transcription factors to cyclins, anaphase-promoting complex regulation, and mitotic entry. Abbreviations are expanded as they appear: APC/C is the anaphase-promoting complex/cyclosome, and PP2A is protein phosphatase 2A.

## Biological story

Cyclin D activity releases E2F from RB1 restraint. E2F induces cyclins E and A plus later regulators, while cyclin-dependent kinase inhibitor p21 restrains cyclin activity. Greatwall kinase and ENSA/ARPP19 inhibit PP2A, helping mitotic phosphorylation persist.

## Main biological players

E2F, RB1, cyclins D/E/A/B, p21, FOXM1, APC/C, CDC20, FZR1, FBXO5, WEE1, Greatwall/MASTL, ENSA/ARPP19, and PP2A-B55.

## Mechanism in plain English

RB1 binding suppresses E2F. Cyclin-dependent phosphorylation weakens RB1, allowing E2F-driven transcription to amplify cyclins and mitotic regulators. FOXM1 supports cyclin B and CDC20 expression. FBXO5 and FZR1 tune APC/C activity, while Greatwall-mediated inhibition of PP2A-B55 protects mitotic phosphates. Negative regulators prevent premature progression.

## Key modeled events

- Cyclin activity phosphorylates RB1 and releases E2F.
- E2F induces cyclins E/A and regulators needed later in the cycle.
- FOXM1 promotes cyclin B and CDC20 expression.
- Greatwall–ENSA/ARPP19 inhibits PP2A-B55 to sustain mitotic phosphorylation.
- APC/C regulators control exit-associated protein turnover.

## What the model measures

Primary readouts are total cyclins E, A, and B and the inhibitor p21, with internal quantities representing E2F, APC/C, phosphatase, and kinase states.

## Expected behavior in plots

Cyclin E should rise near E2F activation, followed by cyclin A and then cyclin B as the program advances. p21 can delay or flatten those waves. A successful mitotic transition should coincide with high cyclin B and suppressed PP2A-B55 activity.

## Caveats

The model is a regulatory synthesis of cell-cycle modules rather than a spatially resolved cell. Exact phase durations depend on its parameterization and starting state.
