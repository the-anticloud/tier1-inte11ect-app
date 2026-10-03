# Deploy Guide — INTE11ECT_APP
## Prerequisites
- Python 3.11+, FastAPI 0.110+, HTMX 1.9+, PAX 27B weights, SQLite (stdlib)

## Environment
- 16GB RAM. GPU optional. Serves on localhost:8080.

## Install
```bash
pip install anticloud-inte11ect fastapi uvicorn[standard] httpx
```

## Start server
```bash
python -m inte11ect_app --model ./pax-27b-q4.gguf --port 8080 --aioss ./inte11ect.aioss
```

## Air-Gap
All deps local, PAX weights local. No CDN, no fonts, no analytics. Fully offline.

## AIOSS Integration
Auto-chains every interaction. Pass `--aioss ./path/to/chain.aioss` at startup.

## Verification
```bash
curl http://localhost:8080/health
aioss verify --chain ./inte11ect.aioss
```
