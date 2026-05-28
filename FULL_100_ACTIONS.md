# Full 100 Actions

생성시각: 2026-05-28T14:52:30.879561+09:00
기준일: 20260521

## Summary

- status: external_actions_required
- remaining_action_count: 8
- remaining_required_action_count: 6
- remaining_optional_action_count: 2
- free_scope_status: external_actions_required
- free_core_status: verified
- external_dependency_status: blocked_external_dependency
- secret_values_recorded: False

## Verification Command

```powershell
python skills/kr-stock-obsidian-graph/scripts/build_kr_stock_graph.py --date 20260521 --kind-api-url $env:KIND_API_URL --bigkinds-api-url $env:BIGKINDS_API_URL --ksd-seibro-api-url $env:SEIBRO_API_URL --provider-api-url $env:PROVIDER_API_URL --fsc-stock-issue-url $env:FSC_STOCK_ISSUE_URL --fsc-stock-dividend-url $env:FSC_STOCK_DIVIDEND_URL --external-api-config $env:EXTERNAL_API_CONFIG --probe-external-apis-only --require-external-direct-apis --output-dir reports/stock_graph
```

## Actions

| ID | Source | Blocks | Required Action | Env Keys | Option | Completion Gate | Latest Probe | Probe Class | Next Fix | Fallback | Evidence |
|---|---|---|---|---|---|---|---|---|---|---|---|
| bigkinds_direct_api_gap | BIGKinds | full_100_direct_api | BIGKinds Open API 이용 신청, 호출 제한과 응답 레이아웃 확인 | BIGKINDS_API_KEY, BIGKINDS_API_URL | --bigkinds-api-url | probe_ok_with_expected_fields | skipped: endpoint_config_missing | endpoint_config_missing | 공식 endpoint URL을 확인해 해당 *_API_URL 환경변수 또는 EXTERNAL_API_CONFIG에 설정한다. | --bigkinds-snapshots | EXTERNAL_API_READINESS.json, SOURCE_COVERAGE.json, COMPLETION_AUDIT.json, FULL_100_ACTIONS.json |
| fsc_stock_dividend_auth_or_license_review_required | data.go.kr FSC | full_100_direct_api | 금융위원회_주식배당정보 활용신청 승인, 일반 인증키 Decoding 값, Swagger operation URL 확인 | DATA_GO_KR_SERVICE_KEY, FSC_STOCK_DIVIDEND_URL | --fsc-stock-dividend-url | probe_ok_with_expected_fields | degraded: HTTP Error 401: Unauthorized | auth_or_approval_failed | data.go.kr 마이페이지에서 해당 서비스 활용신청 승인 상태와 일반 인증키 Decoding 값을 확인한다. | FnGuide 공개 배당률, DART 배당 공시, SEIBro/KSD snapshot import | EXTERNAL_API_READINESS.json, SOURCE_COVERAGE.json, COMPLETION_AUDIT.json, FULL_100_ACTIONS.json |
| fsc_stock_issue_endpoint_review_required | data.go.kr FSC | full_100_direct_api | 금융위원회_주식발행정보 Swagger의 최신 operation URL 확인 후 FSC_STOCK_ISSUE_URL에 반영 | DATA_GO_KR_SERVICE_KEY, FSC_STOCK_ISSUE_URL | --fsc-stock-issue-url | probe_ok_with_expected_fields | degraded: HTTP Error 404: Not Found | endpoint_or_operation_not_found | data.go.kr Swagger에서 최신 service/operation URL을 확인해 endpoint URL을 갱신한다. | DART 발행/자본변동 공시와 KRX 상장주식수 | EXTERNAL_API_READINESS.json, SOURCE_COVERAGE.json, COMPLETION_AUDIT.json, FULL_100_ACTIONS.json |
| kind_direct_api_gap | KIND | full_100_direct_api | KIND 화면별 공식 API 또는 엑셀 다운로드 자동화 규격 확정 | KIND_API_KEY, KIND_API_URL | --kind-api-url | probe_ok_with_expected_fields | skipped: endpoint_config_missing | endpoint_config_missing | 공식 endpoint URL을 확인해 해당 *_API_URL 환경변수 또는 EXTERNAL_API_CONFIG에 설정한다. | --kind-snapshots | EXTERNAL_API_READINESS.json, SOURCE_COVERAGE.json, COMPLETION_AUDIT.json, FULL_100_ACTIONS.json |
| ksd_seibro_direct_api_gap | SEIBro/KSD | full_100_direct_api | SEIBro 오픈플랫폼 또는 KSD GW 서비스별 승인, 레이아웃, 상업적 이용 가능 여부 확인 | SEIBRO_API_KEY, KSD_API_KEY, DATA_GO_KR_SERVICE_KEY, SEIBRO_API_URL, KSD_API_URL | --ksd-seibro-api-url | probe_ok_with_expected_fields | skipped: endpoint_config_missing | endpoint_config_missing | 공식 endpoint URL을 확인해 해당 *_API_URL 환경변수 또는 EXTERNAL_API_CONFIG에 설정한다. | --ksd-seibro-snapshots | EXTERNAL_API_READINESS.json, SOURCE_COVERAGE.json, COMPLETION_AUDIT.json, FULL_100_ACTIONS.json |
| ksd_seibro_license_review_required | SEIBro/KSD | full_100_direct_api | SEIBro/KSD 원천별 이용허락, 출처표시, 비영리/상업적 이용 제한 확인 | - | - | license_review_recorded | not_run | probe_not_run | probe_not_run | --ksd-seibro-snapshots | EXTERNAL_API_READINESS.json, SOURCE_COVERAGE.json, COMPLETION_AUDIT.json, FULL_100_ACTIONS.json |
| paid_provider_contract_required | Paid providers | optional_enrichment | FnGuide/DataGuide/QuantiWise/DeepSearch/Finorma 등 유료 데이터 제공업체와 데이터 사용 계약 체결 | - | - | contract_review_recorded | - | - | probe_not_run | --provider-snapshots | EXTERNAL_API_READINESS.json, SOURCE_COVERAGE.json, COMPLETION_AUDIT.json, FULL_100_ACTIONS.json |
| paid_provider_direct_api_gap | Paid providers | optional_enrichment | FnGuide/DataGuide/QuantiWise/DeepSearch/Finorma 계약과 API key 또는 파일 레이아웃 확인 | FNGUIDE_API_KEY, DATAGUIDE_API_KEY, QUANTIWISE_API_KEY, DEEPSEARCH_API_KEY, FINORMA_API_KEY, PROVIDER_API_URL | --provider-api-url | probe_ok_with_expected_fields | skipped: endpoint_config_missing | endpoint_config_missing | 공식 endpoint URL을 확인해 해당 *_API_URL 환경변수 또는 EXTERNAL_API_CONFIG에 설정한다. | --provider-snapshots | EXTERNAL_API_READINESS.json, SOURCE_COVERAGE.json, COMPLETION_AUDIT.json, FULL_100_ACTIONS.json |

## Official Sources

| ID | Source URLs | Auth Hint | License Note |
|---|---|---|---|
| bigkinds_direct_api_gap | https://www.bigkinds.or.kr/ | - | - |
| fsc_stock_dividend_auth_or_license_review_required | https://www.data.go.kr/data/15043284/openapi.do, https://www.data.go.kr/catalog/15043284/openapi.json | data.go.kr GW Swagger 호출은 일반 인증키 Decoding 값을 serviceKey에 사용 | 공식 catalog/openapi.json 기준 이용허락범위 제한 없음 |
| fsc_stock_issue_endpoint_review_required | https://www.data.go.kr/data/15043423/openapi.do, https://www.data.go.kr/catalog/15043423/openapi.json | data.go.kr GW Swagger 호출은 일반 인증키 Decoding 값을 serviceKey에 사용 | 공식 catalog/openapi.json 기준 제3자 권리 포함, 비영리, 공공누리 제2유형 출처표시+상업적 이용금지; 상업 활용은 한국예탁결제원 정보이용계약 필요 |
| kind_direct_api_gap | https://kind.krx.co.kr/ | - | - |
| ksd_seibro_direct_api_gap | https://seibro.or.kr/, https://www.data.go.kr/ | data.go.kr GW Swagger 호출은 일반 인증키 Decoding 값을 serviceKey에 사용 | - |
| ksd_seibro_license_review_required | https://seibro.or.kr/, https://www.data.go.kr/ | - | - |
| paid_provider_contract_required | https://www.fnguide.com/, https://www.deepsearch.com/ | - | - |
| paid_provider_direct_api_gap | https://www.fnguide.com/, https://www.deepsearch.com/ | - | - |

## Probe Attempts

| ID | Scheme | Key Param | Status | Rows | Error |
|---|---|---|---|---:|---|
| fsc_stock_dividend_auth_or_license_review_required | https | serviceKey | degraded | 0 | HTTP Error 401: Unauthorized |
| fsc_stock_dividend_auth_or_license_review_required | https | ServiceKey | degraded | 0 | HTTP Error 401: Unauthorized |
| fsc_stock_dividend_auth_or_license_review_required | http | serviceKey | degraded | 0 | HTTP Error 401: Unauthorized |
| fsc_stock_dividend_auth_or_license_review_required | http | ServiceKey | degraded | 0 | HTTP Error 401: Unauthorized |
| fsc_stock_issue_endpoint_review_required | https | serviceKey | degraded | 0 | HTTP Error 404: Not Found |
| fsc_stock_issue_endpoint_review_required | https | ServiceKey | degraded | 0 | HTTP Error 404: Not Found |
| fsc_stock_issue_endpoint_review_required | http | serviceKey | degraded | 0 | HTTP Error 404: Not Found |
| fsc_stock_issue_endpoint_review_required | http | ServiceKey | degraded | 0 | HTTP Error 404: Not Found |

## Operation Candidates

| ID | Operation | Name | Purpose | Default URL | Expected Fields |
|---|---|---|---|---|---|
| fsc_stock_issue_endpoint_review_required | getItemBasiInfo | 종목기본정보 조회 | 주식액면가, 발행주식수, 상장/상장폐지일자 등 종목 기본정보 | https://apis.data.go.kr/1160100/service/GetStocIssuInfoService/getItemBasiInfo | crno, isinCd, stckIssuCmpyNm, stckParPrc, issuStckCnt, lstgDt |
| fsc_stock_issue_endpoint_review_required | stock_issue_history | 주식발행내역 조회 | 주식발행일자, 발행차수, 발행사유 등 자본 이벤트 | - | crno, stckIssuCmpyNm, stckIssuDt, isuStckCnt, stckIssuRcdNm |
| fsc_stock_issue_endpoint_review_required | lockup_return | 의무보호예수반환정보 조회 | lockup return / 의무보호예수 반환일자와 반환주식수 | - | crno, stckIssuCmpyNm, rtnDt, rtnStckCnt, dpsgRegDt |
| fsc_stock_issue_endpoint_review_required | getStocIssuStat | 주식발행현황 조회 | 보통주/우선주 총발행수 | https://apis.data.go.kr/1160100/service/GetStocIssuInfoService/getStocIssuStat | crno, stckIssuCmpyNm, onskTisuCnt, pfstTisuCnt |

## Operation Probe Results

| ID | Operation | Name | Status | Rows | Sample Keys | Error |
|---|---|---|---|---:|---|---|
| fsc_stock_issue_endpoint_review_required | getItemBasiInfo | 종목기본정보 조회 | degraded | 0 | - | HTTP Error 404: Not Found |
| fsc_stock_issue_endpoint_review_required | stock_issue_history | 주식발행내역 조회 | skipped | 0 | - | operation_url_missing_from_public_metadata |
| fsc_stock_issue_endpoint_review_required | lockup_return | 의무보호예수반환정보 조회 | skipped | 0 | - | operation_url_missing_from_public_metadata |
| fsc_stock_issue_endpoint_review_required | getStocIssuStat | 주식발행현황 조회 | degraded | 0 | - | HTTP Error 404: Not Found |

## Operator Steps

### bigkinds_direct_api_gap
- BIGKINDS_API_URL에 공식 endpoint URL을 설정한다.
- BIGKINDS_API_KEY 인증키가 .env 또는 실행 환경에 있는지 확인한다.
- probe 실행 후 EXTERNAL_API_READINESS.json의 probe.status가 ok이고 예상 필드가 모두 포함되는지 확인한다.
- SOURCE_COVERAGE.json과 COMPLETION_AUDIT.json을 재생성해 해당 gap이 사라졌는지 확인한다.

### fsc_stock_dividend_auth_or_license_review_required
- FSC_STOCK_DIVIDEND_URL에 공식 endpoint URL을 설정한다.
- DATA_GO_KR_SERVICE_KEY 인증키가 .env 또는 실행 환경에 있는지 확인한다.
- EXTERNAL_API_CONFIG의 data.go.kr FSC.license_review에 license_type, source_name, reviewed_at, intended_use를 기록한다.
- probe 실행 후 EXTERNAL_API_READINESS.json의 probe.status가 ok이고 예상 필드가 모두 포함되는지 확인한다.
- SOURCE_COVERAGE.json과 COMPLETION_AUDIT.json을 재생성해 해당 gap이 사라졌는지 확인한다.

### fsc_stock_issue_endpoint_review_required
- FSC_STOCK_ISSUE_URL에 공식 endpoint URL을 설정한다.
- DATA_GO_KR_SERVICE_KEY 인증키가 .env 또는 실행 환경에 있는지 확인한다.
- EXTERNAL_API_CONFIG의 data.go.kr FSC.license_review에 license_type, source_name, reviewed_at, intended_use를 기록한다.
- probe 실행 후 EXTERNAL_API_READINESS.json의 probe.status가 ok이고 예상 필드가 모두 포함되는지 확인한다.
- SOURCE_COVERAGE.json과 COMPLETION_AUDIT.json을 재생성해 해당 gap이 사라졌는지 확인한다.

### kind_direct_api_gap
- KIND_API_URL에 공식 endpoint URL을 설정한다.
- KIND_API_KEY 인증키가 .env 또는 실행 환경에 있는지 확인한다.
- probe 실행 후 EXTERNAL_API_READINESS.json의 probe.status가 ok이고 예상 필드가 모두 포함되는지 확인한다.
- SOURCE_COVERAGE.json과 COMPLETION_AUDIT.json을 재생성해 해당 gap이 사라졌는지 확인한다.

### ksd_seibro_direct_api_gap
- SEIBRO_API_URL, KSD_API_URL에 공식 endpoint URL을 설정한다.
- SEIBRO_API_KEY, KSD_API_KEY, DATA_GO_KR_SERVICE_KEY 인증키가 .env 또는 실행 환경에 있는지 확인한다.
- probe 실행 후 EXTERNAL_API_READINESS.json의 probe.status가 ok이고 예상 필드가 모두 포함되는지 확인한다.
- SOURCE_COVERAGE.json과 COMPLETION_AUDIT.json을 재생성해 해당 gap이 사라졌는지 확인한다.

### ksd_seibro_license_review_required
- EXTERNAL_API_CONFIG의 SEIBro/KSD.license_review에 이용허락, 상업적 이용 가능 여부, 출처표시 조건을 기록한다.
- SOURCE_COVERAGE.json과 COMPLETION_AUDIT.json을 재생성해 해당 gap이 사라졌는지 확인한다.

### paid_provider_contract_required
- EXTERNAL_API_CONFIG의 Paid providers.contract_review에 계약 ID, 제공사명, 라이선스 범위, 유효기간을 기록한다.
- SOURCE_COVERAGE.json과 COMPLETION_AUDIT.json을 재생성해 해당 gap이 사라졌는지 확인한다.

### paid_provider_direct_api_gap
- PROVIDER_API_URL에 공식 endpoint URL을 설정한다.
- FNGUIDE_API_KEY, DATAGUIDE_API_KEY, QUANTIWISE_API_KEY, DEEPSEARCH_API_KEY, FINORMA_API_KEY 인증키가 .env 또는 실행 환경에 있는지 확인한다.
- probe 실행 후 EXTERNAL_API_READINESS.json의 probe.status가 ok이고 예상 필드가 모두 포함되는지 확인한다.
- SOURCE_COVERAGE.json과 COMPLETION_AUDIT.json을 재생성해 해당 gap이 사라졌는지 확인한다.
