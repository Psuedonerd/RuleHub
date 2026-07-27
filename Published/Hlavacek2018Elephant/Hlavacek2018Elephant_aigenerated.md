# Model Explanation: Hlavacek 2018 Elephant

## One-sentence summary

Two fitted periodic signals are reconstructed as smooth harmonic time courses over one 464-unit cycle.

## What the model shows

This mathematical benchmark represents a measured two-dimensional periodic trajectory using Fourier harmonics rather than a biochemical pathway. It is useful for evaluating parameter fitting of oscillatory data.

## Biological story

A clock-like variable advances uniformly. Two fitted functions, X and Y, combine a baseline with 20 sine and cosine harmonics, allowing a complex closed trajectory to be reproduced over one period.

## Main biological players

A time counter, periodic outputs X and Y, a 464-unit period, and fitted harmonic coefficients.

## Mechanism in plain English

Time increases at a constant rate. Each output sums oscillations at the fundamental frequency and its first 20 harmonics. Different amplitudes and phases shape X and Y, so plotting one against the other reconstructs the fitted “elephant” contour while plotting against time reveals the component waveforms.

## Key modeled events

- A counter advances uniformly through one complete period.
- Twenty harmonics contribute to the X coordinate.
- A separate set of 20 harmonics shapes the Y coordinate.
- The paired outputs trace a closed periodic curve.

## What the model measures

The reported counter gives time, while the two calculated outputs provide the fitted X and Y coordinates.

## Expected behavior in plots

X and Y should each repeat after 464 time units. A phase plot of Y against X should close on itself and reproduce the intended elephant-like outline; a time plot should show structured, non-sinusoidal periodic waveforms.

## Caveats

This is an abstract curve-fitting benchmark, not a biological mechanism. The coordinates and time unit have no assigned molecular interpretation.
