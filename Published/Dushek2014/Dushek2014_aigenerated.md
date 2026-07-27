# Model Explanation: Dushek 2014

## One-sentence summary

A kinase–phosphatase cycle controls biosensor modification, folding, oligomerization, and sequestration across multiple complex sizes.

## What the model shows

This abstract biosensor model asks how enzymatic modification is translated into structural readouts. A kinase E and phosphatase F act on biosensor B, while B can make internal or intermolecular contacts and grow into oligomers as large as 15 units.

## Biological story

The kinase drives B into a phosphorylated form and the phosphatase reverses it. Modification changes which contacts B can make: a biosensor may close internally, associate with another B, or sequester the kinase. These competing states determine whether the signal appears as a compact sensor, a larger assembly, or unavailable enzyme.

## Main biological players

Biosensor B, kinase E, phosphatase F, unphosphorylated and phosphorylated B, internally bound B, B oligomers, and sequestered kinase.

## Mechanism in plain English

E transiently binds B and phosphorylates its tyrosine-like state; F binds the modified sensor and removes that mark. B can form an intramolecular contact or an intermolecular bond through its binding component. Repeated intermolecular association creates oligomers of different sizes. When E is captured in a complex, the free kinase pool falls and further modification can become limited.

## Key modeled events

- Kinase E phosphorylates B, while phosphatase F reverses the modification.
- B can switch between open and internally bound configurations.
- Intermolecular B contacts generate dimers and progressively larger oligomers.
- Binding to B sequesters E and reduces freely available kinase.

## What the model measures

The W and U readouts distinguish broad free/folded biosensor pattern classes, V2 through V15 report exact oligomer sizes, and the E readout tracks kinase captured in a bond. Together they separate modification from assembly and sequestration.

## Expected behavior in plots

Phosphorylated or binding-competent B should appear before large oligomers. Small V2/V3 complexes should rise earlier than high-order V states, while strong sequestration should increase bound E and limit additional biosensor conversion. Changing network truncation would most visibly affect the largest V curves.

## Caveats

E, F, and B are abstract and should not be assigned to a specific pathway. Oligomer generation is explicitly capped, so behavior near size 15 can reflect truncation rather than a physical maximum.
