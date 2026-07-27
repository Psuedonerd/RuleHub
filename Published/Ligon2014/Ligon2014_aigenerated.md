# Model Explanation: Ligon 2014

## One-sentence summary

Clathrin-pit loading and endosomal escape connect extracellular lipoplex uptake to mRNA release and GFP expression.

## What the model shows

This delivery model follows lipoplexes from an extracellular pool through progressive loading of a clathrin-coated pit, conversion to an endosomal state, release of internal cargo, mRNA production, and GFP expression. It is designed to connect uptake bottlenecks with a delayed reporter output.

## Biological story

External lipoplexes can be washed away or attach sequentially to a pit with finite capacity. A loaded pit becomes an endosome, internal lipoplex cargo escapes, and successful delivery yields mRNA that produces GFP before both cargo and products are cleared.

## Main biological players

External and internal lipoplex, clathrin-coated pit/endosome, delivered mRNA, GFP, a degradation sink, and a timer/input variable.

## Mechanism in plain English

Lipoplexes accumulate one by one on a pit until uptake converts that assembly into an endosome. Internalized particles are released from the carrier and can generate mRNA; mRNA then drives GFP production. Washing and degradation compete with delivery, while finite pit capacity makes the number of attached particles an explicit uptake constraint.

## Key modeled events

- Extracellular lipoplex is removed by washing or captured by a clathrin-coated pit.
- Successive particles load a pit up to a finite capacity before endosomal conversion.
- Internal lipoplex escapes from the endosome and produces an mRNA population.
- mRNA is translated into GFP, while delivery intermediates and products are cleared.

## What the model measures

Readouts follow extracellular lipoplex, pits, endosomes, internal lipoplex, mRNA, GFP, and elapsed timer counts.

## Expected behavior in plots

Pit occupancy should rise before endosomes and internal cargo appear. mRNA should lag behind uptake, and GFP should lag behind mRNA and persist according to its production and loss rates. Strong washing should suppress the early extracellular pool and reduce all later delivery readouts.

## Caveats

The delivery stages are deliberately coarse population steps. Membrane fusion, endosomal maturation, individual nucleic-acid molecules, and cell-to-cell variability are not mechanistically resolved.
