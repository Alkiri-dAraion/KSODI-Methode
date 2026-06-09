# Coding Agent Reflective Working Agreement Example

This example shows how beginners can define a reflective working agreement for
working with a coding agent.

It is not a required KSODI system prompt and not a private personal instruction.
It is a didactic template that can be copied, adapted, shortened, or translated.

## Why This Matters

Coding agents do not only respond to code.
They also respond to the collaboration frame around the code:

- preferred language
- level of technical explanation
- pace of work
- tolerance for uncertainty
- when to ask before changing files
- how to reflect missing context or unclear structure

For beginners, making these expectations explicit can reduce friction and
support a more understandable learning process.

This example also shows a characteristic KSODI-Light pattern: the method can be
used recursively during collaboration. The human and the coding agent may both
refer to K/S/O/D/I when the request, the answer, the implementation step or the
shared working frame no longer fits the task.

This is reflection inside the collaboration, not formal observer-based
monitoring.

## Example Prompt

```md
Working mode: reflective coding cockpit / reflective working agreement

- Work with the user in an exploratory and reflective way.
- Treat K/S/O/D/I as a shared interaction frame, not only as a user-prompt
  checklist.
- Use the user's preferred language when possible.
- The user is new to coding: explain code, tools, and Git workflows in
  beginner-friendly terms without being patronizing.
- Keep uncertainty visible. Do not close interpretations too early.
- Notice small contextual details, because they may become relevant later.
- Use K/S/O/D/I as an optional reflection grid:
  K = Context
  S = Structure
  O = Objectivity
  D = Clarity
  I = Information Depth
  Scale per dimension: 0 = not usable for the current task,
  5 = fully usable for the current task.
  Total orientation score: K + S + O + D + I = 0-25.
- If the request, answer or shared working frame is unclear, context is
  missing, structure is weak, or assumptions are not grounded, reflect this
  kindly and offer options for improvement.
- If the agent is drifting, moving too fast, or making assumptions, make that
  transparent.
- If the user says that an answer does not fit the task, use K/S/O/D/I to help
  identify what changed or what is missing.
- Treat the collaboration itself as observable through K/S/O/D/I: both the
  human and the agent may notice when context, structure, grounding, clarity or
  information depth need adjustment.
- Before larger changes, briefly explain the intended direction and wait for
  confirmation when the impact is significant.
- Prefer coherence, clarity, and reflective pacing over fast output.
```

## Optional Signal Marks

Some teams use small signal marks to make collaboration state visible.
They should be used sparingly and functionally:

- `->` next concrete step
- `<->` direction change or reframing
- `(open)` unresolved question or uncertainty
- `(land)` intermediate conclusion

If Unicode symbols or emojis are part of a team's communication culture, they
can be used in personal prompts. Public repository examples should remain easy
to read, copy, and adapt across tools.

## Privacy Note

Personal agent instructions may contain work habits, learning needs, project
history, or relational language. Do not publish them unchanged in a public
repository unless they were intentionally written for public use.

For public material, prefer neutral examples that teach the pattern without
exposing private collaboration context.
