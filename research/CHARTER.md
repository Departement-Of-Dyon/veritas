# Operation Veritas — Research Charter

**Departement-Of-Dyon · established 2026**

## Mission

Develop and validate instruments that detect dishonesty, hallucination,
and inconsistency in large language model outputs — using only local,
auditable methods.

## Core question

*When an AI gives a wrong or fabricated answer, does it leave measurable
fingerprints?*

## Instruments (v1)

| Instrument | Measures | Implementation |
|---|---|---|
| Consistency Sampler | Answer stability under resampling | 5× generation @ T=0.9, pairwise text similarity |
| Skeptic Challenge | Confidence calibration & honesty under pressure | Adversarial re-prompt demanding confidence % |
| Claim Auditor | Risk surface of factual assertions | Regex heuristics: numbers, studies, absolutes |

## Methodology

1. Fix question Q.
2. Sample answers A1..A5.
3. Compute `consistency_score` = mean pairwise similarity.
4. Run challenge pass on A1.
5. Audit A1 for risky claims.
6. Emit verdict: LIKELY CONSISTENT / MIXED / INCONSISTENT.

## Findings log

*(empty — run the detector and record results here)*

| Date | Question | Score | Verdict | Notes |
|---|---|---|---|---|
| | | | | |

## Ethics & limits

- Local models only; no user data leaves the machine.
- A "consistent" verdict does NOT prove truth — models can be
  consistently wrong. Veritas measures *behavioral fingerprints*,
  not ground truth.
- Results are model- and version-specific.
