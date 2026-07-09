# Model Explanation: Dushek 2014

## 1. One-sentence summary

This model represents early T-cell receptor signaling site dynamics, with receptor phosphorylation, kinase/phosphatase regulation, adaptor recruitment, and downstream complex formation.

## 2. Biological meaning

This model represents early T-cell receptor signaling site dynamics, with receptor phosphorylation, kinase/phosphatase regulation, adaptor recruitment, and downstream complex formation. The local model comments and metadata give this context: Model of a kinase (E) and phosphatase (F) actin on a biosensor (B) . Modification module Enzymatic reaction ( kinase ) Enzymatic reaction ( phosphatase ) Intramolecular module Intermolecular module Phosphorylation by E. Dephosphorylation by F. Intramolecular reaction Intermolecular reaction Biosensor in State 1 Biosensor in State 2 Biosensor in State 3 ( combination of a l l states below , see manuscript fordetails ) Sequestered signaling protein. The explanation below is therefore based on the local BNGL model file `Published/Dushek2014/Dushek_2014.bngl` and metadata file `Published/Dushek2014/metadata.yaml`, not on remote URLs.

## 3. Main molecules, sites, and states

BNGL sites are named contact points or state variables on a molecule. A value after `~` is an internal state, such as phosphorylated/unphosphorylated, active/inactive, localized/nonlocalized, or another model-specific switch. Matching bond labels such as `!1` mean the two marked sites are connected in the same complex; a site without a bond label is free or unspecified.

- `E`: kinase enzyme. It has binding or interaction sites `b`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `F`: phosphatase enzyme. It has binding or interaction sites `b`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.
- `B`: biosensor. It has binding/interaction sites `b` and regulated state sites `e~0~1`, `Y~U~P`. It participates wherever these sites become bound with matching `!` labels or change state with `~` values.

## 4. Initial conditions and model setup

The model starts from these encoded species or starting concentrations/copy numbers. Entries without `!` bond labels start as free molecules; entries with matching labels start as pre-assembled complexes.

- `E(b) 1`
- `F(b) 1`
- `B(e~0,b,Y~U) 100`

Important parameters include:

- `Ekf 10`
- `Ekb 1`
- `Ekc 1`
- `Fkf 10`
- `Fkb 1`
- `Fkc 1`
- `kon1 1000`
- `koff1 1`
- `kon2 10`
- `koff2 1`

Functions and simulation/action commands:

- `generate network ({ overwrite =>1,max agg=>15}) ;`
- `generate network ({ overwrite =>1,max agg=>2}) ;`
- `writeMfile ({}) ;`
- `writeMfile ({}) ;`

## 5. Reaction rules in plain English

These rules are the biological mechanism of the model. When a product contains new matching `!` labels, two sites have become bound; when those labels disappear, a complex has separated. For reversible rules, the first listed rate is the forward rate and the second listed rate is the reverse rate.

- **Phosphorylation by E.**: Reversible binding/release. The nearby model comment says: “Phosphorylation by E.”. The rule involves `B`, `E` and produces `B`, `E`. The encoded molecular change is `B` site `e` changes from `0` to `1`; site `e` changes from `0` to `1`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `Ekf, Ekb`.
- **Phosphorylation by E.**: Unbinding or disassembly. The nearby model comment says: “Phosphorylation by E.”. The rule involves `B`, `E` and produces `B`, `E`. The encoded molecular change is `B` site `e` changes from `1` to `0`; site `e` changes from `1` to `0`; site `Y` changes from `U` to `P`. Loss of matching `!` labels means a complex separates. Rate parameter(s): `Ekc`.
- **Dephosphorylation by F.**: Reversible binding/release. The nearby model comment says: “Dephosphorylation by F.”. The rule involves `B`, `F` and produces `B`, `F`. The encoded molecular change is `B` site `e` changes from `0` to `1`; site `e` changes from `0` to `1`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `Fkf,  Fkb`.
- **Dephosphorylation by F.**: Unbinding or disassembly. The nearby model comment says: “Dephosphorylation by F.”. The rule involves `B`, `F` and produces `B`, `F`. The encoded molecular change is `B` site `e` changes from `1` to `0`; site `e` changes from `1` to `0`; site `Y` changes from `P` to `U`. Loss of matching `!` labels means a complex separates. Rate parameter(s): `Fkc`.
- **Intramolecular reaction**: Reversible binding/release. The nearby model comment says: “Intramolecular reaction”. The rule involves `B` and produces `B`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `kon1, koff1`.
- **Intermolecular reaction**: Reversible binding/release. The nearby model comment says: “Intermolecular reaction”. The rule involves `B` and produces `B`. New matching `!` labels in the product mean those sites become physically connected. Because the rule is reversible, the first rate drives the forward event and the second rate drives the reverse event. Rate parameter(s): `kon2, koff2`.

## 6. Observables and expected simulation output

Observables define what the simulator records. They are measurements of matching molecule patterns, complexes, or states, not claims that a particular trajectory must occur.

- `W` (Molecules) tracks phosphorylated/modified molecules. Pattern: `B(e~0,b,Y~P), B(e~0,b,Y~U), B(e~1,b)`.
- `U` (Molecules) tracks phosphorylated/modified molecules, bound complexes. Pattern: `B(e~0,b!1,Y~P!1)`.
- `V2` (Species) tracks patterns containing B==2. Pattern: `B==2`.
- `V3` (Species) tracks patterns containing B==3. Pattern: `B==3`.
- `V4` (Species) tracks patterns containing B==4. Pattern: `B==4`.
- `V5` (Species) tracks patterns containing B==5. Pattern: `B==5`.
- `V6` (Species) tracks patterns containing B==6. Pattern: `B==6`.
- `V7` (Species) tracks patterns containing B==7. Pattern: `B==7`.
- `V8` (Species) tracks patterns containing B==8. Pattern: `B==8`.
- `V9` (Species) tracks patterns containing B==9. Pattern: `B==9`.
- `V10` (Species) tracks patterns containing B==10. Pattern: `B==10`.
- `V11` (Species) tracks patterns containing B==11. Pattern: `B==11`.
- `V12` (Species) tracks patterns containing B==12. Pattern: `B==12`.
- `V13` (Species) tracks patterns containing B==13. Pattern: `B==13`.
- `V14` (Species) tracks patterns containing B==14. Pattern: `B==14`.
- `V15` (Species) tracks patterns containing B==15. Pattern: `B==15`.
- `E` (Molecules) tracks bound complexes. Pattern: `E(b!+)`.

Given these observables, plots from the model would show how the named signaling species, complexes, modified states, or coarse-grained variables change over the simulated time course under the listed initial conditions and rates.

## 7. Metadata, source, and compatibility

- Model id: `Dushek_2014`
- Title/name: `Dushek 2014`
- Category: `signaling`
- Tags: `['published', 'dushek', '2014', 'e', 'f', 'b']`
- Source origin: `published`
- Original repository: `bionetgen-web-simulator`
- Original format: `bngl`
- Metadata source path: `published-models/complex-models/Dushek_2014.bngl`
- Local BNGL file used: `Published/Dushek2014/Dushek_2014.bngl`
- Local YAML file used: `Published/Dushek2014/metadata.yaml`
- Compatibility: bng2 = `true`, NFsim = `true`, methods = `['ode']`
- Playground: visible = `false`, featured = `false`, difficulty = `advanced`

## 8. Caveats or missing information

- This is a local, syntax-based explanation of the model and metadata; it does not validate the biological correctness of the publication model or reproduce simulations.
- Abbreviated molecule names are expanded only when the metadata, comments, or widely used biological abbreviation makes the identity clear; otherwise the BNGL name is preserved.
- Some large models contain many related binding/phosphorylation/dephosphorylation rules. Repetitive families are explained by their encoded biological event and nearby BNGL comments rather than by dumping raw BNGL syntax.
