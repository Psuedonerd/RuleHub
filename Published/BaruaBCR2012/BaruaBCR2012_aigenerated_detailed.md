# Coder Model Explanation: Barua 2012 B-cell receptor signaling model

## 1. Model identity and scope

`BaruaBCR_2012` models how B-cell receptor (BCR) signaling couples Lyn/Fyn/Syk activation to Csk–PAG negative regulation. Sources: `Published/BaruaBCR2012/BaruaBCR_2012.bngl` and `Published/BaruaBCR2012/metadata.yaml`.

## 2. BNGL block inventory

The file contains 118 active parameter declarations, 6 molecule types, 6 initial-species declarations, 0 functions, 76 concrete reaction rules, 9 observable declarations, and 1 execution command. It declares no compartments or anchors.

## 3. Parameters, functions, and rate laws

Every active parameter declaration is listed below; expressions are retained verbatim so scaling and dependencies remain inspectable.

- `p1 3.0e5 # molecules/cell`
- `p2 10.0 # /sec`
- `p3 3.0e-4 # /sec`
- `p4 3.0e-7 # /(molecules/cell)/sec`
- `p5 30.0 # /sec`
- `p6 3.0e-5 # /(molecules/cell)/sec`
- `p7 0.3 # /sec`
- `p8 0.1 # /sec`
- `p9 3.0e-6 # /(molecules/cell)/sec`
- `p10 0.3 # /sec`
- `p11 1.0e-5 # /(molecules/cell)/sec`
- `p12 1.0e3 # /sec`
- `p13 30.0 # /sec`
- `p14 0.1 # /sec`
- `p15 3.0e-7 # /(molecules/cell)/sec`
- `p16 3.0e-3 # /sec`
- `p17 1.0e-10 # /(molecules/cell)/sec`
- `p18 1.0e-7 # /(molecules/cell)/sec`
- `p19 1.0e-7 # /(molecules/cell)/sec`
- `p20 3.0e-5 # /(molecules/cell)/sec`
- `p21 1.0e3 # /sec`
- `p22 3.0e-6 # /(molecules/cell)/sec`
- `p23 3.0e-4 # /(molecules/cell)/sec`
- `p24 1.0 # /sec`
- `p25 5.0 # dimensionless`
- `c 0.0 # dimensionless`
- `BT p1 # total amount of BCR`
- `LT p1 # total amount of Lyn`
- `FT p1 # total amount of Fyn`
- `PT p1 # total amount of PAG`
- `CT p1 # total amount of Csk`
- `ST p1 # total amount of Syk`
- `kf1 p4 # 1: Lyn(unique) binds BCR(Y188_Y199~0)`
- `kr1 p5 # reverse of 1`
- `kf2a p6 # 2a: Lyn(SH2) binds BCR(Y188_Y199~P)`
- `kf2b p6 # 2b: Lyn(SH2) binds BCR(Y188_Y199~PP)`
- `kr2a p7 # reverse of 2a`
- `kr2b p8 # reverse of 2b`
- `kf3 p2 # 3: Lyn(SH2) binds Lyn(Y508~P) in cis`
- `kr3 p3 # reverse of 3`
- `kp4a c*p19 # 4a: Lyn-catalyzed phosphorylation of BCR(Y188_Y199~0)`
- `kp4b c*p19 # 4b: Lyn-catalyzed phosphorylation of BCR(Y188_Y199~P)`
- `kp4c c*p20 # 4c: Lyn-catalyzed phosphorylation of BCR(Y188_Y199~0)`
- `kp4d c*p20 # 4d: Lyn-catalyzed phosphorylation of BCR(Y188_Y199~P)`
- `kp5a c*p19 # 5a: Lyn-catalyzed phosphorylation of BCR(Y196_Y207~0)`
- `kp5b c*p19 # 5b: Lyn-catalyzed phosphorylation of BCR(Y196_Y207~P)`
- `kp5c c*p20 # 5c: Lyn-catalyzed phosphorylation of BCR(Y196_Y207~0)`
- `kp5d c*p20 # 5d: Lyn-catalyzed phosphorylation of BCR(Y196_Y207~P)`
- `kp6a c*p19 # 6a: Lyn-catalyzed phosphorylation of Lyn(Y397~0)`
- `kp6b c*p20 # 6b: Lyn-catalyzed phosphorylation of Lyn(Y397~0)`
- `kp6c p17 # 6c: Lyn-catalyzed phosphorylation of Lyn(Y397~0)`
- `kp6d p18 # 6d: Lyn-catalyzed phosphorylation of Lyn(Y397~0)`
- `kp7a c*p19 # 7a: Lyn-catalyzed phosphorylation of Fyn(Y420~0)`
- `kp7b c*p20 # 7b: Lyn-catalyzed phosphorylation of Fyn(Y420~0)`
- `kp7c p17 # 7c: Lyn-catalyzed phosphorylation of Fyn(Y420~0)`
- `kp7d p18 # 7d: Lyn-catalyzed phosphorylation of Fyn(Y420~0)`
- `kp8a p21 # 8a: Lyn-catalyzed phosphorylation of PAG(Y387_Y417~0)`
- `kp8b p21 # 8b: Lyn-catalyzed phosphorylation of PAG(Y163_Y181~0)`
- `kp8c p21 # 8c: Lyn-catalyzed phosphorylation of PAG(Y317~0)`
- `kf9 p4 # 9: Fyn(unique) binds BCR(Y188_Y199~0)`
- `kr9 p5 # reverse of 9`
- `kf10a p6 # 10a: Fyn(SH2) binds BCR(Y188_Y199~P)`
- `kf10b p6 # 10b: Fyn(SH2) binds BCR(Y188_Y199~PP)`
- `kr10a p7 # reverse of 10a`
- `kr10b p8 # reverse of 10b`
- `kf11 p2 # 11: Fyn(SH2) binds Fyn(Y531~P) in cis`
- `kr11 p3 # reverse of 11`
- `kp12a c*p19/p25 # 12a: Fyn-catalyzed phosphorylation of BCR(Y196_Y207~0)`
- `kp12b c*p19/p25 # 12b: Fyn-catalyzed phosphorylation of BCR(Y196_Y207~P)`
- `kp12c c*p20/p25 # 12c: Fyn-catalyzed phosphorylation of BCR(Y196_Y207~0)`
- `kp12d c*p20/p25 # 12d: Fyn-catalyzed phosphorylation of BCR(Y196_Y207~P)`
- `kp13a c*p19/p25 # 13a: Fyn-catalyzed phosphorylation of BCR(Y188_Y199~0)`
- `kp13b c*p19/p25 # 13b: Fyn-catalyzed phosphorylation of BCR(Y188_Y199~P)`
- `kp13c c*p20/p25 # 13c: Fyn-catalyzed phosphorylation of BCR(Y188_Y199~0)`
- `kp13d c*p20/p25 # 13d: Fyn-catalyzed phosphorylation of BCR(Y188_Y199~P)`
- `kp14a c*p19/p25 # 14a: Fyn-catalyzed phosphorylation of Fyn(Y420~0)`
- `kp14b c*p20/p25 # 14b: Fyn-catalyzed phosphorylation of Fyn(Y420~0)`
- `kp14c p17 # 14c: Fyn-catalyzed phosphorylation of Fyn(Y420~0)`
- `kp14d p18 # 14d: Fyn-catalyzed phosphorylation of Fyn(Y420~0)`
- `kp15a c*p19/p25 # 15a: Fyn-catalyzed phosphorylation of Lyn(Y397~0)`
- `kp15b c*p20/p25 # 15b: Fyn-catalyzed phosphorylation of Lyn(Y397~0)`
- `kp15c p17 # 15c: Fyn-catalyzed phosphorylation of Lyn(Y397~0)`
- `kp15d p18 # 15d: Fyn-catalyzed phosphorylation of Lyn(Y397~0)`
- `kp16a p21 # 16a: Fyn-catalyzed phosphorylation of PAG(Y387_Y417~0)`
- `kp16b 0.0 # 16b: Fyn-catalyzed phosphorylation of PAG(Y163_Y181~0)`
- `kp16c p21 # 16c: Fyn-catalyzed phosphorylation of PAG(Y317~0)`
- `kf17 p9 # 17: Syk(tSH2) binds BCR(Y196_Y207~PP)`
- `kr17 p10 # reverse of 17`
- `kp18a c*p22 # 18a: Syk-catalyzed phosphorylation of Syk(Y525_Y526~0)`
- `kp18b c*p23 # 18b: Syk-catalyzed phosphorylation of Syk(Y525_Y526~0)`
- `kf19a p11 # 19a: Lyn(SH3) binds PAG(PRS2)`
- `kr19a p13 # reverse of 19a`
- `kf19b p12 # 19b: Lyn(SH3) binds PAG(PRS2)`
- `kf20a p6 # 20a: Lyn(SH2) binds PAG(Y387_Y417~P)`
- `kf20b p12 # 20b: Lyn(SH2) binds PAG(Y387_Y417~P)`
- `kr20b p14 # reverse of 20b (and 19b)`
- `kf21a p11 # 21a: Fyn(SH3) binds PAG(PRS1)`
- `kr21a p13 # reverse of 21a`
- `kf21b p12 # 21b: Fyn(SH3) binds PAG(PRS1)`
- `kf22a p6 # 22a: Fyn(SH2) binds PAG(Y163_Y181~P)`
- `kf22b p12 # 22b: Fyn(SH2) binds PAG(Y163_Y181~P)`
- `kr22b p14 # reverse of 22b (and 21b)`
- `kf23 p15 # 23: Csk(SH2) binds PAG(Y317~P)`
- `kr23 p16 # reverse of 23`
- `kp24 p21 # 24: Csk-catalyzed phosphorylation of Lyn(Y508~0)`
- `kp25 p21 # 25: Csk-catalyzed phosphorylation of Fyn(Y531~0)`
- `kdp26a p24 # Dephosphorylation of BCR(Y188_Y199~P)`
- `kdp26b p24 # Dephosphorylation of BCR(Y188_Y199~PP)`
- `kdp27a p24 # Dephosphorylation of BCR(Y196_Y207~P)`
- `kdp27b p24 # Dephosphorylation of BCR(Y196_Y207~PP)`
- `kdp28a p24 # Dephosphorylation of Lyn(Y397~P)`
- `kdp28b p24 # Dephosphorylation of Lyn(Y508~P)`
- `kdp29a p24 # Dephosphorylation of Fyn(Y420~P)`
- `kdp29b p24 # Dephosphorylation of Fyn(Y531~P)`
- `kdp30a p24 # Dephosphorylation of PAG(Y317~P)`
- `kdp30b p24 # Dephosphorylation of PAG(Y387_Y417~P)`
- `kdp30c p24 # Dephosphorylation of PAG(Y163_Y181~P)`
- `kdp31 p24 # Dephosphorylation of Syk(Y525_Y526~P)`

There is no functions block; rules use parameters or literal expressions directly.

## 4. Molecule types, sites, and states

| Molecule type | Site count | Sites/components | Internal states | Anchor/allowed compartments | Binding/modification roles | Notes |
| --- | ---: | --- | --- | --- | --- | --- |
| `BCR` | 2 | `Y188_Y199, Y196_Y207` | `Y188_Y199: 0,P,PP; Y196_Y207: 0,P,PP` | None | Binding/state components are used exactly as shown in the rule inventory. | Declaration: `BCR(Y188_Y199~0~P~PP,Y196_Y207~0~P~PP)` |
| `Lyn` | 5 | `unique, SH3, SH2, Y397, Y508` | `Y397: 0,P; Y508: 0,P` | None | Binding/state components are used exactly as shown in the rule inventory. | Declaration: `Lyn(unique,SH3,SH2,Y397~0~P,Y508~0~P)` |
| `Fyn` | 5 | `unique, SH3, SH2, Y420, Y531` | `Y420: 0,P; Y531: 0,P` | None | Binding/state components are used exactly as shown in the rule inventory. | Declaration: `Fyn(unique,SH3,SH2,Y420~0~P,Y531~0~P)` |
| `Csk` | 1 | `SH2` | `none` | None | Binding/state components are used exactly as shown in the rule inventory. | Declaration: `Csk(SH2)` |
| `PAG` | 5 | `PRS1, PRS2, Y317, Y163_Y181, Y387_Y417` | `Y317: 0,P; Y163_Y181: 0,P; Y387_Y417: 0,P` | None | Binding/state components are used exactly as shown in the rule inventory. | Declaration: `PAG(PRS1,PRS2,Y317~0~P,Y163_Y181~0~P,Y387_Y417~0~P)` |
| `Syk` | 2 | `tSH2, Y525_Y526` | `Y525_Y526: 0,P` | None | Binding/state components are used exactly as shown in the rule inventory. | Declaration: `Syk(tSH2,Y525_Y526~0~P)` |

## 5. Compartments, anchors, initial species, and setup

No BNGL compartments or anchors are declared. Initial patterns and amounts are exhaustive below:

- `BCR(Y188_Y199~0,Y196_Y207~0) BT`
- `Lyn(unique,SH3,SH2,Y397~0,Y508~0) LT`
- `Fyn(unique,SH3,SH2,Y420~0,Y531~0) FT`
- `PAG(PRS1,PRS2,Y317~0,Y163_Y181~0,Y387_Y417~0) PT`
- `Csk(SH2) CT`
- `Syk(tSH2,Y525_Y526~0) ST`

## 6. Complete reaction-rule inventory

**Rule-family orientation.** The family/context column preserves the nearest active BNGL comment; the implementation column preserves every molecule, site, state, bond, direction, and rate expression. Thus repeated families remain one row per concrete rule rather than being collapsed.

| # | Family / technical meaning | Direction | Exact site-level implementation and rate law |
| ---: | --- | --- | --- |
| 1 | unique domain of Lyn binds unphosphorylated Ig-alpha ITAM | Reversible | `BCR(Y188_Y199~0) + Lyn(unique,SH3,SH2) <-> BCR(Y188_Y199~0!1).Lyn(unique!1,SH3,SH2) kf1, kr1` |
| 2 | SH2 domain of Lyn binds phosphorylated Ig-alpha ITAM | Reversible | `BCR(Y188_Y199~P) + Lyn(unique,SH3,SH2) <-> BCR(Y188_Y199~P!1).Lyn(unique,SH3,SH2!1) kf2a, kr2a` |
| 3 | SH2 domain of Lyn binds phosphorylated Ig-alpha ITAM | Reversible | `BCR(Y188_Y199~PP) + Lyn(unique,SH3,SH2) <-> BCR(Y188_Y199~PP!1).Lyn(unique,SH3,SH2!1) kf2b, kr2b` |
| 4 | autoinhibition of Lyn, SH2 domain of Lyn binds C-terminal pY | Reversible | `Lyn(unique,SH3,SH2,Y508~P) <-> Lyn(unique,SH3,SH2!1,Y508~P!1) kf3, kr3` |
| 5 | Lyn phosphorylates Ig-alpha ITAM | One-way | `Lyn(Y397~0).BCR() + BCR(Y188_Y199~0) -> Lyn(Y397~0).BCR() + BCR(Y188_Y199~P) 2*kp4a` |
| 6 | Lyn phosphorylates Ig-alpha ITAM | One-way | `Lyn(Y397~0).BCR() + BCR(Y188_Y199~P) -> Lyn(Y397~0).BCR() + BCR(Y188_Y199~PP) kp4b` |
| 7 | Lyn phosphorylates Ig-alpha ITAM | One-way | `Lyn(Y397~P).BCR() + BCR(Y188_Y199~0) -> Lyn(Y397~P).BCR() + BCR(Y188_Y199~P) 2*kp4c` |
| 8 | Lyn phosphorylates Ig-alpha ITAM | One-way | `Lyn(Y397~P).BCR() + BCR(Y188_Y199~P) -> Lyn(Y397~P).BCR() + BCR(Y188_Y199~PP) kp4d` |
| 9 | Lyn phosphorylates Ig-beta ITAM | One-way | `Lyn(Y397~0).BCR()+BCR(Y196_Y207~0) -> Lyn(Y397~0).BCR()+BCR(Y196_Y207~P) 2*kp5a` |
| 10 | Lyn phosphorylates Ig-beta ITAM | One-way | `Lyn(Y397~0).BCR()+BCR(Y196_Y207~P) -> Lyn(Y397~0).BCR()+BCR(Y196_Y207~PP) kp5b` |
| 11 | Lyn phosphorylates Ig-beta ITAM | One-way | `Lyn(Y397~P).BCR()+BCR(Y196_Y207~0) -> Lyn(Y397~P).BCR()+BCR(Y196_Y207~P) 2*kp5c` |
| 12 | Lyn phosphorylates Ig-beta ITAM | One-way | `Lyn(Y397~P).BCR()+BCR(Y196_Y207~P) -> Lyn(Y397~P).BCR()+BCR(Y196_Y207~PP) kp5d` |
| 13 | receptor-bound Lyn phosphorylates receptor-bound Lyn | One-way | `Lyn(Y397~0).BCR() + BCR().Lyn(Y397~0) -> Lyn(Y397~0).BCR() + BCR().Lyn(Y397~P) kp6a` |
| 14 | receptor-bound Lyn phosphorylates receptor-bound Lyn | One-way | `Lyn(Y397~P).BCR() + BCR().Lyn(Y397~0) -> Lyn(Y397~P).BCR() + BCR().Lyn(Y397~P) kp6b` |
| 15 | free Lyn phosphorylates free Lyn | One-way | `Lyn(unique,SH3,SH2,Y397~0,Y508~0) + Lyn(unique,SH3,SH2,Y397~0,Y508~0) -> Lyn(unique,SH3,SH2,Y397~0,Y508~0) + Lyn(unique,SH3,SH2,Y397~P,Y508~0) kp6c` |
| 16 | free Lyn phosphorylates free Lyn | One-way | `Lyn(unique,SH3,SH2,Y397~P,Y508~0) + Lyn(unique,SH3,SH2,Y397~0,Y508~0) -> Lyn(unique,SH3,SH2,Y397~P,Y508~0) + Lyn(unique,SH3,SH2,Y397~P,Y508~0) kp6d` |
| 17 | receptor-bound Lyn phosphorylates receptor-bound Fyn | One-way | `Lyn(Y397~0).BCR() + BCR().Fyn(Y420~0) -> Lyn(Y397~0).BCR() + BCR().Fyn(Y420~P) kp7a` |
| 18 | receptor-bound Lyn phosphorylates receptor-bound Fyn | One-way | `Lyn(Y397~P).BCR() + BCR().Fyn(Y420~0) -> Lyn(Y397~P).BCR() + BCR().Fyn(Y420~P) kp7b` |
| 19 | free Lyn phosphorylates free Fyn | One-way | `Lyn(unique,SH3,SH2,Y397~0,Y508~0) + Fyn(unique,SH3,SH2,Y420~0,Y531~0) -> Lyn(unique,SH3,SH2,Y397~0,Y508~0) + Fyn(unique,SH3,SH2,Y420~P,Y531~0) kp7c` |
| 20 | free Lyn phosphorylates free Fyn | One-way | `Lyn(unique,SH3,SH2,Y397~P,Y508~0) + Fyn(unique,SH3,SH2,Y420~0,Y531~0) -> Lyn(unique,SH3,SH2,Y397~P,Y508~0) + Fyn(unique,SH3,SH2,Y420~P,Y531~0) kp7d` |
| 21 | Lyn phosphorylates PAG | One-way | `Lyn(Y397~P,Y508).PAG(Y387_Y417~0) -> Lyn(Y397~P,Y508).PAG(Y387_Y417~P) kp8a` |
| 22 | Lyn phosphorylates PAG | One-way | `Lyn(SH2!1,Y397~P,Y508).PAG(Y163_Y181~0,Y387_Y417~P!1) -> Lyn(SH2!1,Y397~P,Y508).PAG(Y163_Y181~P,Y387_Y417~P!1) kp8b` |
| 23 | Lyn phosphorylates PAG | One-way | `Lyn(SH2!1,Y397~P,Y508).PAG(Y317~0,Y387_Y417~P!1) -> Lyn(SH2!1,Y397~P,Y508).PAG(Y317~P,Y387_Y417~P!1) kp8c` |
| 24 | unique domain of Fyn binds unphosphorylated Ig-alpha ITAM | Reversible | `BCR(Y188_Y199~0) + Fyn(unique,SH3,SH2) <-> BCR(Y188_Y199~0!1).Fyn(unique!1,SH3,SH2) kf9, kr9` |
| 25 | SH2 domain of Fyn binds phosphorylated Ig-alpha ITAM | Reversible | `BCR(Y188_Y199~P) + Fyn(unique,SH3,SH2) <-> BCR(Y188_Y199~P!1).Fyn(unique,SH3,SH2!1) kf10a, kr10a` |
| 26 | SH2 domain of Fyn binds phosphorylated Ig-alpha ITAM | Reversible | `BCR(Y188_Y199~PP) + Fyn(unique,SH3,SH2) <-> BCR(Y188_Y199~PP!1).Fyn(unique,SH3,SH2!1) kf10b, kr10b` |
| 27 | autoinhibition of Fyn, SH2 domain of Fyn binds C-terminal pY | Reversible | `Fyn(unique,SH3,SH2,Y531~P) <-> Fyn(unique,SH3,SH2!1,Y531~P!1) kf11, kr11` |
| 28 | Fyn phosphorylates Ig-beta ITAM | One-way | `Fyn(Y420~0).BCR() + BCR(Y196_Y207~0) -> Fyn(Y420~0).BCR() + BCR(Y196_Y207~P) 2*kp12a` |
| 29 | Fyn phosphorylates Ig-beta ITAM | One-way | `Fyn(Y420~0).BCR() + BCR(Y196_Y207~P) -> Fyn(Y420~0).BCR() + BCR(Y196_Y207~PP) kp12b` |
| 30 | Fyn phosphorylates Ig-beta ITAM | One-way | `Fyn(Y420~P).BCR() + BCR(Y196_Y207~0) -> Fyn(Y420~P).BCR() + BCR(Y196_Y207~P) 2*kp12c` |
| 31 | Fyn phosphorylates Ig-beta ITAM | One-way | `Fyn(Y420~P).BCR() + BCR(Y196_Y207~P) -> Fyn(Y420~P).BCR() + BCR(Y196_Y207~PP) kp12d` |
| 32 | Fyn phosphorylates Ig-alpha ITAM | One-way | `Fyn(Y420~0).BCR() + BCR(Y188_Y199~0) -> Fyn(Y420~0).BCR() + BCR(Y188_Y199~P) 2*kp13a` |
| 33 | Fyn phosphorylates Ig-alpha ITAM | One-way | `Fyn(Y420~0).BCR() + BCR(Y188_Y199~P) -> Fyn(Y420~0).BCR() + BCR(Y188_Y199~PP) kp13b` |
| 34 | Fyn phosphorylates Ig-alpha ITAM | One-way | `Fyn(Y420~P).BCR() + BCR(Y188_Y199~0) -> Fyn(Y420~P).BCR() + BCR(Y188_Y199~P) 2*kp13c` |
| 35 | Fyn phosphorylates Ig-alpha ITAM | One-way | `Fyn(Y420~P).BCR() + BCR(Y188_Y199~P) -> Fyn(Y420~P).BCR() + BCR(Y188_Y199~PP) kp13d` |
| 36 | receptor-bound Fyn phosphorylates receptor-bound Fyn | One-way | `Fyn(Y420~0).BCR() + BCR().Fyn(Y420~0) -> Fyn(Y420~0).BCR() + BCR().Fyn(Y420~P) kp14a` |
| 37 | receptor-bound Fyn phosphorylates receptor-bound Fyn | One-way | `Fyn(Y420~P).BCR() + BCR().Fyn(Y420~0) -> Fyn(Y420~P).BCR() + BCR().Fyn(Y420~P) kp14b` |
| 38 | free Fyn phosphorylates free Fyn | One-way | `Fyn(unique,SH3,SH2,Y420~0,Y531~0) + Fyn(unique,SH3,SH2,Y420~0,Y531~0) -> Fyn(unique,SH3,SH2,Y420~0,Y531~0) + Fyn(unique,SH3,SH2,Y420~P,Y531~0) kp14c` |
| 39 | free Fyn phosphorylates free Fyn | One-way | `Fyn(unique,SH3,SH2,Y420~P,Y531~0) + Fyn(unique,SH3,SH2,Y420~0,Y531~0) -> Fyn(unique,SH3,SH2,Y420~P,Y531~0) + Fyn(unique,SH3,SH2,Y420~P,Y531~0) kp14d` |
| 40 | receptor-bound Fyn phosphorylates receptor-bound Lyn | One-way | `Fyn(Y420~0).BCR() + BCR().Lyn(Y397~0) -> Fyn(Y420~0).BCR() + BCR().Lyn(Y397~P) kp15a` |
| 41 | receptor-bound Fyn phosphorylates receptor-bound Lyn | One-way | `Fyn(Y420~P).BCR() + BCR().Lyn(Y397~0) -> Fyn(Y420~P).BCR() + BCR().Lyn(Y397~P) kp15b` |
| 42 | free Fyn phosphorylates free Lyn | One-way | `Fyn(unique,SH3,SH2,Y420~0,Y531~0) + Lyn(unique,SH3,SH2,Y397~0,Y508~0) -> Fyn(unique,SH3,SH2,Y420~0,Y531~0) + Lyn(unique,SH3,SH2,Y397~P,Y508~0) kp15c` |
| 43 | free Fyn phosphorylates free Lyn | One-way | `Fyn(unique,SH3,SH2,Y420~P,Y531~0) + Lyn(unique,SH3,SH2,Y397~0,Y508~0) -> Fyn(unique,SH3,SH2,Y420~P,Y531~0) + Lyn(unique,SH3,SH2,Y397~P,Y508~0) kp15d` |
| 44 | Fyn phosphorylates PAG | One-way | `Fyn(SH2!1,Y420~P,Y531).PAG(Y163_Y181~P!1,Y387_Y417~0) -> Fyn(SH2!1,Y420~P,Y531).PAG(Y163_Y181~P!1,Y387_Y417~P) kp16a` |
| 45 | Fyn phosphorylates PAG | One-way | `Fyn(Y420~P,Y531).PAG(Y163_Y181~0)-> Fyn(Y420~P,Y531).PAG(Y163_Y181~P) kp16b` |
| 46 | Fyn phosphorylates PAG | One-way | `Fyn(SH2!1,Y420~P,Y531).PAG(Y163_Y181~P!1,Y317~0) -> Fyn(SH2!1,Y420~P,Y531).PAG(Y163_Y181~P!1,Y317~P) kp16c` |
| 47 | tandem SH2 domains of Syk bind doubly phosphorylated Ig-beta ITAM | Reversible | `Syk(tSH2) + BCR(Y196_Y207~PP) <-> Syk(tSH2!1).BCR(Y196_Y207~PP!1) kf17, kr17` |
| 48 | trans autophosphorylation of receptor-bound Syk | One-way | `Syk(tSH2!+,Y525_Y526~0) + Syk(tSH2!+,Y525_Y526~0) -> Syk(tSH2!+,Y525_Y526~0) + Syk(tSH2!+,Y525_Y526~P) kp18a` |
| 49 | trans autophosphorylation of receptor-bound Syk | One-way | `Syk(tSH2!+,Y525_Y526~P) + Syk(tSH2!+,Y525_Y526~0) -> Syk(tSH2!+,Y525_Y526~P) + Syk(tSH2!+,Y525_Y526~P) kp18b` |
| 50 | association, Lyn is free | One-way | `Lyn(unique,SH3,SH2) + PAG(PRS2,Y387_Y417) -> Lyn(unique,SH3!1,SH2).PAG(PRS2!1,Y387_Y417) kf19a` |
| 51 | dissociation | One-way | `Lyn(unique,SH3!1,SH2).PAG(PRS2!1,Y387_Y417) -> Lyn(unique,SH3,SH2) + PAG(PRS2,Y387_Y417) kr19a` |
| 52 | Lyn, already tethered in PAG by SH2, binds PAG via SH3 domain | One-way | `Lyn(unique,SH3,SH2!2).PAG(PRS2,Y387_Y417~P!2) -> Lyn(unique,SH3!1,SH2!2).PAG(PRS2!1,Y387_Y417~P!2) kf19b` |
| 53 | association, Lyn is free | One-way | `Lyn(unique,SH3,SH2) + PAG(PRS2,Y387_Y417~P) -> Lyn(unique,SH3,SH2!2).PAG(PRS2,Y387_Y417~P!2) kf20a` |
| 54 | association, Lyn is tethered to PAG (via SH3 domain-PRS interaction) | One-way | `Lyn(unique,SH3!1,SH2).PAG(PRS2!1,Y387_Y417~P) -> Lyn(unique,SH3!1,SH2!2).PAG(PRS2!1,Y387_Y417~P!2) kf20b` |
| 55 | release, breaking two-point attachment | One-way | `Lyn(unique,SH3!1,SH2!2).PAG(PRS2!1,Y387_Y417~P!2) -> Lyn(unique,SH3,SH2) + PAG(PRS2,Y387_Y417~P) kr20b` |
| 56 | association, Fyn is free | One-way | `Fyn(unique,SH3,SH2) + PAG(PRS1,Y163_Y181) -> Fyn(unique,SH3!1,SH2).PAG(PRS1!1,Y163_Y181) kf21a` |
| 57 | dissociation | One-way | `Fyn(unique,SH3!1,SH2).PAG(PRS1!1,Y163_Y181)-> Fyn(unique,SH3,SH2) + PAG(PRS1,Y163_Y181) kr21a` |
| 58 | association, Fyn is tethered to PAG (via SH2 domain-pY interaction) | One-way | `Fyn(unique,SH3,SH2!2).PAG(PRS1,Y163_Y181~P!2) -> Fyn(unique,SH3!1,SH2!2).PAG(PRS1!1,Y163_Y181~P!2) kf21b` |
| 59 | association, Fyn is free | One-way | `Fyn(unique,SH3,SH2) + PAG(PRS1,Y163_Y181~P) -> Fyn(unique,SH3,SH2!2).PAG(PRS1,Y163_Y181~P!2) kf22a` |
| 60 | association, Fyn is tethered to PAG (via SH3 domain-PRS interaction) | One-way | `Fyn(unique,SH3!1,SH2).PAG(PRS1!1,Y163_Y181~P) -> Fyn(unique,SH3!1,SH2!2).PAG(PRS1!1,Y163_Y181~P!2) kf22b` |
| 61 | release, breaking two-point attachment | One-way | `Fyn(unique,SH3!1,SH2!2).PAG(PRS1!1,Y163_Y181~P!2) -> Fyn(unique,SH3,SH2) + PAG(PRS1,Y163_Y181~P) kr22b` |
| 62 | SH2 domain of Csk binds pY317 docking site in PAG | Reversible | `Csk(SH2) + PAG(Y317~P) <-> Csk(SH2!3).PAG(Y317~P!3) kf23, kr23` |
| 63 | Csk cis phosphorylates C-terminal Y in Lyn | One-way | `Lyn(Y508~0).PAG().Csk() -> Lyn(Y508~P).PAG().Csk() kp24` |
| 64 | Csk cis phosphorylates C-terminal Y in Fyn | One-way | `Fyn(Y531~0).PAG().Csk() -> Fyn(Y531~P).PAG().Csk() kp25` |
| 65 | Dephosphorylation of Ig-alpha | One-way | `BCR(Y188_Y199~P) -> BCR(Y188_Y199~0) kdp26a` |
| 66 | Dephosphorylation of Ig-alpha | One-way | `BCR(Y188_Y199~PP) -> BCR(Y188_Y199~P) 2*kdp26b` |
| 67 | Dephosphorylation of Ig-beta | One-way | `BCR(Y196_Y207~P) -> BCR(Y196_Y207~0) kdp27a` |
| 68 | Dephosphorylation of Ig-beta | One-way | `BCR(Y196_Y207~PP) -> BCR(Y196_Y207~P) 2*kdp27b` |
| 69 | Dephosphorylation of Lyn | One-way | `Lyn(Y397~P) -> Lyn(Y397~0) kdp28a` |
| 70 | Dephosphorylation of Lyn | One-way | `Lyn(Y508~P) -> Lyn(Y508~0) kdp28b` |
| 71 | Dephosphorylation of Fyn | One-way | `Fyn(Y420~P) -> Fyn(Y420~0) kdp29a` |
| 72 | Dephosphorylation of Fyn | One-way | `Fyn(Y531~P) -> Fyn(Y531~0) kdp29b` |
| 73 | Dephosphorylation of PAG | One-way | `PAG(Y317~P) -> PAG(Y317~0) kdp30a` |
| 74 | Dephosphorylation of PAG | One-way | `PAG(Y387_Y417~P) -> PAG(Y387_Y417~0) kdp30b` |
| 75 | Dephosphorylation of PAG | One-way | `PAG(Y163_Y181~P) -> PAG(Y163_Y181~0) kdp30c` |
| 76 | Dephosphorylation of Syk | One-way | `Syk(Y525_Y526~P) -> Syk(Y525_Y526~0) kdp31` |

## 7. Observables and technical readouts

Every active observable is retained below. `Molecules` counts pattern matches; `Species` counts matching complete species.

- `Molecules Activated_Syk Syk(Y525_Y526~P)`
- `Molecules Ig_alpha_P BCR(Y188_Y199~P)`
- `Molecules Ig_alpha_PP BCR(Y188_Y199~PP)`
- `Molecules Ig_beta_PP BCR(Y196_Y207~PP)`
- `Molecules Activated_Lyn Lyn(Y397~P)`
- `Molecules Autoinhibited_Lyn Lyn(Y508~P!+)`
- `Molecules Activated_Fyn Fyn(Y420~P)`
- `Molecules Autoinhibited_Fyn Fyn(Y531~P!+)`
- `Molecules PAG1_Csk PAG(Y317~P!+)`

## 8. Actions and simulation workflow

- `generate_network({overwrite=>'1',TextReaction=>'1'})`

## 9. Technical caveats and ambiguities

The model resolves many phosphorylation and binding contexts; wildcards and omitted sites intentionally leave other molecular state unconstrained. Network generation requests `TextReaction`, which may be version-sensitive.
