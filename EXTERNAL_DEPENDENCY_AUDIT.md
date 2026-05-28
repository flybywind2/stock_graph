# External Dependency Audit

생성시각: 2026-05-28T09:28:13.541897+09:00
기준일: 20260521

## Summary

- status: blocked_external_dependency
- gap_count: 5
- full_100_blocked: True
- free_core_blocked: False

## Gaps

| ID | Source | Status | Required Action | Current Fallback | Blocks |
|---|---|---|---|---|---|
| bigkinds_direct_api_gap | BIGKinds | blocked_external_dependency | BIGKinds Open API 이용 신청, 호출 제한과 응답 레이아웃 확인 | --bigkinds-snapshots | full_100_direct_api |
| kind_direct_api_gap | KIND | blocked_external_dependency | KIND 화면별 공식 API 또는 엑셀 다운로드 자동화 규격 확정 | --kind-snapshots | full_100_direct_api |
| ksd_seibro_direct_api_gap | SEIBro/KSD | blocked_external_dependency | SEIBro 오픈플랫폼 또는 KSD GW 서비스별 승인, 레이아웃, 상업적 이용 가능 여부 확인 | --ksd-seibro-snapshots | full_100_direct_api |
| paid_provider_contract_required | Paid providers | blocked_external_dependency | 외부 인증, 계약, 또는 레이아웃 확인 필요 | --provider-snapshots | full_100_direct_api |
| paid_provider_direct_api_gap | Paid providers | blocked_external_dependency | FnGuide/DataGuide/QuantiWise/DeepSearch/Finorma 계약과 API key 또는 파일 레이아웃 확인 | --provider-snapshots | optional_enrichment |
