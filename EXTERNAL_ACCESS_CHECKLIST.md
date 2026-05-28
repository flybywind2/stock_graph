# External Access Checklist

생성시각: 2026-05-28T18:03:02.991564+09:00
기준일: 20260521

## Summary

- status: blocked_external_dependency
- required_open_count: 2
- optional_open_count: 2
- can_claim_full_100_complete: False
- secret_values_recorded: False

## Probe Command

```powershell
python skills/kr-stock-obsidian-graph/scripts/build_kr_stock_graph.py --probe-external-apis-only
```

## Required For 100%

### BIGKinds / bigkinds_direct_api_gap

- probe_status: skipped
- probe_failure_class: credential_missing
- next_fix: BIGKinds Open API access_key를 BIGKINDS_API_KEY에 설정한 뒤 probe를 재실행한다.
- credential_env_keys: BIGKINDS_API_KEY

Operator checklist:
- [ ] BIGKinds Open API access_key를 발급받아 .env의 BIGKINDS_API_KEY에 설정한다.
- [ ] BIGKINDS_API_URL은 비워두면 https://tools.kinds.or.kr/search/news 기본 endpoint를 사용한다.
- [ ] POST_JSON body의 access_key 방식으로 호출되는지 --probe-external-apis-only로 확인한다.
- [ ] EXTERNAL_API_READINESS.json에서 probe.status가 ok이고 return_object.documents row가 잡히는지 확인한다.

### SEIBro/KSD / ksd_seibro_direct_api_gap

- probe_status: degraded
- probe_failure_class: auth_or_approval_failed
- next_fix: data.go.kr 마이페이지에서 한국예탁결제원_주식정보서비스_GW 활용신청 승인 상태와 일반 인증키 Decoding 값을 확인한다.
- credential_env_keys: SEIBRO_API_KEY, KSD_API_KEY, DATA_GO_KR_SERVICE_KEY

Operator checklist:
- [ ] data.go.kr 마이페이지에서 한국예탁결제원_주식정보서비스_GW 활용신청 승인 상태를 확인한다.
- [ ] .env의 DATA_GO_KR_SERVICE_KEY가 같은 계정의 일반 인증키 Decoding 값인지 확인한다.
- [ ] 승인받은 서비스가 B552481/StockSvc 계열인지 확인한다.
- [ ] getStkIsinByShortIsinN1 probe가 HTTP 403 Forbidden 없이 응답하는지 --probe-external-apis-only로 확인한다.
- [ ] 403이 계속되면 해당 서비스의 인증키를 재발급하거나 승인 계정과 키 계정 불일치를 확인한다.

| Operation | Status | Error |
|---|---|---|
| getStkIsinByShortIsinN1 | degraded | HTTP Error 403: Forbidden |
| getDividendRankN1 | degraded | HTTP Error 403: Forbidden |
| getSafeDpDutyDepoStatusN1 | degraded | HTTP Error 403: Forbidden |
| getSafeDpDutyDepoRgtStatusN1 | degraded | HTTP Error 403: Forbidden |
| getStkListInfoN1 | degraded | HTTP Error 403: Forbidden |

## Optional Enrichment

- Paid providers: probe_not_run
- Paid providers: 공식 endpoint URL을 확인해 해당 *_API_URL 환경변수 또는 EXTERNAL_API_CONFIG에 설정한다.
