### IDAS Framework – Public Orientation Note

*Interactive Dialogue, Analytics & Steering (IDAS)*  
Author: Anne Steinacker-Folkerts, Heiko Folkerts

---

## Version Note

This file is a public orientation note. It does not define the current private
KSODI 3.5 reference mathematics.

The public wording has been updated to align KSODI-Light with the current
understanding of a **reflective working agreement**: KSODI-Light can reflect
user input, assistant output and the shared interaction state. Formal numeric
observer layers remain separate.

---

## Changelog – Public Orientation Update

- **Two-phase interaction model**
  - Phase 1: reflective exploration space
  - Phase 2: productive interaction space

- **Clarified architecture**
  - IDAS = interaction architecture
  - KSODI = structural observation method
  - SIRA = interaction protocol

- **Clear separation between**
  - observation (observability)
  - steering (control mechanisms)

- **Clarified KSODI-Light boundary**
  - KSODI-Light = prompt-level reflective working agreement
  - Standard-Eval / Full = formal observer and monitoring layers

---

# IDAS in One Sentence

**IDAS is an architectural framework for structuring, observing and optionally steering human–AI, human-agent and agentic interaction over time.**

It integrates three elements:

| Component | Role |
|---|---|
| KSODI | structural observation method |
| SIRA | interaction protocol |
| IDAS | architectural integration |

---

# Architectural Principle

IDAS intentionally separates three layers of interaction analysis:

1. **Explainability and reflective working agreement**
2. **Observability**  
3. **Optional steering**

This separation ensures that observation and control remain distinguishable.

In this public repository, KSODI-Light belongs to the first layer. It can guide
the interaction from inside a user, account, developer or system prompt. It is
not an external observer by itself.

## From Light to Observer Architecture

KSODI-Light is the practical root layer. It makes the shared interaction frame
explicit before formal mathematics or observer infrastructure is introduced.

For simple chatbot architectures, this prompt-level working agreement may be
sufficient. For MoE systems, multi-agent constellations, tool-using agents or
robotic settings, it is usually not enough to rely on local instructions alone.
In those settings, Light can provide orientation inside the agent or user
interaction while Standard-Eval, KSODI-Full or IDAS-level observers provide a
separate monitoring layer.

The observer does more than collect logs. It asks which interaction conditions
are changing: whether context is drifting, structure is weakening, grounding is
missing, clarity is collapsing, informational movement is becoming repetitive,
or relational coupling between entities is leaving a defined corridor.

This makes IDAS a bridge between AI literacy, interaction design and
governance-oriented AI observability.

---

# Relationship to Existing Evaluation Methods

IDAS and KSODI do **not replace existing evaluation methodologies**.

The framework intentionally builds on concepts already used in:

- prompt evaluation
- interaction analysis
- system observability
- drift detection
- human–computer interaction research

Many mathematical elements therefore rely on established techniques such as:

- vector spaces
- distance measures
- sequence analysis
- statistical distributions

KSODI primarily contributes **a structured way of combining these techniques into a coherent interaction model.**

---

# Two Phases of Interaction

IDAS distinguishes two interaction environments.

## Phase 1 – Reflective Space

A protected exploratory environment.

Characteristics:

- experimentation
- open thinking
- idea generation
- iterative dialogue
- reflective working agreement between user and assistant

This phase is **not intended for formal observer-based monitoring or
governance evaluation**.

Its purpose is cognitive exploration and interaction clarification.

KSODI-Light may be used here as a prompt-level reflective frame. It can help
user and assistant notice missing context, unclear structure, weak grounding or
answers that do not fit the shared task.

---

## Phase 2 – Productive Interaction Space

A structured environment where interaction becomes observable.

Characteristics:

- structured prompts
- analyzable interaction states
- reproducible outputs
- defined observation boundaries

Only this phase is suitable for system-level observer evaluation.

---

# KSODI – Structural Observation Model

KSODI provides a structured way to observe interaction states.

Five operators describe interaction structure:

- **K — Context**
- **S — Structure**
- **O — Objectivity / grounding**
- **D — Clarity**
- **I — Information Depth**

At the KSODI-Light level, these operators can be used as coarse orientation
signals, for example on a 0-5 scale per operator.

In formal observer layers, operator values may be normalized into numeric
representations such as:

```text
[0,1]
```

Together they form the interaction state vector:

```text
Z = (K,S,O,D,I)
```

From this vector further observable interaction structures can be derived.

At the Light level, K/S/O/D/I may refer to:

- user input,
- assistant output,
- the shared interaction state across a turn.

This is why KSODI-Light should not be read as scoring only the user's prompt.
It is better understood as a reflective working agreement for keeping the
interaction understandable, grounded and task-fit.

---

# Observability vs Steering

A central design principle of IDAS is the separation between:

**Observation**

and

**Control**

### Observability

The system describes interaction states.

Examples include:

- state vectors
- interaction distributions
- interaction dynamics
- drift over time

No normative judgement is applied.

---

### Steering

Steering is possible but **not part of the core observation model**.

Control mechanisms arise only when thresholds or policies are introduced.

Examples:

- drift alerts
- anomaly detection
- workflow automation
- fallback behavior

These mechanisms are external to the core observation model.

Prompt-level guidance in KSODI-Light should be distinguished from formal
observer-based steering. Light can ask for clarification or define simple
fallback behavior inside an instruction frame. External monitoring and
auditable intervention belong to Standard-Eval, KSODI-Full or IDAS-level
implementations.

---

# SIRA – Interaction Protocol

While KSODI describes interaction structure, SIRA describes **interaction practice**.

SIRA is a lightweight protocol for structured dialogue.

Steps:

- **Signal** – structural markers in interaction
- **Intention** – clarify purpose
- **Resonance** – verify mutual understanding
- **Adjustment** – allow adaptation and iteration

The protocol does not enforce behavior but encourages structured interaction.

At the KSODI-Light level, SIRA can support the reflective working agreement:
signals are noticed, intention is clarified, fit is checked and the interaction
can be adjusted without treating feedback as blame.

---

# Emergence and Interaction Dynamics

Complex interaction patterns may emerge when structured observation and interaction protocols are combined.

However:

The framework does **not assume or guarantee emergent properties**.

Emergent behavior is treated as an empirical observation that must be critically examined.

---

# Vision

IDAS approaches interaction not as a linear chat log but as a navigable interaction space.

In future systems this could enable:

- interaction maps
- project-level interaction analysis
- visual exploration of dialogue structures

As a long-term working hypothesis, KSODI-Light plus external observer layers
may also become relevant for language-, vision-language- or
vision-language-action-based interaction layers in robotic or embodied agent
contexts. This is a future research direction, not a current implementation
claim.

KSODI is not a robotics controller and not a world model. It does not replace
robotics middleware, sensor-level perception, motion planning, collision
avoidance, emergency mechanisms or physical safety systems.

The possible KSODI layer would be communicative and task-related interaction
orientation: whether the system still shares enough context with humans, keeps
the task structure clear, grounds statements or requests sufficiently, and
remains within defined or empirically learned interaction corridors over time.
In embodied or n-entity environments, this would require separate validation and
may require complex observer forms.

The long-term goal is to make human–AI, human-agent and agentic interaction **more transparent, structured and understandable**.
