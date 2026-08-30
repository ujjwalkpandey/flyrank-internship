# FL-09 — 3–5 Minute Demo Script

This is a narration script. The recorded submission must show the real working artifact on screen; this document is not a substitute for the video.

## 0:00–0:30 — Introduce the problem

“I'm going to show a search-intelligence project I built around CTR and engagement opportunity scoring. The problem is prioritization: a content or SEO reviewer has more pages to inspect than they can investigate equally. The goal is to identify which pages deserve review first.”

## 0:30–1:20 — Show the notebook

Open `work/notebooks/capstone.ipynb`.

Say:

“This notebook connects to the FlyRank internship warehouse through DuckDB. The unit of analysis is a page-level search-performance observation. I use observable search and engagement signals and keep future outcome information separate from decision-time inputs.”

## 1:20–2:10 — Show the methodology

Scroll to the methodology section.

Say:

“The important design choice here is that this is decision support. The score is not supposed to automatically change a page. The reviewer still needs to consider search intent, SERP context, seasonality, and other factors.”

## 2:10–3:00 — Show the evaluation

Show the evaluation output.

Say:

“My first exploratory result looked extremely strong: the baseline MAE was 0.012917 and the model MAE was 0.000016. But I did not accept that result. The model had clicks and impressions as inputs while predicting CTR, and CTR is derived from clicks and impressions. That is target leakage.”

## 3:00–3:40 — Explain the design decision

Say:

“The design decision I kept was to make the final output a ranked queue with an action and reason code rather than an opaque model score. That makes the result easier for a human reviewer to inspect.”

## 3:40–4:20 — Show the recommendation output

Show the ranked recommendation queue.

Say:

“This queue is a prioritization aid. A high-ranked page is a candidate for investigation, not proof that a specific SEO change will work.”

## 4:20–5:00 — State the limitation

Say:

“The main limitation is that the exploratory model result is contaminated by leakage, so I do not claim it proves model superiority. A proper next step is a leakage-safe, time-aware future-window evaluation. I think documenting that limitation is part of the result, not something to hide.”
