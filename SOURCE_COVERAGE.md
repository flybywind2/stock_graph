# Source Coverage

생성시각: 2026-05-28T17:41:20.647234+09:00
기준일: 20260521

## Summary

- source_count: 12
- direct_or_loaded_count: 5
- configured_direct_api_loaded_count: 0
- contract_direct_api_loaded_count: 0
- approved_direct_api_backlog_count: 0
- snapshot_import_path_count: 4
- remaining_direct_api_gaps: bigkinds_direct_api_gap, ksd_seibro_direct_api_gap, paid_provider_direct_api_gap
- remaining_approved_import_backlogs: none

## Sources

| Source | Mode | Status | Count | Gaps |
|---|---|---:|---:|---|
| KRX Open API | direct_api | loaded | 17439 | - |
| OpenDART | direct_api | ok: transaction_docs 14, counterparties 14 | 14 | - |
| data.go.kr FSC | direct_api | ok: 2656 stocks, source_date 20260521 | 2656 | - |
| data.go.kr FTC | direct_api | ok: 388 listed companies, public_ym 202605 | 388 | - |
| data.go.kr FSC approved | direct_api | ok: financial_company_basic 81 companies, bond_basic 0 rows, bond_issue 0 rows, international_dr_item 0 rows, general_commodity_price 2 rows | 5 | - |
| KIND | official_web_export | official_export_path_available | 0 | - |
| BIGKinds | snapshot_import | skipped | 0 | bigkinds_direct_api_gap |
| KRX Data Marketplace | snapshot_import | skipped | 0 | - |
| SEIBro/KSD | snapshot_import | skipped | 0 | ksd_seibro_direct_api_gap |
| Paid providers | contract_snapshot_import | skipped | 0 | paid_provider_contract_required, paid_provider_direct_api_gap |
| Naver Finance | public_page_cache | ok: 2348 stocks, 6448 stock-theme links | 0 | public_page_fragility |
| FnGuide public page | public_page_cache | ok: 2622 stocks | 2652 | public_page_fragility |
