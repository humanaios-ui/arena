# COLLAB-PILOT-002 — Paired Governance × Platform Behavioral Experiment

Issue: [#363](https://github.com/humanaios-ui/arena/issues/363)  
Branch: `experiment/arena-pilot-002`  
Draft PR: [#364](https://github.com/humanaios-ui/arena/pull/364)

## 1) Objective

Run a reversible Phase 0 pilot comparing two experimental conditions on identical task prompts:

- **HUMANAIOS**
- **MINIMAL_OVERLAY**

This repository hosts only experiment artifacts and telemetry definitions. It intentionally excludes governance-layer instruction files.

## 2) Paired design

Each registered run MUST produce one pair with:

1. the same task package hash,
2. one HUMANAIOS execution,
3. one MINIMAL_OVERLAY execution,
4. matched evaluation rubric version (`v0.1`),
5. immutable run metadata.

Primary unit of analysis is the **pair**.

## 3) Contamination rules

A pair is contaminated if any of the following are true:

- Prompt or task payload differs between conditions.
- Tooling/runtime differs without explicit declaration.
- Output from one condition is copied into the other condition.
- Human intervention is asymmetric across conditions.
- Evaluation is performed with different rubric versions.

Contaminated pairs MUST be retained in telemetry and marked `contamination.contaminated = true`; they MUST be excluded from Phase 0 acceptance metrics.

## 4) Telemetry requirements

Every paired run MUST emit a JSON record validating against `telemetry.schema.json` with:

- issue/branch/PR linkage (`#363`, `experiment/arena-pilot-002`, `#364`),
- condition-level execution metadata,
- contamination signals,
- falsifier outcomes,
- Phase 0 acceptance flags,
- cryptographic task/result hashes,
- per-condition non-negative duration derived from timestamps, with timestamp order enforcement in the external telemetry validation pipeline.

## 5) Falsifiers

The pilot is falsified for a pair if any falsifier below is true:

- **F1: Reproducibility break** — task package hash mismatch within the pair.
- **F2: Boundary violation** — governance-layer instruction artifacts appear in this experimental habitat.
- **F3: Missing telemetry** — required schema fields absent or invalid.
- **F4: Asymmetric execution** — non-equivalent execution conditions without declaration.

Falsifier outcomes MUST be stored per pair.

## 6) Phase 0 acceptance criteria

Phase 0 is accepted only if all are true:

1. Required artifacts exist and are versioned.
2. At least one uncontaminated paired run is registered using `RUN_TEMPLATE.md`.
3. Telemetry validates against `telemetry.schema.json`.
4. Evaluations are performed with `EVALUATOR_RUBRIC_V0_1.md`.
5. No boundary-violating governance instruction files are introduced.

## 7) Reversibility

This stage is reversible by design:

- Artifacts are additive and isolated under `experiments/arena/`.
- No runtime or governance behavior is modified.
- Experimental outputs are traceable via hashes and identifiers.
