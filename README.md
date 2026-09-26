# 11 — ESPORTS AGENT v0.1 TEST

Status: **RESEARCH / PAPER ONLY**

## Goal
Prototype the isolated eSports specialist pipeline:

Polymarket Discovery → Resolution Snapshot → CLOB Price/Book → Gemini Grounded Research → Fair Probability → Edge → Risk Gate → Local Test Log

This is not a production strategy and does not place trades.

## Data boundaries
- **Polymarket Gamma API**: event/market discovery, metadata, resolution wording, liquidity and indexed prices.
- **Polymarket CLOB public read endpoint**: orderbook and executable best ask/bid where available.
- **Gemini API + Google Search grounding**: current eSports context such as roster/stand-ins, tournament/format, form, maps/modes, patch/context and postponement/cancellation signals.
- Gemini is instructed **not** to overwrite Polymarket market/rule/price data with web results.

## API key safety
The HTML has a manual Gemini API-key field.
- The key is held only in the page's JavaScript memory.
- It is NOT hard-coded.
- It is NOT saved in localStorage/sessionStorage.
- Do NOT commit a key to GitHub.
- For a public/production deployment, move Gemini calls behind a server-side proxy and use an environment secret.

## How to test
1. Open `index.html`.
2. Paste a Gemini test API key.
3. Press **Test Gemini**.
4. Press **Scan Active Markets**.
5. Select an eSports candidate.
6. Press **Load CLOB Orderbook**.
7. Optional: add known roster/source notes.
8. Press **Run Gemini Analysis**.
9. Inspect CONFIRMED vs UNVERIFIED evidence, fair probability, executable market probability, raw edge, confidence, data quality and risk.
10. Save the snapshot to the local test log and export JSON.

## v0.1 limitations
- Keyword-based eSports discovery; no canonical eSports tag registry yet.
- One outcome (index 0) is modeled per selected market.
- No independent statistical team model yet; Gemini produces an experimental estimate.
- No calibration/backtest database yet.
- No authenticated trading and no order placement.
- No persistent backend.
- Browser CORS behavior depends on the upstream APIs and hosting environment.

## Acceptance gates for v0.2
- Robust game/tournament/match identifier.
- Canonical source registry per game.
- Structured roster and map/mode data.
- Historical dataset with timestamps.
- Independent probability baseline (Elo/Glicko or game-specific model).
- Gemini used as research/context layer, not sole probability model.
- Snapshot/repricing logger.
- Resolution parser and explicit cancellation/walkover handling.
- Backtest with sample size, ROI, Brier/calibration, drawdown, edge, latency sensitivity, resolution errors and data quality.

## Architecture rule
Predictive logic stays inside ESPORTS AGENT. Shared project components remain Resolution, Probability Interface, Edge, Risk, Logger, Backtester and Orchestrator.
