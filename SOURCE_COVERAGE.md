# Source Coverage

생성시각: 2026-05-28T08:37:24.856847+09:00
기준일: 20260521

## Summary

- source_count: 11
- direct_or_loaded_count: 4
- snapshot_import_path_count: 5
- remaining_direct_api_gaps: direct_api_gap

## Sources

| Source | Mode | Status | Count | Gaps |
|---|---|---:|---:|---|
| KRX Open API | direct_api | loaded | 37033 | - |
| OpenDART | direct_api | ok: transaction_docs 14, counterparties 14 | 530 | - |
| data.go.kr FSC | direct_api | ok: 2656 stocks, source_date 20260521 | 2656 | - |
| data.go.kr FTC | direct_api | ok: 388 listed companies, public_ym 202605 | 388 | - |
| KIND | snapshot_import | skipped | 0 | direct_api_gap |
| BIGKinds | snapshot_import | skipped | 0 | direct_api_gap |
| KRX Data Marketplace | snapshot_import | skipped | 0 | - |
| SEIBro/KSD | snapshot_import | skipped | 0 | direct_api_gap, license_review_required |
| Paid providers | contract_snapshot_import | skipped | 0 | contract_required, direct_api_gap |
| Naver Finance | public_page_cache | ok: 2348 stocks, 6448 stock-theme links | 0 | public_page_fragility |
| FnGuide public page | public_page_cache | ok: 2622 stocks | 2652 | public_page_fragility |
