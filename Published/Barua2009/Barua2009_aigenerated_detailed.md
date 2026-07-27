# Detailed Model Explanation: Barua 2009 JAK2–SH2B cooperative activation model

## 1. Model overview

This model uses SH2B as a dimeric scaffold that recruits two JAK2 molecules through phosphorylated docking sites. Once the two kinases share that scaffold, phosphorylation of the first JAK2 is slow and phosphorylation of the second is tenfold faster, producing cooperative activation.

## 2. BNGL block inventory

The file contains 8 parameters, 2 molecule types, 2 initial species, 4 rules, 6 observables, and 2 actions. It has no model wrapper, compartments, anchors, or functions; network generation limits complexes to two JAK2 molecules.

## 3. Parameters, functions, and rate laws

The model uses two reversible binding pairs and two context-dependent phosphorylation rates. All kinetics are direct mass action, and the only nonlinearity emerges from assembling the required two-JAK2 complex.

| Parameter group or names | Function in this model |
| --- | --- |
| `kon_SH2`, `koff_SH2` | Association/dissociation of phosphorylated JAK2 `Y1` with the SH2B `SH2` domain. |
| `kon_dimer`, `koff_dimer` | Association/dissociation of two SH2B `DD` domains, creating the central dimeric scaffold. |
| `kphos_slow`, `kphos_fast` | Phosphorylation of a JAK2 `Y` site when the partner JAK2 is unphosphorylated or already phosphorylated; the latter rate is tenfold higher. |
| `Jtot`, `Stot` | Initial JAK2 and SH2B concentrations. SH2B is present in large excess over JAK2. |

There are no functions.

## 4. Molecule types, sites, and states

| Molecule type(s) | Site count | Sites/components | Internal states | Anchor/allowed compartments | Explanation |
| --- | ---: | --- | --- | --- | --- |
| `S` | 2 | `SH2`, `DD` | None | None | SH2B-like adaptor: `SH2` captures JAK2 `Y1~P`, and `DD` dimerizes two adaptors to hold a JAK2 pair. |
| `J` | 2 | `Y1`, `Y` | `Y1: P` only; `Y: U, P` | None | JAK2-like kinase with a constitutively available phospho-docking site (`Y1`) and a regulated activation site (`Y`). |

## 5. Compartments, anchors, initial species, and setup

The model is nonspatial. It starts with free SH2B and JAK2 whose `Y1` docking site is already phosphorylated but whose regulated `Y` site is unphosphorylated. No adaptor dimers or kinase complexes are seeded, so the complete JAK2–SH2B–SH2B–JAK2 assembly must form before either phosphorylation rule can fire.

## 6. Reaction-rule inventory

**Rule-family orientation.** Rules 1–2 construct the two-kinase scaffold; rules 3–4 phosphorylate its JAK2 pair in a slow-first, fast-second sequence.

| Rule number(s) | Direction | Involved molecules/sites | Exact modeled change and rate logic | Role within the model |
| ---: | --- | --- | --- | --- |
| 1 | Reversible | JAK2 `Y1~P` and SH2B `SH2` | Creates/releases the `Y1–SH2` bond at `kon_SH2/koff_SH2`; JAK2 `Y` is unconstrained. | Recruits each kinase to an adaptor without changing kinase activation. |
| 2 | Reversible | Two SH2B `DD` sites | Creates/releases the adaptor `DD–DD` bond at `kon_dimer/koff_dimer`. | Joins two recruited JAK2–SH2B units into the geometry required for cross-activation. |
| 3 | One-way | Complete JAK2–SH2B dimer with both JAK2 `Y~U` | Changes one JAK2 `Y: U → P` at `kphos_slow`, retaining every scaffold bond and leaving the partner unmodified. | Initiates activation slowly in a fully assembled but inactive kinase pair. |
| 4 | One-way | Same complete scaffold with one JAK2 `Y~P` and the other `Y~U` | Changes the remaining JAK2 `Y: U → P` at `kphos_fast`. | Completes activation rapidly once the first phosphorylation has occurred, implementing positive cooperativity. |

## 7. Observables and technical readouts

| Observable(s) | Type | What is measured | Technical interpretation |
| --- | --- | --- | --- |
| `J_mono` | Molecule count | All JAK2 with the constitutive `Y1~P` state | Effectively a total-JAK2 check, not a strict monomer count, because `Y1` bonding is unconstrained. |
| `JS`, `JSS`, `JSSJ` | Molecule count | One recruited adaptor, a JAK2-bound SH2B dimer, or any complex containing two JAK2 molecules | Stepwise assembly readouts from initial recruitment to the two-kinase scaffold. |
| `J_active`, `J_inactive` | Molecule count | JAK2 with regulated `Y~P` or `Y~U` | Activation-state partition used to see the slow/fast phosphorylation sequence. |

## 8. Actions and simulation workflow

The file generates a network capped at two JAK2 molecules per species and then runs a sparse ODE simulation to time 10,000 with 10,000 output steps. No equilibration or stimulus change precedes the run.

## 9. Technical caveats and ambiguities

- `Y1` is declared only in state `P`; the model cannot represent creation or loss of the SH2B docking phosphate.
- `J_mono` is named as a monomer readout but does not require JAK2 to be unbound.
- `JSSJ` detects two JAK2 molecules without constraining either activation state.
- The ODE action uses `atoll` rather than the usual `atol`, which may be parser-sensitive.
