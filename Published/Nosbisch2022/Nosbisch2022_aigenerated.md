# Model Explanation: Nosbisch 2022

## One-sentence summary

RTK binding, Tyr783 phosphorylation, and intramolecular SH2 engagement govern PLCγ1 activation and shutoff.

## What the model shows

This compact model separates receptor recruitment of PLCγ1 from its internal activation switch. It tracks how an RTK captures inactive or active PLCγ1, promotes Tyr783 phosphorylation, and enables an intramolecular interaction that relieves autoinhibition, followed by dephosphorylation and return to the inactive state.

## Biological story

PLCγ1 begins largely inactive in the cytosol. A phosphorylated RTK recruits it through the N-terminal SH2 domain. Tyr783 becomes phosphorylated, can engage the C-terminal SH2 domain internally, and helps shift the catalytic core toward activity. Reversal steps disengage the internal contact and reset PLCγ1.

## Main biological players

Phosphorylated RTK, PLCγ1 N- and C-terminal SH2 domains, Tyr783, and the inactive/active PLCγ1 core.

## Mechanism in plain English

RTK captures PLCγ1 and holds it near the receptor. Bound PLCγ1 is phosphorylated at Tyr783. The phosphorylated tyrosine associates internally with the C-terminal SH2 domain, competing with an autoinhibitory core contact and favoring the active conformation. PLCγ1 can detach, lose Tyr783 phosphorylation, close its inhibitory contact, and return to inactivity.

## Key modeled events

- Phosphorylated RTK recruits PLCγ1 through its N-terminal SH2 domain.
- Receptor-bound PLCγ1 becomes phosphorylated at Tyr783.
- Tyr783 engages the C-terminal SH2 domain and favors catalytic-core activation.
- Dephosphorylation and inhibitory reclosure return PLCγ1 to the inactive pool.

## What the model measures

Readouts separate total PLCγ1, active and inactive forms, Tyr783 phosphorylation, RTK-bound PLCγ1, inactive receptor complexes, and cytosolic inactive PLCγ1.

## Expected behavior in plots

RTK-bound inactive PLCγ1 should rise early, followed by Tyr783 phosphorylation and active PLCγ1. As dissociation, dephosphorylation, and reclosure proceed, receptor-bound and active curves should fall while inactive cytosolic PLCγ1 recovers.

## Caveats

The model focuses on the PLCγ1 conformational switch. It does not include phospholipid hydrolysis, calcium release, PKC activation, or broader RTK signaling.
