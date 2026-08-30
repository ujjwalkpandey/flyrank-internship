# CTR / Engagement Opportunity Scoring — AI Fluency Capstone

## What I built

I built a public portfolio and a search-intelligence capstone around one practical question:

> Which visible pages should an SEO/content reviewer investigate first for CTR and engagement opportunity?

The project is intended for content and SEO reviewers who need to prioritize a large number of pages without treating an automated score as proof that a page needs a particular change.

The core ML work uses the FlyRank ML Internship search-performance warehouse. The portfolio presents the research work, notebooks, evidence, limitations, and recommendations in a public-safe format.

## What it does

The project:

1. Defines a page-level search-performance problem.
2. Checks whether the signals used by the baseline are actually present and useful.
3. Builds a transparent opportunity-ranking approach.
4. Compares a modeling approach with a baseline.
5. Audits the result for leakage.
6. Produces ranked recommendations with action labels and reason codes.
7. Presents the result as decision support for a human reviewer.

## Repository

https://github.com/ujjwalkpandey/flyrank-internship

## Live portfolio

https://dynamic-chaja-8332db.netlify.app/

## Research paper

https://ujjwalkpandey.github.io/flyrank-internship/

## Setup

The ML notebook uses Google Colab and DuckDB to read the gated FlyRank warehouse.

A stranger reproducing the ML work should:

1. Open `work/notebooks/capstone.ipynb` in Google Colab.
2. Add their authorized `HF_TOKEN` to Colab Secrets under the name `HF_TOKEN`.
3. Run the notebook from top to bottom.
4. Do not paste the token into the notebook or commit credentials.
5. Inspect the generated evaluation output and recommendation artifacts.

The portfolio itself is a static HTML/CSS/JavaScript site and can be served by any static host.

## Example usage

For the ML workflow:

- Load page-level search-performance observations.
- Select decision-time features.
- Define the future-window outcome separately from the feature window.
- Run the baseline and model evaluation.
- Inspect leakage checks.
- Review the ranked recommendation queue.

For the portfolio:

- Open the live URL.
- Read the capstone case study.
- Follow the repository and notebook links.
- Review the methodology, result interpretation, and limitations.

## Architecture

```text
FlyRank search-performance warehouse
              |
              v
       DuckDB / pandas
              |
              v
   Decision-time features
              |
              v
   +----------------------+
   | Baseline + ML model  |
   +----------------------+
              |
              v
       Leakage checks
              |
              v
     Ranked action queue
              |
              v
 Human SEO/content review
              |
              v
      Public case study
```

## Evaluation

An exploratory run produced:

- Baseline MAE: 0.012917
- Model MAE: 0.000016
- Apparent improvement: 0.012902

I do **not** treat those numbers as a valid model win.

The exploratory model used `gsc_clicks` and `gsc_impressions` while predicting CTR. Because CTR is directly derived from clicks and impressions, those inputs leak the target. The near-zero model error is therefore a leakage artifact.

This failure was retained as part of the project's evaluation record rather than hidden. A leakage-safe future-window evaluation is required before claiming that the learned model outperforms the baseline.

## Limitations

- The analysis is observational.
- A low CTR does not prove that a title, metadata element, or content change is required.
- Search intent, SERP features, seasonality, brand/non-brand mix, and other factors can affect CTR.
- A ranking score is decision support, not an automatic publishing instruction.
- The project does not claim to reveal Google's ranking algorithm.
- The project does not establish causal refresh or SEO impact.
- The preliminary model metric is invalid because of target leakage and should not be used as evidence of model superiority.

## Human review

A reviewer should inspect the highest-ranked candidates before making changes. The system should not automatically publish, rewrite, delete, merge, or refresh content based solely on its score.

## AI transparency

I built the portfolio and parts of the project with AI assistance. AI helped with drafting, code scaffolding, explanations, and presentation structure. I checked the resulting code, ran the notebooks, inspected outputs, and explicitly rejected the apparently excellent preliminary model result after identifying target leakage.

## Credits

Built on the FlyRank ML Internship dataset.
