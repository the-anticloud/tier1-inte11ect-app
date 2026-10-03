# Developer Cookbook — INTE11ECT_APP
**Stack:** Python 3.11, FastAPI, HTMX, PAX 27B, SQLite

## Query via API
```python
import httpx
resp = httpx.post("http://localhost:8080/api/query",
    json={"query": "Analyze this ECG for arrhythmia", "session_id": "user_001"})
print(resp.json()["response"], resp.json()["chain_hash"])
```

## Configure domain router
```python
from inte11ect_app import AppShell, DomainRouter
router = DomainRouter()
router.add_domain("clinical", keywords=["patient","drug","symptom","diagnosis","ehr"])
router.add_domain("robotics", keywords=["robot","nav","ros","lidar","joint"])
shell = AppShell(router=router, pax_model="./pax-27b-q4.gguf")
shell.run()
```

## Embed as widget
```python
from inte11ect_app import IntelligenceWidget
widget = IntelligenceWidget(pax_model="./pax-27b-q4.gguf")
response = widget.answer("What is the AIOSS chain format?")
```

## Performance
HTMX streaming: use StreamingResponse. PAX pool: `AppShell(pax_pool_size=2)`.
SQLite WAL mode for concurrent reads during streaming.

## Integration
Uses KAMELOT_SEARCH for RAG, AIOSS_FORMAT for audit, MIIRAI_CHAT for memory,
KANTOR_K5 for factual lookups.
