# Neel Shah

**Quantitative researcher.** I build systems that extract spatial features from NBA broadcast video — defender distance, floor spacing, fatigue proxies — and use them to find edges in prop markets that pure box-score models miss.

The core thesis: broadcast video contains information public APIs don't expose. A shot with a hand in the face at 18 feet is not the same as an open mid-range. Tracking that difference at scale, pricing it, and betting it correctly is the problem.

[![Focus](https://img.shields.io/badge/focus-sports%20quant-0d1117?style=flat-square&labelColor=161b22)](https://github.com/neeljshah/court-vision)
[![Stack](https://img.shields.io/badge/Python%20%7C%20PyTorch%20%7C%20XGBoost-0d1117?style=flat-square&labelColor=161b22)](https://github.com/neeljshah/court-vision)
[![Location](https://img.shields.io/badge/location-United%20States-0d1117?style=flat-square&labelColor=161b22)](https://github.com/neeljshah)

---

## Featured Work

### [court-vision](https://github.com/neeljshah/court-vision)
*Possession-level NBA simulator — broadcast video → spatial features → prop market edges*

The full stack: YOLOv8n detects players and the ball, SIFT homography maps court coordinates, Kalman/Hungarian tracking links identities frame-to-frame, OSNet re-ID resolves jersey swaps, EasyOCR reads jersey numbers. Possession sequences feed 75 trained models. 10K Monte Carlo simulations per game produce a distribution over outcomes. A fractional-Kelly portfolio with CLV tracking sizes bets against the closing line.

**Numbers that matter:**
- 7 live prop models — pts R²=0.47, reb=0.40, ast=0.46, fg3m=0.28, blk=0.18, tov=0.25, stl=0.09
- 80 games ingested from broadcast video at ~$0.40/game on commodity RTX 3090s
- CLV +14 bps/bet vs Pinnacle over 312 settled picks (t=2.3), ROI +3.8%
- Spatial features (defender_distance, spacing, fatigue) account for 31% of SHAP mass in the points model; +0.08 R² over API-only baseline
- Pipeline runs at ~80 fps aggregate (4 workers × 20 fps) on a single RTX 3090 — $2.50–4.50 per full-season run

**Architecture:** `YOLOv8n → SIFT homography → Kalman/Hungarian → OSNet re-ID → EasyOCR → EventDetector → FastAPI → Next.js`

---

### [walkforge](https://github.com/neeljshah/walkforge)
*Timeseries-aware backtester — no leakage, no lookahead, bootstrapped confidence intervals*

Standard k-fold cross-validation leaks future information when features have serial correlation — a real problem in sports modeling where rolling averages, fatigue proxies, and momentum signals are all computed across time. walkforge implements walk-forward validation with embargo gaps and purged k-fold splits. Pandas-in, full metrics-out: Sharpe, Calmar, bootstrapped CIs, per-fold P&L curves.

**Why it matters:** The points model's R²=0.47 is measured with purged k-fold. Naive cross-val on the same data reports R²=0.61. That gap is the leakage penalty — models that "work" in backtesting but fail live.

---

### [kellycorr](https://github.com/neeljshah/kellycorr)
*Fractional-Kelly position sizer with Ledoit-Wolf shrinkage correlation*

Naive Kelly assumes independent bets. Same-game parlays, correlated props (points and assists on a pass-first guard), and parallel legs on the same game all violate this. kellycorr estimates the bet correlation matrix using Ledoit-Wolf shrinkage (avoids singular covariance at small sample sizes), then solves the full correlated Kelly problem. At ρ>0.4, naive Kelly overbets by ~2.3×. The shrinkage estimator closes that without requiring large historical samples.

---

## Spinout Tools
*Extracted from court-vision. Each solves one problem, usable independently.*

| Repo | What it does | Key detail |
|------|-------------|------------|
| [linewatch](https://github.com/neeljshah/linewatch) | Sportsbook line-movement scraper with steam detection and book-disagreement signals | Detects when sharp action moves one book but not others — a CLV leading indicator |
| [calibcraft](https://github.com/neeljshah/calibcraft) | Platt/isotonic/beta calibration with reliability diagrams, ECE, MCE | sklearn-compatible; works on any binary classifier or win-prob model |
| [clvtrack](https://github.com/neeljshah/clvtrack) | Closing-line-value benchmark | Shin-devigged, bootstrap-CI'd, sliced by market, time-to-close, and bet size |

---

## More Projects

| Repo | What | Stack |
|------|------|-------|
| [sports-betting-analytics](https://github.com/neeljshah/sports-betting-analytics) | Market efficiency analysis, EV modeling, Kelly bankroll optimization | Python |
| [draft-value-model](https://github.com/neeljshah/draft-value-model) | NBA draft career WAR prediction + trade analyzer using survival analysis | Python, LightGBM |
| [nba-win-probability](https://github.com/neeljshah/nba-win-probability) | Real-time XGBoost win probability with SHAP explanations + FastAPI serving | Python, XGBoost |
| [game-film-analyzer](https://github.com/neeljshah/game-film-analyzer) | YOLOv8 + ByteTrack + court homography + FastAPI — earlier prototype of court-vision CV layer | Python, PyTorch |
| [injury-risk-predictor](https://github.com/neeljshah/injury-risk-predictor) | NBA injury risk model using survival analysis and LightGBM on load/age/history features | Python |
| [sports-scout-rag](https://github.com/neeljshah/sports-scout-rag) | Scouting report RAG assistant: LangChain + ChromaDB + Claude API | Python |
| [mlops-monitor](https://github.com/neeljshah/mlops-monitor) | Production ML monitoring: concept drift detection with Evidently, experiment tracking with MLflow | Python, Prefect |
| [mlops-pipeline](https://github.com/neeljshah/mlops-pipeline) | End-to-end ML pipeline: MLflow, FastAPI serving, Docker, GitHub Actions CI/CD | Python |
| [sports-vision-tracker](https://github.com/neeljshah/sports-vision-tracker) | Multi-object sports tracking: Kalman filters, court homography, performance analytics | Python, OpenCV |
| [llm-bi-assistant](https://github.com/neeljshah/llm-bi-assistant) | Natural language → SQL with automatic chart generation via Claude API | Python |
| [deep-learning-cv](https://github.com/neeljshah/deep-learning-cv) | NumPy backprop from scratch → PyTorch CNNs → ResNet/EfficientNet transfer learning | Python, PyTorch |
| [nfl-draft-analytics](https://github.com/neeljshah/nfl-draft-analytics) | NFL draft pick value model and trade analyzer using survival analysis and regression | Python |
| [nba-player-analytics](https://github.com/neeljshah/nba-player-analytics) | XGBoost/RF/NN player performance prediction with interactive Plotly dashboards | Python |
| [time-series-forecasting-suite](https://github.com/neeljshah/time-series-forecasting-suite) | ARIMA / Prophet / LSTM benchmark across retail, energy, and web traffic domains | Python |
| [market-sentiment-nlp](https://github.com/neeljshah/market-sentiment-nlp) | FinBERT alpha signal generation with backtesting | Python |
| [customer-churn-predictor](https://github.com/neeljshah/customer-churn-predictor) | Churn prediction with SHAP explainability, ensemble models, Streamlit dashboard | Python |
| [enterpriseRevenueEngine](https://github.com/neeljshah/enterpriseRevenueEngine) | End-to-end BI + AI revenue pipeline | Python |
| [archetypingClustering](https://github.com/neeljshah/archetypingClustering) | NBA player archetype clustering 2023-24 | Python |
| [gravityInfluence](https://github.com/neeljshah/gravityInfluence) | Player gravity / floor-spacing influence study 2023-24 | Python |
| [creationGrade](https://github.com/neeljshah/creationGrade) | Creation grade metric 2023-24 NBA | Python |
| [momentumTrend](https://github.com/neeljshah/momentumTrend) | Momentum and run analysis in NBA games 2023-24 | Python |
| [BasketBallLogic](https://github.com/neeljshah/BasketBallLogic) | AI-assisted basketball analytics experiments | Python |
| [globalSuperstore](https://github.com/neeljshah/globalSuperstore) | Power BI + SQL analysis of global superstore dataset | SQL |

---

## Research Notes

- ***Vig-adjusted no-vig: measuring the efficiency gap between NBA props and sides*** — Shin de-juicing across ~50K prices. Props show 4× the max-min dispersion of sides; the soft-market hypothesis holds at the market level but not within prop types.

- ***Does broadcast video add R²? A SHAP study of spatial features in NBA prop models*** — Points model gains +0.08 R² over an API-only baseline. 31% of SHAP mass concentrates on spatial features (defender_distance, spacing_score, fatigue_proxy). The gain is largest for volume shooters with high shot-location variance.

- ***CLV vs Pinnacle on 312 settled picks*** — +14 bps/bet, t=2.3. Decomposed by market (sides vs totals vs props), time-to-close (sharp early vs closing), and bet size vs Kelly fraction. Props close softer; CLV is higher but variance is wider.

- ***Fractional Kelly under correlated bets: the same-game-parlay trap*** — Naive Kelly overbets by ~2.3× when ρ>0.4. Ledoit-Wolf shrinkage stabilizes the covariance estimate at n=50–200 bets. Full derivation with simulation at different ρ levels.

- ***Debugging an 80-game RunPod run: CFS quota, OMP oversubscription, and a 3× slowdown from one missing env var*** — CFS quota of 17.85 cores throttles parallel workers without warning. `OMP_NUM_THREADS=6` recovered 3× throughput. Notes on decord vs PyAV, VRAM flush intervals, and video-read latency on mfs vs local disk.

---

## Stack

| Concern | Tools |
|---------|-------|
| Data / ingest | yt-dlp, Backblaze B2, SQLite work queue, idempotent content-hash workers |
| Computer vision | PyTorch, YOLOv8n, OpenCV SIFT, Kalman/Hungarian, OSNet re-ID, EasyOCR, decord (NVDEC) |
| Modeling | XGBoost, LightGBM, CatBoost, scikit-learn, Platt/isotonic/beta calibration, SHAP |
| Backtesting | Walk-forward validation, purged k-fold, bootstrapped CIs, embargo gaps |
| Execution / risk | Fractional Kelly, Ledoit-Wolf shrinkage, Shin de-vig, CLV attribution |
| Serving / infra | FastAPI, Next.js, PostgreSQL, conda, RunPod, GCE, GitHub Actions |
