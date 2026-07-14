# Coder Model Explanation: Zhang 2023

## 1. Model identity and scope

- **Model id:** `Zhang_2023`
- **Title:** Zhang 2023
- **BNGL path:** `Published/Zhang2023/Zhang_2023.bngl`
- **YAML path:** `Published/Zhang2023/metadata.yaml`
- **Metadata description:** VEGF signaling
- **Scope:** A large VEGF signaling model centered on VEGF165a, VEGFR2, VEGFR1, NRP1, CD47/TSP1, PI3K/AKT, PLCγ/IP3/DAG/calcium, eNOS, PKC/CIB1/SphK/S1P, Ras/Raf/MEK/ERK, and Axl/Src cross-talk. It is long but still smaller than Dolan2015, with hundreds of explicit rules and no declared compartments or anchors.

## 2. BNGL block inventory

| Block | Present? | Count / role |
| --- | --- | --- |
| Parameters | Yes | 180 parameter entries. |
| Compartments | No | 0 compartment entries. |
| Anchors | No | 0 anchor entries. |
| Molecule types | Yes | 38 molecule type entries. |
| Seed/species | Yes | 34 initial species entries. |
| Observables | Yes | 129 observable entries. |
| Functions | No | 0 function entries. |
| Reaction rules | Yes | 232 reaction rules. |
| Actions | Yes | 1 action or inline execution commands. |

## 3. Parameters, functions, and rate laws

The model uses the following parameter entries. Comment text is preserved when the source provides it; otherwise the role is inferred from the parameter name and where it is used.

| Parameter | Value/expression | Role / source comment |
| --- | --- | --- |
| `Volcyto` | `9.12E-13` | Geometry/scaling parameter. |
| `VolER` | `3.35E-13` | Geometry/scaling parameter. |
| `fextmolar` | `1.205E+15` | Model parameter used by rules, functions, species, or observables. |
| `cellarea` | `1400` | Geometry/scaling parameter. |
| `VEGF165a_0` | `0.0012` | Initial amount or baseline condition parameter. |
| `VEGFR2_0` | `4.29E+00` | Initial amount or baseline condition parameter. |
| `VEGFR1_0` | `1.43` | Initial amount or baseline condition parameter. |
| `NRP1_0` | `2.86E+01` | Initial amount or baseline condition parameter. |
| `TSP1_0` | `0.00E+00` | Initial amount or baseline condition parameter. |
| `Calcium_0` | `0.05` | Initial amount or baseline condition parameter. |
| `CaM_0` | `1` | Initial amount or baseline condition parameter. |
| `eNOS_0` | `0.1` | Initial amount or baseline condition parameter. |
| `kvron` | `10.3` | Kinetic rate or kinetic expression parameter. |
| `kvroff` | `2.36E-01` | Kinetic rate or kinetic expression parameter. |
| `kcVR` | `0.0045` | Kinetic rate or kinetic expression parameter. |
| `kcRR` | `1.11` | Kinetic rate or kinetic expression parameter. |
| `kdRR` | `0.78` | Kinetic rate or kinetic expression parameter. |
| `kvr1on` | `22` | Kinetic rate or kinetic expression parameter. |
| `kvr1off` | `0.026` | Kinetic rate or kinetic expression parameter. |
| `kdeltaRR` | `2.5` | Kinetic rate or kinetic expression parameter. |
| `kdeltaVR` | `2.05` | Kinetic rate or kinetic expression parameter. |
| `kpr2` | `30` | Kinetic rate or kinetic expression parameter. |
| `kdps` | `640` | Kinetic rate or kinetic expression parameter. |
| `kdpi` | `0.72` | Kinetic rate or kinetic expression parameter. |
| `kdpr` | `1.00E+01` | Kinetic rate or kinetic expression parameter. |
| `kcd47free_on` | `100` | Kinetic rate or kinetic expression parameter. |
| `kr2si` | `0.031` | Kinetic rate or kinetic expression parameter. |
| `kr2rs` | `17.18` | Kinetic rate or kinetic expression parameter. |
| `kr2NRP1si` | `0.0014` | Kinetic rate or kinetic expression parameter. |
| `kr2NRP1i2r` | `48` | Kinetic rate or kinetic expression parameter. |
| `kVEGFNRP1on` | `2.48` | Kinetic rate or kinetic expression parameter. |
| `kVEGFNRP1off` | `0.0008` | Kinetic rate or kinetic expression parameter. |
| `kNRP1VEGFR2on` | `0.15` | Kinetic rate or kinetic expression parameter. |
| `kNRP1VEGFR2off` | `0.045` | Kinetic rate or kinetic expression parameter. |
| `kNRP1VEGFR1on` | `5.07` | Kinetic rate or kinetic expression parameter. |
| `kNRP1VEGFR1off` | `0.016` | Kinetic rate or kinetic expression parameter. |
| `kVEGFR2NRP1on` | `0.0022` | Kinetic rate or kinetic expression parameter. |
| `kVEGFR2NRP1off` | `0.014` | Kinetic rate or kinetic expression parameter. |
| `kVEGFR1NRP1on` | `0.004` | Kinetic rate or kinetic expression parameter. |
| `kVEGFR1NRP1off` | `0.1` | Kinetic rate or kinetic expression parameter. |
| `PI3K_0` | `0.1` | Initial amount or baseline condition parameter. |
| `PIP2_0` | `10` | Initial amount or baseline condition parameter. |
| `kPIP2gen` | `0.000048` | Kinetic rate or kinetic expression parameter. |
| `kmPIP2PI3K` | `309.9` | Kinetic rate or kinetic expression parameter. |
| `kcatPI3KPIP2` | `1764.48` | Kinetic rate or kinetic expression parameter. |
| `PTEN_0` | `0.1` | Initial amount or baseline condition parameter. |
| `kmPIP3PTEN` | `6.27` | Kinetic rate or kinetic expression parameter. |
| `kcatPTENPIP3` | `4767.44` | Kinetic rate or kinetic expression parameter. |
| `konPDK1PIP3` | `5828.07` | Kinetic rate or kinetic expression parameter. |
| `koffPDK1PIP3` | `0.64` | Kinetic rate or kinetic expression parameter. |
| `konAKTPIP3` | `12.48` | Kinetic rate or kinetic expression parameter. |
| `koffAKTPIP3` | `0.032` | Kinetic rate or kinetic expression parameter. |
| `AKT_0` | `0.1` | Initial amount or baseline condition parameter. |
| `PDK1_0` | `0.1` | Initial amount or baseline condition parameter. |
| `kpAKTPDK1` | `2` | Kinetic rate or kinetic expression parameter. |
| `mTOR_0` | `0.1` | Initial amount or baseline condition parameter. |
| `kpmTORAKT` | `2` | Kinetic rate or kinetic expression parameter. |
| `kdp473AKTPPase` | `0.1` | Kinetic rate or kinetic expression parameter. |
| `kdp308AKTPPase` | `0.038` | Kinetic rate or kinetic expression parameter. |
| `kpPLCgamma` | `0.045` | Kinetic rate or kinetic expression parameter. |
| `kdpPLCgamma` | `0.014` | Kinetic rate or kinetic expression parameter. |
| `PLCgamma_0` | `0.2` | Initial amount or baseline condition parameter. |
| `kmPIP2PLCgamma` | `4.34` | Kinetic rate or kinetic expression parameter. |
| `nDAG` | `2.6` | Model parameter used by rules, functions, species, or observables. |
| `kcatPLCgammaDAG` | `0.1` | Kinetic rate or kinetic expression parameter. |
| `kdeg_ip3` | `0.47` | Kinetic rate or kinetic expression parameter. |
| `kdeg_DAG` | `0.11` | Kinetic rate or kinetic expression parameter. |
| `CaER_0` | `2.00E+03` | Initial amount or baseline condition parameter. |
| `Iip3Ramp` | `1.31E+05` | Model parameter used by rules, functions, species, or observables. |
| `KmIP3R` | `1.6` | Kinetic rate or kinetic expression parameter. |
| `I_PMCAbar` | `2.02` | Model parameter used by rules, functions, species, or observables. |
| `KmPMCA` | `0.26` | Kinetic rate or kinetic expression parameter. |
| `vSERCA` | `0.39` | Model parameter used by rules, functions, species, or observables. |
| `KleakER` | `1.00E-08` | Kinetic rate or kinetic expression parameter. |
| `KmSERCA` | `0.15` | Kinetic rate or kinetic expression parameter. |
| `KiCa` | `1` | Kinetic rate or kinetic expression parameter. |
| `KBon` | `100` | Kinetic rate or kinetic expression parameter. |
| `KBoff` | `300` | Kinetic rate or kinetic expression parameter. |
| `CaF_0` | `118` | Initial amount or baseline condition parameter. |
| `CaFbound_0` | `2` | Initial amount or baseline condition parameter. |
| `koffCaNCaM1` | `500` | Kinetic rate or kinetic expression parameter. |
| `kdCaNCaM` | `24` | Kinetic rate or kinetic expression parameter. |
| `koffCaCCaM1` | `10` | Kinetic rate or kinetic expression parameter. |
| `kdCaCCaM` | `3.1` | Kinetic rate or kinetic expression parameter. |
| `CSQN_total` | `15000` | Model parameter used by rules, functions, species, or observables. |
| `KCSQN` | `800` | Kinetic rate or kinetic expression parameter. |
| `kdegi0` | `2.02E-03` | Initial amount or baseline condition parameter. |
| `kdegr2NRP1i0` | `7.91E-03` | Initial amount or baseline condition parameter. |
| `kdegi0noP` | `2.85E+00` | Kinetic rate or kinetic expression parameter. |
| `kdegr2NRP1i0noP` | `2.22E-04` | Kinetic rate or kinetic expression parameter. |
| `kr2ii2` | `4.30E-03` | Kinetic rate or kinetic expression parameter. |
| `kr2NRP1ii2` | `4.80E+00` | Kinetic rate or kinetic expression parameter. |
| `kr2i2i` | `3.23E-02` | Kinetic rate or kinetic expression parameter. |
| `kr2NRP1i2i` | `1.00E-03` | Kinetic rate or kinetic expression parameter. |
| `kdegi20` | `2.43E+02` | Initial amount or baseline condition parameter. |
| `kdegr2NRP1i20` | `3.76E-02` | Initial amount or baseline condition parameter. |
| `kdegi20noP` | `4.16E-01` | Kinetic rate or kinetic expression parameter. |
| `kdegr2NRP1i20noP` | `7.56E+02` | Kinetic rate or kinetic expression parameter. |
| `ksingleR2syn` | `1.40E-04` | Kinetic rate or kinetic expression parameter. |
| `ksingleR2deg` | `5.88E-04` | Kinetic rate or kinetic expression parameter. |
| `ksingleR2si` | `7.56E-04` | Kinetic rate or kinetic expression parameter. |
| `ksingleR2is` | `8.66E-04` | Kinetic rate or kinetic expression parameter. |
| `ICracamp` | `5.86E+03` | Model parameter used by rules, functions, species, or observables. |
| `Kcrac` | `169` | Kinetic rate or kinetic expression parameter. |
| `Istim0` | `0.18` | Initial amount or baseline condition parameter. |
| `tau_stim` | `4` | Model parameter used by rules, functions, species, or observables. |
| `ncrac` | `4.2` | Model parameter used by rules, functions, species, or observables. |
| `Src_0` | `0.1` | Initial amount or baseline condition parameter. |
| `Axl_0` | `7.14` | Initial amount or baseline condition parameter. |
| `kpSrc` | `0.61` | Kinetic rate or kinetic expression parameter. |
| `kdpSrc` | `136.5` | Kinetic rate or kinetic expression parameter. |
| `kpSrcAxl` | `3.92` | Kinetic rate or kinetic expression parameter. |
| `kpAxlauto` | `0.12` | Kinetic rate or kinetic expression parameter. |
| `kdpautoAxl` | `1291.1` | Kinetic rate or kinetic expression parameter. |
| `kdpSrcAxl` | `1.79E-03` | Kinetic rate or kinetic expression parameter. |
| `konPI3KAxl` | `55.91688952` | Kinetic rate or kinetic expression parameter. |
| `koffPI3KAxl` | `0.6` | Kinetic rate or kinetic expression parameter. |
| `kDCD47TSP1` | `1.00E-05` | Kinetic rate or kinetic expression parameter. |
| `koffCD47TSP1` | `0.001` | Kinetic rate or kinetic expression parameter. |
| `CD47free_0` | `7.14E+00` | Initial amount or baseline condition parameter. |
| `kdpeNOS` | `5.17E-02` | Kinetic rate or kinetic expression parameter. |
| `konCaMeNOS` | `9.80E+02` | Kinetic rate or kinetic expression parameter. |
| `koffCaMeNOS` | `9.73E+00` | Kinetic rate or kinetic expression parameter. |
| `koffeNOScav1` | `6.875` | Kinetic rate or kinetic expression parameter. |
| `koncaveNOS` | `81.9375` | Kinetic rate or kinetic expression parameter. |
| `kcateNOSAKT` | `1000` | Kinetic rate or kinetic expression parameter. |
| `kr2CD47off` | `1.00E+00` | Kinetic rate or kinetic expression parameter. |
| `f_TSP1deg` | `1.00E+00` | Model parameter used by rules, functions, species, or observables. |
| `fTSP1dp` | `1.00E+00` | Model parameter used by rules, functions, species, or observables. |
| `fTSP1i2r` | `1.00E+00` | Model parameter used by rules, functions, species, or observables. |
| `PKC_0` | `0.1` | Initial amount or baseline condition parameter. |
| `konCaPKC` | `0.3` | Kinetic rate or kinetic expression parameter. |
| `koffCaPKC` | `0.01` | Kinetic rate or kinetic expression parameter. |
| `konDAGPKC` | `0.029957319` | Kinetic rate or kinetic expression parameter. |
| `koffDAGPKC` | `0.124096212` | Kinetic rate or kinetic expression parameter. |
| `kon1CaCIB1` | `0.052631579` | Kinetic rate or kinetic expression parameter. |
| `koff1CaCIB1` | `0.1` | Kinetic rate or kinetic expression parameter. |
| `kon2CaCIB1` | `0.185185185` | Kinetic rate or kinetic expression parameter. |
| `koff2CaCIB1` | `0.1` | Kinetic rate or kinetic expression parameter. |
| `CIB1_0` | `0.5` | Initial amount or baseline condition parameter. |
| `konCIB1SphK1` | `17.6028519` | Kinetic rate or kinetic expression parameter. |
| `koffCIB1SphK1` | `4.403956392` | Kinetic rate or kinetic expression parameter. |
| `SphK_0` | `0.1` | Initial amount or baseline condition parameter. |
| `Sph_0` | `10` | Initial amount or baseline condition parameter. |
| `S1P_0` | `0` | Initial amount or baseline condition parameter. |
| `kcatERK` | `7.882741692` | Kinetic rate or kinetic expression parameter. |
| `kmERKSK1` | `1.198236617` | Kinetic rate or kinetic expression parameter. |
| `ktSK1` | `1` | Kinetic rate or kinetic expression parameter. |
| `koffSK1` | `1.04E-01` | Kinetic rate or kinetic expression parameter. |
| `ktoffSK1` | `6.97E-04` | Kinetic rate or kinetic expression parameter. |
| `kcatPKC` | `10.20798409` | Kinetic rate or kinetic expression parameter. |
| `kmPKCRaf` | `0.313875333` | Kinetic rate or kinetic expression parameter. |
| `RasGTP_0` | `0` | Initial amount or baseline condition parameter. |
| `RasGDP_0` | `0.1` | Initial amount or baseline condition parameter. |
| `Raf_0` | `0.355471965` | Initial amount or baseline condition parameter. |
| `MEK12_0` | `0.288919159` | Initial amount or baseline condition parameter. |
| `ERK12_0` | `0.382329627` | Initial amount or baseline condition parameter. |
| `kdpSK1` | `0.02182773` | Kinetic rate or kinetic expression parameter. |
| `kdpPKCRaf` | `0.720296112` | Kinetic rate or kinetic expression parameter. |
| `kSphgen` | `0.000048` | Kinetic rate or kinetic expression parameter. |
| `kcatSK1Sph` | `37.23820691` | Kinetic rate or kinetic expression parameter. |
| `KmSK1Sph` | `0.029430478` | Kinetic rate or kinetic expression parameter. |
| `kdpS1P` | `1.188017664` | Kinetic rate or kinetic expression parameter. |
| `kS1PRas` | `1.556423632` | Kinetic rate or kinetic expression parameter. |
| `KmS1PRas` | `5.899306591` | Kinetic rate or kinetic expression parameter. |
| `kRasGAP` | `2.941097467` | Kinetic rate or kinetic expression parameter. |
| `konRasRaf` | `13.10183719` | Kinetic rate or kinetic expression parameter. |
| `koffRasRaf` | `0.151878139` | Kinetic rate or kinetic expression parameter. |
| `kpRaf` | `1.67558904` | Kinetic rate or kinetic expression parameter. |
| `kdpRaf` | `0.894826206` | Kinetic rate or kinetic expression parameter. |
| `kpMEK12Raf1` | `1.801786102` | Kinetic rate or kinetic expression parameter. |
| `kpMEK12Raf2` | `1.204676328` | Kinetic rate or kinetic expression parameter. |
| `KmMEK12Raf` | `0.807388937` | Kinetic rate or kinetic expression parameter. |
| `kdpMEK12_1` | `0.111827134` | Kinetic rate or kinetic expression parameter. |
| `kdpMEK12_2` | `0.139705453` | Kinetic rate or kinetic expression parameter. |
| `kpMEK12ERK12_1` | `12.14930177` | Kinetic rate or kinetic expression parameter. |
| `kmMEKERK12` | `0.25546079` | Kinetic rate or kinetic expression parameter. |
| `kpMEK12ERK12_2` | `0.516270813` | Kinetic rate or kinetic expression parameter. |
| `kdpERK12_1` | `6.06E+00` | Kinetic rate or kinetic expression parameter. |
| `kdpERK12_2` | `1.053392443` | Kinetic rate or kinetic expression parameter. |

No separate BNGL functions are declared; rule rates are direct parameters or algebraic expressions embedded in the rule inventory.

## 4. Molecule types, sites, and states

| Molecule type | Site count | Sites/components | Internal states | Anchor/allowed compartments | Binding/modification roles | Notes |
| --- | ---: | --- | --- | --- | --- | --- |
| `vegf` | 4 | `r`, `r`, `nrp1bd`, `c` | c: s, i, i2, r | None | r is used as a binding/matching component; r is used as a binding/matching component; nrp1bd is used as a binding/matching component; c is an internal state/modification coordinate | vegf165a |
| `vegfr2` | 5 | `l1`, `Y1175`, `CD47bd`, `dimer`, `c` | Y1175: Y, pY; c: s, i, i2, r | None | l1 is used as a binding/matching component; Y1175 is an internal state/modification coordinate; CD47bd is used as a binding/matching component; dimer is used as a binding/matching component; c is an internal state/modification coordinate | Declared in molecule types block. |
| `vegfr1` | 4 | `l2`, `dimer`, `nrp1bd`, `c` | c: s | None | l2 is used as a binding/matching component; dimer is used as a binding/matching component; nrp1bd is used as a binding/matching component; c is an internal state/modification coordinate | Declared in molecule types block. |
| `NRP1` | 2 | `vegfabd`, `c` | c: s, i, i2, r | None | vegfabd is used as a binding/matching component; c is an internal state/modification coordinate | Declared in molecule types block. |
| `PI` | 1 | `PIsite` | PIsite: 3P, 4P | None | PIsite is an internal state/modification coordinate | Declared in molecule types block. |
| `PLCgamma` | 1 | `Yplc` | Yplc: Y, pY | None | Yplc is an internal state/modification coordinate | Declared in molecule types block. |
| `DAG` | 1 | `pkcbd` | None | None | pkcbd is used as a binding/matching component | Declared in molecule types block. |
| `IP3_cyto` | 1 | `ip3rbd` | None | None | ip3rbd is used as a binding/matching component | Declared in molecule types block. |
| `Calcium_cyto` | 1 | `bd` | None | None | bd is used as a binding/matching component | Declared in molecule types block. |
| `Trash` | 0 | None | None | None | No specific role inferred beyond molecule identity. | Declared in molecule types block. |
| `CaER` | 1 | `bd` | None | None | bd is used as a binding/matching component | Declared in molecule types block. |
| `CaF` | 1 | `cabd` | None | None | cabd is used as a binding/matching component | Declared in molecule types block. |
| `CSQNF` | 1 | `cabd` | None | None | cabd is used as a binding/matching component | Declared in molecule types block. |
| `CaM` | 5 | `NCaM`, `NCaM`, `CCaM`, `CCaM`, `CaMtargetbd` | None | None | CaMtargetbd is used as a binding/matching component | Declared in molecule types block. |
| `I` | 0 | None | None | None | No specific role inferred beyond molecule identity. | Declared in molecule types block. |
| `Istim` | 0 | None | None | None | No specific role inferred beyond molecule identity. | Declared in molecule types block. |
| `PTEN` | 1 | `PIP3docking` | None | None | No specific role inferred beyond molecule identity. | Declared in molecule types block. |
| `TSADSrc` | 1 | `Y1` | Y1: Y, pY | None | Y1 is an internal state/modification coordinate | Declared in molecule types block. |
| `Axl` | 2 | `Ysrc`, `Yaxl` | Ysrc: Y, pY; Yaxl: Y, pY | None | Ysrc is an internal state/modification coordinate; Yaxl is an internal state/modification coordinate | Declared in molecule types block. |
| `PI3K` | 1 | `state` | state: active, inactive | None | state is an internal state/modification coordinate | Declared in molecule types block. |
| `AKT` | 3 | `PHakt`, `T308`, `S473` | T308: S, pS; S473: S, pS | None | T308 is an internal state/modification coordinate; S473 is an internal state/modification coordinate | Declared in molecule types block. |
| `PDK1` | 2 | `PHpdk1`, `aktbd` | None | None | aktbd is used as a binding/matching component | Declared in molecule types block. |
| `mTOR` | 1 | `aktbd` | None | None | aktbd is used as a binding/matching component | Declared in molecule types block. |
| `CD47SIRPa` | 4 | `VEGFR2bd`, `TSP1bd`, `Y1`, `c` | Y1: Y, pY; c: s, i, i2, r | None | VEGFR2bd is used as a binding/matching component; TSP1bd is used as a binding/matching component; Y1 is an internal state/modification coordinate; c is an internal state/modification coordinate | Declared in molecule types block. |
| `TSP1` | 1 | `CD47bd` | None | None | CD47bd is used as a binding/matching component | Declared in molecule types block. |
| `eNOS` | 3 | `CaMBD`, `S1177`, `cav1BD` | S1177: S, pS | None | CaMBD is used as a binding/matching component; S1177 is an internal state/modification coordinate; cav1BD is used as a binding/matching component | Declared in molecule types block. |
| `caveolin1` | 1 | `eNOSbd` | None | None | eNOSbd is used as a binding/matching component | Declared in molecule types block. |
| `PKC` | 2 | `CalciumBD`, `DAGBD` | None | None | CalciumBD is used as a binding/matching component; DAGBD is used as a binding/matching component | Declared in molecule types block. |
| `CIB1` | 4 | `EF1`, `EF2`, `sk1bd`, `location` | location: cytosol, membrane | None | sk1bd is used as a binding/matching component; location is an internal state/modification coordinate | Declared in molecule types block. |
| `SphK` | 2 | `CIB1bd`, `Serk` | Serk: S, pS | None | CIB1bd is used as a binding/matching component; Serk is an internal state/modification coordinate | Declared in molecule types block. |
| `Sph` | 1 | `skbd` | None | None | skbd is used as a binding/matching component | Declared in molecule types block. |
| `S1P` | 1 | `bd` | None | None | bd is used as a binding/matching component | Declared in molecule types block. |
| `RasGDP` | 1 | `rafbd` | None | None | rafbd is used as a binding/matching component | Declared in molecule types block. |
| `RasGTP` | 1 | `rafbd` | None | None | rafbd is used as a binding/matching component | Declared in molecule types block. |
| `Raf` | 4 | `mekbd`, `rasbd`, `Y1Y2`, `Spkc` | Y1Y2: Y, pY; Spkc: S, pS | None | mekbd is used as a binding/matching component; rasbd is used as a binding/matching component; Y1Y2 is an internal state/modification coordinate; Spkc is an internal state/modification coordinate | Declared in molecule types block. |
| `MEK12` | 3 | `bd`, `S1`, `S2` | S1: S, pS; S2: S, pS | None | bd is used as a binding/matching component; S1 is an internal state/modification coordinate; S2 is an internal state/modification coordinate | Declared in molecule types block. |
| `ERK1` | 2 | `MEK12bd`, `S1` | S1: S, pS | None | MEK12bd is used as a binding/matching component; S1 is an internal state/modification coordinate | Declared in molecule types block. |
| `ERK2` | 2 | `MEK12bd`, `S2` | S2: S, pS | None | MEK12bd is used as a binding/matching component; S2 is an internal state/modification coordinate | Declared in molecule types block. |

## 5. Compartments, anchors, initial species, and setup

No BNGL compartment block is declared.

No anchors block is declared.

VEGF/NRP1/receptor assemblies control VEGFR2 phosphorylation and trafficking, then branch into PI3K/AKT, PLCγ-calcium, eNOS, and MAPK/S1P pathways. TSP1/CD47 and Axl/Src modules provide additional regulation around receptor state, PI3K recruitment, and downstream kinase activity.

| Initial species entry | Initial amount/expression | Technical setup meaning |
| --- | --- | --- |
| `vegf(r,r,nrp1bd,c~s)` | `VEGF165a_0` | Initial population or concentration for this exact pattern. |
| `vegfr1(l2,dimer,nrp1bd,c~s)` | `VEGFR1_0` | Initial population or concentration for this exact pattern. |
| `vegfr2(l1,Y1175~Y,CD47bd,dimer,c~s)` | `VEGFR2_0` | Initial population or concentration for this exact pattern. |
| `NRP1(vegfabd,c~s)` | `NRP1_0` | Initial population or concentration for this exact pattern. |
| `PI(PIsite~3P)` | `PIP2_0` | Initial population or concentration for this exact pattern. |
| `PLCgamma(Yplc~Y)` | `PLCgamma_0` | Initial population or concentration for this exact pattern. |
| `CaER(bd)` | `CaER_0` | Initial population or concentration for this exact pattern. |
| `Calcium_cyto(bd)` | `Calcium_0` | Initial population or concentration for this exact pattern. |
| `CaF(cabd)` | `CaF_0` | Initial population or concentration for this exact pattern. |
| `Calcium_cyto(bd!1).CaF(cabd!1)` | `CaFbound_0` | Initial population or concentration for this exact pattern. |
| `CaM(NCaM,NCaM,CCaM,CCaM,CaMtargetbd)` | `CaM_0` | Initial population or concentration for this exact pattern. |
| `I()` | `1` | Initial population or concentration for this exact pattern. |
| `Istim()` | `Istim0` | Initial population or concentration for this exact pattern. |
| `PTEN(PIP3docking)` | `PTEN_0` | Initial population or concentration for this exact pattern. |
| `TSADSrc(Y1~Y)` | `Src_0` | Initial population or concentration for this exact pattern. |
| `Axl(Ysrc~Y,Yaxl~Y)` | `Axl_0` | Initial population or concentration for this exact pattern. |
| `PI3K(state~inactive)` | `PI3K_0` | Initial population or concentration for this exact pattern. |
| `AKT(PHakt,T308~S,S473~S)` | `AKT_0` | Initial population or concentration for this exact pattern. |
| `PDK1(PHpdk1,aktbd)` | `PDK1_0` | Initial population or concentration for this exact pattern. |
| `mTOR(aktbd)` | `mTOR_0` | Initial population or concentration for this exact pattern. |
| `TSP1(CD47bd)` | `TSP1_0` | Initial population or concentration for this exact pattern. |
| `CD47SIRPa(VEGFR2bd,TSP1bd,Y1~Y,c~s)` | `CD47free_0` | Initial population or concentration for this exact pattern. |
| `eNOS(CaMBD,S1177~S,cav1BD!1).caveolin1(eNOSbd!1)` | `eNOS_0` | Initial population or concentration for this exact pattern. |
| `PKC(CalciumBD,DAGBD)` | `PKC_0` | Initial population or concentration for this exact pattern. |
| `CIB1(EF1,EF2,sk1bd,location~cytosol)` | `CIB1_0` | Initial population or concentration for this exact pattern. |
| `SphK(CIB1bd,Serk~S)` | `SphK_0` | Initial population or concentration for this exact pattern. |
| `Sph(skbd)` | `Sph_0` | Initial population or concentration for this exact pattern. |
| `S1P(bd)` | `S1P_0` | Initial population or concentration for this exact pattern. |
| `RasGDP(rafbd)` | `RasGDP_0` | Initial population or concentration for this exact pattern. |
| `RasGTP(rafbd)` | `RasGTP_0` | Initial population or concentration for this exact pattern. |
| `Raf(mekbd,rasbd,Y1Y2~Y,Spkc~S)` | `Raf_0` | Initial population or concentration for this exact pattern. |
| `MEK12(bd,S1~S,S2~S)` | `MEK12_0` | Initial population or concentration for this exact pattern. |
| `ERK1(MEK12bd,S1~S)` | `ERK12_0` | Initial population or concentration for this exact pattern. |
| `ERK2(MEK12bd,S2~S)` | `ERK12_0` | Initial population or concentration for this exact pattern. |

## 6. Complete reaction-rule inventory

The source contains **232** reaction rules. The inventory below preserves one row per source rule, grouped only for readability.

### Rules 1-232

| # | Rule label/name | Direction | Participants | Rate/expression | Modeled change | Rule pattern | Technical meaning |
| ---: | --- | --- | --- | --- | --- | --- | --- |

| 1 | `Unlabeled` | reversible | vegfr2 | `kcRR, kdRR` | state and binding-pattern rewrite | `vegfr2(l1,dimer,c~s) + vegfr2(l1,dimer,c~s)  <-> vegfr2(l1,dimer!1,c~s).vegfr2(l1,dimer!1,c~s)` | Transforms vegfr2 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2 | `Unlabeled` | reversible | vegfr1, vegfr2 | `kcRR, kdRR` | state and binding-pattern rewrite | `vegfr2(l1,dimer,c~s) + vegfr1(l2,dimer,c~s)  <-> vegfr2(l1,dimer!1,c~s).vegfr1(l2,dimer!1,c~s)` | Transforms vegfr1, vegfr2 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 3 | `Unlabeled` | reversible | vegfr1 | `kcRR, kdRR` | state and binding-pattern rewrite | `vegfr1(l2,dimer,c~s) + vegfr1(l2,dimer,c~s)  <-> vegfr1(l2,dimer!1,c~s).vegfr1(l2,dimer!1,c~s)` | Transforms vegfr1 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 4 | `Unlabeled` | reversible | vegf, vegfr2 | `kdeltaRR, kdRR` | internal-state conversion/modification | `vegf(r!1,r!2,c~s).vegfr2(l1!1,dimer,c~s).vegfr2(l1!2,dimer,c~s)  <-> vegf(r!1,r!2,c~s).vegfr2(l1!1,dimer!3,c~s).vegfr2(l1!2,dimer!3,c~s)` | Transforms vegf, vegfr2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 5 | `Unlabeled` | reversible | vegf, vegfr1, vegfr2 | `kdeltaRR, kdRR` | internal-state conversion/modification | `vegf(r!1,r!2,c~s).vegfr2(l1!1,dimer,c~s).vegfr1(l2!2,dimer,c~s)  <-> vegf(r!1,r!2,c~s).vegfr2(l1!1,dimer!3,c~s).vegfr1(l2!2,dimer!3,c~s)` | Transforms vegf, vegfr1, vegfr2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 6 | `Unlabeled` | reversible | vegf, vegfr1 | `kdeltaRR, kdRR` | internal-state conversion/modification | `vegf(r!1,r!2,c~s).vegfr1(l2!1,dimer,c~s).vegfr1(l2!2,dimer,c~s)  <-> vegf(r!1,r!2,c~s).vegfr1(l2!1,dimer!3,c~s).vegfr1(l2!2,dimer!3,c~s)` | Transforms vegf, vegfr1 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 7 | `Unlabeled` | reversible | NRP1, vegfr1 | `kNRP1VEGFR1on, kNRP1VEGFR1off` | state and binding-pattern rewrite | `vegfr1(nrp1bd,c~s) + NRP1(vegfabd,c~s)  <-> vegfr1(nrp1bd!1,c~s).NRP1(vegfabd!1,c~s)` | Transforms NRP1, vegfr1 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 8 | `Unlabeled` | one-way | I, vegf | `-(kVEGFNRP1on*cellarea/fextmolar)*vegffrees*nrp1s+(kVEGFNRP1off*cellarea/fextmolar)*vegfnrp1s` | source/synthesis or algebraic source term | `I()  -> I() + vegf(r,r,nrp1bd,c~s)` | Transforms I, vegf by source/synthesis or algebraic source term; see the exact pattern for affected sites/states/bonds. |

| 9 | `Unlabeled` | one-way | NRP1, vegf | `kVEGFNRP1on` | state and binding-pattern rewrite | `vegf(r,r,nrp1bd,c~s) + NRP1(vegfabd,c~s)  -> vegf(r,r,nrp1bd,c~s) + vegf(r,r,nrp1bd!1,c~s).NRP1(vegfabd!1,c~s)` | Transforms NRP1, vegf by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 10 | `Unlabeled` | one-way | NRP1, vegf | `kVEGFNRP1off` | state and binding-pattern rewrite | `vegf(r,r,nrp1bd!1,c~s).NRP1(vegfabd!1,c~s)  -> NRP1(vegfabd,c~s)` | Transforms NRP1, vegf by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 11 | `Unlabeled` | reversible | vegf, vegfr2 | `kNRP1VEGFR2on, kNRP1VEGFR2off` | internal-state conversion/modification | `vegf(r,r,nrp1bd!+,c~s) + vegfr2(l1,dimer,c~s)  <-> vegf(r!2,r,nrp1bd!+,c~s).vegfr2(l1!2,dimer,c~s)` | Transforms vegf, vegfr2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 12 | `Unlabeled` | reversible | vegf, vegfr2 | `kNRP1VEGFR2on, kNRP1VEGFR2off` | internal-state conversion/modification | `vegf(r,r,nrp1bd!+,c~s) + vegfr2(l1,dimer!3,c~s).vegfr2(l1,dimer!3,c~s)  <-> vegf(r!2,r,nrp1bd!+,c~s).vegfr2(l1!2,dimer!3,c~s).vegfr2(l1,dimer!3,c~s)` | Transforms vegf, vegfr2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 13 | `Unlabeled` | reversible | vegf, vegfr1, vegfr2 | `kNRP1VEGFR2on, kNRP1VEGFR2off` | internal-state conversion/modification | `vegf(r,r,nrp1bd!+,c~s) + vegfr2(l1,dimer!3,c~s).vegfr1(l2,dimer!3,c~s)  <-> vegf(r!2,r,nrp1bd!+,c~s).vegfr2(l1!2,dimer!3,c~s).vegfr1(l2,dimer!3,c~s)` | Transforms vegf, vegfr1, vegfr2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 14 | `Unlabeled` | reversible | vegf, vegfr1 | `kcVR, kvr1off` | internal-state conversion/modification | `vegf(r,r,nrp1bd!+,c~s) + vegfr1(l2,dimer,c~s)  <-> vegf(r!2,r,nrp1bd!+,c~s).vegfr1(l2!2,dimer,c~s)` | Transforms vegf, vegfr1 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 15 | `Unlabeled` | reversible | vegf, vegfr1 | `kcVR, kvr1off` | internal-state conversion/modification | `vegf(r,r,nrp1bd!+,c~s) + vegfr1(l2,dimer!3,c~s).vegfr1(l2,dimer!3,c~s)  <-> vegf(r!2,r,nrp1bd!+,c~s).vegfr1(l2!2,dimer!3,c~s).vegfr1(l2,dimer!3,c~s)` | Transforms vegf, vegfr1 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 16 | `Unlabeled` | reversible | vegf, vegfr1, vegfr2 | `kcVR, kvr1off` | internal-state conversion/modification | `vegf(r,r,nrp1bd!+,c~s) + vegfr1(l2,dimer!3,c~s).vegfr2(l1,dimer!3,c~s)  <-> vegf(r!2,r,nrp1bd!+,c~s).vegfr1(l2!2,dimer!3,c~s).vegfr2(l1,dimer!3,c~s)` | Transforms vegf, vegfr1, vegfr2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 17 | `Unlabeled` | one-way | I, vegf | `-(kvron*cellarea/fextmolar)*vegffrees*vr2s+(kvroff*cellarea/fextmolar)*vegfr2s` | source/synthesis or algebraic source term | `I()  -> I() + vegf(r,r,nrp1bd,c~s)` | Transforms I, vegf by source/synthesis or algebraic source term; see the exact pattern for affected sites/states/bonds. |

| 18 | `Unlabeled` | one-way | vegf, vegfr2 | `kvron` | state and binding-pattern rewrite | `vegf(r,r,nrp1bd,c~s) + vegfr2(l1,c~s)  -> vegf(r,r,nrp1bd,c~s) + vegf(r!1,r,nrp1bd,c~s).vegfr2(l1!1,c~s)` | Transforms vegf, vegfr2 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 19 | `Unlabeled` | one-way | vegf, vegfr2 | `kvroff` | state and binding-pattern rewrite | `vegf(r!1,r,nrp1bd,c~s).vegfr2(l1!1,c~s)  -> vegfr2(l1,c~s)` | Transforms vegf, vegfr2 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 20 | `Unlabeled` | reversible | vegf, vegfr2 | `kcVR, kvroff` | internal-state conversion/modification | `vegf(r!1,r,nrp1bd,c~s).vegfr2(l1!1,dimer,c~s) + vegfr2(l1,dimer,c~s)  <-> vegf(r!1,r!2,nrp1bd,c~s).vegfr2(l1!1,dimer,c~s).vegfr2(l1!2,dimer,c~s)` | Transforms vegf, vegfr2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 21 | `Unlabeled` | reversible | vegf, vegfr1, vegfr2 | `kcVR, kvr1off` | internal-state conversion/modification | `vegf(r!1,r,nrp1bd,c~s).vegfr2(l1!1,dimer,c~s) + vegfr1(l2,dimer,c~s)  <-> vegf(r!1,r!2,nrp1bd,c~s).vegfr2(l1!1,dimer,c~s).vegfr1(l2!2,dimer,c~s)` | Transforms vegf, vegfr1, vegfr2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 22 | `Unlabeled` | reversible | vegf, vegfr2 | `kdeltaVR, kvroff` | internal-state conversion/modification | `vegf(r!1,r,nrp1bd,c~s).vegfr2(l1!1,dimer!3,c~s).vegfr2(l1,dimer!3,c~s)  <-> vegf(r!1,r!2,nrp1bd,c~s).vegfr2(l1!1,dimer!3,c~s).vegfr2(l1!2,dimer!3,c~s)` | Transforms vegf, vegfr2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 23 | `Unlabeled` | reversible | vegf, vegfr1, vegfr2 | `kdeltaVR, kvr1off` | internal-state conversion/modification | `vegf(r!1,r,nrp1bd,c~s).vegfr2(l1!1,dimer!3,c~s).vegfr1(l2,dimer!3,c~s)  <-> vegf(r!1,r!2,nrp1bd,c~s).vegfr2(l1!1,dimer!3,c~s).vegfr1(l2!2,dimer!3,c~s)` | Transforms vegf, vegfr1, vegfr2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 24 | `Unlabeled` | reversible | vegf, vegfr1 | `kcVR, kvr1off` | internal-state conversion/modification | `vegf(r!1,r,nrp1bd,c~s).vegfr1(l2!1,dimer,c~s) + vegfr1(l2,dimer,c~s)  <-> vegf(r!1,r!2,nrp1bd,c~s).vegfr1(l2!1,dimer,c~s).vegfr1(l2!2,dimer,c~s)` | Transforms vegf, vegfr1 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 25 | `Unlabeled` | reversible | vegf, vegfr1, vegfr2 | `kcVR, kvroff` | internal-state conversion/modification | `vegf(r!1,r,nrp1bd,c~s).vegfr1(l2!1,dimer,c~s) + vegfr2(l1,dimer,c~s)  <-> vegf(r!1,r!2,nrp1bd,c~s).vegfr1(l2!1,dimer,c~s).vegfr2(l1!2,dimer,c~s)` | Transforms vegf, vegfr1, vegfr2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 26 | `Unlabeled` | reversible | vegf, vegfr1 | `kdeltaVR, kvr1off` | internal-state conversion/modification | `vegf(r!1,r,nrp1bd,c~s).vegfr1(l2!1,dimer!3,c~s).vegfr1(l2,dimer!3,c~s)  <-> vegf(r!1,r!2,nrp1bd,c~s).vegfr1(l2!1,dimer!3,c~s).vegfr1(l2!2,dimer!3,c~s)` | Transforms vegf, vegfr1 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 27 | `Unlabeled` | reversible | vegf, vegfr1, vegfr2 | `kdeltaVR, kvroff` | internal-state conversion/modification | `vegf(r!1,r,nrp1bd,c~s).vegfr1(l2!1,dimer!3,c~s).vegfr2(l1,dimer!3,c~s)  <-> vegf(r!1,r!2,nrp1bd,c~s).vegfr1(l2!1,dimer!3,c~s).vegfr2(l1!2,dimer!3,c~s)` | Transforms vegf, vegfr1, vegfr2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 28 | `Unlabeled` | reversible | vegf, vegfr2 | `kNRP1VEGFR2on, kNRP1VEGFR2off` | internal-state conversion/modification | `vegf(r!1,r,nrp1bd!+,c~s).vegfr2(l1!1,dimer,c~s) + vegfr2(l1,dimer,c~s)  <-> vegf(r!1,r!2,nrp1bd!+,c~s).vegfr2(l1!1,dimer,c~s).vegfr2(l1!2,dimer,c~s)` | Transforms vegf, vegfr2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 29 | `Unlabeled` | reversible | vegf, vegfr1, vegfr2 | `kcVR, kvr1off` | internal-state conversion/modification | `vegf(r!1,r,nrp1bd!+,c~s).vegfr2(l1!1,dimer,c~s) + vegfr1(l2,dimer,c~s)  <-> vegf(r!1,r!2,nrp1bd!+,c~s).vegfr2(l1!1,dimer,c~s).vegfr1(l2!2,dimer,c~s)` | Transforms vegf, vegfr1, vegfr2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 30 | `Unlabeled` | reversible | vegf, vegfr2 | `kdeltaVR, kvroff` | internal-state conversion/modification | `vegf(r!1,r,nrp1bd!+,c~s).vegfr2(l1!1,dimer!3,c~s).vegfr2(l1,dimer!3,c~s)  <-> vegf(r!1,r!2,nrp1bd!+,c~s).vegfr2(l1!1,dimer!3,c~s).vegfr2(l1!2,dimer!3,c~s)` | Transforms vegf, vegfr2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 31 | `Unlabeled` | reversible | vegf, vegfr1, vegfr2 | `kdeltaVR, kvr1off` | internal-state conversion/modification | `vegf(r!1,r,nrp1bd!+,c~s).vegfr2(l1!1,dimer!3,c~s).vegfr1(l2,dimer!3,c~s)  <-> vegf(r!1,r!2,nrp1bd!+,c~s).vegfr2(l1!1,dimer!3,c~s).vegfr1(l2!2,dimer!3,c~s)` | Transforms vegf, vegfr1, vegfr2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 32 | `Unlabeled` | reversible | vegf, vegfr1 | `kcVR, kvr1off` | internal-state conversion/modification | `vegf(r!1,r,nrp1bd!+,c~s).vegfr1(l2!1,dimer,c~s) + vegfr1(l2,dimer,c~s)  <-> vegf(r!1,r!2,nrp1bd!+,c~s).vegfr1(l2!1,dimer,c~s).vegfr1(l2!2,dimer,c~s)` | Transforms vegf, vegfr1 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 33 | `Unlabeled` | reversible | vegf, vegfr1, vegfr2 | `kNRP1VEGFR2on, kNRP1VEGFR2off` | internal-state conversion/modification | `vegf(r!1,r,nrp1bd!+,c~s).vegfr1(l2!1,dimer,c~s) + vegfr2(l1,dimer,c~s)  <-> vegf(r!1,r!2,nrp1bd!+,c~s).vegfr1(l2!1,dimer,c~s).vegfr2(l1!2,dimer,c~s)` | Transforms vegf, vegfr1, vegfr2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 34 | `Unlabeled` | reversible | vegf, vegfr1 | `kdeltaVR, kvr1off` | internal-state conversion/modification | `vegf(r!1,r,nrp1bd!+,c~s).vegfr1(l2!1,dimer!3,c~s).vegfr1(l2,dimer!3,c~s)  <-> vegf(r!1,r!2,nrp1bd!+,c~s).vegfr1(l2!1,dimer!3,c~s).vegfr1(l2!2,dimer!3,c~s)` | Transforms vegf, vegfr1 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 35 | `Unlabeled` | reversible | vegf, vegfr1, vegfr2 | `kdeltaVR, kvroff` | internal-state conversion/modification | `vegf(r!1,r,nrp1bd!+,c~s).vegfr1(l2!1,dimer!3,c~s).vegfr2(l1,dimer!3,c~s)  <-> vegf(r!1,r!2,nrp1bd!+,c~s).vegfr1(l2!1,dimer!3,c~s).vegfr2(l1!2,dimer!3,c~s)` | Transforms vegf, vegfr1, vegfr2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 36 | `Unlabeled` | reversible | NRP1, vegf, vegfr2 | `kVEGFR2NRP1on, kVEGFR2NRP1off` | internal-state conversion/modification | `vegf(r!1,r!2,nrp1bd,c~s).vegfr2(l1!1,dimer!3,c~s).vegfr2(l1!2,dimer!3,c~s) + NRP1(vegfabd,c~s)  <-> vegf(r!1,r!2,nrp1bd!4,c~s).vegfr2(l1!1,dimer!3,c~s).vegfr2(l1!2,dimer!3,c~s).NRP1(vegfabd!4,c~s)` | Transforms NRP1, vegf, vegfr2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 37 | `Unlabeled` | reversible | NRP1, vegf, vegfr1 | `kVEGFR2NRP1on, kVEGFR2NRP1off` | internal-state conversion/modification | `vegf(r!1,r!2,nrp1bd,c~s).vegfr1(l2!1,dimer!3,c~s).vegfr1(l2!2,dimer!3,c~s) + NRP1(vegfabd,c~s)  <-> vegf(r!1,r!2,nrp1bd!4,c~s).vegfr1(l2!1,dimer!3,c~s).vegfr1(l2!2,dimer!3,c~s).NRP1(vegfabd!4,c~s)` | Transforms NRP1, vegf, vegfr1 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 38 | `Unlabeled` | reversible | NRP1, vegf, vegfr1, vegfr2 | `kVEGFR2NRP1on, kVEGFR2NRP1off` | internal-state conversion/modification | `vegf(r!1,r!2,nrp1bd,c~s).vegfr2(l1!1,dimer!3,c~s).vegfr1(l2!2,dimer!3,c~s) + NRP1(vegfabd,c~s)  <-> vegf(r!1,r!2,nrp1bd!4,c~s).vegfr2(l1!1,dimer!3,c~s).vegfr1(l2!2,dimer!3,c~s).NRP1(vegfabd!4,c~s)` | Transforms NRP1, vegf, vegfr1, vegfr2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 39 | `Unlabeled` | reversible | NRP1, vegf, vegfr2 | `kVEGFR2NRP1on, kVEGFR2NRP1off` | internal-state conversion/modification | `vegf(r!1,r!2,nrp1bd,c~s).vegfr2(l1!1,dimer,c~s).vegfr2(l1!2,dimer,c~s) + NRP1(vegfabd,c~s)  <-> vegf(r!1,r!2,nrp1bd!4,c~s).vegfr2(l1!1,dimer,c~s).vegfr2(l1!2,dimer,c~s).NRP1(vegfabd!4,c~s)` | Transforms NRP1, vegf, vegfr2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 40 | `Unlabeled` | reversible | NRP1, vegf, vegfr2 | `kVEGFR2NRP1on, kVEGFR2NRP1off` | internal-state conversion/modification | `vegf(r!1,r,nrp1bd,c~s).vegfr2(l1!1,c~s) + NRP1(vegfabd,c~s)  <-> vegf(r!1,r,nrp1bd!2,c~s).vegfr2(l1!1,c~s).NRP1(vegfabd!2,c~s)` | Transforms NRP1, vegf, vegfr2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 41 | `Unlabeled` | reversible | NRP1, vegf, vegfr1 | `kVEGFR1NRP1on, kVEGFR1NRP1off` | internal-state conversion/modification | `vegf(r!1,r,nrp1bd,c~s).vegfr1(l2!1,c~s) + NRP1(vegfabd,c~s)  <-> vegf(r!1,r,nrp1bd!2,c~s).vegfr1(l2!1,c~s).NRP1(vegfabd!2,c~s)` | Transforms NRP1, vegf, vegfr1 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 42 | `Unlabeled` | one-way | I, vegf | `-kvr1on*cellarea/fextmolar*vegffrees*vr1s+kvr1off*vegfr1s*(cellarea/fextmolar)` | source/synthesis or algebraic source term | `I()  -> I() + vegf(r,r,nrp1bd,c~s)` | Transforms I, vegf by source/synthesis or algebraic source term; see the exact pattern for affected sites/states/bonds. |

| 43 | `Unlabeled` | one-way | vegf, vegfr1 | `kvr1on` | state and binding-pattern rewrite | `vegf(r,r,nrp1bd,c~s) + vegfr1(l2,c~s)  -> vegf(r,r,nrp1bd,c~s) + vegf(r!1,r,nrp1bd,c~s).vegfr1(l2!1,c~s)` | Transforms vegf, vegfr1 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 44 | `Unlabeled` | one-way | vegf, vegfr1 | `kvr1off` | state and binding-pattern rewrite | `vegf(r!1,r,nrp1bd,c~s).vegfr1(l2!1,c~s)  -> vegfr1(l2,c~s)` | Transforms vegf, vegfr1 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 45 | `Unlabeled` | reversible | vegf, vegfr1 | `kcVR, kvr1off` | internal-state conversion/modification | `vegf(r!1,r,c~s).vegfr1(l2!1,dimer,c~s) + vegfr1(l2,dimer,c~s)  <-> vegf(r!1,r!2,c~s).vegfr1(l2!1,dimer,c~s).vegfr1(l2!2,dimer,c~s)` | Transforms vegf, vegfr1 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 46 | `Unlabeled` | reversible | vegf, vegfr1, vegfr2 | `kcVR, kvroff` | internal-state conversion/modification | `vegf(r!1,r,c~s).vegfr1(l2!1,dimer,c~s) + vegfr2(l1,dimer,c~s)  <-> vegf(r!1,r!2,c~s).vegfr1(l2!1,dimer,c~s).vegfr2(l1!2,dimer,c~s)` | Transforms vegf, vegfr1, vegfr2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 47 | `Unlabeled` | reversible | vegf, vegfr1 | `kdeltaVR, kvr1off` | internal-state conversion/modification | `vegf(r!1,r,c~s).vegfr1(l2!1,dimer!3,c~s).vegfr1(l2,dimer!3,c~s)  <-> vegf(r!1,r!2,c~s).vegfr1(l2!1,dimer!3,c~s).vegfr1(l2!2,dimer!3,c~s)` | Transforms vegf, vegfr1 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 48 | `Unlabeled` | reversible | vegf, vegfr1, vegfr2 | `kdeltaVR, kvroff` | internal-state conversion/modification | `vegf(r!1,r,c~s).vegfr1(l2!1,dimer!3,c~s).vegfr2(l1,dimer!3,c~s)  <-> vegf(r!1,r!2,c~s).vegfr1(l2!1,dimer!3,c~s).vegfr2(l1!2,dimer!3,c~s)` | Transforms vegf, vegfr1, vegfr2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 49 | `Unlabeled` | one-way | vegf, vegfr2 | `kpr2` | internal-state conversion/modification | `vegf(r!1,r!2,c~s).vegfr2(l1!1,c~s).vegfr2(l1!2,Y1175~Y,c~s)  -> vegf(r!1,r!2,c~s).vegfr2(l1!1,c~s).vegfr2(l1!2,Y1175~pY,c~s)` | Transforms vegf, vegfr2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 50 | `Unlabeled` | one-way | vegf, vegfr2 | `kpr2` | internal-state conversion/modification | `vegf(r!1,r!2,c~i).vegfr2(l1!1,c~i).vegfr2(l1!2,Y1175~Y,c~i)  -> vegf(r!1,r!2,c~i).vegfr2(l1!1,c~i).vegfr2(l1!2,Y1175~pY,c~i)` | Transforms vegf, vegfr2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 51 | `Unlabeled` | one-way | vegf, vegfr2 | `kpr2` | internal-state conversion/modification | `vegf(r!1,r!2,c~i2).vegfr2(l1!1,c~i2).vegfr2(l1!2,Y1175~Y,c~i2)  -> vegf(r!1,r!2,c~i2).vegfr2(l1!1,c~i2).vegfr2(l1!2,Y1175~pY,c~i2)` | Transforms vegf, vegfr2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 52 | `Unlabeled` | one-way | vegf, vegfr2 | `kpr2` | internal-state conversion/modification | `vegf(r!1,r!2,c~r).vegfr2(l1!1,c~r).vegfr2(l1!2,Y1175~Y,c~r)  -> vegf(r!1,r!2,c~r).vegfr2(l1!1,c~r).vegfr2(l1!2,Y1175~pY,c~r)` | Transforms vegf, vegfr2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 53 | `Unlabeled` | one-way | vegfr2 | `kdps` | internal-state conversion/modification | `vegfr2(Y1175~pY,CD47bd,c~s)  -> vegfr2(Y1175~Y,CD47bd,c~s)` | Transforms vegfr2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 54 | `Unlabeled` | one-way | CD47SIRPa, vegfr2 | `kdps` | internal-state conversion/modification | `vegfr2(Y1175~pY,CD47bd!3,c~s).CD47SIRPa(TSP1bd,VEGFR2bd!3,c~s)  -> vegfr2(Y1175~Y,CD47bd!3,c~s).CD47SIRPa(TSP1bd,VEGFR2bd!3,c~s)` | Transforms CD47SIRPa, vegfr2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 55 | `Unlabeled` | one-way | CD47SIRPa, vegfr2 | `kdps*fTSP1dp` | internal-state conversion/modification | `vegfr2(Y1175~pY,CD47bd!3,c~s).CD47SIRPa(TSP1bd!+,VEGFR2bd!3,c~s)  -> vegfr2(Y1175~Y,CD47bd!3,c~s).CD47SIRPa(TSP1bd!+,VEGFR2bd!3,c~s)` | Transforms CD47SIRPa, vegfr2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 56 | `Unlabeled` | one-way | vegfr2 | `kdpi` | internal-state conversion/modification | `vegfr2(Y1175~pY,CD47bd,c~i)  -> vegfr2(Y1175~Y,CD47bd,c~i)` | Transforms vegfr2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 57 | `Unlabeled` | one-way | CD47SIRPa, vegfr2 | `kdpi` | internal-state conversion/modification | `vegfr2(Y1175~pY,CD47bd!3,c~i).CD47SIRPa(TSP1bd,VEGFR2bd!3,c~i)  -> vegfr2(Y1175~Y,CD47bd!3,c~i).CD47SIRPa(TSP1bd,VEGFR2bd!3,c~i)` | Transforms CD47SIRPa, vegfr2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 58 | `Unlabeled` | one-way | CD47SIRPa, vegfr2 | `kdpi*fTSP1dp` | internal-state conversion/modification | `vegfr2(Y1175~pY,CD47bd!3,c~i).CD47SIRPa(TSP1bd!+,VEGFR2bd!3,c~i)  -> vegfr2(Y1175~Y,CD47bd!3,c~i).CD47SIRPa(TSP1bd!+,VEGFR2bd!3,c~i)` | Transforms CD47SIRPa, vegfr2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 59 | `Unlabeled` | one-way | vegfr2 | `kdpi` | internal-state conversion/modification | `vegfr2(Y1175~pY,CD47bd,c~i2)  -> vegfr2(Y1175~Y,CD47bd,c~i2)` | Transforms vegfr2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 60 | `Unlabeled` | one-way | CD47SIRPa, vegfr2 | `kdpi` | internal-state conversion/modification | `vegfr2(Y1175~pY,CD47bd!3,c~i2).CD47SIRPa(TSP1bd,VEGFR2bd!3,c~i2)  -> vegfr2(Y1175~Y,CD47bd!3,c~i2).CD47SIRPa(TSP1bd,VEGFR2bd!3,c~i2)` | Transforms CD47SIRPa, vegfr2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 61 | `Unlabeled` | one-way | CD47SIRPa, vegfr2 | `kdpi*fTSP1dp` | internal-state conversion/modification | `vegfr2(Y1175~pY,CD47bd!3,c~i2).CD47SIRPa(TSP1bd!+,VEGFR2bd!3,c~i2)  -> vegfr2(Y1175~Y,CD47bd!3,c~i2).CD47SIRPa(TSP1bd!+,VEGFR2bd!3,c~i2)` | Transforms CD47SIRPa, vegfr2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 62 | `Unlabeled` | one-way | vegfr2 | `kdpr` | internal-state conversion/modification | `vegfr2(Y1175~pY,c~r)  -> vegfr2(Y1175~Y,c~r)` | Transforms vegfr2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 63 | `Unlabeled` | one-way | vegf, vegfr2 | `kr2si` | internal-state conversion/modification | `vegf(r!1,r!2,nrp1bd,c~s).vegfr2(l1!1,CD47bd,dimer,c~s).vegfr2(l1!2,CD47bd,dimer,c~s)  -> vegf(r!1,r!2,nrp1bd,c~i).vegfr2(l1!1,CD47bd,dimer,c~i).vegfr2(l1!2,CD47bd,dimer,c~i)` | Transforms vegf, vegfr2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 64 | `Unlabeled` | one-way | vegf, vegfr2 | `kr2si` | internal-state conversion/modification | `vegf(r!1,r!2,nrp1bd,c~s).vegfr2(l1!1,CD47bd,dimer!6,c~s).vegfr2(l1!2,CD47bd,dimer!6,c~s)  -> vegf(r!1,r!2,nrp1bd,c~i).vegfr2(l1!1,CD47bd,dimer!6,c~i).vegfr2(l1!2,CD47bd,dimer!6,c~i)` | Transforms vegf, vegfr2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 65 | `Unlabeled` | one-way | CD47SIRPa, vegf, vegfr2 | `kr2si` | internal-state conversion/modification | `vegf(r!1,r!2,nrp1bd,c~s).vegfr2(l1!1,CD47bd!3,dimer,c~s).CD47SIRPa(VEGFR2bd!3,c~s).vegfr2(l1!2,CD47bd,dimer,c~s)  -> vegf(r!1,r!2,nrp1bd,c~i).vegfr2(l1!1,CD47bd!3,dimer,c~i).CD47SIRPa(VEGFR2bd!3,c~i).vegfr2(l1!2,CD47bd,dimer,c~i)` | Transforms CD47SIRPa, vegf, vegfr2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 66 | `Unlabeled` | one-way | CD47SIRPa, vegf, vegfr2 | `kr2si` | internal-state conversion/modification | `vegf(r!1,r!2,nrp1bd,c~s).vegfr2(l1!1,CD47bd!3,dimer!6,c~s).CD47SIRPa(VEGFR2bd!3,c~s).vegfr2(l1!2,CD47bd,dimer!6,c~s)  -> vegf(r!1,r!2,nrp1bd,c~i).vegfr2(l1!1,CD47bd!3,dimer!6,c~i).CD47SIRPa(VEGFR2bd!3,c~i).vegfr2(l1!2,CD47bd,dimer!6,c~i)` | Transforms CD47SIRPa, vegf, vegfr2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 67 | `Unlabeled` | one-way | CD47SIRPa, vegf, vegfr2 | `kr2si` | internal-state conversion/modification | `vegf(r!1,r!2,nrp1bd,c~s).vegfr2(l1!1,CD47bd!3,dimer,c~s).CD47SIRPa(VEGFR2bd!3,c~s).vegfr2(l1!2,CD47bd!4,dimer,c~s).CD47SIRPa(VEGFR2bd!4,c~s)  -> vegf(r!1,r!2,nrp1bd,c~i).vegfr2(l1!1,CD47bd!3,dimer,c~i).CD47SIRPa(VEGFR2bd!3,c~i).vegfr2(l1!2,CD47bd!4,dimer,c~i).CD47SIRPa(VEGFR2bd!4,c~i)` | Transforms CD47SIRPa, vegf, vegfr2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 68 | `Unlabeled` | one-way | CD47SIRPa, vegf, vegfr2 | `kr2si` | internal-state conversion/modification | `vegf(r!1,r!2,nrp1bd,c~s).vegfr2(l1!1,CD47bd!3,dimer!6,c~s).CD47SIRPa(VEGFR2bd!3,c~s).vegfr2(l1!2,CD47bd!4,dimer!6,c~s).CD47SIRPa(VEGFR2bd!4,c~s)  -> vegf(r!1,r!2,nrp1bd,c~i).vegfr2(l1!1,CD47bd!3,dimer!6,c~i).CD47SIRPa(VEGFR2bd!3,c~i).vegfr2(l1!2,CD47bd!4,dimer!6,c~i).CD47SIRPa(VEGFR2bd!4,c~i)` | Transforms CD47SIRPa, vegf, vegfr2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 69 | `Unlabeled` | one-way | NRP1, vegf, vegfr2 | `kr2NRP1si` | internal-state conversion/modification | `vegf(r!1,r!2,nrp1bd!9,c~s).NRP1(vegfabd!9,c~s).vegfr2(l1!1,CD47bd,dimer,c~s).vegfr2(l1!2,CD47bd,dimer,c~s)  -> vegf(r!1,r!2,nrp1bd!9,c~i).NRP1(vegfabd!9,c~i).vegfr2(l1!1,CD47bd,dimer,c~i).vegfr2(l1!2,CD47bd,dimer,c~i)` | Transforms NRP1, vegf, vegfr2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 70 | `Unlabeled` | one-way | CD47SIRPa, NRP1, vegf, vegfr2 | `kr2NRP1si` | internal-state conversion/modification | `vegf(r!1,r!2,nrp1bd!9,c~s).NRP1(vegfabd!9,c~s).vegfr2(l1!1,CD47bd!3,dimer,c~s).CD47SIRPa(VEGFR2bd!3,c~s).vegfr2(l1!2,CD47bd,dimer,c~s)  -> vegf(r!1,r!2,nrp1bd!9,c~i).NRP1(vegfabd!9,c~i).vegfr2(l1!1,CD47bd!3,dimer,c~i).CD47SIRPa(VEGFR2bd!3,c~i).vegfr2(l1!2,CD47bd,dimer,c~i)` | Transforms CD47SIRPa, NRP1, vegf, vegfr2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 71 | `Unlabeled` | one-way | CD47SIRPa, NRP1, vegf, vegfr2 | `kr2NRP1si` | internal-state conversion/modification | `vegf(r!1,r!2,nrp1bd!9,c~s).NRP1(vegfabd!9,c~s).vegfr2(l1!1,CD47bd!3,dimer,c~s).CD47SIRPa(VEGFR2bd!3,c~s).vegfr2(l1!2,CD47bd!4,dimer,c~s).CD47SIRPa(VEGFR2bd!4,c~s)  -> vegf(r!1,r!2,nrp1bd!9,c~i).NRP1(vegfabd!9,c~i).vegfr2(l1!1,CD47bd!3,dimer,c~i).CD47SIRPa(VEGFR2bd!3,c~i).vegfr2(l1!2,CD47bd!4,dimer,c~i).CD47SIRPa(VEGFR2bd!4,c~i)` | Transforms CD47SIRPa, NRP1, vegf, vegfr2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 72 | `Unlabeled` | one-way | NRP1, vegf, vegfr2 | `kr2NRP1si` | internal-state conversion/modification | `vegf(r!1,r!2,nrp1bd!9,c~s).NRP1(vegfabd!9,c~s).vegfr2(l1!1,CD47bd,dimer!6,c~s).vegfr2(l1!2,CD47bd,dimer!6,c~s)  -> vegf(r!1,r!2,nrp1bd!9,c~i).NRP1(vegfabd!9,c~i).vegfr2(l1!1,CD47bd,dimer!6,c~i).vegfr2(l1!2,CD47bd,dimer!6,c~i)` | Transforms NRP1, vegf, vegfr2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 73 | `Unlabeled` | one-way | CD47SIRPa, NRP1, vegf, vegfr2 | `kr2NRP1si` | internal-state conversion/modification | `vegf(r!1,r!2,nrp1bd!9,c~s).NRP1(vegfabd!9,c~s).vegfr2(l1!1,CD47bd!3,dimer!6,c~s).CD47SIRPa(VEGFR2bd!3,c~s).vegfr2(l1!2,CD47bd,dimer!6,c~s)  -> vegf(r!1,r!2,nrp1bd!9,c~i).NRP1(vegfabd!9,c~i).vegfr2(l1!1,CD47bd!3,dimer!6,c~i).CD47SIRPa(VEGFR2bd!3,c~i).vegfr2(l1!2,CD47bd,dimer!6,c~i)` | Transforms CD47SIRPa, NRP1, vegf, vegfr2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 74 | `Unlabeled` | one-way | CD47SIRPa, NRP1, vegf, vegfr2 | `kr2NRP1si` | internal-state conversion/modification | `vegf(r!1,r!2,nrp1bd!9,c~s).NRP1(vegfabd!9,c~s).vegfr2(l1!1,CD47bd!3,dimer!6,c~s).CD47SIRPa(VEGFR2bd!3,c~s).vegfr2(l1!2,CD47bd!4,dimer!6,c~s).CD47SIRPa(VEGFR2bd!4,c~s)  -> vegf(r!1,r!2,nrp1bd!9,c~i).NRP1(vegfabd!9,c~i).vegfr2(l1!1,CD47bd!3,dimer!6,c~i).CD47SIRPa(VEGFR2bd!3,c~i).vegfr2(l1!2,CD47bd!4,dimer!6,c~i).CD47SIRPa(VEGFR2bd!4,c~i)` | Transforms CD47SIRPa, NRP1, vegf, vegfr2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 75 | `Unlabeled` | reversible | vegf, vegfr2 | `kr2ii2, kr2i2i` | internal-state conversion/modification | `vegf(r!1,r!2,nrp1bd,c~i).vegfr2(l1!1,CD47bd,dimer,c~i).vegfr2(l1!2,CD47bd,dimer,c~i)  <-> vegf(r!1,r!2,nrp1bd,c~i2).vegfr2(l1!1,CD47bd,dimer,c~i2).vegfr2(l1!2,CD47bd,dimer,c~i2)` | Transforms vegf, vegfr2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 76 | `Unlabeled` | reversible | vegf, vegfr2 | `kr2ii2, kr2i2i` | internal-state conversion/modification | `vegf(r!1,r!2,nrp1bd,c~i).vegfr2(l1!1,CD47bd,dimer!6,c~i).vegfr2(l1!2,CD47bd,dimer!6,c~i)  <-> vegf(r!1,r!2,nrp1bd,c~i2).vegfr2(l1!1,CD47bd,dimer!6,c~i2).vegfr2(l1!2,CD47bd,dimer!6,c~i2)` | Transforms vegf, vegfr2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 77 | `Unlabeled` | reversible | CD47SIRPa, vegf, vegfr2 | `kr2ii2, kr2i2i` | internal-state conversion/modification | `vegf(r!1,r!2,nrp1bd,c~i).vegfr2(l1!1,CD47bd!3,dimer,c~i).CD47SIRPa(VEGFR2bd!3,c~i).vegfr2(l1!2,CD47bd,dimer,c~i)  <-> vegf(r!1,r!2,nrp1bd,c~i2).vegfr2(l1!1,CD47bd!3,dimer,c~i2).CD47SIRPa(VEGFR2bd!3,c~i2).vegfr2(l1!2,CD47bd,dimer,c~i2)` | Transforms CD47SIRPa, vegf, vegfr2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 78 | `Unlabeled` | reversible | CD47SIRPa, vegf, vegfr2 | `kr2ii2, kr2i2i` | internal-state conversion/modification | `vegf(r!1,r!2,nrp1bd,c~i).vegfr2(l1!1,CD47bd!3,dimer!4,c~i).CD47SIRPa(VEGFR2bd!3,c~i).vegfr2(l1!2,CD47bd,dimer!4,c~i)  <-> vegf(r!1,r!2,nrp1bd,c~i2).vegfr2(l1!1,CD47bd!3,dimer!4,c~i2).CD47SIRPa(VEGFR2bd!3,c~i2).vegfr2(l1!2,CD47bd,dimer!4,c~i2)` | Transforms CD47SIRPa, vegf, vegfr2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 79 | `Unlabeled` | reversible | CD47SIRPa, vegf, vegfr2 | `kr2ii2, kr2i2i` | internal-state conversion/modification | `vegf(r!1,r!2,nrp1bd,c~i).vegfr2(l1!1,CD47bd!3,dimer,c~i).CD47SIRPa(VEGFR2bd!3,c~i).vegfr2(l1!2,CD47bd!4,dimer,c~i).CD47SIRPa(VEGFR2bd!4,c~i)  <-> vegf(r!1,r!2,nrp1bd,c~i2).vegfr2(l1!1,CD47bd!3,dimer,c~i2).CD47SIRPa(VEGFR2bd!3,c~i2).vegfr2(l1!2,CD47bd!4,dimer,c~i2).CD47SIRPa(VEGFR2bd!4,c~i2)` | Transforms CD47SIRPa, vegf, vegfr2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 80 | `Unlabeled` | reversible | CD47SIRPa, vegf, vegfr2 | `kr2ii2, kr2i2i` | internal-state conversion/modification | `vegf(r!1,r!2,nrp1bd,c~i).vegfr2(l1!1,CD47bd!3,dimer!6,c~i).CD47SIRPa(VEGFR2bd!3,c~i).vegfr2(l1!2,CD47bd!4,dimer!6,c~i).CD47SIRPa(VEGFR2bd!4,c~i)  <-> vegf(r!1,r!2,nrp1bd,c~i2).vegfr2(l1!1,CD47bd!3,dimer!6,c~i2).CD47SIRPa(VEGFR2bd!3,c~i2).vegfr2(l1!2,CD47bd!4,dimer!6,c~i2).CD47SIRPa(VEGFR2bd!4,c~i2)` | Transforms CD47SIRPa, vegf, vegfr2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 81 | `Unlabeled` | reversible | NRP1, vegf, vegfr2 | `kr2NRP1ii2, kr2NRP1i2i` | internal-state conversion/modification | `vegf(r!1,r!2,nrp1bd!9,c~i).NRP1(vegfabd!9,c~i).vegfr2(l1!1,CD47bd,dimer,c~i).vegfr2(l1!2,CD47bd,dimer,c~i)  <-> vegf(r!1,r!2,nrp1bd!9,c~i2).NRP1(vegfabd!9,c~i2).vegfr2(l1!1,CD47bd,dimer,c~i2).vegfr2(l1!2,CD47bd,dimer,c~i2)` | Transforms NRP1, vegf, vegfr2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 82 | `Unlabeled` | reversible | NRP1, vegf, vegfr2 | `kr2NRP1ii2, kr2NRP1i2i` | internal-state conversion/modification | `vegf(r!1,r!2,nrp1bd!9,c~i).NRP1(vegfabd!9,c~i).vegfr2(l1!1,CD47bd,dimer!6,c~i).vegfr2(l1!2,CD47bd,dimer!6,c~i)  <-> vegf(r!1,r!2,nrp1bd!9,c~i2).NRP1(vegfabd!9,c~i2).vegfr2(l1!1,CD47bd,dimer!6,c~i2).vegfr2(l1!2,CD47bd,dimer!6,c~i2)` | Transforms NRP1, vegf, vegfr2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 83 | `Unlabeled` | reversible | CD47SIRPa, NRP1, vegf, vegfr2 | `kr2NRP1ii2, kr2NRP1i2i` | internal-state conversion/modification | `vegf(r!1,r!2,nrp1bd!9,c~i).NRP1(vegfabd!9,c~i).vegfr2(l1!1,CD47bd!3,dimer,c~i).CD47SIRPa(VEGFR2bd!3,c~i).vegfr2(l1!2,CD47bd,dimer,c~i)  <-> vegf(r!1,r!2,nrp1bd!9,c~i2).NRP1(vegfabd!9,c~i2).vegfr2(l1!1,CD47bd!3,dimer,c~i2).CD47SIRPa(VEGFR2bd!3,c~i2).vegfr2(l1!2,CD47bd,dimer,c~i2)` | Transforms CD47SIRPa, NRP1, vegf, vegfr2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 84 | `Unlabeled` | reversible | CD47SIRPa, NRP1, vegf, vegfr2 | `kr2NRP1ii2, kr2NRP1i2i` | internal-state conversion/modification | `vegf(r!1,r!2,nrp1bd!9,c~i).NRP1(vegfabd!9,c~i).vegfr2(l1!1,CD47bd!3,dimer!6,c~i).CD47SIRPa(VEGFR2bd!3,c~i).vegfr2(l1!2,CD47bd,dimer!6,c~i)  <-> vegf(r!1,r!2,nrp1bd!9,c~i2).NRP1(vegfabd!9,c~i2).vegfr2(l1!1,CD47bd!3,dimer!6,c~i2).CD47SIRPa(VEGFR2bd!3,c~i2).vegfr2(l1!2,CD47bd,dimer!6,c~i2)` | Transforms CD47SIRPa, NRP1, vegf, vegfr2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 85 | `Unlabeled` | reversible | CD47SIRPa, NRP1, vegf, vegfr2 | `kr2NRP1ii2, kr2NRP1i2i` | internal-state conversion/modification | `vegf(r!1,r!2,nrp1bd!9,c~i).NRP1(vegfabd!9,c~i).vegfr2(l1!1,CD47bd!3,dimer,c~i).CD47SIRPa(VEGFR2bd!3,c~i).vegfr2(l1!2,CD47bd!4,dimer,c~i).CD47SIRPa(VEGFR2bd!4,c~i)  <-> vegf(r!1,r!2,nrp1bd!9,c~i2).NRP1(vegfabd!9,c~i2).vegfr2(l1!1,CD47bd!3,dimer,c~i2).CD47SIRPa(VEGFR2bd!3,c~i2).vegfr2(l1!2,CD47bd!4,dimer,c~i2).CD47SIRPa(VEGFR2bd!4,c~i2)` | Transforms CD47SIRPa, NRP1, vegf, vegfr2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 86 | `Unlabeled` | reversible | CD47SIRPa, NRP1, vegf, vegfr2 | `kr2NRP1ii2, kr2NRP1i2i` | internal-state conversion/modification | `vegf(r!1,r!2,nrp1bd!9,c~i).NRP1(vegfabd!9,c~i).vegfr2(l1!1,CD47bd!3,dimer!6,c~i).CD47SIRPa(VEGFR2bd!3,c~i).vegfr2(l1!2,CD47bd!4,dimer!6,c~i).CD47SIRPa(VEGFR2bd!4,c~i)  <-> vegf(r!1,r!2,nrp1bd!9,c~i2).NRP1(vegfabd!9,c~i2).vegfr2(l1!1,CD47bd!3,dimer!6,c~i2).CD47SIRPa(VEGFR2bd!3,c~i2).vegfr2(l1!2,CD47bd!4,dimer!6,c~i2).CD47SIRPa(VEGFR2bd!4,c~i2)` | Transforms CD47SIRPa, NRP1, vegf, vegfr2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 87 | `Unlabeled` | one-way | NRP1, vegf, vegfr2 | `kr2NRP1i2r` | internal-state conversion/modification | `vegf(r!1,r!2,nrp1bd!9,c~i2).NRP1(vegfabd!9,c~i2).vegfr2(l1!1,CD47bd,dimer,c~i2).vegfr2(l1!2,CD47bd,dimer,c~i2)  -> vegf(r!1,r!2,nrp1bd!9,c~r).NRP1(vegfabd!9,c~r).vegfr2(l1!1,CD47bd,dimer,c~r).vegfr2(l1!2,CD47bd,dimer,c~r)` | Transforms NRP1, vegf, vegfr2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 88 | `Unlabeled` | one-way | NRP1, vegf, vegfr2 | `kr2NRP1i2r` | internal-state conversion/modification | `vegf(r!1,r!2,nrp1bd!9,c~i2).NRP1(vegfabd!9,c~i2).vegfr2(l1!1,CD47bd,dimer!6,c~i2).vegfr2(l1!2,CD47bd,dimer!6,c~i2)  -> vegf(r!1,r!2,nrp1bd!9,c~r).NRP1(vegfabd!9,c~r).vegfr2(l1!1,CD47bd,dimer!6,c~r).vegfr2(l1!2,CD47bd,dimer!6,c~r)` | Transforms NRP1, vegf, vegfr2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 89 | `Unlabeled` | one-way | CD47SIRPa, NRP1, vegf, vegfr2 | `kr2NRP1i2r` | internal-state conversion/modification | `vegf(r!1,r!2,nrp1bd!9,c~i2).NRP1(vegfabd!9,c~i2).vegfr2(l1!1,CD47bd!3,dimer,c~i2).CD47SIRPa(TSP1bd,VEGFR2bd!3,c~i2).vegfr2(l1!2,CD47bd,dimer,c~i2)  -> vegf(r!1,r!2,nrp1bd!9,c~r).NRP1(vegfabd!9,c~r).vegfr2(l1!1,CD47bd!3,dimer,c~r).CD47SIRPa(TSP1bd,VEGFR2bd!3,c~r).vegfr2(l1!2,CD47bd,dimer,c~r)` | Transforms CD47SIRPa, NRP1, vegf, vegfr2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 90 | `Unlabeled` | one-way | CD47SIRPa, NRP1, vegf, vegfr2 | `kr2NRP1i2r` | internal-state conversion/modification | `vegf(r!1,r!2,nrp1bd!9,c~i2).NRP1(vegfabd!9,c~i2).vegfr2(l1!1,CD47bd!3,dimer!6,c~i2).CD47SIRPa(TSP1bd,VEGFR2bd!3,c~i2).vegfr2(l1!2,CD47bd,dimer!6,c~i2)  -> vegf(r!1,r!2,nrp1bd!9,c~r).NRP1(vegfabd!9,c~r).vegfr2(l1!1,CD47bd!3,dimer!6,c~r).CD47SIRPa(TSP1bd,VEGFR2bd!3,c~r).vegfr2(l1!2,CD47bd,dimer!6,c~r)` | Transforms CD47SIRPa, NRP1, vegf, vegfr2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 91 | `Unlabeled` | one-way | CD47SIRPa, NRP1, vegf, vegfr2 | `kr2NRP1i2r` | internal-state conversion/modification | `vegf(r!1,r!2,nrp1bd!9,c~i2).NRP1(vegfabd!9,c~i2).vegfr2(l1!1,CD47bd!3,dimer,c~i2).CD47SIRPa(TSP1bd,VEGFR2bd!3,c~i2).vegfr2(l1!2,CD47bd!4,dimer,c~i2).CD47SIRPa(TSP1bd,VEGFR2bd!4,c~i2)  -> vegf(r!1,r!2,nrp1bd!9,c~r).NRP1(vegfabd!9,c~r).vegfr2(l1!1,CD47bd!3,dimer,c~r).CD47SIRPa(TSP1bd,VEGFR2bd!3,c~r).vegfr2(l1!2,CD47bd!4,dimer,c~r).CD47SIRPa(TSP1bd,VEGFR2bd!4,c~r)` | Transforms CD47SIRPa, NRP1, vegf, vegfr2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 92 | `Unlabeled` | one-way | CD47SIRPa, NRP1, vegf, vegfr2 | `kr2NRP1i2r` | internal-state conversion/modification | `vegf(r!1,r!2,nrp1bd!9,c~i2).NRP1(vegfabd!9,c~i2).vegfr2(l1!1,CD47bd!3,dimer!6,c~i2).CD47SIRPa(TSP1bd,VEGFR2bd!3,c~i2).vegfr2(l1!2,CD47bd!4,dimer!6,c~i2).CD47SIRPa(TSP1bd,VEGFR2bd!4,c~i2)  -> vegf(r!1,r!2,nrp1bd!9,c~r).NRP1(vegfabd!9,c~r).vegfr2(l1!1,CD47bd!3,dimer!6,c~r).CD47SIRPa(TSP1bd,VEGFR2bd!3,c~r).vegfr2(l1!2,CD47bd!4,dimer!6,c~r).CD47SIRPa(TSP1bd,VEGFR2bd!4,c~r)` | Transforms CD47SIRPa, NRP1, vegf, vegfr2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 93 | `Unlabeled` | one-way | CD47SIRPa, NRP1, vegf, vegfr2 | `kr2NRP1i2r*fTSP1i2r` | internal-state conversion/modification | `vegf(r!1,r!2,nrp1bd!9,c~i2).NRP1(vegfabd!9,c~i2).vegfr2(l1!1,CD47bd!3,dimer,c~i2).CD47SIRPa(TSP1bd!+,VEGFR2bd!3,c~i2).vegfr2(l1!2,CD47bd,dimer,c~i2)  -> vegf(r!1,r!2,nrp1bd!9,c~r).NRP1(vegfabd!9,c~r).vegfr2(l1!1,CD47bd!3,dimer,c~r).CD47SIRPa(TSP1bd!+,VEGFR2bd!3,c~r).vegfr2(l1!2,CD47bd,dimer,c~r)` | Transforms CD47SIRPa, NRP1, vegf, vegfr2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 94 | `Unlabeled` | one-way | CD47SIRPa, NRP1, vegf, vegfr2 | `kr2NRP1i2r*fTSP1i2r` | internal-state conversion/modification | `vegf(r!1,r!2,nrp1bd!9,c~i2).NRP1(vegfabd!9,c~i2).vegfr2(l1!1,CD47bd!3,dimer!6,c~i2).CD47SIRPa(TSP1bd!+,VEGFR2bd!3,c~i2).vegfr2(l1!2,CD47bd,dimer!6,c~i2)  -> vegf(r!1,r!2,nrp1bd!9,c~r).NRP1(vegfabd!9,c~r).vegfr2(l1!1,CD47bd!3,dimer!6,c~r).CD47SIRPa(TSP1bd!+,VEGFR2bd!3,c~r).vegfr2(l1!2,CD47bd,dimer!6,c~r)` | Transforms CD47SIRPa, NRP1, vegf, vegfr2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 95 | `Unlabeled` | one-way | CD47SIRPa, NRP1, vegf, vegfr2 | `kr2NRP1i2r*fTSP1i2r` | internal-state conversion/modification | `vegf(r!1,r!2,nrp1bd!9,c~i2).NRP1(vegfabd!9,c~i2).vegfr2(l1!1,CD47bd!3,dimer,c~i2).CD47SIRPa(TSP1bd!+,VEGFR2bd!3,c~i2).vegfr2(l1!2,CD47bd!4,dimer,c~i2).CD47SIRPa(VEGFR2bd!4,c~i2)  -> vegf(r!1,r!2,nrp1bd!9,c~r).NRP1(vegfabd!9,c~r).vegfr2(l1!1,CD47bd!3,dimer,c~r).CD47SIRPa(TSP1bd!+,VEGFR2bd!3,c~r).vegfr2(l1!2,CD47bd!4,dimer,c~r).CD47SIRPa(VEGFR2bd!4,c~r)` | Transforms CD47SIRPa, NRP1, vegf, vegfr2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 96 | `Unlabeled` | one-way | CD47SIRPa, NRP1, vegf, vegfr2 | `kr2NRP1i2r*fTSP1i2r` | internal-state conversion/modification | `vegf(r!1,r!2,nrp1bd!9,c~i2).NRP1(vegfabd!9,c~i2).vegfr2(l1!1,CD47bd!3,dimer!6,c~i2).CD47SIRPa(TSP1bd!+,VEGFR2bd!3,c~i2).vegfr2(l1!2,CD47bd!4,dimer!6,c~i2).CD47SIRPa(VEGFR2bd!4,c~i2)  -> vegf(r!1,r!2,nrp1bd!9,c~r).NRP1(vegfabd!9,c~r).vegfr2(l1!1,CD47bd!3,dimer!6,c~r).CD47SIRPa(TSP1bd!+,VEGFR2bd!3,c~r).vegfr2(l1!2,CD47bd!4,dimer!6,c~r).CD47SIRPa(VEGFR2bd!4,c~r)` | Transforms CD47SIRPa, NRP1, vegf, vegfr2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 97 | `Unlabeled` | one-way | vegfr2 | `kr2rs` | internal-state conversion/modification | `vegfr2(l1,Y1175~Y,CD47bd,dimer,c~r)  -> vegfr2(l1,Y1175~Y,CD47bd,dimer,c~s)` | Transforms vegfr2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 98 | `Unlabeled` | one-way | NRP1 | `kr2rs` | internal-state conversion/modification | `NRP1(vegfabd,c~r)  -> NRP1(vegfabd,c~s)` | Transforms NRP1 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 99 | `Unlabeled` | one-way | CD47SIRPa | `kr2rs` | internal-state conversion/modification | `CD47SIRPa(TSP1bd,VEGFR2bd,c~r)  -> CD47SIRPa(TSP1bd,VEGFR2bd,c~s)` | Transforms CD47SIRPa by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 100 | `Unlabeled` | one-way | NRP1, vegf, vegfr2 | `kvroff` | state and binding-pattern rewrite | `vegf(r!1,r!2,nrp1bd!9,c~r).NRP1(vegfabd!9,c~r).vegfr2(l1!1,dimer,c~r).vegfr2(l1!2,dimer,c~r)  -> NRP1(vegfabd,c~r) + vegfr2(l1,dimer,c~r) + vegfr2(l1,dimer,c~r)` | Transforms NRP1, vegf, vegfr2 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 101 | `Unlabeled` | one-way | NRP1, vegf, vegfr2 | `kvroff` | internal-state conversion/modification | `vegf(r!1,r!2,nrp1bd!9,c~r).NRP1(vegfabd!9,c~r).vegfr2(l1!1,dimer!6,c~r).vegfr2(l1!2,dimer!6,c~r)  -> NRP1(vegfabd,c~r) + vegfr2(l1,dimer!6,c~r).vegfr2(l1,dimer!6,c~r)` | Transforms NRP1, vegf, vegfr2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 102 | `Unlabeled` | one-way | vegfr2 | `kdRR` | state and binding-pattern rewrite | `vegfr2(dimer!6,c~r).vegfr2(dimer!6,c~r)  -> vegfr2(dimer,c~r) + vegfr2(dimer,c~r)` | Transforms vegfr2 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 103 | `Unlabeled` | one-way | CD47SIRPa, vegfr2 | `kr2CD47off` | state and binding-pattern rewrite | `vegfr2(CD47bd!3,c~r).CD47SIRPa(VEGFR2bd!3,c~r)  -> vegfr2(CD47bd,c~r) + CD47SIRPa(VEGFR2bd,c~r)` | Transforms CD47SIRPa, vegfr2 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 104 | `Unlabeled` | one-way | CD47SIRPa, TSP1 | `koffCD47TSP1` | state and binding-pattern rewrite | `CD47SIRPa(TSP1bd!1,c~r).TSP1(CD47bd!1)  -> CD47SIRPa(TSP1bd,c~r)` | Transforms CD47SIRPa, TSP1 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 105 | `Unlabeled` | one-way | Trash, vegf, vegfr2 | `kdegi0` | state and binding-pattern rewrite | `vegf(r!1,r!2,nrp1bd,c~i).vegfr2(l1!1,Y1175~pY,CD47bd,c~i).vegfr2(l1!2,CD47bd,c~i)  -> Trash()` | Transforms Trash, vegf, vegfr2 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 106 | `Unlabeled` | one-way | Trash, vegf, vegfr2 | `kdegi0noP` | state and binding-pattern rewrite | `vegf(r!1,r!2,nrp1bd,c~i).vegfr2(l1!1,Y1175~Y,CD47bd,c~i).vegfr2(l1!2,Y1175~Y,CD47bd,c~i)  -> Trash()` | Transforms Trash, vegf, vegfr2 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 107 | `Unlabeled` | one-way | CD47SIRPa, Trash, vegf, vegfr2 | `kdegi0` | state and binding-pattern rewrite | `vegf(r!1,r!2,nrp1bd,c~i).vegfr2(l1!1,Y1175~pY,CD47bd!3,c~i).CD47SIRPa(TSP1bd,VEGFR2bd!3,c~i).vegfr2(l1!2,CD47bd,c~i)  -> Trash()` | Transforms CD47SIRPa, Trash, vegf, vegfr2 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 108 | `Unlabeled` | one-way | CD47SIRPa, Trash, vegf, vegfr2 | `kdegi0noP` | state and binding-pattern rewrite | `vegf(r!1,r!2,nrp1bd,c~i).vegfr2(l1!1,Y1175~Y,CD47bd!3,c~i).CD47SIRPa(TSP1bd,VEGFR2bd!3,c~i).vegfr2(l1!2,Y1175~Y,CD47bd,c~i)  -> Trash()` | Transforms CD47SIRPa, Trash, vegf, vegfr2 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 109 | `Unlabeled` | one-way | CD47SIRPa, Trash, vegf, vegfr2 | `kdegi0` | state and binding-pattern rewrite | `vegf(r!1,r!2,nrp1bd,c~i).vegfr2(l1!1,Y1175~pY,CD47bd!3,c~i).CD47SIRPa(TSP1bd,VEGFR2bd!3,c~i).vegfr2(l1!2,CD47bd!4,c~i).CD47SIRPa(TSP1bd,VEGFR2bd!4,c~i)  -> Trash()` | Transforms CD47SIRPa, Trash, vegf, vegfr2 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 110 | `Unlabeled` | one-way | CD47SIRPa, Trash, vegf, vegfr2 | `kdegi0noP` | state and binding-pattern rewrite | `vegf(r!1,r!2,nrp1bd,c~i).vegfr2(l1!1,Y1175~Y,CD47bd!3,c~i).CD47SIRPa(TSP1bd,VEGFR2bd!3,c~i).vegfr2(l1!2,Y1175~Y,CD47bd!4,c~i).CD47SIRPa(TSP1bd,VEGFR2bd!4,c~i)  -> Trash()` | Transforms CD47SIRPa, Trash, vegf, vegfr2 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 111 | `Unlabeled` | one-way | Trash, vegf, vegfr2 | `kdegi20` | state and binding-pattern rewrite | `vegf(r!1,r!2,nrp1bd,c~i2).vegfr2(l1!1,Y1175~pY,CD47bd,c~i2).vegfr2(l1!2,CD47bd,c~i2)  -> Trash()` | Transforms Trash, vegf, vegfr2 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 112 | `Unlabeled` | one-way | Trash, vegf, vegfr2 | `kdegi20noP` | state and binding-pattern rewrite | `vegf(r!1,r!2,nrp1bd,c~i2).vegfr2(l1!1,Y1175~Y,CD47bd,c~i2).vegfr2(l1!2,Y1175~Y,CD47bd,c~i2)  -> Trash()` | Transforms Trash, vegf, vegfr2 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 113 | `Unlabeled` | one-way | CD47SIRPa, Trash, vegf, vegfr2 | `kdegi20` | state and binding-pattern rewrite | `vegf(r!1,r!2,nrp1bd,c~i2).vegfr2(l1!1,Y1175~pY,CD47bd!3,c~i2).CD47SIRPa(TSP1bd,VEGFR2bd!3,c~i2).vegfr2(l1!2,CD47bd,c~i2)  -> Trash()` | Transforms CD47SIRPa, Trash, vegf, vegfr2 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 114 | `Unlabeled` | one-way | CD47SIRPa, Trash, vegf, vegfr2 | `kdegi20noP` | state and binding-pattern rewrite | `vegf(r!1,r!2,nrp1bd,c~i2).vegfr2(l1!1,Y1175~Y,CD47bd!3,c~i2).CD47SIRPa(TSP1bd,VEGFR2bd!3,c~i2).vegfr2(l1!2,Y1175~Y,CD47bd,c~i2)  -> Trash()` | Transforms CD47SIRPa, Trash, vegf, vegfr2 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 115 | `Unlabeled` | one-way | CD47SIRPa, Trash, vegf, vegfr2 | `kdegi20` | state and binding-pattern rewrite | `vegf(r!1,r!2,nrp1bd,c~i2).vegfr2(l1!1,Y1175~pY,CD47bd!3,c~i2).CD47SIRPa(TSP1bd,VEGFR2bd!3,c~i2).vegfr2(l1!2,CD47bd!4,c~i2).CD47SIRPa(TSP1bd,VEGFR2bd!4,c~i2)  -> Trash()` | Transforms CD47SIRPa, Trash, vegf, vegfr2 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 116 | `Unlabeled` | one-way | CD47SIRPa, Trash, vegf, vegfr2 | `kdegi20noP` | state and binding-pattern rewrite | `vegf(r!1,r!2,nrp1bd,c~i2).vegfr2(l1!1,Y1175~Y,CD47bd!3,c~i2).CD47SIRPa(TSP1bd,VEGFR2bd!3,c~i2).vegfr2(l1!2,Y1175~Y,CD47bd!4,c~i2).CD47SIRPa(TSP1bd,VEGFR2bd!4,c~i2)  -> Trash()` | Transforms CD47SIRPa, Trash, vegf, vegfr2 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 117 | `Unlabeled` | one-way | NRP1, Trash, vegf, vegfr2 | `kdegr2NRP1i0` | state and binding-pattern rewrite | `vegf(r!1,r!2,nrp1bd!9,c~i).NRP1(vegfabd!9,c~i).vegfr2(l1!1,Y1175~pY,CD47bd,c~i).vegfr2(l1!2,CD47bd,c~i)  -> Trash()` | Transforms NRP1, Trash, vegf, vegfr2 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 118 | `Unlabeled` | one-way | NRP1, Trash, vegf, vegfr2 | `kdegr2NRP1i0noP` | state and binding-pattern rewrite | `vegf(r!1,r!2,nrp1bd!9,c~i).NRP1(vegfabd!9,c~i).vegfr2(l1!1,Y1175~Y,CD47bd,c~i).vegfr2(l1!2,Y1175~Y,CD47bd,c~i)  -> Trash()` | Transforms NRP1, Trash, vegf, vegfr2 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 119 | `Unlabeled` | one-way | CD47SIRPa, NRP1, Trash, vegf, vegfr2 | `kdegr2NRP1i0` | state and binding-pattern rewrite | `vegf(r!1,r!2,nrp1bd!9,c~i).NRP1(vegfabd!9,c~i).vegfr2(l1!1,Y1175~pY,CD47bd!3,c~i).CD47SIRPa(TSP1bd,VEGFR2bd!3,c~i).vegfr2(l1!2,CD47bd,c~i)  -> Trash()` | Transforms CD47SIRPa, NRP1, Trash, vegf, vegfr2 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 120 | `Unlabeled` | one-way | CD47SIRPa, NRP1, Trash, vegf, vegfr2 | `kdegr2NRP1i0noP` | state and binding-pattern rewrite | `vegf(r!1,r!2,nrp1bd!9,c~i).NRP1(vegfabd!9,c~i).vegfr2(l1!1,Y1175~Y,CD47bd!3,c~i).CD47SIRPa(TSP1bd,VEGFR2bd!3,c~i).vegfr2(l1!2,Y1175~Y,CD47bd,c~i)  -> Trash()` | Transforms CD47SIRPa, NRP1, Trash, vegf, vegfr2 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 121 | `Unlabeled` | one-way | CD47SIRPa, NRP1, Trash, vegf, vegfr2 | `kdegr2NRP1i0` | state and binding-pattern rewrite | `vegf(r!1,r!2,nrp1bd!9,c~i).NRP1(vegfabd!9,c~i).vegfr2(l1!1,Y1175~pY,CD47bd!3,c~i).CD47SIRPa(TSP1bd,VEGFR2bd!3,c~i).vegfr2(l1!2,CD47bd!4,c~i).CD47SIRPa(TSP1bd,VEGFR2bd!4,c~i)  -> Trash()` | Transforms CD47SIRPa, NRP1, Trash, vegf, vegfr2 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 122 | `Unlabeled` | one-way | CD47SIRPa, NRP1, Trash, vegf, vegfr2 | `kdegr2NRP1i0noP` | state and binding-pattern rewrite | `vegf(r!1,r!2,nrp1bd!9,c~i).NRP1(vegfabd!9,c~i).vegfr2(l1!1,Y1175~Y,CD47bd!3,c~i).CD47SIRPa(TSP1bd,VEGFR2bd!3,c~i).vegfr2(l1!2,Y1175~Y,CD47bd!4,c~i).CD47SIRPa(TSP1bd,VEGFR2bd!4,c~i)  -> Trash()` | Transforms CD47SIRPa, NRP1, Trash, vegf, vegfr2 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 123 | `Unlabeled` | one-way | NRP1, Trash, vegf, vegfr2 | `kdegr2NRP1i20` | state and binding-pattern rewrite | `vegf(r!1,r!2,nrp1bd!9,c~i2).NRP1(vegfabd!9,c~i2).vegfr2(l1!1,Y1175~pY,CD47bd,c~i2).vegfr2(l1!2,CD47bd,c~i2)  -> Trash()` | Transforms NRP1, Trash, vegf, vegfr2 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 124 | `Unlabeled` | one-way | NRP1, Trash, vegf, vegfr2 | `kdegr2NRP1i20noP` | state and binding-pattern rewrite | `vegf(r!1,r!2,nrp1bd!9,c~i2).NRP1(vegfabd!9,c~i2).vegfr2(l1!1,Y1175~Y,CD47bd,c~i2).vegfr2(l1!2,Y1175~Y,CD47bd,c~i2)  -> Trash()` | Transforms NRP1, Trash, vegf, vegfr2 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 125 | `Unlabeled` | one-way | CD47SIRPa, NRP1, Trash, vegf, vegfr2 | `kdegr2NRP1i20` | state and binding-pattern rewrite | `vegf(r!1,r!2,nrp1bd!9,c~i2).NRP1(vegfabd!9,c~i2).vegfr2(l1!1,Y1175~pY,CD47bd!3,c~i2).CD47SIRPa(TSP1bd,VEGFR2bd!3,c~i2).vegfr2(l1!2,CD47bd,c~i2)  -> Trash()` | Transforms CD47SIRPa, NRP1, Trash, vegf, vegfr2 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 126 | `Unlabeled` | one-way | CD47SIRPa, NRP1, Trash, vegf, vegfr2 | `kdegr2NRP1i20noP` | state and binding-pattern rewrite | `vegf(r!1,r!2,nrp1bd!9,c~i2).NRP1(vegfabd!9,c~i2).vegfr2(l1!1,Y1175~Y,CD47bd!3,c~i2).CD47SIRPa(TSP1bd,VEGFR2bd!3,c~i2).vegfr2(l1!2,Y1175~Y,CD47bd,c~i2)  -> Trash()` | Transforms CD47SIRPa, NRP1, Trash, vegf, vegfr2 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 127 | `Unlabeled` | one-way | CD47SIRPa, NRP1, Trash, vegf, vegfr2 | `kdegr2NRP1i20` | state and binding-pattern rewrite | `vegf(r!1,r!2,nrp1bd!9,c~i2).NRP1(vegfabd!9,c~i2).vegfr2(l1!1,Y1175~pY,CD47bd!3,c~i2).CD47SIRPa(TSP1bd,VEGFR2bd!3,c~i2).vegfr2(l1!2,CD47bd!4,c~i2).CD47SIRPa(TSP1bd,VEGFR2bd!4,c~i2)  -> Trash()` | Transforms CD47SIRPa, NRP1, Trash, vegf, vegfr2 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 128 | `Unlabeled` | one-way | CD47SIRPa, NRP1, Trash, vegf, vegfr2 | `kdegr2NRP1i20noP` | state and binding-pattern rewrite | `vegf(r!1,r!2,nrp1bd!9,c~i2).NRP1(vegfabd!9,c~i2).vegfr2(l1!1,Y1175~Y,CD47bd!3,c~i2).CD47SIRPa(TSP1bd,VEGFR2bd!3,c~i2).vegfr2(l1!2,Y1175~Y,CD47bd!4,c~i2).CD47SIRPa(TSP1bd,VEGFR2bd!4,c~i2)  -> Trash()` | Transforms CD47SIRPa, NRP1, Trash, vegf, vegfr2 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 129 | `Unlabeled` | one-way | CD47SIRPa, Trash, vegf, vegfr2 | `kdegi0*f_TSP1deg` | state and binding-pattern rewrite | `vegf(r!1,r!2,nrp1bd,c~i).vegfr2(l1!1,Y1175~pY,CD47bd!3,c~i).CD47SIRPa(TSP1bd!+,VEGFR2bd!3,c~i).vegfr2(l1!2,CD47bd,c~i)  -> Trash()` | Transforms CD47SIRPa, Trash, vegf, vegfr2 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 130 | `Unlabeled` | one-way | CD47SIRPa, Trash, vegf, vegfr2 | `kdegi0noP*f_TSP1deg` | state and binding-pattern rewrite | `vegf(r!1,r!2,nrp1bd,c~i).vegfr2(l1!1,Y1175~Y,CD47bd!3,c~i).CD47SIRPa(TSP1bd!+,VEGFR2bd!3,c~i).vegfr2(l1!2,Y1175~Y,CD47bd,c~i)  -> Trash()` | Transforms CD47SIRPa, Trash, vegf, vegfr2 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 131 | `Unlabeled` | one-way | CD47SIRPa, Trash, vegf, vegfr2 | `kdegi0*f_TSP1deg` | state and binding-pattern rewrite | `vegf(r!1,r!2,nrp1bd,c~i).vegfr2(l1!1,Y1175~pY,CD47bd!3,c~i).CD47SIRPa(TSP1bd!+,VEGFR2bd!3,c~i).vegfr2(l1!2,CD47bd!4,c~i).CD47SIRPa(VEGFR2bd!4,c~i)  -> Trash()` | Transforms CD47SIRPa, Trash, vegf, vegfr2 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 132 | `Unlabeled` | one-way | CD47SIRPa, Trash, vegf, vegfr2 | `kdegi0noP*f_TSP1deg` | state and binding-pattern rewrite | `vegf(r!1,r!2,nrp1bd,c~i).vegfr2(l1!1,Y1175~Y,CD47bd!3,c~i).CD47SIRPa(TSP1bd!+,VEGFR2bd!3,c~i).vegfr2(l1!2,Y1175~Y,CD47bd!4,c~i).CD47SIRPa(VEGFR2bd!4,c~i)  -> Trash()` | Transforms CD47SIRPa, Trash, vegf, vegfr2 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 133 | `Unlabeled` | one-way | CD47SIRPa, Trash, vegf, vegfr2 | `kdegi20*f_TSP1deg` | state and binding-pattern rewrite | `vegf(r!1,r!2,nrp1bd,c~i2).vegfr2(l1!1,Y1175~pY,CD47bd!3,c~i2).CD47SIRPa(TSP1bd!+,VEGFR2bd!3,c~i2).vegfr2(l1!2,CD47bd,c~i2)  -> Trash()` | Transforms CD47SIRPa, Trash, vegf, vegfr2 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 134 | `Unlabeled` | one-way | CD47SIRPa, Trash, vegf, vegfr2 | `kdegi20noP*f_TSP1deg` | state and binding-pattern rewrite | `vegf(r!1,r!2,nrp1bd,c~i2).vegfr2(l1!1,Y1175~Y,CD47bd!3,c~i2).CD47SIRPa(TSP1bd!+,VEGFR2bd!3,c~i2).vegfr2(l1!2,Y1175~Y,CD47bd,c~i2)  -> Trash()` | Transforms CD47SIRPa, Trash, vegf, vegfr2 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 135 | `Unlabeled` | one-way | CD47SIRPa, Trash, vegf, vegfr2 | `kdegi20*f_TSP1deg` | state and binding-pattern rewrite | `vegf(r!1,r!2,nrp1bd,c~i2).vegfr2(l1!1,Y1175~pY,CD47bd!3,c~i2).CD47SIRPa(TSP1bd!+,VEGFR2bd!3,c~i2).vegfr2(l1!2,CD47bd!4,c~i2).CD47SIRPa(VEGFR2bd!4,c~i2)  -> Trash()` | Transforms CD47SIRPa, Trash, vegf, vegfr2 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 136 | `Unlabeled` | one-way | CD47SIRPa, Trash, vegf, vegfr2 | `kdegi20noP*f_TSP1deg` | state and binding-pattern rewrite | `vegf(r!1,r!2,nrp1bd,c~i2).vegfr2(l1!1,Y1175~Y,CD47bd!3,c~i2).CD47SIRPa(TSP1bd!+,VEGFR2bd!3,c~i2).vegfr2(l1!2,Y1175~Y,CD47bd!4,c~i2).CD47SIRPa(VEGFR2bd!4,c~i2)  -> Trash()` | Transforms CD47SIRPa, Trash, vegf, vegfr2 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 137 | `Unlabeled` | one-way | CD47SIRPa, NRP1, Trash, vegf, vegfr2 | `kdegr2NRP1i0*f_TSP1deg` | state and binding-pattern rewrite | `vegf(r!1,r!2,nrp1bd!9,c~i).NRP1(vegfabd!9,c~i).vegfr2(l1!1,Y1175~pY,CD47bd!3,c~i).CD47SIRPa(TSP1bd!+,VEGFR2bd!3,c~i).vegfr2(l1!2,CD47bd,c~i)  -> Trash()` | Transforms CD47SIRPa, NRP1, Trash, vegf, vegfr2 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 138 | `Unlabeled` | one-way | CD47SIRPa, NRP1, Trash, vegf, vegfr2 | `kdegr2NRP1i0noP*f_TSP1deg` | state and binding-pattern rewrite | `vegf(r!1,r!2,nrp1bd!9,c~i).NRP1(vegfabd!9,c~i).vegfr2(l1!1,Y1175~Y,CD47bd!3,c~i).CD47SIRPa(TSP1bd!+,VEGFR2bd!3,c~i).vegfr2(l1!2,Y1175~Y,CD47bd,c~i)  -> Trash()` | Transforms CD47SIRPa, NRP1, Trash, vegf, vegfr2 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 139 | `Unlabeled` | one-way | CD47SIRPa, NRP1, Trash, vegf, vegfr2 | `kdegr2NRP1i0*f_TSP1deg` | state and binding-pattern rewrite | `vegf(r!1,r!2,nrp1bd!9,c~i).NRP1(vegfabd!9,c~i).vegfr2(l1!1,Y1175~pY,CD47bd!3,c~i).CD47SIRPa(TSP1bd!+,VEGFR2bd!3,c~i).vegfr2(l1!2,CD47bd!4,c~i).CD47SIRPa(VEGFR2bd!4,c~i)  -> Trash()` | Transforms CD47SIRPa, NRP1, Trash, vegf, vegfr2 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 140 | `Unlabeled` | one-way | CD47SIRPa, NRP1, Trash, vegf, vegfr2 | `kdegr2NRP1i0noP*f_TSP1deg` | state and binding-pattern rewrite | `vegf(r!1,r!2,nrp1bd!9,c~i).NRP1(vegfabd!9,c~i).vegfr2(l1!1,Y1175~Y,CD47bd!3,c~i).CD47SIRPa(TSP1bd!+,VEGFR2bd!3,c~i).vegfr2(l1!2,Y1175~Y,CD47bd!4,c~i).CD47SIRPa(VEGFR2bd!4,c~i)  -> Trash()` | Transforms CD47SIRPa, NRP1, Trash, vegf, vegfr2 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 141 | `Unlabeled` | one-way | CD47SIRPa, NRP1, Trash, vegf, vegfr2 | `kdegr2NRP1i20*f_TSP1deg` | state and binding-pattern rewrite | `vegf(r!1,r!2,nrp1bd!9,c~i2).NRP1(vegfabd!9,c~i2).vegfr2(l1!1,Y1175~pY,CD47bd!3,c~i2).CD47SIRPa(TSP1bd!+,VEGFR2bd!3,c~i2).vegfr2(l1!2,CD47bd,c~i2)  -> Trash()` | Transforms CD47SIRPa, NRP1, Trash, vegf, vegfr2 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 142 | `Unlabeled` | one-way | CD47SIRPa, NRP1, Trash, vegf, vegfr2 | `kdegr2NRP1i20noP*f_TSP1deg` | state and binding-pattern rewrite | `vegf(r!1,r!2,nrp1bd!9,c~i2).NRP1(vegfabd!9,c~i2).vegfr2(l1!1,Y1175~Y,CD47bd!3,c~i2).CD47SIRPa(TSP1bd!+,VEGFR2bd!3,c~i2).vegfr2(l1!2,Y1175~Y,CD47bd,c~i2)  -> Trash()` | Transforms CD47SIRPa, NRP1, Trash, vegf, vegfr2 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 143 | `Unlabeled` | one-way | CD47SIRPa, NRP1, Trash, vegf, vegfr2 | `kdegr2NRP1i20*f_TSP1deg` | state and binding-pattern rewrite | `vegf(r!1,r!2,nrp1bd!9,c~i2).NRP1(vegfabd!9,c~i2).vegfr2(l1!1,Y1175~pY,CD47bd!3,c~i2).CD47SIRPa(TSP1bd!+,VEGFR2bd!3,c~i2).vegfr2(l1!2,CD47bd!4,c~i2).CD47SIRPa(VEGFR2bd!4,c~i2)  -> Trash()` | Transforms CD47SIRPa, NRP1, Trash, vegf, vegfr2 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 144 | `Unlabeled` | one-way | CD47SIRPa, NRP1, Trash, vegf, vegfr2 | `kdegr2NRP1i20noP*f_TSP1deg` | state and binding-pattern rewrite | `vegf(r!1,r!2,nrp1bd!9,c~i2).NRP1(vegfabd!9,c~i2).vegfr2(l1!1,Y1175~Y,CD47bd!3,c~i2).CD47SIRPa(TSP1bd!+,VEGFR2bd!3,c~i2).vegfr2(l1!2,Y1175~Y,CD47bd!4,c~i2).CD47SIRPa(VEGFR2bd!4,c~i2)  -> Trash()` | Transforms CD47SIRPa, NRP1, Trash, vegf, vegfr2 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 145 | `Unlabeled` | one-way | CD47SIRPa, Trash, vegfr2 | `ksingleR2deg` | state and binding-pattern rewrite | `vegfr2(l1,CD47bd!1,c~i).CD47SIRPa(TSP1bd,VEGFR2bd!1,c~i)  -> Trash()` | Transforms CD47SIRPa, Trash, vegfr2 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 146 | `Unlabeled` | one-way | Trash, vegfr2 | `ksingleR2deg` | internal-state conversion/modification | `vegfr2(l1,CD47bd,c~i)  -> Trash()` | Transforms Trash, vegfr2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 147 | `Unlabeled` | one-way | CD47SIRPa, Trash, vegfr2 | `ksingleR2deg*f_TSP1deg` | state and binding-pattern rewrite | `vegfr2(l1,CD47bd!1,c~i).CD47SIRPa(TSP1bd!+,VEGFR2bd!1,c~i)  -> Trash()` | Transforms CD47SIRPa, Trash, vegfr2 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 148 | `Unlabeled` | one-way | I, vegfr2 | `ksingleR2syn*VEGFR2total` | source/synthesis or algebraic source term | `I()  -> I() + vegfr2(l1,Y1175~Y,CD47bd,dimer,c~s)` | Transforms I, vegfr2 by source/synthesis or algebraic source term; see the exact pattern for affected sites/states/bonds. |

| 149 | `Unlabeled` | reversible | vegfr2 | `ksingleR2si, ksingleR2is` | internal-state conversion/modification | `vegfr2(l1,CD47bd,dimer,c~s)  <-> vegfr2(l1,CD47bd,dimer,c~i)` | Transforms vegfr2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 150 | `Unlabeled` | reversible | CD47SIRPa, vegfr2 | `ksingleR2si, ksingleR2is` | internal-state conversion/modification | `vegfr2(l1,CD47bd!1,dimer,c~s).CD47SIRPa(VEGFR2bd!1,c~s)  <-> vegfr2(l1,CD47bd!1,dimer,c~i).CD47SIRPa(VEGFR2bd!1,c~i)` | Transforms CD47SIRPa, vegfr2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 151 | `Unlabeled` | reversible | vegfr2 | `ksingleR2si, ksingleR2is` | internal-state conversion/modification | `vegfr2(l1,CD47bd,dimer!3,c~s).vegfr2(l1,CD47bd,dimer!3,c~s)  <-> vegfr2(l1,CD47bd,dimer!3,c~i).vegfr2(l1,CD47bd,dimer!3,c~i)` | Transforms vegfr2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 152 | `Unlabeled` | reversible | CD47SIRPa, vegfr2 | `ksingleR2si, ksingleR2is` | internal-state conversion/modification | `vegfr2(l1,CD47bd!1,dimer!3,c~s).CD47SIRPa(VEGFR2bd!1,c~s).vegfr2(l1,CD47bd,dimer!3,c~s)  <-> vegfr2(l1,CD47bd!1,dimer!3,c~i).CD47SIRPa(VEGFR2bd!1,c~i).vegfr2(l1,CD47bd,dimer!3,c~i)` | Transforms CD47SIRPa, vegfr2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 153 | `Unlabeled` | reversible | CD47SIRPa, vegfr2 | `ksingleR2si, ksingleR2is` | internal-state conversion/modification | `vegfr2(l1,CD47bd!1,dimer!3,c~s).CD47SIRPa(VEGFR2bd!1,c~s).vegfr2(l1,CD47bd!2,dimer!3,c~s).CD47SIRPa(VEGFR2bd!2,c~s)  <-> vegfr2(l1,CD47bd!1,dimer!3,c~i).CD47SIRPa(VEGFR2bd!1,c~i).vegfr2(l1,CD47bd!2,dimer!3,c~i).CD47SIRPa(VEGFR2bd!2,c~i)` | Transforms CD47SIRPa, vegfr2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 154 | `Unlabeled` | one-way | PLCgamma, vegfr2 | `kpPLCgamma` | internal-state conversion/modification | `PLCgamma(Yplc~Y) + vegfr2(Y1175~pY,c~s)  -> PLCgamma(Yplc~pY) + vegfr2(Y1175~pY,c~s)` | Transforms PLCgamma, vegfr2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 155 | `Unlabeled` | one-way | PLCgamma, vegfr2 | `kpPLCgamma` | internal-state conversion/modification | `PLCgamma(Yplc~Y) + vegfr2(Y1175~pY,c~i)  -> PLCgamma(Yplc~pY) + vegfr2(Y1175~pY,c~i)` | Transforms PLCgamma, vegfr2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 156 | `Unlabeled` | one-way | PLCgamma, vegfr2 | `kpPLCgamma` | internal-state conversion/modification | `PLCgamma(Yplc~Y) + vegfr2(Y1175~pY,c~i2)  -> PLCgamma(Yplc~pY) + vegfr2(Y1175~pY,c~i2)` | Transforms PLCgamma, vegfr2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 157 | `Unlabeled` | one-way | PLCgamma | `kdpPLCgamma` | internal-state conversion/modification | `PLCgamma(Yplc~pY)  -> PLCgamma(Yplc~Y)` | Transforms PLCgamma by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 158 | `Unlabeled` | one-way | IP3_cyto, PI, PLCgamma | `kcatPLCgammaDAG*freepip2^(nDAG-1)/(kmPIP2PLCgamma^nDAG+freepip2^nDAG)` | internal-state conversion/modification | `PLCgamma(Yplc~pY) + PI(PIsite~3P)  -> IP3_cyto(ip3rbd) + PLCgamma(Yplc~pY)` | Transforms IP3_cyto, PI, PLCgamma by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 159 | `Unlabeled` | one-way | DAG, PI, PLCgamma | `kcatPLCgammaDAG*freepip2^(nDAG-1)/(kmPIP2PLCgamma^nDAG+freepip2^nDAG)` | internal-state conversion/modification | `PLCgamma(Yplc~pY) + PI(PIsite~3P)  -> DAG(pkcbd) + PLCgamma(Yplc~pY)` | Transforms DAG, PI, PLCgamma by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 160 | `Unlabeled` | one-way | I, PI | `kPIP2gen` | source/synthesis or algebraic source term | `I()  -> I() + PI(PIsite~3P)` | Transforms I, PI by source/synthesis or algebraic source term; see the exact pattern for affected sites/states/bonds. |

| 161 | `Unlabeled` | one-way | IP3_cyto, Trash | `kdeg_ip3` | pattern rewrite | `IP3_cyto(ip3rbd)  -> Trash()` | Transforms IP3_cyto, Trash by pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 162 | `Unlabeled` | one-way | DAG, Trash | `kdeg_DAG` | pattern rewrite | `DAG(pkcbd)  -> Trash()` | Transforms DAG, Trash by pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 163 | `Unlabeled` | reversible | CaF, Calcium_cyto | `KBon, KBoff` | binding/complex formation | `Calcium_cyto(bd) + CaF(cabd)  <-> Calcium_cyto(bd!1).CaF(cabd!1)` | Transforms CaF, Calcium_cyto by binding/complex formation; see the exact pattern for affected sites/states/bonds. |

| 164 | `Unlabeled` | one-way | I, Istim | `ICracamp*(Kcrac^ncrac/(Kcrac^ncrac+Caer^ncrac))/tau_stim-Iopenstim/tau_stim` | source/synthesis or algebraic source term | `I()  -> I() + Istim()` | Transforms I, Istim by source/synthesis or algebraic source term; see the exact pattern for affected sites/states/bonds. |

| 165 | `Unlabeled` | one-way | Calcium_cyto, I | `(VolER/Volcyto)*Iip3Ramp*(Caer-Cac)*(freeip3cyto^3.8/(freeip3cyto^3.8+KmIP3R^3.8))*(KiCa^3.8/(KiCa^3.8+Cac^3.8))` | source/synthesis or algebraic source term | `I()  -> I() + Calcium_cyto(bd)` | Transforms Calcium_cyto, I by source/synthesis or algebraic source term; see the exact pattern for affected sites/states/bonds. |

| 166 | `Unlabeled` | one-way | CaER, I | `)` | source/synthesis or algebraic source term | `I()  -> I() + CaER(bd) -Iip3Ramp*(Caer-Cac)*(freeip3cyto^3.8/(freeip3cyto^3.8+KmIP3R^3.8))*(KiCa^3.8/(KiCa^3.8+Cac^3.8))*( 1/(1+CSQN_total/(KCSQN+Caer)^2)` | Transforms CaER, I by source/synthesis or algebraic source term; see the exact pattern for affected sites/states/bonds. |

| 167 | `Unlabeled` | one-way | Calcium_cyto, I | `Iopenstim` | source/synthesis or algebraic source term | `I()  -> I() + Calcium_cyto(bd) -I_PMCAbar*Cac^1.4/(KmPMCA^1.4+Cac^1.4) +` | PMCA pump |

| 168 | `Unlabeled` | one-way | Calcium_cyto, I | `KleakER*(Caer-Cac)^2` | source/synthesis or algebraic source term | `I()  -> I() + Calcium_cyto(bd) -vSERCA*(Cac/(KmSERCA+Cac))^2 +` | SERCA pump |

| 169 | `Unlabeled` | one-way | CaER, I | `vSERCA*(Cac/(KmSERCA+Cac))^2*(Volcyto/VolER)*(1/(1+CSQN_total/(KCSQN+Caer)^2))` | source/synthesis or algebraic source term | `I()  -> I() + CaER(bd)` | SERCA pump |

| 170 | `Unlabeled` | one-way | CaER, I | `-KleakER*(Volcyto/VolER)*((Caer-Cac)^2)*(1/(1+CSQN_total/(KCSQN+Caer)^2))` | source/synthesis or algebraic source term | `I()  -> I() + CaER(bd)` | Transforms CaER, I by source/synthesis or algebraic source term; see the exact pattern for affected sites/states/bonds. |

| 171 | `Unlabeled` | one-way | CaM, Calcium_cyto | `(koffCaNCaM1/kdCaNCaM)` | binding/complex formation | `CaM(NCaM) + Calcium_cyto(bd)  -> CaM(NCaM!1).Calcium_cyto(bd!1) + Calcium_cyto(bd)` | Transforms CaM, Calcium_cyto by binding/complex formation; see the exact pattern for affected sites/states/bonds. |

| 172 | `Unlabeled` | one-way | CaM, Calcium_cyto | `koffCaNCaM1` | unbinding/complex dissociation | `CaM(NCaM!1).Calcium_cyto(bd!1)  -> CaM(NCaM)` | Transforms CaM, Calcium_cyto by unbinding/complex dissociation; see the exact pattern for affected sites/states/bonds. |

| 173 | `Unlabeled` | one-way | CaM, Calcium_cyto | `(koffCaCCaM1/kdCaCCaM)` | binding/complex formation | `CaM(CCaM) + Calcium_cyto(bd)  -> CaM(CCaM!1).Calcium_cyto(bd!1) + Calcium_cyto(bd)` | Transforms CaM, Calcium_cyto by binding/complex formation; see the exact pattern for affected sites/states/bonds. |

| 174 | `Unlabeled` | one-way | CaM, Calcium_cyto | `koffCaCCaM1` | unbinding/complex dissociation | `CaM(CCaM!1).Calcium_cyto(bd!1)  -> CaM(CCaM)` | Transforms CaM, Calcium_cyto by unbinding/complex dissociation; see the exact pattern for affected sites/states/bonds. |

| 175 | `Unlabeled` | one-way | TSADSrc, vegfr2 | `kpSrc` | internal-state conversion/modification | `TSADSrc(Y1~Y) + vegfr2(Y1175~pY!?,c~s)  -> TSADSrc(Y1~pY) + vegfr2(Y1175~pY!?,c~s)` | Autophosphorylation of Src |

| 176 | `Unlabeled` | one-way | TSADSrc, vegfr2 | `kpSrc` | internal-state conversion/modification | `TSADSrc(Y1~Y) + vegfr2(Y1175~pY!?,c~i)  -> TSADSrc(Y1~pY) + vegfr2(Y1175~pY!?,c~i)` | Autophosphorylation of Src |

| 177 | `Unlabeled` | one-way | TSADSrc, vegfr2 | `kpSrc` | internal-state conversion/modification | `TSADSrc(Y1~Y) + vegfr2(Y1175~pY!?,c~i2)  -> TSADSrc(Y1~pY) + vegfr2(Y1175~pY!?,c~i2)` | Autophosphorylation of Src |

| 178 | `Unlabeled` | one-way | TSADSrc | `kdpSrc` | internal-state conversion/modification | `TSADSrc(Y1~pY)  -> TSADSrc(Y1~Y)` | Transforms TSADSrc by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 179 | `Unlabeled` | one-way | Axl, TSADSrc | `kpSrcAxl` | internal-state conversion/modification | `TSADSrc(Y1~pY) + Axl(Ysrc~Y)  -> TSADSrc(Y1~pY) + Axl(Ysrc~pY)` | Transforms Axl, TSADSrc by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 180 | `Unlabeled` | one-way | Axl | `kpAxlauto` | internal-state conversion/modification | `Axl(Ysrc~pY,Yaxl~Y)  -> Axl(Ysrc~pY,Yaxl~pY)` | Transforms Axl by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 181 | `Unlabeled` | one-way | Axl | `kdpautoAxl` | internal-state conversion/modification | `Axl(Yaxl~pY)  -> Axl(Yaxl~Y)` | Transforms Axl by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 182 | `Unlabeled` | one-way | Axl | `kdpSrcAxl` | internal-state conversion/modification | `Axl(Ysrc~pY)  -> Axl(Ysrc~Y)` | Transforms Axl by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 183 | `Unlabeled` | one-way | Axl, PI3K | `konPI3KAxl` | internal-state conversion/modification | `PI3K(state~inactive) + Axl(Yaxl~pY)  -> PI3K(state~active) + Axl(Yaxl~pY)` | Transforms Axl, PI3K by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 184 | `Unlabeled` | one-way | PI3K | `koffPI3KAxl` | internal-state conversion/modification | `PI3K(state~active)  -> PI3K(state~inactive)` | Transforms PI3K by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 185 | `Unlabeled` | one-way | PI, PI3K | `kcatPI3KPIP2/(kmPIP2PI3K+freepip2)` | internal-state conversion/modification | `PI3K(state~active) + PI(PIsite~3P)  -> PI3K(state~active) + PI(PIsite~4P)` | Transforms PI, PI3K by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 186 | `Unlabeled` | one-way | PI, PTEN | `kcatPTENPIP3/(kmPIP3PTEN+freepip3)` | internal-state conversion/modification | `PTEN(PIP3docking) + PI(PIsite~4P)  -> PTEN(PIP3docking) + PI(PIsite~3P)` | Transforms PI, PTEN by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 187 | `Unlabeled` | reversible | PDK1, PI | `konPDK1PIP3, koffPDK1PIP3` | state and binding-pattern rewrite | `PDK1(PHpdk1) + PI(PIsite~4P)  <-> PDK1(PHpdk1!1).PI(PIsite~4P!1)` | Transforms PDK1, PI by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 188 | `Unlabeled` | reversible | AKT, PI | `konAKTPIP3, koffAKTPIP3` | state and binding-pattern rewrite | `AKT(PHakt) + PI(PIsite~4P)  <-> AKT(PHakt!1).PI(PIsite~4P!1)` | Transforms AKT, PI by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 189 | `Unlabeled` | one-way | AKT | `kpmTORAKT` | internal-state conversion/modification | `AKT(PHakt!+,S473~S)  -> AKT(PHakt!+,S473~pS)` | Transforms AKT by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 190 | `Unlabeled` | one-way | AKT, PDK1 | `kpAKTPDK1` | internal-state conversion/modification | `AKT(PHakt!+,S473~pS,T308~S) + PDK1(PHpdk1!+)  -> PDK1(PHpdk1!+) + AKT(PHakt!+,S473~pS,T308~pS)` | Transforms AKT, PDK1 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 191 | `Unlabeled` | one-way | AKT | `kdp473AKTPPase` | internal-state conversion/modification | `AKT(S473~pS)  -> AKT(S473~S)` | Transforms AKT by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 192 | `Unlabeled` | one-way | AKT | `kdp308AKTPPase` | internal-state conversion/modification | `AKT(T308~pS)  -> AKT(T308~S)` | Transforms AKT by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 193 | `Unlabeled` | reversible | CaM, eNOS | `konCaMeNOS, koffCaMeNOS` | stoichiometric pattern rewrite | `CaM(NCaM!+,NCaM!+,CCaM!+,CCaM!+,CaMtargetbd) + eNOS(CaMBD)  <-> CaM(NCaM!+,NCaM!+,CCaM!+,CCaM!+,CaMtargetbd!1).eNOS(CaMBD!1)` | Transforms CaM, eNOS by stoichiometric pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 194 | `Unlabeled` | one-way | caveolin1, eNOS | `koffeNOScav1` | stoichiometric pattern rewrite | `eNOS(CaMBD!+,cav1BD!1).caveolin1(eNOSbd!1)  -> eNOS(CaMBD!+,cav1BD) + caveolin1(eNOSbd)` | Transforms caveolin1, eNOS by stoichiometric pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 195 | `Unlabeled` | one-way | caveolin1, eNOS | `koffeNOScav1` | state and binding-pattern rewrite | `eNOS(cav1BD!1,S1177~pS).caveolin1(eNOSbd!1)  -> eNOS(cav1BD,S1177~pS) + caveolin1(eNOSbd)` | Transforms caveolin1, eNOS by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 196 | `Unlabeled` | one-way | caveolin1, eNOS | `koncaveNOS` | state and binding-pattern rewrite | `eNOS(CaMBD,cav1BD,S1177~S) + caveolin1(eNOSbd)  -> eNOS(CaMBD,cav1BD!1,S1177~S).caveolin1(eNOSbd!1)` | Transforms caveolin1, eNOS by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 197 | `Unlabeled` | one-way | AKT, eNOS | `kcateNOSAKT` | internal-state conversion/modification | `eNOS(CaMBD!+,S1177~S) + AKT(T308~pS,S473~pS)  -> eNOS(CaMBD!+,S1177~pS) + AKT(T308~pS,S473~pS)` | Transforms AKT, eNOS by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 198 | `Unlabeled` | one-way | eNOS | `kdpeNOS` | internal-state conversion/modification | `eNOS(S1177~pS)  -> eNOS(S1177~S)` | Transforms eNOS by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 199 | `Unlabeled` | one-way | I, TSP1 | `-(koffCD47TSP1/kDCD47TSP1)/fextmolar*tsp1frees*cellarea*cd47s+koffCD47TSP1*cd47tsp1s*cellarea*(1/fextmolar)` | source/synthesis or algebraic source term | `I()  -> I() + TSP1(CD47bd)` | Transforms I, TSP1 by source/synthesis or algebraic source term; see the exact pattern for affected sites/states/bonds. |

| 200 | `Unlabeled` | one-way | CD47SIRPa, TSP1 | `(koffCD47TSP1/kDCD47TSP1)` | state and binding-pattern rewrite | `TSP1(CD47bd) + CD47SIRPa(TSP1bd,c~s)  -> TSP1(CD47bd) + TSP1(CD47bd!1).CD47SIRPa(TSP1bd!1,c~s)` | Transforms CD47SIRPa, TSP1 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 201 | `Unlabeled` | one-way | CD47SIRPa, TSP1 | `koffCD47TSP1` | state and binding-pattern rewrite | `TSP1(CD47bd!1).CD47SIRPa(TSP1bd!1,c~s)  -> CD47SIRPa(TSP1bd,c~s)` | Transforms CD47SIRPa, TSP1 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 202 | `Unlabeled` | one-way | CD47SIRPa, vegfr2 | `kcd47free_on` | state and binding-pattern rewrite | `vegfr2(CD47bd,c~s) + CD47SIRPa(VEGFR2bd,c~s)  -> vegfr2(CD47bd!1,c~s).CD47SIRPa(VEGFR2bd!1,c~s)` | Transforms CD47SIRPa, vegfr2 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 203 | `Unlabeled` | reversible | Calcium_cyto, PKC | `konCaPKC, koffCaPKC` | binding/complex formation | `PKC(CalciumBD) + Calcium_cyto(bd)  <-> PKC(CalciumBD!1).Calcium_cyto(bd!1)` | Transforms Calcium_cyto, PKC by binding/complex formation; see the exact pattern for affected sites/states/bonds. |

| 204 | `Unlabeled` | reversible | DAG, PKC | `konDAGPKC, koffDAGPKC` | binding/complex formation | `PKC(DAGBD) + DAG(pkcbd)  <-> PKC(DAGBD!1).DAG(pkcbd!1)` | Transforms DAG, PKC by binding/complex formation; see the exact pattern for affected sites/states/bonds. |

| 205 | `Unlabeled` | reversible | CIB1, Calcium_cyto | `kon1CaCIB1, koff1CaCIB1` | binding/complex formation | `CIB1(EF1) + Calcium_cyto(bd)  <-> CIB1(EF1!1).Calcium_cyto(bd!1)` | Transforms CIB1, Calcium_cyto by binding/complex formation; see the exact pattern for affected sites/states/bonds. |

| 206 | `Unlabeled` | reversible | CIB1, Calcium_cyto | `kon2CaCIB1, koff2CaCIB1` | binding/complex formation | `CIB1(EF2) + Calcium_cyto(bd)  <-> CIB1(EF2!1).Calcium_cyto(bd!1)` | Transforms CIB1, Calcium_cyto by binding/complex formation; see the exact pattern for affected sites/states/bonds. |

| 207 | `Unlabeled` | reversible | CIB1, SphK | `konCIB1SphK1, koffCIB1SphK1` | internal-state conversion/modification | `CIB1(EF1!+,EF2!+,sk1bd,location~cytosol) + SphK(CIB1bd,Serk~pS)  <-> CIB1(EF1!+,EF2!+,sk1bd!1,location~cytosol).SphK(CIB1bd!1,Serk~pS)` | Transforms CIB1, SphK by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 208 | `Unlabeled` | one-way | ERK2, SphK | `kcatERK/(freeSphK1+kmERKSK1)` | internal-state conversion/modification | `ERK2(S2~pS) + SphK(Serk~S)  -> ERK2(S2~pS) + SphK(Serk~pS)` | Transforms ERK2, SphK by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 209 | `Unlabeled` | reversible | CIB1 | `ktSK1, ktoffSK1` | internal-state conversion/modification | `CIB1(EF1!+,EF2!+,sk1bd!+,location~cytosol)  <-> CIB1(EF1!+,EF2!+,sk1bd!+,location~membrane)` | Transforms CIB1 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 210 | `Unlabeled` | one-way | CIB1 | `koffSK1` | internal-state conversion/modification | `CIB1(EF1,EF2,location~membrane)  -> CIB1(EF1,EF2,location~cytosol)` | Transforms CIB1 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 211 | `Unlabeled` | one-way | DAG, PKC, Raf | `kcatPKC/(freeraf+kmPKCRaf)` | internal-state conversion/modification | `PKC(CalciumBD!+,DAGBD!1).DAG(pkcbd!1) + Raf(Spkc~S)  -> PKC(CalciumBD!+,DAGBD!1).DAG(pkcbd!1) + Raf(Spkc~pS)` | Transforms DAG, PKC, Raf by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 212 | `Unlabeled` | one-way | SphK | `kdpSK1` | internal-state conversion/modification | `SphK(Serk~pS)  -> SphK(Serk~S)` | Transforms SphK by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 213 | `Unlabeled` | one-way | Raf | `kdpPKCRaf` | internal-state conversion/modification | `Raf(Spkc~pS)  -> Raf(Spkc~S)` | Transforms Raf by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 214 | `Unlabeled` | one-way | I, Sph | `kSphgen` | source/synthesis or algebraic source term | `I()  -> I() + Sph(skbd)` | Transforms I, Sph by source/synthesis or algebraic source term; see the exact pattern for affected sites/states/bonds. |

| 215 | `Unlabeled` | one-way | CIB1, S1P, Sph, SphK | `kcatSK1Sph/(KmSK1Sph+freesphingosin)` | internal-state conversion/modification | `CIB1(sk1bd!1,location~membrane).SphK(CIB1bd!1,Serk~pS) +  Sph(skbd)  -> S1P(bd) + CIB1(sk1bd!1,location~membrane).SphK(CIB1bd!1,Serk~pS)` | Transforms CIB1, S1P, Sph, SphK by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 216 | `Unlabeled` | one-way | S1P, Sph | `kdpS1P` | pattern rewrite | `S1P(bd)  -> Sph(skbd)` | Transforms S1P, Sph by pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 217 | `Unlabeled` | one-way | I, RasGTP | `kS1PRas*frees1p/(KmS1PRas+frees1p)-kRasGAP*gtpfreeras` | source/synthesis or algebraic source term | `I()  -> I() + RasGTP(rafbd)` | Transforms I, RasGTP by source/synthesis or algebraic source term; see the exact pattern for affected sites/states/bonds. |

| 218 | `Unlabeled` | reversible | Raf, RasGTP | `konRasRaf, koffRasRaf` | binding/complex formation | `Raf(rasbd) + RasGTP(rafbd)  <-> Raf(rasbd!1).RasGTP(rafbd!1)` | Transforms Raf, RasGTP by binding/complex formation; see the exact pattern for affected sites/states/bonds. |

| 219 | `Unlabeled` | one-way | Raf, RasGTP | `kpRaf` | internal-state conversion/modification | `Raf(rasbd!1,Y1Y2~Y).RasGTP(rafbd!1)  -> Raf(rasbd!1,Y1Y2~pY).RasGTP(rafbd!1)` | Activation of Raf by Tyrosine phosphorylation |

| 220 | `Unlabeled` | one-way | Raf | `kdpRaf` | internal-state conversion/modification | `Raf(Y1Y2~pY)  -> Raf(Y1Y2~Y)` | Transforms Raf by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 221 | `Unlabeled` | one-way | MEK12, Raf | `kpMEK12Raf1/(KmMEK12Raf+mek12s1)` | internal-state conversion/modification | `MEK12(S1~S) + Raf(Y1Y2~pY,Spkc~S)  -> Raf(Y1Y2~pY,Spkc~S) + MEK12(S1~pS)` | Transforms MEK12, Raf by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 222 | `Unlabeled` | one-way | MEK12, Raf | `kpMEK12Raf2/(KmMEK12Raf+mek12s2)` | internal-state conversion/modification | `MEK12(S2~S) + Raf(Y1Y2~pY,Spkc~S)  -> Raf(Y1Y2~pY,Spkc~S) + MEK12(S2~pS)` | Transforms MEK12, Raf by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 223 | `Unlabeled` | one-way | MEK12, Raf | `kpMEK12Raf1/(KmMEK12Raf+mek12s2)` | internal-state conversion/modification | `MEK12(S1~S) + Raf(Y1Y2~pY,Spkc~pS)  -> Raf(Y1Y2~pY,Spkc~pS) + MEK12(S1~pS)` | Transforms MEK12, Raf by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 224 | `Unlabeled` | one-way | MEK12, Raf | `kpMEK12Raf2/(KmMEK12Raf+mek12s2)` | internal-state conversion/modification | `MEK12(S2~S) + Raf(Y1Y2~pY,Spkc~pS)  -> Raf(Y1Y2~pY,Spkc~pS) + MEK12(S2~pS)` | Transforms MEK12, Raf by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 225 | `Unlabeled` | one-way | MEK12, Raf | `kpMEK12Raf1/(KmMEK12Raf+mek12s1)` | internal-state conversion/modification | `MEK12(S1~S) + Raf(Y1Y2~Y,Spkc~pS)  -> Raf(Y1Y2~Y,Spkc~pS) + MEK12(S1~pS)` | Transforms MEK12, Raf by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 226 | `Unlabeled` | one-way | MEK12, Raf | `kpMEK12Raf2/(KmMEK12Raf+mek12s2)` | internal-state conversion/modification | `MEK12(S2~S) + Raf(Y1Y2~Y,Spkc~pS)  -> Raf(Y1Y2~Y,Spkc~pS) + MEK12(S2~pS)` | Transforms MEK12, Raf by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 227 | `Unlabeled` | one-way | MEK12 | `kdpMEK12_1` | internal-state conversion/modification | `MEK12(S1~pS)  -> MEK12(S1~S)` | Transforms MEK12 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 228 | `Unlabeled` | one-way | MEK12 | `kdpMEK12_2` | internal-state conversion/modification | `MEK12(S2~pS)  -> MEK12(S2~S)` | Transforms MEK12 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 229 | `Unlabeled` | one-way | ERK1, MEK12 | `(kpMEK12ERK12_1/(kmMEKERK12+erk12s1))` | internal-state conversion/modification | `MEK12(S1~pS,S2~pS) + ERK1(S1~S)  -> MEK12(S1~pS,S2~pS) + ERK1(S1~pS)` | Transforms ERK1, MEK12 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 230 | `Unlabeled` | one-way | ERK2, MEK12 | `(kpMEK12ERK12_2/(kmMEKERK12+erk12s2))` | internal-state conversion/modification | `MEK12(S1~pS,S2~pS) + ERK2(S2~S)  -> MEK12(S1~pS,S2~pS) + ERK2(S2~pS)` | Transforms ERK2, MEK12 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 231 | `Unlabeled` | one-way | ERK1 | `kdpERK12_1` | internal-state conversion/modification | `ERK1(S1~pS)  -> ERK1(S1~S)` | Transforms ERK1 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 232 | `Unlabeled` | one-way | ERK2 | `kdpERK12_2` | internal-state conversion/modification | `ERK2(S2~pS)  -> ERK2(S2~S)` | Transforms ERK2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

## 7. Observables and technical readouts

| Observable | Type | Pattern / target | Technical interpretation |
| --- | --- | --- | --- |
| `vegffrees` | `Molecules` | `vegf(r,r,nrp1bd,c~s)` | Reports free/unbound species matching the pattern. |
| `VEGFR2total` | `Molecules` | `vegfr2()` | Reports total pool matching the pattern. |
| `tsp1frees` | `Molecules` | `TSP1(CD47bd)` | Reports free/unbound species matching the pattern. |
| `cd47tsp1s` | `Molecules` | `TSP1(CD47bd!1).CD47SIRPa(TSP1bd!1,Y1~Y,c~s)` | Reports bound or complexed species matching the pattern. |
| `cd47s` | `Molecules` | `CD47SIRPa(TSP1bd,Y1~Y,c~s)` | Reports the BNGL pattern for downstream plotting or rate expressions. |
| `VEGFR2tots` | `Molecules` | `vegfr2(c~s)` | Reports total pool matching the pattern. |
| `VEGFR2toti` | `Molecules` | `vegfr2(c~i)` | Reports total pool matching the pattern. |
| `vr2s` | `Molecules` | `vegfr2(l1,c~s)` | Reports the BNGL pattern for downstream plotting or rate expressions. |
| `vr2i` | `Molecules` | `vegfr2(l1,c~i)` | Reports the BNGL pattern for downstream plotting or rate expressions. |
| `vr1s` | `Molecules` | `vegfr1(l2,nrp1bd,c~s)` | Reports the BNGL pattern for downstream plotting or rate expressions. |
| `vegfr2Y1175ps` | `Molecules` | `vegfr2(Y1175~pY!?,c~s)` | Reports phosphorylated or modified species matching the pattern. |
| `vegfr2Y1175pi` | `Molecules` | `vegfr2(Y1175~pY!?,c~i)` | Reports phosphorylated or modified species matching the pattern. |
| `pr2Y1175total` | `Molecules` | `vegfr2(Y1175~pY!?)` | Reports phosphorylated or modified species matching the pattern. |
| `vegfr1tots` | `Molecules` | `vegfr1(c~s)` | Reports total pool matching the pattern. |
| `NRP1VEGFR2s` | `Molecules` | `vegf(r!1,r!2,nrp1bd!+,c~s).vegfr2(l1!1,c~s).vegfr2(l1!2,c~s)` | Reports bound or complexed species matching the pattern. |
| `NRP1VEGFR2i` | `Molecules` | `vegf(r!1,r!2,nrp1bd!+,c~i).vegfr2(l1!1,c~i).vegfr2(l1!2,c~i)` | Reports bound or complexed species matching the pattern. |
| `freeDAGs` | `Molecules` | `DAG(pkcbd!?)` | Reports free/unbound species matching the pattern. |
| `activePLCgamma` | `Molecules` | `PLCgamma(Yplc~pY!?)` | Reports phosphorylated or modified species matching the pattern. |
| `PIP2` | `Molecules` | `PI(PIsite~3P)` | Reports the BNGL pattern for downstream plotting or rate expressions. |
| `PIP3` | `Molecules` | `PI(PIsite~4P)` | Reports the BNGL pattern for downstream plotting or rate expressions. |
| `freeip3cyto` | `Molecules` | `IP3_cyto(ip3rbd)` | Reports free/unbound species matching the pattern. |
| `Cac` | `Molecules` | `Calcium_cyto(bd)` | Reports the BNGL pattern for downstream plotting or rate expressions. |
| `Caer` | `Molecules` | `CaER(bd)` | Reports the BNGL pattern for downstream plotting or rate expressions. |
| `CaBuf_fer` | `Molecules` | `CaF(cabd!+)` | Reports bound or complexed species matching the pattern. |
| `activePKCs` | `Molecules` | `PKC(CalciumBD!+,DAGBD!1).DAG(pkcbd!1)` | Reports bound or complexed species matching the pattern. |
| `activePKCtot` | `Molecules` | `PKC(CalciumBD!+,DAGBD!+)` | Reports total pool matching the pattern. |
| `SphKpkc` | `Molecules` | `SphK(Serk~pS!?)` | Reports phosphorylated or modified species matching the pattern. |
| `S1phosphate` | `Molecules` | `S1P(bd)` | Reports phosphorylated or modified species matching the pattern. |
| `NRP1frees` | `Molecules` | `NRP1(vegfabd,c~s)` | Reports free/unbound species matching the pattern. |
| `NRP1freei` | `Molecules` | `NRP1(vegfabd,c~i)` | Reports free/unbound species matching the pattern. |
| `NRP1bounds` | `Molecules` | `NRP1(vegfabd!+,c~s)` | Reports bound or complexed species matching the pattern. |
| `NRP1boundi` | `Molecules` | `NRP1(vegfabd!+,c~i)` | Reports bound or complexed species matching the pattern. |
| `vr2dimers` | `Molecules` | `vegfr2(l1,dimer!1,c~s).vegfr2(l1,dimer!1,c~s)` | Reports bound or complexed species matching the pattern. |
| `vr2dimeri` | `Molecules` | `vegfr2(l1,dimer!1,c~i).vegfr2(l1,dimer!1,c~i)` | Reports bound or complexed species matching the pattern. |
| `NRP1totals` | `Molecules` | `NRP1(c~s)` | Reports total pool matching the pattern. |
| `NRP1totali` | `Molecules` | `NRP1(c~i)` | Reports total pool matching the pattern. |
| `singleNRP1totals` | `Molecules` | `NRP1(vegfabd,c~s)` | Reports total pool matching the pattern. |
| `singleNRP1totali` | `Molecules` | `NRP1(vegfabd,c~i)` | Reports total pool matching the pattern. |
| `vegfr2total` | `Molecules` | `vegf(r!1).vegfr2(l1!1)` | Reports total pool matching the pattern. |
| `vr2Y1175s` | `Molecules` | `vegfr2(Y1175~pY,c~s)` | Reports phosphorylated or modified species matching the pattern. |
| `vr2Y1175i` | `Molecules` | `vegfr2(Y1175~pY,c~i)` | Reports phosphorylated or modified species matching the pattern. |
| `plcgammafree` | `Molecules` | `PLCgamma(Yplc~Y)` | Reports free/unbound species matching the pattern. |
| `rasgdpfree` | `Molecules` | `RasGDP(rafbd!?)` | Reports free/unbound species matching the pattern. |
| `rasgtpfree` | `Molecules` | `RasGTP(rafbd!?)` | Reports free/unbound species matching the pattern. |
| `activeRafbyrastot` | `Molecules` | `Raf(Y1Y2~pY!?)` | Reports phosphorylated or modified species matching the pattern. |
| `phosphoMEK12tot` | `Molecules` | `MEK12(S1~pS!?,S2~pS!?)` | Reports phosphorylated or modified species matching the pattern. |
| `phosphoERK1tot` | `Molecules` | `ERK1(S1~pS!?)` | Reports phosphorylated or modified species matching the pattern. |
| `phosphoERK2tot` | `Molecules` | `ERK2(S2~pS!?)` | Reports phosphorylated or modified species matching the pattern. |
| `SphK1` | `Molecules` | `SphK(CIB1bd!+,Serk~S).CIB1(sk1bd!1,location~membrane)` | Reports bound or complexed species matching the pattern. |
| `SphK1mempS` | `Molecules` | `SphK(CIB1bd!+,Serk~pS).CIB1(sk1bd!1,location~membrane)` | Reports phosphorylated or modified species matching the pattern. |
| `SphK1cytosol` | `Molecules` | `SphK(CIB1bd!+,Serk~S).CIB1(sk1bd!1,location~cytosol)` | Reports bound or complexed species matching the pattern. |
| `activeSphK1` | `Molecules` | `SphK(Serk~pS!?)` | Reports phosphorylated or modified species matching the pattern. |
| `freeSK1` | `Molecules` | `SphK(CIB1bd,Serk~S)` | Reports free/unbound species matching the pattern. |
| `freeSK1mem` | `Molecules` | `SphK(CIB1bd!1,Serk~S).CIB1(sk1bd!1,location~membrane)` | Reports free/unbound species matching the pattern. |
| `freecib1` | `Molecules` | `CIB1(EF1,EF2,sk1bd)` | Reports free/unbound species matching the pattern. |
| `calciumcib1` | `Molecules` | `CIB1(EF1!+,EF2!+,sk1bd)` | Reports bound or complexed species matching the pattern. |
| `sk1bcib1` | `Molecules` | `CIB1(EF1!+,EF2!+,sk1bd!+)` | Reports bound or complexed species matching the pattern. |
| `nrp1s` | `Molecules` | `NRP1(vegfabd,c~s)` | Reports the BNGL pattern for downstream plotting or rate expressions. |
| `vegfnrp1s` | `Molecules` | `vegf(r,r,nrp1bd!1,c~s).NRP1(vegfabd!1,c~s)` | Reports bound or complexed species matching the pattern. |
| `vegfr1s` | `Molecules` | `vegf(r!1,r,nrp1bd,c~s).vegfr1(l2!1,c~s)` | Reports bound or complexed species matching the pattern. |
| `vegfr2s` | `Molecules` | `vegf(r!1,r,nrp1bd,c~s).vegfr2(l1!1,dimer,c~s)` | Reports bound or complexed species matching the pattern. |
| `freepip2` | `Molecules` | `PI(PIsite~3P)` | Reports free/unbound species matching the pattern. |
| `freesphingosin` | `Molecules` | `Sph(skbd)` | Reports free/unbound species matching the pattern. |
| `freeraf` | `Molecules` | `Raf(Spkc~S)` | Reports free/unbound species matching the pattern. |
| `activeRafPKC` | `Molecules` | `Raf(Spkc~pS!?)` | Reports phosphorylated or modified species matching the pattern. |
| `activeRafPKCERK1` | `Molecules` | `Raf(Spkc~pS!?,Y1Y2~pY!?)` | Reports phosphorylated or modified species matching the pattern. |
| `activeRafPKCERK2` | `Molecules` | `Raf(Spkc~pS!?,Y1Y2~Y!?)` | Reports phosphorylated or modified species matching the pattern. |
| `activeRafPKCERK3` | `Molecules` | `Raf(Spkc~S!?,Y1Y2~pY!?)` | Reports phosphorylated or modified species matching the pattern. |
| `rafY1Y2pY` | `Molecules` | `Raf(Y1Y2~pY,Spkc~S)` | Reports phosphorylated or modified species matching the pattern. |
| `rafY1Y2pYpS` | `Molecules` | `Raf(Y1Y2~pY,Spkc~pS)` | Reports phosphorylated or modified species matching the pattern. |
| `rafpS` | `Molecules` | `Raf(Y1Y2~Y,Spkc~pS)` | Reports phosphorylated or modified species matching the pattern. |
| `erk1s` | `Molecules` | `ERK1(S1~S)` | Reports the BNGL pattern for downstream plotting or rate expressions. |
| `mek12s` | `Molecules` | `MEK12(S1~S,S2~S)` | Reports the BNGL pattern for downstream plotting or rate expressions. |
| `R2singlei` | `Molecules` | `vegfr2(l1,Y1175~Y,dimer,c~i)` | Reports the BNGL pattern for downstream plotting or rate expressions. |
| `pERK1s` | `Molecules` | `ERK1(S1~pS)` | Reports phosphorylated or modified species matching the pattern. |
| `mek12ps` | `Molecules` | `MEK12(S1~pS,S2~S)` | Reports phosphorylated or modified species matching the pattern. |
| `pERK2s` | `Molecules` | `ERK2(S2~pS)` | Reports phosphorylated or modified species matching the pattern. |
| `mek12ps1` | `Molecules` | `MEK12(S1~pS)` | Reports phosphorylated or modified species matching the pattern. |
| `mek12ps2` | `Molecules` | `MEK12(S2~pS)` | Reports phosphorylated or modified species matching the pattern. |
| `erk1ps` | `Molecules` | `ERK1(S1~pS)` | Reports phosphorylated or modified species matching the pattern. |
| `erk2ps` | `Molecules` | `ERK2(S2~pS)` | Reports phosphorylated or modified species matching the pattern. |
| `vr2r2py1175s` | `Molecules` | `vegfr2(Y1175~pY,c~s)` | Reports phosphorylated or modified species matching the pattern. |
| `vr2r2py1175i` | `Molecules` | `vegfr2(Y1175~pY,c~i)` | Reports phosphorylated or modified species matching the pattern. |
| `vr2py1175s` | `Species` | `vegf(r!1,r,c~s).vegfr2(l1!1,Y1175~pY,c~s)` | Reports phosphorylated or modified species matching the pattern. |
| `vr2py1175i` | `Species` | `vegf(r!1,r,c~i).vegfr2(l1!1,Y1175~pY,c~i)` | Reports phosphorylated or modified species matching the pattern. |
| `r2singlepy1175s` | `Molecules` | `vegfr2(l1,Y1175~pY,c~s)` | Reports phosphorylated or modified species matching the pattern. |
| `r2singlepy1175i` | `Molecules` | `vegfr2(l1,Y1175~pY,c~i)` | Reports phosphorylated or modified species matching the pattern. |
| `vr1r2pY1165s` | `Molecules` | `vegf(r!1,r!2,c~s).vegfr1(l2!1,c~s).vegfr2(l1!2,Y1175~pY,c~s)` | Reports phosphorylated or modified species matching the pattern. |
| `pSK1` | `Molecules` | `SphK(Serk~pS)` | Reports phosphorylated or modified species matching the pattern. |
| `frees1p` | `Molecules` | `S1P(bd)` | Reports free/unbound species matching the pattern. |
| `py1y2rafs` | `Molecules` | `Raf(Y1Y2~pY)` | Reports phosphorylated or modified species matching the pattern. |
| `vegfnrp1i` | `Molecules` | `vegf(r,r,nrp1bd!1,c~i).NRP1(vegfabd!1,c~i)` | Reports bound or complexed species matching the pattern. |
| `vegfr2i` | `Species` | `vegf(r!1,r,nrp1bd,c~i).vegfr2(l1!1,c~i)` | Reports bound or complexed species matching the pattern. |
| `totalnrp1` | `Molecules` | `NRP1(vegfabd)` | Reports total pool matching the pattern. |
| `pplcgamma` | `Molecules` | `PLCgamma(Yplc~pY)` | Reports phosphorylated or modified species matching the pattern. |
| `phosphoERKpS1` | `Molecules` | `ERK1(S1~pS!?)` | Reports phosphorylated or modified species matching the pattern. |
| `phosphoERKpS2` | `Molecules` | `ERK2(S2~pS!?)` | Reports phosphorylated or modified species matching the pattern. |
| `phosphoMEKpS1` | `Molecules` | `MEK12(S1~pS!?,S2~S)` | Reports phosphorylated or modified species matching the pattern. |
| `phosphoMEKpS2` | `Molecules` | `MEK12(S1~S,S2~pS!?)` | Reports phosphorylated or modified species matching the pattern. |
| `freeSphK1` | `Molecules` | `SphK(CIB1bd,Serk~S)` | Reports free/unbound species matching the pattern. |
| `rafpkc` | `Molecules` | `Raf(Spkc~pS)` | Reports phosphorylated or modified species matching the pattern. |
| `mek12s1` | `Molecules` | `MEK12(S1~S)` | Reports the BNGL pattern for downstream plotting or rate expressions. |
| `mek12s2` | `Molecules` | `MEK12(S2~S)` | Reports the BNGL pattern for downstream plotting or rate expressions. |
| `erk12s1` | `Molecules` | `ERK1(S1~S)` | Reports the BNGL pattern for downstream plotting or rate expressions. |
| `erk12s2` | `Molecules` | `ERK2(S2~S)` | Reports the BNGL pattern for downstream plotting or rate expressions. |
| `yplcgamma` | `Molecules` | `PLCgamma(Yplc~Y)` | Reports the BNGL pattern for downstream plotting or rate expressions. |
| `gtpfreeras` | `Molecules` | `RasGTP(rafbd)` | Reports free/unbound species matching the pattern. |
| `bvegfr2` | `Molecules` | `vegf(r!1,nrp1bd,c~s).vegfr2(l1!1,c~s)` | Reports bound or complexed species matching the pattern. |
| `bnrp1` | `Molecules` | `vegf(nrp1bd!1,c~s).NRP1(vegfabd!1,c~s)` | Reports bound or complexed species matching the pattern. |
| `bvegfr1` | `Molecules` | `vegf(r!1,nrp1bd,c~s).vegfr1(l2!1,c~s)` | Reports bound or complexed species matching the pattern. |
| `bvegfr1dimer` | `Molecules` | `vegf(r!1,r!2,c~s).vegfr1(l2!1,c~s).vegfr1(l2!2,c~s)` | Reports bound or complexed species matching the pattern. |
| `bvegfr2_2` | `Molecules` | `vegf(r!1,c~s).vegfr2(l1!1,c~s)` | Reports bound or complexed species matching the pattern. |
| `bvegfr1_2` | `Molecules` | `vegf(r!1,c~s).vegfr1(l2!1,c~s)` | Reports bound or complexed species matching the pattern. |
| `vegfbound_1` | `Molecules` | `vegf(r!+,nrp1bd,c~s)` | Reports bound or complexed species matching the pattern. |
| `vegfbound_2` | `Species` | `vegf(r,nrp1bd!+,c~s)` | Reports bound or complexed species matching the pattern. |
| `vegfbound_3` | `Molecules` | `vegf(r!+,c~s)` | Reports bound or complexed species matching the pattern. |
| `vegfbound_4` | `Species` | `vegf(r,r,nrp1bd!1,c~s).NRP1(vegfabd!1,c~s)` | Reports bound or complexed species matching the pattern. |
| `Iopenstim` | `Molecules` | `Istim()` | Reports the BNGL pattern for downstream plotting or rate expressions. |
| `nrp1r1s` | `Molecules` | `NRP1(vegfabd!1,c~s).vegfr1(nrp1bd!1,c~s)` | Reports bound or complexed species matching the pattern. |
| `CIB1mem` | `Molecules` | `CIB1(location~membrane)` | Reports the BNGL pattern for downstream plotting or rate expressions. |
| `freepip3` | `Molecules` | `PI(PIsite~4P)` | Reports free/unbound species matching the pattern. |
| `ps473akt` | `Molecules` | `AKT(S473~pS)` | Reports phosphorylated or modified species matching the pattern. |
| `ps308akt` | `Molecules` | `AKT(T308~pS)` | Reports phosphorylated or modified species matching the pattern. |
| `phosphoAxltotal` | `Molecules` | `Axl(Ysrc~pY!?,Yaxl~pY!?)` | Reports phosphorylated or modified species matching the pattern. |
| `phosphoAxlpSrc` | `Molecules` | `Axl(Ysrc~pY!?)` | Reports phosphorylated or modified species matching the pattern. |
| `phosphoAxlpauto` | `Molecules` | `Axl(Yaxl~pY!?)` | Reports phosphorylated or modified species matching the pattern. |
| `activeSrc` | `Molecules` | `TSADSrc(Y1~pY!?)` | Reports phosphorylated or modified species matching the pattern. |
| `phosphoeNOS` | `Molecules` | `eNOS(S1177~pS)` | Reports phosphorylated or modified species matching the pattern. |
| `ppAkt` | `Molecules` | `AKT(S473~pS,T308~pS)` | Reports phosphorylated or modified species matching the pattern. |

## 8. Actions and simulation workflow

1. `generate_network({overwrite=>1,max_agg=>10})` — execution command affecting network generation, simulation, scanning, or output.

## 9. Technical caveats and ambiguities

- No compartments or anchors are declared despite many molecule states named like surface/internal/recycling states (`s`, `i`, `i2`, `r`). Those are internal states, not BNGL compartments.

- The model uses many algebraic rate expressions directly in reaction rules rather than a separate functions block.

- Several receptor-state transitions are encoded as explicit rules over the `c` internal state.

- The complete rule inventory has 232 rows; downstream review should compare this count with the `begin reaction rules` block after any source edits.

- The summary keeps raw molecule, site, state, and parameter names because this is the coder-facing version and those identifiers are necessary for implementation review.
