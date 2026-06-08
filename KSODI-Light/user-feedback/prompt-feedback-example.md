# KSODI-Light Prompt Feedback Example

This example is for users who want feedback on their own prompt before asking
for a full answer.

It is meant to improve clarity, not to judge the user.

## Example Prompt

```md
Please review my request and, if relevant, your earlier answers in this turn
with KSODI-Light before answering.

Use K/S/O/D/I:

- K = Context
- S = Structure
- O = Objectivity
- D = Clarity
- I = Information Depth

For each dimension, tell me briefly whether it is strong enough for the task.
If something is unclear, ask one clarification question or suggest one improved
version of my prompt.

Only give numeric scores if I explicitly ask for them.
```

## Optional Score Request

```md
Please also give me rough KSODI-Light scores.

Score each operator separately from 0-5:

- 0 = not usable for the current task
- 1-2 = weak or unclear
- 3 = usable
- 4 = strong
- 5 = fully usable for the current task

Then give the total KSODI-Light orientation score from 0-25 and explain which
dimension would improve machine-processability most for this turn.
```

## Scoring Note

In KSODI-Light, each operator is scored on a 0-5 scale.

The total score is the sum of the five operator scores:

```text
K + S + O + D + I = 0-25
```

The score does not judge the user. It indicates how usable the current prompt
or request is for structured machine processing in the given task context.

## Boundary

This feedback example does not perform Standard-Eval, Full evaluation or
observer-based monitoring. It only helps the user make a request clearer and
more useful for the current interaction.
