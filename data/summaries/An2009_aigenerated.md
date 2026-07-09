# Model Explanation: An 2009

## 1. One-sentence summary

This model follows Toll-like receptor 4 signaling from LPS/coreceptor engagement through adaptor recruitment, NF-kB activation, and inflammatory gene-output species.

## 2. Biological meaning

This model follows Toll-like receptor 4 signaling from LPS/coreceptor engagement through adaptor recruitment, NF-kB activation, and inflammatory gene-output species. The local model comments and metadata give this context: Molecules NFkB_Inactive NFkB(Activation~*!+) Molecules Unbound_Cyto_NFkB NFkB(Location~Cytoplasm,Activation) Molecules Inactive_Cyto_NFkB NFkB(Activation~*!0!1,Location~Cytoplasm).IkB(Phos~No,p65!0,p50!1,Degrade~No) BEGIN SIMULATION. The explanation below is therefore based on the local BNGL model file `Published/An2009/An_2009.bngl` and metadata file `Published/An2009/metadata.yaml`, not on remote URLs.

## 3. Main molecules, sites, and states

BNGL sites are named contact points or state variables on a molecule. A value after `~` is an internal state, such as phosphorylated/unphosphorylated, active/inactive, localized/nonlocalized, or another model-specific switch. Matching bond labels such as `!1` mean the two marked sites are connected in the same complex; a site without a bond label is free or unspecified.

- `CD14`: CD14. It has binding or interaction sites `TLR4`, `MD2`, `LPS`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `MD2`: MD2. It has binding or interaction sites `CD14`, `TLR4`, `LPS`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `TLR4`: TLR4. It has binding or interaction sites `MAL`, `TRAM`, `TLR4`, `CD14`, `MD2`, `LPS`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `TRAM`: TRAM. It has binding or interaction sites `TLR4`, `TRIF`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `TRIF`: TRIF. It has binding or interaction sites `TRAM`, `TRAF6`, `RIP1`, `TRAF4`, `SARM`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `SARM`: SARM. It has binding or interaction sites `TRIF`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `TRAF4`: TRAF4. It has binding or interaction sites `TRAF6`, `TAK1`, `TRIF`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `IRAK1`: IRAK1. It has binding or interaction sites `IRAK4`, `MyD88`, `Tollip`, `TRAF6`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `Tollip`: Tollip. It has binding or interaction sites `IRAK1`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `IRAK4`: IRAK4. It has binding or interaction sites `Myd88`, `IRAKM`, `IRAK1`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `IRAKM`: IRAKM. It has binding or interaction sites `IRAK4`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `RP1`: RP1. It has binding or interaction sites `TRIF`, `TRAF6`, `TAK1`, `p38`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `TRAF6`: TRAF6. It has binding or interaction sites `IRAK1`, `TRIF`, `RP1`, `TAK1`, `TRAF4`, `A20`, `JNK`, `p38`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `A20`: A20. It has binding or interaction sites `TRAF6`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `MyD88`: MyD88. It has binding or interaction sites `MAL`, `IRAK1`, `IRAK4`, `MyD88s`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `MyD88s`: MyD88s. It has binding or interaction sites `MyD88`, `IRAK1`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `MAL`: MAL. It has binding or interaction sites `TLR4`, `MyD88`, `SOCS1`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `LPS`: LPS. It has binding or interaction sites `MD2`, `TLR4`, `CD14`, `LPS`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `TAK1`: TAK1. It has binding/interaction sites `TRAF6` and regulated state sites `Activation~No~Yes`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `Ikk_Complex`: Ikk_Complex. It has state sites `Activation~No~Yes`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `IkB`: IkB inhibitor. It has binding/interaction sites `p65`, `p50` and regulated state sites `Phos~No~Yes`, `Degrade~No~Yes`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `Proteasome26s`: Proteasome26s. It has binding or interaction sites `IkB`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `TNF`: TNF. It has binding or interaction sites `TNFr`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `TNFmRNA`: TNFmRNA. It has state sites `Translation~On~Off`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `A20mRNA`: A20mRNA. It has state sites `Translation~On~Off`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `iNOSmRNA`: iNOSmRNA. It has state sites `Translation~On~Off`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `IkBmRNA`: IkBmRNA. It has state sites `Translation~On~Off`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `DNA`: DNA. It has binding or interaction sites `A20`, `TNF`, `iNOS`, `IL10`, `IkB`, `c`, `c`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `Trash`: Trash. It has binding or interaction sites `c`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `Administer`: Administer. It has binding or interaction sites `c`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `NFkB`: NF-kB transcription factor. It has state sites `Transcription~No~Yes`, `Activation~No~Yes`, `Location~Cytoplasm~Nucleus`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.

## 4. Initial conditions and model setup

The model starts from these encoded species or starting concentrations/copy numbers. Entries without `!` bond labels start as free molecules; entries with matching labels start as pre-assembled complexes.

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

Important parameters include:

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

Functions and simulation/action commands:

- `generate_network({overwrite=>1});`
- `simulate_ode({suffix=>"equil",t_end=>50000,n_steps=>10,atol=>1e-12,rtol=>1e-12,sparse=>1,steady_state=>1});`
- `writeSBML();`
- `writeMfile();`
- `simulate_ode({t_end=>100000,n_steps=>500,atol=>1e-12,rtol=>1e-12,sparse=>0});`

## 5. Reaction rules in plain English

These rules are the biological mechanism of the model. When a product contains new matching `!` labels, two sites have become bound; when those labels disappear, a complex has separated. For reversible rules, the first listed rate is the forward rate and the second listed rate is the reverse rate.

- **LPS_MD2**: Reversible binding/release. The rule involves `LPS`, `MD2` and produces `LPS`, `MD2`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `LPS_MD2_Bind, LPS_MD2_Unbind`.
- **LPS_MD2_CD14**: Reversible binding/release. The rule involves `CD14`, `LPS`, `MD2` and produces `CD14`, `LPS`, `MD2`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `LPS_CD14_Bind, LPS_CD14_Unbind`.
- **LPS_MD2_CD14_TLR4**: Reversible binding/release. The rule involves `CD14`, `LPS`, `MD2`, `TLR4` and produces `CD14`, `LPS`, `MD2`, `TLR4`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `LPS_TLR4_Bind, LPS_TLR4_Unbind`.
- **TLR4_Dimerization**: Reversible binding/release. The rule involves `TLR4` and produces `TLR4`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `TLR4_Complex_Dimer_Bind, TLR4_Complex_Dimer_Unbind`.
- **TLR4_TRAM**: Reversible binding/release. The rule involves `TLR4`, `TRAM` and produces `TLR4`, `TRAM`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `TLR4_TRAM_Bind, TLR4_TRAM_Unbind`.
- **TLR4TRAM_TRIF**: Reversible binding/release. The rule involves `TLR4`, `TRAM`, `TRIF` and produces `TLR4`, `TRAM`, `TRIF`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `TLR4TRAM_TRIF_Bind, TLR4TRAM_TRIF_Unbind`.
- **TLR4TRAMTRIFTRAF6_TAK1**: State change or catalytic conversion. The rule involves `TAK1`, `TLR4`, `TRAM`, `TRIF` and produces `TAK1`, `TLR4`, `TRAM`, `TRIF`. The encoded molecular change is `TAK1` site `Activation` changes from `No` to `Yes`; site `Activation` changes from `No` to `Yes`. Rate parameter(s): `TRAF6TRIF_TAK1_Activate`.
- **MyD88_IRAK4**: Reversible binding/release. The rule involves `IRAK4`, `MyD88` and produces `IRAK4`, `MyD88`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `MyD88_IRAK4_Bind, MyD88_IRAK4_Unbind`.
- **MyD88_IRAK1**: Reversible binding/release. The rule involves `IRAK1`, `IRAK4`, `MyD88` and produces `IRAK1`, `IRAK4`, `MyD88`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `MyD88_IRAK1_Bind, MyD88_IRAK1_Unbind`.
- **TNF_Translation**: State change or catalytic conversion. The rule involves `TNFmRNA` and produces `TNF`, `TNFmRNA`. The encoded molecular change is `TNFmRNA` site `Translation` changes from `On` to `Off`; site `Translation` changes from `On` to `Off`. Rate parameter(s): `TNF_Translation_Execute`.
- **A20_Translation**: State change or catalytic conversion. The rule involves `A20mRNA` and produces `A20`, `A20mRNA`. The encoded molecular change is `A20mRNA` site `Translation` changes from `On` to `Off`; site `Translation` changes from `On` to `Off`. Rate parameter(s): `A20_Translation_Execute`.
- **TAK1_Degrade**: Production, removal, or biochemical conversion. The rule involves `TAK1` and produces `Trash`. Rate parameter(s): `TAK1_Degradation`.
- **TLR4_MAL**: Reversible binding/release. The rule involves `MAL`, `TLR4` and produces `MAL`, `TLR4`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `TLR4_MAL_Bind, TLR4_MAL_Unbind`.
- **TLR4MAL_MyD88**: Reversible binding/release. The rule involves `IRAK1`, `IRAK4`, `MAL`, `MyD88`, `TLR4` and produces `IRAK1`, `IRAK4`, `MAL`, `MyD88`, `TLR4`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `TLR4MAL_MyD88_Bind, TLR4MAL_MyD88_Unbind`.
- **MyD88IRAK1_TRAF6**: Reversible binding/release. The rule involves `IRAK1`, `IRAK4`, `MAL`, `MyD88`, `TLR4`, `TRAF6` and produces `IRAK1`, `IRAK4`, `MAL`, `MyD88`, `TLR4`, `TRAF6`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `MyD88IRAK1_TRAF6_Bind, MyD88IRAK1_TRAF6_B_Unbind`.
- **A20_MyD88IRAK1TRAF6**: Unbinding or disassembly. The rule involves `A20`, `IRAK1`, `IRAK4`, `MAL`, `MyD88`, `TLR4`, `TRAF6` and produces `A20`, `IRAK1`, `IRAK4`, `MAL`, `MyD88`, `TLR4`, `TRAF6`. Loss of matching `!` labels means a complex separates. Rate parameter(s): `A20_MyD88IRAK1TRAF6_Degrade`.
- **MyD88IRAK1TRAF6_TAK1**: State change or catalytic conversion. The rule involves `IRAK1`, `IRAK4`, `MAL`, `MyD88`, `TAK1`, `TLR4`, `TRAF6` and produces `IRAK1`, `IRAK4`, `MAL`, `MyD88`, `TAK1`, `TLR4`, `TRAF6`. The encoded molecular change is `TAK1` site `Activation` changes from `No` to `Yes`; site `Activation` changes from `No` to `Yes`. Rate parameter(s): `MyD88IRAK1TRAF6_TAK1_Activate`.
- **IkB_Translation**: State change or catalytic conversion. The rule involves `IkBmRNA` and produces `IkB`, `IkBmRNA`. The encoded molecular change is `IkBmRNA` site `Translation` changes from `On` to `Off`; site `Translation` changes from `On` to `Off`. Rate parameter(s): `IkB_Translation_Execute`.
- **TRIF_RP1**: Reversible binding/release. The rule involves `RP1`, `TRIF` and produces `RP1`, `TRIF`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `RP1_TRIF_Bind, RP1_TRIF_Unbind`.
- **TRIF_TRAF6**: Reversible binding/release. The rule involves `RP1`, `TRAF6`, `TRIF` and produces `RP1`, `TRAF6`, `TRIF`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `TRIF_TRAF6_Bind, TRIF_TRAF6_Unbind`.
- **A20_IkkAct_Deactivate**: State change or catalytic conversion. The rule involves `A20`, `Ikk_Complex` and produces `A20`, `Ikk_Complex`. The encoded molecular change is `Ikk_Complex` site `Activation` changes from `Yes` to `No`; site `Activation` changes from `Yes` to `No`. Rate parameter(s): `A20_IkkAct_Deactivate`.
- **A20_TRAF6TRIFRP1_Degrade**: Unbinding or disassembly. The rule involves `A20`, `RP1`, `TRAF6`, `TRIF` and produces `A20`, `RP1`, `TRAF6`, `TRIF`. Loss of matching `!` labels means a complex separates. Rate parameter(s): `A20_TRAF6TRIFRP1_Degrade`.
- **Ikk_complex_IkB_Phos**: Production, removal, or biochemical conversion. The rule involves `IkB`, `Ikk_Complex`, `NFkB` and produces `IkB`, `Ikk_Complex`, `NFkB`. Rate parameter(s): `Ikk_complex_IkB_Phos`.
- **NFkB_Translocation_Nucleus**: State change or catalytic conversion. The rule involves `NFkB` and produces `NFkB`. The encoded molecular change is site `Location` changes from `Cytoplasm` to `Nucleus`. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `NFkB_Translocation_Nucleus, NFkB_Translocation_Nucleus`.
- **NFkB_DNA_A20**: Reversible binding/release. The rule involves `DNA`, `NFkB` and produces `DNA`, `NFkB`. The encoded molecular change is `NFkB` site `Transcription` changes from `No` to `Yes`; site `Transcription` changes from `No` to `Yes`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `NFkB_DNA_A20_Bind, NFkB_DNA_A20_Unbind`.
- **IkB_DegradeNFkBA20**: Binding or assembly. The rule involves `DNA`, `IkB`, `NFkB` and produces `DNA`, `IkB`, `NFkB`. The encoded molecular change is `NFkB` site `Transcription` changes from `Yes` to `No`; site `Transcription` changes from `Yes` to `No`; site `Activation` changes from `Yes` to `No`; site `Location` changes from `Nucleus` to `Cytoplasm`. New matching `!` labels in the product mean those sites become physically connected. Rate parameter(s): `IkB_DegradeNFkB`.
- **NFkB_DNA_TNF**: Reversible binding/release. The rule involves `DNA`, `NFkB` and produces `DNA`, `NFkB`. The encoded molecular change is `NFkB` site `Transcription` changes from `No` to `Yes`; site `Transcription` changes from `No` to `Yes`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `NFkB_DNA_TNF_Bind, NFkB_DNA_TNF_Unbind`.
- **NFkB_DNA_IkB**: Reversible binding/release. The rule involves `DNA`, `NFkB` and produces `DNA`, `NFkB`. The encoded molecular change is `NFkB` site `Transcription` changes from `No` to `Yes`; site `Transcription` changes from `No` to `Yes`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `NFkB_DNA_IkB_Bind, NFkB_DNA_IkB_Unbind`.
- **IkB_Proteasome23_Degrade**: Unbinding or disassembly. The rule involves `IkB`, `NFkB`, `Proteasome26s` and produces `IkB`, `NFkB`, `Proteasome26s`. Loss of matching `!` labels means a complex separates. Rate parameter(s): `IkB_Proteasome23_Degrade`.
- **NFkB_IkB_Bind**: Reversible binding/release. The nearby model comment says: “NFkB_IkB_Bind: NFkB(Location~Cytoplasm,Activation~*)+IkB(Phos~No,p65,p50,Degrade~No)<->NFkB(Activation~*!0!1,Location~Cytoplasm).IkB(Phos~No,p65!0,p50!1,Degrade~No) NFkB_IkB_Bind,NFkB_IkB_Unbind”. The rule involves `IkB`, `NFkB` and produces `IkB`, `NFkB`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `NFkB_IkB_Bind, NFkB_IkB_Unbind`.
- **Proteasome23_Release**: Unbinding or disassembly. The nearby model comment says: “NFkB_IkB_Bind: NFkB(Location~Cytoplasm,Activation~*)+IkB(Phos~No,p65,p50,Degrade~No)<->NFkB(Activation~*!0!1,Location~Cytoplasm).IkB(Phos~No,p65!0,p50!1,Degrade~No) NFkB_IkB_Bind,NFkB_IkB_Unbind”. The rule involves `IkB`, `Proteasome26s` and produces `IkB`, `Proteasome26s`. Loss of matching `!` labels means a complex separates. Rate parameter(s): `IkB_Proteasome23_Degrade`.
- **IkB_Transcription_Execute**: Production, removal, or biochemical conversion. The nearby model comment says: “NFkB_IkB_Bind: NFkB(Location~Cytoplasm,Activation~*)+IkB(Phos~No,p65,p50,Degrade~No)<->NFkB(Activation~*!0!1,Location~Cytoplasm).IkB(Phos~No,p65!0,p50!1,Degrade~No) NFkB_IkB_Bind,NFkB_IkB_Unbind”. The rule involves `DNA`, `NFkB` and produces `DNA`, `IkBmRNA`, `NFkB`. Rate parameter(s): `IkB_Transcription_Execute`.
- **A20_Transcription_Execute**: Production, removal, or biochemical conversion. The nearby model comment says: “NFkB_IkB_Bind: NFkB(Location~Cytoplasm,Activation~*)+IkB(Phos~No,p65,p50,Degrade~No)<->NFkB(Activation~*!0!1,Location~Cytoplasm).IkB(Phos~No,p65!0,p50!1,Degrade~No) NFkB_IkB_Bind,NFkB_IkB_Unbind”. The rule involves `DNA`, `NFkB` and produces `A20mRNA`, `DNA`, `NFkB`. Rate parameter(s): `A20_Transcription_Execute`.
- **TNF_Transcription_Execute**: Production, removal, or biochemical conversion. The nearby model comment says: “NFkB_IkB_Bind: NFkB(Location~Cytoplasm,Activation~*)+IkB(Phos~No,p65,p50,Degrade~No)<->NFkB(Activation~*!0!1,Location~Cytoplasm).IkB(Phos~No,p65!0,p50!1,Degrade~No) NFkB_IkB_Bind,NFkB_IkB_Unbind”. The rule involves `DNA`, `NFkB` and produces `DNA`, `NFkB`, `TNFmRNA`. Rate parameter(s): `TNF_Transcription_Execute`.
- **TAK1_Deactivation**: State change or catalytic conversion. The nearby model comment says: “NFkB_IkB_Bind: NFkB(Location~Cytoplasm,Activation~*)+IkB(Phos~No,p65,p50,Degrade~No)<->NFkB(Activation~*!0!1,Location~Cytoplasm).IkB(Phos~No,p65!0,p50!1,Degrade~No) NFkB_IkB_Bind,NFkB_IkB_Unbind”. The rule involves `TAK1` and produces `TAK1`. The encoded molecular change is `TAK1` site `Activation` changes from `Yes` to `No`; site `Activation` changes from `Yes` to `No`. Rate parameter(s): `TAK1_Deactivation`.
- **Ikk_Deactivation**: State change or catalytic conversion. The nearby model comment says: “NFkB_IkB_Bind: NFkB(Location~Cytoplasm,Activation~*)+IkB(Phos~No,p65,p50,Degrade~No)<->NFkB(Activation~*!0!1,Location~Cytoplasm).IkB(Phos~No,p65!0,p50!1,Degrade~No) NFkB_IkB_Bind,NFkB_IkB_Unbind”. The rule involves `Ikk_Complex` and produces `Ikk_Complex`. The encoded molecular change is `Ikk_Complex` site `Activation` changes from `Yes` to `No`; site `Activation` changes from `Yes` to `No`. Rate parameter(s): `Ikk_Deactivation`.
- **TAK1_Ikk_Complex_Activate**: State change or catalytic conversion. The nearby model comment says: “NFkB_IkB_Bind: NFkB(Location~Cytoplasm,Activation~*)+IkB(Phos~No,p65,p50,Degrade~No)<->NFkB(Activation~*!0!1,Location~Cytoplasm).IkB(Phos~No,p65!0,p50!1,Degrade~No) NFkB_IkB_Bind,NFkB_IkB_Unbind”. The rule involves `Ikk_Complex`, `TAK1` and produces `Ikk_Complex`, `TAK1`. The encoded molecular change is site `Activation` changes from `No` to `Yes`. Rate parameter(s): `TAK1_Ikk_Complex_Activate`.
- **TNF_Degrade**: Production, removal, or biochemical conversion. The nearby model comment says: “NFkB_IkB_Bind: NFkB(Location~Cytoplasm,Activation~*)+IkB(Phos~No,p65,p50,Degrade~No)<->NFkB(Activation~*!0!1,Location~Cytoplasm).IkB(Phos~No,p65!0,p50!1,Degrade~No) NFkB_IkB_Bind,NFkB_IkB_Unbind”. The rule involves `TNF` and produces `Trash`. Rate parameter(s): `TNF_Degrade`.
- **A20_Degrade**: Production, removal, or biochemical conversion. The nearby model comment says: “NFkB_IkB_Bind: NFkB(Location~Cytoplasm,Activation~*)+IkB(Phos~No,p65,p50,Degrade~No)<->NFkB(Activation~*!0!1,Location~Cytoplasm).IkB(Phos~No,p65!0,p50!1,Degrade~No) NFkB_IkB_Bind,NFkB_IkB_Unbind”. The rule involves `A20` and produces `Trash`. Rate parameter(s): `A20_Degrade`.
- **IkB_DegradeNFkBDNAIkB**: Binding or assembly. The nearby model comment says: “NFkB_IkB_Bind: NFkB(Location~Cytoplasm,Activation~*)+IkB(Phos~No,p65,p50,Degrade~No)<->NFkB(Activation~*!0!1,Location~Cytoplasm).IkB(Phos~No,p65!0,p50!1,Degrade~No) NFkB_IkB_Bind,NFkB_IkB_Unbind”. The rule involves `DNA`, `IkB`, `NFkB` and produces `DNA`, `IkB`, `NFkB`. The encoded molecular change is `NFkB` site `Transcription` changes from `Yes` to `No`. New matching `!` labels in the product mean those sites become physically connected. Rate parameter(s): `IkB_DegradeNFkB`.
- **IkB_DegradeNFkBDNA_TNF**: Binding or assembly. The nearby model comment says: “NFkB_IkB_Bind: NFkB(Location~Cytoplasm,Activation~*)+IkB(Phos~No,p65,p50,Degrade~No)<->NFkB(Activation~*!0!1,Location~Cytoplasm).IkB(Phos~No,p65!0,p50!1,Degrade~No) NFkB_IkB_Bind,NFkB_IkB_Unbind”. The rule involves `DNA`, `IkB`, `NFkB` and produces `DNA`, `IkB`, `NFkB`. The encoded molecular change is `NFkB` site `Transcription` changes from `Yes` to `No`. New matching `!` labels in the product mean those sites become physically connected. Rate parameter(s): `IkB_DegradeNFkB`.

## 6. Observables and expected simulation output

Observables define what the simulator records. They are measurements of matching molecule patterns, complexes, or states, not claims that a particular trajectory must occur.

- `TNF` (Molecules) tracks patterns containing TNF. Pattern: `TNF(TNFr)`.
- `Activated_TAK1` (Molecules) tracks active signaling state. Pattern: `TAK1(TRAF6,Activation~Yes)`.
- `Activated_Ikk_complex` (Molecules) tracks active signaling state. Pattern: `Ikk_Complex(Activation~Yes)`.
- `A20` (Molecules) tracks patterns containing A20. Pattern: `A20(TRAF6)`.
- `NFkB_Active_Cyto` (Molecules) tracks active signaling state. Pattern: `NFkB(Transcription~No,Activation~Yes,Location~Cytoplasm)`.
- `NFkB_Active_Nucleus` (Molecules) tracks active signaling state. Pattern: `NFkB(Transcription~No,Activation~Yes,Location~Nucleus)`.
- `IkB_Degraded` (Molecules) tracks degraded or trash-marked material. Pattern: `IkB(Degrade~Yes)`.
- `IkB_active` (Molecules) tracks patterns containing IkB. Pattern: `IkB(Degrade~No)`.
- `NFkB_Inactive` (Molecules) tracks bound complexes. Pattern: `NFkB(Activation!+)`.
- `NonBoundNonPhos_IkB` (Molecules) tracks patterns containing IkB. Pattern: `IkB(Phos~No,p65,p50,Degrade~No)`.
- `IkBmRNA_Off` (Molecules) tracks patterns containing IkBmRNA. Pattern: `IkBmRNA(Translation~Off)`.
- `NFkB_DNA_IkB` (Molecules) tracks bound complexes, active signaling state. Pattern: `DNA(IkB!0).NFkB(Transcription~Yes!0,Activation~Yes,Location~Nucleus)`.
- `Phos_IkB_NFkB` (Molecules) tracks phosphorylated/modified molecules, bound complexes. Pattern: `NFkB(Transcription~No,Activation~No!0!1,Location~Cytoplasm).IkB(Phos~Yes,p65!0,p50!1,Degrade~No)`.
- `IkB_Prot26s` (Molecules) tracks phosphorylated/modified molecules, bound complexes, degraded or trash-marked material. Pattern: `IkB(Phos~Yes,p65,p50,Degrade~Yes!0).Proteasome26s(IkB!0)`.
- `Unbound_Cyto_NFkB` (Molecules) tracks patterns containing NFkB. Pattern: `NFkB(Location~Cytoplasm,Activation)`.
- `Inactive_Cyto_NFkB` (Molecules) tracks bound complexes. Pattern: `NFkB(Activation!0!1,Location~Cytoplasm).IkB(Phos~No,p65!0,p50!1,Degrade~No)`.
- `TNFmRNA_Off` (Molecules) tracks patterns containing TNFmRNA. Pattern: `TNFmRNA(Translation~Off)`.
- `TNF_NFkB_DNA` (Molecules) tracks bound complexes, active signaling state. Pattern: `DNA(TNF!0).NFkB(Transcription~Yes!0,Activation~Yes,Location~Nucleus)`.
- `A20_NFkB_DNA` (Molecules) tracks bound complexes, active signaling state. Pattern: `DNA(A20!0).NFkB(Transcription~Yes!0,Activation~Yes,Location~Nucleus)`.

Given these observables, plots from the model would show how the named signaling species, complexes, modified states, or coarse-grained variables change over the simulated time course under the listed initial conditions and rates.

## 7. Metadata, source, and compatibility

- Model id: `An_2009`
- Title/name: `An 2009`
- Category: `immunology`
- Tags: `['published', 'immunology', 'an', '2009', 'cd14', 'md2', 'tlr4', 'tram', 'trif', 'sarm', 'traf4', 'irak1']`
- Source origin: `published`
- Original repository: `bionetgen-web-simulator`
- Original format: `bngl`
- Metadata source path: `published-models/immune-signaling/An_2009.bngl`
- Local BNGL file used: `Published/An2009/An_2009.bngl`
- Local YAML file used: `Published/An2009/metadata.yaml`
- Compatibility: bng2 = `true`, NFsim = `false`, methods = `['ode']`
- Playground: visible = `true`, featured = `false`, difficulty = `intermediate`

## 8. Caveats or missing information

- This is a local, syntax-based explanation of the model and metadata; it does not validate the biological correctness of the publication model or reproduce simulations.
- Abbreviated molecule names are expanded only when the metadata, comments, or widely used biological abbreviation makes the identity clear; otherwise the BNGL name is preserved.
- Some large models contain many related binding/phosphorylation/dephosphorylation rules. Repetitive families are explained by their encoded biological event and nearby BNGL comments rather than by dumping raw BNGL syntax.
