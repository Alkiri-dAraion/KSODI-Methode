# KSODI-Light Reflective Working Agreement Example

This example is for users who want feedback on a request, an assistant answer
or the shared state of the current turn.

It is meant to improve clarity and fit, not to judge the user or the assistant.

## Example Prompt

```md
Use KSODI-Light as a reflective working agreement.

Please review my request, your answer, or the shared state of this turn with
KSODI-Light before continuing.

Use K/S/O/D/I:

- K = Context
- S = Structure
- O = Objectivity
- D = Clarity
- I = Information Depth

For each dimension, tell me briefly whether it is strong enough for the task.
If something is unclear, ask one clarification question or suggest one improved
version of the request, answer or working frame.

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

The score does not judge the user or the assistant. It indicates how usable the
current request, answer or shared interaction state is for structured machine
processing in the given task context.

## Boundary

This feedback example does not perform Standard-Eval, Full evaluation or
observer-based monitoring. It only helps user and assistant keep the current
interaction clearer, more useful and better aligned with the task.
