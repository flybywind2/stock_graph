# External API Readiness

생성시각: 2026-05-28T10:16:21.614733+09:00
기준일: 20260521

## Summary

- connector_count: 4
- ready_for_live_fetch_count: 0
- not_ready_count: 4
- secret_values_recorded: False

## Run Command

```powershell
python skills/kr-stock-obsidian-graph/scripts/build_kr_stock_graph.py --date 20260521 --kind-api-url $env:KIND_API_URL --bigkinds-api-url $env:BIGKINDS_API_URL --ksd-seibro-api-url $env:SEIBRO_API_URL --provider-api-url $env:PROVIDER_API_URL --output-dir reports/stock_graph
```

## Connectors

| ID | Source | Ready | Option | Credential Ready | Endpoint Ready | Missing | Coverage Mode | Coverage Status |
|---|---|---:|---|---:|---:|---|---|---|
| bigkinds_direct_api_gap | BIGKinds | False | --bigkinds-api-url | False | False | credential_missing, endpoint_config_missing | snapshot_import | skipped |
| kind_direct_api_gap | KIND | False | --kind-api-url | False | False | credential_missing, endpoint_config_missing | snapshot_import | skipped |
| ksd_seibro_direct_api_gap | SEIBro/KSD | False | --ksd-seibro-api-url | True | False | endpoint_config_missing | snapshot_import | skipped |
| paid_provider_direct_api_gap | Paid providers | False | --provider-api-url | False | False | credential_missing, endpoint_config_missing | contract_snapshot_import | skipped |
