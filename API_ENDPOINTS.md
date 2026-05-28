# API Endpoint Inventory

생성시각: 2026-05-28T14:00:34.681833+09:00
기준일: 20260521

## Summary

- endpoint_count: 45
- direct_api_count: 31
- configured_direct_api_count: 3
- contract_direct_api_count: 1
- approved_direct_api_backlog_count: 0
- snapshot_import_count: 6
- contract_snapshot_import_count: 1
- public_page_cache_count: 3

## Endpoints

| ID | Source | Mode | Auth | URL / Path | Option |
|---|---|---|---|---|---|
| dart_corp_code | OpenDART | direct_api | DART_OPEN_API_KEY | https://opendart.fss.or.kr/api/corpCode.xml | - |
| dart_disclosure_list | OpenDART | direct_api | DART_OPEN_API_KEY | https://opendart.fss.or.kr/api/list.json | - |
| dart_company_profile | OpenDART | direct_api | DART_OPEN_API_KEY | https://opendart.fss.or.kr/api/company.json | - |
| dart_financial_account | OpenDART | direct_api | DART_OPEN_API_KEY | https://opendart.fss.or.kr/api/fnlttSinglAcnt.json | - |
| dart_major_shareholders | OpenDART | direct_api | DART_OPEN_API_KEY | https://opendart.fss.or.kr/api/hyslrSttus.json | - |
| dart_executives | OpenDART | direct_api | DART_OPEN_API_KEY | https://opendart.fss.or.kr/api/exctvSttus.json | - |
| dart_other_company_investments | OpenDART | direct_api | DART_OPEN_API_KEY | https://opendart.fss.or.kr/api/otrCprInvstmntSttus.json | - |
| dart_document | OpenDART | direct_api | DART_OPEN_API_KEY | https://opendart.fss.or.kr/api/document.xml | - |
| fsc_krx_listed_info | data.go.kr FSC | direct_api | DATA_GO_KR_SERVICE_KEY | https://apis.data.go.kr/1160100/service/GetKrxListedInfoService/getItemInfo | - |
| fsc_company_basic | data.go.kr FSC | direct_api | DATA_GO_KR_SERVICE_KEY | https://apis.data.go.kr/1160100/service/GetCorpBasicInfoService_V2/getCorpOutline_V2 | - |
| fsc_company_financial | data.go.kr FSC | direct_api | DATA_GO_KR_SERVICE_KEY | https://apis.data.go.kr/1160100/service/GetFinaStatInfoService_V2/getSummFinaStat_V2 | - |
| fsc_stock_issue | data.go.kr FSC | direct_api | DATA_GO_KR_SERVICE_KEY | https://apis.data.go.kr/1160100/service/GetStocIssuInfoService/getItemBasiInfo | - |
| fsc_stock_dividend | data.go.kr FSC | direct_api | DATA_GO_KR_SERVICE_KEY | https://apis.data.go.kr/1160100/service/GetStocDiviInfoService/getDiviInfo | - |
| fsc_financial_company_basic | data.go.kr FSC approved | direct_api | DATA_GO_KR_SERVICE_KEY | https://apis.data.go.kr/1160100/service/GetFnCoBasiInfoService/getFnCoOutl | - |
| fsc_bond_basic | data.go.kr FSC approved | direct_api | DATA_GO_KR_SERVICE_KEY | https://apis.data.go.kr/1160100/service/GetBondIssuInfoService/getBondBasiInfo | - |
| fsc_bond_issue | data.go.kr FSC approved | direct_api | DATA_GO_KR_SERVICE_KEY | https://apis.data.go.kr/1160100/service/GetBondTradInfoService/getIssuIssuItemStat | - |
| fsc_international_dr_item | data.go.kr FSC approved | direct_api | DATA_GO_KR_SERVICE_KEY | https://apis.data.go.kr/1160100/service/GetInterSecuInfoService/getDRItemInfo | - |
| fsc_general_commodity_price | data.go.kr FSC approved | direct_api | DATA_GO_KR_SERVICE_KEY | https://apis.data.go.kr/1160100/service/GetGeneralProductInfoService/getGoldPriceInfo | - |
| ftc_public_ym | data.go.kr FTC | direct_api | DATA_GO_KR_SERVICE_KEY | https://apis.data.go.kr/1130000/publicYmList/publicYmListApi | - |
| ftc_group_status | data.go.kr FTC | direct_api | DATA_GO_KR_SERVICE_KEY | https://apis.data.go.kr/1130000/appnGroupSttusList/appnGroupSttusListApi | - |
| ftc_group_member | data.go.kr FTC | direct_api | DATA_GO_KR_SERVICE_KEY | https://apis.data.go.kr/1130000/appnGroupAffiList/appnGroupAffiListApi | - |
| ftc_group_company_overview | data.go.kr FTC | direct_api | DATA_GO_KR_SERVICE_KEY | https://apis.data.go.kr/1130000/affiliationCompSttusList/affiliationCompSttusListApi | - |
| ftc_group_activity | data.go.kr FTC | direct_api | DATA_GO_KR_SERVICE_KEY | https://apis.data.go.kr/1130000/typeOfBusinessCompSttusList/typeOfBusinessCompSttusListApi | - |
| ftc_group_financial | data.go.kr FTC | direct_api | DATA_GO_KR_SERVICE_KEY | https://apis.data.go.kr/1130000/financeCompSttusList/financeCompSttusListApi | - |
| krx_kospi_security_master | KRX Open API | direct_api | KRX_OPEN_API_KEY | https://data-dbg.krx.co.kr/svc/apis/sto/stk_isu_base_info | - |
| krx_kosdaq_security_master | KRX Open API | direct_api | KRX_OPEN_API_KEY | https://data-dbg.krx.co.kr/svc/apis/sto/ksq_isu_base_info | - |
| krx_konex_security_master | KRX Open API | direct_api | KRX_OPEN_API_KEY | https://data-dbg.krx.co.kr/svc/apis/sto/knx_isu_base_info | - |
| krx_index_krx_daily | KRX Open API | direct_api | KRX_OPEN_API_KEY | https://data-dbg.krx.co.kr/svc/apis/idx/krx_dd_trd | - |
| krx_index_kospi_daily | KRX Open API | direct_api | KRX_OPEN_API_KEY | https://data-dbg.krx.co.kr/svc/apis/idx/kospi_dd_trd | - |
| krx_index_kosdaq_daily | KRX Open API | direct_api | KRX_OPEN_API_KEY | https://data-dbg.krx.co.kr/svc/apis/idx/kosdaq_dd_trd | - |
| krx_etf_daily | KRX Open API | direct_api | KRX_OPEN_API_KEY | https://data-dbg.krx.co.kr/svc/apis/etp/etf_bydd_trd | - |
| naver_theme_list | Naver Finance | public_page_cache | none | https://finance.naver.com/sise/theme.naver | - |
| naver_theme_detail | Naver Finance | public_page_cache | none | https://finance.naver.com/sise/sise_group_detail.naver | - |
| fnguide_company_profile | FnGuide public page | public_page_cache | none | https://comp.fnguide.com/SVO2/ASP/SVD_Main.asp | - |
| kind_configured_direct_api | KIND | configured_direct_api | KIND_API_KEY | ${KIND_API_URL} | --kind-api-url |
| bigkinds_configured_direct_api | BIGKinds | configured_direct_api | BIGKINDS_API_KEY | ${BIGKINDS_API_URL} | --bigkinds-api-url |
| ksd_seibro_configured_direct_api | SEIBro/KSD | configured_direct_api | SEIBRO_API_KEY/KSD_API_KEY/DATA_GO_KR_SERVICE_KEY | ${SEIBRO_API_URL} or ${KSD_API_URL} | --ksd-seibro-api-url |
| provider_configured_direct_api | Paid providers | contract_direct_api | FNGUIDE_API_KEY/DATAGUIDE_API_KEY/QUANTIWISE_API_KEY/DEEPSEARCH_API_KEY/FINORMA_API_KEY | ${PROVIDER_API_URL} | --provider-api-url |
| kind_snapshots | KIND | snapshot_import | none | local JSON/CSV/TSV file | --kind-snapshots |
| bigkinds_snapshots | BIGKinds | snapshot_import | none or BIGKinds Open API approval | local JSON/CSV/TSV file | --bigkinds-snapshots |
| krx_marketplace_snapshots | KRX Data Marketplace | snapshot_import | none | local JSON/CSV/TSV file | --krx-marketplace-snapshots |
| ksd_seibro_snapshots | SEIBro/KSD | snapshot_import | none or service approval | local JSON/CSV/TSV file | --ksd-seibro-snapshots |
| provider_snapshots | Paid providers | contract_snapshot_import | contract required | local JSON/CSV/TSV file | --provider-snapshots |
| supplemental_events | Manual supplemental | snapshot_import | none | local JSON/CSV/TSV file | --supplemental-events |
| supplemental_relations | Manual supplemental | snapshot_import | none | local JSON/CSV/TSV file | --supplemental-relations |
