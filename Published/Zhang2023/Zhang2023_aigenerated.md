# Model Explanation: Zhang 2023

## One-sentence summary

VEGF165a signaling through VEGFR1, VEGFR2, and neuropilin-1 couples receptor trafficking to calcium, AKT–eNOS, sphingosine-1-phosphate, and MAPK responses that are reshaped by CD47 and thrombospondin-1.

## What the model shows

The model shows how the composition and location of vascular endothelial growth factor (VEGF) receptor complexes can influence several downstream signaling branches at once. It distinguishes VEGFR2 signaling from VEGFR1 competition, includes neuropilin-1 (NRP1) as a co-receptor that alters complex assembly and routing, and lets CD47/SIRPα and thrombospondin-1 (TSP1) change receptor dephosphorylation, recycling, and degradation.

## Biological story

VEGF165a can engage VEGFR1, VEGFR2, and NRP1 in several orders, producing receptor monomers, homodimers, heterodimers, and co-receptor-containing complexes at the cell surface. Ligand-crosslinked VEGFR2 becomes phosphorylated and can continue signaling as complexes move through early internal, later internal, and recycling states. Some complexes return to the surface, whereas others are degraded; association with NRP1, CD47/SIRPα, or TSP1 changes this balance. The surviving phospho-VEGFR2 signal is distributed among second-messenger, survival, nitric-oxide, and MAPK pathways.

## Main biological players

- **VEGF165a, VEGFR1, and VEGFR2:** ligand and receptors that compete, crosslink, dimerize, signal, and traffic.
- **NRP1, CD47/SIRPα, and TSP1:** extracellular and membrane regulators that alter receptor-complex composition and fate.
- **PLCγ, PIP2, IP3, DAG, calcium, calmodulin, and PKC:** the second-messenger branch connecting phospho-VEGFR2 to calcium release and PKC activity.
- **TSAD/Src, Axl, PI3K, PTEN, PDK1, mTOR, AKT, eNOS, and caveolin-1:** the survival and nitric-oxide branch.
- **CIB1, sphingosine kinase, sphingosine-1-phosphate, Ras, Raf, MEK, and ERK:** the lipid-to-MAPK branch that also feeds back to sphingosine kinase.

## Mechanism in plain English

VEGF165a first binds one or two receptor molecules and may also recruit NRP1, while receptors can associate before or after ligand engagement. Ligand-linked VEGFR2 is phosphorylated at its signaling tyrosine and activates PLCγ from the surface or internal states. PLCγ converts PIP2 into IP3 and DAG: IP3 promotes calcium release from the endoplasmic-reticulum pool, and calcium plus DAG assembles active PKC. In parallel, phospho-VEGFR2 activates TSAD/Src and Axl, which activates PI3K; PIP3 then recruits PDK1 and AKT so AKT can acquire both activating phosphorylations and stimulate eNOS. Calcium-loaded CIB1 moves sphingosine kinase toward the membrane, where phosphorylated sphingosine kinase produces sphingosine-1-phosphate and supports Ras–Raf–MEK–ERK signaling. Throughout this process, receptor internalization, recycling, dephosphorylation, and degradation determine how long each branch remains supplied with active VEGFR2.

## Key modeled events

- VEGF165a assembles VEGFR1, VEGFR2, and NRP1 into alternative monomeric, homodimeric, and heterodimeric complexes rather than following one fixed binding order.
- VEGFR2 phosphorylation persists across surface and internal trafficking states, while complex-specific dephosphorylation, recycling, and degradation compete to terminate or restore signaling.
- PLCγ produces IP3 and DAG, linking active VEGFR2 to endoplasmic-reticulum calcium release, calcium buffering and pumping, and calcium/DAG-dependent PKC assembly.
- Src and Axl activate the PI3K–PIP3–AKT pathway, allowing doubly phosphorylated AKT and calcium-bound calmodulin to promote eNOS activation.
- Calcium/CIB1 and ERK activate sphingosine kinase, whose sphingosine-1-phosphate output promotes Ras–Raf–MEK–ERK signaling and connects the calcium and MAPK branches.

## What the model measures

The receptor-level readouts distinguish free VEGF, free and bound NRP1, VEGFR1- and VEGFR2-containing complexes, receptor dimers, surface versus internal receptor pools, and phosphorylated VEGFR2 in several complex contexts. Downstream measurements include active PLCγ, PIP2 and PIP3, IP3 and DAG, cytosolic and endoplasmic-reticulum calcium, active PKC, phosphorylated Src and Axl, singly and doubly phosphorylated AKT, phosphorylated eNOS, membrane-associated or phosphorylated sphingosine kinase, sphingosine-1-phosphate, RasGTP, Raf phosphoforms, and phosphorylated MEK and ERK.

## Expected behavior in plots

After VEGF engagement, ligand-bound receptor complexes and VEGFR2 phosphorylation should rise before or alongside the redistribution of receptor material from the surface into early and later internal pools. Recycling can restore surface VEGFR2 and NRP1, whereas TSP1-associated CD47/SIRPα complexes are expected to favor faster signal loss through enhanced dephosphorylation or degradation. Active PLCγ should precede increases in IP3, DAG, and cytosolic calcium; calcium and DAG together should support active PKC. PIP3 should accompany phosphorylation of AKT at S473 and T308, with doubly phosphorylated AKT preceding phosphorylated eNOS. Sphingosine-1-phosphate and RasGTP should feed the later Raf–MEK–ERK response, so phospho-MEK and phospho-ERK may lag behind proximal receptor and calcium readouts.

## Caveats

The model represents surface, internal, and recycling locations as discrete molecular labels rather than spatially resolved cellular regions. Its receptor section deliberately enumerates many overlapping complex topologies, so similarly named receptor measurements are not mutually exclusive populations. Calcium transport and several ligand or metabolite pools are represented by calculated net fluxes, and the generated network is exported for downstream simulation rather than being simulated directly here. The pathway integrates VEGFR trafficking, calcium, eNOS, sphingolipid, and MAPK mechanisms at substantial breadth, but it does not establish that every parameterized interaction has equal experimental support.
