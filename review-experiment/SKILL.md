---
name: review-experiment
description: Challenge and correct robotics/RL experiment designs, and review logs, checkpoints and reports for validity, causal attribution and capability evidence. Use when questioning a training direction, auditing results, or choosing a discriminating next experiment.
---

# Review experiment

Review evidence without changing application code unless the user requests a fix. Use the project's current acceptance criteria; inspect installed files under `references/` for an applicable local project profile and read it when present.

For optimization, conditioning, dataset independence or demonstration-prior claims, read [the causal and data audit](references/causal-review.md). For racket-return milestones and selecting the next feasibility/learning experiment, read [the progression guide](references/racket-progression.md). Record the review against the same [experiment protocol and evidence ledger](../research-cycle/references/experiment-record.md) used for planning, rather than creating a competing status ledger.

For assumptions, competing explanations, or a proposed training direction, use [design challenge](references/design-challenge.md). When correction and execution are already authorized, carry the reviewed plan into the bounded experiment; do not stop at listing objections. For an evidenced defect in the skills themselves, use `reflect-skills` when maintenance is authorized.

Check:

1. Identity: task, checkpoint, commit plus dirty diff, config and asset/reference hashes, seed, device, sample count and output paths.
2. Implementation exposure: what commands, phase transitions, offsets, rewards and contacts actually occurred, not just requested flags or training steps.
3. Contract: observation/action dimensions and ordering, coordinate/quaternion conventions, raw action scale, reset and auto-reset provenance, release/contact clocks and actual runtime geometry/filter configuration.
4. Measurement: raw episode outcomes, units, all termination reasons and denominators, failure codes and relevant confidence/coverage. Keep paired A/B initial states matched. Treat truncation or an unknown ending as its own category, not an observed success or failure. Use domain-appropriate events; do not import shuttle/racket metrics into ball grasp/throw/catch experiments.
5. Inference: distinguish measured facts, supported interpretation, unresolved alternatives and invalid-run conditions. A negative outcome does not automatically imply optimizer failure; first verify the intended intervention executed. Updates occurring, effective learning and sufficient optimization are separate claims. Training across different versions/tasks/initializers cannot be summed as convergence evidence; same-input local replay cannot establish whole-policy or closed-loop causality.
6. Gate decision: state the applicable milestone, status, what the run establishes or unlocks, the smallest blocker, and whether one diagnostic or further coverage is justified. Do not substitute process completion or reward for gate evidence.

For inherited-policy training, reconstruct the selected checkpoint's actual ancestry and retained updates separately from consumed budget, rollbacks, and diagnostics. Compare learning outcomes at matched exposure. A parent-output drift monitor measures change, not task degradation; distinguish it from an auxiliary retention loss and from physical failure. Check whether a stop skipped final frozen evaluation or the final standard log row. Rollout metrics recorded after update N usually describe trajectories collected by the policy before update N, unless explicitly measured otherwise.

Check the amplitude and provenance of evaluation noise against the actor's own training std. Separate deterministic task performance, own-noise behavior and additional stress tolerance. A stress-only failure must not be relabeled as training-distribution collapse; an own-noise pass does not erase a registered stress-gate failure.

For simulator lifecycle fixes, require relevant regression evidence and a bounded actual runtime check. Preserve raw data and corrections to earlier claims. If dirty=true, preserve the diff required to reproduce the result. Missing measurements remain unknown, never zero.

Use the project's existing status vocabulary. Separate implementation status from experiment validity and capability pass/fail. Report actionable findings with evidence location and impact, then a proportionate next step; do not launch additional runs as part of a read-only review.

Review correctness, hard protection, ordinary learning outcomes, scientific promotion and authorization separately. Distinguish measured physical penetration from FK-only geometric overlap. Retain severe-event protections while allowing valid, authorized learning below final product criteria. State whether a suspected defect is verified, contradicted or untested; do not publish a risk as a confirmed defect. Scope retained historical numbers and version-specific defects to a clearly labeled case, never a default rule.
