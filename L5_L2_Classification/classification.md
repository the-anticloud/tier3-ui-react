# L5 Narrow / L2 General Classification — ui-react
**Platform:** Anticloud | **PAX:** 27B | **IP:** USPTO pending 2026, Anticloud FZ LLE
**Domain:** Sovereign React application shell: SPA for Anticloud operator interface

## L5 Narrow
ui-react specializes in sovereign react application shell: spa for anticloud operator interface within the Anticloud sovereign deployment boundary. All operations stay local — no cloud services, no external APIs, no data exfiltration. The narrow scope ensures deterministic, auditable behavior that PAX 27B can reason about precisely.

## L2 General
L2 General means ui-react is available to all 9 Anticloud tiers without per-tier configuration. The same API serves hospital, defense, robotics, and research deployments.

## PAX Integration
PAX 27B powers the in-app assistant panel: operators ask questions about the system in natural language and PAX responds with grounded, AIOSS-verified answers.

## AIOSS Audit Relevance
Every SPA navigation event (route hash + component render hash + session ID) is AIOSS-chained: H_n = SHA3-256(H_{n-1} || entry_hash_n || timestamp_n).
Tamper-evident, offline-verifiable, zero cloud dependency.

## Regulatory / Compliance
GDPR Art. 25 (SPA: no external CDN, no analytics SDK, no font API calls)
