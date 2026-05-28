# External Dependency Audit

생성시각: 2026-05-28T17:12:59.681641+09:00
기준일: 20260521

## Summary

- status: blocked_external_dependency
- gap_count: 4
- credential_ready_gap_count: 0
- live_fetch_ready_gap_count: 0
- full_100_blocked: True
- free_core_blocked: False

## Gaps

| ID | Source | Status | Required Action | Current Fallback | Row Path | Expected Fields | Normalizes To | Credential Keys | Credential Ready | Endpoint Keys | Endpoint Ready | Direct Connector | Live Fetch Ready | Missing Requirements | Blocks |
|---|---|---|---|---|---|---|---|---|---:|---|---:|---:|---:|---|---|
| bigkinds_direct_api_gap | BIGKinds | blocked_external_dependency | BIGKinds OpenAPI access_key 발급 후 tools.kinds.or.kr POST JSON endpoint 응답 레이아웃 확인 | --bigkinds-snapshots | return_object.documents | article_id, title, published_at, entities, keywords | Event, Evidence, positive_exposure, negative_exposure | BIGKINDS_API_KEY | False | BIGKINDS_API_URL | False | True | False | credential_missing, endpoint_config_missing | full_100_direct_api |
| ksd_seibro_direct_api_gap | SEIBro/KSD | blocked_external_dependency | 한국예탁결제원_주식정보서비스_GW 활용신청 승인 후 StockSvc operation URL과 응답 레이아웃 확인 | --ksd-seibro-snapshots | response.body.items.item | stock_code, isin, event_type, event_date, amount, ratio | Event, Evidence, dividend_event, rights_event, lending_event, lockup_event | SEIBRO_API_KEY, KSD_API_KEY, DATA_GO_KR_SERVICE_KEY | False | SEIBRO_API_URL, KSD_API_URL | False | True | False | credential_missing, endpoint_config_missing | full_100_direct_api |
| paid_provider_contract_required | Paid providers | blocked_external_dependency | FnGuide/DataGuide/QuantiWise/DeepSearch/Finorma 등 유료 데이터 제공업체와 데이터 사용 계약 체결 | --provider-snapshots | data.items | contract_id, license_scope, provider_name, valid_from, valid_to | DataLicense, SourceContract | - | False | - | False | True | False | contract_required | optional_enrichment |
| paid_provider_direct_api_gap | Paid providers | blocked_external_dependency | FnGuide/DataGuide/QuantiWise/DeepSearch/Finorma 계약과 API key 또는 파일 레이아웃 확인 | --provider-snapshots | data.items | stock_code, relation_type, target_code, weight, confidence, source_id | RelationFact, Evidence, provider_relation, broker_report, consensus_metric | FNGUIDE_API_KEY, DATAGUIDE_API_KEY, QUANTIWISE_API_KEY, DEEPSEARCH_API_KEY, FINORMA_API_KEY | False | PROVIDER_API_URL | False | True | False | credential_missing, endpoint_config_missing | optional_enrichment |
