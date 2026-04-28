# Artifact 2 — Rater Calibration Dashboard

**Task type:** Rater onboarding, calibration, and health monitoring  
**File:** [`index.html`](./index.html) — open directly in any browser

---

## The Problem

Getting a new rater to IRR is not hard. Keeping an entire cohort at IRR across a multi-month evaluation program while continuously onboarding new raters, running multiple concurrent task types, and managing vendor relationships — that's the operational challenge.

This dashboard is designed to make the invisible visible: which raters are drifting, which ones are still in onboarding, what the cohort κ trajectory looks like over time, and exactly what to do when something goes wrong.

---

## The Onboarding Protocol

The five-phase protocol is designed to achieve κ ≥ 0.70 in under 7 days for a well-designed evaluation task. Each phase has a specific exit gate — raters don't advance until they clear it.

### Phase 1 — Orientation (Day 1, ~2 hours)

Raters read rubric documentation and watch two annotated training videos: one passing example and one failing example, with expert commentary explaining the scoring rationale at each dimension. The videos are the highest-leverage onboarding investment — they show what good and bad look like in context, which written anchors alone cannot fully convey.

Exit gate: 10-item comprehension quiz, score ≥ 80%.

### Phase 2 — Anchored practice (Days 1–2, 20 tasks)

Raters score 20 gold-standard items with known correct scores. Immediate feedback after each item: rater sees the correct score and the expert rationale. Items are stratified across all four scoring dimensions and include deliberate edge cases (e.g., a synopsis that is accurate but tonally wrong, or one that is engaging but contains a subtle factual error).

The immediate feedback loop is what makes anchored practice different from just doing more tasks. Raters are actively building their internal model of the standard with each item.

Exit gate: Exact agreement ≥ 60% on gold set, adjacent agreement (±1) ≥ 85%.

### Phase 3 — Blind calibration (Days 2–3, 30 tasks)

Raters score 30 items alongside a calibrated senior rater, with no feedback during the session. After completion, raters receive a written debrief report showing:
- Dimension-by-dimension agreement breakdown
- Exact disagreements (where they differed by 2+ points)
- Systematic pattern identification (e.g., "You are lenient on tone in comedy genres")

The written debrief is critical — it gives raters a concrete, personalized account of where their calibration needs work, which is far more actionable than a single aggregate κ score.

Exit gate: Cohen's κ ≥ 0.65 vs. senior rater.

### Phase 4 — Live monitoring (Days 3–7, first 50 production tasks)

Raters enter the production queue with 15% sentinel items embedded. κ is computed per 10-task window. If κ drops below 0.65 in any window, the rater is paused and receives a targeted re-calibration task set before continuing.

The 15% sentinel rate is deliberately higher than steady-state (10%) because early production performance is the highest-variance period — raters are applying their calibration to real task diversity for the first time.

Graduation gate: κ ≥ 0.70 sustained over 50-item window.

### Phase 5 — Ongoing health monitoring (continuous)

Steady-state sentinel rate drops to 10%. Monthly cohort recalibration sessions (group debrief on systematic drift patterns observed across the cohort). Drift alert triggers if a rater's rolling 20-item κ drops more than 0.05 from their established baseline.

The 0.05 drift threshold is empirically calibrated — smaller than that produces too many false positives from normal variance; larger than that allows meaningful drift to go undetected for too long.

---

## Monitoring Design Decisions

### Per-rater κ trend lines, not just current κ

A rater at κ = 0.68 who has been at 0.71, 0.74, 0.76, 0.74, 0.71, 0.68 over six sessions is a very different problem than a rater at κ = 0.68 who has been at 0.62, 0.64, 0.66, 0.67, 0.68. The first is drifting; the second is still improving. The trend line is the signal.

### Speed to IRR as a primary operational metric

Speed to IRR measures how efficiently the onboarding pipeline converts new raters into productive contributors. It is a direct function of rubric clarity, anchor quality, and calibration session design — which means it serves as a leading indicator of evaluation design quality, not just operational throughput.

Benchmark: ≤ 7 days for a well-designed task. If a new task type is taking 12+ days, that's a signal that the rubric needs work, not that the raters are underperforming.

### Cohort-level IRR trajectory

Individual rater κ can fluctuate for reasons unrelated to calibration quality (rater fatigue, task difficulty variation, sampling variance in sentinel items). Cohort-level κ smooths that noise and reveals systemic trends — rubric drift as the task evolves, seasonal effects, or the impact of a new calibration session.

---

## File Structure

```
artifact-2-rater-calibration/
├── README.md          ← this file
└── index.html         ← fully self-contained calibration dashboard
```
