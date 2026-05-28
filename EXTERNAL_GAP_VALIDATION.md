# External Gap Validation

생성시각: 2026-05-28T15:46:28.736032+09:00
기준일: 20260521

## Summary

- status: blocked_external_dependency
- gap_count: 8
- blocked_gap_count: 8
- ready_gap_count: 0
- required_gap_count: 6
- blocked_required_gap_count: 6
- optional_gap_count: 2
- blocked_optional_gap_count: 2
- secret_values_recorded: False

## Gaps

| ID | Source | Blocks | Status | Blocking Requirements | Close Conditions | Probe | Next Fix |
|---|---|---|---|---|---|---|---|
| bigkinds_direct_api_gap | BIGKinds | full_100_direct_api | blocked_external_dependency | credential_missing, endpoint_config_missing | probe_ok_with_expected_fields, endpoint_probe_configured | skipped/endpoint_config_missing | 공식 endpoint URL을 확인해 해당 *_API_URL 환경변수 또는 EXTERNAL_API_CONFIG에 설정한다. |
| fsc_stock_dividend_auth_or_license_review_required | data.go.kr FSC | full_100_direct_api | blocked_external_dependency | - | probe_ok_with_expected_fields, endpoint_probe_configured | degraded/auth_or_approval_failed | data.go.kr 마이페이지에서 해당 서비스 활용신청 승인 상태와 일반 인증키 Decoding 값을 확인한다. |
| fsc_stock_issue_endpoint_review_required | data.go.kr FSC | full_100_direct_api | blocked_external_dependency | license_review_required | license_review_recorded, probe_ok_with_expected_fields, endpoint_probe_configured | degraded/endpoint_or_operation_not_found | data.go.kr Swagger에서 최신 service/operation URL을 확인해 endpoint URL을 갱신한다. |
| kind_direct_api_gap | KIND | full_100_direct_api | blocked_external_dependency | credential_missing, endpoint_config_missing | probe_ok_with_expected_fields, endpoint_probe_configured | skipped/endpoint_config_missing | 공식 endpoint URL을 확인해 해당 *_API_URL 환경변수 또는 EXTERNAL_API_CONFIG에 설정한다. |
| ksd_seibro_direct_api_gap | SEIBro/KSD | full_100_direct_api | blocked_external_dependency | endpoint_config_missing | probe_ok_with_expected_fields, endpoint_probe_configured | skipped/endpoint_config_missing | 공식 endpoint URL을 확인해 해당 *_API_URL 환경변수 또는 EXTERNAL_API_CONFIG에 설정한다. |
| ksd_seibro_license_review_required | SEIBro/KSD | full_100_direct_api | blocked_external_dependency | license_review_required | license_review_recorded | skipped/endpoint_config_missing | 공식 endpoint URL을 확인해 해당 *_API_URL 환경변수 또는 EXTERNAL_API_CONFIG에 설정한다. |
| paid_provider_contract_required | Paid providers | optional_enrichment | blocked_external_dependency | contract_required | contract_review_recorded | not_run | probe_not_run |
| paid_provider_direct_api_gap | Paid providers | optional_enrichment | blocked_external_dependency | credential_missing, endpoint_config_missing | probe_ok_with_expected_fields, endpoint_probe_configured | skipped/endpoint_config_missing | 공식 endpoint URL을 확인해 해당 *_API_URL 환경변수 또는 EXTERNAL_API_CONFIG에 설정한다. |
