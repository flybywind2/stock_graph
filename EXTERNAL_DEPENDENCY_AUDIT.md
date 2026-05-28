# External Dependency Audit

생성시각: 2026-05-28T10:10:55.234949+09:00
기준일: 20260521

## Summary

- status: blocked_external_dependency
- gap_count: 5
- credential_ready_gap_count: 1
- live_fetch_ready_gap_count: 0
- full_100_blocked: True
- free_core_blocked: False

## Gaps

| ID | Source | Status | Required Action | Current Fallback | Credential Keys | Credential Ready | Endpoint Keys | Endpoint Ready | Direct Connector | Live Fetch Ready | Missing Requirements | Blocks |
|---|---|---|---|---|---|---:|---|---:|---:|---:|---|---|
| bigkinds_direct_api_gap | BIGKinds | blocked_external_dependency | BIGKinds Open API 이용 신청, 호출 제한과 응답 레이아웃 확인 | --bigkinds-snapshots | BIGKINDS_API_KEY | False | BIGKINDS_API_URL | False | True | False | credential_missing, endpoint_config_missing | full_100_direct_api |
| kind_direct_api_gap | KIND | blocked_external_dependency | KIND 화면별 공식 API 또는 엑셀 다운로드 자동화 규격 확정 | --kind-snapshots | KIND_API_KEY | False | KIND_API_URL | False | True | False | credential_missing, endpoint_config_missing | full_100_direct_api |
| ksd_seibro_direct_api_gap | SEIBro/KSD | blocked_external_dependency | SEIBro 오픈플랫폼 또는 KSD GW 서비스별 승인, 레이아웃, 상업적 이용 가능 여부 확인 | --ksd-seibro-snapshots | SEIBRO_API_KEY, KSD_API_KEY, DATA_GO_KR_SERVICE_KEY | True | SEIBRO_API_URL, KSD_API_URL | False | True | False | endpoint_config_missing | full_100_direct_api |
| paid_provider_contract_required | Paid providers | blocked_external_dependency | FnGuide/DataGuide/QuantiWise/DeepSearch/Finorma 등 유료 데이터 제공업체와 데이터 사용 계약 체결 | --provider-snapshots | - | False | - | False | True | False | contract_required | full_100_direct_api |
| paid_provider_direct_api_gap | Paid providers | blocked_external_dependency | FnGuide/DataGuide/QuantiWise/DeepSearch/Finorma 계약과 API key 또는 파일 레이아웃 확인 | --provider-snapshots | FNGUIDE_API_KEY, DATAGUIDE_API_KEY, QUANTIWISE_API_KEY, DEEPSEARCH_API_KEY, FINORMA_API_KEY | False | PROVIDER_API_URL | False | True | False | credential_missing, endpoint_config_missing | optional_enrichment |
