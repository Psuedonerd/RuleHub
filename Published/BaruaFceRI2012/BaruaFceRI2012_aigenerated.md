# Model Explanation: BaruaFceRI 2012

## One-sentence summary

Bivalent ligand crosslinks FcεRI and drives Lyn- and Syk-dependent phosphorylation of receptor chains and the LAT adaptor across raft and non-raft membrane environments.

## What the model shows

This model focuses on the first signaling events after aggregation of the high-affinity IgE receptor FcεRI. It connects ligand-mediated receptor crosslinking to phosphorylation of the receptor β and γ chains, recruitment and activation of Syk, and phosphorylation of LAT, while explicitly distinguishing raft-localized from non-raft protein states.

## Biological story

A divalent ligand binds FcεRI and can bridge two receptors into a signaling-competent cluster. Lyn associates with receptor complexes and phosphorylates the β and γ receptor chains. Phosphorylated γ recruits Syk, which becomes activated and phosphorylates LAT; phosphorylated LAT can then recruit Grb2. Proteins can exchange between raft and non-raft states, and dephosphorylation of receptor, Syk, and LAT signals counteracts cluster-driven activation.

## Main biological players

- **Bivalent ligand and FcεRI:** the stimulus and receptor pair whose crosslinking initiates signaling.
- **Lyn:** a Src-family kinase that associates with receptor complexes and phosphorylates FcεRI chains.
- **Syk:** a kinase recruited to phosphorylated receptor γ chains and activated after binding.
- **LAT and Grb2:** a membrane adaptor and its binding partner downstream of active Syk.
- **Raft and non-raft membrane states:** alternative environments that change where receptor-proximal proteins interact.

## Mechanism in plain English

Ligand first binds one FcεRI and then captures a second receptor, producing a crosslinked pair. Lyn can associate with receptor chains in the appropriate membrane environment and add phosphate to the β and γ signaling motifs. Syk recognizes phosphorylated γ, binds the receptor, becomes phosphorylated through Lyn- and Syk-dependent steps, and then phosphorylates LAT. Phosphorylated LAT recruits Grb2 as a downstream signaling complex. Constitutive phosphatase-like removal of phosphate and movement between raft and non-raft states limit how much of each activated species accumulates.

## Key modeled events

- Bivalent ligand binds and crosslinks two FcεRI complexes, creating the receptor assemblies that support kinase activity.
- Lyn phosphorylates FcεRI β and γ signaling motifs and thereby creates docking sites for downstream proteins.
- Syk binds phosphorylated receptor γ, becomes activated, and phosphorylates LAT.
- LAT phosphorylation recruits Grb2, while dephosphorylation and raft exchange restrain the pathway.

## What the model measures

The principal readouts are phosphorylated FcεRI β, phosphorylated FcεRI γ, activated receptor-bound Syk, and phosphorylated LAT. These measurements follow the signaling sequence from receptor modification through kinase activation to adaptor phosphorylation rather than reporting a distal transcriptional or secretory response.

## Expected behavior in plots

Receptor β and γ phosphorylation should appear soon after ligand-driven crosslinking. Activated Syk should depend on phosphorylated γ and therefore follow or overlap the receptor signal, while phosphorylated LAT should appear downstream of active Syk. Raft exchange and distinct membrane versus cytosolic dephosphorylation routes can give Syk and LAT different decay profiles even when receptor phosphorylation has already begun to fall.

## Caveats

The modeled volume represents one of approximately 8,000 membrane-raft-scale subvolumes rather than a whole cell, so absolute molecule numbers require the stated scaling interpretation. The model concentrates on early phosphorylation and adaptor recruitment and does not include the full FcεRI response leading to calcium release, degranulation, or cytokine production. Raft localization is represented as a discrete state rather than a spatial membrane domain.
