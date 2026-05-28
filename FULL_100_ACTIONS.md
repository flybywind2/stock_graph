# Full 100 Actions

생성시각: 2026-05-28T17:07:20.448337+09:00
기준일: 20260521

## Summary

- status: external_actions_required
- remaining_action_count: 4
- remaining_required_action_count: 2
- remaining_optional_action_count: 2
- free_scope_status: external_actions_required
- free_core_status: verified
- external_dependency_status: blocked_external_dependency
- secret_values_recorded: False

## Verification Command

```powershell
python skills/kr-stock-obsidian-graph/scripts/build_kr_stock_graph.py --date 20260528 --kind-api-url $env:KIND_API_URL --bigkinds-api-url $env:BIGKINDS_API_URL --ksd-seibro-api-url $env:SEIBRO_API_URL --provider-api-url $env:PROVIDER_API_URL --fsc-stock-issue-url $env:FSC_STOCK_ISSUE_URL --fsc-stock-dividend-url $env:FSC_STOCK_DIVIDEND_URL --external-api-config $env:EXTERNAL_API_CONFIG --probe-external-apis-only --require-external-direct-apis --output-dir reports/stock_graph
```

## Actions

| ID | Source | Blocks | Required Action | Env Keys | Option | Completion Gate | Latest Probe | Probe Class | Next Fix | Fallback | Evidence |
|---|---|---|---|---|---|---|---|---|---|---|---|
| bigkinds_direct_api_gap | BIGKinds | full_100_direct_api | BIGKinds Open API 이용 신청, 호출 제한과 응답 레이아웃 확인 | BIGKINDS_API_KEY, BIGKINDS_API_URL | --bigkinds-api-url | probe_ok_with_expected_fields | skipped: endpoint_config_missing | endpoint_config_missing | 공식 endpoint URL을 확인해 해당 *_API_URL 환경변수 또는 EXTERNAL_API_CONFIG에 설정한다. | --bigkinds-snapshots | EXTERNAL_API_READINESS.json, SOURCE_COVERAGE.json, COMPLETION_AUDIT.json, FULL_100_ACTIONS.json |
| ksd_seibro_direct_api_gap | SEIBro/KSD | full_100_direct_api | 한국예탁결제원_주식정보서비스_GW 활용신청 승인 후 StockSvc operation URL과 응답 레이아웃 확인 | SEIBRO_API_KEY, KSD_API_KEY, DATA_GO_KR_SERVICE_KEY, SEIBRO_API_URL, KSD_API_URL | --ksd-seibro-api-url | probe_ok_with_expected_fields | skipped: endpoint_config_missing | endpoint_config_missing | 공식 endpoint URL을 확인해 해당 *_API_URL 환경변수 또는 EXTERNAL_API_CONFIG에 설정한다. | --ksd-seibro-snapshots | EXTERNAL_API_READINESS.json, SOURCE_COVERAGE.json, COMPLETION_AUDIT.json, FULL_100_ACTIONS.json |
| paid_provider_contract_required | Paid providers | optional_enrichment | FnGuide/DataGuide/QuantiWise/DeepSearch/Finorma 등 유료 데이터 제공업체와 데이터 사용 계약 체결 | - | - | contract_review_recorded | - | - | probe_not_run | --provider-snapshots | EXTERNAL_API_READINESS.json, SOURCE_COVERAGE.json, COMPLETION_AUDIT.json, FULL_100_ACTIONS.json |
| paid_provider_direct_api_gap | Paid providers | optional_enrichment | FnGuide/DataGuide/QuantiWise/DeepSearch/Finorma 계약과 API key 또는 파일 레이아웃 확인 | FNGUIDE_API_KEY, DATAGUIDE_API_KEY, QUANTIWISE_API_KEY, DEEPSEARCH_API_KEY, FINORMA_API_KEY, PROVIDER_API_URL | --provider-api-url | probe_ok_with_expected_fields | skipped: endpoint_config_missing | endpoint_config_missing | 공식 endpoint URL을 확인해 해당 *_API_URL 환경변수 또는 EXTERNAL_API_CONFIG에 설정한다. | --provider-snapshots | EXTERNAL_API_READINESS.json, SOURCE_COVERAGE.json, COMPLETION_AUDIT.json, FULL_100_ACTIONS.json |

## Official Sources

| ID | Source URLs | Auth Hint | License Note |
|---|---|---|---|
| bigkinds_direct_api_gap | https://www.bigkinds.or.kr/ | - | - |
| ksd_seibro_direct_api_gap | https://seibro.or.kr/, https://www.data.go.kr/data/15157413/openapi.do, https://www.data.go.kr/data/15157416/openapi.do, https://www.data.go.kr/data/15158905/openapi.do, https://www.data.go.kr/data/15157427/openapi.do, https://www.data.go.kr/data/15157428/openapi.do | data.go.kr GW Swagger 호출은 일반 인증키 Decoding 값을 serviceKey에 사용 | - |
| paid_provider_contract_required | https://www.fnguide.com/, https://www.deepsearch.com/ | - | - |
| paid_provider_direct_api_gap | https://www.fnguide.com/, https://www.deepsearch.com/ | - | - |

## Probe Attempts

| ID | Scheme | Key Param | Status | Rows | Error |
|---|---|---|---|---:|---|
| - | - | - | - | 0 | - |

## Operation Candidates

| ID | Operation | Name | Purpose | Default URL | Expected Fields |
|---|---|---|---|---|---|
| ksd_seibro_direct_api_gap | getStkIsinByShortIsinN1 | 단축번호로 주식종목코드(풀코드) 조회 | 상장 단축코드에서 KSD ISIN/발행회사번호/전자증권 여부를 보강 | https://apis.data.go.kr/B552481/StockSvc/getStkIsinByShortIsinN1 | shotnIsin, isin, korSecnNm, issuDt, issucoCustno, eltscYn |
| ksd_seibro_direct_api_gap | getDividendRankN1 | 배당순위조회 | 배당금/배당률 상위 종목을 KSD 근거로 보강 | https://apis.data.go.kr/B552481/StockSvc/getDividendRankN1 | shotnIsin, korSecnNm, divAmtPerStk, divRateCpri, divRatePval |
| ksd_seibro_direct_api_gap | getSafeDpDutyDepoStatusN1 | 의무보호예수전체현황 전체현황표 조회 | 의무보호예수 총량/비율을 권리 이벤트 컨텍스트로 보강 | https://apis.data.go.kr/B552481/StockSvc/getSafeDpDutyDepoStatusN1 | stdDt, stkDepoQty, issuStkqty, safedpRatioValue, secncnt |
| ksd_seibro_direct_api_gap | getSafeDpDutyDepoRgtStatusN1 | 의무보호예수전체현황 사유별 조회 | 의무보호예수 사유별 수량/회사수/종목수를 권리 이벤트 컨텍스트로 보강 | https://apis.data.go.kr/B552481/StockSvc/getSafeDpDutyDepoRgtStatusN1 | safedpRacd, codevalueNm, dutyDepoStkDepoQty, safedpStkDepoQty |
| ksd_seibro_direct_api_gap | getStkListInfoN1 | 주식상장정보 조회 | KSD 상장/상장폐지/발행회사번호를 종목 마스터에 보강 | https://apis.data.go.kr/B552481/StockSvc/getStkListInfoN1 | isin, korSecnNm, listTpcd, apliDt, dlistDt, issucoCustno |

## Operation Probe Results

| ID | Operation | Name | Status | Rows | Sample Keys | Error |
|---|---|---|---|---:|---|---|
| - | - | - | - | 0 | - | - |

## Operator Steps

### bigkinds_direct_api_gap
- BIGKINDS_API_URL에 공식 endpoint URL을 설정한다.
- BIGKINDS_API_KEY 인증키가 .env 또는 실행 환경에 있는지 확인한다.
- probe 실행 후 EXTERNAL_API_READINESS.json의 probe.status가 ok이고 예상 필드가 모두 포함되는지 확인한다.
- SOURCE_COVERAGE.json과 COMPLETION_AUDIT.json을 재생성해 해당 gap이 사라졌는지 확인한다.

### ksd_seibro_direct_api_gap
- SEIBRO_API_URL, KSD_API_URL에 공식 endpoint URL을 설정한다.
- SEIBRO_API_KEY, KSD_API_KEY, DATA_GO_KR_SERVICE_KEY 인증키가 .env 또는 실행 환경에 있는지 확인한다.
- probe 실행 후 EXTERNAL_API_READINESS.json의 probe.status가 ok이고 예상 필드가 모두 포함되는지 확인한다.
- SOURCE_COVERAGE.json과 COMPLETION_AUDIT.json을 재생성해 해당 gap이 사라졌는지 확인한다.

### paid_provider_contract_required
- EXTERNAL_API_CONFIG의 Paid providers.contract_review에 계약 ID, 제공사명, 라이선스 범위, 유효기간을 기록한다.
- SOURCE_COVERAGE.json과 COMPLETION_AUDIT.json을 재생성해 해당 gap이 사라졌는지 확인한다.

### paid_provider_direct_api_gap
- PROVIDER_API_URL에 공식 endpoint URL을 설정한다.
- FNGUIDE_API_KEY, DATAGUIDE_API_KEY, QUANTIWISE_API_KEY, DEEPSEARCH_API_KEY, FINORMA_API_KEY 인증키가 .env 또는 실행 환경에 있는지 확인한다.
- probe 실행 후 EXTERNAL_API_READINESS.json의 probe.status가 ok이고 예상 필드가 모두 포함되는지 확인한다.
- SOURCE_COVERAGE.json과 COMPLETION_AUDIT.json을 재생성해 해당 gap이 사라졌는지 확인한다.
