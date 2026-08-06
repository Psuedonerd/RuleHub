# Detailed Model Explanation: Chylek 2014 FcεRI signaling model

## 1. Model overview

This model follows early FcεRI signaling from transient exposure of two ligand haptens and receptor crosslinking through parallel Lyn- and Fyn-dependent kinase branches. It couples receptor and Syk phosphorylation to PAG1–CSK feedback, LAT adaptor assembly, PI3K/PIP3 signaling, PLCG1 activation, and INPP5D-mediated lipid turnover.

## 2. BNGL block inventory

The model contains 114 active parameter lines, 23 molecule types, 19 seed species, 133 reaction rules, and 32 molecule-count observables. It defines no functions, compartments, anchors, or embedded actions.

## 3. Parameters, functions, and rate laws

Rates are mass-action constants expressed for molecule-number simulation in a 2% cell fraction; bimolecular constants are divided by Avogadro's number and the simulated cell or extracellular volume. Parameter families distinguish binding (`kf`/`kr`), catalytic phosphorylation (`kp` or `kc`), dephosphorylation (`kdp`/`dp`), and lipid interconversion.

| Parameter group or names | Function in this model |
| --- | --- |
| `NA`, `celldensity`, `Fx`, `ECFvol`, `simECFvol`, `Cellvol`, `simCellvol` | Define extracellular and cellular volumes and convert concentration-based association constants for the simulated 2% fraction. |
| `ProteinTot`, `SimProteinTot`, `LigTot`, `SimLigTot` | Set common starting abundances for most proteins and for the bivalent ligand after fractional-cell scaling. |
| `lambda_p`, `lambda_m`, `kfl`, `kxl`, `krl` | Control buried-to-exposed hapten switching, ligand capture, receptor crosslinking, and dissociation. `kfl` is zero here, making receptor engagement dependent on an external stimulus protocol. |
| `kfRecLyn1/2`, `krRecLyn1/2`, `kfLynIn`, `krLynIn` | Govern Lyn binding through its unique or SH2 domain and intramolecular sequestration of SH2 by phosphorylated Y508. |
| `kpLynB1/2`, `kpLynG1/2`, `kfRecSyk`/`krRecSyk`, `kpLynSyk1/2`, `kpSykSyk0/P` | Set Lyn-dependent receptor phosphorylation, Syk docking and Y346 phosphorylation, and Syk activation-loop transphosphorylation. The paired rates distinguish unique-domain versus SH2-bound Lyn and inactive versus activated Syk. |
| `kfPagLynSH3`, `kfPagLynSH3_2`, `krPagLynSH3`, `kfPagLynSH2`, `kfPagLynSH2_2`, `krPagLyn2point`, `kpLynPag` | Control one- and two-point Lyn attachment to PAG1 and Lyn-dependent phosphorylation of PAG1 docking sites. Tethered second-site capture uses a fast first-order rate. |
| `kfCskPag`/`krCskPag`, `kpCskLyn` | Recruit CSK to PAG1 pY317 and install inhibitory Lyn Y508 phosphorylation. |
| Fyn analogues of the receptor, intramolecular, PAG1, and CSK parameters; `eff` | Reproduce the Lyn branch for Fyn. Fyn catalytic rates toward receptor, Syk, and PAG1 are divided by `eff = 5`, while binding rates inherit Lyn values; CSK targets Fyn Y531. |
| `kfSykLat`/`krSykLat`, `kpSykLat1/2` | Govern transient Syk–LAT encounters and phosphorylation of LAT Y136/Y175, with activated Syk using the faster catalytic rate. |
| `KD_LatPlcg`, `kfLatPlcg`/`krLatPlcg`; `kfLatGrb2`/`krLatGrb2`; `kfLatGrap2`/`krLatGrap2` | Set recruitment of PLCG1, GRB2, and GRAP2 to their LAT phosphotyrosine sites; the PLCG1 on-rate is derived from its dissociation constant. |
| `KD_Grb2Gab2`, `kfGrb2Gab2`/`krGrb2Gab2`, `kfGrap2Lcp2`/`krGrap2Lcp2`, `KD_Lcp2Plcg1`, `kfLcp2Plcg1`/`krLcp2Plcg1` | Assemble the GRB2–GAB2 and GRAP2–LCP2–PLCG1 adaptor branches. The source declares the GRB2/GAB2 constant and associated rates twice; later definitions may override earlier ones depending on parser behavior. |
| `kfFynGab2`/`krFynGab2`, `kpFynGab2`, `kfGab2Pi3k`/`krGab2Pi3k` | Control Fyn phosphorylation of GAB2 Y441 and PI3K recruitment to that phosphosite. |
| `kfPi3kPip2`/`krPi3kPip2`, `kpPi3k`, `kfBtkPip3`/`krBtkPip3`, `kfBtkPlcg`/`krBtkPlcg`, `kpBtkPlcg` | Convert PI45P2 to PI345P3, recruit BTK to PI345P3, and let BTK phosphorylate PLCG1 Y783. |
| `kfPlcgPip2`, `krPlcgPip2`, `kcPlcgP`, `kcPlcg0` | Parameterize PLCG1 access to PI45P2 and catalysis by phosphorylated or unphosphorylated PLCG1; no active reaction rules consume these constants in this file. |
| `kfShipRec`/`krShipRec`, `kfShipPip3`/`krShipPip3`, `kdpShipPip3`, `kfShipPip2`/`krShipPip2` | Govern INPP5D recruitment to receptor pY224, binding and removal of PI345P3, and a declared but unused PI34P2-binding pair. |
| `kPten`, `kfP5`, `krP5` | Control background PI345P3-to-PI45P2 conversion and reversible PI4P/PI45P2 interconversion. |
| `p`, `dp` | Apply uniform nonspecific phosphorylation and dephosphorylation to receptor, kinase, scaffold, adaptor, and PLCG1 sites. |

There are no active functions; algebraic relationships such as Fyn's `1/eff` catalytic scaling and affinity-derived on-rates are resolved in the parameter namespace.

## 4. Molecule types, sites, and states

| Molecule type(s) | Site count | Sites/components | Internal states | Anchor/allowed compartments | Explanation |
| --- | ---: | --- | --- | --- | --- |
| `Lig` | 2 | two repeated `hap` sites | Each `hap`: buried `b`, exposed `e` | None | Bivalent ligand whose independently exposed haptens capture and crosslink receptors. |
| `Rec` | 5 | two repeated `fab`, `b_Y218`, `b_Y224`, `g_Y65_Y76` | Each Y variable: `0`, `P` | None | Lumped FcεRI/IgE receptor unit with two ligand-binding sites and β/γ-chain signaling phosphosites. |
| `Lyn` | 5 | `U`, `SH3`, `SH2`, `Y397`, `Y508` | Both Y sites: `0`, `P` | None | Src-family kinase recruited to receptor and PAG1; Y508 supports modeled intramolecular inhibition. |
| `Fyn` | 6 | `U`, `SH3`, `SH2`, `PTK`, `Y420`, `Y531` | Both Y sites: `0`, `P` | None | Parallel Src-family kinase that also phosphorylates GAB2; Y531 supports autoinhibitory closure. |
| `Syk` | 4 | `tSH2`, `Y346`, `PTK`, `Y519_Y520` | Both Y variables: `0`, `P` | None | Binds phosphorylated receptor γ sites and propagates activation to LAT after transphosphorylation. |
| `Pag1` | 5 | `PRS1`, `Y165_Y183`, `PRS2`, `Y317`, `Y386_Y409` | Three Y variables: `0`, `P` | None | Multisite scaffold that captures Fyn/Lyn and CSK to form kinase-specific inhibitory complexes. |
| `Csk` | 1 | `SH2` | None | None | PAG1-recruited kinase that phosphorylates inhibitory Lyn Y508 or Fyn Y531. |
| `Lat` | 2 | `Y136`, `Y175` | Both: `0`, `P` | None | Syk substrate whose two phosphosites recruit PLCG1 or adaptor proteins. |
| `Plcg1` | 4 | `SH2`, `SH3`, `PLC`, `Y783` | `Y783`: `0`, `P` | None | LAT/LCP2-associated effector activated by BTK phosphorylation in the implemented rules. |
| `Grb2`, `Grap2` | 2 each | Grb2: `SH2`, `cSH3`; Grap2: `SH2`, `SH3` | None | None | Adaptors linking LAT Y175 to GAB2–PI3K or LCP2–PLCG1, respectively. |
| `Gab2` | 2 | `PRS`, `Y441` | `Y441`: `0`, `P` | None | GRB2-bound scaffold phosphorylated by Fyn to recruit PI3K. |
| `Lcp2` | 2 | `RxxK`, `PRS` | None | None | GRAP2-linked adaptor that offers a second PLCG1 recruitment site. |
| `Pi3k` | 2 | `p85_SH2`, `PI3Kc` | None | None | Binds GAB2 pY441 and catalyzes PI45P2 conversion to PI345P3. |
| `Btk` | 2 | `PH`, `PTK` | None | None | Recruited by PI345P3 and phosphorylates PLCG1 Y783. |
| `Inpp5d` | 3 | `SH2`, `IPP`, `C2` | None | None | Receptor-recruited lipid phosphatase that consumes PI345P3. |
| `PI34P2`, `PI45P2`, `PI345P3` | 1 each | `bind` | None | None | Explicit phosphoinositide pools; PI45P2 is the PI3K substrate, PI345P3 recruits BTK, and PI34P2 is declared as a potential product/readout but is not generated by an active rule. |
| `PI4P`, `IP3`, `DAG`, `Sink` | 0 each | None | None | None | PI4P exchanges with PI45P2; Sink enables background PI345P3 removal. IP3 and DAG are declared output species but are not produced by active rules. |

## 5. Compartments, anchors, initial species, and setup

The model has no explicit compartments or anchors, so membrane-associated receptors, adaptors, and lipids are represented through molecule identity and bonds rather than localization syntax. Ligand begins with both haptens buried, and the receptor, kinases, adaptors, and enzymes begin free and unphosphorylated at a shared scaled protein abundance. PI45P2, PI4P, and Sink are initially present at that same scale; PI345P3, PI34P2, IP3, and DAG have no seed pools and can appear only if rules produce them—of these, only PI345P3 is actively generated.

## 6. Reaction-rule inventory

**Rule-family orientation.** Rules 1–22 expose ligand, crosslink receptors, and activate the Lyn/Syk core. Rules 23–69 implement parallel PAG1-based Lyn and Fyn feedback; rules 70–105 build LAT, PI3K, BTK, PLCG1, and INPP5D branches, followed by nonspecific phosphosite turnover in rules 106–133.

| Rule number(s) | Direction | Involved molecules/sites | Exact modeled change and rate logic | Role within the model |
| ---: | --- | --- | --- | --- |
| 1 | Reversible | Either ligand `hap` site | Switches one hapten between buried and exposed states at `lambda_p` and `lambda_m`. | Gates receptor accessibility without creating or destroying ligand. |
| 2–5 | One-way | Exposed ligand haptens; receptor `fab` sites | Rules 2–3 capture a receptor through an exposed hapten in the two possible state contexts, rule 4 adds a second receptor to the other exposed hapten, and rule 5 releases a hapten–receptor bond. | Produces the receptor dimers that initiate signaling; with `kfl = 0`, capture is disabled until externally enabled. |
| 6–11 | One-way | Receptor b_Y218; Lyn `U`, `SH2`, Y508 | Rules 6–9 separately form and release unique-domain binding to unphosphorylated receptor or SH2 binding to pY218. Rules 10–11 close and reopen the intramolecular SH2–pY508 bond. | Controls Lyn recruitment and inhibitory sequestration as explicit directional steps. |
| 12–17 | One-way | Crosslinked receptors; receptor Y218, Y224, Y65_Y76; Lyn bound through `U` or `SH2` | Rules 12/13 phosphorylate Y218, 14/15 Y224, and 16/17 the lumped γ-chain site; the first member uses the unique-domain rate and the second the faster SH2-bound rate. | Writes the receptor phosphotyrosines needed for kinase retention, Syk binding, and INPP5D recruitment. |
| 18–20 | Mixed | Receptor pY65_Y76; Syk `tSH2`/Y346; receptor-bound Lyn | Rule 18 reversibly recruits Syk. Rules 19–20 phosphorylate Syk Y346 via unique-domain- or SH2-bound Lyn. | Loads and primes Syk on the phosphorylated receptor γ site. |
| 21–22 | One-way | Two receptor-bound Syk molecules; target Syk Y519_Y520 | One Syk changes the partner's activation-loop variable from `0` to `P`; unphosphorylated Syk uses `kpSykSyk0`, activated Syk the doubled `kpSykSykP`. | Makes receptor crosslinking support cooperative Syk activation. |
| 23–28 | One-way | Lyn `SH3`/`SH2`; PAG1 `PRS2`/Y386_Y409 | Forms either PAG1 contact from solution or rapidly adds it after the other contact has tethered Lyn; separate rules release the SH3 bond or both contacts. | Creates a two-point Lyn–PAG1 complex with avidity-like tethered capture. |
| 29–36 | One-way | PAG1 Y386_Y409, Y165_Y183, Y317; PAG1-bound Lyn | Lyn phosphorylates the three PAG1 variables across one- and two-point occupancy contexts: rule 29 targets Y386_Y409, 30–32 target Y165_Y183, and 33–36 target Y317. | Builds Lyn docking and CSK recruitment sites on the negative-feedback scaffold. |
| 37–40 | Mixed | PAG1 pY317; CSK `SH2`; PAG1-bound Lyn Y508 | Rule 37 reversibly recruits CSK. Rules 38–40 phosphorylate Lyn Y508 in three permitted Lyn–PAG1 topologies. | Converts the Lyn–PAG1 complex into a CSK-dependent inhibitory circuit. |
| 41–46 | One-way | Receptor b_Y218; Fyn `U`, `SH2`, Y531 | Mirrors rules 6–11 for Fyn: directional receptor association/dissociation through `U` or `SH2`, followed by intramolecular SH2–pY531 closure and reopening. | Gives Fyn an independently represented recruitment and autoinhibition cycle. |
| 47–54 | One-way | Crosslinked receptors; receptor Y218/Y224/Y65_Y76; Syk Y346; receptor-bound Fyn | Rules 47–52 phosphorylate the three receptor variables through unique-domain or SH2-bound Fyn; rules 53–54 phosphorylate Syk Y346 in those two contexts. All Fyn catalytic rates are Lyn rates divided by `eff`. | Supplies a slower parallel route for receptor and Syk phosphorylation. |
| 55–60 | One-way | Fyn `SH3`/`SH2`; PAG1 `PRS1`/Y165_Y183 | Forms one- or two-point Fyn–PAG1 attachments, adds the second contact from a tethered state, and releases one or both contacts. | Builds the Fyn-specific half of the PAG1 scaffold using sites distinct from Lyn's. |
| 61–66 | One-way | PAG1 Y386_Y409/Y317; PAG1-bound Fyn | Rules 61–63 phosphorylate Y386_Y409 and rules 64–66 phosphorylate Y317 across three Fyn-binding topologies at the `eff`-reduced PAG1 rate. | Lets Fyn prepare the common CSK docking module despite its distinct PAG1 contacts. |
| 67–69 | One-way | PAG1 pY317; CSK; Fyn Y531 | CSK changes Fyn Y531 from `0` to `P` in three one- or two-point Fyn–PAG1 arrangements. | Closes the Fyn negative-feedback loop through its inhibitory tyrosine. |
| 70–78 | One-way | Receptor-bound Syk `PTK`; LAT Y136 or Y175 | Rules 70–73 bind, release, or phosphorylate Y136; rules 75–78 repeat this for Y175. Activated Syk uses `kpSykLat2`, whereas unactivated Syk uses `kpSykLat1`; rule 74 separately recruits PLCG1 to pY136. | Converts Syk activation into two differentiated LAT docking sites and begins PLCG1 recruitment. |
| 74, 79–83 | Reversible | LAT pY136/pY175; PLCG1 `SH2`; GRB2/GRAP2 `SH2`; GAB2 `PRS`; LCP2 `RxxK`/`PRS`; PLCG1 `SH3` | Rule 74 binds PLCG1 to pY136. Rules 79–80 competitively recruit GRB2 or GRAP2 to pY175; 81 links GRAP2 to LCP2, 82 links GRB2 to GAB2, and 83 links LCP2 to PLCG1. | Splits LAT output into PLCG1, GAB2–PI3K, and LCP2-supported PLCG1 assemblies. |
| 84–87 | One-way | Fyn `PTK`; LAT–GRB2–GAB2 complex; GAB2 Y441 | Rules 84–85 create a transient Fyn–GAB2 catalytic contact from two Fyn recruitment contexts; rule 86 releases unchanged GAB2, while rule 87 releases it with Y441 phosphorylated. | Makes the assembled GRB2/GAB2 branch competent to recruit PI3K. |
| 88 | Reversible | GAB2 pY441; PI3K `p85_SH2` | Creates or releases the GAB2–PI3K bond. | Couples Fyn-dependent adaptor phosphorylation to lipid kinase recruitment. |
| 89–92 | One-way | Recruited PI3K `PI3Kc`; PI45P2 | PI3K binds PI45P2 (89), can release it unchanged (90), or catalyze PI345P3 production while retaining (91) or deleting (92) the matched substrate copy. | Generates the PIP3-like signal while using alternative BNGL product semantics to manage the lipid pool. |
| 93–96 | Mixed | PI345P3; BTK `PH`/`PTK`; recruited PLCG1 Y783 | PI345P3 reversibly recruits BTK. BTK then forms a transient PLCG1 contact, releases unchanged substrate, or releases PLCG1 with Y783 phosphorylated. | Links PI3K lipid production to PLCG1 activation. |
| 97–102 | Mixed | Receptor pY224; INPP5D `SH2`/`IPP`/`C2`; PI345P3; Sink | Rules 97–99 recruit and release INPP5D through two receptor-context routes, with C2-tethered capture accelerated 100-fold. Rules 100–101 bind then delete PI345P3; rule 102 provides slower sink-mediated deletion. | Opposes PI3K by consuming PI345P3 through receptor-coupled and background routes. |
| 103–105 | One-way | PI345P3, PI45P2, PI4P | Rule 103 converts PI345P3 to PI45P2 while deleting the reactant; rules 104–105 interconvert PI4P and PI45P2. | Replenishes and drains the PI45P2 substrate pool independently of receptor complexes. |
| 106–111 | One-way | Receptor Y218, Y224, Y65_Y76 | Consecutive `p`/`dp` rule pairs add or remove phosphorylation at each receptor variable. | Supplies basal receptor-site turnover outside Lyn/Fyn-containing crosslinks. |
| 112–119 | One-way | Lyn Y508, Fyn Y531, Syk Y346/Y519_Y520 | Consecutive phosphorylation/dephosphorylation pairs turn over the inhibitory Src-family sites and both Syk sites. | Maintains resting enzyme-state flux alongside the scaffold-specific catalytic routes. |
| 120–133 | One-way | PAG1 Y317/Y165_Y183/Y386_Y409; GAB2 Y441; LAT Y136/Y175; PLCG1 Y783 | Seven consecutive `p`/`dp` pairs independently turn over these downstream phosphosites. | Produces basal occupancy and decay for feedback, adaptor, scaffold, and effector readouts. |

## 7. Observables and technical readouts

| Observable(s) | Type | What is measured | Technical interpretation |
| --- | --- | --- | --- |
| `Rec_pY218`, `Rec_pY224`, `Rec_pY65_Y76` | Molecule count | Receptor units phosphorylated at each β- or γ-chain variable, regardless of bond occupancy. | Site-specific receptor activation measures; one multisite receptor contributes to every matching readout. |
| `Syk_pY346`, `Syk_pY519_520`, `Lyn_pY508`, `Fyn_pY508` | Molecule count | Syk priming/activation-loop states and inhibitory Src-family phosphorylation. | Distinguishes Syk activation stages and kinase inhibitory-site occupancy. Despite its name, `Fyn_pY508` actually matches Fyn Y531. |
| `Lat_pY136`, `Lat_pY175`, `Gab2_pY441`, `Plcg1_pY783`, `Pag_Y165`, `Pag_Y409` | Molecule count | Phosphorylated scaffold, adaptor, effector, and PAG1 lumped sites. | Reports propagation and feedback, including phosphorylation produced by both specific and nonspecific rules. |
| `LynUbound`, `LynSH2bound`, `Shipbound`, `Btk_recruited` | Molecule count | Lyn with occupied unique or SH2 domains, receptor-bound INPP5D, and PIP3-bound BTK. | Recruitment-state readouts; a Lyn bound at both domains contributes to both Lyn observables. |
| `LynIn`, `FynIn` | Molecule count | Closed intramolecular SH2–inhibitory-pY bonds in Lyn or Fyn. | Directly measures the modeled autoinhibited conformations rather than phosphorylation alone. |
| `Lat_Plc`, `Plc_pip2`, `PI3K_recruited` | Molecule count | LAT–PLCG1, PLCG1–PI45P2, and complete LAT–GRB2–GAB2–PI3K complexes. | `Lat_Plc` and `PI3K_recruited` are active assembly readouts; `Plc_pip2` remains zero because no active rule binds PLCG1 to PI45P2. |
| `PI345P3`, `PI34P2`, `PI45P2`, `IP3` | Molecule count | Counts of the named lipid or soluble-product species in any allowed binding state. | PI345P3 and PI45P2 are dynamic; PI34P2 and IP3 lack active production rules and therefore remain absent from the specified setup. |
| `LigFree`, `LigTotal` | Molecule count | All ligand molecules with unconstrained hapten states/bonds; both patterns are broad. | These patterns do not explicitly require an unbound ligand, so `LigFree` is not a strict free-ligand measure and may track the same total embeddings as `LigTotal`. |
| `Crosslinks` | Molecule count | Ligands using both exposed haptens to bind two receptors. | Measures receptor-crosslinking embeddings rather than necessarily unique connected components. |
| `DNP_exposed_0_of_2`, `DNP_exposed_1_of_2`, `DNP_exposed_2_of_2` | Molecule count | Ligands with zero, one, or two exposed haptens, allowing either bound or free sites. | Partitions ligand by accessibility state; repeated identical `hap` sites can introduce embedding multiplicity, especially in the one-exposed-state pattern. |

## 8. Actions and simulation workflow

No action commands are embedded, so loading the model alone neither generates a network nor runs a trajectory. The metadata identifies ODE simulation, but an external workflow must first enable ligand capture by changing the zero-valued `kfl`, then generate the reaction network and integrate the desired basal/stimulated time course.

## 9. Technical caveats and ambiguities

- The file contains parser-sensitive features: repeated identical sites, `DeleteMolecules`, wildcard bonds, and duplicate parameter declarations. The metadata consequently marks it as not BNG2-compatible even though ODE is listed as the intended simulation method.
- `KD_Grb2Gab2`, `krGrb2Gab2`, and `kfGrb2Gab2` are declared twice with different dissociation-rate definitions; effective behavior depends on how the parser resolves duplicate names.
- Several declared mechanisms are incomplete in the active rules: PLCG1 lipid hydrolysis constants are unused, and no rules create IP3, DAG, or PI34P2. Those observables should not be interpreted as functioning pathway outputs in this version.
- Some names are misleading or lumped: `Fyn_pY508` observes Y531, `Pag_Y165` covers Y165/Y183, and `Pag_Y409` covers Y386/Y409.
- Molecule observables count pattern matches; repeated ligand/receptor sites and multivalent assemblies can yield embedding counts rather than unique ligand or complex counts.
