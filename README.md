[![KSODI + IDAS Concept][banner-image]](https://github.com/Alkiri-dAraion/KSODI-Methode)

[banner-image]: https://raw.githubusercontent.com/Alkiri-dAraion/KSODI-Methode/main/assets/images/ksodi-lab-banner.png

________________________________________________________________

⚠️ This documentation includes hypothesis-oriented material (written in the conditional / Konjunktiv), reflecting ongoing empirical exploration of the KSODI model.  

⚠️ **Research-only notice:** The public KSODI Standard-Eval / Full materials in
this repository are provided for conceptual review, discussion and research
orientation only. They should not be used as an implementation reference. The
public 3.3 materials contain known structural issues, including an objectivity
operator behavior that can make measurement collapse to 0 / not measurable when
no external data source or web access is connected, as well as ambiguities in
variable handling and the unresolved public separation between Z, IK, R0,
IK_rel and the broader R-family of relational observation variants. A revised 3.5 reference specification is maintained
privately and will only be published after final testing and review.

Note:
The usual implementation setting for KSODI Standard-Eval and KSODI Full uses a two-layer or multi-layer system:
1. Agent layer (L1): KSODI-Light runs as a system prompt on one or more agents.
2. Observer layer (L2): KSODI Standard-Eval provides coherence observation for agents, with `R0` / `IK_rel` as the minimum dyadic coherence observation.
3. Full observer layer (L4): KSODI Full observes full coherence and the resonance-family layer.
4. KSODI Full with voice layer (L5): KSODI Full plus additional voice, sound and timing observation.
The observer is usually designed to give the agent feedback when it drifts out of a defined or explainable corridor.

Current line:
`Z(t)` -> `Delta Z` / `Delta2 Z` -> `IK` as monadic projection -> `R0` as relational gate -> `IK_rel` as relational projection after a stable gate -> `R_geom` as geometric coupling -> `RSigma` / `RSigma(Hangar)` -> optional: `V(t)`, `R_takt`, `R_pace` as timing and voice overlays.

# KSODI Method

KSODI is a structured observation model for human-AI, agent-agent and n-agent interaction structures, focussing on explainable governance and observability.
It is part of the IDAS-Framework.

→ See: [KSODI-IDAS-SIRA_Framework](./KSODI-IDAS-SIRA_Framework.md)

The name `KSODI` is intentionally retained from the German development
context. This is not meant as a value judgement between languages. The German
terms helped preserve conceptual precision during the early development of the
method, while English terminology supports international accessibility and
therefore requires explicit definitions. Multilingual discussion, including
French and Chinese perspectives, also helped sharpen the distinctions between
the dimensions.

The framework separates explainability, observability and advanced interaction analysis (with optional steering) into clearly defined layers - such as interaction states, interaction coherence and relational resonance-family observations - over time.

KSODI does **not** evaluate people, personalities or intentions.  
It respects maximum privacy and operates exclusively on observable interaction states.

The framework is organized into clearly separated components with different purposes and licenses.

## Where KSODI Fits

KSODI is a layered method for making human-AI, human-agent and agent-agent
interaction quality observable, discussable and steering-supportive without
reducing it to single-prompt quality or model accuracy.

It is intended to bridge three practical contexts:

- **AI literacy and training:** KSODI-Light gives users, trainers and
  organizations a shared language for context, structure, grounding, clarity
  and information depth.
- **Prompt-level agent guidance:** KSODI-Light can be embedded into user,
  account, developer or system-prompt settings as a disclosed reflective
  working agreement with lightweight corridors and fallback behavior.
- **AI observability and governance:** KSODI Standard-Eval, KSODI Full and
  IDAS/SIRA-level implementations extend the same operator logic into numeric
  observer layers for drift, coupling, corridor exits and longer-term
  interaction monitoring.

KSODI is not presented as a complete alignment solution. It is a structured way
to reason about interaction conditions, drift, corridors and coupling in a form
that remains understandable for humans while remaining compatible with
machine-readable observation.

## Structure

### KSODI-Light
Human-facing and prompt-level variant.
Designed for learning, AI literacy, prompt clarity improvement and lightweight
guidance through disclosed K/S/O/D/I expectations or score corridors.
It can be used as a reflective working agreement in user/account prompts or
embedded by agent creators in developer/system-prompt configurations.
KSODI-Light can reflect user input, assistant output and the shared interaction
state across a turn. Formal observer-based monitoring belongs to Standard-Eval,
KSODI-Full or IDAS/SIRA-level implementations.
→ See: [KSODI-Light](./KSODI-Light)

License: Creative Commons Attribution 4.0 (CC BY 4.0)

---

### KSODI Standard-Eval & KSODI Full
Evaluation-oriented and governance-capable variants.  
Designed for numeric observability, drift detection and system-level stability monitoring with optional steering.
The public materials are not intended for implementation. KSODI 3.5 is the
current private reference specification described in the paper draft and is
intended to resolve known 3.3 ambiguities between interaction coherence and
relational resonance-family observation.
→ See: [KSODI-Eval-Variants](./KSODI-Eval-Variants)

License: Commercial / All rights reserved.

---

## About

KSODI focuses on structured observation across five operators:

- Context  
- Structure  
- Objectivity  
- Clarity  
- Information Depth  

The broader architectural framework integrating KSODI is referred to as IDAS (Interactive Dialog, Analytics & Steering).

For a public development and contribution overview, see:
[KSODI Development Timeline](./docs/timeline/KSODI_Timeline_since_2024-11.md)
([German version](./docs/timeline/KSODI_Timeline_seit_2024-11.md))

For the project origin note and personal context, see:
[ABOUT.md](./ABOUT.md)

---

## Licensing

This repository contains components under different licenses.  
Each folder contains its own LICENSE file.

Unless explicitly stated otherwise in a subfolder license,  
all rights are reserved.

For licensing inquiries, integration, whitelabeling or enterprise adoptions please contact:
ksodi@thevoid.email with details on intended use case.


The public KSODI 3.3 materials are preserved for transparency and research
orientation, but contain known structural issues and should not be used for
implementation.

KSODI 3.5 is the current private reference specification and will only be
published after final testing and review.

---

© 2026 Anne Steinacker-Folkerts & Heiko Folkerts
