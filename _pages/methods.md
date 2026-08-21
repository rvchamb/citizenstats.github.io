---
permalink: /methods/
title: "Publishing Methods & Project Standards"
layout: single
author_profile: false
toc: true
toc_sticky: true
---

<p class="cs-page-intro">CitizenStats is the public analytics lab that demonstrates the work. <a href="https://riggstrategy.com">RIGG Strategy</a> remains the consulting business.</p>

This is a living playbook, intentionally kept short. Individual project pages carry their own source details, definitions, tests, findings, and limitations.

## Publishing structure

- **Substack** presents accessible analysis and narrative for general readers.
- **This site** holds durable technical project pages and portfolio evidence.
- **GitHub** holds code, dbt models, tests, documentation, and reproducible assets.

## Project workflow

<div class="cs-pipeline cs-pipeline--compact">Question <span>→</span> source assessment <span>→</span> raw ingestion <span>→</span> modeling <span>→</span> validation <span>→</span> analysis <span>→</span> visualization <span>→</span> publication</div>

## Data standards

Every published dataset or model should document:

- Source and attribution
- Retrieval or update date
- Grain and intended primary key
- Field and metric definitions
- Transformations and exclusions
- Known limitations and breaks in comparability
- Steps needed to reproduce the result

## Analytics standards

CitizenStats distinguishes among:

- **Source facts:** values and definitions supplied by the publisher
- **Calculated results:** reproducible transformations or metrics
- **Assumptions:** choices required where the source is incomplete or ambiguous
- **Interpretation:** conclusions drawn from the evidence

## Validation standards

Validation should include, as appropriate:

- Row-count and coverage checks
- Uniqueness tests at the stated grain
- Null and accepted-value checks
- Cross-table and formula reconciliation
- Year-over-year reasonableness checks
- Spot checks against source records
- Regression tests for governed metrics and verified questions

## Publication checklist

Before publication:

- Technical review completed
- General-reader review completed
- Charts checked for labels, scales, units, and misleading aggregation
- Citations and source links included
- Caveats and limitations visible
- Repository and technical-method links included
- Final copyedit completed

## Architecture goal

<div class="cs-band cs-band--inline">
  <p class="cs-pipeline">Public data <span>→</span> dbt <span>→</span> Neon/Postgres canonical models <span>→</span> BI-neutral semantic layer <span>→</span> Power BI, Tableau, third-party BI &amp; AI</p>
</div>

The portable semantic layer—not any individual BI model—is intended to govern metrics, dimensions, relationships, business definitions, time behavior, lineage, and validation rules.

## R&D log

Research work should record the objective, uncertainty, alternatives considered, experiments or tests, results, decisions, and approximate time spent.

## Division of labor

Rob owns the analytical judgment: the question, modeling choices, definitions, validation, and conclusions. Family or outside reviewers can improve the hook, clarity, flow, and accessibility without needing to reconstruct the underlying analysis.
