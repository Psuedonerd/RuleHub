# Coder Model Explanation: Ligon 2014

## 1. Model identity and scope

- **Model id:** `Ligon_2014`
- **Title:** Ligon 2014
- **BNGL path:** `Published/Ligon2014/Ligon_2014.bngl`
- **YAML path:** `Published/Ligon2014/metadata.yaml`
- **Metadata description:** Lipoplex delivery
- **Scope:** This NFsim-oriented model tracks external lipoplexes (`Lext`) attaching to pit/endosome carrier sites (`Pit.l1` through `Pit.l10`), pit-to-endosome conversion through `Pit.s p→e`, lysis into internal lipoplexes (`Lint`) with cargo-number state `n`, unpacking into population `mRNA`, translation to population `GFP`, degradation into `Trash`, and a `Timer` population that switches on washout through the `wash` function.

## 2. BNGL block inventory

| Block | Present? | Count / role |
| --- | --- | --- |
| Parameters | Yes | 11 kinetic/control parameters for attachment, endocytosis, lysis, unpacking, translation, wash/degradation, and fast cleanup. |
| Compartments | No | No BNGL compartment block; external/internal/endosome distinctions are encoded as molecule names and `Pit.s` states. |
| Anchors | No | No anchors. |
| Molecule types | Yes | 8 molecule types, including population types for `mRNA`, `GFP`, `I`, and `Timer`. |
| Seed/species | Yes | 16 seed species: 11 `Lext` cargo-number states, one pit, and population/readout species. |
| Observables | Yes | 7 active observables. |
| Functions | Yes | 1 function, `wash`, controlled by `TimerCount`. |
| Reaction rules | Yes | 33 active rules; many higher-occupancy expansions are commented out and excluded. |
| Actions | Yes | One `simulate_nf` command. |

## 3. Parameters, functions, and rate laws

| Parameter | Value/expression | Technical role |
| --- | --- | --- |
| `kFast` | `1e20` | Declared but not used by active rules. |
| `kA` | `0.016*3600` | Lipoplex attachment rate to pit slots `l1`-`l7`. |
| `kE` | `0.45*3600` | Pit-to-endosome conversion rate for occupied pits; rules use `DeleteMolecules`. |
| `kL` | `0.4*3600` | Endosome lysis rate converting bound external lipoplex cargo to internal `Lint`. |
| `kU` | `0.4*3600` | Unpacking rate converting `Lint(n~345/346)` to five `mRNA` population increments. |
| `kTL` | `100.0*3600` | Translation rate: `mRNA -> mRNA + GFP`. |
| `dW` | `0` | Wash parameter declared but not used; active wash uses function `wash`. |
| `dM` | `0.051*3600` | mRNA degradation to `Trash`. |
| `dG` | `0.056*3600` | GFP degradation to `Trash`. |
| `dL` | `0.01*3600` | Internal lipoplex degradation to `Trash`. |
| `dE` | `1.0*3600` | Empty endosome degradation to `Trash`. |

| Function | Technical interpretation |
| --- | --- |
| `wash = if(TimerCount>3600,1e20,0)` | Wash rate is zero until the `TimerCount` observable exceeds 3600, then external `Lext` is sent to `Trash` at a very large rate. |

## 4. Molecule types, sites, and states

| Molecule type | Site count | Sites/components | Internal states | Anchor/allowed compartments | Binding/modification roles | Notes |
| --- | ---: | --- | --- | --- | --- | --- |
| `Lext` | 2 | `p`, `n` | `n`: `345`-`355` | none | `p` binds a pit slot; `n` stores cargo-number state. | External lipoplex. Active rules use `n~345`-`355` for lysis and `p` bonds to pit slots. |
| `Pit` | 11 | `s`, `l1`-`l10` | `s`: `p`, `e` | none | `s` distinguishes pit/endosome; `l1`-`l10` are lipoplex attachment slots. | Active attachment rules fill `l1` through `l7`; active endocytosis rules cover one through five occupied slots. |
| `Lint` | 1 | `n` | `n`: `345`-`355` | none | Internal cargo state; no binding site. | Product of endosome lysis. |
| `mRNA` | 0 | population molecule | none | none | Population count species. | Produced by unpacking and preserved during translation. |
| `GFP` | 0 | population molecule | none | none | Population count species. | Produced from mRNA and degraded to Trash. |
| `Trash` | 0 | none | none | none | Sink species. | Receives washed/degraded material. |
| `I` | 0 | population molecule | none | none | Timer catalyst/source. | Preserved while producing `Timer`. |
| `Timer` | 0 | population molecule | none | none | Timer count for wash function. | Drives `wash` indirectly through observable `TimerCount`. |

## 5. Compartments, anchors, initial species, and setup

No compartments or anchors are declared. Initial `Lext` is distributed across cargo states `n~345` through `n~355` with counts `1,2,6,12,18,20,18,12,6,3,1`. One empty pit starts in state `Pit.s~p` with all ten `l` slots free. `mRNA`, `GFP`, and `Timer` start at zero; `I` starts at one and catalytically produces timer population.

## 6. Complete reaction-rule inventory

**Rule-family orientation:** Rules 2-8 sequentially add external lipoplexes to pit slots `l1`-`l7`; each new `Lext.p` site bonds to the next open `Pit.l*` site. Rules 9-13 convert occupied pits to endosomes by changing `Pit.s p→e` while preserving existing `Lext.p`/`Pit.l*` bonds and using `DeleteMolecules`. Rules 15-26 lyse endosomes and discard the pit/bonds while creating internal `Lint` cargo states. Rules 28-29 unpack only `Lint.n~345` and `Lint.n~346` in the active source.

| # | Rule label/name | Direction | Participants and sites/components | Rate/expression | Exact modeled change | Technical meaning |
| ---: | --- | --- | --- | --- | --- | --- |
| 1 | `Unlabeled` | one-way | `Lext.p`, `Lext.n` | `wash` | `Lext(p,n) → Trash`; no pit bond required. | Removes any external lipoplex after the timer-gated wash turns on. |
| 2 | `Unlabeled` | one-way | free `Lext.p` + free `Pit.l1`, `Pit.s~p` | `kA` | Forms `Lext.p!1`–`Pit.l1!1`; also creates a new free `Pit(s~p,...)` product. | First lipoplex attaches to slot `l1`; the extra free pit product in the rule is a source-like amplification term in the active BNGL. |
| 3 | `Unlabeled` | one-way | free `Lext.p` + open `Pit.l2` on a pit already carrying `l1!1` | `kA` | Forms `Lext.p!2`–`Pit.l2!2`; preserves the existing `l1!1` bond. | Adds a second lipoplex to slot `l2`. |
| 4 | `Unlabeled` | one-way | free `Lext.p` + open `Pit.l3` on a two-lipoplex pit | `kA` | Forms `Lext.p!3`–`Pit.l3!3`; preserves `l1!1,l2!2`. | Adds a third lipoplex to slot `l3`. |
| 5 | `Unlabeled` | one-way | free `Lext.p` + open `Pit.l4` | `kA` | Forms `Lext.p!4`–`Pit.l4!4`; preserves earlier slot bonds. | Adds a fourth lipoplex to slot `l4`. |
| 6 | `Unlabeled` | one-way | free `Lext.p` + open `Pit.l5` | `kA` | Forms `Lext.p!5`–`Pit.l5!5`. | Adds a fifth lipoplex to slot `l5`. |
| 7 | `Unlabeled` | one-way | free `Lext.p` + open `Pit.l6` | `kA` | Forms `Lext.p!6`–`Pit.l6!6`. | Adds a sixth lipoplex to slot `l6`. |
| 8 | `Unlabeled` | one-way | free `Lext.p` + open `Pit.l7` | `kA` | Forms `Lext.p!7`–`Pit.l7!7`. | Adds a seventh lipoplex to slot `l7`; higher slot rules are commented out. |
| 9 | `Unlabeled` | one-way | one-lipoplex pit: `Lext.p!1`–`Pit.l1!1`, `Pit.s~p` | `kE DeleteMolecules` | `Pit.s p→e`; preserves `l1!1`; deletes unmatched molecules from the reactant complex context. | Converts a one-lipoplex pit into an endosome. |
| 10 | `Unlabeled` | one-way | two-lipoplex pit: bonds at `l1!1,l2!2`, `Pit.s~p` | `kE DeleteMolecules` | `Pit.s p→e`; preserves bonds at `l1,l2`. | Converts a two-lipoplex pit into an endosome. |
| 11 | `Unlabeled` | one-way | three-lipoplex pit: bonds at `l1!1,l2!2,l3!3` | `kE DeleteMolecules` | `Pit.s p→e`; preserves bonds at `l1`-`l3`. | Converts a three-lipoplex pit into an endosome. |
| 12 | `Unlabeled` | one-way | four-lipoplex pit: bonds at `l1!1`-`l4!4` | `kE DeleteMolecules` | `Pit.s p→e`; preserves bonds at `l1`-`l4`. | Converts a four-lipoplex pit into an endosome. |
| 13 | `Unlabeled` | one-way | five-lipoplex pit: bonds at `l1!1`-`l5!5` | `kE DeleteMolecules` | `Pit.s p→e`; preserves bonds at `l1`-`l5`. | Converts a five-lipoplex pit into an endosome; the source comments say five more endocytosis rules would be needed. |
| 14 | `Unlabeled` | one-way | empty `Pit.s~e` with all `l1`-`l10` free | `dE` | `Pit(s~e, free slots) → Trash`. | Degrades an empty endosome. |
| 15 | `Unlabeled` | one-way | `Lext.p!1,n~345` bound to `Pit.s~e,l1!1` | `kL` | Releases/deletes the endosome complex and creates `Lint(n~345)`. | Lyses a one-lipoplex endosome carrying `n~345`. |
| 16 | `Unlabeled` | one-way | `Lext.p!1,n~346` bound to `Pit.s~e,l1!1` | `kL` | Creates `Lint(n~346)`. | Lyses a one-lipoplex endosome carrying `n~346`. |
| 17 | `Unlabeled` | one-way | `Lext.p!1,n~347` bound to `Pit.s~e,l1!1` | `kL` | Creates `Lint(n~347)`. | Lyses a one-lipoplex endosome carrying `n~347`. |
| 18 | `Unlabeled` | one-way | `Lext.p!1,n~348` bound to `Pit.s~e,l1!1` | `kL` | Creates `Lint(n~348)`. | Lyses a one-lipoplex endosome carrying `n~348`. |
| 19 | `Unlabeled` | one-way | `Lext.p!1,n~349` bound to `Pit.s~e,l1!1` | `kL` | Creates `Lint(n~349)`. | Lyses a one-lipoplex endosome carrying `n~349`. |
| 20 | `Unlabeled` | one-way | `Lext.p!1,n~350` bound to `Pit.s~e,l1!1` | `kL` | Creates `Lint(n~350)`. | Lyses a one-lipoplex endosome carrying `n~350`. |
| 21 | `Unlabeled` | one-way | `Lext.p!1,n~351` bound to `Pit.s~e,l1!1` | `kL` | Creates `Lint(n~351)`. | Lyses a one-lipoplex endosome carrying `n~351`. |
| 22 | `Unlabeled` | one-way | `Lext.p!1,n~352` bound to `Pit.s~e,l1!1` | `kL` | Creates `Lint(n~352)`. | Lyses a one-lipoplex endosome carrying `n~352`. |
| 23 | `Unlabeled` | one-way | `Lext.p!1,n~353` bound to `Pit.s~e,l1!1` | `kL` | Creates `Lint(n~353)`. | Lyses a one-lipoplex endosome carrying `n~353`. |
| 24 | `Unlabeled` | one-way | `Lext.p!1,n~354` bound to `Pit.s~e,l1!1` | `kL` | Creates `Lint(n~354)`. | Lyses a one-lipoplex endosome carrying `n~354`. |
| 25 | `Unlabeled` | one-way | `Lext.p!1,n~355` bound to `Pit.s~e,l1!1` | `kL` | Creates `Lint(n~355)`. | Lyses a one-lipoplex endosome carrying `n~355`. |
| 26 | `Unlabeled` | one-way | two `Lext` molecules both `n~345`, bound at `Pit.l1!1` and `Pit.l2!2` in an endosome | `kL` | Creates two `Lint(n~345)` products; pit/endosome complex is consumed. | Special two-lipoplex lysis case for the `345/345` cargo-state pair only. |
| 27 | `Unlabeled` | one-way | `Lint` any `n` state | `dL` | `Lint → Trash`. | Degrades internal lipoplex cargo regardless of `n` state. |
| 28 | `Unlabeled` | one-way | `Lint.n~345` | `kU` | `Lint(n~345) → 5 mRNA`. | Unpacks an internal `n~345` lipoplex into five population mRNA increments, not 345 mRNA. |
| 29 | `Unlabeled` | one-way | `Lint.n~346` | `kU` | `Lint(n~346) → 5 mRNA`. | Unpacks an internal `n~346` lipoplex into five mRNA increments; other `n` states have no active unpacking rule. |
| 30 | `Unlabeled` | one-way | population `mRNA` | `dM` | `mRNA → Trash`. | Degrades one mRNA population unit. |
| 31 | `Unlabeled` | one-way | population `mRNA` | `kTL` | `mRNA → mRNA + GFP`. | Translates GFP while preserving the mRNA population unit. |
| 32 | `Unlabeled` | one-way | population `GFP` | `dG` | `GFP → Trash`. | Degrades GFP. |
| 33 | `Unlabeled` | one-way | population `I` | `1` | `I → I + Timer`. | Preserves timer source `I` and increments `Timer`, which eventually activates `wash`. |

## 7. Observables and technical readouts

| Observable | Type | Pattern / target | Technical interpretation |
| --- | --- | --- | --- |
| `Lext` | `Molecules` | `Lext(p,n)` | Counts external lipoplex molecules with unbound `p` and any declared `n` state. Bound `Lext(p!*,n)` is not matched by this exact free-site pattern. |
| `Pit` | `Molecules` | `Pit(s~p)` | Counts pit-state `Pit` molecules regardless of slot occupancy. |
| `Endo` | `Molecules` | `Pit(s~e)` | Counts endosome-state `Pit` molecules. |
| `Lint` | `Molecules` | `Lint()` | Counts internal lipoplex molecules across all `n` states. |
| `mRNA` | `Molecules` | `mRNA` | Counts mRNA population units. |
| `GFP` | `Molecules` | `GFP` | Counts GFP population units. |
| `TimerCount` | `Molecules` | `Timer` | Counts timer population units and feeds the `wash` function. |

## 8. Actions and simulation workflow

`simulate_nf({suffix=>nf,t_end=>30*3600,n_steps=>300});` runs an NFsim simulation for 30 hours of model time with 300 output steps. The commented `writeXML()` is inactive.

## 9. Technical caveats and ambiguities

- The active rule set is deliberately incomplete relative to the comments: higher pit occupancies, many lysis combinations, and most unpacking states are commented out or summarized by comments rather than active BNGL rules.
- Rule 2 creates an additional free `Pit` product while binding the first lipoplex; this is unusual and should be verified against the intended delivery model.
- Population declarations make this NFsim-oriented; some standalone deterministic workflows may not treat population species the same way.
- `dW` and `kFast` are declared but not used by active rules.
