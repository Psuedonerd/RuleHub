# Coder Model Explanation: Dolan 2015

## 1. Model identity and scope

- **Model id:** `Dolan_2015`
- **Title:** Dolan 2015
- **BNGL path:** `Published/Dolan2015/Dolan_2015.bngl`
- **YAML path:** `Published/Dolan2015/metadata.yaml`
- **Metadata description:** Insulin signaling
- **Scope:** A combined DNA-damage, p53/MDM2/p21 stress-response, oxidative damage, non-homologous end joining (NHEJ), PARP/Ligase repair, ATM/H2AX focus, and senescence-switching model. The source explicitly starts as a combined p53 and NHEJ model, then enumerates 50 explicit DNA break loci and many repeated repair-rule families over those loci.

## 2. BNGL block inventory

| Block | Present? | Count / role |
| --- | --- | --- |
| Parameters | Yes | 73 parameter entries. |
| Compartments | No | 0 compartment entries. |
| Anchors | No | 0 anchor entries. |
| Molecule types | Yes | 74 molecule type entries. |
| Seed/species | Yes | 75 initial species entries. |
| Observables | Yes | 176 observable entries. |
| Functions | Yes | 9 function entries. |
| Reaction rules | Yes | 2339 reaction rules. |
| Actions | Yes | 50 action or inline execution commands. |

## 3. Parameters, functions, and rate laws

The model uses the following parameter entries. Comment text is preserved when the source provides it; otherwise the role is inferred from the parameter name and where it is used.

| Parameter | Value/expression | Role / source comment |
| --- | --- | --- |
| `kp53mRNAsyn` | `0.06` | Rate of p53 mRNA Synthesis |
| `kp53mRNAdeg` | `0.006` | Rate of p53 mRNA Degradation |
| `kp53syn` | `0.36` | Rate of p53 Synthesis |
| `kp53deg` | `4.95e-5` | Rate of p53 Degradation |
| `kp53degMDM2dep` | `0.0495` | Rate of p53 Degradation-MDM2 Dependant |
| `kp53phos` | `0.36` | Rate of p53 Phosphorylation |
| `kp53dphos` | `30` | Rate of p53 Dephosphorylation |
| `kMDM2mRNAsyn` | `0.006` | Rate of MDM2 mRNA Synthesis |
| `kMDM2mRNAdeg` | `0.006` | Rate of MDM2 mRNA Degradation |
| `kMDM2syn` | `0.0297` | Rate of MDM2 Synthesis |
| `kMDM2deg` | `0.02598` | Rate of MDM2 Degradation |
| `kMDM2pdeg` | `0.024` | Rate of Phosphorylated MDM2 Degradation |
| `kMDM2phos` | `120` | Rate of MDM2 Phosphorylation |
| `kMDM2dphos` | `30` | Rate of p53 Dephosphorylation |
| `kp53MDM2bind` | `0.0693` | Rate of p53 MDM2 Binding |
| `kp53MDM2dis` | `0.0000693` | Rate of p53 MDM2 Dissociation |
| `kp21mRNAsyn` | `0.0000036` | Rate of p21 mRNA Synthesis (p53) |
| `kp21mRNAsynp` | `0.00036` | Rate of p21 mRNA Synthesis (Phosphorylated p53) |
| `kp21mRNAdeg` | `0.00144` | Rate of p21 mRNA Degradation |
| `kp21synstep1` | `0.024` | Rate of p21 Synthesis Step 1 |
| `kp21synstep2` | `0.0024` | Rate of p21 Synthesis Step 2 |
| `kp21synstep3` | `0.0024` | Rate of p21 Synthesis Step 3 |
| `kp21deg` | `0.0114` | Rate of p21 Degradation |
| `kGADD45act` | `0.00024` | Rate of GADD45 Activation/Production |
| `kGADD45deg` | `0.0006` | Rate of GADD45 Degradation |
| `kp38phos` | `0.48` | Rate of p38 Phosphorylation |
| `kp38dphos` | `6` | Rate of p38 Dephosphorylation |
| `kROSgen` | `1.5` | Rate of ROS Generation by p38 |
| `kIR` | `80` | Kinetic rate or kinetic expression parameter. |
| `kROS` | `50` | Constant rate of ROS production |
| `kdROS` | `5` | ROS degradation rate |
| `kdam1` | `0.000006` | Rate of simple damage production by ROS |
| `kdam2` | `0.000006` | Rate of complex damage production by ROS |
| `kdku1` | `0.5` | Rate of Ku dissociation from a simple break |
| `kdku2` | `0.5` | Rate of Ku dissociation from a complex break |
| `kdku3` | `5` | Rate of oxidised Ku dissociation from a simple break |
| `kdku4` | `5` | Rate of oxidised Ku dissociation from a complex break |
| `kdnapk1` | `0.033` | Rate of DNAPK simple break complex formation |
| `kdnapk2` | `0.0017` | Rate of DNAPK complex break complex formation |
| `kddnapk1` | `0.02` | Rate of DNAPK simple break complex dissociation |
| `kddnapk2` | `0.02` | Rate of DNAPK complex break complex dissociation |
| `kdnapkphos1` | `0.28` | Rate pd DNAPK phosphorylation in a DNAPK complex of a simple break |
| `kdnapkphos2` | `0.28` | Rate pd DNAPK phosphorylation in a DNAPK complex of a complex break |
| `kliIV1` | `0.00071` | Rate of LigaseIV binding to a simple break complex |
| `kliIV2` | `0.00046` | Rate of LigaseIV binding to a complex break complex |
| `kdliIV1` | `0.0001` | Rate of LigaseIV dissociation from a simple break complex |
| `kdliIV2` | `0.0001` | Rate of LigaseIV dissociation from a complex break complex |
| `kfixIV1` | `0.0285` | Rate of DNA repair by LigaseIV of a simple break |
| `kfixIV2` | `0.0285` | Rate of DNA repair by LigaseIV of a complex break |
| `kPARP1` | `0.000077` | Rate of PARP binding to simple break |
| `kPARP2` | `0.000065` | Rate of PARP binding to complex break |
| `kdPARP1` | `0.02` | Rate of PARP dissociation from a simple break |
| `kdPARP2` | `0.02` | Rate of PARP dissociation from a complex break |
| `kliIII1` | `0.0015` | Rate of LigaseIII binding to a simple break |
| `kliIII2` | `0.00024` | Rate of LigaseIII binding to a complex break |
| `kdliIII1` | `0.0001` | Rate of LigaseIII dissociation from a simple break |
| `kdliIII2` | `0.0001` | Rate of LigaseIII dissociation from a complex break |
| `kfixIII1` | `0.0006` | Rate of DNA accurate repair by LigaseIII for a simple break |
| `kfixIII2` | `0.0006` | Rate of DNA accurate repair by LigaseIII for a complex break |
| `kfixIII3` | `0.0009` | Rate of DNA inaccurate repair by LigaseIII for a simple break |
| `kfixIII4` | `0.0009` | Rate of dna inaccurate repair by LigaseIII for a complex break |
| `kATMact` | `0.0012` | Rate of ATM Activation |
| `kATMinact` | `0.03` | Rate of ATM Inactivation |
| `kh2axp1` | `0.1` | Phosphorylation of h2ax via ATM |
| `kh2axp2` | `0.5` | Phosphorylation of h2ax via DNA-PKcs |
| `kh2axu` | `0.01` | Dephosphorylation of h2ax |
| `kh2axfoc` | `0.5` | Creation of damage foci |
| `kfocback` | `0.03` | Resolution of damage foci |
| `kh2axfull` | `0.1` | Creation of complete damage foci |
| `kfocfin` | `0.03` | Resolution of complete damage foci |
| `kox` | `0.000025` | Rate of oxidisation of Ku |
| `kred` | `0.002` | Rate of reduction of Ku |
| `ksen` | `100` | Activation of senescent state |

**Functions**

| Function | Technical interpretation |
| --- | --- |
| `kku1() = if(Senescent_Counter>0,0.000000034,0.00034)` | Executable expression used by rules or rate logic. |
| `kku2() = if(Senescent_Counter>0,0.000000021,0.00021)` | Executable expression used by rules or rate logic. |
| `kplus() = if(p21>15,0.04,0)` | Executable expression used by rules or rate logic. |
| `kminus() = if(p21<=15&&Sen_Min<1,0.5,0)` | Executable expression used by rules or rate logic. |
| `kKuDown() = if(Senescent_Counter==1,0.01,0)` | Executable expression used by rules or rate logic. |
| `kKustop() = if(Ku<=250,0,1)` | Executable expression used by rules or rate logic. |
| `kParpDown() = if(Senescent_Counter==1,0.01,0)` | Executable expression used by rules or rate logic. |
| `kParpstop() = if(PARP<=5,0,1)` | Executable expression used by rules or rate logic. |
| `kDelete()= if(Sink<=5,0,10000)` | Executable expression used by rules or rate logic. |

## 4. Molecule types, sites, and states

| Molecule type | Site count | Sites/components | Internal states | Anchor/allowed compartments | Binding/modification roles | Notes |
| --- | ---: | --- | --- | --- | --- | --- |
| `Time` | 0 | None | None | None | No specific role inferred beyond molecule identity. | Declared in molecule types block. |
| `T` | 0 | None | None | None | No specific role inferred beyond molecule identity. | Declared in molecule types block. |
| `P` | 0 | None | None | None | No specific role inferred beyond molecule identity. | Declared in molecule types block. |
| `E` | 0 | None | None | None | No specific role inferred beyond molecule identity. | Declared in molecule types block. |
| `IR` | 0 | None | None | None | No specific role inferred beyond molecule identity. | Declared in molecule types block. |
| `D` | 0 | None | None | None | No specific role inferred beyond molecule identity. | Declared in molecule types block. |
| `p53_mRNA` | 0 | None | None | None | No specific role inferred beyond molecule identity. | Declared in molecule types block. |
| `p53` | 1 | `Site1` | Site1: u, p | None | Site1 is an internal state/modification coordinate | Declared in molecule types block. |
| `MDM2` | 1 | `Site1` | Site1: u, p | None | Site1 is an internal state/modification coordinate | Declared in molecule types block. |
| `MDM2_mRNA` | 0 | None | None | None | No specific role inferred beyond molecule identity. | Declared in molecule types block. |
| `p21_mRNA` | 0 | None | None | None | No specific role inferred beyond molecule identity. | Declared in molecule types block. |
| `p21` | 1 | `step` | step: 1, 2, 3 | None | step is an internal state/modification coordinate | Declared in molecule types block. |
| `p38` | 1 | `Site1` | Site1: u, p | None | Site1 is an internal state/modification coordinate | Declared in molecule types block. |
| `GADD45` | 0 | None | None | None | No specific role inferred beyond molecule identity. | Declared in molecule types block. |
| `Sink` | 0 | None | None | None | No specific role inferred beyond molecule identity. | Declared in molecule types block. |
| `ATM` | 2 | `state`, `h2ax` | state: 0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 21, 22, 23, 24, 25, 26, 27, 28, 29, 30, 31, 32, 33, 34, 35, 36, 37, 38, 39, 40, 41, 42, 43, 44, 45, 46, 47, 48, 49, 50 | None | state is an internal state/modification coordinate; h2ax is used as a binding/matching component | Declared in molecule types block. |
| `DNA1` | 2 | `site`, `h2ax` | site: ok, sdsb, cdsb; h2ax: u, p, foc | None | site is an internal state/modification coordinate; h2ax is an internal state/modification coordinate | Declared in molecule types block. |
| `DNA2` | 2 | `site`, `h2ax` | site: ok, sdsb, cdsb; h2ax: u, p, foc | None | site is an internal state/modification coordinate; h2ax is an internal state/modification coordinate | Declared in molecule types block. |
| `DNA3` | 2 | `site`, `h2ax` | site: ok, sdsb, cdsb; h2ax: u, p, foc | None | site is an internal state/modification coordinate; h2ax is an internal state/modification coordinate | Declared in molecule types block. |
| `DNA4` | 2 | `site`, `h2ax` | site: ok, sdsb, cdsb; h2ax: u, p, foc | None | site is an internal state/modification coordinate; h2ax is an internal state/modification coordinate | Declared in molecule types block. |
| `DNA5` | 2 | `site`, `h2ax` | site: ok, sdsb, cdsb; h2ax: u, p, foc | None | site is an internal state/modification coordinate; h2ax is an internal state/modification coordinate | Declared in molecule types block. |
| `DNA6` | 2 | `site`, `h2ax` | site: ok, sdsb, cdsb; h2ax: u, p, foc | None | site is an internal state/modification coordinate; h2ax is an internal state/modification coordinate | Declared in molecule types block. |
| `DNA7` | 2 | `site`, `h2ax` | site: ok, sdsb, cdsb; h2ax: u, p, foc | None | site is an internal state/modification coordinate; h2ax is an internal state/modification coordinate | Declared in molecule types block. |
| `DNA8` | 2 | `site`, `h2ax` | site: ok, sdsb, cdsb; h2ax: u, p, foc | None | site is an internal state/modification coordinate; h2ax is an internal state/modification coordinate | Declared in molecule types block. |
| `DNA9` | 2 | `site`, `h2ax` | site: ok, sdsb, cdsb; h2ax: u, p, foc | None | site is an internal state/modification coordinate; h2ax is an internal state/modification coordinate | Declared in molecule types block. |
| `DNA10` | 2 | `site`, `h2ax` | site: ok, sdsb, cdsb; h2ax: u, p, foc | None | site is an internal state/modification coordinate; h2ax is an internal state/modification coordinate | Declared in molecule types block. |
| `DNA11` | 2 | `site`, `h2ax` | site: ok, sdsb, cdsb; h2ax: u, p, foc | None | site is an internal state/modification coordinate; h2ax is an internal state/modification coordinate | Declared in molecule types block. |
| `DNA12` | 2 | `site`, `h2ax` | site: ok, sdsb, cdsb; h2ax: u, p, foc | None | site is an internal state/modification coordinate; h2ax is an internal state/modification coordinate | Declared in molecule types block. |
| `DNA13` | 2 | `site`, `h2ax` | site: ok, sdsb, cdsb; h2ax: u, p, foc | None | site is an internal state/modification coordinate; h2ax is an internal state/modification coordinate | Declared in molecule types block. |
| `DNA14` | 2 | `site`, `h2ax` | site: ok, sdsb, cdsb; h2ax: u, p, foc | None | site is an internal state/modification coordinate; h2ax is an internal state/modification coordinate | Declared in molecule types block. |
| `DNA15` | 2 | `site`, `h2ax` | site: ok, sdsb, cdsb; h2ax: u, p, foc | None | site is an internal state/modification coordinate; h2ax is an internal state/modification coordinate | Declared in molecule types block. |
| `DNA16` | 2 | `site`, `h2ax` | site: ok, sdsb, cdsb; h2ax: u, p, foc | None | site is an internal state/modification coordinate; h2ax is an internal state/modification coordinate | Declared in molecule types block. |
| `DNA17` | 2 | `site`, `h2ax` | site: ok, sdsb, cdsb; h2ax: u, p, foc | None | site is an internal state/modification coordinate; h2ax is an internal state/modification coordinate | Declared in molecule types block. |
| `DNA18` | 2 | `site`, `h2ax` | site: ok, sdsb, cdsb; h2ax: u, p, foc | None | site is an internal state/modification coordinate; h2ax is an internal state/modification coordinate | Declared in molecule types block. |
| `DNA19` | 2 | `site`, `h2ax` | site: ok, sdsb, cdsb; h2ax: u, p, foc | None | site is an internal state/modification coordinate; h2ax is an internal state/modification coordinate | Declared in molecule types block. |
| `DNA20` | 2 | `site`, `h2ax` | site: ok, sdsb, cdsb; h2ax: u, p, foc | None | site is an internal state/modification coordinate; h2ax is an internal state/modification coordinate | Declared in molecule types block. |
| `DNA21` | 2 | `site`, `h2ax` | site: ok, sdsb, cdsb; h2ax: u, p, foc | None | site is an internal state/modification coordinate; h2ax is an internal state/modification coordinate | Declared in molecule types block. |
| `DNA22` | 2 | `site`, `h2ax` | site: ok, sdsb, cdsb; h2ax: u, p, foc | None | site is an internal state/modification coordinate; h2ax is an internal state/modification coordinate | Declared in molecule types block. |
| `DNA23` | 2 | `site`, `h2ax` | site: ok, sdsb, cdsb; h2ax: u, p, foc | None | site is an internal state/modification coordinate; h2ax is an internal state/modification coordinate | Declared in molecule types block. |
| `DNA24` | 2 | `site`, `h2ax` | site: ok, sdsb, cdsb; h2ax: u, p, foc | None | site is an internal state/modification coordinate; h2ax is an internal state/modification coordinate | Declared in molecule types block. |
| `DNA25` | 2 | `site`, `h2ax` | site: ok, sdsb, cdsb; h2ax: u, p, foc | None | site is an internal state/modification coordinate; h2ax is an internal state/modification coordinate | Declared in molecule types block. |
| `DNA26` | 2 | `site`, `h2ax` | site: ok, sdsb, cdsb; h2ax: u, p, foc | None | site is an internal state/modification coordinate; h2ax is an internal state/modification coordinate | Declared in molecule types block. |
| `DNA27` | 2 | `site`, `h2ax` | site: ok, sdsb, cdsb; h2ax: u, p, foc | None | site is an internal state/modification coordinate; h2ax is an internal state/modification coordinate | Declared in molecule types block. |
| `DNA28` | 2 | `site`, `h2ax` | site: ok, sdsb, cdsb; h2ax: u, p, foc | None | site is an internal state/modification coordinate; h2ax is an internal state/modification coordinate | Declared in molecule types block. |
| `DNA29` | 2 | `site`, `h2ax` | site: ok, sdsb, cdsb; h2ax: u, p, foc | None | site is an internal state/modification coordinate; h2ax is an internal state/modification coordinate | Declared in molecule types block. |
| `DNA30` | 2 | `site`, `h2ax` | site: ok, sdsb, cdsb; h2ax: u, p, foc | None | site is an internal state/modification coordinate; h2ax is an internal state/modification coordinate | Declared in molecule types block. |
| `DNA31` | 2 | `site`, `h2ax` | site: ok, sdsb, cdsb; h2ax: u, p, foc | None | site is an internal state/modification coordinate; h2ax is an internal state/modification coordinate | Declared in molecule types block. |
| `DNA32` | 2 | `site`, `h2ax` | site: ok, sdsb, cdsb; h2ax: u, p, foc | None | site is an internal state/modification coordinate; h2ax is an internal state/modification coordinate | Declared in molecule types block. |
| `DNA33` | 2 | `site`, `h2ax` | site: ok, sdsb, cdsb; h2ax: u, p, foc | None | site is an internal state/modification coordinate; h2ax is an internal state/modification coordinate | Declared in molecule types block. |
| `DNA34` | 2 | `site`, `h2ax` | site: ok, sdsb, cdsb; h2ax: u, p, foc | None | site is an internal state/modification coordinate; h2ax is an internal state/modification coordinate | Declared in molecule types block. |
| `DNA35` | 2 | `site`, `h2ax` | site: ok, sdsb, cdsb; h2ax: u, p, foc | None | site is an internal state/modification coordinate; h2ax is an internal state/modification coordinate | Declared in molecule types block. |
| `DNA36` | 2 | `site`, `h2ax` | site: ok, sdsb, cdsb; h2ax: u, p, foc | None | site is an internal state/modification coordinate; h2ax is an internal state/modification coordinate | Declared in molecule types block. |
| `DNA37` | 2 | `site`, `h2ax` | site: ok, sdsb, cdsb; h2ax: u, p, foc | None | site is an internal state/modification coordinate; h2ax is an internal state/modification coordinate | Declared in molecule types block. |
| `DNA38` | 2 | `site`, `h2ax` | site: ok, sdsb, cdsb; h2ax: u, p, foc | None | site is an internal state/modification coordinate; h2ax is an internal state/modification coordinate | Declared in molecule types block. |
| `DNA39` | 2 | `site`, `h2ax` | site: ok, sdsb, cdsb; h2ax: u, p, foc | None | site is an internal state/modification coordinate; h2ax is an internal state/modification coordinate | Declared in molecule types block. |
| `DNA40` | 2 | `site`, `h2ax` | site: ok, sdsb, cdsb; h2ax: u, p, foc | None | site is an internal state/modification coordinate; h2ax is an internal state/modification coordinate | Declared in molecule types block. |
| `DNA41` | 2 | `site`, `h2ax` | site: ok, sdsb, cdsb; h2ax: u, p, foc | None | site is an internal state/modification coordinate; h2ax is an internal state/modification coordinate | Declared in molecule types block. |
| `DNA42` | 2 | `site`, `h2ax` | site: ok, sdsb, cdsb; h2ax: u, p, foc | None | site is an internal state/modification coordinate; h2ax is an internal state/modification coordinate | Declared in molecule types block. |
| `DNA43` | 2 | `site`, `h2ax` | site: ok, sdsb, cdsb; h2ax: u, p, foc | None | site is an internal state/modification coordinate; h2ax is an internal state/modification coordinate | Declared in molecule types block. |
| `DNA44` | 2 | `site`, `h2ax` | site: ok, sdsb, cdsb; h2ax: u, p, foc | None | site is an internal state/modification coordinate; h2ax is an internal state/modification coordinate | Declared in molecule types block. |
| `DNA45` | 2 | `site`, `h2ax` | site: ok, sdsb, cdsb; h2ax: u, p, foc | None | site is an internal state/modification coordinate; h2ax is an internal state/modification coordinate | Declared in molecule types block. |
| `DNA46` | 2 | `site`, `h2ax` | site: ok, sdsb, cdsb; h2ax: u, p, foc | None | site is an internal state/modification coordinate; h2ax is an internal state/modification coordinate | Declared in molecule types block. |
| `DNA47` | 2 | `site`, `h2ax` | site: ok, sdsb, cdsb; h2ax: u, p, foc | None | site is an internal state/modification coordinate; h2ax is an internal state/modification coordinate | Declared in molecule types block. |
| `DNA48` | 2 | `site`, `h2ax` | site: ok, sdsb, cdsb; h2ax: u, p, foc | None | site is an internal state/modification coordinate; h2ax is an internal state/modification coordinate | Declared in molecule types block. |
| `DNA49` | 2 | `site`, `h2ax` | site: ok, sdsb, cdsb; h2ax: u, p, foc | None | site is an internal state/modification coordinate; h2ax is an internal state/modification coordinate | Declared in molecule types block. |
| `DNA50` | 2 | `site`, `h2ax` | site: ok, sdsb, cdsb; h2ax: u, p, foc | None | site is an internal state/modification coordinate; h2ax is an internal state/modification coordinate | Declared in molecule types block. |
| `ROS` | 0 | None | None | None | No specific role inferred beyond molecule identity. | Declared in molecule types block. |
| `Ku` | 3 | `dna`, `cs`, `cys` | cys: red, ox | None | dna is used as a binding/matching component; cs is used as a binding/matching component; cys is an internal state/modification coordinate | Declared in molecule types block. |
| `DNAPKcs` | 3 | `ku`, `liIV`, `psite` | psite: u, p | None | ku is used as a binding/matching component; liIV is used as a binding/matching component; psite is an internal state/modification coordinate | Declared in molecule types block. |
| `LiIII` | 1 | `PARP` | None | None | PARP is used as a binding/matching component | Declared in molecule types block. |
| `LiIV` | 1 | `cs` | None | None | cs is used as a binding/matching component | Declared in molecule types block. |
| `PARP` | 2 | `dna`, `liIII` | None | None | dna is used as a binding/matching component; liIII is used as a binding/matching component | Declared in molecule types block. |
| `I` | 0 | None | None | None | No specific role inferred beyond molecule identity. | Declared in molecule types block. |
| `Sen` | 2 | `int`, `State` | int: 1, 10, PLUS, MINUS; State: normal, sen | None | int is an internal state/modification coordinate; State is an internal state/modification coordinate | Declared in molecule types block. |

## 5. Compartments, anchors, initial species, and setup

No BNGL compartment block is declared.

No anchors block is declared.

Ionizing radiation and ROS generate simple or complex DNA breaks across explicit DNA loci. ATM and DNA-PKcs signal damage to p53, p38, H2AX, and repair machinery; p53 induces MDM2 and p21, p21 controls a senescence counter, and senescence feeds back by reducing Ku/PARP repair availability.

| Initial species entry | Initial amount/expression | Technical setup meaning |
| --- | --- | --- |
| `Time()` | `0` | Initial population or concentration for this exact pattern. |
| `P()` | `1` | Initial population or concentration for this exact pattern. |
| `T()` | `1` | Initial population or concentration for this exact pattern. |
| `E()` | `1` | Initial population or concentration for this exact pattern. |
| `IR()` | `0` | Initial population or concentration for this exact pattern. |
| `D()` | `10` | Initial population or concentration for this exact pattern. |
| `p53_mRNA()` | `10` | Initial population or concentration for this exact pattern. |
| `p53(Site1~u)` | `5` | Initial population or concentration for this exact pattern. |
| `MDM2_mRNA()` | `10` | Initial population or concentration for this exact pattern. |
| `MDM2(Site1~u)` | `5` | Initial population or concentration for this exact pattern. |
| `p53(Site1!1~u).MDM2(Site1!1~u)` | `95` | Initial population or concentration for this exact pattern. |
| `p21_mRNA()` | `1` | Initial population or concentration for this exact pattern. |
| `p21(step~1)` | `0` | Initial population or concentration for this exact pattern. |
| `p38(Site1~u)` | `100` | Initial population or concentration for this exact pattern. |
| `$Sink()` | `0` | Initial population or concentration for this exact pattern. |
| `ATM(state~0,h2ax)` | `200` | Initial population or concentration for this exact pattern. |
| `DNA1(site~ok,h2ax~u)` | `1` | Initial population or concentration for this exact pattern. |
| `DNA2(site~ok,h2ax~u)` | `1` | Initial population or concentration for this exact pattern. |
| `DNA3(site~ok,h2ax~u)` | `1` | Initial population or concentration for this exact pattern. |
| `DNA4(site~ok,h2ax~u)` | `1` | Initial population or concentration for this exact pattern. |
| `DNA5(site~ok,h2ax~u)` | `1` | Initial population or concentration for this exact pattern. |
| `DNA6(site~ok,h2ax~u)` | `1` | Initial population or concentration for this exact pattern. |
| `DNA7(site~ok,h2ax~u)` | `1` | Initial population or concentration for this exact pattern. |
| `DNA8(site~ok,h2ax~u)` | `1` | Initial population or concentration for this exact pattern. |
| `DNA9(site~ok,h2ax~u)` | `1` | Initial population or concentration for this exact pattern. |
| `DNA10(site~ok,h2ax~u)` | `1` | Initial population or concentration for this exact pattern. |
| `DNA11(site~ok,h2ax~u)` | `1` | Initial population or concentration for this exact pattern. |
| `DNA12(site~ok,h2ax~u)` | `1` | Initial population or concentration for this exact pattern. |
| `DNA13(site~ok,h2ax~u)` | `1` | Initial population or concentration for this exact pattern. |
| `DNA14(site~ok,h2ax~u)` | `1` | Initial population or concentration for this exact pattern. |
| `DNA15(site~ok,h2ax~u)` | `1` | Initial population or concentration for this exact pattern. |
| `DNA16(site~ok,h2ax~u)` | `1` | Initial population or concentration for this exact pattern. |
| `DNA17(site~ok,h2ax~u)` | `1` | Initial population or concentration for this exact pattern. |
| `DNA18(site~ok,h2ax~u)` | `1` | Initial population or concentration for this exact pattern. |
| `DNA19(site~ok,h2ax~u)` | `1` | Initial population or concentration for this exact pattern. |
| `DNA20(site~ok,h2ax~u)` | `1` | Initial population or concentration for this exact pattern. |
| `DNA21(site~ok,h2ax~u)` | `1` | Initial population or concentration for this exact pattern. |
| `DNA22(site~ok,h2ax~u)` | `1` | Initial population or concentration for this exact pattern. |
| `DNA23(site~ok,h2ax~u)` | `1` | Initial population or concentration for this exact pattern. |
| `DNA24(site~ok,h2ax~u)` | `1` | Initial population or concentration for this exact pattern. |
| `DNA25(site~ok,h2ax~u)` | `1` | Initial population or concentration for this exact pattern. |
| `DNA26(site~ok,h2ax~u)` | `1` | Initial population or concentration for this exact pattern. |
| `DNA27(site~ok,h2ax~u)` | `1` | Initial population or concentration for this exact pattern. |
| `DNA28(site~ok,h2ax~u)` | `1` | Initial population or concentration for this exact pattern. |
| `DNA29(site~ok,h2ax~u)` | `1` | Initial population or concentration for this exact pattern. |
| `DNA30(site~ok,h2ax~u)` | `1` | Initial population or concentration for this exact pattern. |
| `DNA31(site~ok,h2ax~u)` | `1` | Initial population or concentration for this exact pattern. |
| `DNA32(site~ok,h2ax~u)` | `1` | Initial population or concentration for this exact pattern. |
| `DNA33(site~ok,h2ax~u)` | `1` | Initial population or concentration for this exact pattern. |
| `DNA34(site~ok,h2ax~u)` | `1` | Initial population or concentration for this exact pattern. |
| `DNA35(site~ok,h2ax~u)` | `1` | Initial population or concentration for this exact pattern. |
| `DNA36(site~ok,h2ax~u)` | `1` | Initial population or concentration for this exact pattern. |
| `DNA37(site~ok,h2ax~u)` | `1` | Initial population or concentration for this exact pattern. |
| `DNA38(site~ok,h2ax~u)` | `1` | Initial population or concentration for this exact pattern. |
| `DNA39(site~ok,h2ax~u)` | `1` | Initial population or concentration for this exact pattern. |
| `DNA40(site~ok,h2ax~u)` | `1` | Initial population or concentration for this exact pattern. |
| `DNA41(site~ok,h2ax~u)` | `1` | Initial population or concentration for this exact pattern. |
| `DNA42(site~ok,h2ax~u)` | `1` | Initial population or concentration for this exact pattern. |
| `DNA43(site~ok,h2ax~u)` | `1` | Initial population or concentration for this exact pattern. |
| `DNA44(site~ok,h2ax~u)` | `1` | Initial population or concentration for this exact pattern. |
| `DNA45(site~ok,h2ax~u)` | `1` | Initial population or concentration for this exact pattern. |
| `DNA46(site~ok,h2ax~u)` | `1` | Initial population or concentration for this exact pattern. |
| `DNA47(site~ok,h2ax~u)` | `1` | Initial population or concentration for this exact pattern. |
| `DNA48(site~ok,h2ax~u)` | `1` | Initial population or concentration for this exact pattern. |
| `DNA49(site~ok,h2ax~u)` | `1` | Initial population or concentration for this exact pattern. |
| `DNA50(site~ok,h2ax~u)` | `1` | Initial population or concentration for this exact pattern. |
| `ROS()` | `0` | Initial population or concentration for this exact pattern. |
| `Ku(dna,cs,cys~red)` | `450` | Initial population or concentration for this exact pattern. |
| `Ku(dna,cs,cys~ox)` | `50` | Initial population or concentration for this exact pattern. |
| `DNAPKcs(ku,liIV,psite~u)` | `250` | Initial population or concentration for this exact pattern. |
| `LiIII(PARP)` | `300` | Initial population or concentration for this exact pattern. |
| `LiIV(cs)` | `300` | Initial population or concentration for this exact pattern. |
| `PARP(dna,liIII)` | `500` | Initial population or concentration for this exact pattern. |
| `I()` | `1` | Initial population or concentration for this exact pattern. |
| `Sen(int~1,State~normal)` | `1` | Initial population or concentration for this exact pattern. |

## 6. Complete reaction-rule inventory

The source contains **2339** reaction rules. The inventory below preserves one row per source rule, grouped only for readability.

### Rules 1-250

| # | Rule label/name | Direction | Participants | Rate/expression | Modeled change | Rule pattern | Technical meaning |
| ---: | --- | --- | --- | --- | --- | --- | --- |

| 1 | `Unlabeled` | one-way | D, Sink | `kDelete() (DeleteMolecules)` | stoichiometric pattern rewrite | `D() + Sink()  -> D()` | Transforms D, Sink by stoichiometric pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2 | `Unlabeled` | one-way | P, p53_mRNA | `kp53mRNAsyn` | stoichiometric pattern rewrite | `P()  -> p53_mRNA() + P()` | Transforms P, p53_mRNA by stoichiometric pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 3 | `Unlabeled` | one-way | Sink, p53_mRNA | `kp53mRNAdeg` | sink/degradation/removal | `p53_mRNA()  -> Sink()` | Transforms Sink, p53_mRNA by sink/degradation/removal; see the exact pattern for affected sites/states/bonds. |

| 4 | `Unlabeled` | one-way | p53, p53_mRNA | `kp53syn` | internal-state conversion/modification | `p53_mRNA()  -> p53_mRNA() + p53(Site1~u)` | Transforms p53, p53_mRNA by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 5 | `Unlabeled` | one-way | Sink, p53 | `kp53deg` | sink/degradation/removal | `p53(Site1~u)  -> Sink()` | Transforms Sink, p53 by sink/degradation/removal; see the exact pattern for affected sites/states/bonds. |

| 6 | `Unlabeled` | one-way | Sink, p53 | `kp53deg` | sink/degradation/removal | `p53(Site1~p)  -> Sink()` | Transforms Sink, p53 by sink/degradation/removal; see the exact pattern for affected sites/states/bonds. |

| 7 | `Unlabeled` | one-way | MDM2, p53 | `kp53degMDM2dep (DeleteMolecules)` | state and binding-pattern rewrite | `p53(Site1!1~u).MDM2(Site1!1~u)  -> MDM2(Site1~u)` | Transforms MDM2, p53 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 8 | `Unlabeled` | one-way | ATM, p53 | `kp53phos` | internal-state conversion/modification | `p53(Site1~u) + ATM(state~1,h2ax!?)  -> p53(Site1~p) + ATM(state~1,h2ax!?)` | Transforms ATM, p53 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 9 | `Unlabeled` | one-way | ATM, p53 | `kp53phos` | internal-state conversion/modification | `p53(Site1~u) + ATM(state~2,h2ax!?)  -> p53(Site1~p) + ATM(state~2,h2ax!?)` | Transforms ATM, p53 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 10 | `Unlabeled` | one-way | ATM, p53 | `kp53phos` | internal-state conversion/modification | `p53(Site1~u) + ATM(state~3,h2ax!?)  -> p53(Site1~p) + ATM(state~3,h2ax!?)` | Transforms ATM, p53 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 11 | `Unlabeled` | one-way | ATM, p53 | `kp53phos` | internal-state conversion/modification | `p53(Site1~u) + ATM(state~4,h2ax!?)  -> p53(Site1~p) + ATM(state~4,h2ax!?)` | Transforms ATM, p53 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 12 | `Unlabeled` | one-way | ATM, p53 | `kp53phos` | internal-state conversion/modification | `p53(Site1~u) + ATM(state~5,h2ax!?)  -> p53(Site1~p) + ATM(state~5,h2ax!?)` | Transforms ATM, p53 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 13 | `Unlabeled` | one-way | ATM, p53 | `kp53phos` | internal-state conversion/modification | `p53(Site1~u) + ATM(state~6,h2ax!?)  -> p53(Site1~p) + ATM(state~6,h2ax!?)` | Transforms ATM, p53 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 14 | `Unlabeled` | one-way | ATM, p53 | `kp53phos` | internal-state conversion/modification | `p53(Site1~u) + ATM(state~7,h2ax!?)  -> p53(Site1~p) + ATM(state~7,h2ax!?)` | Transforms ATM, p53 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 15 | `Unlabeled` | one-way | ATM, p53 | `kp53phos` | internal-state conversion/modification | `p53(Site1~u) + ATM(state~8,h2ax!?)  -> p53(Site1~p) + ATM(state~8,h2ax!?)` | Transforms ATM, p53 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 16 | `Unlabeled` | one-way | ATM, p53 | `kp53phos` | internal-state conversion/modification | `p53(Site1~u) + ATM(state~9,h2ax!?)  -> p53(Site1~p) + ATM(state~9,h2ax!?)` | Transforms ATM, p53 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 17 | `Unlabeled` | one-way | ATM, p53 | `kp53phos` | internal-state conversion/modification | `p53(Site1~u) + ATM(state~10,h2ax!?)  -> p53(Site1~p) + ATM(state~10,h2ax!?)` | Transforms ATM, p53 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 18 | `Unlabeled` | one-way | ATM, p53 | `kp53phos` | internal-state conversion/modification | `p53(Site1~u) + ATM(state~11,h2ax!?)  -> p53(Site1~p) + ATM(state~11,h2ax!?)` | Transforms ATM, p53 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 19 | `Unlabeled` | one-way | ATM, p53 | `kp53phos` | internal-state conversion/modification | `p53(Site1~u) + ATM(state~12,h2ax!?)  -> p53(Site1~p) + ATM(state~12,h2ax!?)` | Transforms ATM, p53 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 20 | `Unlabeled` | one-way | ATM, p53 | `kp53phos` | internal-state conversion/modification | `p53(Site1~u) + ATM(state~13,h2ax!?)  -> p53(Site1~p) + ATM(state~13,h2ax!?)` | Transforms ATM, p53 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 21 | `Unlabeled` | one-way | ATM, p53 | `kp53phos` | internal-state conversion/modification | `p53(Site1~u) + ATM(state~14,h2ax!?)  -> p53(Site1~p) + ATM(state~14,h2ax!?)` | Transforms ATM, p53 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 22 | `Unlabeled` | one-way | ATM, p53 | `kp53phos` | internal-state conversion/modification | `p53(Site1~u) + ATM(state~15,h2ax!?)  -> p53(Site1~p) + ATM(state~15,h2ax!?)` | Transforms ATM, p53 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 23 | `Unlabeled` | one-way | ATM, p53 | `kp53phos` | internal-state conversion/modification | `p53(Site1~u) + ATM(state~16,h2ax!?)  -> p53(Site1~p) + ATM(state~16,h2ax!?)` | Transforms ATM, p53 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 24 | `Unlabeled` | one-way | ATM, p53 | `kp53phos` | internal-state conversion/modification | `p53(Site1~u) + ATM(state~17,h2ax!?)  -> p53(Site1~p) + ATM(state~17,h2ax!?)` | Transforms ATM, p53 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 25 | `Unlabeled` | one-way | ATM, p53 | `kp53phos` | internal-state conversion/modification | `p53(Site1~u) + ATM(state~18,h2ax!?)  -> p53(Site1~p) + ATM(state~18,h2ax!?)` | Transforms ATM, p53 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 26 | `Unlabeled` | one-way | ATM, p53 | `kp53phos` | internal-state conversion/modification | `p53(Site1~u) + ATM(state~19,h2ax!?)  -> p53(Site1~p) + ATM(state~19,h2ax!?)` | Transforms ATM, p53 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 27 | `Unlabeled` | one-way | ATM, p53 | `kp53phos` | internal-state conversion/modification | `p53(Site1~u) + ATM(state~20,h2ax!?)  -> p53(Site1~p) + ATM(state~20,h2ax!?)` | Transforms ATM, p53 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 28 | `Unlabeled` | one-way | ATM, p53 | `kp53phos` | internal-state conversion/modification | `p53(Site1~u) + ATM(state~21,h2ax!?)  -> p53(Site1~p) + ATM(state~21,h2ax!?)` | Transforms ATM, p53 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 29 | `Unlabeled` | one-way | ATM, p53 | `kp53phos` | internal-state conversion/modification | `p53(Site1~u) + ATM(state~22,h2ax!?)  -> p53(Site1~p) + ATM(state~22,h2ax!?)` | Transforms ATM, p53 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 30 | `Unlabeled` | one-way | ATM, p53 | `kp53phos` | internal-state conversion/modification | `p53(Site1~u) + ATM(state~23,h2ax!?)  -> p53(Site1~p) + ATM(state~23,h2ax!?)` | Transforms ATM, p53 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 31 | `Unlabeled` | one-way | ATM, p53 | `kp53phos` | internal-state conversion/modification | `p53(Site1~u) + ATM(state~24,h2ax!?)  -> p53(Site1~p) + ATM(state~24,h2ax!?)` | Transforms ATM, p53 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 32 | `Unlabeled` | one-way | ATM, p53 | `kp53phos` | internal-state conversion/modification | `p53(Site1~u) + ATM(state~25,h2ax!?)  -> p53(Site1~p) + ATM(state~25,h2ax!?)` | Transforms ATM, p53 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 33 | `Unlabeled` | one-way | ATM, p53 | `kp53phos` | internal-state conversion/modification | `p53(Site1~u) + ATM(state~26,h2ax!?)  -> p53(Site1~p) + ATM(state~26,h2ax!?)` | Transforms ATM, p53 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 34 | `Unlabeled` | one-way | ATM, p53 | `kp53phos` | internal-state conversion/modification | `p53(Site1~u) + ATM(state~27,h2ax!?)  -> p53(Site1~p) + ATM(state~27,h2ax!?)` | Transforms ATM, p53 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 35 | `Unlabeled` | one-way | ATM, p53 | `kp53phos` | internal-state conversion/modification | `p53(Site1~u) + ATM(state~28,h2ax!?)  -> p53(Site1~p) + ATM(state~28,h2ax!?)` | Transforms ATM, p53 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 36 | `Unlabeled` | one-way | ATM, p53 | `kp53phos` | internal-state conversion/modification | `p53(Site1~u) + ATM(state~29,h2ax!?)  -> p53(Site1~p) + ATM(state~29,h2ax!?)` | Transforms ATM, p53 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 37 | `Unlabeled` | one-way | ATM, p53 | `kp53phos` | internal-state conversion/modification | `p53(Site1~u) + ATM(state~30,h2ax!?)  -> p53(Site1~p) + ATM(state~30,h2ax!?)` | Transforms ATM, p53 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 38 | `Unlabeled` | one-way | ATM, p53 | `kp53phos` | internal-state conversion/modification | `p53(Site1~u) + ATM(state~31,h2ax!?)  -> p53(Site1~p) + ATM(state~31,h2ax!?)` | Transforms ATM, p53 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 39 | `Unlabeled` | one-way | ATM, p53 | `kp53phos` | internal-state conversion/modification | `p53(Site1~u) + ATM(state~32,h2ax!?)  -> p53(Site1~p) + ATM(state~32,h2ax!?)` | Transforms ATM, p53 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 40 | `Unlabeled` | one-way | ATM, p53 | `kp53phos` | internal-state conversion/modification | `p53(Site1~u) + ATM(state~33,h2ax!?)  -> p53(Site1~p) + ATM(state~33,h2ax!?)` | Transforms ATM, p53 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 41 | `Unlabeled` | one-way | ATM, p53 | `kp53phos` | internal-state conversion/modification | `p53(Site1~u) + ATM(state~34,h2ax!?)  -> p53(Site1~p) + ATM(state~34,h2ax!?)` | Transforms ATM, p53 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 42 | `Unlabeled` | one-way | ATM, p53 | `kp53phos` | internal-state conversion/modification | `p53(Site1~u) + ATM(state~35,h2ax!?)  -> p53(Site1~p) + ATM(state~35,h2ax!?)` | Transforms ATM, p53 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 43 | `Unlabeled` | one-way | ATM, p53 | `kp53phos` | internal-state conversion/modification | `p53(Site1~u) + ATM(state~36,h2ax!?)  -> p53(Site1~p) + ATM(state~36,h2ax!?)` | Transforms ATM, p53 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 44 | `Unlabeled` | one-way | ATM, p53 | `kp53phos` | internal-state conversion/modification | `p53(Site1~u) + ATM(state~37,h2ax!?)  -> p53(Site1~p) + ATM(state~37,h2ax!?)` | Transforms ATM, p53 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 45 | `Unlabeled` | one-way | ATM, p53 | `kp53phos` | internal-state conversion/modification | `p53(Site1~u) + ATM(state~38,h2ax!?)  -> p53(Site1~p) + ATM(state~38,h2ax!?)` | Transforms ATM, p53 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 46 | `Unlabeled` | one-way | ATM, p53 | `kp53phos` | internal-state conversion/modification | `p53(Site1~u) + ATM(state~39,h2ax!?)  -> p53(Site1~p) + ATM(state~39,h2ax!?)` | Transforms ATM, p53 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 47 | `Unlabeled` | one-way | ATM, p53 | `kp53phos` | internal-state conversion/modification | `p53(Site1~u) + ATM(state~40,h2ax!?)  -> p53(Site1~p) + ATM(state~40,h2ax!?)` | Transforms ATM, p53 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 48 | `Unlabeled` | one-way | ATM, p53 | `kp53phos` | internal-state conversion/modification | `p53(Site1~u) + ATM(state~41,h2ax!?)  -> p53(Site1~p) + ATM(state~41,h2ax!?)` | Transforms ATM, p53 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 49 | `Unlabeled` | one-way | ATM, p53 | `kp53phos` | internal-state conversion/modification | `p53(Site1~u) + ATM(state~42,h2ax!?)  -> p53(Site1~p) + ATM(state~42,h2ax!?)` | Transforms ATM, p53 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 50 | `Unlabeled` | one-way | ATM, p53 | `kp53phos` | internal-state conversion/modification | `p53(Site1~u) + ATM(state~43,h2ax!?)  -> p53(Site1~p) + ATM(state~43,h2ax!?)` | Transforms ATM, p53 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 51 | `Unlabeled` | one-way | ATM, p53 | `kp53phos` | internal-state conversion/modification | `p53(Site1~u) + ATM(state~44,h2ax!?)  -> p53(Site1~p) + ATM(state~44,h2ax!?)` | Transforms ATM, p53 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 52 | `Unlabeled` | one-way | ATM, p53 | `kp53phos` | internal-state conversion/modification | `p53(Site1~u) + ATM(state~45,h2ax!?)  -> p53(Site1~p) + ATM(state~45,h2ax!?)` | Transforms ATM, p53 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 53 | `Unlabeled` | one-way | ATM, p53 | `kp53phos` | internal-state conversion/modification | `p53(Site1~u) + ATM(state~46,h2ax!?)  -> p53(Site1~p) + ATM(state~46,h2ax!?)` | Transforms ATM, p53 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 54 | `Unlabeled` | one-way | ATM, p53 | `kp53phos` | internal-state conversion/modification | `p53(Site1~u) + ATM(state~47,h2ax!?)  -> p53(Site1~p) + ATM(state~47,h2ax!?)` | Transforms ATM, p53 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 55 | `Unlabeled` | one-way | ATM, p53 | `kp53phos` | internal-state conversion/modification | `p53(Site1~u) + ATM(state~48,h2ax!?)  -> p53(Site1~p) + ATM(state~48,h2ax!?)` | Transforms ATM, p53 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 56 | `Unlabeled` | one-way | ATM, p53 | `kp53phos` | internal-state conversion/modification | `p53(Site1~u) + ATM(state~49,h2ax!?)  -> p53(Site1~p) + ATM(state~49,h2ax!?)` | Transforms ATM, p53 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 57 | `Unlabeled` | one-way | ATM, p53 | `kp53phos` | internal-state conversion/modification | `p53(Site1~u) + ATM(state~50,h2ax!?)  -> p53(Site1~p) + ATM(state~50,h2ax!?)` | Transforms ATM, p53 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 58 | `Unlabeled` | one-way | p53 | `kp53dphos` | internal-state conversion/modification | `p53(Site1~p)  -> p53(Site1~u)` | Transforms p53 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 59 | `Unlabeled` | one-way | MDM2_mRNA, p53 | `kMDM2mRNAsyn` | internal-state conversion/modification | `p53(Site1~u)  -> MDM2_mRNA() + p53(Site1~u)` | Transforms MDM2_mRNA, p53 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 60 | `Unlabeled` | one-way | MDM2_mRNA, p53 | `kMDM2mRNAsyn` | internal-state conversion/modification | `p53(Site1~p)  -> MDM2_mRNA() + p53(Site1~p)` | Transforms MDM2_mRNA, p53 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 61 | `Unlabeled` | one-way | MDM2_mRNA, Sink | `kMDM2mRNAdeg` | sink/degradation/removal | `MDM2_mRNA()  -> Sink()` | Transforms MDM2_mRNA, Sink by sink/degradation/removal; see the exact pattern for affected sites/states/bonds. |

| 62 | `Unlabeled` | one-way | MDM2, MDM2_mRNA | `kMDM2syn` | internal-state conversion/modification | `MDM2_mRNA()  -> MDM2_mRNA() + MDM2(Site1~u)` | Transforms MDM2, MDM2_mRNA by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 63 | `Unlabeled` | one-way | MDM2, Sink | `kMDM2deg` | sink/degradation/removal | `MDM2(Site1~u)  -> Sink()` | Transforms MDM2, Sink by sink/degradation/removal; see the exact pattern for affected sites/states/bonds. |

| 64 | `Unlabeled` | one-way | MDM2, Sink | `kMDM2pdeg` | sink/degradation/removal | `MDM2(Site1~p)  -> Sink()` | Transforms MDM2, Sink by sink/degradation/removal; see the exact pattern for affected sites/states/bonds. |

| 65 | `Unlabeled` | one-way | ATM, MDM2 | `kMDM2phos` | internal-state conversion/modification | `MDM2(Site1~u) + ATM(state~1,h2ax!?)  -> MDM2(Site1~p) + ATM(state~1,h2ax!?)` | Transforms ATM, MDM2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 66 | `Unlabeled` | one-way | ATM, MDM2 | `kMDM2phos` | internal-state conversion/modification | `MDM2(Site1~u) + ATM(state~2,h2ax!?)  -> MDM2(Site1~p) + ATM(state~2,h2ax!?)` | Transforms ATM, MDM2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 67 | `Unlabeled` | one-way | ATM, MDM2 | `kMDM2phos` | internal-state conversion/modification | `MDM2(Site1~u) + ATM(state~3,h2ax!?)  -> MDM2(Site1~p) + ATM(state~3,h2ax!?)` | Transforms ATM, MDM2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 68 | `Unlabeled` | one-way | ATM, MDM2 | `kMDM2phos` | internal-state conversion/modification | `MDM2(Site1~u) + ATM(state~4,h2ax!?)  -> MDM2(Site1~p) + ATM(state~4,h2ax!?)` | Transforms ATM, MDM2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 69 | `Unlabeled` | one-way | ATM, MDM2 | `kMDM2phos` | internal-state conversion/modification | `MDM2(Site1~u) + ATM(state~5,h2ax!?)  -> MDM2(Site1~p) + ATM(state~5,h2ax!?)` | Transforms ATM, MDM2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 70 | `Unlabeled` | one-way | ATM, MDM2 | `kMDM2phos` | internal-state conversion/modification | `MDM2(Site1~u) + ATM(state~6,h2ax!?)  -> MDM2(Site1~p) + ATM(state~6,h2ax!?)` | Transforms ATM, MDM2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 71 | `Unlabeled` | one-way | ATM, MDM2 | `kMDM2phos` | internal-state conversion/modification | `MDM2(Site1~u) + ATM(state~7,h2ax!?)  -> MDM2(Site1~p) + ATM(state~7,h2ax!?)` | Transforms ATM, MDM2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 72 | `Unlabeled` | one-way | ATM, MDM2 | `kMDM2phos` | internal-state conversion/modification | `MDM2(Site1~u) + ATM(state~8,h2ax!?)  -> MDM2(Site1~p) + ATM(state~8,h2ax!?)` | Transforms ATM, MDM2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 73 | `Unlabeled` | one-way | ATM, MDM2 | `kMDM2phos` | internal-state conversion/modification | `MDM2(Site1~u) + ATM(state~9,h2ax!?)  -> MDM2(Site1~p) + ATM(state~9,h2ax!?)` | Transforms ATM, MDM2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 74 | `Unlabeled` | one-way | ATM, MDM2 | `kMDM2phos` | internal-state conversion/modification | `MDM2(Site1~u) + ATM(state~10,h2ax!?)  -> MDM2(Site1~p) + ATM(state~10,h2ax!?)` | Transforms ATM, MDM2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 75 | `Unlabeled` | one-way | ATM, MDM2 | `kMDM2phos` | internal-state conversion/modification | `MDM2(Site1~u) + ATM(state~11,h2ax!?)  -> MDM2(Site1~p) + ATM(state~11,h2ax!?)` | Transforms ATM, MDM2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 76 | `Unlabeled` | one-way | ATM, MDM2 | `kMDM2phos` | internal-state conversion/modification | `MDM2(Site1~u) + ATM(state~12,h2ax!?)  -> MDM2(Site1~p) + ATM(state~12,h2ax!?)` | Transforms ATM, MDM2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 77 | `Unlabeled` | one-way | ATM, MDM2 | `kMDM2phos` | internal-state conversion/modification | `MDM2(Site1~u) + ATM(state~13,h2ax!?)  -> MDM2(Site1~p) + ATM(state~13,h2ax!?)` | Transforms ATM, MDM2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 78 | `Unlabeled` | one-way | ATM, MDM2 | `kMDM2phos` | internal-state conversion/modification | `MDM2(Site1~u) + ATM(state~14,h2ax!?)  -> MDM2(Site1~p) + ATM(state~14,h2ax!?)` | Transforms ATM, MDM2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 79 | `Unlabeled` | one-way | ATM, MDM2 | `kMDM2phos` | internal-state conversion/modification | `MDM2(Site1~u) + ATM(state~15,h2ax!?)  -> MDM2(Site1~p) + ATM(state~15,h2ax!?)` | Transforms ATM, MDM2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 80 | `Unlabeled` | one-way | ATM, MDM2 | `kMDM2phos` | internal-state conversion/modification | `MDM2(Site1~u) + ATM(state~16,h2ax!?)  -> MDM2(Site1~p) + ATM(state~16,h2ax!?)` | Transforms ATM, MDM2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 81 | `Unlabeled` | one-way | ATM, MDM2 | `kMDM2phos` | internal-state conversion/modification | `MDM2(Site1~u) + ATM(state~17,h2ax!?)  -> MDM2(Site1~p) + ATM(state~17,h2ax!?)` | Transforms ATM, MDM2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 82 | `Unlabeled` | one-way | ATM, MDM2 | `kMDM2phos` | internal-state conversion/modification | `MDM2(Site1~u) + ATM(state~18,h2ax!?)  -> MDM2(Site1~p) + ATM(state~18,h2ax!?)` | Transforms ATM, MDM2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 83 | `Unlabeled` | one-way | ATM, MDM2 | `kMDM2phos` | internal-state conversion/modification | `MDM2(Site1~u) + ATM(state~19,h2ax!?)  -> MDM2(Site1~p) + ATM(state~19,h2ax!?)` | Transforms ATM, MDM2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 84 | `Unlabeled` | one-way | ATM, MDM2 | `kMDM2phos` | internal-state conversion/modification | `MDM2(Site1~u) + ATM(state~20,h2ax!?)  -> MDM2(Site1~p) + ATM(state~20,h2ax!?)` | Transforms ATM, MDM2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 85 | `Unlabeled` | one-way | ATM, MDM2 | `kMDM2phos` | internal-state conversion/modification | `MDM2(Site1~u) + ATM(state~21,h2ax!?)  -> MDM2(Site1~p) + ATM(state~21,h2ax!?)` | Transforms ATM, MDM2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 86 | `Unlabeled` | one-way | ATM, MDM2 | `kMDM2phos` | internal-state conversion/modification | `MDM2(Site1~u) + ATM(state~22,h2ax!?)  -> MDM2(Site1~p) + ATM(state~22,h2ax!?)` | Transforms ATM, MDM2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 87 | `Unlabeled` | one-way | ATM, MDM2 | `kMDM2phos` | internal-state conversion/modification | `MDM2(Site1~u) + ATM(state~23,h2ax!?)  -> MDM2(Site1~p) + ATM(state~23,h2ax!?)` | Transforms ATM, MDM2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 88 | `Unlabeled` | one-way | ATM, MDM2 | `kMDM2phos` | internal-state conversion/modification | `MDM2(Site1~u) + ATM(state~24,h2ax!?)  -> MDM2(Site1~p) + ATM(state~24,h2ax!?)` | Transforms ATM, MDM2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 89 | `Unlabeled` | one-way | ATM, MDM2 | `kMDM2phos` | internal-state conversion/modification | `MDM2(Site1~u) + ATM(state~25,h2ax!?)  -> MDM2(Site1~p) + ATM(state~25,h2ax!?)` | Transforms ATM, MDM2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 90 | `Unlabeled` | one-way | ATM, MDM2 | `kMDM2phos` | internal-state conversion/modification | `MDM2(Site1~u) + ATM(state~26,h2ax!?)  -> MDM2(Site1~p) + ATM(state~26,h2ax!?)` | Transforms ATM, MDM2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 91 | `Unlabeled` | one-way | ATM, MDM2 | `kMDM2phos` | internal-state conversion/modification | `MDM2(Site1~u) + ATM(state~27,h2ax!?)  -> MDM2(Site1~p) + ATM(state~27,h2ax!?)` | Transforms ATM, MDM2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 92 | `Unlabeled` | one-way | ATM, MDM2 | `kMDM2phos` | internal-state conversion/modification | `MDM2(Site1~u) + ATM(state~28,h2ax!?)  -> MDM2(Site1~p) + ATM(state~28,h2ax!?)` | Transforms ATM, MDM2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 93 | `Unlabeled` | one-way | ATM, MDM2 | `kMDM2phos` | internal-state conversion/modification | `MDM2(Site1~u) + ATM(state~29,h2ax!?)  -> MDM2(Site1~p) + ATM(state~29,h2ax!?)` | Transforms ATM, MDM2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 94 | `Unlabeled` | one-way | ATM, MDM2 | `kMDM2phos` | internal-state conversion/modification | `MDM2(Site1~u) + ATM(state~30,h2ax!?)  -> MDM2(Site1~p) + ATM(state~30,h2ax!?)` | Transforms ATM, MDM2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 95 | `Unlabeled` | one-way | ATM, MDM2 | `kMDM2phos` | internal-state conversion/modification | `MDM2(Site1~u) + ATM(state~31,h2ax!?)  -> MDM2(Site1~p) + ATM(state~31,h2ax!?)` | Transforms ATM, MDM2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 96 | `Unlabeled` | one-way | ATM, MDM2 | `kMDM2phos` | internal-state conversion/modification | `MDM2(Site1~u) + ATM(state~32,h2ax!?)  -> MDM2(Site1~p) + ATM(state~32,h2ax!?)` | Transforms ATM, MDM2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 97 | `Unlabeled` | one-way | ATM, MDM2 | `kMDM2phos` | internal-state conversion/modification | `MDM2(Site1~u) + ATM(state~33,h2ax!?)  -> MDM2(Site1~p) + ATM(state~33,h2ax!?)` | Transforms ATM, MDM2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 98 | `Unlabeled` | one-way | ATM, MDM2 | `kMDM2phos` | internal-state conversion/modification | `MDM2(Site1~u) + ATM(state~34,h2ax!?)  -> MDM2(Site1~p) + ATM(state~34,h2ax!?)` | Transforms ATM, MDM2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 99 | `Unlabeled` | one-way | ATM, MDM2 | `kMDM2phos` | internal-state conversion/modification | `MDM2(Site1~u) + ATM(state~35,h2ax!?)  -> MDM2(Site1~p) + ATM(state~35,h2ax!?)` | Transforms ATM, MDM2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 100 | `Unlabeled` | one-way | ATM, MDM2 | `kMDM2phos` | internal-state conversion/modification | `MDM2(Site1~u) + ATM(state~36,h2ax!?)  -> MDM2(Site1~p) + ATM(state~36,h2ax!?)` | Transforms ATM, MDM2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 101 | `Unlabeled` | one-way | ATM, MDM2 | `kMDM2phos` | internal-state conversion/modification | `MDM2(Site1~u) + ATM(state~37,h2ax!?)  -> MDM2(Site1~p) + ATM(state~37,h2ax!?)` | Transforms ATM, MDM2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 102 | `Unlabeled` | one-way | ATM, MDM2 | `kMDM2phos` | internal-state conversion/modification | `MDM2(Site1~u) + ATM(state~38,h2ax!?)  -> MDM2(Site1~p) + ATM(state~38,h2ax!?)` | Transforms ATM, MDM2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 103 | `Unlabeled` | one-way | ATM, MDM2 | `kMDM2phos` | internal-state conversion/modification | `MDM2(Site1~u) + ATM(state~39,h2ax!?)  -> MDM2(Site1~p) + ATM(state~39,h2ax!?)` | Transforms ATM, MDM2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 104 | `Unlabeled` | one-way | ATM, MDM2 | `kMDM2phos` | internal-state conversion/modification | `MDM2(Site1~u) + ATM(state~40,h2ax!?)  -> MDM2(Site1~p) + ATM(state~40,h2ax!?)` | Transforms ATM, MDM2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 105 | `Unlabeled` | one-way | ATM, MDM2 | `kMDM2phos` | internal-state conversion/modification | `MDM2(Site1~u) + ATM(state~41,h2ax!?)  -> MDM2(Site1~p) + ATM(state~41,h2ax!?)` | Transforms ATM, MDM2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 106 | `Unlabeled` | one-way | ATM, MDM2 | `kMDM2phos` | internal-state conversion/modification | `MDM2(Site1~u) + ATM(state~42,h2ax!?)  -> MDM2(Site1~p) + ATM(state~42,h2ax!?)` | Transforms ATM, MDM2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 107 | `Unlabeled` | one-way | ATM, MDM2 | `kMDM2phos` | internal-state conversion/modification | `MDM2(Site1~u) + ATM(state~43,h2ax!?)  -> MDM2(Site1~p) + ATM(state~43,h2ax!?)` | Transforms ATM, MDM2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 108 | `Unlabeled` | one-way | ATM, MDM2 | `kMDM2phos` | internal-state conversion/modification | `MDM2(Site1~u) + ATM(state~44,h2ax!?)  -> MDM2(Site1~p) + ATM(state~44,h2ax!?)` | Transforms ATM, MDM2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 109 | `Unlabeled` | one-way | ATM, MDM2 | `kMDM2phos` | internal-state conversion/modification | `MDM2(Site1~u) + ATM(state~45,h2ax!?)  -> MDM2(Site1~p) + ATM(state~45,h2ax!?)` | Transforms ATM, MDM2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 110 | `Unlabeled` | one-way | ATM, MDM2 | `kMDM2phos` | internal-state conversion/modification | `MDM2(Site1~u) + ATM(state~46,h2ax!?)  -> MDM2(Site1~p) + ATM(state~46,h2ax!?)` | Transforms ATM, MDM2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 111 | `Unlabeled` | one-way | ATM, MDM2 | `kMDM2phos` | internal-state conversion/modification | `MDM2(Site1~u) + ATM(state~47,h2ax!?)  -> MDM2(Site1~p) + ATM(state~47,h2ax!?)` | Transforms ATM, MDM2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 112 | `Unlabeled` | one-way | ATM, MDM2 | `kMDM2phos` | internal-state conversion/modification | `MDM2(Site1~u) + ATM(state~48,h2ax!?)  -> MDM2(Site1~p) + ATM(state~48,h2ax!?)` | Transforms ATM, MDM2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 113 | `Unlabeled` | one-way | ATM, MDM2 | `kMDM2phos` | internal-state conversion/modification | `MDM2(Site1~u) + ATM(state~49,h2ax!?)  -> MDM2(Site1~p) + ATM(state~49,h2ax!?)` | Transforms ATM, MDM2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 114 | `Unlabeled` | one-way | ATM, MDM2 | `kMDM2phos` | internal-state conversion/modification | `MDM2(Site1~u) + ATM(state~50,h2ax!?)  -> MDM2(Site1~p) + ATM(state~50,h2ax!?)` | Transforms ATM, MDM2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 115 | `Unlabeled` | one-way | MDM2 | `kMDM2dphos` | internal-state conversion/modification | `MDM2(Site1~p)  -> MDM2(Site1~u)` | Transforms MDM2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 116 | `Unlabeled` | one-way | MDM2, p53 | `kp53MDM2bind` | state and binding-pattern rewrite | `p53(Site1~u) + MDM2(Site1~u)  -> p53(Site1!1~u).MDM2(Site1!1~u)` | Transforms MDM2, p53 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 117 | `Unlabeled` | one-way | MDM2, p53 | `kp53MDM2dis` | state and binding-pattern rewrite | `p53(Site1!1~u).MDM2(Site1!1~u)  -> p53(Site1~u) + MDM2(Site1~u)` | Transforms MDM2, p53 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 118 | `Unlabeled` | one-way | p21_mRNA, p53 | `kp21mRNAsyn` | internal-state conversion/modification | `p53(Site1~u)  -> p21_mRNA() + p53(Site1~u)` | Transforms p21_mRNA, p53 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 119 | `Unlabeled` | one-way | p21_mRNA, p53 | `kp21mRNAsynp` | internal-state conversion/modification | `p53(Site1~p)  -> p21_mRNA() + p53(Site1~p)` | Transforms p21_mRNA, p53 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 120 | `Unlabeled` | one-way | Sink, p21_mRNA | `kp21mRNAdeg` | sink/degradation/removal | `p21_mRNA()  -> Sink()` | Transforms Sink, p21_mRNA by sink/degradation/removal; see the exact pattern for affected sites/states/bonds. |

| 121 | `Unlabeled` | one-way | p21, p21_mRNA | `kp21synstep1` | internal-state conversion/modification | `p21_mRNA()  -> p21(step~1) + p21_mRNA()` | Transforms p21, p21_mRNA by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 122 | `Unlabeled` | one-way | p21 | `kp21synstep2` | internal-state conversion/modification | `p21(step~1)  -> p21(step~2)` | Transforms p21 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 123 | `Unlabeled` | one-way | p21 | `kp21synstep3` | internal-state conversion/modification | `p21(step~2)  -> p21(step~3)` | Transforms p21 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 124 | `Unlabeled` | one-way | Sink, p21 | `kp21deg` | sink/degradation/removal | `p21(step~3)  -> Sink()` | Transforms Sink, p21 by sink/degradation/removal; see the exact pattern for affected sites/states/bonds. |

| 125 | `Unlabeled` | one-way | GADD45, p21 | `kGADD45act` | internal-state conversion/modification | `p21(step~3)  -> p21(step~3) + GADD45()` | Transforms GADD45, p21 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 126 | `Unlabeled` | one-way | GADD45, Sink | `kGADD45deg` | sink/degradation/removal | `GADD45()  -> Sink()` | Transforms GADD45, Sink by sink/degradation/removal; see the exact pattern for affected sites/states/bonds. |

| 127 | `Unlabeled` | one-way | GADD45, p38 | `kp38phos` | internal-state conversion/modification | `p38(Site1~u) + GADD45()  -> p38(Site1~p) + GADD45()` | Transforms GADD45, p38 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 128 | `Unlabeled` | one-way | p38 | `kp38dphos` | internal-state conversion/modification | `p38(Site1~p)  -> p38(Site1~u)` | Transforms p38 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 129 | `Unlabeled` | one-way | ROS, p38 | `kROSgen` | internal-state conversion/modification | `p38(Site1~p)  -> ROS() + p38(Site1~p)` | *kpROSp38 |

| 130 | `Unlabeled` | one-way | DNA1, Ku | `kku1()` | state and binding-pattern rewrite | `DNA1(site~sdsb) + Ku(dna,cs)  -> DNA1(site!1~sdsb).Ku(dna!1,cs)` | Transforms DNA1, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 131 | `Unlabeled` | one-way | DNA2, Ku | `kku1()` | state and binding-pattern rewrite | `DNA2(site~sdsb) + Ku(dna,cs)  -> DNA2(site!1~sdsb).Ku(dna!1,cs)` | Transforms DNA2, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 132 | `Unlabeled` | one-way | DNA3, Ku | `kku1()` | state and binding-pattern rewrite | `DNA3(site~sdsb) + Ku(dna,cs)  -> DNA3(site!1~sdsb).Ku(dna!1,cs)` | Transforms DNA3, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 133 | `Unlabeled` | one-way | DNA4, Ku | `kku1()` | state and binding-pattern rewrite | `DNA4(site~sdsb) + Ku(dna,cs)  -> DNA4(site!1~sdsb).Ku(dna!1,cs)` | Transforms DNA4, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 134 | `Unlabeled` | one-way | DNA5, Ku | `kku1()` | state and binding-pattern rewrite | `DNA5(site~sdsb) + Ku(dna,cs)  -> DNA5(site!1~sdsb).Ku(dna!1,cs)` | Transforms DNA5, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 135 | `Unlabeled` | one-way | DNA6, Ku | `kku1()` | state and binding-pattern rewrite | `DNA6(site~sdsb) + Ku(dna,cs)  -> DNA6(site!1~sdsb).Ku(dna!1,cs)` | Transforms DNA6, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 136 | `Unlabeled` | one-way | DNA7, Ku | `kku1()` | state and binding-pattern rewrite | `DNA7(site~sdsb) + Ku(dna,cs)  -> DNA7(site!1~sdsb).Ku(dna!1,cs)` | Transforms DNA7, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 137 | `Unlabeled` | one-way | DNA8, Ku | `kku1()` | state and binding-pattern rewrite | `DNA8(site~sdsb) + Ku(dna,cs)  -> DNA8(site!1~sdsb).Ku(dna!1,cs)` | Transforms DNA8, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 138 | `Unlabeled` | one-way | DNA9, Ku | `kku1()` | state and binding-pattern rewrite | `DNA9(site~sdsb) + Ku(dna,cs)  -> DNA9(site!1~sdsb).Ku(dna!1,cs)` | Transforms DNA9, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 139 | `Unlabeled` | one-way | DNA10, Ku | `kku1()` | state and binding-pattern rewrite | `DNA10(site~sdsb) + Ku(dna,cs)  -> DNA10(site!1~sdsb).Ku(dna!1,cs)` | Transforms DNA10, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 140 | `Unlabeled` | one-way | DNA11, Ku | `kku1()` | state and binding-pattern rewrite | `DNA11(site~sdsb) + Ku(dna,cs)  -> DNA11(site!1~sdsb).Ku(dna!1,cs)` | Transforms DNA11, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 141 | `Unlabeled` | one-way | DNA12, Ku | `kku1()` | state and binding-pattern rewrite | `DNA12(site~sdsb) + Ku(dna,cs)  -> DNA12(site!1~sdsb).Ku(dna!1,cs)` | Transforms DNA12, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 142 | `Unlabeled` | one-way | DNA13, Ku | `kku1()` | state and binding-pattern rewrite | `DNA13(site~sdsb) + Ku(dna,cs)  -> DNA13(site!1~sdsb).Ku(dna!1,cs)` | Transforms DNA13, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 143 | `Unlabeled` | one-way | DNA14, Ku | `kku1()` | state and binding-pattern rewrite | `DNA14(site~sdsb) + Ku(dna,cs)  -> DNA14(site!1~sdsb).Ku(dna!1,cs)` | Transforms DNA14, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 144 | `Unlabeled` | one-way | DNA15, Ku | `kku1()` | state and binding-pattern rewrite | `DNA15(site~sdsb) + Ku(dna,cs)  -> DNA15(site!1~sdsb).Ku(dna!1,cs)` | Transforms DNA15, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 145 | `Unlabeled` | one-way | DNA16, Ku | `kku1()` | state and binding-pattern rewrite | `DNA16(site~sdsb) + Ku(dna,cs)  -> DNA16(site!1~sdsb).Ku(dna!1,cs)` | Transforms DNA16, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 146 | `Unlabeled` | one-way | DNA17, Ku | `kku1()` | state and binding-pattern rewrite | `DNA17(site~sdsb) + Ku(dna,cs)  -> DNA17(site!1~sdsb).Ku(dna!1,cs)` | Transforms DNA17, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 147 | `Unlabeled` | one-way | DNA18, Ku | `kku1()` | state and binding-pattern rewrite | `DNA18(site~sdsb) + Ku(dna,cs)  -> DNA18(site!1~sdsb).Ku(dna!1,cs)` | Transforms DNA18, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 148 | `Unlabeled` | one-way | DNA19, Ku | `kku1()` | state and binding-pattern rewrite | `DNA19(site~sdsb) + Ku(dna,cs)  -> DNA19(site!1~sdsb).Ku(dna!1,cs)` | Transforms DNA19, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 149 | `Unlabeled` | one-way | DNA20, Ku | `kku1()` | state and binding-pattern rewrite | `DNA20(site~sdsb) + Ku(dna,cs)  -> DNA20(site!1~sdsb).Ku(dna!1,cs)` | Transforms DNA20, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 150 | `Unlabeled` | one-way | DNA21, Ku | `kku1()` | state and binding-pattern rewrite | `DNA21(site~sdsb) + Ku(dna,cs)  -> DNA21(site!1~sdsb).Ku(dna!1,cs)` | Transforms DNA21, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 151 | `Unlabeled` | one-way | DNA22, Ku | `kku1()` | state and binding-pattern rewrite | `DNA22(site~sdsb) + Ku(dna,cs)  -> DNA22(site!1~sdsb).Ku(dna!1,cs)` | Transforms DNA22, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 152 | `Unlabeled` | one-way | DNA23, Ku | `kku1()` | state and binding-pattern rewrite | `DNA23(site~sdsb) + Ku(dna,cs)  -> DNA23(site!1~sdsb).Ku(dna!1,cs)` | Transforms DNA23, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 153 | `Unlabeled` | one-way | DNA24, Ku | `kku1()` | state and binding-pattern rewrite | `DNA24(site~sdsb) + Ku(dna,cs)  -> DNA24(site!1~sdsb).Ku(dna!1,cs)` | Transforms DNA24, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 154 | `Unlabeled` | one-way | DNA25, Ku | `kku1()` | state and binding-pattern rewrite | `DNA25(site~sdsb) + Ku(dna,cs)  -> DNA25(site!1~sdsb).Ku(dna!1,cs)` | Transforms DNA25, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 155 | `Unlabeled` | one-way | DNA26, Ku | `kku1()` | state and binding-pattern rewrite | `DNA26(site~sdsb) + Ku(dna,cs)  -> DNA26(site!1~sdsb).Ku(dna!1,cs)` | Transforms DNA26, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 156 | `Unlabeled` | one-way | DNA27, Ku | `kku1()` | state and binding-pattern rewrite | `DNA27(site~sdsb) + Ku(dna,cs)  -> DNA27(site!1~sdsb).Ku(dna!1,cs)` | Transforms DNA27, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 157 | `Unlabeled` | one-way | DNA28, Ku | `kku1()` | state and binding-pattern rewrite | `DNA28(site~sdsb) + Ku(dna,cs)  -> DNA28(site!1~sdsb).Ku(dna!1,cs)` | Transforms DNA28, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 158 | `Unlabeled` | one-way | DNA29, Ku | `kku1()` | state and binding-pattern rewrite | `DNA29(site~sdsb) + Ku(dna,cs)  -> DNA29(site!1~sdsb).Ku(dna!1,cs)` | Transforms DNA29, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 159 | `Unlabeled` | one-way | DNA30, Ku | `kku1()` | state and binding-pattern rewrite | `DNA30(site~sdsb) + Ku(dna,cs)  -> DNA30(site!1~sdsb).Ku(dna!1,cs)` | Transforms DNA30, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 160 | `Unlabeled` | one-way | DNA31, Ku | `kku1()` | state and binding-pattern rewrite | `DNA31(site~sdsb) + Ku(dna,cs)  -> DNA31(site!1~sdsb).Ku(dna!1,cs)` | Transforms DNA31, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 161 | `Unlabeled` | one-way | DNA32, Ku | `kku1()` | state and binding-pattern rewrite | `DNA32(site~sdsb) + Ku(dna,cs)  -> DNA32(site!1~sdsb).Ku(dna!1,cs)` | Transforms DNA32, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 162 | `Unlabeled` | one-way | DNA33, Ku | `kku1()` | state and binding-pattern rewrite | `DNA33(site~sdsb) + Ku(dna,cs)  -> DNA33(site!1~sdsb).Ku(dna!1,cs)` | Transforms DNA33, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 163 | `Unlabeled` | one-way | DNA34, Ku | `kku1()` | state and binding-pattern rewrite | `DNA34(site~sdsb) + Ku(dna,cs)  -> DNA34(site!1~sdsb).Ku(dna!1,cs)` | Transforms DNA34, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 164 | `Unlabeled` | one-way | DNA35, Ku | `kku1()` | state and binding-pattern rewrite | `DNA35(site~sdsb) + Ku(dna,cs)  -> DNA35(site!1~sdsb).Ku(dna!1,cs)` | Transforms DNA35, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 165 | `Unlabeled` | one-way | DNA36, Ku | `kku1()` | state and binding-pattern rewrite | `DNA36(site~sdsb) + Ku(dna,cs)  -> DNA36(site!1~sdsb).Ku(dna!1,cs)` | Transforms DNA36, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 166 | `Unlabeled` | one-way | DNA37, Ku | `kku1()` | state and binding-pattern rewrite | `DNA37(site~sdsb) + Ku(dna,cs)  -> DNA37(site!1~sdsb).Ku(dna!1,cs)` | Transforms DNA37, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 167 | `Unlabeled` | one-way | DNA38, Ku | `kku1()` | state and binding-pattern rewrite | `DNA38(site~sdsb) + Ku(dna,cs)  -> DNA38(site!1~sdsb).Ku(dna!1,cs)` | Transforms DNA38, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 168 | `Unlabeled` | one-way | DNA39, Ku | `kku1()` | state and binding-pattern rewrite | `DNA39(site~sdsb) + Ku(dna,cs)  -> DNA39(site!1~sdsb).Ku(dna!1,cs)` | Transforms DNA39, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 169 | `Unlabeled` | one-way | DNA40, Ku | `kku1()` | state and binding-pattern rewrite | `DNA40(site~sdsb) + Ku(dna,cs)  -> DNA40(site!1~sdsb).Ku(dna!1,cs)` | Transforms DNA40, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 170 | `Unlabeled` | one-way | DNA41, Ku | `kku1()` | state and binding-pattern rewrite | `DNA41(site~sdsb) + Ku(dna,cs)  -> DNA41(site!1~sdsb).Ku(dna!1,cs)` | Transforms DNA41, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 171 | `Unlabeled` | one-way | DNA42, Ku | `kku1()` | state and binding-pattern rewrite | `DNA42(site~sdsb) + Ku(dna,cs)  -> DNA42(site!1~sdsb).Ku(dna!1,cs)` | Transforms DNA42, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 172 | `Unlabeled` | one-way | DNA43, Ku | `kku1()` | state and binding-pattern rewrite | `DNA43(site~sdsb) + Ku(dna,cs)  -> DNA43(site!1~sdsb).Ku(dna!1,cs)` | Transforms DNA43, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 173 | `Unlabeled` | one-way | DNA44, Ku | `kku1()` | state and binding-pattern rewrite | `DNA44(site~sdsb) + Ku(dna,cs)  -> DNA44(site!1~sdsb).Ku(dna!1,cs)` | Transforms DNA44, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 174 | `Unlabeled` | one-way | DNA45, Ku | `kku1()` | state and binding-pattern rewrite | `DNA45(site~sdsb) + Ku(dna,cs)  -> DNA45(site!1~sdsb).Ku(dna!1,cs)` | Transforms DNA45, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 175 | `Unlabeled` | one-way | DNA46, Ku | `kku1()` | state and binding-pattern rewrite | `DNA46(site~sdsb) + Ku(dna,cs)  -> DNA46(site!1~sdsb).Ku(dna!1,cs)` | Transforms DNA46, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 176 | `Unlabeled` | one-way | DNA47, Ku | `kku1()` | state and binding-pattern rewrite | `DNA47(site~sdsb) + Ku(dna,cs)  -> DNA47(site!1~sdsb).Ku(dna!1,cs)` | Transforms DNA47, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 177 | `Unlabeled` | one-way | DNA48, Ku | `kku1()` | state and binding-pattern rewrite | `DNA48(site~sdsb) + Ku(dna,cs)  -> DNA48(site!1~sdsb).Ku(dna!1,cs)` | Transforms DNA48, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 178 | `Unlabeled` | one-way | DNA49, Ku | `kku1()` | state and binding-pattern rewrite | `DNA49(site~sdsb) + Ku(dna,cs)  -> DNA49(site!1~sdsb).Ku(dna!1,cs)` | Transforms DNA49, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 179 | `Unlabeled` | one-way | DNA50, Ku | `kku1()` | state and binding-pattern rewrite | `DNA50(site~sdsb) + Ku(dna,cs)  -> DNA50(site!1~sdsb).Ku(dna!1,cs)` | Transforms DNA50, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 180 | `Unlabeled` | one-way | DNA1, Ku | `kku2()` | state and binding-pattern rewrite | `DNA1(site~cdsb) + Ku(dna,cs)  -> DNA1(site!1~cdsb).Ku(dna!1,cs)` | Transforms DNA1, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 181 | `Unlabeled` | one-way | DNA2, Ku | `kku2()` | state and binding-pattern rewrite | `DNA2(site~cdsb) + Ku(dna,cs)  -> DNA2(site!1~cdsb).Ku(dna!1,cs)` | Transforms DNA2, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 182 | `Unlabeled` | one-way | DNA3, Ku | `kku2()` | state and binding-pattern rewrite | `DNA3(site~cdsb) + Ku(dna,cs)  -> DNA3(site!1~cdsb).Ku(dna!1,cs)` | Transforms DNA3, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 183 | `Unlabeled` | one-way | DNA4, Ku | `kku2()` | state and binding-pattern rewrite | `DNA4(site~cdsb) + Ku(dna,cs)  -> DNA4(site!1~cdsb).Ku(dna!1,cs)` | Transforms DNA4, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 184 | `Unlabeled` | one-way | DNA5, Ku | `kku2()` | state and binding-pattern rewrite | `DNA5(site~cdsb) + Ku(dna,cs)  -> DNA5(site!1~cdsb).Ku(dna!1,cs)` | Transforms DNA5, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 185 | `Unlabeled` | one-way | DNA6, Ku | `kku2()` | state and binding-pattern rewrite | `DNA6(site~cdsb) + Ku(dna,cs)  -> DNA6(site!1~cdsb).Ku(dna!1,cs)` | Transforms DNA6, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 186 | `Unlabeled` | one-way | DNA7, Ku | `kku2()` | state and binding-pattern rewrite | `DNA7(site~cdsb) + Ku(dna,cs)  -> DNA7(site!1~cdsb).Ku(dna!1,cs)` | Transforms DNA7, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 187 | `Unlabeled` | one-way | DNA8, Ku | `kku2()` | state and binding-pattern rewrite | `DNA8(site~cdsb) + Ku(dna,cs)  -> DNA8(site!1~cdsb).Ku(dna!1,cs)` | Transforms DNA8, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 188 | `Unlabeled` | one-way | DNA9, Ku | `kku2()` | state and binding-pattern rewrite | `DNA9(site~cdsb) + Ku(dna,cs)  -> DNA9(site!1~cdsb).Ku(dna!1,cs)` | Transforms DNA9, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 189 | `Unlabeled` | one-way | DNA10, Ku | `kku2()` | state and binding-pattern rewrite | `DNA10(site~cdsb) + Ku(dna,cs)  -> DNA10(site!1~cdsb).Ku(dna!1,cs)` | Transforms DNA10, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 190 | `Unlabeled` | one-way | DNA11, Ku | `kku2()` | state and binding-pattern rewrite | `DNA11(site~cdsb) + Ku(dna,cs)  -> DNA11(site!1~cdsb).Ku(dna!1,cs)` | Transforms DNA11, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 191 | `Unlabeled` | one-way | DNA12, Ku | `kku2()` | state and binding-pattern rewrite | `DNA12(site~cdsb) + Ku(dna,cs)  -> DNA12(site!1~cdsb).Ku(dna!1,cs)` | Transforms DNA12, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 192 | `Unlabeled` | one-way | DNA13, Ku | `kku2()` | state and binding-pattern rewrite | `DNA13(site~cdsb) + Ku(dna,cs)  -> DNA13(site!1~cdsb).Ku(dna!1,cs)` | Transforms DNA13, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 193 | `Unlabeled` | one-way | DNA14, Ku | `kku2()` | state and binding-pattern rewrite | `DNA14(site~cdsb) + Ku(dna,cs)  -> DNA14(site!1~cdsb).Ku(dna!1,cs)` | Transforms DNA14, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 194 | `Unlabeled` | one-way | DNA15, Ku | `kku2()` | state and binding-pattern rewrite | `DNA15(site~cdsb) + Ku(dna,cs)  -> DNA15(site!1~cdsb).Ku(dna!1,cs)` | Transforms DNA15, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 195 | `Unlabeled` | one-way | DNA16, Ku | `kku2()` | state and binding-pattern rewrite | `DNA16(site~cdsb) + Ku(dna,cs)  -> DNA16(site!1~cdsb).Ku(dna!1,cs)` | Transforms DNA16, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 196 | `Unlabeled` | one-way | DNA17, Ku | `kku2()` | state and binding-pattern rewrite | `DNA17(site~cdsb) + Ku(dna,cs)  -> DNA17(site!1~cdsb).Ku(dna!1,cs)` | Transforms DNA17, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 197 | `Unlabeled` | one-way | DNA18, Ku | `kku2()` | state and binding-pattern rewrite | `DNA18(site~cdsb) + Ku(dna,cs)  -> DNA18(site!1~cdsb).Ku(dna!1,cs)` | Transforms DNA18, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 198 | `Unlabeled` | one-way | DNA19, Ku | `kku2()` | state and binding-pattern rewrite | `DNA19(site~cdsb) + Ku(dna,cs)  -> DNA19(site!1~cdsb).Ku(dna!1,cs)` | Transforms DNA19, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 199 | `Unlabeled` | one-way | DNA20, Ku | `kku2()` | state and binding-pattern rewrite | `DNA20(site~cdsb) + Ku(dna,cs)  -> DNA20(site!1~cdsb).Ku(dna!1,cs)` | Transforms DNA20, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 200 | `Unlabeled` | one-way | DNA21, Ku | `kku2()` | state and binding-pattern rewrite | `DNA21(site~cdsb) + Ku(dna,cs)  -> DNA21(site!1~cdsb).Ku(dna!1,cs)` | Transforms DNA21, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 201 | `Unlabeled` | one-way | DNA22, Ku | `kku2()` | state and binding-pattern rewrite | `DNA22(site~cdsb) + Ku(dna,cs)  -> DNA22(site!1~cdsb).Ku(dna!1,cs)` | Transforms DNA22, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 202 | `Unlabeled` | one-way | DNA23, Ku | `kku2()` | state and binding-pattern rewrite | `DNA23(site~cdsb) + Ku(dna,cs)  -> DNA23(site!1~cdsb).Ku(dna!1,cs)` | Transforms DNA23, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 203 | `Unlabeled` | one-way | DNA24, Ku | `kku2()` | state and binding-pattern rewrite | `DNA24(site~cdsb) + Ku(dna,cs)  -> DNA24(site!1~cdsb).Ku(dna!1,cs)` | Transforms DNA24, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 204 | `Unlabeled` | one-way | DNA25, Ku | `kku2()` | state and binding-pattern rewrite | `DNA25(site~cdsb) + Ku(dna,cs)  -> DNA25(site!1~cdsb).Ku(dna!1,cs)` | Transforms DNA25, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 205 | `Unlabeled` | one-way | DNA26, Ku | `kku2()` | state and binding-pattern rewrite | `DNA26(site~cdsb) + Ku(dna,cs)  -> DNA26(site!1~cdsb).Ku(dna!1,cs)` | Transforms DNA26, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 206 | `Unlabeled` | one-way | DNA27, Ku | `kku2()` | state and binding-pattern rewrite | `DNA27(site~cdsb) + Ku(dna,cs)  -> DNA27(site!1~cdsb).Ku(dna!1,cs)` | Transforms DNA27, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 207 | `Unlabeled` | one-way | DNA28, Ku | `kku2()` | state and binding-pattern rewrite | `DNA28(site~cdsb) + Ku(dna,cs)  -> DNA28(site!1~cdsb).Ku(dna!1,cs)` | Transforms DNA28, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 208 | `Unlabeled` | one-way | DNA29, Ku | `kku2()` | state and binding-pattern rewrite | `DNA29(site~cdsb) + Ku(dna,cs)  -> DNA29(site!1~cdsb).Ku(dna!1,cs)` | Transforms DNA29, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 209 | `Unlabeled` | one-way | DNA30, Ku | `kku2()` | state and binding-pattern rewrite | `DNA30(site~cdsb) + Ku(dna,cs)  -> DNA30(site!1~cdsb).Ku(dna!1,cs)` | Transforms DNA30, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 210 | `Unlabeled` | one-way | DNA31, Ku | `kku2()` | state and binding-pattern rewrite | `DNA31(site~cdsb) + Ku(dna,cs)  -> DNA31(site!1~cdsb).Ku(dna!1,cs)` | Transforms DNA31, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 211 | `Unlabeled` | one-way | DNA32, Ku | `kku2()` | state and binding-pattern rewrite | `DNA32(site~cdsb) + Ku(dna,cs)  -> DNA32(site!1~cdsb).Ku(dna!1,cs)` | Transforms DNA32, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 212 | `Unlabeled` | one-way | DNA33, Ku | `kku2()` | state and binding-pattern rewrite | `DNA33(site~cdsb) + Ku(dna,cs)  -> DNA33(site!1~cdsb).Ku(dna!1,cs)` | Transforms DNA33, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 213 | `Unlabeled` | one-way | DNA34, Ku | `kku2()` | state and binding-pattern rewrite | `DNA34(site~cdsb) + Ku(dna,cs)  -> DNA34(site!1~cdsb).Ku(dna!1,cs)` | Transforms DNA34, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 214 | `Unlabeled` | one-way | DNA35, Ku | `kku2()` | state and binding-pattern rewrite | `DNA35(site~cdsb) + Ku(dna,cs)  -> DNA35(site!1~cdsb).Ku(dna!1,cs)` | Transforms DNA35, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 215 | `Unlabeled` | one-way | DNA36, Ku | `kku2()` | state and binding-pattern rewrite | `DNA36(site~cdsb) + Ku(dna,cs)  -> DNA36(site!1~cdsb).Ku(dna!1,cs)` | Transforms DNA36, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 216 | `Unlabeled` | one-way | DNA37, Ku | `kku2()` | state and binding-pattern rewrite | `DNA37(site~cdsb) + Ku(dna,cs)  -> DNA37(site!1~cdsb).Ku(dna!1,cs)` | Transforms DNA37, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 217 | `Unlabeled` | one-way | DNA38, Ku | `kku2()` | state and binding-pattern rewrite | `DNA38(site~cdsb) + Ku(dna,cs)  -> DNA38(site!1~cdsb).Ku(dna!1,cs)` | Transforms DNA38, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 218 | `Unlabeled` | one-way | DNA39, Ku | `kku2()` | state and binding-pattern rewrite | `DNA39(site~cdsb) + Ku(dna,cs)  -> DNA39(site!1~cdsb).Ku(dna!1,cs)` | Transforms DNA39, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 219 | `Unlabeled` | one-way | DNA40, Ku | `kku2()` | state and binding-pattern rewrite | `DNA40(site~cdsb) + Ku(dna,cs)  -> DNA40(site!1~cdsb).Ku(dna!1,cs)` | Transforms DNA40, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 220 | `Unlabeled` | one-way | DNA41, Ku | `kku2()` | state and binding-pattern rewrite | `DNA41(site~cdsb) + Ku(dna,cs)  -> DNA41(site!1~cdsb).Ku(dna!1,cs)` | Transforms DNA41, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 221 | `Unlabeled` | one-way | DNA42, Ku | `kku2()` | state and binding-pattern rewrite | `DNA42(site~cdsb) + Ku(dna,cs)  -> DNA42(site!1~cdsb).Ku(dna!1,cs)` | Transforms DNA42, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 222 | `Unlabeled` | one-way | DNA43, Ku | `kku2()` | state and binding-pattern rewrite | `DNA43(site~cdsb) + Ku(dna,cs)  -> DNA43(site!1~cdsb).Ku(dna!1,cs)` | Transforms DNA43, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 223 | `Unlabeled` | one-way | DNA44, Ku | `kku2()` | state and binding-pattern rewrite | `DNA44(site~cdsb) + Ku(dna,cs)  -> DNA44(site!1~cdsb).Ku(dna!1,cs)` | Transforms DNA44, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 224 | `Unlabeled` | one-way | DNA45, Ku | `kku2()` | state and binding-pattern rewrite | `DNA45(site~cdsb) + Ku(dna,cs)  -> DNA45(site!1~cdsb).Ku(dna!1,cs)` | Transforms DNA45, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 225 | `Unlabeled` | one-way | DNA46, Ku | `kku2()` | state and binding-pattern rewrite | `DNA46(site~cdsb) + Ku(dna,cs)  -> DNA46(site!1~cdsb).Ku(dna!1,cs)` | Transforms DNA46, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 226 | `Unlabeled` | one-way | DNA47, Ku | `kku2()` | state and binding-pattern rewrite | `DNA47(site~cdsb) + Ku(dna,cs)  -> DNA47(site!1~cdsb).Ku(dna!1,cs)` | Transforms DNA47, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 227 | `Unlabeled` | one-way | DNA48, Ku | `kku2()` | state and binding-pattern rewrite | `DNA48(site~cdsb) + Ku(dna,cs)  -> DNA48(site!1~cdsb).Ku(dna!1,cs)` | Transforms DNA48, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 228 | `Unlabeled` | one-way | DNA49, Ku | `kku2()` | state and binding-pattern rewrite | `DNA49(site~cdsb) + Ku(dna,cs)  -> DNA49(site!1~cdsb).Ku(dna!1,cs)` | Transforms DNA49, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 229 | `Unlabeled` | one-way | DNA50, Ku | `kku2()` | state and binding-pattern rewrite | `DNA50(site~cdsb) + Ku(dna,cs)  -> DNA50(site!1~cdsb).Ku(dna!1,cs)` | Transforms DNA50, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 230 | `Unlabeled` | one-way | DNA1, Ku | `kdku1` | state and binding-pattern rewrite | `DNA1(site!1~sdsb).Ku(dna!1,cs,cys~red)  -> DNA1(site~sdsb) + Ku(dna,cs,cys~red)` | Transforms DNA1, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 231 | `Unlabeled` | one-way | DNA2, Ku | `kdku1` | state and binding-pattern rewrite | `DNA2(site!1~sdsb).Ku(dna!1,cs,cys~red)  -> DNA2(site~sdsb) + Ku(dna,cs,cys~red)` | Transforms DNA2, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 232 | `Unlabeled` | one-way | DNA3, Ku | `kdku1` | state and binding-pattern rewrite | `DNA3(site!1~sdsb).Ku(dna!1,cs,cys~red)  -> DNA3(site~sdsb) + Ku(dna,cs,cys~red)` | Transforms DNA3, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 233 | `Unlabeled` | one-way | DNA4, Ku | `kdku1` | state and binding-pattern rewrite | `DNA4(site!1~sdsb).Ku(dna!1,cs,cys~red)  -> DNA4(site~sdsb) + Ku(dna,cs,cys~red)` | Transforms DNA4, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 234 | `Unlabeled` | one-way | DNA5, Ku | `kdku1` | state and binding-pattern rewrite | `DNA5(site!1~sdsb).Ku(dna!1,cs,cys~red)  -> DNA5(site~sdsb) + Ku(dna,cs,cys~red)` | Transforms DNA5, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 235 | `Unlabeled` | one-way | DNA6, Ku | `kdku1` | state and binding-pattern rewrite | `DNA6(site!1~sdsb).Ku(dna!1,cs,cys~red)  -> DNA6(site~sdsb) + Ku(dna,cs,cys~red)` | Transforms DNA6, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 236 | `Unlabeled` | one-way | DNA7, Ku | `kdku1` | state and binding-pattern rewrite | `DNA7(site!1~sdsb).Ku(dna!1,cs,cys~red)  -> DNA7(site~sdsb) + Ku(dna,cs,cys~red)` | Transforms DNA7, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 237 | `Unlabeled` | one-way | DNA8, Ku | `kdku1` | state and binding-pattern rewrite | `DNA8(site!1~sdsb).Ku(dna!1,cs,cys~red)  -> DNA8(site~sdsb) + Ku(dna,cs,cys~red)` | Transforms DNA8, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 238 | `Unlabeled` | one-way | DNA9, Ku | `kdku1` | state and binding-pattern rewrite | `DNA9(site!1~sdsb).Ku(dna!1,cs,cys~red)  -> DNA9(site~sdsb) + Ku(dna,cs,cys~red)` | Transforms DNA9, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 239 | `Unlabeled` | one-way | DNA10, Ku | `kdku1` | state and binding-pattern rewrite | `DNA10(site!1~sdsb).Ku(dna!1,cs,cys~red)  -> DNA10(site~sdsb) + Ku(dna,cs,cys~red)` | Transforms DNA10, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 240 | `Unlabeled` | one-way | DNA11, Ku | `kdku1` | state and binding-pattern rewrite | `DNA11(site!1~sdsb).Ku(dna!1,cs,cys~red)  -> DNA11(site~sdsb) + Ku(dna,cs,cys~red)` | Transforms DNA11, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 241 | `Unlabeled` | one-way | DNA12, Ku | `kdku1` | state and binding-pattern rewrite | `DNA12(site!1~sdsb).Ku(dna!1,cs,cys~red)  -> DNA12(site~sdsb) + Ku(dna,cs,cys~red)` | Transforms DNA12, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 242 | `Unlabeled` | one-way | DNA13, Ku | `kdku1` | state and binding-pattern rewrite | `DNA13(site!1~sdsb).Ku(dna!1,cs,cys~red)  -> DNA13(site~sdsb) + Ku(dna,cs,cys~red)` | Transforms DNA13, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 243 | `Unlabeled` | one-way | DNA14, Ku | `kdku1` | state and binding-pattern rewrite | `DNA14(site!1~sdsb).Ku(dna!1,cs,cys~red)  -> DNA14(site~sdsb) + Ku(dna,cs,cys~red)` | Transforms DNA14, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 244 | `Unlabeled` | one-way | DNA15, Ku | `kdku1` | state and binding-pattern rewrite | `DNA15(site!1~sdsb).Ku(dna!1,cs,cys~red)  -> DNA15(site~sdsb) + Ku(dna,cs,cys~red)` | Transforms DNA15, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 245 | `Unlabeled` | one-way | DNA16, Ku | `kdku1` | state and binding-pattern rewrite | `DNA16(site!1~sdsb).Ku(dna!1,cs,cys~red)  -> DNA16(site~sdsb) + Ku(dna,cs,cys~red)` | Transforms DNA16, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 246 | `Unlabeled` | one-way | DNA17, Ku | `kdku1` | state and binding-pattern rewrite | `DNA17(site!1~sdsb).Ku(dna!1,cs,cys~red)  -> DNA17(site~sdsb) + Ku(dna,cs,cys~red)` | Transforms DNA17, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 247 | `Unlabeled` | one-way | DNA18, Ku | `kdku1` | state and binding-pattern rewrite | `DNA18(site!1~sdsb).Ku(dna!1,cs,cys~red)  -> DNA18(site~sdsb) + Ku(dna,cs,cys~red)` | Transforms DNA18, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 248 | `Unlabeled` | one-way | DNA19, Ku | `kdku1` | state and binding-pattern rewrite | `DNA19(site!1~sdsb).Ku(dna!1,cs,cys~red)  -> DNA19(site~sdsb) + Ku(dna,cs,cys~red)` | Transforms DNA19, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 249 | `Unlabeled` | one-way | DNA20, Ku | `kdku1` | state and binding-pattern rewrite | `DNA20(site!1~sdsb).Ku(dna!1,cs,cys~red)  -> DNA20(site~sdsb) + Ku(dna,cs,cys~red)` | Transforms DNA20, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 250 | `Unlabeled` | one-way | DNA21, Ku | `kdku1` | state and binding-pattern rewrite | `DNA21(site!1~sdsb).Ku(dna!1,cs,cys~red)  -> DNA21(site~sdsb) + Ku(dna,cs,cys~red)` | Transforms DNA21, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

### Rules 251-500

| # | Rule label/name | Direction | Participants | Rate/expression | Modeled change | Rule pattern | Technical meaning |
| ---: | --- | --- | --- | --- | --- | --- | --- |

| 251 | `Unlabeled` | one-way | DNA22, Ku | `kdku1` | state and binding-pattern rewrite | `DNA22(site!1~sdsb).Ku(dna!1,cs,cys~red)  -> DNA22(site~sdsb) + Ku(dna,cs,cys~red)` | Transforms DNA22, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 252 | `Unlabeled` | one-way | DNA23, Ku | `kdku1` | state and binding-pattern rewrite | `DNA23(site!1~sdsb).Ku(dna!1,cs,cys~red)  -> DNA23(site~sdsb) + Ku(dna,cs,cys~red)` | Transforms DNA23, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 253 | `Unlabeled` | one-way | DNA24, Ku | `kdku1` | state and binding-pattern rewrite | `DNA24(site!1~sdsb).Ku(dna!1,cs,cys~red)  -> DNA24(site~sdsb) + Ku(dna,cs,cys~red)` | Transforms DNA24, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 254 | `Unlabeled` | one-way | DNA25, Ku | `kdku1` | state and binding-pattern rewrite | `DNA25(site!1~sdsb).Ku(dna!1,cs,cys~red)  -> DNA25(site~sdsb) + Ku(dna,cs,cys~red)` | Transforms DNA25, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 255 | `Unlabeled` | one-way | DNA26, Ku | `kdku1` | state and binding-pattern rewrite | `DNA26(site!1~sdsb).Ku(dna!1,cs,cys~red)  -> DNA26(site~sdsb) + Ku(dna,cs,cys~red)` | Transforms DNA26, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 256 | `Unlabeled` | one-way | DNA27, Ku | `kdku1` | state and binding-pattern rewrite | `DNA27(site!1~sdsb).Ku(dna!1,cs,cys~red)  -> DNA27(site~sdsb) + Ku(dna,cs,cys~red)` | Transforms DNA27, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 257 | `Unlabeled` | one-way | DNA28, Ku | `kdku1` | state and binding-pattern rewrite | `DNA28(site!1~sdsb).Ku(dna!1,cs,cys~red)  -> DNA28(site~sdsb) + Ku(dna,cs,cys~red)` | Transforms DNA28, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 258 | `Unlabeled` | one-way | DNA29, Ku | `kdku1` | state and binding-pattern rewrite | `DNA29(site!1~sdsb).Ku(dna!1,cs,cys~red)  -> DNA29(site~sdsb) + Ku(dna,cs,cys~red)` | Transforms DNA29, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 259 | `Unlabeled` | one-way | DNA30, Ku | `kdku1` | state and binding-pattern rewrite | `DNA30(site!1~sdsb).Ku(dna!1,cs,cys~red)  -> DNA30(site~sdsb) + Ku(dna,cs,cys~red)` | Transforms DNA30, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 260 | `Unlabeled` | one-way | DNA31, Ku | `kdku1` | state and binding-pattern rewrite | `DNA31(site!1~sdsb).Ku(dna!1,cs,cys~red)  -> DNA31(site~sdsb) + Ku(dna,cs,cys~red)` | Transforms DNA31, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 261 | `Unlabeled` | one-way | DNA32, Ku | `kdku1` | state and binding-pattern rewrite | `DNA32(site!1~sdsb).Ku(dna!1,cs,cys~red)  -> DNA32(site~sdsb) + Ku(dna,cs,cys~red)` | Transforms DNA32, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 262 | `Unlabeled` | one-way | DNA33, Ku | `kdku1` | state and binding-pattern rewrite | `DNA33(site!1~sdsb).Ku(dna!1,cs,cys~red)  -> DNA33(site~sdsb) + Ku(dna,cs,cys~red)` | Transforms DNA33, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 263 | `Unlabeled` | one-way | DNA34, Ku | `kdku1` | state and binding-pattern rewrite | `DNA34(site!1~sdsb).Ku(dna!1,cs,cys~red)  -> DNA34(site~sdsb) + Ku(dna,cs,cys~red)` | Transforms DNA34, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 264 | `Unlabeled` | one-way | DNA35, Ku | `kdku1` | state and binding-pattern rewrite | `DNA35(site!1~sdsb).Ku(dna!1,cs,cys~red)  -> DNA35(site~sdsb) + Ku(dna,cs,cys~red)` | Transforms DNA35, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 265 | `Unlabeled` | one-way | DNA36, Ku | `kdku1` | state and binding-pattern rewrite | `DNA36(site!1~sdsb).Ku(dna!1,cs,cys~red)  -> DNA36(site~sdsb) + Ku(dna,cs,cys~red)` | Transforms DNA36, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 266 | `Unlabeled` | one-way | DNA37, Ku | `kdku1` | state and binding-pattern rewrite | `DNA37(site!1~sdsb).Ku(dna!1,cs,cys~red)  -> DNA37(site~sdsb) + Ku(dna,cs,cys~red)` | Transforms DNA37, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 267 | `Unlabeled` | one-way | DNA38, Ku | `kdku1` | state and binding-pattern rewrite | `DNA38(site!1~sdsb).Ku(dna!1,cs,cys~red)  -> DNA38(site~sdsb) + Ku(dna,cs,cys~red)` | Transforms DNA38, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 268 | `Unlabeled` | one-way | DNA39, Ku | `kdku1` | state and binding-pattern rewrite | `DNA39(site!1~sdsb).Ku(dna!1,cs,cys~red)  -> DNA39(site~sdsb) + Ku(dna,cs,cys~red)` | Transforms DNA39, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 269 | `Unlabeled` | one-way | DNA40, Ku | `kdku1` | state and binding-pattern rewrite | `DNA40(site!1~sdsb).Ku(dna!1,cs,cys~red)  -> DNA40(site~sdsb) + Ku(dna,cs,cys~red)` | Transforms DNA40, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 270 | `Unlabeled` | one-way | DNA41, Ku | `kdku1` | state and binding-pattern rewrite | `DNA41(site!1~sdsb).Ku(dna!1,cs,cys~red)  -> DNA41(site~sdsb) + Ku(dna,cs,cys~red)` | Transforms DNA41, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 271 | `Unlabeled` | one-way | DNA42, Ku | `kdku1` | state and binding-pattern rewrite | `DNA42(site!1~sdsb).Ku(dna!1,cs,cys~red)  -> DNA42(site~sdsb) + Ku(dna,cs,cys~red)` | Transforms DNA42, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 272 | `Unlabeled` | one-way | DNA43, Ku | `kdku1` | state and binding-pattern rewrite | `DNA43(site!1~sdsb).Ku(dna!1,cs,cys~red)  -> DNA43(site~sdsb) + Ku(dna,cs,cys~red)` | Transforms DNA43, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 273 | `Unlabeled` | one-way | DNA44, Ku | `kdku1` | state and binding-pattern rewrite | `DNA44(site!1~sdsb).Ku(dna!1,cs,cys~red)  -> DNA44(site~sdsb) + Ku(dna,cs,cys~red)` | Transforms DNA44, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 274 | `Unlabeled` | one-way | DNA45, Ku | `kdku1` | state and binding-pattern rewrite | `DNA45(site!1~sdsb).Ku(dna!1,cs,cys~red)  -> DNA45(site~sdsb) + Ku(dna,cs,cys~red)` | Transforms DNA45, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 275 | `Unlabeled` | one-way | DNA46, Ku | `kdku1` | state and binding-pattern rewrite | `DNA46(site!1~sdsb).Ku(dna!1,cs,cys~red)  -> DNA46(site~sdsb) + Ku(dna,cs,cys~red)` | Transforms DNA46, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 276 | `Unlabeled` | one-way | DNA47, Ku | `kdku1` | state and binding-pattern rewrite | `DNA47(site!1~sdsb).Ku(dna!1,cs,cys~red)  -> DNA47(site~sdsb) + Ku(dna,cs,cys~red)` | Transforms DNA47, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 277 | `Unlabeled` | one-way | DNA48, Ku | `kdku1` | state and binding-pattern rewrite | `DNA48(site!1~sdsb).Ku(dna!1,cs,cys~red)  -> DNA48(site~sdsb) + Ku(dna,cs,cys~red)` | Transforms DNA48, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 278 | `Unlabeled` | one-way | DNA49, Ku | `kdku1` | state and binding-pattern rewrite | `DNA49(site!1~sdsb).Ku(dna!1,cs,cys~red)  -> DNA49(site~sdsb) + Ku(dna,cs,cys~red)` | Transforms DNA49, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 279 | `Unlabeled` | one-way | DNA50, Ku | `kdku1` | state and binding-pattern rewrite | `DNA50(site!1~sdsb).Ku(dna!1,cs,cys~red)  -> DNA50(site~sdsb) + Ku(dna,cs,cys~red)` | Transforms DNA50, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 280 | `Unlabeled` | one-way | DNA1, Ku | `kdku2` | state and binding-pattern rewrite | `DNA1(site!1~cdsb).Ku(dna!1,cs,cys~red)  -> DNA1(site~cdsb) + Ku(dna,cs,cys~red)` | Transforms DNA1, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 281 | `Unlabeled` | one-way | DNA2, Ku | `kdku2` | state and binding-pattern rewrite | `DNA2(site!1~cdsb).Ku(dna!1,cs,cys~red)  -> DNA2(site~cdsb) + Ku(dna,cs,cys~red)` | Transforms DNA2, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 282 | `Unlabeled` | one-way | DNA3, Ku | `kdku2` | state and binding-pattern rewrite | `DNA3(site!1~cdsb).Ku(dna!1,cs,cys~red)  -> DNA3(site~cdsb) + Ku(dna,cs,cys~red)` | Transforms DNA3, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 283 | `Unlabeled` | one-way | DNA4, Ku | `kdku2` | state and binding-pattern rewrite | `DNA4(site!1~cdsb).Ku(dna!1,cs,cys~red)  -> DNA4(site~cdsb) + Ku(dna,cs,cys~red)` | Transforms DNA4, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 284 | `Unlabeled` | one-way | DNA5, Ku | `kdku2` | state and binding-pattern rewrite | `DNA5(site!1~cdsb).Ku(dna!1,cs,cys~red)  -> DNA5(site~cdsb) + Ku(dna,cs,cys~red)` | Transforms DNA5, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 285 | `Unlabeled` | one-way | DNA6, Ku | `kdku2` | state and binding-pattern rewrite | `DNA6(site!1~cdsb).Ku(dna!1,cs,cys~red)  -> DNA6(site~cdsb) + Ku(dna,cs,cys~red)` | Transforms DNA6, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 286 | `Unlabeled` | one-way | DNA7, Ku | `kdku2` | state and binding-pattern rewrite | `DNA7(site!1~cdsb).Ku(dna!1,cs,cys~red)  -> DNA7(site~cdsb) + Ku(dna,cs,cys~red)` | Transforms DNA7, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 287 | `Unlabeled` | one-way | DNA8, Ku | `kdku2` | state and binding-pattern rewrite | `DNA8(site!1~cdsb).Ku(dna!1,cs,cys~red)  -> DNA8(site~cdsb) + Ku(dna,cs,cys~red)` | Transforms DNA8, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 288 | `Unlabeled` | one-way | DNA9, Ku | `kdku2` | state and binding-pattern rewrite | `DNA9(site!1~cdsb).Ku(dna!1,cs,cys~red)  -> DNA9(site~cdsb) + Ku(dna,cs,cys~red)` | Transforms DNA9, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 289 | `Unlabeled` | one-way | DNA10, Ku | `kdku2` | state and binding-pattern rewrite | `DNA10(site!1~cdsb).Ku(dna!1,cs,cys~red)  -> DNA10(site~cdsb) + Ku(dna,cs,cys~red)` | Transforms DNA10, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 290 | `Unlabeled` | one-way | DNA11, Ku | `kdku2` | state and binding-pattern rewrite | `DNA11(site!1~cdsb).Ku(dna!1,cs,cys~red)  -> DNA11(site~cdsb) + Ku(dna,cs,cys~red)` | Transforms DNA11, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 291 | `Unlabeled` | one-way | DNA12, Ku | `kdku2` | state and binding-pattern rewrite | `DNA12(site!1~cdsb).Ku(dna!1,cs,cys~red)  -> DNA12(site~cdsb) + Ku(dna,cs,cys~red)` | Transforms DNA12, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 292 | `Unlabeled` | one-way | DNA13, Ku | `kdku2` | state and binding-pattern rewrite | `DNA13(site!1~cdsb).Ku(dna!1,cs,cys~red)  -> DNA13(site~cdsb) + Ku(dna,cs,cys~red)` | Transforms DNA13, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 293 | `Unlabeled` | one-way | DNA14, Ku | `kdku2` | state and binding-pattern rewrite | `DNA14(site!1~cdsb).Ku(dna!1,cs,cys~red)  -> DNA14(site~cdsb) + Ku(dna,cs,cys~red)` | Transforms DNA14, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 294 | `Unlabeled` | one-way | DNA15, Ku | `kdku2` | state and binding-pattern rewrite | `DNA15(site!1~cdsb).Ku(dna!1,cs,cys~red)  -> DNA15(site~cdsb) + Ku(dna,cs,cys~red)` | Transforms DNA15, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 295 | `Unlabeled` | one-way | DNA16, Ku | `kdku2` | state and binding-pattern rewrite | `DNA16(site!1~cdsb).Ku(dna!1,cs,cys~red)  -> DNA16(site~cdsb) + Ku(dna,cs,cys~red)` | Transforms DNA16, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 296 | `Unlabeled` | one-way | DNA17, Ku | `kdku2` | state and binding-pattern rewrite | `DNA17(site!1~cdsb).Ku(dna!1,cs,cys~red)  -> DNA17(site~cdsb) + Ku(dna,cs,cys~red)` | Transforms DNA17, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 297 | `Unlabeled` | one-way | DNA18, Ku | `kdku2` | state and binding-pattern rewrite | `DNA18(site!1~cdsb).Ku(dna!1,cs,cys~red)  -> DNA18(site~cdsb) + Ku(dna,cs,cys~red)` | Transforms DNA18, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 298 | `Unlabeled` | one-way | DNA19, Ku | `kdku2` | state and binding-pattern rewrite | `DNA19(site!1~cdsb).Ku(dna!1,cs,cys~red)  -> DNA19(site~cdsb) + Ku(dna,cs,cys~red)` | Transforms DNA19, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 299 | `Unlabeled` | one-way | DNA20, Ku | `kdku2` | state and binding-pattern rewrite | `DNA20(site!1~cdsb).Ku(dna!1,cs,cys~red)  -> DNA20(site~cdsb) + Ku(dna,cs,cys~red)` | Transforms DNA20, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 300 | `Unlabeled` | one-way | DNA21, Ku | `kdku2` | state and binding-pattern rewrite | `DNA21(site!1~cdsb).Ku(dna!1,cs,cys~red)  -> DNA21(site~cdsb) + Ku(dna,cs,cys~red)` | Transforms DNA21, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 301 | `Unlabeled` | one-way | DNA22, Ku | `kdku2` | state and binding-pattern rewrite | `DNA22(site!1~cdsb).Ku(dna!1,cs,cys~red)  -> DNA22(site~cdsb) + Ku(dna,cs,cys~red)` | Transforms DNA22, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 302 | `Unlabeled` | one-way | DNA23, Ku | `kdku2` | state and binding-pattern rewrite | `DNA23(site!1~cdsb).Ku(dna!1,cs,cys~red)  -> DNA23(site~cdsb) + Ku(dna,cs,cys~red)` | Transforms DNA23, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 303 | `Unlabeled` | one-way | DNA24, Ku | `kdku2` | state and binding-pattern rewrite | `DNA24(site!1~cdsb).Ku(dna!1,cs,cys~red)  -> DNA24(site~cdsb) + Ku(dna,cs,cys~red)` | Transforms DNA24, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 304 | `Unlabeled` | one-way | DNA25, Ku | `kdku2` | state and binding-pattern rewrite | `DNA25(site!1~cdsb).Ku(dna!1,cs,cys~red)  -> DNA25(site~cdsb) + Ku(dna,cs,cys~red)` | Transforms DNA25, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 305 | `Unlabeled` | one-way | DNA26, Ku | `kdku2` | state and binding-pattern rewrite | `DNA26(site!1~cdsb).Ku(dna!1,cs,cys~red)  -> DNA26(site~cdsb) + Ku(dna,cs,cys~red)` | Transforms DNA26, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 306 | `Unlabeled` | one-way | DNA27, Ku | `kdku2` | state and binding-pattern rewrite | `DNA27(site!1~cdsb).Ku(dna!1,cs,cys~red)  -> DNA27(site~cdsb) + Ku(dna,cs,cys~red)` | Transforms DNA27, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 307 | `Unlabeled` | one-way | DNA28, Ku | `kdku2` | state and binding-pattern rewrite | `DNA28(site!1~cdsb).Ku(dna!1,cs,cys~red)  -> DNA28(site~cdsb) + Ku(dna,cs,cys~red)` | Transforms DNA28, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 308 | `Unlabeled` | one-way | DNA29, Ku | `kdku2` | state and binding-pattern rewrite | `DNA29(site!1~cdsb).Ku(dna!1,cs,cys~red)  -> DNA29(site~cdsb) + Ku(dna,cs,cys~red)` | Transforms DNA29, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 309 | `Unlabeled` | one-way | DNA30, Ku | `kdku2` | state and binding-pattern rewrite | `DNA30(site!1~cdsb).Ku(dna!1,cs,cys~red)  -> DNA30(site~cdsb) + Ku(dna,cs,cys~red)` | Transforms DNA30, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 310 | `Unlabeled` | one-way | DNA31, Ku | `kdku2` | state and binding-pattern rewrite | `DNA31(site!1~cdsb).Ku(dna!1,cs,cys~red)  -> DNA31(site~cdsb) + Ku(dna,cs,cys~red)` | Transforms DNA31, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 311 | `Unlabeled` | one-way | DNA32, Ku | `kdku2` | state and binding-pattern rewrite | `DNA32(site!1~cdsb).Ku(dna!1,cs,cys~red)  -> DNA32(site~cdsb) + Ku(dna,cs,cys~red)` | Transforms DNA32, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 312 | `Unlabeled` | one-way | DNA33, Ku | `kdku2` | state and binding-pattern rewrite | `DNA33(site!1~cdsb).Ku(dna!1,cs,cys~red)  -> DNA33(site~cdsb) + Ku(dna,cs,cys~red)` | Transforms DNA33, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 313 | `Unlabeled` | one-way | DNA34, Ku | `kdku2` | state and binding-pattern rewrite | `DNA34(site!1~cdsb).Ku(dna!1,cs,cys~red)  -> DNA34(site~cdsb) + Ku(dna,cs,cys~red)` | Transforms DNA34, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 314 | `Unlabeled` | one-way | DNA35, Ku | `kdku2` | state and binding-pattern rewrite | `DNA35(site!1~cdsb).Ku(dna!1,cs,cys~red)  -> DNA35(site~cdsb) + Ku(dna,cs,cys~red)` | Transforms DNA35, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 315 | `Unlabeled` | one-way | DNA36, Ku | `kdku2` | state and binding-pattern rewrite | `DNA36(site!1~cdsb).Ku(dna!1,cs,cys~red)  -> DNA36(site~cdsb) + Ku(dna,cs,cys~red)` | Transforms DNA36, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 316 | `Unlabeled` | one-way | DNA37, Ku | `kdku2` | state and binding-pattern rewrite | `DNA37(site!1~cdsb).Ku(dna!1,cs,cys~red)  -> DNA37(site~cdsb) + Ku(dna,cs,cys~red)` | Transforms DNA37, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 317 | `Unlabeled` | one-way | DNA38, Ku | `kdku2` | state and binding-pattern rewrite | `DNA38(site!1~cdsb).Ku(dna!1,cs,cys~red)  -> DNA38(site~cdsb) + Ku(dna,cs,cys~red)` | Transforms DNA38, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 318 | `Unlabeled` | one-way | DNA39, Ku | `kdku2` | state and binding-pattern rewrite | `DNA39(site!1~cdsb).Ku(dna!1,cs,cys~red)  -> DNA39(site~cdsb) + Ku(dna,cs,cys~red)` | Transforms DNA39, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 319 | `Unlabeled` | one-way | DNA40, Ku | `kdku2` | state and binding-pattern rewrite | `DNA40(site!1~cdsb).Ku(dna!1,cs,cys~red)  -> DNA40(site~cdsb) + Ku(dna,cs,cys~red)` | Transforms DNA40, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 320 | `Unlabeled` | one-way | DNA41, Ku | `kdku2` | state and binding-pattern rewrite | `DNA41(site!1~cdsb).Ku(dna!1,cs,cys~red)  -> DNA41(site~cdsb) + Ku(dna,cs,cys~red)` | Transforms DNA41, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 321 | `Unlabeled` | one-way | DNA42, Ku | `kdku2` | state and binding-pattern rewrite | `DNA42(site!1~cdsb).Ku(dna!1,cs,cys~red)  -> DNA42(site~cdsb) + Ku(dna,cs,cys~red)` | Transforms DNA42, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 322 | `Unlabeled` | one-way | DNA43, Ku | `kdku2` | state and binding-pattern rewrite | `DNA43(site!1~cdsb).Ku(dna!1,cs,cys~red)  -> DNA43(site~cdsb) + Ku(dna,cs,cys~red)` | Transforms DNA43, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 323 | `Unlabeled` | one-way | DNA44, Ku | `kdku2` | state and binding-pattern rewrite | `DNA44(site!1~cdsb).Ku(dna!1,cs,cys~red)  -> DNA44(site~cdsb) + Ku(dna,cs,cys~red)` | Transforms DNA44, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 324 | `Unlabeled` | one-way | DNA45, Ku | `kdku2` | state and binding-pattern rewrite | `DNA45(site!1~cdsb).Ku(dna!1,cs,cys~red)  -> DNA45(site~cdsb) + Ku(dna,cs,cys~red)` | Transforms DNA45, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 325 | `Unlabeled` | one-way | DNA46, Ku | `kdku2` | state and binding-pattern rewrite | `DNA46(site!1~cdsb).Ku(dna!1,cs,cys~red)  -> DNA46(site~cdsb) + Ku(dna,cs,cys~red)` | Transforms DNA46, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 326 | `Unlabeled` | one-way | DNA47, Ku | `kdku2` | state and binding-pattern rewrite | `DNA47(site!1~cdsb).Ku(dna!1,cs,cys~red)  -> DNA47(site~cdsb) + Ku(dna,cs,cys~red)` | Transforms DNA47, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 327 | `Unlabeled` | one-way | DNA48, Ku | `kdku2` | state and binding-pattern rewrite | `DNA48(site!1~cdsb).Ku(dna!1,cs,cys~red)  -> DNA48(site~cdsb) + Ku(dna,cs,cys~red)` | Transforms DNA48, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 328 | `Unlabeled` | one-way | DNA49, Ku | `kdku2` | state and binding-pattern rewrite | `DNA49(site!1~cdsb).Ku(dna!1,cs,cys~red)  -> DNA49(site~cdsb) + Ku(dna,cs,cys~red)` | Transforms DNA49, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 329 | `Unlabeled` | one-way | DNA50, Ku | `kdku2` | state and binding-pattern rewrite | `DNA50(site!1~cdsb).Ku(dna!1,cs,cys~red)  -> DNA50(site~cdsb) + Ku(dna,cs,cys~red)` | Transforms DNA50, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 330 | `Unlabeled` | one-way | DNA1, DNAPKcs, Ku | `kdnapk1` | internal-state conversion/modification | `DNA1(site!1~sdsb).Ku(dna!1,cs) + DNAPKcs(ku,liIV,psite~u)  -> DNA1(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)` | Transforms DNA1, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 331 | `Unlabeled` | one-way | DNA2, DNAPKcs, Ku | `kdnapk1` | internal-state conversion/modification | `DNA2(site!1~sdsb).Ku(dna!1,cs) + DNAPKcs(ku,liIV,psite~u)  -> DNA2(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)` | Transforms DNA2, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 332 | `Unlabeled` | one-way | DNA3, DNAPKcs, Ku | `kdnapk1` | internal-state conversion/modification | `DNA3(site!1~sdsb).Ku(dna!1,cs) + DNAPKcs(ku,liIV,psite~u)  -> DNA3(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)` | Transforms DNA3, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 333 | `Unlabeled` | one-way | DNA4, DNAPKcs, Ku | `kdnapk1` | internal-state conversion/modification | `DNA4(site!1~sdsb).Ku(dna!1,cs) + DNAPKcs(ku,liIV,psite~u)  -> DNA4(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)` | Transforms DNA4, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 334 | `Unlabeled` | one-way | DNA5, DNAPKcs, Ku | `kdnapk1` | internal-state conversion/modification | `DNA5(site!1~sdsb).Ku(dna!1,cs) + DNAPKcs(ku,liIV,psite~u)  -> DNA5(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)` | Transforms DNA5, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 335 | `Unlabeled` | one-way | DNA6, DNAPKcs, Ku | `kdnapk1` | internal-state conversion/modification | `DNA6(site!1~sdsb).Ku(dna!1,cs) + DNAPKcs(ku,liIV,psite~u)  -> DNA6(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)` | Transforms DNA6, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 336 | `Unlabeled` | one-way | DNA7, DNAPKcs, Ku | `kdnapk1` | internal-state conversion/modification | `DNA7(site!1~sdsb).Ku(dna!1,cs) + DNAPKcs(ku,liIV,psite~u)  -> DNA7(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)` | Transforms DNA7, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 337 | `Unlabeled` | one-way | DNA8, DNAPKcs, Ku | `kdnapk1` | internal-state conversion/modification | `DNA8(site!1~sdsb).Ku(dna!1,cs) + DNAPKcs(ku,liIV,psite~u)  -> DNA8(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)` | Transforms DNA8, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 338 | `Unlabeled` | one-way | DNA9, DNAPKcs, Ku | `kdnapk1` | internal-state conversion/modification | `DNA9(site!1~sdsb).Ku(dna!1,cs) + DNAPKcs(ku,liIV,psite~u)  -> DNA9(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)` | Transforms DNA9, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 339 | `Unlabeled` | one-way | DNA10, DNAPKcs, Ku | `kdnapk1` | internal-state conversion/modification | `DNA10(site!1~sdsb).Ku(dna!1,cs) + DNAPKcs(ku,liIV,psite~u)  -> DNA10(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)` | Transforms DNA10, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 340 | `Unlabeled` | one-way | DNA11, DNAPKcs, Ku | `kdnapk1` | internal-state conversion/modification | `DNA11(site!1~sdsb).Ku(dna!1,cs) + DNAPKcs(ku,liIV,psite~u)  -> DNA11(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)` | Transforms DNA11, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 341 | `Unlabeled` | one-way | DNA12, DNAPKcs, Ku | `kdnapk1` | internal-state conversion/modification | `DNA12(site!1~sdsb).Ku(dna!1,cs) + DNAPKcs(ku,liIV,psite~u)  -> DNA12(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)` | Transforms DNA12, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 342 | `Unlabeled` | one-way | DNA13, DNAPKcs, Ku | `kdnapk1` | internal-state conversion/modification | `DNA13(site!1~sdsb).Ku(dna!1,cs) + DNAPKcs(ku,liIV,psite~u)  -> DNA13(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)` | Transforms DNA13, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 343 | `Unlabeled` | one-way | DNA14, DNAPKcs, Ku | `kdnapk1` | internal-state conversion/modification | `DNA14(site!1~sdsb).Ku(dna!1,cs) + DNAPKcs(ku,liIV,psite~u)  -> DNA14(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)` | Transforms DNA14, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 344 | `Unlabeled` | one-way | DNA15, DNAPKcs, Ku | `kdnapk1` | internal-state conversion/modification | `DNA15(site!1~sdsb).Ku(dna!1,cs) + DNAPKcs(ku,liIV,psite~u)  -> DNA15(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)` | Transforms DNA15, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 345 | `Unlabeled` | one-way | DNA16, DNAPKcs, Ku | `kdnapk1` | internal-state conversion/modification | `DNA16(site!1~sdsb).Ku(dna!1,cs) + DNAPKcs(ku,liIV,psite~u)  -> DNA16(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)` | Transforms DNA16, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 346 | `Unlabeled` | one-way | DNA17, DNAPKcs, Ku | `kdnapk1` | internal-state conversion/modification | `DNA17(site!1~sdsb).Ku(dna!1,cs) + DNAPKcs(ku,liIV,psite~u)  -> DNA17(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)` | Transforms DNA17, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 347 | `Unlabeled` | one-way | DNA18, DNAPKcs, Ku | `kdnapk1` | internal-state conversion/modification | `DNA18(site!1~sdsb).Ku(dna!1,cs) + DNAPKcs(ku,liIV,psite~u)  -> DNA18(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)` | Transforms DNA18, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 348 | `Unlabeled` | one-way | DNA19, DNAPKcs, Ku | `kdnapk1` | internal-state conversion/modification | `DNA19(site!1~sdsb).Ku(dna!1,cs) + DNAPKcs(ku,liIV,psite~u)  -> DNA19(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)` | Transforms DNA19, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 349 | `Unlabeled` | one-way | DNA20, DNAPKcs, Ku | `kdnapk1` | internal-state conversion/modification | `DNA20(site!1~sdsb).Ku(dna!1,cs) + DNAPKcs(ku,liIV,psite~u)  -> DNA20(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)` | Transforms DNA20, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 350 | `Unlabeled` | one-way | DNA21, DNAPKcs, Ku | `kdnapk1` | internal-state conversion/modification | `DNA21(site!1~sdsb).Ku(dna!1,cs) + DNAPKcs(ku,liIV,psite~u)  -> DNA21(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)` | Transforms DNA21, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 351 | `Unlabeled` | one-way | DNA22, DNAPKcs, Ku | `kdnapk1` | internal-state conversion/modification | `DNA22(site!1~sdsb).Ku(dna!1,cs) + DNAPKcs(ku,liIV,psite~u)  -> DNA22(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)` | Transforms DNA22, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 352 | `Unlabeled` | one-way | DNA23, DNAPKcs, Ku | `kdnapk1` | internal-state conversion/modification | `DNA23(site!1~sdsb).Ku(dna!1,cs) + DNAPKcs(ku,liIV,psite~u)  -> DNA23(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)` | Transforms DNA23, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 353 | `Unlabeled` | one-way | DNA24, DNAPKcs, Ku | `kdnapk1` | internal-state conversion/modification | `DNA24(site!1~sdsb).Ku(dna!1,cs) + DNAPKcs(ku,liIV,psite~u)  -> DNA24(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)` | Transforms DNA24, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 354 | `Unlabeled` | one-way | DNA25, DNAPKcs, Ku | `kdnapk1` | internal-state conversion/modification | `DNA25(site!1~sdsb).Ku(dna!1,cs) + DNAPKcs(ku,liIV,psite~u)  -> DNA25(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)` | Transforms DNA25, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 355 | `Unlabeled` | one-way | DNA26, DNAPKcs, Ku | `kdnapk1` | internal-state conversion/modification | `DNA26(site!1~sdsb).Ku(dna!1,cs) + DNAPKcs(ku,liIV,psite~u)  -> DNA26(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)` | Transforms DNA26, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 356 | `Unlabeled` | one-way | DNA27, DNAPKcs, Ku | `kdnapk1` | internal-state conversion/modification | `DNA27(site!1~sdsb).Ku(dna!1,cs) + DNAPKcs(ku,liIV,psite~u)  -> DNA27(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)` | Transforms DNA27, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 357 | `Unlabeled` | one-way | DNA28, DNAPKcs, Ku | `kdnapk1` | internal-state conversion/modification | `DNA28(site!1~sdsb).Ku(dna!1,cs) + DNAPKcs(ku,liIV,psite~u)  -> DNA28(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)` | Transforms DNA28, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 358 | `Unlabeled` | one-way | DNA29, DNAPKcs, Ku | `kdnapk1` | internal-state conversion/modification | `DNA29(site!1~sdsb).Ku(dna!1,cs) + DNAPKcs(ku,liIV,psite~u)  -> DNA29(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)` | Transforms DNA29, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 359 | `Unlabeled` | one-way | DNA30, DNAPKcs, Ku | `kdnapk1` | internal-state conversion/modification | `DNA30(site!1~sdsb).Ku(dna!1,cs) + DNAPKcs(ku,liIV,psite~u)  -> DNA30(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)` | Transforms DNA30, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 360 | `Unlabeled` | one-way | DNA31, DNAPKcs, Ku | `kdnapk1` | internal-state conversion/modification | `DNA31(site!1~sdsb).Ku(dna!1,cs) + DNAPKcs(ku,liIV,psite~u)  -> DNA31(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)` | Transforms DNA31, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 361 | `Unlabeled` | one-way | DNA32, DNAPKcs, Ku | `kdnapk1` | internal-state conversion/modification | `DNA32(site!1~sdsb).Ku(dna!1,cs) + DNAPKcs(ku,liIV,psite~u)  -> DNA32(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)` | Transforms DNA32, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 362 | `Unlabeled` | one-way | DNA33, DNAPKcs, Ku | `kdnapk1` | internal-state conversion/modification | `DNA33(site!1~sdsb).Ku(dna!1,cs) + DNAPKcs(ku,liIV,psite~u)  -> DNA33(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)` | Transforms DNA33, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 363 | `Unlabeled` | one-way | DNA34, DNAPKcs, Ku | `kdnapk1` | internal-state conversion/modification | `DNA34(site!1~sdsb).Ku(dna!1,cs) + DNAPKcs(ku,liIV,psite~u)  -> DNA34(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)` | Transforms DNA34, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 364 | `Unlabeled` | one-way | DNA35, DNAPKcs, Ku | `kdnapk1` | internal-state conversion/modification | `DNA35(site!1~sdsb).Ku(dna!1,cs) + DNAPKcs(ku,liIV,psite~u)  -> DNA35(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)` | Transforms DNA35, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 365 | `Unlabeled` | one-way | DNA36, DNAPKcs, Ku | `kdnapk1` | internal-state conversion/modification | `DNA36(site!1~sdsb).Ku(dna!1,cs) + DNAPKcs(ku,liIV,psite~u)  -> DNA36(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)` | Transforms DNA36, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 366 | `Unlabeled` | one-way | DNA37, DNAPKcs, Ku | `kdnapk1` | internal-state conversion/modification | `DNA37(site!1~sdsb).Ku(dna!1,cs) + DNAPKcs(ku,liIV,psite~u)  -> DNA37(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)` | Transforms DNA37, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 367 | `Unlabeled` | one-way | DNA38, DNAPKcs, Ku | `kdnapk1` | internal-state conversion/modification | `DNA38(site!1~sdsb).Ku(dna!1,cs) + DNAPKcs(ku,liIV,psite~u)  -> DNA38(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)` | Transforms DNA38, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 368 | `Unlabeled` | one-way | DNA39, DNAPKcs, Ku | `kdnapk1` | internal-state conversion/modification | `DNA39(site!1~sdsb).Ku(dna!1,cs) + DNAPKcs(ku,liIV,psite~u)  -> DNA39(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)` | Transforms DNA39, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 369 | `Unlabeled` | one-way | DNA40, DNAPKcs, Ku | `kdnapk1` | internal-state conversion/modification | `DNA40(site!1~sdsb).Ku(dna!1,cs) + DNAPKcs(ku,liIV,psite~u)  -> DNA40(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)` | Transforms DNA40, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 370 | `Unlabeled` | one-way | DNA41, DNAPKcs, Ku | `kdnapk1` | internal-state conversion/modification | `DNA41(site!1~sdsb).Ku(dna!1,cs) + DNAPKcs(ku,liIV,psite~u)  -> DNA41(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)` | Transforms DNA41, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 371 | `Unlabeled` | one-way | DNA42, DNAPKcs, Ku | `kdnapk1` | internal-state conversion/modification | `DNA42(site!1~sdsb).Ku(dna!1,cs) + DNAPKcs(ku,liIV,psite~u)  -> DNA42(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)` | Transforms DNA42, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 372 | `Unlabeled` | one-way | DNA43, DNAPKcs, Ku | `kdnapk1` | internal-state conversion/modification | `DNA43(site!1~sdsb).Ku(dna!1,cs) + DNAPKcs(ku,liIV,psite~u)  -> DNA43(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)` | Transforms DNA43, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 373 | `Unlabeled` | one-way | DNA44, DNAPKcs, Ku | `kdnapk1` | internal-state conversion/modification | `DNA44(site!1~sdsb).Ku(dna!1,cs) + DNAPKcs(ku,liIV,psite~u)  -> DNA44(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)` | Transforms DNA44, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 374 | `Unlabeled` | one-way | DNA45, DNAPKcs, Ku | `kdnapk1` | internal-state conversion/modification | `DNA45(site!1~sdsb).Ku(dna!1,cs) + DNAPKcs(ku,liIV,psite~u)  -> DNA45(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)` | Transforms DNA45, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 375 | `Unlabeled` | one-way | DNA46, DNAPKcs, Ku | `kdnapk1` | internal-state conversion/modification | `DNA46(site!1~sdsb).Ku(dna!1,cs) + DNAPKcs(ku,liIV,psite~u)  -> DNA46(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)` | Transforms DNA46, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 376 | `Unlabeled` | one-way | DNA47, DNAPKcs, Ku | `kdnapk1` | internal-state conversion/modification | `DNA47(site!1~sdsb).Ku(dna!1,cs) + DNAPKcs(ku,liIV,psite~u)  -> DNA47(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)` | Transforms DNA47, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 377 | `Unlabeled` | one-way | DNA48, DNAPKcs, Ku | `kdnapk1` | internal-state conversion/modification | `DNA48(site!1~sdsb).Ku(dna!1,cs) + DNAPKcs(ku,liIV,psite~u)  -> DNA48(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)` | Transforms DNA48, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 378 | `Unlabeled` | one-way | DNA49, DNAPKcs, Ku | `kdnapk1` | internal-state conversion/modification | `DNA49(site!1~sdsb).Ku(dna!1,cs) + DNAPKcs(ku,liIV,psite~u)  -> DNA49(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)` | Transforms DNA49, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 379 | `Unlabeled` | one-way | DNA50, DNAPKcs, Ku | `kdnapk1` | internal-state conversion/modification | `DNA50(site!1~sdsb).Ku(dna!1,cs) + DNAPKcs(ku,liIV,psite~u)  -> DNA50(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)` | Transforms DNA50, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 380 | `Unlabeled` | one-way | DNA1, DNAPKcs, Ku | `kdnapk2` | internal-state conversion/modification | `DNA1(site!1~cdsb).Ku(dna!1,cs)  + DNAPKcs(ku,liIV,psite~u)  -> DNA1(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)` | Transforms DNA1, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 381 | `Unlabeled` | one-way | DNA2, DNAPKcs, Ku | `kdnapk2` | internal-state conversion/modification | `DNA2(site!1~cdsb).Ku(dna!1,cs) + DNAPKcs(ku,liIV,psite~u)  -> DNA2(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)` | Transforms DNA2, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 382 | `Unlabeled` | one-way | DNA3, DNAPKcs, Ku | `kdnapk2` | internal-state conversion/modification | `DNA3(site!1~cdsb).Ku(dna!1,cs) + DNAPKcs(ku,liIV,psite~u)  -> DNA3(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)` | Transforms DNA3, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 383 | `Unlabeled` | one-way | DNA4, DNAPKcs, Ku | `kdnapk2` | internal-state conversion/modification | `DNA4(site!1~cdsb).Ku(dna!1,cs) + DNAPKcs(ku,liIV,psite~u)  -> DNA4(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)` | Transforms DNA4, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 384 | `Unlabeled` | one-way | DNA5, DNAPKcs, Ku | `kdnapk2` | internal-state conversion/modification | `DNA5(site!1~cdsb).Ku(dna!1,cs) + DNAPKcs(ku,liIV,psite~u)  -> DNA5(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)` | Transforms DNA5, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 385 | `Unlabeled` | one-way | DNA6, DNAPKcs, Ku | `kdnapk2` | internal-state conversion/modification | `DNA6(site!1~cdsb).Ku(dna!1,cs) + DNAPKcs(ku,liIV,psite~u)  -> DNA6(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)` | Transforms DNA6, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 386 | `Unlabeled` | one-way | DNA7, DNAPKcs, Ku | `kdnapk2` | internal-state conversion/modification | `DNA7(site!1~cdsb).Ku(dna!1,cs)  + DNAPKcs(ku,liIV,psite~u)  -> DNA7(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)` | Transforms DNA7, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 387 | `Unlabeled` | one-way | DNA8, DNAPKcs, Ku | `kdnapk2` | internal-state conversion/modification | `DNA8(site!1~cdsb).Ku(dna!1,cs)  + DNAPKcs(ku,liIV,psite~u)  -> DNA8(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)` | Transforms DNA8, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 388 | `Unlabeled` | one-way | DNA9, DNAPKcs, Ku | `kdnapk2` | internal-state conversion/modification | `DNA9(site!1~cdsb).Ku(dna!1,cs) + DNAPKcs(ku,liIV,psite~u)  -> DNA9(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)` | Transforms DNA9, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 389 | `Unlabeled` | one-way | DNA10, DNAPKcs, Ku | `kdnapk2` | internal-state conversion/modification | `DNA10(site!1~cdsb).Ku(dna!1,cs) + DNAPKcs(ku,liIV,psite~u)  -> DNA10(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)` | Transforms DNA10, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 390 | `Unlabeled` | one-way | DNA11, DNAPKcs, Ku | `kdnapk2` | internal-state conversion/modification | `DNA11(site!1~cdsb).Ku(dna!1,cs) + DNAPKcs(ku,liIV,psite~u)  -> DNA11(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)` | Transforms DNA11, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 391 | `Unlabeled` | one-way | DNA12, DNAPKcs, Ku | `kdnapk2` | internal-state conversion/modification | `DNA12(site!1~cdsb).Ku(dna!1,cs) + DNAPKcs(ku,liIV,psite~u)  -> DNA12(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)` | Transforms DNA12, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 392 | `Unlabeled` | one-way | DNA13, DNAPKcs, Ku | `kdnapk2` | internal-state conversion/modification | `DNA13(site!1~cdsb).Ku(dna!1,cs) + DNAPKcs(ku,liIV,psite~u)  -> DNA13(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)` | Transforms DNA13, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 393 | `Unlabeled` | one-way | DNA14, DNAPKcs, Ku | `kdnapk2` | internal-state conversion/modification | `DNA14(site!1~cdsb).Ku(dna!1,cs) + DNAPKcs(ku,liIV,psite~u)  -> DNA14(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)` | Transforms DNA14, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 394 | `Unlabeled` | one-way | DNA15, DNAPKcs, Ku | `kdnapk2` | internal-state conversion/modification | `DNA15(site!1~cdsb).Ku(dna!1,cs) + DNAPKcs(ku,liIV,psite~u)  -> DNA15(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)` | Transforms DNA15, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 395 | `Unlabeled` | one-way | DNA16, DNAPKcs, Ku | `kdnapk2` | internal-state conversion/modification | `DNA16(site!1~cdsb).Ku(dna!1,cs) + DNAPKcs(ku,liIV,psite~u)  -> DNA16(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)` | Transforms DNA16, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 396 | `Unlabeled` | one-way | DNA17, DNAPKcs, Ku | `kdnapk2` | internal-state conversion/modification | `DNA17(site!1~cdsb).Ku(dna!1,cs) + DNAPKcs(ku,liIV,psite~u)  -> DNA17(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)` | Transforms DNA17, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 397 | `Unlabeled` | one-way | DNA18, DNAPKcs, Ku | `kdnapk2` | internal-state conversion/modification | `DNA18(site!1~cdsb).Ku(dna!1,cs) + DNAPKcs(ku,liIV,psite~u)  -> DNA18(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)` | Transforms DNA18, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 398 | `Unlabeled` | one-way | DNA19, DNAPKcs, Ku | `kdnapk2` | internal-state conversion/modification | `DNA19(site!1~cdsb).Ku(dna!1,cs) + DNAPKcs(ku,liIV,psite~u)  -> DNA19(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)` | Transforms DNA19, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 399 | `Unlabeled` | one-way | DNA20, DNAPKcs, Ku | `kdnapk2` | internal-state conversion/modification | `DNA20(site!1~cdsb).Ku(dna!1,cs) + DNAPKcs(ku,liIV,psite~u)  -> DNA20(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)` | Transforms DNA20, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 400 | `Unlabeled` | one-way | DNA21, DNAPKcs, Ku | `kdnapk2` | internal-state conversion/modification | `DNA21(site!1~cdsb).Ku(dna!1,cs) + DNAPKcs(ku,liIV,psite~u)  -> DNA21(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)` | Transforms DNA21, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 401 | `Unlabeled` | one-way | DNA22, DNAPKcs, Ku | `kdnapk2` | internal-state conversion/modification | `DNA22(site!1~cdsb).Ku(dna!1,cs) + DNAPKcs(ku,liIV,psite~u)  -> DNA22(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)` | Transforms DNA22, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 402 | `Unlabeled` | one-way | DNA23, DNAPKcs, Ku | `kdnapk2` | internal-state conversion/modification | `DNA23(site!1~cdsb).Ku(dna!1,cs) + DNAPKcs(ku,liIV,psite~u)  -> DNA23(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)` | Transforms DNA23, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 403 | `Unlabeled` | one-way | DNA24, DNAPKcs, Ku | `kdnapk2` | internal-state conversion/modification | `DNA24(site!1~cdsb).Ku(dna!1,cs) + DNAPKcs(ku,liIV,psite~u)  -> DNA24(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)` | Transforms DNA24, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 404 | `Unlabeled` | one-way | DNA25, DNAPKcs, Ku | `kdnapk2` | internal-state conversion/modification | `DNA25(site!1~cdsb).Ku(dna!1,cs) + DNAPKcs(ku,liIV,psite~u)  -> DNA25(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)` | Transforms DNA25, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 405 | `Unlabeled` | one-way | DNA26, DNAPKcs, Ku | `kdnapk2` | internal-state conversion/modification | `DNA26(site!1~cdsb).Ku(dna!1,cs) + DNAPKcs(ku,liIV,psite~u)  -> DNA26(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)` | Transforms DNA26, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 406 | `Unlabeled` | one-way | DNA27, DNAPKcs, Ku | `kdnapk2` | internal-state conversion/modification | `DNA27(site!1~cdsb).Ku(dna!1,cs) + DNAPKcs(ku,liIV,psite~u)  -> DNA27(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)` | Transforms DNA27, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 407 | `Unlabeled` | one-way | DNA28, DNAPKcs, Ku | `kdnapk2` | internal-state conversion/modification | `DNA28(site!1~cdsb).Ku(dna!1,cs) + DNAPKcs(ku,liIV,psite~u)  -> DNA28(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)` | Transforms DNA28, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 408 | `Unlabeled` | one-way | DNA29, DNAPKcs, Ku | `kdnapk2` | internal-state conversion/modification | `DNA29(site!1~cdsb).Ku(dna!1,cs) + DNAPKcs(ku,liIV,psite~u)  -> DNA29(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)` | Transforms DNA29, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 409 | `Unlabeled` | one-way | DNA30, DNAPKcs, Ku | `kdnapk2` | internal-state conversion/modification | `DNA30(site!1~cdsb).Ku(dna!1,cs) + DNAPKcs(ku,liIV,psite~u)  -> DNA30(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)` | Transforms DNA30, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 410 | `Unlabeled` | one-way | DNA31, DNAPKcs, Ku | `kdnapk2` | internal-state conversion/modification | `DNA31(site!1~cdsb).Ku(dna!1,cs) + DNAPKcs(ku,liIV,psite~u)  -> DNA31(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)` | Transforms DNA31, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 411 | `Unlabeled` | one-way | DNA32, DNAPKcs, Ku | `kdnapk2` | internal-state conversion/modification | `DNA32(site!1~cdsb).Ku(dna!1,cs) + DNAPKcs(ku,liIV,psite~u)  -> DNA32(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)` | Transforms DNA32, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 412 | `Unlabeled` | one-way | DNA33, DNAPKcs, Ku | `kdnapk2` | internal-state conversion/modification | `DNA33(site!1~cdsb).Ku(dna!1,cs) + DNAPKcs(ku,liIV,psite~u)  -> DNA33(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)` | Transforms DNA33, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 413 | `Unlabeled` | one-way | DNA34, DNAPKcs, Ku | `kdnapk2` | internal-state conversion/modification | `DNA34(site!1~cdsb).Ku(dna!1,cs) + DNAPKcs(ku,liIV,psite~u)  -> DNA34(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)` | Transforms DNA34, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 414 | `Unlabeled` | one-way | DNA35, DNAPKcs, Ku | `kdnapk2` | internal-state conversion/modification | `DNA35(site!1~cdsb).Ku(dna!1,cs) + DNAPKcs(ku,liIV,psite~u)  -> DNA35(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)` | Transforms DNA35, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 415 | `Unlabeled` | one-way | DNA36, DNAPKcs, Ku | `kdnapk2` | internal-state conversion/modification | `DNA36(site!1~cdsb).Ku(dna!1,cs) + DNAPKcs(ku,liIV,psite~u)  -> DNA36(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)` | Transforms DNA36, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 416 | `Unlabeled` | one-way | DNA37, DNAPKcs, Ku | `kdnapk2` | internal-state conversion/modification | `DNA37(site!1~cdsb).Ku(dna!1,cs) + DNAPKcs(ku,liIV,psite~u)  -> DNA37(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)` | Transforms DNA37, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 417 | `Unlabeled` | one-way | DNA38, DNAPKcs, Ku | `kdnapk2` | internal-state conversion/modification | `DNA38(site!1~cdsb).Ku(dna!1,cs) + DNAPKcs(ku,liIV,psite~u)  -> DNA38(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)` | Transforms DNA38, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 418 | `Unlabeled` | one-way | DNA39, DNAPKcs, Ku | `kdnapk2` | internal-state conversion/modification | `DNA39(site!1~cdsb).Ku(dna!1,cs) + DNAPKcs(ku,liIV,psite~u)  -> DNA39(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)` | Transforms DNA39, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 419 | `Unlabeled` | one-way | DNA40, DNAPKcs, Ku | `kdnapk2` | internal-state conversion/modification | `DNA40(site!1~cdsb).Ku(dna!1,cs) + DNAPKcs(ku,liIV,psite~u)  -> DNA40(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)` | Transforms DNA40, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 420 | `Unlabeled` | one-way | DNA41, DNAPKcs, Ku | `kdnapk2` | internal-state conversion/modification | `DNA41(site!1~cdsb).Ku(dna!1,cs) + DNAPKcs(ku,liIV,psite~u)  -> DNA41(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)` | Transforms DNA41, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 421 | `Unlabeled` | one-way | DNA42, DNAPKcs, Ku | `kdnapk2` | internal-state conversion/modification | `DNA42(site!1~cdsb).Ku(dna!1,cs) + DNAPKcs(ku,liIV,psite~u)  -> DNA42(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)` | Transforms DNA42, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 422 | `Unlabeled` | one-way | DNA43, DNAPKcs, Ku | `kdnapk2` | internal-state conversion/modification | `DNA43(site!1~cdsb).Ku(dna!1,cs) + DNAPKcs(ku,liIV,psite~u)  -> DNA43(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)` | Transforms DNA43, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 423 | `Unlabeled` | one-way | DNA44, DNAPKcs, Ku | `kdnapk2` | internal-state conversion/modification | `DNA44(site!1~cdsb).Ku(dna!1,cs) + DNAPKcs(ku,liIV,psite~u)  -> DNA44(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)` | Transforms DNA44, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 424 | `Unlabeled` | one-way | DNA45, DNAPKcs, Ku | `kdnapk2` | internal-state conversion/modification | `DNA45(site!1~cdsb).Ku(dna!1,cs) + DNAPKcs(ku,liIV,psite~u)  -> DNA45(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)` | Transforms DNA45, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 425 | `Unlabeled` | one-way | DNA46, DNAPKcs, Ku | `kdnapk2` | internal-state conversion/modification | `DNA46(site!1~cdsb).Ku(dna!1,cs) + DNAPKcs(ku,liIV,psite~u)  -> DNA46(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)` | Transforms DNA46, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 426 | `Unlabeled` | one-way | DNA47, DNAPKcs, Ku | `kdnapk2` | internal-state conversion/modification | `DNA47(site!1~cdsb).Ku(dna!1,cs) + DNAPKcs(ku,liIV,psite~u)  -> DNA47(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)` | Transforms DNA47, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 427 | `Unlabeled` | one-way | DNA48, DNAPKcs, Ku | `kdnapk2` | internal-state conversion/modification | `DNA48(site!1~cdsb).Ku(dna!1,cs) + DNAPKcs(ku,liIV,psite~u)  -> DNA48(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)` | Transforms DNA48, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 428 | `Unlabeled` | one-way | DNA49, DNAPKcs, Ku | `kdnapk2` | internal-state conversion/modification | `DNA49(site!1~cdsb).Ku(dna!1,cs) + DNAPKcs(ku,liIV,psite~u)  -> DNA49(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)` | Transforms DNA49, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 429 | `Unlabeled` | one-way | DNA50, DNAPKcs, Ku | `kdnapk2` | internal-state conversion/modification | `DNA50(site!1~cdsb).Ku(dna!1,cs) + DNAPKcs(ku,liIV,psite~u)  -> DNA50(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)` | Transforms DNA50, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 430 | `Unlabeled` | one-way | DNA1, DNAPKcs, Ku | `kddnapk1` | state and binding-pattern rewrite | `DNA1(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~?)  -> DNA1(site~sdsb) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u)` | Transforms DNA1, DNAPKcs, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 431 | `Unlabeled` | one-way | DNA2, DNAPKcs, Ku | `kddnapk1` | state and binding-pattern rewrite | `DNA2(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~?)  -> DNA2(site~sdsb) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u)` | Transforms DNA2, DNAPKcs, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 432 | `Unlabeled` | one-way | DNA3, DNAPKcs, Ku | `kddnapk1` | state and binding-pattern rewrite | `DNA3(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~?)  -> DNA3(site~sdsb) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u)` | Transforms DNA3, DNAPKcs, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 433 | `Unlabeled` | one-way | DNA4, DNAPKcs, Ku | `kddnapk1` | state and binding-pattern rewrite | `DNA4(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~?)  -> DNA4(site~sdsb) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u)` | Transforms DNA4, DNAPKcs, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 434 | `Unlabeled` | one-way | DNA5, DNAPKcs, Ku | `kddnapk1` | state and binding-pattern rewrite | `DNA5(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~?)  -> DNA5(site~sdsb) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u)` | Transforms DNA5, DNAPKcs, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 435 | `Unlabeled` | one-way | DNA6, DNAPKcs, Ku | `kddnapk1` | state and binding-pattern rewrite | `DNA6(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~?)  -> DNA6(site~sdsb) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u)` | Transforms DNA6, DNAPKcs, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 436 | `Unlabeled` | one-way | DNA7, DNAPKcs, Ku | `kddnapk1` | state and binding-pattern rewrite | `DNA7(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~?)  -> DNA7(site~sdsb) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u)` | Transforms DNA7, DNAPKcs, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 437 | `Unlabeled` | one-way | DNA8, DNAPKcs, Ku | `kddnapk1` | state and binding-pattern rewrite | `DNA8(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~?)  -> DNA8(site~sdsb) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u)` | Transforms DNA8, DNAPKcs, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 438 | `Unlabeled` | one-way | DNA9, DNAPKcs, Ku | `kddnapk1` | state and binding-pattern rewrite | `DNA9(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~?)  -> DNA9(site~sdsb) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u)` | Transforms DNA9, DNAPKcs, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 439 | `Unlabeled` | one-way | DNA10, DNAPKcs, Ku | `kddnapk1` | state and binding-pattern rewrite | `DNA10(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~?)  -> DNA10(site~sdsb) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u)` | Transforms DNA10, DNAPKcs, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 440 | `Unlabeled` | one-way | DNA11, DNAPKcs, Ku | `kddnapk1` | state and binding-pattern rewrite | `DNA11(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~?)  -> DNA11(site~sdsb) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u)` | Transforms DNA11, DNAPKcs, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 441 | `Unlabeled` | one-way | DNA12, DNAPKcs, Ku | `kddnapk1` | state and binding-pattern rewrite | `DNA12(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~?)  -> DNA12(site~sdsb) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u)` | Transforms DNA12, DNAPKcs, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 442 | `Unlabeled` | one-way | DNA13, DNAPKcs, Ku | `kddnapk1` | state and binding-pattern rewrite | `DNA13(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~?)  -> DNA13(site~sdsb) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u)` | Transforms DNA13, DNAPKcs, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 443 | `Unlabeled` | one-way | DNA14, DNAPKcs, Ku | `kddnapk1` | state and binding-pattern rewrite | `DNA14(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~?)  -> DNA14(site~sdsb) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u)` | Transforms DNA14, DNAPKcs, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 444 | `Unlabeled` | one-way | DNA15, DNAPKcs, Ku | `kddnapk1` | state and binding-pattern rewrite | `DNA15(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~?)  -> DNA15(site~sdsb) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u)` | Transforms DNA15, DNAPKcs, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 445 | `Unlabeled` | one-way | DNA16, DNAPKcs, Ku | `kddnapk1` | state and binding-pattern rewrite | `DNA16(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~?)  -> DNA16(site~sdsb) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u)` | Transforms DNA16, DNAPKcs, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 446 | `Unlabeled` | one-way | DNA17, DNAPKcs, Ku | `kddnapk1` | state and binding-pattern rewrite | `DNA17(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~?)  -> DNA17(site~sdsb) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u)` | Transforms DNA17, DNAPKcs, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 447 | `Unlabeled` | one-way | DNA18, DNAPKcs, Ku | `kddnapk1` | state and binding-pattern rewrite | `DNA18(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~?)  -> DNA18(site~sdsb) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u)` | Transforms DNA18, DNAPKcs, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 448 | `Unlabeled` | one-way | DNA19, DNAPKcs, Ku | `kddnapk1` | state and binding-pattern rewrite | `DNA19(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~?)  -> DNA19(site~sdsb) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u)` | Transforms DNA19, DNAPKcs, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 449 | `Unlabeled` | one-way | DNA20, DNAPKcs, Ku | `kddnapk1` | state and binding-pattern rewrite | `DNA20(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~?)  -> DNA20(site~sdsb) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u)` | Transforms DNA20, DNAPKcs, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 450 | `Unlabeled` | one-way | DNA21, DNAPKcs, Ku | `kddnapk1` | state and binding-pattern rewrite | `DNA21(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~?)  -> DNA21(site~sdsb) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u)` | Transforms DNA21, DNAPKcs, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 451 | `Unlabeled` | one-way | DNA22, DNAPKcs, Ku | `kddnapk1` | state and binding-pattern rewrite | `DNA22(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~?)  -> DNA22(site~sdsb) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u)` | Transforms DNA22, DNAPKcs, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 452 | `Unlabeled` | one-way | DNA23, DNAPKcs, Ku | `kddnapk1` | state and binding-pattern rewrite | `DNA23(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~?)  -> DNA23(site~sdsb) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u)` | Transforms DNA23, DNAPKcs, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 453 | `Unlabeled` | one-way | DNA24, DNAPKcs, Ku | `kddnapk1` | state and binding-pattern rewrite | `DNA24(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~?)  -> DNA24(site~sdsb) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u)` | Transforms DNA24, DNAPKcs, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 454 | `Unlabeled` | one-way | DNA25, DNAPKcs, Ku | `kddnapk1` | state and binding-pattern rewrite | `DNA25(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~?)  -> DNA25(site~sdsb) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u)` | Transforms DNA25, DNAPKcs, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 455 | `Unlabeled` | one-way | DNA26, DNAPKcs, Ku | `kddnapk1` | state and binding-pattern rewrite | `DNA26(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~?)  -> DNA26(site~sdsb) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u)` | Transforms DNA26, DNAPKcs, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 456 | `Unlabeled` | one-way | DNA27, DNAPKcs, Ku | `kddnapk1` | state and binding-pattern rewrite | `DNA27(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~?)  -> DNA27(site~sdsb) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u)` | Transforms DNA27, DNAPKcs, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 457 | `Unlabeled` | one-way | DNA28, DNAPKcs, Ku | `kddnapk1` | state and binding-pattern rewrite | `DNA28(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~?)  -> DNA28(site~sdsb) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u)` | Transforms DNA28, DNAPKcs, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 458 | `Unlabeled` | one-way | DNA29, DNAPKcs, Ku | `kddnapk1` | state and binding-pattern rewrite | `DNA29(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~?)  -> DNA29(site~sdsb) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u)` | Transforms DNA29, DNAPKcs, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 459 | `Unlabeled` | one-way | DNA30, DNAPKcs, Ku | `kddnapk1` | state and binding-pattern rewrite | `DNA30(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~?)  -> DNA30(site~sdsb) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u)` | Transforms DNA30, DNAPKcs, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 460 | `Unlabeled` | one-way | DNA31, DNAPKcs, Ku | `kddnapk1` | state and binding-pattern rewrite | `DNA31(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~?)  -> DNA31(site~sdsb) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u)` | Transforms DNA31, DNAPKcs, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 461 | `Unlabeled` | one-way | DNA32, DNAPKcs, Ku | `kddnapk1` | state and binding-pattern rewrite | `DNA32(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~?)  -> DNA32(site~sdsb) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u)` | Transforms DNA32, DNAPKcs, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 462 | `Unlabeled` | one-way | DNA33, DNAPKcs, Ku | `kddnapk1` | state and binding-pattern rewrite | `DNA33(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~?)  -> DNA33(site~sdsb) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u)` | Transforms DNA33, DNAPKcs, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 463 | `Unlabeled` | one-way | DNA34, DNAPKcs, Ku | `kddnapk1` | state and binding-pattern rewrite | `DNA34(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~?)  -> DNA34(site~sdsb) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u)` | Transforms DNA34, DNAPKcs, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 464 | `Unlabeled` | one-way | DNA35, DNAPKcs, Ku | `kddnapk1` | state and binding-pattern rewrite | `DNA35(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~?)  -> DNA35(site~sdsb) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u)` | Transforms DNA35, DNAPKcs, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 465 | `Unlabeled` | one-way | DNA36, DNAPKcs, Ku | `kddnapk1` | state and binding-pattern rewrite | `DNA36(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~?)  -> DNA36(site~sdsb) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u)` | Transforms DNA36, DNAPKcs, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 466 | `Unlabeled` | one-way | DNA37, DNAPKcs, Ku | `kddnapk1` | state and binding-pattern rewrite | `DNA37(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~?)  -> DNA37(site~sdsb) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u)` | Transforms DNA37, DNAPKcs, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 467 | `Unlabeled` | one-way | DNA38, DNAPKcs, Ku | `kddnapk1` | state and binding-pattern rewrite | `DNA38(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~?)  -> DNA38(site~sdsb) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u)` | Transforms DNA38, DNAPKcs, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 468 | `Unlabeled` | one-way | DNA39, DNAPKcs, Ku | `kddnapk1` | state and binding-pattern rewrite | `DNA39(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~?)  -> DNA39(site~sdsb) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u)` | Transforms DNA39, DNAPKcs, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 469 | `Unlabeled` | one-way | DNA40, DNAPKcs, Ku | `kddnapk1` | state and binding-pattern rewrite | `DNA40(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~?)  -> DNA40(site~sdsb) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u)` | Transforms DNA40, DNAPKcs, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 470 | `Unlabeled` | one-way | DNA41, DNAPKcs, Ku | `kddnapk1` | state and binding-pattern rewrite | `DNA41(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~?)  -> DNA41(site~sdsb) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u)` | Transforms DNA41, DNAPKcs, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 471 | `Unlabeled` | one-way | DNA42, DNAPKcs, Ku | `kddnapk1` | state and binding-pattern rewrite | `DNA42(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~?)  -> DNA42(site~sdsb) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u)` | Transforms DNA42, DNAPKcs, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 472 | `Unlabeled` | one-way | DNA43, DNAPKcs, Ku | `kddnapk1` | state and binding-pattern rewrite | `DNA43(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~?)  -> DNA43(site~sdsb) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u)` | Transforms DNA43, DNAPKcs, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 473 | `Unlabeled` | one-way | DNA44, DNAPKcs, Ku | `kddnapk1` | state and binding-pattern rewrite | `DNA44(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~?)  -> DNA44(site~sdsb) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u)` | Transforms DNA44, DNAPKcs, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 474 | `Unlabeled` | one-way | DNA45, DNAPKcs, Ku | `kddnapk1` | state and binding-pattern rewrite | `DNA45(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~?)  -> DNA45(site~sdsb) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u)` | Transforms DNA45, DNAPKcs, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 475 | `Unlabeled` | one-way | DNA46, DNAPKcs, Ku | `kddnapk1` | state and binding-pattern rewrite | `DNA46(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~?)  -> DNA46(site~sdsb) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u)` | Transforms DNA46, DNAPKcs, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 476 | `Unlabeled` | one-way | DNA47, DNAPKcs, Ku | `kddnapk1` | state and binding-pattern rewrite | `DNA47(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~?)  -> DNA47(site~sdsb) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u)` | Transforms DNA47, DNAPKcs, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 477 | `Unlabeled` | one-way | DNA48, DNAPKcs, Ku | `kddnapk1` | state and binding-pattern rewrite | `DNA48(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~?)  -> DNA48(site~sdsb) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u)` | Transforms DNA48, DNAPKcs, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 478 | `Unlabeled` | one-way | DNA49, DNAPKcs, Ku | `kddnapk1` | state and binding-pattern rewrite | `DNA49(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~?)  -> DNA49(site~sdsb) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u)` | Transforms DNA49, DNAPKcs, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 479 | `Unlabeled` | one-way | DNA50, DNAPKcs, Ku | `kddnapk1` | state and binding-pattern rewrite | `DNA50(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~?)  -> DNA50(site~sdsb) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u)` | Transforms DNA50, DNAPKcs, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 480 | `Unlabeled` | one-way | DNA1, DNAPKcs, Ku | `kddnapk2` | state and binding-pattern rewrite | `DNA1(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~?)  -> DNA1(site~cdsb) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u)` | Transforms DNA1, DNAPKcs, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 481 | `Unlabeled` | one-way | DNA2, DNAPKcs, Ku | `kddnapk2` | state and binding-pattern rewrite | `DNA2(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~?)  -> DNA2(site~cdsb) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u)` | Transforms DNA2, DNAPKcs, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 482 | `Unlabeled` | one-way | DNA3, DNAPKcs, Ku | `kddnapk2` | state and binding-pattern rewrite | `DNA3(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~?)  -> DNA3(site~cdsb) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u)` | Transforms DNA3, DNAPKcs, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 483 | `Unlabeled` | one-way | DNA4, DNAPKcs, Ku | `kddnapk2` | state and binding-pattern rewrite | `DNA4(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~?)  -> DNA4(site~cdsb) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u)` | Transforms DNA4, DNAPKcs, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 484 | `Unlabeled` | one-way | DNA5, DNAPKcs, Ku | `kddnapk2` | state and binding-pattern rewrite | `DNA5(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~?)  -> DNA5(site~cdsb) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u)` | Transforms DNA5, DNAPKcs, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 485 | `Unlabeled` | one-way | DNA6, DNAPKcs, Ku | `kddnapk2` | state and binding-pattern rewrite | `DNA6(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~?)  -> DNA6(site~cdsb) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u)` | Transforms DNA6, DNAPKcs, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 486 | `Unlabeled` | one-way | DNA7, DNAPKcs, Ku | `kddnapk2` | state and binding-pattern rewrite | `DNA7(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~?)  -> DNA7(site~cdsb) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u)` | Transforms DNA7, DNAPKcs, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 487 | `Unlabeled` | one-way | DNA8, DNAPKcs, Ku | `kddnapk2` | state and binding-pattern rewrite | `DNA8(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~?)  -> DNA8(site~cdsb) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u)` | Transforms DNA8, DNAPKcs, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 488 | `Unlabeled` | one-way | DNA9, DNAPKcs, Ku | `kddnapk2` | state and binding-pattern rewrite | `DNA9(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~?)  -> DNA9(site~cdsb) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u)` | Transforms DNA9, DNAPKcs, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 489 | `Unlabeled` | one-way | DNA10, DNAPKcs, Ku | `kddnapk2` | state and binding-pattern rewrite | `DNA10(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~?)  -> DNA10(site~cdsb) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u)` | Transforms DNA10, DNAPKcs, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 490 | `Unlabeled` | one-way | DNA11, DNAPKcs, Ku | `kddnapk2` | state and binding-pattern rewrite | `DNA11(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~?)  -> DNA11(site~cdsb) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u)` | Transforms DNA11, DNAPKcs, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 491 | `Unlabeled` | one-way | DNA12, DNAPKcs, Ku | `kddnapk2` | state and binding-pattern rewrite | `DNA12(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~?)  -> DNA12(site~cdsb) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u)` | Transforms DNA12, DNAPKcs, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 492 | `Unlabeled` | one-way | DNA13, DNAPKcs, Ku | `kddnapk2` | state and binding-pattern rewrite | `DNA13(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~?)  -> DNA13(site~cdsb) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u)` | Transforms DNA13, DNAPKcs, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 493 | `Unlabeled` | one-way | DNA14, DNAPKcs, Ku | `kddnapk2` | state and binding-pattern rewrite | `DNA14(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~?)  -> DNA14(site~cdsb) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u)` | Transforms DNA14, DNAPKcs, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 494 | `Unlabeled` | one-way | DNA15, DNAPKcs, Ku | `kddnapk2` | state and binding-pattern rewrite | `DNA15(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~?)  -> DNA15(site~cdsb) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u)` | Transforms DNA15, DNAPKcs, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 495 | `Unlabeled` | one-way | DNA16, DNAPKcs, Ku | `kddnapk2` | state and binding-pattern rewrite | `DNA16(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~?)  -> DNA16(site~cdsb) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u)` | Transforms DNA16, DNAPKcs, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 496 | `Unlabeled` | one-way | DNA17, DNAPKcs, Ku | `kddnapk2` | state and binding-pattern rewrite | `DNA17(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~?)  -> DNA17(site~cdsb) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u)` | Transforms DNA17, DNAPKcs, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 497 | `Unlabeled` | one-way | DNA18, DNAPKcs, Ku | `kddnapk2` | state and binding-pattern rewrite | `DNA18(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~?)  -> DNA18(site~cdsb) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u)` | Transforms DNA18, DNAPKcs, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 498 | `Unlabeled` | one-way | DNA19, DNAPKcs, Ku | `kddnapk2` | state and binding-pattern rewrite | `DNA19(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~?)  -> DNA19(site~cdsb) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u)` | Transforms DNA19, DNAPKcs, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 499 | `Unlabeled` | one-way | DNA20, DNAPKcs, Ku | `kddnapk2` | state and binding-pattern rewrite | `DNA20(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~?)  -> DNA20(site~cdsb) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u)` | Transforms DNA20, DNAPKcs, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 500 | `Unlabeled` | one-way | DNA21, DNAPKcs, Ku | `kddnapk2` | state and binding-pattern rewrite | `DNA21(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~?)  -> DNA21(site~cdsb) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u)` | Transforms DNA21, DNAPKcs, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

### Rules 501-750

| # | Rule label/name | Direction | Participants | Rate/expression | Modeled change | Rule pattern | Technical meaning |
| ---: | --- | --- | --- | --- | --- | --- | --- |

| 501 | `Unlabeled` | one-way | DNA22, DNAPKcs, Ku | `kddnapk2` | state and binding-pattern rewrite | `DNA22(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~?)  -> DNA22(site~cdsb) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u)` | Transforms DNA22, DNAPKcs, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 502 | `Unlabeled` | one-way | DNA23, DNAPKcs, Ku | `kddnapk2` | state and binding-pattern rewrite | `DNA23(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~?)  -> DNA23(site~cdsb) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u)` | Transforms DNA23, DNAPKcs, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 503 | `Unlabeled` | one-way | DNA24, DNAPKcs, Ku | `kddnapk2` | state and binding-pattern rewrite | `DNA24(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~?)  -> DNA24(site~cdsb) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u)` | Transforms DNA24, DNAPKcs, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 504 | `Unlabeled` | one-way | DNA25, DNAPKcs, Ku | `kddnapk2` | state and binding-pattern rewrite | `DNA25(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~?)  -> DNA25(site~cdsb) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u)` | Transforms DNA25, DNAPKcs, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 505 | `Unlabeled` | one-way | DNA26, DNAPKcs, Ku | `kddnapk2` | state and binding-pattern rewrite | `DNA26(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~?)  -> DNA26(site~cdsb) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u)` | Transforms DNA26, DNAPKcs, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 506 | `Unlabeled` | one-way | DNA27, DNAPKcs, Ku | `kddnapk2` | state and binding-pattern rewrite | `DNA27(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~?)  -> DNA27(site~cdsb) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u)` | Transforms DNA27, DNAPKcs, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 507 | `Unlabeled` | one-way | DNA28, DNAPKcs, Ku | `kddnapk2` | state and binding-pattern rewrite | `DNA28(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~?)  -> DNA28(site~cdsb) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u)` | Transforms DNA28, DNAPKcs, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 508 | `Unlabeled` | one-way | DNA29, DNAPKcs, Ku | `kddnapk2` | state and binding-pattern rewrite | `DNA29(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~?)  -> DNA29(site~cdsb) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u)` | Transforms DNA29, DNAPKcs, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 509 | `Unlabeled` | one-way | DNA30, DNAPKcs, Ku | `kddnapk2` | state and binding-pattern rewrite | `DNA30(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~?)  -> DNA30(site~cdsb) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u)` | Transforms DNA30, DNAPKcs, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 510 | `Unlabeled` | one-way | DNA31, DNAPKcs, Ku | `kddnapk2` | state and binding-pattern rewrite | `DNA31(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~?)  -> DNA31(site~cdsb) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u)` | Transforms DNA31, DNAPKcs, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 511 | `Unlabeled` | one-way | DNA32, DNAPKcs, Ku | `kddnapk2` | state and binding-pattern rewrite | `DNA32(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~?)  -> DNA32(site~cdsb) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u)` | Transforms DNA32, DNAPKcs, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 512 | `Unlabeled` | one-way | DNA33, DNAPKcs, Ku | `kddnapk2` | state and binding-pattern rewrite | `DNA33(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~?)  -> DNA33(site~cdsb) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u)` | Transforms DNA33, DNAPKcs, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 513 | `Unlabeled` | one-way | DNA34, DNAPKcs, Ku | `kddnapk2` | state and binding-pattern rewrite | `DNA34(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~?)  -> DNA34(site~cdsb) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u)` | Transforms DNA34, DNAPKcs, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 514 | `Unlabeled` | one-way | DNA35, DNAPKcs, Ku | `kddnapk2` | state and binding-pattern rewrite | `DNA35(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~?)  -> DNA35(site~cdsb) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u)` | Transforms DNA35, DNAPKcs, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 515 | `Unlabeled` | one-way | DNA36, DNAPKcs, Ku | `kddnapk2` | state and binding-pattern rewrite | `DNA36(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~?)  -> DNA36(site~cdsb) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u)` | Transforms DNA36, DNAPKcs, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 516 | `Unlabeled` | one-way | DNA37, DNAPKcs, Ku | `kddnapk2` | state and binding-pattern rewrite | `DNA37(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~?)  -> DNA37(site~cdsb) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u)` | Transforms DNA37, DNAPKcs, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 517 | `Unlabeled` | one-way | DNA38, DNAPKcs, Ku | `kddnapk2` | state and binding-pattern rewrite | `DNA38(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~?)  -> DNA38(site~cdsb) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u)` | Transforms DNA38, DNAPKcs, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 518 | `Unlabeled` | one-way | DNA39, DNAPKcs, Ku | `kddnapk2` | state and binding-pattern rewrite | `DNA39(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~?)  -> DNA39(site~cdsb) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u)` | Transforms DNA39, DNAPKcs, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 519 | `Unlabeled` | one-way | DNA40, DNAPKcs, Ku | `kddnapk2` | state and binding-pattern rewrite | `DNA40(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~?)  -> DNA40(site~cdsb) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u)` | Transforms DNA40, DNAPKcs, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 520 | `Unlabeled` | one-way | DNA41, DNAPKcs, Ku | `kddnapk2` | state and binding-pattern rewrite | `DNA41(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~?)  -> DNA41(site~cdsb) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u)` | Transforms DNA41, DNAPKcs, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 521 | `Unlabeled` | one-way | DNA42, DNAPKcs, Ku | `kddnapk2` | state and binding-pattern rewrite | `DNA42(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~?)  -> DNA42(site~cdsb) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u)` | Transforms DNA42, DNAPKcs, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 522 | `Unlabeled` | one-way | DNA43, DNAPKcs, Ku | `kddnapk2` | state and binding-pattern rewrite | `DNA43(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~?)  -> DNA43(site~cdsb) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u)` | Transforms DNA43, DNAPKcs, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 523 | `Unlabeled` | one-way | DNA44, DNAPKcs, Ku | `kddnapk2` | state and binding-pattern rewrite | `DNA44(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~?)  -> DNA44(site~cdsb) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u)` | Transforms DNA44, DNAPKcs, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 524 | `Unlabeled` | one-way | DNA45, DNAPKcs, Ku | `kddnapk2` | state and binding-pattern rewrite | `DNA45(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~?)  -> DNA45(site~cdsb) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u)` | Transforms DNA45, DNAPKcs, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 525 | `Unlabeled` | one-way | DNA46, DNAPKcs, Ku | `kddnapk2` | state and binding-pattern rewrite | `DNA46(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~?)  -> DNA46(site~cdsb) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u)` | Transforms DNA46, DNAPKcs, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 526 | `Unlabeled` | one-way | DNA47, DNAPKcs, Ku | `kddnapk2` | state and binding-pattern rewrite | `DNA47(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~?)  -> DNA47(site~cdsb) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u)` | Transforms DNA47, DNAPKcs, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 527 | `Unlabeled` | one-way | DNA48, DNAPKcs, Ku | `kddnapk2` | state and binding-pattern rewrite | `DNA48(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~?)  -> DNA48(site~cdsb) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u)` | Transforms DNA48, DNAPKcs, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 528 | `Unlabeled` | one-way | DNA49, DNAPKcs, Ku | `kddnapk2` | state and binding-pattern rewrite | `DNA49(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~?)  -> DNA49(site~cdsb) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u)` | Transforms DNA49, DNAPKcs, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 529 | `Unlabeled` | one-way | DNA50, DNAPKcs, Ku | `kddnapk2` | state and binding-pattern rewrite | `DNA50(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~?)  -> DNA50(site~cdsb) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u)` | Transforms DNA50, DNAPKcs, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 530 | `Unlabeled` | one-way | DNA1, DNAPKcs, Ku | `kdnapkphos1` | internal-state conversion/modification | `DNA1(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)  -> DNA1(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA1, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 531 | `Unlabeled` | one-way | DNA2, DNAPKcs, Ku | `kdnapkphos1` | internal-state conversion/modification | `DNA2(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)  -> DNA2(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA2, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 532 | `Unlabeled` | one-way | DNA3, DNAPKcs, Ku | `kdnapkphos1` | internal-state conversion/modification | `DNA3(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)  -> DNA3(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA3, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 533 | `Unlabeled` | one-way | DNA4, DNAPKcs, Ku | `kdnapkphos1` | internal-state conversion/modification | `DNA4(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)  -> DNA4(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA4, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 534 | `Unlabeled` | one-way | DNA5, DNAPKcs, Ku | `kdnapkphos1` | internal-state conversion/modification | `DNA5(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)  -> DNA5(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA5, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 535 | `Unlabeled` | one-way | DNA6, DNAPKcs, Ku | `kdnapkphos1` | internal-state conversion/modification | `DNA6(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)  -> DNA6(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA6, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 536 | `Unlabeled` | one-way | DNA7, DNAPKcs, Ku | `kdnapkphos1` | internal-state conversion/modification | `DNA7(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)  -> DNA7(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA7, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 537 | `Unlabeled` | one-way | DNA8, DNAPKcs, Ku | `kdnapkphos1` | internal-state conversion/modification | `DNA8(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)  -> DNA8(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA8, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 538 | `Unlabeled` | one-way | DNA9, DNAPKcs, Ku | `kdnapkphos1` | internal-state conversion/modification | `DNA9(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)  -> DNA9(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA9, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 539 | `Unlabeled` | one-way | DNA10, DNAPKcs, Ku | `kdnapkphos1` | internal-state conversion/modification | `DNA10(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)  -> DNA10(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA10, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 540 | `Unlabeled` | one-way | DNA11, DNAPKcs, Ku | `kdnapkphos1` | internal-state conversion/modification | `DNA11(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)  -> DNA11(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA11, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 541 | `Unlabeled` | one-way | DNA12, DNAPKcs, Ku | `kdnapkphos1` | internal-state conversion/modification | `DNA12(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)  -> DNA12(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA12, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 542 | `Unlabeled` | one-way | DNA13, DNAPKcs, Ku | `kdnapkphos1` | internal-state conversion/modification | `DNA13(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)  -> DNA13(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA13, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 543 | `Unlabeled` | one-way | DNA14, DNAPKcs, Ku | `kdnapkphos1` | internal-state conversion/modification | `DNA14(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)  -> DNA14(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA14, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 544 | `Unlabeled` | one-way | DNA15, DNAPKcs, Ku | `kdnapkphos1` | internal-state conversion/modification | `DNA15(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)  -> DNA15(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA15, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 545 | `Unlabeled` | one-way | DNA16, DNAPKcs, Ku | `kdnapkphos1` | internal-state conversion/modification | `DNA16(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)  -> DNA16(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA16, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 546 | `Unlabeled` | one-way | DNA17, DNAPKcs, Ku | `kdnapkphos1` | internal-state conversion/modification | `DNA17(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)  -> DNA17(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA17, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 547 | `Unlabeled` | one-way | DNA18, DNAPKcs, Ku | `kdnapkphos1` | internal-state conversion/modification | `DNA18(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)  -> DNA18(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA18, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 548 | `Unlabeled` | one-way | DNA19, DNAPKcs, Ku | `kdnapkphos1` | internal-state conversion/modification | `DNA19(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)  -> DNA19(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA19, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 549 | `Unlabeled` | one-way | DNA20, DNAPKcs, Ku | `kdnapkphos1` | internal-state conversion/modification | `DNA20(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)  -> DNA20(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA20, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 550 | `Unlabeled` | one-way | DNA21, DNAPKcs, Ku | `kdnapkphos1` | internal-state conversion/modification | `DNA21(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)  -> DNA21(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA21, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 551 | `Unlabeled` | one-way | DNA22, DNAPKcs, Ku | `kdnapkphos1` | internal-state conversion/modification | `DNA22(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)  -> DNA22(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA22, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 552 | `Unlabeled` | one-way | DNA23, DNAPKcs, Ku | `kdnapkphos1` | internal-state conversion/modification | `DNA23(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)  -> DNA23(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA23, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 553 | `Unlabeled` | one-way | DNA24, DNAPKcs, Ku | `kdnapkphos1` | internal-state conversion/modification | `DNA24(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)  -> DNA24(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA24, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 554 | `Unlabeled` | one-way | DNA25, DNAPKcs, Ku | `kdnapkphos1` | internal-state conversion/modification | `DNA25(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)  -> DNA25(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA25, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 555 | `Unlabeled` | one-way | DNA26, DNAPKcs, Ku | `kdnapkphos1` | internal-state conversion/modification | `DNA26(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)  -> DNA26(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA26, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 556 | `Unlabeled` | one-way | DNA27, DNAPKcs, Ku | `kdnapkphos1` | internal-state conversion/modification | `DNA27(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)  -> DNA27(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA27, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 557 | `Unlabeled` | one-way | DNA28, DNAPKcs, Ku | `kdnapkphos1` | internal-state conversion/modification | `DNA28(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)  -> DNA28(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA28, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 558 | `Unlabeled` | one-way | DNA29, DNAPKcs, Ku | `kdnapkphos1` | internal-state conversion/modification | `DNA29(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)  -> DNA29(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA29, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 559 | `Unlabeled` | one-way | DNA30, DNAPKcs, Ku | `kdnapkphos1` | internal-state conversion/modification | `DNA30(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)  -> DNA30(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA30, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 560 | `Unlabeled` | one-way | DNA31, DNAPKcs, Ku | `kdnapkphos1` | internal-state conversion/modification | `DNA31(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)  -> DNA31(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA31, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 561 | `Unlabeled` | one-way | DNA32, DNAPKcs, Ku | `kdnapkphos1` | internal-state conversion/modification | `DNA32(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)  -> DNA32(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA32, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 562 | `Unlabeled` | one-way | DNA33, DNAPKcs, Ku | `kdnapkphos1` | internal-state conversion/modification | `DNA33(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)  -> DNA33(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA33, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 563 | `Unlabeled` | one-way | DNA34, DNAPKcs, Ku | `kdnapkphos1` | internal-state conversion/modification | `DNA34(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)  -> DNA34(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA34, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 564 | `Unlabeled` | one-way | DNA35, DNAPKcs, Ku | `kdnapkphos1` | internal-state conversion/modification | `DNA35(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)  -> DNA35(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA35, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 565 | `Unlabeled` | one-way | DNA36, DNAPKcs, Ku | `kdnapkphos1` | internal-state conversion/modification | `DNA36(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)  -> DNA36(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA36, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 566 | `Unlabeled` | one-way | DNA37, DNAPKcs, Ku | `kdnapkphos1` | internal-state conversion/modification | `DNA37(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)  -> DNA37(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA37, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 567 | `Unlabeled` | one-way | DNA38, DNAPKcs, Ku | `kdnapkphos1` | internal-state conversion/modification | `DNA38(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)  -> DNA38(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA38, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 568 | `Unlabeled` | one-way | DNA39, DNAPKcs, Ku | `kdnapkphos1` | internal-state conversion/modification | `DNA39(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)  -> DNA39(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA39, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 569 | `Unlabeled` | one-way | DNA40, DNAPKcs, Ku | `kdnapkphos1` | internal-state conversion/modification | `DNA40(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)  -> DNA40(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA40, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 570 | `Unlabeled` | one-way | DNA41, DNAPKcs, Ku | `kdnapkphos1` | internal-state conversion/modification | `DNA41(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)  -> DNA41(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA41, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 571 | `Unlabeled` | one-way | DNA42, DNAPKcs, Ku | `kdnapkphos1` | internal-state conversion/modification | `DNA42(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)  -> DNA42(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA42, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 572 | `Unlabeled` | one-way | DNA43, DNAPKcs, Ku | `kdnapkphos1` | internal-state conversion/modification | `DNA43(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)  -> DNA43(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA43, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 573 | `Unlabeled` | one-way | DNA44, DNAPKcs, Ku | `kdnapkphos1` | internal-state conversion/modification | `DNA44(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)  -> DNA44(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA44, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 574 | `Unlabeled` | one-way | DNA45, DNAPKcs, Ku | `kdnapkphos1` | internal-state conversion/modification | `DNA45(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)  -> DNA45(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA45, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 575 | `Unlabeled` | one-way | DNA46, DNAPKcs, Ku | `kdnapkphos1` | internal-state conversion/modification | `DNA46(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)  -> DNA46(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA46, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 576 | `Unlabeled` | one-way | DNA47, DNAPKcs, Ku | `kdnapkphos1` | internal-state conversion/modification | `DNA47(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)  -> DNA47(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA47, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 577 | `Unlabeled` | one-way | DNA48, DNAPKcs, Ku | `kdnapkphos1` | internal-state conversion/modification | `DNA48(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)  -> DNA48(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA48, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 578 | `Unlabeled` | one-way | DNA49, DNAPKcs, Ku | `kdnapkphos1` | internal-state conversion/modification | `DNA49(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)  -> DNA49(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA49, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 579 | `Unlabeled` | one-way | DNA50, DNAPKcs, Ku | `kdnapkphos1` | internal-state conversion/modification | `DNA50(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)  -> DNA50(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA50, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 580 | `Unlabeled` | one-way | DNA1, DNAPKcs, Ku | `kdnapkphos2` | internal-state conversion/modification | `DNA1(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)  -> DNA1(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA1, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 581 | `Unlabeled` | one-way | DNA2, DNAPKcs, Ku | `kdnapkphos2` | internal-state conversion/modification | `DNA2(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)  -> DNA2(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA2, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 582 | `Unlabeled` | one-way | DNA3, DNAPKcs, Ku | `kdnapkphos2` | internal-state conversion/modification | `DNA3(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)  -> DNA3(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA3, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 583 | `Unlabeled` | one-way | DNA4, DNAPKcs, Ku | `kdnapkphos2` | internal-state conversion/modification | `DNA4(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)  -> DNA4(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA4, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 584 | `Unlabeled` | one-way | DNA5, DNAPKcs, Ku | `kdnapkphos2` | internal-state conversion/modification | `DNA5(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)  -> DNA5(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA5, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 585 | `Unlabeled` | one-way | DNA6, DNAPKcs, Ku | `kdnapkphos2` | internal-state conversion/modification | `DNA6(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)  -> DNA6(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA6, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 586 | `Unlabeled` | one-way | DNA7, DNAPKcs, Ku | `kdnapkphos2` | internal-state conversion/modification | `DNA7(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)  -> DNA7(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA7, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 587 | `Unlabeled` | one-way | DNA8, DNAPKcs, Ku | `kdnapkphos2` | internal-state conversion/modification | `DNA8(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)  -> DNA8(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA8, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 588 | `Unlabeled` | one-way | DNA9, DNAPKcs, Ku | `kdnapkphos2` | internal-state conversion/modification | `DNA9(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)  -> DNA9(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA9, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 589 | `Unlabeled` | one-way | DNA10, DNAPKcs, Ku | `kdnapkphos2` | internal-state conversion/modification | `DNA10(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)  -> DNA10(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA10, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 590 | `Unlabeled` | one-way | DNA11, DNAPKcs, Ku | `kdnapkphos2` | internal-state conversion/modification | `DNA11(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)  -> DNA11(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA11, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 591 | `Unlabeled` | one-way | DNA12, DNAPKcs, Ku | `kdnapkphos2` | internal-state conversion/modification | `DNA12(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)  -> DNA12(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA12, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 592 | `Unlabeled` | one-way | DNA13, DNAPKcs, Ku | `kdnapkphos2` | internal-state conversion/modification | `DNA13(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)  -> DNA13(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA13, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 593 | `Unlabeled` | one-way | DNA14, DNAPKcs, Ku | `kdnapkphos2` | internal-state conversion/modification | `DNA14(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)  -> DNA14(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA14, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 594 | `Unlabeled` | one-way | DNA15, DNAPKcs, Ku | `kdnapkphos2` | internal-state conversion/modification | `DNA15(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)  -> DNA15(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA15, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 595 | `Unlabeled` | one-way | DNA16, DNAPKcs, Ku | `kdnapkphos2` | internal-state conversion/modification | `DNA16(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)  -> DNA16(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA16, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 596 | `Unlabeled` | one-way | DNA17, DNAPKcs, Ku | `kdnapkphos2` | internal-state conversion/modification | `DNA17(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)  -> DNA17(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA17, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 597 | `Unlabeled` | one-way | DNA18, DNAPKcs, Ku | `kdnapkphos2` | internal-state conversion/modification | `DNA18(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)  -> DNA18(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA18, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 598 | `Unlabeled` | one-way | DNA19, DNAPKcs, Ku | `kdnapkphos2` | internal-state conversion/modification | `DNA19(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)  -> DNA19(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA19, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 599 | `Unlabeled` | one-way | DNA20, DNAPKcs, Ku | `kdnapkphos2` | internal-state conversion/modification | `DNA20(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)  -> DNA20(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA20, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 600 | `Unlabeled` | one-way | DNA21, DNAPKcs, Ku | `kdnapkphos2` | internal-state conversion/modification | `DNA21(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)  -> DNA21(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA21, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 601 | `Unlabeled` | one-way | DNA22, DNAPKcs, Ku | `kdnapkphos2` | internal-state conversion/modification | `DNA22(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)  -> DNA22(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA22, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 602 | `Unlabeled` | one-way | DNA23, DNAPKcs, Ku | `kdnapkphos2` | internal-state conversion/modification | `DNA23(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)  -> DNA23(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA23, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 603 | `Unlabeled` | one-way | DNA24, DNAPKcs, Ku | `kdnapkphos2` | internal-state conversion/modification | `DNA24(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)  -> DNA24(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA24, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 604 | `Unlabeled` | one-way | DNA25, DNAPKcs, Ku | `kdnapkphos2` | internal-state conversion/modification | `DNA25(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)  -> DNA25(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA25, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 605 | `Unlabeled` | one-way | DNA26, DNAPKcs, Ku | `kdnapkphos2` | internal-state conversion/modification | `DNA26(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)  -> DNA26(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA26, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 606 | `Unlabeled` | one-way | DNA27, DNAPKcs, Ku | `kdnapkphos2` | internal-state conversion/modification | `DNA27(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)  -> DNA27(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA27, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 607 | `Unlabeled` | one-way | DNA28, DNAPKcs, Ku | `kdnapkphos2` | internal-state conversion/modification | `DNA28(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)  -> DNA28(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA28, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 608 | `Unlabeled` | one-way | DNA29, DNAPKcs, Ku | `kdnapkphos2` | internal-state conversion/modification | `DNA29(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)  -> DNA29(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA29, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 609 | `Unlabeled` | one-way | DNA30, DNAPKcs, Ku | `kdnapkphos2` | internal-state conversion/modification | `DNA30(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)  -> DNA30(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA30, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 610 | `Unlabeled` | one-way | DNA31, DNAPKcs, Ku | `kdnapkphos2` | internal-state conversion/modification | `DNA31(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)  -> DNA31(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA31, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 611 | `Unlabeled` | one-way | DNA32, DNAPKcs, Ku | `kdnapkphos2` | internal-state conversion/modification | `DNA32(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)  -> DNA32(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA32, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 612 | `Unlabeled` | one-way | DNA33, DNAPKcs, Ku | `kdnapkphos2` | internal-state conversion/modification | `DNA33(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)  -> DNA33(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA33, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 613 | `Unlabeled` | one-way | DNA34, DNAPKcs, Ku | `kdnapkphos2` | internal-state conversion/modification | `DNA34(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)  -> DNA34(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA34, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 614 | `Unlabeled` | one-way | DNA35, DNAPKcs, Ku | `kdnapkphos2` | internal-state conversion/modification | `DNA35(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)  -> DNA35(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA35, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 615 | `Unlabeled` | one-way | DNA36, DNAPKcs, Ku | `kdnapkphos2` | internal-state conversion/modification | `DNA36(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)  -> DNA36(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA36, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 616 | `Unlabeled` | one-way | DNA37, DNAPKcs, Ku | `kdnapkphos2` | internal-state conversion/modification | `DNA37(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)  -> DNA37(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA37, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 617 | `Unlabeled` | one-way | DNA38, DNAPKcs, Ku | `kdnapkphos2` | internal-state conversion/modification | `DNA38(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)  -> DNA38(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA38, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 618 | `Unlabeled` | one-way | DNA39, DNAPKcs, Ku | `kdnapkphos2` | internal-state conversion/modification | `DNA39(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)  -> DNA39(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA39, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 619 | `Unlabeled` | one-way | DNA40, DNAPKcs, Ku | `kdnapkphos2` | internal-state conversion/modification | `DNA40(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)  -> DNA40(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA40, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 620 | `Unlabeled` | one-way | DNA41, DNAPKcs, Ku | `kdnapkphos2` | internal-state conversion/modification | `DNA41(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)  -> DNA41(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA41, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 621 | `Unlabeled` | one-way | DNA42, DNAPKcs, Ku | `kdnapkphos2` | internal-state conversion/modification | `DNA42(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)  -> DNA42(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA42, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 622 | `Unlabeled` | one-way | DNA43, DNAPKcs, Ku | `kdnapkphos2` | internal-state conversion/modification | `DNA43(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)  -> DNA43(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA43, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 623 | `Unlabeled` | one-way | DNA44, DNAPKcs, Ku | `kdnapkphos2` | internal-state conversion/modification | `DNA44(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)  -> DNA44(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA44, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 624 | `Unlabeled` | one-way | DNA45, DNAPKcs, Ku | `kdnapkphos2` | internal-state conversion/modification | `DNA45(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)  -> DNA45(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA45, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 625 | `Unlabeled` | one-way | DNA46, DNAPKcs, Ku | `kdnapkphos2` | internal-state conversion/modification | `DNA46(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)  -> DNA46(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA46, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 626 | `Unlabeled` | one-way | DNA47, DNAPKcs, Ku | `kdnapkphos2` | internal-state conversion/modification | `DNA47(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)  -> DNA47(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA47, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 627 | `Unlabeled` | one-way | DNA48, DNAPKcs, Ku | `kdnapkphos2` | internal-state conversion/modification | `DNA48(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)  -> DNA48(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA48, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 628 | `Unlabeled` | one-way | DNA49, DNAPKcs, Ku | `kdnapkphos2` | internal-state conversion/modification | `DNA49(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)  -> DNA49(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA49, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 629 | `Unlabeled` | one-way | DNA50, DNAPKcs, Ku | `kdnapkphos2` | internal-state conversion/modification | `DNA50(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~u)  -> DNA50(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA50, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 630 | `Unlabeled` | one-way | DNA1, DNAPKcs, Ku, LiIV | `kliIV1` | internal-state conversion/modification | `DNA1(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)  -> DNA1(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)` | Transforms DNA1, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 631 | `Unlabeled` | one-way | DNA2, DNAPKcs, Ku, LiIV | `kliIV1` | internal-state conversion/modification | `DNA2(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)  -> DNA2(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)` | Transforms DNA2, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 632 | `Unlabeled` | one-way | DNA3, DNAPKcs, Ku, LiIV | `kliIV1` | internal-state conversion/modification | `DNA3(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)  -> DNA3(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)` | Transforms DNA3, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 633 | `Unlabeled` | one-way | DNA4, DNAPKcs, Ku, LiIV | `kliIV1` | internal-state conversion/modification | `DNA4(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)  -> DNA4(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)` | Transforms DNA4, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 634 | `Unlabeled` | one-way | DNA5, DNAPKcs, Ku, LiIV | `kliIV1` | internal-state conversion/modification | `DNA5(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)  -> DNA5(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)` | Transforms DNA5, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 635 | `Unlabeled` | one-way | DNA6, DNAPKcs, Ku, LiIV | `kliIV1` | internal-state conversion/modification | `DNA6(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)  -> DNA6(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)` | Transforms DNA6, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 636 | `Unlabeled` | one-way | DNA7, DNAPKcs, Ku, LiIV | `kliIV1` | internal-state conversion/modification | `DNA7(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)  -> DNA7(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)` | Transforms DNA7, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 637 | `Unlabeled` | one-way | DNA8, DNAPKcs, Ku, LiIV | `kliIV1` | internal-state conversion/modification | `DNA8(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)  -> DNA8(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)` | Transforms DNA8, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 638 | `Unlabeled` | one-way | DNA9, DNAPKcs, Ku, LiIV | `kliIV1` | internal-state conversion/modification | `DNA9(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)  -> DNA9(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)` | Transforms DNA9, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 639 | `Unlabeled` | one-way | DNA10, DNAPKcs, Ku, LiIV | `kliIV1` | internal-state conversion/modification | `DNA10(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)  -> DNA10(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)` | Transforms DNA10, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 640 | `Unlabeled` | one-way | DNA11, DNAPKcs, Ku, LiIV | `kliIV1` | internal-state conversion/modification | `DNA11(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)  -> DNA11(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)` | Transforms DNA11, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 641 | `Unlabeled` | one-way | DNA12, DNAPKcs, Ku, LiIV | `kliIV1` | internal-state conversion/modification | `DNA12(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)  -> DNA12(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)` | Transforms DNA12, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 642 | `Unlabeled` | one-way | DNA13, DNAPKcs, Ku, LiIV | `kliIV1` | internal-state conversion/modification | `DNA13(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)  -> DNA13(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)` | Transforms DNA13, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 643 | `Unlabeled` | one-way | DNA14, DNAPKcs, Ku, LiIV | `kliIV1` | internal-state conversion/modification | `DNA14(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)  -> DNA14(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)` | Transforms DNA14, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 644 | `Unlabeled` | one-way | DNA15, DNAPKcs, Ku, LiIV | `kliIV1` | internal-state conversion/modification | `DNA15(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)  -> DNA15(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)` | Transforms DNA15, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 645 | `Unlabeled` | one-way | DNA16, DNAPKcs, Ku, LiIV | `kliIV1` | internal-state conversion/modification | `DNA16(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)  -> DNA16(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)` | Transforms DNA16, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 646 | `Unlabeled` | one-way | DNA17, DNAPKcs, Ku, LiIV | `kliIV1` | internal-state conversion/modification | `DNA17(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)  -> DNA17(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)` | Transforms DNA17, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 647 | `Unlabeled` | one-way | DNA18, DNAPKcs, Ku, LiIV | `kliIV1` | internal-state conversion/modification | `DNA18(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)  -> DNA18(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)` | Transforms DNA18, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 648 | `Unlabeled` | one-way | DNA19, DNAPKcs, Ku, LiIV | `kliIV1` | internal-state conversion/modification | `DNA19(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)  -> DNA19(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)` | Transforms DNA19, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 649 | `Unlabeled` | one-way | DNA20, DNAPKcs, Ku, LiIV | `kliIV1` | internal-state conversion/modification | `DNA20(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)  -> DNA20(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)` | Transforms DNA20, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 650 | `Unlabeled` | one-way | DNA21, DNAPKcs, Ku, LiIV | `kliIV1` | internal-state conversion/modification | `DNA21(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)  -> DNA21(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)` | Transforms DNA21, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 651 | `Unlabeled` | one-way | DNA22, DNAPKcs, Ku, LiIV | `kliIV1` | internal-state conversion/modification | `DNA22(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)  -> DNA22(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)` | Transforms DNA22, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 652 | `Unlabeled` | one-way | DNA23, DNAPKcs, Ku, LiIV | `kliIV1` | internal-state conversion/modification | `DNA23(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)  -> DNA23(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)` | Transforms DNA23, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 653 | `Unlabeled` | one-way | DNA24, DNAPKcs, Ku, LiIV | `kliIV1` | internal-state conversion/modification | `DNA24(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)  -> DNA24(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)` | Transforms DNA24, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 654 | `Unlabeled` | one-way | DNA25, DNAPKcs, Ku, LiIV | `kliIV1` | internal-state conversion/modification | `DNA25(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)  -> DNA25(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)` | Transforms DNA25, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 655 | `Unlabeled` | one-way | DNA26, DNAPKcs, Ku, LiIV | `kliIV1` | internal-state conversion/modification | `DNA26(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)  -> DNA26(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)` | Transforms DNA26, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 656 | `Unlabeled` | one-way | DNA27, DNAPKcs, Ku, LiIV | `kliIV1` | internal-state conversion/modification | `DNA27(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)  -> DNA27(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)` | Transforms DNA27, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 657 | `Unlabeled` | one-way | DNA28, DNAPKcs, Ku, LiIV | `kliIV1` | internal-state conversion/modification | `DNA28(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)  -> DNA28(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)` | Transforms DNA28, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 658 | `Unlabeled` | one-way | DNA29, DNAPKcs, Ku, LiIV | `kliIV1` | internal-state conversion/modification | `DNA29(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)  -> DNA29(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)` | Transforms DNA29, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 659 | `Unlabeled` | one-way | DNA30, DNAPKcs, Ku, LiIV | `kliIV1` | internal-state conversion/modification | `DNA30(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)  -> DNA30(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)` | Transforms DNA30, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 660 | `Unlabeled` | one-way | DNA31, DNAPKcs, Ku, LiIV | `kliIV1` | internal-state conversion/modification | `DNA31(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)  -> DNA31(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)` | Transforms DNA31, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 661 | `Unlabeled` | one-way | DNA32, DNAPKcs, Ku, LiIV | `kliIV1` | internal-state conversion/modification | `DNA32(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)  -> DNA32(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)` | Transforms DNA32, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 662 | `Unlabeled` | one-way | DNA33, DNAPKcs, Ku, LiIV | `kliIV1` | internal-state conversion/modification | `DNA33(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)  -> DNA33(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)` | Transforms DNA33, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 663 | `Unlabeled` | one-way | DNA34, DNAPKcs, Ku, LiIV | `kliIV1` | internal-state conversion/modification | `DNA34(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)  -> DNA34(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)` | Transforms DNA34, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 664 | `Unlabeled` | one-way | DNA35, DNAPKcs, Ku, LiIV | `kliIV1` | internal-state conversion/modification | `DNA35(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)  -> DNA35(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)` | Transforms DNA35, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 665 | `Unlabeled` | one-way | DNA36, DNAPKcs, Ku, LiIV | `kliIV1` | internal-state conversion/modification | `DNA36(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)  -> DNA36(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)` | Transforms DNA36, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 666 | `Unlabeled` | one-way | DNA37, DNAPKcs, Ku, LiIV | `kliIV1` | internal-state conversion/modification | `DNA37(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)  -> DNA37(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)` | Transforms DNA37, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 667 | `Unlabeled` | one-way | DNA38, DNAPKcs, Ku, LiIV | `kliIV1` | internal-state conversion/modification | `DNA38(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)  -> DNA38(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)` | Transforms DNA38, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 668 | `Unlabeled` | one-way | DNA39, DNAPKcs, Ku, LiIV | `kliIV1` | internal-state conversion/modification | `DNA39(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)  -> DNA39(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)` | Transforms DNA39, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 669 | `Unlabeled` | one-way | DNA40, DNAPKcs, Ku, LiIV | `kliIV1` | internal-state conversion/modification | `DNA40(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)  -> DNA40(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)` | Transforms DNA40, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 670 | `Unlabeled` | one-way | DNA41, DNAPKcs, Ku, LiIV | `kliIV1` | internal-state conversion/modification | `DNA41(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)  -> DNA41(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)` | Transforms DNA41, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 671 | `Unlabeled` | one-way | DNA42, DNAPKcs, Ku, LiIV | `kliIV1` | internal-state conversion/modification | `DNA42(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)  -> DNA42(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)` | Transforms DNA42, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 672 | `Unlabeled` | one-way | DNA43, DNAPKcs, Ku, LiIV | `kliIV1` | internal-state conversion/modification | `DNA43(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)  -> DNA43(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)` | Transforms DNA43, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 673 | `Unlabeled` | one-way | DNA44, DNAPKcs, Ku, LiIV | `kliIV1` | internal-state conversion/modification | `DNA44(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)  -> DNA44(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)` | Transforms DNA44, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 674 | `Unlabeled` | one-way | DNA45, DNAPKcs, Ku, LiIV | `kliIV1` | internal-state conversion/modification | `DNA45(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)  -> DNA45(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)` | Transforms DNA45, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 675 | `Unlabeled` | one-way | DNA46, DNAPKcs, Ku, LiIV | `kliIV1` | internal-state conversion/modification | `DNA46(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)  -> DNA46(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)` | Transforms DNA46, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 676 | `Unlabeled` | one-way | DNA47, DNAPKcs, Ku, LiIV | `kliIV1` | internal-state conversion/modification | `DNA47(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)  -> DNA47(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)` | Transforms DNA47, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 677 | `Unlabeled` | one-way | DNA48, DNAPKcs, Ku, LiIV | `kliIV1` | internal-state conversion/modification | `DNA48(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)  -> DNA48(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)` | Transforms DNA48, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 678 | `Unlabeled` | one-way | DNA49, DNAPKcs, Ku, LiIV | `kliIV1` | internal-state conversion/modification | `DNA49(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)  -> DNA49(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)` | Transforms DNA49, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 679 | `Unlabeled` | one-way | DNA50, DNAPKcs, Ku, LiIV | `kliIV1` | internal-state conversion/modification | `DNA50(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)  -> DNA50(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)` | Transforms DNA50, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 680 | `Unlabeled` | one-way | DNA1, DNAPKcs, Ku, LiIV | `kliIV2` | internal-state conversion/modification | `DNA1(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)  -> DNA1(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)` | Transforms DNA1, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 681 | `Unlabeled` | one-way | DNA2, DNAPKcs, Ku, LiIV | `kliIV2` | internal-state conversion/modification | `DNA2(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)  -> DNA2(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)` | Transforms DNA2, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 682 | `Unlabeled` | one-way | DNA3, DNAPKcs, Ku, LiIV | `kliIV2` | internal-state conversion/modification | `DNA3(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)  -> DNA3(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)` | Transforms DNA3, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 683 | `Unlabeled` | one-way | DNA4, DNAPKcs, Ku, LiIV | `kliIV2` | internal-state conversion/modification | `DNA4(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)  -> DNA4(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)` | Transforms DNA4, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 684 | `Unlabeled` | one-way | DNA5, DNAPKcs, Ku, LiIV | `kliIV2` | internal-state conversion/modification | `DNA5(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)  -> DNA5(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)` | Transforms DNA5, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 685 | `Unlabeled` | one-way | DNA6, DNAPKcs, Ku, LiIV | `kliIV2` | internal-state conversion/modification | `DNA6(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)  -> DNA6(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)` | Transforms DNA6, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 686 | `Unlabeled` | one-way | DNA7, DNAPKcs, Ku, LiIV | `kliIV2` | internal-state conversion/modification | `DNA7(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)  -> DNA7(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)` | Transforms DNA7, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 687 | `Unlabeled` | one-way | DNA8, DNAPKcs, Ku, LiIV | `kliIV2` | internal-state conversion/modification | `DNA8(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)  -> DNA8(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)` | Transforms DNA8, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 688 | `Unlabeled` | one-way | DNA9, DNAPKcs, Ku, LiIV | `kliIV2` | internal-state conversion/modification | `DNA9(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)  -> DNA9(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)` | Transforms DNA9, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 689 | `Unlabeled` | one-way | DNA10, DNAPKcs, Ku, LiIV | `kliIV2` | internal-state conversion/modification | `DNA10(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)  -> DNA10(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)` | Transforms DNA10, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 690 | `Unlabeled` | one-way | DNA11, DNAPKcs, Ku, LiIV | `kliIV2` | internal-state conversion/modification | `DNA11(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)  -> DNA11(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)` | Transforms DNA11, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 691 | `Unlabeled` | one-way | DNA12, DNAPKcs, Ku, LiIV | `kliIV2` | internal-state conversion/modification | `DNA12(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)  -> DNA12(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)` | Transforms DNA12, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 692 | `Unlabeled` | one-way | DNA13, DNAPKcs, Ku, LiIV | `kliIV2` | internal-state conversion/modification | `DNA13(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)  -> DNA13(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)` | Transforms DNA13, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 693 | `Unlabeled` | one-way | DNA14, DNAPKcs, Ku, LiIV | `kliIV2` | internal-state conversion/modification | `DNA14(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)  -> DNA14(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)` | Transforms DNA14, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 694 | `Unlabeled` | one-way | DNA15, DNAPKcs, Ku, LiIV | `kliIV2` | internal-state conversion/modification | `DNA15(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)  -> DNA15(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)` | Transforms DNA15, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 695 | `Unlabeled` | one-way | DNA16, DNAPKcs, Ku, LiIV | `kliIV2` | internal-state conversion/modification | `DNA16(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)  -> DNA16(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)` | Transforms DNA16, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 696 | `Unlabeled` | one-way | DNA17, DNAPKcs, Ku, LiIV | `kliIV2` | internal-state conversion/modification | `DNA17(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)  -> DNA17(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)` | Transforms DNA17, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 697 | `Unlabeled` | one-way | DNA18, DNAPKcs, Ku, LiIV | `kliIV2` | internal-state conversion/modification | `DNA18(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)  -> DNA18(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)` | Transforms DNA18, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 698 | `Unlabeled` | one-way | DNA19, DNAPKcs, Ku, LiIV | `kliIV2` | internal-state conversion/modification | `DNA19(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)  -> DNA19(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)` | Transforms DNA19, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 699 | `Unlabeled` | one-way | DNA20, DNAPKcs, Ku, LiIV | `kliIV2` | internal-state conversion/modification | `DNA20(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)  -> DNA20(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)` | Transforms DNA20, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 700 | `Unlabeled` | one-way | DNA21, DNAPKcs, Ku, LiIV | `kliIV2` | internal-state conversion/modification | `DNA21(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)  -> DNA21(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)` | Transforms DNA21, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 701 | `Unlabeled` | one-way | DNA22, DNAPKcs, Ku, LiIV | `kliIV2` | internal-state conversion/modification | `DNA22(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)  -> DNA22(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)` | Transforms DNA22, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 702 | `Unlabeled` | one-way | DNA23, DNAPKcs, Ku, LiIV | `kliIV2` | internal-state conversion/modification | `DNA23(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)  -> DNA23(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)` | Transforms DNA23, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 703 | `Unlabeled` | one-way | DNA24, DNAPKcs, Ku, LiIV | `kliIV2` | internal-state conversion/modification | `DNA24(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)  -> DNA24(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)` | Transforms DNA24, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 704 | `Unlabeled` | one-way | DNA25, DNAPKcs, Ku, LiIV | `kliIV2` | internal-state conversion/modification | `DNA25(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)  -> DNA25(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)` | Transforms DNA25, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 705 | `Unlabeled` | one-way | DNA26, DNAPKcs, Ku, LiIV | `kliIV2` | internal-state conversion/modification | `DNA26(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)  -> DNA26(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)` | Transforms DNA26, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 706 | `Unlabeled` | one-way | DNA27, DNAPKcs, Ku, LiIV | `kliIV2` | internal-state conversion/modification | `DNA27(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)  -> DNA27(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)` | Transforms DNA27, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 707 | `Unlabeled` | one-way | DNA28, DNAPKcs, Ku, LiIV | `kliIV2` | internal-state conversion/modification | `DNA28(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)  -> DNA28(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)` | Transforms DNA28, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 708 | `Unlabeled` | one-way | DNA29, DNAPKcs, Ku, LiIV | `kliIV2` | internal-state conversion/modification | `DNA29(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)  -> DNA29(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)` | Transforms DNA29, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 709 | `Unlabeled` | one-way | DNA30, DNAPKcs, Ku, LiIV | `kliIV2` | internal-state conversion/modification | `DNA30(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)  -> DNA30(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)` | Transforms DNA30, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 710 | `Unlabeled` | one-way | DNA31, DNAPKcs, Ku, LiIV | `kliIV2` | internal-state conversion/modification | `DNA31(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)  -> DNA31(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)` | Transforms DNA31, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 711 | `Unlabeled` | one-way | DNA32, DNAPKcs, Ku, LiIV | `kliIV2` | internal-state conversion/modification | `DNA32(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)  -> DNA32(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)` | Transforms DNA32, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 712 | `Unlabeled` | one-way | DNA33, DNAPKcs, Ku, LiIV | `kliIV2` | internal-state conversion/modification | `DNA33(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)  -> DNA33(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)` | Transforms DNA33, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 713 | `Unlabeled` | one-way | DNA34, DNAPKcs, Ku, LiIV | `kliIV2` | internal-state conversion/modification | `DNA34(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)  -> DNA34(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)` | Transforms DNA34, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 714 | `Unlabeled` | one-way | DNA35, DNAPKcs, Ku, LiIV | `kliIV2` | internal-state conversion/modification | `DNA35(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)  -> DNA35(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)` | Transforms DNA35, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 715 | `Unlabeled` | one-way | DNA36, DNAPKcs, Ku, LiIV | `kliIV2` | internal-state conversion/modification | `DNA36(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)  -> DNA36(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)` | Transforms DNA36, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 716 | `Unlabeled` | one-way | DNA37, DNAPKcs, Ku, LiIV | `kliIV2` | internal-state conversion/modification | `DNA37(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)  -> DNA37(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)` | Transforms DNA37, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 717 | `Unlabeled` | one-way | DNA38, DNAPKcs, Ku, LiIV | `kliIV2` | internal-state conversion/modification | `DNA38(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)  -> DNA38(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)` | Transforms DNA38, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 718 | `Unlabeled` | one-way | DNA39, DNAPKcs, Ku, LiIV | `kliIV2` | internal-state conversion/modification | `DNA39(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)  -> DNA39(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)` | Transforms DNA39, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 719 | `Unlabeled` | one-way | DNA40, DNAPKcs, Ku, LiIV | `kliIV2` | internal-state conversion/modification | `DNA40(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)  -> DNA40(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)` | Transforms DNA40, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 720 | `Unlabeled` | one-way | DNA41, DNAPKcs, Ku, LiIV | `kliIV2` | internal-state conversion/modification | `DNA41(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)  -> DNA41(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)` | Transforms DNA41, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 721 | `Unlabeled` | one-way | DNA42, DNAPKcs, Ku, LiIV | `kliIV2` | internal-state conversion/modification | `DNA42(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)  -> DNA42(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)` | Transforms DNA42, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 722 | `Unlabeled` | one-way | DNA43, DNAPKcs, Ku, LiIV | `kliIV2` | internal-state conversion/modification | `DNA43(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)  -> DNA43(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)` | Transforms DNA43, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 723 | `Unlabeled` | one-way | DNA44, DNAPKcs, Ku, LiIV | `kliIV2` | internal-state conversion/modification | `DNA44(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)  -> DNA44(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)` | Transforms DNA44, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 724 | `Unlabeled` | one-way | DNA45, DNAPKcs, Ku, LiIV | `kliIV2` | internal-state conversion/modification | `DNA45(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)  -> DNA45(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)` | Transforms DNA45, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 725 | `Unlabeled` | one-way | DNA46, DNAPKcs, Ku, LiIV | `kliIV2` | internal-state conversion/modification | `DNA46(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)  -> DNA46(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)` | Transforms DNA46, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 726 | `Unlabeled` | one-way | DNA47, DNAPKcs, Ku, LiIV | `kliIV2` | internal-state conversion/modification | `DNA47(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)  -> DNA47(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)` | Transforms DNA47, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 727 | `Unlabeled` | one-way | DNA48, DNAPKcs, Ku, LiIV | `kliIV2` | internal-state conversion/modification | `DNA48(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)  -> DNA48(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)` | Transforms DNA48, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 728 | `Unlabeled` | one-way | DNA49, DNAPKcs, Ku, LiIV | `kliIV2` | internal-state conversion/modification | `DNA49(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)  -> DNA49(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)` | Transforms DNA49, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 729 | `Unlabeled` | one-way | DNA50, DNAPKcs, Ku, LiIV | `kliIV2` | internal-state conversion/modification | `DNA50(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)  -> DNA50(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)` | Transforms DNA50, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 730 | `Unlabeled` | one-way | DNA1, DNAPKcs, Ku, LiIV | `kdliIV1` | internal-state conversion/modification | `DNA1(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)  -> DNA1(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)` | Transforms DNA1, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 731 | `Unlabeled` | one-way | DNA2, DNAPKcs, Ku, LiIV | `kdliIV1` | internal-state conversion/modification | `DNA2(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)  -> DNA2(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)` | Transforms DNA2, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 732 | `Unlabeled` | one-way | DNA3, DNAPKcs, Ku, LiIV | `kdliIV1` | internal-state conversion/modification | `DNA3(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)  -> DNA3(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)` | Transforms DNA3, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 733 | `Unlabeled` | one-way | DNA4, DNAPKcs, Ku, LiIV | `kdliIV1` | internal-state conversion/modification | `DNA4(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)  -> DNA4(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)` | Transforms DNA4, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 734 | `Unlabeled` | one-way | DNA5, DNAPKcs, Ku, LiIV | `kdliIV1` | internal-state conversion/modification | `DNA5(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)  -> DNA5(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)` | Transforms DNA5, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 735 | `Unlabeled` | one-way | DNA6, DNAPKcs, Ku, LiIV | `kdliIV1` | internal-state conversion/modification | `DNA6(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)  -> DNA6(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)` | Transforms DNA6, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 736 | `Unlabeled` | one-way | DNA7, DNAPKcs, Ku, LiIV | `kdliIV1` | internal-state conversion/modification | `DNA7(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)  -> DNA7(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)` | Transforms DNA7, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 737 | `Unlabeled` | one-way | DNA8, DNAPKcs, Ku, LiIV | `kdliIV1` | internal-state conversion/modification | `DNA8(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)  -> DNA8(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)` | Transforms DNA8, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 738 | `Unlabeled` | one-way | DNA9, DNAPKcs, Ku, LiIV | `kdliIV1` | internal-state conversion/modification | `DNA9(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)  -> DNA9(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)` | Transforms DNA9, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 739 | `Unlabeled` | one-way | DNA10, DNAPKcs, Ku, LiIV | `kdliIV1` | internal-state conversion/modification | `DNA10(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)  -> DNA10(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)` | Transforms DNA10, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 740 | `Unlabeled` | one-way | DNA11, DNAPKcs, Ku, LiIV | `kdliIV1` | internal-state conversion/modification | `DNA11(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)  -> DNA11(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)` | Transforms DNA11, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 741 | `Unlabeled` | one-way | DNA12, DNAPKcs, Ku, LiIV | `kdliIV1` | internal-state conversion/modification | `DNA12(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)  -> DNA12(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)` | Transforms DNA12, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 742 | `Unlabeled` | one-way | DNA13, DNAPKcs, Ku, LiIV | `kdliIV1` | internal-state conversion/modification | `DNA13(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)  -> DNA13(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)` | Transforms DNA13, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 743 | `Unlabeled` | one-way | DNA14, DNAPKcs, Ku, LiIV | `kdliIV1` | internal-state conversion/modification | `DNA14(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)  -> DNA14(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)` | Transforms DNA14, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 744 | `Unlabeled` | one-way | DNA15, DNAPKcs, Ku, LiIV | `kdliIV1` | internal-state conversion/modification | `DNA15(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)  -> DNA15(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)` | Transforms DNA15, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 745 | `Unlabeled` | one-way | DNA16, DNAPKcs, Ku, LiIV | `kdliIV1` | internal-state conversion/modification | `DNA16(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)  -> DNA16(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)` | Transforms DNA16, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 746 | `Unlabeled` | one-way | DNA17, DNAPKcs, Ku, LiIV | `kdliIV1` | internal-state conversion/modification | `DNA17(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)  -> DNA17(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)` | Transforms DNA17, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 747 | `Unlabeled` | one-way | DNA18, DNAPKcs, Ku, LiIV | `kdliIV1` | internal-state conversion/modification | `DNA18(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)  -> DNA18(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)` | Transforms DNA18, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 748 | `Unlabeled` | one-way | DNA19, DNAPKcs, Ku, LiIV | `kdliIV1` | internal-state conversion/modification | `DNA19(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)  -> DNA19(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)` | Transforms DNA19, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 749 | `Unlabeled` | one-way | DNA20, DNAPKcs, Ku, LiIV | `kdliIV1` | internal-state conversion/modification | `DNA20(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)  -> DNA20(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)` | Transforms DNA20, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 750 | `Unlabeled` | one-way | DNA21, DNAPKcs, Ku, LiIV | `kdliIV1` | internal-state conversion/modification | `DNA21(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)  -> DNA21(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)` | Transforms DNA21, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

### Rules 751-1000

| # | Rule label/name | Direction | Participants | Rate/expression | Modeled change | Rule pattern | Technical meaning |
| ---: | --- | --- | --- | --- | --- | --- | --- |

| 751 | `Unlabeled` | one-way | DNA22, DNAPKcs, Ku, LiIV | `kdliIV1` | internal-state conversion/modification | `DNA22(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)  -> DNA22(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)` | Transforms DNA22, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 752 | `Unlabeled` | one-way | DNA23, DNAPKcs, Ku, LiIV | `kdliIV1` | internal-state conversion/modification | `DNA23(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)  -> DNA23(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)` | Transforms DNA23, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 753 | `Unlabeled` | one-way | DNA24, DNAPKcs, Ku, LiIV | `kdliIV1` | internal-state conversion/modification | `DNA24(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)  -> DNA24(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)` | Transforms DNA24, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 754 | `Unlabeled` | one-way | DNA25, DNAPKcs, Ku, LiIV | `kdliIV1` | internal-state conversion/modification | `DNA25(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)  -> DNA25(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)` | Transforms DNA25, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 755 | `Unlabeled` | one-way | DNA26, DNAPKcs, Ku, LiIV | `kdliIV1` | internal-state conversion/modification | `DNA26(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)  -> DNA26(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)` | Transforms DNA26, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 756 | `Unlabeled` | one-way | DNA27, DNAPKcs, Ku, LiIV | `kdliIV1` | internal-state conversion/modification | `DNA27(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)  -> DNA27(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)` | Transforms DNA27, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 757 | `Unlabeled` | one-way | DNA28, DNAPKcs, Ku, LiIV | `kdliIV1` | internal-state conversion/modification | `DNA28(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)  -> DNA28(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)` | Transforms DNA28, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 758 | `Unlabeled` | one-way | DNA29, DNAPKcs, Ku, LiIV | `kdliIV1` | internal-state conversion/modification | `DNA29(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)  -> DNA29(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)` | Transforms DNA29, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 759 | `Unlabeled` | one-way | DNA30, DNAPKcs, Ku, LiIV | `kdliIV1` | internal-state conversion/modification | `DNA30(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)  -> DNA30(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)` | Transforms DNA30, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 760 | `Unlabeled` | one-way | DNA31, DNAPKcs, Ku, LiIV | `kdliIV1` | internal-state conversion/modification | `DNA31(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)  -> DNA31(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)` | Transforms DNA31, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 761 | `Unlabeled` | one-way | DNA32, DNAPKcs, Ku, LiIV | `kdliIV1` | internal-state conversion/modification | `DNA32(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)  -> DNA32(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)` | Transforms DNA32, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 762 | `Unlabeled` | one-way | DNA33, DNAPKcs, Ku, LiIV | `kdliIV1` | internal-state conversion/modification | `DNA33(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)  -> DNA33(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)` | Transforms DNA33, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 763 | `Unlabeled` | one-way | DNA34, DNAPKcs, Ku, LiIV | `kdliIV1` | internal-state conversion/modification | `DNA34(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)  -> DNA34(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)` | Transforms DNA34, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 764 | `Unlabeled` | one-way | DNA35, DNAPKcs, Ku, LiIV | `kdliIV1` | internal-state conversion/modification | `DNA35(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)  -> DNA35(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)` | Transforms DNA35, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 765 | `Unlabeled` | one-way | DNA36, DNAPKcs, Ku, LiIV | `kdliIV1` | internal-state conversion/modification | `DNA36(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)  -> DNA36(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)` | Transforms DNA36, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 766 | `Unlabeled` | one-way | DNA37, DNAPKcs, Ku, LiIV | `kdliIV1` | internal-state conversion/modification | `DNA37(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)  -> DNA37(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)` | Transforms DNA37, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 767 | `Unlabeled` | one-way | DNA38, DNAPKcs, Ku, LiIV | `kdliIV1` | internal-state conversion/modification | `DNA38(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)  -> DNA38(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)` | Transforms DNA38, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 768 | `Unlabeled` | one-way | DNA39, DNAPKcs, Ku, LiIV | `kdliIV1` | internal-state conversion/modification | `DNA39(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)  -> DNA39(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)` | Transforms DNA39, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 769 | `Unlabeled` | one-way | DNA40, DNAPKcs, Ku, LiIV | `kdliIV1` | internal-state conversion/modification | `DNA40(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)  -> DNA40(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)` | Transforms DNA40, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 770 | `Unlabeled` | one-way | DNA41, DNAPKcs, Ku, LiIV | `kdliIV1` | internal-state conversion/modification | `DNA41(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)  -> DNA41(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)` | Transforms DNA41, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 771 | `Unlabeled` | one-way | DNA42, DNAPKcs, Ku, LiIV | `kdliIV1` | internal-state conversion/modification | `DNA42(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)  -> DNA42(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)` | Transforms DNA42, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 772 | `Unlabeled` | one-way | DNA43, DNAPKcs, Ku, LiIV | `kdliIV1` | internal-state conversion/modification | `DNA43(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)  -> DNA43(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)` | Transforms DNA43, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 773 | `Unlabeled` | one-way | DNA44, DNAPKcs, Ku, LiIV | `kdliIV1` | internal-state conversion/modification | `DNA44(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)  -> DNA44(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)` | Transforms DNA44, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 774 | `Unlabeled` | one-way | DNA45, DNAPKcs, Ku, LiIV | `kdliIV1` | internal-state conversion/modification | `DNA45(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)  -> DNA45(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)` | Transforms DNA45, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 775 | `Unlabeled` | one-way | DNA46, DNAPKcs, Ku, LiIV | `kdliIV1` | internal-state conversion/modification | `DNA46(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)  -> DNA46(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)` | Transforms DNA46, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 776 | `Unlabeled` | one-way | DNA47, DNAPKcs, Ku, LiIV | `kdliIV1` | internal-state conversion/modification | `DNA47(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)  -> DNA47(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)` | Transforms DNA47, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 777 | `Unlabeled` | one-way | DNA48, DNAPKcs, Ku, LiIV | `kdliIV1` | internal-state conversion/modification | `DNA48(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)  -> DNA48(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)` | Transforms DNA48, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 778 | `Unlabeled` | one-way | DNA49, DNAPKcs, Ku, LiIV | `kdliIV1` | internal-state conversion/modification | `DNA49(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)  -> DNA49(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)` | Transforms DNA49, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 779 | `Unlabeled` | one-way | DNA50, DNAPKcs, Ku, LiIV | `kdliIV1` | internal-state conversion/modification | `DNA50(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)  -> DNA50(site!1~sdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)` | Transforms DNA50, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 780 | `Unlabeled` | one-way | DNA1, DNAPKcs, Ku, LiIV | `kdliIV2` | internal-state conversion/modification | `DNA1(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)  -> DNA1(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)` | Transforms DNA1, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 781 | `Unlabeled` | one-way | DNA2, DNAPKcs, Ku, LiIV | `kdliIV2` | internal-state conversion/modification | `DNA2(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)  -> DNA2(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)` | Transforms DNA2, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 782 | `Unlabeled` | one-way | DNA3, DNAPKcs, Ku, LiIV | `kdliIV2` | internal-state conversion/modification | `DNA3(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)  -> DNA3(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)` | Transforms DNA3, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 783 | `Unlabeled` | one-way | DNA4, DNAPKcs, Ku, LiIV | `kdliIV2` | internal-state conversion/modification | `DNA4(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)  -> DNA4(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)` | Transforms DNA4, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 784 | `Unlabeled` | one-way | DNA5, DNAPKcs, Ku, LiIV | `kdliIV2` | internal-state conversion/modification | `DNA5(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)  -> DNA5(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)` | Transforms DNA5, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 785 | `Unlabeled` | one-way | DNA6, DNAPKcs, Ku, LiIV | `kdliIV2` | internal-state conversion/modification | `DNA6(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)  -> DNA6(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)` | Transforms DNA6, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 786 | `Unlabeled` | one-way | DNA7, DNAPKcs, Ku, LiIV | `kdliIV2` | internal-state conversion/modification | `DNA7(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)  -> DNA7(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)` | Transforms DNA7, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 787 | `Unlabeled` | one-way | DNA8, DNAPKcs, Ku, LiIV | `kdliIV2` | internal-state conversion/modification | `DNA8(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)  -> DNA8(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)` | Transforms DNA8, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 788 | `Unlabeled` | one-way | DNA9, DNAPKcs, Ku, LiIV | `kdliIV2` | internal-state conversion/modification | `DNA9(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)  -> DNA9(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)` | Transforms DNA9, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 789 | `Unlabeled` | one-way | DNA10, DNAPKcs, Ku, LiIV | `kdliIV2` | internal-state conversion/modification | `DNA10(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)  -> DNA10(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)` | Transforms DNA10, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 790 | `Unlabeled` | one-way | DNA11, DNAPKcs, Ku, LiIV | `kdliIV2` | internal-state conversion/modification | `DNA11(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)  -> DNA11(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)` | Transforms DNA11, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 791 | `Unlabeled` | one-way | DNA12, DNAPKcs, Ku, LiIV | `kdliIV2` | internal-state conversion/modification | `DNA12(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)  -> DNA12(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)` | Transforms DNA12, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 792 | `Unlabeled` | one-way | DNA13, DNAPKcs, Ku, LiIV | `kdliIV2` | internal-state conversion/modification | `DNA13(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)  -> DNA13(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)` | Transforms DNA13, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 793 | `Unlabeled` | one-way | DNA14, DNAPKcs, Ku, LiIV | `kdliIV2` | internal-state conversion/modification | `DNA14(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)  -> DNA14(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)` | Transforms DNA14, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 794 | `Unlabeled` | one-way | DNA15, DNAPKcs, Ku, LiIV | `kdliIV2` | internal-state conversion/modification | `DNA15(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)  -> DNA15(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)` | Transforms DNA15, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 795 | `Unlabeled` | one-way | DNA16, DNAPKcs, Ku, LiIV | `kdliIV2` | internal-state conversion/modification | `DNA16(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)  -> DNA16(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)` | Transforms DNA16, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 796 | `Unlabeled` | one-way | DNA17, DNAPKcs, Ku, LiIV | `kdliIV2` | internal-state conversion/modification | `DNA17(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)  -> DNA17(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)` | Transforms DNA17, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 797 | `Unlabeled` | one-way | DNA18, DNAPKcs, Ku, LiIV | `kdliIV2` | internal-state conversion/modification | `DNA18(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)  -> DNA18(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)` | Transforms DNA18, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 798 | `Unlabeled` | one-way | DNA19, DNAPKcs, Ku, LiIV | `kdliIV2` | internal-state conversion/modification | `DNA19(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)  -> DNA19(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)` | Transforms DNA19, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 799 | `Unlabeled` | one-way | DNA20, DNAPKcs, Ku, LiIV | `kdliIV2` | internal-state conversion/modification | `DNA20(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)  -> DNA20(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)` | Transforms DNA20, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 800 | `Unlabeled` | one-way | DNA21, DNAPKcs, Ku, LiIV | `kdliIV2` | internal-state conversion/modification | `DNA21(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)  -> DNA21(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)` | Transforms DNA21, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 801 | `Unlabeled` | one-way | DNA22, DNAPKcs, Ku, LiIV | `kdliIV2` | internal-state conversion/modification | `DNA22(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)  -> DNA22(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)` | Transforms DNA22, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 802 | `Unlabeled` | one-way | DNA23, DNAPKcs, Ku, LiIV | `kdliIV2` | internal-state conversion/modification | `DNA23(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)  -> DNA23(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)` | Transforms DNA23, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 803 | `Unlabeled` | one-way | DNA24, DNAPKcs, Ku, LiIV | `kdliIV2` | internal-state conversion/modification | `DNA24(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)  -> DNA24(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)` | Transforms DNA24, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 804 | `Unlabeled` | one-way | DNA25, DNAPKcs, Ku, LiIV | `kdliIV2` | internal-state conversion/modification | `DNA25(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)  -> DNA25(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)` | Transforms DNA25, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 805 | `Unlabeled` | one-way | DNA26, DNAPKcs, Ku, LiIV | `kdliIV2` | internal-state conversion/modification | `DNA26(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)  -> DNA26(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)` | Transforms DNA26, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 806 | `Unlabeled` | one-way | DNA27, DNAPKcs, Ku, LiIV | `kdliIV2` | internal-state conversion/modification | `DNA27(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)  -> DNA27(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)` | Transforms DNA27, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 807 | `Unlabeled` | one-way | DNA28, DNAPKcs, Ku, LiIV | `kdliIV2` | internal-state conversion/modification | `DNA28(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)  -> DNA28(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)` | Transforms DNA28, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 808 | `Unlabeled` | one-way | DNA29, DNAPKcs, Ku, LiIV | `kdliIV2` | internal-state conversion/modification | `DNA29(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)  -> DNA29(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)` | Transforms DNA29, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 809 | `Unlabeled` | one-way | DNA30, DNAPKcs, Ku, LiIV | `kdliIV2` | internal-state conversion/modification | `DNA30(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)  -> DNA30(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)` | Transforms DNA30, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 810 | `Unlabeled` | one-way | DNA31, DNAPKcs, Ku, LiIV | `kdliIV2` | internal-state conversion/modification | `DNA31(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)  -> DNA31(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)` | Transforms DNA31, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 811 | `Unlabeled` | one-way | DNA32, DNAPKcs, Ku, LiIV | `kdliIV2` | internal-state conversion/modification | `DNA32(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)  -> DNA32(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)` | Transforms DNA32, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 812 | `Unlabeled` | one-way | DNA33, DNAPKcs, Ku, LiIV | `kdliIV2` | internal-state conversion/modification | `DNA33(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)  -> DNA33(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)` | Transforms DNA33, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 813 | `Unlabeled` | one-way | DNA34, DNAPKcs, Ku, LiIV | `kdliIV2` | internal-state conversion/modification | `DNA34(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)  -> DNA34(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)` | Transforms DNA34, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 814 | `Unlabeled` | one-way | DNA35, DNAPKcs, Ku, LiIV | `kdliIV2` | internal-state conversion/modification | `DNA35(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)  -> DNA35(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)` | Transforms DNA35, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 815 | `Unlabeled` | one-way | DNA36, DNAPKcs, Ku, LiIV | `kdliIV2` | internal-state conversion/modification | `DNA36(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)  -> DNA36(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)` | Transforms DNA36, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 816 | `Unlabeled` | one-way | DNA37, DNAPKcs, Ku, LiIV | `kdliIV2` | internal-state conversion/modification | `DNA37(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)  -> DNA37(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)` | Transforms DNA37, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 817 | `Unlabeled` | one-way | DNA38, DNAPKcs, Ku, LiIV | `kdliIV2` | internal-state conversion/modification | `DNA38(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)  -> DNA38(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)` | Transforms DNA38, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 818 | `Unlabeled` | one-way | DNA39, DNAPKcs, Ku, LiIV | `kdliIV2` | internal-state conversion/modification | `DNA39(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)  -> DNA39(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)` | Transforms DNA39, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 819 | `Unlabeled` | one-way | DNA40, DNAPKcs, Ku, LiIV | `kdliIV2` | internal-state conversion/modification | `DNA40(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)  -> DNA40(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)` | Transforms DNA40, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 820 | `Unlabeled` | one-way | DNA41, DNAPKcs, Ku, LiIV | `kdliIV2` | internal-state conversion/modification | `DNA41(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)  -> DNA41(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)` | Transforms DNA41, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 821 | `Unlabeled` | one-way | DNA42, DNAPKcs, Ku, LiIV | `kdliIV2` | internal-state conversion/modification | `DNA42(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)  -> DNA42(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)` | Transforms DNA42, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 822 | `Unlabeled` | one-way | DNA43, DNAPKcs, Ku, LiIV | `kdliIV2` | internal-state conversion/modification | `DNA43(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)  -> DNA43(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)` | Transforms DNA43, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 823 | `Unlabeled` | one-way | DNA44, DNAPKcs, Ku, LiIV | `kdliIV2` | internal-state conversion/modification | `DNA44(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)  -> DNA44(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)` | Transforms DNA44, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 824 | `Unlabeled` | one-way | DNA45, DNAPKcs, Ku, LiIV | `kdliIV2` | internal-state conversion/modification | `DNA45(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)  -> DNA45(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)` | Transforms DNA45, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 825 | `Unlabeled` | one-way | DNA46, DNAPKcs, Ku, LiIV | `kdliIV2` | internal-state conversion/modification | `DNA46(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)  -> DNA46(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)` | Transforms DNA46, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 826 | `Unlabeled` | one-way | DNA47, DNAPKcs, Ku, LiIV | `kdliIV2` | internal-state conversion/modification | `DNA47(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)  -> DNA47(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)` | Transforms DNA47, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 827 | `Unlabeled` | one-way | DNA48, DNAPKcs, Ku, LiIV | `kdliIV2` | internal-state conversion/modification | `DNA48(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)  -> DNA48(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)` | Transforms DNA48, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 828 | `Unlabeled` | one-way | DNA49, DNAPKcs, Ku, LiIV | `kdliIV2` | internal-state conversion/modification | `DNA49(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)  -> DNA49(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)` | Transforms DNA49, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 829 | `Unlabeled` | one-way | DNA50, DNAPKcs, Ku, LiIV | `kdliIV2` | internal-state conversion/modification | `DNA50(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3)  -> DNA50(site!1~cdsb).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p) + LiIV(cs)` | Transforms DNA50, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 830 | `Unlabeled` | one-way | ATM, DNA1, DNAPKcs, Ku, LiIV | `kfixIV1` | internal-state conversion/modification | `DNA1(site!1~sdsb,h2ax!4~foc).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3).ATM(h2ax!4)  -> DNA1(site~ok,h2ax!1~foc).ATM(h2ax!1) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u) + LiIV(cs)` | Transforms ATM, DNA1, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 831 | `Unlabeled` | one-way | ATM, DNA2, DNAPKcs, Ku, LiIV | `kfixIV1` | internal-state conversion/modification | `DNA2(site!1~sdsb,h2ax!4~foc).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3).ATM(h2ax!4)  -> DNA2(site~ok,h2ax!1~foc).ATM(h2ax!1) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u) + LiIV(cs)` | Transforms ATM, DNA2, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 832 | `Unlabeled` | one-way | ATM, DNA3, DNAPKcs, Ku, LiIV | `kfixIV1` | internal-state conversion/modification | `DNA3(site!1~sdsb,h2ax!4~foc).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3).ATM(h2ax!4)  -> DNA3(site~ok,h2ax!1~foc).ATM(h2ax!1) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u) + LiIV(cs)` | Transforms ATM, DNA3, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 833 | `Unlabeled` | one-way | ATM, DNA4, DNAPKcs, Ku, LiIV | `kfixIV1` | internal-state conversion/modification | `DNA4(site!1~sdsb,h2ax!4~foc).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3).ATM(h2ax!4)  -> DNA4(site~ok,h2ax!1~foc).ATM(h2ax!1) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u) + LiIV(cs)` | Transforms ATM, DNA4, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 834 | `Unlabeled` | one-way | ATM, DNA5, DNAPKcs, Ku, LiIV | `kfixIV1` | internal-state conversion/modification | `DNA5(site!1~sdsb,h2ax!4~foc).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3).ATM(h2ax!4)  -> DNA5(site~ok,h2ax!1~foc).ATM(h2ax!1) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u) + LiIV(cs)` | Transforms ATM, DNA5, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 835 | `Unlabeled` | one-way | ATM, DNA6, DNAPKcs, Ku, LiIV | `kfixIV1` | internal-state conversion/modification | `DNA6(site!1~sdsb,h2ax!4~foc).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3).ATM(h2ax!4)  -> DNA6(site~ok,h2ax!1~foc).ATM(h2ax!1) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u) + LiIV(cs)` | Transforms ATM, DNA6, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 836 | `Unlabeled` | one-way | ATM, DNA7, DNAPKcs, Ku, LiIV | `kfixIV1` | internal-state conversion/modification | `DNA7(site!1~sdsb,h2ax!4~foc).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3).ATM(h2ax!4)  -> DNA7(site~ok,h2ax!1~foc).ATM(h2ax!1) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u) + LiIV(cs)` | Transforms ATM, DNA7, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 837 | `Unlabeled` | one-way | ATM, DNA8, DNAPKcs, Ku, LiIV | `kfixIV1` | internal-state conversion/modification | `DNA8(site!1~sdsb,h2ax!4~foc).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3).ATM(h2ax!4)  -> DNA8(site~ok,h2ax!1~foc).ATM(h2ax!1) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u) + LiIV(cs)` | Transforms ATM, DNA8, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 838 | `Unlabeled` | one-way | ATM, DNA9, DNAPKcs, Ku, LiIV | `kfixIV1` | internal-state conversion/modification | `DNA9(site!1~sdsb,h2ax!4~foc).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3).ATM(h2ax!4)  -> DNA9(site~ok,h2ax!1~foc).ATM(h2ax!1) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u) + LiIV(cs)` | Transforms ATM, DNA9, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 839 | `Unlabeled` | one-way | ATM, DNA10, DNAPKcs, Ku, LiIV | `kfixIV1` | internal-state conversion/modification | `DNA10(site!1~sdsb,h2ax!4~foc).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3).ATM(h2ax!4)  -> DNA10(site~ok,h2ax!1~foc).ATM(h2ax!1) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u) + LiIV(cs)` | Transforms ATM, DNA10, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 840 | `Unlabeled` | one-way | ATM, DNA11, DNAPKcs, Ku, LiIV | `kfixIV1` | internal-state conversion/modification | `DNA11(site!1~sdsb,h2ax!4~foc).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3).ATM(h2ax!4)  -> DNA11(site~ok,h2ax!1~foc).ATM(h2ax!1) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u) + LiIV(cs)` | Transforms ATM, DNA11, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 841 | `Unlabeled` | one-way | ATM, DNA12, DNAPKcs, Ku, LiIV | `kfixIV1` | internal-state conversion/modification | `DNA12(site!1~sdsb,h2ax!4~foc).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3).ATM(h2ax!4)  -> DNA12(site~ok,h2ax!1~foc).ATM(h2ax!1) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u) + LiIV(cs)` | Transforms ATM, DNA12, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 842 | `Unlabeled` | one-way | ATM, DNA13, DNAPKcs, Ku, LiIV | `kfixIV1` | internal-state conversion/modification | `DNA13(site!1~sdsb,h2ax!4~foc).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3).ATM(h2ax!4)  -> DNA13(site~ok,h2ax!1~foc).ATM(h2ax!1) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u) + LiIV(cs)` | Transforms ATM, DNA13, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 843 | `Unlabeled` | one-way | ATM, DNA14, DNAPKcs, Ku, LiIV | `kfixIV1` | internal-state conversion/modification | `DNA14(site!1~sdsb,h2ax!4~foc).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3).ATM(h2ax!4)  -> DNA14(site~ok,h2ax!1~foc).ATM(h2ax!1) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u) + LiIV(cs)` | Transforms ATM, DNA14, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 844 | `Unlabeled` | one-way | ATM, DNA15, DNAPKcs, Ku, LiIV | `kfixIV1` | internal-state conversion/modification | `DNA15(site!1~sdsb,h2ax!4~foc).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3).ATM(h2ax!4)  -> DNA15(site~ok,h2ax!1~foc).ATM(h2ax!1) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u) + LiIV(cs)` | Transforms ATM, DNA15, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 845 | `Unlabeled` | one-way | ATM, DNA16, DNAPKcs, Ku, LiIV | `kfixIV1` | internal-state conversion/modification | `DNA16(site!1~sdsb,h2ax!4~foc).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3).ATM(h2ax!4)  -> DNA16(site~ok,h2ax!1~foc).ATM(h2ax!1) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u) + LiIV(cs)` | Transforms ATM, DNA16, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 846 | `Unlabeled` | one-way | ATM, DNA17, DNAPKcs, Ku, LiIV | `kfixIV1` | internal-state conversion/modification | `DNA17(site!1~sdsb,h2ax!4~foc).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3).ATM(h2ax!4)  -> DNA17(site~ok,h2ax!1~foc).ATM(h2ax!1) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u) + LiIV(cs)` | Transforms ATM, DNA17, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 847 | `Unlabeled` | one-way | ATM, DNA18, DNAPKcs, Ku, LiIV | `kfixIV1` | internal-state conversion/modification | `DNA18(site!1~sdsb,h2ax!4~foc).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3).ATM(h2ax!4)  -> DNA18(site~ok,h2ax!1~foc).ATM(h2ax!1) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u) + LiIV(cs)` | Transforms ATM, DNA18, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 848 | `Unlabeled` | one-way | ATM, DNA19, DNAPKcs, Ku, LiIV | `kfixIV1` | internal-state conversion/modification | `DNA19(site!1~sdsb,h2ax!4~foc).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3).ATM(h2ax!4)  -> DNA19(site~ok,h2ax!1~foc).ATM(h2ax!1) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u) + LiIV(cs)` | Transforms ATM, DNA19, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 849 | `Unlabeled` | one-way | ATM, DNA20, DNAPKcs, Ku, LiIV | `kfixIV1` | internal-state conversion/modification | `DNA20(site!1~sdsb,h2ax!4~foc).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3).ATM(h2ax!4)  -> DNA20(site~ok,h2ax!1~foc).ATM(h2ax!1) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u) + LiIV(cs)` | Transforms ATM, DNA20, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 850 | `Unlabeled` | one-way | ATM, DNA21, DNAPKcs, Ku, LiIV | `kfixIV1` | internal-state conversion/modification | `DNA21(site!1~sdsb,h2ax!4~foc).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3).ATM(h2ax!4)  -> DNA21(site~ok,h2ax!1~foc).ATM(h2ax!1) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u) + LiIV(cs)` | Transforms ATM, DNA21, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 851 | `Unlabeled` | one-way | ATM, DNA22, DNAPKcs, Ku, LiIV | `kfixIV1` | internal-state conversion/modification | `DNA22(site!1~sdsb,h2ax!4~foc).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3).ATM(h2ax!4)  -> DNA22(site~ok,h2ax!1~foc).ATM(h2ax!1) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u) + LiIV(cs)` | Transforms ATM, DNA22, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 852 | `Unlabeled` | one-way | ATM, DNA23, DNAPKcs, Ku, LiIV | `kfixIV1` | internal-state conversion/modification | `DNA23(site!1~sdsb,h2ax!4~foc).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3).ATM(h2ax!4)  -> DNA23(site~ok,h2ax!1~foc).ATM(h2ax!1) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u) + LiIV(cs)` | Transforms ATM, DNA23, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 853 | `Unlabeled` | one-way | ATM, DNA24, DNAPKcs, Ku, LiIV | `kfixIV1` | internal-state conversion/modification | `DNA24(site!1~sdsb,h2ax!4~foc).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3).ATM(h2ax!4)  -> DNA24(site~ok,h2ax!1~foc).ATM(h2ax!1) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u) + LiIV(cs)` | Transforms ATM, DNA24, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 854 | `Unlabeled` | one-way | ATM, DNA25, DNAPKcs, Ku, LiIV | `kfixIV1` | internal-state conversion/modification | `DNA25(site!1~sdsb,h2ax!4~foc).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3).ATM(h2ax!4)  -> DNA25(site~ok,h2ax!1~foc).ATM(h2ax!1) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u) + LiIV(cs)` | Transforms ATM, DNA25, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 855 | `Unlabeled` | one-way | ATM, DNA26, DNAPKcs, Ku, LiIV | `kfixIV1` | internal-state conversion/modification | `DNA26(site!1~sdsb,h2ax!4~foc).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3).ATM(h2ax!4)  -> DNA26(site~ok,h2ax!1~foc).ATM(h2ax!1) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u) + LiIV(cs)` | Transforms ATM, DNA26, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 856 | `Unlabeled` | one-way | ATM, DNA27, DNAPKcs, Ku, LiIV | `kfixIV1` | internal-state conversion/modification | `DNA27(site!1~sdsb,h2ax!4~foc).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3).ATM(h2ax!4)  -> DNA27(site~ok,h2ax!1~foc).ATM(h2ax!1) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u) + LiIV(cs)` | Transforms ATM, DNA27, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 857 | `Unlabeled` | one-way | ATM, DNA28, DNAPKcs, Ku, LiIV | `kfixIV1` | internal-state conversion/modification | `DNA28(site!1~sdsb,h2ax!4~foc).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3).ATM(h2ax!4)  -> DNA28(site~ok,h2ax!1~foc).ATM(h2ax!1) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u) + LiIV(cs)` | Transforms ATM, DNA28, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 858 | `Unlabeled` | one-way | ATM, DNA29, DNAPKcs, Ku, LiIV | `kfixIV1` | internal-state conversion/modification | `DNA29(site!1~sdsb,h2ax!4~foc).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3).ATM(h2ax!4)  -> DNA29(site~ok,h2ax!1~foc).ATM(h2ax!1) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u) + LiIV(cs)` | Transforms ATM, DNA29, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 859 | `Unlabeled` | one-way | ATM, DNA30, DNAPKcs, Ku, LiIV | `kfixIV1` | internal-state conversion/modification | `DNA30(site!1~sdsb,h2ax!4~foc).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3).ATM(h2ax!4)  -> DNA30(site~ok,h2ax!1~foc).ATM(h2ax!1) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u) + LiIV(cs)` | Transforms ATM, DNA30, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 860 | `Unlabeled` | one-way | ATM, DNA31, DNAPKcs, Ku, LiIV | `kfixIV1` | internal-state conversion/modification | `DNA31(site!1~sdsb,h2ax!4~foc).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3).ATM(h2ax!4)  -> DNA31(site~ok,h2ax!1~foc).ATM(h2ax!1) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u) + LiIV(cs)` | Transforms ATM, DNA31, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 861 | `Unlabeled` | one-way | ATM, DNA32, DNAPKcs, Ku, LiIV | `kfixIV1` | internal-state conversion/modification | `DNA32(site!1~sdsb,h2ax!4~foc).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3).ATM(h2ax!4)  -> DNA32(site~ok,h2ax!1~foc).ATM(h2ax!1) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u) + LiIV(cs)` | Transforms ATM, DNA32, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 862 | `Unlabeled` | one-way | ATM, DNA33, DNAPKcs, Ku, LiIV | `kfixIV1` | internal-state conversion/modification | `DNA33(site!1~sdsb,h2ax!4~foc).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3).ATM(h2ax!4)  -> DNA33(site~ok,h2ax!1~foc).ATM(h2ax!1) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u) + LiIV(cs)` | Transforms ATM, DNA33, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 863 | `Unlabeled` | one-way | ATM, DNA34, DNAPKcs, Ku, LiIV | `kfixIV1` | internal-state conversion/modification | `DNA34(site!1~sdsb,h2ax!4~foc).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3).ATM(h2ax!4)  -> DNA34(site~ok,h2ax!1~foc).ATM(h2ax!1) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u) + LiIV(cs)` | Transforms ATM, DNA34, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 864 | `Unlabeled` | one-way | ATM, DNA35, DNAPKcs, Ku, LiIV | `kfixIV1` | internal-state conversion/modification | `DNA35(site!1~sdsb,h2ax!4~foc).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3).ATM(h2ax!4)  -> DNA35(site~ok,h2ax!1~foc).ATM(h2ax!1) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u) + LiIV(cs)` | Transforms ATM, DNA35, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 865 | `Unlabeled` | one-way | ATM, DNA36, DNAPKcs, Ku, LiIV | `kfixIV1` | internal-state conversion/modification | `DNA36(site!1~sdsb,h2ax!4~foc).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3).ATM(h2ax!4)  -> DNA36(site~ok,h2ax!1~foc).ATM(h2ax!1) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u) + LiIV(cs)` | Transforms ATM, DNA36, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 866 | `Unlabeled` | one-way | ATM, DNA37, DNAPKcs, Ku, LiIV | `kfixIV1` | internal-state conversion/modification | `DNA37(site!1~sdsb,h2ax!4~foc).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3).ATM(h2ax!4)  -> DNA37(site~ok,h2ax!1~foc).ATM(h2ax!1) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u) + LiIV(cs)` | Transforms ATM, DNA37, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 867 | `Unlabeled` | one-way | ATM, DNA38, DNAPKcs, Ku, LiIV | `kfixIV1` | internal-state conversion/modification | `DNA38(site!1~sdsb,h2ax!4~foc).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3).ATM(h2ax!4)  -> DNA38(site~ok,h2ax!1~foc).ATM(h2ax!1) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u) + LiIV(cs)` | Transforms ATM, DNA38, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 868 | `Unlabeled` | one-way | ATM, DNA39, DNAPKcs, Ku, LiIV | `kfixIV1` | internal-state conversion/modification | `DNA39(site!1~sdsb,h2ax!4~foc).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3).ATM(h2ax!4)  -> DNA39(site~ok,h2ax!1~foc).ATM(h2ax!1) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u) + LiIV(cs)` | Transforms ATM, DNA39, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 869 | `Unlabeled` | one-way | ATM, DNA40, DNAPKcs, Ku, LiIV | `kfixIV1` | internal-state conversion/modification | `DNA40(site!1~sdsb,h2ax!4~foc).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3).ATM(h2ax!4)  -> DNA40(site~ok,h2ax!1~foc).ATM(h2ax!1) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u) + LiIV(cs)` | Transforms ATM, DNA40, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 870 | `Unlabeled` | one-way | ATM, DNA41, DNAPKcs, Ku, LiIV | `kfixIV1` | internal-state conversion/modification | `DNA41(site!1~sdsb,h2ax!4~foc).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3).ATM(h2ax!4)  -> DNA41(site~ok,h2ax!1~foc).ATM(h2ax!1) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u) + LiIV(cs)` | Transforms ATM, DNA41, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 871 | `Unlabeled` | one-way | ATM, DNA42, DNAPKcs, Ku, LiIV | `kfixIV1` | internal-state conversion/modification | `DNA42(site!1~sdsb,h2ax!4~foc).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3).ATM(h2ax!4)  -> DNA42(site~ok,h2ax!1~foc).ATM(h2ax!1) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u) + LiIV(cs)` | Transforms ATM, DNA42, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 872 | `Unlabeled` | one-way | ATM, DNA43, DNAPKcs, Ku, LiIV | `kfixIV1` | internal-state conversion/modification | `DNA43(site!1~sdsb,h2ax!4~foc).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3).ATM(h2ax!4)  -> DNA43(site~ok,h2ax!1~foc).ATM(h2ax!1) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u) + LiIV(cs)` | Transforms ATM, DNA43, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 873 | `Unlabeled` | one-way | ATM, DNA44, DNAPKcs, Ku, LiIV | `kfixIV1` | internal-state conversion/modification | `DNA44(site!1~sdsb,h2ax!4~foc).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3).ATM(h2ax!4)  -> DNA44(site~ok,h2ax!1~foc).ATM(h2ax!1) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u) + LiIV(cs)` | Transforms ATM, DNA44, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 874 | `Unlabeled` | one-way | ATM, DNA45, DNAPKcs, Ku, LiIV | `kfixIV1` | internal-state conversion/modification | `DNA45(site!1~sdsb,h2ax!4~foc).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3).ATM(h2ax!4)  -> DNA45(site~ok,h2ax!1~foc).ATM(h2ax!1) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u) + LiIV(cs)` | Transforms ATM, DNA45, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 875 | `Unlabeled` | one-way | ATM, DNA46, DNAPKcs, Ku, LiIV | `kfixIV1` | internal-state conversion/modification | `DNA46(site!1~sdsb,h2ax!4~foc).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3).ATM(h2ax!4)  -> DNA46(site~ok,h2ax!1~foc).ATM(h2ax!1) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u) + LiIV(cs)` | Transforms ATM, DNA46, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 876 | `Unlabeled` | one-way | ATM, DNA47, DNAPKcs, Ku, LiIV | `kfixIV1` | internal-state conversion/modification | `DNA47(site!1~sdsb,h2ax!4~foc).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3).ATM(h2ax!4)  -> DNA47(site~ok,h2ax!1~foc).ATM(h2ax!1) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u) + LiIV(cs)` | Transforms ATM, DNA47, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 877 | `Unlabeled` | one-way | ATM, DNA48, DNAPKcs, Ku, LiIV | `kfixIV1` | internal-state conversion/modification | `DNA48(site!1~sdsb,h2ax!4~foc).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3).ATM(h2ax!4)  -> DNA48(site~ok,h2ax!1~foc).ATM(h2ax!1) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u) + LiIV(cs)` | Transforms ATM, DNA48, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 878 | `Unlabeled` | one-way | ATM, DNA49, DNAPKcs, Ku, LiIV | `kfixIV1` | internal-state conversion/modification | `DNA49(site!1~sdsb,h2ax!4~foc).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3).ATM(h2ax!4)  -> DNA49(site~ok,h2ax!1~foc).ATM(h2ax!1) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u) + LiIV(cs)` | Transforms ATM, DNA49, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 879 | `Unlabeled` | one-way | ATM, DNA50, DNAPKcs, Ku, LiIV | `kfixIV1` | internal-state conversion/modification | `DNA50(site!1~sdsb,h2ax!4~foc).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3).ATM(h2ax!4)  -> DNA50(site~ok,h2ax!1~foc).ATM(h2ax!1) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u) + LiIV(cs)` | Transforms ATM, DNA50, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 880 | `Unlabeled` | one-way | ATM, DNA1, DNAPKcs, Ku, LiIV | `kfixIV2` | internal-state conversion/modification | `DNA1(site!1~cdsb,h2ax!4~foc).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3).ATM(h2ax!4)  -> DNA1(site~ok,h2ax!1~foc).ATM(h2ax!1) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u) + LiIV(cs)` | Transforms ATM, DNA1, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 881 | `Unlabeled` | one-way | ATM, DNA2, DNAPKcs, Ku, LiIV | `kfixIV2` | internal-state conversion/modification | `DNA2(site!1~cdsb,h2ax!4~foc).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3).ATM(h2ax!4)  -> DNA2(site~ok,h2ax!1~foc).ATM(h2ax!1) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u) + LiIV(cs)` | Transforms ATM, DNA2, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 882 | `Unlabeled` | one-way | ATM, DNA3, DNAPKcs, Ku, LiIV | `kfixIV2` | internal-state conversion/modification | `DNA3(site!1~cdsb,h2ax!4~foc).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3).ATM(h2ax!4)  -> DNA3(site~ok,h2ax!1~foc).ATM(h2ax!1) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u) + LiIV(cs)` | Transforms ATM, DNA3, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 883 | `Unlabeled` | one-way | ATM, DNA4, DNAPKcs, Ku, LiIV | `kfixIV2` | internal-state conversion/modification | `DNA4(site!1~cdsb,h2ax!4~foc).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3).ATM(h2ax!4)  -> DNA4(site~ok,h2ax!1~foc).ATM(h2ax!1) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u) + LiIV(cs)` | Transforms ATM, DNA4, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 884 | `Unlabeled` | one-way | ATM, DNA5, DNAPKcs, Ku, LiIV | `kfixIV2` | internal-state conversion/modification | `DNA5(site!1~cdsb,h2ax!4~foc).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3).ATM(h2ax!4)  -> DNA5(site~ok,h2ax!1~foc).ATM(h2ax!1) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u) + LiIV(cs)` | Transforms ATM, DNA5, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 885 | `Unlabeled` | one-way | ATM, DNA6, DNAPKcs, Ku, LiIV | `kfixIV2` | internal-state conversion/modification | `DNA6(site!1~cdsb,h2ax!4~foc).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3).ATM(h2ax!4)  -> DNA6(site~ok,h2ax!1~foc).ATM(h2ax!1) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u) + LiIV(cs)` | Transforms ATM, DNA6, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 886 | `Unlabeled` | one-way | ATM, DNA7, DNAPKcs, Ku, LiIV | `kfixIV2` | internal-state conversion/modification | `DNA7(site!1~cdsb,h2ax!4~foc).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3).ATM(h2ax!4)  -> DNA7(site~ok,h2ax!1~foc).ATM(h2ax!1) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u) + LiIV(cs)` | Transforms ATM, DNA7, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 887 | `Unlabeled` | one-way | ATM, DNA8, DNAPKcs, Ku, LiIV | `kfixIV2` | internal-state conversion/modification | `DNA8(site!1~cdsb,h2ax!4~foc).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3).ATM(h2ax!4)  -> DNA8(site~ok,h2ax!1~foc).ATM(h2ax!1) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u) + LiIV(cs)` | Transforms ATM, DNA8, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 888 | `Unlabeled` | one-way | ATM, DNA9, DNAPKcs, Ku, LiIV | `kfixIV2` | internal-state conversion/modification | `DNA9(site!1~cdsb,h2ax!4~foc).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3).ATM(h2ax!4)  -> DNA9(site~ok,h2ax!1~foc).ATM(h2ax!1) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u) + LiIV(cs)` | Transforms ATM, DNA9, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 889 | `Unlabeled` | one-way | ATM, DNA10, DNAPKcs, Ku, LiIV | `kfixIV2` | internal-state conversion/modification | `DNA10(site!1~cdsb,h2ax!4~foc).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3).ATM(h2ax!4)  -> DNA10(site~ok,h2ax!1~foc).ATM(h2ax!1) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u) + LiIV(cs)` | Transforms ATM, DNA10, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 890 | `Unlabeled` | one-way | ATM, DNA11, DNAPKcs, Ku, LiIV | `kfixIV2` | internal-state conversion/modification | `DNA11(site!1~cdsb,h2ax!4~foc).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3).ATM(h2ax!4)  -> DNA11(site~ok,h2ax!1~foc).ATM(h2ax!1) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u) + LiIV(cs)` | Transforms ATM, DNA11, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 891 | `Unlabeled` | one-way | ATM, DNA12, DNAPKcs, Ku, LiIV | `kfixIV2` | internal-state conversion/modification | `DNA12(site!1~cdsb,h2ax!4~foc).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3).ATM(h2ax!4)  -> DNA12(site~ok,h2ax!1~foc).ATM(h2ax!1) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u) + LiIV(cs)` | Transforms ATM, DNA12, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 892 | `Unlabeled` | one-way | ATM, DNA13, DNAPKcs, Ku, LiIV | `kfixIV2` | internal-state conversion/modification | `DNA13(site!1~cdsb,h2ax!4~foc).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3).ATM(h2ax!4)  -> DNA13(site~ok,h2ax!1~foc).ATM(h2ax!1) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u) + LiIV(cs)` | Transforms ATM, DNA13, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 893 | `Unlabeled` | one-way | ATM, DNA14, DNAPKcs, Ku, LiIV | `kfixIV2` | internal-state conversion/modification | `DNA14(site!1~cdsb,h2ax!4~foc).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3).ATM(h2ax!4)  -> DNA14(site~ok,h2ax!1~foc).ATM(h2ax!1) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u) + LiIV(cs)` | Transforms ATM, DNA14, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 894 | `Unlabeled` | one-way | ATM, DNA15, DNAPKcs, Ku, LiIV | `kfixIV2` | internal-state conversion/modification | `DNA15(site!1~cdsb,h2ax!4~foc).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3).ATM(h2ax!4)  -> DNA15(site~ok,h2ax!1~foc).ATM(h2ax!1) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u) + LiIV(cs)` | Transforms ATM, DNA15, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 895 | `Unlabeled` | one-way | ATM, DNA16, DNAPKcs, Ku, LiIV | `kfixIV2` | internal-state conversion/modification | `DNA16(site!1~cdsb,h2ax!4~foc).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3).ATM(h2ax!4)  -> DNA16(site~ok,h2ax!1~foc).ATM(h2ax!1) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u) + LiIV(cs)` | Transforms ATM, DNA16, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 896 | `Unlabeled` | one-way | ATM, DNA17, DNAPKcs, Ku, LiIV | `kfixIV2` | internal-state conversion/modification | `DNA17(site!1~cdsb,h2ax!4~foc).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3).ATM(h2ax!4)  -> DNA17(site~ok,h2ax!1~foc).ATM(h2ax!1) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u) + LiIV(cs)` | Transforms ATM, DNA17, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 897 | `Unlabeled` | one-way | ATM, DNA18, DNAPKcs, Ku, LiIV | `kfixIV2` | internal-state conversion/modification | `DNA18(site!1~cdsb,h2ax!4~foc).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3).ATM(h2ax!4)  -> DNA18(site~ok,h2ax!1~foc).ATM(h2ax!1) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u) + LiIV(cs)` | Transforms ATM, DNA18, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 898 | `Unlabeled` | one-way | ATM, DNA19, DNAPKcs, Ku, LiIV | `kfixIV2` | internal-state conversion/modification | `DNA19(site!1~cdsb,h2ax!4~foc).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3).ATM(h2ax!4)  -> DNA19(site~ok,h2ax!1~foc).ATM(h2ax!1) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u) + LiIV(cs)` | Transforms ATM, DNA19, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 899 | `Unlabeled` | one-way | ATM, DNA20, DNAPKcs, Ku, LiIV | `kfixIV2` | internal-state conversion/modification | `DNA20(site!1~cdsb,h2ax!4~foc).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3).ATM(h2ax!4)  -> DNA20(site~ok,h2ax!1~foc).ATM(h2ax!1) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u) + LiIV(cs)` | Transforms ATM, DNA20, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 900 | `Unlabeled` | one-way | ATM, DNA21, DNAPKcs, Ku, LiIV | `kfixIV2` | internal-state conversion/modification | `DNA21(site!1~cdsb,h2ax!4~foc).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3).ATM(h2ax!4)  -> DNA21(site~ok,h2ax!1~foc).ATM(h2ax!1) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u) + LiIV(cs)` | Transforms ATM, DNA21, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 901 | `Unlabeled` | one-way | ATM, DNA22, DNAPKcs, Ku, LiIV | `kfixIV2` | internal-state conversion/modification | `DNA22(site!1~cdsb,h2ax!4~foc).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3).ATM(h2ax!4)  -> DNA22(site~ok,h2ax!1~foc).ATM(h2ax!1) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u) + LiIV(cs)` | Transforms ATM, DNA22, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 902 | `Unlabeled` | one-way | ATM, DNA23, DNAPKcs, Ku, LiIV | `kfixIV2` | internal-state conversion/modification | `DNA23(site!1~cdsb,h2ax!4~foc).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3).ATM(h2ax!4)  -> DNA23(site~ok,h2ax!1~foc).ATM(h2ax!1) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u) + LiIV(cs)` | Transforms ATM, DNA23, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 903 | `Unlabeled` | one-way | ATM, DNA24, DNAPKcs, Ku, LiIV | `kfixIV2` | internal-state conversion/modification | `DNA24(site!1~cdsb,h2ax!4~foc).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3).ATM(h2ax!4)  -> DNA24(site~ok,h2ax!1~foc).ATM(h2ax!1) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u) + LiIV(cs)` | Transforms ATM, DNA24, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 904 | `Unlabeled` | one-way | ATM, DNA25, DNAPKcs, Ku, LiIV | `kfixIV2` | internal-state conversion/modification | `DNA25(site!1~cdsb,h2ax!4~foc).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3).ATM(h2ax!4)  -> DNA25(site~ok,h2ax!1~foc).ATM(h2ax!1) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u) + LiIV(cs)` | Transforms ATM, DNA25, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 905 | `Unlabeled` | one-way | ATM, DNA26, DNAPKcs, Ku, LiIV | `kfixIV2` | internal-state conversion/modification | `DNA26(site!1~cdsb,h2ax!4~foc).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3).ATM(h2ax!4)  -> DNA26(site~ok,h2ax!1~foc).ATM(h2ax!1) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u) + LiIV(cs)` | Transforms ATM, DNA26, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 906 | `Unlabeled` | one-way | ATM, DNA27, DNAPKcs, Ku, LiIV | `kfixIV2` | internal-state conversion/modification | `DNA27(site!1~cdsb,h2ax!4~foc).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3).ATM(h2ax!4)  -> DNA27(site~ok,h2ax!1~foc).ATM(h2ax!1) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u) + LiIV(cs)` | Transforms ATM, DNA27, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 907 | `Unlabeled` | one-way | ATM, DNA28, DNAPKcs, Ku, LiIV | `kfixIV2` | internal-state conversion/modification | `DNA28(site!1~cdsb,h2ax!4~foc).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3).ATM(h2ax!4)  -> DNA28(site~ok,h2ax!1~foc).ATM(h2ax!1) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u) + LiIV(cs)` | Transforms ATM, DNA28, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 908 | `Unlabeled` | one-way | ATM, DNA29, DNAPKcs, Ku, LiIV | `kfixIV2` | internal-state conversion/modification | `DNA29(site!1~cdsb,h2ax!4~foc).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3).ATM(h2ax!4)  -> DNA29(site~ok,h2ax!1~foc).ATM(h2ax!1) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u) + LiIV(cs)` | Transforms ATM, DNA29, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 909 | `Unlabeled` | one-way | ATM, DNA30, DNAPKcs, Ku, LiIV | `kfixIV2` | internal-state conversion/modification | `DNA30(site!1~cdsb,h2ax!4~foc).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3).ATM(h2ax!4)  -> DNA30(site~ok,h2ax!1~foc).ATM(h2ax!1) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u) + LiIV(cs)` | Transforms ATM, DNA30, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 910 | `Unlabeled` | one-way | ATM, DNA31, DNAPKcs, Ku, LiIV | `kfixIV2` | internal-state conversion/modification | `DNA31(site!1~cdsb,h2ax!4~foc).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3).ATM(h2ax!4)  -> DNA31(site~ok,h2ax!1~foc).ATM(h2ax!1) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u) + LiIV(cs)` | Transforms ATM, DNA31, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 911 | `Unlabeled` | one-way | ATM, DNA32, DNAPKcs, Ku, LiIV | `kfixIV2` | internal-state conversion/modification | `DNA32(site!1~cdsb,h2ax!4~foc).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3).ATM(h2ax!4)  -> DNA32(site~ok,h2ax!1~foc).ATM(h2ax!1) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u) + LiIV(cs)` | Transforms ATM, DNA32, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 912 | `Unlabeled` | one-way | ATM, DNA33, DNAPKcs, Ku, LiIV | `kfixIV2` | internal-state conversion/modification | `DNA33(site!1~cdsb,h2ax!4~foc).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3).ATM(h2ax!4)  -> DNA33(site~ok,h2ax!1~foc).ATM(h2ax!1) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u) + LiIV(cs)` | Transforms ATM, DNA33, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 913 | `Unlabeled` | one-way | ATM, DNA34, DNAPKcs, Ku, LiIV | `kfixIV2` | internal-state conversion/modification | `DNA34(site!1~cdsb,h2ax!4~foc).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3).ATM(h2ax!4)  -> DNA34(site~ok,h2ax!1~foc).ATM(h2ax!1) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u) + LiIV(cs)` | Transforms ATM, DNA34, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 914 | `Unlabeled` | one-way | ATM, DNA35, DNAPKcs, Ku, LiIV | `kfixIV2` | internal-state conversion/modification | `DNA35(site!1~cdsb,h2ax!4~foc).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3).ATM(h2ax!4)  -> DNA35(site~ok,h2ax!1~foc).ATM(h2ax!1) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u) + LiIV(cs)` | Transforms ATM, DNA35, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 915 | `Unlabeled` | one-way | ATM, DNA36, DNAPKcs, Ku, LiIV | `kfixIV2` | internal-state conversion/modification | `DNA36(site!1~cdsb,h2ax!4~foc).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3).ATM(h2ax!4)  -> DNA36(site~ok,h2ax!1~foc).ATM(h2ax!1) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u) + LiIV(cs)` | Transforms ATM, DNA36, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 916 | `Unlabeled` | one-way | ATM, DNA37, DNAPKcs, Ku, LiIV | `kfixIV2` | internal-state conversion/modification | `DNA37(site!1~cdsb,h2ax!4~foc).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3).ATM(h2ax!4)  -> DNA37(site~ok,h2ax!1~foc).ATM(h2ax!1) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u) + LiIV(cs)` | Transforms ATM, DNA37, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 917 | `Unlabeled` | one-way | ATM, DNA38, DNAPKcs, Ku, LiIV | `kfixIV2` | internal-state conversion/modification | `DNA38(site!1~cdsb,h2ax!4~foc).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3).ATM(h2ax!4)  -> DNA38(site~ok,h2ax!1~foc).ATM(h2ax!1) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u) + LiIV(cs)` | Transforms ATM, DNA38, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 918 | `Unlabeled` | one-way | ATM, DNA39, DNAPKcs, Ku, LiIV | `kfixIV2` | internal-state conversion/modification | `DNA39(site!1~cdsb,h2ax!4~foc).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3).ATM(h2ax!4)  -> DNA39(site~ok,h2ax!1~foc).ATM(h2ax!1) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u) + LiIV(cs)` | Transforms ATM, DNA39, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 919 | `Unlabeled` | one-way | ATM, DNA40, DNAPKcs, Ku, LiIV | `kfixIV2` | internal-state conversion/modification | `DNA40(site!1~cdsb,h2ax!4~foc).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3).ATM(h2ax!4)  -> DNA40(site~ok,h2ax!1~foc).ATM(h2ax!1) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u) + LiIV(cs)` | Transforms ATM, DNA40, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 920 | `Unlabeled` | one-way | ATM, DNA41, DNAPKcs, Ku, LiIV | `kfixIV2` | internal-state conversion/modification | `DNA41(site!1~cdsb,h2ax!4~foc).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3).ATM(h2ax!4)  -> DNA41(site~ok,h2ax!1~foc).ATM(h2ax!1) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u) + LiIV(cs)` | Transforms ATM, DNA41, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 921 | `Unlabeled` | one-way | ATM, DNA42, DNAPKcs, Ku, LiIV | `kfixIV2` | internal-state conversion/modification | `DNA42(site!1~cdsb,h2ax!4~foc).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3).ATM(h2ax!4)  -> DNA42(site~ok,h2ax!1~foc).ATM(h2ax!1) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u) + LiIV(cs)` | Transforms ATM, DNA42, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 922 | `Unlabeled` | one-way | ATM, DNA43, DNAPKcs, Ku, LiIV | `kfixIV2` | internal-state conversion/modification | `DNA43(site!1~cdsb,h2ax!4~foc).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3).ATM(h2ax!4)  -> DNA43(site~ok,h2ax!1~foc).ATM(h2ax!1) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u) + LiIV(cs)` | Transforms ATM, DNA43, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 923 | `Unlabeled` | one-way | ATM, DNA44, DNAPKcs, Ku, LiIV | `kfixIV2` | internal-state conversion/modification | `DNA44(site!1~cdsb,h2ax!4~foc).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3).ATM(h2ax!4)  -> DNA44(site~ok,h2ax!1~foc).ATM(h2ax!1) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u) + LiIV(cs)` | Transforms ATM, DNA44, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 924 | `Unlabeled` | one-way | ATM, DNA45, DNAPKcs, Ku, LiIV | `kfixIV2` | internal-state conversion/modification | `DNA45(site!1~cdsb,h2ax!4~foc).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3).ATM(h2ax!4)  -> DNA45(site~ok,h2ax!1~foc).ATM(h2ax!1) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u) + LiIV(cs)` | Transforms ATM, DNA45, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 925 | `Unlabeled` | one-way | ATM, DNA46, DNAPKcs, Ku, LiIV | `kfixIV2` | internal-state conversion/modification | `DNA46(site!1~cdsb,h2ax!4~foc).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3).ATM(h2ax!4)  -> DNA46(site~ok,h2ax!1~foc).ATM(h2ax!1) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u) + LiIV(cs)` | Transforms ATM, DNA46, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 926 | `Unlabeled` | one-way | ATM, DNA47, DNAPKcs, Ku, LiIV | `kfixIV2` | internal-state conversion/modification | `DNA47(site!1~cdsb,h2ax!4~foc).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3).ATM(h2ax!4)  -> DNA47(site~ok,h2ax!1~foc).ATM(h2ax!1) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u) + LiIV(cs)` | Transforms ATM, DNA47, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 927 | `Unlabeled` | one-way | ATM, DNA48, DNAPKcs, Ku, LiIV | `kfixIV2` | internal-state conversion/modification | `DNA48(site!1~cdsb,h2ax!4~foc).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3).ATM(h2ax!4)  -> DNA48(site~ok,h2ax!1~foc).ATM(h2ax!1) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u) + LiIV(cs)` | Transforms ATM, DNA48, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 928 | `Unlabeled` | one-way | ATM, DNA49, DNAPKcs, Ku, LiIV | `kfixIV2` | internal-state conversion/modification | `DNA49(site!1~cdsb,h2ax!4~foc).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3).ATM(h2ax!4)  -> DNA49(site~ok,h2ax!1~foc).ATM(h2ax!1) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u) + LiIV(cs)` | Transforms ATM, DNA49, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 929 | `Unlabeled` | one-way | ATM, DNA50, DNAPKcs, Ku, LiIV | `kfixIV2` | internal-state conversion/modification | `DNA50(site!1~cdsb,h2ax!4~foc).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV!3,psite~p).LiIV(cs!3).ATM(h2ax!4)  -> DNA50(site~ok,h2ax!1~foc).ATM(h2ax!1) + Ku(dna,cs) + DNAPKcs(ku,liIV,psite~u) + LiIV(cs)` | Transforms ATM, DNA50, DNAPKcs, Ku, LiIV by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 930 | `Unlabeled` | one-way | DNA1, PARP | `kPARP1` | state and binding-pattern rewrite | `DNA1(site~sdsb) + PARP(dna,liIII)  -> DNA1(site!1~sdsb).PARP(dna!1,liIII)` | Transforms DNA1, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 931 | `Unlabeled` | one-way | DNA2, PARP | `kPARP1` | state and binding-pattern rewrite | `DNA2(site~sdsb) + PARP(dna,liIII)  -> DNA2(site!1~sdsb).PARP(dna!1,liIII)` | Transforms DNA2, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 932 | `Unlabeled` | one-way | DNA3, PARP | `kPARP1` | state and binding-pattern rewrite | `DNA3(site~sdsb) + PARP(dna,liIII)  -> DNA3(site!1~sdsb).PARP(dna!1,liIII)` | Transforms DNA3, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 933 | `Unlabeled` | one-way | DNA4, PARP | `kPARP1` | state and binding-pattern rewrite | `DNA4(site~sdsb) + PARP(dna,liIII)  -> DNA4(site!1~sdsb).PARP(dna!1,liIII)` | Transforms DNA4, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 934 | `Unlabeled` | one-way | DNA5, PARP | `kPARP1` | state and binding-pattern rewrite | `DNA5(site~sdsb) + PARP(dna,liIII)  -> DNA5(site!1~sdsb).PARP(dna!1,liIII)` | Transforms DNA5, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 935 | `Unlabeled` | one-way | DNA6, PARP | `kPARP1` | state and binding-pattern rewrite | `DNA6(site~sdsb) + PARP(dna,liIII)  -> DNA6(site!1~sdsb).PARP(dna!1,liIII)` | Transforms DNA6, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 936 | `Unlabeled` | one-way | DNA7, PARP | `kPARP1` | state and binding-pattern rewrite | `DNA7(site~sdsb) + PARP(dna,liIII)  -> DNA7(site!1~sdsb).PARP(dna!1,liIII)` | Transforms DNA7, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 937 | `Unlabeled` | one-way | DNA8, PARP | `kPARP1` | state and binding-pattern rewrite | `DNA8(site~sdsb) + PARP(dna,liIII)  -> DNA8(site!1~sdsb).PARP(dna!1,liIII)` | Transforms DNA8, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 938 | `Unlabeled` | one-way | DNA9, PARP | `kPARP1` | state and binding-pattern rewrite | `DNA9(site~sdsb) + PARP(dna,liIII)  -> DNA9(site!1~sdsb).PARP(dna!1,liIII)` | Transforms DNA9, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 939 | `Unlabeled` | one-way | DNA10, PARP | `kPARP1` | state and binding-pattern rewrite | `DNA10(site~sdsb) + PARP(dna,liIII)  -> DNA10(site!1~sdsb).PARP(dna!1,liIII)` | Transforms DNA10, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 940 | `Unlabeled` | one-way | DNA11, PARP | `kPARP1` | state and binding-pattern rewrite | `DNA11(site~sdsb) + PARP(dna,liIII)  -> DNA11(site!1~sdsb).PARP(dna!1,liIII)` | Transforms DNA11, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 941 | `Unlabeled` | one-way | DNA12, PARP | `kPARP1` | state and binding-pattern rewrite | `DNA12(site~sdsb) + PARP(dna,liIII)  -> DNA12(site!1~sdsb).PARP(dna!1,liIII)` | Transforms DNA12, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 942 | `Unlabeled` | one-way | DNA13, PARP | `kPARP1` | state and binding-pattern rewrite | `DNA13(site~sdsb) + PARP(dna,liIII)  -> DNA13(site!1~sdsb).PARP(dna!1,liIII)` | Transforms DNA13, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 943 | `Unlabeled` | one-way | DNA14, PARP | `kPARP1` | state and binding-pattern rewrite | `DNA14(site~sdsb) + PARP(dna,liIII)  -> DNA14(site!1~sdsb).PARP(dna!1,liIII)` | Transforms DNA14, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 944 | `Unlabeled` | one-way | DNA15, PARP | `kPARP1` | state and binding-pattern rewrite | `DNA15(site~sdsb) + PARP(dna,liIII)  -> DNA15(site!1~sdsb).PARP(dna!1,liIII)` | Transforms DNA15, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 945 | `Unlabeled` | one-way | DNA16, PARP | `kPARP1` | state and binding-pattern rewrite | `DNA16(site~sdsb) + PARP(dna,liIII)  -> DNA16(site!1~sdsb).PARP(dna!1,liIII)` | Transforms DNA16, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 946 | `Unlabeled` | one-way | DNA17, PARP | `kPARP1` | state and binding-pattern rewrite | `DNA17(site~sdsb) + PARP(dna,liIII)  -> DNA17(site!1~sdsb).PARP(dna!1,liIII)` | Transforms DNA17, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 947 | `Unlabeled` | one-way | DNA18, PARP | `kPARP1` | state and binding-pattern rewrite | `DNA18(site~sdsb) + PARP(dna,liIII)  -> DNA18(site!1~sdsb).PARP(dna!1,liIII)` | Transforms DNA18, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 948 | `Unlabeled` | one-way | DNA19, PARP | `kPARP1` | state and binding-pattern rewrite | `DNA19(site~sdsb) + PARP(dna,liIII)  -> DNA19(site!1~sdsb).PARP(dna!1,liIII)` | Transforms DNA19, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 949 | `Unlabeled` | one-way | DNA20, PARP | `kPARP1` | state and binding-pattern rewrite | `DNA20(site~sdsb) + PARP(dna,liIII)  -> DNA20(site!1~sdsb).PARP(dna!1,liIII)` | Transforms DNA20, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 950 | `Unlabeled` | one-way | DNA21, PARP | `kPARP1` | state and binding-pattern rewrite | `DNA21(site~sdsb) + PARP(dna,liIII)  -> DNA21(site!1~sdsb).PARP(dna!1,liIII)` | Transforms DNA21, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 951 | `Unlabeled` | one-way | DNA22, PARP | `kPARP1` | state and binding-pattern rewrite | `DNA22(site~sdsb) + PARP(dna,liIII)  -> DNA22(site!1~sdsb).PARP(dna!1,liIII)` | Transforms DNA22, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 952 | `Unlabeled` | one-way | DNA23, PARP | `kPARP1` | state and binding-pattern rewrite | `DNA23(site~sdsb) + PARP(dna,liIII)  -> DNA23(site!1~sdsb).PARP(dna!1,liIII)` | Transforms DNA23, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 953 | `Unlabeled` | one-way | DNA24, PARP | `kPARP1` | state and binding-pattern rewrite | `DNA24(site~sdsb) + PARP(dna,liIII)  -> DNA24(site!1~sdsb).PARP(dna!1,liIII)` | Transforms DNA24, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 954 | `Unlabeled` | one-way | DNA25, PARP | `kPARP1` | state and binding-pattern rewrite | `DNA25(site~sdsb) + PARP(dna,liIII)  -> DNA25(site!1~sdsb).PARP(dna!1,liIII)` | Transforms DNA25, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 955 | `Unlabeled` | one-way | DNA26, PARP | `kPARP1` | state and binding-pattern rewrite | `DNA26(site~sdsb) + PARP(dna,liIII)  -> DNA26(site!1~sdsb).PARP(dna!1,liIII)` | Transforms DNA26, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 956 | `Unlabeled` | one-way | DNA27, PARP | `kPARP1` | state and binding-pattern rewrite | `DNA27(site~sdsb) + PARP(dna,liIII)  -> DNA27(site!1~sdsb).PARP(dna!1,liIII)` | Transforms DNA27, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 957 | `Unlabeled` | one-way | DNA28, PARP | `kPARP1` | state and binding-pattern rewrite | `DNA28(site~sdsb) + PARP(dna,liIII)  -> DNA28(site!1~sdsb).PARP(dna!1,liIII)` | Transforms DNA28, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 958 | `Unlabeled` | one-way | DNA29, PARP | `kPARP1` | state and binding-pattern rewrite | `DNA29(site~sdsb) + PARP(dna,liIII)  -> DNA29(site!1~sdsb).PARP(dna!1,liIII)` | Transforms DNA29, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 959 | `Unlabeled` | one-way | DNA30, PARP | `kPARP1` | state and binding-pattern rewrite | `DNA30(site~sdsb) + PARP(dna,liIII)  -> DNA30(site!1~sdsb).PARP(dna!1,liIII)` | Transforms DNA30, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 960 | `Unlabeled` | one-way | DNA31, PARP | `kPARP1` | state and binding-pattern rewrite | `DNA31(site~sdsb) + PARP(dna,liIII)  -> DNA31(site!1~sdsb).PARP(dna!1,liIII)` | Transforms DNA31, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 961 | `Unlabeled` | one-way | DNA32, PARP | `kPARP1` | state and binding-pattern rewrite | `DNA32(site~sdsb) + PARP(dna,liIII)  -> DNA32(site!1~sdsb).PARP(dna!1,liIII)` | Transforms DNA32, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 962 | `Unlabeled` | one-way | DNA33, PARP | `kPARP1` | state and binding-pattern rewrite | `DNA33(site~sdsb) + PARP(dna,liIII)  -> DNA33(site!1~sdsb).PARP(dna!1,liIII)` | Transforms DNA33, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 963 | `Unlabeled` | one-way | DNA34, PARP | `kPARP1` | state and binding-pattern rewrite | `DNA34(site~sdsb) + PARP(dna,liIII)  -> DNA34(site!1~sdsb).PARP(dna!1,liIII)` | Transforms DNA34, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 964 | `Unlabeled` | one-way | DNA35, PARP | `kPARP1` | state and binding-pattern rewrite | `DNA35(site~sdsb) + PARP(dna,liIII)  -> DNA35(site!1~sdsb).PARP(dna!1,liIII)` | Transforms DNA35, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 965 | `Unlabeled` | one-way | DNA36, PARP | `kPARP1` | state and binding-pattern rewrite | `DNA36(site~sdsb) + PARP(dna,liIII)  -> DNA36(site!1~sdsb).PARP(dna!1,liIII)` | Transforms DNA36, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 966 | `Unlabeled` | one-way | DNA37, PARP | `kPARP1` | state and binding-pattern rewrite | `DNA37(site~sdsb) + PARP(dna,liIII)  -> DNA37(site!1~sdsb).PARP(dna!1,liIII)` | Transforms DNA37, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 967 | `Unlabeled` | one-way | DNA38, PARP | `kPARP1` | state and binding-pattern rewrite | `DNA38(site~sdsb) + PARP(dna,liIII)  -> DNA38(site!1~sdsb).PARP(dna!1,liIII)` | Transforms DNA38, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 968 | `Unlabeled` | one-way | DNA39, PARP | `kPARP1` | state and binding-pattern rewrite | `DNA39(site~sdsb) + PARP(dna,liIII)  -> DNA39(site!1~sdsb).PARP(dna!1,liIII)` | Transforms DNA39, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 969 | `Unlabeled` | one-way | DNA40, PARP | `kPARP1` | state and binding-pattern rewrite | `DNA40(site~sdsb) + PARP(dna,liIII)  -> DNA40(site!1~sdsb).PARP(dna!1,liIII)` | Transforms DNA40, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 970 | `Unlabeled` | one-way | DNA41, PARP | `kPARP1` | state and binding-pattern rewrite | `DNA41(site~sdsb) + PARP(dna,liIII)  -> DNA41(site!1~sdsb).PARP(dna!1,liIII)` | Transforms DNA41, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 971 | `Unlabeled` | one-way | DNA42, PARP | `kPARP1` | state and binding-pattern rewrite | `DNA42(site~sdsb) + PARP(dna,liIII)  -> DNA42(site!1~sdsb).PARP(dna!1,liIII)` | Transforms DNA42, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 972 | `Unlabeled` | one-way | DNA43, PARP | `kPARP1` | state and binding-pattern rewrite | `DNA43(site~sdsb) + PARP(dna,liIII)  -> DNA43(site!1~sdsb).PARP(dna!1,liIII)` | Transforms DNA43, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 973 | `Unlabeled` | one-way | DNA44, PARP | `kPARP1` | state and binding-pattern rewrite | `DNA44(site~sdsb) + PARP(dna,liIII)  -> DNA44(site!1~sdsb).PARP(dna!1,liIII)` | Transforms DNA44, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 974 | `Unlabeled` | one-way | DNA45, PARP | `kPARP1` | state and binding-pattern rewrite | `DNA45(site~sdsb) + PARP(dna,liIII)  -> DNA45(site!1~sdsb).PARP(dna!1,liIII)` | Transforms DNA45, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 975 | `Unlabeled` | one-way | DNA46, PARP | `kPARP1` | state and binding-pattern rewrite | `DNA46(site~sdsb) + PARP(dna,liIII)  -> DNA46(site!1~sdsb).PARP(dna!1,liIII)` | Transforms DNA46, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 976 | `Unlabeled` | one-way | DNA47, PARP | `kPARP1` | state and binding-pattern rewrite | `DNA47(site~sdsb) + PARP(dna,liIII)  -> DNA47(site!1~sdsb).PARP(dna!1,liIII)` | Transforms DNA47, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 977 | `Unlabeled` | one-way | DNA48, PARP | `kPARP1` | state and binding-pattern rewrite | `DNA48(site~sdsb) + PARP(dna,liIII)  -> DNA48(site!1~sdsb).PARP(dna!1,liIII)` | Transforms DNA48, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 978 | `Unlabeled` | one-way | DNA49, PARP | `kPARP1` | state and binding-pattern rewrite | `DNA49(site~sdsb) + PARP(dna,liIII)  -> DNA49(site!1~sdsb).PARP(dna!1,liIII)` | Transforms DNA49, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 979 | `Unlabeled` | one-way | DNA50, PARP | `kPARP1` | state and binding-pattern rewrite | `DNA50(site~sdsb) + PARP(dna,liIII)  -> DNA50(site!1~sdsb).PARP(dna!1,liIII)` | Transforms DNA50, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 980 | `Unlabeled` | one-way | DNA1, PARP | `kPARP2` | state and binding-pattern rewrite | `DNA1(site~cdsb) + PARP(dna,liIII)  -> DNA1(site!1~cdsb).PARP(dna!1,liIII)` | Transforms DNA1, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 981 | `Unlabeled` | one-way | DNA2, PARP | `kPARP2` | state and binding-pattern rewrite | `DNA2(site~cdsb) + PARP(dna,liIII)  -> DNA2(site!1~cdsb).PARP(dna!1,liIII)` | Transforms DNA2, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 982 | `Unlabeled` | one-way | DNA3, PARP | `kPARP2` | state and binding-pattern rewrite | `DNA3(site~cdsb) + PARP(dna,liIII)  -> DNA3(site!1~cdsb).PARP(dna!1,liIII)` | Transforms DNA3, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 983 | `Unlabeled` | one-way | DNA4, PARP | `kPARP2` | state and binding-pattern rewrite | `DNA4(site~cdsb) + PARP(dna,liIII)  -> DNA4(site!1~cdsb).PARP(dna!1,liIII)` | Transforms DNA4, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 984 | `Unlabeled` | one-way | DNA5, PARP | `kPARP2` | state and binding-pattern rewrite | `DNA5(site~cdsb) + PARP(dna,liIII)  -> DNA5(site!1~cdsb).PARP(dna!1,liIII)` | Transforms DNA5, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 985 | `Unlabeled` | one-way | DNA6, PARP | `kPARP2` | state and binding-pattern rewrite | `DNA6(site~cdsb) + PARP(dna,liIII)  -> DNA6(site!1~cdsb).PARP(dna!1,liIII)` | Transforms DNA6, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 986 | `Unlabeled` | one-way | DNA7, PARP | `kPARP2` | state and binding-pattern rewrite | `DNA7(site~cdsb) + PARP(dna,liIII)  -> DNA7(site!1~cdsb).PARP(dna!1,liIII)` | Transforms DNA7, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 987 | `Unlabeled` | one-way | DNA8, PARP | `kPARP2` | state and binding-pattern rewrite | `DNA8(site~cdsb) + PARP(dna,liIII)  -> DNA8(site!1~cdsb).PARP(dna!1,liIII)` | Transforms DNA8, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 988 | `Unlabeled` | one-way | DNA9, PARP | `kPARP2` | state and binding-pattern rewrite | `DNA9(site~cdsb) + PARP(dna,liIII)  -> DNA9(site!1~cdsb).PARP(dna!1,liIII)` | Transforms DNA9, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 989 | `Unlabeled` | one-way | DNA10, PARP | `kPARP2` | state and binding-pattern rewrite | `DNA10(site~cdsb) + PARP(dna,liIII)  -> DNA10(site!1~cdsb).PARP(dna!1,liIII)` | Transforms DNA10, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 990 | `Unlabeled` | one-way | DNA11, PARP | `kPARP2` | state and binding-pattern rewrite | `DNA11(site~cdsb) + PARP(dna,liIII)  -> DNA11(site!1~cdsb).PARP(dna!1,liIII)` | Transforms DNA11, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 991 | `Unlabeled` | one-way | DNA12, PARP | `kPARP2` | state and binding-pattern rewrite | `DNA12(site~cdsb) + PARP(dna,liIII)  -> DNA12(site!1~cdsb).PARP(dna!1,liIII)` | Transforms DNA12, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 992 | `Unlabeled` | one-way | DNA13, PARP | `kPARP2` | state and binding-pattern rewrite | `DNA13(site~cdsb) + PARP(dna,liIII)  -> DNA13(site!1~cdsb).PARP(dna!1,liIII)` | Transforms DNA13, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 993 | `Unlabeled` | one-way | DNA14, PARP | `kPARP2` | state and binding-pattern rewrite | `DNA14(site~cdsb) + PARP(dna,liIII)  -> DNA14(site!1~cdsb).PARP(dna!1,liIII)` | Transforms DNA14, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 994 | `Unlabeled` | one-way | DNA15, PARP | `kPARP2` | state and binding-pattern rewrite | `DNA15(site~cdsb) + PARP(dna,liIII)  -> DNA15(site!1~cdsb).PARP(dna!1,liIII)` | Transforms DNA15, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 995 | `Unlabeled` | one-way | DNA16, PARP | `kPARP2` | state and binding-pattern rewrite | `DNA16(site~cdsb) + PARP(dna,liIII)  -> DNA16(site!1~cdsb).PARP(dna!1,liIII)` | Transforms DNA16, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 996 | `Unlabeled` | one-way | DNA17, PARP | `kPARP2` | state and binding-pattern rewrite | `DNA17(site~cdsb) + PARP(dna,liIII)  -> DNA17(site!1~cdsb).PARP(dna!1,liIII)` | Transforms DNA17, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 997 | `Unlabeled` | one-way | DNA18, PARP | `kPARP2` | state and binding-pattern rewrite | `DNA18(site~cdsb) + PARP(dna,liIII)  -> DNA18(site!1~cdsb).PARP(dna!1,liIII)` | Transforms DNA18, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 998 | `Unlabeled` | one-way | DNA19, PARP | `kPARP2` | state and binding-pattern rewrite | `DNA19(site~cdsb) + PARP(dna,liIII)  -> DNA19(site!1~cdsb).PARP(dna!1,liIII)` | Transforms DNA19, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 999 | `Unlabeled` | one-way | DNA20, PARP | `kPARP2` | state and binding-pattern rewrite | `DNA20(site~cdsb) + PARP(dna,liIII)  -> DNA20(site!1~cdsb).PARP(dna!1,liIII)` | Transforms DNA20, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 1000 | `Unlabeled` | one-way | DNA21, PARP | `kPARP2` | state and binding-pattern rewrite | `DNA21(site~cdsb) + PARP(dna,liIII)  -> DNA21(site!1~cdsb).PARP(dna!1,liIII)` | Transforms DNA21, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

### Rules 1001-1250

| # | Rule label/name | Direction | Participants | Rate/expression | Modeled change | Rule pattern | Technical meaning |
| ---: | --- | --- | --- | --- | --- | --- | --- |

| 1001 | `Unlabeled` | one-way | DNA22, PARP | `kPARP2` | state and binding-pattern rewrite | `DNA22(site~cdsb) + PARP(dna,liIII)  -> DNA22(site!1~cdsb).PARP(dna!1,liIII)` | Transforms DNA22, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 1002 | `Unlabeled` | one-way | DNA23, PARP | `kPARP2` | state and binding-pattern rewrite | `DNA23(site~cdsb) + PARP(dna,liIII)  -> DNA23(site!1~cdsb).PARP(dna!1,liIII)` | Transforms DNA23, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 1003 | `Unlabeled` | one-way | DNA24, PARP | `kPARP2` | state and binding-pattern rewrite | `DNA24(site~cdsb) + PARP(dna,liIII)  -> DNA24(site!1~cdsb).PARP(dna!1,liIII)` | Transforms DNA24, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 1004 | `Unlabeled` | one-way | DNA25, PARP | `kPARP2` | state and binding-pattern rewrite | `DNA25(site~cdsb) + PARP(dna,liIII)  -> DNA25(site!1~cdsb).PARP(dna!1,liIII)` | Transforms DNA25, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 1005 | `Unlabeled` | one-way | DNA26, PARP | `kPARP2` | state and binding-pattern rewrite | `DNA26(site~cdsb) + PARP(dna,liIII)  -> DNA26(site!1~cdsb).PARP(dna!1,liIII)` | Transforms DNA26, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 1006 | `Unlabeled` | one-way | DNA27, PARP | `kPARP2` | state and binding-pattern rewrite | `DNA27(site~cdsb) + PARP(dna,liIII)  -> DNA27(site!1~cdsb).PARP(dna!1,liIII)` | Transforms DNA27, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 1007 | `Unlabeled` | one-way | DNA28, PARP | `kPARP2` | state and binding-pattern rewrite | `DNA28(site~cdsb) + PARP(dna,liIII)  -> DNA28(site!1~cdsb).PARP(dna!1,liIII)` | Transforms DNA28, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 1008 | `Unlabeled` | one-way | DNA29, PARP | `kPARP2` | state and binding-pattern rewrite | `DNA29(site~cdsb) + PARP(dna,liIII)  -> DNA29(site!1~cdsb).PARP(dna!1,liIII)` | Transforms DNA29, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 1009 | `Unlabeled` | one-way | DNA30, PARP | `kPARP2` | state and binding-pattern rewrite | `DNA30(site~cdsb) + PARP(dna,liIII)  -> DNA30(site!1~cdsb).PARP(dna!1,liIII)` | Transforms DNA30, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 1010 | `Unlabeled` | one-way | DNA31, PARP | `kPARP2` | state and binding-pattern rewrite | `DNA31(site~cdsb) + PARP(dna,liIII)  -> DNA31(site!1~cdsb).PARP(dna!1,liIII)` | Transforms DNA31, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 1011 | `Unlabeled` | one-way | DNA32, PARP | `kPARP2` | state and binding-pattern rewrite | `DNA32(site~cdsb) + PARP(dna,liIII)  -> DNA32(site!1~cdsb).PARP(dna!1,liIII)` | Transforms DNA32, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 1012 | `Unlabeled` | one-way | DNA33, PARP | `kPARP2` | state and binding-pattern rewrite | `DNA33(site~cdsb) + PARP(dna,liIII)  -> DNA33(site!1~cdsb).PARP(dna!1,liIII)` | Transforms DNA33, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 1013 | `Unlabeled` | one-way | DNA34, PARP | `kPARP2` | state and binding-pattern rewrite | `DNA34(site~cdsb) + PARP(dna,liIII)  -> DNA34(site!1~cdsb).PARP(dna!1,liIII)` | Transforms DNA34, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 1014 | `Unlabeled` | one-way | DNA35, PARP | `kPARP2` | state and binding-pattern rewrite | `DNA35(site~cdsb) + PARP(dna,liIII)  -> DNA35(site!1~cdsb).PARP(dna!1,liIII)` | Transforms DNA35, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 1015 | `Unlabeled` | one-way | DNA36, PARP | `kPARP2` | state and binding-pattern rewrite | `DNA36(site~cdsb) + PARP(dna,liIII)  -> DNA36(site!1~cdsb).PARP(dna!1,liIII)` | Transforms DNA36, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 1016 | `Unlabeled` | one-way | DNA37, PARP | `kPARP2` | state and binding-pattern rewrite | `DNA37(site~cdsb) + PARP(dna,liIII)  -> DNA37(site!1~cdsb).PARP(dna!1,liIII)` | Transforms DNA37, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 1017 | `Unlabeled` | one-way | DNA38, PARP | `kPARP2` | state and binding-pattern rewrite | `DNA38(site~cdsb) + PARP(dna,liIII)  -> DNA38(site!1~cdsb).PARP(dna!1,liIII)` | Transforms DNA38, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 1018 | `Unlabeled` | one-way | DNA39, PARP | `kPARP2` | state and binding-pattern rewrite | `DNA39(site~cdsb) + PARP(dna,liIII)  -> DNA39(site!1~cdsb).PARP(dna!1,liIII)` | Transforms DNA39, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 1019 | `Unlabeled` | one-way | DNA40, PARP | `kPARP2` | state and binding-pattern rewrite | `DNA40(site~cdsb) + PARP(dna,liIII)  -> DNA40(site!1~cdsb).PARP(dna!1,liIII)` | Transforms DNA40, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 1020 | `Unlabeled` | one-way | DNA41, PARP | `kPARP2` | state and binding-pattern rewrite | `DNA41(site~cdsb) + PARP(dna,liIII)  -> DNA41(site!1~cdsb).PARP(dna!1,liIII)` | Transforms DNA41, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 1021 | `Unlabeled` | one-way | DNA42, PARP | `kPARP2` | state and binding-pattern rewrite | `DNA42(site~cdsb) + PARP(dna,liIII)  -> DNA42(site!1~cdsb).PARP(dna!1,liIII)` | Transforms DNA42, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 1022 | `Unlabeled` | one-way | DNA43, PARP | `kPARP2` | state and binding-pattern rewrite | `DNA43(site~cdsb) + PARP(dna,liIII)  -> DNA43(site!1~cdsb).PARP(dna!1,liIII)` | Transforms DNA43, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 1023 | `Unlabeled` | one-way | DNA44, PARP | `kPARP2` | state and binding-pattern rewrite | `DNA44(site~cdsb) + PARP(dna,liIII)  -> DNA44(site!1~cdsb).PARP(dna!1,liIII)` | Transforms DNA44, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 1024 | `Unlabeled` | one-way | DNA45, PARP | `kPARP2` | state and binding-pattern rewrite | `DNA45(site~cdsb) + PARP(dna,liIII)  -> DNA45(site!1~cdsb).PARP(dna!1,liIII)` | Transforms DNA45, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 1025 | `Unlabeled` | one-way | DNA46, PARP | `kPARP2` | state and binding-pattern rewrite | `DNA46(site~cdsb) + PARP(dna,liIII)  -> DNA46(site!1~cdsb).PARP(dna!1,liIII)` | Transforms DNA46, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 1026 | `Unlabeled` | one-way | DNA47, PARP | `kPARP2` | state and binding-pattern rewrite | `DNA47(site~cdsb) + PARP(dna,liIII)  -> DNA47(site!1~cdsb).PARP(dna!1,liIII)` | Transforms DNA47, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 1027 | `Unlabeled` | one-way | DNA48, PARP | `kPARP2` | state and binding-pattern rewrite | `DNA48(site~cdsb) + PARP(dna,liIII)  -> DNA48(site!1~cdsb).PARP(dna!1,liIII)` | Transforms DNA48, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 1028 | `Unlabeled` | one-way | DNA49, PARP | `kPARP2` | state and binding-pattern rewrite | `DNA49(site~cdsb) + PARP(dna,liIII)  -> DNA49(site!1~cdsb).PARP(dna!1,liIII)` | Transforms DNA49, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 1029 | `Unlabeled` | one-way | DNA50, PARP | `kPARP2` | state and binding-pattern rewrite | `DNA50(site~cdsb) + PARP(dna,liIII)  -> DNA50(site!1~cdsb).PARP(dna!1,liIII)` | Transforms DNA50, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 1030 | `Unlabeled` | one-way | DNA1, PARP | `kdPARP1` | state and binding-pattern rewrite | `DNA1(site!1~sdsb).PARP(dna!1,liIII)  -> DNA1(site~sdsb) + PARP(dna,liIII)` | Transforms DNA1, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 1031 | `Unlabeled` | one-way | DNA2, PARP | `kdPARP1` | state and binding-pattern rewrite | `DNA2(site!1~sdsb).PARP(dna!1,liIII)  -> DNA2(site~sdsb) + PARP(dna,liIII)` | Transforms DNA2, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 1032 | `Unlabeled` | one-way | DNA3, PARP | `kdPARP1` | state and binding-pattern rewrite | `DNA3(site!1~sdsb).PARP(dna!1,liIII)  -> DNA3(site~sdsb) + PARP(dna,liIII)` | Transforms DNA3, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 1033 | `Unlabeled` | one-way | DNA4, PARP | `kdPARP1` | state and binding-pattern rewrite | `DNA4(site!1~sdsb).PARP(dna!1,liIII)  -> DNA4(site~sdsb) + PARP(dna,liIII)` | Transforms DNA4, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 1034 | `Unlabeled` | one-way | DNA5, PARP | `kdPARP1` | state and binding-pattern rewrite | `DNA5(site!1~sdsb).PARP(dna!1,liIII)  -> DNA5(site~sdsb) + PARP(dna,liIII)` | Transforms DNA5, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 1035 | `Unlabeled` | one-way | DNA6, PARP | `kdPARP1` | state and binding-pattern rewrite | `DNA6(site!1~sdsb).PARP(dna!1,liIII)  -> DNA6(site~sdsb) + PARP(dna,liIII)` | Transforms DNA6, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 1036 | `Unlabeled` | one-way | DNA7, PARP | `kdPARP1` | state and binding-pattern rewrite | `DNA7(site!1~sdsb).PARP(dna!1,liIII)  -> DNA7(site~sdsb) + PARP(dna,liIII)` | Transforms DNA7, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 1037 | `Unlabeled` | one-way | DNA8, PARP | `kdPARP1` | state and binding-pattern rewrite | `DNA8(site!1~sdsb).PARP(dna!1,liIII)  -> DNA8(site~sdsb) + PARP(dna,liIII)` | Transforms DNA8, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 1038 | `Unlabeled` | one-way | DNA9, PARP | `kdPARP1` | state and binding-pattern rewrite | `DNA9(site!1~sdsb).PARP(dna!1,liIII)  -> DNA9(site~sdsb) + PARP(dna,liIII)` | Transforms DNA9, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 1039 | `Unlabeled` | one-way | DNA10, PARP | `kdPARP1` | state and binding-pattern rewrite | `DNA10(site!1~sdsb).PARP(dna!1,liIII)  -> DNA10(site~sdsb) + PARP(dna,liIII)` | Transforms DNA10, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 1040 | `Unlabeled` | one-way | DNA11, PARP | `kdPARP1` | state and binding-pattern rewrite | `DNA11(site!1~sdsb).PARP(dna!1,liIII)  -> DNA11(site~sdsb) + PARP(dna,liIII)` | Transforms DNA11, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 1041 | `Unlabeled` | one-way | DNA12, PARP | `kdPARP1` | state and binding-pattern rewrite | `DNA12(site!1~sdsb).PARP(dna!1,liIII)  -> DNA12(site~sdsb) + PARP(dna,liIII)` | Transforms DNA12, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 1042 | `Unlabeled` | one-way | DNA13, PARP | `kdPARP1` | state and binding-pattern rewrite | `DNA13(site!1~sdsb).PARP(dna!1,liIII)  -> DNA13(site~sdsb) + PARP(dna,liIII)` | Transforms DNA13, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 1043 | `Unlabeled` | one-way | DNA14, PARP | `kdPARP1` | state and binding-pattern rewrite | `DNA14(site!1~sdsb).PARP(dna!1,liIII)  -> DNA14(site~sdsb) + PARP(dna,liIII)` | Transforms DNA14, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 1044 | `Unlabeled` | one-way | DNA15, PARP | `kdPARP1` | state and binding-pattern rewrite | `DNA15(site!1~sdsb).PARP(dna!1,liIII)  -> DNA15(site~sdsb) + PARP(dna,liIII)` | Transforms DNA15, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 1045 | `Unlabeled` | one-way | DNA16, PARP | `kdPARP1` | state and binding-pattern rewrite | `DNA16(site!1~sdsb).PARP(dna!1,liIII)  -> DNA16(site~sdsb) + PARP(dna,liIII)` | Transforms DNA16, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 1046 | `Unlabeled` | one-way | DNA17, PARP | `kdPARP1` | state and binding-pattern rewrite | `DNA17(site!1~sdsb).PARP(dna!1,liIII)  -> DNA17(site~sdsb) + PARP(dna,liIII)` | Transforms DNA17, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 1047 | `Unlabeled` | one-way | DNA18, PARP | `kdPARP1` | state and binding-pattern rewrite | `DNA18(site!1~sdsb).PARP(dna!1,liIII)  -> DNA18(site~sdsb) + PARP(dna,liIII)` | Transforms DNA18, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 1048 | `Unlabeled` | one-way | DNA19, PARP | `kdPARP1` | state and binding-pattern rewrite | `DNA19(site!1~sdsb).PARP(dna!1,liIII)  -> DNA19(site~sdsb) + PARP(dna,liIII)` | Transforms DNA19, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 1049 | `Unlabeled` | one-way | DNA20, PARP | `kdPARP1` | state and binding-pattern rewrite | `DNA20(site!1~sdsb).PARP(dna!1,liIII)  -> DNA20(site~sdsb) + PARP(dna,liIII)` | Transforms DNA20, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 1050 | `Unlabeled` | one-way | DNA21, PARP | `kdPARP1` | state and binding-pattern rewrite | `DNA21(site!1~sdsb).PARP(dna!1,liIII)  -> DNA21(site~sdsb) + PARP(dna,liIII)` | Transforms DNA21, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 1051 | `Unlabeled` | one-way | DNA22, PARP | `kdPARP1` | state and binding-pattern rewrite | `DNA22(site!1~sdsb).PARP(dna!1,liIII)  -> DNA22(site~sdsb) + PARP(dna,liIII)` | Transforms DNA22, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 1052 | `Unlabeled` | one-way | DNA23, PARP | `kdPARP1` | state and binding-pattern rewrite | `DNA23(site!1~sdsb).PARP(dna!1,liIII)  -> DNA23(site~sdsb) + PARP(dna,liIII)` | Transforms DNA23, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 1053 | `Unlabeled` | one-way | DNA24, PARP | `kdPARP1` | state and binding-pattern rewrite | `DNA24(site!1~sdsb).PARP(dna!1,liIII)  -> DNA24(site~sdsb) + PARP(dna,liIII)` | Transforms DNA24, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 1054 | `Unlabeled` | one-way | DNA25, PARP | `kdPARP1` | state and binding-pattern rewrite | `DNA25(site!1~sdsb).PARP(dna!1,liIII)  -> DNA25(site~sdsb) + PARP(dna,liIII)` | Transforms DNA25, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 1055 | `Unlabeled` | one-way | DNA26, PARP | `kdPARP1` | state and binding-pattern rewrite | `DNA26(site!1~sdsb).PARP(dna!1,liIII)  -> DNA26(site~sdsb) + PARP(dna,liIII)` | Transforms DNA26, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 1056 | `Unlabeled` | one-way | DNA27, PARP | `kdPARP1` | state and binding-pattern rewrite | `DNA27(site!1~sdsb).PARP(dna!1,liIII)  -> DNA27(site~sdsb) + PARP(dna,liIII)` | Transforms DNA27, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 1057 | `Unlabeled` | one-way | DNA28, PARP | `kdPARP1` | state and binding-pattern rewrite | `DNA28(site!1~sdsb).PARP(dna!1,liIII)  -> DNA28(site~sdsb) + PARP(dna,liIII)` | Transforms DNA28, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 1058 | `Unlabeled` | one-way | DNA29, PARP | `kdPARP1` | state and binding-pattern rewrite | `DNA29(site!1~sdsb).PARP(dna!1,liIII)  -> DNA29(site~sdsb) + PARP(dna,liIII)` | Transforms DNA29, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 1059 | `Unlabeled` | one-way | DNA30, PARP | `kdPARP1` | state and binding-pattern rewrite | `DNA30(site!1~sdsb).PARP(dna!1,liIII)  -> DNA30(site~sdsb) + PARP(dna,liIII)` | Transforms DNA30, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 1060 | `Unlabeled` | one-way | DNA31, PARP | `kdPARP1` | state and binding-pattern rewrite | `DNA31(site!1~sdsb).PARP(dna!1,liIII)  -> DNA31(site~sdsb) + PARP(dna,liIII)` | Transforms DNA31, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 1061 | `Unlabeled` | one-way | DNA32, PARP | `kdPARP1` | state and binding-pattern rewrite | `DNA32(site!1~sdsb).PARP(dna!1,liIII)  -> DNA32(site~sdsb) + PARP(dna,liIII)` | Transforms DNA32, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 1062 | `Unlabeled` | one-way | DNA33, PARP | `kdPARP1` | state and binding-pattern rewrite | `DNA33(site!1~sdsb).PARP(dna!1,liIII)  -> DNA33(site~sdsb) + PARP(dna,liIII)` | Transforms DNA33, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 1063 | `Unlabeled` | one-way | DNA34, PARP | `kdPARP1` | state and binding-pattern rewrite | `DNA34(site!1~sdsb).PARP(dna!1,liIII)  -> DNA34(site~sdsb) + PARP(dna,liIII)` | Transforms DNA34, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 1064 | `Unlabeled` | one-way | DNA35, PARP | `kdPARP1` | state and binding-pattern rewrite | `DNA35(site!1~sdsb).PARP(dna!1,liIII)  -> DNA35(site~sdsb) + PARP(dna,liIII)` | Transforms DNA35, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 1065 | `Unlabeled` | one-way | DNA36, PARP | `kdPARP1` | state and binding-pattern rewrite | `DNA36(site!1~sdsb).PARP(dna!1,liIII)  -> DNA36(site~sdsb) + PARP(dna,liIII)` | Transforms DNA36, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 1066 | `Unlabeled` | one-way | DNA37, PARP | `kdPARP1` | state and binding-pattern rewrite | `DNA37(site!1~sdsb).PARP(dna!1,liIII)  -> DNA37(site~sdsb) + PARP(dna,liIII)` | Transforms DNA37, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 1067 | `Unlabeled` | one-way | DNA38, PARP | `kdPARP1` | state and binding-pattern rewrite | `DNA38(site!1~sdsb).PARP(dna!1,liIII)  -> DNA38(site~sdsb) + PARP(dna,liIII)` | Transforms DNA38, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 1068 | `Unlabeled` | one-way | DNA39, PARP | `kdPARP1` | state and binding-pattern rewrite | `DNA39(site!1~sdsb).PARP(dna!1,liIII)  -> DNA39(site~sdsb) + PARP(dna,liIII)` | Transforms DNA39, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 1069 | `Unlabeled` | one-way | DNA40, PARP | `kdPARP1` | state and binding-pattern rewrite | `DNA40(site!1~sdsb).PARP(dna!1,liIII)  -> DNA40(site~sdsb) + PARP(dna,liIII)` | Transforms DNA40, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 1070 | `Unlabeled` | one-way | DNA41, PARP | `kdPARP1` | state and binding-pattern rewrite | `DNA41(site!1~sdsb).PARP(dna!1,liIII)  -> DNA41(site~sdsb) + PARP(dna,liIII)` | Transforms DNA41, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 1071 | `Unlabeled` | one-way | DNA42, PARP | `kdPARP1` | state and binding-pattern rewrite | `DNA42(site!1~sdsb).PARP(dna!1,liIII)  -> DNA42(site~sdsb) + PARP(dna,liIII)` | Transforms DNA42, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 1072 | `Unlabeled` | one-way | DNA43, PARP | `kdPARP1` | state and binding-pattern rewrite | `DNA43(site!1~sdsb).PARP(dna!1,liIII)  -> DNA43(site~sdsb) + PARP(dna,liIII)` | Transforms DNA43, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 1073 | `Unlabeled` | one-way | DNA44, PARP | `kdPARP1` | state and binding-pattern rewrite | `DNA44(site!1~sdsb).PARP(dna!1,liIII)  -> DNA44(site~sdsb) + PARP(dna,liIII)` | Transforms DNA44, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 1074 | `Unlabeled` | one-way | DNA45, PARP | `kdPARP1` | state and binding-pattern rewrite | `DNA45(site!1~sdsb).PARP(dna!1,liIII)  -> DNA45(site~sdsb) + PARP(dna,liIII)` | Transforms DNA45, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 1075 | `Unlabeled` | one-way | DNA46, PARP | `kdPARP1` | state and binding-pattern rewrite | `DNA46(site!1~sdsb).PARP(dna!1,liIII)  -> DNA46(site~sdsb) + PARP(dna,liIII)` | Transforms DNA46, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 1076 | `Unlabeled` | one-way | DNA47, PARP | `kdPARP1` | state and binding-pattern rewrite | `DNA47(site!1~sdsb).PARP(dna!1,liIII)  -> DNA47(site~sdsb) + PARP(dna,liIII)` | Transforms DNA47, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 1077 | `Unlabeled` | one-way | DNA48, PARP | `kdPARP1` | state and binding-pattern rewrite | `DNA48(site!1~sdsb).PARP(dna!1,liIII)  -> DNA48(site~sdsb) + PARP(dna,liIII)` | Transforms DNA48, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 1078 | `Unlabeled` | one-way | DNA49, PARP | `kdPARP1` | state and binding-pattern rewrite | `DNA49(site!1~sdsb).PARP(dna!1,liIII)  -> DNA49(site~sdsb) + PARP(dna,liIII)` | Transforms DNA49, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 1079 | `Unlabeled` | one-way | DNA50, PARP | `kdPARP1` | state and binding-pattern rewrite | `DNA50(site!1~sdsb).PARP(dna!1,liIII)  -> DNA50(site~sdsb) + PARP(dna,liIII)` | Transforms DNA50, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 1080 | `Unlabeled` | one-way | DNA1, PARP | `kdPARP2` | state and binding-pattern rewrite | `DNA1(site!1~cdsb).PARP(dna!1,liIII)  -> DNA1(site~cdsb) + PARP(dna,liIII)` | Transforms DNA1, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 1081 | `Unlabeled` | one-way | DNA2, PARP | `kdPARP2` | state and binding-pattern rewrite | `DNA2(site!1~cdsb).PARP(dna!1,liIII)  -> DNA2(site~cdsb) + PARP(dna,liIII)` | Transforms DNA2, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 1082 | `Unlabeled` | one-way | DNA3, PARP | `kdPARP2` | state and binding-pattern rewrite | `DNA3(site!1~cdsb).PARP(dna!1,liIII)  -> DNA3(site~cdsb) + PARP(dna,liIII)` | Transforms DNA3, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 1083 | `Unlabeled` | one-way | DNA4, PARP | `kdPARP2` | state and binding-pattern rewrite | `DNA4(site!1~cdsb).PARP(dna!1,liIII)  -> DNA4(site~cdsb) + PARP(dna,liIII)` | Transforms DNA4, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 1084 | `Unlabeled` | one-way | DNA5, PARP | `kdPARP2` | state and binding-pattern rewrite | `DNA5(site!1~cdsb).PARP(dna!1,liIII)  -> DNA5(site~cdsb) + PARP(dna,liIII)` | Transforms DNA5, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 1085 | `Unlabeled` | one-way | DNA6, PARP | `kdPARP2` | state and binding-pattern rewrite | `DNA6(site!1~cdsb).PARP(dna!1,liIII)  -> DNA6(site~cdsb) + PARP(dna,liIII)` | Transforms DNA6, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 1086 | `Unlabeled` | one-way | DNA7, PARP | `kdPARP2` | state and binding-pattern rewrite | `DNA7(site!1~cdsb).PARP(dna!1,liIII)  -> DNA7(site~cdsb) + PARP(dna,liIII)` | Transforms DNA7, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 1087 | `Unlabeled` | one-way | DNA8, PARP | `kdPARP2` | state and binding-pattern rewrite | `DNA8(site!1~cdsb).PARP(dna!1,liIII)  -> DNA8(site~cdsb) + PARP(dna,liIII)` | Transforms DNA8, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 1088 | `Unlabeled` | one-way | DNA9, PARP | `kdPARP2` | state and binding-pattern rewrite | `DNA9(site!1~cdsb).PARP(dna!1,liIII)  -> DNA9(site~cdsb) + PARP(dna,liIII)` | Transforms DNA9, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 1089 | `Unlabeled` | one-way | DNA10, PARP | `kdPARP2` | state and binding-pattern rewrite | `DNA10(site!1~cdsb).PARP(dna!1,liIII)  -> DNA10(site~cdsb) + PARP(dna,liIII)` | Transforms DNA10, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 1090 | `Unlabeled` | one-way | DNA11, PARP | `kdPARP2` | state and binding-pattern rewrite | `DNA11(site!1~cdsb).PARP(dna!1,liIII)  -> DNA11(site~cdsb) + PARP(dna,liIII)` | Transforms DNA11, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 1091 | `Unlabeled` | one-way | DNA12, PARP | `kdPARP2` | state and binding-pattern rewrite | `DNA12(site!1~cdsb).PARP(dna!1,liIII)  -> DNA12(site~cdsb) + PARP(dna,liIII)` | Transforms DNA12, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 1092 | `Unlabeled` | one-way | DNA13, PARP | `kdPARP2` | state and binding-pattern rewrite | `DNA13(site!1~cdsb).PARP(dna!1,liIII)  -> DNA13(site~cdsb) + PARP(dna,liIII)` | Transforms DNA13, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 1093 | `Unlabeled` | one-way | DNA14, PARP | `kdPARP2` | state and binding-pattern rewrite | `DNA14(site!1~cdsb).PARP(dna!1,liIII)  -> DNA14(site~cdsb) + PARP(dna,liIII)` | Transforms DNA14, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 1094 | `Unlabeled` | one-way | DNA15, PARP | `kdPARP2` | state and binding-pattern rewrite | `DNA15(site!1~cdsb).PARP(dna!1,liIII)  -> DNA15(site~cdsb) + PARP(dna,liIII)` | Transforms DNA15, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 1095 | `Unlabeled` | one-way | DNA16, PARP | `kdPARP2` | state and binding-pattern rewrite | `DNA16(site!1~cdsb).PARP(dna!1,liIII)  -> DNA16(site~cdsb) + PARP(dna,liIII)` | Transforms DNA16, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 1096 | `Unlabeled` | one-way | DNA17, PARP | `kdPARP2` | state and binding-pattern rewrite | `DNA17(site!1~cdsb).PARP(dna!1,liIII)  -> DNA17(site~cdsb) + PARP(dna,liIII)` | Transforms DNA17, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 1097 | `Unlabeled` | one-way | DNA18, PARP | `kdPARP2` | state and binding-pattern rewrite | `DNA18(site!1~cdsb).PARP(dna!1,liIII)  -> DNA18(site~cdsb) + PARP(dna,liIII)` | Transforms DNA18, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 1098 | `Unlabeled` | one-way | DNA19, PARP | `kdPARP2` | state and binding-pattern rewrite | `DNA19(site!1~cdsb).PARP(dna!1,liIII)  -> DNA19(site~cdsb) + PARP(dna,liIII)` | Transforms DNA19, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 1099 | `Unlabeled` | one-way | DNA20, PARP | `kdPARP2` | state and binding-pattern rewrite | `DNA20(site!1~cdsb).PARP(dna!1,liIII)  -> DNA20(site~cdsb) + PARP(dna,liIII)` | Transforms DNA20, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 1100 | `Unlabeled` | one-way | DNA21, PARP | `kdPARP2` | state and binding-pattern rewrite | `DNA21(site!1~cdsb).PARP(dna!1,liIII)  -> DNA21(site~cdsb) + PARP(dna,liIII)` | Transforms DNA21, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 1101 | `Unlabeled` | one-way | DNA22, PARP | `kdPARP2` | state and binding-pattern rewrite | `DNA22(site!1~cdsb).PARP(dna!1,liIII)  -> DNA22(site~cdsb) + PARP(dna,liIII)` | Transforms DNA22, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 1102 | `Unlabeled` | one-way | DNA23, PARP | `kdPARP2` | state and binding-pattern rewrite | `DNA23(site!1~cdsb).PARP(dna!1,liIII)  -> DNA23(site~cdsb) + PARP(dna,liIII)` | Transforms DNA23, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 1103 | `Unlabeled` | one-way | DNA24, PARP | `kdPARP2` | state and binding-pattern rewrite | `DNA24(site!1~cdsb).PARP(dna!1,liIII)  -> DNA24(site~cdsb) + PARP(dna,liIII)` | Transforms DNA24, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 1104 | `Unlabeled` | one-way | DNA25, PARP | `kdPARP2` | state and binding-pattern rewrite | `DNA25(site!1~cdsb).PARP(dna!1,liIII)  -> DNA25(site~cdsb) + PARP(dna,liIII)` | Transforms DNA25, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 1105 | `Unlabeled` | one-way | DNA26, PARP | `kdPARP2` | state and binding-pattern rewrite | `DNA26(site!1~cdsb).PARP(dna!1,liIII)  -> DNA26(site~cdsb) + PARP(dna,liIII)` | Transforms DNA26, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 1106 | `Unlabeled` | one-way | DNA27, PARP | `kdPARP2` | state and binding-pattern rewrite | `DNA27(site!1~cdsb).PARP(dna!1,liIII)  -> DNA27(site~cdsb) + PARP(dna,liIII)` | Transforms DNA27, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 1107 | `Unlabeled` | one-way | DNA28, PARP | `kdPARP2` | state and binding-pattern rewrite | `DNA28(site!1~cdsb).PARP(dna!1,liIII)  -> DNA28(site~cdsb) + PARP(dna,liIII)` | Transforms DNA28, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 1108 | `Unlabeled` | one-way | DNA29, PARP | `kdPARP2` | state and binding-pattern rewrite | `DNA29(site!1~cdsb).PARP(dna!1,liIII)  -> DNA29(site~cdsb) + PARP(dna,liIII)` | Transforms DNA29, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 1109 | `Unlabeled` | one-way | DNA30, PARP | `kdPARP2` | state and binding-pattern rewrite | `DNA30(site!1~cdsb).PARP(dna!1,liIII)  -> DNA30(site~cdsb) + PARP(dna,liIII)` | Transforms DNA30, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 1110 | `Unlabeled` | one-way | DNA31, PARP | `kdPARP2` | state and binding-pattern rewrite | `DNA31(site!1~cdsb).PARP(dna!1,liIII)  -> DNA31(site~cdsb) + PARP(dna,liIII)` | Transforms DNA31, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 1111 | `Unlabeled` | one-way | DNA32, PARP | `kdPARP2` | state and binding-pattern rewrite | `DNA32(site!1~cdsb).PARP(dna!1,liIII)  -> DNA32(site~cdsb) + PARP(dna,liIII)` | Transforms DNA32, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 1112 | `Unlabeled` | one-way | DNA33, PARP | `kdPARP2` | state and binding-pattern rewrite | `DNA33(site!1~cdsb).PARP(dna!1,liIII)  -> DNA33(site~cdsb) + PARP(dna,liIII)` | Transforms DNA33, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 1113 | `Unlabeled` | one-way | DNA34, PARP | `kdPARP2` | state and binding-pattern rewrite | `DNA34(site!1~cdsb).PARP(dna!1,liIII)  -> DNA34(site~cdsb) + PARP(dna,liIII)` | Transforms DNA34, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 1114 | `Unlabeled` | one-way | DNA35, PARP | `kdPARP2` | state and binding-pattern rewrite | `DNA35(site!1~cdsb).PARP(dna!1,liIII)  -> DNA35(site~cdsb) + PARP(dna,liIII)` | Transforms DNA35, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 1115 | `Unlabeled` | one-way | DNA36, PARP | `kdPARP2` | state and binding-pattern rewrite | `DNA36(site!1~cdsb).PARP(dna!1,liIII)  -> DNA36(site~cdsb) + PARP(dna,liIII)` | Transforms DNA36, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 1116 | `Unlabeled` | one-way | DNA37, PARP | `kdPARP2` | state and binding-pattern rewrite | `DNA37(site!1~cdsb).PARP(dna!1,liIII)  -> DNA37(site~cdsb) + PARP(dna,liIII)` | Transforms DNA37, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 1117 | `Unlabeled` | one-way | DNA38, PARP | `kdPARP2` | state and binding-pattern rewrite | `DNA38(site!1~cdsb).PARP(dna!1,liIII)  -> DNA38(site~cdsb) + PARP(dna,liIII)` | Transforms DNA38, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 1118 | `Unlabeled` | one-way | DNA39, PARP | `kdPARP2` | state and binding-pattern rewrite | `DNA39(site!1~cdsb).PARP(dna!1,liIII)  -> DNA39(site~cdsb) + PARP(dna,liIII)` | Transforms DNA39, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 1119 | `Unlabeled` | one-way | DNA40, PARP | `kdPARP2` | state and binding-pattern rewrite | `DNA40(site!1~cdsb).PARP(dna!1,liIII)  -> DNA40(site~cdsb) + PARP(dna,liIII)` | Transforms DNA40, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 1120 | `Unlabeled` | one-way | DNA41, PARP | `kdPARP2` | state and binding-pattern rewrite | `DNA41(site!1~cdsb).PARP(dna!1,liIII)  -> DNA41(site~cdsb) + PARP(dna,liIII)` | Transforms DNA41, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 1121 | `Unlabeled` | one-way | DNA42, PARP | `kdPARP2` | state and binding-pattern rewrite | `DNA42(site!1~cdsb).PARP(dna!1,liIII)  -> DNA42(site~cdsb) + PARP(dna,liIII)` | Transforms DNA42, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 1122 | `Unlabeled` | one-way | DNA43, PARP | `kdPARP2` | state and binding-pattern rewrite | `DNA43(site!1~cdsb).PARP(dna!1,liIII)  -> DNA43(site~cdsb) + PARP(dna,liIII)` | Transforms DNA43, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 1123 | `Unlabeled` | one-way | DNA44, PARP | `kdPARP2` | state and binding-pattern rewrite | `DNA44(site!1~cdsb).PARP(dna!1,liIII)  -> DNA44(site~cdsb) + PARP(dna,liIII)` | Transforms DNA44, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 1124 | `Unlabeled` | one-way | DNA45, PARP | `kdPARP2` | state and binding-pattern rewrite | `DNA45(site!1~cdsb).PARP(dna!1,liIII)  -> DNA45(site~cdsb) + PARP(dna,liIII)` | Transforms DNA45, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 1125 | `Unlabeled` | one-way | DNA46, PARP | `kdPARP2` | state and binding-pattern rewrite | `DNA46(site!1~cdsb).PARP(dna!1,liIII)  -> DNA46(site~cdsb) + PARP(dna,liIII)` | Transforms DNA46, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 1126 | `Unlabeled` | one-way | DNA47, PARP | `kdPARP2` | state and binding-pattern rewrite | `DNA47(site!1~cdsb).PARP(dna!1,liIII)  -> DNA47(site~cdsb) + PARP(dna,liIII)` | Transforms DNA47, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 1127 | `Unlabeled` | one-way | DNA48, PARP | `kdPARP2` | state and binding-pattern rewrite | `DNA48(site!1~cdsb).PARP(dna!1,liIII)  -> DNA48(site~cdsb) + PARP(dna,liIII)` | Transforms DNA48, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 1128 | `Unlabeled` | one-way | DNA49, PARP | `kdPARP2` | state and binding-pattern rewrite | `DNA49(site!1~cdsb).PARP(dna!1,liIII)  -> DNA49(site~cdsb) + PARP(dna,liIII)` | Transforms DNA49, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 1129 | `Unlabeled` | one-way | DNA50, PARP | `kdPARP2` | state and binding-pattern rewrite | `DNA50(site!1~cdsb).PARP(dna!1,liIII)  -> DNA50(site~cdsb) + PARP(dna,liIII)` | Transforms DNA50, PARP by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 1130 | `Unlabeled` | one-way | DNA1, LiIII, PARP | `kliIII1` | internal-state conversion/modification | `DNA1(site!1~sdsb).PARP(dna!1,liIII) + LiIII(PARP)  -> DNA1(site!1~sdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)` | Transforms DNA1, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1131 | `Unlabeled` | one-way | DNA2, LiIII, PARP | `kliIII1` | internal-state conversion/modification | `DNA2(site!1~sdsb).PARP(dna!1,liIII) + LiIII(PARP)  -> DNA2(site!1~sdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)` | Transforms DNA2, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1132 | `Unlabeled` | one-way | DNA3, LiIII, PARP | `kliIII1` | internal-state conversion/modification | `DNA3(site!1~sdsb).PARP(dna!1,liIII) + LiIII(PARP)  -> DNA3(site!1~sdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)` | Transforms DNA3, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1133 | `Unlabeled` | one-way | DNA4, LiIII, PARP | `kliIII1` | internal-state conversion/modification | `DNA4(site!1~sdsb).PARP(dna!1,liIII) + LiIII(PARP)  -> DNA4(site!1~sdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)` | Transforms DNA4, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1134 | `Unlabeled` | one-way | DNA5, LiIII, PARP | `kliIII1` | internal-state conversion/modification | `DNA5(site!1~sdsb).PARP(dna!1,liIII) + LiIII(PARP)  -> DNA5(site!1~sdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)` | Transforms DNA5, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1135 | `Unlabeled` | one-way | DNA6, LiIII, PARP | `kliIII1` | internal-state conversion/modification | `DNA6(site!1~sdsb).PARP(dna!1,liIII) + LiIII(PARP)  -> DNA6(site!1~sdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)` | Transforms DNA6, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1136 | `Unlabeled` | one-way | DNA7, LiIII, PARP | `kliIII1` | internal-state conversion/modification | `DNA7(site!1~sdsb).PARP(dna!1,liIII) + LiIII(PARP)  -> DNA7(site!1~sdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)` | Transforms DNA7, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1137 | `Unlabeled` | one-way | DNA8, LiIII, PARP | `kliIII1` | internal-state conversion/modification | `DNA8(site!1~sdsb).PARP(dna!1,liIII) + LiIII(PARP)  -> DNA8(site!1~sdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)` | Transforms DNA8, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1138 | `Unlabeled` | one-way | DNA9, LiIII, PARP | `kliIII1` | internal-state conversion/modification | `DNA9(site!1~sdsb).PARP(dna!1,liIII) + LiIII(PARP)  -> DNA9(site!1~sdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)` | Transforms DNA9, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1139 | `Unlabeled` | one-way | DNA10, LiIII, PARP | `kliIII1` | internal-state conversion/modification | `DNA10(site!1~sdsb).PARP(dna!1,liIII) + LiIII(PARP)  -> DNA10(site!1~sdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)` | Transforms DNA10, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1140 | `Unlabeled` | one-way | DNA11, LiIII, PARP | `kliIII1` | internal-state conversion/modification | `DNA11(site!1~sdsb).PARP(dna!1,liIII) + LiIII(PARP)  -> DNA11(site!1~sdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)` | Transforms DNA11, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1141 | `Unlabeled` | one-way | DNA12, LiIII, PARP | `kliIII1` | internal-state conversion/modification | `DNA12(site!1~sdsb).PARP(dna!1,liIII) + LiIII(PARP)  -> DNA12(site!1~sdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)` | Transforms DNA12, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1142 | `Unlabeled` | one-way | DNA13, LiIII, PARP | `kliIII1` | internal-state conversion/modification | `DNA13(site!1~sdsb).PARP(dna!1,liIII) + LiIII(PARP)  -> DNA13(site!1~sdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)` | Transforms DNA13, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1143 | `Unlabeled` | one-way | DNA14, LiIII, PARP | `kliIII1` | internal-state conversion/modification | `DNA14(site!1~sdsb).PARP(dna!1,liIII) + LiIII(PARP)  -> DNA14(site!1~sdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)` | Transforms DNA14, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1144 | `Unlabeled` | one-way | DNA15, LiIII, PARP | `kliIII1` | internal-state conversion/modification | `DNA15(site!1~sdsb).PARP(dna!1,liIII) + LiIII(PARP)  -> DNA15(site!1~sdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)` | Transforms DNA15, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1145 | `Unlabeled` | one-way | DNA16, LiIII, PARP | `kliIII1` | internal-state conversion/modification | `DNA16(site!1~sdsb).PARP(dna!1,liIII) + LiIII(PARP)  -> DNA16(site!1~sdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)` | Transforms DNA16, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1146 | `Unlabeled` | one-way | DNA17, LiIII, PARP | `kliIII1` | internal-state conversion/modification | `DNA17(site!1~sdsb).PARP(dna!1,liIII) + LiIII(PARP)  -> DNA17(site!1~sdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)` | Transforms DNA17, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1147 | `Unlabeled` | one-way | DNA18, LiIII, PARP | `kliIII1` | internal-state conversion/modification | `DNA18(site!1~sdsb).PARP(dna!1,liIII) + LiIII(PARP)  -> DNA18(site!1~sdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)` | Transforms DNA18, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1148 | `Unlabeled` | one-way | DNA19, LiIII, PARP | `kliIII1` | internal-state conversion/modification | `DNA19(site!1~sdsb).PARP(dna!1,liIII) + LiIII(PARP)  -> DNA19(site!1~sdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)` | Transforms DNA19, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1149 | `Unlabeled` | one-way | DNA20, LiIII, PARP | `kliIII1` | internal-state conversion/modification | `DNA20(site!1~sdsb).PARP(dna!1,liIII) + LiIII(PARP)  -> DNA20(site!1~sdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)` | Transforms DNA20, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1150 | `Unlabeled` | one-way | DNA21, LiIII, PARP | `kliIII1` | internal-state conversion/modification | `DNA21(site!1~sdsb).PARP(dna!1,liIII) + LiIII(PARP)  -> DNA21(site!1~sdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)` | Transforms DNA21, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1151 | `Unlabeled` | one-way | DNA22, LiIII, PARP | `kliIII1` | internal-state conversion/modification | `DNA22(site!1~sdsb).PARP(dna!1,liIII) + LiIII(PARP)  -> DNA22(site!1~sdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)` | Transforms DNA22, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1152 | `Unlabeled` | one-way | DNA23, LiIII, PARP | `kliIII1` | internal-state conversion/modification | `DNA23(site!1~sdsb).PARP(dna!1,liIII) + LiIII(PARP)  -> DNA23(site!1~sdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)` | Transforms DNA23, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1153 | `Unlabeled` | one-way | DNA24, LiIII, PARP | `kliIII1` | internal-state conversion/modification | `DNA24(site!1~sdsb).PARP(dna!1,liIII) + LiIII(PARP)  -> DNA24(site!1~sdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)` | Transforms DNA24, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1154 | `Unlabeled` | one-way | DNA25, LiIII, PARP | `kliIII1` | internal-state conversion/modification | `DNA25(site!1~sdsb).PARP(dna!1,liIII) + LiIII(PARP)  -> DNA25(site!1~sdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)` | Transforms DNA25, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1155 | `Unlabeled` | one-way | DNA26, LiIII, PARP | `kliIII1` | internal-state conversion/modification | `DNA26(site!1~sdsb).PARP(dna!1,liIII) + LiIII(PARP)  -> DNA26(site!1~sdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)` | Transforms DNA26, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1156 | `Unlabeled` | one-way | DNA27, LiIII, PARP | `kliIII1` | internal-state conversion/modification | `DNA27(site!1~sdsb).PARP(dna!1,liIII) + LiIII(PARP)  -> DNA27(site!1~sdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)` | Transforms DNA27, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1157 | `Unlabeled` | one-way | DNA28, LiIII, PARP | `kliIII1` | internal-state conversion/modification | `DNA28(site!1~sdsb).PARP(dna!1,liIII) + LiIII(PARP)  -> DNA28(site!1~sdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)` | Transforms DNA28, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1158 | `Unlabeled` | one-way | DNA29, LiIII, PARP | `kliIII1` | internal-state conversion/modification | `DNA29(site!1~sdsb).PARP(dna!1,liIII) + LiIII(PARP)  -> DNA29(site!1~sdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)` | Transforms DNA29, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1159 | `Unlabeled` | one-way | DNA30, LiIII, PARP | `kliIII1` | internal-state conversion/modification | `DNA30(site!1~sdsb).PARP(dna!1,liIII) + LiIII(PARP)  -> DNA30(site!1~sdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)` | Transforms DNA30, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1160 | `Unlabeled` | one-way | DNA31, LiIII, PARP | `kliIII1` | internal-state conversion/modification | `DNA31(site!1~sdsb).PARP(dna!1,liIII) + LiIII(PARP)  -> DNA31(site!1~sdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)` | Transforms DNA31, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1161 | `Unlabeled` | one-way | DNA32, LiIII, PARP | `kliIII1` | internal-state conversion/modification | `DNA32(site!1~sdsb).PARP(dna!1,liIII) + LiIII(PARP)  -> DNA32(site!1~sdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)` | Transforms DNA32, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1162 | `Unlabeled` | one-way | DNA33, LiIII, PARP | `kliIII1` | internal-state conversion/modification | `DNA33(site!1~sdsb).PARP(dna!1,liIII) + LiIII(PARP)  -> DNA33(site!1~sdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)` | Transforms DNA33, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1163 | `Unlabeled` | one-way | DNA34, LiIII, PARP | `kliIII1` | internal-state conversion/modification | `DNA34(site!1~sdsb).PARP(dna!1,liIII) + LiIII(PARP)  -> DNA34(site!1~sdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)` | Transforms DNA34, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1164 | `Unlabeled` | one-way | DNA35, LiIII, PARP | `kliIII1` | internal-state conversion/modification | `DNA35(site!1~sdsb).PARP(dna!1,liIII) + LiIII(PARP)  -> DNA35(site!1~sdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)` | Transforms DNA35, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1165 | `Unlabeled` | one-way | DNA36, LiIII, PARP | `kliIII1` | internal-state conversion/modification | `DNA36(site!1~sdsb).PARP(dna!1,liIII) + LiIII(PARP)  -> DNA36(site!1~sdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)` | Transforms DNA36, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1166 | `Unlabeled` | one-way | DNA37, LiIII, PARP | `kliIII1` | internal-state conversion/modification | `DNA37(site!1~sdsb).PARP(dna!1,liIII) + LiIII(PARP)  -> DNA37(site!1~sdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)` | Transforms DNA37, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1167 | `Unlabeled` | one-way | DNA38, LiIII, PARP | `kliIII1` | internal-state conversion/modification | `DNA38(site!1~sdsb).PARP(dna!1,liIII) + LiIII(PARP)  -> DNA38(site!1~sdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)` | Transforms DNA38, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1168 | `Unlabeled` | one-way | DNA39, LiIII, PARP | `kliIII1` | internal-state conversion/modification | `DNA39(site!1~sdsb).PARP(dna!1,liIII) + LiIII(PARP)  -> DNA39(site!1~sdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)` | Transforms DNA39, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1169 | `Unlabeled` | one-way | DNA40, LiIII, PARP | `kliIII1` | internal-state conversion/modification | `DNA40(site!1~sdsb).PARP(dna!1,liIII) + LiIII(PARP)  -> DNA40(site!1~sdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)` | Transforms DNA40, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1170 | `Unlabeled` | one-way | DNA41, LiIII, PARP | `kliIII1` | internal-state conversion/modification | `DNA41(site!1~sdsb).PARP(dna!1,liIII) + LiIII(PARP)  -> DNA41(site!1~sdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)` | Transforms DNA41, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1171 | `Unlabeled` | one-way | DNA42, LiIII, PARP | `kliIII1` | internal-state conversion/modification | `DNA42(site!1~sdsb).PARP(dna!1,liIII) + LiIII(PARP)  -> DNA42(site!1~sdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)` | Transforms DNA42, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1172 | `Unlabeled` | one-way | DNA43, LiIII, PARP | `kliIII1` | internal-state conversion/modification | `DNA43(site!1~sdsb).PARP(dna!1,liIII) + LiIII(PARP)  -> DNA43(site!1~sdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)` | Transforms DNA43, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1173 | `Unlabeled` | one-way | DNA44, LiIII, PARP | `kliIII1` | internal-state conversion/modification | `DNA44(site!1~sdsb).PARP(dna!1,liIII) + LiIII(PARP)  -> DNA44(site!1~sdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)` | Transforms DNA44, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1174 | `Unlabeled` | one-way | DNA45, LiIII, PARP | `kliIII1` | internal-state conversion/modification | `DNA45(site!1~sdsb).PARP(dna!1,liIII) + LiIII(PARP)  -> DNA45(site!1~sdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)` | Transforms DNA45, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1175 | `Unlabeled` | one-way | DNA46, LiIII, PARP | `kliIII1` | internal-state conversion/modification | `DNA46(site!1~sdsb).PARP(dna!1,liIII) + LiIII(PARP)  -> DNA46(site!1~sdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)` | Transforms DNA46, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1176 | `Unlabeled` | one-way | DNA47, LiIII, PARP | `kliIII1` | internal-state conversion/modification | `DNA47(site!1~sdsb).PARP(dna!1,liIII) + LiIII(PARP)  -> DNA47(site!1~sdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)` | Transforms DNA47, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1177 | `Unlabeled` | one-way | DNA48, LiIII, PARP | `kliIII1` | internal-state conversion/modification | `DNA48(site!1~sdsb).PARP(dna!1,liIII) + LiIII(PARP)  -> DNA48(site!1~sdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)` | Transforms DNA48, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1178 | `Unlabeled` | one-way | DNA49, LiIII, PARP | `kliIII1` | internal-state conversion/modification | `DNA49(site!1~sdsb).PARP(dna!1,liIII) + LiIII(PARP)  -> DNA49(site!1~sdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)` | Transforms DNA49, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1179 | `Unlabeled` | one-way | DNA50, LiIII, PARP | `kliIII1` | internal-state conversion/modification | `DNA50(site!1~sdsb).PARP(dna!1,liIII) + LiIII(PARP)  -> DNA50(site!1~sdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)` | Transforms DNA50, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1180 | `Unlabeled` | one-way | DNA1, LiIII, PARP | `kliIII2` | internal-state conversion/modification | `DNA1(site!1~cdsb).PARP(dna!1,liIII) + LiIII(PARP)  -> DNA1(site!1~cdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)` | Transforms DNA1, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1181 | `Unlabeled` | one-way | DNA2, LiIII, PARP | `kliIII2` | internal-state conversion/modification | `DNA2(site!1~cdsb).PARP(dna!1,liIII) + LiIII(PARP)  -> DNA2(site!1~cdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)` | Transforms DNA2, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1182 | `Unlabeled` | one-way | DNA3, LiIII, PARP | `kliIII2` | internal-state conversion/modification | `DNA3(site!1~cdsb).PARP(dna!1,liIII) + LiIII(PARP)  -> DNA3(site!1~cdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)` | Transforms DNA3, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1183 | `Unlabeled` | one-way | DNA4, LiIII, PARP | `kliIII2` | internal-state conversion/modification | `DNA4(site!1~cdsb).PARP(dna!1,liIII) + LiIII(PARP)  -> DNA4(site!1~cdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)` | Transforms DNA4, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1184 | `Unlabeled` | one-way | DNA5, LiIII, PARP | `kliIII2` | internal-state conversion/modification | `DNA5(site!1~cdsb).PARP(dna!1,liIII) + LiIII(PARP)  -> DNA5(site!1~cdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)` | Transforms DNA5, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1185 | `Unlabeled` | one-way | DNA6, LiIII, PARP | `kliIII2` | internal-state conversion/modification | `DNA6(site!1~cdsb).PARP(dna!1,liIII) + LiIII(PARP)  -> DNA6(site!1~cdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)` | Transforms DNA6, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1186 | `Unlabeled` | one-way | DNA7, LiIII, PARP | `kliIII2` | internal-state conversion/modification | `DNA7(site!1~cdsb).PARP(dna!1,liIII) + LiIII(PARP)  -> DNA7(site!1~cdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)` | Transforms DNA7, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1187 | `Unlabeled` | one-way | DNA8, LiIII, PARP | `kliIII2` | internal-state conversion/modification | `DNA8(site!1~cdsb).PARP(dna!1,liIII) + LiIII(PARP)  -> DNA8(site!1~cdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)` | Transforms DNA8, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1188 | `Unlabeled` | one-way | DNA9, LiIII, PARP | `kliIII2` | internal-state conversion/modification | `DNA9(site!1~cdsb).PARP(dna!1,liIII) + LiIII(PARP)  -> DNA9(site!1~cdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)` | Transforms DNA9, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1189 | `Unlabeled` | one-way | DNA10, LiIII, PARP | `kliIII2` | internal-state conversion/modification | `DNA10(site!1~cdsb).PARP(dna!1,liIII) + LiIII(PARP)  -> DNA10(site!1~cdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)` | Transforms DNA10, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1190 | `Unlabeled` | one-way | DNA11, LiIII, PARP | `kliIII2` | internal-state conversion/modification | `DNA11(site!1~cdsb).PARP(dna!1,liIII) + LiIII(PARP)  -> DNA11(site!1~cdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)` | Transforms DNA11, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1191 | `Unlabeled` | one-way | DNA12, LiIII, PARP | `kliIII2` | internal-state conversion/modification | `DNA12(site!1~cdsb).PARP(dna!1,liIII) + LiIII(PARP)  -> DNA12(site!1~cdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)` | Transforms DNA12, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1192 | `Unlabeled` | one-way | DNA13, LiIII, PARP | `kliIII2` | internal-state conversion/modification | `DNA13(site!1~cdsb).PARP(dna!1,liIII) + LiIII(PARP)  -> DNA13(site!1~cdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)` | Transforms DNA13, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1193 | `Unlabeled` | one-way | DNA14, LiIII, PARP | `kliIII2` | internal-state conversion/modification | `DNA14(site!1~cdsb).PARP(dna!1,liIII) + LiIII(PARP)  -> DNA14(site!1~cdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)` | Transforms DNA14, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1194 | `Unlabeled` | one-way | DNA15, LiIII, PARP | `kliIII2` | internal-state conversion/modification | `DNA15(site!1~cdsb).PARP(dna!1,liIII) + LiIII(PARP)  -> DNA15(site!1~cdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)` | Transforms DNA15, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1195 | `Unlabeled` | one-way | DNA16, LiIII, PARP | `kliIII2` | internal-state conversion/modification | `DNA16(site!1~cdsb).PARP(dna!1,liIII) + LiIII(PARP)  -> DNA16(site!1~cdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)` | Transforms DNA16, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1196 | `Unlabeled` | one-way | DNA17, LiIII, PARP | `kliIII2` | internal-state conversion/modification | `DNA17(site!1~cdsb).PARP(dna!1,liIII) + LiIII(PARP)  -> DNA17(site!1~cdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)` | Transforms DNA17, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1197 | `Unlabeled` | one-way | DNA18, LiIII, PARP | `kliIII2` | internal-state conversion/modification | `DNA18(site!1~cdsb).PARP(dna!1,liIII) + LiIII(PARP)  -> DNA18(site!1~cdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)` | Transforms DNA18, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1198 | `Unlabeled` | one-way | DNA19, LiIII, PARP | `kliIII2` | internal-state conversion/modification | `DNA19(site!1~cdsb).PARP(dna!1,liIII) + LiIII(PARP)  -> DNA19(site!1~cdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)` | Transforms DNA19, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1199 | `Unlabeled` | one-way | DNA20, LiIII, PARP | `kliIII2` | internal-state conversion/modification | `DNA20(site!1~cdsb).PARP(dna!1,liIII) + LiIII(PARP)  -> DNA20(site!1~cdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)` | Transforms DNA20, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1200 | `Unlabeled` | one-way | DNA21, LiIII, PARP | `kliIII2` | internal-state conversion/modification | `DNA21(site!1~cdsb).PARP(dna!1,liIII) + LiIII(PARP)  -> DNA21(site!1~cdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)` | Transforms DNA21, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1201 | `Unlabeled` | one-way | DNA22, LiIII, PARP | `kliIII2` | internal-state conversion/modification | `DNA22(site!1~cdsb).PARP(dna!1,liIII) + LiIII(PARP)  -> DNA22(site!1~cdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)` | Transforms DNA22, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1202 | `Unlabeled` | one-way | DNA23, LiIII, PARP | `kliIII2` | internal-state conversion/modification | `DNA23(site!1~cdsb).PARP(dna!1,liIII) + LiIII(PARP)  -> DNA23(site!1~cdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)` | Transforms DNA23, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1203 | `Unlabeled` | one-way | DNA24, LiIII, PARP | `kliIII2` | internal-state conversion/modification | `DNA24(site!1~cdsb).PARP(dna!1,liIII) + LiIII(PARP)  -> DNA24(site!1~cdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)` | Transforms DNA24, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1204 | `Unlabeled` | one-way | DNA25, LiIII, PARP | `kliIII2` | internal-state conversion/modification | `DNA25(site!1~cdsb).PARP(dna!1,liIII) + LiIII(PARP)  -> DNA25(site!1~cdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)` | Transforms DNA25, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1205 | `Unlabeled` | one-way | DNA26, LiIII, PARP | `kliIII2` | internal-state conversion/modification | `DNA26(site!1~cdsb).PARP(dna!1,liIII) + LiIII(PARP)  -> DNA26(site!1~cdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)` | Transforms DNA26, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1206 | `Unlabeled` | one-way | DNA27, LiIII, PARP | `kliIII2` | internal-state conversion/modification | `DNA27(site!1~cdsb).PARP(dna!1,liIII) + LiIII(PARP)  -> DNA27(site!1~cdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)` | Transforms DNA27, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1207 | `Unlabeled` | one-way | DNA28, LiIII, PARP | `kliIII2` | internal-state conversion/modification | `DNA28(site!1~cdsb).PARP(dna!1,liIII) + LiIII(PARP)  -> DNA28(site!1~cdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)` | Transforms DNA28, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1208 | `Unlabeled` | one-way | DNA29, LiIII, PARP | `kliIII2` | internal-state conversion/modification | `DNA29(site!1~cdsb).PARP(dna!1,liIII) + LiIII(PARP)  -> DNA29(site!1~cdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)` | Transforms DNA29, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1209 | `Unlabeled` | one-way | DNA30, LiIII, PARP | `kliIII2` | internal-state conversion/modification | `DNA30(site!1~cdsb).PARP(dna!1,liIII) + LiIII(PARP)  -> DNA30(site!1~cdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)` | Transforms DNA30, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1210 | `Unlabeled` | one-way | DNA31, LiIII, PARP | `kliIII2` | internal-state conversion/modification | `DNA31(site!1~cdsb).PARP(dna!1,liIII) + LiIII(PARP)  -> DNA31(site!1~cdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)` | Transforms DNA31, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1211 | `Unlabeled` | one-way | DNA32, LiIII, PARP | `kliIII2` | internal-state conversion/modification | `DNA32(site!1~cdsb).PARP(dna!1,liIII) + LiIII(PARP)  -> DNA32(site!1~cdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)` | Transforms DNA32, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1212 | `Unlabeled` | one-way | DNA33, LiIII, PARP | `kliIII2` | internal-state conversion/modification | `DNA33(site!1~cdsb).PARP(dna!1,liIII) + LiIII(PARP)  -> DNA33(site!1~cdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)` | Transforms DNA33, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1213 | `Unlabeled` | one-way | DNA34, LiIII, PARP | `kliIII2` | internal-state conversion/modification | `DNA34(site!1~cdsb).PARP(dna!1,liIII) + LiIII(PARP)  -> DNA34(site!1~cdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)` | Transforms DNA34, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1214 | `Unlabeled` | one-way | DNA35, LiIII, PARP | `kliIII2` | internal-state conversion/modification | `DNA35(site!1~cdsb).PARP(dna!1,liIII) + LiIII(PARP)  -> DNA35(site!1~cdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)` | Transforms DNA35, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1215 | `Unlabeled` | one-way | DNA36, LiIII, PARP | `kliIII2` | internal-state conversion/modification | `DNA36(site!1~cdsb).PARP(dna!1,liIII) + LiIII(PARP)  -> DNA36(site!1~cdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)` | Transforms DNA36, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1216 | `Unlabeled` | one-way | DNA37, LiIII, PARP | `kliIII2` | internal-state conversion/modification | `DNA37(site!1~cdsb).PARP(dna!1,liIII) + LiIII(PARP)  -> DNA37(site!1~cdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)` | Transforms DNA37, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1217 | `Unlabeled` | one-way | DNA38, LiIII, PARP | `kliIII2` | internal-state conversion/modification | `DNA38(site!1~cdsb).PARP(dna!1,liIII) + LiIII(PARP)  -> DNA38(site!1~cdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)` | Transforms DNA38, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1218 | `Unlabeled` | one-way | DNA39, LiIII, PARP | `kliIII2` | internal-state conversion/modification | `DNA39(site!1~cdsb).PARP(dna!1,liIII) + LiIII(PARP)  -> DNA39(site!1~cdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)` | Transforms DNA39, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1219 | `Unlabeled` | one-way | DNA40, LiIII, PARP | `kliIII2` | internal-state conversion/modification | `DNA40(site!1~cdsb).PARP(dna!1,liIII) + LiIII(PARP)  -> DNA40(site!1~cdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)` | Transforms DNA40, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1220 | `Unlabeled` | one-way | DNA41, LiIII, PARP | `kliIII2` | internal-state conversion/modification | `DNA41(site!1~cdsb).PARP(dna!1,liIII) + LiIII(PARP)  -> DNA41(site!1~cdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)` | Transforms DNA41, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1221 | `Unlabeled` | one-way | DNA42, LiIII, PARP | `kliIII2` | internal-state conversion/modification | `DNA42(site!1~cdsb).PARP(dna!1,liIII) + LiIII(PARP)  -> DNA42(site!1~cdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)` | Transforms DNA42, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1222 | `Unlabeled` | one-way | DNA43, LiIII, PARP | `kliIII2` | internal-state conversion/modification | `DNA43(site!1~cdsb).PARP(dna!1,liIII) + LiIII(PARP)  -> DNA43(site!1~cdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)` | Transforms DNA43, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1223 | `Unlabeled` | one-way | DNA44, LiIII, PARP | `kliIII2` | internal-state conversion/modification | `DNA44(site!1~cdsb).PARP(dna!1,liIII) + LiIII(PARP)  -> DNA44(site!1~cdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)` | Transforms DNA44, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1224 | `Unlabeled` | one-way | DNA45, LiIII, PARP | `kliIII2` | internal-state conversion/modification | `DNA45(site!1~cdsb).PARP(dna!1,liIII) + LiIII(PARP)  -> DNA45(site!1~cdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)` | Transforms DNA45, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1225 | `Unlabeled` | one-way | DNA46, LiIII, PARP | `kliIII2` | internal-state conversion/modification | `DNA46(site!1~cdsb).PARP(dna!1,liIII) + LiIII(PARP)  -> DNA46(site!1~cdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)` | Transforms DNA46, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1226 | `Unlabeled` | one-way | DNA47, LiIII, PARP | `kliIII2` | internal-state conversion/modification | `DNA47(site!1~cdsb).PARP(dna!1,liIII) + LiIII(PARP)  -> DNA47(site!1~cdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)` | Transforms DNA47, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1227 | `Unlabeled` | one-way | DNA48, LiIII, PARP | `kliIII2` | internal-state conversion/modification | `DNA48(site!1~cdsb).PARP(dna!1,liIII) + LiIII(PARP)  -> DNA48(site!1~cdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)` | Transforms DNA48, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1228 | `Unlabeled` | one-way | DNA49, LiIII, PARP | `kliIII2` | internal-state conversion/modification | `DNA49(site!1~cdsb).PARP(dna!1,liIII) + LiIII(PARP)  -> DNA49(site!1~cdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)` | Transforms DNA49, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1229 | `Unlabeled` | one-way | DNA50, LiIII, PARP | `kliIII2` | internal-state conversion/modification | `DNA50(site!1~cdsb).PARP(dna!1,liIII) + LiIII(PARP)  -> DNA50(site!1~cdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)` | Transforms DNA50, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1230 | `Unlabeled` | one-way | DNA1, LiIII, PARP | `kdliIII1` | internal-state conversion/modification | `DNA1(site!1~sdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)  -> DNA1(site!1~sdsb).PARP(dna!1,liIII) + LiIII(PARP)` | Transforms DNA1, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1231 | `Unlabeled` | one-way | DNA2, LiIII, PARP | `kdliIII1` | internal-state conversion/modification | `DNA2(site!1~sdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)  -> DNA2(site!1~sdsb).PARP(dna!1,liIII) + LiIII(PARP)` | Transforms DNA2, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1232 | `Unlabeled` | one-way | DNA3, LiIII, PARP | `kdliIII1` | internal-state conversion/modification | `DNA3(site!1~sdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)  -> DNA3(site!1~sdsb).PARP(dna!1,liIII) + LiIII(PARP)` | Transforms DNA3, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1233 | `Unlabeled` | one-way | DNA4, LiIII, PARP | `kdliIII1` | internal-state conversion/modification | `DNA4(site!1~sdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)  -> DNA4(site!1~sdsb).PARP(dna!1,liIII) + LiIII(PARP)` | Transforms DNA4, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1234 | `Unlabeled` | one-way | DNA5, LiIII, PARP | `kdliIII1` | internal-state conversion/modification | `DNA5(site!1~sdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)  -> DNA5(site!1~sdsb).PARP(dna!1,liIII) + LiIII(PARP)` | Transforms DNA5, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1235 | `Unlabeled` | one-way | DNA6, LiIII, PARP | `kdliIII1` | internal-state conversion/modification | `DNA6(site!1~sdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)  -> DNA6(site!1~sdsb).PARP(dna!1,liIII) + LiIII(PARP)` | Transforms DNA6, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1236 | `Unlabeled` | one-way | DNA7, LiIII, PARP | `kdliIII1` | internal-state conversion/modification | `DNA7(site!1~sdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)  -> DNA7(site!1~sdsb).PARP(dna!1,liIII) + LiIII(PARP)` | Transforms DNA7, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1237 | `Unlabeled` | one-way | DNA8, LiIII, PARP | `kdliIII1` | internal-state conversion/modification | `DNA8(site!1~sdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)  -> DNA8(site!1~sdsb).PARP(dna!1,liIII) + LiIII(PARP)` | Transforms DNA8, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1238 | `Unlabeled` | one-way | DNA9, LiIII, PARP | `kdliIII1` | internal-state conversion/modification | `DNA9(site!1~sdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)  -> DNA9(site!1~sdsb).PARP(dna!1,liIII) + LiIII(PARP)` | Transforms DNA9, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1239 | `Unlabeled` | one-way | DNA10, LiIII, PARP | `kdliIII1` | internal-state conversion/modification | `DNA10(site!1~sdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)  -> DNA10(site!1~sdsb).PARP(dna!1,liIII) + LiIII(PARP)` | Transforms DNA10, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1240 | `Unlabeled` | one-way | DNA11, LiIII, PARP | `kdliIII1` | internal-state conversion/modification | `DNA11(site!1~sdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)  -> DNA11(site!1~sdsb).PARP(dna!1,liIII) + LiIII(PARP)` | Transforms DNA11, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1241 | `Unlabeled` | one-way | DNA12, LiIII, PARP | `kdliIII1` | internal-state conversion/modification | `DNA12(site!1~sdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)  -> DNA12(site!1~sdsb).PARP(dna!1,liIII) + LiIII(PARP)` | Transforms DNA12, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1242 | `Unlabeled` | one-way | DNA13, LiIII, PARP | `kdliIII1` | internal-state conversion/modification | `DNA13(site!1~sdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)  -> DNA13(site!1~sdsb).PARP(dna!1,liIII) + LiIII(PARP)` | Transforms DNA13, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1243 | `Unlabeled` | one-way | DNA14, LiIII, PARP | `kdliIII1` | internal-state conversion/modification | `DNA14(site!1~sdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)  -> DNA14(site!1~sdsb).PARP(dna!1,liIII) + LiIII(PARP)` | Transforms DNA14, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1244 | `Unlabeled` | one-way | DNA15, LiIII, PARP | `kdliIII1` | internal-state conversion/modification | `DNA15(site!1~sdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)  -> DNA15(site!1~sdsb).PARP(dna!1,liIII) + LiIII(PARP)` | Transforms DNA15, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1245 | `Unlabeled` | one-way | DNA16, LiIII, PARP | `kdliIII1` | internal-state conversion/modification | `DNA16(site!1~sdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)  -> DNA16(site!1~sdsb).PARP(dna!1,liIII) + LiIII(PARP)` | Transforms DNA16, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1246 | `Unlabeled` | one-way | DNA17, LiIII, PARP | `kdliIII1` | internal-state conversion/modification | `DNA17(site!1~sdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)  -> DNA17(site!1~sdsb).PARP(dna!1,liIII) + LiIII(PARP)` | Transforms DNA17, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1247 | `Unlabeled` | one-way | DNA18, LiIII, PARP | `kdliIII1` | internal-state conversion/modification | `DNA18(site!1~sdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)  -> DNA18(site!1~sdsb).PARP(dna!1,liIII) + LiIII(PARP)` | Transforms DNA18, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1248 | `Unlabeled` | one-way | DNA19, LiIII, PARP | `kdliIII1` | internal-state conversion/modification | `DNA19(site!1~sdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)  -> DNA19(site!1~sdsb).PARP(dna!1,liIII) + LiIII(PARP)` | Transforms DNA19, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1249 | `Unlabeled` | one-way | DNA20, LiIII, PARP | `kdliIII1` | internal-state conversion/modification | `DNA20(site!1~sdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)  -> DNA20(site!1~sdsb).PARP(dna!1,liIII) + LiIII(PARP)` | Transforms DNA20, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1250 | `Unlabeled` | one-way | DNA21, LiIII, PARP | `kdliIII1` | internal-state conversion/modification | `DNA21(site!1~sdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)  -> DNA21(site!1~sdsb).PARP(dna!1,liIII) + LiIII(PARP)` | Transforms DNA21, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

### Rules 1251-1500

| # | Rule label/name | Direction | Participants | Rate/expression | Modeled change | Rule pattern | Technical meaning |
| ---: | --- | --- | --- | --- | --- | --- | --- |

| 1251 | `Unlabeled` | one-way | DNA22, LiIII, PARP | `kdliIII1` | internal-state conversion/modification | `DNA22(site!1~sdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)  -> DNA22(site!1~sdsb).PARP(dna!1,liIII) + LiIII(PARP)` | Transforms DNA22, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1252 | `Unlabeled` | one-way | DNA23, LiIII, PARP | `kdliIII1` | internal-state conversion/modification | `DNA23(site!1~sdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)  -> DNA23(site!1~sdsb).PARP(dna!1,liIII) + LiIII(PARP)` | Transforms DNA23, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1253 | `Unlabeled` | one-way | DNA24, LiIII, PARP | `kdliIII1` | internal-state conversion/modification | `DNA24(site!1~sdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)  -> DNA24(site!1~sdsb).PARP(dna!1,liIII) + LiIII(PARP)` | Transforms DNA24, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1254 | `Unlabeled` | one-way | DNA25, LiIII, PARP | `kdliIII1` | internal-state conversion/modification | `DNA25(site!1~sdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)  -> DNA25(site!1~sdsb).PARP(dna!1,liIII) + LiIII(PARP)` | Transforms DNA25, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1255 | `Unlabeled` | one-way | DNA26, LiIII, PARP | `kdliIII1` | internal-state conversion/modification | `DNA26(site!1~sdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)  -> DNA26(site!1~sdsb).PARP(dna!1,liIII) + LiIII(PARP)` | Transforms DNA26, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1256 | `Unlabeled` | one-way | DNA27, LiIII, PARP | `kdliIII1` | internal-state conversion/modification | `DNA27(site!1~sdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)  -> DNA27(site!1~sdsb).PARP(dna!1,liIII) + LiIII(PARP)` | Transforms DNA27, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1257 | `Unlabeled` | one-way | DNA28, LiIII, PARP | `kdliIII1` | internal-state conversion/modification | `DNA28(site!1~sdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)  -> DNA28(site!1~sdsb).PARP(dna!1,liIII) + LiIII(PARP)` | Transforms DNA28, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1258 | `Unlabeled` | one-way | DNA29, LiIII, PARP | `kdliIII1` | internal-state conversion/modification | `DNA29(site!1~sdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)  -> DNA29(site!1~sdsb).PARP(dna!1,liIII) + LiIII(PARP)` | Transforms DNA29, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1259 | `Unlabeled` | one-way | DNA30, LiIII, PARP | `kdliIII1` | internal-state conversion/modification | `DNA30(site!1~sdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)  -> DNA30(site!1~sdsb).PARP(dna!1,liIII) + LiIII(PARP)` | Transforms DNA30, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1260 | `Unlabeled` | one-way | DNA31, LiIII, PARP | `kdliIII1` | internal-state conversion/modification | `DNA31(site!1~sdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)  -> DNA31(site!1~sdsb).PARP(dna!1,liIII) + LiIII(PARP)` | Transforms DNA31, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1261 | `Unlabeled` | one-way | DNA32, LiIII, PARP | `kdliIII1` | internal-state conversion/modification | `DNA32(site!1~sdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)  -> DNA32(site!1~sdsb).PARP(dna!1,liIII) + LiIII(PARP)` | Transforms DNA32, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1262 | `Unlabeled` | one-way | DNA33, LiIII, PARP | `kdliIII1` | internal-state conversion/modification | `DNA33(site!1~sdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)  -> DNA33(site!1~sdsb).PARP(dna!1,liIII) + LiIII(PARP)` | Transforms DNA33, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1263 | `Unlabeled` | one-way | DNA34, LiIII, PARP | `kdliIII1` | internal-state conversion/modification | `DNA34(site!1~sdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)  -> DNA34(site!1~sdsb).PARP(dna!1,liIII) + LiIII(PARP)` | Transforms DNA34, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1264 | `Unlabeled` | one-way | DNA35, LiIII, PARP | `kdliIII1` | internal-state conversion/modification | `DNA35(site!1~sdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)  -> DNA35(site!1~sdsb).PARP(dna!1,liIII) + LiIII(PARP)` | Transforms DNA35, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1265 | `Unlabeled` | one-way | DNA36, LiIII, PARP | `kdliIII1` | internal-state conversion/modification | `DNA36(site!1~sdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)  -> DNA36(site!1~sdsb).PARP(dna!1,liIII) + LiIII(PARP)` | Transforms DNA36, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1266 | `Unlabeled` | one-way | DNA37, LiIII, PARP | `kdliIII1` | internal-state conversion/modification | `DNA37(site!1~sdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)  -> DNA37(site!1~sdsb).PARP(dna!1,liIII) + LiIII(PARP)` | Transforms DNA37, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1267 | `Unlabeled` | one-way | DNA38, LiIII, PARP | `kdliIII1` | internal-state conversion/modification | `DNA38(site!1~sdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)  -> DNA38(site!1~sdsb).PARP(dna!1,liIII) + LiIII(PARP)` | Transforms DNA38, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1268 | `Unlabeled` | one-way | DNA39, LiIII, PARP | `kdliIII1` | internal-state conversion/modification | `DNA39(site!1~sdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)  -> DNA39(site!1~sdsb).PARP(dna!1,liIII) + LiIII(PARP)` | Transforms DNA39, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1269 | `Unlabeled` | one-way | DNA40, LiIII, PARP | `kdliIII1` | internal-state conversion/modification | `DNA40(site!1~sdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)  -> DNA40(site!1~sdsb).PARP(dna!1,liIII) + LiIII(PARP)` | Transforms DNA40, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1270 | `Unlabeled` | one-way | DNA41, LiIII, PARP | `kdliIII1` | internal-state conversion/modification | `DNA41(site!1~sdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)  -> DNA41(site!1~sdsb).PARP(dna!1,liIII) + LiIII(PARP)` | Transforms DNA41, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1271 | `Unlabeled` | one-way | DNA42, LiIII, PARP | `kdliIII1` | internal-state conversion/modification | `DNA42(site!1~sdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)  -> DNA42(site!1~sdsb).PARP(dna!1,liIII) + LiIII(PARP)` | Transforms DNA42, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1272 | `Unlabeled` | one-way | DNA43, LiIII, PARP | `kdliIII1` | internal-state conversion/modification | `DNA43(site!1~sdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)  -> DNA43(site!1~sdsb).PARP(dna!1,liIII) + LiIII(PARP)` | Transforms DNA43, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1273 | `Unlabeled` | one-way | DNA44, LiIII, PARP | `kdliIII1` | internal-state conversion/modification | `DNA44(site!1~sdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)  -> DNA44(site!1~sdsb).PARP(dna!1,liIII) + LiIII(PARP)` | Transforms DNA44, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1274 | `Unlabeled` | one-way | DNA45, LiIII, PARP | `kdliIII1` | internal-state conversion/modification | `DNA45(site!1~sdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)  -> DNA45(site!1~sdsb).PARP(dna!1,liIII) + LiIII(PARP)` | Transforms DNA45, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1275 | `Unlabeled` | one-way | DNA46, LiIII, PARP | `kdliIII1` | internal-state conversion/modification | `DNA46(site!1~sdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)  -> DNA46(site!1~sdsb).PARP(dna!1,liIII) + LiIII(PARP)` | Transforms DNA46, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1276 | `Unlabeled` | one-way | DNA47, LiIII, PARP | `kdliIII1` | internal-state conversion/modification | `DNA47(site!1~sdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)  -> DNA47(site!1~sdsb).PARP(dna!1,liIII) + LiIII(PARP)` | Transforms DNA47, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1277 | `Unlabeled` | one-way | DNA48, LiIII, PARP | `kdliIII1` | internal-state conversion/modification | `DNA48(site!1~sdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)  -> DNA48(site!1~sdsb).PARP(dna!1,liIII) + LiIII(PARP)` | Transforms DNA48, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1278 | `Unlabeled` | one-way | DNA49, LiIII, PARP | `kdliIII1` | internal-state conversion/modification | `DNA49(site!1~sdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)  -> DNA49(site!1~sdsb).PARP(dna!1,liIII) + LiIII(PARP)` | Transforms DNA49, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1279 | `Unlabeled` | one-way | DNA50, LiIII, PARP | `kdliIII1` | internal-state conversion/modification | `DNA50(site!1~sdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)  -> DNA50(site!1~sdsb).PARP(dna!1,liIII) + LiIII(PARP)` | Transforms DNA50, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1280 | `Unlabeled` | one-way | DNA1, LiIII, PARP | `kdliIII2` | internal-state conversion/modification | `DNA1(site!1~cdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)  -> DNA1(site!1~cdsb).PARP(dna!1,liIII) + LiIII(PARP)` | Transforms DNA1, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1281 | `Unlabeled` | one-way | DNA2, LiIII, PARP | `kdliIII2` | internal-state conversion/modification | `DNA2(site!1~cdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)  -> DNA2(site!1~cdsb).PARP(dna!1,liIII) + LiIII(PARP)` | Transforms DNA2, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1282 | `Unlabeled` | one-way | DNA3, LiIII, PARP | `kdliIII2` | internal-state conversion/modification | `DNA3(site!1~cdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)  -> DNA3(site!1~cdsb).PARP(dna!1,liIII) + LiIII(PARP)` | Transforms DNA3, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1283 | `Unlabeled` | one-way | DNA4, LiIII, PARP | `kdliIII2` | internal-state conversion/modification | `DNA4(site!1~cdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)  -> DNA4(site!1~cdsb).PARP(dna!1,liIII) + LiIII(PARP)` | Transforms DNA4, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1284 | `Unlabeled` | one-way | DNA5, LiIII, PARP | `kdliIII2` | internal-state conversion/modification | `DNA5(site!1~cdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)  -> DNA5(site!1~cdsb).PARP(dna!1,liIII) + LiIII(PARP)` | Transforms DNA5, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1285 | `Unlabeled` | one-way | DNA6, LiIII, PARP | `kdliIII2` | internal-state conversion/modification | `DNA6(site!1~cdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)  -> DNA6(site!1~cdsb).PARP(dna!1,liIII) + LiIII(PARP)` | Transforms DNA6, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1286 | `Unlabeled` | one-way | DNA7, LiIII, PARP | `kdliIII2` | internal-state conversion/modification | `DNA7(site!1~cdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)  -> DNA7(site!1~cdsb).PARP(dna!1,liIII) + LiIII(PARP)` | Transforms DNA7, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1287 | `Unlabeled` | one-way | DNA8, LiIII, PARP | `kdliIII2` | internal-state conversion/modification | `DNA8(site!1~cdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)  -> DNA8(site!1~cdsb).PARP(dna!1,liIII) + LiIII(PARP)` | Transforms DNA8, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1288 | `Unlabeled` | one-way | DNA9, LiIII, PARP | `kdliIII2` | internal-state conversion/modification | `DNA9(site!1~cdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)  -> DNA9(site!1~cdsb).PARP(dna!1,liIII) + LiIII(PARP)` | Transforms DNA9, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1289 | `Unlabeled` | one-way | DNA10, LiIII, PARP | `kdliIII2` | internal-state conversion/modification | `DNA10(site!1~cdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)  -> DNA10(site!1~cdsb).PARP(dna!1,liIII) + LiIII(PARP)` | Transforms DNA10, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1290 | `Unlabeled` | one-way | DNA11, LiIII, PARP | `kdliIII2` | internal-state conversion/modification | `DNA11(site!1~cdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)  -> DNA11(site!1~cdsb).PARP(dna!1,liIII) + LiIII(PARP)` | Transforms DNA11, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1291 | `Unlabeled` | one-way | DNA12, LiIII, PARP | `kdliIII2` | internal-state conversion/modification | `DNA12(site!1~cdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)  -> DNA12(site!1~cdsb).PARP(dna!1,liIII) + LiIII(PARP)` | Transforms DNA12, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1292 | `Unlabeled` | one-way | DNA13, LiIII, PARP | `kdliIII2` | internal-state conversion/modification | `DNA13(site!1~cdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)  -> DNA13(site!1~cdsb).PARP(dna!1,liIII) + LiIII(PARP)` | Transforms DNA13, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1293 | `Unlabeled` | one-way | DNA14, LiIII, PARP | `kdliIII2` | internal-state conversion/modification | `DNA14(site!1~cdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)  -> DNA14(site!1~cdsb).PARP(dna!1,liIII) + LiIII(PARP)` | Transforms DNA14, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1294 | `Unlabeled` | one-way | DNA15, LiIII, PARP | `kdliIII2` | internal-state conversion/modification | `DNA15(site!1~cdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)  -> DNA15(site!1~cdsb).PARP(dna!1,liIII) + LiIII(PARP)` | Transforms DNA15, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1295 | `Unlabeled` | one-way | DNA16, LiIII, PARP | `kdliIII2` | internal-state conversion/modification | `DNA16(site!1~cdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)  -> DNA16(site!1~cdsb).PARP(dna!1,liIII) + LiIII(PARP)` | Transforms DNA16, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1296 | `Unlabeled` | one-way | DNA17, LiIII, PARP | `kdliIII2` | internal-state conversion/modification | `DNA17(site!1~cdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)  -> DNA17(site!1~cdsb).PARP(dna!1,liIII) + LiIII(PARP)` | Transforms DNA17, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1297 | `Unlabeled` | one-way | DNA18, LiIII, PARP | `kdliIII2` | internal-state conversion/modification | `DNA18(site!1~cdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)  -> DNA18(site!1~cdsb).PARP(dna!1,liIII) + LiIII(PARP)` | Transforms DNA18, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1298 | `Unlabeled` | one-way | DNA19, LiIII, PARP | `kdliIII2` | internal-state conversion/modification | `DNA19(site!1~cdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)  -> DNA19(site!1~cdsb).PARP(dna!1,liIII) + LiIII(PARP)` | Transforms DNA19, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1299 | `Unlabeled` | one-way | DNA20, LiIII, PARP | `kdliIII2` | internal-state conversion/modification | `DNA20(site!1~cdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)  -> DNA20(site!1~cdsb).PARP(dna!1,liIII) + LiIII(PARP)` | Transforms DNA20, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1300 | `Unlabeled` | one-way | DNA21, LiIII, PARP | `kdliIII2` | internal-state conversion/modification | `DNA21(site!1~cdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)  -> DNA21(site!1~cdsb).PARP(dna!1,liIII) + LiIII(PARP)` | Transforms DNA21, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1301 | `Unlabeled` | one-way | DNA22, LiIII, PARP | `kdliIII2` | internal-state conversion/modification | `DNA22(site!1~cdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)  -> DNA22(site!1~cdsb).PARP(dna!1,liIII) + LiIII(PARP)` | Transforms DNA22, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1302 | `Unlabeled` | one-way | DNA23, LiIII, PARP | `kdliIII2` | internal-state conversion/modification | `DNA23(site!1~cdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)  -> DNA23(site!1~cdsb).PARP(dna!1,liIII) + LiIII(PARP)` | Transforms DNA23, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1303 | `Unlabeled` | one-way | DNA24, LiIII, PARP | `kdliIII2` | internal-state conversion/modification | `DNA24(site!1~cdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)  -> DNA24(site!1~cdsb).PARP(dna!1,liIII) + LiIII(PARP)` | Transforms DNA24, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1304 | `Unlabeled` | one-way | DNA25, LiIII, PARP | `kdliIII2` | internal-state conversion/modification | `DNA25(site!1~cdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)  -> DNA25(site!1~cdsb).PARP(dna!1,liIII) + LiIII(PARP)` | Transforms DNA25, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1305 | `Unlabeled` | one-way | DNA26, LiIII, PARP | `kdliIII2` | internal-state conversion/modification | `DNA26(site!1~cdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)  -> DNA26(site!1~cdsb).PARP(dna!1,liIII) + LiIII(PARP)` | Transforms DNA26, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1306 | `Unlabeled` | one-way | DNA27, LiIII, PARP | `kdliIII2` | internal-state conversion/modification | `DNA27(site!1~cdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)  -> DNA27(site!1~cdsb).PARP(dna!1,liIII) + LiIII(PARP)` | Transforms DNA27, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1307 | `Unlabeled` | one-way | DNA28, LiIII, PARP | `kdliIII2` | internal-state conversion/modification | `DNA28(site!1~cdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)  -> DNA28(site!1~cdsb).PARP(dna!1,liIII) + LiIII(PARP)` | Transforms DNA28, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1308 | `Unlabeled` | one-way | DNA29, LiIII, PARP | `kdliIII2` | internal-state conversion/modification | `DNA29(site!1~cdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)  -> DNA29(site!1~cdsb).PARP(dna!1,liIII) + LiIII(PARP)` | Transforms DNA29, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1309 | `Unlabeled` | one-way | DNA30, LiIII, PARP | `kdliIII2` | internal-state conversion/modification | `DNA30(site!1~cdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)  -> DNA30(site!1~cdsb).PARP(dna!1,liIII) + LiIII(PARP)` | Transforms DNA30, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1310 | `Unlabeled` | one-way | DNA31, LiIII, PARP | `kdliIII2` | internal-state conversion/modification | `DNA31(site!1~cdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)  -> DNA31(site!1~cdsb).PARP(dna!1,liIII) + LiIII(PARP)` | Transforms DNA31, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1311 | `Unlabeled` | one-way | DNA32, LiIII, PARP | `kdliIII2` | internal-state conversion/modification | `DNA32(site!1~cdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)  -> DNA32(site!1~cdsb).PARP(dna!1,liIII) + LiIII(PARP)` | Transforms DNA32, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1312 | `Unlabeled` | one-way | DNA33, LiIII, PARP | `kdliIII2` | internal-state conversion/modification | `DNA33(site!1~cdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)  -> DNA33(site!1~cdsb).PARP(dna!1,liIII) + LiIII(PARP)` | Transforms DNA33, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1313 | `Unlabeled` | one-way | DNA34, LiIII, PARP | `kdliIII2` | internal-state conversion/modification | `DNA34(site!1~cdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)  -> DNA34(site!1~cdsb).PARP(dna!1,liIII) + LiIII(PARP)` | Transforms DNA34, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1314 | `Unlabeled` | one-way | DNA35, LiIII, PARP | `kdliIII2` | internal-state conversion/modification | `DNA35(site!1~cdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)  -> DNA35(site!1~cdsb).PARP(dna!1,liIII) + LiIII(PARP)` | Transforms DNA35, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1315 | `Unlabeled` | one-way | DNA36, LiIII, PARP | `kdliIII2` | internal-state conversion/modification | `DNA36(site!1~cdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)  -> DNA36(site!1~cdsb).PARP(dna!1,liIII) + LiIII(PARP)` | Transforms DNA36, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1316 | `Unlabeled` | one-way | DNA37, LiIII, PARP | `kdliIII2` | internal-state conversion/modification | `DNA37(site!1~cdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)  -> DNA37(site!1~cdsb).PARP(dna!1,liIII) + LiIII(PARP)` | Transforms DNA37, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1317 | `Unlabeled` | one-way | DNA38, LiIII, PARP | `kdliIII2` | internal-state conversion/modification | `DNA38(site!1~cdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)  -> DNA38(site!1~cdsb).PARP(dna!1,liIII) + LiIII(PARP)` | Transforms DNA38, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1318 | `Unlabeled` | one-way | DNA39, LiIII, PARP | `kdliIII2` | internal-state conversion/modification | `DNA39(site!1~cdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)  -> DNA39(site!1~cdsb).PARP(dna!1,liIII) + LiIII(PARP)` | Transforms DNA39, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1319 | `Unlabeled` | one-way | DNA40, LiIII, PARP | `kdliIII2` | internal-state conversion/modification | `DNA40(site!1~cdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)  -> DNA40(site!1~cdsb).PARP(dna!1,liIII) + LiIII(PARP)` | Transforms DNA40, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1320 | `Unlabeled` | one-way | DNA41, LiIII, PARP | `kdliIII2` | internal-state conversion/modification | `DNA41(site!1~cdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)  -> DNA41(site!1~cdsb).PARP(dna!1,liIII) + LiIII(PARP)` | Transforms DNA41, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1321 | `Unlabeled` | one-way | DNA42, LiIII, PARP | `kdliIII2` | internal-state conversion/modification | `DNA42(site!1~cdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)  -> DNA42(site!1~cdsb).PARP(dna!1,liIII) + LiIII(PARP)` | Transforms DNA42, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1322 | `Unlabeled` | one-way | DNA43, LiIII, PARP | `kdliIII2` | internal-state conversion/modification | `DNA43(site!1~cdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)  -> DNA43(site!1~cdsb).PARP(dna!1,liIII) + LiIII(PARP)` | Transforms DNA43, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1323 | `Unlabeled` | one-way | DNA44, LiIII, PARP | `kdliIII2` | internal-state conversion/modification | `DNA44(site!1~cdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)  -> DNA44(site!1~cdsb).PARP(dna!1,liIII) + LiIII(PARP)` | Transforms DNA44, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1324 | `Unlabeled` | one-way | DNA45, LiIII, PARP | `kdliIII2` | internal-state conversion/modification | `DNA45(site!1~cdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)  -> DNA45(site!1~cdsb).PARP(dna!1,liIII) + LiIII(PARP)` | Transforms DNA45, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1325 | `Unlabeled` | one-way | DNA46, LiIII, PARP | `kdliIII2` | internal-state conversion/modification | `DNA46(site!1~cdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)  -> DNA46(site!1~cdsb).PARP(dna!1,liIII) + LiIII(PARP)` | Transforms DNA46, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1326 | `Unlabeled` | one-way | DNA47, LiIII, PARP | `kdliIII2` | internal-state conversion/modification | `DNA47(site!1~cdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)  -> DNA47(site!1~cdsb).PARP(dna!1,liIII) + LiIII(PARP)` | Transforms DNA47, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1327 | `Unlabeled` | one-way | DNA48, LiIII, PARP | `kdliIII2` | internal-state conversion/modification | `DNA48(site!1~cdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)  -> DNA48(site!1~cdsb).PARP(dna!1,liIII) + LiIII(PARP)` | Transforms DNA48, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1328 | `Unlabeled` | one-way | DNA49, LiIII, PARP | `kdliIII2` | internal-state conversion/modification | `DNA49(site!1~cdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)  -> DNA49(site!1~cdsb).PARP(dna!1,liIII) + LiIII(PARP)` | Transforms DNA49, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1329 | `Unlabeled` | one-way | DNA50, LiIII, PARP | `kdliIII2` | internal-state conversion/modification | `DNA50(site!1~cdsb).PARP(dna!1,liIII!2).LiIII(PARP!2)  -> DNA50(site!1~cdsb).PARP(dna!1,liIII) + LiIII(PARP)` | Transforms DNA50, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1330 | `Unlabeled` | one-way | ATM, DNA1, LiIII, PARP | `kfixIII1` | internal-state conversion/modification | `DNA1(site!1~sdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA1(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA1, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1331 | `Unlabeled` | one-way | ATM, DNA2, LiIII, PARP | `kfixIII1` | internal-state conversion/modification | `DNA2(site!1~sdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA2(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA2, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1332 | `Unlabeled` | one-way | ATM, DNA3, LiIII, PARP | `kfixIII1` | internal-state conversion/modification | `DNA3(site!1~sdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA3(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA3, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1333 | `Unlabeled` | one-way | ATM, DNA4, LiIII, PARP | `kfixIII1` | internal-state conversion/modification | `DNA4(site!1~sdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA4(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA4, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1334 | `Unlabeled` | one-way | ATM, DNA5, LiIII, PARP | `kfixIII1` | internal-state conversion/modification | `DNA5(site!1~sdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA5(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA5, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1335 | `Unlabeled` | one-way | ATM, DNA6, LiIII, PARP | `kfixIII1` | internal-state conversion/modification | `DNA6(site!1~sdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA6(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA6, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1336 | `Unlabeled` | one-way | ATM, DNA7, LiIII, PARP | `kfixIII1` | internal-state conversion/modification | `DNA7(site!1~sdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA7(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA7, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1337 | `Unlabeled` | one-way | ATM, DNA8, LiIII, PARP | `kfixIII1` | internal-state conversion/modification | `DNA8(site!1~sdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA8(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA8, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1338 | `Unlabeled` | one-way | ATM, DNA9, LiIII, PARP | `kfixIII1` | internal-state conversion/modification | `DNA9(site!1~sdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA9(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA9, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1339 | `Unlabeled` | one-way | ATM, DNA10, LiIII, PARP | `kfixIII1` | internal-state conversion/modification | `DNA10(site!1~sdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA10(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA10, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1340 | `Unlabeled` | one-way | ATM, DNA11, LiIII, PARP | `kfixIII1` | internal-state conversion/modification | `DNA11(site!1~sdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA11(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA11, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1341 | `Unlabeled` | one-way | ATM, DNA12, LiIII, PARP | `kfixIII1` | internal-state conversion/modification | `DNA12(site!1~sdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA12(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA12, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1342 | `Unlabeled` | one-way | ATM, DNA13, LiIII, PARP | `kfixIII1` | internal-state conversion/modification | `DNA13(site!1~sdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA13(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA13, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1343 | `Unlabeled` | one-way | ATM, DNA14, LiIII, PARP | `kfixIII1` | internal-state conversion/modification | `DNA14(site!1~sdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA14(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA14, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1344 | `Unlabeled` | one-way | ATM, DNA15, LiIII, PARP | `kfixIII1` | internal-state conversion/modification | `DNA15(site!1~sdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA15(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA15, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1345 | `Unlabeled` | one-way | ATM, DNA16, LiIII, PARP | `kfixIII1` | internal-state conversion/modification | `DNA16(site!1~sdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA16(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA16, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1346 | `Unlabeled` | one-way | ATM, DNA17, LiIII, PARP | `kfixIII1` | internal-state conversion/modification | `DNA17(site!1~sdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA17(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA17, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1347 | `Unlabeled` | one-way | ATM, DNA18, LiIII, PARP | `kfixIII1` | internal-state conversion/modification | `DNA18(site!1~sdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA18(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA18, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1348 | `Unlabeled` | one-way | ATM, DNA19, LiIII, PARP | `kfixIII1` | internal-state conversion/modification | `DNA19(site!1~sdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA19(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA19, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1349 | `Unlabeled` | one-way | ATM, DNA20, LiIII, PARP | `kfixIII1` | internal-state conversion/modification | `DNA20(site!1~sdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA20(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA20, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1350 | `Unlabeled` | one-way | ATM, DNA21, LiIII, PARP | `kfixIII1` | internal-state conversion/modification | `DNA21(site!1~sdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA21(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA21, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1351 | `Unlabeled` | one-way | ATM, DNA22, LiIII, PARP | `kfixIII1` | internal-state conversion/modification | `DNA22(site!1~sdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA22(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA22, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1352 | `Unlabeled` | one-way | ATM, DNA23, LiIII, PARP | `kfixIII1` | internal-state conversion/modification | `DNA23(site!1~sdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA23(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA23, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1353 | `Unlabeled` | one-way | ATM, DNA24, LiIII, PARP | `kfixIII1` | internal-state conversion/modification | `DNA24(site!1~sdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA24(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA24, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1354 | `Unlabeled` | one-way | ATM, DNA25, LiIII, PARP | `kfixIII1` | internal-state conversion/modification | `DNA25(site!1~sdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA25(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA25, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1355 | `Unlabeled` | one-way | ATM, DNA26, LiIII, PARP | `kfixIII1` | internal-state conversion/modification | `DNA26(site!1~sdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA26(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA26, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1356 | `Unlabeled` | one-way | ATM, DNA27, LiIII, PARP | `kfixIII1` | internal-state conversion/modification | `DNA27(site!1~sdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA27(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA27, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1357 | `Unlabeled` | one-way | ATM, DNA28, LiIII, PARP | `kfixIII1` | internal-state conversion/modification | `DNA28(site!1~sdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA28(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA28, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1358 | `Unlabeled` | one-way | ATM, DNA29, LiIII, PARP | `kfixIII1` | internal-state conversion/modification | `DNA29(site!1~sdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA29(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA29, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1359 | `Unlabeled` | one-way | ATM, DNA30, LiIII, PARP | `kfixIII1` | internal-state conversion/modification | `DNA30(site!1~sdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA30(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA30, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1360 | `Unlabeled` | one-way | ATM, DNA31, LiIII, PARP | `kfixIII1` | internal-state conversion/modification | `DNA31(site!1~sdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA31(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA31, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1361 | `Unlabeled` | one-way | ATM, DNA32, LiIII, PARP | `kfixIII1` | internal-state conversion/modification | `DNA32(site!1~sdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA32(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA32, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1362 | `Unlabeled` | one-way | ATM, DNA33, LiIII, PARP | `kfixIII1` | internal-state conversion/modification | `DNA33(site!1~sdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA33(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA33, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1363 | `Unlabeled` | one-way | ATM, DNA34, LiIII, PARP | `kfixIII1` | internal-state conversion/modification | `DNA34(site!1~sdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA34(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA34, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1364 | `Unlabeled` | one-way | ATM, DNA35, LiIII, PARP | `kfixIII1` | internal-state conversion/modification | `DNA35(site!1~sdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA35(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA35, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1365 | `Unlabeled` | one-way | ATM, DNA36, LiIII, PARP | `kfixIII1` | internal-state conversion/modification | `DNA36(site!1~sdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA36(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA36, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1366 | `Unlabeled` | one-way | ATM, DNA37, LiIII, PARP | `kfixIII1` | internal-state conversion/modification | `DNA37(site!1~sdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA37(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA37, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1367 | `Unlabeled` | one-way | ATM, DNA38, LiIII, PARP | `kfixIII1` | internal-state conversion/modification | `DNA38(site!1~sdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA38(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA38, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1368 | `Unlabeled` | one-way | ATM, DNA39, LiIII, PARP | `kfixIII1` | internal-state conversion/modification | `DNA39(site!1~sdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA39(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA39, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1369 | `Unlabeled` | one-way | ATM, DNA40, LiIII, PARP | `kfixIII1` | internal-state conversion/modification | `DNA40(site!1~sdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA40(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA40, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1370 | `Unlabeled` | one-way | ATM, DNA41, LiIII, PARP | `kfixIII1` | internal-state conversion/modification | `DNA41(site!1~sdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA41(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA41, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1371 | `Unlabeled` | one-way | ATM, DNA42, LiIII, PARP | `kfixIII1` | internal-state conversion/modification | `DNA42(site!1~sdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA42(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA42, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1372 | `Unlabeled` | one-way | ATM, DNA43, LiIII, PARP | `kfixIII1` | internal-state conversion/modification | `DNA43(site!1~sdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA43(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA43, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1373 | `Unlabeled` | one-way | ATM, DNA44, LiIII, PARP | `kfixIII1` | internal-state conversion/modification | `DNA44(site!1~sdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA44(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA44, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1374 | `Unlabeled` | one-way | ATM, DNA45, LiIII, PARP | `kfixIII1` | internal-state conversion/modification | `DNA45(site!1~sdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA45(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA45, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1375 | `Unlabeled` | one-way | ATM, DNA46, LiIII, PARP | `kfixIII1` | internal-state conversion/modification | `DNA46(site!1~sdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA46(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA46, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1376 | `Unlabeled` | one-way | ATM, DNA47, LiIII, PARP | `kfixIII1` | internal-state conversion/modification | `DNA47(site!1~sdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA47(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA47, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1377 | `Unlabeled` | one-way | ATM, DNA48, LiIII, PARP | `kfixIII1` | internal-state conversion/modification | `DNA48(site!1~sdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA48(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA48, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1378 | `Unlabeled` | one-way | ATM, DNA49, LiIII, PARP | `kfixIII1` | internal-state conversion/modification | `DNA49(site!1~sdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA49(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA49, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1379 | `Unlabeled` | one-way | ATM, DNA50, LiIII, PARP | `kfixIII1` | internal-state conversion/modification | `DNA50(site!1~sdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA50(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA50, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1380 | `Unlabeled` | one-way | ATM, DNA1, LiIII, PARP | `kfixIII2` | internal-state conversion/modification | `DNA1(site!1~cdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA1(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA1, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1381 | `Unlabeled` | one-way | ATM, DNA2, LiIII, PARP | `kfixIII2` | internal-state conversion/modification | `DNA2(site!1~cdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA2(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA2, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1382 | `Unlabeled` | one-way | ATM, DNA3, LiIII, PARP | `kfixIII2` | internal-state conversion/modification | `DNA3(site!1~cdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA3(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA3, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1383 | `Unlabeled` | one-way | ATM, DNA4, LiIII, PARP | `kfixIII2` | internal-state conversion/modification | `DNA4(site!1~cdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA4(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA4, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1384 | `Unlabeled` | one-way | ATM, DNA5, LiIII, PARP | `kfixIII2` | internal-state conversion/modification | `DNA5(site!1~cdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA5(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA5, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1385 | `Unlabeled` | one-way | ATM, DNA6, LiIII, PARP | `kfixIII2` | internal-state conversion/modification | `DNA6(site!1~cdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA6(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA6, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1386 | `Unlabeled` | one-way | ATM, DNA7, LiIII, PARP | `kfixIII2` | internal-state conversion/modification | `DNA7(site!1~cdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA7(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA7, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1387 | `Unlabeled` | one-way | ATM, DNA8, LiIII, PARP | `kfixIII2` | internal-state conversion/modification | `DNA8(site!1~cdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA8(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA8, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1388 | `Unlabeled` | one-way | ATM, DNA9, LiIII, PARP | `kfixIII2` | internal-state conversion/modification | `DNA9(site!1~cdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA9(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA9, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1389 | `Unlabeled` | one-way | ATM, DNA10, LiIII, PARP | `kfixIII2` | internal-state conversion/modification | `DNA10(site!1~cdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA10(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA10, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1390 | `Unlabeled` | one-way | ATM, DNA11, LiIII, PARP | `kfixIII2` | internal-state conversion/modification | `DNA11(site!1~cdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA11(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA11, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1391 | `Unlabeled` | one-way | ATM, DNA12, LiIII, PARP | `kfixIII2` | internal-state conversion/modification | `DNA12(site!1~cdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA12(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA12, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1392 | `Unlabeled` | one-way | ATM, DNA13, LiIII, PARP | `kfixIII2` | internal-state conversion/modification | `DNA13(site!1~cdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA13(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA13, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1393 | `Unlabeled` | one-way | ATM, DNA14, LiIII, PARP | `kfixIII2` | internal-state conversion/modification | `DNA14(site!1~cdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA14(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA14, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1394 | `Unlabeled` | one-way | ATM, DNA15, LiIII, PARP | `kfixIII2` | internal-state conversion/modification | `DNA15(site!1~cdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA15(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA15, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1395 | `Unlabeled` | one-way | ATM, DNA16, LiIII, PARP | `kfixIII2` | internal-state conversion/modification | `DNA16(site!1~cdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA16(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA16, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1396 | `Unlabeled` | one-way | ATM, DNA17, LiIII, PARP | `kfixIII2` | internal-state conversion/modification | `DNA17(site!1~cdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA17(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA17, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1397 | `Unlabeled` | one-way | ATM, DNA18, LiIII, PARP | `kfixIII2` | internal-state conversion/modification | `DNA18(site!1~cdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA18(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA18, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1398 | `Unlabeled` | one-way | ATM, DNA19, LiIII, PARP | `kfixIII2` | internal-state conversion/modification | `DNA19(site!1~cdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA19(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA19, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1399 | `Unlabeled` | one-way | ATM, DNA20, LiIII, PARP | `kfixIII2` | internal-state conversion/modification | `DNA20(site!1~cdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA20(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA20, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1400 | `Unlabeled` | one-way | ATM, DNA21, LiIII, PARP | `kfixIII2` | internal-state conversion/modification | `DNA21(site!1~cdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA21(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA21, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1401 | `Unlabeled` | one-way | ATM, DNA22, LiIII, PARP | `kfixIII2` | internal-state conversion/modification | `DNA22(site!1~cdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA22(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA22, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1402 | `Unlabeled` | one-way | ATM, DNA23, LiIII, PARP | `kfixIII2` | internal-state conversion/modification | `DNA23(site!1~cdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA23(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA23, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1403 | `Unlabeled` | one-way | ATM, DNA24, LiIII, PARP | `kfixIII2` | internal-state conversion/modification | `DNA24(site!1~cdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA24(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA24, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1404 | `Unlabeled` | one-way | ATM, DNA25, LiIII, PARP | `kfixIII2` | internal-state conversion/modification | `DNA25(site!1~cdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA25(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA25, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1405 | `Unlabeled` | one-way | ATM, DNA26, LiIII, PARP | `kfixIII2` | internal-state conversion/modification | `DNA26(site!1~cdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA26(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA26, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1406 | `Unlabeled` | one-way | ATM, DNA27, LiIII, PARP | `kfixIII2` | internal-state conversion/modification | `DNA27(site!1~cdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA27(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA27, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1407 | `Unlabeled` | one-way | ATM, DNA28, LiIII, PARP | `kfixIII2` | internal-state conversion/modification | `DNA28(site!1~cdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA28(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA28, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1408 | `Unlabeled` | one-way | ATM, DNA29, LiIII, PARP | `kfixIII2` | internal-state conversion/modification | `DNA29(site!1~cdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA29(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA29, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1409 | `Unlabeled` | one-way | ATM, DNA30, LiIII, PARP | `kfixIII2` | internal-state conversion/modification | `DNA30(site!1~cdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA30(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA30, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1410 | `Unlabeled` | one-way | ATM, DNA31, LiIII, PARP | `kfixIII2` | internal-state conversion/modification | `DNA31(site!1~cdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA31(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA31, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1411 | `Unlabeled` | one-way | ATM, DNA32, LiIII, PARP | `kfixIII2` | internal-state conversion/modification | `DNA32(site!1~cdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA32(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA32, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1412 | `Unlabeled` | one-way | ATM, DNA33, LiIII, PARP | `kfixIII2` | internal-state conversion/modification | `DNA33(site!1~cdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA33(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA33, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1413 | `Unlabeled` | one-way | ATM, DNA34, LiIII, PARP | `kfixIII2` | internal-state conversion/modification | `DNA34(site!1~cdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA34(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA34, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1414 | `Unlabeled` | one-way | ATM, DNA35, LiIII, PARP | `kfixIII2` | internal-state conversion/modification | `DNA35(site!1~cdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA35(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA35, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1415 | `Unlabeled` | one-way | ATM, DNA36, LiIII, PARP | `kfixIII2` | internal-state conversion/modification | `DNA36(site!1~cdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA36(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA36, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1416 | `Unlabeled` | one-way | ATM, DNA37, LiIII, PARP | `kfixIII2` | internal-state conversion/modification | `DNA37(site!1~cdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA37(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA37, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1417 | `Unlabeled` | one-way | ATM, DNA38, LiIII, PARP | `kfixIII2` | internal-state conversion/modification | `DNA38(site!1~cdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA38(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA38, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1418 | `Unlabeled` | one-way | ATM, DNA39, LiIII, PARP | `kfixIII2` | internal-state conversion/modification | `DNA39(site!1~cdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA39(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA39, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1419 | `Unlabeled` | one-way | ATM, DNA40, LiIII, PARP | `kfixIII2` | internal-state conversion/modification | `DNA40(site!1~cdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA40(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA40, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1420 | `Unlabeled` | one-way | ATM, DNA41, LiIII, PARP | `kfixIII2` | internal-state conversion/modification | `DNA41(site!1~cdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA41(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA41, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1421 | `Unlabeled` | one-way | ATM, DNA42, LiIII, PARP | `kfixIII2` | internal-state conversion/modification | `DNA42(site!1~cdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA42(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA42, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1422 | `Unlabeled` | one-way | ATM, DNA43, LiIII, PARP | `kfixIII2` | internal-state conversion/modification | `DNA43(site!1~cdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA43(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA43, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1423 | `Unlabeled` | one-way | ATM, DNA44, LiIII, PARP | `kfixIII2` | internal-state conversion/modification | `DNA44(site!1~cdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA44(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA44, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1424 | `Unlabeled` | one-way | ATM, DNA45, LiIII, PARP | `kfixIII2` | internal-state conversion/modification | `DNA45(site!1~cdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA45(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA45, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1425 | `Unlabeled` | one-way | ATM, DNA46, LiIII, PARP | `kfixIII2` | internal-state conversion/modification | `DNA46(site!1~cdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA46(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA46, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1426 | `Unlabeled` | one-way | ATM, DNA47, LiIII, PARP | `kfixIII2` | internal-state conversion/modification | `DNA47(site!1~cdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA47(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA47, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1427 | `Unlabeled` | one-way | ATM, DNA48, LiIII, PARP | `kfixIII2` | internal-state conversion/modification | `DNA48(site!1~cdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA48(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA48, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1428 | `Unlabeled` | one-way | ATM, DNA49, LiIII, PARP | `kfixIII2` | internal-state conversion/modification | `DNA49(site!1~cdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA49(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA49, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1429 | `Unlabeled` | one-way | ATM, DNA50, LiIII, PARP | `kfixIII2` | internal-state conversion/modification | `DNA50(site!1~cdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA50(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA50, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1430 | `Unlabeled` | one-way | ATM, DNA1, LiIII, PARP | `kfixIII3` | internal-state conversion/modification | `DNA1(site!1~sdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA1(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA1, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1431 | `Unlabeled` | one-way | ATM, DNA2, LiIII, PARP | `kfixIII3` | internal-state conversion/modification | `DNA2(site!1~sdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA2(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA2, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1432 | `Unlabeled` | one-way | ATM, DNA3, LiIII, PARP | `kfixIII3` | internal-state conversion/modification | `DNA3(site!1~sdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA3(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA3, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1433 | `Unlabeled` | one-way | ATM, DNA4, LiIII, PARP | `kfixIII3` | internal-state conversion/modification | `DNA4(site!1~sdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA4(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA4, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1434 | `Unlabeled` | one-way | ATM, DNA5, LiIII, PARP | `kfixIII3` | internal-state conversion/modification | `DNA5(site!1~sdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA5(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA5, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1435 | `Unlabeled` | one-way | ATM, DNA6, LiIII, PARP | `kfixIII3` | internal-state conversion/modification | `DNA6(site!1~sdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA6(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA6, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1436 | `Unlabeled` | one-way | ATM, DNA7, LiIII, PARP | `kfixIII3` | internal-state conversion/modification | `DNA7(site!1~sdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA7(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA7, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1437 | `Unlabeled` | one-way | ATM, DNA8, LiIII, PARP | `kfixIII3` | internal-state conversion/modification | `DNA8(site!1~sdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA8(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA8, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1438 | `Unlabeled` | one-way | ATM, DNA9, LiIII, PARP | `kfixIII3` | internal-state conversion/modification | `DNA9(site!1~sdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA9(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA9, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1439 | `Unlabeled` | one-way | ATM, DNA10, LiIII, PARP | `kfixIII3` | internal-state conversion/modification | `DNA10(site!1~sdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA10(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA10, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1440 | `Unlabeled` | one-way | ATM, DNA11, LiIII, PARP | `kfixIII3` | internal-state conversion/modification | `DNA11(site!1~sdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA11(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA11, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1441 | `Unlabeled` | one-way | ATM, DNA12, LiIII, PARP | `kfixIII3` | internal-state conversion/modification | `DNA12(site!1~sdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA12(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA12, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1442 | `Unlabeled` | one-way | ATM, DNA13, LiIII, PARP | `kfixIII3` | internal-state conversion/modification | `DNA13(site!1~sdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA13(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA13, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1443 | `Unlabeled` | one-way | ATM, DNA14, LiIII, PARP | `kfixIII3` | internal-state conversion/modification | `DNA14(site!1~sdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA14(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA14, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1444 | `Unlabeled` | one-way | ATM, DNA15, LiIII, PARP | `kfixIII3` | internal-state conversion/modification | `DNA15(site!1~sdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA15(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA15, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1445 | `Unlabeled` | one-way | ATM, DNA16, LiIII, PARP | `kfixIII3` | internal-state conversion/modification | `DNA16(site!1~sdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA16(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA16, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1446 | `Unlabeled` | one-way | ATM, DNA17, LiIII, PARP | `kfixIII3` | internal-state conversion/modification | `DNA17(site!1~sdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA17(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA17, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1447 | `Unlabeled` | one-way | ATM, DNA18, LiIII, PARP | `kfixIII3` | internal-state conversion/modification | `DNA18(site!1~sdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA18(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA18, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1448 | `Unlabeled` | one-way | ATM, DNA19, LiIII, PARP | `kfixIII3` | internal-state conversion/modification | `DNA19(site!1~sdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA19(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA19, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1449 | `Unlabeled` | one-way | ATM, DNA20, LiIII, PARP | `kfixIII3` | internal-state conversion/modification | `DNA20(site!1~sdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA20(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA20, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1450 | `Unlabeled` | one-way | ATM, DNA21, LiIII, PARP | `kfixIII3` | internal-state conversion/modification | `DNA21(site!1~sdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA21(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA21, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1451 | `Unlabeled` | one-way | ATM, DNA22, LiIII, PARP | `kfixIII3` | internal-state conversion/modification | `DNA22(site!1~sdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA22(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA22, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1452 | `Unlabeled` | one-way | ATM, DNA23, LiIII, PARP | `kfixIII3` | internal-state conversion/modification | `DNA23(site!1~sdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA23(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA23, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1453 | `Unlabeled` | one-way | ATM, DNA24, LiIII, PARP | `kfixIII3` | internal-state conversion/modification | `DNA24(site!1~sdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA24(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA24, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1454 | `Unlabeled` | one-way | ATM, DNA25, LiIII, PARP | `kfixIII3` | internal-state conversion/modification | `DNA25(site!1~sdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA25(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA25, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1455 | `Unlabeled` | one-way | ATM, DNA26, LiIII, PARP | `kfixIII3` | internal-state conversion/modification | `DNA26(site!1~sdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA26(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA26, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1456 | `Unlabeled` | one-way | ATM, DNA27, LiIII, PARP | `kfixIII3` | internal-state conversion/modification | `DNA27(site!1~sdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA27(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA27, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1457 | `Unlabeled` | one-way | ATM, DNA28, LiIII, PARP | `kfixIII3` | internal-state conversion/modification | `DNA28(site!1~sdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA28(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA28, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1458 | `Unlabeled` | one-way | ATM, DNA29, LiIII, PARP | `kfixIII3` | internal-state conversion/modification | `DNA29(site!1~sdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA29(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA29, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1459 | `Unlabeled` | one-way | ATM, DNA30, LiIII, PARP | `kfixIII3` | internal-state conversion/modification | `DNA30(site!1~sdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA30(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA30, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1460 | `Unlabeled` | one-way | ATM, DNA31, LiIII, PARP | `kfixIII3` | internal-state conversion/modification | `DNA31(site!1~sdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA31(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA31, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1461 | `Unlabeled` | one-way | ATM, DNA32, LiIII, PARP | `kfixIII3` | internal-state conversion/modification | `DNA32(site!1~sdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA32(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA32, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1462 | `Unlabeled` | one-way | ATM, DNA33, LiIII, PARP | `kfixIII3` | internal-state conversion/modification | `DNA33(site!1~sdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA33(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA33, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1463 | `Unlabeled` | one-way | ATM, DNA34, LiIII, PARP | `kfixIII3` | internal-state conversion/modification | `DNA34(site!1~sdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA34(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA34, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1464 | `Unlabeled` | one-way | ATM, DNA35, LiIII, PARP | `kfixIII3` | internal-state conversion/modification | `DNA35(site!1~sdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA35(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA35, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1465 | `Unlabeled` | one-way | ATM, DNA36, LiIII, PARP | `kfixIII3` | internal-state conversion/modification | `DNA36(site!1~sdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA36(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA36, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1466 | `Unlabeled` | one-way | ATM, DNA37, LiIII, PARP | `kfixIII3` | internal-state conversion/modification | `DNA37(site!1~sdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA37(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA37, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1467 | `Unlabeled` | one-way | ATM, DNA38, LiIII, PARP | `kfixIII3` | internal-state conversion/modification | `DNA38(site!1~sdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA38(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA38, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1468 | `Unlabeled` | one-way | ATM, DNA39, LiIII, PARP | `kfixIII3` | internal-state conversion/modification | `DNA39(site!1~sdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA39(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA39, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1469 | `Unlabeled` | one-way | ATM, DNA40, LiIII, PARP | `kfixIII3` | internal-state conversion/modification | `DNA40(site!1~sdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA40(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA40, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1470 | `Unlabeled` | one-way | ATM, DNA41, LiIII, PARP | `kfixIII3` | internal-state conversion/modification | `DNA41(site!1~sdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA41(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA41, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1471 | `Unlabeled` | one-way | ATM, DNA42, LiIII, PARP | `kfixIII3` | internal-state conversion/modification | `DNA42(site!1~sdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA42(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA42, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1472 | `Unlabeled` | one-way | ATM, DNA43, LiIII, PARP | `kfixIII3` | internal-state conversion/modification | `DNA43(site!1~sdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA43(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA43, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1473 | `Unlabeled` | one-way | ATM, DNA44, LiIII, PARP | `kfixIII3` | internal-state conversion/modification | `DNA44(site!1~sdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA44(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA44, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1474 | `Unlabeled` | one-way | ATM, DNA45, LiIII, PARP | `kfixIII3` | internal-state conversion/modification | `DNA45(site!1~sdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA45(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA45, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1475 | `Unlabeled` | one-way | ATM, DNA46, LiIII, PARP | `kfixIII3` | internal-state conversion/modification | `DNA46(site!1~sdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA46(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA46, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1476 | `Unlabeled` | one-way | ATM, DNA47, LiIII, PARP | `kfixIII3` | internal-state conversion/modification | `DNA47(site!1~sdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA47(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA47, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1477 | `Unlabeled` | one-way | ATM, DNA48, LiIII, PARP | `kfixIII3` | internal-state conversion/modification | `DNA48(site!1~sdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA48(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA48, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1478 | `Unlabeled` | one-way | ATM, DNA49, LiIII, PARP | `kfixIII3` | internal-state conversion/modification | `DNA49(site!1~sdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA49(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA49, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1479 | `Unlabeled` | one-way | ATM, DNA50, LiIII, PARP | `kfixIII3` | internal-state conversion/modification | `DNA50(site!1~sdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA50(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA50, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1480 | `Unlabeled` | one-way | ATM, DNA1, LiIII, PARP | `kfixIII4` | internal-state conversion/modification | `DNA1(site!1~cdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA1(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA1, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1481 | `Unlabeled` | one-way | ATM, DNA2, LiIII, PARP | `kfixIII4` | internal-state conversion/modification | `DNA2(site!1~cdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA2(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA2, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1482 | `Unlabeled` | one-way | ATM, DNA3, LiIII, PARP | `kfixIII4` | internal-state conversion/modification | `DNA3(site!1~cdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA3(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA3, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1483 | `Unlabeled` | one-way | ATM, DNA4, LiIII, PARP | `kfixIII4` | internal-state conversion/modification | `DNA4(site!1~cdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA4(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA4, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1484 | `Unlabeled` | one-way | ATM, DNA5, LiIII, PARP | `kfixIII4` | internal-state conversion/modification | `DNA5(site!1~cdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA5(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA5, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1485 | `Unlabeled` | one-way | ATM, DNA6, LiIII, PARP | `kfixIII4` | internal-state conversion/modification | `DNA6(site!1~cdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA6(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA6, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1486 | `Unlabeled` | one-way | ATM, DNA7, LiIII, PARP | `kfixIII4` | internal-state conversion/modification | `DNA7(site!1~cdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA7(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA7, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1487 | `Unlabeled` | one-way | ATM, DNA8, LiIII, PARP | `kfixIII4` | internal-state conversion/modification | `DNA8(site!1~cdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA8(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA8, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1488 | `Unlabeled` | one-way | ATM, DNA9, LiIII, PARP | `kfixIII4` | internal-state conversion/modification | `DNA9(site!1~cdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA9(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA9, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1489 | `Unlabeled` | one-way | ATM, DNA10, LiIII, PARP | `kfixIII4` | internal-state conversion/modification | `DNA10(site!1~cdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA10(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA10, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1490 | `Unlabeled` | one-way | ATM, DNA11, LiIII, PARP | `kfixIII4` | internal-state conversion/modification | `DNA11(site!1~cdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA11(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA11, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1491 | `Unlabeled` | one-way | ATM, DNA12, LiIII, PARP | `kfixIII4` | internal-state conversion/modification | `DNA12(site!1~cdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA12(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA12, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1492 | `Unlabeled` | one-way | ATM, DNA13, LiIII, PARP | `kfixIII4` | internal-state conversion/modification | `DNA13(site!1~cdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA13(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA13, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1493 | `Unlabeled` | one-way | ATM, DNA14, LiIII, PARP | `kfixIII4` | internal-state conversion/modification | `DNA14(site!1~cdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA14(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA14, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1494 | `Unlabeled` | one-way | ATM, DNA15, LiIII, PARP | `kfixIII4` | internal-state conversion/modification | `DNA15(site!1~cdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA15(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA15, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1495 | `Unlabeled` | one-way | ATM, DNA16, LiIII, PARP | `kfixIII4` | internal-state conversion/modification | `DNA16(site!1~cdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA16(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA16, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1496 | `Unlabeled` | one-way | ATM, DNA17, LiIII, PARP | `kfixIII4` | internal-state conversion/modification | `DNA17(site!1~cdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA17(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA17, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1497 | `Unlabeled` | one-way | ATM, DNA18, LiIII, PARP | `kfixIII4` | internal-state conversion/modification | `DNA18(site!1~cdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA18(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA18, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1498 | `Unlabeled` | one-way | ATM, DNA19, LiIII, PARP | `kfixIII4` | internal-state conversion/modification | `DNA19(site!1~cdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA19(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA19, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1499 | `Unlabeled` | one-way | ATM, DNA20, LiIII, PARP | `kfixIII4` | internal-state conversion/modification | `DNA20(site!1~cdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA20(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA20, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1500 | `Unlabeled` | one-way | ATM, DNA21, LiIII, PARP | `kfixIII4` | internal-state conversion/modification | `DNA21(site!1~cdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA21(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA21, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

### Rules 1501-1750

| # | Rule label/name | Direction | Participants | Rate/expression | Modeled change | Rule pattern | Technical meaning |
| ---: | --- | --- | --- | --- | --- | --- | --- |

| 1501 | `Unlabeled` | one-way | ATM, DNA22, LiIII, PARP | `kfixIII4` | internal-state conversion/modification | `DNA22(site!1~cdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA22(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA22, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1502 | `Unlabeled` | one-way | ATM, DNA23, LiIII, PARP | `kfixIII4` | internal-state conversion/modification | `DNA23(site!1~cdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA23(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA23, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1503 | `Unlabeled` | one-way | ATM, DNA24, LiIII, PARP | `kfixIII4` | internal-state conversion/modification | `DNA24(site!1~cdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA24(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA24, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1504 | `Unlabeled` | one-way | ATM, DNA25, LiIII, PARP | `kfixIII4` | internal-state conversion/modification | `DNA25(site!1~cdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA25(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA25, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1505 | `Unlabeled` | one-way | ATM, DNA26, LiIII, PARP | `kfixIII4` | internal-state conversion/modification | `DNA26(site!1~cdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA26(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA26, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1506 | `Unlabeled` | one-way | ATM, DNA27, LiIII, PARP | `kfixIII4` | internal-state conversion/modification | `DNA27(site!1~cdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA27(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA27, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1507 | `Unlabeled` | one-way | ATM, DNA28, LiIII, PARP | `kfixIII4` | internal-state conversion/modification | `DNA28(site!1~cdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA28(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA28, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1508 | `Unlabeled` | one-way | ATM, DNA29, LiIII, PARP | `kfixIII4` | internal-state conversion/modification | `DNA29(site!1~cdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA29(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA29, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1509 | `Unlabeled` | one-way | ATM, DNA30, LiIII, PARP | `kfixIII4` | internal-state conversion/modification | `DNA30(site!1~cdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA30(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA30, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1510 | `Unlabeled` | one-way | ATM, DNA31, LiIII, PARP | `kfixIII4` | internal-state conversion/modification | `DNA31(site!1~cdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA31(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA31, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1511 | `Unlabeled` | one-way | ATM, DNA32, LiIII, PARP | `kfixIII4` | internal-state conversion/modification | `DNA32(site!1~cdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA32(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA32, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1512 | `Unlabeled` | one-way | ATM, DNA33, LiIII, PARP | `kfixIII4` | internal-state conversion/modification | `DNA33(site!1~cdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA33(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA33, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1513 | `Unlabeled` | one-way | ATM, DNA34, LiIII, PARP | `kfixIII4` | internal-state conversion/modification | `DNA34(site!1~cdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA34(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA34, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1514 | `Unlabeled` | one-way | ATM, DNA35, LiIII, PARP | `kfixIII4` | internal-state conversion/modification | `DNA35(site!1~cdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA35(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA35, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1515 | `Unlabeled` | one-way | ATM, DNA36, LiIII, PARP | `kfixIII4` | internal-state conversion/modification | `DNA36(site!1~cdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA36(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA36, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1516 | `Unlabeled` | one-way | ATM, DNA37, LiIII, PARP | `kfixIII4` | internal-state conversion/modification | `DNA37(site!1~cdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA37(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA37, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1517 | `Unlabeled` | one-way | ATM, DNA38, LiIII, PARP | `kfixIII4` | internal-state conversion/modification | `DNA38(site!1~cdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA38(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA38, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1518 | `Unlabeled` | one-way | ATM, DNA39, LiIII, PARP | `kfixIII4` | internal-state conversion/modification | `DNA39(site!1~cdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA39(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA39, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1519 | `Unlabeled` | one-way | ATM, DNA40, LiIII, PARP | `kfixIII4` | internal-state conversion/modification | `DNA40(site!1~cdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA40(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA40, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1520 | `Unlabeled` | one-way | ATM, DNA41, LiIII, PARP | `kfixIII4` | internal-state conversion/modification | `DNA41(site!1~cdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA41(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA41, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1521 | `Unlabeled` | one-way | ATM, DNA42, LiIII, PARP | `kfixIII4` | internal-state conversion/modification | `DNA42(site!1~cdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA42(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA42, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1522 | `Unlabeled` | one-way | ATM, DNA43, LiIII, PARP | `kfixIII4` | internal-state conversion/modification | `DNA43(site!1~cdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA43(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA43, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1523 | `Unlabeled` | one-way | ATM, DNA44, LiIII, PARP | `kfixIII4` | internal-state conversion/modification | `DNA44(site!1~cdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA44(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA44, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1524 | `Unlabeled` | one-way | ATM, DNA45, LiIII, PARP | `kfixIII4` | internal-state conversion/modification | `DNA45(site!1~cdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA45(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA45, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1525 | `Unlabeled` | one-way | ATM, DNA46, LiIII, PARP | `kfixIII4` | internal-state conversion/modification | `DNA46(site!1~cdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA46(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA46, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1526 | `Unlabeled` | one-way | ATM, DNA47, LiIII, PARP | `kfixIII4` | internal-state conversion/modification | `DNA47(site!1~cdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA47(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA47, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1527 | `Unlabeled` | one-way | ATM, DNA48, LiIII, PARP | `kfixIII4` | internal-state conversion/modification | `DNA48(site!1~cdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA48(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA48, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1528 | `Unlabeled` | one-way | ATM, DNA49, LiIII, PARP | `kfixIII4` | internal-state conversion/modification | `DNA49(site!1~cdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA49(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA49, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1529 | `Unlabeled` | one-way | ATM, DNA50, LiIII, PARP | `kfixIII4` | internal-state conversion/modification | `DNA50(site!1~cdsb,h2ax!3~foc).PARP(dna!1,liIII!2).LiIII(PARP!2).ATM(h2ax!3)  -> DNA50(site~ok,h2ax!1~foc).ATM(h2ax!1) + PARP(dna,liIII) + LiIII(PARP)` | Transforms ATM, DNA50, LiIII, PARP by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1530 | `Unlabeled` | one-way | ATM, DNA1 | `kATMact` | internal-state conversion/modification | `DNA1(site!?~sdsb) + ATM(state~0,h2ax)  -> DNA1(site!?~sdsb) + ATM(state~1,h2ax)` | Transforms ATM, DNA1 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1531 | `Unlabeled` | one-way | ATM, DNA2 | `kATMact` | internal-state conversion/modification | `DNA2(site!?~sdsb) + ATM(state~0,h2ax)  -> DNA2(site!?~sdsb) + ATM(state~2,h2ax)` | Transforms ATM, DNA2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1532 | `Unlabeled` | one-way | ATM, DNA3 | `kATMact` | internal-state conversion/modification | `DNA3(site!?~sdsb) + ATM(state~0,h2ax)  -> DNA3(site!?~sdsb) + ATM(state~3,h2ax)` | Transforms ATM, DNA3 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1533 | `Unlabeled` | one-way | ATM, DNA4 | `kATMact` | internal-state conversion/modification | `DNA4(site!?~sdsb) + ATM(state~0,h2ax)  -> DNA4(site!?~sdsb) + ATM(state~4,h2ax)` | Transforms ATM, DNA4 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1534 | `Unlabeled` | one-way | ATM, DNA5 | `kATMact` | internal-state conversion/modification | `DNA5(site!?~sdsb) + ATM(state~0,h2ax)  -> DNA5(site!?~sdsb) + ATM(state~5,h2ax)` | Transforms ATM, DNA5 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1535 | `Unlabeled` | one-way | ATM, DNA6 | `kATMact` | internal-state conversion/modification | `DNA6(site!?~sdsb) + ATM(state~0,h2ax)  -> DNA6(site!?~sdsb) + ATM(state~6,h2ax)` | Transforms ATM, DNA6 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1536 | `Unlabeled` | one-way | ATM, DNA7 | `kATMact` | internal-state conversion/modification | `DNA7(site!?~sdsb) + ATM(state~0,h2ax)  -> DNA7(site!?~sdsb) + ATM(state~7,h2ax)` | Transforms ATM, DNA7 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1537 | `Unlabeled` | one-way | ATM, DNA8 | `kATMact` | internal-state conversion/modification | `DNA8(site!?~sdsb) + ATM(state~0,h2ax)  -> DNA8(site!?~sdsb) + ATM(state~8,h2ax)` | Transforms ATM, DNA8 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1538 | `Unlabeled` | one-way | ATM, DNA9 | `kATMact` | internal-state conversion/modification | `DNA9(site!?~sdsb) + ATM(state~0,h2ax)  -> DNA9(site!?~sdsb) + ATM(state~9,h2ax)` | Transforms ATM, DNA9 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1539 | `Unlabeled` | one-way | ATM, DNA10 | `kATMact` | internal-state conversion/modification | `DNA10(site!?~sdsb) + ATM(state~0,h2ax)  -> DNA10(site!?~sdsb) + ATM(state~10,h2ax)` | Transforms ATM, DNA10 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1540 | `Unlabeled` | one-way | ATM, DNA11 | `kATMact` | internal-state conversion/modification | `DNA11(site!?~sdsb) + ATM(state~0,h2ax)  -> DNA11(site!?~sdsb) + ATM(state~11,h2ax)` | Transforms ATM, DNA11 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1541 | `Unlabeled` | one-way | ATM, DNA12 | `kATMact` | internal-state conversion/modification | `DNA12(site!?~sdsb) + ATM(state~0,h2ax)  -> DNA12(site!?~sdsb) + ATM(state~12,h2ax)` | Transforms ATM, DNA12 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1542 | `Unlabeled` | one-way | ATM, DNA13 | `kATMact` | internal-state conversion/modification | `DNA13(site!?~sdsb) + ATM(state~0,h2ax)  -> DNA13(site!?~sdsb) + ATM(state~13,h2ax)` | Transforms ATM, DNA13 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1543 | `Unlabeled` | one-way | ATM, DNA14 | `kATMact` | internal-state conversion/modification | `DNA14(site!?~sdsb) + ATM(state~0,h2ax)  -> DNA14(site!?~sdsb) + ATM(state~14,h2ax)` | Transforms ATM, DNA14 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1544 | `Unlabeled` | one-way | ATM, DNA15 | `kATMact` | internal-state conversion/modification | `DNA15(site!?~sdsb) + ATM(state~0,h2ax)  -> DNA15(site!?~sdsb) + ATM(state~15,h2ax)` | Transforms ATM, DNA15 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1545 | `Unlabeled` | one-way | ATM, DNA16 | `kATMact` | internal-state conversion/modification | `DNA16(site!?~sdsb) + ATM(state~0,h2ax)  -> DNA16(site!?~sdsb) + ATM(state~16,h2ax)` | Transforms ATM, DNA16 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1546 | `Unlabeled` | one-way | ATM, DNA17 | `kATMact` | internal-state conversion/modification | `DNA17(site!?~sdsb) + ATM(state~0,h2ax)  -> DNA17(site!?~sdsb) + ATM(state~17,h2ax)` | Transforms ATM, DNA17 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1547 | `Unlabeled` | one-way | ATM, DNA18 | `kATMact` | internal-state conversion/modification | `DNA18(site!?~sdsb) + ATM(state~0,h2ax)  -> DNA18(site!?~sdsb) + ATM(state~18,h2ax)` | Transforms ATM, DNA18 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1548 | `Unlabeled` | one-way | ATM, DNA19 | `kATMact` | internal-state conversion/modification | `DNA19(site!?~sdsb) + ATM(state~0,h2ax)  -> DNA19(site!?~sdsb) + ATM(state~19,h2ax)` | Transforms ATM, DNA19 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1549 | `Unlabeled` | one-way | ATM, DNA20 | `kATMact` | internal-state conversion/modification | `DNA20(site!?~sdsb) + ATM(state~0,h2ax)  -> DNA20(site!?~sdsb) + ATM(state~20,h2ax)` | Transforms ATM, DNA20 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1550 | `Unlabeled` | one-way | ATM, DNA21 | `kATMact` | internal-state conversion/modification | `DNA21(site!?~sdsb) + ATM(state~0,h2ax)  -> DNA21(site!?~sdsb) + ATM(state~21,h2ax)` | Transforms ATM, DNA21 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1551 | `Unlabeled` | one-way | ATM, DNA22 | `kATMact` | internal-state conversion/modification | `DNA22(site!?~sdsb) + ATM(state~0,h2ax)  -> DNA22(site!?~sdsb) + ATM(state~22,h2ax)` | Transforms ATM, DNA22 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1552 | `Unlabeled` | one-way | ATM, DNA23 | `kATMact` | internal-state conversion/modification | `DNA23(site!?~sdsb) + ATM(state~0,h2ax)  -> DNA23(site!?~sdsb) + ATM(state~23,h2ax)` | Transforms ATM, DNA23 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1553 | `Unlabeled` | one-way | ATM, DNA24 | `kATMact` | internal-state conversion/modification | `DNA24(site!?~sdsb) + ATM(state~0,h2ax)  -> DNA24(site!?~sdsb) + ATM(state~24,h2ax)` | Transforms ATM, DNA24 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1554 | `Unlabeled` | one-way | ATM, DNA25 | `kATMact` | internal-state conversion/modification | `DNA25(site!?~sdsb) + ATM(state~0,h2ax)  -> DNA25(site!?~sdsb) + ATM(state~25,h2ax)` | Transforms ATM, DNA25 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1555 | `Unlabeled` | one-way | ATM, DNA26 | `kATMact` | internal-state conversion/modification | `DNA26(site!?~sdsb) + ATM(state~0,h2ax)  -> DNA26(site!?~sdsb) + ATM(state~26,h2ax)` | Transforms ATM, DNA26 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1556 | `Unlabeled` | one-way | ATM, DNA27 | `kATMact` | internal-state conversion/modification | `DNA27(site!?~sdsb) + ATM(state~0,h2ax)  -> DNA27(site!?~sdsb) + ATM(state~27,h2ax)` | Transforms ATM, DNA27 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1557 | `Unlabeled` | one-way | ATM, DNA28 | `kATMact` | internal-state conversion/modification | `DNA28(site!?~sdsb) + ATM(state~0,h2ax)  -> DNA28(site!?~sdsb) + ATM(state~28,h2ax)` | Transforms ATM, DNA28 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1558 | `Unlabeled` | one-way | ATM, DNA29 | `kATMact` | internal-state conversion/modification | `DNA29(site!?~sdsb) + ATM(state~0,h2ax)  -> DNA29(site!?~sdsb) + ATM(state~29,h2ax)` | Transforms ATM, DNA29 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1559 | `Unlabeled` | one-way | ATM, DNA30 | `kATMact` | internal-state conversion/modification | `DNA30(site!?~sdsb) + ATM(state~0,h2ax)  -> DNA30(site!?~sdsb) + ATM(state~30,h2ax)` | Transforms ATM, DNA30 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1560 | `Unlabeled` | one-way | ATM, DNA31 | `kATMact` | internal-state conversion/modification | `DNA31(site!?~sdsb) + ATM(state~0,h2ax)  -> DNA31(site!?~sdsb) + ATM(state~31,h2ax)` | Transforms ATM, DNA31 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1561 | `Unlabeled` | one-way | ATM, DNA32 | `kATMact` | internal-state conversion/modification | `DNA32(site!?~sdsb) + ATM(state~0,h2ax)  -> DNA32(site!?~sdsb) + ATM(state~32,h2ax)` | Transforms ATM, DNA32 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1562 | `Unlabeled` | one-way | ATM, DNA33 | `kATMact` | internal-state conversion/modification | `DNA33(site!?~sdsb) + ATM(state~0,h2ax)  -> DNA33(site!?~sdsb) + ATM(state~33,h2ax)` | Transforms ATM, DNA33 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1563 | `Unlabeled` | one-way | ATM, DNA34 | `kATMact` | internal-state conversion/modification | `DNA34(site!?~sdsb) + ATM(state~0,h2ax)  -> DNA34(site!?~sdsb) + ATM(state~34,h2ax)` | Transforms ATM, DNA34 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1564 | `Unlabeled` | one-way | ATM, DNA35 | `kATMact` | internal-state conversion/modification | `DNA35(site!?~sdsb) + ATM(state~0,h2ax)  -> DNA35(site!?~sdsb) + ATM(state~35,h2ax)` | Transforms ATM, DNA35 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1565 | `Unlabeled` | one-way | ATM, DNA36 | `kATMact` | internal-state conversion/modification | `DNA36(site!?~sdsb) + ATM(state~0,h2ax)  -> DNA36(site!?~sdsb) + ATM(state~36,h2ax)` | Transforms ATM, DNA36 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1566 | `Unlabeled` | one-way | ATM, DNA37 | `kATMact` | internal-state conversion/modification | `DNA37(site!?~sdsb) + ATM(state~0,h2ax)  -> DNA37(site!?~sdsb) + ATM(state~37,h2ax)` | Transforms ATM, DNA37 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1567 | `Unlabeled` | one-way | ATM, DNA38 | `kATMact` | internal-state conversion/modification | `DNA38(site!?~sdsb) + ATM(state~0,h2ax)  -> DNA38(site!?~sdsb) + ATM(state~38,h2ax)` | Transforms ATM, DNA38 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1568 | `Unlabeled` | one-way | ATM, DNA39 | `kATMact` | internal-state conversion/modification | `DNA39(site!?~sdsb) + ATM(state~0,h2ax)  -> DNA39(site!?~sdsb) + ATM(state~39,h2ax)` | Transforms ATM, DNA39 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1569 | `Unlabeled` | one-way | ATM, DNA40 | `kATMact` | internal-state conversion/modification | `DNA40(site!?~sdsb) + ATM(state~0,h2ax)  -> DNA40(site!?~sdsb) + ATM(state~40,h2ax)` | Transforms ATM, DNA40 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1570 | `Unlabeled` | one-way | ATM, DNA41 | `kATMact` | internal-state conversion/modification | `DNA41(site!?~sdsb) + ATM(state~0,h2ax)  -> DNA41(site!?~sdsb) + ATM(state~41,h2ax)` | Transforms ATM, DNA41 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1571 | `Unlabeled` | one-way | ATM, DNA42 | `kATMact` | internal-state conversion/modification | `DNA42(site!?~sdsb) + ATM(state~0,h2ax)  -> DNA42(site!?~sdsb) + ATM(state~42,h2ax)` | Transforms ATM, DNA42 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1572 | `Unlabeled` | one-way | ATM, DNA43 | `kATMact` | internal-state conversion/modification | `DNA43(site!?~sdsb) + ATM(state~0,h2ax)  -> DNA43(site!?~sdsb) + ATM(state~43,h2ax)` | Transforms ATM, DNA43 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1573 | `Unlabeled` | one-way | ATM, DNA44 | `kATMact` | internal-state conversion/modification | `DNA44(site!?~sdsb) + ATM(state~0,h2ax)  -> DNA44(site!?~sdsb) + ATM(state~44,h2ax)` | Transforms ATM, DNA44 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1574 | `Unlabeled` | one-way | ATM, DNA45 | `kATMact` | internal-state conversion/modification | `DNA45(site!?~sdsb) + ATM(state~0,h2ax)  -> DNA45(site!?~sdsb) + ATM(state~45,h2ax)` | Transforms ATM, DNA45 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1575 | `Unlabeled` | one-way | ATM, DNA46 | `kATMact` | internal-state conversion/modification | `DNA46(site!?~sdsb) + ATM(state~0,h2ax)  -> DNA46(site!?~sdsb) + ATM(state~46,h2ax)` | Transforms ATM, DNA46 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1576 | `Unlabeled` | one-way | ATM, DNA47 | `kATMact` | internal-state conversion/modification | `DNA47(site!?~sdsb) + ATM(state~0,h2ax)  -> DNA47(site!?~sdsb) + ATM(state~47,h2ax)` | Transforms ATM, DNA47 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1577 | `Unlabeled` | one-way | ATM, DNA48 | `kATMact` | internal-state conversion/modification | `DNA48(site!?~sdsb) + ATM(state~0,h2ax)  -> DNA48(site!?~sdsb) + ATM(state~48,h2ax)` | Transforms ATM, DNA48 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1578 | `Unlabeled` | one-way | ATM, DNA49 | `kATMact` | internal-state conversion/modification | `DNA49(site!?~sdsb) + ATM(state~0,h2ax)  -> DNA49(site!?~sdsb) + ATM(state~49,h2ax)` | Transforms ATM, DNA49 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1579 | `Unlabeled` | one-way | ATM, DNA50 | `kATMact` | internal-state conversion/modification | `DNA50(site!?~sdsb) + ATM(state~0,h2ax)  -> DNA50(site!?~sdsb) + ATM(state~50,h2ax)` | Transforms ATM, DNA50 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1580 | `Unlabeled` | one-way | ATM, DNA1 | `kATMact` | internal-state conversion/modification | `DNA1(site!?~cdsb) + ATM(state~0,h2ax)  -> DNA1(site!?~cdsb) + ATM(state~1,h2ax)` | Transforms ATM, DNA1 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1581 | `Unlabeled` | one-way | ATM, DNA2 | `kATMact` | internal-state conversion/modification | `DNA2(site!?~cdsb) + ATM(state~0,h2ax)  -> DNA2(site!?~cdsb) + ATM(state~2,h2ax)` | Transforms ATM, DNA2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1582 | `Unlabeled` | one-way | ATM, DNA3 | `kATMact` | internal-state conversion/modification | `DNA3(site!?~cdsb) + ATM(state~0,h2ax)  -> DNA3(site!?~cdsb) + ATM(state~3,h2ax)` | Transforms ATM, DNA3 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1583 | `Unlabeled` | one-way | ATM, DNA4 | `kATMact` | internal-state conversion/modification | `DNA4(site!?~cdsb) + ATM(state~0,h2ax)  -> DNA4(site!?~cdsb) + ATM(state~4,h2ax)` | Transforms ATM, DNA4 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1584 | `Unlabeled` | one-way | ATM, DNA5 | `kATMact` | internal-state conversion/modification | `DNA5(site!?~cdsb) + ATM(state~0,h2ax)  -> DNA5(site!?~cdsb) + ATM(state~5,h2ax)` | Transforms ATM, DNA5 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1585 | `Unlabeled` | one-way | ATM, DNA6 | `kATMact` | internal-state conversion/modification | `DNA6(site!?~cdsb) + ATM(state~0,h2ax)  -> DNA6(site!?~cdsb) + ATM(state~6,h2ax)` | Transforms ATM, DNA6 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1586 | `Unlabeled` | one-way | ATM, DNA7 | `kATMact` | internal-state conversion/modification | `DNA7(site!?~cdsb) + ATM(state~0,h2ax)  -> DNA7(site!?~cdsb) + ATM(state~7,h2ax)` | Transforms ATM, DNA7 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1587 | `Unlabeled` | one-way | ATM, DNA8 | `kATMact` | internal-state conversion/modification | `DNA8(site!?~cdsb) + ATM(state~0,h2ax)  -> DNA8(site!?~cdsb) + ATM(state~8,h2ax)` | Transforms ATM, DNA8 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1588 | `Unlabeled` | one-way | ATM, DNA9 | `kATMact` | internal-state conversion/modification | `DNA9(site!?~cdsb) + ATM(state~0,h2ax)  -> DNA9(site!?~cdsb) + ATM(state~9,h2ax)` | Transforms ATM, DNA9 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1589 | `Unlabeled` | one-way | ATM, DNA10 | `kATMact` | internal-state conversion/modification | `DNA10(site!?~cdsb) + ATM(state~0,h2ax)  -> DNA10(site!?~cdsb) + ATM(state~10,h2ax)` | Transforms ATM, DNA10 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1590 | `Unlabeled` | one-way | ATM, DNA11 | `kATMact` | internal-state conversion/modification | `DNA11(site!?~cdsb) + ATM(state~0,h2ax)  -> DNA11(site!?~cdsb) + ATM(state~12,h2ax)` | Transforms ATM, DNA11 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1591 | `Unlabeled` | one-way | ATM, DNA12 | `kATMact` | internal-state conversion/modification | `DNA12(site!?~cdsb) + ATM(state~0,h2ax)  -> DNA12(site!?~cdsb) + ATM(state~13,h2ax)` | Transforms ATM, DNA12 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1592 | `Unlabeled` | one-way | ATM, DNA13 | `kATMact` | internal-state conversion/modification | `DNA13(site!?~cdsb) + ATM(state~0,h2ax)  -> DNA13(site!?~cdsb) + ATM(state~13,h2ax)` | Transforms ATM, DNA13 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1593 | `Unlabeled` | one-way | ATM, DNA14 | `kATMact` | internal-state conversion/modification | `DNA14(site!?~cdsb) + ATM(state~0,h2ax)  -> DNA14(site!?~cdsb) + ATM(state~14,h2ax)` | Transforms ATM, DNA14 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1594 | `Unlabeled` | one-way | ATM, DNA15 | `kATMact` | internal-state conversion/modification | `DNA15(site!?~cdsb) + ATM(state~0,h2ax)  -> DNA15(site!?~cdsb) + ATM(state~15,h2ax)` | Transforms ATM, DNA15 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1595 | `Unlabeled` | one-way | ATM, DNA16 | `kATMact` | internal-state conversion/modification | `DNA16(site!?~cdsb) + ATM(state~0,h2ax)  -> DNA16(site!?~cdsb) + ATM(state~16,h2ax)` | Transforms ATM, DNA16 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1596 | `Unlabeled` | one-way | ATM, DNA17 | `kATMact` | internal-state conversion/modification | `DNA17(site!?~cdsb) + ATM(state~0,h2ax)  -> DNA17(site!?~cdsb) + ATM(state~17,h2ax)` | Transforms ATM, DNA17 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1597 | `Unlabeled` | one-way | ATM, DNA18 | `kATMact` | internal-state conversion/modification | `DNA18(site!?~cdsb) + ATM(state~0,h2ax)  -> DNA18(site!?~cdsb) + ATM(state~18,h2ax)` | Transforms ATM, DNA18 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1598 | `Unlabeled` | one-way | ATM, DNA19 | `kATMact` | internal-state conversion/modification | `DNA19(site!?~cdsb) + ATM(state~0,h2ax)  -> DNA19(site!?~cdsb) + ATM(state~19,h2ax)` | Transforms ATM, DNA19 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1599 | `Unlabeled` | one-way | ATM, DNA20 | `kATMact` | internal-state conversion/modification | `DNA20(site!?~cdsb) + ATM(state~0,h2ax)  -> DNA20(site!?~cdsb) + ATM(state~20,h2ax)` | Transforms ATM, DNA20 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1600 | `Unlabeled` | one-way | ATM, DNA21 | `kATMact` | internal-state conversion/modification | `DNA21(site!?~cdsb) + ATM(state~0,h2ax)  -> DNA21(site!?~cdsb) + ATM(state~21,h2ax)` | Transforms ATM, DNA21 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1601 | `Unlabeled` | one-way | ATM, DNA22 | `kATMact` | internal-state conversion/modification | `DNA22(site!?~cdsb) + ATM(state~0,h2ax)  -> DNA22(site!?~cdsb) + ATM(state~22,h2ax)` | Transforms ATM, DNA22 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1602 | `Unlabeled` | one-way | ATM, DNA23 | `kATMact` | internal-state conversion/modification | `DNA23(site!?~cdsb) + ATM(state~0,h2ax)  -> DNA23(site!?~cdsb) + ATM(state~23,h2ax)` | Transforms ATM, DNA23 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1603 | `Unlabeled` | one-way | ATM, DNA24 | `kATMact` | internal-state conversion/modification | `DNA24(site!?~cdsb) + ATM(state~0,h2ax)  -> DNA24(site!?~cdsb) + ATM(state~24,h2ax)` | Transforms ATM, DNA24 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1604 | `Unlabeled` | one-way | ATM, DNA25 | `kATMact` | internal-state conversion/modification | `DNA25(site!?~cdsb) + ATM(state~0,h2ax)  -> DNA25(site!?~cdsb) + ATM(state~25,h2ax)` | Transforms ATM, DNA25 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1605 | `Unlabeled` | one-way | ATM, DNA26 | `kATMact` | internal-state conversion/modification | `DNA26(site!?~cdsb) + ATM(state~0,h2ax)  -> DNA26(site!?~cdsb) + ATM(state~26,h2ax)` | Transforms ATM, DNA26 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1606 | `Unlabeled` | one-way | ATM, DNA27 | `kATMact` | internal-state conversion/modification | `DNA27(site!?~cdsb) + ATM(state~0,h2ax)  -> DNA27(site!?~cdsb) + ATM(state~27,h2ax)` | Transforms ATM, DNA27 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1607 | `Unlabeled` | one-way | ATM, DNA28 | `kATMact` | internal-state conversion/modification | `DNA28(site!?~cdsb) + ATM(state~0,h2ax)  -> DNA28(site!?~cdsb) + ATM(state~28,h2ax)` | Transforms ATM, DNA28 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1608 | `Unlabeled` | one-way | ATM, DNA29 | `kATMact` | internal-state conversion/modification | `DNA29(site!?~cdsb) + ATM(state~0,h2ax)  -> DNA29(site!?~cdsb) + ATM(state~29,h2ax)` | Transforms ATM, DNA29 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1609 | `Unlabeled` | one-way | ATM, DNA30 | `kATMact` | internal-state conversion/modification | `DNA30(site!?~cdsb) + ATM(state~0,h2ax)  -> DNA30(site!?~cdsb) + ATM(state~30,h2ax)` | Transforms ATM, DNA30 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1610 | `Unlabeled` | one-way | ATM, DNA31 | `kATMact` | internal-state conversion/modification | `DNA31(site!?~cdsb) + ATM(state~0,h2ax)  -> DNA31(site!?~cdsb) + ATM(state~31,h2ax)` | Transforms ATM, DNA31 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1611 | `Unlabeled` | one-way | ATM, DNA32 | `kATMact` | internal-state conversion/modification | `DNA32(site!?~cdsb) + ATM(state~0,h2ax)  -> DNA32(site!?~cdsb) + ATM(state~32,h2ax)` | Transforms ATM, DNA32 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1612 | `Unlabeled` | one-way | ATM, DNA33 | `kATMact` | internal-state conversion/modification | `DNA33(site!?~cdsb) + ATM(state~0,h2ax)  -> DNA33(site!?~cdsb) + ATM(state~33,h2ax)` | Transforms ATM, DNA33 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1613 | `Unlabeled` | one-way | ATM, DNA34 | `kATMact` | internal-state conversion/modification | `DNA34(site!?~cdsb) + ATM(state~0,h2ax)  -> DNA34(site!?~cdsb) + ATM(state~34,h2ax)` | Transforms ATM, DNA34 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1614 | `Unlabeled` | one-way | ATM, DNA35 | `kATMact` | internal-state conversion/modification | `DNA35(site!?~cdsb) + ATM(state~0,h2ax)  -> DNA35(site!?~cdsb) + ATM(state~35,h2ax)` | Transforms ATM, DNA35 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1615 | `Unlabeled` | one-way | ATM, DNA36 | `kATMact` | internal-state conversion/modification | `DNA36(site!?~cdsb) + ATM(state~0,h2ax)  -> DNA36(site!?~cdsb) + ATM(state~36,h2ax)` | Transforms ATM, DNA36 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1616 | `Unlabeled` | one-way | ATM, DNA37 | `kATMact` | internal-state conversion/modification | `DNA37(site!?~cdsb) + ATM(state~0,h2ax)  -> DNA37(site!?~cdsb) + ATM(state~37,h2ax)` | Transforms ATM, DNA37 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1617 | `Unlabeled` | one-way | ATM, DNA38 | `kATMact` | internal-state conversion/modification | `DNA38(site!?~cdsb) + ATM(state~0,h2ax)  -> DNA38(site!?~cdsb) + ATM(state~38,h2ax)` | Transforms ATM, DNA38 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1618 | `Unlabeled` | one-way | ATM, DNA39 | `kATMact` | internal-state conversion/modification | `DNA39(site!?~cdsb) + ATM(state~0,h2ax)  -> DNA39(site!?~cdsb) + ATM(state~39,h2ax)` | Transforms ATM, DNA39 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1619 | `Unlabeled` | one-way | ATM, DNA40 | `kATMact` | internal-state conversion/modification | `DNA40(site!?~cdsb) + ATM(state~0,h2ax)  -> DNA40(site!?~cdsb) + ATM(state~40,h2ax)` | Transforms ATM, DNA40 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1620 | `Unlabeled` | one-way | ATM, DNA41 | `kATMact` | internal-state conversion/modification | `DNA41(site!?~cdsb) + ATM(state~0,h2ax)  -> DNA41(site!?~cdsb) + ATM(state~41,h2ax)` | Transforms ATM, DNA41 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1621 | `Unlabeled` | one-way | ATM, DNA42 | `kATMact` | internal-state conversion/modification | `DNA42(site!?~cdsb) + ATM(state~0,h2ax)  -> DNA42(site!?~cdsb) + ATM(state~42,h2ax)` | Transforms ATM, DNA42 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1622 | `Unlabeled` | one-way | ATM, DNA43 | `kATMact` | internal-state conversion/modification | `DNA43(site!?~cdsb) + ATM(state~0,h2ax)  -> DNA43(site!?~cdsb) + ATM(state~43,h2ax)` | Transforms ATM, DNA43 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1623 | `Unlabeled` | one-way | ATM, DNA44 | `kATMact` | internal-state conversion/modification | `DNA44(site!?~cdsb) + ATM(state~0,h2ax)  -> DNA44(site!?~cdsb) + ATM(state~44,h2ax)` | Transforms ATM, DNA44 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1624 | `Unlabeled` | one-way | ATM, DNA45 | `kATMact` | internal-state conversion/modification | `DNA45(site!?~cdsb) + ATM(state~0,h2ax)  -> DNA45(site!?~cdsb) + ATM(state~45,h2ax)` | Transforms ATM, DNA45 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1625 | `Unlabeled` | one-way | ATM, DNA46 | `kATMact` | internal-state conversion/modification | `DNA46(site!?~cdsb) + ATM(state~0,h2ax)  -> DNA46(site!?~cdsb) + ATM(state~46,h2ax)` | Transforms ATM, DNA46 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1626 | `Unlabeled` | one-way | ATM, DNA47 | `kATMact` | internal-state conversion/modification | `DNA47(site!?~cdsb) + ATM(state~0,h2ax)  -> DNA47(site!?~cdsb) + ATM(state~47,h2ax)` | Transforms ATM, DNA47 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1627 | `Unlabeled` | one-way | ATM, DNA48 | `kATMact` | internal-state conversion/modification | `DNA48(site!?~cdsb) + ATM(state~0,h2ax)  -> DNA48(site!?~cdsb) + ATM(state~48,h2ax)` | Transforms ATM, DNA48 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1628 | `Unlabeled` | one-way | ATM, DNA49 | `kATMact` | internal-state conversion/modification | `DNA49(site!?~cdsb) + ATM(state~0,h2ax)  -> DNA49(site!?~cdsb) + ATM(state~49,h2ax)` | Transforms ATM, DNA49 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1629 | `Unlabeled` | one-way | ATM, DNA50 | `kATMact` | internal-state conversion/modification | `DNA50(site!?~cdsb) + ATM(state~0,h2ax)  -> DNA50(site!?~cdsb) + ATM(state~50,h2ax)` | Transforms ATM, DNA50 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1630 | `Unlabeled` | one-way | ATM | `kATMinact` | internal-state conversion/modification | `ATM(state~1,h2ax)  -> ATM(state~0,h2ax)` | Transforms ATM by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1631 | `Unlabeled` | one-way | ATM | `kATMinact` | internal-state conversion/modification | `ATM(state~2,h2ax)  -> ATM(state~0,h2ax)` | Transforms ATM by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1632 | `Unlabeled` | one-way | ATM | `kATMinact` | internal-state conversion/modification | `ATM(state~3,h2ax)  -> ATM(state~0,h2ax)` | Transforms ATM by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1633 | `Unlabeled` | one-way | ATM | `kATMinact` | internal-state conversion/modification | `ATM(state~4,h2ax)  -> ATM(state~0,h2ax)` | Transforms ATM by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1634 | `Unlabeled` | one-way | ATM | `kATMinact` | internal-state conversion/modification | `ATM(state~5,h2ax)  -> ATM(state~0,h2ax)` | Transforms ATM by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1635 | `Unlabeled` | one-way | ATM | `kATMinact` | internal-state conversion/modification | `ATM(state~6,h2ax)  -> ATM(state~0,h2ax)` | Transforms ATM by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1636 | `Unlabeled` | one-way | ATM | `kATMinact` | internal-state conversion/modification | `ATM(state~7,h2ax)  -> ATM(state~0,h2ax)` | Transforms ATM by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1637 | `Unlabeled` | one-way | ATM | `kATMinact` | internal-state conversion/modification | `ATM(state~8,h2ax)  -> ATM(state~0,h2ax)` | Transforms ATM by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1638 | `Unlabeled` | one-way | ATM | `kATMinact` | internal-state conversion/modification | `ATM(state~9,h2ax)  -> ATM(state~0,h2ax)` | Transforms ATM by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1639 | `Unlabeled` | one-way | ATM | `kATMinact` | internal-state conversion/modification | `ATM(state~10,h2ax)  -> ATM(state~0,h2ax)` | Transforms ATM by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1640 | `Unlabeled` | one-way | ATM | `kATMinact` | internal-state conversion/modification | `ATM(state~11,h2ax)  -> ATM(state~0,h2ax)` | Transforms ATM by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1641 | `Unlabeled` | one-way | ATM | `kATMinact` | internal-state conversion/modification | `ATM(state~12,h2ax)  -> ATM(state~0,h2ax)` | Transforms ATM by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1642 | `Unlabeled` | one-way | ATM | `kATMinact` | internal-state conversion/modification | `ATM(state~13,h2ax)  -> ATM(state~0,h2ax)` | Transforms ATM by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1643 | `Unlabeled` | one-way | ATM | `kATMinact` | internal-state conversion/modification | `ATM(state~14,h2ax)  -> ATM(state~0,h2ax)` | Transforms ATM by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1644 | `Unlabeled` | one-way | ATM | `kATMinact` | internal-state conversion/modification | `ATM(state~15,h2ax)  -> ATM(state~0,h2ax)` | Transforms ATM by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1645 | `Unlabeled` | one-way | ATM | `kATMinact` | internal-state conversion/modification | `ATM(state~16,h2ax)  -> ATM(state~0,h2ax)` | Transforms ATM by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1646 | `Unlabeled` | one-way | ATM | `kATMinact` | internal-state conversion/modification | `ATM(state~17,h2ax)  -> ATM(state~0,h2ax)` | Transforms ATM by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1647 | `Unlabeled` | one-way | ATM | `kATMinact` | internal-state conversion/modification | `ATM(state~18,h2ax)  -> ATM(state~0,h2ax)` | Transforms ATM by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1648 | `Unlabeled` | one-way | ATM | `kATMinact` | internal-state conversion/modification | `ATM(state~19,h2ax)  -> ATM(state~0,h2ax)` | Transforms ATM by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1649 | `Unlabeled` | one-way | ATM | `kATMinact` | internal-state conversion/modification | `ATM(state~20,h2ax)  -> ATM(state~0,h2ax)` | Transforms ATM by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1650 | `Unlabeled` | one-way | ATM | `kATMinact` | internal-state conversion/modification | `ATM(state~21,h2ax)  -> ATM(state~0,h2ax)` | Transforms ATM by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1651 | `Unlabeled` | one-way | ATM | `kATMinact` | internal-state conversion/modification | `ATM(state~22,h2ax)  -> ATM(state~0,h2ax)` | Transforms ATM by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1652 | `Unlabeled` | one-way | ATM | `kATMinact` | internal-state conversion/modification | `ATM(state~23,h2ax)  -> ATM(state~0,h2ax)` | Transforms ATM by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1653 | `Unlabeled` | one-way | ATM | `kATMinact` | internal-state conversion/modification | `ATM(state~24,h2ax)  -> ATM(state~0,h2ax)` | Transforms ATM by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1654 | `Unlabeled` | one-way | ATM | `kATMinact` | internal-state conversion/modification | `ATM(state~25,h2ax)  -> ATM(state~0,h2ax)` | Transforms ATM by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1655 | `Unlabeled` | one-way | ATM | `kATMinact` | internal-state conversion/modification | `ATM(state~26,h2ax)  -> ATM(state~0,h2ax)` | Transforms ATM by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1656 | `Unlabeled` | one-way | ATM | `kATMinact` | internal-state conversion/modification | `ATM(state~27,h2ax)  -> ATM(state~0,h2ax)` | Transforms ATM by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1657 | `Unlabeled` | one-way | ATM | `kATMinact` | internal-state conversion/modification | `ATM(state~28,h2ax)  -> ATM(state~0,h2ax)` | Transforms ATM by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1658 | `Unlabeled` | one-way | ATM | `kATMinact` | internal-state conversion/modification | `ATM(state~29,h2ax)  -> ATM(state~0,h2ax)` | Transforms ATM by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1659 | `Unlabeled` | one-way | ATM | `kATMinact` | internal-state conversion/modification | `ATM(state~30,h2ax)  -> ATM(state~0,h2ax)` | Transforms ATM by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1660 | `Unlabeled` | one-way | ATM | `kATMinact` | internal-state conversion/modification | `ATM(state~31,h2ax)  -> ATM(state~0,h2ax)` | Transforms ATM by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1661 | `Unlabeled` | one-way | ATM | `kATMinact` | internal-state conversion/modification | `ATM(state~32,h2ax)  -> ATM(state~0,h2ax)` | Transforms ATM by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1662 | `Unlabeled` | one-way | ATM | `kATMinact` | internal-state conversion/modification | `ATM(state~33,h2ax)  -> ATM(state~0,h2ax)` | Transforms ATM by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1663 | `Unlabeled` | one-way | ATM | `kATMinact` | internal-state conversion/modification | `ATM(state~34,h2ax)  -> ATM(state~0,h2ax)` | Transforms ATM by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1664 | `Unlabeled` | one-way | ATM | `kATMinact` | internal-state conversion/modification | `ATM(state~35,h2ax)  -> ATM(state~0,h2ax)` | Transforms ATM by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1665 | `Unlabeled` | one-way | ATM | `kATMinact` | internal-state conversion/modification | `ATM(state~36,h2ax)  -> ATM(state~0,h2ax)` | Transforms ATM by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1666 | `Unlabeled` | one-way | ATM | `kATMinact` | internal-state conversion/modification | `ATM(state~37,h2ax)  -> ATM(state~0,h2ax)` | Transforms ATM by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1667 | `Unlabeled` | one-way | ATM | `kATMinact` | internal-state conversion/modification | `ATM(state~38,h2ax)  -> ATM(state~0,h2ax)` | Transforms ATM by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1668 | `Unlabeled` | one-way | ATM | `kATMinact` | internal-state conversion/modification | `ATM(state~39,h2ax)  -> ATM(state~0,h2ax)` | Transforms ATM by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1669 | `Unlabeled` | one-way | ATM | `kATMinact` | internal-state conversion/modification | `ATM(state~40,h2ax)  -> ATM(state~0,h2ax)` | Transforms ATM by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1670 | `Unlabeled` | one-way | ATM | `kATMinact` | internal-state conversion/modification | `ATM(state~41,h2ax)  -> ATM(state~0,h2ax)` | Transforms ATM by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1671 | `Unlabeled` | one-way | ATM | `kATMinact` | internal-state conversion/modification | `ATM(state~42,h2ax)  -> ATM(state~0,h2ax)` | Transforms ATM by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1672 | `Unlabeled` | one-way | ATM | `kATMinact` | internal-state conversion/modification | `ATM(state~43,h2ax)  -> ATM(state~0,h2ax)` | Transforms ATM by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1673 | `Unlabeled` | one-way | ATM | `kATMinact` | internal-state conversion/modification | `ATM(state~44,h2ax)  -> ATM(state~0,h2ax)` | Transforms ATM by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1674 | `Unlabeled` | one-way | ATM | `kATMinact` | internal-state conversion/modification | `ATM(state~45,h2ax)  -> ATM(state~0,h2ax)` | Transforms ATM by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1675 | `Unlabeled` | one-way | ATM | `kATMinact` | internal-state conversion/modification | `ATM(state~46,h2ax)  -> ATM(state~0,h2ax)` | Transforms ATM by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1676 | `Unlabeled` | one-way | ATM | `kATMinact` | internal-state conversion/modification | `ATM(state~47,h2ax)  -> ATM(state~0,h2ax)` | Transforms ATM by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1677 | `Unlabeled` | one-way | ATM | `kATMinact` | internal-state conversion/modification | `ATM(state~48,h2ax)  -> ATM(state~0,h2ax)` | Transforms ATM by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1678 | `Unlabeled` | one-way | ATM | `kATMinact` | internal-state conversion/modification | `ATM(state~49,h2ax)  -> ATM(state~0,h2ax)` | Transforms ATM by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1679 | `Unlabeled` | one-way | ATM | `kATMinact` | internal-state conversion/modification | `ATM(state~50,h2ax)  -> ATM(state~0,h2ax)` | Transforms ATM by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1680 | `Unlabeled` | one-way | ATM, DNA1 | `kh2axp1` | internal-state conversion/modification | `DNA1(site!?~sdsb,h2ax~u) + ATM(state~1,h2ax)  -> DNA1(site!?~sdsb,h2ax~p) + ATM(state~1,h2ax)` | Transforms ATM, DNA1 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1681 | `Unlabeled` | one-way | ATM, DNA2 | `kh2axp1` | internal-state conversion/modification | `DNA2(site!?~sdsb,h2ax~u) + ATM(state~2,h2ax)  -> DNA2(site!?~sdsb,h2ax~p) + ATM(state~2,h2ax)` | Transforms ATM, DNA2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1682 | `Unlabeled` | one-way | ATM, DNA3 | `kh2axp1` | internal-state conversion/modification | `DNA3(site!?~sdsb,h2ax~u) + ATM(state~3,h2ax)  -> DNA3(site!?~sdsb,h2ax~p) + ATM(state~3,h2ax)` | Transforms ATM, DNA3 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1683 | `Unlabeled` | one-way | ATM, DNA4 | `kh2axp1` | internal-state conversion/modification | `DNA4(site!?~sdsb,h2ax~u) + ATM(state~4,h2ax)  -> DNA4(site!?~sdsb,h2ax~p) + ATM(state~4,h2ax)` | Transforms ATM, DNA4 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1684 | `Unlabeled` | one-way | ATM, DNA5 | `kh2axp1` | internal-state conversion/modification | `DNA5(site!?~sdsb,h2ax~u) + ATM(state~5,h2ax)  -> DNA5(site!?~sdsb,h2ax~p) + ATM(state~5,h2ax)` | Transforms ATM, DNA5 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1685 | `Unlabeled` | one-way | ATM, DNA6 | `kh2axp1` | internal-state conversion/modification | `DNA6(site!?~sdsb,h2ax~u) + ATM(state~6,h2ax)  -> DNA6(site!?~sdsb,h2ax~p) + ATM(state~6,h2ax)` | Transforms ATM, DNA6 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1686 | `Unlabeled` | one-way | ATM, DNA7 | `kh2axp1` | internal-state conversion/modification | `DNA7(site!?~sdsb,h2ax~u) + ATM(state~7,h2ax)  -> DNA7(site!?~sdsb,h2ax~p) + ATM(state~7,h2ax)` | Transforms ATM, DNA7 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1687 | `Unlabeled` | one-way | ATM, DNA8 | `kh2axp1` | internal-state conversion/modification | `DNA8(site!?~sdsb,h2ax~u) + ATM(state~8,h2ax)  -> DNA8(site!?~sdsb,h2ax~p) + ATM(state~8,h2ax)` | Transforms ATM, DNA8 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1688 | `Unlabeled` | one-way | ATM, DNA9 | `kh2axp1` | internal-state conversion/modification | `DNA9(site!?~sdsb,h2ax~u) + ATM(state~9,h2ax)  -> DNA9(site!?~sdsb,h2ax~p) + ATM(state~9,h2ax)` | Transforms ATM, DNA9 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1689 | `Unlabeled` | one-way | ATM, DNA10 | `kh2axp1` | internal-state conversion/modification | `DNA10(site!?~sdsb,h2ax~u) + ATM(state~10,h2ax)  -> DNA10(site!?~sdsb,h2ax~p) + ATM(state~10,h2ax)` | Transforms ATM, DNA10 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1690 | `Unlabeled` | one-way | ATM, DNA11 | `kh2axp1` | internal-state conversion/modification | `DNA11(site!?~sdsb,h2ax~u) + ATM(state~11,h2ax)  -> DNA11(site!?~sdsb,h2ax~p) + ATM(state~11,h2ax)` | Transforms ATM, DNA11 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1691 | `Unlabeled` | one-way | ATM, DNA12 | `kh2axp1` | internal-state conversion/modification | `DNA12(site!?~sdsb,h2ax~u) + ATM(state~12,h2ax)  -> DNA12(site!?~sdsb,h2ax~p) + ATM(state~12,h2ax)` | Transforms ATM, DNA12 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1692 | `Unlabeled` | one-way | ATM, DNA13 | `kh2axp1` | internal-state conversion/modification | `DNA13(site!?~sdsb,h2ax~u) + ATM(state~13,h2ax)  -> DNA13(site!?~sdsb,h2ax~p) + ATM(state~13,h2ax)` | Transforms ATM, DNA13 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1693 | `Unlabeled` | one-way | ATM, DNA14 | `kh2axp1` | internal-state conversion/modification | `DNA14(site!?~sdsb,h2ax~u) + ATM(state~14,h2ax)  -> DNA14(site!?~sdsb,h2ax~p) + ATM(state~14,h2ax)` | Transforms ATM, DNA14 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1694 | `Unlabeled` | one-way | ATM, DNA15 | `kh2axp1` | internal-state conversion/modification | `DNA15(site!?~sdsb,h2ax~u) + ATM(state~15,h2ax)  -> DNA15(site!?~sdsb,h2ax~p) + ATM(state~15,h2ax)` | Transforms ATM, DNA15 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1695 | `Unlabeled` | one-way | ATM, DNA16 | `kh2axp1` | internal-state conversion/modification | `DNA16(site!?~sdsb,h2ax~u) + ATM(state~16,h2ax)  -> DNA16(site!?~sdsb,h2ax~p) + ATM(state~16,h2ax)` | Transforms ATM, DNA16 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1696 | `Unlabeled` | one-way | ATM, DNA17 | `kh2axp1` | internal-state conversion/modification | `DNA17(site!?~sdsb,h2ax~u) + ATM(state~17,h2ax)  -> DNA17(site!?~sdsb,h2ax~p) + ATM(state~17,h2ax)` | Transforms ATM, DNA17 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1697 | `Unlabeled` | one-way | ATM, DNA18 | `kh2axp1` | internal-state conversion/modification | `DNA18(site!?~sdsb,h2ax~u) + ATM(state~18,h2ax)  -> DNA18(site!?~sdsb,h2ax~p) + ATM(state~18,h2ax)` | Transforms ATM, DNA18 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1698 | `Unlabeled` | one-way | ATM, DNA19 | `kh2axp1` | internal-state conversion/modification | `DNA19(site!?~sdsb,h2ax~u) + ATM(state~19,h2ax)  -> DNA19(site!?~sdsb,h2ax~p) + ATM(state~19,h2ax)` | Transforms ATM, DNA19 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1699 | `Unlabeled` | one-way | ATM, DNA20 | `kh2axp1` | internal-state conversion/modification | `DNA20(site!?~sdsb,h2ax~u) + ATM(state~20,h2ax)  -> DNA20(site!?~sdsb,h2ax~p) + ATM(state~20,h2ax)` | Transforms ATM, DNA20 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1700 | `Unlabeled` | one-way | ATM, DNA21 | `kh2axp1` | internal-state conversion/modification | `DNA21(site!?~sdsb,h2ax~u) + ATM(state~21,h2ax)  -> DNA21(site!?~sdsb,h2ax~p) + ATM(state~21,h2ax)` | Transforms ATM, DNA21 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1701 | `Unlabeled` | one-way | ATM, DNA22 | `kh2axp1` | internal-state conversion/modification | `DNA22(site!?~sdsb,h2ax~u) + ATM(state~22,h2ax)  -> DNA22(site!?~sdsb,h2ax~p) + ATM(state~22,h2ax)` | Transforms ATM, DNA22 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1702 | `Unlabeled` | one-way | ATM, DNA23 | `kh2axp1` | internal-state conversion/modification | `DNA23(site!?~sdsb,h2ax~u) + ATM(state~23,h2ax)  -> DNA23(site!?~sdsb,h2ax~p) + ATM(state~23,h2ax)` | Transforms ATM, DNA23 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1703 | `Unlabeled` | one-way | ATM, DNA24 | `kh2axp1` | internal-state conversion/modification | `DNA24(site!?~sdsb,h2ax~u) + ATM(state~24,h2ax)  -> DNA24(site!?~sdsb,h2ax~p) + ATM(state~24,h2ax)` | Transforms ATM, DNA24 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1704 | `Unlabeled` | one-way | ATM, DNA25 | `kh2axp1` | internal-state conversion/modification | `DNA25(site!?~sdsb,h2ax~u) + ATM(state~25,h2ax)  -> DNA25(site!?~sdsb,h2ax~p) + ATM(state~25,h2ax)` | Transforms ATM, DNA25 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1705 | `Unlabeled` | one-way | ATM, DNA26 | `kh2axp1` | internal-state conversion/modification | `DNA26(site!?~sdsb,h2ax~u) + ATM(state~26,h2ax)  -> DNA26(site!?~sdsb,h2ax~p) + ATM(state~26,h2ax)` | Transforms ATM, DNA26 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1706 | `Unlabeled` | one-way | ATM, DNA27 | `kh2axp1` | internal-state conversion/modification | `DNA27(site!?~sdsb,h2ax~u) + ATM(state~27,h2ax)  -> DNA27(site!?~sdsb,h2ax~p) + ATM(state~27,h2ax)` | Transforms ATM, DNA27 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1707 | `Unlabeled` | one-way | ATM, DNA28 | `kh2axp1` | internal-state conversion/modification | `DNA28(site!?~sdsb,h2ax~u) + ATM(state~28,h2ax)  -> DNA28(site!?~sdsb,h2ax~p) + ATM(state~28,h2ax)` | Transforms ATM, DNA28 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1708 | `Unlabeled` | one-way | ATM, DNA29 | `kh2axp1` | internal-state conversion/modification | `DNA29(site!?~sdsb,h2ax~u) + ATM(state~29,h2ax)  -> DNA29(site!?~sdsb,h2ax~p) + ATM(state~29,h2ax)` | Transforms ATM, DNA29 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1709 | `Unlabeled` | one-way | ATM, DNA30 | `kh2axp1` | internal-state conversion/modification | `DNA30(site!?~sdsb,h2ax~u) + ATM(state~30,h2ax)  -> DNA30(site!?~sdsb,h2ax~p) + ATM(state~30,h2ax)` | Transforms ATM, DNA30 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1710 | `Unlabeled` | one-way | ATM, DNA31 | `kh2axp1` | internal-state conversion/modification | `DNA31(site!?~sdsb,h2ax~u) + ATM(state~31,h2ax)  -> DNA31(site!?~sdsb,h2ax~p) + ATM(state~31,h2ax)` | Transforms ATM, DNA31 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1711 | `Unlabeled` | one-way | ATM, DNA32 | `kh2axp1` | internal-state conversion/modification | `DNA32(site!?~sdsb,h2ax~u) + ATM(state~32,h2ax)  -> DNA32(site!?~sdsb,h2ax~p) + ATM(state~32,h2ax)` | Transforms ATM, DNA32 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1712 | `Unlabeled` | one-way | ATM, DNA33 | `kh2axp1` | internal-state conversion/modification | `DNA33(site!?~sdsb,h2ax~u) + ATM(state~33,h2ax)  -> DNA33(site!?~sdsb,h2ax~p) + ATM(state~33,h2ax)` | Transforms ATM, DNA33 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1713 | `Unlabeled` | one-way | ATM, DNA34 | `kh2axp1` | internal-state conversion/modification | `DNA34(site!?~sdsb,h2ax~u) + ATM(state~34,h2ax)  -> DNA34(site!?~sdsb,h2ax~p) + ATM(state~34,h2ax)` | Transforms ATM, DNA34 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1714 | `Unlabeled` | one-way | ATM, DNA35 | `kh2axp1` | internal-state conversion/modification | `DNA35(site!?~sdsb,h2ax~u) + ATM(state~35,h2ax)  -> DNA35(site!?~sdsb,h2ax~p) + ATM(state~35,h2ax)` | Transforms ATM, DNA35 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1715 | `Unlabeled` | one-way | ATM, DNA36 | `kh2axp1` | internal-state conversion/modification | `DNA36(site!?~sdsb,h2ax~u) + ATM(state~36,h2ax)  -> DNA36(site!?~sdsb,h2ax~p) + ATM(state~36,h2ax)` | Transforms ATM, DNA36 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1716 | `Unlabeled` | one-way | ATM, DNA37 | `kh2axp1` | internal-state conversion/modification | `DNA37(site!?~sdsb,h2ax~u) + ATM(state~37,h2ax)  -> DNA37(site!?~sdsb,h2ax~p) + ATM(state~37,h2ax)` | Transforms ATM, DNA37 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1717 | `Unlabeled` | one-way | ATM, DNA38 | `kh2axp1` | internal-state conversion/modification | `DNA38(site!?~sdsb,h2ax~u) + ATM(state~38,h2ax)  -> DNA38(site!?~sdsb,h2ax~p) + ATM(state~38,h2ax)` | Transforms ATM, DNA38 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1718 | `Unlabeled` | one-way | ATM, DNA39 | `kh2axp1` | internal-state conversion/modification | `DNA39(site!?~sdsb,h2ax~u) + ATM(state~39,h2ax)  -> DNA39(site!?~sdsb,h2ax~p) + ATM(state~39,h2ax)` | Transforms ATM, DNA39 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1719 | `Unlabeled` | one-way | ATM, DNA40 | `kh2axp1` | internal-state conversion/modification | `DNA40(site!?~sdsb,h2ax~u) + ATM(state~40,h2ax)  -> DNA40(site!?~sdsb,h2ax~p) + ATM(state~40,h2ax)` | Transforms ATM, DNA40 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1720 | `Unlabeled` | one-way | ATM, DNA41 | `kh2axp1` | internal-state conversion/modification | `DNA41(site!?~sdsb,h2ax~u) + ATM(state~41,h2ax)  -> DNA41(site!?~sdsb,h2ax~p) + ATM(state~41,h2ax)` | Transforms ATM, DNA41 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1721 | `Unlabeled` | one-way | ATM, DNA42 | `kh2axp1` | internal-state conversion/modification | `DNA42(site!?~sdsb,h2ax~u) + ATM(state~42,h2ax)  -> DNA42(site!?~sdsb,h2ax~p) + ATM(state~42,h2ax)` | Transforms ATM, DNA42 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1722 | `Unlabeled` | one-way | ATM, DNA43 | `kh2axp1` | internal-state conversion/modification | `DNA43(site!?~sdsb,h2ax~u) + ATM(state~43,h2ax)  -> DNA43(site!?~sdsb,h2ax~p) + ATM(state~43,h2ax)` | Transforms ATM, DNA43 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1723 | `Unlabeled` | one-way | ATM, DNA44 | `kh2axp1` | internal-state conversion/modification | `DNA44(site!?~sdsb,h2ax~u) + ATM(state~44,h2ax)  -> DNA44(site!?~sdsb,h2ax~p) + ATM(state~44,h2ax)` | Transforms ATM, DNA44 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1724 | `Unlabeled` | one-way | ATM, DNA45 | `kh2axp1` | internal-state conversion/modification | `DNA45(site!?~sdsb,h2ax~u) + ATM(state~45,h2ax)  -> DNA45(site!?~sdsb,h2ax~p) + ATM(state~45,h2ax)` | Transforms ATM, DNA45 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1725 | `Unlabeled` | one-way | ATM, DNA46 | `kh2axp1` | internal-state conversion/modification | `DNA46(site!?~sdsb,h2ax~u) + ATM(state~46,h2ax)  -> DNA46(site!?~sdsb,h2ax~p) + ATM(state~46,h2ax)` | Transforms ATM, DNA46 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1726 | `Unlabeled` | one-way | ATM, DNA47 | `kh2axp1` | internal-state conversion/modification | `DNA47(site!?~sdsb,h2ax~u) + ATM(state~47,h2ax)  -> DNA47(site!?~sdsb,h2ax~p) + ATM(state~47,h2ax)` | Transforms ATM, DNA47 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1727 | `Unlabeled` | one-way | ATM, DNA48 | `kh2axp1` | internal-state conversion/modification | `DNA48(site!?~sdsb,h2ax~u) + ATM(state~48,h2ax)  -> DNA48(site!?~sdsb,h2ax~p) + ATM(state~48,h2ax)` | Transforms ATM, DNA48 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1728 | `Unlabeled` | one-way | ATM, DNA49 | `kh2axp1` | internal-state conversion/modification | `DNA49(site!?~sdsb,h2ax~u) + ATM(state~49,h2ax)  -> DNA49(site!?~sdsb,h2ax~p) + ATM(state~49,h2ax)` | Transforms ATM, DNA49 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1729 | `Unlabeled` | one-way | ATM, DNA50 | `kh2axp1` | internal-state conversion/modification | `DNA50(site!?~sdsb,h2ax~u) + ATM(state~50,h2ax)  -> DNA50(site!?~sdsb,h2ax~p) + ATM(state~50,h2ax)` | Transforms ATM, DNA50 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1730 | `Unlabeled` | one-way | ATM, DNA1 | `kh2axp1` | internal-state conversion/modification | `DNA1(site!?~cdsb,h2ax~u) + ATM(state~1,h2ax)  -> DNA1(site!?~cdsb,h2ax~p) + ATM(state~1,h2ax)` | Transforms ATM, DNA1 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1731 | `Unlabeled` | one-way | ATM, DNA2 | `kh2axp1` | internal-state conversion/modification | `DNA2(site!?~cdsb,h2ax~u) + ATM(state~2,h2ax)  -> DNA2(site!?~cdsb,h2ax~p) + ATM(state~2,h2ax)` | Transforms ATM, DNA2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1732 | `Unlabeled` | one-way | ATM, DNA3 | `kh2axp1` | internal-state conversion/modification | `DNA3(site!?~cdsb,h2ax~u) + ATM(state~3,h2ax)  -> DNA3(site!?~cdsb,h2ax~p) + ATM(state~3,h2ax)` | Transforms ATM, DNA3 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1733 | `Unlabeled` | one-way | ATM, DNA4 | `kh2axp1` | internal-state conversion/modification | `DNA4(site!?~cdsb,h2ax~u) + ATM(state~4,h2ax)  -> DNA4(site!?~cdsb,h2ax~p) + ATM(state~4,h2ax)` | Transforms ATM, DNA4 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1734 | `Unlabeled` | one-way | ATM, DNA5 | `kh2axp1` | internal-state conversion/modification | `DNA5(site!?~cdsb,h2ax~u) + ATM(state~5,h2ax)  -> DNA5(site!?~cdsb,h2ax~p) + ATM(state~5,h2ax)` | Transforms ATM, DNA5 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1735 | `Unlabeled` | one-way | ATM, DNA6 | `kh2axp1` | internal-state conversion/modification | `DNA6(site!?~cdsb,h2ax~u) + ATM(state~6,h2ax)  -> DNA6(site!?~cdsb,h2ax~p) + ATM(state~6,h2ax)` | Transforms ATM, DNA6 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1736 | `Unlabeled` | one-way | ATM, DNA7 | `kh2axp1` | internal-state conversion/modification | `DNA7(site!?~cdsb,h2ax~u) + ATM(state~7,h2ax)  -> DNA7(site!?~cdsb,h2ax~p) + ATM(state~7,h2ax)` | Transforms ATM, DNA7 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1737 | `Unlabeled` | one-way | ATM, DNA8 | `kh2axp1` | internal-state conversion/modification | `DNA8(site!?~cdsb,h2ax~u) + ATM(state~8,h2ax)  -> DNA8(site!?~cdsb,h2ax~p) + ATM(state~8,h2ax)` | Transforms ATM, DNA8 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1738 | `Unlabeled` | one-way | ATM, DNA9 | `kh2axp1` | internal-state conversion/modification | `DNA9(site!?~cdsb,h2ax~u) + ATM(state~9,h2ax)  -> DNA9(site!?~cdsb,h2ax~p) + ATM(state~9,h2ax)` | Transforms ATM, DNA9 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1739 | `Unlabeled` | one-way | ATM, DNA10 | `kh2axp1` | internal-state conversion/modification | `DNA10(site!?~cdsb,h2ax~u) + ATM(state~10,h2ax)  -> DNA10(site!?~cdsb,h2ax~p) + ATM(state~10,h2ax)` | Transforms ATM, DNA10 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1740 | `Unlabeled` | one-way | ATM, DNA11 | `kh2axp1` | internal-state conversion/modification | `DNA11(site!?~cdsb,h2ax~u) + ATM(state~11,h2ax)  -> DNA11(site!?~cdsb,h2ax~p) + ATM(state~11,h2ax)` | Transforms ATM, DNA11 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1741 | `Unlabeled` | one-way | ATM, DNA12 | `kh2axp1` | internal-state conversion/modification | `DNA12(site!?~cdsb,h2ax~u) + ATM(state~12,h2ax)  -> DNA12(site!?~cdsb,h2ax~p) + ATM(state~12,h2ax)` | Transforms ATM, DNA12 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1742 | `Unlabeled` | one-way | ATM, DNA13 | `kh2axp1` | internal-state conversion/modification | `DNA13(site!?~cdsb,h2ax~u) + ATM(state~13,h2ax)  -> DNA13(site!?~cdsb,h2ax~p) + ATM(state~13,h2ax)` | Transforms ATM, DNA13 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1743 | `Unlabeled` | one-way | ATM, DNA14 | `kh2axp1` | internal-state conversion/modification | `DNA14(site!?~cdsb,h2ax~u) + ATM(state~14,h2ax)  -> DNA14(site!?~cdsb,h2ax~p) + ATM(state~14,h2ax)` | Transforms ATM, DNA14 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1744 | `Unlabeled` | one-way | ATM, DNA15 | `kh2axp1` | internal-state conversion/modification | `DNA15(site!?~cdsb,h2ax~u) + ATM(state~15,h2ax)  -> DNA15(site!?~cdsb,h2ax~p) + ATM(state~15,h2ax)` | Transforms ATM, DNA15 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1745 | `Unlabeled` | one-way | ATM, DNA16 | `kh2axp1` | internal-state conversion/modification | `DNA16(site!?~cdsb,h2ax~u) + ATM(state~16,h2ax)  -> DNA16(site!?~cdsb,h2ax~p) + ATM(state~16,h2ax)` | Transforms ATM, DNA16 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1746 | `Unlabeled` | one-way | ATM, DNA17 | `kh2axp1` | internal-state conversion/modification | `DNA17(site!?~cdsb,h2ax~u) + ATM(state~17,h2ax)  -> DNA17(site!?~cdsb,h2ax~p) + ATM(state~17,h2ax)` | Transforms ATM, DNA17 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1747 | `Unlabeled` | one-way | ATM, DNA18 | `kh2axp1` | internal-state conversion/modification | `DNA18(site!?~cdsb,h2ax~u) + ATM(state~18,h2ax)  -> DNA18(site!?~cdsb,h2ax~p) + ATM(state~18,h2ax)` | Transforms ATM, DNA18 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1748 | `Unlabeled` | one-way | ATM, DNA19 | `kh2axp1` | internal-state conversion/modification | `DNA19(site!?~cdsb,h2ax~u) + ATM(state~19,h2ax)  -> DNA19(site!?~cdsb,h2ax~p) + ATM(state~19,h2ax)` | Transforms ATM, DNA19 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1749 | `Unlabeled` | one-way | ATM, DNA20 | `kh2axp1` | internal-state conversion/modification | `DNA20(site!?~cdsb,h2ax~u) + ATM(state~20,h2ax)  -> DNA20(site!?~cdsb,h2ax~p) + ATM(state~20,h2ax)` | Transforms ATM, DNA20 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1750 | `Unlabeled` | one-way | ATM, DNA21 | `kh2axp1` | internal-state conversion/modification | `DNA21(site!?~cdsb,h2ax~u) + ATM(state~21,h2ax)  -> DNA21(site!?~cdsb,h2ax~p) + ATM(state~21,h2ax)` | Transforms ATM, DNA21 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

### Rules 1751-2000

| # | Rule label/name | Direction | Participants | Rate/expression | Modeled change | Rule pattern | Technical meaning |
| ---: | --- | --- | --- | --- | --- | --- | --- |

| 1751 | `Unlabeled` | one-way | ATM, DNA22 | `kh2axp1` | internal-state conversion/modification | `DNA22(site!?~cdsb,h2ax~u) + ATM(state~22,h2ax)  -> DNA22(site!?~cdsb,h2ax~p) + ATM(state~22,h2ax)` | Transforms ATM, DNA22 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1752 | `Unlabeled` | one-way | ATM, DNA23 | `kh2axp1` | internal-state conversion/modification | `DNA23(site!?~cdsb,h2ax~u) + ATM(state~23,h2ax)  -> DNA23(site!?~cdsb,h2ax~p) + ATM(state~23,h2ax)` | Transforms ATM, DNA23 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1753 | `Unlabeled` | one-way | ATM, DNA24 | `kh2axp1` | internal-state conversion/modification | `DNA24(site!?~cdsb,h2ax~u) + ATM(state~24,h2ax)  -> DNA24(site!?~cdsb,h2ax~p) + ATM(state~24,h2ax)` | Transforms ATM, DNA24 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1754 | `Unlabeled` | one-way | ATM, DNA25 | `kh2axp1` | internal-state conversion/modification | `DNA25(site!?~cdsb,h2ax~u) + ATM(state~25,h2ax)  -> DNA25(site!?~cdsb,h2ax~p) + ATM(state~25,h2ax)` | Transforms ATM, DNA25 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1755 | `Unlabeled` | one-way | ATM, DNA26 | `kh2axp1` | internal-state conversion/modification | `DNA26(site!?~cdsb,h2ax~u) + ATM(state~26,h2ax)  -> DNA26(site!?~cdsb,h2ax~p) + ATM(state~26,h2ax)` | Transforms ATM, DNA26 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1756 | `Unlabeled` | one-way | ATM, DNA27 | `kh2axp1` | internal-state conversion/modification | `DNA27(site!?~cdsb,h2ax~u) + ATM(state~27,h2ax)  -> DNA27(site!?~cdsb,h2ax~p) + ATM(state~27,h2ax)` | Transforms ATM, DNA27 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1757 | `Unlabeled` | one-way | ATM, DNA28 | `kh2axp1` | internal-state conversion/modification | `DNA28(site!?~cdsb,h2ax~u) + ATM(state~28,h2ax)  -> DNA28(site!?~cdsb,h2ax~p) + ATM(state~28,h2ax)` | Transforms ATM, DNA28 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1758 | `Unlabeled` | one-way | ATM, DNA29 | `kh2axp1` | internal-state conversion/modification | `DNA29(site!?~cdsb,h2ax~u) + ATM(state~29,h2ax)  -> DNA29(site!?~cdsb,h2ax~p) + ATM(state~29,h2ax)` | Transforms ATM, DNA29 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1759 | `Unlabeled` | one-way | ATM, DNA30 | `kh2axp1` | internal-state conversion/modification | `DNA30(site!?~cdsb,h2ax~u) + ATM(state~30,h2ax)  -> DNA30(site!?~cdsb,h2ax~p) + ATM(state~30,h2ax)` | Transforms ATM, DNA30 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1760 | `Unlabeled` | one-way | ATM, DNA31 | `kh2axp1` | internal-state conversion/modification | `DNA31(site!?~cdsb,h2ax~u) + ATM(state~31,h2ax)  -> DNA31(site!?~cdsb,h2ax~p) + ATM(state~31,h2ax)` | Transforms ATM, DNA31 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1761 | `Unlabeled` | one-way | ATM, DNA32 | `kh2axp1` | internal-state conversion/modification | `DNA32(site!?~cdsb,h2ax~u) + ATM(state~32,h2ax)  -> DNA32(site!?~cdsb,h2ax~p) + ATM(state~32,h2ax)` | Transforms ATM, DNA32 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1762 | `Unlabeled` | one-way | ATM, DNA33 | `kh2axp1` | internal-state conversion/modification | `DNA33(site!?~cdsb,h2ax~u) + ATM(state~33,h2ax)  -> DNA33(site!?~cdsb,h2ax~p) + ATM(state~33,h2ax)` | Transforms ATM, DNA33 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1763 | `Unlabeled` | one-way | ATM, DNA34 | `kh2axp1` | internal-state conversion/modification | `DNA34(site!?~cdsb,h2ax~u) + ATM(state~34,h2ax)  -> DNA34(site!?~cdsb,h2ax~p) + ATM(state~34,h2ax)` | Transforms ATM, DNA34 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1764 | `Unlabeled` | one-way | ATM, DNA35 | `kh2axp1` | internal-state conversion/modification | `DNA35(site!?~cdsb,h2ax~u) + ATM(state~35,h2ax)  -> DNA35(site!?~cdsb,h2ax~p) + ATM(state~35,h2ax)` | Transforms ATM, DNA35 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1765 | `Unlabeled` | one-way | ATM, DNA36 | `kh2axp1` | internal-state conversion/modification | `DNA36(site!?~cdsb,h2ax~u) + ATM(state~36,h2ax)  -> DNA36(site!?~cdsb,h2ax~p) + ATM(state~36,h2ax)` | Transforms ATM, DNA36 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1766 | `Unlabeled` | one-way | ATM, DNA37 | `kh2axp1` | internal-state conversion/modification | `DNA37(site!?~cdsb,h2ax~u) + ATM(state~37,h2ax)  -> DNA37(site!?~cdsb,h2ax~p) + ATM(state~37,h2ax)` | Transforms ATM, DNA37 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1767 | `Unlabeled` | one-way | ATM, DNA38 | `kh2axp1` | internal-state conversion/modification | `DNA38(site!?~cdsb,h2ax~u) + ATM(state~38,h2ax)  -> DNA38(site!?~cdsb,h2ax~p) + ATM(state~38,h2ax)` | Transforms ATM, DNA38 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1768 | `Unlabeled` | one-way | ATM, DNA39 | `kh2axp1` | internal-state conversion/modification | `DNA39(site!?~cdsb,h2ax~u) + ATM(state~39,h2ax)  -> DNA39(site!?~cdsb,h2ax~p) + ATM(state~39,h2ax)` | Transforms ATM, DNA39 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1769 | `Unlabeled` | one-way | ATM, DNA40 | `kh2axp1` | internal-state conversion/modification | `DNA40(site!?~cdsb,h2ax~u) + ATM(state~40,h2ax)  -> DNA40(site!?~cdsb,h2ax~p) + ATM(state~40,h2ax)` | Transforms ATM, DNA40 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1770 | `Unlabeled` | one-way | ATM, DNA41 | `kh2axp1` | internal-state conversion/modification | `DNA41(site!?~cdsb,h2ax~u) + ATM(state~41,h2ax)  -> DNA41(site!?~cdsb,h2ax~p) + ATM(state~41,h2ax)` | Transforms ATM, DNA41 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1771 | `Unlabeled` | one-way | ATM, DNA42 | `kh2axp1` | internal-state conversion/modification | `DNA42(site!?~cdsb,h2ax~u) + ATM(state~42,h2ax)  -> DNA42(site!?~cdsb,h2ax~p) + ATM(state~42,h2ax)` | Transforms ATM, DNA42 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1772 | `Unlabeled` | one-way | ATM, DNA43 | `kh2axp1` | internal-state conversion/modification | `DNA43(site!?~cdsb,h2ax~u) + ATM(state~43,h2ax)  -> DNA43(site!?~cdsb,h2ax~p) + ATM(state~43,h2ax)` | Transforms ATM, DNA43 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1773 | `Unlabeled` | one-way | ATM, DNA44 | `kh2axp1` | internal-state conversion/modification | `DNA44(site!?~cdsb,h2ax~u) + ATM(state~44,h2ax)  -> DNA44(site!?~cdsb,h2ax~p) + ATM(state~44,h2ax)` | Transforms ATM, DNA44 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1774 | `Unlabeled` | one-way | ATM, DNA45 | `kh2axp1` | internal-state conversion/modification | `DNA45(site!?~cdsb,h2ax~u) + ATM(state~45,h2ax)  -> DNA45(site!?~cdsb,h2ax~p) + ATM(state~45,h2ax)` | Transforms ATM, DNA45 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1775 | `Unlabeled` | one-way | ATM, DNA46 | `kh2axp1` | internal-state conversion/modification | `DNA46(site!?~cdsb,h2ax~u) + ATM(state~46,h2ax)  -> DNA46(site!?~cdsb,h2ax~p) + ATM(state~46,h2ax)` | Transforms ATM, DNA46 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1776 | `Unlabeled` | one-way | ATM, DNA47 | `kh2axp1` | internal-state conversion/modification | `DNA47(site!?~cdsb,h2ax~u) + ATM(state~47,h2ax)  -> DNA47(site!?~cdsb,h2ax~p) + ATM(state~47,h2ax)` | Transforms ATM, DNA47 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1777 | `Unlabeled` | one-way | ATM, DNA48 | `kh2axp1` | internal-state conversion/modification | `DNA48(site!?~cdsb,h2ax~u) + ATM(state~48,h2ax)  -> DNA48(site!?~cdsb,h2ax~p) + ATM(state~48,h2ax)` | Transforms ATM, DNA48 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1778 | `Unlabeled` | one-way | ATM, DNA49 | `kh2axp1` | internal-state conversion/modification | `DNA49(site!?~cdsb,h2ax~u) + ATM(state~49,h2ax)  -> DNA49(site!?~cdsb,h2ax~p) + ATM(state~49,h2ax)` | Transforms ATM, DNA49 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1779 | `Unlabeled` | one-way | ATM, DNA50 | `kh2axp1` | internal-state conversion/modification | `DNA50(site!?~cdsb,h2ax~u) + ATM(state~50,h2ax)  -> DNA50(site!?~cdsb,h2ax~p) + ATM(state~50,h2ax)` | Transforms ATM, DNA50 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1780 | `Unlabeled` | one-way | DNA1, DNAPKcs, Ku | `kh2axp2` | internal-state conversion/modification | `DNA1(site!1~sdsb,h2ax~u).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)  -> DNA1(site!1~sdsb,h2ax~p).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA1, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1781 | `Unlabeled` | one-way | DNA2, DNAPKcs, Ku | `kh2axp2` | internal-state conversion/modification | `DNA2(site!1~sdsb,h2ax~u).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)  -> DNA2(site!1~sdsb,h2ax~p).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA2, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1782 | `Unlabeled` | one-way | DNA3, DNAPKcs, Ku | `kh2axp2` | internal-state conversion/modification | `DNA3(site!1~sdsb,h2ax~u).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)  -> DNA3(site!1~sdsb,h2ax~p).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA3, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1783 | `Unlabeled` | one-way | DNA4, DNAPKcs, Ku | `kh2axp2` | internal-state conversion/modification | `DNA4(site!1~sdsb,h2ax~u).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)  -> DNA4(site!1~sdsb,h2ax~p).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA4, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1784 | `Unlabeled` | one-way | DNA5, DNAPKcs, Ku | `kh2axp2` | internal-state conversion/modification | `DNA5(site!1~sdsb,h2ax~u).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)  -> DNA5(site!1~sdsb,h2ax~p).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA5, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1785 | `Unlabeled` | one-way | DNA6, DNAPKcs, Ku | `kh2axp2` | internal-state conversion/modification | `DNA6(site!1~sdsb,h2ax~u).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)  -> DNA6(site!1~sdsb,h2ax~p).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA6, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1786 | `Unlabeled` | one-way | DNA7, DNAPKcs, Ku | `kh2axp2` | internal-state conversion/modification | `DNA7(site!1~sdsb,h2ax~u).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)  -> DNA7(site!1~sdsb,h2ax~p).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA7, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1787 | `Unlabeled` | one-way | DNA8, DNAPKcs, Ku | `kh2axp2` | internal-state conversion/modification | `DNA8(site!1~sdsb,h2ax~u).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)  -> DNA8(site!1~sdsb,h2ax~p).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA8, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1788 | `Unlabeled` | one-way | DNA9, DNAPKcs, Ku | `kh2axp2` | internal-state conversion/modification | `DNA9(site!1~sdsb,h2ax~u).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)  -> DNA9(site!1~sdsb,h2ax~p).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA9, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1789 | `Unlabeled` | one-way | DNA10, DNAPKcs, Ku | `kh2axp2` | internal-state conversion/modification | `DNA10(site!1~sdsb,h2ax~u).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)  -> DNA10(site!1~sdsb,h2ax~p).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA10, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1790 | `Unlabeled` | one-way | DNA11, DNAPKcs, Ku | `kh2axp2` | internal-state conversion/modification | `DNA11(site!1~sdsb,h2ax~u).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)  -> DNA11(site!1~sdsb,h2ax~p).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA11, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1791 | `Unlabeled` | one-way | DNA12, DNAPKcs, Ku | `kh2axp2` | internal-state conversion/modification | `DNA12(site!1~sdsb,h2ax~u).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)  -> DNA12(site!1~sdsb,h2ax~p).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA12, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1792 | `Unlabeled` | one-way | DNA13, DNAPKcs, Ku | `kh2axp2` | internal-state conversion/modification | `DNA13(site!1~sdsb,h2ax~u).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)  -> DNA13(site!1~sdsb,h2ax~p).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA13, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1793 | `Unlabeled` | one-way | DNA14, DNAPKcs, Ku | `kh2axp2` | internal-state conversion/modification | `DNA14(site!1~sdsb,h2ax~u).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)  -> DNA14(site!1~sdsb,h2ax~p).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA14, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1794 | `Unlabeled` | one-way | DNA15, DNAPKcs, Ku | `kh2axp2` | internal-state conversion/modification | `DNA15(site!1~sdsb,h2ax~u).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)  -> DNA15(site!1~sdsb,h2ax~p).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA15, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1795 | `Unlabeled` | one-way | DNA16, DNAPKcs, Ku | `kh2axp2` | internal-state conversion/modification | `DNA16(site!1~sdsb,h2ax~u).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)  -> DNA16(site!1~sdsb,h2ax~p).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA16, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1796 | `Unlabeled` | one-way | DNA17, DNAPKcs, Ku | `kh2axp2` | internal-state conversion/modification | `DNA17(site!1~sdsb,h2ax~u).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)  -> DNA17(site!1~sdsb,h2ax~p).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA17, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1797 | `Unlabeled` | one-way | DNA18, DNAPKcs, Ku | `kh2axp2` | internal-state conversion/modification | `DNA18(site!1~sdsb,h2ax~u).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)  -> DNA18(site!1~sdsb,h2ax~p).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA18, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1798 | `Unlabeled` | one-way | DNA19, DNAPKcs, Ku | `kh2axp2` | internal-state conversion/modification | `DNA19(site!1~sdsb,h2ax~u).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)  -> DNA19(site!1~sdsb,h2ax~p).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA19, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1799 | `Unlabeled` | one-way | DNA20, DNAPKcs, Ku | `kh2axp2` | internal-state conversion/modification | `DNA20(site!1~sdsb,h2ax~u).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)  -> DNA20(site!1~sdsb,h2ax~p).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA20, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1800 | `Unlabeled` | one-way | DNA21, DNAPKcs, Ku | `kh2axp2` | internal-state conversion/modification | `DNA21(site!1~sdsb,h2ax~u).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)  -> DNA21(site!1~sdsb,h2ax~p).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA21, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1801 | `Unlabeled` | one-way | DNA22, DNAPKcs, Ku | `kh2axp2` | internal-state conversion/modification | `DNA22(site!1~sdsb,h2ax~u).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)  -> DNA22(site!1~sdsb,h2ax~p).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA22, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1802 | `Unlabeled` | one-way | DNA23, DNAPKcs, Ku | `kh2axp2` | internal-state conversion/modification | `DNA23(site!1~sdsb,h2ax~u).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)  -> DNA23(site!1~sdsb,h2ax~p).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA23, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1803 | `Unlabeled` | one-way | DNA24, DNAPKcs, Ku | `kh2axp2` | internal-state conversion/modification | `DNA24(site!1~sdsb,h2ax~u).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)  -> DNA24(site!1~sdsb,h2ax~p).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA24, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1804 | `Unlabeled` | one-way | DNA25, DNAPKcs, Ku | `kh2axp2` | internal-state conversion/modification | `DNA25(site!1~sdsb,h2ax~u).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)  -> DNA25(site!1~sdsb,h2ax~p).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA25, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1805 | `Unlabeled` | one-way | DNA26, DNAPKcs, Ku | `kh2axp2` | internal-state conversion/modification | `DNA26(site!1~sdsb,h2ax~u).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)  -> DNA26(site!1~sdsb,h2ax~p).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA26, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1806 | `Unlabeled` | one-way | DNA27, DNAPKcs, Ku | `kh2axp2` | internal-state conversion/modification | `DNA27(site!1~sdsb,h2ax~u).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)  -> DNA27(site!1~sdsb,h2ax~p).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA27, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1807 | `Unlabeled` | one-way | DNA28, DNAPKcs, Ku | `kh2axp2` | internal-state conversion/modification | `DNA28(site!1~sdsb,h2ax~u).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)  -> DNA28(site!1~sdsb,h2ax~p).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA28, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1808 | `Unlabeled` | one-way | DNA29, DNAPKcs, Ku | `kh2axp2` | internal-state conversion/modification | `DNA29(site!1~sdsb,h2ax~u).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)  -> DNA29(site!1~sdsb,h2ax~p).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA29, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1809 | `Unlabeled` | one-way | DNA30, DNAPKcs, Ku | `kh2axp2` | internal-state conversion/modification | `DNA30(site!1~sdsb,h2ax~u).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)  -> DNA30(site!1~sdsb,h2ax~p).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA30, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1810 | `Unlabeled` | one-way | DNA31, DNAPKcs, Ku | `kh2axp2` | internal-state conversion/modification | `DNA31(site!1~sdsb,h2ax~u).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)  -> DNA31(site!1~sdsb,h2ax~p).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA31, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1811 | `Unlabeled` | one-way | DNA32, DNAPKcs, Ku | `kh2axp2` | internal-state conversion/modification | `DNA32(site!1~sdsb,h2ax~u).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)  -> DNA32(site!1~sdsb,h2ax~p).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA32, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1812 | `Unlabeled` | one-way | DNA33, DNAPKcs, Ku | `kh2axp2` | internal-state conversion/modification | `DNA33(site!1~sdsb,h2ax~u).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)  -> DNA33(site!1~sdsb,h2ax~p).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA33, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1813 | `Unlabeled` | one-way | DNA34, DNAPKcs, Ku | `kh2axp2` | internal-state conversion/modification | `DNA34(site!1~sdsb,h2ax~u).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)  -> DNA34(site!1~sdsb,h2ax~p).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA34, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1814 | `Unlabeled` | one-way | DNA35, DNAPKcs, Ku | `kh2axp2` | internal-state conversion/modification | `DNA35(site!1~sdsb,h2ax~u).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)  -> DNA35(site!1~sdsb,h2ax~p).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA35, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1815 | `Unlabeled` | one-way | DNA36, DNAPKcs, Ku | `kh2axp2` | internal-state conversion/modification | `DNA36(site!1~sdsb,h2ax~u).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)  -> DNA36(site!1~sdsb,h2ax~p).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA36, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1816 | `Unlabeled` | one-way | DNA37, DNAPKcs, Ku | `kh2axp2` | internal-state conversion/modification | `DNA37(site!1~sdsb,h2ax~u).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)  -> DNA37(site!1~sdsb,h2ax~p).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA37, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1817 | `Unlabeled` | one-way | DNA38, DNAPKcs, Ku | `kh2axp2` | internal-state conversion/modification | `DNA38(site!1~sdsb,h2ax~u).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)  -> DNA38(site!1~sdsb,h2ax~p).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA38, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1818 | `Unlabeled` | one-way | DNA39, DNAPKcs, Ku | `kh2axp2` | internal-state conversion/modification | `DNA39(site!1~sdsb,h2ax~u).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)  -> DNA39(site!1~sdsb,h2ax~p).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA39, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1819 | `Unlabeled` | one-way | DNA40, DNAPKcs, Ku | `kh2axp2` | internal-state conversion/modification | `DNA40(site!1~sdsb,h2ax~u).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)  -> DNA40(site!1~sdsb,h2ax~p).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA40, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1820 | `Unlabeled` | one-way | DNA41, DNAPKcs, Ku | `kh2axp2` | internal-state conversion/modification | `DNA41(site!1~sdsb,h2ax~u).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)  -> DNA41(site!1~sdsb,h2ax~p).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA41, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1821 | `Unlabeled` | one-way | DNA42, DNAPKcs, Ku | `kh2axp2` | internal-state conversion/modification | `DNA42(site!1~sdsb,h2ax~u).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)  -> DNA42(site!1~sdsb,h2ax~p).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA42, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1822 | `Unlabeled` | one-way | DNA43, DNAPKcs, Ku | `kh2axp2` | internal-state conversion/modification | `DNA43(site!1~sdsb,h2ax~u).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)  -> DNA43(site!1~sdsb,h2ax~p).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA43, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1823 | `Unlabeled` | one-way | DNA44, DNAPKcs, Ku | `kh2axp2` | internal-state conversion/modification | `DNA44(site!1~sdsb,h2ax~u).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)  -> DNA44(site!1~sdsb,h2ax~p).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA44, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1824 | `Unlabeled` | one-way | DNA45, DNAPKcs, Ku | `kh2axp2` | internal-state conversion/modification | `DNA45(site!1~sdsb,h2ax~u).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)  -> DNA45(site!1~sdsb,h2ax~p).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA45, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1825 | `Unlabeled` | one-way | DNA46, DNAPKcs, Ku | `kh2axp2` | internal-state conversion/modification | `DNA46(site!1~sdsb,h2ax~u).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)  -> DNA46(site!1~sdsb,h2ax~p).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA46, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1826 | `Unlabeled` | one-way | DNA47, DNAPKcs, Ku | `kh2axp2` | internal-state conversion/modification | `DNA47(site!1~sdsb,h2ax~u).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)  -> DNA47(site!1~sdsb,h2ax~p).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA47, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1827 | `Unlabeled` | one-way | DNA48, DNAPKcs, Ku | `kh2axp2` | internal-state conversion/modification | `DNA48(site!1~sdsb,h2ax~u).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)  -> DNA48(site!1~sdsb,h2ax~p).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA48, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1828 | `Unlabeled` | one-way | DNA49, DNAPKcs, Ku | `kh2axp2` | internal-state conversion/modification | `DNA49(site!1~sdsb,h2ax~u).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)  -> DNA49(site!1~sdsb,h2ax~p).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA49, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1829 | `Unlabeled` | one-way | DNA50, DNAPKcs, Ku | `kh2axp2` | internal-state conversion/modification | `DNA50(site!1~sdsb,h2ax~u).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)  -> DNA50(site!1~sdsb,h2ax~p).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA50, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1830 | `Unlabeled` | one-way | DNA1, DNAPKcs, Ku | `kh2axp2` | internal-state conversion/modification | `DNA1(site!1~cdsb,h2ax~u).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)  -> DNA1(site!1~cdsb,h2ax~p).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA1, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1831 | `Unlabeled` | one-way | DNA2, DNAPKcs, Ku | `kh2axp2` | internal-state conversion/modification | `DNA2(site!1~cdsb,h2ax~u).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)  -> DNA2(site!1~cdsb,h2ax~p).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA2, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1832 | `Unlabeled` | one-way | DNA3, DNAPKcs, Ku | `kh2axp2` | internal-state conversion/modification | `DNA3(site!1~cdsb,h2ax~u).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)  -> DNA3(site!1~cdsb,h2ax~p).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA3, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1833 | `Unlabeled` | one-way | DNA4, DNAPKcs, Ku | `kh2axp2` | internal-state conversion/modification | `DNA4(site!1~cdsb,h2ax~u).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)  -> DNA4(site!1~cdsb,h2ax~p).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA4, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1834 | `Unlabeled` | one-way | DNA5, DNAPKcs, Ku | `kh2axp2` | internal-state conversion/modification | `DNA5(site!1~cdsb,h2ax~u).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)  -> DNA5(site!1~cdsb,h2ax~p).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA5, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1835 | `Unlabeled` | one-way | DNA6, DNAPKcs, Ku | `kh2axp2` | internal-state conversion/modification | `DNA6(site!1~cdsb,h2ax~u).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)  -> DNA6(site!1~cdsb,h2ax~p).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA6, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1836 | `Unlabeled` | one-way | DNA7, DNAPKcs, Ku | `kh2axp2` | internal-state conversion/modification | `DNA7(site!1~cdsb,h2ax~u).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)  -> DNA7(site!1~cdsb,h2ax~p).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA7, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1837 | `Unlabeled` | one-way | DNA8, DNAPKcs, Ku | `kh2axp2` | internal-state conversion/modification | `DNA8(site!1~cdsb,h2ax~u).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)  -> DNA8(site!1~cdsb,h2ax~p).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA8, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1838 | `Unlabeled` | one-way | DNA9, DNAPKcs, Ku | `kh2axp2` | internal-state conversion/modification | `DNA9(site!1~cdsb,h2ax~u).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)  -> DNA9(site!1~cdsb,h2ax~p).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA9, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1839 | `Unlabeled` | one-way | DNA10, DNAPKcs, Ku | `kh2axp2` | internal-state conversion/modification | `DNA10(site!1~cdsb,h2ax~u).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)  -> DNA10(site!1~cdsb,h2ax~p).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA10, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1840 | `Unlabeled` | one-way | DNA11, DNAPKcs, Ku | `kh2axp2` | internal-state conversion/modification | `DNA11(site!1~cdsb,h2ax~u).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)  -> DNA11(site!1~cdsb,h2ax~p).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA11, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1841 | `Unlabeled` | one-way | DNA12, DNAPKcs, Ku | `kh2axp2` | internal-state conversion/modification | `DNA12(site!1~cdsb,h2ax~u).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)  -> DNA12(site!1~cdsb,h2ax~p).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA12, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1842 | `Unlabeled` | one-way | DNA13, DNAPKcs, Ku | `kh2axp2` | internal-state conversion/modification | `DNA13(site!1~cdsb,h2ax~u).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)  -> DNA13(site!1~cdsb,h2ax~p).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA13, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1843 | `Unlabeled` | one-way | DNA14, DNAPKcs, Ku | `kh2axp2` | internal-state conversion/modification | `DNA14(site!1~cdsb,h2ax~u).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)  -> DNA14(site!1~cdsb,h2ax~p).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA14, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1844 | `Unlabeled` | one-way | DNA15, DNAPKcs, Ku | `kh2axp2` | internal-state conversion/modification | `DNA15(site!1~cdsb,h2ax~u).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)  -> DNA15(site!1~cdsb,h2ax~p).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA15, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1845 | `Unlabeled` | one-way | DNA16, DNAPKcs, Ku | `kh2axp2` | internal-state conversion/modification | `DNA16(site!1~cdsb,h2ax~u).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)  -> DNA16(site!1~cdsb,h2ax~p).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA16, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1846 | `Unlabeled` | one-way | DNA17, DNAPKcs, Ku | `kh2axp2` | internal-state conversion/modification | `DNA17(site!1~cdsb,h2ax~u).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)  -> DNA17(site!1~cdsb,h2ax~p).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA17, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1847 | `Unlabeled` | one-way | DNA18, DNAPKcs, Ku | `kh2axp2` | internal-state conversion/modification | `DNA18(site!1~cdsb,h2ax~u).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)  -> DNA18(site!1~cdsb,h2ax~p).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA18, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1848 | `Unlabeled` | one-way | DNA19, DNAPKcs, Ku | `kh2axp2` | internal-state conversion/modification | `DNA19(site!1~cdsb,h2ax~u).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)  -> DNA19(site!1~cdsb,h2ax~p).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA19, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1849 | `Unlabeled` | one-way | DNA20, DNAPKcs, Ku | `kh2axp2` | internal-state conversion/modification | `DNA20(site!1~cdsb,h2ax~u).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)  -> DNA20(site!1~cdsb,h2ax~p).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA20, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1850 | `Unlabeled` | one-way | DNA21, DNAPKcs, Ku | `kh2axp2` | internal-state conversion/modification | `DNA21(site!1~cdsb,h2ax~u).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)  -> DNA21(site!1~cdsb,h2ax~p).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA21, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1851 | `Unlabeled` | one-way | DNA22, DNAPKcs, Ku | `kh2axp2` | internal-state conversion/modification | `DNA22(site!1~cdsb,h2ax~u).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)  -> DNA22(site!1~cdsb,h2ax~p).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA22, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1852 | `Unlabeled` | one-way | DNA23, DNAPKcs, Ku | `kh2axp2` | internal-state conversion/modification | `DNA23(site!1~cdsb,h2ax~u).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)  -> DNA23(site!1~cdsb,h2ax~p).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA23, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1853 | `Unlabeled` | one-way | DNA24, DNAPKcs, Ku | `kh2axp2` | internal-state conversion/modification | `DNA24(site!1~cdsb,h2ax~u).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)  -> DNA24(site!1~cdsb,h2ax~p).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA24, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1854 | `Unlabeled` | one-way | DNA25, DNAPKcs, Ku | `kh2axp2` | internal-state conversion/modification | `DNA25(site!1~cdsb,h2ax~u).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)  -> DNA25(site!1~cdsb,h2ax~p).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA25, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1855 | `Unlabeled` | one-way | DNA26, DNAPKcs, Ku | `kh2axp2` | internal-state conversion/modification | `DNA26(site!1~cdsb,h2ax~u).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)  -> DNA26(site!1~cdsb,h2ax~p).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA26, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1856 | `Unlabeled` | one-way | DNA27, DNAPKcs, Ku | `kh2axp2` | internal-state conversion/modification | `DNA27(site!1~cdsb,h2ax~u).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)  -> DNA27(site!1~cdsb,h2ax~p).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA27, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1857 | `Unlabeled` | one-way | DNA28, DNAPKcs, Ku | `kh2axp2` | internal-state conversion/modification | `DNA28(site!1~cdsb,h2ax~u).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)  -> DNA28(site!1~cdsb,h2ax~p).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA28, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1858 | `Unlabeled` | one-way | DNA29, DNAPKcs, Ku | `kh2axp2` | internal-state conversion/modification | `DNA29(site!1~cdsb,h2ax~u).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)  -> DNA29(site!1~cdsb,h2ax~p).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA29, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1859 | `Unlabeled` | one-way | DNA30, DNAPKcs, Ku | `kh2axp2` | internal-state conversion/modification | `DNA30(site!1~cdsb,h2ax~u).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)  -> DNA30(site!1~cdsb,h2ax~p).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA30, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1860 | `Unlabeled` | one-way | DNA31, DNAPKcs, Ku | `kh2axp2` | internal-state conversion/modification | `DNA31(site!1~cdsb,h2ax~u).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)  -> DNA31(site!1~cdsb,h2ax~p).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA31, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1861 | `Unlabeled` | one-way | DNA32, DNAPKcs, Ku | `kh2axp2` | internal-state conversion/modification | `DNA32(site!1~cdsb,h2ax~u).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)  -> DNA32(site!1~cdsb,h2ax~p).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA32, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1862 | `Unlabeled` | one-way | DNA33, DNAPKcs, Ku | `kh2axp2` | internal-state conversion/modification | `DNA33(site!1~cdsb,h2ax~u).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)  -> DNA33(site!1~cdsb,h2ax~p).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA33, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1863 | `Unlabeled` | one-way | DNA34, DNAPKcs, Ku | `kh2axp2` | internal-state conversion/modification | `DNA34(site!1~cdsb,h2ax~u).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)  -> DNA34(site!1~cdsb,h2ax~p).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA34, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1864 | `Unlabeled` | one-way | DNA35, DNAPKcs, Ku | `kh2axp2` | internal-state conversion/modification | `DNA35(site!1~cdsb,h2ax~u).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)  -> DNA35(site!1~cdsb,h2ax~p).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA35, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1865 | `Unlabeled` | one-way | DNA36, DNAPKcs, Ku | `kh2axp2` | internal-state conversion/modification | `DNA36(site!1~cdsb,h2ax~u).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)  -> DNA36(site!1~cdsb,h2ax~p).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA36, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1866 | `Unlabeled` | one-way | DNA37, DNAPKcs, Ku | `kh2axp2` | internal-state conversion/modification | `DNA37(site!1~cdsb,h2ax~u).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)  -> DNA37(site!1~cdsb,h2ax~p).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA37, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1867 | `Unlabeled` | one-way | DNA38, DNAPKcs, Ku | `kh2axp2` | internal-state conversion/modification | `DNA38(site!1~cdsb,h2ax~u).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)  -> DNA38(site!1~cdsb,h2ax~p).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA38, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1868 | `Unlabeled` | one-way | DNA39, DNAPKcs, Ku | `kh2axp2` | internal-state conversion/modification | `DNA39(site!1~cdsb,h2ax~u).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)  -> DNA39(site!1~cdsb,h2ax~p).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA39, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1869 | `Unlabeled` | one-way | DNA40, DNAPKcs, Ku | `kh2axp2` | internal-state conversion/modification | `DNA40(site!1~cdsb,h2ax~u).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)  -> DNA40(site!1~cdsb,h2ax~p).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA40, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1870 | `Unlabeled` | one-way | DNA41, DNAPKcs, Ku | `kh2axp2` | internal-state conversion/modification | `DNA41(site!1~cdsb,h2ax~u).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)  -> DNA41(site!1~cdsb,h2ax~p).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA41, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1871 | `Unlabeled` | one-way | DNA42, DNAPKcs, Ku | `kh2axp2` | internal-state conversion/modification | `DNA42(site!1~cdsb,h2ax~u).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)  -> DNA42(site!1~cdsb,h2ax~p).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA42, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1872 | `Unlabeled` | one-way | DNA43, DNAPKcs, Ku | `kh2axp2` | internal-state conversion/modification | `DNA43(site!1~cdsb,h2ax~u).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)  -> DNA43(site!1~cdsb,h2ax~p).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA43, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1873 | `Unlabeled` | one-way | DNA44, DNAPKcs, Ku | `kh2axp2` | internal-state conversion/modification | `DNA44(site!1~cdsb,h2ax~u).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)  -> DNA44(site!1~cdsb,h2ax~p).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA44, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1874 | `Unlabeled` | one-way | DNA45, DNAPKcs, Ku | `kh2axp2` | internal-state conversion/modification | `DNA45(site!1~cdsb,h2ax~u).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)  -> DNA45(site!1~cdsb,h2ax~p).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA45, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1875 | `Unlabeled` | one-way | DNA46, DNAPKcs, Ku | `kh2axp2` | internal-state conversion/modification | `DNA46(site!1~cdsb,h2ax~u).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)  -> DNA46(site!1~cdsb,h2ax~p).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA46, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1876 | `Unlabeled` | one-way | DNA47, DNAPKcs, Ku | `kh2axp2` | internal-state conversion/modification | `DNA47(site!1~cdsb,h2ax~u).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)  -> DNA47(site!1~cdsb,h2ax~p).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA47, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1877 | `Unlabeled` | one-way | DNA48, DNAPKcs, Ku | `kh2axp2` | internal-state conversion/modification | `DNA48(site!1~cdsb,h2ax~u).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)  -> DNA48(site!1~cdsb,h2ax~p).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA48, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1878 | `Unlabeled` | one-way | DNA49, DNAPKcs, Ku | `kh2axp2` | internal-state conversion/modification | `DNA49(site!1~cdsb,h2ax~u).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)  -> DNA49(site!1~cdsb,h2ax~p).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA49, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1879 | `Unlabeled` | one-way | DNA50, DNAPKcs, Ku | `kh2axp2` | internal-state conversion/modification | `DNA50(site!1~cdsb,h2ax~u).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)  -> DNA50(site!1~cdsb,h2ax~p).Ku(dna!1,cs!2).DNAPKcs(ku!2,liIV,psite~p)` | Transforms DNA50, DNAPKcs, Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1880 | `Unlabeled` | one-way | DNA1 | `kh2axu` | internal-state conversion/modification | `DNA1(h2ax~p)  -> DNA1(h2ax~u)` | Transforms DNA1 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1881 | `Unlabeled` | one-way | DNA2 | `kh2axu` | internal-state conversion/modification | `DNA2(h2ax~p)  -> DNA2(h2ax~u)` | Transforms DNA2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1882 | `Unlabeled` | one-way | DNA3 | `kh2axu` | internal-state conversion/modification | `DNA3(h2ax~p)  -> DNA3(h2ax~u)` | Transforms DNA3 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1883 | `Unlabeled` | one-way | DNA4 | `kh2axu` | internal-state conversion/modification | `DNA4(h2ax~p)  -> DNA4(h2ax~u)` | Transforms DNA4 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1884 | `Unlabeled` | one-way | DNA5 | `kh2axu` | internal-state conversion/modification | `DNA5(h2ax~p)  -> DNA5(h2ax~u)` | Transforms DNA5 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1885 | `Unlabeled` | one-way | DNA6 | `kh2axu` | internal-state conversion/modification | `DNA6(h2ax~p)  -> DNA6(h2ax~u)` | Transforms DNA6 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1886 | `Unlabeled` | one-way | DNA7 | `kh2axu` | internal-state conversion/modification | `DNA7(h2ax~p)  -> DNA7(h2ax~u)` | Transforms DNA7 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1887 | `Unlabeled` | one-way | DNA8 | `kh2axu` | internal-state conversion/modification | `DNA8(h2ax~p)  -> DNA8(h2ax~u)` | Transforms DNA8 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1888 | `Unlabeled` | one-way | DNA9 | `kh2axu` | internal-state conversion/modification | `DNA9(h2ax~p)  -> DNA9(h2ax~u)` | Transforms DNA9 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1889 | `Unlabeled` | one-way | DNA10 | `kh2axu` | internal-state conversion/modification | `DNA10(h2ax~p)  -> DNA10(h2ax~u)` | Transforms DNA10 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1890 | `Unlabeled` | one-way | DNA11 | `kh2axu` | internal-state conversion/modification | `DNA11(h2ax~p)  -> DNA11(h2ax~u)` | Transforms DNA11 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1891 | `Unlabeled` | one-way | DNA12 | `kh2axu` | internal-state conversion/modification | `DNA12(h2ax~p)  -> DNA12(h2ax~u)` | Transforms DNA12 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1892 | `Unlabeled` | one-way | DNA13 | `kh2axu` | internal-state conversion/modification | `DNA13(h2ax~p)  -> DNA13(h2ax~u)` | Transforms DNA13 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1893 | `Unlabeled` | one-way | DNA14 | `kh2axu` | internal-state conversion/modification | `DNA14(h2ax~p)  -> DNA14(h2ax~u)` | Transforms DNA14 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1894 | `Unlabeled` | one-way | DNA15 | `kh2axu` | internal-state conversion/modification | `DNA15(h2ax~p)  -> DNA15(h2ax~u)` | Transforms DNA15 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1895 | `Unlabeled` | one-way | DNA16 | `kh2axu` | internal-state conversion/modification | `DNA16(h2ax~p)  -> DNA16(h2ax~u)` | Transforms DNA16 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1896 | `Unlabeled` | one-way | DNA17 | `kh2axu` | internal-state conversion/modification | `DNA17(h2ax~p)  -> DNA17(h2ax~u)` | Transforms DNA17 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1897 | `Unlabeled` | one-way | DNA18 | `kh2axu` | internal-state conversion/modification | `DNA18(h2ax~p)  -> DNA18(h2ax~u)` | Transforms DNA18 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1898 | `Unlabeled` | one-way | DNA19 | `kh2axu` | internal-state conversion/modification | `DNA19(h2ax~p)  -> DNA19(h2ax~u)` | Transforms DNA19 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1899 | `Unlabeled` | one-way | DNA20 | `kh2axu` | internal-state conversion/modification | `DNA20(h2ax~p)  -> DNA20(h2ax~u)` | Transforms DNA20 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1900 | `Unlabeled` | one-way | DNA21 | `kh2axu` | internal-state conversion/modification | `DNA21(h2ax~p)  -> DNA21(h2ax~u)` | Transforms DNA21 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1901 | `Unlabeled` | one-way | DNA22 | `kh2axu` | internal-state conversion/modification | `DNA22(h2ax~p)  -> DNA22(h2ax~u)` | Transforms DNA22 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1902 | `Unlabeled` | one-way | DNA23 | `kh2axu` | internal-state conversion/modification | `DNA23(h2ax~p)  -> DNA23(h2ax~u)` | Transforms DNA23 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1903 | `Unlabeled` | one-way | DNA24 | `kh2axu` | internal-state conversion/modification | `DNA24(h2ax~p)  -> DNA24(h2ax~u)` | Transforms DNA24 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1904 | `Unlabeled` | one-way | DNA25 | `kh2axu` | internal-state conversion/modification | `DNA25(h2ax~p)  -> DNA25(h2ax~u)` | Transforms DNA25 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1905 | `Unlabeled` | one-way | DNA26 | `kh2axu` | internal-state conversion/modification | `DNA26(h2ax~p)  -> DNA26(h2ax~u)` | Transforms DNA26 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1906 | `Unlabeled` | one-way | DNA27 | `kh2axu` | internal-state conversion/modification | `DNA27(h2ax~p)  -> DNA27(h2ax~u)` | Transforms DNA27 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1907 | `Unlabeled` | one-way | DNA28 | `kh2axu` | internal-state conversion/modification | `DNA28(h2ax~p)  -> DNA28(h2ax~u)` | Transforms DNA28 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1908 | `Unlabeled` | one-way | DNA29 | `kh2axu` | internal-state conversion/modification | `DNA29(h2ax~p)  -> DNA29(h2ax~u)` | Transforms DNA29 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1909 | `Unlabeled` | one-way | DNA30 | `kh2axu` | internal-state conversion/modification | `DNA30(h2ax~p)  -> DNA30(h2ax~u)` | Transforms DNA30 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1910 | `Unlabeled` | one-way | DNA31 | `kh2axu` | internal-state conversion/modification | `DNA31(h2ax~p)  -> DNA31(h2ax~u)` | Transforms DNA31 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1911 | `Unlabeled` | one-way | DNA32 | `kh2axu` | internal-state conversion/modification | `DNA32(h2ax~p)  -> DNA32(h2ax~u)` | Transforms DNA32 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1912 | `Unlabeled` | one-way | DNA33 | `kh2axu` | internal-state conversion/modification | `DNA33(h2ax~p)  -> DNA33(h2ax~u)` | Transforms DNA33 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1913 | `Unlabeled` | one-way | DNA34 | `kh2axu` | internal-state conversion/modification | `DNA34(h2ax~p)  -> DNA34(h2ax~u)` | Transforms DNA34 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1914 | `Unlabeled` | one-way | DNA35 | `kh2axu` | internal-state conversion/modification | `DNA35(h2ax~p)  -> DNA35(h2ax~u)` | Transforms DNA35 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1915 | `Unlabeled` | one-way | DNA36 | `kh2axu` | internal-state conversion/modification | `DNA36(h2ax~p)  -> DNA36(h2ax~u)` | Transforms DNA36 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1916 | `Unlabeled` | one-way | DNA37 | `kh2axu` | internal-state conversion/modification | `DNA37(h2ax~p)  -> DNA37(h2ax~u)` | Transforms DNA37 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1917 | `Unlabeled` | one-way | DNA38 | `kh2axu` | internal-state conversion/modification | `DNA38(h2ax~p)  -> DNA38(h2ax~u)` | Transforms DNA38 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1918 | `Unlabeled` | one-way | DNA39 | `kh2axu` | internal-state conversion/modification | `DNA39(h2ax~p)  -> DNA39(h2ax~u)` | Transforms DNA39 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1919 | `Unlabeled` | one-way | DNA40 | `kh2axu` | internal-state conversion/modification | `DNA40(h2ax~p)  -> DNA40(h2ax~u)` | Transforms DNA40 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1920 | `Unlabeled` | one-way | DNA41 | `kh2axu` | internal-state conversion/modification | `DNA41(h2ax~p)  -> DNA41(h2ax~u)` | Transforms DNA41 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1921 | `Unlabeled` | one-way | DNA42 | `kh2axu` | internal-state conversion/modification | `DNA42(h2ax~p)  -> DNA42(h2ax~u)` | Transforms DNA42 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1922 | `Unlabeled` | one-way | DNA43 | `kh2axu` | internal-state conversion/modification | `DNA43(h2ax~p)  -> DNA43(h2ax~u)` | Transforms DNA43 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1923 | `Unlabeled` | one-way | DNA44 | `kh2axu` | internal-state conversion/modification | `DNA44(h2ax~p)  -> DNA44(h2ax~u)` | Transforms DNA44 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1924 | `Unlabeled` | one-way | DNA45 | `kh2axu` | internal-state conversion/modification | `DNA45(h2ax~p)  -> DNA45(h2ax~u)` | Transforms DNA45 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1925 | `Unlabeled` | one-way | DNA46 | `kh2axu` | internal-state conversion/modification | `DNA46(h2ax~p)  -> DNA46(h2ax~u)` | Transforms DNA46 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1926 | `Unlabeled` | one-way | DNA47 | `kh2axu` | internal-state conversion/modification | `DNA47(h2ax~p)  -> DNA47(h2ax~u)` | Transforms DNA47 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1927 | `Unlabeled` | one-way | DNA48 | `kh2axu` | internal-state conversion/modification | `DNA48(h2ax~p)  -> DNA48(h2ax~u)` | Transforms DNA48 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1928 | `Unlabeled` | one-way | DNA49 | `kh2axu` | internal-state conversion/modification | `DNA49(h2ax~p)  -> DNA49(h2ax~u)` | Transforms DNA49 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1929 | `Unlabeled` | one-way | DNA50 | `kh2axu` | internal-state conversion/modification | `DNA50(h2ax~p)  -> DNA50(h2ax~u)` | Transforms DNA50 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1930 | `Unlabeled` | one-way | DNA1 | `kh2axfoc` | internal-state conversion/modification | `DNA1(h2ax~p)  -> DNA1(h2ax~foc)` | Transforms DNA1 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1931 | `Unlabeled` | one-way | DNA2 | `kh2axfoc` | internal-state conversion/modification | `DNA2(h2ax~p)  -> DNA2(h2ax~foc)` | Transforms DNA2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1932 | `Unlabeled` | one-way | DNA3 | `kh2axfoc` | internal-state conversion/modification | `DNA3(h2ax~p)  -> DNA3(h2ax~foc)` | Transforms DNA3 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1933 | `Unlabeled` | one-way | DNA4 | `kh2axfoc` | internal-state conversion/modification | `DNA4(h2ax~p)  -> DNA4(h2ax~foc)` | Transforms DNA4 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1934 | `Unlabeled` | one-way | DNA5 | `kh2axfoc` | internal-state conversion/modification | `DNA5(h2ax~p)  -> DNA5(h2ax~foc)` | Transforms DNA5 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1935 | `Unlabeled` | one-way | DNA6 | `kh2axfoc` | internal-state conversion/modification | `DNA6(h2ax~p)  -> DNA6(h2ax~foc)` | Transforms DNA6 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1936 | `Unlabeled` | one-way | DNA7 | `kh2axfoc` | internal-state conversion/modification | `DNA7(h2ax~p)  -> DNA7(h2ax~foc)` | Transforms DNA7 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1937 | `Unlabeled` | one-way | DNA8 | `kh2axfoc` | internal-state conversion/modification | `DNA8(h2ax~p)  -> DNA8(h2ax~foc)` | Transforms DNA8 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1938 | `Unlabeled` | one-way | DNA9 | `kh2axfoc` | internal-state conversion/modification | `DNA9(h2ax~p)  -> DNA9(h2ax~foc)` | Transforms DNA9 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1939 | `Unlabeled` | one-way | DNA10 | `kh2axfoc` | internal-state conversion/modification | `DNA10(h2ax~p)  -> DNA10(h2ax~foc)` | Transforms DNA10 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1940 | `Unlabeled` | one-way | DNA11 | `kh2axfoc` | internal-state conversion/modification | `DNA11(h2ax~p)  -> DNA11(h2ax~foc)` | Transforms DNA11 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1941 | `Unlabeled` | one-way | DNA12 | `kh2axfoc` | internal-state conversion/modification | `DNA12(h2ax~p)  -> DNA12(h2ax~foc)` | Transforms DNA12 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1942 | `Unlabeled` | one-way | DNA13 | `kh2axfoc` | internal-state conversion/modification | `DNA13(h2ax~p)  -> DNA13(h2ax~foc)` | Transforms DNA13 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1943 | `Unlabeled` | one-way | DNA14 | `kh2axfoc` | internal-state conversion/modification | `DNA14(h2ax~p)  -> DNA14(h2ax~foc)` | Transforms DNA14 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1944 | `Unlabeled` | one-way | DNA15 | `kh2axfoc` | internal-state conversion/modification | `DNA15(h2ax~p)  -> DNA15(h2ax~foc)` | Transforms DNA15 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1945 | `Unlabeled` | one-way | DNA16 | `kh2axfoc` | internal-state conversion/modification | `DNA16(h2ax~p)  -> DNA16(h2ax~foc)` | Transforms DNA16 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1946 | `Unlabeled` | one-way | DNA17 | `kh2axfoc` | internal-state conversion/modification | `DNA17(h2ax~p)  -> DNA17(h2ax~foc)` | Transforms DNA17 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1947 | `Unlabeled` | one-way | DNA18 | `kh2axfoc` | internal-state conversion/modification | `DNA18(h2ax~p)  -> DNA18(h2ax~foc)` | Transforms DNA18 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1948 | `Unlabeled` | one-way | DNA19 | `kh2axfoc` | internal-state conversion/modification | `DNA19(h2ax~p)  -> DNA19(h2ax~foc)` | Transforms DNA19 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1949 | `Unlabeled` | one-way | DNA20 | `kh2axfoc` | internal-state conversion/modification | `DNA20(h2ax~p)  -> DNA20(h2ax~foc)` | Transforms DNA20 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1950 | `Unlabeled` | one-way | DNA21 | `kh2axfoc` | internal-state conversion/modification | `DNA21(h2ax~p)  -> DNA21(h2ax~foc)` | Transforms DNA21 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1951 | `Unlabeled` | one-way | DNA22 | `kh2axfoc` | internal-state conversion/modification | `DNA22(h2ax~p)  -> DNA22(h2ax~foc)` | Transforms DNA22 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1952 | `Unlabeled` | one-way | DNA23 | `kh2axfoc` | internal-state conversion/modification | `DNA23(h2ax~p)  -> DNA23(h2ax~foc)` | Transforms DNA23 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1953 | `Unlabeled` | one-way | DNA24 | `kh2axfoc` | internal-state conversion/modification | `DNA24(h2ax~p)  -> DNA24(h2ax~foc)` | Transforms DNA24 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1954 | `Unlabeled` | one-way | DNA25 | `kh2axfoc` | internal-state conversion/modification | `DNA25(h2ax~p)  -> DNA25(h2ax~foc)` | Transforms DNA25 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1955 | `Unlabeled` | one-way | DNA26 | `kh2axfoc` | internal-state conversion/modification | `DNA26(h2ax~p)  -> DNA26(h2ax~foc)` | Transforms DNA26 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1956 | `Unlabeled` | one-way | DNA27 | `kh2axfoc` | internal-state conversion/modification | `DNA27(h2ax~p)  -> DNA27(h2ax~foc)` | Transforms DNA27 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1957 | `Unlabeled` | one-way | DNA28 | `kh2axfoc` | internal-state conversion/modification | `DNA28(h2ax~p)  -> DNA28(h2ax~foc)` | Transforms DNA28 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1958 | `Unlabeled` | one-way | DNA29 | `kh2axfoc` | internal-state conversion/modification | `DNA29(h2ax~p)  -> DNA29(h2ax~foc)` | Transforms DNA29 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1959 | `Unlabeled` | one-way | DNA30 | `kh2axfoc` | internal-state conversion/modification | `DNA30(h2ax~p)  -> DNA30(h2ax~foc)` | Transforms DNA30 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1960 | `Unlabeled` | one-way | DNA31 | `kh2axfoc` | internal-state conversion/modification | `DNA31(h2ax~p)  -> DNA31(h2ax~foc)` | Transforms DNA31 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1961 | `Unlabeled` | one-way | DNA32 | `kh2axfoc` | internal-state conversion/modification | `DNA32(h2ax~p)  -> DNA32(h2ax~foc)` | Transforms DNA32 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1962 | `Unlabeled` | one-way | DNA33 | `kh2axfoc` | internal-state conversion/modification | `DNA33(h2ax~p)  -> DNA33(h2ax~foc)` | Transforms DNA33 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1963 | `Unlabeled` | one-way | DNA34 | `kh2axfoc` | internal-state conversion/modification | `DNA34(h2ax~p)  -> DNA34(h2ax~foc)` | Transforms DNA34 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1964 | `Unlabeled` | one-way | DNA35 | `kh2axfoc` | internal-state conversion/modification | `DNA35(h2ax~p)  -> DNA35(h2ax~foc)` | Transforms DNA35 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1965 | `Unlabeled` | one-way | DNA36 | `kh2axfoc` | internal-state conversion/modification | `DNA36(h2ax~p)  -> DNA36(h2ax~foc)` | Transforms DNA36 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1966 | `Unlabeled` | one-way | DNA37 | `kh2axfoc` | internal-state conversion/modification | `DNA37(h2ax~p)  -> DNA37(h2ax~foc)` | Transforms DNA37 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1967 | `Unlabeled` | one-way | DNA38 | `kh2axfoc` | internal-state conversion/modification | `DNA38(h2ax~p)  -> DNA38(h2ax~foc)` | Transforms DNA38 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1968 | `Unlabeled` | one-way | DNA39 | `kh2axfoc` | internal-state conversion/modification | `DNA39(h2ax~p)  -> DNA39(h2ax~foc)` | Transforms DNA39 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1969 | `Unlabeled` | one-way | DNA40 | `kh2axfoc` | internal-state conversion/modification | `DNA40(h2ax~p)  -> DNA40(h2ax~foc)` | Transforms DNA40 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1970 | `Unlabeled` | one-way | DNA41 | `kh2axfoc` | internal-state conversion/modification | `DNA41(h2ax~p)  -> DNA41(h2ax~foc)` | Transforms DNA41 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1971 | `Unlabeled` | one-way | DNA42 | `kh2axfoc` | internal-state conversion/modification | `DNA42(h2ax~p)  -> DNA42(h2ax~foc)` | Transforms DNA42 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1972 | `Unlabeled` | one-way | DNA43 | `kh2axfoc` | internal-state conversion/modification | `DNA43(h2ax~p)  -> DNA43(h2ax~foc)` | Transforms DNA43 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1973 | `Unlabeled` | one-way | DNA44 | `kh2axfoc` | internal-state conversion/modification | `DNA44(h2ax~p)  -> DNA44(h2ax~foc)` | Transforms DNA44 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1974 | `Unlabeled` | one-way | DNA45 | `kh2axfoc` | internal-state conversion/modification | `DNA45(h2ax~p)  -> DNA45(h2ax~foc)` | Transforms DNA45 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1975 | `Unlabeled` | one-way | DNA46 | `kh2axfoc` | internal-state conversion/modification | `DNA46(h2ax~p)  -> DNA46(h2ax~foc)` | Transforms DNA46 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1976 | `Unlabeled` | one-way | DNA47 | `kh2axfoc` | internal-state conversion/modification | `DNA47(h2ax~p)  -> DNA47(h2ax~foc)` | Transforms DNA47 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1977 | `Unlabeled` | one-way | DNA48 | `kh2axfoc` | internal-state conversion/modification | `DNA48(h2ax~p)  -> DNA48(h2ax~foc)` | Transforms DNA48 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1978 | `Unlabeled` | one-way | DNA49 | `kh2axfoc` | internal-state conversion/modification | `DNA49(h2ax~p)  -> DNA49(h2ax~foc)` | Transforms DNA49 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1979 | `Unlabeled` | one-way | DNA50 | `kh2axfoc` | internal-state conversion/modification | `DNA50(h2ax~p)  -> DNA50(h2ax~foc)` | Transforms DNA50 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1980 | `Unlabeled` | one-way | DNA1 | `kfocback` | internal-state conversion/modification | `DNA1(h2ax~foc)  -> DNA1(h2ax~u)` | Transforms DNA1 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1981 | `Unlabeled` | one-way | DNA2 | `kfocback` | internal-state conversion/modification | `DNA2(h2ax~foc)  -> DNA2(h2ax~u)` | Transforms DNA2 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1982 | `Unlabeled` | one-way | DNA3 | `kfocback` | internal-state conversion/modification | `DNA3(h2ax~foc)  -> DNA3(h2ax~u)` | Transforms DNA3 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1983 | `Unlabeled` | one-way | DNA4 | `kfocback` | internal-state conversion/modification | `DNA4(h2ax~foc)  -> DNA4(h2ax~u)` | Transforms DNA4 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1984 | `Unlabeled` | one-way | DNA5 | `kfocback` | internal-state conversion/modification | `DNA5(h2ax~foc)  -> DNA5(h2ax~u)` | Transforms DNA5 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1985 | `Unlabeled` | one-way | DNA6 | `kfocback` | internal-state conversion/modification | `DNA6(h2ax~foc)  -> DNA6(h2ax~u)` | Transforms DNA6 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1986 | `Unlabeled` | one-way | DNA7 | `kfocback` | internal-state conversion/modification | `DNA7(h2ax~foc)  -> DNA7(h2ax~u)` | Transforms DNA7 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1987 | `Unlabeled` | one-way | DNA8 | `kfocback` | internal-state conversion/modification | `DNA8(h2ax~foc)  -> DNA8(h2ax~u)` | Transforms DNA8 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1988 | `Unlabeled` | one-way | DNA9 | `kfocback` | internal-state conversion/modification | `DNA9(h2ax~foc)  -> DNA9(h2ax~u)` | Transforms DNA9 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1989 | `Unlabeled` | one-way | DNA10 | `kfocback` | internal-state conversion/modification | `DNA10(h2ax~foc)  -> DNA10(h2ax~u)` | Transforms DNA10 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1990 | `Unlabeled` | one-way | DNA11 | `kfocback` | internal-state conversion/modification | `DNA11(h2ax~foc)  -> DNA11(h2ax~u)` | Transforms DNA11 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1991 | `Unlabeled` | one-way | DNA12 | `kfocback` | internal-state conversion/modification | `DNA12(h2ax~foc)  -> DNA12(h2ax~u)` | Transforms DNA12 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1992 | `Unlabeled` | one-way | DNA13 | `kfocback` | internal-state conversion/modification | `DNA13(h2ax~foc)  -> DNA13(h2ax~u)` | Transforms DNA13 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1993 | `Unlabeled` | one-way | DNA14 | `kfocback` | internal-state conversion/modification | `DNA14(h2ax~foc)  -> DNA14(h2ax~u)` | Transforms DNA14 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1994 | `Unlabeled` | one-way | DNA15 | `kfocback` | internal-state conversion/modification | `DNA15(h2ax~foc)  -> DNA15(h2ax~u)` | Transforms DNA15 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1995 | `Unlabeled` | one-way | DNA16 | `kfocback` | internal-state conversion/modification | `DNA16(h2ax~foc)  -> DNA16(h2ax~u)` | Transforms DNA16 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1996 | `Unlabeled` | one-way | DNA17 | `kfocback` | internal-state conversion/modification | `DNA17(h2ax~foc)  -> DNA17(h2ax~u)` | Transforms DNA17 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1997 | `Unlabeled` | one-way | DNA18 | `kfocback` | internal-state conversion/modification | `DNA18(h2ax~foc)  -> DNA18(h2ax~u)` | Transforms DNA18 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1998 | `Unlabeled` | one-way | DNA19 | `kfocback` | internal-state conversion/modification | `DNA19(h2ax~foc)  -> DNA19(h2ax~u)` | Transforms DNA19 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 1999 | `Unlabeled` | one-way | DNA20 | `kfocback` | internal-state conversion/modification | `DNA20(h2ax~foc)  -> DNA20(h2ax~u)` | Transforms DNA20 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 2000 | `Unlabeled` | one-way | DNA21 | `kfocback` | internal-state conversion/modification | `DNA21(h2ax~foc)  -> DNA21(h2ax~u)` | Transforms DNA21 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

### Rules 2001-2250

| # | Rule label/name | Direction | Participants | Rate/expression | Modeled change | Rule pattern | Technical meaning |
| ---: | --- | --- | --- | --- | --- | --- | --- |

| 2001 | `Unlabeled` | one-way | DNA22 | `kfocback` | internal-state conversion/modification | `DNA22(h2ax~foc)  -> DNA22(h2ax~u)` | Transforms DNA22 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 2002 | `Unlabeled` | one-way | DNA23 | `kfocback` | internal-state conversion/modification | `DNA23(h2ax~foc)  -> DNA23(h2ax~u)` | Transforms DNA23 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 2003 | `Unlabeled` | one-way | DNA24 | `kfocback` | internal-state conversion/modification | `DNA24(h2ax~foc)  -> DNA24(h2ax~u)` | Transforms DNA24 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 2004 | `Unlabeled` | one-way | DNA25 | `kfocback` | internal-state conversion/modification | `DNA25(h2ax~foc)  -> DNA25(h2ax~u)` | Transforms DNA25 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 2005 | `Unlabeled` | one-way | DNA26 | `kfocback` | internal-state conversion/modification | `DNA26(h2ax~foc)  -> DNA26(h2ax~u)` | Transforms DNA26 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 2006 | `Unlabeled` | one-way | DNA27 | `kfocback` | internal-state conversion/modification | `DNA27(h2ax~foc)  -> DNA27(h2ax~u)` | Transforms DNA27 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 2007 | `Unlabeled` | one-way | DNA28 | `kfocback` | internal-state conversion/modification | `DNA28(h2ax~foc)  -> DNA28(h2ax~u)` | Transforms DNA28 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 2008 | `Unlabeled` | one-way | DNA29 | `kfocback` | internal-state conversion/modification | `DNA29(h2ax~foc)  -> DNA29(h2ax~u)` | Transforms DNA29 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 2009 | `Unlabeled` | one-way | DNA30 | `kfocback` | internal-state conversion/modification | `DNA30(h2ax~foc)  -> DNA30(h2ax~u)` | Transforms DNA30 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 2010 | `Unlabeled` | one-way | DNA31 | `kfocback` | internal-state conversion/modification | `DNA31(h2ax~foc)  -> DNA31(h2ax~u)` | Transforms DNA31 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 2011 | `Unlabeled` | one-way | DNA32 | `kfocback` | internal-state conversion/modification | `DNA32(h2ax~foc)  -> DNA32(h2ax~u)` | Transforms DNA32 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 2012 | `Unlabeled` | one-way | DNA33 | `kfocback` | internal-state conversion/modification | `DNA33(h2ax~foc)  -> DNA33(h2ax~u)` | Transforms DNA33 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 2013 | `Unlabeled` | one-way | DNA34 | `kfocback` | internal-state conversion/modification | `DNA34(h2ax~foc)  -> DNA34(h2ax~u)` | Transforms DNA34 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 2014 | `Unlabeled` | one-way | DNA35 | `kfocback` | internal-state conversion/modification | `DNA35(h2ax~foc)  -> DNA35(h2ax~u)` | Transforms DNA35 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 2015 | `Unlabeled` | one-way | DNA36 | `kfocback` | internal-state conversion/modification | `DNA36(h2ax~foc)  -> DNA36(h2ax~u)` | Transforms DNA36 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 2016 | `Unlabeled` | one-way | DNA37 | `kfocback` | internal-state conversion/modification | `DNA37(h2ax~foc)  -> DNA37(h2ax~u)` | Transforms DNA37 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 2017 | `Unlabeled` | one-way | DNA38 | `kfocback` | internal-state conversion/modification | `DNA38(h2ax~foc)  -> DNA38(h2ax~u)` | Transforms DNA38 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 2018 | `Unlabeled` | one-way | DNA39 | `kfocback` | internal-state conversion/modification | `DNA39(h2ax~foc)  -> DNA39(h2ax~u)` | Transforms DNA39 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 2019 | `Unlabeled` | one-way | DNA40 | `kfocback` | internal-state conversion/modification | `DNA40(h2ax~foc)  -> DNA40(h2ax~u)` | Transforms DNA40 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 2020 | `Unlabeled` | one-way | DNA41 | `kfocback` | internal-state conversion/modification | `DNA41(h2ax~foc)  -> DNA41(h2ax~u)` | Transforms DNA41 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 2021 | `Unlabeled` | one-way | DNA42 | `kfocback` | internal-state conversion/modification | `DNA42(h2ax~foc)  -> DNA42(h2ax~u)` | Transforms DNA42 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 2022 | `Unlabeled` | one-way | DNA43 | `kfocback` | internal-state conversion/modification | `DNA43(h2ax~foc)  -> DNA43(h2ax~u)` | Transforms DNA43 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 2023 | `Unlabeled` | one-way | DNA44 | `kfocback` | internal-state conversion/modification | `DNA44(h2ax~foc)  -> DNA44(h2ax~u)` | Transforms DNA44 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 2024 | `Unlabeled` | one-way | DNA45 | `kfocback` | internal-state conversion/modification | `DNA45(h2ax~foc)  -> DNA45(h2ax~u)` | Transforms DNA45 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 2025 | `Unlabeled` | one-way | DNA46 | `kfocback` | internal-state conversion/modification | `DNA46(h2ax~foc)  -> DNA46(h2ax~u)` | Transforms DNA46 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 2026 | `Unlabeled` | one-way | DNA47 | `kfocback` | internal-state conversion/modification | `DNA47(h2ax~foc)  -> DNA47(h2ax~u)` | Transforms DNA47 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 2027 | `Unlabeled` | one-way | DNA48 | `kfocback` | internal-state conversion/modification | `DNA48(h2ax~foc)  -> DNA48(h2ax~u)` | Transforms DNA48 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 2028 | `Unlabeled` | one-way | DNA49 | `kfocback` | internal-state conversion/modification | `DNA49(h2ax~foc)  -> DNA49(h2ax~u)` | Transforms DNA49 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 2029 | `Unlabeled` | one-way | DNA50 | `kfocback` | internal-state conversion/modification | `DNA50(h2ax~foc)  -> DNA50(h2ax~u)` | Transforms DNA50 by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 2030 | `Unlabeled` | one-way | ATM, DNA1 | `kh2axfull` | state and binding-pattern rewrite | `DNA1(h2ax~foc) + ATM(state~1,h2ax)  -> DNA1(h2ax!1~foc).ATM(state~1,h2ax!1)` | Transforms ATM, DNA1 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2031 | `Unlabeled` | one-way | ATM, DNA2 | `kh2axfull` | state and binding-pattern rewrite | `DNA2(h2ax~foc) + ATM(state~2,h2ax)  -> DNA2(h2ax!1~foc).ATM(state~2,h2ax!1)` | Transforms ATM, DNA2 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2032 | `Unlabeled` | one-way | ATM, DNA3 | `kh2axfull` | state and binding-pattern rewrite | `DNA3(h2ax~foc) + ATM(state~3,h2ax)  -> DNA3(h2ax!1~foc).ATM(state~3,h2ax!1)` | Transforms ATM, DNA3 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2033 | `Unlabeled` | one-way | ATM, DNA4 | `kh2axfull` | state and binding-pattern rewrite | `DNA4(h2ax~foc) + ATM(state~4,h2ax)  -> DNA4(h2ax!1~foc).ATM(state~4,h2ax!1)` | Transforms ATM, DNA4 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2034 | `Unlabeled` | one-way | ATM, DNA5 | `kh2axfull` | state and binding-pattern rewrite | `DNA5(h2ax~foc) + ATM(state~5,h2ax)  -> DNA5(h2ax!1~foc).ATM(state~5,h2ax!1)` | Transforms ATM, DNA5 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2035 | `Unlabeled` | one-way | ATM, DNA6 | `kh2axfull` | state and binding-pattern rewrite | `DNA6(h2ax~foc) + ATM(state~6,h2ax)  -> DNA6(h2ax!1~foc).ATM(state~6,h2ax!1)` | Transforms ATM, DNA6 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2036 | `Unlabeled` | one-way | ATM, DNA7 | `kh2axfull` | state and binding-pattern rewrite | `DNA7(h2ax~foc) + ATM(state~7,h2ax)  -> DNA7(h2ax!1~foc).ATM(state~7,h2ax!1)` | Transforms ATM, DNA7 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2037 | `Unlabeled` | one-way | ATM, DNA8 | `kh2axfull` | state and binding-pattern rewrite | `DNA8(h2ax~foc) + ATM(state~8,h2ax)  -> DNA8(h2ax!1~foc).ATM(state~8,h2ax!1)` | Transforms ATM, DNA8 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2038 | `Unlabeled` | one-way | ATM, DNA9 | `kh2axfull` | state and binding-pattern rewrite | `DNA9(h2ax~foc) + ATM(state~9,h2ax)  -> DNA9(h2ax!1~foc).ATM(state~9,h2ax!1)` | Transforms ATM, DNA9 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2039 | `Unlabeled` | one-way | ATM, DNA10 | `kh2axfull` | state and binding-pattern rewrite | `DNA10(h2ax~foc) + ATM(state~10,h2ax)  -> DNA10(h2ax!1~foc).ATM(state~10,h2ax!1)` | Transforms ATM, DNA10 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2040 | `Unlabeled` | one-way | ATM, DNA11 | `kh2axfull` | state and binding-pattern rewrite | `DNA11(h2ax~foc) + ATM(state~11,h2ax)  -> DNA11(h2ax!1~foc).ATM(state~11,h2ax!1)` | Transforms ATM, DNA11 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2041 | `Unlabeled` | one-way | ATM, DNA12 | `kh2axfull` | state and binding-pattern rewrite | `DNA12(h2ax~foc) + ATM(state~12,h2ax)  -> DNA12(h2ax!1~foc).ATM(state~12,h2ax!1)` | Transforms ATM, DNA12 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2042 | `Unlabeled` | one-way | ATM, DNA13 | `kh2axfull` | state and binding-pattern rewrite | `DNA13(h2ax~foc) + ATM(state~13,h2ax)  -> DNA13(h2ax!1~foc).ATM(state~13,h2ax!1)` | Transforms ATM, DNA13 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2043 | `Unlabeled` | one-way | ATM, DNA14 | `kh2axfull` | state and binding-pattern rewrite | `DNA14(h2ax~foc) + ATM(state~14,h2ax)  -> DNA14(h2ax!1~foc).ATM(state~14,h2ax!1)` | Transforms ATM, DNA14 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2044 | `Unlabeled` | one-way | ATM, DNA15 | `kh2axfull` | state and binding-pattern rewrite | `DNA15(h2ax~foc) + ATM(state~15,h2ax)  -> DNA15(h2ax!1~foc).ATM(state~15,h2ax!1)` | Transforms ATM, DNA15 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2045 | `Unlabeled` | one-way | ATM, DNA16 | `kh2axfull` | state and binding-pattern rewrite | `DNA16(h2ax~foc) + ATM(state~16,h2ax)  -> DNA16(h2ax!1~foc).ATM(state~16,h2ax!1)` | Transforms ATM, DNA16 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2046 | `Unlabeled` | one-way | ATM, DNA17 | `kh2axfull` | state and binding-pattern rewrite | `DNA17(h2ax~foc) + ATM(state~17,h2ax)  -> DNA17(h2ax!1~foc).ATM(state~17,h2ax!1)` | Transforms ATM, DNA17 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2047 | `Unlabeled` | one-way | ATM, DNA18 | `kh2axfull` | state and binding-pattern rewrite | `DNA18(h2ax~foc) + ATM(state~18,h2ax)  -> DNA18(h2ax!1~foc).ATM(state~18,h2ax!1)` | Transforms ATM, DNA18 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2048 | `Unlabeled` | one-way | ATM, DNA19 | `kh2axfull` | state and binding-pattern rewrite | `DNA19(h2ax~foc) + ATM(state~19,h2ax)  -> DNA19(h2ax!1~foc).ATM(state~19,h2ax!1)` | Transforms ATM, DNA19 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2049 | `Unlabeled` | one-way | ATM, DNA20 | `kh2axfull` | state and binding-pattern rewrite | `DNA20(h2ax~foc) + ATM(state~20,h2ax)  -> DNA20(h2ax!1~foc).ATM(state~20,h2ax!1)` | Transforms ATM, DNA20 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2050 | `Unlabeled` | one-way | ATM, DNA21 | `kh2axfull` | state and binding-pattern rewrite | `DNA21(h2ax~foc) + ATM(state~21,h2ax)  -> DNA21(h2ax!1~foc).ATM(state~21,h2ax!1)` | Transforms ATM, DNA21 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2051 | `Unlabeled` | one-way | ATM, DNA22 | `kh2axfull` | state and binding-pattern rewrite | `DNA22(h2ax~foc) + ATM(state~22,h2ax)  -> DNA22(h2ax!1~foc).ATM(state~22,h2ax!1)` | Transforms ATM, DNA22 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2052 | `Unlabeled` | one-way | ATM, DNA23 | `kh2axfull` | state and binding-pattern rewrite | `DNA23(h2ax~foc) + ATM(state~23,h2ax)  -> DNA23(h2ax!1~foc).ATM(state~23,h2ax!1)` | Transforms ATM, DNA23 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2053 | `Unlabeled` | one-way | ATM, DNA24 | `kh2axfull` | state and binding-pattern rewrite | `DNA24(h2ax~foc) + ATM(state~24,h2ax)  -> DNA24(h2ax!1~foc).ATM(state~24,h2ax!1)` | Transforms ATM, DNA24 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2054 | `Unlabeled` | one-way | ATM, DNA25 | `kh2axfull` | state and binding-pattern rewrite | `DNA25(h2ax~foc) + ATM(state~25,h2ax)  -> DNA25(h2ax!1~foc).ATM(state~25,h2ax!1)` | Transforms ATM, DNA25 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2055 | `Unlabeled` | one-way | ATM, DNA26 | `kh2axfull` | state and binding-pattern rewrite | `DNA26(h2ax~foc) + ATM(state~26,h2ax)  -> DNA26(h2ax!1~foc).ATM(state~26,h2ax!1)` | Transforms ATM, DNA26 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2056 | `Unlabeled` | one-way | ATM, DNA27 | `kh2axfull` | state and binding-pattern rewrite | `DNA27(h2ax~foc) + ATM(state~27,h2ax)  -> DNA27(h2ax!1~foc).ATM(state~27,h2ax!1)` | Transforms ATM, DNA27 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2057 | `Unlabeled` | one-way | ATM, DNA28 | `kh2axfull` | state and binding-pattern rewrite | `DNA28(h2ax~foc) + ATM(state~28,h2ax)  -> DNA28(h2ax!1~foc).ATM(state~28,h2ax!1)` | Transforms ATM, DNA28 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2058 | `Unlabeled` | one-way | ATM, DNA29 | `kh2axfull` | state and binding-pattern rewrite | `DNA29(h2ax~foc) + ATM(state~29,h2ax)  -> DNA29(h2ax!1~foc).ATM(state~29,h2ax!1)` | Transforms ATM, DNA29 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2059 | `Unlabeled` | one-way | ATM, DNA30 | `kh2axfull` | state and binding-pattern rewrite | `DNA30(h2ax~foc) + ATM(state~30,h2ax)  -> DNA30(h2ax!1~foc).ATM(state~30,h2ax!1)` | Transforms ATM, DNA30 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2060 | `Unlabeled` | one-way | ATM, DNA31 | `kh2axfull` | state and binding-pattern rewrite | `DNA31(h2ax~foc) + ATM(state~31,h2ax)  -> DNA31(h2ax!1~foc).ATM(state~31,h2ax!1)` | Transforms ATM, DNA31 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2061 | `Unlabeled` | one-way | ATM, DNA32 | `kh2axfull` | state and binding-pattern rewrite | `DNA32(h2ax~foc) + ATM(state~32,h2ax)  -> DNA32(h2ax!1~foc).ATM(state~32,h2ax!1)` | Transforms ATM, DNA32 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2062 | `Unlabeled` | one-way | ATM, DNA33 | `kh2axfull` | state and binding-pattern rewrite | `DNA33(h2ax~foc) + ATM(state~33,h2ax)  -> DNA33(h2ax!1~foc).ATM(state~33,h2ax!1)` | Transforms ATM, DNA33 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2063 | `Unlabeled` | one-way | ATM, DNA34 | `kh2axfull` | state and binding-pattern rewrite | `DNA34(h2ax~foc) + ATM(state~34,h2ax)  -> DNA34(h2ax!1~foc).ATM(state~34,h2ax!1)` | Transforms ATM, DNA34 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2064 | `Unlabeled` | one-way | ATM, DNA35 | `kh2axfull` | state and binding-pattern rewrite | `DNA35(h2ax~foc) + ATM(state~35,h2ax)  -> DNA35(h2ax!1~foc).ATM(state~35,h2ax!1)` | Transforms ATM, DNA35 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2065 | `Unlabeled` | one-way | ATM, DNA36 | `kh2axfull` | state and binding-pattern rewrite | `DNA36(h2ax~foc) + ATM(state~36,h2ax)  -> DNA36(h2ax!1~foc).ATM(state~36,h2ax!1)` | Transforms ATM, DNA36 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2066 | `Unlabeled` | one-way | ATM, DNA37 | `kh2axfull` | state and binding-pattern rewrite | `DNA37(h2ax~foc) + ATM(state~37,h2ax)  -> DNA37(h2ax!1~foc).ATM(state~37,h2ax!1)` | Transforms ATM, DNA37 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2067 | `Unlabeled` | one-way | ATM, DNA38 | `kh2axfull` | state and binding-pattern rewrite | `DNA38(h2ax~foc) + ATM(state~38,h2ax)  -> DNA38(h2ax!1~foc).ATM(state~38,h2ax!1)` | Transforms ATM, DNA38 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2068 | `Unlabeled` | one-way | ATM, DNA39 | `kh2axfull` | state and binding-pattern rewrite | `DNA39(h2ax~foc) + ATM(state~39,h2ax)  -> DNA39(h2ax!1~foc).ATM(state~39,h2ax!1)` | Transforms ATM, DNA39 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2069 | `Unlabeled` | one-way | ATM, DNA40 | `kh2axfull` | state and binding-pattern rewrite | `DNA40(h2ax~foc) + ATM(state~40,h2ax)  -> DNA40(h2ax!1~foc).ATM(state~40,h2ax!1)` | Transforms ATM, DNA40 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2070 | `Unlabeled` | one-way | ATM, DNA41 | `kh2axfull` | state and binding-pattern rewrite | `DNA41(h2ax~foc) + ATM(state~41,h2ax)  -> DNA41(h2ax!1~foc).ATM(state~41,h2ax!1)` | Transforms ATM, DNA41 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2071 | `Unlabeled` | one-way | ATM, DNA42 | `kh2axfull` | state and binding-pattern rewrite | `DNA42(h2ax~foc) + ATM(state~42,h2ax)  -> DNA42(h2ax!1~foc).ATM(state~42,h2ax!1)` | Transforms ATM, DNA42 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2072 | `Unlabeled` | one-way | ATM, DNA43 | `kh2axfull` | state and binding-pattern rewrite | `DNA43(h2ax~foc) + ATM(state~43,h2ax)  -> DNA43(h2ax!1~foc).ATM(state~43,h2ax!1)` | Transforms ATM, DNA43 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2073 | `Unlabeled` | one-way | ATM, DNA44 | `kh2axfull` | state and binding-pattern rewrite | `DNA44(h2ax~foc) + ATM(state~44,h2ax)  -> DNA44(h2ax!1~foc).ATM(state~44,h2ax!1)` | Transforms ATM, DNA44 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2074 | `Unlabeled` | one-way | ATM, DNA45 | `kh2axfull` | state and binding-pattern rewrite | `DNA45(h2ax~foc) + ATM(state~45,h2ax)  -> DNA45(h2ax!1~foc).ATM(state~45,h2ax!1)` | Transforms ATM, DNA45 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2075 | `Unlabeled` | one-way | ATM, DNA46 | `kh2axfull` | state and binding-pattern rewrite | `DNA46(h2ax~foc) + ATM(state~46,h2ax)  -> DNA46(h2ax!1~foc).ATM(state~46,h2ax!1)` | Transforms ATM, DNA46 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2076 | `Unlabeled` | one-way | ATM, DNA47 | `kh2axfull` | state and binding-pattern rewrite | `DNA47(h2ax~foc) + ATM(state~47,h2ax)  -> DNA47(h2ax!1~foc).ATM(state~47,h2ax!1)` | Transforms ATM, DNA47 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2077 | `Unlabeled` | one-way | ATM, DNA48 | `kh2axfull` | state and binding-pattern rewrite | `DNA48(h2ax~foc) + ATM(state~48,h2ax)  -> DNA48(h2ax!1~foc).ATM(state~48,h2ax!1)` | Transforms ATM, DNA48 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2078 | `Unlabeled` | one-way | ATM, DNA49 | `kh2axfull` | state and binding-pattern rewrite | `DNA49(h2ax~foc) + ATM(state~49,h2ax)  -> DNA49(h2ax!1~foc).ATM(state~49,h2ax!1)` | Transforms ATM, DNA49 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2079 | `Unlabeled` | one-way | ATM, DNA50 | `kh2axfull` | state and binding-pattern rewrite | `DNA50(h2ax~foc) + ATM(state~50,h2ax)  -> DNA50(h2ax!1~foc).ATM(state~50,h2ax!1)` | Transforms ATM, DNA50 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2080 | `Unlabeled` | one-way | ATM, DNA1 | `kfocfin` | state and binding-pattern rewrite | `DNA1(h2ax!1~foc).ATM(state~1,h2ax!1)  -> DNA1(h2ax~u) + ATM(state~0,h2ax)` | Transforms ATM, DNA1 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2081 | `Unlabeled` | one-way | ATM, DNA2 | `kfocfin` | state and binding-pattern rewrite | `DNA2(h2ax!1~foc).ATM(state~2,h2ax!1)  -> DNA2(h2ax~u) + ATM(state~0,h2ax)` | Transforms ATM, DNA2 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2082 | `Unlabeled` | one-way | ATM, DNA3 | `kfocfin` | state and binding-pattern rewrite | `DNA3(h2ax!1~foc).ATM(state~3,h2ax!1)  -> DNA3(h2ax~u) + ATM(state~0,h2ax)` | Transforms ATM, DNA3 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2083 | `Unlabeled` | one-way | ATM, DNA4 | `kfocfin` | state and binding-pattern rewrite | `DNA4(h2ax!1~foc).ATM(state~4,h2ax!1)  -> DNA4(h2ax~u) + ATM(state~0,h2ax)` | Transforms ATM, DNA4 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2084 | `Unlabeled` | one-way | ATM, DNA5 | `kfocfin` | state and binding-pattern rewrite | `DNA5(h2ax!1~foc).ATM(state~5,h2ax!1)  -> DNA5(h2ax~u) + ATM(state~0,h2ax)` | Transforms ATM, DNA5 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2085 | `Unlabeled` | one-way | ATM, DNA6 | `kfocfin` | state and binding-pattern rewrite | `DNA6(h2ax!1~foc).ATM(state~6,h2ax!1)  -> DNA6(h2ax~u) + ATM(state~0,h2ax)` | Transforms ATM, DNA6 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2086 | `Unlabeled` | one-way | ATM, DNA7 | `kfocfin` | state and binding-pattern rewrite | `DNA7(h2ax!1~foc).ATM(state~7,h2ax!1)  -> DNA7(h2ax~u) + ATM(state~0,h2ax)` | Transforms ATM, DNA7 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2087 | `Unlabeled` | one-way | ATM, DNA8 | `kfocfin` | state and binding-pattern rewrite | `DNA8(h2ax!1~foc).ATM(state~8,h2ax!1)  -> DNA8(h2ax~u) + ATM(state~0,h2ax)` | Transforms ATM, DNA8 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2088 | `Unlabeled` | one-way | ATM, DNA9 | `kfocfin` | state and binding-pattern rewrite | `DNA9(h2ax!1~foc).ATM(state~9,h2ax!1)  -> DNA9(h2ax~u) + ATM(state~0,h2ax)` | Transforms ATM, DNA9 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2089 | `Unlabeled` | one-way | ATM, DNA10 | `kfocfin` | state and binding-pattern rewrite | `DNA10(h2ax!1~foc).ATM(state~10,h2ax!1)  -> DNA10(h2ax~u) + ATM(state~0,h2ax)` | Transforms ATM, DNA10 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2090 | `Unlabeled` | one-way | ATM, DNA11 | `kfocfin` | state and binding-pattern rewrite | `DNA11(h2ax!1~foc).ATM(state~11,h2ax!1)  -> DNA11(h2ax~u) + ATM(state~0,h2ax)` | Transforms ATM, DNA11 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2091 | `Unlabeled` | one-way | ATM, DNA12 | `kfocfin` | state and binding-pattern rewrite | `DNA12(h2ax!1~foc).ATM(state~12,h2ax!1)  -> DNA12(h2ax~u) + ATM(state~0,h2ax)` | Transforms ATM, DNA12 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2092 | `Unlabeled` | one-way | ATM, DNA13 | `kfocfin` | state and binding-pattern rewrite | `DNA13(h2ax!1~foc).ATM(state~13,h2ax!1)  -> DNA13(h2ax~u) + ATM(state~0,h2ax)` | Transforms ATM, DNA13 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2093 | `Unlabeled` | one-way | ATM, DNA14 | `kfocfin` | state and binding-pattern rewrite | `DNA14(h2ax!1~foc).ATM(state~14,h2ax!1)  -> DNA14(h2ax~u) + ATM(state~0,h2ax)` | Transforms ATM, DNA14 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2094 | `Unlabeled` | one-way | ATM, DNA15 | `kfocfin` | state and binding-pattern rewrite | `DNA15(h2ax!1~foc).ATM(state~15,h2ax!1)  -> DNA15(h2ax~u) + ATM(state~0,h2ax)` | Transforms ATM, DNA15 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2095 | `Unlabeled` | one-way | ATM, DNA16 | `kfocfin` | state and binding-pattern rewrite | `DNA16(h2ax!1~foc).ATM(state~16,h2ax!1)  -> DNA16(h2ax~u) + ATM(state~0,h2ax)` | Transforms ATM, DNA16 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2096 | `Unlabeled` | one-way | ATM, DNA17 | `kfocfin` | state and binding-pattern rewrite | `DNA17(h2ax!1~foc).ATM(state~17,h2ax!1)  -> DNA17(h2ax~u) + ATM(state~0,h2ax)` | Transforms ATM, DNA17 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2097 | `Unlabeled` | one-way | ATM, DNA18 | `kfocfin` | state and binding-pattern rewrite | `DNA18(h2ax!1~foc).ATM(state~18,h2ax!1)  -> DNA18(h2ax~u) + ATM(state~0,h2ax)` | Transforms ATM, DNA18 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2098 | `Unlabeled` | one-way | ATM, DNA19 | `kfocfin` | state and binding-pattern rewrite | `DNA19(h2ax!1~foc).ATM(state~19,h2ax!1)  -> DNA19(h2ax~u) + ATM(state~0,h2ax)` | Transforms ATM, DNA19 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2099 | `Unlabeled` | one-way | ATM, DNA20 | `kfocfin` | state and binding-pattern rewrite | `DNA20(h2ax!1~foc).ATM(state~20,h2ax!1)  -> DNA20(h2ax~u) + ATM(state~0,h2ax)` | Transforms ATM, DNA20 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2100 | `Unlabeled` | one-way | ATM, DNA21 | `kfocfin` | state and binding-pattern rewrite | `DNA21(h2ax!1~foc).ATM(state~21,h2ax!1)  -> DNA21(h2ax~u) + ATM(state~0,h2ax)` | Transforms ATM, DNA21 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2101 | `Unlabeled` | one-way | ATM, DNA22 | `kfocfin` | state and binding-pattern rewrite | `DNA22(h2ax!1~foc).ATM(state~22,h2ax!1)  -> DNA22(h2ax~u) + ATM(state~0,h2ax)` | Transforms ATM, DNA22 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2102 | `Unlabeled` | one-way | ATM, DNA23 | `kfocfin` | state and binding-pattern rewrite | `DNA23(h2ax!1~foc).ATM(state~23,h2ax!1)  -> DNA23(h2ax~u) + ATM(state~0,h2ax)` | Transforms ATM, DNA23 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2103 | `Unlabeled` | one-way | ATM, DNA24 | `kfocfin` | state and binding-pattern rewrite | `DNA24(h2ax!1~foc).ATM(state~24,h2ax!1)  -> DNA24(h2ax~u) + ATM(state~0,h2ax)` | Transforms ATM, DNA24 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2104 | `Unlabeled` | one-way | ATM, DNA25 | `kfocfin` | state and binding-pattern rewrite | `DNA25(h2ax!1~foc).ATM(state~25,h2ax!1)  -> DNA25(h2ax~u) + ATM(state~0,h2ax)` | Transforms ATM, DNA25 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2105 | `Unlabeled` | one-way | ATM, DNA26 | `kfocfin` | state and binding-pattern rewrite | `DNA26(h2ax!1~foc).ATM(state~26,h2ax!1)  -> DNA26(h2ax~u) + ATM(state~0,h2ax)` | Transforms ATM, DNA26 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2106 | `Unlabeled` | one-way | ATM, DNA27 | `kfocfin` | state and binding-pattern rewrite | `DNA27(h2ax!1~foc).ATM(state~27,h2ax!1)  -> DNA27(h2ax~u) + ATM(state~0,h2ax)` | Transforms ATM, DNA27 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2107 | `Unlabeled` | one-way | ATM, DNA28 | `kfocfin` | state and binding-pattern rewrite | `DNA28(h2ax!1~foc).ATM(state~28,h2ax!1)  -> DNA28(h2ax~u) + ATM(state~0,h2ax)` | Transforms ATM, DNA28 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2108 | `Unlabeled` | one-way | ATM, DNA29 | `kfocfin` | state and binding-pattern rewrite | `DNA29(h2ax!1~foc).ATM(state~29,h2ax!1)  -> DNA29(h2ax~u) + ATM(state~0,h2ax)` | Transforms ATM, DNA29 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2109 | `Unlabeled` | one-way | ATM, DNA30 | `kfocfin` | state and binding-pattern rewrite | `DNA30(h2ax!1~foc).ATM(state~30,h2ax!1)  -> DNA30(h2ax~u) + ATM(state~0,h2ax)` | Transforms ATM, DNA30 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2110 | `Unlabeled` | one-way | ATM, DNA31 | `kfocfin` | state and binding-pattern rewrite | `DNA31(h2ax!1~foc).ATM(state~31,h2ax!1)  -> DNA31(h2ax~u) + ATM(state~0,h2ax)` | Transforms ATM, DNA31 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2111 | `Unlabeled` | one-way | ATM, DNA32 | `kfocfin` | state and binding-pattern rewrite | `DNA32(h2ax!1~foc).ATM(state~32,h2ax!1)  -> DNA32(h2ax~u) + ATM(state~0,h2ax)` | Transforms ATM, DNA32 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2112 | `Unlabeled` | one-way | ATM, DNA33 | `kfocfin` | state and binding-pattern rewrite | `DNA33(h2ax!1~foc).ATM(state~33,h2ax!1)  -> DNA33(h2ax~u) + ATM(state~0,h2ax)` | Transforms ATM, DNA33 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2113 | `Unlabeled` | one-way | ATM, DNA34 | `kfocfin` | state and binding-pattern rewrite | `DNA34(h2ax!1~foc).ATM(state~34,h2ax!1)  -> DNA34(h2ax~u) + ATM(state~0,h2ax)` | Transforms ATM, DNA34 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2114 | `Unlabeled` | one-way | ATM, DNA35 | `kfocfin` | state and binding-pattern rewrite | `DNA35(h2ax!1~foc).ATM(state~35,h2ax!1)  -> DNA35(h2ax~u) + ATM(state~0,h2ax)` | Transforms ATM, DNA35 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2115 | `Unlabeled` | one-way | ATM, DNA36 | `kfocfin` | state and binding-pattern rewrite | `DNA36(h2ax!1~foc).ATM(state~36,h2ax!1)  -> DNA36(h2ax~u) + ATM(state~0,h2ax)` | Transforms ATM, DNA36 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2116 | `Unlabeled` | one-way | ATM, DNA37 | `kfocfin` | state and binding-pattern rewrite | `DNA37(h2ax!1~foc).ATM(state~37,h2ax!1)  -> DNA37(h2ax~u) + ATM(state~0,h2ax)` | Transforms ATM, DNA37 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2117 | `Unlabeled` | one-way | ATM, DNA38 | `kfocfin` | state and binding-pattern rewrite | `DNA38(h2ax!1~foc).ATM(state~38,h2ax!1)  -> DNA38(h2ax~u) + ATM(state~0,h2ax)` | Transforms ATM, DNA38 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2118 | `Unlabeled` | one-way | ATM, DNA39 | `kfocfin` | state and binding-pattern rewrite | `DNA39(h2ax!1~foc).ATM(state~39,h2ax!1)  -> DNA39(h2ax~u) + ATM(state~0,h2ax)` | Transforms ATM, DNA39 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2119 | `Unlabeled` | one-way | ATM, DNA40 | `kfocfin` | state and binding-pattern rewrite | `DNA40(h2ax!1~foc).ATM(state~40,h2ax!1)  -> DNA40(h2ax~u) + ATM(state~0,h2ax)` | Transforms ATM, DNA40 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2120 | `Unlabeled` | one-way | ATM, DNA41 | `kfocfin` | state and binding-pattern rewrite | `DNA41(h2ax!1~foc).ATM(state~41,h2ax!1)  -> DNA41(h2ax~u) + ATM(state~0,h2ax)` | Transforms ATM, DNA41 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2121 | `Unlabeled` | one-way | ATM, DNA42 | `kfocfin` | state and binding-pattern rewrite | `DNA42(h2ax!1~foc).ATM(state~42,h2ax!1)  -> DNA42(h2ax~u) + ATM(state~0,h2ax)` | Transforms ATM, DNA42 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2122 | `Unlabeled` | one-way | ATM, DNA43 | `kfocfin` | state and binding-pattern rewrite | `DNA43(h2ax!1~foc).ATM(state~43,h2ax!1)  -> DNA43(h2ax~u) + ATM(state~0,h2ax)` | Transforms ATM, DNA43 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2123 | `Unlabeled` | one-way | ATM, DNA44 | `kfocfin` | state and binding-pattern rewrite | `DNA44(h2ax!1~foc).ATM(state~44,h2ax!1)  -> DNA44(h2ax~u) + ATM(state~0,h2ax)` | Transforms ATM, DNA44 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2124 | `Unlabeled` | one-way | ATM, DNA45 | `kfocfin` | state and binding-pattern rewrite | `DNA45(h2ax!1~foc).ATM(state~45,h2ax!1)  -> DNA45(h2ax~u) + ATM(state~0,h2ax)` | Transforms ATM, DNA45 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2125 | `Unlabeled` | one-way | ATM, DNA46 | `kfocfin` | state and binding-pattern rewrite | `DNA46(h2ax!1~foc).ATM(state~46,h2ax!1)  -> DNA46(h2ax~u) + ATM(state~0,h2ax)` | Transforms ATM, DNA46 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2126 | `Unlabeled` | one-way | ATM, DNA47 | `kfocfin` | state and binding-pattern rewrite | `DNA47(h2ax!1~foc).ATM(state~47,h2ax!1)  -> DNA47(h2ax~u) + ATM(state~0,h2ax)` | Transforms ATM, DNA47 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2127 | `Unlabeled` | one-way | ATM, DNA48 | `kfocfin` | state and binding-pattern rewrite | `DNA48(h2ax!1~foc).ATM(state~48,h2ax!1)  -> DNA48(h2ax~u) + ATM(state~0,h2ax)` | Transforms ATM, DNA48 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2128 | `Unlabeled` | one-way | ATM, DNA49 | `kfocfin` | state and binding-pattern rewrite | `DNA49(h2ax!1~foc).ATM(state~49,h2ax!1)  -> DNA49(h2ax~u) + ATM(state~0,h2ax)` | Transforms ATM, DNA49 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2129 | `Unlabeled` | one-way | ATM, DNA50 | `kfocfin` | state and binding-pattern rewrite | `DNA50(h2ax!1~foc).ATM(state~50,h2ax!1)  -> DNA50(h2ax~u) + ATM(state~0,h2ax)` | Transforms ATM, DNA50 by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2130 | `Unlabeled` | one-way | I, ROS | `kROS` | source/synthesis or algebraic source term | `I()  -> I() + ROS()` | Transforms I, ROS by source/synthesis or algebraic source term; see the exact pattern for affected sites/states/bonds. |

| 2131 | `Unlabeled` | one-way | ROS, Sink | `kdROS` | sink/degradation/removal | `ROS()  -> Sink()` | Transforms ROS, Sink by sink/degradation/removal; see the exact pattern for affected sites/states/bonds. |

| 2132 | `Unlabeled` | one-way | IR, ROS | `kIR` | stoichiometric pattern rewrite | `IR()  -> IR() + ROS()` | Transforms IR, ROS by stoichiometric pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2133 | `Unlabeled` | one-way | DNA1, ROS | `kdam1` | internal-state conversion/modification | `DNA1(site~ok) + ROS()  -> DNA1(site~sdsb)` | Transforms DNA1, ROS by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 2134 | `Unlabeled` | one-way | DNA2, ROS | `kdam1` | internal-state conversion/modification | `DNA2(site~ok) + ROS()  -> DNA2(site~sdsb)` | Transforms DNA2, ROS by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 2135 | `Unlabeled` | one-way | DNA3, ROS | `kdam1` | internal-state conversion/modification | `DNA3(site~ok) + ROS()  -> DNA3(site~sdsb)` | Transforms DNA3, ROS by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 2136 | `Unlabeled` | one-way | DNA4, ROS | `kdam1` | internal-state conversion/modification | `DNA4(site~ok) + ROS()  -> DNA4(site~sdsb)` | Transforms DNA4, ROS by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 2137 | `Unlabeled` | one-way | DNA5, ROS | `kdam1` | internal-state conversion/modification | `DNA5(site~ok) + ROS()  -> DNA5(site~sdsb)` | Transforms DNA5, ROS by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 2138 | `Unlabeled` | one-way | DNA6, ROS | `kdam1` | internal-state conversion/modification | `DNA6(site~ok) + ROS()  -> DNA6(site~sdsb)` | Transforms DNA6, ROS by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 2139 | `Unlabeled` | one-way | DNA7, ROS | `kdam1` | internal-state conversion/modification | `DNA7(site~ok) + ROS()  -> DNA7(site~sdsb)` | Transforms DNA7, ROS by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 2140 | `Unlabeled` | one-way | DNA8, ROS | `kdam1` | internal-state conversion/modification | `DNA8(site~ok) + ROS()  -> DNA8(site~sdsb)` | Transforms DNA8, ROS by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 2141 | `Unlabeled` | one-way | DNA9, ROS | `kdam1` | internal-state conversion/modification | `DNA9(site~ok) + ROS()  -> DNA9(site~sdsb)` | Transforms DNA9, ROS by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 2142 | `Unlabeled` | one-way | DNA10, ROS | `kdam1` | internal-state conversion/modification | `DNA10(site~ok) + ROS()  -> DNA10(site~sdsb)` | Transforms DNA10, ROS by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 2143 | `Unlabeled` | one-way | DNA11, ROS | `kdam1` | internal-state conversion/modification | `DNA11(site~ok) + ROS()  -> DNA11(site~sdsb)` | Transforms DNA11, ROS by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 2144 | `Unlabeled` | one-way | DNA12, ROS | `kdam1` | internal-state conversion/modification | `DNA12(site~ok) + ROS()  -> DNA12(site~sdsb)` | Transforms DNA12, ROS by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 2145 | `Unlabeled` | one-way | DNA13, ROS | `kdam1` | internal-state conversion/modification | `DNA13(site~ok) + ROS()  -> DNA13(site~sdsb)` | Transforms DNA13, ROS by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 2146 | `Unlabeled` | one-way | DNA14, ROS | `kdam1` | internal-state conversion/modification | `DNA14(site~ok) + ROS()  -> DNA14(site~sdsb)` | Transforms DNA14, ROS by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 2147 | `Unlabeled` | one-way | DNA15, ROS | `kdam1` | internal-state conversion/modification | `DNA15(site~ok) + ROS()  -> DNA15(site~sdsb)` | Transforms DNA15, ROS by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 2148 | `Unlabeled` | one-way | DNA16, ROS | `kdam1` | internal-state conversion/modification | `DNA16(site~ok) + ROS()  -> DNA16(site~sdsb)` | Transforms DNA16, ROS by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 2149 | `Unlabeled` | one-way | DNA17, ROS | `kdam1` | internal-state conversion/modification | `DNA17(site~ok) + ROS()  -> DNA17(site~sdsb)` | Transforms DNA17, ROS by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 2150 | `Unlabeled` | one-way | DNA18, ROS | `kdam1` | internal-state conversion/modification | `DNA18(site~ok) + ROS()  -> DNA18(site~sdsb)` | Transforms DNA18, ROS by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 2151 | `Unlabeled` | one-way | DNA19, ROS | `kdam1` | internal-state conversion/modification | `DNA19(site~ok) + ROS()  -> DNA19(site~sdsb)` | Transforms DNA19, ROS by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 2152 | `Unlabeled` | one-way | DNA20, ROS | `kdam1` | internal-state conversion/modification | `DNA20(site~ok) + ROS()  -> DNA20(site~sdsb)` | Transforms DNA20, ROS by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 2153 | `Unlabeled` | one-way | DNA21, ROS | `kdam1` | internal-state conversion/modification | `DNA21(site~ok) + ROS()  -> DNA21(site~sdsb)` | Transforms DNA21, ROS by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 2154 | `Unlabeled` | one-way | DNA22, ROS | `kdam1` | internal-state conversion/modification | `DNA22(site~ok) + ROS()  -> DNA22(site~sdsb)` | Transforms DNA22, ROS by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 2155 | `Unlabeled` | one-way | DNA23, ROS | `kdam1` | internal-state conversion/modification | `DNA23(site~ok) + ROS()  -> DNA23(site~sdsb)` | Transforms DNA23, ROS by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 2156 | `Unlabeled` | one-way | DNA24, ROS | `kdam1` | internal-state conversion/modification | `DNA24(site~ok) + ROS()  -> DNA24(site~sdsb)` | Transforms DNA24, ROS by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 2157 | `Unlabeled` | one-way | DNA25, ROS | `kdam1` | internal-state conversion/modification | `DNA25(site~ok) + ROS()  -> DNA25(site~sdsb)` | Transforms DNA25, ROS by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 2158 | `Unlabeled` | one-way | DNA26, ROS | `kdam1` | internal-state conversion/modification | `DNA26(site~ok) + ROS()  -> DNA26(site~sdsb)` | Transforms DNA26, ROS by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 2159 | `Unlabeled` | one-way | DNA27, ROS | `kdam1` | internal-state conversion/modification | `DNA27(site~ok) + ROS()  -> DNA27(site~sdsb)` | Transforms DNA27, ROS by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 2160 | `Unlabeled` | one-way | DNA28, ROS | `kdam1` | internal-state conversion/modification | `DNA28(site~ok) + ROS()  -> DNA28(site~sdsb)` | Transforms DNA28, ROS by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 2161 | `Unlabeled` | one-way | DNA29, ROS | `kdam1` | internal-state conversion/modification | `DNA29(site~ok) + ROS()  -> DNA29(site~sdsb)` | Transforms DNA29, ROS by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 2162 | `Unlabeled` | one-way | DNA30, ROS | `kdam1` | internal-state conversion/modification | `DNA30(site~ok) + ROS()  -> DNA30(site~sdsb)` | Transforms DNA30, ROS by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 2163 | `Unlabeled` | one-way | DNA31, ROS | `kdam1` | internal-state conversion/modification | `DNA31(site~ok) + ROS()  -> DNA31(site~sdsb)` | Transforms DNA31, ROS by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 2164 | `Unlabeled` | one-way | DNA32, ROS | `kdam1` | internal-state conversion/modification | `DNA32(site~ok) + ROS()  -> DNA32(site~sdsb)` | Transforms DNA32, ROS by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 2165 | `Unlabeled` | one-way | DNA33, ROS | `kdam1` | internal-state conversion/modification | `DNA33(site~ok) + ROS()  -> DNA33(site~sdsb)` | Transforms DNA33, ROS by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 2166 | `Unlabeled` | one-way | DNA34, ROS | `kdam1` | internal-state conversion/modification | `DNA34(site~ok) + ROS()  -> DNA34(site~sdsb)` | Transforms DNA34, ROS by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 2167 | `Unlabeled` | one-way | DNA35, ROS | `kdam1` | internal-state conversion/modification | `DNA35(site~ok) + ROS()  -> DNA35(site~sdsb)` | Transforms DNA35, ROS by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 2168 | `Unlabeled` | one-way | DNA36, ROS | `kdam1` | internal-state conversion/modification | `DNA36(site~ok) + ROS()  -> DNA36(site~sdsb)` | Transforms DNA36, ROS by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 2169 | `Unlabeled` | one-way | DNA37, ROS | `kdam1` | internal-state conversion/modification | `DNA37(site~ok) + ROS()  -> DNA37(site~sdsb)` | Transforms DNA37, ROS by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 2170 | `Unlabeled` | one-way | DNA38, ROS | `kdam1` | internal-state conversion/modification | `DNA38(site~ok) + ROS()  -> DNA38(site~sdsb)` | Transforms DNA38, ROS by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 2171 | `Unlabeled` | one-way | DNA39, ROS | `kdam1` | internal-state conversion/modification | `DNA39(site~ok) + ROS()  -> DNA39(site~sdsb)` | Transforms DNA39, ROS by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 2172 | `Unlabeled` | one-way | DNA40, ROS | `kdam1` | internal-state conversion/modification | `DNA40(site~ok) + ROS()  -> DNA40(site~sdsb)` | Transforms DNA40, ROS by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 2173 | `Unlabeled` | one-way | DNA41, ROS | `kdam1` | internal-state conversion/modification | `DNA41(site~ok) + ROS()  -> DNA41(site~sdsb)` | Transforms DNA41, ROS by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 2174 | `Unlabeled` | one-way | DNA42, ROS | `kdam1` | internal-state conversion/modification | `DNA42(site~ok) + ROS()  -> DNA42(site~sdsb)` | Transforms DNA42, ROS by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 2175 | `Unlabeled` | one-way | DNA43, ROS | `kdam1` | internal-state conversion/modification | `DNA43(site~ok) + ROS()  -> DNA43(site~sdsb)` | Transforms DNA43, ROS by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 2176 | `Unlabeled` | one-way | DNA44, ROS | `kdam1` | internal-state conversion/modification | `DNA44(site~ok) + ROS()  -> DNA44(site~sdsb)` | Transforms DNA44, ROS by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 2177 | `Unlabeled` | one-way | DNA45, ROS | `kdam1` | internal-state conversion/modification | `DNA45(site~ok) + ROS()  -> DNA45(site~sdsb)` | Transforms DNA45, ROS by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 2178 | `Unlabeled` | one-way | DNA46, ROS | `kdam1` | internal-state conversion/modification | `DNA46(site~ok) + ROS()  -> DNA46(site~sdsb)` | Transforms DNA46, ROS by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 2179 | `Unlabeled` | one-way | DNA47, ROS | `kdam1` | internal-state conversion/modification | `DNA47(site~ok) + ROS()  -> DNA47(site~sdsb)` | Transforms DNA47, ROS by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 2180 | `Unlabeled` | one-way | DNA48, ROS | `kdam1` | internal-state conversion/modification | `DNA48(site~ok) + ROS()  -> DNA48(site~sdsb)` | Transforms DNA48, ROS by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 2181 | `Unlabeled` | one-way | DNA49, ROS | `kdam1` | internal-state conversion/modification | `DNA49(site~ok) + ROS()  -> DNA49(site~sdsb)` | Transforms DNA49, ROS by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 2182 | `Unlabeled` | one-way | DNA50, ROS | `kdam1` | internal-state conversion/modification | `DNA50(site~ok) + ROS()  -> DNA50(site~sdsb)` | Transforms DNA50, ROS by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 2183 | `Unlabeled` | one-way | DNA1, ROS | `kdam2` | internal-state conversion/modification | `DNA1(site~ok) + ROS()  -> DNA1(site~cdsb)` | Transforms DNA1, ROS by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 2184 | `Unlabeled` | one-way | DNA2, ROS | `kdam2` | internal-state conversion/modification | `DNA2(site~ok) + ROS()  -> DNA2(site~cdsb)` | Transforms DNA2, ROS by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 2185 | `Unlabeled` | one-way | DNA3, ROS | `kdam2` | internal-state conversion/modification | `DNA3(site~ok) + ROS()  -> DNA3(site~cdsb)` | Transforms DNA3, ROS by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 2186 | `Unlabeled` | one-way | DNA4, ROS | `kdam2` | internal-state conversion/modification | `DNA4(site~ok) + ROS()  -> DNA4(site~cdsb)` | Transforms DNA4, ROS by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 2187 | `Unlabeled` | one-way | DNA5, ROS | `kdam2` | internal-state conversion/modification | `DNA5(site~ok) + ROS()  -> DNA5(site~cdsb)` | Transforms DNA5, ROS by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 2188 | `Unlabeled` | one-way | DNA6, ROS | `kdam2` | internal-state conversion/modification | `DNA6(site~ok) + ROS()  -> DNA6(site~cdsb)` | Transforms DNA6, ROS by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 2189 | `Unlabeled` | one-way | DNA7, ROS | `kdam2` | internal-state conversion/modification | `DNA7(site~ok) + ROS()  -> DNA7(site~cdsb)` | Transforms DNA7, ROS by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 2190 | `Unlabeled` | one-way | DNA8, ROS | `kdam2` | internal-state conversion/modification | `DNA8(site~ok) + ROS()  -> DNA8(site~cdsb)` | Transforms DNA8, ROS by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 2191 | `Unlabeled` | one-way | DNA9, ROS | `kdam2` | internal-state conversion/modification | `DNA9(site~ok) + ROS()  -> DNA9(site~cdsb)` | Transforms DNA9, ROS by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 2192 | `Unlabeled` | one-way | DNA10, ROS | `kdam2` | internal-state conversion/modification | `DNA10(site~ok) + ROS()  -> DNA10(site~cdsb)` | Transforms DNA10, ROS by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 2193 | `Unlabeled` | one-way | DNA11, ROS | `kdam2` | internal-state conversion/modification | `DNA11(site~ok) + ROS()  -> DNA11(site~cdsb)` | Transforms DNA11, ROS by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 2194 | `Unlabeled` | one-way | DNA12, ROS | `kdam2` | internal-state conversion/modification | `DNA12(site~ok) + ROS()  -> DNA12(site~cdsb)` | Transforms DNA12, ROS by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 2195 | `Unlabeled` | one-way | DNA13, ROS | `kdam2` | internal-state conversion/modification | `DNA13(site~ok) + ROS()  -> DNA13(site~cdsb)` | Transforms DNA13, ROS by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 2196 | `Unlabeled` | one-way | DNA14, ROS | `kdam2` | internal-state conversion/modification | `DNA14(site~ok) + ROS()  -> DNA14(site~cdsb)` | Transforms DNA14, ROS by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 2197 | `Unlabeled` | one-way | DNA15, ROS | `kdam2` | internal-state conversion/modification | `DNA15(site~ok) + ROS()  -> DNA15(site~cdsb)` | Transforms DNA15, ROS by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 2198 | `Unlabeled` | one-way | DNA16, ROS | `kdam2` | internal-state conversion/modification | `DNA16(site~ok) + ROS()  -> DNA16(site~cdsb)` | Transforms DNA16, ROS by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 2199 | `Unlabeled` | one-way | DNA17, ROS | `kdam2` | internal-state conversion/modification | `DNA17(site~ok) + ROS()  -> DNA17(site~cdsb)` | Transforms DNA17, ROS by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 2200 | `Unlabeled` | one-way | DNA18, ROS | `kdam2` | internal-state conversion/modification | `DNA18(site~ok) + ROS()  -> DNA18(site~cdsb)` | Transforms DNA18, ROS by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 2201 | `Unlabeled` | one-way | DNA19, ROS | `kdam2` | internal-state conversion/modification | `DNA19(site~ok) + ROS()  -> DNA19(site~cdsb)` | Transforms DNA19, ROS by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 2202 | `Unlabeled` | one-way | DNA20, ROS | `kdam2` | internal-state conversion/modification | `DNA20(site~ok) + ROS()  -> DNA20(site~cdsb)` | Transforms DNA20, ROS by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 2203 | `Unlabeled` | one-way | DNA21, ROS | `kdam2` | internal-state conversion/modification | `DNA21(site~ok) + ROS()  -> DNA21(site~cdsb)` | Transforms DNA21, ROS by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 2204 | `Unlabeled` | one-way | DNA22, ROS | `kdam2` | internal-state conversion/modification | `DNA22(site~ok) + ROS()  -> DNA22(site~cdsb)` | Transforms DNA22, ROS by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 2205 | `Unlabeled` | one-way | DNA23, ROS | `kdam2` | internal-state conversion/modification | `DNA23(site~ok) + ROS()  -> DNA23(site~cdsb)` | Transforms DNA23, ROS by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 2206 | `Unlabeled` | one-way | DNA24, ROS | `kdam2` | internal-state conversion/modification | `DNA24(site~ok) + ROS()  -> DNA24(site~cdsb)` | Transforms DNA24, ROS by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 2207 | `Unlabeled` | one-way | DNA25, ROS | `kdam2` | internal-state conversion/modification | `DNA25(site~ok) + ROS()  -> DNA25(site~cdsb)` | Transforms DNA25, ROS by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 2208 | `Unlabeled` | one-way | DNA26, ROS | `kdam2` | internal-state conversion/modification | `DNA26(site~ok) + ROS()  -> DNA26(site~cdsb)` | Transforms DNA26, ROS by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 2209 | `Unlabeled` | one-way | DNA27, ROS | `kdam2` | internal-state conversion/modification | `DNA27(site~ok) + ROS()  -> DNA27(site~cdsb)` | Transforms DNA27, ROS by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 2210 | `Unlabeled` | one-way | DNA28, ROS | `kdam2` | internal-state conversion/modification | `DNA28(site~ok) + ROS()  -> DNA28(site~cdsb)` | Transforms DNA28, ROS by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 2211 | `Unlabeled` | one-way | DNA29, ROS | `kdam2` | internal-state conversion/modification | `DNA29(site~ok) + ROS()  -> DNA29(site~cdsb)` | Transforms DNA29, ROS by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 2212 | `Unlabeled` | one-way | DNA30, ROS | `kdam2` | internal-state conversion/modification | `DNA30(site~ok) + ROS()  -> DNA30(site~cdsb)` | Transforms DNA30, ROS by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 2213 | `Unlabeled` | one-way | DNA31, ROS | `kdam2` | internal-state conversion/modification | `DNA31(site~ok) + ROS()  -> DNA31(site~cdsb)` | Transforms DNA31, ROS by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 2214 | `Unlabeled` | one-way | DNA32, ROS | `kdam2` | internal-state conversion/modification | `DNA32(site~ok) + ROS()  -> DNA32(site~cdsb)` | Transforms DNA32, ROS by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 2215 | `Unlabeled` | one-way | DNA33, ROS | `kdam2` | internal-state conversion/modification | `DNA33(site~ok) + ROS()  -> DNA33(site~cdsb)` | Transforms DNA33, ROS by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 2216 | `Unlabeled` | one-way | DNA34, ROS | `kdam2` | internal-state conversion/modification | `DNA34(site~ok) + ROS()  -> DNA34(site~cdsb)` | Transforms DNA34, ROS by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 2217 | `Unlabeled` | one-way | DNA35, ROS | `kdam2` | internal-state conversion/modification | `DNA35(site~ok) + ROS()  -> DNA35(site~cdsb)` | Transforms DNA35, ROS by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 2218 | `Unlabeled` | one-way | DNA36, ROS | `kdam2` | internal-state conversion/modification | `DNA36(site~ok) + ROS()  -> DNA36(site~cdsb)` | Transforms DNA36, ROS by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 2219 | `Unlabeled` | one-way | DNA37, ROS | `kdam2` | internal-state conversion/modification | `DNA37(site~ok) + ROS()  -> DNA37(site~cdsb)` | Transforms DNA37, ROS by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 2220 | `Unlabeled` | one-way | DNA38, ROS | `kdam2` | internal-state conversion/modification | `DNA38(site~ok) + ROS()  -> DNA38(site~cdsb)` | Transforms DNA38, ROS by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 2221 | `Unlabeled` | one-way | DNA39, ROS | `kdam2` | internal-state conversion/modification | `DNA39(site~ok) + ROS()  -> DNA39(site~cdsb)` | Transforms DNA39, ROS by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 2222 | `Unlabeled` | one-way | DNA40, ROS | `kdam2` | internal-state conversion/modification | `DNA40(site~ok) + ROS()  -> DNA40(site~cdsb)` | Transforms DNA40, ROS by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 2223 | `Unlabeled` | one-way | DNA41, ROS | `kdam2` | internal-state conversion/modification | `DNA41(site~ok) + ROS()  -> DNA41(site~cdsb)` | Transforms DNA41, ROS by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 2224 | `Unlabeled` | one-way | DNA42, ROS | `kdam2` | internal-state conversion/modification | `DNA42(site~ok) + ROS()  -> DNA42(site~cdsb)` | Transforms DNA42, ROS by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 2225 | `Unlabeled` | one-way | DNA43, ROS | `kdam2` | internal-state conversion/modification | `DNA43(site~ok) + ROS()  -> DNA43(site~cdsb)` | Transforms DNA43, ROS by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 2226 | `Unlabeled` | one-way | DNA44, ROS | `kdam2` | internal-state conversion/modification | `DNA44(site~ok) + ROS()  -> DNA44(site~cdsb)` | Transforms DNA44, ROS by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 2227 | `Unlabeled` | one-way | DNA45, ROS | `kdam2` | internal-state conversion/modification | `DNA45(site~ok) + ROS()  -> DNA45(site~cdsb)` | Transforms DNA45, ROS by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 2228 | `Unlabeled` | one-way | DNA46, ROS | `kdam2` | internal-state conversion/modification | `DNA46(site~ok) + ROS()  -> DNA46(site~cdsb)` | Transforms DNA46, ROS by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 2229 | `Unlabeled` | one-way | DNA47, ROS | `kdam2` | internal-state conversion/modification | `DNA47(site~ok) + ROS()  -> DNA47(site~cdsb)` | Transforms DNA47, ROS by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 2230 | `Unlabeled` | one-way | DNA48, ROS | `kdam2` | internal-state conversion/modification | `DNA48(site~ok) + ROS()  -> DNA48(site~cdsb)` | Transforms DNA48, ROS by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 2231 | `Unlabeled` | one-way | DNA49, ROS | `kdam2` | internal-state conversion/modification | `DNA49(site~ok) + ROS()  -> DNA49(site~cdsb)` | Transforms DNA49, ROS by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 2232 | `Unlabeled` | one-way | DNA50, ROS | `kdam2` | internal-state conversion/modification | `DNA50(site~ok) + ROS()  -> DNA50(site~cdsb)` | Transforms DNA50, ROS by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 2233 | `Unlabeled` | one-way | Ku, ROS | `kox` | internal-state conversion/modification | `Ku(dna,cs,cys~red) + ROS()  -> Ku(dna,cs,cys~ox) + ROS()` | Transforms Ku, ROS by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 2234 | `Unlabeled` | one-way | Ku | `kred` | internal-state conversion/modification | `Ku(dna,cs,cys~ox)  -> Ku(dna,cs,cys~red)` | Transforms Ku by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 2235 | `Unlabeled` | one-way | DNA1, Ku | `kdku3` | state and binding-pattern rewrite | `DNA1(site!1~sdsb).Ku(dna!1,cs,cys~ox)  -> DNA1(site~sdsb) + Ku(dna,cs,cys~ox)` | Transforms DNA1, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2236 | `Unlabeled` | one-way | DNA2, Ku | `kdku3` | state and binding-pattern rewrite | `DNA2(site!1~sdsb).Ku(dna!1,cs,cys~ox)  -> DNA2(site~sdsb) + Ku(dna,cs,cys~ox)` | Transforms DNA2, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2237 | `Unlabeled` | one-way | DNA3, Ku | `kdku3` | state and binding-pattern rewrite | `DNA3(site!1~sdsb).Ku(dna!1,cs,cys~ox)  -> DNA3(site~sdsb) + Ku(dna,cs,cys~ox)` | Transforms DNA3, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2238 | `Unlabeled` | one-way | DNA4, Ku | `kdku3` | state and binding-pattern rewrite | `DNA4(site!1~sdsb).Ku(dna!1,cs,cys~ox)  -> DNA4(site~sdsb) + Ku(dna,cs,cys~ox)` | Transforms DNA4, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2239 | `Unlabeled` | one-way | DNA5, Ku | `kdku3` | state and binding-pattern rewrite | `DNA5(site!1~sdsb).Ku(dna!1,cs,cys~ox)  -> DNA5(site~sdsb) + Ku(dna,cs,cys~ox)` | Transforms DNA5, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2240 | `Unlabeled` | one-way | DNA6, Ku | `kdku3` | state and binding-pattern rewrite | `DNA6(site!1~sdsb).Ku(dna!1,cs,cys~ox)  -> DNA6(site~sdsb) + Ku(dna,cs,cys~ox)` | Transforms DNA6, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2241 | `Unlabeled` | one-way | DNA7, Ku | `kdku3` | state and binding-pattern rewrite | `DNA7(site!1~sdsb).Ku(dna!1,cs,cys~ox)  -> DNA7(site~sdsb) + Ku(dna,cs,cys~ox)` | Transforms DNA7, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2242 | `Unlabeled` | one-way | DNA8, Ku | `kdku3` | state and binding-pattern rewrite | `DNA8(site!1~sdsb).Ku(dna!1,cs,cys~ox)  -> DNA8(site~sdsb) + Ku(dna,cs,cys~ox)` | Transforms DNA8, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2243 | `Unlabeled` | one-way | DNA9, Ku | `kdku3` | state and binding-pattern rewrite | `DNA9(site!1~sdsb).Ku(dna!1,cs,cys~ox)  -> DNA9(site~sdsb) + Ku(dna,cs,cys~ox)` | Transforms DNA9, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2244 | `Unlabeled` | one-way | DNA10, Ku | `kdku3` | state and binding-pattern rewrite | `DNA10(site!1~sdsb).Ku(dna!1,cs,cys~ox)  -> DNA10(site~sdsb) + Ku(dna,cs,cys~ox)` | Transforms DNA10, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2245 | `Unlabeled` | one-way | DNA11, Ku | `kdku3` | state and binding-pattern rewrite | `DNA11(site!1~sdsb).Ku(dna!1,cs,cys~ox)  -> DNA11(site~sdsb) + Ku(dna,cs,cys~ox)` | Transforms DNA11, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2246 | `Unlabeled` | one-way | DNA12, Ku | `kdku3` | state and binding-pattern rewrite | `DNA12(site!1~sdsb).Ku(dna!1,cs,cys~ox)  -> DNA12(site~sdsb) + Ku(dna,cs,cys~ox)` | Transforms DNA12, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2247 | `Unlabeled` | one-way | DNA13, Ku | `kdku3` | state and binding-pattern rewrite | `DNA13(site!1~sdsb).Ku(dna!1,cs,cys~ox)  -> DNA13(site~sdsb) + Ku(dna,cs,cys~ox)` | Transforms DNA13, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2248 | `Unlabeled` | one-way | DNA14, Ku | `kdku3` | state and binding-pattern rewrite | `DNA14(site!1~sdsb).Ku(dna!1,cs,cys~ox)  -> DNA14(site~sdsb) + Ku(dna,cs,cys~ox)` | Transforms DNA14, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2249 | `Unlabeled` | one-way | DNA15, Ku | `kdku3` | state and binding-pattern rewrite | `DNA15(site!1~sdsb).Ku(dna!1,cs,cys~ox)  -> DNA15(site~sdsb) + Ku(dna,cs,cys~ox)` | Transforms DNA15, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2250 | `Unlabeled` | one-way | DNA16, Ku | `kdku3` | state and binding-pattern rewrite | `DNA16(site!1~sdsb).Ku(dna!1,cs,cys~ox)  -> DNA16(site~sdsb) + Ku(dna,cs,cys~ox)` | Transforms DNA16, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

### Rules 2251-2339

| # | Rule label/name | Direction | Participants | Rate/expression | Modeled change | Rule pattern | Technical meaning |
| ---: | --- | --- | --- | --- | --- | --- | --- |

| 2251 | `Unlabeled` | one-way | DNA17, Ku | `kdku3` | state and binding-pattern rewrite | `DNA17(site!1~sdsb).Ku(dna!1,cs,cys~ox)  -> DNA17(site~sdsb) + Ku(dna,cs,cys~ox)` | Transforms DNA17, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2252 | `Unlabeled` | one-way | DNA18, Ku | `kdku3` | state and binding-pattern rewrite | `DNA18(site!1~sdsb).Ku(dna!1,cs,cys~ox)  -> DNA18(site~sdsb) + Ku(dna,cs,cys~ox)` | Transforms DNA18, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2253 | `Unlabeled` | one-way | DNA19, Ku | `kdku3` | state and binding-pattern rewrite | `DNA19(site!1~sdsb).Ku(dna!1,cs,cys~ox)  -> DNA19(site~sdsb) + Ku(dna,cs,cys~ox)` | Transforms DNA19, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2254 | `Unlabeled` | one-way | DNA20, Ku | `kdku3` | state and binding-pattern rewrite | `DNA20(site!1~sdsb).Ku(dna!1,cs,cys~ox)  -> DNA20(site~sdsb) + Ku(dna,cs,cys~ox)` | Transforms DNA20, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2255 | `Unlabeled` | one-way | DNA21, Ku | `kdku3` | state and binding-pattern rewrite | `DNA21(site!1~sdsb).Ku(dna!1,cs,cys~ox)  -> DNA21(site~sdsb) + Ku(dna,cs,cys~ox)` | Transforms DNA21, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2256 | `Unlabeled` | one-way | DNA22, Ku | `kdku3` | state and binding-pattern rewrite | `DNA22(site!1~sdsb).Ku(dna!1,cs,cys~ox)  -> DNA22(site~sdsb) + Ku(dna,cs,cys~ox)` | Transforms DNA22, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2257 | `Unlabeled` | one-way | DNA23, Ku | `kdku3` | state and binding-pattern rewrite | `DNA23(site!1~sdsb).Ku(dna!1,cs,cys~ox)  -> DNA23(site~sdsb) + Ku(dna,cs,cys~ox)` | Transforms DNA23, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2258 | `Unlabeled` | one-way | DNA24, Ku | `kdku3` | state and binding-pattern rewrite | `DNA24(site!1~sdsb).Ku(dna!1,cs,cys~ox)  -> DNA24(site~sdsb) + Ku(dna,cs,cys~ox)` | Transforms DNA24, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2259 | `Unlabeled` | one-way | DNA25, Ku | `kdku3` | state and binding-pattern rewrite | `DNA25(site!1~sdsb).Ku(dna!1,cs,cys~ox)  -> DNA25(site~sdsb) + Ku(dna,cs,cys~ox)` | Transforms DNA25, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2260 | `Unlabeled` | one-way | DNA26, Ku | `kdku3` | state and binding-pattern rewrite | `DNA26(site!1~sdsb).Ku(dna!1,cs,cys~ox)  -> DNA26(site~sdsb) + Ku(dna,cs,cys~ox)` | Transforms DNA26, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2261 | `Unlabeled` | one-way | DNA27, Ku | `kdku3` | state and binding-pattern rewrite | `DNA27(site!1~sdsb).Ku(dna!1,cs,cys~ox)  -> DNA27(site~sdsb) + Ku(dna,cs,cys~ox)` | Transforms DNA27, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2262 | `Unlabeled` | one-way | DNA28, Ku | `kdku3` | state and binding-pattern rewrite | `DNA28(site!1~sdsb).Ku(dna!1,cs,cys~ox)  -> DNA28(site~sdsb) + Ku(dna,cs,cys~ox)` | Transforms DNA28, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2263 | `Unlabeled` | one-way | DNA29, Ku | `kdku3` | state and binding-pattern rewrite | `DNA29(site!1~sdsb).Ku(dna!1,cs,cys~ox)  -> DNA29(site~sdsb) + Ku(dna,cs,cys~ox)` | Transforms DNA29, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2264 | `Unlabeled` | one-way | DNA30, Ku | `kdku3` | state and binding-pattern rewrite | `DNA30(site!1~sdsb).Ku(dna!1,cs,cys~ox)  -> DNA30(site~sdsb) + Ku(dna,cs,cys~ox)` | Transforms DNA30, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2265 | `Unlabeled` | one-way | DNA31, Ku | `kdku3` | state and binding-pattern rewrite | `DNA31(site!1~sdsb).Ku(dna!1,cs,cys~ox)  -> DNA31(site~sdsb) + Ku(dna,cs,cys~ox)` | Transforms DNA31, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2266 | `Unlabeled` | one-way | DNA32, Ku | `kdku3` | state and binding-pattern rewrite | `DNA32(site!1~sdsb).Ku(dna!1,cs,cys~ox)  -> DNA32(site~sdsb) + Ku(dna,cs,cys~ox)` | Transforms DNA32, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2267 | `Unlabeled` | one-way | DNA33, Ku | `kdku3` | state and binding-pattern rewrite | `DNA33(site!1~sdsb).Ku(dna!1,cs,cys~ox)  -> DNA33(site~sdsb) + Ku(dna,cs,cys~ox)` | Transforms DNA33, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2268 | `Unlabeled` | one-way | DNA34, Ku | `kdku3` | state and binding-pattern rewrite | `DNA34(site!1~sdsb).Ku(dna!1,cs,cys~ox)  -> DNA34(site~sdsb) + Ku(dna,cs,cys~ox)` | Transforms DNA34, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2269 | `Unlabeled` | one-way | DNA35, Ku | `kdku3` | state and binding-pattern rewrite | `DNA35(site!1~sdsb).Ku(dna!1,cs,cys~ox)  -> DNA35(site~sdsb) + Ku(dna,cs,cys~ox)` | Transforms DNA35, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2270 | `Unlabeled` | one-way | DNA36, Ku | `kdku3` | state and binding-pattern rewrite | `DNA36(site!1~sdsb).Ku(dna!1,cs,cys~ox)  -> DNA36(site~sdsb) + Ku(dna,cs,cys~ox)` | Transforms DNA36, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2271 | `Unlabeled` | one-way | DNA37, Ku | `kdku3` | state and binding-pattern rewrite | `DNA37(site!1~sdsb).Ku(dna!1,cs,cys~ox)  -> DNA37(site~sdsb) + Ku(dna,cs,cys~ox)` | Transforms DNA37, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2272 | `Unlabeled` | one-way | DNA38, Ku | `kdku3` | state and binding-pattern rewrite | `DNA38(site!1~sdsb).Ku(dna!1,cs,cys~ox)  -> DNA38(site~sdsb) + Ku(dna,cs,cys~ox)` | Transforms DNA38, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2273 | `Unlabeled` | one-way | DNA39, Ku | `kdku3` | state and binding-pattern rewrite | `DNA39(site!1~sdsb).Ku(dna!1,cs,cys~ox)  -> DNA39(site~sdsb) + Ku(dna,cs,cys~ox)` | Transforms DNA39, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2274 | `Unlabeled` | one-way | DNA40, Ku | `kdku3` | state and binding-pattern rewrite | `DNA40(site!1~sdsb).Ku(dna!1,cs,cys~ox)  -> DNA40(site~sdsb) + Ku(dna,cs,cys~ox)` | Transforms DNA40, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2275 | `Unlabeled` | one-way | DNA41, Ku | `kdku3` | state and binding-pattern rewrite | `DNA41(site!1~sdsb).Ku(dna!1,cs,cys~ox)  -> DNA41(site~sdsb) + Ku(dna,cs,cys~ox)` | Transforms DNA41, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2276 | `Unlabeled` | one-way | DNA42, Ku | `kdku3` | state and binding-pattern rewrite | `DNA42(site!1~sdsb).Ku(dna!1,cs,cys~ox)  -> DNA42(site~sdsb) + Ku(dna,cs,cys~ox)` | Transforms DNA42, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2277 | `Unlabeled` | one-way | DNA43, Ku | `kdku3` | state and binding-pattern rewrite | `DNA43(site!1~sdsb).Ku(dna!1,cs,cys~ox)  -> DNA43(site~sdsb) + Ku(dna,cs,cys~ox)` | Transforms DNA43, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2278 | `Unlabeled` | one-way | DNA44, Ku | `kdku3` | state and binding-pattern rewrite | `DNA44(site!1~sdsb).Ku(dna!1,cs,cys~ox)  -> DNA44(site~sdsb) + Ku(dna,cs,cys~ox)` | Transforms DNA44, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2279 | `Unlabeled` | one-way | DNA45, Ku | `kdku3` | state and binding-pattern rewrite | `DNA45(site!1~sdsb).Ku(dna!1,cs,cys~ox)  -> DNA45(site~sdsb) + Ku(dna,cs,cys~ox)` | Transforms DNA45, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2280 | `Unlabeled` | one-way | DNA46, Ku | `kdku3` | state and binding-pattern rewrite | `DNA46(site!1~sdsb).Ku(dna!1,cs,cys~ox)  -> DNA46(site~sdsb) + Ku(dna,cs,cys~ox)` | Transforms DNA46, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2281 | `Unlabeled` | one-way | DNA47, Ku | `kdku3` | state and binding-pattern rewrite | `DNA47(site!1~sdsb).Ku(dna!1,cs,cys~ox)  -> DNA47(site~sdsb) + Ku(dna,cs,cys~ox)` | Transforms DNA47, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2282 | `Unlabeled` | one-way | DNA48, Ku | `kdku3` | state and binding-pattern rewrite | `DNA48(site!1~sdsb).Ku(dna!1,cs,cys~ox)  -> DNA48(site~sdsb) + Ku(dna,cs,cys~ox)` | Transforms DNA48, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2283 | `Unlabeled` | one-way | DNA49, Ku | `kdku3` | state and binding-pattern rewrite | `DNA49(site!1~sdsb).Ku(dna!1,cs,cys~ox)  -> DNA49(site~sdsb) + Ku(dna,cs,cys~ox)` | Transforms DNA49, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2284 | `Unlabeled` | one-way | DNA50, Ku | `kdku3` | state and binding-pattern rewrite | `DNA50(site!1~sdsb).Ku(dna!1,cs,cys~ox)  -> DNA50(site~sdsb) + Ku(dna,cs,cys~ox)` | Transforms DNA50, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2285 | `Unlabeled` | one-way | DNA1, Ku | `kdku4` | state and binding-pattern rewrite | `DNA1(site!1~cdsb).Ku(dna!1,cs,cys~ox)  -> DNA1(site~cdsb) + Ku(dna,cs,cys~ox)` | Transforms DNA1, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2286 | `Unlabeled` | one-way | DNA2, Ku | `kdku4` | state and binding-pattern rewrite | `DNA2(site!1~cdsb).Ku(dna!1,cs,cys~ox)  -> DNA2(site~cdsb) + Ku(dna,cs,cys~ox)` | Transforms DNA2, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2287 | `Unlabeled` | one-way | DNA3, Ku | `kdku4` | state and binding-pattern rewrite | `DNA3(site!1~cdsb).Ku(dna!1,cs,cys~ox)  -> DNA3(site~cdsb) + Ku(dna,cs,cys~ox)` | Transforms DNA3, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2288 | `Unlabeled` | one-way | DNA4, Ku | `kdku4` | state and binding-pattern rewrite | `DNA4(site!1~cdsb).Ku(dna!1,cs,cys~ox)  -> DNA4(site~cdsb) + Ku(dna,cs,cys~ox)` | Transforms DNA4, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2289 | `Unlabeled` | one-way | DNA5, Ku | `kdku4` | state and binding-pattern rewrite | `DNA5(site!1~cdsb).Ku(dna!1,cs,cys~ox)  -> DNA5(site~cdsb) + Ku(dna,cs,cys~ox)` | Transforms DNA5, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2290 | `Unlabeled` | one-way | DNA6, Ku | `kdku4` | state and binding-pattern rewrite | `DNA6(site!1~cdsb).Ku(dna!1,cs,cys~ox)  -> DNA6(site~cdsb) + Ku(dna,cs,cys~ox)` | Transforms DNA6, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2291 | `Unlabeled` | one-way | DNA7, Ku | `kdku4` | state and binding-pattern rewrite | `DNA7(site!1~cdsb).Ku(dna!1,cs,cys~ox)  -> DNA7(site~cdsb) + Ku(dna,cs,cys~ox)` | Transforms DNA7, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2292 | `Unlabeled` | one-way | DNA8, Ku | `kdku4` | state and binding-pattern rewrite | `DNA8(site!1~cdsb).Ku(dna!1,cs,cys~ox)  -> DNA8(site~cdsb) + Ku(dna,cs,cys~ox)` | Transforms DNA8, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2293 | `Unlabeled` | one-way | DNA9, Ku | `kdku4` | state and binding-pattern rewrite | `DNA9(site!1~cdsb).Ku(dna!1,cs,cys~ox)  -> DNA9(site~cdsb) + Ku(dna,cs,cys~ox)` | Transforms DNA9, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2294 | `Unlabeled` | one-way | DNA10, Ku | `kdku4` | state and binding-pattern rewrite | `DNA10(site!1~cdsb).Ku(dna!1,cs,cys~ox)  -> DNA10(site~cdsb) + Ku(dna,cs,cys~ox)` | Transforms DNA10, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2295 | `Unlabeled` | one-way | DNA11, Ku | `kdku4` | state and binding-pattern rewrite | `DNA11(site!1~cdsb).Ku(dna!1,cs,cys~ox)  -> DNA11(site~cdsb) + Ku(dna,cs,cys~ox)` | Transforms DNA11, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2296 | `Unlabeled` | one-way | DNA12, Ku | `kdku4` | state and binding-pattern rewrite | `DNA12(site!1~cdsb).Ku(dna!1,cs,cys~ox)  -> DNA12(site~cdsb) + Ku(dna,cs,cys~ox)` | Transforms DNA12, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2297 | `Unlabeled` | one-way | DNA13, Ku | `kdku4` | state and binding-pattern rewrite | `DNA13(site!1~cdsb).Ku(dna!1,cs,cys~ox)  -> DNA13(site~cdsb) + Ku(dna,cs,cys~ox)` | Transforms DNA13, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2298 | `Unlabeled` | one-way | DNA14, Ku | `kdku4` | state and binding-pattern rewrite | `DNA14(site!1~cdsb).Ku(dna!1,cs,cys~ox)  -> DNA14(site~cdsb) + Ku(dna,cs,cys~ox)` | Transforms DNA14, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2299 | `Unlabeled` | one-way | DNA15, Ku | `kdku4` | state and binding-pattern rewrite | `DNA15(site!1~cdsb).Ku(dna!1,cs,cys~ox)  -> DNA15(site~cdsb) + Ku(dna,cs,cys~ox)` | Transforms DNA15, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2300 | `Unlabeled` | one-way | DNA16, Ku | `kdku4` | state and binding-pattern rewrite | `DNA16(site!1~cdsb).Ku(dna!1,cs,cys~ox)  -> DNA16(site~cdsb) + Ku(dna,cs,cys~ox)` | Transforms DNA16, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2301 | `Unlabeled` | one-way | DNA17, Ku | `kdku4` | state and binding-pattern rewrite | `DNA17(site!1~cdsb).Ku(dna!1,cs,cys~ox)  -> DNA17(site~cdsb) + Ku(dna,cs,cys~ox)` | Transforms DNA17, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2302 | `Unlabeled` | one-way | DNA18, Ku | `kdku4` | state and binding-pattern rewrite | `DNA18(site!1~cdsb).Ku(dna!1,cs,cys~ox)  -> DNA18(site~cdsb) + Ku(dna,cs,cys~ox)` | Transforms DNA18, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2303 | `Unlabeled` | one-way | DNA19, Ku | `kdku4` | state and binding-pattern rewrite | `DNA19(site!1~cdsb).Ku(dna!1,cs,cys~ox)  -> DNA19(site~cdsb) + Ku(dna,cs,cys~ox)` | Transforms DNA19, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2304 | `Unlabeled` | one-way | DNA20, Ku | `kdku4` | state and binding-pattern rewrite | `DNA20(site!1~cdsb).Ku(dna!1,cs,cys~ox)  -> DNA20(site~cdsb) + Ku(dna,cs,cys~ox)` | Transforms DNA20, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2305 | `Unlabeled` | one-way | DNA21, Ku | `kdku4` | state and binding-pattern rewrite | `DNA21(site!1~cdsb).Ku(dna!1,cs,cys~ox)  -> DNA21(site~cdsb) + Ku(dna,cs,cys~ox)` | Transforms DNA21, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2306 | `Unlabeled` | one-way | DNA22, Ku | `kdku4` | state and binding-pattern rewrite | `DNA22(site!1~cdsb).Ku(dna!1,cs,cys~ox)  -> DNA22(site~cdsb) + Ku(dna,cs,cys~ox)` | Transforms DNA22, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2307 | `Unlabeled` | one-way | DNA23, Ku | `kdku4` | state and binding-pattern rewrite | `DNA23(site!1~cdsb).Ku(dna!1,cs,cys~ox)  -> DNA23(site~cdsb) + Ku(dna,cs,cys~ox)` | Transforms DNA23, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2308 | `Unlabeled` | one-way | DNA24, Ku | `kdku4` | state and binding-pattern rewrite | `DNA24(site!1~cdsb).Ku(dna!1,cs,cys~ox)  -> DNA24(site~cdsb) + Ku(dna,cs,cys~ox)` | Transforms DNA24, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2309 | `Unlabeled` | one-way | DNA25, Ku | `kdku4` | state and binding-pattern rewrite | `DNA25(site!1~cdsb).Ku(dna!1,cs,cys~ox)  -> DNA25(site~cdsb) + Ku(dna,cs,cys~ox)` | Transforms DNA25, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2310 | `Unlabeled` | one-way | DNA26, Ku | `kdku4` | state and binding-pattern rewrite | `DNA26(site!1~cdsb).Ku(dna!1,cs,cys~ox)  -> DNA26(site~cdsb) + Ku(dna,cs,cys~ox)` | Transforms DNA26, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2311 | `Unlabeled` | one-way | DNA27, Ku | `kdku4` | state and binding-pattern rewrite | `DNA27(site!1~cdsb).Ku(dna!1,cs,cys~ox)  -> DNA27(site~cdsb) + Ku(dna,cs,cys~ox)` | Transforms DNA27, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2312 | `Unlabeled` | one-way | DNA28, Ku | `kdku4` | state and binding-pattern rewrite | `DNA28(site!1~cdsb).Ku(dna!1,cs,cys~ox)  -> DNA28(site~cdsb) + Ku(dna,cs,cys~ox)` | Transforms DNA28, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2313 | `Unlabeled` | one-way | DNA29, Ku | `kdku4` | state and binding-pattern rewrite | `DNA29(site!1~cdsb).Ku(dna!1,cs,cys~ox)  -> DNA29(site~cdsb) + Ku(dna,cs,cys~ox)` | Transforms DNA29, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2314 | `Unlabeled` | one-way | DNA30, Ku | `kdku4` | state and binding-pattern rewrite | `DNA30(site!1~cdsb).Ku(dna!1,cs,cys~ox)  -> DNA30(site~cdsb) + Ku(dna,cs,cys~ox)` | Transforms DNA30, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2315 | `Unlabeled` | one-way | DNA31, Ku | `kdku4` | state and binding-pattern rewrite | `DNA31(site!1~cdsb).Ku(dna!1,cs,cys~ox)  -> DNA31(site~cdsb) + Ku(dna,cs,cys~ox)` | Transforms DNA31, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2316 | `Unlabeled` | one-way | DNA32, Ku | `kdku4` | state and binding-pattern rewrite | `DNA32(site!1~cdsb).Ku(dna!1,cs,cys~ox)  -> DNA32(site~cdsb) + Ku(dna,cs,cys~ox)` | Transforms DNA32, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2317 | `Unlabeled` | one-way | DNA33, Ku | `kdku4` | state and binding-pattern rewrite | `DNA33(site!1~cdsb).Ku(dna!1,cs,cys~ox)  -> DNA33(site~cdsb) + Ku(dna,cs,cys~ox)` | Transforms DNA33, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2318 | `Unlabeled` | one-way | DNA34, Ku | `kdku4` | state and binding-pattern rewrite | `DNA34(site!1~cdsb).Ku(dna!1,cs,cys~ox)  -> DNA34(site~cdsb) + Ku(dna,cs,cys~ox)` | Transforms DNA34, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2319 | `Unlabeled` | one-way | DNA35, Ku | `kdku4` | state and binding-pattern rewrite | `DNA35(site!1~cdsb).Ku(dna!1,cs,cys~ox)  -> DNA35(site~cdsb) + Ku(dna,cs,cys~ox)` | Transforms DNA35, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2320 | `Unlabeled` | one-way | DNA36, Ku | `kdku4` | state and binding-pattern rewrite | `DNA36(site!1~cdsb).Ku(dna!1,cs,cys~ox)  -> DNA36(site~cdsb) + Ku(dna,cs,cys~ox)` | Transforms DNA36, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2321 | `Unlabeled` | one-way | DNA37, Ku | `kdku4` | state and binding-pattern rewrite | `DNA37(site!1~cdsb).Ku(dna!1,cs,cys~ox)  -> DNA37(site~cdsb) + Ku(dna,cs,cys~ox)` | Transforms DNA37, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2322 | `Unlabeled` | one-way | DNA38, Ku | `kdku4` | state and binding-pattern rewrite | `DNA38(site!1~cdsb).Ku(dna!1,cs,cys~ox)  -> DNA38(site~cdsb) + Ku(dna,cs,cys~ox)` | Transforms DNA38, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2323 | `Unlabeled` | one-way | DNA39, Ku | `kdku4` | state and binding-pattern rewrite | `DNA39(site!1~cdsb).Ku(dna!1,cs,cys~ox)  -> DNA39(site~cdsb) + Ku(dna,cs,cys~ox)` | Transforms DNA39, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2324 | `Unlabeled` | one-way | DNA40, Ku | `kdku4` | state and binding-pattern rewrite | `DNA40(site!1~cdsb).Ku(dna!1,cs,cys~ox)  -> DNA40(site~cdsb) + Ku(dna,cs,cys~ox)` | Transforms DNA40, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2325 | `Unlabeled` | one-way | DNA41, Ku | `kdku4` | state and binding-pattern rewrite | `DNA41(site!1~cdsb).Ku(dna!1,cs,cys~ox)  -> DNA41(site~cdsb) + Ku(dna,cs,cys~ox)` | Transforms DNA41, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2326 | `Unlabeled` | one-way | DNA42, Ku | `kdku4` | state and binding-pattern rewrite | `DNA42(site!1~cdsb).Ku(dna!1,cs,cys~ox)  -> DNA42(site~cdsb) + Ku(dna,cs,cys~ox)` | Transforms DNA42, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2327 | `Unlabeled` | one-way | DNA43, Ku | `kdku4` | state and binding-pattern rewrite | `DNA43(site!1~cdsb).Ku(dna!1,cs,cys~ox)  -> DNA43(site~cdsb) + Ku(dna,cs,cys~ox)` | Transforms DNA43, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2328 | `Unlabeled` | one-way | DNA44, Ku | `kdku4` | state and binding-pattern rewrite | `DNA44(site!1~cdsb).Ku(dna!1,cs,cys~ox)  -> DNA44(site~cdsb) + Ku(dna,cs,cys~ox)` | Transforms DNA44, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2329 | `Unlabeled` | one-way | DNA45, Ku | `kdku4` | state and binding-pattern rewrite | `DNA45(site!1~cdsb).Ku(dna!1,cs,cys~ox)  -> DNA45(site~cdsb) + Ku(dna,cs,cys~ox)` | Transforms DNA45, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2330 | `Unlabeled` | one-way | DNA46, Ku | `kdku4` | state and binding-pattern rewrite | `DNA46(site!1~cdsb).Ku(dna!1,cs,cys~ox)  -> DNA46(site~cdsb) + Ku(dna,cs,cys~ox)` | Transforms DNA46, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2331 | `Unlabeled` | one-way | DNA47, Ku | `kdku4` | state and binding-pattern rewrite | `DNA47(site!1~cdsb).Ku(dna!1,cs,cys~ox)  -> DNA47(site~cdsb) + Ku(dna,cs,cys~ox)` | Transforms DNA47, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2332 | `Unlabeled` | one-way | DNA48, Ku | `kdku4` | state and binding-pattern rewrite | `DNA48(site!1~cdsb).Ku(dna!1,cs,cys~ox)  -> DNA48(site~cdsb) + Ku(dna,cs,cys~ox)` | Transforms DNA48, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2333 | `Unlabeled` | one-way | DNA49, Ku | `kdku4` | state and binding-pattern rewrite | `DNA49(site!1~cdsb).Ku(dna!1,cs,cys~ox)  -> DNA49(site~cdsb) + Ku(dna,cs,cys~ox)` | Transforms DNA49, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2334 | `Unlabeled` | one-way | DNA50, Ku | `kdku4` | state and binding-pattern rewrite | `DNA50(site!1~cdsb).Ku(dna!1,cs,cys~ox)  -> DNA50(site~cdsb) + Ku(dna,cs,cys~ox)` | Transforms DNA50, Ku by state and binding-pattern rewrite; see the exact pattern for affected sites/states/bonds. |

| 2335 | `Unlabeled` | one-way | Sen | `kplus()` | internal-state conversion/modification | `Sen(int~?,State~normal)  -> Sen(int~PLUS,State~normal)` | Transforms Sen by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 2336 | `Unlabeled` | one-way | Sen | `kminus()` | internal-state conversion/modification | `Sen(int~?,State~normal)  -> Sen(int~MINUS,State~normal)` | Transforms Sen by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 2337 | `Unlabeled` | one-way | Sen | `ksen` | internal-state conversion/modification | `Sen(int~10,State~normal)  -> Sen(int~10,State~sen)` | Transforms Sen by internal-state conversion/modification; see the exact pattern for affected sites/states/bonds. |

| 2338 | `Unlabeled` | one-way | Ku, Sink, kKuDown | `kKustop()` | sink/degradation/removal | `Ku(dna,cs,cys~?)  -> Sink() kKuDown() *` | Transforms Ku, Sink, kKuDown by sink/degradation/removal; see the exact pattern for affected sites/states/bonds. |

| 2339 | `Unlabeled` | one-way | PARP, Sink, kParpDown | `kParpstop()` | sink/degradation/removal | `PARP(dna,liIII)  -> Sink() kParpDown() *` | Transforms PARP, Sink, kParpDown by sink/degradation/removal; see the exact pattern for affected sites/states/bonds. |

## 7. Observables and technical readouts

| Observable | Type | Pattern / target | Technical interpretation |
| --- | --- | --- | --- |
| `Time` | `Molecules` | `Time()` | Reports the BNGL pattern for downstream plotting or rate expressions. |
| `p53` | `Molecules` | `p53()` | Reports the BNGL pattern for downstream plotting or rate expressions. |
| `p53_Bound` | `Molecules` | `p53(Site1!1~u).MDM2(Site1!1~u)` | Reports bound or complexed species matching the pattern. |
| `p53_Phos` | `Molecules` | `p53(Site1~p)` | Reports phosphorylated or modified species matching the pattern. |
| `p53_Unphos` | `Molecules` | `p53(Site1~u)` | Reports phosphorylated or modified species matching the pattern. |
| `p21` | `Molecules` | `p21(step~3)` | Reports the BNGL pattern for downstream plotting or rate expressions. |
| `p38p` | `Molecules` | `p38(Site1~p)` | Reports phosphorylated or modified species matching the pattern. |
| `p38u` | `Molecules` | `p38(Site1~u)` | Reports the BNGL pattern for downstream plotting or rate expressions. |
| `ROS` | `Molecules` | `ROS()` | Reports the BNGL pattern for downstream plotting or rate expressions. |
| `p53_mRNA` | `Molecules` | `p53_mRNA()` | Reports the BNGL pattern for downstream plotting or rate expressions. |
| `MDM2_Phos` | `Molecules` | `MDM2(Site1~p)` | Reports phosphorylated or modified species matching the pattern. |
| `MDM2_Unphos` | `Molecules` | `MDM2(Site1~u)` | Reports phosphorylated or modified species matching the pattern. |
| `MDM2_mRNA` | `Molecules` | `MDM2_mRNA()` | Reports the BNGL pattern for downstream plotting or rate expressions. |
| `p21_mRNA` | `Molecules` | `p21_mRNA()` | Reports the BNGL pattern for downstream plotting or rate expressions. |
| `GADD45` | `Molecules` | `GADD45()` | Reports the BNGL pattern for downstream plotting or rate expressions. |
| `ATM0` | `Molecules` | `ATM(state~0)` | Reports the BNGL pattern for downstream plotting or rate expressions. |
| `ATM1` | `Molecules` | `ATM(state~1)` | Reports the BNGL pattern for downstream plotting or rate expressions. |
| `ATM2` | `Molecules` | `ATM(state~2)` | Reports the BNGL pattern for downstream plotting or rate expressions. |
| `ATM3` | `Molecules` | `ATM(state~3)` | Reports the BNGL pattern for downstream plotting or rate expressions. |
| `ATM4` | `Molecules` | `ATM(state~4)` | Reports the BNGL pattern for downstream plotting or rate expressions. |
| `ATM5` | `Molecules` | `ATM(state~5)` | Reports the BNGL pattern for downstream plotting or rate expressions. |
| `ATM6` | `Molecules` | `ATM(state~6)` | Reports the BNGL pattern for downstream plotting or rate expressions. |
| `ATM7` | `Molecules` | `ATM(state~7)` | Reports the BNGL pattern for downstream plotting or rate expressions. |
| `ATM8` | `Molecules` | `ATM(state~8)` | Reports the BNGL pattern for downstream plotting or rate expressions. |
| `ATM9` | `Molecules` | `ATM(state~9)` | Reports the BNGL pattern for downstream plotting or rate expressions. |
| `ATM10` | `Molecules` | `ATM(state~10)` | Reports the BNGL pattern for downstream plotting or rate expressions. |
| `ATM11` | `Molecules` | `ATM(state~11)` | Reports the BNGL pattern for downstream plotting or rate expressions. |
| `ATM12` | `Molecules` | `ATM(state~12)` | Reports the BNGL pattern for downstream plotting or rate expressions. |
| `ATM13` | `Molecules` | `ATM(state~13)` | Reports the BNGL pattern for downstream plotting or rate expressions. |
| `ATM14` | `Molecules` | `ATM(state~14)` | Reports the BNGL pattern for downstream plotting or rate expressions. |
| `ATM15` | `Molecules` | `ATM(state~15)` | Reports the BNGL pattern for downstream plotting or rate expressions. |
| `ATM16` | `Molecules` | `ATM(state~16)` | Reports the BNGL pattern for downstream plotting or rate expressions. |
| `ATM17` | `Molecules` | `ATM(state~17)` | Reports the BNGL pattern for downstream plotting or rate expressions. |
| `ATM18` | `Molecules` | `ATM(state~18)` | Reports the BNGL pattern for downstream plotting or rate expressions. |
| `ATM19` | `Molecules` | `ATM(state~19)` | Reports the BNGL pattern for downstream plotting or rate expressions. |
| `ATM20` | `Molecules` | `ATM(state~20)` | Reports the BNGL pattern for downstream plotting or rate expressions. |
| `ATM21` | `Molecules` | `ATM(state~21)` | Reports the BNGL pattern for downstream plotting or rate expressions. |
| `ATM22` | `Molecules` | `ATM(state~22)` | Reports the BNGL pattern for downstream plotting or rate expressions. |
| `ATM23` | `Molecules` | `ATM(state~23)` | Reports the BNGL pattern for downstream plotting or rate expressions. |
| `ATM24` | `Molecules` | `ATM(state~24)` | Reports the BNGL pattern for downstream plotting or rate expressions. |
| `ATM25` | `Molecules` | `ATM(state~25)` | Reports the BNGL pattern for downstream plotting or rate expressions. |
| `ATM26` | `Molecules` | `ATM(state~26)` | Reports the BNGL pattern for downstream plotting or rate expressions. |
| `ATM27` | `Molecules` | `ATM(state~27)` | Reports the BNGL pattern for downstream plotting or rate expressions. |
| `ATM28` | `Molecules` | `ATM(state~28)` | Reports the BNGL pattern for downstream plotting or rate expressions. |
| `ATM29` | `Molecules` | `ATM(state~29)` | Reports the BNGL pattern for downstream plotting or rate expressions. |
| `ATM30` | `Molecules` | `ATM(state~30)` | Reports the BNGL pattern for downstream plotting or rate expressions. |
| `ATM31` | `Molecules` | `ATM(state~31)` | Reports the BNGL pattern for downstream plotting or rate expressions. |
| `ATM32` | `Molecules` | `ATM(state~32)` | Reports the BNGL pattern for downstream plotting or rate expressions. |
| `ATM33` | `Molecules` | `ATM(state~33)` | Reports the BNGL pattern for downstream plotting or rate expressions. |
| `ATM34` | `Molecules` | `ATM(state~34)` | Reports the BNGL pattern for downstream plotting or rate expressions. |
| `ATM35` | `Molecules` | `ATM(state~35)` | Reports the BNGL pattern for downstream plotting or rate expressions. |
| `ATM36` | `Molecules` | `ATM(state~36)` | Reports the BNGL pattern for downstream plotting or rate expressions. |
| `ATM37` | `Molecules` | `ATM(state~37)` | Reports the BNGL pattern for downstream plotting or rate expressions. |
| `ATM38` | `Molecules` | `ATM(state~38)` | Reports the BNGL pattern for downstream plotting or rate expressions. |
| `ATM39` | `Molecules` | `ATM(state~39)` | Reports the BNGL pattern for downstream plotting or rate expressions. |
| `ATM40` | `Molecules` | `ATM(state~40)` | Reports the BNGL pattern for downstream plotting or rate expressions. |
| `ATM41` | `Molecules` | `ATM(state~41)` | Reports the BNGL pattern for downstream plotting or rate expressions. |
| `ATM42` | `Molecules` | `ATM(state~42)` | Reports the BNGL pattern for downstream plotting or rate expressions. |
| `ATM43` | `Molecules` | `ATM(state~43)` | Reports the BNGL pattern for downstream plotting or rate expressions. |
| `ATM44` | `Molecules` | `ATM(state~44)` | Reports the BNGL pattern for downstream plotting or rate expressions. |
| `ATM45` | `Molecules` | `ATM(state~45)` | Reports the BNGL pattern for downstream plotting or rate expressions. |
| `ATM46` | `Molecules` | `ATM(state~46)` | Reports the BNGL pattern for downstream plotting or rate expressions. |
| `ATM47` | `Molecules` | `ATM(state~47)` | Reports the BNGL pattern for downstream plotting or rate expressions. |
| `ATM48` | `Molecules` | `ATM(state~48)` | Reports the BNGL pattern for downstream plotting or rate expressions. |
| `ATM49` | `Molecules` | `ATM(state~49)` | Reports the BNGL pattern for downstream plotting or rate expressions. |
| `ATM50` | `Molecules` | `ATM(state~50)` | Reports the BNGL pattern for downstream plotting or rate expressions. |
| `Damage_Foci_1` | `Molecules` | `DNA1(site!?~?,h2ax~foc)` | Reports the BNGL pattern for downstream plotting or rate expressions. |
| `Complete_Damage_Foci_1` | `Molecules` | `DNA1(h2ax!1~foc).ATM(state~1,h2ax!1)` | Reports bound or complexed species matching the pattern. |
| `Damage_Foci_2` | `Molecules` | `DNA2(site!?~?,h2ax~foc)` | Reports the BNGL pattern for downstream plotting or rate expressions. |
| `Complete_Damage_Foci_2` | `Molecules` | `DNA2(h2ax!1~foc).ATM(state~2,h2ax!1)` | Reports bound or complexed species matching the pattern. |
| `Damage_Foci_3` | `Molecules` | `DNA3(site!?~?,h2ax~foc)` | Reports the BNGL pattern for downstream plotting or rate expressions. |
| `Complete_Damage_Foci_3` | `Molecules` | `DNA3(h2ax!1~foc).ATM(state~3,h2ax!1)` | Reports bound or complexed species matching the pattern. |
| `Damage_Foci_4` | `Molecules` | `DNA4(site!?~?,h2ax~foc)` | Reports the BNGL pattern for downstream plotting or rate expressions. |
| `Complete_Damage_Foci_4` | `Molecules` | `DNA4(h2ax!1~foc).ATM(state~4,h2ax!1)` | Reports bound or complexed species matching the pattern. |
| `Damage_Foci_5` | `Molecules` | `DNA5(site!?~?,h2ax~foc)` | Reports the BNGL pattern for downstream plotting or rate expressions. |
| `Complete_Damage_Foci_5` | `Molecules` | `DNA5(h2ax!1~foc).ATM(state~5,h2ax!1)` | Reports bound or complexed species matching the pattern. |
| `Damage_Foci_6` | `Molecules` | `DNA6(site!?~?,h2ax~foc)` | Reports the BNGL pattern for downstream plotting or rate expressions. |
| `Complete_Damage_Foci_6` | `Molecules` | `DNA6(h2ax!1~foc).ATM(state~6,h2ax!1)` | Reports bound or complexed species matching the pattern. |
| `Damage_Foci_7` | `Molecules` | `DNA7(site!?~?,h2ax~foc)` | Reports the BNGL pattern for downstream plotting or rate expressions. |
| `Complete_Damage_Foci_7` | `Molecules` | `DNA7(h2ax!1~foc).ATM(state~7,h2ax!1)` | Reports bound or complexed species matching the pattern. |
| `Damage_Foci_8` | `Molecules` | `DNA8(site!?~?,h2ax~foc)` | Reports the BNGL pattern for downstream plotting or rate expressions. |
| `Complete_Damage_Foci_8` | `Molecules` | `DNA8(h2ax!1~foc).ATM(state~8,h2ax!1)` | Reports bound or complexed species matching the pattern. |
| `Damage_Foci_9` | `Molecules` | `DNA9(site!?~?,h2ax~foc)` | Reports the BNGL pattern for downstream plotting or rate expressions. |
| `Complete_Damage_Foci_9` | `Molecules` | `DNA9(h2ax!1~foc).ATM(state~9,h2ax!1)` | Reports bound or complexed species matching the pattern. |
| `Damage_Foci_10` | `Molecules` | `DNA10(site!?~?,h2ax~foc)` | Reports the BNGL pattern for downstream plotting or rate expressions. |
| `Complete_Damage_Foci_10` | `Molecules` | `DNA10(h2ax!1~foc).ATM(state~10,h2ax!1)` | Reports bound or complexed species matching the pattern. |
| `Damage_Foci_11` | `Molecules` | `DNA11(site!?~?,h2ax~foc)` | Reports the BNGL pattern for downstream plotting or rate expressions. |
| `Complete_Damage_Foci_11` | `Molecules` | `DNA11(h2ax!1~foc).ATM(state~11,h2ax!1)` | Reports bound or complexed species matching the pattern. |
| `Damage_Foci_12` | `Molecules` | `DNA12(site!?~?,h2ax~foc)` | Reports the BNGL pattern for downstream plotting or rate expressions. |
| `Complete_Damage_Foci_12` | `Molecules` | `DNA12(h2ax!1~foc).ATM(state~12,h2ax!1)` | Reports bound or complexed species matching the pattern. |
| `Damage_Foci_13` | `Molecules` | `DNA13(site!?~?,h2ax~foc)` | Reports the BNGL pattern for downstream plotting or rate expressions. |
| `Complete_Damage_Foci_13` | `Molecules` | `DNA13(h2ax!1~foc).ATM(state~13,h2ax!1)` | Reports bound or complexed species matching the pattern. |
| `Damage_Foci_14` | `Molecules` | `DNA14(site!?~?,h2ax~foc)` | Reports the BNGL pattern for downstream plotting or rate expressions. |
| `Complete_Damage_Foci_14` | `Molecules` | `DNA14(h2ax!1~foc).ATM(state~14,h2ax!1)` | Reports bound or complexed species matching the pattern. |
| `Damage_Foci_15` | `Molecules` | `DNA15(site!?~?,h2ax~foc)` | Reports the BNGL pattern for downstream plotting or rate expressions. |
| `Complete_Damage_Foci_15` | `Molecules` | `DNA15(h2ax!1~foc).ATM(state~15,h2ax!1)` | Reports bound or complexed species matching the pattern. |
| `Damage_Foci_16` | `Molecules` | `DNA16(site!?~?,h2ax~foc)` | Reports the BNGL pattern for downstream plotting or rate expressions. |
| `Complete_Damage_Foci_16` | `Molecules` | `DNA16(h2ax!1~foc).ATM(state~16,h2ax!1)` | Reports bound or complexed species matching the pattern. |
| `Damage_Foci_17` | `Molecules` | `DNA17(site!?~?,h2ax~foc)` | Reports the BNGL pattern for downstream plotting or rate expressions. |
| `Complete_Damage_Foci_17` | `Molecules` | `DNA17(h2ax!1~foc).ATM(state~17,h2ax!1)` | Reports bound or complexed species matching the pattern. |
| `Damage_Foci_18` | `Molecules` | `DNA18(site!?~?,h2ax~foc)` | Reports the BNGL pattern for downstream plotting or rate expressions. |
| `Complete_Damage_Foci_18` | `Molecules` | `DNA18(h2ax!1~foc).ATM(state~18,h2ax!1)` | Reports bound or complexed species matching the pattern. |
| `Damage_Foci_19` | `Molecules` | `DNA19(site!?~?,h2ax~foc)` | Reports the BNGL pattern for downstream plotting or rate expressions. |
| `Complete_Damage_Foci_19` | `Molecules` | `DNA19(h2ax!1~foc).ATM(state~19,h2ax!1)` | Reports bound or complexed species matching the pattern. |
| `Damage_Foci_20` | `Molecules` | `DNA20(site!?~?,h2ax~foc)` | Reports the BNGL pattern for downstream plotting or rate expressions. |
| `Complete_Damage_Foci_20` | `Molecules` | `DNA20(h2ax!1~foc).ATM(state~20,h2ax!1)` | Reports bound or complexed species matching the pattern. |
| `Damage_Foci_21` | `Molecules` | `DNA21(site!?~?,h2ax~foc)` | Reports the BNGL pattern for downstream plotting or rate expressions. |
| `Complete_Damage_Foci_21` | `Molecules` | `DNA21(h2ax!1~foc).ATM(state~21,h2ax!1)` | Reports bound or complexed species matching the pattern. |
| `Damage_Foci_22` | `Molecules` | `DNA22(site!?~?,h2ax~foc)` | Reports the BNGL pattern for downstream plotting or rate expressions. |
| `Complete_Damage_Foci_22` | `Molecules` | `DNA22(h2ax!1~foc).ATM(state~22,h2ax!1)` | Reports bound or complexed species matching the pattern. |
| `Damage_Foci_23` | `Molecules` | `DNA23(site!?~?,h2ax~foc)` | Reports the BNGL pattern for downstream plotting or rate expressions. |
| `Complete_Damage_Foci_23` | `Molecules` | `DNA23(h2ax!1~foc).ATM(state~23,h2ax!1)` | Reports bound or complexed species matching the pattern. |
| `Damage_Foci_24` | `Molecules` | `DNA24(site!?~?,h2ax~foc)` | Reports the BNGL pattern for downstream plotting or rate expressions. |
| `Complete_Damage_Foci_24` | `Molecules` | `DNA24(h2ax!1~foc).ATM(state~24,h2ax!1)` | Reports bound or complexed species matching the pattern. |
| `Damage_Foci_25` | `Molecules` | `DNA25(site!?~?,h2ax~foc)` | Reports the BNGL pattern for downstream plotting or rate expressions. |
| `Complete_Damage_Foci_25` | `Molecules` | `DNA25(h2ax!1~foc).ATM(state~25,h2ax!1)` | Reports bound or complexed species matching the pattern. |
| `Damage_Foci_26` | `Molecules` | `DNA26(site!?~?,h2ax~foc)` | Reports the BNGL pattern for downstream plotting or rate expressions. |
| `Complete_Damage_Foci_26` | `Molecules` | `DNA26(h2ax!1~foc).ATM(state~26,h2ax!1)` | Reports bound or complexed species matching the pattern. |
| `Damage_Foci_27` | `Molecules` | `DNA27(site!?~?,h2ax~foc)` | Reports the BNGL pattern for downstream plotting or rate expressions. |
| `Complete_Damage_Foci_27` | `Molecules` | `DNA27(h2ax!1~foc).ATM(state~27,h2ax!1)` | Reports bound or complexed species matching the pattern. |
| `Damage_Foci_28` | `Molecules` | `DNA28(site!?~?,h2ax~foc)` | Reports the BNGL pattern for downstream plotting or rate expressions. |
| `Complete_Damage_Foci_28` | `Molecules` | `DNA28(h2ax!1~foc).ATM(state~28,h2ax!1)` | Reports bound or complexed species matching the pattern. |
| `Damage_Foci_29` | `Molecules` | `DNA29(site!?~?,h2ax~foc)` | Reports the BNGL pattern for downstream plotting or rate expressions. |
| `Complete_Damage_Foci_29` | `Molecules` | `DNA29(h2ax!1~foc).ATM(state~29,h2ax!1)` | Reports bound or complexed species matching the pattern. |
| `Damage_Foci_30` | `Molecules` | `DNA30(site!?~?,h2ax~foc)` | Reports the BNGL pattern for downstream plotting or rate expressions. |
| `Complete_Damage_Foci_30` | `Molecules` | `DNA30(h2ax!1~foc).ATM(state~30,h2ax!1)` | Reports bound or complexed species matching the pattern. |
| `Damage_Foci_31` | `Molecules` | `DNA31(site!?~?,h2ax~foc)` | Reports the BNGL pattern for downstream plotting or rate expressions. |
| `Complete_Damage_Foci_31` | `Molecules` | `DNA31(h2ax!1~foc).ATM(state~31,h2ax!1)` | Reports bound or complexed species matching the pattern. |
| `Damage_Foci_32` | `Molecules` | `DNA32(site!?~?,h2ax~foc)` | Reports the BNGL pattern for downstream plotting or rate expressions. |
| `Complete_Damage_Foci_32` | `Molecules` | `DNA32(h2ax!1~foc).ATM(state~32,h2ax!1)` | Reports bound or complexed species matching the pattern. |
| `Damage_Foci_33` | `Molecules` | `DNA33(site!?~?,h2ax~foc)` | Reports the BNGL pattern for downstream plotting or rate expressions. |
| `Complete_Damage_Foci_33` | `Molecules` | `DNA33(h2ax!1~foc).ATM(state~33,h2ax!1)` | Reports bound or complexed species matching the pattern. |
| `Damage_Foci_34` | `Molecules` | `DNA34(site!?~?,h2ax~foc)` | Reports the BNGL pattern for downstream plotting or rate expressions. |
| `Complete_Damage_Foci_34` | `Molecules` | `DNA34(h2ax!1~foc).ATM(state~34,h2ax!1)` | Reports bound or complexed species matching the pattern. |
| `Damage_Foci_35` | `Molecules` | `DNA35(site!?~?,h2ax~foc)` | Reports the BNGL pattern for downstream plotting or rate expressions. |
| `Complete_Damage_Foci_35` | `Molecules` | `DNA35(h2ax!1~foc).ATM(state~35,h2ax!1)` | Reports bound or complexed species matching the pattern. |
| `Damage_Foci_36` | `Molecules` | `DNA36(site!?~?,h2ax~foc)` | Reports the BNGL pattern for downstream plotting or rate expressions. |
| `Complete_Damage_Foci_36` | `Molecules` | `DNA36(h2ax!1~foc).ATM(state~36,h2ax!1)` | Reports bound or complexed species matching the pattern. |
| `Damage_Foci_37` | `Molecules` | `DNA37(site!?~?,h2ax~foc)` | Reports the BNGL pattern for downstream plotting or rate expressions. |
| `Complete_Damage_Foci_37` | `Molecules` | `DNA37(h2ax!1~foc).ATM(state~37,h2ax!1)` | Reports bound or complexed species matching the pattern. |
| `Damage_Foci_38` | `Molecules` | `DNA38(site!?~?,h2ax~foc)` | Reports the BNGL pattern for downstream plotting or rate expressions. |
| `Complete_Damage_Foci_38` | `Molecules` | `DNA38(h2ax!1~foc).ATM(state~38,h2ax!1)` | Reports bound or complexed species matching the pattern. |
| `Damage_Foci_39` | `Molecules` | `DNA39(site!?~?,h2ax~foc)` | Reports the BNGL pattern for downstream plotting or rate expressions. |
| `Complete_Damage_Foci_39` | `Molecules` | `DNA39(h2ax!1~foc).ATM(state~39,h2ax!1)` | Reports bound or complexed species matching the pattern. |
| `Damage_Foci_40` | `Molecules` | `DNA40(site!?~?,h2ax~foc)` | Reports the BNGL pattern for downstream plotting or rate expressions. |
| `Complete_Damage_Foci_40` | `Molecules` | `DNA40(h2ax!1~foc).ATM(state~40,h2ax!1)` | Reports bound or complexed species matching the pattern. |
| `Damage_Foci_41` | `Molecules` | `DNA41(site!?~?,h2ax~foc)` | Reports the BNGL pattern for downstream plotting or rate expressions. |
| `Complete_Damage_Foci_41` | `Molecules` | `DNA41(h2ax!1~foc).ATM(state~41,h2ax!1)` | Reports bound or complexed species matching the pattern. |
| `Damage_Foci_42` | `Molecules` | `DNA42(site!?~?,h2ax~foc)` | Reports the BNGL pattern for downstream plotting or rate expressions. |
| `Complete_Damage_Foci_42` | `Molecules` | `DNA42(h2ax!1~foc).ATM(state~42,h2ax!1)` | Reports bound or complexed species matching the pattern. |
| `Damage_Foci_43` | `Molecules` | `DNA43(site!?~?,h2ax~foc)` | Reports the BNGL pattern for downstream plotting or rate expressions. |
| `Complete_Damage_Foci_43` | `Molecules` | `DNA43(h2ax!1~foc).ATM(state~43,h2ax!1)` | Reports bound or complexed species matching the pattern. |
| `Damage_Foci_44` | `Molecules` | `DNA44(site!?~?,h2ax~foc)` | Reports the BNGL pattern for downstream plotting or rate expressions. |
| `Complete_Damage_Foci_44` | `Molecules` | `DNA44(h2ax!1~foc).ATM(state~44,h2ax!1)` | Reports bound or complexed species matching the pattern. |
| `Damage_Foci_45` | `Molecules` | `DNA45(site!?~?,h2ax~foc)` | Reports the BNGL pattern for downstream plotting or rate expressions. |
| `Complete_Damage_Foci_45` | `Molecules` | `DNA45(h2ax!1~foc).ATM(state~45,h2ax!1)` | Reports bound or complexed species matching the pattern. |
| `Damage_Foci_46` | `Molecules` | `DNA46(site!?~?,h2ax~foc)` | Reports the BNGL pattern for downstream plotting or rate expressions. |
| `Complete_Damage_Foci_46` | `Molecules` | `DNA46(h2ax!1~foc).ATM(state~46,h2ax!1)` | Reports bound or complexed species matching the pattern. |
| `Damage_Foci_47` | `Molecules` | `DNA47(site!?~?,h2ax~foc)` | Reports the BNGL pattern for downstream plotting or rate expressions. |
| `Complete_Damage_Foci_47` | `Molecules` | `DNA47(h2ax!1~foc).ATM(state~47,h2ax!1)` | Reports bound or complexed species matching the pattern. |
| `Damage_Foci_48` | `Molecules` | `DNA48(site!?~?,h2ax~foc)` | Reports the BNGL pattern for downstream plotting or rate expressions. |
| `Complete_Damage_Foci_48` | `Molecules` | `DNA48(h2ax!1~foc).ATM(state~48,h2ax!1)` | Reports bound or complexed species matching the pattern. |
| `Damage_Foci_49` | `Molecules` | `DNA49(site!?~?,h2ax~foc)` | Reports the BNGL pattern for downstream plotting or rate expressions. |
| `Complete_Damage_Foci_49` | `Molecules` | `DNA49(h2ax!1~foc).ATM(state~49,h2ax!1)` | Reports bound or complexed species matching the pattern. |
| `Damage_Foci_50` | `Molecules` | `DNA50(site!?~?,h2ax~foc)` | Reports the BNGL pattern for downstream plotting or rate expressions. |
| `Complete_Damage_Foci_50` | `Molecules` | `DNA50(h2ax!1~foc).ATM(state~50,h2ax!1)` | Reports bound or complexed species matching the pattern. |
| `Ku` | `Molecules` | `Ku(dna,cs,cys~?)` | Reports the BNGL pattern for downstream plotting or rate expressions. |
| `PARP` | `Molecules` | `PARP(dna,liIII)` | Reports the BNGL pattern for downstream plotting or rate expressions. |
| `Ku_Red` | `Molecules` | `Ku(dna,cs,cys~red)` | Reports the BNGL pattern for downstream plotting or rate expressions. |
| `Ku_Ox` | `Molecules` | `Ku(dna,cs,cys~ox)` | Reports the BNGL pattern for downstream plotting or rate expressions. |
| `DNA_PKcs` | `Molecules` | `DNAPKcs(ku,liIV,psite~u)` | Reports the BNGL pattern for downstream plotting or rate expressions. |
| `LiIII` | `Molecules` | `LiIII(PARP)` | Reports the BNGL pattern for downstream plotting or rate expressions. |
| `LiIV` | `Molecules` | `LiIV(cs)` | Reports the BNGL pattern for downstream plotting or rate expressions. |
| `Senescent_Counter` | `Molecules` | `Sen(int~?,State~sen)` | Reports the BNGL pattern for downstream plotting or rate expressions. |
| `Sen_Min` | `Molecules` | `Sen(int~1,State~?)` | Reports the BNGL pattern for downstream plotting or rate expressions. |
| `Sink` | `Molecules` | `Sink()` | Reports the BNGL pattern for downstream plotting or rate expressions. |

## 8. Actions and simulation workflow

1. `simulate_nf({suffix=>"nf_run1",t_end=>2400,n_steps=>2400,param=> "-v -gml 1000000000"})` — execution command affecting network generation, simulation, scanning, or output.

2. `simulate_nf({suffix=>"nf_run2",t_end=>2400,n_steps=>2400,param=> "-v -gml 1000000000"})` — execution command affecting network generation, simulation, scanning, or output.

3. `simulate_nf({suffix=>"nf_run3",t_end=>2400,n_steps=>2400,param=> "-v -gml 1000000000"})` — execution command affecting network generation, simulation, scanning, or output.

4. `simulate_nf({suffix=>"nf_run4",t_end=>2400,n_steps=>2400,param=> "-v -gml 1000000000"})` — execution command affecting network generation, simulation, scanning, or output.

5. `simulate_nf({suffix=>"nf_run5",t_end=>2400,n_steps=>2400,param=> "-v -gml 1000000000"})` — execution command affecting network generation, simulation, scanning, or output.

6. `simulate_nf({suffix=>"nf_run6",t_end=>2400,n_steps=>2400,param=> "-v -gml 1000000000"})` — execution command affecting network generation, simulation, scanning, or output.

7. `simulate_nf({suffix=>"nf_run7",t_end=>2400,n_steps=>2400,param=> "-v -gml 1000000000"})` — execution command affecting network generation, simulation, scanning, or output.

8. `simulate_nf({suffix=>"nf_run8",t_end=>2400,n_steps=>2400,param=> "-v -gml 1000000000"})` — execution command affecting network generation, simulation, scanning, or output.

9. `simulate_nf({suffix=>"nf_run9",t_end=>2400,n_steps=>2400,param=> "-v -gml 1000000000"})` — execution command affecting network generation, simulation, scanning, or output.

10. `simulate_nf({suffix=>"nf_run10",t_end=>2400,n_steps=>2400,param=> "-v -gml 1000000000"})` — execution command affecting network generation, simulation, scanning, or output.

11. `simulate_nf({suffix=>"nf_run11",t_end=>2400,n_steps=>2400,param=> "-v -gml 1000000000"})` — execution command affecting network generation, simulation, scanning, or output.

12. `simulate_nf({suffix=>"nf_run12",t_end=>2400,n_steps=>2400,param=> "-v -gml 1000000000"})` — execution command affecting network generation, simulation, scanning, or output.

13. `simulate_nf({suffix=>"nf_run13",t_end=>2400,n_steps=>2400,param=> "-v -gml 1000000000"})` — execution command affecting network generation, simulation, scanning, or output.

14. `simulate_nf({suffix=>"nf_run14",t_end=>2400,n_steps=>2400,param=> "-v -gml 1000000000"})` — execution command affecting network generation, simulation, scanning, or output.

15. `simulate_nf({suffix=>"nf_run15",t_end=>2400,n_steps=>2400,param=> "-v -gml 1000000000"})` — execution command affecting network generation, simulation, scanning, or output.

16. `simulate_nf({suffix=>"nf_run16",t_end=>2400,n_steps=>2400,param=> "-v -gml 1000000000"})` — execution command affecting network generation, simulation, scanning, or output.

17. `simulate_nf({suffix=>"nf_run17",t_end=>2400,n_steps=>2400,param=> "-v -gml 1000000000"})` — execution command affecting network generation, simulation, scanning, or output.

18. `simulate_nf({suffix=>"nf_run18",t_end=>2400,n_steps=>2400,param=> "-v -gml 1000000000"})` — execution command affecting network generation, simulation, scanning, or output.

19. `simulate_nf({suffix=>"nf_run19",t_end=>2400,n_steps=>2400,param=> "-v -gml 1000000000"})` — execution command affecting network generation, simulation, scanning, or output.

20. `simulate_nf({suffix=>"nf_run20",t_end=>2400,n_steps=>2400,param=> "-v -gml 1000000000"})` — execution command affecting network generation, simulation, scanning, or output.

21. `simulate_nf({suffix=>"nf_run21",t_end=>2400,n_steps=>2400,param=> "-v -gml 1000000000"})` — execution command affecting network generation, simulation, scanning, or output.

22. `simulate_nf({suffix=>"nf_run22",t_end=>2400,n_steps=>2400,param=> "-v -gml 1000000000"})` — execution command affecting network generation, simulation, scanning, or output.

23. `simulate_nf({suffix=>"nf_run23",t_end=>2400,n_steps=>2400,param=> "-v -gml 1000000000"})` — execution command affecting network generation, simulation, scanning, or output.

24. `simulate_nf({suffix=>"nf_run24",t_end=>2400,n_steps=>2400,param=> "-v -gml 1000000000"})` — execution command affecting network generation, simulation, scanning, or output.

25. `simulate_nf({suffix=>"nf_run25",t_end=>2400,n_steps=>2400,param=> "-v -gml 1000000000"})` — execution command affecting network generation, simulation, scanning, or output.

26. `simulate_nf({suffix=>"nf_run26",t_end=>2400,n_steps=>2400,param=> "-v -gml 1000000000"})` — execution command affecting network generation, simulation, scanning, or output.

27. `simulate_nf({suffix=>"nf_run27",t_end=>2400,n_steps=>2400,param=> "-v -gml 1000000000"})` — execution command affecting network generation, simulation, scanning, or output.

28. `simulate_nf({suffix=>"nf_run28",t_end=>2400,n_steps=>2400,param=> "-v -gml 1000000000"})` — execution command affecting network generation, simulation, scanning, or output.

29. `simulate_nf({suffix=>"nf_run29",t_end=>2400,n_steps=>2400,param=> "-v -gml 1000000000"})` — execution command affecting network generation, simulation, scanning, or output.

30. `simulate_nf({suffix=>"nf_run30",t_end=>2400,n_steps=>2400,param=> "-v -gml 1000000000"})` — execution command affecting network generation, simulation, scanning, or output.

31. `simulate_nf({suffix=>"nf_run31",t_end=>2400,n_steps=>2400,param=> "-v -gml 1000000000"})` — execution command affecting network generation, simulation, scanning, or output.

32. `simulate_nf({suffix=>"nf_run32",t_end=>2400,n_steps=>2400,param=> "-v -gml 1000000000"})` — execution command affecting network generation, simulation, scanning, or output.

33. `simulate_nf({suffix=>"nf_run33",t_end=>2400,n_steps=>2400,param=> "-v -gml 1000000000"})` — execution command affecting network generation, simulation, scanning, or output.

34. `simulate_nf({suffix=>"nf_run34",t_end=>2400,n_steps=>2400,param=> "-v -gml 1000000000"})` — execution command affecting network generation, simulation, scanning, or output.

35. `simulate_nf({suffix=>"nf_run35",t_end=>2400,n_steps=>2400,param=> "-v -gml 1000000000"})` — execution command affecting network generation, simulation, scanning, or output.

36. `simulate_nf({suffix=>"nf_run36",t_end=>2400,n_steps=>2400,param=> "-v -gml 1000000000"})` — execution command affecting network generation, simulation, scanning, or output.

37. `simulate_nf({suffix=>"nf_run37",t_end=>2400,n_steps=>2400,param=> "-v -gml 1000000000"})` — execution command affecting network generation, simulation, scanning, or output.

38. `simulate_nf({suffix=>"nf_run38",t_end=>2400,n_steps=>2400,param=> "-v -gml 1000000000"})` — execution command affecting network generation, simulation, scanning, or output.

39. `simulate_nf({suffix=>"nf_run39",t_end=>2400,n_steps=>2400,param=> "-v -gml 1000000000"})` — execution command affecting network generation, simulation, scanning, or output.

40. `simulate_nf({suffix=>"nf_run40",t_end=>2400,n_steps=>2400,param=> "-v -gml 1000000000"})` — execution command affecting network generation, simulation, scanning, or output.

41. `simulate_nf({suffix=>"nf_run41",t_end=>2400,n_steps=>2400,param=> "-v -gml 1000000000"})` — execution command affecting network generation, simulation, scanning, or output.

42. `simulate_nf({suffix=>"nf_run42",t_end=>2400,n_steps=>2400,param=> "-v -gml 1000000000"})` — execution command affecting network generation, simulation, scanning, or output.

43. `simulate_nf({suffix=>"nf_run43",t_end=>2400,n_steps=>2400,param=> "-v -gml 1000000000"})` — execution command affecting network generation, simulation, scanning, or output.

44. `simulate_nf({suffix=>"nf_run44",t_end=>2400,n_steps=>2400,param=> "-v -gml 1000000000"})` — execution command affecting network generation, simulation, scanning, or output.

45. `simulate_nf({suffix=>"nf_run45",t_end=>2400,n_steps=>2400,param=> "-v -gml 1000000000"})` — execution command affecting network generation, simulation, scanning, or output.

46. `simulate_nf({suffix=>"nf_run46",t_end=>2400,n_steps=>2400,param=> "-v -gml 1000000000"})` — execution command affecting network generation, simulation, scanning, or output.

47. `simulate_nf({suffix=>"nf_run47",t_end=>2400,n_steps=>2400,param=> "-v -gml 1000000000"})` — execution command affecting network generation, simulation, scanning, or output.

48. `simulate_nf({suffix=>"nf_run48",t_end=>2400,n_steps=>2400,param=> "-v -gml 1000000000"})` — execution command affecting network generation, simulation, scanning, or output.

49. `simulate_nf({suffix=>"nf_run49",t_end=>2400,n_steps=>2400,param=> "-v -gml 1000000000"})` — execution command affecting network generation, simulation, scanning, or output.

50. `simulate_nf({suffix=>"nf_run50",t_end=>2400,n_steps=>2400,param=> "-v -gml 1000000000"})` — execution command affecting network generation, simulation, scanning, or output.

## 9. Technical caveats and ambiguities

- No compartments or anchors are declared; all spatial interpretation is abstract.

- The 50 DNA molecule types are explicit copies, so many rule families repeat once per DNA locus rather than using a single generic DNA molecule.

- The reaction-rule inventory is intentionally very large because the source file literally enumerates each locus-specific rule.

- The complete rule inventory has 2339 rows; downstream review should compare this count with the `begin reaction rules` block after any source edits.

- The summary keeps raw molecule, site, state, and parameter names because this is the coder-facing version and those identifiers are necessary for implementation review.
