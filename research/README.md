# Akhilesh Veerapareddy — research portfolio

Research interests: AI systems, embodied AI, robot learning, and intelligent autonomous systems.

This portfolio connects existing engineering projects with a proposed program of reproducible research. The study below is **planned**; this repository does not report experiments, peer-reviewed publications, or measured improvements.

## Research website
[Research agenda and project context](https://aveerapareddy.github.io/research/)

## Broader proposed directions
Reliability-aware agentic robotics; efficient Physical AI inference; autonomous geospatial intelligence. The current deadline-aware simulation study is a small proposed pilot within the efficiency direction. These are research directions, not claims of completed findings.

## First planned study
**Deadline-aware evaluation of simulated navigation pipelines.** Measure how planning delay and timeout policies affect timely mission completion in controlled, reproducible simulation.

- [Study protocol](protocol.md)
- [Run-record JSON Schema](run.schema.json)
- [Empty run-log template](runs.template.jsonl)
- [Experiment checklist](experiment-checklist.md)
- [Results policy](results/README.md)

## Existing engineering foundations
These are implementation projects, not evidence of research findings.

| Project | Current basis reviewed on 2026-11-27 | Limitations |
| --- | --- | --- |
| [AutonomyOS](https://github.com/aveerapareddy/AutonomyOS) | Python/FastAPI, PyBullet simulation, occupancy-grid A*, rule-based metadata perception, waypoint execution, telemetry, scenario/benchmark foundations | Static worlds, open-loop execution, no learned navigation policy or image-based perception established by the README |
| [GPU Inference Platform](https://github.com/aveerapareddy/gpu-inference-platform) | Serving architecture, observability, persistence, vLLM-adapter implementation status documented in README | No benchmark results established; README contains historical phase text, so verify code and pin a commit before experiments |
| [ModelOps Control Plane](https://github.com/aveerapareddy/modelops-control-plane) | Lifecycle architecture and transition documentation | Documentation only; executable lifecycle runtime not started per README |

Repository capability summaries are based on their READMEs, not an independent runtime audit.

## Reproducibility principles
1. Pin source commits, environment versions, seeds, scenario definitions, and treatment order before collecting runs.
2. Preserve failures and raw logs. Never replace measured values with estimates.
3. Separate pilot/debug runs from the frozen evaluation set.
4. Report uncertainty, denominators, exclusions, and simulator limitations.
5. Publish only original or appropriately licensed material, with data/code provenance and release rights checked.

## Contact
Akhilesh Veerapareddy · [GitHub](https://github.com/aveerapareddy) · [Email](mailto:akhileshveerapareddy@gmail.com)

Last updated: 2026-11-27.
