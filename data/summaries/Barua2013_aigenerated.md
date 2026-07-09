# Model Explanation: Barua 2013

## One-sentence summary

Beta-catenin control by the Axin/APC/GSK3/CK1 destruction complex.

## What the model shows

This model shows how beta-catenin is captured by a destruction complex, phosphorylated at specific regulatory sites, released or degraded, and replenished by synthesis. It emphasizes how Axin and APC organize beta-catenin with the kinases CK1 and GSK3.

## Biological story

The model is useful as a mechanistic sketch of how molecular interactions create a time-dependent biological response. It is not just a list of reactions: the important behavior is how binding, activation, inhibition, degradation, or transport events combine to change the abundance of active signaling states and complexes over time.

## Main biological players

Beta-catenin, APC, Axin, GSK3 beta, CK1 alpha, and degraded beta-catenin.

## Mechanism in plain English

Beta-catenin binds APC and Axin through different interaction surfaces. APC binds Axin, GSK3 binds Axin, and CK1 also binds Axin, assembling a phosphorylation-competent destruction complex. CK1 phosphorylates beta-catenin first, GSK3 phosphorylates additional beta-catenin sites, APC can also be phosphorylated, and phosphatase-like reactions reverse those modifications. Beta-catenin can be synthesized, degraded slowly when not appropriately phosphorylated, or degraded faster after phosphorylation. Degradation releases the associated complex members.

## Key modeled events

- Beta-catenin binds APC and Axin, placing it into the destruction-complex environment.
- CK1 and GSK3 phosphorylate beta-catenin in sequence, converting it into a form that is removed more rapidly.
- When beta-catenin is degraded, associated APC or Axin partners are released so the scaffold can participate in another cycle.

## What the model measures

The readouts track total live beta-catenin, beta-catenin phosphorylated at CK1 and GSK3 target sites, phosphorylated APC, and beta-catenin bound to Axin. The model shows how destruction-complex assembly controls the balance between beta-catenin persistence and removal.

## How to interpret the plots

A rising curve means that the corresponding active molecule, modified state, complex, or output is accumulating. A falling curve means it is being consumed, deactivated, degraded, released, or diluted. If two curves move in opposite directions, the model is showing a shift between biological states, such as free versus complexed receptor, inactive versus active kinase, or unmodified versus modified substrate.

## Caveats

This is an explanatory summary of the encoded mechanism, not a claim that the model is experimentally complete. When molecule names are abstract or abbreviated, the summary avoids inventing identities beyond what the model itself supports.
