# CLAUDE.md — supplychain-predictive-maintenance

## Project Context
- **Industry:** Supply Chain
- **Role focus:** Data Engineer
- **Portfolio goal:** predictive maintenance from real sensor telemetry — a bigger 2026 supply-chain hiring signal than another demand-forecast notebook.

## Data
- **Dataset:** NASA C-MAPSS Turbofan Engine Degradation dataset
- **Source:** NASA Prognostics Data Repository (also mirrored on Kaggle as "NASA Turbofan Jet Engine Data Set")
- **Access constraints:** open, no credentialing needed

## Required Stack
Python, a simulated streaming sensor ingestion layer, feature engineering on degradation trends, survival-analysis or gradient-boosted remaining-useful-life (RUL) model, Flask API, Docker, Azure Container Apps.

## Standard Repo Structure
```
src/
├── app.py                  # Flask RUL prediction endpoint
├── pipeline/
│   ├── ingestion.py           # simulated streaming sensor feed
│   ├── features.py             # degradation-trend feature engineering
│   └── train.py                  # RUL model training
notebooks/                   # EDA on C-MAPSS sample
data/                          # C-MAPSS (open, fine to include or document download)
tests/
docker/
infra/
.github/workflows/ci.yml
```

## Subagent Ownership
1. **Architect subagent** — confirm structure, plan ingestion → features → train → API flow
2. **Pipeline subagent** — owns `src/pipeline/`
3. **API subagent** — owns `src/app.py`
4. **Infra subagent** — owns `docker/` and `infra/`
5. **Docs/test subagent** — owns `tests/`, README must include a "equipment at risk" monitoring view, not just a single RUL number

## Hard Constraints
- Report RUL prediction error (RMSE) alongside a practical framing: what maintenance-scheduling decision would this actually inform?
- Include the monitoring/alerting view in the README — this is what turns a regression model into an operational tool

## Definition of Done (v1)
- [ ] Simulated streaming sensor ingestion
- [ ] Degradation-trend feature engineering pipeline
- [ ] RUL model trained with reported RMSE
- [ ] Flask API + "equipment at risk" monitoring view
- [ ] Dockerized, deployed to Azure
- [ ] README complete, tagged `v1.0`
