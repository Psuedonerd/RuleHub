# Model Explanation: Wnt Signaling

## One-sentence summary

Wnt assembles a Frizzled–Dishevelled–Axin–LRP5 complex that releases β-catenin from Axin.

## What the model shows

This compact Wnt model focuses on receptor-complex assembly and liberation of β-catenin. It follows ordered recruitment of Dishevelled and an Axin-containing complex to Wnt-bound Frizzled, engagement of LRP5, and release of β-catenin from the assembled platform.

## Biological story

Wnt first binds Frizzled. Frizzled recruits Dishevelled, which captures Axin; that assembly then engages LRP5. β-catenin initially associated with Axin is released once the full receptor complex forms, increasing the free β-catenin pool.

## Main biological players

Wnt, Frizzled, Dishevelled (DSH), Axin complex (AxC), LRP5, and β-catenin.

## Mechanism in plain English

Ligand-bound Frizzled recruits DSH, and DSH recruits AxC. Frizzled and AxC then make coordinated contacts with LRP5 to create a higher-order receptor complex. When β-catenin is carried into that complex through AxC, it is released, leaving the receptor assembly intact and increasing free β-catenin.

## Key modeled events

- Wnt binds Frizzled reversibly.
- Activated Frizzled recruits DSH, which then recruits AxC.
- The Frizzled–DSH–AxC assembly engages LRP5.
- Completion of the receptor complex releases β-catenin from AxC.

## What the model measures

Readouts track free β-catenin and three successive complexes: DSH–AxC, Wnt–Frizzled–DSH–AxC, and the full LRP5-containing assembly with β-catenin. Total pools of the major components are also followed.

## Expected behavior in plots

The DSH–AxC complex should appear before the Frizzled-containing intermediate, with the full LRP5 complex forming later. Free β-catenin should rise only as the complete assembly turns over its bound β-catenin, giving a delayed output relative to receptor-complex formation.

## Caveats

The model represents β-catenin release but not its synthesis, destruction-complex phosphorylation, nuclear entry, or transcription. Several Wnt pathway components are compressed into AxC.
