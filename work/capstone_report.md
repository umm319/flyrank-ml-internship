# Capstone Report — SEO Content Optimization

- **Author:** Umm-e-Kalsoom
- **Lane:** SEO Content Optimization
- **Repo:** https://github.com/umm319/flyrank-ml-internship
- **Date:** August 2026

## 1. Problem Framing

This project supports decisions about which website pages should be reviewed first for SEO improvement.

**Unit of analysis:** Web page.

**Output:** A ranked list of pages with a baseline priority score, reason code, and recommended action.

**Decision supported:** A content manager can use the ranked queue to decide which pages should receive SEO review first.

**Human action:** The editor reviews the highest-priority pages and decides whether to update the title, content, search intent, or other on-page elements.

**Cost of a wrong decision:** If a page is incorrectly prioritized, editing time may be spent on a page with limited improvement opportunity.

Machine learning and data analysis can help by processing many pages consistently and identifying pages that deserve further review.

---

## 2. Data Safety

The project uses the FlyRank internship dataset for SEO content analysis.

The dataset contains 30,000 rows and 44 columns.

The analysis uses SEO performance signals such as:

- CTR
- Average position
- Impressions
- Clicks
- Search volume
- Competition
- Content age
- Word count
- Engagement-related metrics

For the baseline action score, the main decision signals are **CTR and average search position**.

The fields `trend_direction` and `trend_pct` were not used as inputs to the baseline rule because they may contain information about changes over time.

Pseudonymous identifiers such as `content_id` and `client_id` are not used as predictive signals.

No client names, private queries, or other client-identifying information are included in the analysis.

---

## 3. Baseline

The baseline uses a simple transparent rule:

> Pages with low CTR and poor average search position should receive higher priority for optimization.

**Reason code:** `CTR_LOW_POSITION`

The priority score combines the two signals so that pages with weaker CTR and poorer search position receive a higher review priority.

The baseline is useful because it is simple, interpretable, and easy for an editor to understand.

The output is a ranked queue containing:

- Priority rank
- Content ID
- CTR
- Average position
- Priority score
- Reason code
- Recommended action

This baseline is intended for **decision support**, not as proof that an optimization will cause higher CTR.

---

## 4. Methodology

The analysis first loads the anonymized SEO dataset and checks the available columns and data structure.

The baseline uses CTR and average position as the main prioritization signals.

Low CTR indicates that a page receives relatively few clicks compared with its impressions. Poor average position indicates that the page appears lower in search results.

These signals are combined into a priority score and the pages are sorted from highest priority to lowest priority.

The resulting queue is used to identify the top pages for human review.

The methodology deliberately avoids using the target or future-derived information as part of the baseline decision rule.

---

## 5. Evaluation

The baseline is evaluated as a ranking and decision-support system rather than as a causal model.

The top-20 pages were reviewed individually using their priority score, CTR, average position, reason code, and recommended action.

The highest-ranked examples generally show very low CTR together with poor average position.

The top-ranked page had:

- CTR: 0.0
- Average position: 245.0
- Priority score: 21.491228
- Reason code: `CTR_LOW_POSITION`

Other high-priority pages also showed 0.0 CTR with poor average positions.

These observations support the intended behavior of the baseline: pages showing both weak click-through performance and poor search position are placed near the top of the review queue.

This ranking should be treated as directional decision support rather than proof that updating a page will improve its CTR.

---

## 6. Interpretation

The baseline identifies pages where low CTR and poor search position occur together.

The strongest priority signals are therefore the two signals directly used by the rule:

- Lower CTR increases priority.
- Worse average position increases priority.

The top-20 review shows that several highly ranked pages have a CTR of 0.0 and very poor average positions.

These pages may deserve human review of their titles, search intent, content quality, and other on-page factors.

However, the baseline does not determine why a page has low CTR. Factors such as search intent, SERP features, seasonality, or content relevance may also contribute.

---

## 7. Recommendations

The ranked queue should be used as a review list rather than an automatic instruction to edit every page.

Recommended workflow:

1. Start with the highest-priority pages.
2. Check whether the low CTR is supported by sufficient impressions.
3. Review the page title and meta description.
4. Check whether the content matches search intent.
5. Review content freshness and quality.
6. Make an update only when the human review supports it.
7. Monitor future performance after an update.

### Confidence and limitations

The baseline provides directional prioritization, not causal evidence.

A high priority score does not guarantee that an SEO change will improve CTR.

Seasonality, search intent, SERP features, insufficient impressions, and other factors can make a recommendation wrong.

The final decision should therefore remain with a human editor.

---

## 8. Reproducibility

The project can be reproduced from the repository by opening:

`work/notebooks/capstone.ipynb`

The notebook should be run from top to bottom after the required dataset is available.

The analysis uses Python and common data-science libraries including:

- pandas
- numpy
- matplotlib
- scikit-learn where required by the notebook

The baseline ranking is deterministic for the same input data and configuration.

The repository contains the completed Capstone notebook under:

`work/notebooks/capstone.ipynb`

The work is intended to be reproducible and uses public-safe language throughout.

---

## 9. Demo Outline

**Question:** Which SEO pages should be prioritized for review?

**Method:** Transparent baseline scoring using CTR and average search position.

**Output:** Ranked queue with priority score, reason code, and recommended action.

**Example result:** The highest-priority pages had very low CTR and poor average search positions.

**Recommendation:** Review high-priority pages first, then decide whether title, meta description, content, or search-intent changes are appropriate.

---

## Social Post

Built a baseline SEO content optimization workflow using anonymized search-performance data. The analysis ranks pages using CTR and average search position and provides reason codes and recommendations for human review. The result is designed as directional decision support rather than a causal claim.

#MachineLearning #SEO #DataScience #FlyRank

---

## Employer Summary

I built an SEO content optimization workflow that ranks web pages for review using CTR and average search position. The project produces a transparent priority score, reason code, and recommended action for each page. The workflow is designed to help content teams focus their review effort on pages showing weaker search-performance signals.
