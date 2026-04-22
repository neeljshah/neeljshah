### Neel Shah

Quantitative researcher — spatial CV features from broadcast video that public NBA APIs don't ship, priced against prop markets.

[![GitHub followers](https://img.shields.io/github/followers/neeljshah?style=flat&color=blue&label=followers)](https://github.com/neeljshah)
[![Stars](https://img.shields.io/badge/total%20stars-2-yellow)](https://github.com/neeljshah)
[![Focus](https://img.shields.io/badge/focus-sports%20quant-lightgrey)](https://github.com/neeljshah/court-vision)
[![Stack](https://img.shields.io/badge/stack-Python%20%7C%20PyTorch%20%7C%20XGBoost-informational)](https://github.com/neeljshah/court-vision)

---

**Featured**

**[court-vision](https://github.com/neeljshah/court-vision)** — *Possession-level NBA simulator: CV tracking → 75 ML models → 10K Monte Carlo → Kelly portfolio.*
7 live prop markets (pts R²=0.47, reb=0.40, ast=0.46); 80 games ingested from broadcast video at ~$0.40/game on commodity GPUs; CLV +14 bps/bet vs Pinnacle over 312 settled picks (t=2.3).

**[walkforge](https://github.com/neeljshah/walkforge)** — *Timeseries-aware walk-forward + purged-K-fold backtester for ML models.*
Prevents leakage across 60+ sports features; pandas-in, full metrics-out including bootstrapped CIs and Sharpe decomposition.

**[kellycorr](https://github.com/neeljshah/kellycorr)** — *Fractional-Kelly sizer with Ledoit-Wolf shrinkage correlation.*
Handles correlated legs (same-game parlays); naive Kelly overbets by ~2.3× at ρ>0.4 — shrinkage estimator closes the gap.

---

**More projects**

| Repo | What | Stack | Status |
|------|------|-------|--------|
| [linewatch](https://github.com/neeljshah/linewatch) | Line-movement scraper; steam detection + book disagreement signals | Python, SQLite | active |
| [calibcraft](https://github.com/neeljshah/calibcraft) | Platt/isotonic/beta calibration with ECE, MCE, reliability diagrams | sklearn, Python | active |
| [clvtrack](https://github.com/neeljshah/clvtrack) | CLV benchmark: Shin-devigged, bootstrap-CI'd, sliced by market/time/size | Python | active |
| [enterpriseRevenueEngine](https://github.com/neeljshah/enterpriseRevenueEngine) | End-to-end BI + AI revenue pipeline | Python | prototype |
| [BasketBallLogic](https://github.com/neeljshah/BasketBallLogic) | AI-assisted basketball analytics | Python | prototype |
| [sports-betting-analytics](https://github.com/neeljshah/sports-betting-analytics) | Market efficiency analysis, EV modeling, Kelly bankroll optimization | Python | stable |
| [draft-value-model](https://github.com/neeljshah/draft-value-model) | NBA draft career WAR prediction + trade analyzer | Python | stable |
| [mlops-monitor](https://github.com/neeljshah/mlops-monitor) | ML monitoring pipeline: Prefect + MLflow + Evidently + Grafana | Python | stable |
| [game-film-analyzer](https://github.com/neeljshah/game-film-analyzer) | YOLOv8 + ByteTrack + court homography + FastAPI | Python | stable |
| [sports-scout-rag](https://github.com/neeljshah/sports-scout-rag) | Scouting RAG assistant: LangChain + ChromaDB + Claude API | Python | stable |
| [injury-risk-predictor](https://github.com/neeljshah/injury-risk-predictor) | NBA injury risk: survival analysis + LightGBM | Python | stable |
| [nba-win-probability](https://github.com/neeljshah/nba-win-probability) | Real-time XGBoost win prob + SHAP + FastAPI + Streamlit | Python | stable |
| [mlops-pipeline](https://github.com/neeljshah/mlops-pipeline) | Production ML pipeline: MLflow, FastAPI, Docker, CI/CD | Python | stable |
| [sports-vision-tracker](https://github.com/neeljshah/sports-vision-tracker) | Multi-object tracking: Kalman filters, court homography, perf analytics | Python, OpenCV | stable |
| [deep-learning-cv](https://github.com/neeljshah/deep-learning-cv) | NumPy backprop → PyTorch CNNs → ResNet/EfficientNet transfer learning | Python, PyTorch | stable |
| [llm-bi-assistant](https://github.com/neeljshah/llm-bi-assistant) | NL→SQL with auto-viz via Claude API | Python | stable |
| [time-series-forecasting-suite](https://github.com/neeljshah/time-series-forecasting-suite) | ARIMA/Prophet/LSTM benchmark across retail, energy, web traffic | Python | stable |
| [nfl-draft-analytics](https://github.com/neeljshah/nfl-draft-analytics) | NFL draft value model: survival analysis + regression | Python | stable |
| [nba-player-analytics](https://github.com/neeljshah/nba-player-analytics) | XGBoost/RF/NN player perf prediction + Plotly dashboards | Python | stable |
| [market-sentiment-nlp](https://github.com/neeljshah/market-sentiment-nlp) | FinBERT alpha signals + backtesting | Python | stable |
| [customer-churn-predictor](https://github.com/neeljshah/customer-churn-predictor) | Churn prediction: SHAP, ensemble models, Streamlit | Python | stable |
| [archetypingClustering](https://github.com/neeljshah/archetypingClustering) | NBA player archetype clustering 2023-24 | Python | archive |
| [gravityInfluence](https://github.com/neeljshah/gravityInfluence) | Player gravity / floor-spacing influence 2023-24 | Python | archive |
| [globalSuperstore](https://github.com/neeljshah/globalSuperstore) | Power BI + SQL global superstore analysis | SQL | archive |
| [creationGrade](https://github.com/neeljshah/creationGrade) | Creation grade metric 2023-24 NBA | Python | archive |
| [momentumTrend](https://github.com/neeljshah/momentumTrend) | Momentum/run analysis in NBA games 2023-24 | Python | archive |
| [onlineRetail](https://github.com/neeljshah/onlineRetail) | European online retail dataset EDA | Python | archive |
| [housingPrice](https://github.com/neeljshah/housingPrice) | Ames housing price prediction | Python | archive |
| [breastCancer](https://github.com/neeljshah/breastCancer) | Wisconsin breast cancer classification | Python | archive |

---

**Research notes**

- *Vig-adjusted no-vig: measuring the efficiency gap between NBA props and sides* — Shin de-juicing across ~50K prices; props show 4× the max-min dispersion of sides.
- *Does broadcast video add R²? A SHAP study of spatial features in NBA prop models* — points model gains +0.08 R² over API-only baseline; 31% of SHAP mass on spatial features.
- *CLV vs Pinnacle on 312 settled picks* — +14 bps/bet, t=2.3. Decomposed by market, time-to-close, and bet-size-vs-Kelly.
- *Fractional Kelly under correlated bets: the same-game-parlay trap* — naive Kelly overbets by ~2.3× when correlation ρ>0.4; shrinkage estimator cuts this.
- *Debugging an 80-game RunPod run: CFS quota, OMP oversubscription, and a 3× slowdown from one missing env var* — ops writeup.

---

**Stack**

- *Data / ingest:* yt-dlp, B2, SQLite work queue, idempotent workers, content-hash verification
- *CV:* PyTorch, YOLOv8n, OpenCV SIFT, Kalman/Hungarian, OSNet, EasyOCR, decord (NVDEC)
- *Modeling:* XGBoost, LightGBM, CatBoost, sklearn, Platt/isotonic/beta calibration, SHAP
- *Backtesting:* walk-forward, purged K-fold, bootstrapped CIs
- *Execution / risk:* fractional Kelly, correlation shrinkage, Shin de-vig, CLV attribution
- *Infra:* FastAPI, Next.js, Postgres, conda, RunPod/GCE, GitHub Actions

---

![Streak](https://streak-stats.demolab.com?user=neeljshah&theme=tokyonight&hide_border=true)
![Stats](https://github-readme-stats.vercel.app/api?username=neeljshah&theme=tokyonight&show_icons=true&hide_border=true&count_private=true)
![Top Languages](https://github-readme-stats.vercel.app/api/top-langs/?username=neeljshah&theme=tokyonight&layout=compact&hide_border=true)
