# Operations Manual

## Phase 0 — Setup
```bash
docker compose up -d
cp .env.development .env
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```

## Phase 1 — Start API
```bash
uvicorn app.main:app --reload
```

Verify:
```bash
curl http://127.0.0.1:8000/health
```

## Phase 2 — Ingest Data
```bash
curl -X POST http://127.0.0.1:8000/data/ingest \
  -H 'Content-Type: application/json' \
  -d '{"tx_hash":"0xdemo001","payload":"nft mint volume rising on bnb","chain":"bnb"}'
```

## Phase 3 — Insights
```bash
curl http://127.0.0.1:8000/data/insights
```

## Phase 4 — Search
```bash
curl -X POST http://127.0.0.1:8000/data/search \
  -H 'Content-Type: application/json' \
  -d '{"query":"nft volume trend","top_k":3,"probes":10}'
```

## Phase 5 — Advisor
```bash
curl -X POST http://127.0.0.1:8000/advisor/recommend \
  -H 'Content-Type: application/json' \
  -d '{"profile":{"risk_tolerance":0.45,"horizon_days":120,"max_drawdown":0.2},"objective":"income","user_id":"user-1"}'
```

## Phase 6 — Execution Plan (dry‑run)
```bash
curl -X POST http://127.0.0.1:8000/execute/plan \
  -H 'Content-Type: application/json' \
  -d '{"asset":"BNB","action":"swap","size":5.0,"strategy_id":"strat-001"}'
```

## Phase 7 — Scorecard
```bash
curl http://127.0.0.1:8000/scorecard
```

## Phase 8 — Orchestrator (MCP)
```bash
curl -X POST http://127.0.0.1:8000/mcp/route \
  -H 'Content-Type: application/json' \
  -d '{"route":"advise","user_id":"user-1","intent":"portfolio","profile":{"risk_tolerance":0.45,"horizon_days":120,"max_drawdown":0.2},"payload":{"objective":"income"}}'
```
