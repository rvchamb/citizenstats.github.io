---
permalink: /projects/semantic-layer/
title: "CitizenStats Semantic Layer"
layout: single
author_profile: false
toc: true
toc_sticky: true
classes: wide
---

<p class="cs-page-intro">An R&D project testing whether governed analytical definitions can remain consistent across Power BI, Tableau, third-party BI tools, and AI.</p>

## The problem

Metrics are often rebuilt separately in each reporting tool. Definitions drift, filters diverge, time behavior changes, and validation becomes difficult to reuse. A dashboard may be internally correct while the organization still lacks a portable analytical contract.

## Architecture goal

<div class="cs-band cs-band--inline">
  <p class="cs-pipeline">Public data <span>→</span> dbt <span>→</span> Neon/Postgres canonical models <span>→</span> BI-neutral semantic layer <span>→</span> Power BI, Tableau, third-party BI &amp; AI</p>
</div>

The semantic layer should govern:

- Metrics and calculation logic
- Dimensions and relationships
- Grain and valid aggregation
- Fiscal-year and other time behavior
- Default filters and exclusions
- Business definitions, lineage, and caveats
- Validation rules and verified questions

## Demonstration plan

Chapter 70 will provide the first metric set. A small number of governed definitions—such as Chapter 70 aid, foundation budget, required local contribution, and weighted aid per foundation pupil—will be implemented once and consumed by more than one tool.

A successful demonstration should show that:

1. Power BI and another consumer return the same governed result.
2. Definitions and lineage are inspectable outside either BI tool.
3. dbt tests and verified-answer regression tests catch structural and semantic errors.
4. Documentation can be generated from the same underlying contracts.

## Technology evaluation

The initial evaluation will compare portable/open approaches, including Cube Core and dbt MetricFlow, against a concrete CH70 contract. Apache projects and interoperability standards will be monitored where they improve portability.

Power BI PBIP/TMDL files remain valuable as a version-controlled implementation of the Power BI model, but Power BI will not be the authoritative home of cross-tool definitions.

## R&D record

The project will maintain contemporaneous notes on uncertainties, alternatives, experiments, results, decisions, and approximate time spent. This supports both good engineering practice and potential R&D documentation.
