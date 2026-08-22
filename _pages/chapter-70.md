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

The current canonical model uses two longitudinal extracts assembled from supporting worksheets in DESE’s [Chapter 70 Trends in Aid and Local Contribution workbook](https://www.doe.mass.edu/finance/chapter70/keyfactors.xlsx):

- [District aid extract]({{ '/assets/data/chapter70/districtaid.csv' | relative_url }}) — foundation enrollment, foundation budget, required local contribution, target aid percentage, Chapter 70 aid, foundation-aid increment, and required net school spending
- [District wealth extract]({{ '/assets/data/chapter70/districtwealth.csv' | relative_url }}) — property valuation, income, combined effort yield, foundation budget, target and required local contributions, and enrollment

DESE publishes the underlying information, but the workbook’s supporting-sheet structure is not a straightforward comparison-ready dataset. CitizenStats reshapes those supporting sheets into documented CSV extracts for reproducible longitudinal analysis. The files are transformed through dbt staging models and joined at **district × fiscal year**. The resulting mart includes source amounts, per-foundation-pupil measures, funding shares, reconciliation differences, and data-coverage flags.

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

## Source files and reproducibility

The current comparison extracts are publicly available:

- [Download district aid CSV]({{ '/assets/data/chapter70/districtaid.csv' | relative_url }})
- [Download district wealth CSV]({{ '/assets/data/chapter70/districtwealth.csv' | relative_url }})
- [Read the source and transformation notes](https://github.com/rvchamb/citizenstats.github.io/blob/master/assets/data/chapter70/README.md)
- [DESE Chapter 70 program page](https://www.doe.mass.edu/finance/chapter70/)

These are independently prepared extracts from DESE supporting worksheets, not direct DESE CSV downloads. The dbt development repository remains private while its starter documentation is replaced, tests are added, and the public release is reviewed for reproducibility and credential safety.

## Next milestones

- Complete the DESE source inventory and citations
- Add dbt model descriptions and tests
- Resolve statewide per-pupil aggregation
- Reconcile statewide totals and selected district-years
- Define the first governed CH70 metric contracts
- Publish the first accessible narrative on Substack
