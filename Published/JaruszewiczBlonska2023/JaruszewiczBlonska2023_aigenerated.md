# Model Explanation: Jaruszewicz-Blonska 2023

## One-sentence summary

Canonical nuclear factor κB signaling balances IKK activation with IκBα and A20 negative feedback.

## What the model shows

This identifiable pathway model focuses on the core canonical NF-κB module. NF-κB means nuclear factor kappa B, IKK is the IκB kinase complex, IκBα is its inhibitory binding protein, and A20 is a feedback inhibitor.

## Biological story

Active IKK promotes removal of IκBα, freeing NF-κB to accumulate in the nucleus. Nuclear NF-κB induces new IκBα and A20; IκBα recaptures NF-κB, while A20 restrains upstream IKK activity.

## Main biological players

IKK, IκBα protein and messenger RNA, nuclear NF-κB, and A20.

## Mechanism in plain English

IKK shifts into an active form and accelerates IκBα loss. Released NF-κB enters the nuclear pool and stimulates transcription of IκBα and A20. Newly synthesized IκBα suppresses NF-κB directly, whereas A20 weakens the activating arm. Their different production and decay times create delayed negative feedback.

## Key modeled events

- IKK becomes active and removes the IκBα brake.
- NF-κB accumulates in the nucleus after inhibitor loss.
- Nuclear NF-κB induces IκBα and A20 expression.
- IκBα and A20 shut down the response through complementary feedback routes.

## What the model measures

Readouts follow active and neutral IKK, nuclear NF-κB, IκBα protein and transcript, and A20 abundance.

## Expected behavior in plots

Active IKK should rise before nuclear NF-κB. IκBα transcript and A20 should lag behind NF-κB, then help drive NF-κB and IKK downward; depending on feedback timing, the response may pulse or show damped oscillatory structure.

## Caveats

This reduced model emphasizes identifiable core feedback and omits receptor-specific inputs, cell-to-cell spatial detail, and many NF-κB target genes.
