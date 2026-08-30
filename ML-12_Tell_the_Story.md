# ML-12 — Tell the Story

## 5-minute demo outline

### 0:00–0:40 — Question

**Question:** Which visible pages should an SEO/content reviewer investigate first for CTR and engagement opportunity?

The practical problem is that search teams have more pages to review than they can manually inspect. The goal is therefore to turn search-performance signals into a ranked, human-reviewable priority queue.

### 0:40–1:30 — Method

I worked in the CTR / Engagement Opportunity Scoring lane.

The unit of analysis is a page-level search-performance observation. I used the FlyRank internship warehouse and focused on observable search and engagement signals such as impressions, clicks, CTR, average position, sessions, and engagement context.

The intended modeling design is time-aware: information available at month *t* is used to assess an outcome in a later month, while future outcome information is kept out of the feature set.

I also compared the learned approach against a transparent baseline rather than presenting the model in isolation.

### 1:30–2:30 — One chart / evidence

Show the **baseline-vs-model evaluation chart or table from the executed capstone notebook**.

Explain what the metric measures in one sentence before discussing the number.

The warehouse connection used in the notebook covered daily search-performance data from January 2025 through June 2026 for the queried relation.

### 2:30–3:30 — One honest result

The first exploratory model run produced:

- Baseline MAE: **0.012917**
- Model MAE: **0.000016**
- Apparent improvement: **0.012902**

However, I do **not** present this as evidence that the model beats the baseline. The run included clicks and impressions as inputs while predicting CTR, and CTR is directly derived from clicks divided by impressions. That creates target leakage.

The important result from the audit is therefore that the leakage was detected and the apparent performance was rejected rather than being presented as a successful model result.

### 3:30–4:20 — Recommendation

The intended output is a ranked content-review queue.

The highest-ranked pages should be treated as **review candidates**, not automatic change requests. A reviewer should inspect search intent, SERP context, seasonality, brand/non-brand mix, and the actual page before changing metadata or content.

A representative action label is:

**REVIEW_CTR_METADATA**

with a reason code such as:

**HIGH_IMPRESSIONS_LOW_CTR**

### 4:20–5:00 — Close

The main takeaway is that the value of the system is not a mysterious score. It is a repeatable way to prioritize limited human review while making the assumptions and failure modes visible.

The next technical step is a leakage-safe future-window evaluation before claiming that a learned model outperforms the baseline.

---

## Employer-facing summary

I built a CTR / Engagement Opportunity Scoring workflow on the FlyRank ML Internship search-performance warehouse to identify pages that may deserve SEO/content review. The work uses page-level search visibility and engagement signals and is designed around time-aware validation and leakage checks. An exploratory model appeared dramatically better than the baseline, but I found that the run leaked CTR information through clicks and impressions, so I rejected that result instead of presenting it as valid model performance; the resulting ranked queue is intended as human decision support, not an automated SEO system.

---

## Social post

I built a search-intelligence baseline for the FlyRank ML Internship using real, pseudonymized search-performance data.

The goal was simple: turn a large set of page-level search signals into a ranked queue showing which pages might deserve CTR/content review first.

The most useful part wasn't getting a spectacular model score. A preliminary run looked almost perfect, but a leakage audit showed why: clicks and impressions directly determine CTR, so using them to predict CTR made the result invalid.

I kept the failure, documented it, and treated the output as decision support rather than pretending the model had proved something it hadn't. That's the lesson I wanted the capstone to demonstrate: a trustworthy ML workflow is not just about performance; it's about knowing when not to trust your own result.

---

## Public-safe case-study framing

The underlying content problem is prioritization: a reviewer cannot manually investigate every visible page with the same depth. Search visibility and engagement signals can help narrow that queue, but they do not establish why a page is underperforming or guarantee that a particular content change will improve it.

This project therefore frames the score as **decision support**. The system is designed to surface candidates for human investigation, with reason codes that make the ranking easier to inspect.

The project does not claim to reveal Google's ranking algorithm, prove causality, or establish that refreshing a page causes a ranking or CTR improvement.

---

## Reproducibility

Repository:

https://github.com/ujjwalkpandey/flyrank-internship

Capstone notebook:

`work/notebooks/capstone.ipynb`

Baseline notebook:

`work/notebooks/w04_baseline_score.ipynb`

Deployed paper:

https://ujjwalkpandey.github.io/flyrank-internship/

Data credit:

Built on the FlyRank ML Internship dataset.

