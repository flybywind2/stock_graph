# External API Live Runbook

이 runbook은 `EXTERNAL_API.env.example`을 실제 `.env` 값으로 채운 뒤 설정형 direct API를 live fetch로 전환하는 절차다. Secret 값은 이 문서와 감사 산출물에 기록하지 않는다.

## 1. Fill .env

- `EXTERNAL_API.env.example`의 빈 값을 실제 발급 키와 endpoint URL로 채운다.
- KIND/BIGKinds/SEIBro/KSD/provider 중 아직 계약이나 URL이 없는 항목은 비워둔다.
- `EXTERNAL_API_CONFIG.example.json`을 복사해 실제 제공처 레이아웃에 맞춘 config JSON을 만든다.
- 서비스별 파라미터명이나 응답 배열 위치가 다르면 `EXTERNAL_API_CONFIG` JSON 파일에 `url`, `api_key_name`, `params`, `row_path`를 설정한다.
- 주식발행정보/주식배당정보는 고정 data.go.kr client가 사용하므로 최신 Swagger operation URL을 확인한 뒤 `FSC_STOCK_ISSUE_URL`, `FSC_STOCK_DIVIDEND_URL`에 직접 넣는다.
- SEIBro/KSD 라이선스 검토가 끝나면 `SEIBro/KSD.license_review`에 `license_type`, `commercial_use_allowed`, `attribution_required`, `source_name`, `reviewed_at`을 채운다.
- data.go.kr FSC 주식발행/배당은 공식 catalog상 KSD 제3자 권리와 상업적 이용금지 조건이 있으므로 `data.go.kr FSC.license_review`에 `license_type`, `source_name`, `reviewed_at`, `intended_use`를 채운다.
- 유료 provider 계약이 끝나면 `Paid providers.contract_review`에 `contract_id`, `license_scope`, `provider_name`, `valid_from`, `valid_to`를 채운다.

## 2. Probe endpoints first

```powershell
python skills/kr-stock-obsidian-graph/scripts/build_kr_stock_graph.py `
  --date 20260731 `
  --kind-api-url $env:KIND_API_URL `
  --bigkinds-api-url $env:BIGKINDS_API_URL `
  --ksd-seibro-api-url $env:SEIBRO_API_URL `
  --provider-api-url $env:PROVIDER_API_URL `
  --fsc-stock-issue-url $env:FSC_STOCK_ISSUE_URL `
  --fsc-stock-dividend-url $env:FSC_STOCK_DIVIDEND_URL `
  --external-api-config $env:EXTERNAL_API_CONFIG `
  --probe-external-apis-only `
  --require-external-direct-apis `
  --output-dir reports/stock_graph
```

## 3. Run live build

```powershell
python skills/kr-stock-obsidian-graph/scripts/build_kr_stock_graph.py `
  --date 20260731 `
  --kind-api-url $env:KIND_API_URL `
  --bigkinds-api-url $env:BIGKINDS_API_URL `
  --ksd-seibro-api-url $env:SEIBRO_API_URL `
  --provider-api-url $env:PROVIDER_API_URL `
  --fsc-stock-issue-url $env:FSC_STOCK_ISSUE_URL `
  --fsc-stock-dividend-url $env:FSC_STOCK_DIVIDEND_URL `
  --external-api-config $env:EXTERNAL_API_CONFIG `
  --probe-external-apis `
  --require-external-direct-apis `
  --output-dir reports/stock_graph
```

## 4. Verify gates

- `EXTERNAL_DEPENDENCY_AUDIT.json`: `live_fetch_ready_gap_count`가 채운 원천 수만큼 증가해야 한다.
- `EXTERNAL_API_READINESS.json`: `probe.status`가 `ok`이고 `probe.row_count`가 1 이상이면 endpoint와 레이아웃이 실제 응답을 반환한 것이다.
- `SOURCE_COVERAGE.json`: 해당 source status가 `ok: direct_api ... rows` 또는 loaded 상태로 바뀌어야 한다.
- `COMPLETION_AUDIT.json`: 무료 코어 `free_core_status`는 계속 `verified`여야 한다.
- `--require-external-direct-apis`: direct API completion이 `verified`가 아니면 exit code 8로 실패해야 한다.
- `QUALITY_AUDIT.json`: status가 `pass`여야 한다.

## 5. Current gaps

| ID | Ready | Missing Requirements |
|---|---:|---|
| bigkinds_direct_api_gap | False | credential_missing |
| ksd_seibro_direct_api_gap | True | - |
| paid_provider_contract_required | False | contract_required |
| paid_provider_direct_api_gap | False | credential_missing, endpoint_config_missing |
