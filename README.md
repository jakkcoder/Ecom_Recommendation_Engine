# Recommendation Engine Case Study (Marketplace)

This repository is a learning-focused case study for a product + data science/ML interview round at a marketplace. It is written as a short conversation between interviewer and candidate.

## Conversation

**Interviewer**: You are joining a marketplace platform where users browse and bid on curated items across many categories. Recent data shows:

- Declining engagement on the home feed
- Lower conversion on item detail pages
- Increased catalog size and fast item turnover (new items daily, some items expire quickly)

Propose and prototype a recommendation system that improves engagement and conversion while respecting marketplace constraints (freshness, diversity, fraud/abuse risk, and latency).

**Candidate**: Before I propose solutions, I will briefly state the user journey to ground the discussion. Users discover items via home feed or search, evaluate on item pages, and take actions like click, save, or bid.

To proceed quickly, I will ask only a few key clarification questions.

**Candidate**: Which surface are we optimizing (home feed, search, item page)?
**Interviewer**: Focus on the **home feed** for an auction marketplace like Catawiki. Users land there first, and it’s underperforming.

**Candidate**: What is the north-star metric and one key guardrail?
**Interviewer**: **North-star**: qualified engagement per session on the home feed (e.g., session with at least one meaningful action like click → watchlist or bid).  
**Guardrail**: don’t reduce conversion to bid, and don’t hurt user trust (e.g., hides/complaints).

**Candidate**: Which user segment and journey stage matter most?
**Interviewer**: Prioritize **returning users** (they drive most bids). Biggest drop-off is **feed → item-detail click**. Secondary: item-detail → watchlist/bid.

**Candidate**: What data is available (impressions, clicks, bids, saves)?
**Interviewer**: We have feed impressions (items shown + position), clicks to item pages, watchlist/saves, bids (and outcomes), and item metadata (category/attributes, price estimate, auction end time, plus item/seller quality signals).

**Candidate**: Any hard constraints (latency, freshness/diversity, integrity)?
**Interviewer**: Yes. Latency p95 ~150ms, enforce freshness (new items + ending soon), ensure diversity (avoid near-duplicates), and protect integrity (avoid manipulation; don’t over-promote low-quality sellers/items).

**Interviewer**: Please proceed with reasonable assumptions. State them clearly, and explain how you’d validate them with data.

**Candidate**: Great. I’ll state assumptions explicitly (and flag what I’d validate), define success metrics, propose a baseline retrieval + ranking approach, and then outline a stronger model with offline evaluation and an online rollout plan with guardrails.

## References (Public Case Study Examples)

- https://www.casebasix.com/pages/amazon-case-study-interview
- https://finalroundai.com/interview-questions/design-amazon-recommender-system
- https://rohan-paul.com/p/ml-case-study-interview-question-a5a

