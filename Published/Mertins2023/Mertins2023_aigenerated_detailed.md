# Detailed Model Explanation: Mertins 2023 DNA-Damage, PARP Inhibition, and Apoptosis

## 1. Model overview

This model is intended to couple competition between p53 and PARP at DNA double-strand breaks to Bax production and caspase activation. A PARP inhibitor competes with NAD at activated, DNA-bound PARP and releases PARP from damage, while the Bax–BclXL–Bad module determines how much free Bax can drive apoptosis.

## 2. BNGL block inventory

The text contains 38 intended parameter declarations, 13 molecule types, 10 seed species, 5 molecule-count observables, and 19 intended reactions, with no functions, compartments, anchors, or actions. However, missing/mismatched block terminators prevent these from forming valid active BNGL blocks as written; the counts describe the clearly delimited intended content rather than successfully parsed model blocks.

## 3. Parameters, functions, and rate laws

The namespace separates synthesis/degradation (`s*`, `d*`), reversible binding (`b*`, `u*`, `kf*`, `kr*`), phosphorylation (`p1`, `q1`), caspase activation (`a1`, `a2`), PAR turnover (`kcat1`, `kcat2`), and initial totals. Reactions mix mass action with an observable-dependent Hill transcription term and an additive caspase activation rate; these expressions are interpretable but not executable until the block syntax and undefined seed symbols are repaired.

| Parameter group or names | Function in this model |
| --- | --- |
| `s1`, `s2`, `d1`, `M` | Control basal Bax-mRNA production, p53/DNA-bound inducible production, transcript loss, and the half-saturation scale of the squared p53 response. |
| `s4`, `d2` | Translate Bax in proportion to mRNA and remove free or BclXL-bound Bax. |
| `s3`, `d3`, `a1`, `a2` | Produce procaspase, turn over either caspase state, and activate procaspase through free Bax plus quadratic active-caspase feedback. |
| `b1/u1`, `b2/u2`, `b3/u3` | Reversibly bind Bax–BclXL, unphosphorylated Bad–BclXL, and phosphorylated Bad–14-3-3. |
| `p1`, `q1`, `AKTtot` | Set AKT-dependent Bad phosphorylation and reverse dephosphorylation; `AKTtot=0` disables the forward reaction in the supplied setup. |
| `b4`, `u4` | Give p53 and PARP a shared association/dissociation scale for competing at the DNA-break site. |
| `kf1/kr1`, `kcat1` | Control NAD binding to DNA-activated PARP and PARP-catalyzed PARylation of XRCC1. |
| `kcat2` | Controls PARG-catalyzed removal of PAR from XRCC1. |
| `IC50`, `kf2`, `kr2` | Define inhibitor competition at the PARP NAD pocket; `kr2` is derived from `IC50` and the NAD dissociation scale. |
| `DNADSBtot`, `p53tot`, `BADtot`, `BCLXLtot`, `SCAFtot`, `PARPtot`, `NADtot`, `XRCC1tot`, `PARGtot`, `Inhtot` | Intended initial amounts for damage, p53, apoptotic regulators, PAR metabolism, repair scaffold, and inhibitor. |

There are no declared functions. The p53-dependent transcription and caspase feedback calculations are written directly as rule-rate expressions.

## 4. Molecule types, sites, and states

| Molecule type(s) | Site count | Sites/components | Internal states | Anchor/allowed compartments | Explanation |
| --- | ---: | --- | --- | --- | --- |
| `DNADSB`, `p53` | 1 each | `br`; `dna` | None | None | Competing damage site and p53 DNA-binding participant used to drive Bax transcription. |
| `mRNA_Bax` | 0 | None | None | None | Transcript produced basally or through damage-bound p53. |
| `Bax`, `BclXL` | 1 each | `b` | None | None | Pro-apoptotic Bax is buffered by binding the anti-apoptotic BclXL pool. |
| `Bad` | 2 | `S75_S99`, `b` | `0/PP` | None | Competes with Bax for BclXL when unphosphorylated and switches to 14-3-3 binding after phosphorylation. |
| `Fourteen_3_3` | 1 | `b` | None | None | Sequesters phosphorylated Bad. |
| `Caspase` | 1 | `csp` | `Pro/Act` | None | Terminal protease switch activated by free Bax and by active-caspase feedback. |
| `PARP` | 3 | `DNA`, `CD`, `NAD` | catalytic domain `inact/act` | None | Binds damage, becomes catalytically active, and uses its NAD pocket for substrate or inhibitor binding. |
| `NAD` | 1 | `sub` | None | None | PARP substrate that is bound before XRCC1 PARylation. |
| `XRCC1` | 1 | `Glu` | unmodified (`uPAR`) or PARylated (`PAR`) | None | Representative repair scaffold modified by PARP and reversed by PARG. |
| `PARG` | 1 | `CD` | None | None | Catalytically removes PAR from XRCC1. |
| `Inh` | 1 | `isub` | None | None | Competitive PARP inhibitor occupying the NAD site. |

## 5. Compartments, anchors, initial species, and setup

No spatial structure is intended. Damage, p53, BclXL, unphosphorylated Bad, 14-3-3, inactive PARP, NAD, unmodified XRCC1, PARG, and inhibitor are seeded; Bax mRNA, Bax, and caspase arise dynamically. Two seed expressions refer to undefined names—`BCLXtot` instead of `BCLXLtot` and `NADPtot` instead of `NADtot`—so even after block repair those initial pools require correction. Active AKT is initialized to zero, making Bad phosphorylation and the associated release reactions silent unless that parameter is changed.

## 6. Reaction-rule inventory

**Rule-family orientation.** Intended reactions 1–6 describe competition and catalysis at DNA damage, 7–11 produce and buffer Bax, 12–16 control Bad's choice of binding partner, and 17–19 implement caspase production, turnover, and activation.

| Rule number(s) | Direction | Involved molecules/sites | Exact modeled change and rate logic | Role within the model |
| ---: | --- | --- | --- | --- |
| 1 | Reversible | `p53.dna`, `DNADSB.br` | Creates or releases the p53–break bond at `b4/u4`. | Generates the `p53_DNAbound` signal used by inducible Bax transcription. |
| 2 | Reversible | Inactive `PARP.DNA/CD`, free `DNADSB.br` | PARP binds the break and changes its catalytic domain `inact→act`; dissociation restores free inactive PARP. | Makes PARP compete with p53 for the same damage pool and licenses catalysis. |
| 3 | Reversible | DNA-bound active PARP `NAD`, `NAD.sub` | Creates the PARP–NAD bond at `kf1` and releases it at `kr1`. | Loads activated PARP with substrate. |
| 4 | One-way | NAD-loaded DNA-bound PARP, `XRCC1.Glu=uPAR` | Releases NAD, retains PARP on DNA, and changes XRCC1 `uPAR→PAR` at `kcat1`. | Represents one repair-scaffold PARylation cycle. |
| 5 | One-way | `PARG`, `XRCC1.Glu=PAR` | Retains PARG and changes XRCC1 `PAR→uPAR` at `kcat2`. | Reverses the PARP modification. |
| 6 | Reversible | `Inh.isub`; active DNA-bound PARP `NAD`; damage site | Inhibitor binding occupies the NAD pocket and simultaneously releases PARP from DNA; reverse binding restores the DNA complex and frees inhibitor. | Encodes inhibitor competition as both catalytic blockade and PARP displacement. |
| 7 | Reversible source/sink | `mRNA_Bax` | Creates transcript basally at `s1` and removes it at `d1`. | Establishes basal Bax expression. |
| 8 | One-way source | Observable `p53_DNAbound` | Creates mRNA at `s2*p53_DNAbound²/(M²+p53_DNAbound²)`. | Converts p53 occupancy of damage into a saturating transcriptional response. |
| 9 | Reversible source/sink | Observable `mRNA_Bax`, free `Bax.b` | Creates Bax at `s4*mRNA_Bax` and removes it at `d2`. | Links transcription to the pro-apoptotic protein pool. |
| 10 | Reversible | `Bax.b`, `BclXL.b` | Creates or releases the inhibitory Bax–BclXL bond at `b1/u1`. | Buffers free Bax away from caspase activation. |
| 11 | One-way | Bax–BclXL complex | Removes bound Bax at `d2` and releases BclXL. | Recycles the anti-apoptotic binding capacity. |
| 12 | Reversible | Unphosphorylated `Bad.b`, `BclXL.b` | Creates or releases the Bad–BclXL bond at `b2/u2`. | Lets Bad displace the Bax-buffering role of BclXL. |
| 13 | Reversible | Free `Bad.S75_S99` | Changes Bad `0↔PP` at `p1*AKTtot` and `q1`. | Couples the binding competition to survival-kinase activity. |
| 14 | Reversible | Phosphorylated `Bad.b`, `Fourteen_3_3.b` | Creates or releases the Bad–14-3-3 bond at `b3/u3`. | Sequesters phosphorylated Bad away from BclXL. |
| 15 | One-way | BclXL-bound unphosphorylated Bad | AKT-dependent phosphorylation changes Bad `0→PP` and releases both partners. | Restores free BclXL when survival signaling is active. |
| 16 | One-way | 14-3-3-bound phosphorylated Bad | Dephosphorylation changes Bad `PP→0` and releases 14-3-3. | Returns Bad to the BclXL-competitive pool. |
| 17 | One-way source | `Caspase.csp=Pro` | Creates procaspase at `s3`. | Supplies substrate for the terminal activation switch. |
| 18 | One-way sink | Either caspase state | Removes caspase at `d3`. | Limits both proenzyme and active enzyme abundance. |
| 19 | One-way | `Caspase.csp=Pro`; `Bax_free`, `Caspase_act` observables | Changes procaspase `Pro→Act` at `a1*Bax_free + a2*Caspase_act²`. | Combines Bax initiation with autocatalytic amplification of apoptosis. |

## 7. Observables and technical readouts

| Observable(s) | Type | What is measured | Technical interpretation |
| --- | --- | --- | --- |
| `mRNA_Bax`, `Bax_free` | Molecule count | Bax transcript and unbound Bax. | These drive protein synthesis and the linear component of caspase activation, respectively. |
| `Caspase_act` | Molecule count | Active caspase. | Serves as both apoptotic output and the squared positive-feedback term in reaction 19. |
| `p53_DNAbound` | Molecule count | p53 engaged through its DNA site. | Drives the Hill transcription term; because the pattern only requires a bond, its partner is inferred from the available reaction topology. |
| `PARP_Inhbound` | Molecule count | Catalytically active PARP with inhibitor in its NAD pocket and no DNA bond required by the pattern. | Reports inhibited PARP produced by the displacement reaction, not total inhibitor or all PARP-bound complexes. |

## 8. Actions and simulation workflow

There is no active simulation workflow. The intended reactions imply an ODE-compatible concentration model, but the malformed block structure, undefined seed symbols, and absence of network-generation or simulation actions must be resolved before it can be executed.

## 9. Technical caveats and ambiguities

- The `parameters` block is never closed; reactions begin with `begin reactions` but end with both `end reaction rules` and `end reactions`. Standard BNGL expects a consistently named reaction-rule block.
- `BCLXtot` and `NADPtot` are undefined; the likely declared candidates are `BCLXLtot` and `NADtot`, but this summary does not silently substitute them.
- Metadata claims ODE and NFsim properties despite there being no active action and no currently parseable reaction-rule block.
- The same `b4/u4` rates are reused for p53 and PARP binding to damage, which is a modeling simplification rather than evidence of identical molecular affinities.
- With `AKTtot=0`, reactions 13 forward and 15 are inactive, biasing Bad toward its unphosphorylated BclXL-binding form.
