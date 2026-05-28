# Completion Audit

생성시각: 2026-05-28T15:33:41.694694+09:00
기준일: 20260521

## Summary

- requirement_count: 18
- verified_count: 16
- partial_count: 0
- blocked_external_dependency_count: 1
- remaining_statuses: blocked_external_dependency, optional_external_dependency
- free_core_status: verified
- free_core_verified_count: 14 / 14

## Requirements

| ID | Scope | Status | Evidence | Gaps |
|---|---|---|---|---|
| fact_graph | free_core | verified | stock_graph_YYYYMMDD.json, listed_on, classified_as, identified_by, public_data_mapped_to | - |
| propagation_graph | free_core | verified | business_family_peer, business_peer, co_moves, group_peer, has_event, industry_peer, leads, negative_exposure, positive_exposure, related_stock, theme_peer | - |
| signed_path_scoring | free_core | verified | meta.impact_summary, meta.impact_summary_policy, HTML detail panel path scoring | - |
| source_coverage | free_core | verified | SOURCE_COVERAGE.json, SOURCE_COVERAGE.md | bigkinds_direct_api_gap, fsc_stock_dividend_auth_or_license_review_required, fsc_stock_issue_endpoint_review_required, kind_direct_api_gap, ksd_seibro_direct_api_gap, ksd_seibro_license_review_required, paid_provider_contract_required, paid_provider_direct_api_gap |
| approved_free_api_backlog | free_approved_backlog | verified | SOURCE_COVERAGE.json, API_ENDPOINTS.json | - |
| neo4j_export | free_core | verified | neo4j/nodes.csv, neo4j/relationships.csv, neo4j/import.cypher | - |
| obsidian_vault | free_core | verified | vault/Home.md, vault/Stocks, vault/Industries, vault/Markets | - |
| html_explorer | free_core | verified | index.html, graph_data.js, legend filtering, edge render limit, 2D/3D toggle | - |
| governance_metadata | free_core | verified | edge.metadata, SOURCE_COVERAGE.json, DATA_SOURCE_ACCESS_REQUIREMENTS.md | - |
| graph_quality_gate | free_core | verified | QUALITY_AUDIT.json, QUALITY_AUDIT.md, quality_status=pass | - |
| strategy_traceability | free_core | verified | TRACEABILITY_MATRIX.json, TRACEABILITY_MATRIX.md, traceability_status=blocked_external_dependency | - |
| pages_deployment_readiness | free_core | verified | DEPLOYMENT_AUDIT.json, DEPLOYMENT_AUDIT.md, deployment_status=ready | - |
| ui_interaction_gate | free_core | verified | UI_INTERACTION_AUDIT.json, UI_INTERACTION_AUDIT.md, ui_status=pass | - |
| data_freshness_gate | free_core | verified | DATA_FRESHNESS_AUDIT.json, DATA_FRESHNESS_AUDIT.md, freshness_status=pass | - |
| investment_analysis_gate | investment_analysis | verified | INVESTMENT_ANALYSIS_AUDIT.json, INVESTMENT_ANALYSIS_AUDIT.md, investment_status=pass | - |
| direct_api_completion | external_direct_api | blocked_external_dependency | SOURCE_COVERAGE.json, EXTERNAL_DEPENDENCY_AUDIT.json, EXTERNAL_API_READINESS.json, EXTERNAL_API_READINESS.md, EXTERNAL_API.env.example, EXTERNAL_API_LIVE_RUNBOOK.md, DATA_SOURCE_ACCESS_REQUIREMENTS.md | bigkinds_direct_api_gap, fsc_stock_dividend_auth_or_license_review_required, fsc_stock_issue_endpoint_review_required, kind_direct_api_gap, ksd_seibro_direct_api_gap, ksd_seibro_license_review_required, paid_provider_contract_required, paid_provider_direct_api_gap |
| optional_paid_provider_completion | optional_enrichment | optional_external_dependency | --provider-snapshots, has_consensus_metric, broker_report, provider_relation | contract_required |
| free_core_completion | free_core | verified | KRX Open API, OpenDART, data.go.kr FSC/FTC, KIND snapshots, KRX Data Marketplace snapshots, SEIBro/KSD snapshots, BIGKinds snapshots | - |
