# Detailed Model Explanation: Barua 2013 beta-catenin destruction model

## 1. Model identity and scope

Despite conflicting legacy metadata text, `Barua_2013.bngl` explicitly models beta-catenin (`bCat`) binding to APC and AXIN, recruitment of GSK3b and CK1a, phosphorylation, synthesis, degradation-state conversion, and release from destruction-complex partners. Sources: `Published/Barua2013/Barua_2013.bngl` and `Published/Barua2013/Barua_2013_metadata.yaml`.

## 2. BNGL block inventory

The file contains 25 parameters, 7 molecule types, 7 initial species, 29 reaction rules, 5 observables, and 2 inline actions. It uses `begin species` rather than `begin seed species`; there are no model delimiters, compartments, anchors, functions, or energy patterns.

## 3. Parameters, functions, and rate laws

The parameters fall into five functional groups:

- **Initial molecular pools**
  - `BCATtot = 11000`: live beta-catenin.
  - `APCtot = 31540`: APC.
  - `AXINtot = 3154`: AXIN scaffold.
  - `GSKtot = 31540`: GSK3b.
  - `CK1atot = 31540`: CK1a.
- **Beta-catenin binding**
  - APC 15-aa interface: `kf1_bap = 3.17e-6`, `kr1_bap = 0.273`.
  - Phosphorylated APC 20-aa interface: `kf2_bap = 3.17e-6`, `kr2_bap = 0.0015`.
  - AXIN interface: `kf_ba = 3.17e-6`, `kr_ba = 0.227`.
- **Destruction-complex assembly**
  - APC–AXIN: `kf_apa = 3.17e-6`, `kr_apa = 0.1`.
  - GSK3b–AXIN: `kf_ga = 3.17e-6`, `kr_ga = 0.065`.
  - CK1a–AXIN: `kf_ca = 3.17e-6`, `kr_ca = 0.1`.
  - `chi = 3154000` multiplies forward rates when two sites meet within an existing complex rather than by free diffusion.
- **Modification and turnover**
  - Beta-catenin phosphorylation/dephosphorylation: `kpb = 0.05`, `kmpb = 0.0012`.
  - APC phosphorylation/dephosphorylation: `kp = 0.05`, `kmp = 0.05`.
  - Slow unphosphorylated versus fast phosphorylated beta-catenin degradation marking: `kdb1 = 0.0000428`, `kdb2 = 0.00428`.
  - Constitutive beta-catenin synthesis: `ksb = 4.0`.
  - Five post-degradation bond-release rules use the literal fast rate `1000`.

There is no functions block; every rule uses these parameters or the literal cleanup rate directly.

## 4. Molecule types, sites, and states

| Molecule type | Site count | Sites/components | Internal states | Anchor/allowed compartments | Binding/modification roles | Notes |
| --- | ---: | --- | --- | --- | --- | --- |
| `AXIN` | 4 | `rgs`, `gid`, `b`, `e` | None | None | Binds APC, GSK3b, bCat, CK1a respectively | Scaffold |
| `GSK3b` | 1 | `a` | None | None | Binds `AXIN.gid`; catalyzes contextual phosphorylation patterns | Kinase |
| `APC` | 3 | `a15`, `a20`, `s` | `a20: U,P` | None | `a15` and phospho-`a20` bind bCat; `s` binds AXIN | Destruction-complex component |
| `bCat` | 5 | `s33s37`, `s45`, `ARM34`, `ARM59`, `ss` | `s33s37: U,P`; `s45: U,P`; `ss: l,d` | None | Two phosphosites, AXIN/APC-binding ARM regions, live/degraded status | Beta-catenin |
| `CK1a` | 1 | `e` | None | None | Binds `AXIN.e`; catalyzes contextual S45 phosphorylation | Kinase |
| `dead` | 0 | None | None | None | Seeded at zero but unused by rules | Nullary marker |
| `I` | 0 | None | None | None | Catalytic source carried through synthesis | Nullary source |

## 5. Compartments, anchors, initial species, and setup

No compartments or anchors are present. Free pools seed live, unphosphorylated bCat; unphosphorylated APC; AXIN; GSK3b; and CK1a at their total parameters. `I` is seeded at 1 and acts as a conserved source catalyst; `dead` is seeded at zero and never appears in a rule. The bCat seed contains a doubled comma after `s45~U`, a parser-sensitive typo.

## 6. Complete reaction-rule inventory

**Rule-family orientation.** Rules 1–15 assemble the destruction complex through free association or `chi`-accelerated intracomplex closure. Rules 16–24 implement ordered phosphorylation, reversal, synthesis, and degradation marking. Rules 25–29 rapidly dismantle contacts after degradation. Bond numbers are omitted here because they are local BNGL identifiers; the biologically relevant site pairs are named explicitly.

| # | Direction | Participants and required context | Bond or state change | Rate(s) | Implementation consequence |
| ---: | --- | --- | --- | --- | --- |
| 1 | Reversible | live `bCat` (`ARM59`) and APC (`a15`) | Create/remove the `ARM59–a15` bond | `kf1_bap`; `kr1_bap` | Allows beta-catenin to enter or leave APC through the 15-aa-repeat contact. |
| 2 | Reversible | bCat–AXIN–APC complex already linked through `ARM34–AXIN.b` and `AXIN.rgs–APC.s` | Close/open an additional `bCat.ARM59–APC.a15` bond | `chi*kf1_bap`; `kr1_bap` | Converts an already assembled chain into a multivalent closed complex; `chi` accelerates the intracomplex encounter. |
| 3 | Reversible | bCat already linked to phosphorylated `APC.a20` through `ARM34` | Close/open `bCat.ARM59–APC.a15` on that same pair | `chi*kf1_bap`; `kr1_bap` | Makes beta-catenin bivalently attached to APC through both ARM contact regions. |
| 4 | Reversible | live bCat (`ARM34`) and APC with `a20~P` | Create/remove the `ARM34–a20~P` bond | `kf2_bap`; `kr2_bap` | Makes APC phosphorylation permissive for the second beta-catenin-binding interface. |
| 5 | Reversible | bCat–APC pair already joined through `ARM59–a15`; APC `a20~P` | Close/open the second `ARM34–a20` contact | `chi*kf2_bap`; `kr2_bap` | Converts a singly attached pair into a bivalent bCat–APC complex. |
| 6 | Reversible | live bCat (`ARM34`) and AXIN (`b`) | Create/remove the `ARM34–b` bond | `kf_ba`; `kr_ba` | Directly recruits beta-catenin to the AXIN scaffold. |
| 7 | Reversible | bCat and AXIN already co-confined by an APC bridge | Close/open `bCat.ARM34–AXIN.b` | `chi*kf_ba`; `kr_ba` | Closes the APC–AXIN–bCat assembly into a multivalent complex. |
| 8 | Reversible | unphosphorylated APC (`a20~U`, `s`) and AXIN (`rgs`) | Create/remove `APC.s–AXIN.rgs` | `kf_apa`; `kr_apa` | Scaffolds APC to AXIN before APC phosphorylation. |
| 9 | Reversible | phosphorylated APC with free `a20~P`, plus AXIN | Create/remove `APC.s–AXIN.rgs` | `kf_apa`; `kr_apa` | Allows phosphorylated but beta-catenin-free APC to bind AXIN. |
| 10 | Reversible | phosphorylated APC whose `a20~P` is already occupied, plus AXIN | Create/remove `APC.s–AXIN.rgs` | `kf_apa`; `kr_apa` | Recruits a beta-catenin-occupied APC molecule to AXIN. |
| 11 | Reversible | APC–bCat–AXIN complex with APC `a20~U` and existing bCat–APC/AXIN contacts | Close/open `APC.s–AXIN.rgs` | `chi*kf_apa`; `kr_apa` | Adds the APC–AXIN contact inside an unphosphorylated multicomponent complex. |
| 12 | Reversible | same three-component context, but APC has free `a20~P` | Close/open `APC.s–AXIN.rgs` | `chi*kf_apa`; `kr_apa` | Stabilizes the phosphorylated destruction complex by intracomplex closure. |
| 13 | Reversible | same context with occupied `APC.a20~P` | Close/open `APC.s–AXIN.rgs` | `chi*kf_apa`; `kr_apa` | Completes a highly multivalent complex in which APC is also bound to beta-catenin at `a20`. |
| 14 | Reversible | GSK3b (`a`) and AXIN (`gid`) | Create/remove the kinase–scaffold bond | `kf_ga`; `kr_ga` | Positions GSK3b on AXIN for complex-localized phosphorylation. |
| 15 | Reversible | AXIN (`e`) and CK1a (`e`) | Create/remove the CK1a–AXIN bond | `kf_ca`; `kr_ca` | Positions CK1a on the destruction scaffold. |
| 16 | One-way | live bCat and CK1a in the same connected complex | `bCat.s45`: `U→P`; bonds unchanged | `kpb` | Primes beta-catenin at S45 without consuming or releasing CK1a. |
| 17 | One-way | live, S45-phosphorylated bCat and GSK3b in the same complex | `bCat.s33s37`: `U→P`; bonds unchanged | `kpb` | Adds the degradation-associated S33/S37 phosphorylation after S45 priming. |
| 18 | One-way | APC and GSK3b in the same connected complex | `APC.a20`: `U→P` | `kp` | Creates the APC state that can engage `bCat.ARM34`. |
| 19 | One-way | live S45-phosphorylated bCat | `s45`: `P→U` | `kmpb` | Removes the priming phosphate independently of complex membership. |
| 20 | One-way | live S33/S37-phosphorylated bCat | `s33s37`: `P→U` | `kmpb` | Reverses the degradation-associated beta-catenin modification. |
| 21 | One-way | phosphorylated APC in any AXIN-containing complex | `APC.a20`: `P→U` | `kmp` | Turns off the phospho-APC beta-catenin-binding state while APC remains scaffold-associated. |
| 22 | One-way | conserved source marker `I` | Create one free live bCat with both phosphosites `U`; retain `I` | `ksb` | Implements constitutive beta-catenin synthesis without depleting the source. |
| 23 | One-way | live bCat with `s33s37~U` | `ss`: `l→d` | `kdb1` | Marks unphosphorylated beta-catenin degraded at the slow basal rate. |
| 24 | One-way | live bCat with `s33s37~P` | `ss`: `l→d` | `kdb2` | Marks phosphorylated beta-catenin degraded at the much faster regulated rate. |
| 25 | One-way | degraded bCat bound through `ARM59` to `APC.a15` | Break `ARM59–a15`; emit separate molecules | `1000` | Rapidly clears the APC 15-aa contact after beta-catenin degradation. |
| 26 | One-way | same degraded bCat–APC contact, with another unspecified connection retaining one complex | Break `ARM59–a15`; keep products connected elsewhere | `1000` | Removes this contact without forcing complete complex dissociation. |
| 27 | One-way | degraded bCat bound through `ARM34` to phosphorylated `APC.a20` | Break `ARM34–a20`; emit separate molecules | `1000` | Releases APC from degraded beta-catenin. |
| 28 | One-way | degraded bCat bound through `ARM34` to `AXIN.b` | Break `ARM34–b`; emit separate molecules | `1000` | Releases AXIN from degraded beta-catenin. |
| 29 | One-way | same degraded bCat–AXIN contact, with another connection retaining the complex | Break `ARM34–b`; keep products connected elsewhere | `1000` | Removes the direct AXIN contact while preserving any alternative connection. |

## 7. Observables and technical readouts

Molecules `bcat_tot` counts live (`ss~l`) bCat. `bCat_pS45` and `bCat_pS33S37` count live bCat phosphorylated at the named sites. `APC_p20a` counts phosphorylated `APC.a20~P` whether unbound or bound (`!?`). Species `BCat_Axin` counts complete species containing the explicit live `bCat.ARM34!1-AXIN.b!1` complex.

## 8. Actions and simulation workflow

`generate_network` overwrites the network and caps `APC`, `AXIN`, and `bCat` at one copy per species. `simulate_ode` runs to `t_end=250000` with 2500 steps, sparse integration, `rtol=1e-8`, and an apparent misspelling `atoll=>1e-08`.

## 9. Technical caveats and ambiguities

The detailed metadata description (“JAK2-SH2B signaling”) and tags conflict with both the BNGL and the simpler metadata, which identify beta-catenin destruction; this explanation follows the model. Kinases in rules 16–18 appear only as unconstrained members of the same connected complex—no catalytic binding-site edit occurs in those rules. The connected product forms in rules 26 and 29 rely on other unspecified bonds to retain connectivity. The doubled comma in the seed, `atoll` action key, nullary molecule syntax, and bounded `max_stoich` map may require parser-specific handling.
