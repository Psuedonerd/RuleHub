# Model Explanation: Lin 2019 ERK model

## One-sentence summary

EGF receptor activation propagates through SOS, RAS, RAF, MEK, and ERK with feedback-sensitive signaling dynamics.

## What the model shows

This model follows the epidermal growth factor (EGF) receptor to extracellular signal-regulated kinase (ERK) and was used to compare stochastic scaling methods. SOS is Son of Sevenless, a RAS nucleotide-exchange factor.

## Biological story

Activated EGFR recruits SOS, which converts RAS from GDP- to GTP-bound form. RAS activates RAF, RAF activates MEK, and MEK activates ERK. GAP proteins and phosphatases reset the cascade, while feedback changes SOS activity.

## Main biological players

EGF, EGFR, SOS, RAS, RAS-GAP, RAF, MEK, ERK, and pathway phosphatases.

## Mechanism in plain English

Ligand activates EGFR and creates an SOS docking platform. SOS promotes guanosine triphosphate (GTP) loading of RAS; RAS-GTP recruits the RAF kinase, which passes activity through MEK to ERK. GTPase-activating protein (GAP) accelerates RAS shutoff, and phosphatases reverse kinase phosphorylation.

## Key modeled events

- EGF activates EGFR and recruits SOS.
- SOS loads RAS with GTP, while RAS-GAP promotes inactivation.
- RAS activates RAF, followed by MEK and ERK phosphorylation.
- Phosphatases and feedback restrain cascade duration.

## What the model measures

Representative readouts include inactive ERK, RAS-GTP bound to RAS-GAP, EGFR–SOS complexes, and EGFR–SOS complexes carrying active RAS.

## Expected behavior in plots

Receptor–SOS complexes should form before RAS-GTP and downstream ERK activation. GAP-bound RAS should follow RAS activation, while phosphatases should eventually restore inactive ERK; feedback can make the response transient rather than sustained.

## Caveats

This summary describes the mechanistic ERK variant selected from a three-model collection. The model was also designed for simulation-scaling studies, not solely biological calibration.
