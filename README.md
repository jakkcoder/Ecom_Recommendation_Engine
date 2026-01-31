# Recommendation Engine Case Study (Catawiki-style Marketplace)

This repository is a learning-focused case study for a product + data science/ML interview round at a marketplace similar to Catawiki. The goal is to design, evaluate, and communicate a recommendation system that improves user engagement and business outcomes while handling real-world constraints.

## Problem Statement

You are joining a marketplace platform where users browse and bid on curated items across many categories. Recent data shows:

- Declining engagement on the home feed
- Lower conversion on item detail pages
- Increased catalog size and fast item turnover (new items daily, some items expire quickly)

**Task**: Propose and prototype a recommendation system that improves engagement and conversion while respecting marketplace constraints (freshness, diversity, fraud/abuse risk, and latency).

### Business Goals

- Increase qualified engagement (clicks, bids, saves)
- Improve conversion to bids/sales
- Maintain user trust and avoid spammy recommendations

### Technical Constraints

- Large and sparse user-item interactions
- Fast-changing inventory with cold-start items
- Low-latency serving for real-time personalization
- Need to balance relevance, diversity, and freshness

## What You Can Be Asked in the Interview

Below are common questions and prompts used by Amazon/Google-like product case study rounds and marketplace recommendation interviews. Use these to practice structured thinking.

### Product & Strategy

- What is the north-star metric for this product surface (home feed, search, item page)?
- How would you define success in 30/60/90 days?
- What trade-offs exist between revenue, trust, and long-term engagement?
- How would you prevent recommendation echo chambers in a marketplace?
- How do you handle cold-start for new users and new items?

### Data & Metrics

- What data would you log to train and evaluate the system?
- Which offline metrics would you choose (e.g., NDCG, MAP, precision/recall) and why?
- How would you design an online A/B test and avoid novelty bias?
- What guardrail metrics should never regress?

### Modeling & Ranking

- How would you design a baseline (e.g., item-item similarity, popularity, recency)?
- When would you choose collaborative filtering vs. content-based vs. hybrid?
- How would you incorporate item freshness, price, and seller quality?
- How would you prevent bias toward popular items?

### System Design

- Describe an end-to-end architecture from data ingestion to serving.
- What latency budget is acceptable, and how do you achieve it?
- How would you use embeddings and vector search for retrieval?
- What does the feature store look like for near-real-time signals?

### Experimentation

- What is the hypothesis for your first experiment?
- How would you determine sample size and test duration?
- How would you interpret a result where CTR increases but conversions drop?

### Risk & Integrity

- How would you protect the system against manipulation or spam?
- What ethical or compliance issues could arise from personalization?
- How would you ensure fairness across categories or sellers?

## Suggested Deliverables for the Case Study

- A one-page product brief with goals, metrics, and success criteria
- A baseline recommender and a stronger candidate model
- Offline evaluation and a proposal for online testing
- A diagram of the data pipeline and serving architecture

## References (Public Case Study Examples)

These links are useful for understanding typical interview expectations and system design patterns:

- https://www.casebasix.com/pages/amazon-case-study-interview
- https://finalroundai.com/interview-questions/design-amazon-recommender-system
- https://rohan-paul.com/p/ml-case-study-interview-question-a5a

