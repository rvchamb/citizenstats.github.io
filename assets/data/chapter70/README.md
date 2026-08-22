# Massachusetts Chapter 70 comparison extracts

These CSV files are analysis-ready extracts assembled from the `dataMultiChart` supporting worksheet in the Massachusetts Department of Elementary and Secondary Education (DESE) **Chapter 70 Trends in Aid and Local Contribution** workbook.

## Official source

- DESE Chapter 70 program page: https://www.doe.mass.edu/finance/chapter70/
- Source workbook currently linked by DESE: https://www.doe.mass.edu/finance/chapter70/keyfactors.xlsx
- DESE label: “Chapter 70 Trends in Aid and Local Contribution”

DESE describes the workbook as providing trend data for key factors influencing required local contributions and state-aid calculations back to FY2007.

## Archived source version

The workbook used for the current extracts identifies itself as:

- **Title:** FY26 Foundation Budget Per Pupil
- **Updated:** October 2025
- **Workbook:** `dese_chapter70_key_factors_fy2026_updated_2025-10.xlsx`
- **File size:** 5,291,679 bytes
- **SHA-256:** `95d7f39f1317b1b2e77c3ce791800eaf7cf334b722767f8655d6a26c2fbc8d89`

The archived workbook is retained byte-for-byte for reproducibility. DESE remains the authoritative source; consult the official link above for the latest version.

## Published extracts

| File | Exact source worksheet | Source block | Intended grain | Description |
|---|---|---|---|---|
| `districtaid.csv` | `dataMultiChart` | District-aid field block | District × fiscal year | Foundation enrollment, foundation budget, required local contribution, target aid percentage, Chapter 70 aid, foundation-aid increment, and required net school spending |
| `districtwealth.csv` | `dataMultiChart` | Wealth/contribution field block | District × fiscal year | Equalized property valuation, income, combined effort yield, foundation budget, target and required local contributions, foundation enrollment, and contribution/wealth measures |

The files include DESE’s statewide aggregate rows as well as district records. Downstream models must distinguish statewide rows from district-level observations before aggregating.

## Workbook inventory and future analysis

The workbook also contains presentation, lookup, consolidated-data, and detailed supporting tabs. The most relevant next-stage data tabs are:

- `dataContribution` — detailed components behind local wealth, effort, target contribution, reductions, shortfalls, and required local contribution
- `dataAid` — detailed Chapter 70 aid increments, adjustments, reductions, and required net school spending
- `dataNSS`, `dataLEAName`, and `LEA Codes` — supporting measures and district reference data

These tabs are not yet part of the two baseline extracts. They are candidates for separately modeled, documented extensions after the current Chapter 70 baseline is validated.

## Transformation note

These are not direct CSV downloads from DESE. They were assembled from the workbook’s supporting worksheet to make longitudinal comparison and reproducible modeling practical. Values remain source-shaped in these files—including commas, currency-like text, and percentages—and are cleaned and typed in dbt staging models.

## Attribution and limitations

- Source publisher: Massachusetts Department of Elementary and Secondary Education
- Data should be interpreted using DESE’s Chapter 70 documentation and annual formula materials.
- Historical values may be revised when DESE republishes the workbook.
- District organization, enrollment, formula rules, and definitions can change across fiscal years.
- Monetary values are nominal unless a downstream model explicitly adjusts them for inflation.
- CitizenStats is an independent analytical project and is not affiliated with or endorsed by DESE.

## Reproducibility status

The extracts are published to make the current CitizenStats analysis inspectable. Field-level documentation, automated dbt tests, and formal statewide reconciliations are being added as the Chapter 70 project moves toward publication.
