# Co-occurrence Tool

Standalone HTML tool to compute co-occurrence statistics from annotation JSON outputs.

## What it does

- Load a JSON file containing annotations.
- Create **cohorts** (saved boolean scripts) either by:
  - selecting themes/codes/subcodes from the annotation tree, or
  - writing custom logic in the cohort editor.
- Compute a co-occurrence table across cohorts with counts, probabilities, and correlation.
- Sort by clicking column headers; filter numeric columns via min/max filters (filtered columns show an indicator).
- Export results as CSV / JSON / Excel (`.xls`).

## Input format (expected)

- A JSON array of datapoints, where each datapoint has an `annotation` field, OR
- A JSON object with a `data` array of datapoints with `annotation`.

`annotation` can be:

- a list of strings (typical), e.g. `["support: addiction _ generative ai"]`, or
- a single value (binary classification outputs), which will be treated as a single-item annotation.

Each annotation string is typically parsed as:

`theme: code _ subcode`

The tool extracts `THEME`, `CODE`, and `SUBCODE` for boolean queries.

## Cohort script syntax

Supported operators:

- `AND`, `OR`, `NOT`
- Parentheses: `(`, `)`
- Equality predicates: `THEME='value'`, `CODE='value'`, `SUBCODE='value'`

Examples:

- `(THEME='support') AND (CODE='addiction')`
- `(THEME='generative ai') AND (NOT((CODE='parenting style') OR (CODE='overreliance')))`

If a script is invalid, the cohort row shows an error with the line number.

## Run

Open `co-occurrence-tool/index.html` in a browser.

## Sample file

Use `co-occurrence-tool/sample_annotations.json` as a small example input (load it via the `📁 Open` button).
