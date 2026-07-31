<div align="center">

# Neel J. Shah

### ML Engineer &middot; Computer Vision &middot; Probabilistic Modeling &middot; Sports Quant

[![Email](https://img.shields.io/badge/neeljshah22%40gmail.com-D14836?style=flat&logo=gmail&logoColor=white)](mailto:neeljshah22@gmail.com)
[![LinkedIn](https://img.shields.io/badge/neeljshah22-0A66C2?style=flat&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/neeljshah22/)

</div>

---

I build forecasting systems, and the validation tooling that decides whether they
are any good. My main project takes broadcast video in and puts calibrated
probabilities out across four sports. The part worth looking at is the harness:
leak-guarded walk-forward validation, pre-registered claims, and an acceptance
gate with the authority to reject my own results. It usually does.

Open to ML, Computer Vision, Quantitative Research, and Sports Analytics roles.
**US citizen, no sponsorship needed, available anywhere in the US or fully remote.**

---

## CourtVision

**[court-vision](https://github.com/neeljshah/court-vision)** -- an end-to-end
multi-sport forecasting platform (NBA, MLB, soccer, tennis).

```
Broadcast Video -> YOLOv8n detection -> SIFT homography -> Kalman+Hungarian tracking
  -> OSNet re-ID -> OCR -> court-coordinate features that exist in no public dataset
  -> calibrated win-prob + prop models -> possession-level Monte Carlo
  -> walk-forward, leak-guarded validation -> receipt-backed evidence layer
```

**What makes it different is the epistemics, not the model zoo:**

- **Leak-free walk-forward validation** with assertion-level per-fold guards and
  truncation-invariance property tests -- the harness fails the build on lookahead.
- **21,000+ pre-registered hypothesis cards**: claim, expected sign, and magnitude
  written down *before* outcomes are looked at, then graded mechanically. The
  large majority of graded cards are honest REJECTs -- which is what real signal
  discovery looks like.
- **A full-season market-efficiency result I publish instead of hiding**: my
  calibrated models *match* the Shin-devigged closing line within noise on
  team-strength markets across 6 independent corpora. The one measured win is
  in-game conditioning (pregame prior fused with realized game state), labelled
  as calibration, not a betting edge.
- **A reject graveyard and retraction log**: 500+ candidate signals killed by the
  gate with reasons recorded; early headline numbers that did not survive
  adversarial re-audit are documented as retractions, not quietly deleted.
- **A receipt system**: every headline number on the public evidence surface
  carries its source artifact path, sha256, honesty label, and as-of date -- and
  a fail-closed linter blocks the bundle on edge-language or any retracted number.

Start here: [`docs/JOB_EVIDENCE_PACKET.md`](https://github.com/neeljshah/court-vision/blob/master/docs/JOB_EVIDENCE_PACKET.md)
-- the adversarially-audited account of every claim, including the do-not-claim list.

---

## Single-concept repos distilled from the platform

| Repo | The skill it isolates |
|---|---|
| [walkforward-guard](https://github.com/neeljshah/walkforward-guard) | Leak-proof time-series CV; the demo plants two real leaks and catches both |
| [calibration-gate](https://github.com/neeljshah/calibration-gate) | Brier decomposition, ECE, PAVA/Platt recalibration + a 2-corpus acceptance gate |
| [prereg-cards](https://github.com/neeljshah/prereg-cards) | Pre-registration workflow: peek-guarded registry, mechanical grading, honesty lint |
| [shin-devig](https://github.com/neeljshah/shin-devig) | Four de-vig methods incl. Shin (1992) via stable bisection |
| [kalman-hungarian-tracker](https://github.com/neeljshah/kalman-hungarian-tracker) | Multi-object tracking from primitives -- hand-rolled 6D Kalman + Hungarian assignment |
| [agentic-fleet-playbook](https://github.com/neeljshah/agentic-fleet-playbook) | Orchestrating AI agent fleets that ship *verified* software, failure modes included |

---

## How it was built

A solo human directing a multi-model agent fleet: a frontier model decides, reviews,
and adjudicates; mid-tier models execute in parallel against frozen contracts; small
models scan. Hard guardrails live outside model discretion -- pre-commit hooks,
fail-closed lint gates, append-only ledgers, binding invariant files. The patterns
(and the failure modes) are written up honestly in
[agentic-fleet-playbook](https://github.com/neeljshah/agentic-fleet-playbook).

---

## Licensing

Stating this plainly because it decides whether the work is usable commercially.
The ball detector in CourtVision fine-tunes Ultralytics YOLOv8, which is
**AGPL-3.0**: fine for research and portfolio use, not fine inside a closed-source
commercial product without a paid Ultralytics license. Shipping it commercially
would mean retraining the detector on a permissively licensed backbone, which is a
scoped swap, not a rewrite. The single-concept repos above carry no such
constraint and are MIT.

---

<div align="center">

*The market is mostly efficient. Saying so, with instruments, is the credential.*

</div>
