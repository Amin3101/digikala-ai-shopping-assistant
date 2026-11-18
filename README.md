# Digikala AI Shopping Assistant

Final project for Quera AI Bootcamp — Cohort 13.

An LLM-powered system built on a real-world dataset of Digikala products and user reviews
(1M+ product records, 6M+ Persian user comments). The system helps users search, compare,
and understand products based on real user feedback, and helps store category managers
analyze recurring issues and brand feedback at scale.

## Features

1. **Product Search & Discovery** — Natural language (Persian) product search combining
   structured product data and free-text reviews (price range, brand, satisfaction, etc.).
2. **Review-Based Q&A** — Answers questions about a specific product grounded in real user
   reviews, with cited review IDs/evidence (e.g. "What do buyers complain about most?").
3. **Product Comparison** — Compares two or more products based on price, specs, and
   review-derived pros/cons, distinguishing hard data from inferred/model opinion.
4. **Category-Level Analytics** — Answers category-level analytical questions for store
   managers (recurring complaints, brand comparisons, high-review/low-recommendation
   products, etc.).

## Purchase Recommendation Prediction

A supervised model that predicts `status_recommendation` for a review
(`recommended` / `not_recommended` / `no_idea`) from review text. Evaluated primarily
with **Macro F1** (all three classes matter, not just the majority class).

## Evaluation

The final system is evaluated across multiple dimensions:
- **Answer quality** — relevance and usefulness to the user's need
- **Grounding** — whether claims are supported by retrieved product/review data
- **Retrieval quality** — relevance of retrieved evidence/reviews
- **Recommendation prediction** — Macro F1 on `status_recommendation`
- **Latency** — response time across scenarios
- **Cost** — API usage / token consumption
- **Failure analysis** — real failure cases, likely causes, and mitigation attempts

## Dataset

[Digikala_comments_products](https://huggingface.co/datasets/RadeAI/Digikala_comments_products)
(pinned revision `89c3133b169c8d3793db8834f56f32fee33d9db0`)

- `digikala-products.csv` — product metadata (title, rating, category, brand, price, etc.)
- `digikala-comments.csv` — user reviews (text, rating, recommendation status, pros/cons, etc.)

Linked via product `id`.

> ⚠️ Raw data — not guaranteed to be clean, deduplicated, balanced, or ML-ready.
> Data-quality decisions (cleaning, sampling, Persian text preprocessing, etc.) are
> part of the project and documented in the report.

## Tech Stack / Approach

Architecture choice (Prompting, RAG, Embeddings, Fine-tuning, Agents, Tool Calling, etc.)
is documented in `/docs` along with the rationale and experimental evidence behind it.

## Project Structure

```
.
├── data/              # raw & processed data (not committed — see .gitignore)
├── src/               # core source code
├── notebooks/         # exploration & experiments
├── eval/              # evaluation sets and scripts
├── docs/              # report, analysis, design decisions
└── README.md
```

## Setup

```bash
git clone <repo-url>
cd digikala-ai-shopping-assistant
pip install -r requirements.txt
```

Set your API key as an environment variable (do **not** commit it):

```bash
export QBC13_API_KEY="your-key-here"
```

## Running

```bash
# TODO: add run instructions as the system is implemented
```

## Evaluation

```bash
# TODO: add evaluation run instructions
```

## Team

- Nima
- Amin
- Hirad
- Arshia
- Pourya
- Mohammad Hossein

## Branching Strategy

- `main` — stable, production-ready code
- `develop` — integration branch for ongoing work
- `nima`, `amin`, `hirad`, `arshia`, `pourya`, `Mohammad Hossein` — individual feature branches, branched
  off `develop`, merged back via PR

## License

TODO
