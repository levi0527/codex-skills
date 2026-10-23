---
name: research-cycle
description: Plan and execute bounded robotics/RL training, evaluation, and physical-contact experiments. Use for hypotheses, run design, simulator regression checks, evidence capture, and milestone closeout; not ordinary documentation edits.
---

# Research cycle

Use the active project's own plan, runtime contract, and acceptance criteria. Inspect installed files under `references/` and read an applicable local project profile when present. Project profiles and historical gates apply only to their named task; do not transplant metrics, architecture constraints or old directory paths into another project.

Use [the experiment protocol and evidence ledger](references/experiment-record.md) for each experiment, in the project's existing record format. Register the hypothesis, actual intervention, matched control, fixed variables, independent samples/seeds, budget and decision rules before running; close the same record with results, supported and unsupported conclusions, confounds and a falsifying next experiment. Observations, causal attribution and hypotheses are distinct.

For fine-tuning, curriculum changes, or inherited-policy regressions, use the [RL training experiment template](references/rl-training.md). First identify the current version's actual optimizer and objective from implementation; its PPO/value-specific sections apply only when those mechanisms are present. It does not prescribe universal reward weights or training budgets.

For contact-rich training automation or policy delivery, read a local `references/validated-pipeline.md` if installed. Its optional executor requires project-specific task adapters and capability gates; this workflow does not require that executor.

When a proposed direction rests on a disputed assumption or repeated inconclusive runs, use the available `review-experiment` design-challenge mode before expanding it. When validated evidence exposes a defective skill rule, use `reflect-skills` under existing maintenance authorization, then resume the experiment rather than turning reflection into an open-ended prerequisite.

## Before a run

1. Identify the relevant milestone and capability gate, its current evidence, one falsifiable hypothesis, and a success/failure rule. Define a bounded budget, evaluation points, promotion/stop rules and next action for either outcome. Separate implementation/data validity, severe-event protection, ordinary learning failure, scientific promotion, and budget/authorization. An unadapted policy need not pass final product criteria before learning; final distant goals need not gate every early diagnostic.
2. Record task, obs/act dimensions and order, coordinate/quaternion conventions, action scale, reset/phase clocks, seed, checkpoint, actual GPU, code commit plus dirty diff, configuration and asset/reference hashes. A dimension match alone does not validate geometry or semantics.
3. Choose the smallest intervention that distinguishes live alternatives. Reuse applicable evidence; do not repeatedly probe a demonstrated capability. Keep A/B exogenous tasks, initial states, available information, action authority, execution constraints and training exposure matched except for the intended variable; disclose privileges and extra computation. For racket-return capability, use review-experiment's [progression guide](../review-experiment/references/racket-progression.md).
4. For changes to reset, contacts, clocks or reward activation, run a relevant bounded regression and actual simulator lifecycle check: reset, step, reset after stepping, partial reset when applicable, repeated episodes. Check actual reward activation and tensor aliasing, not only configuration values. Scale tests to the change.

## Execute within the requested scope

Record the reproducible command, environment and assigned GPU. Check actual free resources before launch. Do not escalate a short run into long training, expand a matrix, or start real robot motion based solely on this skill. Follow the user's existing authorization and the project's runtime constraints.

Prefer a coherent bounded continuation with registered evaluation points to fragmented restarts. Set numerical limits from the task, baseline and available resources; historical thresholds are not defaults. After testing a narrow engineering repair already within scope, continue the authorized plan without inventing repeat approvals. Changes to task, physics, protections or budget follow the actual authorization boundary. Closed budgets are not reusable automatically. After a severe anomaly, stop the affected execution and choose a bounded diagnostic among candidate mechanisms; do not let repeated patches consume the main experiment indefinitely.

## Close the loop

Compare intended and measured intervention exposure, train/eval parity, checkpoint-restored RNG and matched initial states. Separate an invalid run from a negative scientific result. Distinguish measured facts, supported inference and unresolved alternatives; contact, reference tracking, proxy score, GPU utilization or a running process do not establish final functional success. Fixing a protection anomaly is implementation closure, not functional acceptance.

Keep raw episodes, manifest, configuration, command, logs and a concise closeout in the project's experiment location. Closeout: hypothesis → implementation/check → measured exposure → task outcome → supported inference / remaining alternative → bounded next action. Update the linked milestone and daily plan only to the extent justified by evidence. New candidate ideas remain proposals until their entry conditions are satisfied.

When skill maintenance is requested or already authorized, distill demonstrated decision rules after closing the experiment. Keep task-specific constants and evidence links in the project profile; distinguish a useful diagnostic from a proven training improvement. Narrowly amend existing guidance rather than accumulating a new mandatory checklist after each failure.
