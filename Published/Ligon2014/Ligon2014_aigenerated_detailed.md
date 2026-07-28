# Detailed Model Explanation: Ligon 2014 Lipoplex Delivery

## 1. Model overview

This model follows extracellular lipoplexes as they load sequentially into pits, enter an endosomal state, release internal cargo, and produce green fluorescent protein (GFP). It combines a distribution of lipoplex cargo sizes with an explicit uptake-capacity mechanism, but implements only a deliberately limited subset of the possible multi-particle release and unpacking reactions.

## 2. BNGL block inventory

The model contains 11 parameters, 8 molecule types (including four population types), 16 seed species, 1 function, 33 active reaction rules, 7 molecule-count observables, and 1 network-free simulation action. It has no compartments or anchors; extracellular, pit, endosomal, and internal status are represented by molecule identity or internal state.

## 3. Parameters, functions, and rate laws

Rates are named by process and are converted from per-second source values to per-hour values where the factor `3600` appears. Rules otherwise use mass-action rates, except for the time-dependent wash function.

| Parameter group or names | Function in this model |
| --- | --- |
| `kA`, `kE` | Control successive lipoplex capture by a pit and conversion of a loaded pit to an endosome, respectively. |
| `kL`, `kU` | Set endosomal lysis/cargo release and conversion of selected internal lipoplexes into messenger RNA (mRNA). |
| `kTL` | Controls catalytic GFP production by mRNA; the mRNA is retained during translation. |
| `dE`, `dL` | Remove empty endosomes and internal lipoplexes. |
| `dM`, `dG` | Set turnover of the mRNA and fluorescent reporter pools. |
| `kFast`, `dW` | Declared but unused by active rules; washing is instead governed by `wash`. |

| Function | Inputs/dependencies | Meaning and use in this model |
| --- | --- | --- |
| `wash` | `TimerCount` | Returns zero until the timer exceeds 3,600 counts, then returns an extremely large removal rate. Rule 1 uses this as an abrupt delayed wash of extracellular lipoplex. |

## 4. Molecule types, sites, and states

| Molecule type(s) | Site count | Sites/components | Internal states | Anchor/allowed compartments | Explanation |
| --- | ---: | --- | --- | --- | --- |
| `Lext` | 2 | `p`, `n` | `n`: 345–355 | None | An extracellular lipoplex; `p` binds a pit slot and `n` records its cargo-size class. |
| `Pit` | 11 | `s`; `l1`–`l10` | `s`: pit (`p`) or endosome (`e`) | None | A ten-slot uptake carrier whose state distinguishes surface capture from internalized cargo. |
| `Lint` | 1 | `n` | `n`: 345–355 | None | Released intracellular lipoplex, retaining the cargo-size class of its extracellular precursor. |
| `mRNA`, `GFP` | 0 each | None | Population types | None | Coarse-grained cargo transcript and translated fluorescent output. |
| `I`, `Timer` | 0 each | None | Population types | None | `I` is a persistent clock catalyst; `Timer` accumulates one unit at a time and triggers washing. |
| `Trash` | 0 | None | None | None | Sink receiving washed or degraded material. |

## 5. Compartments, anchors, initial species, and setup

There are no explicit compartments or anchors. The extracellular input is distributed over cargo classes 345–355 with a peaked abundance centered near 350, while one empty pit starts in the surface-pit state. The internal lipoplex, mRNA, GFP, and timer pools start at zero; a single `I` population particle drives timer accumulation.

## 6. Reaction-rule inventory

**Rule-family orientation.** Rules 1–8 govern exposure and pit loading, rules 9–14 internalize or clear pits, rules 15–27 release and remove internal cargo, and rules 28–33 turn a small implemented subset of that cargo into the fluorescent readout.

| Rule number(s) | Direction | Involved molecules/sites | Exact modeled change and rate logic | Role within the model |
| ---: | --- | --- | --- | --- |
| 1 | One-way | `Lext`; timer-dependent `wash` | Sends any extracellular lipoplex to `Trash` at the conditional wash rate. | Terminates further uptake after the modeled exposure period. |
| 2–8 | One-way | `Lext.p`; `Pit.l1`–`l7` in state `s=p` | Adds one lipoplex to the next free pit slot at `kA`; rules 2–8 fill `l1` through `l7`, respectively. Rule 2 also produces an additional empty pit. | Builds pit occupancy stepwise while preserving the cargo class of every captured lipoplex. |
| 9–13 | One-way | Loaded `Pit` with `l1` through `l1`–`l5` occupied | Changes `Pit.s` from `p` to `e` at `kE` for occupancy levels one through five; `DeleteMolecules` applies to unmatched context. | Internalizes explicitly represented low-occupancy pits as endosomes. |
| 14 | One-way | Empty `Pit` with `s=e` | Removes an unoccupied endosome to `Trash` at `dE`. | Clears endosomal carriers that contain no lipoplex. |
| 15–25 | One-way | One `Lext` bound at `Pit.l1`; cargo state 345–355 | Consumes the one-particle endosome and creates the matching `Lint.n` class at `kL`; rules 15–25 map states 345–355, respectively. | Represents endosomal escape while retaining cargo-size identity. |
| 26 | One-way | Two `Lext` particles of class 345 at `Pit.l1,l2` | Consumes the two-particle endosome and releases two class-345 internal lipoplexes at `kL`. | Supplies the sole implemented example of multi-particle endosomal lysis. |
| 27 | One-way | `Lint` | Sends any internal lipoplex class to `Trash` at `dL`. | Competes with productive unpacking and limits intracellular cargo persistence. |
| 28–29 | One-way | `Lint.n=345` or `346` | Consumes one selected internal lipoplex and creates five mRNA population units at `kU`. | Implements productive unpacking only for two cargo classes, with a five-transcript yield rather than the numeric state value. |
| 30 | One-way | `mRNA` | Removes mRNA to `Trash` at `dM`. | Limits the duration of reporter production. |
| 31 | One-way | `mRNA`, `GFP` | Retains mRNA while adding one GFP unit at `kTL`. | Converts delivered cargo into the measured fluorescent signal. |
| 32 | One-way | `GFP` | Removes GFP to `Trash` at `dG`. | Gives the reporter a finite lifetime. |
| 33 | One-way | `I`, `Timer` | Retains `I` and creates Timer at unit rate. | Provides the internal clock used by the delayed wash function. |

## 7. Observables and technical readouts

| Observable(s) | Type | What is measured | Technical interpretation |
| --- | --- | --- | --- |
| `Lext` | Molecule count | Extracellular lipoplex molecules across cargo classes and binding states. | Reports material remaining outside or associated with pits before internal conversion. |
| `Pit`, `Endo` | Molecule count | `Pit` molecules in surface (`p`) and endosomal (`e`) states. | Separates capture carriers from internalized carriers, independent of their occupancy. |
| `Lint` | Molecule count | All released internal lipoplex classes. | Measures cargo that escaped an endosome but has not unpacked or degraded. |
| `mRNA`, `GFP` | Molecule count | Population units of transcript and fluorescent protein. | These are the productive-delivery intermediate and final reporter, not explicit molecular complexes. |
| `TimerCount` | Molecule count | Accumulated Timer population. | Directly controls when `wash` switches on. |

## 8. Actions and simulation workflow

The model runs a 30-hour network-free simulation with 300 output intervals. Network-free simulation avoids enumerating the pit-loading combinatorics, while the timer generated during the same run switches on extracellular clearance after 3,600 timer units.

## 9. Technical caveats and ambiguities

- Pit loading is active only through seven of ten slots, and endocytosis is active only for one-to-five-particle pits; the higher-occupancy variants are absent or commented out.
- Complete lysis would require cargo-class combinations for every occupancy. Only all one-particle classes and one two-particle class are active.
- Productive unpacking exists only for cargo states 345 and 346, and both yield five mRNA units; the declared numeric cargo state should therefore not be read as the implemented transcript yield.
- Rule 2 creates a second empty pit as well as the loaded pit, so the pit pool can expand during first capture.
- The metadata and README disagree about BNG2 compatibility; the active workflow is explicitly network-free.
