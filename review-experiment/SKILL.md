---
name: review-experiment
description: Audit robotics/RL experiment results for validity, causal claims, contracts, and whether the next GPU budget is justified. Use when reviewing logs, checkpoints, reports, or experiment plans.
---

# Review experiment

Do not modify application code during a result review unless the user asks for a fix.

Check, in order:

1. Identity: task, route, checkpoint, commit/diff, config digest, seed, GPU, transitions, and output path.
2. Exposure: what command/offset distribution the policy actually saw, not only the requested CLI or stage label.
3. Contract: observation/action dimensions, frame and quaternion convention, raw action scale, true shuttle launch, reference impact clock, reset and auto-reset provenance.
4. Measurement: episode-level C0, impact position, outgoing direction/speed, fall/timeout, and units. Check that paired rows share the intended initial state.
5. Inference: separate measured facts, supported interpretation, unresolved alternatives, and invalid-run conditions.
6. Decision: whether the result supports the registered gate, requires one bounded diagnostic, or justifies more seeds/coverage. Keep the next spend smaller than the evidence it is meant to obtain.

7. Implementation closure: compare measured activation/exposure with the intended intervention. For a proposed bug fix require a relevant regression check plus a bounded real runtime check for simulator lifecycle changes. Return to the original hypothesis after validation; do not substitute a new experiment plan for proving that the modified code behaves as intended.

8. Milestone position: every review must state the current V2 milestone, its registered gate, the evidence status (`planned`, `ready`, `running`, `measured`, `passed`, `blocked`, or `invalid`), what this run unlocks, and the smallest remaining blocker. Do not describe local training progress as milestone progress unless the gate evidence is measured.

Distinguish command target, racket sweet center, and actual contact/cork point, each with its clock. Inspect active USD/C0 geometry and filters before attributing an implausible collision to policy behavior. Train/eval launch offsets and checkpoint-restored RNG can change the experiment even when CLI seeds and labels look identical. Do not re-probe an already established capability merely to postpone the authorized next training step.

For M3.1, require raw episode records and paired `target` vs `matched_p_contact`. Compute or inspect paired ΔC0 and `K_p = Δp_impact / Δp_command`; a missing or null signed response is a diagnostic gap, not a conditioning claim. A report with `dirty=true` must preserve the actual patch or diff needed to reproduce it.

Use status words `planned`, `ready`, `running`, `blocked`, `implemented_unmeasured`, `measured`, `passed`, `invalid`, and `withdrawn`; do not use `completed` as scientific evidence.
