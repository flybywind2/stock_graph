# Data Source Access Requirements

생성일: 2026-05-21

이 문서는 현재 그래프 파이프라인이 직접 호출하는 데이터와, 아직 직접 API로 연결하지 못해 파일 import 또는 별도 인증이 필요한 데이터를 구분한다.

## 현재 직접 호출

| Source | Environment key | Access | Used for |
|---|---|---|---|
| KRX Open API | `KRX_OPEN_API_KEY` | KRX Open API 이용신청 및 `AUTH_KEY` 헤더 | KOSPI/KOSDAQ 일별매매, 종목기본정보, 지수, ETF |
| OpenDART | `DART_OPEN_API_KEY` | OpenDART 인증키 | corpCode, 공시목록, 원문, 기업개황, 주요계정, 최대주주, 임원, 타법인출자 |
| data.go.kr 금융위원회 | `DATA_GO_KR_SERVICE_KEY` | 공공데이터포털 활용신청 | KRX 상장종목정보, 기업기본정보, 기업 재무정보, 주식발행정보, 주식배당정보 |
| data.go.kr 공정거래위원회 | `DATA_GO_KR_SERVICE_KEY` | 공공데이터포털 활용신청 | 대규모기업집단, 소속회사, 참여업종, 재무현황 |
| KIND export | 없음 | 웹에서 CSV/TSV/JSON 다운로드 후 `--kind-snapshots` 지정 | 거래소 공시, IR자료, 기업분석보고서 이벤트/증거 |
| BIGKinds export | 없음 또는 Open API 승인 | CSV/TSV/JSON 다운로드 후 `--bigkinds-snapshots` 지정 | 뉴스 기사, 개체명, 키워드 기반 이벤트/증거 |
| KRX Data Marketplace export | 없음 | 웹에서 CSV/TSV/JSON 다운로드 후 `--krx-marketplace-snapshots` 지정 | 업종분류, 지수구성종목, ETF PDF/편입종목 |
| SEIBro / KSD export | 없음 또는 서비스별 승인 | CSV/TSV/JSON 다운로드 후 `--ksd-seibro-snapshots` 지정 | 배당/권리, 증권대차, 보호예수 해제 이벤트 |
| Paid provider export | 계약 필요 | CSV/TSV/JSON 다운로드 후 `--provider-snapshots` 지정 | 컨센서스, 리포트, 정제 공급망/관계망 |
| Naver Finance | 없음 | 공개 페이지 캐시 | 테마 그룹 보강 |
| FnGuide public page | 없음 | 공개 페이지 캐시 | 섹터, 업종, PER/PBR/배당 보강 |

## HTML graph layer

| Preset | Meaning |
|---|---|
| 거래 관계 | DART 공급/판매계약, 계열 상품·용역거래, RelationFact/Evidence 근거 |
| 공식 사실 그래프 | KRX, DART, 금융위, 공정위에서 확인되는 식별자, 시장, 업종, 기업집단, 재무, 지분, 임원, 발행/배당 관계 |
| 시장·이벤트 파급 | 잔차 동행, 1일 선행, 거래, peer, positive/negative exposure 기반 1~3홉 파급 관계 |
| 의미 중심 | 기업집단, 참여업종, 사업군, 테마, 외부 업종 중심 관계 |
| 투자지표 포함 | 의미 관계에 재무, 밸류에이션, 배당, DART 구조 관계를 추가 |

## Graph DB export

`neo4j/nodes.csv`, `neo4j/relationships.csv`, `neo4j/import.cypher`를 함께 생성한다. 정적 HTML은 탐색용이고, Neo4j export는 전략 문서의 다중 홉 질의, 경로 점수 검증, 그래프 DB 이전 검토용이다.

## Impact summary

그래프 JSON/JS의 `meta.impact_summary`에는 상위 종목별 1~3홉 signed path 영향권 요약을 저장한다. HTML 상세 패널의 실시간 계산과 같은 방향의 점수이며, 외부 분석이나 Neo4j 검증에서 빠른 후보군으로 사용할 수 있다.

## Source coverage

`SOURCE_COVERAGE.json`과 `SOURCE_COVERAGE.md`를 함께 생성한다. 각 원천의 `direct_api`, `snapshot_import`, `contract_snapshot_import`, `public_page_cache` 상태와 count, 남은 direct API gap을 기계적으로 확인하기 위한 산출물이다.

## Completion audit

`COMPLETION_AUDIT.json`과 `COMPLETION_AUDIT.md`를 함께 생성한다. 전략 문서의 사실 그래프, 파급 그래프, signed path scoring, source coverage, Neo4j export, Obsidian Vault, HTML explorer, governance metadata 요구사항을 항목별로 검증하고, 외부 인증/계약 때문에 남은 direct API gap은 `blocked_external_dependency`로 분리한다.

## API endpoint inventory

`API_ENDPOINTS.json`과 `API_ENDPOINTS.md`를 함께 생성한다. 현재 코드가 직접 호출하는 OpenDART, data.go.kr FSC/FTC, KRX Open API, Naver/FnGuide 공개 페이지 endpoint와 KIND, BIGKinds, KRX Data Marketplace, SEIBro/KSD, provider snapshot import 경로를 한 파일에서 확인한다.

## 아직 직접 API 미연결

| Source | 필요한 조치 | 현재 반영 방법 |
|---|---|---|
| KIND direct API | 공식 API 또는 화면별 엑셀 다운로드 자동화 규격 확정 | 다운로드 스냅샷은 `--kind-snapshots`로 1급 import, API 직결은 화면별 문서 필요 |
| SEIBro / KSD direct API | 오픈플랫폼 또는 KSD GW 서비스별 승인, 레이아웃 확인, 상업적 이용 가능 여부 확인 | 다운로드 스냅샷은 `--ksd-seibro-snapshots`로 1급 import, API 직결은 서비스별 문서 필요 |
| BIGKinds direct API | Open API 이용 신청, 호출 제한, 응답 레이아웃 확인 | 다운로드/API 결과 스냅샷은 `--bigkinds-snapshots`로 1급 import |
| 유료 FnGuide/DataGuide/QuantiWise direct API | 계약, 데이터 사용권, API key 또는 파일 레이아웃 확인 | 계약 데이터 export는 `--provider-snapshots`로 1급 import |
| DeepSearch / Finorma direct API | 계약 및 API key 발급 | 계약 데이터 export는 `--provider-snapshots`로 1급 import |

## KIND snapshots

KIND 상장공시, IR자료실, 기업분석보고서 export 파일은 `snapshot_type`으로 구분해 넣는다. CSV/TSV/JSON을 지원하고, 이벤트 노드와 Evidence 노드를 함께 만들어 `positive_exposure`, `negative_exposure`, 또는 중립 `has_event`로 종목에 연결한다.

지원 타입:

| snapshot_type | 최소 필드 | 생성 관계 |
|---|---|---|
| `disclosure_event` | `stock_code`, `document_id` 또는 `title` | `event -> stock` `positive_exposure`/`negative_exposure`/`has_event` |
| `ir_material` | `stock_code`, `document_id` 또는 `title` | `event -> stock` + `event -> evidence` |
| `analysis_report` | `stock_code`, `document_id` 또는 `title` | `event -> stock` + `event -> evidence` |

CSV 예시:

```csv
snapshot_type,stock_code,stock_name,document_id,document_type,title,published_at,url,summary,sign,weight,confidence
disclosure_event,005930,삼성전자,KIND-1,단일판매공급계약,삼성전자 공급계약,20260522,https://kind.krx.co.kr/disclosure,공급계약 체결,positive,0.8,0.75
ir_material,000660,SK하이닉스,KIND-IR-1,IR,SK하이닉스 IR,20260521,https://kind.krx.co.kr/ir,HBM 투자 설명,positive,0.6,0.65
analysis_report,214320,이노션,KIND-R-1,기업분석보고서,이노션 분석,20260520,https://kind.krx.co.kr/report,광고 경기 점검,neutral,0.4,0.55
```

CLI 예시:

```powershell
python skills/kr-stock-obsidian-graph/scripts/build_kr_stock_graph.py --kind-snapshots reports/stock_graph/kind_snapshots.csv
```

## BIGKinds snapshots

BIGKinds 뉴스검색/분석 또는 Open API 결과는 `snapshot_type`으로 구분해 넣는다. 기사, 개체명, 키워드 후보를 Evidence로 보존하고 종목에는 이벤트 노출로 연결한다. 뉴스는 공식 사실이 아니라 증거 레이어이므로 `confidence`를 낮게 시작하고 다른 원천과 교차확인하는 전제가 맞다.

지원 타입:

| snapshot_type | 최소 필드 | 생성 관계 |
|---|---|---|
| `article_event` | `stock_code`, `article_id` 또는 `title` | `event -> stock` `positive_exposure`/`negative_exposure`/`has_event` |
| `entity_mention` | `stock_code`, `entity` 또는 `article_id` | `event -> stock` + `event -> evidence` |
| `keyword_signal` | `stock_code`, `keyword` 또는 `article_id` | `event -> stock` + `event -> evidence` |

CSV 예시:

```csv
snapshot_type,stock_code,stock_name,article_id,title,published_at,url,summary,topic,keyword,entity,sentiment,weight,confidence
article_event,005930,삼성전자,BK-1,삼성전자 HBM 증설,20260522,https://bigkinds.or.kr/a,HBM 투자 확대,HBM,HBM,삼성전자,positive,0.7,0.62
entity_mention,000660,SK하이닉스,BK-2,SK하이닉스 공급망,20260521,https://bigkinds.or.kr/b,공급망 점검,공급망,반도체,SK하이닉스,neutral,0.4,0.55
```

CLI 예시:

```powershell
python skills/kr-stock-obsidian-graph/scripts/build_kr_stock_graph.py --bigkinds-snapshots reports/stock_graph/bigkinds_snapshots.csv
```

## Paid provider snapshots

FnGuide/DataGuide/QuantiWise/DeepSearch/Finorma 같은 계약형 데이터는 원문 전문을 그래프에 넣지 않고, 컨센서스 지표·리포트 신호·정제 관계만 넣는다. 실제 API 직접 호출은 계약서와 레이아웃 확인이 필요하지만, 받은 파일은 `--provider-snapshots`로 바로 반영할 수 있다.

지원 타입:

| snapshot_type | 최소 필드 | 생성 관계 |
|---|---|---|
| `consensus` | `provider`, `stock_code`, `source_id`, `metric` | `stock -> provider_metric` `has_consensus_metric` |
| `broker_report` | `provider`, `stock_code`, `source_id`, `title` | `provider_report -> stock` `positive_exposure`/`negative_exposure`/`has_event` |
| `provider_relation` | `provider`, `stock_code`, `target_stock_code`, `rel_type` | `stock -> stock` `supplies_to`/`related_stock` 등 |

CSV 예시:

```csv
snapshot_type,provider,stock_code,stock_name,source_id,title,published_at,url,metric,value,target_price,rating,rel_type,target_stock_code,sign,weight,confidence
consensus,DataGuide,005930,삼성전자,DG-1,삼성전자 컨센서스,20260522,,12m_forward_per,9.8,95000,BUY,,,+,0.7,0.8
broker_report,QuantiWise,000660,SK하이닉스,QW-1,SK하이닉스 리포트,20260521,https://example.com/qw,투자의견,BUY,310000,BUY,,,+,0.6,0.75
provider_relation,DeepSearch,095340,ISC,DS-1,ISC 공급망,20260520,https://example.com/ds,,,,,supplies_to,005930,+,0.8,0.7
```

CLI 예시:

```powershell
python skills/kr-stock-obsidian-graph/scripts/build_kr_stock_graph.py --provider-snapshots reports/stock_graph/provider_snapshots.csv
```

## KRX Data Marketplace snapshots

KRX Data Marketplace에서 받은 업종분류, 지수구성종목, ETF PDF/편입종목 파일은 `snapshot_type`으로 구분해 넣는다. CSV/TSV/JSON을 지원하고, `snapshot_type`이 비어 있어도 컬럼 조합으로 일부 자동 추론한다.

지원 타입:

| snapshot_type | 최소 필드 | 생성 관계 |
|---|---|---|
| `industry_classification` | `stock_code`, `industry_name` | `stock -> industry` `classified_as` |
| `index_constituent` | `stock_code`, `index_name` 또는 `index_code` | `stock -> index` `member_of` |
| `etf_holding` | `stock_code`, `etf_code` 또는 `etf_name` | `etf -> stock` `holds` |

CSV 예시:

```csv
snapshot_type,stock_code,stock_name,index_name,index_code,etf_code,etf_name,weight,industry_name,industry_system,basis_date
index_constituent,005930,삼성전자,코스피 200,1028,,,31.2,,,20260522
etf_holding,000660,SK하이닉스,,,069500,KODEX 200,6.4,,,20260522
industry_classification,214320,이노션,,,,,,광고,KRX 업종,20260522
```

CLI 예시:

```powershell
python skills/kr-stock-obsidian-graph/scripts/build_kr_stock_graph.py --krx-marketplace-snapshots reports/stock_graph/krx_marketplace_snapshots.csv
```

## SEIBro / KSD snapshots

SEIBro 오픈플랫폼 또는 KSD GW에서 받은 권리/배당, 증권대차, 보호예수 해제 파일은 `snapshot_type`으로 구분해 넣는다. CSV/TSV/JSON을 지원하고, 권리성 이벤트는 투자지표 포함 프리셋과 공식 사실 그래프에 같이 표시된다.

지원 타입:

| snapshot_type | 최소 필드 | 생성 관계 |
|---|---|---|
| `dividend_right` | `stock_code`, `event_type` 또는 `event_date` | `stock -> rights_event` `has_rights_event` |
| `securities_lending` | `stock_code`, `quantity` 또는 `ratio` | `stock -> rights_event` `has_lending_signal` |
| `lockup_release` | `stock_code`, `event_date` 또는 `quantity` | `stock -> rights_event` `has_lockup_release` |

CSV 예시:

```csv
snapshot_type,stock_code,stock_name,event_type,event_date,quantity,amount,ratio,source_system,source_id,title,url
dividend_right,005930,삼성전자,현금배당,20260522,,1444,2.1,SEIBRO,div-1,삼성전자 배당,https://example.com/div
securities_lending,000660,SK하이닉스,대차잔고,20260522,1234567,,1.4,KSD_GW,slb-1,SK하이닉스 대차잔고,
lockup_release,214320,이노션,보호예수해제,20260522,100000,,0.9,SEIBRO,lock-1,이노션 보호예수,
```

CLI 예시:

```powershell
python skills/kr-stock-obsidian-graph/scripts/build_kr_stock_graph.py --ksd-seibro-snapshots reports/stock_graph/ksd_seibro_snapshots.csv
```

## supplemental-events format

JSON 배열 또는 CSV/TSV를 사용할 수 있다. 최소 필드는 아래와 같다.

```json
[
  {
    "source_system": "BIGKINDS",
    "source_id": "article-1",
    "event_type": "HBM 수혜",
    "target_stock_code": "005930",
    "sign": "positive",
    "weight": 0.7,
    "confidence": 0.6,
    "title": "HBM 투자 확대",
    "url": "https://example.com/article"
  }
]
```

CLI 예시:

```powershell
python skills/kr-stock-obsidian-graph/scripts/build_kr_stock_graph.py --supplemental-events reports/stock_graph/kind_events.csv --supplemental-events reports/stock_graph/bigkinds_events.json
```

## supplemental-relations format

KIND, SEIBro/KSD, BIGKinds, 리포트, 유료 벤더, 수동 검토 결과에서 확인한 공급망·고객사·권리·지분 관계를 일반 관계로 넣을 수 있다.

```json
{
  "relations": [
    {
      "source_system": "KIND",
      "source_id": "report-1",
      "rel_type": "supplies_to",
      "source_stock_code": "095340",
      "target_stock_code": "005930",
      "sign": "positive",
      "weight": 0.8,
      "confidence": 0.7,
      "title": "삼성전자 공급망 보고서",
      "url": "https://example.com/report"
    }
  ]
}
```

CLI 예시:

```powershell
python skills/kr-stock-obsidian-graph/scripts/build_kr_stock_graph.py --supplemental-relations reports/stock_graph/supply_chain_relations.csv
```
