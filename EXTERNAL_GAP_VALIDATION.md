# External Gap Validation

생성시각: 2026-05-28T20:59:21.104278+09:00
기준일: 20260521

## Summary

- status: blocked_external_dependency
- gap_count: 4
- blocked_gap_count: 3
- ready_gap_count: 1
- required_gap_count: 1
- blocked_required_gap_count: 0
- optional_gap_count: 3
- blocked_optional_gap_count: 3
- secret_values_recorded: False

## Gaps

| ID | Source | Blocks | Status | Blocking Requirements | Close Conditions | Probe | Next Fix |
|---|---|---|---|---|---|---|---|
| bigkinds_direct_api_gap | BIGKinds | optional_enrichment | blocked_external_dependency | credential_missing | probe_ok_with_expected_fields, endpoint_probe_configured | skipped/credential_missing | BIGKinds Open API access_key를 BIGKINDS_API_KEY에 설정한 뒤 probe를 재실행한다. |
| ksd_seibro_direct_api_gap | SEIBro/KSD | full_100_direct_api | ready | - | probe_ok_with_expected_fields, endpoint_probe_configured | ok/ok | none |
| paid_provider_contract_required | Paid providers | optional_enrichment | blocked_external_dependency | contract_required | contract_review_recorded | not_run | probe_not_run |
| paid_provider_direct_api_gap | Paid providers | optional_enrichment | blocked_external_dependency | credential_missing, endpoint_config_missing | probe_ok_with_expected_fields, endpoint_probe_configured | skipped/endpoint_config_missing | 공식 endpoint URL을 확인해 해당 *_API_URL 환경변수 또는 EXTERNAL_API_CONFIG에 설정한다. |
