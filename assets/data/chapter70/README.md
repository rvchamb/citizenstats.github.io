# Massachusetts Chapter 70 comparison extracts

These CSV files are analysis-ready extracts assembled from supporting worksheets in the Massachusetts Department of Elementary and Secondary Education (DESE) **Chapter 70 Trends in Aid and Local Contribution** workbook.

## Official source

- DESE Chapter 70 program page: https://www.doe.mass.edu/finance/chapter70/
- Source workbook currently linked by DESE: https://www.doe.mass.edu/finance/chapter70/keyfactors.xlsx
- DESE label: “Chapter 70 Trends in Aid and Local Contribution”

DESE describes the workbook as providing trend data for key factors influencing required local contributions and state-aid calculations back to FY2007.

## Published extracts

| File | Source worksheet | Intended grain | Description |
|---|---|---|---|
| `districtaid.csv` | District aid supporting sheet | District × fiscal year | Foundation enrollment, foundation budget, required local contribution, target aid percentage, Chapter 70 aid, foundation-aid increment, and required net school spending |
| `districtwealth.csv` | District wealth supporting sheet | District × fiscal year | Equalized property valuation, income, combined effort yield, foundation budget, target and required local contributions, foundation enrollment, and contribution/wealth measures |

The files include DESE’s statewide aggregate rows as well as district records. Downstream models must distinguish statewide rows from district-level observations before aggregating.

## Transformation note

These are not direct CSV downloads from DESE. They were assembled from the workbook’s supporting worksheets to make longitudinal comparison and reproducible modeling practical. Values remain source-shaped in these files—including commas, currency-like text, and percentages—and are cleaned and typed in dbt staging models.

## Attribution and limitations

- Source publisher: Massachusetts Department of Elementary and Secondary Education
- Data should be interpreted using DESE’s Chapter 70 documentation and annual formula materials.
- Historical values may be revised when DESE republishes the workbook.
- District organization, enrollment, formula rules, and definitions can change across fiscal years.
- Monetary values are nominal unless a downstream model explicitly adjusts them for inflation.
- CitizenStats is an independent analytical project and is not affiliated with or endorsed by DESE.

## Reproducibility status

The extracts are published to make the current CitizenStats analysis inspectable. Field-level documentation, automated dbt tests, source hashes, and formal statewide reconciliations are being added as the Chapter 70 project moves toward publication.
