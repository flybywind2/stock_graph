# External API Env Template

이 파일은 `EXTERNAL_DEPENDENCY_AUDIT.json`의 남은 credential/endpoint gap에서 생성한 `.env` 입력 템플릿이다. 실제 secret 값은 기록하지 않는다.

## Keys

| Key | Purpose |
|---|---|
| EXTERNAL_API_CONFIG | Optional JSON file overriding source URLs, key names, and params |
| BIGKINDS_API_KEY | BIGKinds configured direct API credential |
| BIGKINDS_API_URL | BIGKinds configured direct API endpoint |
| DATA_GO_KR_SERVICE_KEY | data.go.kr fallback credential for SEIBro/KSD-style configured APIs |
| FSC_STOCK_DIVIDEND_URL | Configured external API value |
| FSC_STOCK_ISSUE_URL | Configured external API value |
| KIND_API_KEY | KIND configured direct API credential |
| KIND_API_URL | KIND configured direct API endpoint |
| SEIBRO_API_KEY | SEIBro configured direct API credential |
| KSD_API_KEY | KSD GW configured direct API credential |
| SEIBRO_API_URL | SEIBro configured direct API endpoint |
| KSD_API_URL | KSD configured direct API endpoint |
| FNGUIDE_API_KEY | FnGuide provider credential |
| DATAGUIDE_API_KEY | DataGuide provider credential |
| QUANTIWISE_API_KEY | QuantiWise provider credential |
| DEEPSEARCH_API_KEY | DeepSearch provider credential |
| FINORMA_API_KEY | Finorma provider credential |
| PROVIDER_API_URL | Configured paid provider endpoint |

## Template

```dotenv
# Fill these values in .env to enable configured external direct APIs.
# Secret values are intentionally omitted from generated reports.

EXTERNAL_API_CONFIG=
BIGKINDS_API_KEY=
BIGKINDS_API_URL=
DATA_GO_KR_SERVICE_KEY=
FSC_STOCK_DIVIDEND_URL=
FSC_STOCK_ISSUE_URL=
KIND_API_KEY=
KIND_API_URL=
SEIBRO_API_KEY=
KSD_API_KEY=
SEIBRO_API_URL=
KSD_API_URL=
FNGUIDE_API_KEY=
DATAGUIDE_API_KEY=
QUANTIWISE_API_KEY=
DEEPSEARCH_API_KEY=
FINORMA_API_KEY=
PROVIDER_API_URL=
```
