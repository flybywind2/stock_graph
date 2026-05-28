# Source Coverage

생성시각: 2026-05-28T12:00:25.138041+09:00
기준일: 20260521

## Summary

- source_count: 12
- direct_or_loaded_count: 4
- configured_direct_api_loaded_count: 0
- contract_direct_api_loaded_count: 0
- approved_direct_api_backlog_count: 1
- snapshot_import_path_count: 5
- remaining_direct_api_gaps: bigkinds_direct_api_gap, kind_direct_api_gap, ksd_seibro_direct_api_gap, paid_provider_direct_api_gap
- remaining_approved_import_backlogs: approved_data_go_kr_import_backlog

## Sources

| Source | Mode | Status | Count | Gaps |
|---|---|---:|---:|---|
| KRX Open API | direct_api | loaded | 37038 | - |
| OpenDART | direct_api | ok: transaction_docs 14, counterparties 14 | 530 | - |
| data.go.kr FSC | direct_api | ok: 2656 stocks, source_date 20260521 | 2656 | - |
| data.go.kr FTC | direct_api | ok: 388 listed companies, public_ym 202605 | 388 | - |
| data.go.kr FSC approved | approved_direct_api_backlog | approved_not_imported | 5 | approved_data_go_kr_import_backlog |
| KIND | snapshot_import | skipped | 0 | kind_direct_api_gap |
| BIGKinds | snapshot_import | skipped | 0 | bigkinds_direct_api_gap |
| KRX Data Marketplace | snapshot_import | skipped | 0 | - |
| SEIBro/KSD | snapshot_import | skipped | 0 | ksd_seibro_direct_api_gap, ksd_seibro_license_review_required |
| Paid providers | contract_snapshot_import | skipped | 0 | paid_provider_contract_required, paid_provider_direct_api_gap |
| Naver Finance | public_page_cache | ok: 2348 stocks, 6448 stock-theme links | 0 | public_page_fragility |
| FnGuide public page | public_page_cache | ok: 2622 stocks | 2652 | public_page_fragility |
