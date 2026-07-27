# Detailed Model Explanation: An 2009 TLR4 signaling model

## 1. Model identity and scope

`An_2009` models how lipopolysaccharide (LPS) recognition by Toll-like receptor 4 (TLR4) drives adaptor signaling, NF-κB activation, inflammatory outputs, and feedback. Sources: `Published/An2009/An_2009.bngl` and `Published/An2009/metadata.yaml`.

## 2. BNGL block inventory

The file contains 97 active parameter declarations, 31 molecule types, 19 initial-species declarations, 0 functions, 41 concrete reaction rules, 19 observable declarations, and 7 execution commands. It declares no compartments or anchors.

## 3. Parameters, functions, and rate laws

Rate names encode their pathway edge and direction: receptor/adaptor association pairs end in `Bind`/`Unbind`, activation steps end in `Activate`, and feedback or turnover steps identify their target. The exhaustive one-per-bullet list follows receptor assembly, TRIF/MyD88 branches, TAK1–IKK–NF-κB signaling, translation, and inhibition.

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

**Rule-family orientation.** Rules follow LPS receptor assembly, TRAM/TRIF and MAL/MyD88 adaptor routes, TAK1/IKK/NF-κB activation, inflammatory translation, and inhibitory feedback. Named BNGL labels are rendered as readable mechanisms rather than copied patterns.

| # | Direction | Required molecules/sites | Net bond, state, or species edit | Rate/expression | Functional interpretation |
| ---: | --- | --- | --- | --- | --- |
| 1 | Reversible | `LPS` (`MD2`, `TLR4`, `CD14`, `LPS`); `MD2` (`CD14`, `TLR4`, `LPS`) | forms the explicitly site-matched bond(s) | LPS_MD2_Bind,LPS_MD2_Unbind | LPS MD2. |
| 2 | Reversible | `LPS` (`MD2`, `TLR4`, `CD14`, `LPS`); `MD2` (`CD14`, `TLR4`, `LPS`); `CD14` (`TLR4`, `MD2`, `LPS`) | forms the explicitly site-matched bond(s) | LPS_CD14_Bind,LPS_CD14_Unbind | LPS MD2 CD14. |
| 3 | Reversible | `LPS` (`MD2`, `TLR4`, `CD14`, `LPS`); `MD2` (`CD14`, `TLR4`, `LPS`); `CD14` (`TLR4`, `MD2`, `LPS`); `TLR4` (`MAL`, `TRAM`, `TLR4`, `CD14`, `MD2`, `LPS`) | forms the explicitly site-matched bond(s) | LPS_TLR4_Bind,LPS_TLR4_Unbind | LPS MD2 CD14 TLR4. |
| 4 | Reversible | `TLR4` (`TLR4`, `CD14`, `LPS`, `MD2`); `TLR4` (`TLR4`, `CD14`, `MD2`, `LPS`) | forms the explicitly site-matched bond(s) | TLR4_Complex_Dimer_Bind,TLR4_Complex_Dimer_Unbind | TLR4 Dimerization. |
| 5 | Reversible | `TLR4` (`TLR4`, `CD14`, `LPS`, `MD2`, `TRAM`, `MAL`); `TRAM` (`TLR4`, `TRIF`) | forms the explicitly site-matched bond(s) | TLR4_TRAM_Bind,TLR4_TRAM_Unbind | TLR4 TRAM. |
| 6 | Reversible | `TRAM` (`TLR4`, `TRIF`); `TLR4` (`TLR4`, `CD14`, `LPS`, `MD2`, `TRAM`, `MAL`); `TRIF` (`TRAM`, `TRAF6`, `RIP1`, `TRAF4`, `SARM`) | forms the explicitly site-matched bond(s) | TLR4TRAM_TRIF_Bind,TLR4TRAM_TRIF_Unbind | TLR4TRAM TRIF. |
| 7 | One-way | `TRAM` (`TLR4`, `TRIF`); `TLR4` (`TLR4`, `CD14`, `LPS`, `MD2`, `TRAM`, `MAL`); `TRIF` (`TRAM`, `TRAF6`, `RIP1`, `TRAF4`, `SARM`); `TAK1` (`TRAF6`, `Activation`) | `TAK1.Activation` No→Yes | TRAF6TRIF_TAK1_Activate | TLR4TRAMTRIFTRAF6 TAK1. |
| 8 | Reversible | `MyD88` (`MAL`, `IRAK1`, `IRAK4`, `MyD88s`); `IRAK4` (`Myd88`, `IRAKM`, `IRAK1`) | forms the explicitly site-matched bond(s) | MyD88_IRAK4_Bind,MyD88_IRAK4_Unbind | MyD88 IRAK4. |
| 9 | Reversible | `MyD88` (`MAL`, `IRAK1`, `IRAK4`, `MyD88s`); `IRAK4` (`Myd88`, `IRAKM`, `IRAK1`); `IRAK1` (`IRAK4`, `MyD88`, `Tollip`, `TRAF6`) | forms the explicitly site-matched bond(s) | MyD88_IRAK1_Bind,MyD88_IRAK1_Unbind | MyD88 IRAK1. |
| 10 | One-way | `TNFmRNA` (`Translation`); `TNF` (`TNFr`) | `TNFmRNA.Translation` On→Off; creates `TNF` | TNF_Translation_Execute | TNF Translation. |
| 11 | One-way | `A20mRNA` (`Translation`); `A20` (`TRAF6`) | `A20mRNA.Translation` On→Off; creates `A20` | A20_Translation_Execute | A20 Translation. |
| 12 | One-way | `TAK1` (`TRAF6`, `Activation`); `Trash` (`c`) | routes the reactant to `Trash`; removes `TAK1` | TAK1_Degradation | TAK1 Degrade. |
| 13 | Reversible | `TLR4` (`TLR4`, `CD14`, `LPS`, `MD2`, `TRAM`, `MAL`); `MAL` (`TLR4`, `MyD88`, `SOCS1`); `MAL` (`SOCS1`, `TLR4`, `MyD88`) | forms the explicitly site-matched bond(s) | TLR4_MAL_Bind,TLR4_MAL_Unbind | TLR4 MAL. |
| 14 | Reversible | `TLR4` (`TLR4`, `CD14`, `LPS`, `MD2`, `TRAM`, `MAL`); `MAL` (`TLR4`, `MyD88`, `SOCS1`); `IRAK1` (`IRAK4`, `MyD88`, `Tollip`, `TRAF6`); `MyD88` (`MAL`, `IRAK1`, `IRAK4`, `MyD88s`); `IRAK4` (`Myd88`, `IRAKM`, `IRAK1`) | forms the explicitly site-matched bond(s) | TLR4MAL_MyD88_Bind,TLR4MAL_MyD88_Unbind | TLR4MAL MyD88. |
| 15 | Reversible | `TRAF6` (`IRAK1`, `TRIF`, `RP1`, `TRAF4`, `A20`, `JNK`, `p38`, `TAK1`); `TLR4` (`TLR4`, `CD14`, `LPS`, `MD2`, `TRAM`, `MAL`); `MAL` (`TLR4`, `MyD88`, `SOCS1`); `IRAK1` (`IRAK4`, `MyD88`, `Tollip`, `TRAF6`); `MyD88` (`MAL`, `IRAK1`, `IRAK4`, `MyD88s`); `IRAK4` (`Myd88`, `IRAKM`, `IRAK1`) | forms the explicitly site-matched bond(s) | MyD88IRAK1_TRAF6_Bind,MyD88IRAK1_TRAF6_B_Unbind | MyD88IRAK1 TRAF6. |
| 16 | One-way | `TRAF6` (`IRAK1`, `TRIF`, `RP1`, `TRAF4`, `A20`, `JNK`, `p38`, `TAK1`); `TLR4` (`TLR4`, `CD14`, `LPS`, `MD2`, `TRAM`, `MAL`); `MAL` (`TLR4`, `MyD88`, `SOCS1`); `IRAK1` (`IRAK4`, `MyD88`, `Tollip`, `TRAF6`); `MyD88` (`MAL`, `IRAK1`, `IRAK4`, `MyD88s`); `IRAK4` (`Myd88`, `IRAKM`, `IRAK1`); `A20` (`TRAF6`); `TRAF6` (`IRAK1`, `TRIF`, `RP1`, `TAK1`, `TRAF4`, `A20`, `JNK`, `p38`) | releases the explicitly site-matched bond(s) | A20_MyD88IRAK1TRAF6_Degrade | A20 MyD88IRAK1TRAF6. |
| 17 | One-way | `TRAF6` (`IRAK1`, `TRIF`, `RP1`, `TRAF4`, `A20`, `JNK`, `p38`, `TAK1`); `TLR4` (`TLR4`, `CD14`, `LPS`, `MD2`, `TRAM`, `MAL`); `MAL` (`TLR4`, `MyD88`, `SOCS1`); `IRAK1` (`IRAK4`, `MyD88`, `Tollip`, `TRAF6`); `MyD88` (`MAL`, `IRAK1`, `IRAK4`, `MyD88s`); `IRAK4` (`Myd88`, `IRAKM`, `IRAK1`); `TAK1` (`TRAF6`, `Activation`) | `TAK1.Activation` No→Yes | MyD88IRAK1TRAF6_TAK1_Activate | MyD88IRAK1TRAF6 TAK1. |
| 18 | One-way | `IkBmRNA` (`Translation`); `IkB` (`Phos`, `p65`, `p50`, `Degrade`) | `IkBmRNA.Translation` On→Off; creates `IkB` | IkB_Translation_Execute | IkB Translation. |
| 19 | Reversible | `TRIF` (`TRAM`, `TRAF6`, `RIP1`, `TRAF4`, `SARM`); `RP1` (`TRIF`, `TRAF6`, `TAK1`, `p38`) | forms the explicitly site-matched bond(s) | RP1_TRIF_Bind,RP1_TRIF_Unbind | TRIF RP1. |
| 20 | Reversible | `RP1` (`TRIF`, `TRAF6`, `TAK1`, `p38`); `TRIF` (`TRAM`, `TRAF6`, `RIP1`, `TRAF4`, `SARM`); `TRAF6` (`IRAK1`, `TRIF`, `RP1`, `TAK1`, `TRAF4`, `A20`, `JNK`, `p38`) | forms the explicitly site-matched bond(s) | TRIF_TRAF6_Bind,TRIF_TRAF6_Unbind | TRIF TRAF6. |
| 21 | One-way | `A20` (`TRAF6`); `Ikk_Complex` (`Activation`) | `Ikk_Complex.Activation` Yes→No | A20_IkkAct_Deactivate | A20 IkkAct Deactivate. |
| 22 | One-way | `A20` (`TRAF6`); `RP1` (`TRIF`, `TRAF6`, `TAK1`, `p38`); `TRIF` (`TRAM`, `TRAF6`, `RIP1`, `TRAF4`, `SARM`); `TRAF6` (`IRAK1`, `TRIF`, `RP1`, `TAK1`, `TRAF4`, `A20`, `JNK`, `p38`) | releases the explicitly site-matched bond(s) | A20_TRAF6TRIFRP1_Degrade | A20 TRAF6TRIFRP1 Degrade. |
| 23 | One-way | `Ikk_Complex` (`Activation`); `NFkB` (`Transcription`, `Activation`, `Location`); `IkB` (`Phos`, `p65`, `p50`, `Degrade`); `IkB` (`p65`, `p50`, `Degrade`, `Phos`) | `IkB.Phos` No→Yes | Ikk_complex_IkB_Phos | Ikk complex IkB Phos. |
| 24 | Reversible | `NFkB` (`Transcription`, `Activation`, `Location`) | `NFkB.Location` Cytoplasm→Nucleus | NFkB_Translocation_Nucleus,NFkB_Translocation_Nucleus | NFkB Translocation Nucleus. |
| 25 | Reversible | `NFkB` (`Transcription`, `Activation`, `Location`); `DNA` (`A20`) | `NFkB.Transcription` No→Yes; forms the explicitly site-matched bond(s) | NFkB_DNA_A20_Bind,NFkB_DNA_A20_Unbind | NFkB DNA A20. |
| 26 | One-way | `DNA` (`A20`); `NFkB` (`Transcription`, `Activation`, `Location`); `IkB` (`Phos`, `p65`, `p50`, `Degrade`) | `NFkB.Transcription` Yes→No; `NFkB.Activation` Yes→No; `NFkB.Location` Nucleus→Cytoplasm; forms the explicitly site-matched bond(s) | IkB_DegradeNFkB | IkB DegradeNFkBA20. |
| 27 | Reversible | `NFkB` (`Transcription`, `Activation`, `Location`); `DNA` (`TNF`) | `NFkB.Transcription` No→Yes; forms the explicitly site-matched bond(s) | NFkB_DNA_TNF_Bind,NFkB_DNA_TNF_Unbind | NFkB DNA TNF. |
| 28 | Reversible | `NFkB` (`Transcription`, `Activation`, `Location`); `DNA` (`IkB`) | `NFkB.Transcription` No→Yes; forms the explicitly site-matched bond(s) | NFkB_DNA_IkB_Bind,NFkB_DNA_IkB_Unbind | NFkB DNA IkB. |
| 29 | One-way | `Proteasome26s` (`IkB`); `NFkB` (`Transcription`, `Activation`, `Location`); `IkB` (`Phos`, `p65`, `p50`, `Degrade`) | `NFkB.Activation` No→Yes; `IkB.Degrade` No→Yes; releases the explicitly site-matched bond(s) | IkB_Proteasome23_Degrade | IkB Proteasome23 Degrade. |
| 30 | Reversible | `NFkB` (`Location`, `Activation`); `IkB` (`Phos`, `p65`, `p50`, `Degrade`); `NFkB` (`Activation`, `Location`) | forms the explicitly site-matched bond(s) | NFkB_IkB_Bind,NFkB_IkB_Unbind | Cytosolic IκB binds both NF-κB subunit interfaces and converts free NF-κB into its inhibited complex. |
| 31 | One-way | `IkB` (`Degrade`); `Proteasome26s` (`IkB`) | releases the explicitly site-matched bond(s) | IkB_Proteasome23_Degrade | Proteasome releases IκB after its degradation flag is set, recycling the proteasome for another substrate. |
| 32 | One-way | `DNA` (`IkB`); `NFkB` (`Transcription`, `Activation`, `Location`); `IkBmRNA` (`Translation`) | creates `IkBmRNA` | IkB_Transcription_Execute | NF-κB bound at the IκB promoter produces translation-ready `IkBmRNA` while remaining promoter-bound. |
| 33 | One-way | `DNA` (`A20`); `NFkB` (`Transcription`, `Activation`, `Location`); `A20mRNA` (`Translation`) | creates `A20mRNA` | A20_Transcription_Execute | NF-κB bound at the A20 promoter produces translation-ready `A20mRNA`, implementing delayed negative feedback. |
| 34 | One-way | `DNA` (`TNF`); `NFkB` (`Transcription`, `Activation`, `Location`); `TNFmRNA` (`Translation`) | creates `TNFmRNA` | TNF_Transcription_Execute | NF-κB bound at the TNF promoter produces translation-ready `TNFmRNA`, closing the positive autocrine loop. |
| 35 | One-way | `TAK1` (`TRAF6`, `Activation`) | `TAK1.Activation` Yes→No | TAK1_Deactivation | Active TAK1 returns to its inactive state without changing its TRAF6-binding capacity. |
| 36 | One-way | `Ikk_Complex` (`Activation`) | `Ikk_Complex.Activation` Yes→No | Ikk_Deactivation | The active IKK complex relaxes to its inactive state, limiting continued IκB phosphorylation. |
| 37 | One-way | `TAK1` (`TRAF6`, `Activation`); `Ikk_Complex` (`Activation`) | `Ikk_Complex.Activation` No→Yes | TAK1_Ikk_Complex_Activate | Active TAK1 catalytically switches IKK from inactive to active and is carried through unchanged. |
| 38 | One-way | `TNF` (`TNFr`); `Trash` (`c`) | routes the reactant to `Trash`; removes `TNF` | TNF_Degrade | TNF is removed into `Trash`, limiting the duration of extracellular/autocrine stimulation. |
| 39 | One-way | `A20` (`TRAF6`); `Trash` (`c`) | routes the reactant to `Trash`; removes `A20` | A20_Degrade | A20 is removed into `Trash`, allowing inhibitory feedback strength to decay. |
| 40 | One-way | `DNA` (`IkB`); `NFkB` (`Transcription`, `Activation`, `Location`); `IkB` (`Phos`, `p65`, `p50`, `Degrade`) | `NFkB.Transcription` Yes→No; `NFkB.Activation` Yes→No; `NFkB.Location` Nucleus→Cytoplasm; forms the explicitly site-matched bond(s) | IkB_DegradeNFkB | New IκB strips NF-κB from the IκB promoter, returns NF-κB to an inactive cytosolic IκB complex, and frees the promoter. |
| 41 | One-way | `DNA` (`TNF`); `NFkB` (`Transcription`, `Activation`, `Location`); `IkB` (`Phos`, `p65`, `p50`, `Degrade`) | `NFkB.Transcription` Yes→No; `NFkB.Activation` Yes→No; `NFkB.Location` Nucleus→Cytoplasm; forms the explicitly site-matched bond(s) | IkB_DegradeNFkB | New IκB strips NF-κB from the TNF promoter, terminates TNF transcription, and exports inhibited NF-κB to cytosol. |

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
