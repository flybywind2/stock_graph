# External Dependency Audit

생성시각: 2026-05-28T16:28:13.029120+09:00
기준일: 20260521

## Summary

- status: blocked_external_dependency
- gap_count: 8
- credential_ready_gap_count: 3
- live_fetch_ready_gap_count: 0
- full_100_blocked: True
- free_core_blocked: False

## Gaps

| ID | Source | Status | Required Action | Current Fallback | Row Path | Expected Fields | Normalizes To | Credential Keys | Credential Ready | Endpoint Keys | Endpoint Ready | Direct Connector | Live Fetch Ready | Missing Requirements | Blocks |
|---|---|---|---|---|---|---|---|---|---:|---|---:|---:|---:|---|---|
| bigkinds_direct_api_gap | BIGKinds | blocked_external_dependency | BIGKinds Open API 이용 신청, 호출 제한과 응답 레이아웃 확인 | --bigkinds-snapshots | return_object.documents | article_id, title, published_at, entities, keywords | Event, Evidence, positive_exposure, negative_exposure | BIGKINDS_API_KEY | False | BIGKINDS_API_URL | False | True | False | credential_missing, endpoint_config_missing | full_100_direct_api |
| fsc_stock_dividend_auth_or_license_review_required | data.go.kr FSC | blocked_external_dependency | 금융위원회_주식배당정보 활용신청 승인, 일반 인증키 Decoding 값, Swagger operation URL 확인 | FnGuide 공개 배당률, DART 배당 공시, SEIBro/KSD snapshot import | response.body.items.item | crno, stckIssuCmpyNm, diviBseDt, cashDvdnPayDt, stckGenrDvdnAmt | Event, Evidence, dividend_event | DATA_GO_KR_SERVICE_KEY | True | FSC_STOCK_DIVIDEND_URL | True | True | False | license_review_required | full_100_direct_api |
| fsc_stock_issue_endpoint_review_required | data.go.kr FSC | blocked_external_dependency | 금융위원회_주식발행정보 Swagger의 최신 operation URL 확인 후 FSC_STOCK_ISSUE_URL에 반영 | DART 발행/자본변동 공시와 KRX 상장주식수 | response.body.items.item | crno, stckIssuCmpyNm, onskTisuCnt, pfstTisuCnt | Event, Evidence, stock_issue, rights_event | DATA_GO_KR_SERVICE_KEY | True | FSC_STOCK_ISSUE_URL | True | True | False | license_review_required | full_100_direct_api |
| kind_direct_api_gap | KIND | blocked_external_dependency | KIND 화면별 공식 API 또는 엑셀 다운로드 자동화 규격 확정 | --kind-snapshots | response.body.items.item | corp_name, stock_code, disclosure_id, title, published_at, report_type | Disclosure, Event, Evidence, has_event | KIND_API_KEY | False | KIND_API_URL | False | True | False | credential_missing, endpoint_config_missing | full_100_direct_api |
| ksd_seibro_direct_api_gap | SEIBro/KSD | blocked_external_dependency | SEIBro 오픈플랫폼 또는 KSD GW 서비스별 승인, 레이아웃, 상업적 이용 가능 여부 확인 | --ksd-seibro-snapshots | response.body.items.item | stock_code, isin, event_type, event_date, amount, ratio | Event, Evidence, dividend_event, rights_event, lending_event, lockup_event | SEIBRO_API_KEY, KSD_API_KEY, DATA_GO_KR_SERVICE_KEY | True | SEIBRO_API_URL, KSD_API_URL | False | True | False | endpoint_config_missing | full_100_direct_api |
| ksd_seibro_license_review_required | SEIBro/KSD | blocked_external_dependency | SEIBro/KSD 원천별 이용허락, 출처표시, 비영리/상업적 이용 제한 확인 | --ksd-seibro-snapshots | license.review | license_type, commercial_use_allowed, attribution_required, source_name, reviewed_at | DataLicense, SourceContract | - | False | - | False | True | False | license_review_required | full_100_direct_api |
| paid_provider_contract_required | Paid providers | blocked_external_dependency | FnGuide/DataGuide/QuantiWise/DeepSearch/Finorma 등 유료 데이터 제공업체와 데이터 사용 계약 체결 | --provider-snapshots | data.items | contract_id, license_scope, provider_name, valid_from, valid_to | DataLicense, SourceContract | - | False | - | False | True | False | contract_required | optional_enrichment |
| paid_provider_direct_api_gap | Paid providers | blocked_external_dependency | FnGuide/DataGuide/QuantiWise/DeepSearch/Finorma 계약과 API key 또는 파일 레이아웃 확인 | --provider-snapshots | data.items | stock_code, relation_type, target_code, weight, confidence, source_id | RelationFact, Evidence, provider_relation, broker_report, consensus_metric | FNGUIDE_API_KEY, DATAGUIDE_API_KEY, QUANTIWISE_API_KEY, DEEPSEARCH_API_KEY, FINORMA_API_KEY | False | PROVIDER_API_URL | False | True | False | credential_missing, endpoint_config_missing | optional_enrichment |
