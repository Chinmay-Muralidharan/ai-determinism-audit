# AI Determinism Audit: Reproducibility Framework

**Researcher:** Chinmay Muralidharan

---

## 1. Project Overview — The Bit-Identical Standard

This framework is designed for the rigorous auditing of generative models.  
In safety-critical applications—such as the Biomedical Engineering domains I’ve worked in—visual similarity is a failure state.

### Standard

Verification is explicitly defined as bit-identical output.

### Method

Every generation is validated using SHA-256 cryptographic hashes.  
A single-bit difference results in an audit failure.

---

## 2. Technical Pillars

I have formalized the following four pillars to guide my Diagnostic Probing research.

## Pillar 1 — Fixed System Boundary

To isolate the causes of stochastic drift, the following variables are strictly locked:

#### Model Weights: Specific LoRA or base model checkpoints

#### Hyperparameters: Fixed sampler type, inference steps, guidance scale

#### Precision: Fixed floating-point precision (e.g., FP32)

#### Hardware: Controlled random seed handling on a fixed GPU architecture

## Pillar 2 — Failure Mapping Logic

Using a Sensitivity & Robustness Analysis approach, system fragility is identified:

### Baseline:

Establish a bit-identical SHA-256 hash across three repeated runs

### Probe:

Change exactly one variable

Examples: CUDA version, library update, FP32 → FP16

### Map:

Document the precise point where SHA-256 identity breaks

### Pillar 3 — Writing & Reporting Discipline

In line with my research values of empirical grounding over intuition, all findings follow a strict structure:

### Separation:

Observation, Action, and Result are kept distinct

### Structure:

Findings are presented using tables and bullet points

No speculative narrative

### 3. Framework Status

As of Jan 28, 2026:

 Establish Bit-Identical Standard

 Define Fixed System Boundary

 Formalize Failure Mapping Logic

 Commit to Reporting Discipline

### 4. Immediate Next Steps

 Execution: Generate baseline hashes on a T4 GPU

 Diagnostic: Perform first precision-shift probe (FP32 → FP16)

 Logging: Record results in a structured AUDIT_LOG.md

### Research Philosophy

This research prioritizes:

Transparency about system limitations

Preference for negative results when they are informative

Reproducibility over aesthetic output


