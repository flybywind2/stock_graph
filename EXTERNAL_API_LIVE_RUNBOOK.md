# External API Live Runbook

이 runbook은 `EXTERNAL_API.env.example`을 실제 `.env` 값으로 채운 뒤 설정형 direct API를 live fetch로 전환하는 절차다. Secret 값은 이 문서와 감사 산출물에 기록하지 않는다.

## 1. Fill .env

- `EXTERNAL_API.env.example`의 빈 값을 실제 발급 키와 endpoint URL로 채운다.
- KIND/BIGKinds/SEIBro/KSD/provider 중 아직 계약이나 URL이 없는 항목은 비워둔다.

## 2. Probe endpoints first

```powershell
python skills/kr-stock-obsidian-graph/scripts/build_kr_stock_graph.py `
  --date 20260521 `
  --kind-api-url $env:KIND_API_URL `
  --bigkinds-api-url $env:BIGKINDS_API_URL `
  --ksd-seibro-api-url $env:SEIBRO_API_URL `
  --provider-api-url $env:PROVIDER_API_URL `
  --probe-external-apis-only `
  --output-dir reports/stock_graph
```

## 3. Run live build

```powershell
python skills/kr-stock-obsidian-graph/scripts/build_kr_stock_graph.py `
  --date 20260521 `
  --kind-api-url $env:KIND_API_URL `
  --bigkinds-api-url $env:BIGKINDS_API_URL `
  --ksd-seibro-api-url $env:SEIBRO_API_URL `
  --provider-api-url $env:PROVIDER_API_URL `
  --probe-external-apis `
  --output-dir reports/stock_graph
```

## 4. Verify gates

- `EXTERNAL_DEPENDENCY_AUDIT.json`: `live_fetch_ready_gap_count`가 채운 원천 수만큼 증가해야 한다.
- `EXTERNAL_API_READINESS.json`: `probe.status`가 `ok`이고 `probe.row_count`가 1 이상이면 endpoint와 레이아웃이 실제 응답을 반환한 것이다.
- `SOURCE_COVERAGE.json`: 해당 source status가 `ok: direct_api ... rows` 또는 loaded 상태로 바뀌어야 한다.
- `COMPLETION_AUDIT.json`: 무료 코어 `free_core_status`는 계속 `verified`여야 한다.
- `QUALITY_AUDIT.json`: status가 `pass`여야 한다.

## 5. Current gaps

| ID | Ready | Missing Requirements |
|---|---:|---|
| bigkinds_direct_api_gap | False | credential_missing, endpoint_config_missing |
| kind_direct_api_gap | False | credential_missing, endpoint_config_missing |
| ksd_seibro_direct_api_gap | False | endpoint_config_missing |
| paid_provider_contract_required | False | contract_required |
| paid_provider_direct_api_gap | False | credential_missing, endpoint_config_missing |
