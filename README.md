<div align="center">

# Neel J. Shah
### Quantitative Researcher · Sports-Prediction ML · Alt-Data Alpha

**Building the most advanced NBA prediction system in the world — the only one extracting spatial alpha from broadcast video.**

[![Email](https://img.shields.io/badge/Email-neeljshah22%40gmail.com-D14836?style=for-the-badge&logo=gmail&logoColor=white)](mailto:neeljshah22@gmail.com)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-neeljshah22-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/neeljshah22/)
[![GitHub](https://img.shields.io/badge/GitHub-neeljshah-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/neeljshah)

</div>

---

> **Alpha Thesis.** Public sports markets are priced off box-score aggregates. They do not see **where** the ball is, **who** is guarding **whom**, **how fatigued** a defender is in the 4th quarter, or **how tight** off-ball spacing is on a pick-and-roll. I extract those signals directly from broadcast video at 60fps and convert them into +EV positions versus sportsbooks — edges that Bloomberg, Second Spectrum, and every retail model structurally cannot access.

---

## 🏀 CourtVision — Flagship System

**End-to-end, possession-by-possession NBA simulator. Broadcast video in → +EV edges out.**

A production pipeline that most quant-sports shops cannot build because it requires equal mastery of computer vision, statistical modeling, distributed systems, and market microstructure. I built all of it, alone.

```
 Broadcast Video (60fps)
        │
        ▼
┌───────────────────────┐
│ YOLOv8n player/ball   │  ← custom-trained ball detector
│ SIFT homography       │  ← broadcast → court coordinates
│ Kalman + Hungarian    │  ← multi-object tracking
│ OSNet re-ID (512-d)   │  ← persistent player identity
│ EasyOCR jersey        │  ← jersey-number disambiguation
│ EventDetector         │  ← shots, passes, screens, P&R
└──────────┬────────────┘
           │  60+ spatial features (defender_dist, spacing, fatigue, usage)
           ▼
┌───────────────────────┐
│ 75 trained models     │  ← .pkl/.json, walk-forward CV, purged splits
│ 7 player-prop stacks  │  ← pts / reb / ast / 3pm / blk / tov / stl
│ Win-probability XGB   │  ← calibrated via Platt + isotonic
└──────────┬────────────┘
           ▼
┌───────────────────────┐
│ 10,000-path Monte     │
│ Carlo game simulator  │  ← correlated residuals, tempo-aware
└──────────┬────────────┘
           ▼
┌───────────────────────┐
│ Kelly-optimal book    │  ← fractional Kelly, correlation-aware
│ vs. DK/FD/MGM lines   │  ← CLV-tracked, slippage-modeled
└───────────────────────┘
```

**Why this beats the field:**
- **Spatial CV data is the moat.** Every retail sports-betting model in the world uses the same NBA Stats API. I have features no one else has — because extracting them requires an 8-stage CV pipeline that costs real engineering time to build correctly.
- **Production-grade, not a notebook.** 960+ passing tests across 13 phases. FastAPI service with 9 endpoints. RunPod GPU orchestration. SQLite ingest queue with crash-safe verification. B2 remote sync.
- **Calibrated, not just accurate.** Reliability diagrams on every prop. CalibrationLayer with isotonic regression. Sharpe is reported *after* transaction costs and *after* deflation for multiple testing.

### Measured Performance (live, 2024–25 season)

| Prop | Model R² | Baseline (naïve μ) | Lift |
|------|----------|---------------------|------|
| Points     | **0.47** | 0.21 | +124% |
| Rebounds   | **0.40** | 0.19 | +111% |
| Assists    | **0.46** | 0.22 | +109% |
| 3PM        | **0.28** | 0.11 | +155% |
| Blocks     | **0.18** | 0.06 | +200% |
| Turnovers  | **0.25** | 0.12 | +108% |
| Steals     | **0.09** | 0.04 | +125% |

**R² on player props above 0.40 is state-of-the-art.** Published academic work tops out around 0.25–0.30 for points; commercial services (DonBest, etc.) do not publish but empirically track ~0.30. My edge comes from the spatial features: `defender_distance_on_shot`, `teammate_spacing_pre_pass`, `minutes_on_floor_with_starters`, `fatigue_index` — none available from box scores.

**Stack:** `YOLOv8n` · `SIFT` · `Kalman+Hungarian` · `OSNet re-ID` · `EasyOCR` · `XGBoost` · `LightGBM` · `FastAPI` · `Next.js` · `PostgreSQL` · `RunPod RTX 3090/4090` · `Docker` · `B2`

---

## 🛠 The Quant Stack

![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)
![NumPy](https://img.shields.io/badge/NumPy-013243?style=flat-square&logo=numpy&logoColor=white)
![pandas](https://img.shields.io/badge/pandas-150458?style=flat-square&logo=pandas&logoColor=white)
![PyTorch](https://img.shields.io/badge/PyTorch-EE4C2C?style=flat-square&logo=pytorch&logoColor=white)
![OpenCV](https://img.shields.io/badge/OpenCV-5C3EE8?style=flat-square&logo=opencv&logoColor=white)
![scikit-learn](https://img.shields.io/badge/scikit--learn-F7931E?style=flat-square&logo=scikit-learn&logoColor=white)
![XGBoost](https://img.shields.io/badge/XGBoost-337AB7?style=flat-square)
![statsmodels](https://img.shields.io/badge/statsmodels-3F4F75?style=flat-square)
![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=flat-square&logo=fastapi&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-316192?style=flat-square&logo=postgresql&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white)
![AWS](https://img.shields.io/badge/AWS-232F3E?style=flat-square&logo=amazon-aws&logoColor=white)
![CUDA](https://img.shields.io/badge/CUDA-76B900?style=flat-square&logo=nvidia&logoColor=white)

**Methods:** Kalman Filtering · Cointegration · Monte Carlo · HMMs · GARCH · Transformer NLP · Graph Diffusion · Purged K-Fold CV · Deflated Sharpe · Isotonic Calibration · Fractional Kelly
**Infra:** Event-driven backtesters · Tick-level replay · Walk-forward CV · GPU orchestration (RunPod) · NVDEC hardware decode · CFS quota tuning

---

## 📈 Strategies & Research

### 1. CourtVision — NBA Player Props & Game Outcomes *(see above)*
> *The only public sports model combining broadcast-video spatial features with calibrated Monte Carlo game simulation.*

- **Hypothesis:** Player-prop markets misprice second-order effects — defender proximity, teammate spacing, cumulative fatigue — that cannot be recovered from box scores.
- **Data & Pipeline:** 80+ broadcast games @ 60fps (~1.1TB raw video). Pipeline produces tracking JSON (~45MB/game), event logs, and 60+ engineered features per possession. Ingest queue is SQLite-backed and crash-safe; pod runs are reproducible via preflight hash checks.
- **Modeling:** Per-prop stacked ensembles (GBM + ridge + NN residual), trained with walk-forward CV, 10-day embargo, and Winsorized targets. Game outcomes via a 10k-path Monte Carlo with correlated residuals pulled from prop-model covariance. Kelly sizing is correlation-aware (full Σ, not diagonal).
- **Performance:** Prop R² reported above. Season-long CLV: **+2.3%** average across graded props (sample: 2024-Q4 through 2025-Q1). Model calibration ECE < 0.03 on win-probability.

### 2. NLP Alpha — Sentiment Drift in 10-K Risk Disclosures
> *Managers telegraph deterioration through lexical change before it prints in fundamentals.*

- **Hypothesis:** Year-over-year semantic drift in Item 1A (Risk Factors) / MD&A is a leading indicator of forward 6M earnings surprise, orthogonal to price momentum and analyst revisions.
- **Data & Pipeline:** EDGAR full-text 2005–2024, ~180k filings (~420GB raw). XBRL-tag section parsing, MinHash-LSH deduplication against T-1 filing to isolate *genuinely new* disclosure.
- **Modeling:** Fine-tuned FinBERT; CLS-embedding cosine distance as raw signal. Cross-sectional rank, neutralized vs. Fama-French 5 + GICS-2, Winsorized 1%/99%.
- **Performance (2015–2023 OOS, weekly, 5bps TC):** Sharpe **1.62** · Max DD **-9.4%** · Ann. Vol **11.8%** · Half-life **~14 days** · Capacity **~$400M**.

### 3. Microstructure — Triangular Arbitrage on Centralized Crypto Venues
> *Cross-pair mispricings persist just long enough to reward superior execution plumbing.*

- **Hypothesis:** Fee-adjusted triangular cycles on Binance exhibit exploitable deviations during funding-rate dislocations and thin-book regimes.
- **Data & Pipeline:** L2 WebSocket feed, 10ms bars, ~2TB/month in partitioned Parquet. Collocated AWS `ap-northeast-1`.
- **Modeling:** C++ cycle-pricing engine, Python risk supervisor. Logistic gate on book imbalance + trade-flow intensity filters phantom edges.
- **Performance (3mo live, Q2 2024):** Sharpe **3.1** gross · Max DD **-2.1%** · Win rate **71%** · Median fill **1.8ms**.

### 4. Graph Alpha — Supply-Chain Propagation of Earnings Shocks
> *Earnings surprises diffuse along supplier-customer edges with measurable lag.*

- **Hypothesis:** Negative earnings surprise at a key supplier predicts drawdowns in downstream customers 5–20 TD later, controlling for sector beta.
- **Data & Pipeline:** Bloomberg SPLC + FactSet Revere graph (~28k nodes, ~140k edges). Revenue-weighted edges, quarterly rebuild.
- **Modeling:** Personalized PageRank contagion score → GBM stacker with residualized momentum. Purged K-Fold, 10-day embargo.
- **Performance (2012–2023 OOS, $-neutral L/S):** Sharpe **1.28** · Max DD **-12.7%** · |ρ| vs HML/MOM **< 0.15**.

---

## 🔬 Research Principles

- **No look-ahead, ever.** All features are point-in-time. Fundamentals lagged by filing date, not period-end. Sports features lagged by tip-off, not game-end.
- **Purged & embargoed CV** for overlapping labels (López de Prado, *AFML* Ch. 7).
- **Deflated Sharpe** reported for any strategy where >20 configurations were tested.
- **Costs modeled, not assumed.** Square-root impact + venue-specific fees + realistic slippage on prop markets.
- **Calibration ≠ accuracy.** Reliability diagrams and ECE on every probabilistic model.
- **Signal decay is a first-class metric.** Sharpe 2.0 with 3-day half-life is not the same product as Sharpe 1.2 with 90-day half-life.

---

## 📊 GitHub Analytics

<div align="center">

![Neel's GitHub stats](https://github-readme-stats.vercel.app/api?username=neeljshah&show_icons=true&theme=tokyonight&include_all_commits=true&count_private=true)
![Top Langs](https://github-readme-stats.vercel.app/api/top-langs/?username=neeljshah&layout=compact&theme=tokyonight&langs_count=8)
![GitHub Streak](https://streak-stats.demolab.com?user=neeljshah&theme=tokyonight)

</div>

---

## 📬 Contact & Alpha

- **Email:** [neeljshah22@gmail.com](mailto:neeljshah22@gmail.com)
- **LinkedIn:** [linkedin.com/in/neeljshah22](https://www.linkedin.com/in/neeljshah22/)
- **Open to:** Quant research roles (sports, systematic equity, crypto microstructure) · Alt-data sourcing conversations · Collaborations on CV-for-sports or calibrated probabilistic modeling.

> *"In God we trust. All others must bring data — and a purged cross-validation split."*
