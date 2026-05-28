# External API Readiness

생성시각: 2026-05-28T11:36:42.360192+09:00
기준일: 20260521

## Summary

- connector_count: 5
- ready_for_live_fetch_count: 0
- not_ready_count: 5
- secret_values_recorded: False

## Run Command

```powershell
python skills/kr-stock-obsidian-graph/scripts/build_kr_stock_graph.py --date 20260521 --kind-api-url $env:KIND_API_URL --bigkinds-api-url $env:BIGKINDS_API_URL --ksd-seibro-api-url $env:SEIBRO_API_URL --provider-api-url $env:PROVIDER_API_URL --probe-external-apis --output-dir reports/stock_graph
```

## Connectors

| ID | Source | Ready | Option | Row Path | Expected Fields | Normalizes To | Credential Ready | Endpoint Ready | Missing | Probe Status | Probe Rows | Field Coverage | Missing Fields | Coverage Mode | Coverage Status |
|---|---|---:|---|---|---|---|---:|---:|---|---|---:|---|---|---|---|
| bigkinds_direct_api_gap | BIGKinds | False | --bigkinds-api-url | return_object.documents | article_id, title, published_at, entities, keywords | Event, Evidence, positive_exposure, negative_exposure | False | False | credential_missing, endpoint_config_missing | not_run | 0 | not_run | article_id, title, published_at, entities, keywords | snapshot_import | skipped |
| kind_direct_api_gap | KIND | False | --kind-api-url | response.body.items.item | corp_name, stock_code, disclosure_id, title, published_at, report_type | Disclosure, Event, Evidence, has_event | False | False | credential_missing, endpoint_config_missing | not_run | 0 | not_run | corp_name, stock_code, disclosure_id, title, published_at, report_type | snapshot_import | skipped |
| ksd_seibro_direct_api_gap | SEIBro/KSD | False | --ksd-seibro-api-url | response.body.items.item | stock_code, isin, event_type, event_date, amount, ratio | Event, Evidence, dividend_event, rights_event, lending_event, lockup_event | True | False | endpoint_config_missing | not_run | 0 | not_run | stock_code, isin, event_type, event_date, amount, ratio | snapshot_import | skipped |
| ksd_seibro_license_review_required | SEIBro/KSD | False | - | license.review | license_type, commercial_use_allowed, attribution_required, source_name, reviewed_at | DataLicense, SourceContract | False | False | license_review_required | not_run | 0 | not_run | license_type, commercial_use_allowed, attribution_required, source_name, reviewed_at | snapshot_import | skipped |
| paid_provider_direct_api_gap | Paid providers | False | --provider-api-url | data.items | stock_code, relation_type, target_code, weight, confidence, source_id | RelationFact, Evidence, provider_relation, broker_report, consensus_metric | False | False | credential_missing, endpoint_config_missing | not_run | 0 | not_run | stock_code, relation_type, target_code, weight, confidence, source_id | contract_snapshot_import | skipped |
