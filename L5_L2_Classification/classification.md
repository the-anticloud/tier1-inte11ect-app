# L5 Narrow / L2 General Classification — INTE11ECT_APP
**Platform:** Anticloud | **PAX:** 27B | **IP:** USPTO pending 2026, Anticloud FZ LLE

## L5 Narrow
INTE11ECT_APP is the sovereign user-facing application shell: query routing, domain classification,
PAX response streaming, AIOSS audit. It does not attempt cloud sync or multi-tenant SaaS patterns.
Single deployment, single user group, full local sovereignty.

## L2 General
Same application shell for any Anticloud deployment — hospital, defense, robotics lab, research.
Adapts to deployed tier configuration (clinical vs robotics vs security) without code changes.

## PAX Integration
User queries → domain classification → PAX 27B specialty module → streamed response + AIOSS entry.

## AIOSS Audit Relevance
Every user interaction (query + response + routing metadata) is hash-chained. Compliance officers
can audit exactly what the AI said to whom and when, all on-device, no cloud logs.

## Regulatory
GDPR Art. 25 (privacy by design), CCPA, ISO 27701 (privacy management)
