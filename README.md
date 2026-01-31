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

**Candidate**: Here are my assumptions (and how I’d validate them):

- The home feed is a ranked list where we can log impressions reliably (validate: impression logging completeness + position bias checks).
- “Qualified engagement” is a leading indicator for bidding (validate: correlation/causal lift via A/B test; check downstream bid impact).
- Recency and “ending soon” matter in auctions and should be explicit features/constraints (validate: engagement vs. time-to-end curves).

**Candidate**: Next, I’ll structure the solution in steps.

**Candidate (Step 2 — Define metrics)**:

- Primary: qualified engagement per session (as defined).
- Guardrails: bid conversion, hides/complaints, diversity coverage (e.g., category entropy), latency p95.
- Slice metrics by user segment (new vs returning), category, price band, and time-to-end.

**Candidate (Step 3 — Baseline)**:

- Retrieval: rule-based candidates (ending soon + newly listed + popular in category) + simple item-item similarity (co-view/co-bid).
- Ranking: a lightweight model (e.g., logistic regression / GBDT) predicting click or “qualified action” using user features + item features + context (position, time).
- Rerank layer: enforce freshness and diversity constraints.

**Candidate (Step 4 — Stronger model)**:

- Use user/item embeddings for retrieval (two-tower) to handle sparsity and scale.
- Add a learning-to-rank stage that optimizes qualified engagement with calibration for bids as a downstream objective.
- Handle cold-start with content features (category/attributes) and exploration.

**Candidate (Step 5 — Evaluation & experimentation)**:

- Offline: temporal train/validation split; report NDCG/Recall@K for clicks/qualified actions plus bias-aware analysis.
- Online: A/B test on returning users first; monitor guardrails (bids, trust signals, diversity, latency).

**Candidate (Step 6 — Rollout & operations)**:

- Start with a safe baseline behind a feature flag, then iterate.
- Add monitoring for drift (new inventory shifts), abuse patterns, and seller fairness.

## References (Public Case Study Examples)

- https://www.casebasix.com/pages/amazon-case-study-interview
- https://finalroundai.com/interview-questions/design-amazon-recommender-system
- https://rohan-paul.com/p/ml-case-study-interview-question-a5a

