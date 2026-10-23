# RL training experiment template

Use for continuing a learned robot skill, changing curriculum/rewards, or diagnosing a policy that degrades during optimization. Adapt the sequence to what is already established; do not rerun proven physics or calibration checks without a relevant change.

Inspect the active trainer/optimizer first. The PPO, critic, return and bootstrap sections below are conditional on those mechanisms actually being used; an environment step reward is not necessarily the optimized loss. Use [the shared experiment record](experiment-record.md) for the protocol and closeout and [the causal audit](../../review-experiment/references/causal-review.md) when tracing objective, gradient, conditioning or data provenance. Separate update occurrence, effective functional learning and evidence of sufficient optimization.

## Recover the actual learning problem

Define task success with physical quantities and phase-specific quality. Keep runtime validity, relative skill retention, absolute task acceptance, and deployment acceptance separate. A natural episode end is not necessarily a valid throw or a correct recovery pose.

Reconstruct checkpoint lineage, not just run names: parent hash, selected child, updates retained along that path, discarded attempts, rollback points, optimizer state, and normalization state. An older model is not inherently uncorrupted; a later model may retain valuable skills despite a flawed critic or incomplete task acceptance. Select candidates by measured capabilities and correction cost.

Name the retention anchor separately from the next initializer. Changing the initializer must not silently ratchet longitudinal protection limits outward.

Record which configuration semantics changed: reference and clocks; observations and frames; action mapping; physics; reward functions and temporal scaling; completion/termination predicates; sampling; optimizer; evaluation and stopping. Equal dimensions or matching reward names do not establish parity. Separate a necessary implementation repair from the hypothesis about which training objective improves behavior.

## Freeze a baseline before optimizing

Evaluate the inherited actor on full courses with the intended runtime. Where exploration stability matters, compare deterministic means and a declared noise protocol. Common noise/std can help isolate the mean controller; own-policy noise measures its actual training distribution. These answer different questions. Keep reset seeds and independent noise-generator seeds explicit.

When investigating noise-induced failure, compare old/new means under matched noise and, if warranted, exchange standard deviations or perturb action subsets. Quantify common-noise amplitude relative to each actor's own std: a retained stress protocol may be stronger than the current training distribution. Trace raw mean/noise → scaled/clamped targets → actual joints/contact → subsequent observations/actions. Do not infer an excessively large learned noise scale solely from noisy failures, or call stress-only failure training-distribution collapse.

Scope a fixed noise reference to its task and comparison. Matching action dimensions does not justify copying another motion's learned std into routine acceptance. Report per-joint target-angle amplitude and control frequency, not just mean raw std; action position clipping alone does not establish a realistic disturbance limit. An untruncated Gaussian's three-sigma interval is not a hard bound. Use deterministic and own-policy evaluations for their stated scopes; additional stress needs a separately justified distribution and must remain labeled as stress. Preserve historical stress failures when correcting the next protocol. Inspect body/arm/finger entropy separately when actuator scaling, phase gating or saturation makes raw total entropy a poor measure of effective exploration.

Freeze evaluation intervals, units, denominators, physical events, and missing-data behavior. Save enough continuous trajectories to inspect transitions and failure onset; peak-only metrics can hide a bad path. A maximum pooled across environments and timesteps also becomes more sensitive as sample count grows. Before treating a mild peak exceedance as task regression, inspect its duration, per-episode distribution and physical outcome under the declared noise. Retain genuine severe-event bounds; calibrate any revised progression rule on stable and failed cases before new optimization, while preserving historical decisions. Distinguish a withheld random seed from clones or interpolation within a narrow development grid.

## Choose the next curriculum from the capability gap

Write the next stage as a capability to gain while naming capabilities to retain. If an inherited actor already releases the object reliably but starts or finishes in a bad pose, first test posture correction with a fixed achievable release target. Raising speed, broadening DR and repairing posture together makes failure hard to attribute.

For a new contact task, a useful candidate sequence is nominal contact/control → complete task sequence and transitions → task-quality range → robustness. This is a planning pattern, not a validated universal schedule: skip capabilities already demonstrated, and use the project's constraints to choose the next step. A reference is an input/prior whose timing, continuity and feasibility need evidence; tracking score need not be the final task objective.

Predeclare the promotion evaluation, minimum exposure, budget and rollback checkpoint for each stage. Promote on physical capability evidence under the intended noise/domain, rather than elapsed hours, total reward or a visually flat training curve. If a stage fails, classify missing behavior, invalid runtime, insufficient exposure and destructive optimization before changing coefficients. Preserve the useful actor and diagnose the smallest failing transition.

## Migrate reward and value semantics deliberately

For a finite observed task, check the actual wrapper/PPO bootstrap at natural completion and at rollout truncation; these are different boundaries. Preserve meaningful success/failure bookkeeping when correcting horizon semantics.

Check critic feature ranges along the entire physical course, including after objects leave the hand. If reward, horizon, or privileged-input semantics change, decide whether the inherited critic/Adam remain usable. A critic-only recalibration may preserve a useful actor; verify actor, std and normalizers stay unchanged, and validate value bias/error by phase on held-out collection. This does not guarantee value accuracy after the actor changes distribution.

Audit actual weighted rewards, event counts and temporal integrals. In dt-scaled managers, per-event returns and per-second rates differ. Raw weight values are not comparable across normalized phase budgets or different kernels. A positive term that is nearly zero over all encountered errors may provide little learning signal; merely increasing its nominal maximum does not establish effective shaping. Model-free PPO still needs useful sampled action variation.

For an ablation, inspect the installed manager's zero-weight behavior: it may skip the callback while retaining the term name. Verify the actual zero contribution and unchanged physical transitions; do not assume missing diagnostics imply a missing registered term, or substitute an epsilon weight to make a broken checker pass. Preserve failed implementation preflights separately from learning outcomes.

Use task events for task outcomes and recovery-state criteria for recovery quality when that matches the objective. Reward activation in separate phases does not separate shared policy parameters or eliminate physical consequences across phases. Record any remaining coupling through early termination or delayed event confirmation.

## Design one interpretable comparison

Fix the common actor and runtime, then vary one named factor or explicitly declared bundle. Calibrate each arm's critic for its own reward if required; do not mislabel this necessary value adaptation as identical critic weights. Prefer replicated A/B seeds over many unrelated recipes when the question is causal.

Preserve comparisons at the declared shared exposure when branches stop differently. Longer surviving branches provide additional learning trajectories; they do not replace the missing replication or justify comparing separately selected best checkpoints.

Keep samples, minibatches, epochs, LR schedules, and evaluation budgets comparable. Distinguish independent experimental replicas from distributed ranks that jointly update one policy; four GPUs do not by themselves imply a four-rank global batch. If resumed blocks reseed, distinguish the stable trial/cohort seed from the current worker's RNG seed in logs and tags. Record:

```text
global transitions/update = environments/rank × ranks × rollout steps
local minibatch size = environments/rank × rollout steps / minibatches
optimizer steps/update = epochs × minibatches  (verify implementation)
physical time sampled/environment = updates × rollout steps × control_dt
```

Many environments do not ensure phase coverage. Inspect measured phase visits in each rollout, including after early failures change resets. Physical phase staggering can preserve contact history; arbitrary mid-trajectory resets can create false skill evidence. Label discarded warmup prefixes separately from the trajectories retained for training. Synchronization is a hypothesis to test, not a universal explanation for failure.

Preserve task-level absolute acceptance while providing learnable intermediate training objectives. Avoid simultaneously changing reference, motors, DR, architecture, and reward to repair one symptom. If historical configurations already show a useful effect, use them as evidence rather than re-discovering it or reverting all subsequent repairs.

## Stop optimization without losing the answer

When the hypothesis includes delayed adaptation, define an observation horizon separately from checkpoint acceptance. A task-quality failure may withhold promotion while learning continues within the authorized budget; it need not be a runtime fault. Audit implicit aborts in warmup, phase-coverage checks and diagnostics as well as the main controller. Keep episode termination, numerical/physics validity and bounded optimization protections explicit. An early stop limits inference about later recovery; continuing observation does not retrospectively pass the earlier checkpoint. This does not authorize restarting an old stopped trial: record a new authorized protocol and preserve the old decision.

Predefine three responses: runtime/physics fault, observed task regression, and diagnostic deviation such as parent-output drift. A monitor is not a retention loss. State its formula, action subset, sample distribution and thresholds; an averaged squared mean shift is not full Gaussian KL or a joint angle.

Reference tracking error, actual joint-limit excess and loss of balance are different measurements. Localize a triggered proxy in the saved trajectory before assigning a physical cause. Repeated independent noise sequences can characterize a sensitive maximum, but do not retroactively turn a failed registered gate into a pass or justify restarting the stopped branch.

Save final weights, termination reason and the last complete metrics before normal early exit. If physics and numerical validity permit and evaluation is authorized within budget, perform a frozen full-course evaluation after stopping optimization—even when a scheduled training block did not finish. Do not resume optimization or loosen a threshold merely because the process stopped early. Runtime faults require validity review before replay.

Respect the pre-registered global and per-run budgets, including evaluation reserve. Report wall time, formal updates, diagnostic updates, retained lineage updates and actual samples separately. Do not call a short guarded run a converged plateau, and do not equate thousands of consumed rollback updates with thousands learned by the selected policy.

For block-resumed telemetry, reconcile summary counters against ordered history rows and durable local completed-update records before inferring missing training. A stale dashboard summary can coexist with complete reward/termination history; fix the metadata without duplicating scientific runs or replaying optimization.

Training logs and final evaluation have different provenance. Specify whether update-N telemetry was collected before the Nth optimization; count actual ended episodes, allow overlapping failure flags, and avoid treating correlated rolling episodes as iid final-policy success trials. Compare physical units and success criteria across reward versions, not their total reward scores.

## Minimal run record and closeout

Use project-native files; the following are fields, not a requirement to create separate documents for each:

```yaml
question: one falsifiable capability or mechanism question
common_runtime: source/config/reference/asset hashes; interface and timing contract
parent: checkpoint hash; retained lineage; optimizer/normalizer handling
arms: intended difference; matched initial states; seeds and actual devices
budget: formal/diagnostic/evaluation samples; updates; time limits; reserve
exposure: measured phases, contacts, event counts, DR and executed optimizer steps
acceptance: validity; relative retention; absolute task gates; missing measurements
stopping: runtime fault; regression; diagnostic deviation; final-evaluation action
outcome: physical metrics; uncertainty/coverage; saved checkpoints; rejection reason
inference: observed fact; supported interpretation; unresolved alternatives
next_action: smallest discriminating step within user-authorized scope
```

When maintaining this skill, promote an experimental lesson into guidance only to the extent established. A repeatable logging/lifecycle fix may generalize directly; a reward coefficient or causal explanation needs task evidence. Add evidence and applicability to the project's profile, revise superseded advice, and retain failed-run records in the project rather than copying all history into the skill.
