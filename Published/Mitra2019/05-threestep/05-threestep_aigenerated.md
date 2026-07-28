# Model Explanation: Mitra 2019 three-step cascade

## One-sentence summary

A four-state irreversible cascade exposes how three sequential rates shape signal delay and output accumulation.

## What the model shows

This toy model provides a transparent parameter-fitting example rather than a named biochemical pathway. A starting population passes through intermediates B and C before reaching terminal state D.

## Biological story

All material begins as A. It is converted to B, then C, then D, with a separate rate governing each step and no reverse flow.

## Main biological players

Abstract states A, B, C, and D and three transition rates.

## Mechanism in plain English

The first process consumes A and produces B. B then feeds C, and C feeds the terminal D pool. Because each intermediate must be populated before the next step can proceed, the model turns rate differences into measurable delays and transient intermediate peaks.

## Key modeled events

- A is converted irreversibly to B.
- B is converted irreversibly to C.
- C is converted irreversibly to terminal state D.

## What the model measures

Readouts report the abundance of A, B, C, and D throughout the time course.

## Expected behavior in plots

A should decay monotonically and D should rise monotonically. B should peak first and C later; the slowest of the three transitions should create the largest upstream buildup and dominate the delay before D accumulates.

## Caveats

The states are intentionally abstract and do not correspond to named molecules. The model omits synthesis, degradation, feedback, and reversibility.
