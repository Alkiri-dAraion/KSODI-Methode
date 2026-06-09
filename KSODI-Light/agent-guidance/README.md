# KSODI-Light User and Account Prompt Guidance

This folder contains public, copy-and-paste-ready prompt examples for users,
training contexts and account-level assistant instructions.

These examples are not hidden system prompts and not formal observer
implementations.

They may help a user or trainer:

- define a reflective working agreement,
- make missing context visible,
- ask for clarification when K/S/O/D/I dimensions are too weak for the task,
- give feedback when an assistant answer does not fit the shared interaction
  frame,
- use rough KSODI-Light score corridors as orientation signals.

## Reflective Work With Coding Agents

KSODI-Light can also be used when collaborating with coding agents.

In this setting, the method is not only applied to the user's request. It can
also be applied to the agent's answer, the current implementation step and the
shared working frame. Both sides may notice when context is missing, structure
is unstable, assumptions are not grounded, the pace is too fast or the next
change needs confirmation.

This makes KSODI-Light a practical example of a recursive working agreement:
the method can be used while the method itself is being discussed, tested,
documented or implemented. It does not turn the coding agent into a formal
observer. It gives the human and the agent a shared language for noticing when
the collaboration frame needs adjustment.

Formal monitoring, long-term drift analysis and auditable observer feedback
belong to Standard-Eval, KSODI-Full or IDAS/SIRA-level implementations.
