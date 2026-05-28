# Official Snapshot Import

Generated: 2026-05-28T15:51:47.340317+09:00

| Field | Value |
|---|---|
| ready_to_close_any_gap | False |
| ready_file_count | 0 |
| all_templates_header_only | True |

## Standard Command

```powershell
python skills/kr-stock-obsidian-graph/scripts/build_kr_stock_graph.py --official-snapshot-dir reports/stock_graph/official_snapshots --output-dir reports/stock_graph
```

## Files

| File | Template Rows | Imported Rows | Ready | Closes gaps |
|---|---:|---:|---|---|
| `kind_events.csv` | 0 | 0 | False | kind_direct_api_gap |
| `bigkinds_articles.csv` | 0 | 0 | False | bigkinds_direct_api_gap |
| `ksd_seibro_events.csv` | 0 | 0 | False | ksd_seibro_direct_api_gap, ksd_seibro_license_review_required |
| `fsc_stock_issue_events.csv` | 0 | 0 | False | fsc_stock_issue_endpoint_review_required |
| `fsc_stock_dividend_events.csv` | 0 | 0 | False | fsc_stock_dividend_auth_or_license_review_required |
