# SEO Content Optimization using Data Analysis

## Author

Umm-e-Kalsoom

## Overview

This project supports SEO content optimization by identifying web pages that should be reviewed first.

The workflow uses a transparent baseline priority score based mainly on Click-Through Rate (CTR) and average search position.

The output is a ranked review queue with a priority score, reason code, and recommended action.

## Research Question

Which SEO pages should be prioritized for human review based on observed CTR and average search position?

## Unit of Analysis

Web page.

## Dataset

The project uses the FlyRank internship anonymized SEO dataset.

- 30,000 rows
- 44 columns
- SEO-related performance and content signals

No client names, private queries, or client-identifying information are included.

## Method

The baseline uses two main signals:

- CTR
- Average search position

Pages with lower CTR and poorer average position receive higher priority for review.

The output contains:

- Priority rank
- Content ID
- CTR
- Average position
- Priority score
- Reason code
- Recommended action

## Example Recommendation

A high-priority page may have:

- Very low CTR
- Poor average search position
- Reason code: `CTR_LOW_POSITION`

The recommended action is to review the page's title, search intent, meta description, and on-page content.

## Results

The baseline produced a ranked queue of 30,000 pages.

The highest-priority page in the reviewed output had:

- CTR: 0.0
- Average position: 245.0
- Priority score: 21.491228
- Reason code: `CTR_LOW_POSITION`

The top-20 review showed that the highest-priority pages generally had very low CTR together with poor average search positions.

These results are descriptive and directional. They do not prove that an SEO change will cause CTR to increase.

## Recommendations

A content editor can:

1. Start with the highest-priority pages.
2. Check whether there are enough impressions for meaningful review.
3. Review the title and meta description.
4. Check search intent and content relevance.
5. Review content freshness and quality.
6. Decide whether an update is appropriate.
7. Monitor performance after the update.

## Limitations

The ranking is decision support, not causal evidence.

A high priority score does not guarantee that an SEO update will improve CTR.

Other factors such as search intent, seasonality, SERP features, and insufficient impressions can affect performance.

The final decision should remain with a human editor.

## Technologies

- Python
- Pandas
- NumPy
- Matplotlib
- Jupyter / Google Colab

## Repository

https://github.com/umm319/flyrank-ml-internship

## Capstone Notebook

`work/notebooks/capstone.ipynb`

## GitHub Pages

https://umm319.github.io/flyrank-ml-internship/
