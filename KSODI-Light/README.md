[cc-by-badge]: https://i.creativecommons.org/l/by/4.0/88x31.png
[cc-by-shield]: https://img.shields.io/badge/License-CC%20BY%204.0-lightgrey.svg
[cc-by]: http://creativecommons.org/licenses/by/4.0/


[![CC BY 4.0][cc-by-badge]][cc-by]
<br>
The work in this folder and its subfolders is licensed under a [Creative Commons Attribution 4.0 International License][cc-by].


## CC-License

This work, *KSODI – Method for Structuring and Optimising Human-AI Interactions* © 2024 by  
Anne Steinacker-Folkerts, Heiko Folkerts, and Silke Honerkamp is licensed under CC BY 4.0.  
To view a copy of this license, visit [![CC BY 4.0][cc-by-shield]][cc-by] .


## Contributions

Developers are welcome to contribute code, provide feedback, or implement the method in their own systems. Pull requests are appreciated.  
Special thanks to Benjamin Gage-Prater for early RAG testing and feedback, and to Patrick Barthelmäs for platform and integration support, including the [KSODI-Light-Agent PoC (GitHub)](https://github.com/blackbaddl13/r-KSODI-POC).

## Invitation for Research & Feedback

**Multidisciplinary collaborators** are invited to explore KSODI (CSOCI in English) in the context of user experience enhancement and preference-based suitability.
<br>

[cc-by-image]: https://raw.githubusercontent.com/Alkiri-dAraion/KSODI-Methode/main/assets/images/ksodi-lab-banner.png


# KSODI-Light

KSODI-Light is the human-facing and prompt-level variant of the KSODI
observation model.

It can be used as a **reflective working agreement** between user and
assistant. In that sense, KSODI-Light does not only reflect the user's prompt.
It can also reflect assistant output, feedback from the user and the shared
interaction state across a turn.

It supports:

- clearer prompt formulation
- explainability
- AI literacy development
- structured reflection on interaction quality
- bidirectional feedback when a request, answer or shared working frame does
  not fit the task
- beginner-friendly collaboration with coding agents
- lightweight guidance when K/S/O/D/I expectations are embedded into user,
  account, developer or system prompts

KSODI-Light does not evaluate correctness and does not judge users.
It supports learning and clarity.

## Agent Literacy and Prompt Guidance

KSODI-Light can also support beginners who work with coding agents.
The examples below show how users can define reflective collaboration modes
and lightweight agent prompts without publishing private personal instructions:

- User and account prompts:
  [Coding Agent Guidance Example](./agent-guidance/coding-agent-guidance-example.md)
  and [General Assistant Guidance Example](./agent-guidance/general-assistant-guidance-example.md)
- User feedback:
  [Prompt Feedback Example](./user-feedback/prompt-feedback-example.md)
- Developer and system-prompt notes:
  [KSODI-Light Steering, Self-Alignment and Observer-Based Monitoring](./developer-notes/self-alignment-vs-steering.md)
- Method orientation:
  [KSODI-Light Method Comparison](./KSODI%20method%20comparison-EN.md)
  and [KSODI / CSOCI Terminology](./KSODI-CSOCI_EN.md)

The guidance examples are not hidden system prompts. They are public,
copy-and-paste-ready orientation prompts for user accounts, training contexts
and simple assistant setups. More specialized variants, such as research,
education, creative writing or child-friendly prompts, can be added separately.

KSODI-Light may support reflective self-alignment patterns in assistants, such
as asking for clarification, keeping uncertainty visible and adapting K/S/O/D/I
expectations to the task context.

When embedded by a user, trainer, developer or agent creator, KSODI-Light can
also support lightweight steering. Examples include:

- asking for clarification if `K`, `S`, `O`, `D` or `I` is too low for the
  task,
- using different expectation corridors for different domains,
- defining fallback behavior such as "if objectivity is too low, ask before
  answering",
- keeping the assistant inside a reflective collaboration mode.

Users can also use the same grid to give feedback when an assistant answer does
not fit the shared frame, for example because it lost context, overclaimed,
answered the wrong task or moved too quickly.

These patterns remain prompt-level guidance. They are not the same as formal
Standard-Eval or KSODI-Full monitoring.

## Score Corridors

KSODI-Light scores are coarse orientation signals.

A score corridor such as `K=4, S=4, O=3, D=4, I=4` should be read as a
context-specific expectation, not as a universal quality target.

The score may refer to user input, assistant output or the current shared
interaction state. It should always be interpreted as usability for the current
task, not as a judgement of a person.

Different tasks may need different corridors:

- creative or science-fiction discussion may allow lower objectivity while
  still requiring clear context and structure,
- documentation of an image may require high objectivity and distinctness,
- legal, medical, safety or governance contexts may require much stricter
  grounding and source boundaries.

For public examples, score corridors should be disclosed and explained. Hidden
or automated score-based intervention belongs to formal observer architectures,
not to this public KSODI-Light example set.

## Observer Boundary

An external observer can add an auditable layer around an agent. It can monitor
drift, compare trajectories over time, report corridor exits and support human
oversight.

That observer layer belongs to Standard-Eval, KSODI-Full or IDAS/SIRA-level
implementations.

KSODI-Light may guide an assistant from inside the prompt. Observer-based
monitoring evaluates behavior from outside the prompt. Both can be useful, but
they are different layers.

## Scope

Suitable for:

- individual users
- training contexts
- educational environments
- organizations introducing structured AI usage

This variant can be used independently of the full governance framework.

## License

Creative Commons Attribution 4.0 International (CC BY 4.0)

You are free to use, adapt and share this material, including commercially,  
provided appropriate attribution is given.

See LICENSE file in this folder for details.

---

© 2026 Anne Steinacker-Folkerts & Heiko Folkerts
Licensed under CC-BY-4.0
