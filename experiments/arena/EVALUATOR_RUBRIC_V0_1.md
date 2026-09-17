# EVALUATOR_RUBRIC_V0_1

Status: **Frozen for COLLAB-PILOT-002 Phase 0**

## Scope

This rubric is used to evaluate both conditions in each pair:

- HUMANAIOS
- MINIMAL_OVERLAY

Evaluators MUST apply identical criteria to both condition outputs.

## Dimensions (0-2 scale each)

### 1. Task fidelity

- **0**: Fails to address core task requirements.
- **1**: Partially satisfies requirements with notable gaps.
- **2**: Fully satisfies stated task requirements.

### 2. Reproducibility evidence

- **0**: No traceable evidence (missing hashes/metadata).
- **1**: Partial traceability; some required evidence missing.
- **2**: Complete traceability with required hashes and metadata.

### 3. Constraint adherence

- **0**: Violates explicit constraints or boundaries.
- **1**: Minor deviations with limited impact.
- **2**: Fully adheres to all explicit constraints.

### 4. Output quality

- **0**: Output is unusable or significantly incorrect.
- **1**: Output is usable with meaningful defects.
- **2**: Output is usable, coherent, and materially correct.

## Evaluation procedure

1. Confirm pair integrity and contamination status.
2. Score each condition independently across all dimensions.
3. Record scores and evidence in paired-run records.
4. Keep this rubric version fixed as `v0.1` for all Phase 0 runs.

## Tie-breaking and exclusions

- Contaminated pairs are excluded from acceptance metrics.
- If falsifiers are triggered, mark pair as not eligible for metrics.
- Do not alter dimension definitions during Phase 0.
