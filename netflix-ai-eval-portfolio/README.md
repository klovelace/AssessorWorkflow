# Netflix AI Evaluation Portfolio

**Kraemer A. Lovelace** · Washington, DC · [klovelace@gmail.com](mailto:klovelace@gmail.com)

---

## Overview

This portfolio demonstrates applied evaluation design and data operations work scoped specifically to the kinds of AI features Netflix is building — AI-generated content descriptions, personalized recommendation explanations, search relevance scoring, and metadata classification.

Each artifact addresses one of the three core competencies called out in the role:

| # | Artifact | Core Competency |
|---|----------|----------------|
| 1 | [Interactive Scoring Rubric](./artifact-1-scoring-rubric/) | Develop clear, scalable guidelines and scoring rubrics to ensure consistent rater judgment |
| 2 | [Rater Calibration Dashboard](./artifact-2-rater-calibration/) | Oversee rater onboarding, calibration, and QA workflows |
| 3 | [Eval Ops Health Dashboard](./artifact-3-eval-ops-health/) | Define and monitor success metrics — speed to IRR, throughput, task effectiveness |

All three artifacts are fully interactive HTML files. Open them in any browser — no server, no dependencies, no build step.

---

## The Problem Space

Netflix is building AI systems that affect what people watch. An AI that generates a slightly misleading synopsis, recommends a show with a confusing rationale, or misclassifies content metadata degrades user trust at scale. Human evaluation is the quality gate that ensures those systems behave correctly — but only if the evaluation itself is rigorous, consistent, and operationally sound.

The three failure modes I designed against:

**1. Rubric ambiguity** — When raters disagree, it almost always traces back to a rubric that leaves room for interpretation. The fix is behavioral anchor examples at every score level, not just definitions. Artifact 1 demonstrates this.

**2. Slow or inconsistent calibration** — Getting raters to inter-rater reliability (IRR) is not a one-time event. It requires a structured onboarding pipeline, ongoing sentinel monitoring, and a clear response protocol when drift is detected. Artifact 2 demonstrates this.

**3. Invisible operational health** — Evaluation programs fail silently. Throughput looks fine while a single task type is stuck below κ = 0.70, or a new rater cohort is three days behind onboarding. The fix is a unified health view that surfaces blockers before they become delivery misses. Artifact 3 demonstrates this.

---

## Background

I spent 15 years at USAID designing and running evaluation systems for high-stakes development programs — including 30+ evaluations with formal IRR requirements, rater training and calibration across a global workforce, and scoring rubric development adopted agency-wide. The specific methods here (weighted composite scoring, Cohen's κ monitoring, sentinel item embedding, drift detection thresholds) are drawn directly from that operational experience, translated into the Netflix AI product context.

---

## How to Use This Portfolio

```bash
git clone https://github.com/YOUR_USERNAME/netflix-ai-eval-portfolio.git
cd netflix-ai-eval-portfolio

# Open any artifact directly in browser
open artifact-1-scoring-rubric/index.html
open artifact-2-rater-calibration/index.html
open artifact-3-eval-ops-health/index.html
```

No npm install. No build. Each file is a single self-contained HTML document.

---

## Artifact Quick Reference

### Artifact 1 — Interactive Scoring Rubric
> *"How do you get 50 raters in different countries to agree on what 'good' means?"*

A fully interactive rater-facing scoring tool for AI-generated Netflix content. Four weighted dimensions, behavioral anchors at each score level, live weighted composite score, and explicit IRR threshold targets. Designed so a rater can score a task, see exactly why their judgment was correct or not, and build calibration through use.

**Key design decisions documented in:** [`artifact-1-scoring-rubric/README.md`](./artifact-1-scoring-rubric/README.md)

---

### Artifact 2 — Rater Calibration Dashboard
> *"How do you get raters to IRR fast — and keep them there?"*

A program management dashboard showing a 5-phase onboarding protocol, per-rater κ trend lines, cohort IRR trajectory over time, and automated drift alerts. The onboarding protocol is designed to achieve κ ≥ 0.70 in under 7 days while maintaining quality as the cohort scales.

**Key design decisions documented in:** [`artifact-2-rater-calibration/README.md`](./artifact-2-rater-calibration/README.md)

---

### Artifact 3 — Eval Ops Health Dashboard
> *"How do you know if your evaluation operation is working?"*

A real-time operational health view across concurrent evaluation tasks — throughput, κ scores, delivery ETAs, blocker escalations, and sprint milestone tracking. Built around four top-line metrics: speed to IRR, weekly throughput, task effectiveness rate, and arbitration rate.

**Key design decisions documented in:** [`artifact-3-eval-ops-health/README.md`](./artifact-3-eval-ops-health/README.md)
