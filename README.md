# Neel J. Shah

**ML Engineer — computer vision, probabilistic modeling, sports quant**

[![Email](https://img.shields.io/badge/email-neeljshah22%40gmail.com-blue?style=flat&logo=gmail)](mailto:neeljshah22@gmail.com)
[![Portfolio](https://img.shields.io/badge/portfolio-neelshahportfolio.netlify.app-blue?style=flat)](https://neelshahportfolio.netlify.app)
[![LinkedIn](https://img.shields.io/badge/linkedin-neeljshah22-blue?style=flat&logo=linkedin)](https://linkedin.com/in/neeljshah22)

I build end-to-end ML systems that go from raw unstructured data to calibrated, deployable predictions. Current focus: extracting spatial features from broadcast video that don't exist in any public dataset — defender distance, off-ball spacing, fatigue signals — and routing them into live probabilistic models.


---

## What I Build

| Domain | Projects |
|--------|----------|
| **Computer Vision & Tracking** — object detection, homography, re-ID, event detection | [court-vision](https://github.com/neeljshah/court-vision) · [game-film-analyzer](https://github.com/neeljshah/game-film-analyzer) · [sports-vision-tracker](https://github.com/neeljshah/sports-vision-tracker) · [deep-learning-cv](https://github.com/neeljshah/deep-learning-cv) |
| **Probabilistic Modeling & Calibration** — reliability, ECE, Kelly sizing, CLV | [calibcraft](https://github.com/neeljshah/calibcraft) · [kellycorr](https://github.com/neeljshah/kellycorr) · [clvtrack](https://github.com/neeljshah/clvtrack) · [walkforge](https://github.com/neeljshah/walkforge) |
| **MLOps & Production** — experiment tracking, monitoring, LLM pipelines | [mlops-monitor](https://github.com/neeljshah/mlops-monitor) · [mlops-pipeline](https://github.com/neeljshah/mlops-pipeline) · [llm-bi-assistant](https://github.com/neeljshah/llm-bi-assistant) |
| **Sports Analytics** — player props, draft, win probability, injury risk | [linewatch](https://github.com/neeljshah/linewatch) · [draft-value-model](https://github.com/neeljshah/draft-value-model) · [injury-risk-predictor](https://github.com/neeljshah/injury-risk-predictor) · [nba-win-probability](https://github.com/neeljshah/nba-win-probability) · [nfl-draft-analytics](https://github.com/neeljshah/nfl-draft-analytics) |

---

## Technical Stack

| | |
|---|---|
| **ML / DL** | PyTorch · XGBoost · LightGBM · scikit-learn · YOLOv8 · OpenCV |
| **Data** | PostgreSQL · Pandas · NumPy · Polars |
| **Serving** | FastAPI · Docker · REST · WebSocket |
| **MLOps** | MLflow · Prefect · Grafana · LangChain |

---

## Flagship: court-vision

`YOLOv8n → SIFT homography → Kalman+Hungarian → OSNet re-ID → EventDetector → FastAPI → Next.js`

Possession-by-possession NBA simulator. Spatial CV features (defender distance, spacing, fatigue) extracted from broadcast video → 75 trained models → 10K Monte Carlo simulation → +EV edges vs sportsbooks.

**75 trained models · 7 prop models · R² 0.47 pts · +14 bps CLV vs Pinnacle close**

→ [neeljshah/court-vision](https://github.com/neeljshah/court-vision)
