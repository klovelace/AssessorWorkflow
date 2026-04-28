# Artifact 3 — Eval Ops Health Dashboard

**Task type:** Evaluation operations program management  
**File:** [`index.html`](./index.html) — open directly in any browser

---

## The Problem

A mature evaluation program at Netflix might be running 5–8 concurrent task types simultaneously — synopsis quality, search relevance, recommendation explanations, metadata tagging, safety review — each with different rater cohorts, different rubrics, different κ thresholds, and different delivery timelines.

Without a unified health view, problems become visible only when they've already caused a delivery miss: a task type has been stuck below κ threshold for two weeks, a vendor cohort is behind on onboarding, a rubric ambiguity is causing systematic disagreement on a specific edge case. By then, the damage is done.

This dashboard is designed to surface those issues days before they become misses.

---

## The Four Top-Line Metrics

### Speed to IRR

The number of days from a rater's first task to achieving sustained κ ≥ 0.70. Tracked per cohort and averaged across the program. This is the primary leading indicator of evaluation design quality — slow speed to IRR almost always means rubric anchors need work, not that raters are underperforming.

**Target:** ≤ 7 days  
**Current:** 6.2 days (↓ 26% vs. Q1 benchmark)

### Throughput rate

Tasks completed per week as a percentage of planned capacity. Distinguishes between rater availability issues (throughput is low because raters aren't working) and quality issues (throughput is low because tasks are being failed QA and recycled).

**Target:** ≥ 85% of planned weekly capacity  
**Current:** 87% (on target)

### Task effectiveness rate

The percentage of completed tasks that pass QA on first review — i.e., do not require rework, arbitration, or recycling due to rater error or rubric ambiguity. This is the quality-adjusted throughput metric. A program with 95% throughput and 70% effectiveness is actually running at ~67% effective output.

**Target:** ≥ 92%  
**Current:** 94% (↑ 3 points since rubric v2.1)

### Arbitration rate

The percentage of tasks where two raters disagree by 2+ points, requiring a third-party resolution. High arbitration rates indicate either rubric ambiguity (the standard is unclear), rater drift (calibration has degraded), or task difficulty (the output type is genuinely hard to evaluate consistently).

**Target:** < 3%  
**Current:** 2.1% (below target — healthy)

---

## Blocker Escalation Design

The dashboard surfaces three categories of blocker with different escalation paths:

**Hard blocker (red):** A task type has failed to achieve or maintain κ threshold and is at risk of missing delivery. Requires immediate intervention — typically a targeted re-calibration session or rubric amendment. If not resolved within 48 hours, escalates to program lead.

**Soft blocker (amber):** A rubric ambiguity or operational dependency that hasn't yet caused a quality issue but will if unaddressed. Typically resolved in the next sprint via rubric update, anchor example addition, or vendor coordination.

**Operational risk (amber):** Delivery dependencies (vendor onboarding, localization, tooling) that are behind plan. Not a quality issue yet, but on the critical path to a delivery commitment.

The escalation design is explicit: every blocker has an owner, a resolution action, and a due date visible in the sprint tracker. The connective tissue role is not just identifying blockers — it's making sure every blocker has a named person driving it to resolution.

---

## Sprint Delivery Tracker

The sprint tracker is the program management layer that ties evaluation quality to delivery commitments. It surfaces:

- **Milestone:** What needs to be true for a delivery commitment to be met
- **Owner:** Who is accountable
- **Progress:** Where the milestone currently stands (with visual progress bars)
- **Status:** On track / at risk / blocked — updated in real time as κ scores and throughput data change

The tracker is designed to be the single source of truth for stakeholder communication. Rather than preparing a separate status report, the program lead can point stakeholders to this view and walk through it in a sync.

---

## Design Philosophy

The dashboard is built on one principle: **proactive communication over reactive reporting**.

Every metric is chosen because it gives the program lead signal *before* a problem becomes a miss. Speed to IRR is a leading indicator. Task effectiveness rate flags rubric problems before they accumulate. Blocker escalation surfaces operational risks before they hit the critical path.

The goal is a program lead who never has to say "I didn't see that coming."

---

## File Structure

```
artifact-3-eval-ops-health/
├── README.md          ← this file
└── index.html         ← fully self-contained ops health dashboard
```
