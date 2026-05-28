# Strategy Traceability Matrix

생성시각: 2026-05-28T17:41:29.152139+09:00
기준일: 20260521

## Summary

- status: blocked_external_dependency
- requirement_count: 6
- verified_count: 5
- partial_count: 0
- blocked_external_dependency_count: 1
- external_gap_count: 4

## Matrix

| ID | Strategy Section | Status | Evidence |
|---|---|---|---|
| official_fact_graph | 공식 사실 그래프: Company, Security, Disclosure, Index/ETF, Evidence | verified | COMPLETION_AUDIT.json, SOURCE_COVERAGE.json, neo4j/nodes.csv, vault/Home.md, index.html |
| propagation_graph | 시장·이벤트 파급 그래프: CO_MOVES, LEADS, exposure, peer, transaction | verified | COMPLETION_AUDIT.json, QUALITY_AUDIT.json, graph_data.js |
| signed_path_scorer | 2~3홉 signed path impact scoring | verified | COMPLETION_AUDIT.json, INVESTMENT_ANALYSIS_AUDIT.json, stock_graph_YYYYMMDD.json, graph_data.js |
| source_priority_and_access | OpenDART, FSC/KRX, KRX Marketplace, KIND, SEIBro/KSD, BIGKinds, provider 접근 방식 | blocked_external_dependency | SOURCE_COVERAGE.json, API_ENDPOINTS.json, EXTERNAL_API_READINESS.json, DATA_SOURCE_ACCESS_REQUIREMENTS.md |
| governance_and_lineage | source_system, source_id, confidence, evidence, license/access gap 거버넌스 | verified | COMPLETION_AUDIT.json, SOURCE_COVERAGE.json, DATA_FRESHNESS_AUDIT.json, DATA_SOURCE_ACCESS_REQUIREMENTS.md |
| quality_and_deployment | 품질 게이트, 정적 HTML, GitHub Pages 배포 | verified | QUALITY_AUDIT.json, QUALITY_AUDIT.md, UI_INTERACTION_AUDIT.json, DEPLOYMENT_AUDIT.json, index.html, graph_data.js |
