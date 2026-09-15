---
name: research-cycle
description: Plan and execute bounded robotics/RL research experiments for Beyondmimic V2. Use when proposing, launching, or reviewing a training or evaluation run.
---

# Research cycle

Use this workflow for Badminton V2 experiments. Follow `AGENTS.md`, the V2 README, SM, and the task's single linked spec.

1. State the final-goal link (Q1–Q4) and the exact spec section/script step.
2. State one falsifiable hypothesis, expected observation, success/failure rule, budget, and the next action for both outcomes.
3. Check the runtime contract before running: task, observation/action dimensions, body frame, impact clock, raw action scale, seed, checkpoint and code digest.
4. Choose checks that distinguish live alternatives. When measured evidence already establishes local learnability, proceed to the authorized training intervention; do not repeatedly launch feasibility probes. A short implementation regression check is still required for changed reset, clocks, contacts, or reward activation.
5. For M3.1 preserve paired counterfactuals. `target` and `matched_p_contact` share reset state, shuttle, `tau`, `n`, and `v`; only shown `p_contact` changes.
6. Save evidence under `docs/badminton_v2/evidence/<Gate>/<date>_<task>/` with raw episode records, manifest, command, environment/config snapshot, and `TASK_CLOSEOUT.md`.
7. Report measured facts separately from inference. Never promote a single seed, reward, standing time, or smoke run to Pass.
8. Stop at the registered decision point. Do not expand a matrix, add a new mechanism, or spend additional GPU budget merely because a result is ambiguous; define the smallest discriminating follow-up.

9. Milestone progress: every experiment plan and review must include a short current-milestone assessment. Name the active V2 milestone and registered gate, mark its evidence status with the allowed status words, explain the direct contribution of the experiment to that gate, and identify the smallest remaining blocker. A running or successful training process does not advance a milestone to `measured` or `passed` without the gate's required evidence.

Remote runs must include a GPU assignment and a reproducible shell command. A large GPU increases parallel sample throughput and may reduce wall-clock time; it does not by itself improve PPO sample efficiency or solve reward/action-contract problems.

## Close the hypothesis–implementation–evidence loop

Before a change, write the observed anomaly, competing explanations, evidence that distinguishes them, the selected hypothesis, affected files, and the smallest intervention. Distinguish a defective objective/interface from an optimizer or network-capacity hypothesis; do not blame PPO merely because reward increased without task success.

Before GPU training, tie the scientific hypothesis to a code-level invariant and its check. For fragile simulator code verify a full lifecycle: initial reset → action/physics step → reset after stepping → partial reset → repeated episodes. Check actual reward activation and tensor aliasing, not just weights in a config. Demonstrate that a regression check detects the original defect when practical, then verify the repair in Isaac. Bound this protection to minutes rather than creating another research campaign.

For command/contact claims record three separate positions (command target, racket sweet center, actual contact/cork point) at explicitly identified times; also record signed arrival error, reference time, absolute launch offset and its delta from the training configuration. Check the active USD/contact backend, dimensions, coordinate transforms and pair filters; a URDF filename or dimension-only match is not runtime geometry validation.

After training, compare observed effects with the hypothesis AND verify that the intervention actually executed: reward nonzero fractions, command exposure, first-contact attribution, source/config hashes, reset integrity, train/eval parity, seeds after checkpoint load, and matched initial states. Separate negative scientific results from invalid implementation exposure. Retain original data; correct earlier claims openly.

Each closeout states: hypothesis → implementation → regression/Isaac validation → measured exposure → task outcome → supported inference / unresolved alternative → bounded next action. Record candidate ideas as planned appendices with entry conditions; do not silently replace the active mainline. Generic distribution priors or candidate-window interfaces require their own attribution experiment before being called innovations.
