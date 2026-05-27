# Completion Audit

생성시각: 2026-05-28T08:42:26.236896+09:00
기준일: 20260521

## Summary

- requirement_count: 9
- verified_count: 8
- partial_count: 0
- blocked_external_dependency_count: 1
- remaining_statuses: blocked_external_dependency

## Requirements

| ID | Status | Evidence | Gaps |
|---|---|---|---|
| fact_graph | verified | stock_graph_YYYYMMDD.json, listed_on, classified_as, identified_by, public_data_mapped_to | - |
| propagation_graph | verified | business_family_peer, business_peer, co_moves, group_peer, has_event, industry_peer, leads, negative_exposure, positive_exposure, related_stock, theme_peer | - |
| signed_path_scoring | verified | meta.impact_summary, meta.impact_summary_policy, HTML detail panel path scoring | - |
| source_coverage | verified | SOURCE_COVERAGE.json, SOURCE_COVERAGE.md | direct_api_gap |
| neo4j_export | verified | neo4j/nodes.csv, neo4j/relationships.csv, neo4j/import.cypher | - |
| obsidian_vault | verified | vault/Home.md, vault/Stocks, vault/Industries, vault/Markets | - |
| html_explorer | verified | index.html, graph_data.js, legend filtering, edge render limit, 2D/3D toggle | - |
| governance_metadata | verified | edge.metadata, SOURCE_COVERAGE.json, DATA_SOURCE_ACCESS_REQUIREMENTS.md | - |
| direct_api_completion | blocked_external_dependency | SOURCE_COVERAGE.json, DATA_SOURCE_ACCESS_REQUIREMENTS.md | direct_api_gap |
