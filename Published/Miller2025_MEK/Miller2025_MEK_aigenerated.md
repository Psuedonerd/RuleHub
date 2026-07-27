# Model Explanation: Miller 2025 MEK1 N78G

## One-sentence summary

The MEK1 N78G variant reshapes ERK amplitude and duration through MEK1–MEK2 heterodimerization and negative feedback.

## What the model shows

This selected variant follows the epidermal growth factor receptor (EGFR)–RAS–RAF–MEK–ERK cascade. MEK denotes mitogen-activated protein kinase kinase, and ERK denotes extracellular signal-regulated kinase.

## Biological story

EGFR activates RAS and RAF, which phosphorylate MEK1 and MEK2. MEK heterodimers transmit signal to ERK, while active ERK feeds back to receptor-proximal components and MEK1. The N78G substitution is represented in the MEK1 branch.

## Main biological players

EGFR, SOS1, RAS, RAF, MEK1 N78G, MEK2, ERK, phosphatase, source and sink pools.

## Mechanism in plain English

Ligand-activated EGFR recruits SOS1 to activate RAS. RAS activates RAF, which modifies MEK isoforms; MEK then activates ERK. MEK1 and MEK2 associate, allowing isoform state to influence output. ERK feedback phosphorylates upstream components and helps limit signal duration.

## Key modeled events

- EGFR–SOS1 activates RAS and RAF.
- RAF phosphorylates MEK1 N78G and MEK2.
- MEK isoforms heterodimerize and activate ERK.
- Active ERK feeds back on SOS1, EGFR, and MEK1.

## What the model measures

Readouts include phosphorylated SOS1 and EGFR, doubly phosphorylated ERK, activated MEK1 and MEK2, and their combined active pool.

## Expected behavior in plots

EGFR and SOS1 modification should precede MEK and ERK activation. The N78G-dependent MEK1 trajectory can be compared with MEK2 to see whether heterodimerization changes ERK peak height or persistence; feedback should eventually reduce upstream drive.

## Caveats

This is one optimized perturbation from a multi-variant collection. Interpretation of the N78G effect requires comparison with wild type and other fitted variants.
