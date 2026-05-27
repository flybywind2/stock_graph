# Data Source Access Requirements

생성일: 2026-05-21

이 문서는 현재 그래프 파이프라인이 직접 호출하는 데이터와, 아직 직접 API로 연결하지 못해 파일 import 또는 별도 인증이 필요한 데이터를 구분한다.

## 현재 직접 호출

| Source | Environment key | Access | Used for |
|---|---|---|---|
| KRX Open API | `KRX_OPEN_API_KEY` | KRX Open API 이용신청 및 `AUTH_KEY` 헤더 | KOSPI/KOSDAQ 일별매매, 종목기본정보, 지수, ETF |
| OpenDART | `DART_OPEN_API_KEY` | OpenDART 인증키 | corpCode, 공시목록, 원문, 기업개황, 주요계정, 최대주주, 임원, 타법인출자 |
| data.go.kr 금융위원회 | `DATA_GO_KR_SERVICE_KEY` | 공공데이터포털 활용신청 | KRX 상장종목정보, 기업기본정보, 기업 재무정보 |
| data.go.kr 공정거래위원회 | `DATA_GO_KR_SERVICE_KEY` | 공공데이터포털 활용신청 | 대규모기업집단, 소속회사, 참여업종, 재무현황 |
| Naver Finance | 없음 | 공개 페이지 캐시 | 테마 그룹 보강 |
| FnGuide public page | 없음 | 공개 페이지 캐시 | 섹터, 업종, PER/PBR/배당 보강 |

## 아직 직접 API 미연결

| Source | 필요한 조치 | 현재 반영 방법 |
|---|---|---|
| KIND | 공시/IR/기업분석 보고서 다운로드 경로 또는 API/엑셀 export 규격 확정 | `--supplemental-events` JSON/CSV/TSV로 이벤트/증거 import |
| SEIBro / KSD | 오픈플랫폼 또는 KSD GW 서비스별 승인, 레이아웃 확인, 상업적 이용 가능 여부 확인 | 배당, 보호예수, 대차, 권리 이벤트를 supplemental event 또는 별도 CSV로 import 예정 |
| BIGKinds | Open API 이용 신청 및 호출 제한 확인 | 기사/개체명/이벤트 후보를 `--supplemental-events`로 import |
| KRX Data Marketplace 웹 다운로드 | 필요한 통계 메뉴의 다운로드 파일 포맷 고정 | 업종분류, 지수구성, ETF PDF 같은 스냅샷 CSV import 예정 |
| 유료 FnGuide/DataGuide/QuantiWise | 계약 및 데이터 사용권 확인 | 컨센서스, 정제 공급망, 리포트 edge 보강용 |
| DeepSearch / Finorma | 계약 및 API key 발급 | 뉴스/문서/공급망 후보 보강용 |

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
