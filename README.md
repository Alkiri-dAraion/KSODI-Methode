[cc-by]: http://creativecommons.org/licenses/by/4.0/
[cc-by-badge]: https://i.creativecommons.org/l/by/4.0/88x31.png
[cc-by-shield]: https://img.shields.io/badge/License-CC%20BY%204.0-lightgrey.svg

[banner-image]: https://raw.githubusercontent.com/Alkiri-dAraion/KSODI-Methode/main/ksodi-lab-banner.png

![KSODI / IDAS – Möbius Concept Banner][banner-image]


[![CC BY 4.0][cc-by-image]][cc-by]
<br>
This work is licensed under a [Creative Commons Attribution 4.0 International License][cc-by].

## CC-License

This work, *KSODI – Method for Structuring and Optimising Human-AI Interactions* © 2024 by  
Anne Steinacker-Folkerts, Heiko Folkerts, and Silke Honerkamp is licensed under CC BY 4.0.  
To view a copy of this license, visit [![CC BY 4.0][cc-by-shield]][cc-by] .


## Contributions

Developers are welcome to contribute code, provide feedback, or implement the method in their own systems. Pull requests are appreciated.  
Special thanks to Benjamin Gage-Prater and Patrick Barthelmäs (platform & integration support) and the "KSODI-Light-Agent"-PoC:
[KSODI-Light-Agent PoC (GitHub)](https://github.com/blackbaddl13/r-KSODI-POC)

## Invitation for Research & Feedback

**Multidisciplinary collaborators** are invited to explore KSODI (CSOCI in English) in the context of user experience enhancement and preference-based suitability — including psychological perspectives such as C.G. Jung. (Important: MBTI / G.P.O.P (Golden) in this context explicitly used as a *preference-test* )  
We warmly welcome contributions that explore its effectiveness across different user groups.
<br>

*full english version under the **EN** - all Sections under construction)*


[cc-by-image]: https://raw.githubusercontent.com/Alkiri-dAraion/KSODI-Methode/main/ksodi-lab-banner.png


________________________________________________________________


## From KSODI to IDAS

The **KSODI Method** originated as a structured approach to improve the clarity, precision and quality of human–AI interaction.

As practical applications evolved — from individual prompt usage to continuous, agent-based and organizational AI systems — it became clear that isolated evaluation was no longer sufficient.

To address this, KSODI was embedded into a broader framework:

**IDAS – Interactive Dialog, Analytics & Steering**

IDAS provides the architectural, temporal and governance-oriented context in which KSODI operates today.  
While KSODI defines *what can be observed*, IDAS defines *how observation, analysis and stabilization are applied over time*.

The following sections describe the IDAS Framework and explain how KSODI and SIRA work together as part of a coherent governance and early-warning approach.


# IDAS Framework

### Interactive Dialog, Analytics & Steering

*(with KSODI & SIRA)*

---

## Overview

The **IDAS Framework** is a governance-oriented framework for the **observation, analysis and stabilization of human–AI interactions over time**.

It is designed for contexts in which AI systems are used **continuously, dialogically or autonomously** — such as:

* enterprise environments
* public administration
* healthcare and regulated domains
* agent-based or multi-agent systems

IDAS does **not** evaluate content, decisions or correctness.
Instead, it focuses on **observable interaction structure**, enabling:

* explainability
* early detection of drift
* stability monitoring
* and privacy-preserving AI governance

---

## Why IDAS exists

Most AI evaluation approaches focus on **individual outputs**:

* accuracy
* correctness
* latency
* confidence scores

These metrics are useful — but they fail to capture what actually causes many real-world problems.

In practice, issues rarely arise from a single wrong answer.
They emerge **gradually**:

* context shifts without being noticed
* assumptions change implicitly
* task boundaries blur
* systems remain formally “correct” but drift away from their intended goal

IDAS addresses this gap by treating **interaction itself** as an observable process — not as isolated events.

The key question is not:

> *Is this answer correct?*

but:

> *Does the system remain coherent, stable and aligned within its intended reference and goal space over time?*

---

## Core components

IDAS consists of three tightly connected elements:

### KSODI – Semantic Observation Model

**KSODI** structures interaction quality using **five observable dimensions**:

1. **Context**
2. **Structure**
3. **Objectivity**
4. **Clarity (Distinctness)**
5. **Information Content**

These dimensions form a **semantic observation field**.

Important:
KSODI does **not** interpret meaning.
It measures **how interaction behaves**, not *what it says*.

This allows:

* separation of individual user fields
* separation of agent behavior
* separation of system-level effects

without mixing identities, content or intent.

---

### KSODI Variants

KSODI is available in three clearly separated variants:

#### KSODI-Light

* supports humans in formulating clearer prompts
* improves explainability and AI literacy
* helps users understand why interactions succeed or fail
* improves prompt quality **over time**, often reducing token usage
* suitable without the full framework

KSODI-Light does **not** judge people or answers — it supports learning.

#### KSODI-Standard-Eval

* numeric, model-agnostic evaluation
* designed for agent systems and continuous interaction
* enables early detection of drift
* auditable and suitable for governance contexts

#### KSODI-Full

* extended analysis of dynamics, transitions and resonance
* long-term observation of interaction patterns
* supports architectural and governance decisions
* explanatory, not normative
* never decision-making

---

### SIRA – Structured Interaction & Resonance Analysis

**SIRA** provides the temporal and structural protocol layer for IDAS.

It enables:

* observation across time
* comparison of interaction states
* detection of gradual change rather than sudden failure

Together with KSODI, SIRA allows IDAS to function as a **continuous early-warning and explainability system**.

---

## Observation instead of evaluation

A central design principle of IDAS is a **methodological perspective shift**.

Instead of evaluating answers, IDAS observes:

* how context is formed
* how structure evolves
* how clarity increases or degrades
* how interaction remains aligned — or drifts

This approach has several consequences:

* it works with API black boxes
* it is independent of model vendors
* it does not require content access
* it detects problems **before** they become visible as errors

Responsibility, decisions and actions remain **explicitly outside** the framework.

---

## Context, hallucinations and drift

Missing or unstable context is one of the main causes of:

* hallucinations
* incoherent answers
* over-confident but incorrect responses

Similarly, poorly structured prompting can push systems into unstable interaction patterns — even when models themselves function correctly.

KSODI does not attempt to suppress or “punish” such behavior.
It **observes** it.

KSODI-Light helps humans improve prompt quality.
KSODI-Standard and Full make drift and instability **visible early**, before operational or safety issues arise.

---

## Privacy & data protection by design

IDAS is built on a strict **observation-only principle**.

* no chat content storage
* no semantic interpretation of personal data
* no user profiling

KSODI and SIRA operate on **numeric values and observable patterns only**.

This makes IDAS suitable for:

* sensitive environments
* regulated domains
* governance and compliance contexts

---

## Agent systems & early drift detection

IDAS is particularly suited for observing autonomous or semi-autonomous agents.

Example:

> An agent originally designed for orthopedic medication ordering
> gradually shifts toward cardiology-related ordering behavior.

Without reading a single message, IDAS can detect:

* structural change
* goal drift
* tonal or interaction instability

This enables **early intervention** instead of post-incident analysis.

---

## Formal foundation & implementability

KSODI is defined with a **clean mathematical structure** and is fully implementable in software systems.

During development, the method was approached from both perspectives:

* developer-centric (signals, metrics, integration)
* user-centric (clarity, explainability, interaction quality)

Only by stepping back from both views and focusing on **observation across the five KSODI operators** did the relative nature of reference frames and goal spaces become visible.

---

## Ethics & scope

IDAS and KSODI are designed as:

* observation and early-warning tools
* learning and explainability instruments
* governance-supporting frameworks

They are **not**:

* decision systems
* control mechanisms
* behavior enforcement tools

A clear ethical framework ensures responsible usage.
(See dedicated documentation for details.)

---

## Status

The framework is actively developed and used in real-world contexts.
Documentation, examples and further technical details are continuously expanded.

