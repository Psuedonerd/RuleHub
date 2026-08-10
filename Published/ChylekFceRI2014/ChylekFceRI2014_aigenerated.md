# Model Explanation: Chylek 2014 (FceRI)

## One-sentence summary

Transient exposure of two haptens on DNP-BSA controls FcεRI crosslinking and launches a Lyn/Fyn/Syk network that activates LAT–PLCγ1 and PI3K lipid signaling while PAG1–Csk and phosphatases provide restraint.

## What the model shows

This detailed early FcεRI signaling model connects dynamic antigen accessibility to receptor aggregation, Src-family kinase regulation, Syk activation, adaptor-complex assembly, and phosphoinositide conversion. It is designed to distinguish how receptor-chain phosphosites, Lyn and Fyn, PAG1–Csk inhibition, LAT scaffolding, and PI3K/PLCγ1 branches contribute to the proximal response.

## Biological story

The ligand DNP-BSA carries two virtual haptens that fluctuate between buried and exposed states. Only exposed haptens bind IgE–FcεRI, and simultaneous exposure allows one ligand to crosslink two receptors. Lyn and Fyn associate with aggregated receptors, phosphorylate receptor β and γ chains, and activate Syk. Active Syk and Fyn then build LAT-, Grb2-, Gab2-, Grap2-, Lcp2-, PI3K-, Btk-, and PLCγ1-containing complexes. In parallel, phosphorylated PAG1 recruits Csk, which adds inhibitory phosphates to Lyn and Fyn, and multiple dephosphorylation processes reset the network.

## Main biological players

- **DNP-BSA and IgE–FcεRI:** fluctuating bivalent antigen and receptor complexes whose crosslinking initiates signaling.
- **Lyn, Fyn, Syk, PAG1, and Csk:** activating kinases, scaffold, and inhibitory kinase that control receptor-proximal phosphorylation.
- **LAT, PLCγ1, Grb2, Gab2, Grap2, and Lcp2:** adaptor network that connects activated Syk to downstream enzymes.
- **PI3K, Btk, and the PIP2/PIP3 lipid pools:** lipid-signaling branch that supports PLCγ1 recruitment and activation.
- **SHIP/Inpp5d:** phosphoinositide phosphatase recruited to a phosphorylated receptor β-chain site.

## Mechanism in plain English

Hapten exposure allows DNP-BSA to bind one receptor and then crosslink a second. Lyn and Fyn dock through receptor-binding domains or phosphorylated receptor sites, acquire activating phosphates, and phosphorylate the receptor β and γ motifs. Doubly phosphorylated γ recruits Syk, which is further activated and phosphorylates LAT. LAT phosphosites recruit PLCγ1 and Grb2/Gab2 or Grap2/Lcp2 assemblies; Gab2 recruits PI3K, which converts PIP2 into PIP3, allowing Btk recruitment and Btk-dependent PLCγ1 phosphorylation. Active PLCγ1 binds PIP2 and generates IP3 and DAG. PAG1 recruits Csk to phosphorylate the inhibitory tails of Lyn and Fyn, while SHIP and other dephosphorylation reactions reduce receptor, kinase, adaptor, and lipid signals.

## Key modeled events

- DNP-BSA haptens switch between buried and exposed states, making receptor binding and crosslinking dynamically conditional on antigen accessibility.
- Lyn and Fyn phosphorylate FcεRI β and γ motifs, and phosphorylated γ recruits and activates Syk.
- Syk phosphorylates LAT, allowing PLCγ1 and multi-adaptor complexes to assemble around distinct LAT sites.
- Gab2 recruits PI3K, PIP3 recruits Btk, and Btk activates PLCγ1 to generate IP3 and DAG from PIP2.
- PAG1-bound Csk, SHIP, and dephosphorylation reactions oppose Src-family kinase, receptor, adaptor, and lipid activation.

## What the model measures

Readouts include phosphorylation of LAT, the FcεRI β and γ chains, Syk, Gab2, PLCγ1, PAG1, and the Syk activation loop; recruitment of PI3K, Btk, SHIP, and PLCγ1-containing complexes; PIP2, PIP3, PI(3,4)P2, IP3, and ligand crosslinks; Lyn and Fyn binding or autoinhibited conformations; and the number of ligand haptens that are exposed. This combination connects antigen availability to receptor activation, scaffold assembly, and lipid second-messenger production.

## Expected behavior in plots

The exposed-hapten measurements should control how rapidly free ligand is converted into receptor crosslinks. Receptor β/γ phosphorylation should precede Syk activation and LAT phosphorylation, with LAT-associated PI3K and PLCγ1 complexes appearing downstream. PIP3 and Btk recruitment should support PLCγ1 Y783 phosphorylation, after which IP3 should rise as PIP2 is consumed. PAG1 phosphorylation, Csk recruitment, Lyn/Fyn inhibitory conformations, and SHIP binding should develop as counter-signals that limit the amplitude or duration of receptor and lipid-pathway readouts.

## Caveats

The antigen is represented with two virtual haptens and the receptor includes only one of its two γ chains, simplifying actual FcεRI stoichiometry. Several pairs of nearby tyrosines are lumped into single modeled states, so the corresponding measurements do not resolve individual residues. The model focuses on early phosphorylation and lipid signaling and does not extend to calcium dynamics, degranulation, or cytokine production.
