# Self-Alignment vs. Observer-Based Steering

KSODI-Light can support reflective self-alignment patterns in assistants, such
as asking for clarification, keeping uncertainty visible, and adapting the
strictness of K/S/O/D/I expectations to the interaction context.

This is not governance steering.

Strong steering, fallback logic, corridor enforcement, drift monitoring and
observer feedback belong to Standard-Eval, KSODI-Full or IDAS-level
implementations.

## Light-Level Self-Alignment

At the KSODI-Light level, an assistant may be instructed to:

- ask for clarification when the request is unclear,
- make uncertainty visible,
- avoid judging users,
- adapt objectivity requirements to the task context,
- keep interaction quality discussable.

Examples:

- image discussion may require high objectivity and cautious identification,
- poetry or science-fiction reflection may allow lower objectivity and more
  imaginative exploration,
- research support may require explicit source boundaries and uncertainty
  labels.

These are guidance patterns, not enforced control corridors.

## Observer-Based Steering

Observer-based steering would be different.

It may involve:

- defined IK corridors,
- explicit fallback thresholds,
- drift detection,
- external feedback to an agent,
- escalation to a human or governance layer.

Such mechanisms require formal observation logic and should not be presented as
KSODI-Light functionality.

## Research Status

Prompt-score thresholds, operator weightings and observer settings should be
treated as empirical research questions.

They should be observed over time before becoming normative configuration
rules.
