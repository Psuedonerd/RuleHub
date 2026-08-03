# Published YAML Feature Audit — New 30-Model Batch

Audited 30 models and created 30 `metadata_aigenerated.yaml` files. Inserted 239 missing values; 27 items require review.

## Barua2013

- Inserted false: `uses_cbngl_compartments`, `uses_vcell_compartments`.
- Review change: `default_sim_command: ode` → `simulate_ode` — active `simulate_ode(...)` action.

## BaruaBCR2012

- Inserted false: `uses_cbngl_compartments`, `uses_vcell_compartments`.

## BaruaFceRI2012

- Inserted false: `uses_cbngl_compartments`, `uses_vcell_compartments`, `uses_moveconnected`, `uses_trash_molecules`, `uses_anchors`, `uses_deletes_molecules`, `uses_exclude_include_reactants`.
- Review insertion: `uses_multiple_identical_sites: true` — repeated `l` site in `L(l,l)`.
- Review insertion: `uses_generate_network: true` — active `generate_network(...)` action.

## Blinov2006

- Inserted false: `uses_cbngl_compartments`, `uses_vcell_compartments`.
- Review change: `default_sim_command: ode` → `simulate_ode` — active `simulate_ode(...)` action.

## Chattaraj2021

- Inserted false: `uses_cbngl_compartments`, `uses_vcell_compartments`, `uses_moveconnected`, `uses_trash_molecules`, `uses_anchors`, `uses_multiple_identical_sites`, `uses_deletes_molecules`, `uses_exclude_include_reactants`, `uses_generate_network`.

## CheemalavaguJAKSTAT

- Inserted false: `uses_cbngl_compartments`, `uses_vcell_compartments`, `uses_moveconnected`, `uses_trash_molecules`, `uses_anchors`, `uses_multiple_identical_sites`, `uses_deletes_molecules`, `uses_exclude_include_reactants`.
- Review insertion: `uses_generate_network: true` — active `generate_network(...)` action.

## ChylekTCR2014

- Inserted false: `uses_cbngl_compartments`, `uses_vcell_compartments`, `uses_moveconnected`, `uses_trash_molecules`, `uses_anchors`, `uses_deletes_molecules`, `uses_exclude_include_reactants`, `uses_generate_network`.
- Review insertion: `uses_multiple_identical_sites: true` — repeated `aCD28` site in `Lig1(aCD28,aCD28)`.

## Dushek2011

- Inserted false: `uses_cbngl_compartments`, `uses_vcell_compartments`, `uses_moveconnected`, `uses_trash_molecules`, `uses_anchors`, `uses_multiple_identical_sites`, `uses_deletes_molecules`, `uses_exclude_include_reactants`.
- Review insertion: `uses_generate_network: true` — active `generate_network(...)` action.

## Dushek2014

- Inserted false: `uses_cbngl_compartments`, `uses_vcell_compartments`.
- Review change: `uses_generate_network: true` → `false` — no active `generate_network(...)` action.

## Erdem2021

- Inserted false: `uses_cbngl_compartments`, `uses_vcell_compartments`, `uses_moveconnected`, `uses_trash_molecules`, `uses_anchors`, `uses_multiple_identical_sites`, `uses_deletes_molecules`, `uses_exclude_include_reactants`.
- Review insertion: `uses_generate_network: true` — active `generate_network(...)` action.

## Goldstein1980

- Inserted false: `uses_cbngl_compartments`, `uses_vcell_compartments`, `uses_moveconnected`, `uses_trash_molecules`, `uses_anchors`, `uses_multiple_identical_sites`, `uses_exclude_include_reactants`, `uses_generate_network`.
- Review insertion: `uses_deletes_molecules: true` — active `DeleteMolecules` construct.

## Harmon2017

- Inserted false: `uses_cbngl_compartments`, `uses_vcell_compartments`, `uses_moveconnected`, `uses_trash_molecules`, `uses_anchors`, `uses_multiple_identical_sites`, `uses_deletes_molecules`, `uses_exclude_include_reactants`.
- Review insertion: `uses_generate_network: true` — active `generate_network(...)` action.

## Hat2016

- Inserted false: `uses_cbngl_compartments`, `uses_vcell_compartments`.
- Review change: `default_sim_command: ode` → `simulate` — active `simulate(...)` action.

## Hlavacek1999

- Inserted false: `uses_cbngl_compartments`, `uses_vcell_compartments`, `uses_moveconnected`, `uses_trash_molecules`, `uses_anchors`, `uses_multiple_identical_sites`, `uses_deletes_molecules`, `uses_exclude_include_reactants`.
- Review insertion: `uses_generate_network: true` — active `generate_network(...)` action.

## Hlavacek2018Egg

- Inserted false: `uses_cbngl_compartments`, `uses_vcell_compartments`, `uses_moveconnected`, `uses_trash_molecules`, `uses_anchors`, `uses_multiple_identical_sites`, `uses_deletes_molecules`, `uses_exclude_include_reactants`.
- Review insertion: `uses_generate_network: true` — active `generate_network(...)` action.

## JaruszewiczBlonska2023

- Inserted false: `uses_cbngl_compartments`, `uses_vcell_compartments`, `uses_moveconnected`, `uses_trash_molecules`, `uses_anchors`, `uses_multiple_identical_sites`, `uses_deletes_molecules`, `uses_exclude_include_reactants`.
- Review insertion: `uses_generate_network: true` — active `generate_network(...)` action.

## Kesseler2013

- Inserted false: `uses_cbngl_compartments`, `uses_vcell_compartments`, `uses_moveconnected`, `uses_trash_molecules`, `uses_anchors`, `uses_multiple_identical_sites`, `uses_deletes_molecules`, `uses_exclude_include_reactants`, `uses_generate_network`.

## Kocieniewski2012

- Inserted false: `uses_cbngl_compartments`, `uses_vcell_compartments`.
- Review change: `uses_generate_network: true` → `false` — no active `generate_network(...)` action.

## Korwek2023

- Inserted false: `uses_cbngl_compartments`, `uses_vcell_compartments`, `uses_moveconnected`, `uses_trash_molecules`, `uses_anchors`, `uses_multiple_identical_sites`, `uses_deletes_molecules`, `uses_exclude_include_reactants`.
- Review insertion: `uses_generate_network: true` — active `generate_network(...)` action.

## Kozer2013

- Inserted false: `uses_cbngl_compartments`, `uses_vcell_compartments`, `uses_moveconnected`, `uses_trash_molecules`, `uses_anchors`, `uses_multiple_identical_sites`, `uses_deletes_molecules`, `uses_exclude_include_reactants`.
- Review insertion: `uses_generate_network: true` — active `generate_network(...)` action.

## Kozer2014

- Inserted false: `uses_cbngl_compartments`, `uses_vcell_compartments`.
- Review change: `default_sim_command: ode` → `simulate_ode` — active `simulate_ode(...)` action.

## LinERK2019

- Inserted false: `uses_cbngl_compartments`, `uses_vcell_compartments`, `uses_moveconnected`, `uses_trash_molecules`, `uses_anchors`, `uses_multiple_identical_sites`, `uses_deletes_molecules`, `uses_exclude_include_reactants`.
- Review insertion: `uses_generate_network: true` — active `generate_network(...)` action.

## LinPrion2019

- Inserted false: `uses_cbngl_compartments`, `uses_vcell_compartments`, `uses_moveconnected`, `uses_trash_molecules`, `uses_anchors`, `uses_multiple_identical_sites`, `uses_deletes_molecules`, `uses_exclude_include_reactants`.
- Review insertion: `uses_generate_network: true` — active `generate_network(...)` action.

## LinTCR2019

- Inserted false: `uses_cbngl_compartments`, `uses_vcell_compartments`, `uses_moveconnected`, `uses_trash_molecules`, `uses_anchors`, `uses_multiple_identical_sites`, `uses_deletes_molecules`, `uses_exclude_include_reactants`.
- Review insertion: `uses_generate_network: true` — active `generate_network(...)` action.

## Macken1982

- Inserted false: `uses_cbngl_compartments`, `uses_vcell_compartments`, `uses_moveconnected`, `uses_trash_molecules`, `uses_anchors`, `uses_deletes_molecules`, `uses_exclude_include_reactants`, `uses_generate_network`.
- Review insertion: `uses_multiple_identical_sites: true` — repeated `r` site in `L(r,r,r)`.

## Alabama

- Inserted false: `uses_cbngl_compartments`, `uses_vcell_compartments`, `uses_moveconnected`, `uses_trash_molecules`, `uses_anchors`, `uses_multiple_identical_sites`, `uses_deletes_molecules`, `uses_exclude_include_reactants`.
- Review insertion: `uses_generate_network: true` — active `generate_network(...)` action.

## Massole2023

- Inserted false: `uses_cbngl_compartments`, `uses_vcell_compartments`, `uses_moveconnected`, `uses_trash_molecules`, `uses_anchors`, `uses_deletes_molecules`, `uses_exclude_include_reactants`, `uses_generate_network`.
- Review insertion: `uses_multiple_identical_sites: true` — repeated `oh` site in `_EG_(oh~p,oh~p)`.

## McMillan2021

- Inserted false: `uses_cbngl_compartments`, `uses_vcell_compartments`, `uses_moveconnected`, `uses_trash_molecules`, `uses_anchors`, `uses_multiple_identical_sites`, `uses_deletes_molecules`, `uses_exclude_include_reactants`.
- Review insertion: `uses_generate_network: true` — active `generate_network(...)` action.

## Mertins2023

- Inserted false: `uses_cbngl_compartments`, `uses_vcell_compartments`, `uses_moveconnected`, `uses_trash_molecules`, `uses_anchors`, `uses_multiple_identical_sites`, `uses_deletes_molecules`, `uses_exclude_include_reactants`, `uses_generate_network`.

## InputFiles

- Inserted false: `uses_cbngl_compartments`, `uses_vcell_compartments`, `uses_moveconnected`, `uses_trash_molecules`, `uses_anchors`, `uses_multiple_identical_sites`, `uses_deletes_molecules`, `uses_exclude_include_reactants`.
- Review insertion: `uses_generate_network: true` — active `generate_network(...)` action.
