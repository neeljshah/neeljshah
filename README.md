### Neel Shah

Quantitative researcher. I extract spatial features from broadcast video — defender
distance, floor spacing, fatigue — that public NBA APIs don't ship, and price prop
markets against them.

**Current work**

- **[nba-ai-system](https://github.com/neeljshah/nba-ai-system)** — Possession-level NBA simulator. 75 models, 7 live prop markets (pts R²=0.47, reb=0.40, ast=0.46), fractional-Kelly portfolio with CLV tracking. 80+ games ingested from broadcast video at ~$0.40/game on commodity GPUs.
- **[courtvision-cv](https://github.com/neeljshah/courtvision-cv)** — Broadcast → homography → tracking pipeline. YOLOv8 + SIFT + Kalman/Hungarian + OSNet re-ID. 20 fps/worker on RTX 3090, linear scaling to 80 fps aggregate at parallel-4.
- **[kellycorr](https://github.com/neeljshah/kellycorr)** — Fractional-Kelly sizer with shrinkage-estimated correlation matrix. Handles correlated legs (same-game parlays) without blowing up position sizing.

**Research notes**

- *Vig-adjusted no-vig: measuring the efficiency gap between NBA props and sides* — Shin de-juicing across ~50K prices; props show 4× the max-min dispersion of sides.
- *Does broadcast video add R²? A SHAP study of spatial features in NBA prop models* — points model gains +0.08 R² over API-only baseline; 31% of SHAP mass on spatial features.
- *CLV vs Pinnacle on 312 settled picks* — +14 bps/bet, t=2.3. Decomposed by market, time-to-close, and bet-size-vs-Kelly.
- *Fractional Kelly under correlated bets: the same-game-parlay trap* — naive Kelly overbets by ~2.3× when correlation ρ>0.4; shrinkage estimator cuts this.
- *Debugging an 80-game RunPod run: CFS quota, OMP oversubscription, and a 3× slowdown from one missing env var* — ops writeup.

**Stack (by concern, not by logo wall)**

- *Data / ingest:* yt-dlp, B2, SQLite work queue, idempotent workers, content-hash verification
- *CV:* PyTorch, YOLOv8n, OpenCV SIFT, Kalman/Hungarian, OSNet, EasyOCR, decord (NVDEC)
- *Modeling:* XGBoost, LightGBM, CatBoost, sklearn, Platt/isotonic/beta calibration, SHAP
- *Backtesting:* walk-forward, purged K-fold, bootstrapped CIs
- *Execution / risk:* fractional Kelly, correlation shrinkage, Shin de-vig, CLV attribution
- *Infra:* FastAPI, Next.js, Postgres, conda, RunPod/GCE, GitHub Actions
