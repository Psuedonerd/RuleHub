# Model Explanation: Korwek 2023

## One-sentence summary

Double-stranded non-self RNA coordinates antiviral translation arrest, RNA decay, NF-κB signaling, and interferon-β feedback.

## What the model shows

This innate-immune model links polyinosinic:polycytidylic acid, abbreviated poly(I:C), to several antiviral sensors. It integrates RIG-I–MAVS, PKR–eIF2α, OAS3–RNase L, NF-κB, and interferon regulatory factor signaling.

## Biological story

Cytoplasmic non-self RNA activates retinoic acid-inducible gene I (RIG-I), protein kinase R (PKR), and oligoadenylate synthetase 3 (OAS3). These branches inhibit translation, degrade RNA, and induce cytokines and antiviral genes, which feed back through interferon signaling.

## Main biological players

poly(I:C), RIG-I, MAVS, PKR, eIF2α, OAS3, RNase L, TAK1, IKK, NF-κB, TBK1, IRF3, interferon-β, and JAK–STAT feedback.

## Mechanism in plain English

RIG-I binds RNA and signals through mitochondrial antiviral-signaling protein (MAVS). PKR phosphorylates eukaryotic initiation factor 2α (eIF2α) to suppress translation. OAS3 activates RNase L to remove RNA. Parallel kinase routes activate nuclear factor κB (NF-κB) and interferon regulatory factor 3 (IRF3), inducing cytokines and antiviral sensor expression.

## Key modeled events

- Non-self RNA activates RIG-I, PKR, and OAS3.
- PKR phosphorylates eIF2α and reduces protein synthesis.
- OAS3 activates RNase L to accelerate RNA degradation.
- NF-κB and IRF3 induce inflammatory and interferon outputs.
- Interferon feedback raises antiviral sensor abundance.

## What the model measures

Readouts span sensor proteins and transcripts, active RNase L, phosphorylated eIF2α, nuclear NF-κB, kinase states, cytokines, and interferon-pathway outputs.

## Expected behavior in plots

Sensor activation should precede eIF2α phosphorylation and RNase L activity. Nuclear NF-κB and IRF3-dependent outputs should then rise, followed by slower interferon-driven increases in RIG-I, PKR, OAS3, and RNase L expression.

## Caveats

The model integrates many antiviral branches but still compresses RNA species, translation, and cytokine communication into population-level processes.
