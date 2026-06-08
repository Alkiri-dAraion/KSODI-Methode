# KSODI-Light Method Comparison

This note compares KSODI-Light with common prompting methods.

It is intended as public orientation material under CC BY 4.0. It does not
define the formal Standard-Eval or KSODI-Full mathematics.

## Short Comparison Matrix

| Method | Main purpose | Typical structure | Best suited for | Limitation |
|---|---|---|---|---|
| KSODI-Light | Reflective working agreement and prompt-level guidance | Context, Structure, Objectivity, Clarity, Information Depth | Learning, AI literacy, assistant guidance, bidirectional feedback, disclosed score corridors | Coarse and didactic unless connected to formal observer layers |
| RTF | Preparing a clearer prompt before asking | Read, Think, Formulate | Quick self-check before submitting a request | Linear; does not observe interaction dynamics over time |
| STAR | Structuring a situation or experience | Situation, Task, Action, Result | Case descriptions, interviews, retrospectives, incident reports | Strong for narrative structure, weaker for ongoing human-AI interaction quality |
| Iterative Prompting | Improving results through repeated refinement | Ask, review, adjust, ask again | Exploration, drafting, debugging, creative work | Depends on user judgement; lacks a stable dimension set unless one is added |
| Chain-of-Thought prompting | Encouraging stepwise reasoning behavior | Request a stepwise solution or rationale | Complex reasoning tasks and transparent problem solving | Should not be used to demand hidden model reasoning; better request concise rationale or verifiable steps |
| Self-Consistency | Comparing multiple generated answers | Generate variants, compare convergence, select stable answer | Reducing uncertainty in reasoning or classification tasks | Computationally heavier; compares outputs but does not structure the original interaction frame |

## What Makes KSODI-Light Different

Most prompting methods help a user formulate or refine a single prompt.

KSODI-Light adds a stable reflection grid:

```text
K = Context
S = Structure
O = Objectivity
D = Clarity
I = Information Depth
```

This makes interaction quality discussable across prompts, answers, users,
agents and training contexts.

KSODI-Light can be used in three public-facing ways:

- user and assistant feedback: the interaction partners can improve a request,
  answer or shared turn,
- account prompts: a user defines a reflective working agreement,
- developer or system-prompt guidance: an agent creator embeds disclosed
  K/S/O/D/I expectations or fallback behavior.

At this level, score corridors are orientation signals, not formal governance
metrics.

## Score Corridors Compared With Prompt Templates

Prompt templates such as RTF or STAR mainly define the shape of an input.
KSODI-Light can also reflect whether the answer and the ongoing turn still fit
the intended task.

KSODI-Light can also define an expected quality corridor, for example:

```text
K=4, S=4, O=3, D=4, I=4
```

Such a corridor does not mean that every task needs the same values.

Examples:

- science-fiction discussion may allow lower objectivity and more imaginative
  framing,
- image documentation may require higher objectivity and clarity,
- research or governance contexts may require strict grounding and source
  boundaries.

The corridor should be disclosed and adapted to the domain.

## Boundary to Standard-Eval and KSODI-Full

KSODI-Light operates at prompt and interaction level.

It can guide behavior from inside a prompt, but it does not perform formal
external monitoring.

Formal observer architectures may add:

- numeric trajectories,
- drift observation,
- corridor movement over time,
- dyadic or n-adic comparison,
- audit and governance feedback.

Those functions belong to Standard-Eval, KSODI-Full or IDAS/SIRA-level
implementations.

## Practical Reading

Use RTF or STAR when a user needs a quick template.

Use iterative prompting when the answer must be explored and improved over
several turns.

Use Chain-of-Thought style prompting carefully: request concise reasoning,
checks or verifiable steps instead of hidden internal reasoning.

Use KSODI-Light when the goal is to make interaction quality explicit,
repeatable and teachable across users, tasks, assistant outputs and assistant
configurations.
