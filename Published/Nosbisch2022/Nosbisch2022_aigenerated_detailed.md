# Detailed Model Explanation: Nosbisch 2022 RTK–PLCγ1 activation model

## 1. Model overview

This model follows phospholipase C gamma 1 (PLCγ1) recruitment to a phosphorylated receptor tyrosine kinase (RTK), phosphorylation of PLCγ1 Tyr783, and rearrangement of its inhibitory intramolecular contacts. Receptor binding and a time-gated background pathway activate the PLCγ1 core, while dephosphorylation, contact re-formation, and core inactivation return it toward the resting state.

## 2. BNGL block inventory

The model has 1 three-dimensional compartment, an empty parameters block, 2 molecule types, 2 seed species, 9 observables, an empty functions block, 12 labeled rules, and 1 network-generation action. It has no anchors and no simulation action.

## 3. Parameters, functions, and rate laws

Most rules use literal first-order or association rates. Two rules use time-dependent Boolean expressions intended to turn off at `t = 5000`, and one of them multiplies that gate by `kact_p`, which is not declared locally.

| Parameter group or names | Function in this model |
| --- | --- |
| Literal association rates `1000.0` and `100.0` | Drive fast active-PLCγ1 recruitment to RTK and rapid formation of inhibitory or Tyr783–cSH2 intramolecular contacts. |
| Literal transition rates `10.0`, `1.0`, and `0.1` | Control receptor-bound core activation, most bond/state reversals, and slow spontaneous core inactivation, respectively. |
| Time gate `(t < 5000)` | Limits inactive PLCγ1 recruitment in `r01` and background activation in `r11` to the early phase, assuming the parser evaluates the comparison numerically. |
| `kact_p` | Scales the gated background activation rule `r11`, but no value is declared in the BNGL file. |

There are no active functions despite the empty functions block.

## 4. Molecule types, sites, and states

| Molecule type(s) | Site count | Sites/components | Internal states | Anchor/allowed compartments | Explanation |
| --- | ---: | --- | --- | --- | --- |
| `RTK` | 1 | `pY` | None | `cell` | A receptor represented only by a phosphotyrosine docking site for PLCγ1 `nSH2`; receptor phosphorylation itself is not modeled as a state transition. |
| `PLCgamma1` | 4 | `nSH2`, `Tyr783`, `cSH2`, `core` | `Tyr783: u, p`; `core: inactive, active` | `cell` | The signaling protein: `nSH2` docks to RTK, Tyr783 is phosphorylated/dephosphorylated, `cSH2` forms alternative intramolecular contacts, and `core` records catalytic activation. |

## 5. Compartments, anchors, initial species, and setup

All species occupy one unit-volume, three-dimensional `cell` compartment; there are no anchors or transport rules. RTK begins free at 0.05, while PLCγ1 begins at 0.02 in an inactive, Tyr783-unphosphorylated conformation whose `cSH2` and `core` sites are internally bonded. Thus the initial PLCγ1 pool must first open or be activated before it can explore all modeled contacts.

## 6. Reaction-rule inventory

**Rule-family orientation.** Rules `r01`–`r05` cover receptor docking and Tyr783 modification. Rules `r06`–`r09` exchange the resting cSH2–core contact for a phospho-Tyr783–cSH2 contact. Rules `r10`–`r12` govern activation and deactivation of the PLCγ1 core.

| Rule number(s) | Direction | Involved molecules/sites | Exact modeled change and rate logic | Role within the model |
| ---: | --- | --- | --- | --- |
| `r02` | One-way | RTK `pY`; active PLCγ1 `nSH2` | Creates the RTK-pY–PLCγ1-nSH2 bond at `1000.0`; no PLCγ1 state changes. | Rapidly captures already-active PLCγ1 at the receptor. |
| `r01` | One-way | RTK `pY`; inactive PLCγ1 `nSH2`; any existing bond on `core` is allowed | Creates the same receptor–nSH2 bond only while `(t < 5000)` evaluates true. | Restricts recruitment of inactive PLCγ1 to the intended early stimulation window. |
| `r03` | One-way | RTK-bound PLCγ1 through `pY–nSH2` | Releases the receptor–nSH2 bond at `1.0`. | Returns both proteins to their free docking states and opposes `r01`/`r02`. |
| `r04` | One-way | RTK-bound PLCγ1 with `Tyr783~u`, regardless of a Tyr783 bond | Changes `Tyr783: u → p` at `1.0` while retaining receptor binding. | Couples receptor residence to phosphorylation of the PLCγ1 regulatory tyrosine. |
| `r05` | One-way | Any PLCγ1 with unbound `Tyr783~p` | Changes `Tyr783: p → u` at `1.0`. | Removes the phosphotyrosine signal, but cannot act while Tyr783 is engaged with cSH2. |
| `r06` | One-way | Inactive PLCγ1 with an internal `cSH2–core` bond | Breaks the cSH2–core bond at `1.0`; the core remains inactive. | Opens the resting autoinhibitory contact without directly activating the core. |
| `r07` | One-way | Inactive PLCγ1 with free `cSH2` and `core` | Re-forms the internal cSH2–core bond at `100.0`. | Strongly favors restoration of the closed resting conformation. |
| `r08` | One-way | PLCγ1 with phosphorylated, free Tyr783 and free cSH2 | Creates an intramolecular Tyr783-p–cSH2 bond at `100.0`. | Lets phosphorylated Tyr783 sequester cSH2 away from the inhibitory core contact. |
| `r09` | One-way | PLCγ1 containing the Tyr783-p–cSH2 bond | Releases that intramolecular bond at `1.0` without dephosphorylating Tyr783. | Reopens both sites so cSH2 can rebind the core or Tyr783 can be dephosphorylated. |
| `r10` | One-way | RTK-bound PLCγ1 with inactive core | Changes `core: inactive → active` at `10.0`; receptor binding remains intact. | Makes receptor recruitment a direct activation route. |
| `r11` | One-way | Cytosolic PLCγ1 with free nSH2 and inactive core | Changes `core: inactive → active` at `(t < 5000) * kact_p`. | Provides a receptor-independent, early-phase activation route whose strength depends on the missing `kact_p`. |
| `r12` | One-way | Any PLCγ1 with active core | Changes `core: active → inactive` at `0.1`. | Supplies basal signal termination regardless of receptor or intramolecular-contact state. |

## 7. Observables and technical readouts

| Observable(s) | Type | What is measured | Technical interpretation |
| --- | --- | --- | --- |
| `O0_RTK_tot`, `O0_PLCgamma1_tot` | Molecule count | All RTK or all PLCγ1 molecules in `cell` | Conservation checks for the two molecular pools. |
| `O0_PLCgamma1_active`, `O0_PLCgamma1_inactive` | Molecule count | PLCγ1 grouped by core state, independent of whether the core site is bonded | The principal activation-state readouts; together they partition the PLCγ1 pool by core activity. |
| `O0_PLCgamma1_pTyr783`, `O0_PLCgamma1_dpTyr783` | Molecule count | Phosphorylated or unphosphorylated Tyr783, with either bond status | Reports the regulatory-tyrosine cycle separately from core activation. |
| `O0_PLCgamma1_RTK_bound_inactive` | Molecule count | Inactive PLCγ1 joined from nSH2 to RTK pY | Isolates the recruited-but-not-yet-activated intermediate consumed by `r10`. |
| `O0_PLCgamma1_RTK_bound` | Molecule count | Any PLCγ1 joined to RTK through nSH2 | Total receptor recruitment, irrespective of Tyr783 or core state. |
| `O0_PLCgamma1_cytosol` | Molecule count | Inactive PLCγ1 with free nSH2 | Operational “cytosolic” pool; because there is only one compartment, this means receptor-unbound rather than a distinct spatial location. |

## 8. Actions and simulation workflow

The file generates a bounded reaction network with at most seven iterations, aggregate size 10, and up to 100 copies each of RTK and PLCγ1. It does not run a simulation; an external workflow must supply `kact_p`, select a simulator, and integrate across the `t = 5000` gate if that syntax is supported.

## 9. Technical caveats and ambiguities

- `kact_p` is referenced but undeclared, so `r11` cannot be assigned a numerical rate from this file alone.
- The comparison expression in `r01` is itself placed in the rate position; support for Boolean-valued time expressions is parser-dependent.
- Metadata claims ODE support even though the file contains only network generation and the compatibility record marks BNG2 as false.
- “Cytosol” is an observable name, not a separate compartment.
- The initial cSH2–core bond is intramolecular; summaries or visualizers that treat it as an intermolecular complex would misread the setup.
