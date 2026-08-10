# Model Explanation: Hat 2016

## One-sentence summary

DNA damage engages a feedback-rich p53 network that can favor repair-associated arrest or Bax–caspase-mediated death.

## What the model shows

This model connects DNA double-strand breaks to ataxia-telangiectasia mutated kinase (ATM), p53 stabilization, Mdm2 feedback, phosphatase control, cell-cycle arrest, and apoptosis. It is designed to show how feedback strength and damage duration can move the same network among recovery, oscillatory, arrest, and death-associated regimes.

## Biological story

Irradiation creates DNA damage and activates ATM. ATM modifies p53 and its regulator Mdm2, while p53 induces Mdm2 and Wip1 as negative feedback. In parallel, p53 induces PTEN and p21 to oppose growth and cell-cycle progression, or Bax to engage the mitochondrial death module when the damage response becomes sufficiently strong.

## Main biological players

DNA double-strand breaks, ATM, p53, Mdm2, Wip1, SIAH1, HIPK2, PTEN, PI3K–AKT signaling, p21, cyclin E, Rb–E2F1, Bax, BclXL, Bad, 14-3-3, and caspase.

## Mechanism in plain English

Damage activates ATM, which stabilizes and phosphorylates p53. p53-dependent transcription produces Mdm2 and Wip1, which suppress p53 and ATM, forming delayed negative feedback. p53 also raises PTEN and p21, restraining AKT and cyclin E and reinforcing arrest. A stronger p53 modification state induces Bax; free Bax promotes caspase activation unless it is sequestered by BclXL, with Bad phosphorylation controlling that protection.

## Key modeled events

- DNA damage activates ATM and raises modified p53.
- p53 induces Mdm2 and Wip1, which feed back on p53 and ATM.
- The PTEN–AKT and p21–cyclin E branches support growth restraint and cell-cycle arrest.
- HIPK2-associated p53 modification favors Bax expression and caspase activation.
- BclXL, Bad, and 14-3-3 tune whether Bax remains available to promote death.

## What the model measures

Readouts span damage and ATM, distinct p53 modification states, Mdm2/Wip1 feedback, PTEN–AKT signaling, the p21–cyclin E–Rb–E2F1 arrest module, and Bax/BclXL/Bad/caspase death states.

## Expected behavior in plots

After irradiation, ATM and arrest-associated p53 should rise before the induced Mdm2 and Wip1 brakes. Repairable damage can yield p53 pulses and recovery; sustained damage should maintain the high p53 “kill” state, increase Bax and active caspase, and separate the death trajectory from the p21-dominated arrest trajectory.

## Caveats

The network is broad but still coarse-grains repair, transcription, and cell fate into selected modules. Its fate boundaries depend strongly on irradiation settings and parameters and should not be interpreted as universal thresholds.
