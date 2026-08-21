---
permalink: /projects/chapter-70/
title: "Massachusetts Chapter 70 School Finance"
layout: single
author_profile: false
toc: true
toc_sticky: true
classes: wide
---

<p class="cs-page-intro">A reproducible examination of how Massachusetts funds public education—and how statewide growth can conceal very different district experiences.</p>

<div class="cs-project-meta">
  <span><strong>Status</strong> Active analysis</span>
  <span><strong>Coverage</strong> District × fiscal year</span>
  <span><strong>Primary source</strong> Massachusetts DESE</span>
  <span><strong>Stack</strong> dbt · Neon/Postgres · Power BI</span>
</div>

## Questions

The project begins with three connected questions:

1. How have Chapter 70 aid and foundation budgets changed over time?
2. How differently do districts experience those changes?
3. How do local fiscal capacity, enrollment, and the funding formula shape the result?

## Current analytical foundation

The current canonical model combines two Massachusetts Department of Elementary and Secondary Education inputs:

- District-level Chapter 70 aid and foundation-budget data
- District wealth and required-local-contribution data

The files are transformed through dbt staging models and joined at **district × fiscal year**. The resulting mart includes source amounts, per-foundation-pupil measures, funding shares, reconciliation differences, and data-coverage flags.

<div class="cs-band cs-band--inline">
  <p class="cs-pipeline">DESE files <span>→</span> dbt staging <span>→</span> canonical CH70 mart <span>→</span> Neon/Postgres <span>→</span> semantic layer <span>→</span> BI</p>
</div>

## Core measures under review

| Measure | Working definition | Publication status |
|---|---|---|
| Chapter 70 aid | District Chapter 70 aid reported by DESE | Source reconciliation pending |
| Foundation budget | DESE district foundation budget | Cross-file reconciliation underway |
| Foundation enrollment | Enrollment used in the Chapter 70 foundation calculation | Definition review underway |
| Required local contribution | Required district contribution reported by DESE | Cross-file reconciliation underway |
| Aid per foundation pupil | Chapter 70 aid ÷ foundation enrollment | Statewide aggregation must be weighted |
| Aid share of foundation | Chapter 70 aid ÷ foundation budget | Formula and exception review underway |

## Validation plan

Before findings are published, the project will document and execute:

- Uniqueness at district × fiscal year
- Null, zero-denominator, and accepted-value checks
- Fiscal-year and district coverage
- Reconciliation between aid and wealth inputs
- Formula checks for funding components
- Statewide totals compared with DESE publications
- District-year spot checks against source material
- Explicit distinction between nominal and inflation-adjusted dollars

> **Current caution:** A statewide “average district aid per pupil” is not the same as statewide aid divided by statewide foundation enrollment. The published view will use the appropriately weighted calculation and label it clearly.

## Early analytical view

The Power BI report currently explores total Chapter 70 aid, aid per pupil, and change over time. These visuals are analytical prototypes—not yet publication-ready findings—until the source inventory, aggregation logic, and statewide reconciliations are complete.

## Reproducibility

The dbt models are maintained in the private development repository while documentation and validation are strengthened. Public code and reproducibility links will be added before publication.

## Next milestones

- Complete the DESE source inventory and citations
- Add dbt model descriptions and tests
- Resolve statewide per-pupil aggregation
- Reconcile statewide totals and selected district-years
- Define the first governed CH70 metric contracts
- Publish the first accessible narrative on Substack
