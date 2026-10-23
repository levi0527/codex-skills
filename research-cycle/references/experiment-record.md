# Experiment protocol and evidence ledger

Use one record per experiment, adapted to the project's existing files. Fill the protocol before execution and complete its result fields afterward. An absent measurement stays unknown. This template authorizes no run, budget extension, reset of a closed budget or external publication.

## Protocol

```yaml
identity:
  question: null                 # one falsifiable hypothesis
  task_and_capability_level: null # current milestone, final goal and diagnostic scope
  code_config_assets: null       # version, commit, dirty diff and relevant hashes
  checkpoint_lineage: null       # initializer, retained updates, optimizer/normalizer state
  evidence_locations: []         # private project paths; sanitize before sharing
design:
  hypothesis: null
  alternatives: []
  falsifying_observation: null
  intended_intervention: null
  matched_control: null
  fixed_variables: []            # exogenous task, state, information, actions, constraints
  privileges_and_extra_compute: []
  actual_optimizer_and_objective: null # inspected implementation/version, not a label
  predicted_mechanism: null      # event -> objective -> gradient -> update -> function
data:
  independent_unit: null         # source trajectory / collection batch / independent trial
  source_groups_and_splits: null # isolate related clips; identify development reuse
  events_clips_independent_sources: null # separate counts, not interchangeable N
  leakage_and_reset_audit: null  # verified evidence, risk or unknown
  coverage_axes: []             # position, timing, direction, speed, racket, ready/recovery
exposure:
  arms_seeds_initial_states: null
  samples_updates_epochs: null
  budget_and_authorization: null # train/diagnostic/eval reserve, resource/time limits
  evaluation_points: []
  comparable_exposure_rule: null # handling unequal early stops and selected checkpoints
decisions:
  implementation_data_validity: null
  hard_severe_event_protection: null
  ordinary_learning_failure_response: null
  functional_metrics_and_denominators: null
  promotion_rule: null
  stop_loss_rule: null
  post_stop_diagnostic_or_evaluation: null # only if validity and authorization permit
  next_action_for_each_outcome: null
```

Derive thresholds, seeds, exposure and budgets from the task's constraints and baseline. Do not fill these fields with historical constants by default. Record any revision, its reason and timing; a new criterion does not erase an earlier failed registered criterion.

## Results in the same record

```yaml
results:
  actual_intervention: null     # measured activation, exposure and deviations
  actual_samples_and_budget: null # consumed vs retained training; no pooling unlike lineages
  actual_optimizer_steps: null
  independent_functional_evaluation: null
  outcomes_and_uncertainty: null # per-arm/seed, confidence appropriate to independent units
  all_terminations: null        # success/failure/truncated/unknown, counts and denominator
  selected_checkpoint_and_rule: null # distinguish endpoint and posthoc best selection
  artifacts: []                # raw episodes, manifest, command, hashes; stay in project
  implementation_status: null
  experiment_validity: null
  capability_gate_status: null
  budget_status: null           # open/closed under actual authorization
inference:
  observations: []
  supported_conclusions: []
  unsupported_conclusions: []
  confounds_and_unresolved_alternatives: []
  next_falsifying_experiment: null # bounded proposal, not automatic execution permission
```

## Compact claim ledger

| Claim and scope | Type | Evidence and counterevidence | Independent unit / exposure | Status and limit | Next falsifier |
| --- | --- | --- | --- | --- | --- |
| State a task/version/distribution-specific claim | Observation / causal attribution / hypothesis | Exact artifact and measurement; include contrary results | Source groups, seeds, retained lineage and comparable budget | Supported / contradicted / untested; what is not established | Smallest experiment that could overturn the judgment |

Preserve this distinction in prose: “The objective activated and parameters changed” is an observation; “the intervention improved return quality versus matched controls” requires functional outcome evidence and uncertainty; “a shared gradient caused the failure” remains a hypothesis without a discriminating intervention.

## Closeout review

- Does the actual intervention match the hypothesis and control, including initial states, clocks, privileges and exposure?
- Do measurements establish the named capability level, and are all terminations and unknown endings accounted for?
- What improved relative to both the matched control and starting checkpoint? What remains unsupported?
- Did the experiment distinguish the live explanations? If not, specify the confound or missing measurement rather than inventing a cause.
- Is the next action within existing authorization and an open budget? A tested narrow repair can proceed within scope; a stopped/closed campaign does not restart itself.

For public skill maintenance, distill only reusable methods and necessary de-identified examples. Keep raw logs, weights, credentials, personal/company details and internal records in the project. Put any retained historical version defect or numerical threshold in a labeled non-default case with its applicability and unresolved limits.
