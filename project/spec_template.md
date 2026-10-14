# Spec: <name of the thing you're building>

A spec is where *you* make the decisions, so the agent doesn't make them for you. Keep it short: one or two pages is plenty. See `example_spec.md` for a filled-in example.

## Goal and user
Who will use this, and what do they need it for? One or two sentences.

## Inputs
The data (or other inputs): where it comes from, its format, how big it is now, and how big it could get.

## Outputs
Exactly what gets produced: files and their columns, figures, tables, printed summaries, a function's return value...

## Definitions and rules
Every decision someone could reasonably make differently: how things are calculated, what counts as invalid, what happens to missing values, units, time zones.

## Acceptance criteria
How you will know it's done. Each one should be something a test or a quick check can confirm, e.g. "cash tips are missing (NaN), not 0", rather than "the output is clean".

## Performance budget
How much data, how fast, and how much memory, e.g. "a 7-million-row month in under a minute and 4 GB".

## Out of scope
What it should *not* do (yet).

## Open questions
Decisions you haven't made yet. Ask the agent to add to this list rather than guessing.
