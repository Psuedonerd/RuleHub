# Model Explanation: Erdem 2021

## One-sentence summary

IGF1–IGF1R and insulin–InsR signaling split into Ras–Raf–MEK–ERK and IRS–PI3K–PDK1–Akt–mTOR–RPS6K branches that inhibit one another through multiple feedback routes.

## What the model shows

This model represents early insulin receptor (InsR) and insulin-like growth factor 1 receptor (IGF1R) signaling in an MCF7-cell context. It compares how the two ligand–receptor pairs activate shared MAPK and Akt/mTOR pathways and how ERK, Akt, and RPS6K feedback suppresses intermediates, generating adaptation and cross-pathway control.

## Biological story

IGF1 binds IGF1R and insulin binds InsR; each occupied receptor becomes phosphorylated and can then activate IRS and SOS. SOS drives Ras, Raf, MEK, and ERK, whereas IRS drives PI3K, PDK1, Akt, TSC2, mTOR, and RPS6K. The branches are not independent: active ERK inhibits SOS, MEK, IRS, and Akt; active Akt inhibits Raf and IRS; and active RPS6K inhibits IRS. Inhibited intermediates can recover, and activated receptors are internalized and recycled to an unphosphorylated surface-ready state.

## Main biological players

- **IGF1, insulin, IGF1R, and InsR:** two specific ligand–receptor inputs that feed shared intracellular pathways.
- **IRS and SOS:** receptor-proximal intermediates that launch the Akt/mTOR and MAPK branches.
- **Ras, Raf, MEK, and ERK:** the mitogen-activated protein kinase cascade.
- **PI3K, PDK1, Akt, TSC2, mTOR, and RPS6K:** the growth and protein-synthesis signaling branch.
- **Feedback and recycling states:** reversible inhibition of pathway intermediates and return of internalized receptors.

## Mechanism in plain English

Each ligand binds only its matching receptor. Ligand-bound IGF1R or InsR becomes phosphorylated and catalytically activates IRS and SOS. Active SOS loads Ras with GTP, allowing Ras to activate Raf, Raf to phosphorylate MEK, and MEK to phosphorylate ERK. Active IRS separately activates PI3K and then PDK1 and Akt; Akt phosphorylates TSC2, enabling mTOR and RPS6K activation. Constitutive reversal reactions remove activation marks, while active ERK, Akt, and RPS6K add inhibitory states to selected upstream or parallel components. These inhibited proteins later recover, and receptor internalization followed by ligand loss returns unphosphorylated receptor to the responsive pool.

## Key modeled events

- IGF1 activates IGF1R and insulin activates InsR, with no cross-binding between the two ligand–receptor pairs.
- Phosphorylated receptors activate both IRS and SOS, splitting the signal toward Akt/mTOR and Ras/ERK.
- The IRS–PI3K–PDK1–Akt branch relieves TSC2 restraint and activates mTOR and RPS6K.
- ERK, Akt, and RPS6K inhibit multiple upstream intermediates, producing feedback within and between the two branches.
- Activated receptors internalize and recycle after ligand removal, restoring unphosphorylated receptor availability.

## What the model measures

The four principal readouts are total phosphorylated surface IGF1R and InsR, phosphorylated Akt, phosphorylated RPS6K, and phosphorylated ERK. They report proximal receptor activation, activity in the PI3K/Akt arm, output from the mTOR branch, and output from the MAPK branch, respectively.

## Expected behavior in plots

IGF1 or insulin stimulation should first increase phosphorylated surface receptor, followed by Akt, ERK, and RPS6K activation through their respective cascades. Akt and ERK need not follow identical time courses because they arise from different receptor-proximal intermediates and inhibit different targets. RPS6K should lag behind Akt because it lies downstream of TSC2 and mTOR. As ERK-, Akt-, and RPS6K-mediated feedback accumulates and receptors internalize, pathway outputs may peak and adapt even while ligand remains present; recovery and receptor recycling can restore later responsiveness.

## Caveats

The model includes one activation site per receptor and omits basal receptor phosphorylation, making receptor activation deliberately coarse. It captures signaling behavior fitted to MCF7-cell RPPA measurements but does not represent all receptor substrates, phosphosites, trafficking compartments, or transcriptional consequences. IGF1R and InsR share downstream mechanisms here, so receptor-specific biology beyond their ligand binding and fitted rates is limited.
