# Full 100 Completion Gate

생성시각: 2026-05-28T16:28:13.603815+09:00
기준일: 20260521

## Summary

- status: blocked_external_dependency
- can_claim_full_100_complete: False
- can_claim_free_scope_complete: False
- failed_criteria_count: 5
- failed_required_criteria_count: 3
- blocker_count: 8
- required_blocker_count: 6
- optional_blocker_count: 2

## Criteria

| Criterion | Passed | Evidence | Actual |
|---|---:|---|---|
| free_core_verified | True | COMPLETION_AUDIT.json | verified |
| traceability_verified | False | TRACEABILITY_MATRIX.json | blocked_external_dependency |
| external_gap_validation_ready | False | EXTERNAL_GAP_VALIDATION.json | blocked_external_dependency |
| external_required_gap_validation_ready | False | EXTERNAL_GAP_VALIDATION.json | blocked_required_gap_count=6 |
| no_remaining_full_100_actions | False | FULL_100_ACTIONS.json | external_actions_required |
| no_remaining_required_full_100_actions | False | FULL_100_ACTIONS.json | remaining_required_action_count=6 |

## Blockers

| ID | Source | Blocks | Status | Next Fix |
|---|---|---|---|---|
| bigkinds_direct_api_gap | BIGKinds | full_100_direct_api | blocked_external_dependency | 공식 endpoint URL을 확인해 해당 *_API_URL 환경변수 또는 EXTERNAL_API_CONFIG에 설정한다. |
| fsc_stock_dividend_auth_or_license_review_required | data.go.kr FSC | full_100_direct_api | blocked_external_dependency | probe는 응답했지만 기대 필드가 없어 기준일/조회 파라미터 또는 row_path를 조정한 뒤 재실행한다. |
| fsc_stock_issue_endpoint_review_required | data.go.kr FSC | full_100_direct_api | blocked_external_dependency | none |
| kind_direct_api_gap | KIND | full_100_direct_api | blocked_external_dependency | 공식 endpoint URL을 확인해 해당 *_API_URL 환경변수 또는 EXTERNAL_API_CONFIG에 설정한다. |
| ksd_seibro_direct_api_gap | SEIBro/KSD | full_100_direct_api | blocked_external_dependency | 공식 endpoint URL을 확인해 해당 *_API_URL 환경변수 또는 EXTERNAL_API_CONFIG에 설정한다. |
| ksd_seibro_license_review_required | SEIBro/KSD | full_100_direct_api | blocked_external_dependency | 공식 endpoint URL을 확인해 해당 *_API_URL 환경변수 또는 EXTERNAL_API_CONFIG에 설정한다. |
| paid_provider_contract_required | Paid providers | optional_enrichment | blocked_external_dependency | probe_not_run |
| paid_provider_direct_api_gap | Paid providers | optional_enrichment | blocked_external_dependency | 공식 endpoint URL을 확인해 해당 *_API_URL 환경변수 또는 EXTERNAL_API_CONFIG에 설정한다. |
