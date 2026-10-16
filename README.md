# AI Evaluation Operations | Interactive Portfolio Prototype

**Independent prototype for AI-content assessment, rater calibration, and operational quality management**

This repository demonstrates three layers of evaluation quality assurance: a clear scoring standard, consistent human ratings, and visibility into operational bottlenecks.

The browser-based artifacts use a hypothetical streaming-media evaluation scenario. They are independent portfolio demonstrations, not commissioned work for Netflix or another company. References to Netflix in original scenario files do not imply affiliation. Displayed operational figures, rater statistics, and performance metrics are illustrative rather than live production data.

## Explore the three artifacts

| Artifact | Question | Demo |
| --- | --- | --- |
| Interactive scoring rubric | How can evaluators apply consistent criteria to AI-generated content? | [Open rubric](./netflix-ai-eval-portfolio/artifact-1-scoring-rubric/index.html) |
| Rater calibration | How would an evaluation lead detect disagreement and scoring drift? | [Open calibration](./netflix-ai-eval-portfolio/artifact-2-rater-calibration/index.html) |
| Evaluation operations health | Which workstreams require intervention before quality and delivery suffer? | [Open operations dashboard](./netflix-ai-eval-portfolio/artifact-3-eval-ops-health/index.html) |

Download the repository and open the relevant HTML file. Some chart views load Chart.js from a public CDN and therefore require an internet connection.

## Workflow

1. **Define the standard:** Break quality into observable scoring dimensions, behavioral anchors, and escalation rules.
2. **Calibrate the reviewers:** Monitor inter-rater agreement, improvement, and potential drift using proposed onboarding and review processes.
3. **Operate the program:** Surface throughput, arbitration, overdue tasks, and blockers for timely intervention.
4. **Make a decision:** Revise scoring rules, investigate disagreement, retrain reviewers, or proceed based on evidence.

The three artifacts demonstrate a conceptual operating model. They do not share a backend, ingest real rater events, or validate their proposed operating thresholds.

## Methods and decisions

The case study covers weighted rubrics, behavioral anchors, Cohen's kappa, exact and adjacent agreement, proposed sentinel reviews, rater-cohort monitoring, and quality-adjusted throughput.

All numerical thresholds are illustrative design assumptions. An actual evaluation operation would require representative samples, empirical calibration, threshold validation, and integration testing.

## Repository layout

- [Extended case study](./netflix-ai-eval-portfolio/README.md)
- [Scoring rubric rationale](./netflix-ai-eval-portfolio/artifact-1-scoring-rubric/README.md)
- [Rater calibration rationale](./netflix-ai-eval-portfolio/artifact-2-rater-calibration/README.md)
- [Evaluation operations rationale](./netflix-ai-eval-portfolio/artifact-3-eval-ops-health/README.md)
- `index.html`: original rubric entry page

## Why this matters

An evaluation program succeeds when its labels are interpretable, its disagreements are actionable, and its managers can distinguish reliable progress from superficially high throughput. These demos translate evaluation methodology into an operator-facing design and make underlying quality decisions visible.

**Disclosure:** Independent portfolio demonstration, with no private client data, production integrations, or claim of sponsorship or endorsement.
