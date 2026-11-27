# Proposed protocol: deadline-aware simulated navigation evaluation

**Author:** Akhilesh Veerapareddy  
**Status:** Planned; implementation and pilot validation pending.  
**Version:** 0.1 — 2026-11-27  
**Study identifier:** autonomy-deadlines-v01

## Question
How do injected planning delay and explicit timeout policies change the probability of completing a simulated navigation mission before a fixed wall-clock deadline?

This is a systems evaluation, not a claim of robot learning, physical safety, novel planning, or real-world robotics performance.

## Starting point and scope
Use the existing AutonomyOS static, single-robot simulation foundation: seeded scenario generation, metadata perception, occupancy-grid A*, and waypoint execution. Before running, independently verify these capabilities at a pinned commit. The new delay injector, deadline enforcement, policies, and instrumentation are proposed additions.

Static worlds cannot establish resistance to moving obstacles or stale observations. A later study would require implemented dynamic worlds, online sensing/replanning, and separate validation.

## Hypothesis and treatments
**Preregistered direction to test:** reserving an execution budget will reduce late starts relative to waiting without a planning timeout. Whether this improves timely completion is an empirical question.

Three proposed policies:
- **Wait:** wait for the planning result, then execute; still record the common evaluation deadline.
- **Deadline gate:** abort before execution if the deadline is already reached.
- **Budget gate:** abort if remaining wall-clock budget is below an execution reserve fixed using pilot runs only.

Use injected planning delay levels of 0, 50, 200, and 1000 ms. These are experimental perturbations, not measured model latency. An eventual LLM-planner study must log actual inference latency separately and pin model/version/prompt/decoding settings.

## Experimental design
- Pilot on seeds 0–9; use pilot data only to choose the deadline, reserve, and simulation step limit.
- Freeze those values and the exact scenario generator/configuration before evaluation.
- Evaluate seeds 100–199 across every policy × delay level, with three timing repetitions per cell.
- Pair comparisons by scenario seed. Timing repetitions are nested within scenario; do not treat 3600 runs as independent scenarios.
- Randomize treatment order using a recorded order seed. Generate all scenarios independently of policy outcomes.
- Keep simulator step size, physics options, robot kinematics, obstacle inflation, waypoint tolerances, hardware, OS, and process/thread limits fixed.
- Use a monotonic clock for elapsed wall-clock measurements. Record simulation time separately.
- Mission timing starts before planning delay and ends at completion/abort/failure. State clearly whether setup and teardown are excluded.
- Keep visualization off for primary timing runs and document headless mode.
- Preserve run errors and deadline misses, not only successful paths.

Proposed total: 100 scenario seeds × 3 policies × 4 delay levels × 3 repetitions = 3600 evaluation runs after the protocol is frozen.

## Outcomes
**Primary:** timely completion = successful goal completion with total elapsed wall-clock time ≤ fixed deadline. Denominator includes all attempted evaluation runs; infrastructure failures are also reported separately.

**Secondary:** late completion rate, abort rate, failure rate, planning elapsed time, total elapsed time, execution steps, and path length when available.

Report medians and p95 latency descriptively, paired policy differences by scenario, and 95% bootstrap intervals resampling scenario seeds (all nested repetitions and treatments together). Do not use run-level resampling as a substitute for independent scenario sampling.

## Implementation prerequisites
1. Pin AutonomyOS source and dependencies; confirm a baseline mission executes.
2. Validate that planning and execution use the same scenario geometry.
3. Add monotonic timing boundaries and an independently testable delay injection point.
4. Implement policies with explicit terminal outcomes and reason codes.
5. Verify deadline checks in edge cases: zero delay, already-expired deadline, no path, and execution failure.
6. Verify that logged timings include injected delay and that simulator time is not labeled wall-clock time.
7. Complete pilot and commit frozen configuration before evaluation.

## Logging and analysis
One JSON object per attempted run, conforming to [run.schema.json](run.schema.json). Save raw events separately and record their checksum. Schema validity alone does not prove scientific validity.

Use an immutable run directory keyed by study version and source commit. Record exclusions before analysis; never delete failed runs. Commit analysis code and record its commit. Produce tables/plots only from measured logs, with units and sample counts.

## Release and interpretation
Release a reproducible artifact only after review for originality, licenses, data provenance, secrets, and rights to publish. Public engineering work should use personal or properly licensed assets, with no employer/client data.

Label simulations, pilot results, and preprints accurately. Do not infer physical-robot safety, real-world deployment, causal effects of learned models, or immigration eligibility from this study. A positive result would support only the tested environment, policies, hardware, and deadline configuration.

## Amendments
Record every post-freeze change here with date, rationale, affected runs, and whether it occurred before or after seeing evaluation outcomes.

No evaluation configuration has been frozen and no data has been collected under this protocol.
