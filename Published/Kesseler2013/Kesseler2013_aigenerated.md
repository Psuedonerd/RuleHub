# Model Explanation: Kesseler 2013

## One-sentence summary

Interlocking kinase, phosphatase, and transport controls govern commitment from the G2 checkpoint into mitosis.

## What the model shows

This detailed cell-cycle model follows activation of maturation-promoting factor (MPF), the cyclin B–CDK1 complex, together with CDC25 phosphatases, WEE1/MYT1 kinases, polo-like kinase 1 (PLK1), and checkpoint kinases.

## Biological story

Before mitosis, WEE1 and MYT1 keep MPF inhibited. CDC25 removes inhibitory phosphates, active MPF reinforces CDC25 and suppresses WEE1, and PLK1 supports the switch. CHK1 and CHK2 preserve checkpoint arrest when damage signaling is present.

## Main biological players

MPF, CDC25A/B/C, WEE1, MYT1, PLK1, CHK1, CHK2, PP2A phosphatase, PIN1, import/export factors, and histone H3.

## Mechanism in plain English

Competing enzymes write and erase inhibitory marks on MPF. Once CDC25 activity gains an advantage, MPF activation feeds back positively on its activators and negatively on its inhibitors, producing switch-like entry into mitosis. Nuclear transport changes access to regulators, while checkpoint kinases and PP2A oppose commitment. PLK1 and histone H3 phosphorylation mark progression.

## Key modeled events

- WEE1 and MYT1 impose inhibitory phosphorylation on MPF.
- CDC25 phosphatases remove inhibition and activate MPF.
- Active MPF and PLK1 reinforce CDC25 while weakening WEE1.
- CHK1/CHK2 and PP2A stabilize checkpoint restraint.
- Histone H3 phosphorylation reports mitotic entry.

## What the model measures

The extensive readouts distinguish active and localized CDC25 isoforms, WEE1 and PLK1 states, MPF-related regulators, and phosphorylated histone H3.

## Expected behavior in plots

A successful transition should show a sharp rise in active CDC25, MPF-associated positive feedback, active PLK1, and histone H3 phosphorylation, accompanied by loss of active WEE1. Checkpoint engagement should delay or suppress that coordinated switch.

## Caveats

The model is large and mechanistically annotated but not a complete cell cycle. Its many fitted or assumed rates make qualitative state ordering more secure than exact timing without reproducing the original conditions.
