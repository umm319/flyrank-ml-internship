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

**Human action:** The editor reviews the highest-priority pages and decides whether a title, meta description, content, or search-intent change is appropriate.

**Cost of a wrong decision:** If a page is incorrectly prioritized, editing time may be spent on a page with limited improvement opportunity.

Data analysis helps process many pages consistently and identify pages that deserve further review.

## 2. Data Safety

The project uses the FlyRank internship dataset for SEO content analysis.

The dataset contains 30,000 rows and 44 columns.

The dataset includes SEO-related signals such as CTR, impressions, clicks, average position, search volume, competition, content age, word count, and engagement metrics.

For the baseline action score, the main decision signals are **CTR and average search position**.

The fields `trend_direction` and `trend_pct` were not used as inputs to the baseline rule because they may contain information about changes over time.

Pseudonymous identifiers such as `content_id` and `client_id` were not used as predictive signals.

No client names, private queries, or other client-identifying information are included in the analysis.

## 3. Baseline

The baseline uses a simple transparent rule:

> Pages with low CTR and poor average search position should receive higher priority for optimization.

**Reason code:** `CTR_LOW_POSITION`

The priority score combines the two signals so that pages with weaker CTR and poorer search position receive higher review priority.

The output contains:

- Priority rank
- Content ID
- CTR
- Average position
- Priority score
- Reason code
- Recommended action

The baseline is transparent and easy for an editor to understand.

It is intended as decision support rather than proof that an optimization will cause higher CTR.

## 4. Methodology

The analysis loads the anonymized SEO dataset and checks its available columns and structure.

The baseline uses CTR and average position as the main prioritization signals.

Low CTR indicates relatively few clicks compared with impressions. Poor average position indicates that a page appears lower in search results.

These signals are combined into a priority score and pages are sorted from highest priority to lowest priority.

The resulting queue is used to identify pages for human review.

The baseline does not use `trend_direction` or `trend_pct` as decision inputs and does not use client identifiers as predictive features.

## 5. Results

The baseline produced a ranked queue of 30,000 pages.

The highest-priority pages showed very low CTR together with poor average search position.

The top-ranked page had:

- **CTR:** 0.0
- **Average position:** 245.0
- **Priority score:** 21.491228
- **Reason code:** `CTR_LOW_POSITION`

Other high-priority pages also showed 0.0 CTR and poor average positions.

The top-20 review therefore shows that the baseline behaves as intended: pages with weak CTR and poor search position are placed near the top of the review queue.

These results are descriptive and directional. They do not establish that changing a page will cause CTR to increase.

## 6. Interpretation

The baseline identifies pages where low CTR and poor search position occur together.

The two main signals have a direct relationship with the priority score:

- Lower CTR increases priority.
- Worse average position increases priority.

The top-ranked pages provide candidates for human review.

However, the baseline cannot determine why a page has low CTR. Possible explanations include search intent, SERP features, seasonality, content relevance, or insufficient evidence.

Therefore, the ranking should be treated as a review queue rather than an automatic optimization decision.

## 7. Recommendations

A FlyRank editor can use the ranked queue as follows:

1. Start with the highest-priority pages.
2. Check whether the page has enough impressions to support a meaningful review.
3. Review the title and meta description.
4. Check whether the content matches search intent.
5. Review content freshness and quality.
6. Make an update only when the human review supports it.
7. Monitor performance after the update.

### Confidence and limitations

The baseline provides directional prioritization, not causal evidence.

A high priority score does not guarantee that an SEO change will improve CTR.

Seasonality, search intent, SERP features, insufficient impressions, and other factors can make a recommendation wrong.

The final decision should remain with a human editor.

## 8. Reproducibility

The completed analysis is contained in:

`work/notebooks/capstone.ipynb`

To reproduce the analysis:

1. Clone the repository.
2. Make the approved dataset available at the expected path.
3. Open `work/notebooks/capstone.ipynb`.
4. Run the notebook from top to bottom.
5. Review the generated ranked recommendations and summary outputs.

The analysis uses Python with common data-science libraries including pandas, numpy, matplotlib, and scikit-learn where required.

The baseline ranking is deterministic for the same input data and configuration.

## 9. Demo Outline

- **Question:** Which SEO pages should be prioritized for review?
- **Method:** Transparent baseline scoring using CTR and average search position.
- **Output:** Ranked queue with priority score, reason code, and recommended action.
- **Result:** The highest-priority pages showed very low CTR and poor average search positions.
- **Recommendation:** Review high-priority pages first and then decide whether title, meta description, content, or search-intent changes are appropriate.

## Social Post

Built a baseline SEO content optimization workflow using anonymized search-performance data. The analysis ranks pages using CTR and average search position and provides reason codes and recommendations for human review. The result is designed as directional decision support rather than a causal claim.

#MachineLearning #SEO #DataScience #FlyRank

## Employer Summary

I built an SEO content optimization workflow that ranks web pages for review using CTR and average search position. The project produces a transparent priority score, reason code, and recommended action for each page. The workflow is designed to help content teams focus their review effort on pages showing weaker search-performance signals.
