# Official Snapshot Import

Generated: 2026-05-28T20:59:22.926930+09:00

| Field | Value |
|---|---|
| ready_to_close_any_gap | False |
| ready_file_count | 0 |
| all_templates_header_only | True |
| source_dir |  |
| loaded_files |  |
| missing_files |  |

## Standard Command

```powershell
python skills/kr-stock-obsidian-graph/scripts/build_kr_stock_graph.py --official-snapshot-dir reports/stock_graph/official_snapshots --output-dir reports/stock_graph
```

## Files

| File | Template Rows | Source Rows | Imported Rows | Loaded | Missing | Ready | Closes gaps |
|---|---:|---:|---:|---|---|---|---|
| `kind_events.csv` | 0 | 0 | 0 | False | False | False | kind_direct_api_gap |
| `bigkinds_articles.csv` | 0 | 0 | 0 | False | False | False | bigkinds_direct_api_gap |
| `ksd_seibro_events.csv` | 0 | 0 | 0 | False | False | False | ksd_seibro_direct_api_gap, ksd_seibro_license_review_required |
| `fsc_stock_issue_events.csv` | 0 | 0 | 0 | False | False | False | fsc_stock_issue_endpoint_review_required |
| `fsc_stock_dividend_events.csv` | 0 | 0 | 0 | False | False | False | fsc_stock_dividend_auth_or_license_review_required |
