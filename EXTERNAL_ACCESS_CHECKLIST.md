# External Access Checklist

생성시각: 2026-05-28T20:50:04.343106+09:00
기준일: 20260521

## Summary

- status: blocked_external_dependency
- required_open_count: 0
- optional_open_count: 3
- can_claim_full_100_complete: False
- secret_values_recorded: False

## Probe Command

```powershell
python skills/kr-stock-obsidian-graph/scripts/build_kr_stock_graph.py --probe-external-apis-only
```

## Required For 100%

## Optional Enrichment

- BIGKinds: BIGKinds Open API access_key를 BIGKINDS_API_KEY에 설정한 뒤 probe를 재실행한다.
- Paid providers: probe_not_run
- Paid providers: 공식 endpoint URL을 확인해 해당 *_API_URL 환경변수 또는 EXTERNAL_API_CONFIG에 설정한다.
