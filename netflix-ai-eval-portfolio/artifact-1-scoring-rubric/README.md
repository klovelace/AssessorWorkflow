# Artifact 1 — Interactive Scoring Rubric

**Task type:** AI-generated content evaluation (synopsis quality)  
**File:** [`index.html`](./index.html) — open directly in any browser

---

## The Problem

Netflix generates AI-written synopses, recommendation explanations, and metadata at scale. Before any of that reaches a user, a human rater needs to evaluate whether the output meets the quality bar. The core challenge: how do you ensure that 50 raters — across different time zones, languages, and cultural contexts — apply the same standard to the same content?

The answer is not a better definition. It's behavioral anchors.

A rubric that says *"the synopsis should be accurate"* is not actionable. A rubric that says *"Score 1 = contains invented plot elements or wrong character names; Score 4 = precise, factually tight, verifiably accurate, no embellishment"* gives raters something to match against. This tool is built on that principle.

---

## Design Decisions

### Four-dimension weighted scoring

Rather than a single holistic quality score, the rubric decomposes output quality into four distinct dimensions with explicit weights:

| Dimension | Weight | Rationale |
|-----------|--------|-----------|
| Factual accuracy | 35% | Highest weight — hallucinated content is the primary failure mode of LLM-generated synopses and the hardest to recover from in a user-trust context |
| Tone & brand fit | 25% | Netflix has a distinct editorial voice; AI outputs that sound generic or press-release-like degrade brand perception even when factually correct |
| Viewer hook | 25% | A synopsis that doesn't drive play intent has failed its core job, regardless of accuracy |
| Safety & policy | 15% | Lower weight because safety violations are relatively rare, but scored separately so they can be surfaced as a hard block even when composite score is passing |

The weighted composite maps to a three-tier decision:
- **≥ 3.5** — Ship
- **2.5–3.49** — Human review required
- **< 2.5** — Reject and flag as retraining candidate

### Anchor examples at every score level

Each dimension has four behavioral anchors (one per score level). The anchors are written as observable behaviors, not adjectives. This is the primary driver of IRR — raters shouldn't have to interpret the rubric, they should be able to match the output to a description.

Anchors are displayed dynamically as raters score, so they reinforce calibration during the rating task itself, not just during onboarding.

### Explicit IRR targets embedded in the rubric

The IRR thresholds (Cohen's κ ≥ 0.70, exact agreement ≥ 65%, adjacent agreement ≥ 90%) are surfaced directly in the rater-facing tool. This is intentional — raters who understand that their job is not just to score accurately but to score *consistently with peers* tend to apply standards more carefully.

### Safety as a separable dimension

Safety and policy compliance is scored on the same 1–4 scale as other dimensions, but it functions as a partial hard block. A composite score ≥ 3.5 with a safety score of 1 would still be routed to review. This mirrors how production content moderation actually works — a beautiful, accurate, engaging synopsis that contains a policy violation is still a reject.

---

## IRR Design Rationale

Cohen's κ ≥ 0.70 is the standard "substantial agreement" threshold in the psychometrics literature. For AI evaluation tasks where the output space is wide and subjective (versus structured labeling), 0.70 is achievable with good anchors and calibration, and meaningful — it means raters are agreeing substantially more than chance.

The adjacent agreement floor (±1 = ≥ 90%) matters because a 1-point disagreement (e.g., one rater scores 3, another scores 2) is often acceptable in practice — both raters see the same flaw, they differ slightly on severity. A 2-point disagreement (1 vs 3 or 2 vs 4) suggests the raters are applying fundamentally different standards and requires arbitration.

---

## How to Extend This

To adapt this rubric for a different Netflix AI task (e.g., search relevance, recommendation explanation), the key parameters to change are:

1. **Dimension names and weights** — search relevance needs a "query match" dimension; recommendation explanation needs a "personalization evidence" dimension
2. **Anchor examples** — re-write anchors for the new output type; keep the 4-level structure
3. **Decision thresholds** — may need adjustment depending on task criticality (safety tasks may warrant a higher ship threshold)

---

## File Structure

```
artifact-1-scoring-rubric/
├── README.md          ← this file
└── index.html         ← fully self-contained interactive rubric
```
