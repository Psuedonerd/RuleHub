# Model Explanation: Hlavacek 1999

## 1. One-sentence summary

This model represents how steric hindrance reduces multivalent ligand binding as bound receptors occupy ligand surface area.

## 2. Biological meaning

This model represents how steric hindrance reduces multivalent ligand binding as bound receptors occupy ligand surface area. The local model comments and metadata give this context: Dimensionless kinetic model of multivalent ligand-receptor binding with steric hindrance. A multivalent ligand with n=20 equivalent binding sites interacts with monovalent cell-surface receptors. Bound receptors cover a circular area a on the ligand surface, sterically excluding nearby sites from further binding. The approximate insertion probability (Eq. 10) gives the fraction of unbound sites available for receptor binding: P_i(A) = (1 - i/n)(1 - ia/A)(1 - 3a/(A - ia))^i with a/A = 0.01 (receptor footprint is 1% of ligand surface) and gamma = 1 (circular receptor footprint). The steric hindrance factor H(i) = (1 - ia/A)(1 - 3a/(A-ia))^i reduces the number of available sites nu(i) = (n-i)*H(i) below the equivalent-site value (n-i). Variables are dimensionless: x_i = L_i/R_T (surface-bound. The explanation below is therefore based on the local BNGL model file `Published/Hlavacek1999/steric_effects_hlavacek1999.bngl` and metadata file `Published/Hlavacek1999/metadata.yaml`, not on remote URLs.

## 3. Main molecules, sites, and states

BNGL sites are named contact points or state variables on a molecule. A value after `~` is an internal state, such as phosphorylated/unphosphorylated, active/inactive, localized/nonlocalized, or another model-specific switch. Matching bond labels such as `!1` mean the two marked sites are connected in the same complex; a site without a bond label is free or unspecified.

- `Lig`: Lig. It has state sites `b~1~2~3~4~5~6~7~8~9~10~11~12~13~14~15~16~17~18~19~20`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.

## 4. Initial conditions and model setup

The model starts from these encoded species or starting concentrations/copy numbers. Entries without `!` bond labels start as free molecules; entries with matching labels start as pre-assembled complexes.

- `Lig(b~1)  0`

Important parameters include:

- `n  20`
- `vKLT  1`
- `KxRT  10`
- `CRT_LT  10`
- `kr_kmx  1`
- `aA  0.01`
- `nu_1   (n-1)*(1-1*aA)*(1-3*aA/(1-1*aA))^1`
- `nu_2   (n-2)*(1-2*aA)*(1-3*aA/(1-2*aA))^2`
- `nu_3   (n-3)*(1-3*aA)*(1-3*aA/(1-3*aA))^3`
- `nu_4   (n-4)*(1-4*aA)*(1-3*aA/(1-4*aA))^4`
- `nu_5   (n-5)*(1-5*aA)*(1-3*aA/(1-5*aA))^5`
- `nu_6   (n-6)*(1-6*aA)*(1-3*aA/(1-6*aA))^6`
- `nu_7   (n-7)*(1-7*aA)*(1-3*aA/(1-7*aA))^7`
- `nu_8   (n-8)*(1-8*aA)*(1-3*aA/(1-8*aA))^8`
- `nu_9   (n-9)*(1-9*aA)*(1-3*aA/(1-9*aA))^9`
- `nu_10  (n-10)*(1-10*aA)*(1-3*aA/(1-10*aA))^10`
- `nu_11  (n-11)*(1-11*aA)*(1-3*aA/(1-11*aA))^11`
- `nu_12  (n-12)*(1-12*aA)*(1-3*aA/(1-12*aA))^12`
- `nu_13  (n-13)*(1-13*aA)*(1-3*aA/(1-13*aA))^13`
- `nu_14  (n-14)*(1-14*aA)*(1-3*aA/(1-14*aA))^14`
- `nu_15  (n-15)*(1-15*aA)*(1-3*aA/(1-15*aA))^15`
- `nu_16  (n-16)*(1-16*aA)*(1-3*aA/(1-16*aA))^16`
- `nu_17  (n-17)*(1-17*aA)*(1-3*aA/(1-17*aA))^17`
- `nu_18  (n-18)*(1-18*aA)*(1-3*aA/(1-18*aA))^18`
- `nu_19  (n-19)*(1-19*aA)*(1-3*aA/(1-19*aA))^19`

Functions and simulation/action commands:

- `r_b_lo() = Obs_L1 + 2*Obs_L2 + 3*Obs_L3 + 4*Obs_L4 + 5*Obs_L5`
- `r_b_md() = 6*Obs_L6 + 7*Obs_L7 + 8*Obs_L8 + 9*Obs_L9 + 10*Obs_L10`
- `r_b_hi() = 11*Obs_L11 + 12*Obs_L12 + 13*Obs_L13 + 14*Obs_L14`
- `r_b_vh() = 15*Obs_L15 + 16*Obs_L16 + 17*Obs_L17 + 18*Obs_L18`
- `r_b_xx() = 19*Obs_L19 + 20*Obs_L20`
- `r_free() = 1 - r_b_lo() - r_b_md() - r_b_hi() - r_b_vh() - r_b_xx()`
- `l_free() = 1 - CRT_LT*Obs_L_tot`
- `fn_bind() = kr_kmx*vKLT*r_free()*l_free()`
- `alpha_2() = 1 - r_free() - Obs_L1`
- `alpha_10() = 10*Obs_L10 + r_b_hi() + r_b_vh() + r_b_xx()`
- `generate_network({overwrite=>1})`
- `simulate({method=>"ode",suffix=>"ode",\`
- `t_start=>0,t_end=>2.5,n_steps=>500})`
- `generate_network({overwrite=>1})`

## 5. Reaction rules in plain English

These rules are the biological mechanism of the model. When a product contains new matching `!` labels, two sites have become bound; when those labels disappear, a complex has separated. For reversible rules, the first listed rate is the forward rate and the second listed rate is the reverse rate.

- **See Eq. 15, u_0 forward term.**: Production, removal, or biochemical conversion. The nearby model comment says: “See Eq. 15, u_0 forward term.”. The rule involves the listed reactant pattern and produces `Lig`. Rate parameter(s): `fn_bind()`.
- **BNG multiplies by [Lig(b~1)].**: Production, removal, or biochemical conversion. The nearby model comment says: “BNG multiplies by [Lig(b~1)].”. The rule involves `Lig` and produces the listed product pattern. Rate parameter(s): `kr_kmx`.
- **nu(i)*KxRT*r*x_i. See Eq. 15, u_i forward term.**: State change or catalytic conversion. The nearby model comment says: “nu(i)*KxRT*r*x_i. See Eq. 15, u_i forward term.”. The rule involves `Lig` and produces `Lig`. The encoded molecular change is `Lig` site `b` changes from `1` to `2`; site `b` changes from `1` to `2`. Rate parameter(s): `nu_1*KxRT*r_free()`.
- **nu(i)*KxRT*r*x_i. See Eq. 15, u_i forward term.**: State change or catalytic conversion. The nearby model comment says: “nu(i)*KxRT*r*x_i. See Eq. 15, u_i forward term.”. The rule involves `Lig` and produces `Lig`. The encoded molecular change is `Lig` site `b` changes from `2` to `3`; site `b` changes from `2` to `3`. Rate parameter(s): `nu_2*KxRT*r_free()`.
- **nu(i)*KxRT*r*x_i. See Eq. 15, u_i forward term.**: State change or catalytic conversion. The nearby model comment says: “nu(i)*KxRT*r*x_i. See Eq. 15, u_i forward term.”. The rule involves `Lig` and produces `Lig`. The encoded molecular change is `Lig` site `b` changes from `3` to `4`; site `b` changes from `3` to `4`. Rate parameter(s): `nu_3*KxRT*r_free()`.
- **nu(i)*KxRT*r*x_i. See Eq. 15, u_i forward term.**: State change or catalytic conversion. The nearby model comment says: “nu(i)*KxRT*r*x_i. See Eq. 15, u_i forward term.”. The rule involves `Lig` and produces `Lig`. The encoded molecular change is `Lig` site `b` changes from `4` to `5`; site `b` changes from `4` to `5`. Rate parameter(s): `nu_4*KxRT*r_free()`.
- **nu(i)*KxRT*r*x_i. See Eq. 15, u_i forward term.**: State change or catalytic conversion. The nearby model comment says: “nu(i)*KxRT*r*x_i. See Eq. 15, u_i forward term.”. The rule involves `Lig` and produces `Lig`. The encoded molecular change is `Lig` site `b` changes from `5` to `6`; site `b` changes from `5` to `6`. Rate parameter(s): `nu_5*KxRT*r_free()`.
- **nu(i)*KxRT*r*x_i. See Eq. 15, u_i forward term.**: State change or catalytic conversion. The nearby model comment says: “nu(i)*KxRT*r*x_i. See Eq. 15, u_i forward term.”. The rule involves `Lig` and produces `Lig`. The encoded molecular change is `Lig` site `b` changes from `6` to `7`; site `b` changes from `6` to `7`. Rate parameter(s): `nu_6*KxRT*r_free()`.
- **nu(i)*KxRT*r*x_i. See Eq. 15, u_i forward term.**: State change or catalytic conversion. The nearby model comment says: “nu(i)*KxRT*r*x_i. See Eq. 15, u_i forward term.”. The rule involves `Lig` and produces `Lig`. The encoded molecular change is `Lig` site `b` changes from `7` to `8`; site `b` changes from `7` to `8`. Rate parameter(s): `nu_7*KxRT*r_free()`.
- **nu(i)*KxRT*r*x_i. See Eq. 15, u_i forward term.**: State change or catalytic conversion. The nearby model comment says: “nu(i)*KxRT*r*x_i. See Eq. 15, u_i forward term.”. The rule involves `Lig` and produces `Lig`. The encoded molecular change is `Lig` site `b` changes from `8` to `9`; site `b` changes from `8` to `9`. Rate parameter(s): `nu_8*KxRT*r_free()`.
- **nu(i)*KxRT*r*x_i. See Eq. 15, u_i forward term.**: State change or catalytic conversion. The nearby model comment says: “nu(i)*KxRT*r*x_i. See Eq. 15, u_i forward term.”. The rule involves `Lig` and produces `Lig`. The encoded molecular change is `Lig` site `b` changes from `9` to `10`; site `b` changes from `9` to `10`. Rate parameter(s): `nu_9*KxRT*r_free()`.
- **nu(i)*KxRT*r*x_i. See Eq. 15, u_i forward term.**: State change or catalytic conversion. The nearby model comment says: “nu(i)*KxRT*r*x_i. See Eq. 15, u_i forward term.”. The rule involves `Lig` and produces `Lig`. The encoded molecular change is `Lig` site `b` changes from `10` to `11`; site `b` changes from `10` to `11`. Rate parameter(s): `nu_10*KxRT*r_free()`.
- **nu(i)*KxRT*r*x_i. See Eq. 15, u_i forward term.**: State change or catalytic conversion. The nearby model comment says: “nu(i)*KxRT*r*x_i. See Eq. 15, u_i forward term.”. The rule involves `Lig` and produces `Lig`. The encoded molecular change is `Lig` site `b` changes from `11` to `12`; site `b` changes from `11` to `12`. Rate parameter(s): `nu_11*KxRT*r_free()`.
- **nu(i)*KxRT*r*x_i. See Eq. 15, u_i forward term.**: State change or catalytic conversion. The nearby model comment says: “nu(i)*KxRT*r*x_i. See Eq. 15, u_i forward term.”. The rule involves `Lig` and produces `Lig`. The encoded molecular change is `Lig` site `b` changes from `12` to `13`; site `b` changes from `12` to `13`. Rate parameter(s): `nu_12*KxRT*r_free()`.
- **nu(i)*KxRT*r*x_i. See Eq. 15, u_i forward term.**: State change or catalytic conversion. The nearby model comment says: “nu(i)*KxRT*r*x_i. See Eq. 15, u_i forward term.”. The rule involves `Lig` and produces `Lig`. The encoded molecular change is `Lig` site `b` changes from `13` to `14`; site `b` changes from `13` to `14`. Rate parameter(s): `nu_13*KxRT*r_free()`.
- **nu(i)*KxRT*r*x_i. See Eq. 15, u_i forward term.**: State change or catalytic conversion. The nearby model comment says: “nu(i)*KxRT*r*x_i. See Eq. 15, u_i forward term.”. The rule involves `Lig` and produces `Lig`. The encoded molecular change is `Lig` site `b` changes from `14` to `15`; site `b` changes from `14` to `15`. Rate parameter(s): `nu_14*KxRT*r_free()`.
- **nu(i)*KxRT*r*x_i. See Eq. 15, u_i forward term.**: State change or catalytic conversion. The nearby model comment says: “nu(i)*KxRT*r*x_i. See Eq. 15, u_i forward term.”. The rule involves `Lig` and produces `Lig`. The encoded molecular change is `Lig` site `b` changes from `15` to `16`; site `b` changes from `15` to `16`. Rate parameter(s): `nu_15*KxRT*r_free()`.
- **nu(i)*KxRT*r*x_i. See Eq. 15, u_i forward term.**: State change or catalytic conversion. The nearby model comment says: “nu(i)*KxRT*r*x_i. See Eq. 15, u_i forward term.”. The rule involves `Lig` and produces `Lig`. The encoded molecular change is `Lig` site `b` changes from `16` to `17`; site `b` changes from `16` to `17`. Rate parameter(s): `nu_16*KxRT*r_free()`.
- **nu(i)*KxRT*r*x_i. See Eq. 15, u_i forward term.**: State change or catalytic conversion. The nearby model comment says: “nu(i)*KxRT*r*x_i. See Eq. 15, u_i forward term.”. The rule involves `Lig` and produces `Lig`. The encoded molecular change is `Lig` site `b` changes from `17` to `18`; site `b` changes from `17` to `18`. Rate parameter(s): `nu_17*KxRT*r_free()`.
- **nu(i)*KxRT*r*x_i. See Eq. 15, u_i forward term.**: State change or catalytic conversion. The nearby model comment says: “nu(i)*KxRT*r*x_i. See Eq. 15, u_i forward term.”. The rule involves `Lig` and produces `Lig`. The encoded molecular change is `Lig` site `b` changes from `18` to `19`; site `b` changes from `18` to `19`. Rate parameter(s): `nu_18*KxRT*r_free()`.
- **nu(i)*KxRT*r*x_i. See Eq. 15, u_i forward term.**: State change or catalytic conversion. The nearby model comment says: “nu(i)*KxRT*r*x_i. See Eq. 15, u_i forward term.”. The rule involves `Lig` and produces `Lig`. The encoded molecular change is `Lig` site `b` changes from `19` to `20`; site `b` changes from `19` to `20`. Rate parameter(s): `nu_19*KxRT*r_free()`.
- **See Eq. 15, u_i reverse term.**: State change or catalytic conversion. The nearby model comment says: “See Eq. 15, u_i reverse term.”. The rule involves `Lig` and produces `Lig`. The encoded molecular change is `Lig` site `b` changes from `2` to `1`; site `b` changes from `2` to `1`. Rate parameter(s): `2`.
- **See Eq. 15, u_i reverse term.**: State change or catalytic conversion. The nearby model comment says: “See Eq. 15, u_i reverse term.”. The rule involves `Lig` and produces `Lig`. The encoded molecular change is `Lig` site `b` changes from `3` to `2`; site `b` changes from `3` to `2`. Rate parameter(s): `3`.
- **See Eq. 15, u_i reverse term.**: State change or catalytic conversion. The nearby model comment says: “See Eq. 15, u_i reverse term.”. The rule involves `Lig` and produces `Lig`. The encoded molecular change is `Lig` site `b` changes from `4` to `3`; site `b` changes from `4` to `3`. Rate parameter(s): `4`.
- **See Eq. 15, u_i reverse term.**: State change or catalytic conversion. The nearby model comment says: “See Eq. 15, u_i reverse term.”. The rule involves `Lig` and produces `Lig`. The encoded molecular change is `Lig` site `b` changes from `5` to `4`; site `b` changes from `5` to `4`. Rate parameter(s): `5`.
- **See Eq. 15, u_i reverse term.**: State change or catalytic conversion. The nearby model comment says: “See Eq. 15, u_i reverse term.”. The rule involves `Lig` and produces `Lig`. The encoded molecular change is `Lig` site `b` changes from `6` to `5`; site `b` changes from `6` to `5`. Rate parameter(s): `6`.
- **See Eq. 15, u_i reverse term.**: State change or catalytic conversion. The nearby model comment says: “See Eq. 15, u_i reverse term.”. The rule involves `Lig` and produces `Lig`. The encoded molecular change is `Lig` site `b` changes from `7` to `6`; site `b` changes from `7` to `6`. Rate parameter(s): `7`.
- **See Eq. 15, u_i reverse term.**: State change or catalytic conversion. The nearby model comment says: “See Eq. 15, u_i reverse term.”. The rule involves `Lig` and produces `Lig`. The encoded molecular change is `Lig` site `b` changes from `8` to `7`; site `b` changes from `8` to `7`. Rate parameter(s): `8`.
- **See Eq. 15, u_i reverse term.**: State change or catalytic conversion. The nearby model comment says: “See Eq. 15, u_i reverse term.”. The rule involves `Lig` and produces `Lig`. The encoded molecular change is `Lig` site `b` changes from `9` to `8`; site `b` changes from `9` to `8`. Rate parameter(s): `9`.
- **See Eq. 15, u_i reverse term.**: State change or catalytic conversion. The nearby model comment says: “See Eq. 15, u_i reverse term.”. The rule involves `Lig` and produces `Lig`. The encoded molecular change is `Lig` site `b` changes from `10` to `9`; site `b` changes from `10` to `9`. Rate parameter(s): `10`.
- **See Eq. 15, u_i reverse term.**: State change or catalytic conversion. The nearby model comment says: “See Eq. 15, u_i reverse term.”. The rule involves `Lig` and produces `Lig`. The encoded molecular change is `Lig` site `b` changes from `11` to `10`; site `b` changes from `11` to `10`. Rate parameter(s): `11`.
- **See Eq. 15, u_i reverse term.**: State change or catalytic conversion. The nearby model comment says: “See Eq. 15, u_i reverse term.”. The rule involves `Lig` and produces `Lig`. The encoded molecular change is `Lig` site `b` changes from `12` to `11`; site `b` changes from `12` to `11`. Rate parameter(s): `12`.
- **See Eq. 15, u_i reverse term.**: State change or catalytic conversion. The nearby model comment says: “See Eq. 15, u_i reverse term.”. The rule involves `Lig` and produces `Lig`. The encoded molecular change is `Lig` site `b` changes from `13` to `12`; site `b` changes from `13` to `12`. Rate parameter(s): `13`.
- **See Eq. 15, u_i reverse term.**: State change or catalytic conversion. The nearby model comment says: “See Eq. 15, u_i reverse term.”. The rule involves `Lig` and produces `Lig`. The encoded molecular change is `Lig` site `b` changes from `14` to `13`; site `b` changes from `14` to `13`. Rate parameter(s): `14`.
- **See Eq. 15, u_i reverse term.**: State change or catalytic conversion. The nearby model comment says: “See Eq. 15, u_i reverse term.”. The rule involves `Lig` and produces `Lig`. The encoded molecular change is `Lig` site `b` changes from `15` to `14`; site `b` changes from `15` to `14`. Rate parameter(s): `15`.
- **See Eq. 15, u_i reverse term.**: State change or catalytic conversion. The nearby model comment says: “See Eq. 15, u_i reverse term.”. The rule involves `Lig` and produces `Lig`. The encoded molecular change is `Lig` site `b` changes from `16` to `15`; site `b` changes from `16` to `15`. Rate parameter(s): `16`.
- **See Eq. 15, u_i reverse term.**: State change or catalytic conversion. The nearby model comment says: “See Eq. 15, u_i reverse term.”. The rule involves `Lig` and produces `Lig`. The encoded molecular change is `Lig` site `b` changes from `17` to `16`; site `b` changes from `17` to `16`. Rate parameter(s): `17`.
- **See Eq. 15, u_i reverse term.**: State change or catalytic conversion. The nearby model comment says: “See Eq. 15, u_i reverse term.”. The rule involves `Lig` and produces `Lig`. The encoded molecular change is `Lig` site `b` changes from `18` to `17`; site `b` changes from `18` to `17`. Rate parameter(s): `18`.
- **See Eq. 15, u_i reverse term.**: State change or catalytic conversion. The nearby model comment says: “See Eq. 15, u_i reverse term.”. The rule involves `Lig` and produces `Lig`. The encoded molecular change is `Lig` site `b` changes from `19` to `18`; site `b` changes from `19` to `18`. Rate parameter(s): `19`.
- **See Eq. 15, u_i reverse term.**: State change or catalytic conversion. The nearby model comment says: “See Eq. 15, u_i reverse term.”. The rule involves `Lig` and produces `Lig`. The encoded molecular change is `Lig` site `b` changes from `20` to `19`; site `b` changes from `20` to `19`. Rate parameter(s): `20`.

## 6. Observables and expected simulation output

Observables define what the simulator records. They are measurements of matching molecule patterns, complexes, or states, not claims that a particular trajectory must occur.

- `Obs_L1` (Molecules) tracks patterns containing Lig. Pattern: `Lig(b~1)`.
- `Obs_L2` (Molecules) tracks patterns containing Lig. Pattern: `Lig(b~2)`.
- `Obs_L3` (Molecules) tracks patterns containing Lig. Pattern: `Lig(b~3)`.
- `Obs_L4` (Molecules) tracks patterns containing Lig. Pattern: `Lig(b~4)`.
- `Obs_L5` (Molecules) tracks patterns containing Lig. Pattern: `Lig(b~5)`.
- `Obs_L6` (Molecules) tracks patterns containing Lig. Pattern: `Lig(b~6)`.
- `Obs_L7` (Molecules) tracks patterns containing Lig. Pattern: `Lig(b~7)`.
- `Obs_L8` (Molecules) tracks patterns containing Lig. Pattern: `Lig(b~8)`.
- `Obs_L9` (Molecules) tracks patterns containing Lig. Pattern: `Lig(b~9)`.
- `Obs_L10` (Molecules) tracks patterns containing Lig. Pattern: `Lig(b~10)`.
- `Obs_L11` (Molecules) tracks patterns containing Lig. Pattern: `Lig(b~11)`.
- `Obs_L12` (Molecules) tracks patterns containing Lig. Pattern: `Lig(b~12)`.
- `Obs_L13` (Molecules) tracks patterns containing Lig. Pattern: `Lig(b~13)`.
- `Obs_L14` (Molecules) tracks patterns containing Lig. Pattern: `Lig(b~14)`.
- `Obs_L15` (Molecules) tracks patterns containing Lig. Pattern: `Lig(b~15)`.
- `Obs_L16` (Molecules) tracks patterns containing Lig. Pattern: `Lig(b~16)`.
- `Obs_L17` (Molecules) tracks patterns containing Lig. Pattern: `Lig(b~17)`.
- `Obs_L18` (Molecules) tracks patterns containing Lig. Pattern: `Lig(b~18)`.
- `Obs_L19` (Molecules) tracks patterns containing Lig. Pattern: `Lig(b~19)`.
- `Obs_L20` (Molecules) tracks patterns containing Lig. Pattern: `Lig(b~20)`.
- `Obs_L_tot` (Molecules) tracks patterns containing Lig. Pattern: `Lig()`.

Given these observables, plots from the model would show how the named signaling species, complexes, modified states, or coarse-grained variables change over the simulated time course under the listed initial conditions and rates.

## 7. Metadata, source, and compatibility

- Model id: `Hlavacek_1999`
- Title/name: `Hlavacek 1999`
- Category: `physics`
- Tags: `['published', 'physics', 'hlavacek', '1999']`
- Source origin: `published`
- Original repository: `bionetgen/BNGL-Models`
- Original format: `bngl`
- Metadata source path: `missing`
- Local BNGL file used: `Published/Hlavacek1999/steric_effects_hlavacek1999.bngl`
- Local YAML file used: `Published/Hlavacek1999/metadata.yaml`
- Compatibility: bng2 = `true`, NFsim = `false`, methods = `['ode']`
- Playground: visible = `true`, featured = `false`, difficulty = `intermediate`

## 8. Caveats or missing information

- This is a local, syntax-based explanation of the model and metadata; it does not validate the biological correctness of the publication model or reproduce simulations.
- Abbreviated molecule names are expanded only when the metadata, comments, or widely used biological abbreviation makes the identity clear; otherwise the BNGL name is preserved.
- Some large models contain many related binding/phosphorylation/dephosphorylation rules. Repetitive families are explained by their encoded biological event and nearby BNGL comments rather than by dumping raw BNGL syntax.
