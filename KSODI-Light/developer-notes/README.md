# KSODI-Light Developer and System-Prompt Notes

This folder contains public notes for developers, trainers and agent creators
who want to embed KSODI-Light guidance into assistant or system-prompt
configurations.

At this level, KSODI-Light may define:

- K/S/O/D/I expectation corridors,
- task-specific fallback behavior,
- clarification rules,
- domain-dependent objectivity or grounding requirements.
- bidirectional feedback rules for user input, assistant output and the shared
  interaction state.

This is prompt-level steering. It can guide an assistant from inside its
instruction frame.

It is not the same as an external KSODI observer. Observer-based monitoring
evaluates trajectories from outside the prompt, records drift over time and
belongs to Standard-Eval, KSODI-Full or IDAS/SIRA-level implementations.
