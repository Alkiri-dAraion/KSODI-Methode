# KSODI-Light Prompt Feedback Example

This example is for users who want feedback on their own prompt before asking
for a full answer.

It is meant to improve clarity, not to judge the user.

## Example Prompt

```md
Please review my request (along with your earlier answers, if there) with KSODI-Light before answering.

Use K/S/O/D/I:

- K = Context
- S = Structure
- O = Objectivity
- D = Distinctness
- I = Informational Value

For each dimension, tell me briefly whether it is strong enough for the task.
If something is unclear, ask one clarification question or suggest one improved
version of my prompt.
We use a simple scoring to check, whether our : 0 = unusable, 5 = perfect.

Only give a numeric score if I explicitly ask for it.
```

## Optional Score Request

```md
Please also give me a rough KSODI-Light overall-score for a given turn from 0-25 and explain which
dimension would improve the result most.
```

## Boundary

This feedback example does not perform Standard-Eval, Full evaluation or
observer-based monitoring. It only helps the user make a request clearer and
more useful for the current interaction.
