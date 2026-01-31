# Step 1: Clarify and Frame the Problem

This document is a guide for the first step in a case study interview: clarifying and framing the problem. The goal is to remove ambiguity, align on success metrics, and define constraints before proposing solutions.

## Outcome of Step 1

By the end of this step, you should have:

- A clear restatement of the problem
- The target surface and user segment
- A primary success metric (north-star)
- Key constraints and risks
- A shared understanding of scope and time horizon

## Clarifying Questions to Ask

Use these questions to gather the minimum information needed to proceed.

### Product Context

- Which product surface are we focusing on (home feed, search, item page)?
- Who is the primary user segment for this surface?
- What is the primary business goal for this initiative?

### Success Metrics

- What is the north-star metric we should optimize?
- What guardrail metrics must not regress?
- Over what time horizon should we measure impact (30/60/90 days)?

### Constraints & Trade-offs

- Are there latency or infrastructure constraints for serving recommendations?
- How important is freshness vs. relevance vs. diversity?
- Are there marketplace integrity constraints (spam, fraud, seller fairness)?

### Data & Experimentation

- What data is available for training and evaluation?
- Do we have historical interaction logs (clicks, bids, saves)?
- What experiments or A/B testing capabilities exist today?

### Scope & Priorities

- Is the goal to build a baseline quickly or to maximize performance?
- Are we expected to propose a full system design or a prototype model?
- What is the acceptable implementation complexity for this round?

## Suggested Framing Statement (Example)

“We’re improving recommendations for the home feed to increase qualified engagement while respecting freshness and diversity. I’ll start with a simple baseline, define success metrics, and then propose a stronger model with an evaluation plan.”

