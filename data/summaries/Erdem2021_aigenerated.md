# Model Explanation: Erdem 2021

## 1. One-sentence summary

This model represents early insulin and IGF1 receptor signaling in MCF7 cells, including ligand binding, receptor phosphorylation, downstream adaptor signaling, feedback, and receptor recycling.

## 2. Biological meaning

This model represents early insulin and IGF1 receptor signaling in MCF7 cells, including ligand binding, receptor phosphorylation, downstream adaptor signaling, feedback, and receptor recycling. The local model comments and metadata give this context: CMM for MCF7 cell line 03/01/18 by Cemal ERDEM This is the BioNetGen model of early-stage signaling through InsR and IGF1R. Parameters are fit to RPPA data from MCF7 cells as described in the main text. To Run: Change the file extension from '.txt' to '.bngl' and use as input to BioNetGen. Details on BioNetGen can be found at bionetgen.org MODEL details: 1) IGF1-IGF1R and insulin-InsR binding only 2) ONE phospho sites at each receptor 3) NO basal phosphorylation 4) Rate parameters are in log10 5) FOUR observables. The explanation below is therefore based on the local BNGL model file `Published/Erdem2021/Erdem_2021.bngl` and metadata file `Published/Erdem2021/metadata.yaml`, not on remote URLs.

## 3. Main molecules, sites, and states

BNGL sites are named contact points or state variables on a molecule. A value after `~` is an internal state, such as phosphorylated/unphosphorylated, active/inactive, localized/nonlocalized, or another model-specific switch. Matching bond labels such as `!1` mean the two marked sites are connected in the same complex; a site without a bond label is free or unspecified.

- `IGF1`: IGF1. It has binding or interaction sites `rec`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `Ins`: Ins. It has binding or interaction sites `rec`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `IGF1R`: IGF1R. It has binding/interaction sites `lig` and regulated state sites `phos~U~P`, `int~N~Y`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `InsR`: InsR. It has binding/interaction sites `lig` and regulated state sites `phos~U~P`, `int~N~Y`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `IRS`: IRS. It has state sites `phos~U~P`, `inh~N~Y`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `SOS`: SOS. It has state sites `act~N~Y`, `inh~N~Y`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `Ras`: Ras. It has state sites `gtp~N~Y`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `Raf`: Raf. It has state sites `phos~U~P`, `inh~N~Y`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `MEK`: MEK. It has state sites `phos~U~P`, `inh~N~Y`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `PI3K`: PI3K. It has state sites `act~N~Y`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `PDK1`: PDK1. It has state sites `act~N~Y`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `TSC2`: TSC2. It has state sites `phos~U~P`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `mTOR`: mTOR. It has state sites `act~N~Y`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `Akt`: Akt. It has state sites `phos~U~P`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `RPS6K`: RPS6K. It has state sites `phos~U~P`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `ERK`: ERK. It has state sites `phos~U~P`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.

## 4. Initial conditions and model setup

The model starts from these encoded species or starting concentrations/copy numbers. Entries without `!` bond labels start as free molecules; entries with matching labels start as pre-assembled complexes.

- `IGF1(rec) IGF1_0`
- `Ins(rec) INS_0`
- `IGF1R(lig,phos~U,int~N) IGF1R_0`
- `InsR(lig,phos~U,int~N) INSR_0`
- `IRS(phos~U,inh~N) IRS_0`
- `SOS(act~N,inh~N) SOS_0`
- `Ras(gtp~N) RAS_0`
- `Raf(phos~U,inh~N) RAF_0`
- `MEK(phos~U,inh~N) MEK_0`
- `PI3K(act~N) PI3K_0`
- `PDK1(act~N) PDK1_0`
- `TSC2(phos~U) TSC2_0`
- `mTOR(act~N) MTOR_0`
- `Akt(phos~U) AKT_0`
- `RPS6K(phos~U) RPS6K_0`
- `ERK(phos~U) ERK_0`

Important parameters include:

- `IGF1_0 1e5`
- `INS_0 0`
- `IGF1R_0 25000.0`
- `INSR_0 25000.0`
- `IRS_0 92766.0`
- `SOS_0 90075.0`
- `RAS_0 230642.0`
- `RAF_0 126069.0`
- `MEK_0 1098164.0`
- `ERK_0 763172.0`
- `PI3K_0 64009.0`
- `PDK1_0 186081.0`
- `AKT_0 432907.0`
- `TSC2_0 131339.0`
- `MTOR_0 83469.0`
- `RPS6K_0 121978.0`
- `kf1		0.4837`
- `kf1b	-2.9153`
- `kf1c	2.9865`
- `kf1d	1.2052`
- `kf2		4.6312`
- `kf2b	-0.8667`
- `kf2c	4.8758`
- `kf2d	-2.6526`
- `kf3		-2.7913`

Functions and simulation/action commands:

- `generate_network({overwrite=>1})`
- `simulate({method=>"ode",t_start=>0,t_end=>1800,n_steps=>2e4})`
- `writeLatex()`
- `generate_network({overwrite=>1})`
- `writeLatex()`

## 5. Reaction rules in plain English

These rules are the biological mechanism of the model. When a product contains new matching `!` labels, two sites have become bound; when those labels disappear, a complex has separated. For reversible rules, the first listed rate is the forward rate and the second listed rate is the reverse rate.

- **Initial ligand-receptor binding**: Reversible binding/release. The nearby model comment says: “Initial ligand-receptor binding”. The rule involves `IGF1`, `IGF1R` and produces `IGF1`, `IGF1R`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `10^kf1, 10^kf1b`.
- **Initial ligand-receptor binding**: State change or catalytic conversion. The nearby model comment says: “Initial ligand-receptor binding”. The rule involves `IGF1R` and produces `IGF1R`. The encoded molecular change is site `phos` changes from `U` to `P`. Rate parameter(s): `10^kf1c`.
- **Initial ligand-receptor binding**: Unbinding or disassembly. The nearby model comment says: “Initial ligand-receptor binding”. The rule involves `IGF1R` and produces `IGF1R`. The encoded molecular change is site `phos` changes from `P` to `U`. Loss of matching `!` labels means a complex separates. Rate parameter(s): `10^kf1d`.
- **Initial ligand-receptor binding**: Reversible binding/release. The nearby model comment says: “Initial ligand-receptor binding”. The rule involves `Ins`, `InsR` and produces `Ins`, `InsR`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `10^kf2, 10^kf2b`.
- **Initial ligand-receptor binding**: State change or catalytic conversion. The nearby model comment says: “Initial ligand-receptor binding”. The rule involves `InsR` and produces `InsR`. The encoded molecular change is site `phos` changes from `U` to `P`. Rate parameter(s): `10^kf2c`.
- **Initial ligand-receptor binding**: Unbinding or disassembly. The nearby model comment says: “Initial ligand-receptor binding”. The rule involves `InsR` and produces `InsR`. The encoded molecular change is site `phos` changes from `P` to `U`. Loss of matching `!` labels means a complex separates. Rate parameter(s): `10^kf2d`.
- **pReceptor-IRS binding and activation**: State change or catalytic conversion. The nearby model comment says: “pReceptor-IRS binding and activation”. The rule involves `IGF1R`, `IRS` and produces `IGF1R`, `IRS`. The encoded molecular change is site `phos` changes from `U` to `P`. Rate parameter(s): `10^kf3`.
- **pReceptor-IRS binding and activation**: State change or catalytic conversion. The nearby model comment says: “pReceptor-IRS binding and activation”. The rule involves `IRS`, `InsR` and produces `IRS`, `InsR`. The encoded molecular change is site `phos` changes from `U` to `P`. Rate parameter(s): `10^kf4`.
- **pReceptor-SOS binding and activation**: State change or catalytic conversion. The nearby model comment says: “pReceptor-SOS binding and activation”. The rule involves `IGF1R`, `SOS` and produces `IGF1R`, `SOS`. The encoded molecular change is site `act` changes from `N` to `Y`. Rate parameter(s): `10^kf5`.
- **pReceptor-SOS binding and activation**: State change or catalytic conversion. The nearby model comment says: “pReceptor-SOS binding and activation”. The rule involves `InsR`, `SOS` and produces `InsR`, `SOS`. The encoded molecular change is site `act` changes from `N` to `Y`. Rate parameter(s): `10^kf6`.
- **SOS activation by IRS1**: State change or catalytic conversion. The nearby model comment says: “SOS activation by IRS1”. The rule involves `IRS`, `SOS` and produces `IRS`, `SOS`. The encoded molecular change is site `act` changes from `N` to `Y`. Rate parameter(s): `10^kf7`.
- **Ras activation by SOS**: State change or catalytic conversion. The nearby model comment says: “Ras activation by SOS”. The rule involves `Ras`, `SOS` and produces `Ras`, `SOS`. The encoded molecular change is site `gtp` changes from `N` to `Y`. Rate parameter(s): `10^kf8`.
- **Raf activation by Ras**: State change or catalytic conversion. The nearby model comment says: “Raf activation by Ras”. The rule involves `Raf`, `Ras` and produces `Raf`, `Ras`. The encoded molecular change is site `phos` changes from `U` to `P`. Rate parameter(s): `10^kf9`.
- **MEK activation by Raf**: State change or catalytic conversion. The nearby model comment says: “MEK activation by Raf”. The rule involves `MEK`, `Raf` and produces `MEK`, `Raf`. The encoded molecular change is site `phos` changes from `U` to `P`. Rate parameter(s): `10^kf10`.
- **ERK activation by MEK**: State change or catalytic conversion. The nearby model comment says: “ERK activation by MEK”. The rule involves `ERK`, `MEK` and produces `ERK`, `MEK`. The encoded molecular change is site `phos` changes from `U` to `P`. Rate parameter(s): `10^kf11`.
- **PI3K activation by IRS1**: State change or catalytic conversion. The nearby model comment says: “PI3K activation by IRS1”. The rule involves `IRS`, `PI3K` and produces `IRS`, `PI3K`. The encoded molecular change is site `act` changes from `N` to `Y`. Rate parameter(s): `10^kf12`.
- **PDK1 activation PI3K**: State change or catalytic conversion. The nearby model comment says: “PDK1 activation PI3K”. The rule involves `PDK1`, `PI3K` and produces `PDK1`, `PI3K`. The encoded molecular change is site `act` changes from `N` to `Y`. Rate parameter(s): `10^kf13`.
- **Akt activation by PDK1**: State change or catalytic conversion. The nearby model comment says: “Akt activation by PDK1”. The rule involves `Akt`, `PDK1` and produces `Akt`, `PDK1`. The encoded molecular change is site `phos` changes from `U` to `P`. Rate parameter(s): `10^kf14`.
- **TSC2 inactivation by Akt**: State change or catalytic conversion. The nearby model comment says: “TSC2 inactivation by Akt”. The rule involves `Akt`, `TSC2` and produces `Akt`, `TSC2`. The encoded molecular change is site `phos` changes from `U` to `P`. Rate parameter(s): `10^kf15`.
- **mTOR activation by inactive TSC2**: State change or catalytic conversion. The nearby model comment says: “mTOR activation by inactive TSC2”. The rule involves `TSC2`, `mTOR` and produces `TSC2`, `mTOR`. The encoded molecular change is site `act` changes from `N` to `Y`. Rate parameter(s): `10^kf16`.
- **RPS6K activation by mTOR**: State change or catalytic conversion. The nearby model comment says: “RPS6K activation by mTOR”. The rule involves `RPS6K`, `mTOR` and produces `RPS6K`, `mTOR`. The encoded molecular change is site `phos` changes from `U` to `P`. Rate parameter(s): `10^kf17`.
- **De-phosphorylation (-P) events**: State change or catalytic conversion. The nearby model comment says: “De-phosphorylation (-P) events”. The rule involves `IRS` and produces `IRS`. The encoded molecular change is `IRS` site `phos` changes from `P` to `U`; site `phos` changes from `P` to `U`. Rate parameter(s): `10^kf101`.
- **De-phosphorylation (-P) events**: State change or catalytic conversion. The nearby model comment says: “De-phosphorylation (-P) events”. The rule involves `SOS` and produces `SOS`. The encoded molecular change is `SOS` site `act` changes from `Y` to `N`; site `act` changes from `Y` to `N`. Rate parameter(s): `10^kf102`.
- **De-phosphorylation (-P) events**: State change or catalytic conversion. The nearby model comment says: “De-phosphorylation (-P) events”. The rule involves `Ras` and produces `Ras`. The encoded molecular change is `Ras` site `gtp` changes from `Y` to `N`; site `gtp` changes from `Y` to `N`. Rate parameter(s): `10^kf103`.
- **De-phosphorylation (-P) events**: State change or catalytic conversion. The nearby model comment says: “De-phosphorylation (-P) events”. The rule involves `Raf` and produces `Raf`. The encoded molecular change is `Raf` site `phos` changes from `P` to `U`; site `phos` changes from `P` to `U`. Rate parameter(s): `10^kf104`.
- **De-phosphorylation (-P) events**: State change or catalytic conversion. The nearby model comment says: “De-phosphorylation (-P) events”. The rule involves `MEK` and produces `MEK`. The encoded molecular change is `MEK` site `phos` changes from `P` to `U`; site `phos` changes from `P` to `U`. Rate parameter(s): `10^kf105`.
- **De-phosphorylation (-P) events**: State change or catalytic conversion. The nearby model comment says: “De-phosphorylation (-P) events”. The rule involves `PI3K` and produces `PI3K`. The encoded molecular change is `PI3K` site `act` changes from `Y` to `N`; site `act` changes from `Y` to `N`. Rate parameter(s): `10^kf106`.
- **De-phosphorylation (-P) events**: State change or catalytic conversion. The nearby model comment says: “De-phosphorylation (-P) events”. The rule involves `PDK1` and produces `PDK1`. The encoded molecular change is `PDK1` site `act` changes from `Y` to `N`; site `act` changes from `Y` to `N`. Rate parameter(s): `10^kf107`.
- **De-phosphorylation (-P) events**: State change or catalytic conversion. The nearby model comment says: “De-phosphorylation (-P) events”. The rule involves `TSC2` and produces `TSC2`. The encoded molecular change is `TSC2` site `phos` changes from `P` to `U`; site `phos` changes from `P` to `U`. Rate parameter(s): `10^kf108`.
- **De-phosphorylation (-P) events**: State change or catalytic conversion. The nearby model comment says: “De-phosphorylation (-P) events”. The rule involves `mTOR` and produces `mTOR`. The encoded molecular change is `mTOR` site `act` changes from `Y` to `N`; site `act` changes from `Y` to `N`. Rate parameter(s): `10^kf109`.
- **De-phosphorylation (-P) events**: State change or catalytic conversion. The nearby model comment says: “De-phosphorylation (-P) events”. The rule involves `Akt` and produces `Akt`. The encoded molecular change is `Akt` site `phos` changes from `P` to `U`; site `phos` changes from `P` to `U`. Rate parameter(s): `10^kf110`.
- **De-phosphorylation (-P) events**: State change or catalytic conversion. The nearby model comment says: “De-phosphorylation (-P) events”. The rule involves `RPS6K` and produces `RPS6K`. The encoded molecular change is `RPS6K` site `phos` changes from `P` to `U`; site `phos` changes from `P` to `U`. Rate parameter(s): `10^kf111`.
- **De-phosphorylation (-P) events**: State change or catalytic conversion. The nearby model comment says: “De-phosphorylation (-P) events”. The rule involves `ERK` and produces `ERK`. The encoded molecular change is `ERK` site `phos` changes from `P` to `U`; site `phos` changes from `P` to `U`. Rate parameter(s): `10^kf112`.
- **SOS inactivation by pERK**: State change or catalytic conversion. The nearby model comment says: “SOS inactivation by pERK”. The rule involves `ERK`, `SOS` and produces `ERK`, `SOS`. The encoded molecular change is site `inh` changes from `N` to `Y`. Rate parameter(s): `10^kf201`.
- **MEK inactivation by pERK**: State change or catalytic conversion. The nearby model comment says: “MEK inactivation by pERK”. The rule involves `ERK`, `MEK` and produces `ERK`, `MEK`. The encoded molecular change is site `inh` changes from `N` to `Y`. Rate parameter(s): `10^kf202`.
- **IRS1 inhibition by pRPS6K**: State change or catalytic conversion. The nearby model comment says: “IRS1 inhibition by pRPS6K”. The rule involves `IRS`, `RPS6K` and produces `IRS`, `RPS6K`. The encoded molecular change is site `inh` changes from `N` to `Y`. Rate parameter(s): `10^kf203`.
- **Raf inactivation by pAkt**: State change or catalytic conversion. The nearby model comment says: “Raf inactivation by pAkt”. The rule involves `Akt`, `Raf` and produces `Akt`, `Raf`. The encoded molecular change is site `inh` changes from `N` to `Y`. Rate parameter(s): `10^kf204`.
- **IRS inactivation by pERK**: State change or catalytic conversion. The nearby model comment says: “IRS inactivation by pERK”. The rule involves `ERK`, `IRS` and produces `ERK`, `IRS`. The encoded molecular change is site `inh` changes from `N` to `Y`. Rate parameter(s): `10^kf206`.
- **Akt inactivation by pERK**: State change or catalytic conversion. The nearby model comment says: “Akt inactivation by pERK”. The rule involves `Akt`, `ERK` and produces `Akt`, `ERK`. The encoded molecular change is site `phos` changes from `P` to `U`. Rate parameter(s): `10^kf207`.
- **IRS inactivation by pAkt**: State change or catalytic conversion. The nearby model comment says: “IRS inactivation by pAkt”. The rule involves `Akt`, `IRS` and produces `Akt`, `IRS`. The encoded molecular change is site `inh` changes from `N` to `Y`. Rate parameter(s): `10^kf208`.
- **### Re-sensitization**: State change or catalytic conversion. The nearby model comment says: “### Re-sensitization”. The rule involves `IRS` and produces `IRS`. The encoded molecular change is `IRS` site `inh` changes from `Y` to `N`; site `inh` changes from `Y` to `N`. Rate parameter(s): `10^kf301`.
- **### Re-sensitization**: State change or catalytic conversion. The nearby model comment says: “### Re-sensitization”. The rule involves `SOS` and produces `SOS`. The encoded molecular change is `SOS` site `inh` changes from `Y` to `N`; site `inh` changes from `Y` to `N`. Rate parameter(s): `10^kf302`.
- **### Re-sensitization**: State change or catalytic conversion. The nearby model comment says: “### Re-sensitization”. The rule involves `Raf` and produces `Raf`. The encoded molecular change is `Raf` site `inh` changes from `Y` to `N`; site `inh` changes from `Y` to `N`. Rate parameter(s): `10^kf303`.
- **### Re-sensitization**: State change or catalytic conversion. The nearby model comment says: “### Re-sensitization”. The rule involves `MEK` and produces `MEK`. The encoded molecular change is `MEK` site `inh` changes from `Y` to `N`; site `inh` changes from `Y` to `N`. Rate parameter(s): `10^kf304`.
- **# Recepter recycling**: State change or catalytic conversion. The nearby model comment says: “# Recepter recycling”. The rule involves `IGF1R` and produces `IGF1R`. The encoded molecular change is `IGF1R` site `int` changes from `N` to `Y`; site `int` changes from `N` to `Y`. Rate parameter(s): `10^kf401`.
- **# Recepter recycling**: Unbinding or disassembly. The nearby model comment says: “# Recepter recycling”. The rule involves `IGF1`, `IGF1R` and produces `IGF1R`. The encoded molecular change is `IGF1R` site `int` changes from `Y` to `N`; site `int` changes from `Y` to `N`; site `phos` changes from `P` to `U`. Loss of matching `!` labels means a complex separates. Rate parameter(s): `10^kf402`.
- **# Recepter recycling**: State change or catalytic conversion. The nearby model comment says: “# Recepter recycling”. The rule involves `InsR` and produces `InsR`. The encoded molecular change is `InsR` site `int` changes from `N` to `Y`; site `int` changes from `N` to `Y`. Rate parameter(s): `10^kf403`.
- **# Recepter recycling**: Unbinding or disassembly. The nearby model comment says: “# Recepter recycling”. The rule involves `Ins`, `InsR` and produces `InsR`. The encoded molecular change is `InsR` site `int` changes from `Y` to `N`; site `int` changes from `Y` to `N`; site `phos` changes from `P` to `U`. Loss of matching `!` labels means a complex separates. Rate parameter(s): `10^kf404`.

## 6. Observables and expected simulation output

Observables define what the simulator records. They are measurements of matching molecule patterns, complexes, or states, not claims that a particular trajectory must occur.

- `pRecTot_free` (Species) tracks phosphorylated/modified molecules. Pattern: `IGF1R(int~N,phos~P),InsR(int~N,phos~P)`.
- `pAkt308_free` (Species) tracks phosphorylated/modified molecules. Pattern: `Akt(phos~P)`.
- `pRPS6K_free` (Species) tracks phosphorylated/modified molecules. Pattern: `RPS6K(phos~P)`.
- `pERK_free` (Species) tracks phosphorylated/modified molecules. Pattern: `ERK(phos~P)`.

Given these observables, plots from the model would show how the named signaling species, complexes, modified states, or coarse-grained variables change over the simulated time course under the listed initial conditions and rates.

## 7. Metadata, source, and compatibility

- Model id: `Erdem_2021`
- Title/name: `Erdem 2021`
- Category: `signaling`
- Tags: `['published', 'erdem', '2021', 'igf1', 'ins', 'igf1r', 'insr', 'irs', 'sos', 'ras', 'raf']`
- Source origin: `published`
- Original repository: `bionetgen-web-simulator`
- Original format: `bngl`
- Metadata source path: `published-models/complex-models/Erdem_2021.bngl`
- Local BNGL file used: `Published/Erdem2021/Erdem_2021.bngl`
- Local YAML file used: `Published/Erdem2021/metadata.yaml`
- Compatibility: bng2 = `false`, NFsim = `false`, methods = `['ode']`
- Playground: visible = `false`, featured = `false`, difficulty = `advanced`

## 8. Caveats or missing information

- This is a local, syntax-based explanation of the model and metadata; it does not validate the biological correctness of the publication model or reproduce simulations.
- Abbreviated molecule names are expanded only when the metadata, comments, or widely used biological abbreviation makes the identity clear; otherwise the BNGL name is preserved.
- Some large models contain many related binding/phosphorylation/dephosphorylation rules. Repetitive families are explained by their encoded biological event and nearby BNGL comments rather than by dumping raw BNGL syntax.
