# Coder Model Explanation: An 2009 TLR4 signaling model

## 1. Model identity and scope

`An_2009` models how lipopolysaccharide (LPS) recognition by Toll-like receptor 4 (TLR4) drives adaptor signaling, NF-κB activation, inflammatory outputs, and feedback. Sources: `Published/An2009/An_2009.bngl` and `Published/An2009/metadata.yaml`.

## 2. BNGL block inventory

The file contains 97 active parameter declarations, 31 molecule types, 19 initial-species declarations, 0 functions, 41 concrete reaction rules, 19 observable declarations, and 7 execution commands. It declares no compartments or anchors.

## 3. Parameters, functions, and rate laws

Every active parameter declaration is listed below; expressions are retained verbatim so scaling and dependencies remain inspectable.

- `LPS_MD2_Bind 0.001`
- `LPS_MD2_Unbind 0.1`
- `LPS_CD14_Bind 0.001`
- `LPS_CD14_Unbind 0.1`
- `CD14_MD2_Bind 0.001`
- `CD14_MD2_Unbind 0.1`
- `LPS_TLR4_Bind 0.001`
- `LPS_TLR4_Unbind 0.1`
- `CD14_TLR4_Bind 0.001`
- `CD14_TLR4_Unbind 0.1`
- `MD2_TLR4_Bind 0.001`
- `MD2_TLR4_Unbind 0.1`
- `TLR4_Complex_Dimer_Bind 0.001`
- `TLR4_Complex_Dimer_Unbind 0.1`
- `RP1_TRIF_Bind 0.001`
- `RP1_TRIF_Unbind 0.1`
- `TRIF_TRAF6_Bind 0.001`
- `TRIF_TRAF6_Unbind 0.1`
- `RP1_TRAF6_Bind 0.001`
- `RP1_TRAF6_Unbind 0.1`
- `TLR4_TRAM_Bind 0.001`
- `TLR4_TRAM_Unbind 0.1`
- `TLR4TRAM_TRIF_Bind 0.001`
- `TLR4TRAM_TRIF_Unbind 0.1`
- `TRAF6_TRIF_Bind 0.001`
- `TRAF6_TRIF_Unbind 0.1`
- `TRAF6TRIF_TAK1_Activate 0.001`
- `MyD88_IRAK4_Bind 0.001`
- `MyD88_IRAK4_Unbind 0.1`
- `MyD88_IRAK1_Bind 0.001`
- `MyD88_IRAK1_Unbind 0.1`
- `IRAK1_IRAK4_Bind 0.001`
- `IRAK1_IRAK4_Unbind 0.1`
- `TLR4_MAL_Bind 0.001`
- `TLR4_MAL_Unbind 0.1`
- `TLR4MAL_MyD88_Bind 0.001`
- `TLR4MAL_MyD88_Unbind 0.1`
- `MyD88IRAK1_TRAF6_Bind 0.001`
- `MyD88IRAK1_TRAF6_B_Unbind 0.1`
- `MyD88IRAK1TRAF6_TAK1_Activate 0.001`
- `TRAF6_MyD88IRAK1_Bind 0.001`
- `TRAF6_MyD88IRAK1_Unbind 0.1`
- `TAK1_Ikk_Complex_Activate 0.001`
- `Ikk_complex_IkB_Phos 0.00001`
- `IkB_Proteasome23_Degrade 0.1`
- `p65_p50_Bind 0.001`
- `p65_p50_Unbind 0.1`
- `NFkB_DNA_A20_Bind 0.001`
- `A20_Transcription_Execute 1`
- `A20_TRAF6_Bind 0.001`
- `A20_TRAF6_Unbind 0.1`
- `NFkB_DNA_A20_Unbind 0.1`
- `NFkB_DNA_TNF_Bind 0.001`
- `NFkB_DNA_TNF_Unbind 0.1`
- `TNF_Transcription_Execute 1`
- `CD14_Init 10000`
- `MD2_Init 10000`
- `TLR_Init 10000`
- `LPS_Init 100`
- `TRAM_Init 10000`
- `MAL_Init 10000`
- `TRIF_Init 10000`
- `MyD88_Init 10000`
- `RP1_Init 10000`
- `IRAK1_Init 10000`
- `IRAK4_Init 10000`
- `TRAF6_Init 10000`
- `TAK1_Init 10000`
- `Ikk_Complex_Init 10000`
- `Proteasome23_Init 10000`
- `p65_Init 10000`
- `IkB_Init 10000`
- `p50_Init 10000`
- `DNA 2`
- `A20_Translation_Execute 0.1`
- `TNF_Translation_Execute 0.1`
- `TAK1_Degradation 0`
- `NFkB_Degredation 0`
- `A20_MyD88IRAK1TRAF6_Degrade 10`
- `A20_TRAF6TRIFRP1_Degrade 10`
- `A20_Init 0`
- `A20_Preconditioned 0`
- `Ikk_Degradation_Rate 0`
- `NFkB_DNA_IkB_Bind 0.001`
- `NFkB_DNA_IkB_Unbind 0.01`
- `IkB_Transcription_Execute 1`
- `IkB_Translation_Execute 0.1`
- `A20_IkkAct_Deactivate 10`
- `IkB_DegradeNFkB 0.001`
- `NFkB_Inactive_Cytoplasm 10000`
- `NFkB_IkB_Bind 0.001`
- `NFkB_Translocation_Nucleus 0.01`
- `NFkB_IkB_Unbind 0.0001`
- `TAK1_Deactivation 0.10`
- `Ikk_Deactivation 0`
- `TNF_Degrade 0.0005`
- `A20_Degrade 0.0001`

There is no functions block; rules use parameters or literal expressions directly.

## 4. Molecule types, sites, and states

| Molecule type | Site count | Sites/components | Internal states | Anchor/allowed compartments | Binding/modification roles | Notes |
| --- | ---: | --- | --- | --- | --- | --- |
| `CD14` | 3 | `TLR4, MD2, LPS` | `none` | None | Binding/state components are used exactly as shown in the rule inventory. | Declaration: `CD14(TLR4,MD2,LPS)` |
| `MD2` | 3 | `CD14, TLR4, LPS` | `none` | None | Binding/state components are used exactly as shown in the rule inventory. | Declaration: `MD2(CD14,TLR4,LPS)` |
| `TLR4` | 6 | `MAL, TRAM, TLR4, CD14, MD2, LPS` | `none` | None | Binding/state components are used exactly as shown in the rule inventory. | Declaration: `TLR4(MAL,TRAM,TLR4,CD14,MD2,LPS)` |
| `TRAM` | 2 | `TLR4, TRIF` | `none` | None | Binding/state components are used exactly as shown in the rule inventory. | Declaration: `TRAM(TLR4,TRIF)` |
| `TRIF` | 5 | `TRAM, TRAF6, RIP1, TRAF4, SARM` | `none` | None | Binding/state components are used exactly as shown in the rule inventory. | Declaration: `TRIF(TRAM,TRAF6,RIP1,TRAF4,SARM)` |
| `SARM` | 1 | `TRIF` | `none` | None | Binding/state components are used exactly as shown in the rule inventory. | Declaration: `SARM(TRIF)` |
| `TRAF4` | 3 | `TRAF6, TAK1, TRIF` | `none` | None | Binding/state components are used exactly as shown in the rule inventory. | Declaration: `TRAF4(TRAF6,TAK1,TRIF)` |
| `IRAK1` | 4 | `IRAK4, MyD88, Tollip, TRAF6` | `none` | None | Binding/state components are used exactly as shown in the rule inventory. | Declaration: `IRAK1(IRAK4,MyD88,Tollip,TRAF6)` |
| `Tollip` | 1 | `IRAK1` | `none` | None | Binding/state components are used exactly as shown in the rule inventory. | Declaration: `Tollip(IRAK1)` |
| `IRAK4` | 3 | `Myd88, IRAKM, IRAK1` | `none` | None | Binding/state components are used exactly as shown in the rule inventory. | Declaration: `IRAK4(Myd88,IRAKM,IRAK1)` |
| `IRAKM` | 1 | `IRAK4` | `none` | None | Binding/state components are used exactly as shown in the rule inventory. | Declaration: `IRAKM(IRAK4)` |
| `RP1` | 4 | `TRIF, TRAF6, TAK1, p38` | `none` | None | Binding/state components are used exactly as shown in the rule inventory. | Declaration: `RP1(TRIF,TRAF6,TAK1,p38)` |
| `TRAF6` | 8 | `IRAK1, TRIF, RP1, TAK1, TRAF4, A20, JNK, p38` | `none` | None | Binding/state components are used exactly as shown in the rule inventory. | Declaration: `TRAF6(IRAK1,TRIF,RP1,TAK1,TRAF4,A20,JNK,p38)` |
| `A20` | 1 | `TRAF6` | `none` | None | Binding/state components are used exactly as shown in the rule inventory. | Declaration: `A20(TRAF6)` |
| `MyD88` | 4 | `MAL, IRAK1, IRAK4, MyD88s` | `none` | None | Binding/state components are used exactly as shown in the rule inventory. | Declaration: `MyD88(MAL,IRAK1,IRAK4,MyD88s)` |
| `MyD88s` | 2 | `MyD88, IRAK1` | `none` | None | Binding/state components are used exactly as shown in the rule inventory. | Declaration: `MyD88s(MyD88,IRAK1)` |
| `MAL` | 3 | `TLR4, MyD88, SOCS1` | `none` | None | Binding/state components are used exactly as shown in the rule inventory. | Declaration: `MAL(TLR4,MyD88,SOCS1)` |
| `LPS` | 4 | `MD2, TLR4, CD14, LPS` | `none` | None | Binding/state components are used exactly as shown in the rule inventory. | Declaration: `LPS(MD2,TLR4,CD14,LPS)` |
| `TAK1` | 2 | `TRAF6, Activation` | `Activation: No,Yes` | None | Binding/state components are used exactly as shown in the rule inventory. | Declaration: `TAK1(TRAF6,Activation~No~Yes)` |
| `Ikk_Complex` | 1 | `Activation` | `Activation: No,Yes` | None | Binding/state components are used exactly as shown in the rule inventory. | Declaration: `Ikk_Complex(Activation~No~Yes)` |
| `IkB` | 4 | `Phos, p65, p50, Degrade` | `Phos: No,Yes; Degrade: No,Yes` | None | Binding/state components are used exactly as shown in the rule inventory. | Declaration: `IkB(Phos~No~Yes,p65,p50,Degrade~No~Yes)` |
| `Proteasome26s` | 1 | `IkB` | `none` | None | Binding/state components are used exactly as shown in the rule inventory. | Declaration: `Proteasome26s(IkB)` |
| `TNF` | 1 | `TNFr` | `none` | None | Binding/state components are used exactly as shown in the rule inventory. | Declaration: `TNF(TNFr)` |
| `TNFmRNA` | 1 | `Translation` | `Translation: On,Off` | None | Binding/state components are used exactly as shown in the rule inventory. | Declaration: `TNFmRNA(Translation~On~Off)` |
| `A20mRNA` | 1 | `Translation` | `Translation: On,Off` | None | Binding/state components are used exactly as shown in the rule inventory. | Declaration: `A20mRNA(Translation~On~Off)` |
| `iNOSmRNA` | 1 | `Translation` | `Translation: On,Off` | None | Binding/state components are used exactly as shown in the rule inventory. | Declaration: `iNOSmRNA(Translation~On~Off)` |
| `IkBmRNA` | 1 | `Translation` | `Translation: On,Off` | None | Binding/state components are used exactly as shown in the rule inventory. | Declaration: `IkBmRNA(Translation~On~Off)` |
| `DNA` | 7 | `A20, TNF, iNOS, IL10, IkB, c, c` | `none` | None | Binding/state components are used exactly as shown in the rule inventory. | Declaration: `DNA(A20,TNF,iNOS,IL10,IkB,c,c)` |
| `Trash` | 1 | `c` | `none` | None | Binding/state components are used exactly as shown in the rule inventory. | Declaration: `Trash(c)` |
| `Administer` | 1 | `c` | `none` | None | Binding/state components are used exactly as shown in the rule inventory. | Declaration: `Administer(c)` |
| `NFkB` | 3 | `Transcription, Activation, Location` | `Transcription: No,Yes; Activation: No,Yes; Location: Cytoplasm,Nucleus` | None | Binding/state components are used exactly as shown in the rule inventory. | Declaration: `NFkB(Transcription~No~Yes,Activation~No~Yes,Location~Cytoplasm~Nucleus)` |

## 5. Compartments, anchors, initial species, and setup

No BNGL compartments or anchors are declared. Initial patterns and amounts are exhaustive below:

- `CD14: CD14(TLR4,MD2,LPS) CD14_Init`
- `MD2: MD2(CD14,TLR4,LPS) MD2_Init`
- `TLR4: TLR4(MAL,TRAM,TLR4,CD14,MD2,LPS) TLR_Init`
- `TRAM: TRAM(TLR4,TRIF) TRAM_Init`
- `MAL: MAL(TLR4,MyD88,SOCS1) MAL_Init`
- `TRIF: TRIF(TRAM,TRAF6,RIP1,SARM,TRAF4) TRIF_Init`
- `MyD88: MyD88(MAL,IRAK1,IRAK4,MyD88s) MyD88_Init`
- `RP1: RP1(TRIF,TRAF6,TAK1,p38) RP1_Init`
- `IRAK1: IRAK1(IRAK4,MyD88,Tollip,TRAF6) IRAK1_Init`
- `IRAK4: IRAK4(Myd88,IRAKM,IRAK1) IRAK4_Init`
- `TRAF6: TRAF6(IRAK1,TRIF,RP1,TAK1,TRAF4,A20,JNK,p38) TRAF6_Init`
- `TAK1: TAK1(TRAF6,Activation~No) TAK1_Init`
- `Ikk_Complex: Ikk_Complex(Activation~No) Ikk_Complex_Init`
- `Proteasome23: Proteasome26s(IkB) Proteasome23_Init`
- `IkB: IkB(Phos~No,p65,p50,Degrade~No) IkB_Init`
- `DNA: DNA(A20,TNF,iNOS,IL10,IkB,c,c) DNA`
- `LPS: LPS(MD2,TLR4,CD14,LPS) LPS_Init`
- `A20: A20(TRAF6) A20_Preconditioned`
- `NFkB_Inactive_Cytoplasm: NFkB(Transcription~No,Activation~No,Location~Cytoplasm) NFkB_Inactive_Cytoplasm`

## 6. Complete reaction-rule inventory

**Rule-family orientation.** The family/context column preserves the nearest active BNGL comment; the implementation column preserves every molecule, site, state, bond, direction, and rate expression. Thus repeated families remain one row per concrete rule rather than being collapsed.

| # | Family / technical meaning | Direction | Exact site-level implementation and rate law |
| ---: | --- | --- | --- |
| 1 | LPS MD2 | Reversible | `LPS_MD2: LPS(MD2,TLR4,CD14,LPS)+MD2(CD14,TLR4,LPS)<->LPS(MD2!0,TLR4,CD14,LPS).MD2(CD14,TLR4,LPS!0) LPS_MD2_Bind,LPS_MD2_Unbind` |
| 2 | LPS MD2 CD14 | Reversible | `LPS_MD2_CD14: LPS(MD2!0,TLR4,CD14,LPS).MD2(CD14,TLR4,LPS!0)+CD14(TLR4,MD2,LPS)<->LPS(MD2!0,TLR4,CD14!1,LPS).MD2(CD14,TLR4,LPS!0).CD14(TLR4,MD2,LPS!1) LPS_CD14_Bind,LPS_CD14_Unbind` |
| 3 | LPS MD2 CD14 TLR4 | Reversible | `LPS_MD2_CD14_TLR4: LPS(MD2!0,TLR4,CD14!1,LPS).MD2(CD14,TLR4,LPS!0).CD14(TLR4,MD2,LPS!1) + TLR4(MAL,TRAM,TLR4,CD14,MD2,LPS) <-> LPS(MD2!0,TLR4!2,CD14!1,LPS).MD2(CD14!3,TLR4!4,LPS!0).CD14(TLR4!5,MD2!3,LPS!1).TLR4(MAL,TRAM,TLR4,CD14!5,MD2!4,LPS!2) LPS_TLR4_Bind,LPS_TLR4_Unbind` |
| 4 | TLR4 Dimerization | Reversible | `TLR4_Dimerization: TLR4(TLR4,CD14!+,LPS!+,MD2!+)+TLR4(TLR4,CD14!+,MD2!+,LPS!+)<->TLR4(TLR4!0,CD14!+,LPS!+,MD2!+).TLR4(TLR4!0,CD14!+,LPS!+,MD2!+) TLR4_Complex_Dimer_Bind,TLR4_Complex_Dimer_Unbind` |
| 5 | TLR4 TRAM | Reversible | `TLR4_TRAM: TLR4(TLR4!+,CD14!+,LPS!+,MD2!+,TRAM,MAL)+TRAM(TLR4,TRIF)<->TRAM(TLR4!0,TRIF).TLR4(TLR4!+,CD14!+,LPS!+,MD2!+,TRAM!0,MAL) TLR4_TRAM_Bind,TLR4_TRAM_Unbind` |
| 6 | TLR4TRAM TRIF | Reversible | `TLR4TRAM_TRIF: TRAM(TLR4!0,TRIF).TLR4(TLR4!+,CD14!+,LPS!+,MD2!+,TRAM!0,MAL)+TRIF(TRAM,TRAF6!+,RIP1!+,TRAF4,SARM)<->TRAM(TLR4!0,TRIF!1).TLR4(TLR4!+,CD14!+,LPS!+,MD2!+,TRAM!0,MAL).TRIF(TRAM!1,TRAF6!+,RIP1!+,TRAF4,SARM) TLR4TRAM_TRIF_Bind,TLR4TRAM_TRIF_Unbind` |
| 7 | TLR4TRAMTRIFTRAF6 TAK1 | One-way | `TLR4TRAMTRIFTRAF6_TAK1: TRAM(TLR4!0,TRIF!1).TLR4(TLR4!+,CD14!+,LPS!+,MD2!+,TRAM!0,MAL).TRIF(TRAM!1,TRAF6!+,RIP1!+,TRAF4,SARM)+TAK1(TRAF6,Activation~No)->TRAM(TLR4!0,TRIF!1).TLR4(TLR4!+,CD14!+,LPS!+,MD2!+,TRAM!0,MAL).TRIF(TRAM!1,TRAF6!+,RIP1!+,TRAF4,SARM)+TAK1(TRAF6,Activation~Yes) TRAF6TRIF_TAK1_Activate` |
| 8 | MyD88 IRAK4 | Reversible | `MyD88_IRAK4: MyD88(MAL,IRAK1,IRAK4,MyD88s)+IRAK4(Myd88,IRAKM,IRAK1)<->MyD88(MAL,IRAK1,IRAK4!0,MyD88s).IRAK4(Myd88!0,IRAKM,IRAK1) MyD88_IRAK4_Bind,MyD88_IRAK4_Unbind` |
| 9 | MyD88 IRAK1 | Reversible | `MyD88_IRAK1: MyD88(MAL,IRAK1,IRAK4!0,MyD88s).IRAK4(Myd88!0,IRAKM,IRAK1)+IRAK1(IRAK4,MyD88,Tollip,TRAF6)<->IRAK1(IRAK4,MyD88!0,Tollip,TRAF6).MyD88(MAL,IRAK1!0,IRAK4!1,MyD88s).IRAK4(Myd88!1,IRAKM,IRAK1) MyD88_IRAK1_Bind,MyD88_IRAK1_Unbind` |
| 10 | TNF Translation | One-way | `TNF_Translation: TNFmRNA(Translation~On)->TNFmRNA(Translation~Off)+TNF(TNFr) TNF_Translation_Execute` |
| 11 | A20 Translation | One-way | `A20_Translation: A20mRNA(Translation~On)->A20mRNA(Translation~Off)+A20(TRAF6) A20_Translation_Execute` |
| 12 | TAK1 Degrade | One-way | `TAK1_Degrade: TAK1(TRAF6,Activation~Yes)->Trash(c) TAK1_Degradation` |
| 13 | TLR4 MAL | Reversible | `TLR4_MAL: TLR4(TLR4!+,CD14!+,LPS!+,MD2!+,TRAM,MAL)+MAL(TLR4,MyD88,SOCS1)<->TLR4(TLR4!+,CD14!+,LPS!+,MD2!+,TRAM,MAL!0).MAL(SOCS1,TLR4!0,MyD88) TLR4_MAL_Bind,TLR4_MAL_Unbind` |
| 14 | TLR4MAL MyD88 | Reversible | `TLR4MAL_MyD88: TLR4(TLR4!+,CD14!+,LPS!+,MD2!+,TRAM,MAL!0).MAL(TLR4!0,MyD88,SOCS1) + IRAK1(IRAK4,MyD88!2,Tollip,TRAF6).MyD88(MAL,IRAK1!2,IRAK4!1,MyD88s).IRAK4(Myd88!1,IRAKM,IRAK1) <-> TLR4(TLR4!+,CD14!+,LPS!+,MD2!+,TRAM,MAL!0).MAL(TLR4!0,MyD88!4,SOCS1).IRAK1(IRAK4,MyD88!2,Tollip,TRAF6).MyD88(MAL!4,IRAK1!2,IRAK4!3,MyD88s).IRAK4(Myd88!3,IRAKM,IRAK1) TLR4MAL_MyD88_Bind,TLR4MAL_MyD88_Unbind` |
| 15 | MyD88IRAK1 TRAF6 | Reversible | `MyD88IRAK1_TRAF6: TRAF6(IRAK1,TRIF,RP1,TRAF4,A20,JNK,p38,TAK1)+TLR4(TLR4!+,CD14!+,LPS!+,MD2!+,TRAM,MAL!0).MAL(TLR4!0,MyD88!1,SOCS1).IRAK1(IRAK4,MyD88!2,Tollip,TRAF6).MyD88(MAL!1,IRAK1!2,IRAK4!3,MyD88s).IRAK4(Myd88!3,IRAKM,IRAK1)<->TRAF6(IRAK1!4,TRIF,RP1,TRAF4,A20,JNK,p38,TAK1).TLR4(TLR4!+,CD14!+,LPS!+,MD2!+,TRAM,MAL!0).MAL(TLR4!0,MyD88!1,SOCS1).IRAK1(IRAK4,MyD88!2,Tollip,TRAF6!4).MyD88(MAL!1,IRAK1!2,IRAK4!3,MyD88s).IRAK4(Myd88!3,IRAKM,IRAK1) MyD88IRAK1_TRAF6_Bind,MyD88IRAK1_TRAF6_B_Unbind` |
| 16 | A20 MyD88IRAK1TRAF6 | One-way | `A20_MyD88IRAK1TRAF6: TRAF6(IRAK1!0,TRIF,RP1,TRAF4,A20,JNK,p38,TAK1).TLR4(TLR4!+,CD14!+,LPS!+,MD2!+,TRAM,MAL!1).MAL(TLR4!1,MyD88!2,SOCS1).IRAK1(IRAK4,MyD88!3,Tollip,TRAF6!0).MyD88(MAL!2,IRAK1!3,IRAK4!4,MyD88s).IRAK4(Myd88!4,IRAKM,IRAK1)+A20(TRAF6)->TRAF6(IRAK1,TRIF,RP1,TAK1,TRAF4,A20,JNK,p38)+TLR4(TLR4!+,CD14!+,LPS!+,MD2!+,TRAM,MAL!1).MAL(TLR4!1,MyD88!2,SOCS1).IRAK1(IRAK4,MyD88!3,Tollip,TRAF6).MyD88(MAL!2,IRAK1!3,IRAK4!4,MyD88s).IRAK4(Myd88!4,IRAKM,IRAK1)+A20(TRAF6) A20_MyD88IRAK1TRAF6_Degrade` |
| 17 | MyD88IRAK1TRAF6 TAK1 | One-way | `MyD88IRAK1TRAF6_TAK1: TRAF6(IRAK1!0,TRIF,RP1,TRAF4,A20,JNK,p38,TAK1).TLR4(TLR4!+,CD14!+,LPS!+,MD2!+,TRAM,MAL!1).MAL(TLR4!1,MyD88!2,SOCS1).IRAK1(IRAK4,MyD88!3,Tollip,TRAF6!0).MyD88(MAL!2,IRAK1!3,IRAK4!4,MyD88s).IRAK4(Myd88!4,IRAKM,IRAK1)+TAK1(TRAF6,Activation~No)->TRAF6(IRAK1!0,TRIF,RP1,TRAF4,A20,JNK,p38,TAK1).TLR4(TLR4!+,CD14!+,LPS!+,MD2!+,TRAM,MAL!1).MAL(TLR4!1,MyD88!2,SOCS1).IRAK1(IRAK4,MyD88!3,Tollip,TRAF6!0).MyD88(MAL!2,IRAK1!3,IRAK4!4,MyD88s).IRAK4(Myd88!4,IRAKM,IRAK1)+TAK1(TRAF6,Activation~Yes) MyD88IRAK1TRAF6_TAK1_Activate` |
| 18 | IkB Translation | One-way | `IkB_Translation: IkBmRNA(Translation~On)->IkBmRNA(Translation~Off)+IkB(Phos~No,p65,p50,Degrade~No) IkB_Translation_Execute` |
| 19 | TRIF RP1 | Reversible | `TRIF_RP1: TRIF(TRAM,TRAF6,RIP1,TRAF4,SARM)+RP1(TRIF,TRAF6,TAK1,p38)<->RP1(TRIF!0,TRAF6,TAK1,p38).TRIF(TRAM,TRAF6,RIP1!0,TRAF4,SARM) RP1_TRIF_Bind,RP1_TRIF_Unbind` |
| 20 | TRIF TRAF6 | Reversible | `TRIF_TRAF6: RP1(TRIF!0,TRAF6,TAK1,p38).TRIF(TRAM,TRAF6,RIP1!0,TRAF4,SARM)+TRAF6(IRAK1,TRIF,RP1,TAK1,TRAF4,A20,JNK,p38)<->RP1(TRIF!0,TRAF6!1,TAK1,p38).TRIF(TRAM,TRAF6!2,RIP1!0,TRAF4,SARM).TRAF6(IRAK1,TRIF!2,RP1!1,TAK1,TRAF4,A20,JNK,p38) TRIF_TRAF6_Bind,TRIF_TRAF6_Unbind` |
| 21 | A20 IkkAct Deactivate | One-way | `A20_IkkAct_Deactivate: A20(TRAF6)+Ikk_Complex(Activation~Yes)->A20(TRAF6)+Ikk_Complex(Activation~No) A20_IkkAct_Deactivate` |
| 22 | A20 TRAF6TRIFRP1 Degrade | One-way | `A20_TRAF6TRIFRP1_Degrade: A20(TRAF6)+RP1(TRIF!0,TRAF6!1,TAK1,p38).TRIF(TRAM,TRAF6!2,RIP1!0,TRAF4,SARM).TRAF6(IRAK1,TRIF!2,RP1!1,TAK1,TRAF4,A20,JNK,p38)->TRAF6(IRAK1,TRIF,RP1,TAK1,TRAF4,A20,JNK,p38)+RP1(TRIF,TRAF6,TAK1,p38)+TRIF(TRAM,TRAF6,RIP1,TRAF4,SARM)+A20(TRAF6) A20_TRAF6TRIFRP1_Degrade` |
| 23 | Ikk complex IkB Phos | One-way | `Ikk_complex_IkB_Phos: Ikk_Complex(Activation~Yes)+NFkB(Transcription~No,Activation~No!0!1,Location~Cytoplasm).IkB(Phos~No,p65!0,p50!1,Degrade~No)->Ikk_Complex(Activation~Yes)+NFkB(Transcription~No,Activation~No!0!1,Location~Cytoplasm).IkB(p65!0,p50!1,Degrade~No,Phos~Yes) Ikk_complex_IkB_Phos` |
| 24 | NFkB Translocation Nucleus | Reversible | `NFkB_Translocation_Nucleus: NFkB(Transcription~No,Activation~Yes,Location~Cytoplasm)<->NFkB(Transcription~No,Activation~Yes,Location~Nucleus) NFkB_Translocation_Nucleus,NFkB_Translocation_Nucleus` |
| 25 | NFkB DNA A20 | Reversible | `NFkB_DNA_A20: NFkB(Transcription~No,Activation~Yes,Location~Nucleus)+DNA(A20)<->DNA(A20!0).NFkB(Transcription~Yes!0,Activation~Yes,Location~Nucleus) NFkB_DNA_A20_Bind,NFkB_DNA_A20_Unbind` |
| 26 | IkB DegradeNFkBA20 | One-way | `IkB_DegradeNFkBA20: DNA(A20!0).NFkB(Transcription~Yes!0,Activation~Yes,Location~Nucleus)+IkB(Phos~No,p65,p50,Degrade~No)->DNA(A20)+NFkB(Transcription~No,Activation~No!0!1,Location~Cytoplasm).IkB(Phos~No,p65!0,p50!1,Degrade~No) IkB_DegradeNFkB` |
| 27 | NFkB DNA TNF | Reversible | `NFkB_DNA_TNF: NFkB(Transcription~No,Activation~Yes,Location~Nucleus)+DNA(TNF)<->DNA(TNF!0).NFkB(Transcription~Yes!0,Activation~Yes,Location~Nucleus) NFkB_DNA_TNF_Bind,NFkB_DNA_TNF_Unbind` |
| 28 | NFkB DNA IkB | Reversible | `NFkB_DNA_IkB: NFkB(Transcription~No,Activation~Yes,Location~Nucleus)+DNA(IkB)<->DNA(IkB!0).NFkB(Transcription~Yes!0,Activation~Yes,Location~Nucleus) NFkB_DNA_IkB_Bind,NFkB_DNA_IkB_Unbind` |
| 29 | IkB Proteasome23 Degrade | One-way | `IkB_Proteasome23_Degrade: Proteasome26s(IkB)+NFkB(Transcription~No,Activation~No!0!1,Location~Cytoplasm).IkB(Phos~Yes,p65!0,p50!1,Degrade~No)->IkB(Phos~Yes,p65,p50,Degrade~Yes!0).Proteasome26s(IkB!0)+NFkB(Transcription~No,Activation~Yes,Location~Cytoplasm) IkB_Proteasome23_Degrade` |
| 30 | NFkB_IkB_Bind: NFkB(Location~Cytoplasm,Activation~*)+IkB(Phos~No,p65,p50,Degrade~No)<->NFkB(Activation~*!0!1,Location~Cytoplasm).IkB(Phos~No,p65!0,p50!1,Degrade~No) NFkB_IkB_Bind,NFkB_IkB_Unbind | Reversible | `NFkB_IkB_Bind: NFkB(Location~Cytoplasm,Activation)+IkB(Phos~No,p65,p50,Degrade~No)<->NFkB(Activation!0!1,Location~Cytoplasm).IkB(Phos~No,p65!0,p50!1,Degrade~No) NFkB_IkB_Bind,NFkB_IkB_Unbind` |
| 31 | NFkB_IkB_Bind: NFkB(Location~Cytoplasm,Activation~*)+IkB(Phos~No,p65,p50,Degrade~No)<->NFkB(Activation~*!0!1,Location~Cytoplasm).IkB(Phos~No,p65!0,p50!1,Degrade~No) NFkB_IkB_Bind,NFkB_IkB_Unbind | One-way | `Proteasome23_Release: IkB(Degrade~Yes!0).Proteasome26s(IkB!0)->IkB(Degrade~Yes)+Proteasome26s(IkB) IkB_Proteasome23_Degrade` |
| 32 | NFkB_IkB_Bind: NFkB(Location~Cytoplasm,Activation~*)+IkB(Phos~No,p65,p50,Degrade~No)<->NFkB(Activation~*!0!1,Location~Cytoplasm).IkB(Phos~No,p65!0,p50!1,Degrade~No) NFkB_IkB_Bind,NFkB_IkB_Unbind | One-way | `IkB_Transcription_Execute: DNA(IkB!0).NFkB(Transcription~Yes!0,Activation~Yes,Location~Nucleus)->IkBmRNA(Translation~On)+DNA(IkB!0).NFkB(Transcription~Yes!0,Activation~Yes,Location~Nucleus) IkB_Transcription_Execute` |
| 33 | NFkB_IkB_Bind: NFkB(Location~Cytoplasm,Activation~*)+IkB(Phos~No,p65,p50,Degrade~No)<->NFkB(Activation~*!0!1,Location~Cytoplasm).IkB(Phos~No,p65!0,p50!1,Degrade~No) NFkB_IkB_Bind,NFkB_IkB_Unbind | One-way | `A20_Transcription_Execute: DNA(A20!0).NFkB(Transcription~Yes!0,Activation~Yes,Location~Nucleus)->A20mRNA(Translation~On)+DNA(A20!0).NFkB(Transcription~Yes!0,Activation~Yes,Location~Nucleus) A20_Transcription_Execute` |
| 34 | NFkB_IkB_Bind: NFkB(Location~Cytoplasm,Activation~*)+IkB(Phos~No,p65,p50,Degrade~No)<->NFkB(Activation~*!0!1,Location~Cytoplasm).IkB(Phos~No,p65!0,p50!1,Degrade~No) NFkB_IkB_Bind,NFkB_IkB_Unbind | One-way | `TNF_Transcription_Execute: DNA(TNF!0).NFkB(Transcription~Yes!0,Activation~Yes,Location~Nucleus)->TNFmRNA(Translation~On)+DNA(TNF!0).NFkB(Transcription~Yes!0,Activation~Yes,Location~Nucleus) TNF_Transcription_Execute` |
| 35 | NFkB_IkB_Bind: NFkB(Location~Cytoplasm,Activation~*)+IkB(Phos~No,p65,p50,Degrade~No)<->NFkB(Activation~*!0!1,Location~Cytoplasm).IkB(Phos~No,p65!0,p50!1,Degrade~No) NFkB_IkB_Bind,NFkB_IkB_Unbind | One-way | `TAK1_Deactivation: TAK1(TRAF6,Activation~Yes)->TAK1(TRAF6,Activation~No) TAK1_Deactivation` |
| 36 | NFkB_IkB_Bind: NFkB(Location~Cytoplasm,Activation~*)+IkB(Phos~No,p65,p50,Degrade~No)<->NFkB(Activation~*!0!1,Location~Cytoplasm).IkB(Phos~No,p65!0,p50!1,Degrade~No) NFkB_IkB_Bind,NFkB_IkB_Unbind | One-way | `Ikk_Deactivation: Ikk_Complex(Activation~Yes)->Ikk_Complex(Activation~No) Ikk_Deactivation` |
| 37 | NFkB_IkB_Bind: NFkB(Location~Cytoplasm,Activation~*)+IkB(Phos~No,p65,p50,Degrade~No)<->NFkB(Activation~*!0!1,Location~Cytoplasm).IkB(Phos~No,p65!0,p50!1,Degrade~No) NFkB_IkB_Bind,NFkB_IkB_Unbind | One-way | `TAK1_Ikk_Complex_Activate: TAK1(TRAF6,Activation~Yes)+Ikk_Complex(Activation~No)->TAK1(TRAF6,Activation~Yes)+Ikk_Complex(Activation~Yes) TAK1_Ikk_Complex_Activate` |
| 38 | NFkB_IkB_Bind: NFkB(Location~Cytoplasm,Activation~*)+IkB(Phos~No,p65,p50,Degrade~No)<->NFkB(Activation~*!0!1,Location~Cytoplasm).IkB(Phos~No,p65!0,p50!1,Degrade~No) NFkB_IkB_Bind,NFkB_IkB_Unbind | One-way | `TNF_Degrade: TNF(TNFr)->Trash(c) TNF_Degrade` |
| 39 | NFkB_IkB_Bind: NFkB(Location~Cytoplasm,Activation~*)+IkB(Phos~No,p65,p50,Degrade~No)<->NFkB(Activation~*!0!1,Location~Cytoplasm).IkB(Phos~No,p65!0,p50!1,Degrade~No) NFkB_IkB_Bind,NFkB_IkB_Unbind | One-way | `A20_Degrade: A20(TRAF6)->Trash(c) A20_Degrade` |
| 40 | NFkB_IkB_Bind: NFkB(Location~Cytoplasm,Activation~*)+IkB(Phos~No,p65,p50,Degrade~No)<->NFkB(Activation~*!0!1,Location~Cytoplasm).IkB(Phos~No,p65!0,p50!1,Degrade~No) NFkB_IkB_Bind,NFkB_IkB_Unbind | One-way | `IkB_DegradeNFkBDNAIkB: DNA(IkB!0).NFkB(Transcription~Yes!0,Activation~Yes,Location~Nucleus)+IkB(Phos~No,p65,p50,Degrade~No)->DNA(IkB)+IkB(Phos~No,p65!0,p50!1,Degrade~No).NFkB(Transcription~No,Activation~No!0!1,Location~Cytoplasm) IkB_DegradeNFkB` |
| 41 | NFkB_IkB_Bind: NFkB(Location~Cytoplasm,Activation~*)+IkB(Phos~No,p65,p50,Degrade~No)<->NFkB(Activation~*!0!1,Location~Cytoplasm).IkB(Phos~No,p65!0,p50!1,Degrade~No) NFkB_IkB_Bind,NFkB_IkB_Unbind | One-way | `IkB_DegradeNFkBDNA_TNF: DNA(TNF!0).NFkB(Transcription~Yes!0,Activation~Yes,Location~Nucleus)+IkB(Phos~No,p65,p50,Degrade~No)->DNA(TNF)+IkB(Phos~No,p65!0,p50!1,Degrade~No).NFkB(Transcription~No,Activation~No!0!1,Location~Cytoplasm) IkB_DegradeNFkB` |

## 7. Observables and technical readouts

Every active observable is retained below. `Molecules` counts pattern matches; `Species` counts matching complete species.

- `Molecules TNF TNF(TNFr)`
- `Molecules Activated_TAK1 TAK1(TRAF6,Activation~Yes)`
- `Molecules Activated_Ikk_complex Ikk_Complex(Activation~Yes)`
- `Molecules A20 A20(TRAF6)`
- `Molecules NFkB_Active_Cyto NFkB(Transcription~No,Activation~Yes,Location~Cytoplasm)`
- `Molecules NFkB_Active_Nucleus NFkB(Transcription~No,Activation~Yes,Location~Nucleus)`
- `Molecules IkB_Degraded IkB(Degrade~Yes)`
- `Molecules IkB_active IkB(Degrade~No)`
- `Molecules NFkB_Inactive NFkB(Activation!+)`
- `Molecules NonBoundNonPhos_IkB IkB(Phos~No,p65,p50,Degrade~No)`
- `Molecules IkBmRNA_Off IkBmRNA(Translation~Off)`
- `Molecules NFkB_DNA_IkB DNA(IkB!0).NFkB(Transcription~Yes!0,Activation~Yes,Location~Nucleus)`
- `Molecules Phos_IkB_NFkB NFkB(Transcription~No,Activation~No!0!1,Location~Cytoplasm).IkB(Phos~Yes,p65!0,p50!1,Degrade~No)`
- `Molecules IkB_Prot26s IkB(Phos~Yes,p65,p50,Degrade~Yes!0).Proteasome26s(IkB!0)`
- `Molecules Unbound_Cyto_NFkB NFkB(Location~Cytoplasm,Activation)`
- `Molecules Inactive_Cyto_NFkB NFkB(Activation!0!1,Location~Cytoplasm).IkB(Phos~No,p65!0,p50!1,Degrade~No)`
- `Molecules TNFmRNA_Off TNFmRNA(Translation~Off)`
- `Molecules TNF_NFkB_DNA DNA(TNF!0).NFkB(Transcription~Yes!0,Activation~Yes,Location~Nucleus)`
- `Molecules A20_NFkB_DNA DNA(A20!0).NFkB(Transcription~Yes!0,Activation~Yes,Location~Nucleus)`

## 8. Actions and simulation workflow

- `generate_network({overwrite=>1});`
- `setConcentration("LPS(MD2,TLR4,CD14,LPS)",0);`
- `simulate_ode({suffix=>"equil",t_end=>50000,n_steps=>10,atol=>1e-12,rtol=>1e-12,sparse=>1,steady_state=>1});`
- `setConcentration("LPS(MD2,TLR4,CD14,LPS)","LPS_Init");`
- `writeSBML();`
- `writeMfile();`
- `simulate_ode({t_end=>100000,n_steps=>500,atol=>1e-12,rtol=>1e-12,sparse=>0});`

## 9. Technical caveats and ambiguities

The network is nonspatial despite biological membrane/cytosolic/nuclear language. The equilibration explicitly removes LPS before restoring it. Local abbreviations and lumped species should not be assigned finer biochemical identities than their declarations support.
