# Model Explanation: Mitra 2019 Rab conversion

## One-sentence summary

EGFR trafficking drives a Rab5-to-Rab7 endosomal identity switch through coordinated GEF and GAP recruitment.

## What the model shows

This model connects epidermal growth factor receptor (EGFR) endocytosis to Rab-family GTPase control. GEF means guanine nucleotide exchange factor, and GAP means GTPase-activating protein.

## Biological story

Activated, ubiquitinated EGFR enters endosomes and recruits Rab5 activators. Rab5-GTP establishes early-endosome identity, then recruits the MON1–CCZ1 complex that activates Rab7. Rab7 and GAP activity displace Rab5 as the compartment matures toward degradation.

## Main biological players

EGFR, Rab5, Rab7, Rabex5/RABGEF1, RIN1, Rabaptin/RABEP1, SGSM3, MON1, CCZ1, and a digestion endpoint.

## Mechanism in plain English

Receptor activation and ubiquitination recruit exchange factors that load Rab5 with GTP. Rab5-GTP recruits effectors and the MON1–CCZ1 Rab7 GEF. Rab7 activation rises as SGSM3 accelerates Rab5 GTP hydrolysis, producing an ordered identity transition. Mature endosomes deliver EGFR to digestion.

## Key modeled events

- Activated EGFR is internalized and ubiquitinated.
- Rab5 GEFs create Rab5-GTP on the early endosome.
- Rab5 recruits MON1–CCZ1, which activates Rab7.
- SGSM3 inactivates Rab5 as Rab7 identity increases.
- Mature endosomes deliver EGFR toward digestion.

## What the model measures

Readouts track total, phosphorylated, and ubiquitinated EGFR; free and bound Rab5 states; catalytic GEF complexes; free and endosomal Rab7-GTP; and recruited SGSM3 GAP.

## Expected behavior in plots

Rab5-GTP and its effector complexes should rise early after EGFR entry. MON1–CCZ1 recruitment should precede Rab7-GTP, while SGSM3 should accompany decline of Rab5 activity. EGFR digestion should be the latest event.

## Caveats

The selected wild-type member belongs to a perturbation collection. Organelle geometry and many additional Rab effectors are omitted.
