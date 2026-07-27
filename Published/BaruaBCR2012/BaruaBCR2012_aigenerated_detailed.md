# Detailed Model Explanation: Barua 2012 B-cell receptor signaling model

## 1. Model identity and scope

`BaruaBCR_2012` models how B-cell receptor (BCR) signaling couples Lyn/Fyn/Syk activation to Csk–PAG negative regulation. Sources: `Published/BaruaBCR2012/BaruaBCR_2012.bngl` and `Published/BaruaBCR2012/metadata.yaml`.

## 2. BNGL block inventory

The file contains 118 active parameter declarations, 6 molecule types, 6 initial-species declarations, 0 functions, 76 concrete reaction rules, 9 observable declarations, and 1 execution command. It declares no compartments or anchors.

## 3. Parameters, functions, and rate laws

The parameter set is large because it assigns distinct rates to Lyn, Fyn, and Syk states and to singly versus doubly phosphorylated BCR ITAMs. Parameters are ordered exactly as the source families—initial scaling, Lyn/BCR, Fyn, Syk, and Csk–PAG—while remaining one-per-bullet for lookup.

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

**Rule-family orientation.** Rules are grouped in source order across Lyn binding/activity, BCR ITAM phosphorylation, Fyn, Syk, and Csk–PAG inhibition. Repeated rows are retained because kinase state and target ITAM state select different rates.

| # | Direction | Required molecules/sites | Net bond, state, or species edit | Rate/expression | Functional interpretation |
| ---: | --- | --- | --- | --- | --- |
| 1 | Reversible | `BCR` (`Y188_Y199`); `Lyn` (`unique`, `SH3`, `SH2`) | forms the explicitly site-matched bond(s) | kf1, kr1 | unique domain of Lyn binds unphosphorylated Ig-alpha ITAM. |
| 2 | Reversible | `BCR` (`Y188_Y199`); `Lyn` (`unique`, `SH3`, `SH2`) | forms the explicitly site-matched bond(s) | kf2a, kr2a | SH2 domain of Lyn binds phosphorylated Ig-alpha ITAM; this `kf2a, kr2a` variant requires `BCR` (`Y188_Y199`); `Lyn` (`unique`, `SH3`, `SH2`) and forms the explicitly site-matched bond(s). |
| 3 | Reversible | `BCR` (`Y188_Y199`); `Lyn` (`unique`, `SH3`, `SH2`) | forms the explicitly site-matched bond(s) | kf2b, kr2b | SH2 domain of Lyn binds phosphorylated Ig-alpha ITAM; this `kf2b, kr2b` variant requires `BCR` (`Y188_Y199`); `Lyn` (`unique`, `SH3`, `SH2`) and forms the explicitly site-matched bond(s). |
| 4 | Reversible | `Lyn` (`unique`, `SH3`, `SH2`, `Y508`) | forms the explicitly site-matched bond(s) | kf3, kr3 | autoinhibition of Lyn, SH2 domain of Lyn binds C-terminal pY. |
| 5 | One-way | `Lyn` (`Y397`); `BCR`; `BCR` (`Y188_Y199`) | `BCR.Y188_Y199` 0→P | 2*kp4a | Lyn phosphorylates Ig-alpha ITAM; this `2*kp4a` variant requires `Lyn` (`Y397`); `BCR`; `BCR` (`Y188_Y199`) and `BCR.Y188_Y199` 0→P. |
| 6 | One-way | `Lyn` (`Y397`); `BCR`; `BCR` (`Y188_Y199`) | `BCR.Y188_Y199` P→PP | kp4b | Lyn phosphorylates Ig-alpha ITAM; this `kp4b` variant requires `Lyn` (`Y397`); `BCR`; `BCR` (`Y188_Y199`) and `BCR.Y188_Y199` P→PP. |
| 7 | One-way | `Lyn` (`Y397`); `BCR`; `BCR` (`Y188_Y199`) | `BCR.Y188_Y199` 0→P | 2*kp4c | Lyn phosphorylates Ig-alpha ITAM; this `2*kp4c` variant requires `Lyn` (`Y397`); `BCR`; `BCR` (`Y188_Y199`) and `BCR.Y188_Y199` 0→P. |
| 8 | One-way | `Lyn` (`Y397`); `BCR`; `BCR` (`Y188_Y199`) | `BCR.Y188_Y199` P→PP | kp4d | Lyn phosphorylates Ig-alpha ITAM; this `kp4d` variant requires `Lyn` (`Y397`); `BCR`; `BCR` (`Y188_Y199`) and `BCR.Y188_Y199` P→PP. |
| 9 | One-way | `Lyn` (`Y397`); `BCR`; `BCR` (`Y196_Y207`) | `BCR.Y196_Y207` 0→P | 2*kp5a | Lyn phosphorylates Ig-beta ITAM; this `2*kp5a` variant requires `Lyn` (`Y397`); `BCR`; `BCR` (`Y196_Y207`) and `BCR.Y196_Y207` 0→P. |
| 10 | One-way | `Lyn` (`Y397`); `BCR`; `BCR` (`Y196_Y207`) | `BCR.Y196_Y207` P→PP | kp5b | Lyn phosphorylates Ig-beta ITAM; this `kp5b` variant requires `Lyn` (`Y397`); `BCR`; `BCR` (`Y196_Y207`) and `BCR.Y196_Y207` P→PP. |
| 11 | One-way | `Lyn` (`Y397`); `BCR`; `BCR` (`Y196_Y207`) | `BCR.Y196_Y207` 0→P | 2*kp5c | Lyn phosphorylates Ig-beta ITAM; this `2*kp5c` variant requires `Lyn` (`Y397`); `BCR`; `BCR` (`Y196_Y207`) and `BCR.Y196_Y207` 0→P. |
| 12 | One-way | `Lyn` (`Y397`); `BCR`; `BCR` (`Y196_Y207`) | `BCR.Y196_Y207` P→PP | kp5d | Lyn phosphorylates Ig-beta ITAM; this `kp5d` variant requires `Lyn` (`Y397`); `BCR`; `BCR` (`Y196_Y207`) and `BCR.Y196_Y207` P→PP. |
| 13 | One-way | `Lyn` (`Y397`); `BCR` | `Lyn.Y397` 0→P | kp6a | receptor-bound Lyn phosphorylates receptor-bound Lyn; this `kp6a` variant requires `Lyn` (`Y397`); `BCR` and `Lyn.Y397` 0→P. |
| 14 | One-way | `Lyn` (`Y397`); `BCR` | `Lyn.Y397` 0→P | kp6b | receptor-bound Lyn phosphorylates receptor-bound Lyn; this `kp6b` variant requires `Lyn` (`Y397`); `BCR` and `Lyn.Y397` 0→P. |
| 15 | One-way | `Lyn` (`unique`, `SH3`, `SH2`, `Y397`, `Y508`) | `Lyn.Y397` 0→P | kp6c | free Lyn phosphorylates free Lyn; this `kp6c` variant requires `Lyn` (`unique`, `SH3`, `SH2`, `Y397`, `Y508`) and `Lyn.Y397` 0→P. |
| 16 | One-way | `Lyn` (`unique`, `SH3`, `SH2`, `Y397`, `Y508`) | `Lyn.Y397` 0→P | kp6d | free Lyn phosphorylates free Lyn; this `kp6d` variant requires `Lyn` (`unique`, `SH3`, `SH2`, `Y397`, `Y508`) and `Lyn.Y397` 0→P. |
| 17 | One-way | `Lyn` (`Y397`); `BCR`; `Fyn` (`Y420`) | `Fyn.Y420` 0→P | kp7a | receptor-bound Lyn phosphorylates receptor-bound Fyn; this `kp7a` variant requires `Lyn` (`Y397`); `BCR`; `Fyn` (`Y420`) and `Fyn.Y420` 0→P. |
| 18 | One-way | `Lyn` (`Y397`); `BCR`; `Fyn` (`Y420`) | `Fyn.Y420` 0→P | kp7b | receptor-bound Lyn phosphorylates receptor-bound Fyn; this `kp7b` variant requires `Lyn` (`Y397`); `BCR`; `Fyn` (`Y420`) and `Fyn.Y420` 0→P. |
| 19 | One-way | `Lyn` (`unique`, `SH3`, `SH2`, `Y397`, `Y508`); `Fyn` (`unique`, `SH3`, `SH2`, `Y420`, `Y531`) | `Fyn.Y420` 0→P | kp7c | free Lyn phosphorylates free Fyn; this `kp7c` variant requires `Lyn` (`unique`, `SH3`, `SH2`, `Y397`, `Y508`); `Fyn` (`unique`, `SH3`, `SH2`, `Y420`, `Y531`) and `Fyn.Y420` 0→P. |
| 20 | One-way | `Lyn` (`unique`, `SH3`, `SH2`, `Y397`, `Y508`); `Fyn` (`unique`, `SH3`, `SH2`, `Y420`, `Y531`) | `Fyn.Y420` 0→P | kp7d | free Lyn phosphorylates free Fyn; this `kp7d` variant requires `Lyn` (`unique`, `SH3`, `SH2`, `Y397`, `Y508`); `Fyn` (`unique`, `SH3`, `SH2`, `Y420`, `Y531`) and `Fyn.Y420` 0→P. |
| 21 | One-way | `Lyn` (`Y397`, `Y508`); `PAG` (`Y387_Y417`) | `PAG.Y387_Y417` 0→P | kp8a | Lyn phosphorylates PAG; this `kp8a` variant requires `Lyn` (`Y397`, `Y508`); `PAG` (`Y387_Y417`) and `PAG.Y387_Y417` 0→P. |
| 22 | One-way | `Lyn` (`SH2`, `Y397`, `Y508`); `PAG` (`Y163_Y181`, `Y387_Y417`) | `PAG.Y163_Y181` 0→P | kp8b | Lyn phosphorylates PAG; this `kp8b` variant requires `Lyn` (`SH2`, `Y397`, `Y508`); `PAG` (`Y163_Y181`, `Y387_Y417`) and `PAG.Y163_Y181` 0→P. |
| 23 | One-way | `Lyn` (`SH2`, `Y397`, `Y508`); `PAG` (`Y317`, `Y387_Y417`) | `PAG.Y317` 0→P | kp8c | Lyn phosphorylates PAG; this `kp8c` variant requires `Lyn` (`SH2`, `Y397`, `Y508`); `PAG` (`Y317`, `Y387_Y417`) and `PAG.Y317` 0→P. |
| 24 | Reversible | `BCR` (`Y188_Y199`); `Fyn` (`unique`, `SH3`, `SH2`) | forms the explicitly site-matched bond(s) | kf9, kr9 | unique domain of Fyn binds unphosphorylated Ig-alpha ITAM. |
| 25 | Reversible | `BCR` (`Y188_Y199`); `Fyn` (`unique`, `SH3`, `SH2`) | forms the explicitly site-matched bond(s) | kf10a, kr10a | SH2 domain of Fyn binds phosphorylated Ig-alpha ITAM; this `kf10a, kr10a` variant requires `BCR` (`Y188_Y199`); `Fyn` (`unique`, `SH3`, `SH2`) and forms the explicitly site-matched bond(s). |
| 26 | Reversible | `BCR` (`Y188_Y199`); `Fyn` (`unique`, `SH3`, `SH2`) | forms the explicitly site-matched bond(s) | kf10b, kr10b | SH2 domain of Fyn binds phosphorylated Ig-alpha ITAM; this `kf10b, kr10b` variant requires `BCR` (`Y188_Y199`); `Fyn` (`unique`, `SH3`, `SH2`) and forms the explicitly site-matched bond(s). |
| 27 | Reversible | `Fyn` (`unique`, `SH3`, `SH2`, `Y531`) | forms the explicitly site-matched bond(s) | kf11, kr11 | autoinhibition of Fyn, SH2 domain of Fyn binds C-terminal pY. |
| 28 | One-way | `Fyn` (`Y420`); `BCR`; `BCR` (`Y196_Y207`) | `BCR.Y196_Y207` 0→P | 2*kp12a | Fyn phosphorylates Ig-beta ITAM; this `2*kp12a` variant requires `Fyn` (`Y420`); `BCR`; `BCR` (`Y196_Y207`) and `BCR.Y196_Y207` 0→P. |
| 29 | One-way | `Fyn` (`Y420`); `BCR`; `BCR` (`Y196_Y207`) | `BCR.Y196_Y207` P→PP | kp12b | Fyn phosphorylates Ig-beta ITAM; this `kp12b` variant requires `Fyn` (`Y420`); `BCR`; `BCR` (`Y196_Y207`) and `BCR.Y196_Y207` P→PP. |
| 30 | One-way | `Fyn` (`Y420`); `BCR`; `BCR` (`Y196_Y207`) | `BCR.Y196_Y207` 0→P | 2*kp12c | Fyn phosphorylates Ig-beta ITAM; this `2*kp12c` variant requires `Fyn` (`Y420`); `BCR`; `BCR` (`Y196_Y207`) and `BCR.Y196_Y207` 0→P. |
| 31 | One-way | `Fyn` (`Y420`); `BCR`; `BCR` (`Y196_Y207`) | `BCR.Y196_Y207` P→PP | kp12d | Fyn phosphorylates Ig-beta ITAM; this `kp12d` variant requires `Fyn` (`Y420`); `BCR`; `BCR` (`Y196_Y207`) and `BCR.Y196_Y207` P→PP. |
| 32 | One-way | `Fyn` (`Y420`); `BCR`; `BCR` (`Y188_Y199`) | `BCR.Y188_Y199` 0→P | 2*kp13a | Fyn phosphorylates Ig-alpha ITAM; this `2*kp13a` variant requires `Fyn` (`Y420`); `BCR`; `BCR` (`Y188_Y199`) and `BCR.Y188_Y199` 0→P. |
| 33 | One-way | `Fyn` (`Y420`); `BCR`; `BCR` (`Y188_Y199`) | `BCR.Y188_Y199` P→PP | kp13b | Fyn phosphorylates Ig-alpha ITAM; this `kp13b` variant requires `Fyn` (`Y420`); `BCR`; `BCR` (`Y188_Y199`) and `BCR.Y188_Y199` P→PP. |
| 34 | One-way | `Fyn` (`Y420`); `BCR`; `BCR` (`Y188_Y199`) | `BCR.Y188_Y199` 0→P | 2*kp13c | Fyn phosphorylates Ig-alpha ITAM; this `2*kp13c` variant requires `Fyn` (`Y420`); `BCR`; `BCR` (`Y188_Y199`) and `BCR.Y188_Y199` 0→P. |
| 35 | One-way | `Fyn` (`Y420`); `BCR`; `BCR` (`Y188_Y199`) | `BCR.Y188_Y199` P→PP | kp13d | Fyn phosphorylates Ig-alpha ITAM; this `kp13d` variant requires `Fyn` (`Y420`); `BCR`; `BCR` (`Y188_Y199`) and `BCR.Y188_Y199` P→PP. |
| 36 | One-way | `Fyn` (`Y420`); `BCR` | `Fyn.Y420` 0→P | kp14a | receptor-bound Fyn phosphorylates receptor-bound Fyn; this `kp14a` variant requires `Fyn` (`Y420`); `BCR` and `Fyn.Y420` 0→P. |
| 37 | One-way | `Fyn` (`Y420`); `BCR` | `Fyn.Y420` 0→P | kp14b | receptor-bound Fyn phosphorylates receptor-bound Fyn; this `kp14b` variant requires `Fyn` (`Y420`); `BCR` and `Fyn.Y420` 0→P. |
| 38 | One-way | `Fyn` (`unique`, `SH3`, `SH2`, `Y420`, `Y531`) | `Fyn.Y420` 0→P | kp14c | free Fyn phosphorylates free Fyn; this `kp14c` variant requires `Fyn` (`unique`, `SH3`, `SH2`, `Y420`, `Y531`) and `Fyn.Y420` 0→P. |
| 39 | One-way | `Fyn` (`unique`, `SH3`, `SH2`, `Y420`, `Y531`) | `Fyn.Y420` 0→P | kp14d | free Fyn phosphorylates free Fyn; this `kp14d` variant requires `Fyn` (`unique`, `SH3`, `SH2`, `Y420`, `Y531`) and `Fyn.Y420` 0→P. |
| 40 | One-way | `Fyn` (`Y420`); `BCR`; `Lyn` (`Y397`) | `Lyn.Y397` 0→P | kp15a | receptor-bound Fyn phosphorylates receptor-bound Lyn; this `kp15a` variant requires `Fyn` (`Y420`); `BCR`; `Lyn` (`Y397`) and `Lyn.Y397` 0→P. |
| 41 | One-way | `Fyn` (`Y420`); `BCR`; `Lyn` (`Y397`) | `Lyn.Y397` 0→P | kp15b | receptor-bound Fyn phosphorylates receptor-bound Lyn; this `kp15b` variant requires `Fyn` (`Y420`); `BCR`; `Lyn` (`Y397`) and `Lyn.Y397` 0→P. |
| 42 | One-way | `Fyn` (`unique`, `SH3`, `SH2`, `Y420`, `Y531`); `Lyn` (`unique`, `SH3`, `SH2`, `Y397`, `Y508`) | `Lyn.Y397` 0→P | kp15c | free Fyn phosphorylates free Lyn; this `kp15c` variant requires `Fyn` (`unique`, `SH3`, `SH2`, `Y420`, `Y531`); `Lyn` (`unique`, `SH3`, `SH2`, `Y397`, `Y508`) and `Lyn.Y397` 0→P. |
| 43 | One-way | `Fyn` (`unique`, `SH3`, `SH2`, `Y420`, `Y531`); `Lyn` (`unique`, `SH3`, `SH2`, `Y397`, `Y508`) | `Lyn.Y397` 0→P | kp15d | free Fyn phosphorylates free Lyn; this `kp15d` variant requires `Fyn` (`unique`, `SH3`, `SH2`, `Y420`, `Y531`); `Lyn` (`unique`, `SH3`, `SH2`, `Y397`, `Y508`) and `Lyn.Y397` 0→P. |
| 44 | One-way | `Fyn` (`SH2`, `Y420`, `Y531`); `PAG` (`Y163_Y181`, `Y387_Y417`) | `PAG.Y387_Y417` 0→P | kp16a | Fyn phosphorylates PAG; this `kp16a` variant requires `Fyn` (`SH2`, `Y420`, `Y531`); `PAG` (`Y163_Y181`, `Y387_Y417`) and `PAG.Y387_Y417` 0→P. |
| 45 | One-way | `Fyn` (`Y420`, `Y531`); `PAG` (`Y163_Y181`) | `PAG.Y163_Y181` 0→P | kp16b | Fyn phosphorylates PAG; this `kp16b` variant requires `Fyn` (`Y420`, `Y531`); `PAG` (`Y163_Y181`) and `PAG.Y163_Y181` 0→P. |
| 46 | One-way | `Fyn` (`SH2`, `Y420`, `Y531`); `PAG` (`Y163_Y181`, `Y317`) | `PAG.Y317` 0→P | kp16c | Fyn phosphorylates PAG; this `kp16c` variant requires `Fyn` (`SH2`, `Y420`, `Y531`); `PAG` (`Y163_Y181`, `Y317`) and `PAG.Y317` 0→P. |
| 47 | Reversible | `Syk` (`tSH2`); `BCR` (`Y196_Y207`) | forms the explicitly site-matched bond(s) | kf17, kr17 | tandem SH2 domains of Syk bind doubly phosphorylated Ig-beta ITAM. |
| 48 | One-way | `Syk` (`tSH2`, `Y525_Y526`) | `Syk.Y525_Y526` 0→P | kp18a | trans autophosphorylation of receptor-bound Syk; this `kp18a` variant requires `Syk` (`tSH2`, `Y525_Y526`) and `Syk.Y525_Y526` 0→P. |
| 49 | One-way | `Syk` (`tSH2`, `Y525_Y526`) | `Syk.Y525_Y526` 0→P | kp18b | trans autophosphorylation of receptor-bound Syk; this `kp18b` variant requires `Syk` (`tSH2`, `Y525_Y526`) and `Syk.Y525_Y526` 0→P. |
| 50 | One-way | `Lyn` (`unique`, `SH3`, `SH2`); `PAG` (`PRS2`, `Y387_Y417`) | forms the explicitly site-matched bond(s) | kf19a | association, Lyn is free; this `kf19a` variant requires `Lyn` (`unique`, `SH3`, `SH2`); `PAG` (`PRS2`, `Y387_Y417`) and forms the explicitly site-matched bond(s). |
| 51 | One-way | `Lyn` (`unique`, `SH3`, `SH2`); `PAG` (`PRS2`, `Y387_Y417`) | releases the explicitly site-matched bond(s) | kr19a | dissociation; this `kr19a` variant requires `Lyn` (`unique`, `SH3`, `SH2`); `PAG` (`PRS2`, `Y387_Y417`) and releases the explicitly site-matched bond(s). |
| 52 | One-way | `Lyn` (`unique`, `SH3`, `SH2`); `PAG` (`PRS2`, `Y387_Y417`) | forms the explicitly site-matched bond(s) | kf19b | Lyn, already tethered in PAG by SH2, binds PAG via SH3 domain. |
| 53 | One-way | `Lyn` (`unique`, `SH3`, `SH2`); `PAG` (`PRS2`, `Y387_Y417`) | forms the explicitly site-matched bond(s) | kf20a | association, Lyn is free; this `kf20a` variant requires `Lyn` (`unique`, `SH3`, `SH2`); `PAG` (`PRS2`, `Y387_Y417`) and forms the explicitly site-matched bond(s). |
| 54 | One-way | `Lyn` (`unique`, `SH3`, `SH2`); `PAG` (`PRS2`, `Y387_Y417`) | forms the explicitly site-matched bond(s) | kf20b | association, Lyn is tethered to PAG (via SH3 domain-PRS interaction). |
| 55 | One-way | `Lyn` (`unique`, `SH3`, `SH2`); `PAG` (`PRS2`, `Y387_Y417`) | releases the explicitly site-matched bond(s) | kr20b | release, breaking two-point attachment; this `kr20b` variant requires `Lyn` (`unique`, `SH3`, `SH2`); `PAG` (`PRS2`, `Y387_Y417`) and releases the explicitly site-matched bond(s). |
| 56 | One-way | `Fyn` (`unique`, `SH3`, `SH2`); `PAG` (`PRS1`, `Y163_Y181`) | forms the explicitly site-matched bond(s) | kf21a | association, Fyn is free; this `kf21a` variant requires `Fyn` (`unique`, `SH3`, `SH2`); `PAG` (`PRS1`, `Y163_Y181`) and forms the explicitly site-matched bond(s). |
| 57 | One-way | `Fyn` (`unique`, `SH3`, `SH2`); `PAG` (`PRS1`, `Y163_Y181`) | releases the explicitly site-matched bond(s) | kr21a | dissociation; this `kr21a` variant requires `Fyn` (`unique`, `SH3`, `SH2`); `PAG` (`PRS1`, `Y163_Y181`) and releases the explicitly site-matched bond(s). |
| 58 | One-way | `Fyn` (`unique`, `SH3`, `SH2`); `PAG` (`PRS1`, `Y163_Y181`) | forms the explicitly site-matched bond(s) | kf21b | association, Fyn is tethered to PAG (via SH2 domain-pY interaction). |
| 59 | One-way | `Fyn` (`unique`, `SH3`, `SH2`); `PAG` (`PRS1`, `Y163_Y181`) | forms the explicitly site-matched bond(s) | kf22a | association, Fyn is free; this `kf22a` variant requires `Fyn` (`unique`, `SH3`, `SH2`); `PAG` (`PRS1`, `Y163_Y181`) and forms the explicitly site-matched bond(s). |
| 60 | One-way | `Fyn` (`unique`, `SH3`, `SH2`); `PAG` (`PRS1`, `Y163_Y181`) | forms the explicitly site-matched bond(s) | kf22b | association, Fyn is tethered to PAG (via SH3 domain-PRS interaction). |
| 61 | One-way | `Fyn` (`unique`, `SH3`, `SH2`); `PAG` (`PRS1`, `Y163_Y181`) | releases the explicitly site-matched bond(s) | kr22b | release, breaking two-point attachment; this `kr22b` variant requires `Fyn` (`unique`, `SH3`, `SH2`); `PAG` (`PRS1`, `Y163_Y181`) and releases the explicitly site-matched bond(s). |
| 62 | Reversible | `Csk` (`SH2`); `PAG` (`Y317`) | forms the explicitly site-matched bond(s) | kf23, kr23 | SH2 domain of Csk binds pY317 docking site in PAG. |
| 63 | One-way | `Lyn` (`Y508`); `PAG`; `Csk` | `Lyn.Y508` 0→P | kp24 | Csk cis phosphorylates C-terminal Y in Lyn. |
| 64 | One-way | `Fyn` (`Y531`); `PAG`; `Csk` | `Fyn.Y531` 0→P | kp25 | Csk cis phosphorylates C-terminal Y in Fyn. |
| 65 | One-way | `BCR` (`Y188_Y199`) | `BCR.Y188_Y199` P→0 | kdp26a | Dephosphorylation of Ig-alpha; this `kdp26a` variant requires `BCR` (`Y188_Y199`) and `BCR.Y188_Y199` P→0. |
| 66 | One-way | `BCR` (`Y188_Y199`) | `BCR.Y188_Y199` PP→P | 2*kdp26b | Dephosphorylation of Ig-alpha; this `2*kdp26b` variant requires `BCR` (`Y188_Y199`) and `BCR.Y188_Y199` PP→P. |
| 67 | One-way | `BCR` (`Y196_Y207`) | `BCR.Y196_Y207` P→0 | kdp27a | Dephosphorylation of Ig-beta; this `kdp27a` variant requires `BCR` (`Y196_Y207`) and `BCR.Y196_Y207` P→0. |
| 68 | One-way | `BCR` (`Y196_Y207`) | `BCR.Y196_Y207` PP→P | 2*kdp27b | Dephosphorylation of Ig-beta; this `2*kdp27b` variant requires `BCR` (`Y196_Y207`) and `BCR.Y196_Y207` PP→P. |
| 69 | One-way | `Lyn` (`Y397`) | `Lyn.Y397` P→0 | kdp28a | Dephosphorylation of Lyn; this `kdp28a` variant requires `Lyn` (`Y397`) and `Lyn.Y397` P→0. |
| 70 | One-way | `Lyn` (`Y508`) | `Lyn.Y508` P→0 | kdp28b | Dephosphorylation of Lyn; this `kdp28b` variant requires `Lyn` (`Y508`) and `Lyn.Y508` P→0. |
| 71 | One-way | `Fyn` (`Y420`) | `Fyn.Y420` P→0 | kdp29a | Dephosphorylation of Fyn; this `kdp29a` variant requires `Fyn` (`Y420`) and `Fyn.Y420` P→0. |
| 72 | One-way | `Fyn` (`Y531`) | `Fyn.Y531` P→0 | kdp29b | Dephosphorylation of Fyn; this `kdp29b` variant requires `Fyn` (`Y531`) and `Fyn.Y531` P→0. |
| 73 | One-way | `PAG` (`Y317`) | `PAG.Y317` P→0 | kdp30a | Dephosphorylation of PAG; this `kdp30a` variant requires `PAG` (`Y317`) and `PAG.Y317` P→0. |
| 74 | One-way | `PAG` (`Y387_Y417`) | `PAG.Y387_Y417` P→0 | kdp30b | Dephosphorylation of PAG; this `kdp30b` variant requires `PAG` (`Y387_Y417`) and `PAG.Y387_Y417` P→0. |
| 75 | One-way | `PAG` (`Y163_Y181`) | `PAG.Y163_Y181` P→0 | kdp30c | Dephosphorylation of PAG; this `kdp30c` variant requires `PAG` (`Y163_Y181`) and `PAG.Y163_Y181` P→0. |
| 76 | One-way | `Syk` (`Y525_Y526`) | `Syk.Y525_Y526` P→0 | kdp31 | Dephosphorylation of Syk. |

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
