# Graph Quality Audit

생성시각: 2026-05-28T13:43:07.340088+09:00
기준일: 20260521

## Summary

- status: pass
- node_count: 33033
- edge_count: 180294
- duplicate_node_id_count: 0
- broken_edge_count: 0
- relation_layer_count: 6
- relation_layers: event, fact, market, peer, structure, transaction
- render_payload_bytes: 39783201

## Checks

| ID | Status | Evidence |
|---|---|---|
| node_id_uniqueness | pass | unique graph node ids |
| edge_endpoint_integrity | pass | all edge endpoints resolve to node ids |
| required_relation_layers | pass | event, fact, market, peer, structure, transaction |
| render_payload_budget | pass | graph_data.js payload budget |
| metadata_presence | pass | source_coverage, api_endpoint_inventory |
