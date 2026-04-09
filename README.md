# Betting Benchmarks

**Sports analytics platform that tracks public NFL prediction models and benchmarks their accuracy.**

[bettingbenchmarks.com](https://bettingbenchmarks.com)

---

## What it does

Betting Benchmarks aggregates public NFL prediction models, tracks their picks across every game, and ranks them in a composite accuracy leaderboard. It also includes a proprietary ML model that consistently outperforms market lines.

**800 monthly active users.** Mentioned by [NFElo](https://nfelo.espn.com/) and used by analysts at ESPN.

## How it works

```
  ┌─────────────────────┐
  │  Model Sources       │
  │                     │
  │  Public NFL prediction│
  │  models, market lines,│
  │  historical results   │
  └──────────┬──────────┘
             │
  ┌──────────▼──────────┐
  │  Data Pipelines      │
  │  (Python)            │
  │                     │
  │  Scrape, normalize,  │
  │  validate predictions│
  │  against outcomes    │
  └──────────┬──────────┘
             │
  ┌──────────▼──────────┐
  │  Scoring Engine      │
  │                     │
  │  Accuracy metrics,   │
  │  composite rankings, │
  │  head-to-head stats  │
  └──────────┬──────────┘
             │
  ┌──────────▼──────────┐     ┌──────────────────┐
  │  Web Application     │     │  Proprietary ML  │
  │  (Next.js + Vercel)  │     │  Model           │
  │                     │     │                  │
  │  Leaderboards,      │     │  Feature eng.,   │
  │  model comparisons, │◄────│  scikit-learn,   │
  │  historical trends  │     │  backtested      │
  └─────────────────────┘     └──────────────────┘
```

## Key Design Decisions

### Composite leaderboard scoring
Individual accuracy metrics (ATS, O/U, moneyline) can be misleading in isolation. The composite score weights multiple dimensions to surface models that are consistently good rather than occasionally great.

### Proprietary ML model
Built a prediction model using engineered features from historical game data, team metrics, and situational factors. Trained with scikit-learn and backtested across multiple seasons to validate out-of-sample performance before deploying live.

### Automated pipelines
Predictions are scraped and validated automatically each week during the NFL season. Results are scored against outcomes as games complete. Zero manual intervention during the season.

## Tech Stack

| Layer | Technology |
|-------|-----------|
| ML/Analytics | Python, scikit-learn, pandas |
| Frontend | Next.js, Vercel |
| Database | Supabase (PostgreSQL) |
| Backend | Railway |
| Data Collection | Custom scrapers, public model APIs |

## Status

Live at [bettingbenchmarks.com](https://bettingbenchmarks.com). Active during NFL season (September - February).

---

*Source code is in a private repository. This repo documents the architecture and design decisions.*
