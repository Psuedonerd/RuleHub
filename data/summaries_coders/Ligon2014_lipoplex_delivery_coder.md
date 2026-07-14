# Coder Model Explanation: Ligon 2014

## 1. Model identity and scope

- **Model id:** `Ligon_2014`
- **Title:** Ligon 2014
- **BNGL path:** `Published/Ligon2014/Ligon_2014.bngl`
- **YAML path:** `Published/Ligon2014/metadata.yaml`
- **Metadata description:** Lipoplex delivery
- **Scope:** A lipoplex delivery model that tracks external lipoplex attachment to pits, conversion of pits to endosomes, lysis/unpacking into internal lipoplex cargo, mRNA production, GFP translation, washout, degradation, and a timer species for wash control.

## 2. BNGL block inventory

| Block | Present? | Count / role |
| --- | --- | --- |
| Parameters | Yes | 11 parameter entries. |
| Compartments | No | 0 compartment entries. |
| Anchors | No | 0 anchor entries. |
| Molecule types | Yes | 8 molecule type entries. |
| Seed/species | Yes | 16 initial species entries. |
| Observables | Yes | 7 observable entries. |
| Functions | Yes | 1 function entries. |
| Reaction rules | Yes | 33 reaction rules. |
| Actions | Yes | 1 active action or inline execution commands. |

## 3. Parameters, functions, and rate laws

The parameter table is complete for this small model and preserves source comments when available.

| Parameter | Value/expression | Role / source comment |
| --- | --- | --- |
| `kFast` | `1e20` | kinetic or model-control parameter |
| `kA` | `0.016*3600` | attach |
| `kE` | `0.45*3600` | endocytosis |
| `kL` | `0.4*3600` | lyse endosome |
| `kU` | `0.4*3600` | unpack lipoplex |
| `kTL` | `100.0*3600` | translate |
| `dW` | `0` | wash (degrade external lipoplexes) |
| `dM` | `0.051*3600` | delta mRNA degradation |
| `dG` | `0.056*3600` | beta GFP degradation |
| `dL` | `0.01*3600` | lipoplex degradation |
| `dE` | `1.0*3600` | endosome degradation |

**Functions and derived rates**

| Function | Technical interpretation |
| --- | --- |
| `wash = if(TimerCount>3600,1e20,0)` | derived rate/readout expression used by rules, observables, or simulation output |

## 4. Molecule types, sites, and states

| Molecule type | Site count | Sites/components | Internal states | Anchor/allowed compartments | Binding/modification roles | Notes |
| --- | ---: | --- | --- | --- | --- | --- |
| `Lext` | 2 | p, n~345~346~347~348~349~350~351~352~353~354~355 | n: 345, 346, 347, 348, 349, 350, 351, 352, 353, 354, 355 | none | binding/modification candidate sites: p |  |
| `Pit` | 11 | s~p~e, l1, l2, l3, l4, l5, l6, l7, l8, l9, l10 | s: p, e | none | binding/modification candidate sites: l1, l2, l3, l4, l5, l6, l7, l8, l9, l10 | pit now has flag fpr pit vs. endosome |
| `Lint` | 1 | n~345~346~347~348~349~350~351~352~353~354~355 | n: 345, 346, 347, 348, 349, 350, 351, 352, 353, 354, 355 | none | no explicit binding/modification site role beyond whole-molecule abundance |  |
| `mRNA population` | 0 | none declared | none declared | none | ambiguous | raw molecule type declaration could not be parsed |
| `GFP population` | 0 | none declared | none declared | none | ambiguous | raw molecule type declaration could not be parsed |
| `Trash` | 0 | none declared | none declared | none | ambiguous | raw molecule type declaration could not be parsed |
| `I population` | 0 | none declared | none declared | none | ambiguous | raw molecule type declaration could not be parsed |
| `Timer population` | 0 | none declared | none declared | none | ambiguous | raw molecule type declaration could not be parsed |

## 5. Compartments, anchors, initial species, and setup

- Compartments: none declared.

- Anchors: none declared.

| Initial species/pattern | Initial amount | Setup role |
| --- | --- | --- |
| `Lext(p,n~345)` | `1` | starting species pool for this pattern |
| `Lext(p,n~346)` | `2` | starting species pool for this pattern |
| `Lext(p,n~347)` | `6` | starting species pool for this pattern |
| `Lext(p,n~348)` | `12` | starting species pool for this pattern |
| `Lext(p,n~349)` | `18` | starting species pool for this pattern |
| `Lext(p,n~350)` | `20` | starting species pool for this pattern |
| `Lext(p,n~351)` | `18` | starting species pool for this pattern |
| `Lext(p,n~352)` | `12` | starting species pool for this pattern |
| `Lext(p,n~353)` | `6` | starting species pool for this pattern |
| `Lext(p,n~354)` | `3` | starting species pool for this pattern |
| `Lext(p,n~355)` | `1` | starting species pool for this pattern |
| `Pit(s~p,l1,l2,l3,l4,l5,l6,l7,l8,l9,l10)` | `1` | starting species pool for this pattern |
| `mRNA` | `0` | starting species pool for this pattern |
| `GFP` | `0` | starting species pool for this pattern |
| `I` | `1` | starting species pool for this pattern |
| `Timer` | `0` | starting species pool for this pattern |

## 6. Complete reaction-rule inventory

The source contains **33** reaction rules. Every concrete rule is listed below.

| # | Rule label/name | Direction | Participants and sites/components | Rate/expression | Modeled change | Rule pattern | Technical meaning |
| ---: | --- | --- | --- | --- | --- | --- | --- |
| 1 | `Unlabeled` | one-way | Lext, Trash | `wash` | stoichiometric pattern rewrite | `Lext(p,n) -> Trash` | degrade external lipoplex (washing). Produces Trash while retaining or consuming Lext. Rate/expression: wash. |
| 2 | `Unlabeled` | one-way | Lext, Pit | `kA` | binding-pattern rewrite | `Lext(p,n) + Pit(s~p,l1,l2,l3,l4,l5,l6,l7,l8,l9,l10) -> Lext(p!1,n).Pit(s~p,l1!1,l2,l3,l4,l5,l6,l7,l8,l9,l10) + Pit(s~p,l1,l2,l3,l4,l5,l6,l7,l8,l9,l10)` | attach - external lipoplex attaches to clathrin-coated pit. Forms binding contacts among Lext, Pit through Lext.p, Pit.l1. Rate/expression: kA. |
| 3 | `Unlabeled` | one-way | Lext, Pit | `kA` | binding-pattern rewrite | `Lext(p,n) + Lext(p!1,n).Pit(s~p,l1!1,l2,l3,l4,l5,l6,l7,l8,l9,l10) -> Lext(p!2,n).Lext(p!1,n).Pit(s~p,l1!1,l2!2,l3,l4,l5,l6,l7,l8,l9,l10)` | Forms binding contacts among Lext, Pit through Pit.l2. Rate/expression: kA. |
| 4 | `Unlabeled` | one-way | Lext, Pit | `kA` | binding-pattern rewrite | `Lext(p,n) + Lext(p!2,n).Lext(p!1,n).Pit(s~p,l1!1,l2!2,l3,l4,l5,l6,l7,l8,l9,l10) -> Lext(p!3,n).Lext(p!2,n).Lext(p!1,n).Pit(s~p,l1!1,l2!2,l3!3,l4,l5,l6,l7,l8,l9,l10)` | Forms binding contacts among Lext, Pit through Pit.l3. Rate/expression: kA. |
| 5 | `Unlabeled` | one-way | Lext, Pit | `kA` | binding-pattern rewrite | `Lext(p,n) + Lext(p!3,n).Lext(p!2,n).Lext(p!1,n).Pit(s~p,l1!1,l2!2,l3!3,l4,l5,l6,l7,l8,l9,l10) -> Lext(p!4,n).Lext(p!3,n).Lext(p!2,n).Lext(p!1,n).Pit(s~p,l1!1,l2!2,l3!3,l4!4,l5,l6,l7,l8,l9,l10)` | Forms binding contacts among Lext, Pit through Pit.l4. Rate/expression: kA. |
| 6 | `Unlabeled` | one-way | Lext, Pit | `kA` | binding-pattern rewrite | `Lext(p,n) + Lext(p!4,n).Lext(p!3,n).Lext(p!2,n).Lext(p!1,n).Pit(s~p,l1!1,l2!2,l3!3,l4!4,l5,l6,l7,l8,l9,l10) -> Lext(p!5,n).Lext(p!4,n).Lext(p!3,n).Lext(p!2,n).Lext(p!1,n).Pit(s~p,l1!1,l2!2,l3!3,l4!4,l5!5,l6,l7,l8,l9,l10)` | Forms binding contacts among Lext, Pit through Pit.l5. Rate/expression: kA. |
| 7 | `Unlabeled` | one-way | Lext, Pit | `kA` | binding-pattern rewrite | `Lext(p,n) + Lext(p!5,n).Lext(p!4,n).Lext(p!3,n).Lext(p!2,n).Lext(p!1,n).Pit(s~p,l1!1,l2!2,l3!3,l4!4,l5!5,l6,l7,l8,l9,l10) -> Lext(p!6,n).Lext(p!5,n).Lext(p!4,n).Lext(p!3,n).Lext(p!2,n).Lext(p!1,n).Pit(s~p,l1!1,l2!2,l3!3,l4!4,l5!5,l6!6,l7,l8,l9,l10)` | Forms binding contacts among Lext, Pit through Pit.l6. Rate/expression: kA. |
| 8 | `Unlabeled` | one-way | Lext, Pit | `kA` | binding-pattern rewrite | `Lext(p,n) + Lext(p!6,n).Lext(p!5,n).Lext(p!4,n).Lext(p!3,n).Lext(p!2,n).Lext(p!1,n).Pit(s~p,l1!1,l2!2,l3!3,l4!4,l5!5,l6!6,l7,l8,l9,l10) -> Lext(p!7,n).Lext(p!6,n).Lext(p!5,n).Lext(p!4,n).Lext(p!3,n).Lext(p!2,n).Lext(p!1,n).Pit(s~p,l1!1,l2!2,l3!3,l4!4,l5!5,l6!6,l7!7,l8,l9,l10)` | Forms binding contacts among Lext, Pit through Pit.l7. Rate/expression: kA. |
| 9 | `Unlabeled` | one-way | Lext, Pit | `kE (DeleteMolecules)` | internal-state conversion/modification | `Lext(p!1,n).Pit(s~p,l1!1,l2,l3,l4,l5,l6,l7,l8,l9,l10) -> Lext(p!1,n).Pit(s~e,l1!1,l2,l3,l4,l5,l6,l7,l8,l9,l10)` | endocytosis - pit is converted to endosome. Explicit cleanup/removal rule: after matching Lext, Pit, the listed product pattern remains and deleted components are removed. Rate/expression: kE (DeleteMolecules). |
| 10 | `Unlabeled` | one-way | Lext, Pit | `kE (DeleteMolecules)` | internal-state conversion/modification | `Lext(p!2,n).Lext(p!1,n).Pit(s~p,l1!1,l2!2,l3,l4,l5,l6,l7,l8,l9,l10) -> Lext(p!2,n).Lext(p!1,n).Pit(s~e,l1!1,l2!2,l3,l4,l5,l6,l7,l8,l9,l10)` | Explicit cleanup/removal rule: after matching Lext, Pit, the listed product pattern remains and deleted components are removed. Rate/expression: kE (DeleteMolecules). |
| 11 | `Unlabeled` | one-way | Lext, Pit | `kE (DeleteMolecules)` | internal-state conversion/modification | `Lext(p!3,n).Lext(p!2,n).Lext(p!1,n).Pit(s~p,l1!1,l2!2,l3!3,l4,l5,l6,l7,l8,l9,l10) -> Lext(p!3,n).Lext(p!2,n).Lext(p!1,n).Pit(s~e,l1!1,l2!2,l3!3,l4,l5,l6,l7,l8,l9,l10)` | Explicit cleanup/removal rule: after matching Lext, Pit, the listed product pattern remains and deleted components are removed. Rate/expression: kE (DeleteMolecules). |
| 12 | `Unlabeled` | one-way | Lext, Pit | `kE (DeleteMolecules)` | internal-state conversion/modification | `Lext(p!4,n).Lext(p!3,n).Lext(p!2,n).Lext(p!1,n).Pit(s~p,l1!1,l2!2,l3!3,l4!4,l5,l6,l7,l8,l9,l10) -> Lext(p!4,n).Lext(p!3,n).Lext(p!2,n).Lext(p!1,n).Pit(s~e,l1!1,l2!2,l3!3,l4!4,l5,l6,l7,l8,l9,l10)` | Explicit cleanup/removal rule: after matching Lext, Pit, the listed product pattern remains and deleted components are removed. Rate/expression: kE (DeleteMolecules). |
| 13 | `Unlabeled` | one-way | Lext, Pit | `kE (DeleteMolecules)` | internal-state conversion/modification | `Lext(p!5,n).Lext(p!4,n).Lext(p!3,n).Lext(p!2,n).Lext(p!1,n).Pit(s~p,l1!1,l2!2,l3!3,l4!4,l5!5,l6,l7,l8,l9,l10) -> Lext(p!5,n).Lext(p!4,n).Lext(p!3,n).Lext(p!2,n).Lext(p!1,n).Pit(s~e,l1!1,l2!2,l3!3,l4!4,l5!5,l6,l7,l8,l9,l10)` | Explicit cleanup/removal rule: after matching Lext, Pit, the listed product pattern remains and deleted components are removed. Rate/expression: kE (DeleteMolecules). |
| 14 | `Unlabeled` | one-way | Pit, Trash | `dE` | stoichiometric pattern rewrite | `Pit(s~e,l1,l2,l3,l4,l5,l6,l7,l8,l9,l10) -> Trash` | 5 more endocytosis reactions needed; endosome degradation. Produces Trash while retaining or consuming Pit. Rate/expression: dE. |
| 15 | `Unlabeled` | one-way | Lext, Lint, Pit | `kL` | binding-pattern rewrite | `Lext(p!1,n~345).Pit(s~e,l1!1,l2,l3,l4,l5,l6,l7,l8,l9,l10) -> Lint(n~345)` | the following reactions hit combinatorial complexity, but would be OK if it were possible to use the state of the reactant in the product; !! lysis of endosome with 1 lipoplex - 11 reactions. Releases binding contacts among Lext, Lint, Pit by freeing Lext.p, Pit.l1. Rate/expression: kL. |
| 16 | `Unlabeled` | one-way | Lext, Lint, Pit | `kL` | binding-pattern rewrite | `Lext(p!1,n~346).Pit(s~e,l1!1,l2,l3,l4,l5,l6,l7,l8,l9,l10) -> Lint(n~346)` | Releases binding contacts among Lext, Lint, Pit by freeing Lext.p, Pit.l1. Rate/expression: kL. |
| 17 | `Unlabeled` | one-way | Lext, Lint, Pit | `kL` | binding-pattern rewrite | `Lext(p!1,n~347).Pit(s~e,l1!1,l2,l3,l4,l5,l6,l7,l8,l9,l10) -> Lint(n~347)` | Releases binding contacts among Lext, Lint, Pit by freeing Lext.p, Pit.l1. Rate/expression: kL. |
| 18 | `Unlabeled` | one-way | Lext, Lint, Pit | `kL` | binding-pattern rewrite | `Lext(p!1,n~348).Pit(s~e,l1!1,l2,l3,l4,l5,l6,l7,l8,l9,l10) -> Lint(n~348)` | Releases binding contacts among Lext, Lint, Pit by freeing Lext.p, Pit.l1. Rate/expression: kL. |
| 19 | `Unlabeled` | one-way | Lext, Lint, Pit | `kL` | binding-pattern rewrite | `Lext(p!1,n~349).Pit(s~e,l1!1,l2,l3,l4,l5,l6,l7,l8,l9,l10) -> Lint(n~349)` | Releases binding contacts among Lext, Lint, Pit by freeing Lext.p, Pit.l1. Rate/expression: kL. |
| 20 | `Unlabeled` | one-way | Lext, Lint, Pit | `kL` | binding-pattern rewrite | `Lext(p!1,n~350).Pit(s~e,l1!1,l2,l3,l4,l5,l6,l7,l8,l9,l10) -> Lint(n~350)` | Releases binding contacts among Lext, Lint, Pit by freeing Lext.p, Pit.l1. Rate/expression: kL. |
| 21 | `Unlabeled` | one-way | Lext, Lint, Pit | `kL` | binding-pattern rewrite | `Lext(p!1,n~351).Pit(s~e,l1!1,l2,l3,l4,l5,l6,l7,l8,l9,l10) -> Lint(n~351)` | Releases binding contacts among Lext, Lint, Pit by freeing Lext.p, Pit.l1. Rate/expression: kL. |
| 22 | `Unlabeled` | one-way | Lext, Lint, Pit | `kL` | binding-pattern rewrite | `Lext(p!1,n~352).Pit(s~e,l1!1,l2,l3,l4,l5,l6,l7,l8,l9,l10) -> Lint(n~352)` | Releases binding contacts among Lext, Lint, Pit by freeing Lext.p, Pit.l1. Rate/expression: kL. |
| 23 | `Unlabeled` | one-way | Lext, Lint, Pit | `kL` | binding-pattern rewrite | `Lext(p!1,n~353).Pit(s~e,l1!1,l2,l3,l4,l5,l6,l7,l8,l9,l10) -> Lint(n~353)` | Releases binding contacts among Lext, Lint, Pit by freeing Lext.p, Pit.l1. Rate/expression: kL. |
| 24 | `Unlabeled` | one-way | Lext, Lint, Pit | `kL` | binding-pattern rewrite | `Lext(p!1,n~354).Pit(s~e,l1!1,l2,l3,l4,l5,l6,l7,l8,l9,l10) -> Lint(n~354)` | Releases binding contacts among Lext, Lint, Pit by freeing Lext.p, Pit.l1. Rate/expression: kL. |
| 25 | `Unlabeled` | one-way | Lext, Lint, Pit | `kL` | binding-pattern rewrite | `Lext(p!1,n~355).Pit(s~e,l1!1,l2,l3,l4,l5,l6,l7,l8,l9,l10) -> Lint(n~355)` | Releases binding contacts among Lext, Lint, Pit by freeing Lext.p, Pit.l1. Rate/expression: kL. |
| 26 | `Unlabeled` | one-way | Lext, Lint, Pit | `kL` | binding-pattern rewrite | `Lext(p!2,n~345).Lext(p!1,n~345).Pit(s~e,l1!1,l2!2,l3,l4,l5,l6,l7,l8,l9,l10) -> Lint(n~345) + Lint(n~345)` | !! lysis of endosome with 2 lipoplexes - 11^2 reactions. Releases binding contacts among Lext, Lint, Pit by freeing Lext.p, Pit.l1, Pit.l2. Rate/expression: kL. |
| 27 | `Unlabeled` | one-way | Lint, Trash | `dL` | stoichiometric pattern rewrite | `Lint -> Trash` | lysis of endosome with 10 lipoplexes - 11^10 reactions; lipoplex degradation. Converts internal lipoplex cargo into Trash/degraded material. Rate/expression: dL. |
| 28 | `Unlabeled` | one-way | Lint, mRNA | `kU` | stoichiometric pattern rewrite | `Lint(n~345) -> mRNA+mRNA+mRNA+mRNA+mRNA` | !! unpacking of lipoplex - 11 reactions with sum of 345 to 355 elements. Produces mRNA while retaining or consuming Lint. Rate/expression: kU. |
| 29 | `Unlabeled` | one-way | Lint, mRNA | `kU` | stoichiometric pattern rewrite | `Lint(n~346) -> mRNA+mRNA+mRNA+mRNA+mRNA` | Produces mRNA while retaining or consuming Lint. Rate/expression: kU. |
| 30 | `Unlabeled` | one-way | Trash, mRNA | `dM` | stoichiometric pattern rewrite | `mRNA -> Trash` | mRNA degradation. Produces Trash while retaining or consuming mRNA. Rate/expression: dM. |
| 31 | `Unlabeled` | one-way | GFP, mRNA | `kTL` | stoichiometric pattern rewrite | `mRNA -> mRNA + GFP` | translation. Produces GFP while retaining or consuming mRNA. Rate/expression: kTL. |
| 32 | `Unlabeled` | one-way | GFP, Trash | `dG` | stoichiometric pattern rewrite | `GFP -> Trash` | GFP degradation. Produces Trash while retaining or consuming GFP. Rate/expression: dG. |
| 33 | `Unlabeled` | one-way | I, Timer | `1` | stoichiometric pattern rewrite | `I -> I + Timer` | Produces Timer while retaining or consuming I. Rate/expression: 1. |

## 7. Observables and technical readouts

| Observable | Type | Pattern / target | Technical interpretation |
| --- | --- | --- | --- |
| `Lext` | `Molecules` | `Lext(p,n)` | counts molecule-pattern matches |
| `Pit` | `Molecules` | `Pit(s~p)` | counts molecule-pattern matches |
| `Endo` | `Molecules` | `Pit(s~e)` | counts molecule-pattern matches |
| `Lint` | `Molecules` | `Lint()` | counts molecule-pattern matches |
| `mRNA` | `Molecules` | `mRNA` | counts molecule-pattern matches |
| `GFP` | `Molecules` | `GFP` | counts molecule-pattern matches |
| `TimerCount` | `Molecules` | `Timer` | counts molecule-pattern matches |

## 8. Actions and simulation workflow

1. `simulate_nf({suffix=>nf,t_end=>30*3600,n_steps=>300});` — active execution command in the actions block

## 9. Technical caveats and ambiguities

- The source intentionally comments out several higher-occupancy attachment/lysis expansions and notes combinatorial complexity; the summary inventories only active concrete rules.

- Population molecule declarations are used for mRNA, GFP, I, and Timer, which is important for NFsim-oriented execution.

- No formal compartments are declared; pit/endosome/internal/external distinctions are encoded as molecule names and Pit.s internal states rather than BNGL compartment blocks.
