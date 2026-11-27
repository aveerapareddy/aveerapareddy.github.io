# Experiment checklist

Status: not started. Check items only against recorded evidence.

## Before pilot
- [ ] Pin code commit and scenario generator; verify existing capabilities.
- [ ] Save dependency lockfile, Python/PyBullet versions, hardware, OS, thread limits.
- [ ] Implement deadline policies, delay injection, monotonic timing, terminal outcomes.
- [ ] Validate timing units and ensure artificial delay is included.
- [ ] Validate scenario geometry and deterministic seeds.
- [ ] Record data/license provenance and personal publication rights.

## Before evaluation
- [ ] Keep pilot seeds separate from evaluation seeds.
- [ ] Fix deadline, execution reserve, simulation step limit, and exclusion rules.
- [ ] Commit frozen configuration and protocol version.
- [ ] Generate/record randomized paired treatment order.
- [ ] Ensure every attempt, including failures, produces a valid run record.
- [ ] Record raw-event log checksums.

## Before release
- [ ] Analyze at scenario level, keeping repetitions paired/nested.
- [ ] Report all denominators, exclusions, uncertainty, and negative results.
- [ ] Distinguish wall-clock time, simulation time, and injected delay.
- [ ] Publish configuration and analysis code with raw-data provenance.
- [ ] Explain simulator limitations and avoid physical safety or novelty claims.
- [ ] Check artifact URLs, license compatibility, secrets, and employer/client confidentiality.
- [ ] Label manuscript, preprint, and peer-reviewed status accurately.
