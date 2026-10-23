# Causal, optimization and data audit

Read for claims about learning, conditional control, demonstrations or architecture comparisons. Use the active implementation and raw evidence; a framework name is not an implementation audit. Findings distinguish verified defects, plausible risks and untested questions.

## Audit two separate chains

**Learning chain:** successful physical event → actual optimized objective/loss → contributing samples and gradients → parameter updates → independent functional metric.

Locate the current trainer, optimizer construction, objective assembly, masks, sample weighting and update calls. Check whether environment step reward actually enters the loss; some trainers use imitation or other objectives instead. Explain PPO, returns or GAE only after confirming their implementation and use in this version. Check event timing and whether the successful samples survive filtering and supply a useful learning signal. Where warranted, inspect loss contributions, gradient paths and parameter deltas without mistaking a nonzero gradient for beneficial learning.

Report three distinct claims: updates occurred; useful behavior was learned versus a valid baseline; optimization was sufficient for the question. A plateau or consumed GPU time does not establish the last claim. Reconstruct retained checkpoint ancestry; training on different tasks, versions or initializers cannot be added up to demonstrate convergence. Discarded rollbacks and diagnostics count toward spent budget, not updates learned by the selected actor.

**Control chain:** exogenous incoming object / target variation → actual racket pose and velocity change at the relevant event → actual outgoing trajectory.

Inspect the command target, racket sweet center and physical contact point separately, with their clocks. Measure signed response to task changes as well as physical outcomes. Preserve matched incoming conditions and initial states for the declared counterfactual, changing only the intended factor. For example, paired target vs matched-contact-command tests must share the reset state, incoming object, contact time, surface normal and incoming velocity except for the displayed command being tested. Name additional effects if the intervention bundles them.

For a position-command sensitivity test, report paired contact changes and a declared directional ratio such as `K_p = delta impact position / delta command position`, with axes, units and a nonzero perturbation defined. A missing signed response remains a diagnostic gap; null is not zero and does not establish conditioning.

An offline same-input replacement can localize an output effect under that fixed input. In closed loop the replacement changes later states, observations, contacts and actions; evaluate that feedback path before making whole-policy or causal task-performance claims. A successful local hybrid is not automatically an executable teacher, a learned controller or an explanation of the historical training gradient.

## Independent data and coverage

Count contact events, windows, clips, source trajectories and collection batches separately. Repeated windows from a continuous segment are not independent demonstrations. Split related segments by source/batch before fitting, tuning and evaluation; report any development-set reuse, exact duplicates, near duplicates and common ancestors. Estimate uncertainty at an appropriate independent unit rather than treating correlated events as iid.

Trace construction provenance in both directions: was the incoming object or target generated from the demonstration being scored, and was that demonstration chosen using the same generated task? Such coupling can make the task easier and limit generalization claims. It is a risk until verified, not a confirmed leakage defect. Likewise inspect privileged reset state, future/reference channels, fixed phase/timing, teacher information and train/test overlap. State what was checked and what remains unknown.

Describe coverage along task-relevant axes: position, arrival/contact timing, direction, incoming/outgoing speed, racket orientation/velocity, preparation and recovery states. “More spatial coverage” does not establish timing, direction, control or transition coverage. Keep withheld independent incoming conditions distinct from new random seeds inside the same construction recipe.

## Separate demonstration interfaces

| Intervention | Evidence needed to support its claimed role |
| --- | --- |
| Reference visible in observations | The reference reaches the network with correct timing and semantics |
| Network actually uses the reference | Controlled reference changes produce relevant behavior, with confounds controlled |
| Imitation loss | Actual targets, masks, weights and gradient contribution; no assumption from reference visibility |
| Executable teacher | Feasible closed-loop actions under the teacher's declared information/action privileges |
| Initialization condition | Exact state/phase/velocity/history used, including privileged resets |
| Online correction | When feedback acts, its available signals and control authority, and resulting physical effect |

A reference-visible arm losing does not show that demonstrations are useless: it tests that interface and training condition. Do not equate a replay trajectory with a teacher, reference visibility with imitation, or initialization help with online adaptation.

For architecture A/B comparisons, align exogenous tasks, initial conditions, available information, action authority, execution constraints and training exposure as far as possible. Disclose privileged information, additional teacher/planning compute and unmatched costs. If equalization changes the architecture's purpose, report both the controlled comparison and the system-level comparison with different claim scopes.

## Review disposition

Give evidence location, scope, impact and one proportionate next action for consequential findings. Prefer a falsifiable control that separates candidate mechanisms. Do not turn missing evidence into a proven bug, a negative search into impossibility, or a noisy best seed into a stable capability. For the next racket-return experiment use [the progression guide](racket-progression.md); record its protocol and inference in [the shared ledger](../../research-cycle/references/experiment-record.md).
