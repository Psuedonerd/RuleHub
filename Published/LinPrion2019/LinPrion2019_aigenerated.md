# Model Explanation: Lin Prion 2019

## One-sentence summary

Prion replication emerges from conversion-dependent polymer growth, fragmentation, synthesis, and clearance of PrP conformers.

## What the model shows

This nucleated-polymerization model follows normal cellular PrP and misfolded PrPSc polymers over days. It captures how chain elongation and breakage can amplify replication-competent ends while synthesis, degradation, clearance, and conformational reversion oppose accumulation.

## Biological story

Normal PrP is continually supplied and removed. Misfolded chains recruit normal protein at their ends, converting it into the PrPSc state; chains also break, increasing the number of growth-capable fragments. Slow clearance removes entire PrPSc-containing chains, and short misfolded units can revert to the normal conformation.

## Main biological players

Cellular PrP, misfolded PrPSc, polymer ends, short and long PrPSc chains, and synthesis/clearance processes.

## Mechanism in plain English

New PrP enters the normal pool. A normal molecule attaches to a misfolded chain and adopts the misfolded conformation, extending the polymer. Fragmentation splits chains and creates more ends, accelerating subsequent recruitment. Whole-chain clearance and normal-protein degradation remove material, while conformational reversion provides an additional loss route for short misfolded assemblies.

## Key modeled events

- Normal PrP is synthesized and degraded continuously.
- PrPSc chains recruit normal PrP and convert it during elongation.
- Polymer breakage generates additional fragments and growth-capable ends.
- Slow chain clearance and conformational reversion oppose PrPSc accumulation.

## What the model measures

Readouts distinguish free normal PrP and representative PrPSc polymers containing 3, 15, or 30 molecules, providing snapshots of the chain-length distribution.

## Expected behavior in plots

Normal PrP may initially approach a supply–loss balance while small PrPSc chains seed growth. If elongation and fragmentation dominate clearance, short-chain abundance should rise first and longer 15- and 30-unit chains should appear later; stronger clearance should blunt or delay that progression.

## Caveats

Polymer lengths are truncated for tractability, and only selected chain sizes are reported. The model addresses replication kinetics rather than neuronal toxicity, tissue spread, or detailed prion structure.
