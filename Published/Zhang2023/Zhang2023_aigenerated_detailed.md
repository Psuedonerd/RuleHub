# Detailed Model Explanation: Zhang 2023 VEGF Receptor Trafficking and Multibranch Signaling

## 1. Model overview

This model follows VEGF165a binding to VEGFR1, VEGFR2, and neuropilin-1 (NRP1), the formation and trafficking of receptor complexes, and regulation by CD47/SIRPα and thrombospondin-1 (TSP1). Phosphorylated VEGFR2 feeds PLCγ–calcium–PKC, Src–Axl–PI3K–AKT–eNOS, and CIB1–sphingosine kinase–S1P–Ras–Raf–MEK–ERK branches, linking receptor routing to calcium, survival, nitric-oxide, and MAPK outputs.

## 2. BNGL block inventory

The model contains 180 parameters, 38 molecule types, 34 seed species, 232 logical reaction rules (318 active physical lines because many rules continue), 129 observables, and 2 actions. It has no BNGL compartments or anchors; surface, two internal stages, recycling, cytosolic, and membrane locations are represented by internal states.

## 3. Parameters, functions, and rate laws

The namespace is organized by biochemical module rather than a single rate convention. Receptor binding and trafficking mostly use mass action, whereas ligand bookkeeping, calcium fluxes, lipid conversion, and kinase cascades use observable-dependent balance, Hill, or Michaelis–Menten-like expressions; `I` is retained as a source catalyst for several continuous pool-flux approximations.

| Parameter group or names | Function in this model |
| --- | --- |
| `Volcyto`, `VolER`, `fextmolar`, `cellarea` | Convert between cytosolic, endoplasmic-reticulum, extracellular concentration, and surface-count scales in ligand and calcium flux expressions. |
| `VEGF165a_0`, `VEGFR2_0`, `VEGFR1_0`, `NRP1_0`, `TSP1_0` | Establish extracellular ligand and receptor/co-receptor pools. |
| `kvron/off`, `kvr1on/off`, `kcVR`, `kcRR`, `kdRR`, `kdeltaVR`, `kdeltaRR` | Control VEGF binding to VEGFR2/VEGFR1, ligand-independent receptor coupling, and ligand-assisted receptor dimerization. |
| `kVEGFNRP1*`, `kNRP1VEGFR1*`, `kNRP1VEGFR2*`, `kVEGFR1NRP1*`, `kVEGFR2NRP1*` | Build NRP1–VEGF and NRP1-associated VEGFR1/2 complexes in multiple assembly orders. |
| `kpr2`, `kdps`, `kdpi`, `kdpr` | Phosphorylate VEGFR2 Y1175 in ligand-crosslinked complexes and dephosphorylate it at surface, internal, or recycling states. |
| `kr2si`, `kr2ii2`, `kr2i2i`, `kr2rs`; corresponding `kr2NRP1*` | Move receptor complexes from surface to early internal, late internal, recycling, and back to surface, with NRP1-specific routing where declared. |
| `kdegi*`, `kdegr2NRP1*`, `f_TSP1deg`, `ksingleR2syn/deg/si/is` | Control phosphostate-, NRP1-, TSP1-, and location-dependent degradation plus synthesis/trafficking of single VEGFR2. |
| `kcd47free_on`, `kr2CD47off`, `kDCD47TSP1`, `koffCD47TSP1`, `CD47free_0`, `fTSP1dp`, `fTSP1i2r` | Couple CD47/SIRPα and TSP1 to VEGFR2 binding, dephosphorylation, degradation, and recycling biases. |
| `PLCgamma_0`, `kp/kdpPLCgamma`, `PIP2_0`, `kPIP2gen`, `kmPIP2PLCgamma`, `nDAG`, `kcatPLCgammaDAG`, `kdeg_ip3`, `kdeg_DAG` | Activate PLCγ from phospho-VEGFR2 and generate/clear IP3 and DAG from PIP2. |
| `Calcium_0`, `CaER_0`, `CaF_0`, `CaFbound_0`, `CaM_0`; IP3R/PMCA/SERCA/leak and buffer parameters | Set cytosolic/ER calcium pools, IP3-dependent release, plasma-membrane removal, ER uptake/leak, buffering, and calmodulin binding. |
| `ICracamp`, `Kcrac`, `Istim0`, `tau_stim`, `ncrac`, `CSQN_total`, `KCSQN` | Define store-operated calcium stimulation and ER calsequestrin buffering. |
| `Src_0`, `Axl_0`, `kp/kdpSrc`, `kpSrcAxl`, `kpAxlauto`, `kdpautoAxl`, `kdpSrcAxl` | Activate TSAD/Src from phospho-VEGFR2 and relay it through two Axl phosphorylation sites. |
| `PI3K_0`, `PTEN_0`, `PIP2_0`, `AKT_0`, `PDK1_0`, `mTOR_0`; PI3K/PTEN/PIP3/AKT kinetic terms | Convert PIP2/PIP3, recruit PDK1 and AKT, and phosphorylate AKT at S473 and T308. |
| `eNOS_0`, `kon/offCaMeNOS`, `koncaveNOS`, `koffeNOScav1`, `kcateNOSAKT`, `kdpeNOS` | Control calmodulin/caveolin binding and doubly phosphorylated AKT activation of eNOS S1177. |
| `PKC_0`, `kon/offCaPKC`, `kon/offDAGPKC`, `kcatPKC`, `kmPKCRaf` | Assemble calcium/DAG-bound PKC and phosphorylate Raf at its PKC-regulated serine. |
| `CIB1_0`, `SphK_0`, `Sph_0`, `S1P_0`; CIB1/SphK binding, transport, phosphorylation, and S1P terms | Couple calcium-loaded CIB1 and ERK2 to membrane SphK activation and sphingosine-to-S1P conversion. |
| `RasGTP_0`, `RasGDP_0`, `Raf_0`, `MEK12_0`, `ERK12_0`; Ras/Raf/MEK/ERK kinetic terms | Generate RasGTP from S1P, activate Raf, phosphorylate both MEK sites and ERK1/2, and reset each kinase. |

There are no active functions; all nonlinear calculations appear directly in rule-rate expressions.

## 4. Molecule types, sites, and states

| Molecule type(s) | Site count | Sites/components | Internal states | Anchor/allowed compartments | Explanation |
| --- | ---: | --- | --- | --- | --- |
| `vegf` | 4 | two repeated `r`, `nrp1bd`, `c` | `c`: `s/i/i2/r` | None | Bivalent VEGF165a ligand that can crosslink receptors, bind NRP1, and travel with complexes. |
| `vegfr2` | 5 | `l1`, `Y1175`, `CD47bd`, `dimer`, `c` | Y1175 `Y/pY`; `c`: `s/i/i2/r` | None | Principal signaling receptor with ligand, dimer, CD47, phosphosite, and routing information. |
| `vegfr1` | 4 | `l2`, `dimer`, `nrp1bd`, `c` | `c`: `s` | None | Competing VEGF receptor that forms homo/heterodimers and associates with NRP1. |
| `NRP1` | 2 | `vegfabd`, `c` | `c`: `s/i/i2/r` | None | Co-receptor that alters VEGFR complex assembly, degradation, and recycling. |
| `CD47SIRPa` | 4 | `VEGFR2bd`, `TSP1bd`, `Y1`, `c` | Y1 `Y/pY`; `c`: `s/i/i2/r` | None | Composite inhibitory/regulatory receptor that binds VEGFR2 and TSP1 during trafficking. |
| `TSP1` | 1 | `CD47bd` | None | None | Extracellular ligand that engages CD47/SIRPα and modifies receptor fate. |
| `PI`, `PLCgamma`, `DAG`, `IP3_cyto` | 1 each | `PIsite`; `Yplc`; `pkcbd`; `ip3rbd` | PI `3P/4P`; PLCγ `Y/pY` | None | PIP2/PIP3 and PLCγ-derived second-messenger machinery. |
| `Calcium_cyto`, `CaER`, `CaF`, `CSQNF` | 1 each | `bd`; `bd`; `cabd`; `cabd` | None | None | Cytosolic and ER calcium plus cytosolic and ER buffering species. |
| `CaM` | 5 | two repeated `NCaM`, two repeated `CCaM`, `CaMtargetbd` | None | None | Calmodulin with four explicit calcium-binding components and an effector-binding site. |
| `I`, `Istim`, `Trash` | 0 each | None | None | None | Persistent source catalyst, store-operated influx signal, and degradation sink. |
| `PTEN`, `PI3K` | 1 each | `PIP3docking`; `state` | PI3K `active/inactive` | None | Opposing PIP3 regulator and Axl-responsive lipid kinase. |
| `TSADSrc` | 1 | `Y1` | `Y/pY` | None | VEGFR2-responsive Src-like relay upstream of Axl. |
| `Axl` | 2 | `Ysrc`, `Yaxl` | each `Y/pY` | None | Two-stage receptor kinase relay that activates PI3K after Src and auto-phosphorylation. |
| `AKT` | 3 | `PHakt`, `T308`, `S473` | T308/S473 `S/pS` | None | PIP3-recruited kinase requiring two activating phosphorylations. |
| `PDK1`, `mTOR` | 2; 1 | PDK1: `PHpdk1`, `aktbd`; mTOR: `aktbd` | None | None | PIP3-recruited T308 kinase and implicit S473 kinase input. |
| `eNOS`, `caveolin1` | 3; 1 | eNOS: `CaMBD`, `S1177`, `cav1BD`; caveolin: `eNOSbd` | S1177 `S/pS` | None | Nitric-oxide synthase controlled positively by CaM/AKT and negatively by caveolin binding. |
| `PKC` | 2 | `CalciumBD`, `DAGBD` | None | None | Requires calcium and DAG contacts to phosphorylate Raf. |
| `CIB1` | 4 | `EF1`, `EF2`, `sk1bd`, `location` | `cytosol/membrane` | None | Calcium sensor that recruits SphK and transports it to the membrane. |
| `SphK`, `Sph`, `S1P` | 2; 1; 1 | SphK: `CIB1bd`, `Serk`; Sph: `skbd`; S1P: `bd` | SphK Ser `S/pS` | None | Sphingosine kinase branch generating S1P after ERK-dependent activation. |
| `RasGDP`, `RasGTP` | 1 each | `rafbd` | None | None | Inactive and active Ras pools; the model generates RasGTP directly from the S1P readout. |
| `Raf` | 4 | `mekbd`, `rasbd`, `Y1Y2`, `Spkc` | Y1Y2 `Y/pY`; Spkc `S/pS` | None | Integrates Ras-dependent tyrosine phosphorylation and PKC-dependent serine phosphorylation. |
| `MEK12` | 3 | `bd`, `S1`, `S2` | both sites `S/pS` | None | Dual-site MAPK kinase activated by multiple Raf phosphoforms. |
| `ERK1`, `ERK2` | 2 each | `MEK12bd`, `S1` or `S2` | `S/pS` | None | Terminal MAPKs; ERK2 additionally phosphorylates SphK. |

## 5. Compartments, anchors, initial species, and setup

No physical compartments or anchors are declared. Receptor and ligand state `s` represents the starting surface pool, while `i`, `i2`, and `r` encode sequential early-internal, late-internal, and recycling states; downstream proteins begin as unbound and generally unphosphorylated pools. PIP2, cytosolic and ER calcium, buffers, calmodulin, caveolin-bound basal eNOS, and inactive kinases establish the signaling substrate. Several source-catalyzed rules maintain ligand, receptor, lipid, calcium, and sphingosine pools through calculated fluxes rather than discrete synthesis reactions.

## 6. Reaction-rule inventory

**Rule-family orientation.** Rules 1–48 assemble VEGF/VEGFR/NRP1 complexes; 49–153 phosphorylate, route, recycle, degrade, and replenish receptors with CD47/TSP1 modulation; 154–174 generate PLCγ, IP3/DAG, and calcium/CaM signals; 175–198 form the Src–Axl–PI3K–AKT–eNOS branch; and 199–232 connect TSP1/CD47, PKC, CIB1/SphK/S1P, and Ras–MAPK signaling.

| Rule number(s) | Direction | Involved molecules/sites | Exact modeled change and rate logic | Role within the model |
| ---: | --- | --- | --- | --- |
| 1–6 | Reversible | Surface VEGFR1/2 `dimer`; VEGF-crosslinked receptor pairs | Form receptor homo- or heterodimers either without ligand (1–3) or within VEGF-crosslinked pairs (4–6), using basal versus ligand-assisted coupling rates. | Establishes receptor association before and after ligand crosslinking. |
| 7–16 | Reversible or source-balanced | VEGFR1, NRP1, VEGF `nrp1bd/r` | Binds VEGFR1 directly to NRP1, binds VEGF to NRP1, and adds VEGFR1/2 to NRP1-bound ligand in monomeric or dimerized receptor contexts. Source-catalyzed rule 8 balances free ligand against the measured NRP1 complex. | Permits multiple assembly orders for the co-receptor-containing signal complex. |
| 17–41 | Reversible or source-balanced | VEGF repeated `r`, VEGFR1 `l2`, VEGFR2 `l1`, NRP1 | Rules 17–35 bind one or two receptor molecules to VEGF across homo/heterodimer and NRP1 contexts; 36–41 add NRP1 to preassembled ligand–receptor complexes. | Enumerates the major surface stoichiometries without assuming a single binding sequence. |
| 42–48 | Reversible or source-balanced | VEGF and VEGFR1/2 | Balances VEGF–VEGFR1 binding and extends a singly ligated VEGFR1 into VEGFR1 homodimers or VEGFR1–VEGFR2 heterodimers, including pre-coupled receptors. | Adds VEGFR1 competition and mixed receptor complexes to the VEGFR2-focused network. |
| 49–52 | One-way | VEGF-crosslinked VEGFR2 Y1175 in `s/i/i2/r` | Changes Y1175 `Y→pY` at the same receptor phosphorylation rate in all four routing states. | Allows signaling competence to arise or persist during trafficking. |
| 53–62 | One-way | VEGFR2 Y1175; CD47/SIRPα-bound or free contexts | Dephosphorylates Y1175 at surface, internal, or recycling-specific rates; CD47/TSP1 contexts use the corresponding modifiers. | Makes receptor activity sensitive to both location and inhibitory complex composition. |
| 63–74 | Reversible | VEGF–VEGFR2 complexes with optional receptor dimer, NRP1, and one/two CD47/SIRPα partners | Moves complete complexes `s↔i`, preserving all ligand and regulatory bonds; NRP1- and TSP1-containing variants use adjusted rates. | Internalizes intact receptor assemblies rather than stripping them at the membrane. |
| 75–86 | Reversible | The same complex variants in `i/i2` | Moves early-internal complexes `i↔i2`, with separate NRP1 routing constants and retained CD47/TSP1 topology. | Creates a second sorting stage before recycling or degradation. |
| 87–96 | One-way | Late-internal NRP1/VEGFR2 complexes, optional CD47/TSP1 | Changes all complex members `i2→r`; TSP1-bound variants apply its recycling factor. | Selects late-internal complexes for the recycling route. |
| 97–104 | One-way | Free recycling VEGFR2, NRP1, CD47/SIRPα and assembled complexes | Returns free components `r→s`, releases VEGF and/or NRP1, breaks receptor dimers, and dissociates CD47 or TSP1 contacts. | Resets recycled material into surface-competent building blocks. |
| 105–128 | One-way sink | VEGF–VEGFR2 complexes in `i/i2`, with phospho/unphospho receptor, NRP1, and zero/one/two CD47 partners | Sends each enumerated topology to `Trash`; rates distinguish location, Y1175 state, and NRP1 content. | Competes degradation against receptor recycling across the combinatorial complex family. |
| 129–144 | One-way sink | The corresponding complexes with TSP1-bound CD47/SIRPα | Removes the same phosphostate/location/NRP1 variants with rates multiplied by `f_TSP1deg`. | Encodes TSP1-dependent bias toward complex degradation. |
| 145–153 | One-way or reversible | Single VEGFR2, CD47/SIRPα, receptor dimer, surface/internal states | Degrades single internal receptor with or without CD47/TSP1 (145–147), synthesizes surface receptor (148), and moves free/dimer/CD47-bound single receptor `s↔i` (149–153). | Maintains and routes receptor not incorporated into VEGF-crosslinked complexes. |
| 154–157 | One-way | PLCγ Yplc; phospho-VEGFR2 in `s/i/i2` | Catalytically changes PLCγ `Y→pY` from any signaling location, followed by dephosphorylation. | Couples receptor activity to the phosphoinositide/calcium branch. |
| 158–162 | One-way | Active PLCγ, PIP2, IP3, DAG, source catalyst | Active PLCγ consumes PIP2 to create IP3 or DAG with saturating PIP2 dependence; PIP2 is replenished and both messengers degrade. | Produces the two inputs required for calcium release and PKC activation. |
| 163–170 | Reversible binding or source-balanced flux | Cytosolic/ER calcium, CaF, `Istim`, IP3 and pump/buffer observables | Buffers cytosolic calcium and implements store-operated influx, IP3R release, PMCA export, SERCA uptake, ER leak, and calsequestrin correction through signed pool fluxes. | Approximates continuous calcium homeostasis without explicit channel molecules. |
| 171–174 | One-way association/dissociation | Repeated N- and C-lobe CaM sites; cytosolic calcium | Loads one calcium onto an available N- or C-lobe site while retaining a free calcium product, then unloads it at lobe-specific rates. | Builds calcium-bound CaM states used for eNOS and CIB1-linked signaling. |
| 175–178 | One-way | TSADSrc Y1; phospho-VEGFR2 in `s/i/i2` | Receptor catalytically changes Src `Y→pY` in three locations; Src then dephosphorylates. | Starts the Axl/PI3K branch from routed receptor. |
| 179–184 | One-way | Active Src, Axl Ysrc/Yaxl, PI3K state | Src phosphorylates Axl Ysrc, Axl auto-phosphorylates Yaxl, both sites reset independently, and Yaxl-p activates PI3K, which later inactivates. | Converts receptor/Src activity into a transient lipid-kinase signal. |
| 185–192 | One-way or reversible | PI3K/PTEN, PI `3P/4P`, PDK1/AKT PH sites, AKT S473/T308 | PI3K makes PIP3 and PTEN restores PIP2; PIP3 recruits PDK1/AKT; mTOR-dependent S473 and PDK1-dependent T308 phosphorylation produce doubly active AKT; phosphatases reset both sites. | Implements the survival/AKT arm with ordered membrane recruitment and dual phosphorylation. |
| 193–198 | Reversible or one-way | Calcium-loaded CaM, eNOS CaMBD/cav1BD/S1177, caveolin, doubly active AKT | CaM binds eNOS, CaM or S1177 phosphorylation releases caveolin, caveolin can rebind basal eNOS, AKT changes S1177 `S→pS`, and phosphatase resets it. | Integrates calcium and AKT signals at eNOS. |
| 199–204 | Source-balanced or reversible | TSP1–CD47/SIRPα, VEGFR2–CD47, PKC calcium/DAG sites | Balances TSP1 binding, binds CD47/SIRPα to VEGFR2, and independently loads PKC with calcium and DAG. | Connects extracellular inhibition to receptor fate and assembles active PKC. |
| 205–210 | Reversible or one-way | CIB1 EF1/EF2, calcium, CIB1–SphK bond/location, SphK Ser | Loads both CIB1 EF sites, binds phosphorylated SphK, and moves the complex cytosol↔membrane; calcium-free membrane CIB1 returns to cytosol. | Couples calcium to localization of the S1P-producing enzyme. |
| 208, 211–216 | One-way | Active ERK2 or PKC; SphK/Raf phosphosites; sphingosine/S1P | ERK2 phosphorylates SphK; active PKC phosphorylates Raf; both reset. Source maintains sphingosine, membrane phospho-SphK converts it to S1P, and S1P reverts to sphingosine. | Creates cross-talk from MAPK and PKC into the S1P relay. |
| 217–220 | Source-balanced or reversible/one-way | S1P, RasGTP, Raf `rasbd/Y1Y2` | S1P-dependent production and GAP loss control RasGTP; RasGTP binds Raf and enables Raf tyrosine phosphorylation, which later resets. | Converts the lipid messenger into active Raf. |
| 221–228 | One-way | Raf Y1Y2/Spkc combinations; MEK12 S1/S2 | Any signaling-competent Raf phosphoform catalyzes site-specific MEK phosphorylation with substrate saturation; separate rules dephosphorylate both MEK sites. | Integrates Ras- and PKC-derived Raf activation at the dual-site MEK node. |
| 229–232 | One-way | Doubly phosphorylated MEK12; ERK1 S1, ERK2 S2 | Active MEK phosphorylates ERK1 or ERK2 with saturating rates; each ERK resets independently. | Produces terminal MAPK outputs, including ERK2 input to SphK rule 208. |

## 7. Observables and technical readouts

| Observable(s) | Type | What is measured | Technical interpretation |
| --- | --- | --- | --- |
| `vegffrees`, `VEGFR2total`, `VEGFR2tots`, `VEGFR2toti`, `vr2s`, `vr2i`, `R2singlei`, `vr1s`, `vegfr1tots`, `NRP1totals`, `NRP1totali`, `totalnrp1` | Molecule count | Free ligand and receptor/co-receptor totals by routing state, including unligated internal single VEGFR2. | Broad totals include bound contexts unless a free site is explicitly required. |
| `NRP1frees`, `NRP1freei`, `NRP1bounds`, `NRP1boundi`, `singleNRP1totals`, `singleNRP1totali`, `nrp1s`, `nrp1r1s` | Molecule count | Free, VEGF-bound, single, and VEGFR1-associated NRP1 at surface/internal states. | Resolve the co-receptor's alternative binding and routing roles. |
| `vegfnrp1s`, `vegfnrp1i`, `vegfr1s`, `vegfr2s`, `vegfr2i`, `vegfr2total`, `NRP1VEGFR2s`, `NRP1VEGFR2i`, `vr2dimers`, `vr2dimeri` | Molecule/species count | Ligand–receptor/co-receptor complexes and receptor dimers by location. | Species-count entries refer to complete matching complexes, unlike embedding-based molecule counts. |
| `bvegfr2`, `bnrp1`, `bvegfr1`, `bvegfr1dimer`, `bvegfr2_2`, `bvegfr1_2`, `vegfbound_1`, `vegfbound_2`, `vegfbound_3`, `vegfbound_4` | Mixed molecule/species count | Alternative VEGF binding topologies. | Provide overlapping views of ligand occupancy; they should not be summed as disjoint populations. |
| `vegfr2Y1175ps`, `vegfr2Y1175pi`, `pr2Y1175total`, `vr2Y1175s`, `vr2Y1175i`, `vr2r2py1175s`, `vr2r2py1175i`, `vr2py1175s`, `vr2py1175i`, `r2singlepy1175s`, `r2singlepy1175i`, `vr1r2pY1165s` | Mixed molecule/species count | Phospho-Y1175 VEGFR2 in total, single, ligand-bound, homo/heteroreceptor, surface, or internal contexts. | Distinguish receptor activity from receptor abundance and routing. |
| `tsp1frees`, `cd47tsp1s`, `cd47s`, `phosphoAxltotal`, `phosphoAxlpSrc`, `phosphoAxlpauto`, `activeSrc` | Molecule count | TSP1/CD47 availability and Src/Axl phosphostates. | Track the inhibitory extracellular arm and the proximal PI3K-activating relay. |
| `freeDAGs`, `activePLCgamma`, `pplcgamma`, `plcgammafree`, `yplcgamma`, `PIP2`, `PIP3`, `freepip2`, `freepip3`, `freeip3cyto` | Molecule count | PLCγ state, phosphoinositides, DAG, and IP3. | Several names overlap intentionally; “freeDAGs” allows either DAG bond state because its pattern uses a bond wildcard. |
| `Cac`, `Caer`, `CaBuf_fer`, `Iopenstim`, `activePKCs`, `activePKCtot`, `CIB1mem`, `freecib1`, `calciumcib1`, `sk1bcib1` | Molecule count | Calcium pools/buffering, influx proxy, PKC assembly, and calcium-loaded CIB1. | Translate signed calcium-flux rules into experimentally interpretable pool readouts. |
| `ps473akt`, `ps308akt`, `ppAkt`, `phosphoeNOS` | Molecule count | Singly/doubly phosphorylated AKT and active eNOS. | `ppAkt` is the kinase state used by the eNOS phosphorylation rule. |
| `SphKpkc`, `SphK1`, `SphK1mempS`, `SphK1cytosol`, `activeSphK1`, `freeSK1`, `freeSK1mem`, `freeSphK1`, `pSK1`, `freesphingosin`, `S1phosphate`, `frees1p` | Molecule count | SphK phosphorylation/binding/location plus sphingosine and S1P pools. | Resolve activation and membrane delivery of the S1P-producing branch; several “free” patterns differ in whether binding or phosphorylation is constrained. |
| `rasgdpfree`, `rasgtpfree`, `gtpfreeras`, `freeraf`, `activeRafbyrastot`, `activeRafPKC`, `activeRafPKCERK1`, `activeRafPKCERK2`, `activeRafPKCERK3`, `rafY1Y2pY`, `rafY1Y2pYpS`, `rafpS`, `py1y2rafs`, `rafpkc` | Molecule count | Ras nucleotide pools and Raf tyrosine/serine phosphoforms. | Separate Ras-bound activation from PKC phosphorylation and combined Raf states. |
| `phosphoMEK12tot`, `mek12s`, `mek12ps`, `mek12ps1`, `mek12ps2`, `phosphoMEKpS1`, `phosphoMEKpS2`, `mek12s1`, `mek12s2` | Molecule count | Total and site-specific MEK12 phosphorylation/substrate pools. | Rate-law substrate observables such as `mek12s1/2` are narrower than total unphosphorylated MEK. |
| `phosphoERK1tot`, `phosphoERK2tot`, `erk1s`, `pERK1s`, `pERK2s`, `erk1ps`, `erk2ps`, `phosphoERKpS1`, `phosphoERKpS2`, `erk12s1`, `erk12s2` | Molecule count | ERK1/2 unphosphorylated and phosphorylated pools under several pattern constraints. | Report terminal MAPK activation and provide substrate denominators for saturating rules. |
| `freepip3`, `freeSphK1`, `frees1p`, `gtpfreeras`, `Iopenstim` | Molecule count | Free metabolic/signaling pools reused directly in rate expressions. | These repeated regulatory readouts are highlighted because changing their pattern semantics changes multiple nonlinear fluxes. |

## 8. Actions and simulation workflow

The file generates the reaction network with aggregate size capped at 10 and then exports the resulting network as SBML. It does not run a trajectory itself; the many trafficking states, continuous source-flux expressions, and nonlinear calcium/kinase rates are intended for simulation by an SBML-capable downstream solver.

## 9. Technical caveats and ambiguities

- The model has 232 logical rules but 318 active physical lines because continued patterns span lines; grouped rule numbers here follow complete reactions.
- Surface/internal/recycling and cytosol/membrane labels are internal states, not BNGL compartments, so spatial volume effects occur only where explicitly included in rate expressions.
- Many observables overlap substantially and mix `Molecules` with `Species`; summing them can double-count embeddings or complexes.
- Several source-catalyzed rules use signed rates to approximate continuous pool fluxes. Their direction and positivity depend on the current observables rather than a simple irreversible chemical event.
- The receptor-trafficking inventory groups repetitive topology variants, but every rule range preserves distinctions in NRP1, CD47/SIRPα, TSP1, phosphostate, and routing state that determine the chosen rate.
- The `CaM` type repeats both N- and C-lobe components, so pattern matching can create symmetry/embedding multiplicities that should be checked in generated reactions.
