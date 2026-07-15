# Stock Research Assistant

A Google Colab–first financial analysis toolkit implemented as interactive Jupyter notebooks. It automates stock data collection, basic analyses, and generates AI-ready prompts and structured outputs for downstream research.

> Note: This repository is notebook-driven. The most up-to-date code and usage instructions live in the notebook(s). Open them in Google Colab to run and configure the tool.

## What this repo contains

- One or more Jupyter Notebooks (.ipynb) designed to run in Google Colab.
- Notebook cells that install dependencies, configure inputs (tickers, date ranges, API keys), fetch market and fundamental data, run analyses, and export results (JSON/CSV/Markdown).

## Key changes (since previous README)

- The project is now maintained and executed primarily inside Colab notebooks — the README points you to the notebooks for concrete configuration and the latest behavior.
- Any implementation details (data sources, API integrations, analysis modules) should be confirmed by inspecting the top configuration cells of the notebook(s). This README intentionally stays high-level to avoid becoming outdated.

## Quick start

1. Open the notebooks in Google Colab:
   - https://colab.research.google.com/github/rx-ie/stock-research-assistant
2. Inspect the top cells for configuration options and instructions.
3. Populate inputs (tickers, date range, API keys) in the configuration cell.
4. Run the notebook cells in order. Outputs will appear inline and can be downloaded or saved to Google Drive.

## Typical configuration options

- List of tickers to analyze
- Historical date range for price and fundamentals
- API keys for third-party data providers or language models
- Analysis toggles (which modules to run, output formats)

Store secrets securely in Colab (runtime environment variables or Secrets manager) — do not hardcode API keys in notebooks committed to the repo.

## Outputs

Notebooks may produce:
- Human-readable summaries (Markdown/text)
- AI-ready prompts and prompt templates
- Structured exports (JSON, CSV, Parquet)
- Visualizations embedded in the notebook

Location of saved files depends on your runtime choices (local Colab VM, Google Drive, or manual export).

## Recommended workflow for contributors

- Edit notebooks directly for feature changes. Use nbdime or a notebook diff tool for clean diffs.
- Keep configuration and usage instructions in the top cells of each notebook.
- Add or update a short explanatory cell near any new analysis module describing inputs, outputs, and assumptions.

## Troubleshooting

- If dependency installation fails in Colab, re-run the install cell and restart the runtime if needed.
- If data fetching fails, check the API keys and rate limits for the external provider used by the notebook.
- If a notebook behaves differently than described here, open the notebook and read the configuration/usage cells — they are authoritative.

## License

No LICENSE file is included in the repository. If you want this project to be open source, add a LICENSE file (MIT, Apache-2.0, etc.).

---

Last updated: July 2026
Author: rx-ie
