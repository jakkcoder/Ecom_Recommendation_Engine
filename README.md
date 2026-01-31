# Recommendation Engine Case Study (Marketplace)

This repository is a learning-focused case study for a product + data science/ML interview round at a marketplace. It is written as a short conversation between interviewer and candidate.

## Conversation

**Interviewer**: You are joining a marketplace platform where users browse and bid on curated items across many categories. Recent data shows:

- Declining engagement on the home feed
- Lower conversion on item detail pages
- Increased catalog size and fast item turnover (new items daily, some items expire quickly)

Propose and prototype a recommendation system that improves engagement and conversion while respecting marketplace constraints (freshness, diversity, fraud/abuse risk, and latency).

**Candidate**: Before I propose solutions, I will briefly state the user journey to ground the discussion. Users discover items via home feed or search, evaluate on item pages, and take actions like click, save, or bid.

To proceed quickly, I will ask only key clarification questions:

- Which surface are we optimizing (home feed, search, item page)?
- What is the north-star metric and key guardrail?
- Which user segment and journey stage matter most?
- What data is available (impressions, clicks, bids, saves)?
- Any hard constraints (latency, freshness/diversity, integrity)?

**Interviewer**: Please proceed with reasonable assumptions. Just state them clearly, and explain how you’d validate them with data.

**Candidate**: Great. I’ll state my assumptions explicitly (and flag what I’d validate), define success metrics, propose a baseline, and then outline a stronger model with evaluation and a rollout plan.

## References (Public Case Study Examples)

- https://www.casebasix.com/pages/amazon-case-study-interview
- https://finalroundai.com/interview-questions/design-amazon-recommender-system
- https://rohan-paul.com/p/ml-case-study-interview-question-a5a

