# Data Browser

Standalone HTML tool to find all datapoints whose annotations satisfy one boolean script.

## What it does

- Load a JSON file containing annotations.
- Write one script using the same syntax as the co-occurrence tool.
- Evaluate that script against every datapoint annotation set.
- Return a list of all matching datapoints.
- Show annotation codes as color tags for quick scanning.
- Let you configure visible table columns and their order from datapoint JSON fields.
- Export matches as CSV or JSON.

## Input format (expected)

- A JSON array of datapoints, where each datapoint has an `annotation` field, OR
- A JSON object with a `data` array of datapoints with `annotation`.

`annotation` can be:

- a list of strings (typical), e.g. `["support: addiction _ generative ai"]`, or
- a single value (binary classification outputs), which is treated as a single-item annotation.

Each annotation string is typically parsed as:

`theme: code _ subcode`

The tool extracts `THEME`, `CODE`, and `SUBCODE` for queries.

## Script syntax

Supported operators:

- `AND`, `OR`, `NOT`
- Parentheses: `(`, `)`
- Equality predicates: `THEME='value'`, `CODE='value'`, `SUBCODE='value'`

Examples:

- `(THEME='support') AND (CODE='addiction')`
- `(THEME='generative ai') AND (NOT((CODE='parenting style') OR (CODE='overreliance')))`

If a script is invalid, the editor shows an error with the line number.

## Run

Open `data-browser/index.html` in a browser.

## Sample file

Use `data-browser/sample_annotations.json` as a quick example input.
