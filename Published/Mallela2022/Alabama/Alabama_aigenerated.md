# Model Explanation: Mallela 2022 — Alabama

## One-sentence summary

A staged COVID-19 transmission model links social distancing, case detection, hospitalization, recovery, and death in Alabama.

## What the model shows

This regional severe acute respiratory syndrome coronavirus 2 (SARS-CoV-2) model divides infection into multiple exposed stages before asymptomatic or symptomatic disease. The selected state member uses Alabama-specific population and distancing parameters.

## Biological story

In Alabama, susceptible people move between mixing and protected behavior. Infection progresses through five exposed stages, then branches into asymptomatic or symptomatic outcomes; detected cases can enter quarantine, and severe cases enter hospital before recovery or death.

## Main biological players

Susceptible people in Alabama, five exposed stages, asymptomatic infection, symptomatic infection, hospitalized, recovered, deceased, quarantined counterparts, and a dynamic social-distancing variable.

## Mechanism in plain English

Infectious people transmit within the Alabama mixing susceptible population, with lower exposure among protected people. A chain of exposed stages approximates a distributed incubation period. Symptomatic detection redirects cases toward isolation, while hospitalization and outcome processes account for severe disease. Social-distancing setpoints change over time and feed back on contact.

## Key modeled events

- Behavioral transitions redistribute the Alabama population between mixing and protected susceptible groups.
- New infections pass through five exposed stages.
- Cases branch into asymptomatic and symptomatic infectious populations.
- Detection and quarantine remove infectious people from ordinary mixing.
- Hospitalization resolves into recovery or death.

## What the model measures

Readouts report susceptible behavior, each exposed stage, asymptomatic and symptomatic infection, quarantine, hospitalization, recovery, death, and cumulative detected cases for Alabama.

## Expected behavior in plots

After introduction, exposed stages should rise in sequence before symptomatic cases and hospitalizations. Stronger distancing should lower and delay the infectious peak; deaths and cumulative detected cases should lag behind incidence. The selected state member uses Alabama-specific population and distancing parameters.

## Caveats

This is the fitted Alabama member of a larger collection. It represents population averages and does not resolve age, household structure, individual contact networks, or viral evolution.
