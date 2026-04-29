<div align="center">

# Neel J. Shah

### ML Engineer &middot; Computer Vision &middot; Probabilistic Modeling &middot; Sports Quant


[![Email](https://img.shields.io/badge/neeljshah22%40gmail.com-D14836?style=flat&logo=gmail&logoColor=white)](mailto:neeljshah22@gmail.com)
[![Portfolio](https://img.shields.io/badge/portfolio-neelshahportfolio.netlify.app-000?style=flat)](https://neelshahportfolio.netlify.app)
[![LinkedIn](https://img.shields.io/badge/neeljshah22-0A66C2?style=flat&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/neeljshah22/)

</div>

---

I build end-to-end ML systems &mdash; from raw unstructured data through feature engineering, model training, calibration, and production serving. My work spans computer vision, NLP, reinforcement learning, causal inference, recommendation systems, time-series forecasting, and MLOps. Current focus: extracting spatial features from broadcast video that don't exist in any public dataset and pricing them against live sports markets. Open to any role in ML, Computer Vision, Quantitative Researcher, and/or Sports Analytics.

---

## Flagship &mdash; CourtVision

**[court-vision](https://github.com/neeljshah/court-vision)** &mdash; Possession-level NBA simulator. Broadcast video in, fractional-Kelly-sized +EV positions out.

```
Broadcast Video -> YOLOv8n detection -> SIFT homography -> Kalman+Hungarian tracking
  -> OSNet re-ID -> EasyOCR -> EventDetector -> CV Features (defender_distance,
    spacing_score, legs_fatigue) -> 75-Model ML Stack -> 10K Monte Carlo
  -> Fractional Kelly + Ledoit-Wolf correlation -> CLV benchmark vs Pinnacle close
```

**75 trained models &middot; 7 prop models &middot; R&sup2; 0.47 pts &middot; +14 bps CLV vs Pinnacle close &middot; 960+ tests**

Three CV features carry 31% of SHAP mass in the points model &mdash; these don't exist in any public NBA dataset. Walk-forward season-purged evaluation, Shin-devigged closing lines, conformal prediction intervals on every bet.

---

## What I Build

### Computer Vision & Tracking

| Project | What It Does |
|---------|-------------|
| [court-vision](https://github.com/neeljshah/court-vision) | Full CV+ML NBA pipeline &mdash; YOLOv8, homography, multi-object tracking, re-ID, event detection. 75 models, FastAPI + Next.js serving |
| [game-film-analyzer](https://github.com/neeljshah/game-film-analyzer) | Automated play breakdown &mdash; YOLOv8 + ByteTrack + court homography + FastAPI |
| [sports-vision-tracker](https://github.com/neeljshah/sports-vision-tracker) | Multi-object player tracking with Kalman filters, court homography, real-time analytics |
| [deep-learning-cv](https://github.com/neeljshah/deep-learning-cv) | Deep learning from scratch &mdash; NumPy backprop implementation through PyTorch CNNs and ResNet/EfficientNet transfer learning |

### Probabilistic Modeling & Calibration

| Project | What It Does |
|---------|-------------|
| [calibcraft](https://github.com/neeljshah/calibcraft) | Platt / isotonic / beta calibration with reliability diagrams, ECE, MCE. Sklearn-compatible |
| [kellycorr](https://github.com/neeljshah/kellycorr) | Correlated Kelly criterion &mdash; full-covariance fractional Kelly sizing for multi-leg portfolios |
| [clvtrack](https://github.com/neeljshah/clvtrack) | Closing-line value tracker &mdash; benchmarks predictions against Pinnacle close to measure edge decay |
| [walkforge](https://github.com/neeljshah/walkforge) | Walk-forward + purged-K-fold backtester for ML models. Pandas-in, metrics-out |

### Reinforcement Learning & Optimization

| Project | What It Does |
|---------|-------------|
| [rl-portfolio-optimizer](https://github.com/neeljshah/rl-portfolio-optimizer) | PPO/SAC agents for multi-asset portfolio rebalancing &mdash; Gymnasium env with transaction costs, HMM regime detection, walk-forward backtest. Sharpe 1.31 vs 0.91 risk-parity baseline |

### Causal Inference & Experimentation

| Project | What It Does |
|---------|-------------|
| [causal-inference-toolkit](https://github.com/neeljshah/causal-inference-toolkit) | Full causal pipeline &mdash; propensity matching, doubly-robust estimation, IV, DiD, uplift modeling, A/B test analysis (CUPED, sequential testing) with DoWhy + EconML |

### Recommendation Systems

| Project | What It Does |
|---------|-------------|
| [recommendation-system](https://github.com/neeljshah/recommendation-system) | Hybrid recommender &mdash; ALS + content-based + two-tower neural retrieval with FAISS ANN. Re-ranking with popularity debiasing. NDCG@10 0.378 on MovieLens-25M |

### Fraud & Anomaly Detection

| Project | What It Does |
|---------|-------------|
| [fraud-detection-engine](https://github.com/neeljshah/fraud-detection-engine) | Real-time fraud detection &mdash; XGBoost + Isolation Forest + LSTM autoencoder ensemble. Sub-100ms inference, SHAP explainability, streaming simulation. AUPRC 0.89 |

### NLP & Language Models

| Project | What It Does |
|---------|-------------|
| [market-sentiment-nlp](https://github.com/neeljshah/market-sentiment-nlp) | Stock sentiment analysis &mdash; FinBERT + traditional NLP for alpha signal generation with walk-forward backtest |
| [llm-bi-assistant](https://github.com/neeljshah/llm-bi-assistant) | LLM-powered BI assistant &mdash; natural language to SQL query generation with automatic visualization using Claude API |
| [sports-scout-rag](https://github.com/neeljshah/sports-scout-rag) | RAG scouting assistant &mdash; LangChain + ChromaDB + Claude for natural-language queries over structured sports data |

### MLOps & Infrastructure

| Project | What It Does |
|---------|-------------|
| [mlops-monitor](https://github.com/neeljshah/mlops-monitor) | Automated ML monitoring &mdash; Prefect orchestration + MLflow tracking + Evidently drift detection + Grafana dashboards |
| [mlops-pipeline](https://github.com/neeljshah/mlops-pipeline) | Production ML pipeline &mdash; MLflow experiment tracking, FastAPI serving, Docker containerization, CI/CD |
| [realtime-feature-platform](https://github.com/neeljshah/realtime-feature-platform) | Feature store &mdash; point-in-time joins, sliding-window streaming aggregates, online/offline parity monitoring. Redis + DuckDB + FastAPI |

### Sports Analytics

| Project | What It Does |
|---------|-------------|
| [linewatch](https://github.com/neeljshah/linewatch) | Real-time line movement tracker &mdash; scrapes opening/closing odds, flags sharp action and steam moves across books |
| [draft-value-model](https://github.com/neeljshah/draft-value-model) | NBA draft value model &mdash; career WAR prediction from combine + college stats with trade surplus analyzer |
| [injury-risk-predictor](https://github.com/neeljshah/injury-risk-predictor) | NBA injury risk &mdash; survival analysis + LightGBM for return-to-play and load management |
| [nba-win-probability](https://github.com/neeljshah/nba-win-probability) | Real-time NBA win probability &mdash; XGBoost + SHAP + FastAPI + Streamlit |
| [nfl-draft-analytics](https://github.com/neeljshah/nfl-draft-analytics) | NFL draft pick value model &mdash; survival analysis + regression on historical career outcomes |
| [nba-player-analytics](https://github.com/neeljshah/nba-player-analytics) | NBA player performance analytics &mdash; XGBoost, Random Forest, Neural Networks with Plotly dashboards |

### Time Series & Forecasting

| Project | What It Does |
|---------|-------------|
| [time-series-forecasting-suite](https://github.com/neeljshah/time-series-forecasting-suite) | Forecasting benchmark &mdash; ARIMA, Prophet, LSTM across retail, energy, and web traffic domains |
| [customer-churn-predictor](https://github.com/neeljshah/customer-churn-predictor) | End-to-end churn prediction &mdash; ensemble models + SHAP explainability + Streamlit dashboard |

### Data Analytics & BI

| Project | What It Does |
|---------|-------------|
| [enterpriseRevenueEngine](https://github.com/neeljshah/enterpriseRevenueEngine) | Enterprise revenue engine &mdash; end-to-end BI + AI for revenue forecasting and attribution |
| [globalSuperstore](https://github.com/neeljshah/globalSuperstore) | Global retail analytics &mdash; Power BI dashboards + SQL analysis on international superstore data |

### Original NBA Research

| Project | What It Does |
|---------|-------------|
| [archetypingClustering](https://github.com/neeljshah/archetypingClustering) | NBA player archetypes &mdash; K-Means clustering on 2023-24 season performance profiles |
| [gravityInfluence](https://github.com/neeljshah/gravityInfluence) | Offensive gravity analysis &mdash; measuring off-ball influence on spacing and shot quality |
| [creationGrade](https://github.com/neeljshah/creationGrade) | Shot creation grading &mdash; difficulty-adjusted shot generation metric |
| [momentumTrend](https://github.com/neeljshah/momentumTrend) | In-game momentum &mdash; run detection and swing-state analysis |
| [BasketBallLogic](https://github.com/neeljshah/BasketBallLogic) | Basketball analytics &mdash; AI-driven game analysis and strategic insights |

---

## Technical Stack

| Domain | Tools |
|--------|-------|
| **ML / DL** | PyTorch &middot; XGBoost &middot; LightGBM &middot; CatBoost &middot; scikit-learn &middot; Stable-Baselines3 |
| **CV** | YOLOv8 &middot; OpenCV &middot; SIFT &middot; EasyOCR &middot; OSNet &middot; decord (NVDEC) |
| **NLP** | LangChain &middot; FinBERT &middot; ChromaDB &middot; Claude API &middot; RAG |
| **Causal / Stats** | DoWhy &middot; EconML &middot; statsmodels &middot; scipy |
| **Data** | PostgreSQL &middot; DuckDB &middot; Redis &middot; pandas &middot; Polars &middot; BigQuery &middot; dbt |
| **Serving** | FastAPI &middot; Streamlit &middot; Next.js &middot; Docker &middot; WebSocket |
| **MLOps** | MLflow &middot; Prefect &middot; Evidently &middot; Grafana &middot; GitHub Actions |
| **Infra** | RunPod GPU &middot; FAISS &middot; Kafka &middot; B2 Cloud |
| **Languages** | Python &middot; SQL &middot; JavaScript &middot; bash |

---

## Research Principles

- **Walk-forward, purged, always.** K-fold on time-ordered data is a correctness bug. Train on t-1, evaluate on t, purge the overlap.
- **Baselines first.** Every model has a cheap baseline it must beat. The delta is the headline, not the number.
- **CLV over ROI.** Realized ROI on small samples is noisy. Closing-line value is approximately unbiased and converges 5x faster.
- **Calibration &ne; accuracy.** Reliability diagrams and ECE on every probabilistic model. Miscalibrated models can't be Kelly-sized safely.
- **Ship the bug list.** The STL model R&sup2;=0.09 isn't humility &mdash; it's a spec for where the model must not be trusted.

---

<div align="center">

**[neeljshah22@gmail.com](mailto:neeljshah22@gmail.com)** &middot; **[LinkedIn](https://www.linkedin.com/in/neeljshah22/)** &middot; **[Portfolio](https://neelshahportfolio.netlify.app)**

</div>
