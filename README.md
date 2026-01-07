# Google Trends Scraper API

[![Promo](https://github.com/luminati-io/LinkedIn-Scraper/blob/main/Proxies%20and%20scrapers%20GitHub%20bonus%20banner.png)](https://brightdata.co.kr/products/serp-api/google-search/trends)

이 리포지토리는 Google Trends 데이터를 수집하기 위한 두 가지 접근 방식을 제공합니다:

1. **무료 스크레이퍼:** 소규모 프로젝트, 테스트, 개인 연구 및 교육 목적을 위한 가벼운 솔루션입니다.
2. **[Bright Data Google Trends Scraper API](https://brightdata.co.kr/products/serp-api/google-search/trends):** 엔터프라이즈 수준의 확장 가능하고 신뢰할 수 있는 데이터 추출을 위한 견고한 대용량 솔루션입니다.

## Table of Contents
- [Free Scraper](#free-scraper)
  - [Setup](#setup)
  - [Quick Start](#quick-start)
  - [Sample Output](#sample-output)
  - [Limitations](#limitations)
- [Bright Data Enterprise Solution](#bright-data-enterprise-solution)
  - [Getting Started](#getting-started)
  - [Direct API Access](#direct-api-access)
  - [Native Proxy-Based Access](#native-proxy-based-access)
- [Advanced Features](#advanced-features)
  - [Widgets](#widgets)
  - [Geographic Filtering](#geographic-filtering)
  - [Localization](#localization)
  - [Time Range](#time-range)
  - [Category Filtering](#category-filtering)
  - [Search Type](#search-type)
- [Support & Resources](#support--resources)

## Free Scraper

<img width="700" alt="bright-data-google-trends-api-screenshot-google-trends-page" src="https://github.com/luminati-io/google-trends-api/blob/main/images/418445062-2168a20d-a588-454e-a682-a6bba3e4e460.png" />

소규모 데이터 수집 프로젝트를 위한 간단한 Google Trends 스크레이퍼입니다.


### Setup

**요구 사항:**
- Python 3.9+
- Playwright (브라우저 자동화용)

**설치:**
```bash
pip install playwright
playwright install
```

> **Webスクレイピング이 처음이신가요?** 당사의 [Python으로 하는 web scraping 초보자 가이드](https://brightdata.co.kr/blog/how-tos/web-scraping-with-python)를 따라 해보시기 바랍니다.
>

### Quick Start
1. [google-trends-scraper.py](https://github.com/luminati-io/Google-Trends-Scraper-API/blob/main/google-trends-scraper/google-trends-scraper.py)에서 다음 변수를 편집합니다:
```python
query = "cryptocurrency"  # Your search term
geo = "US"                # Country code
hl = "en-US"              # Language code
```
2. 스크립트를 실행합니다

💡 **Pro Tip:** Google의 anti-scraping 시스템에 의한 탐지를 줄이려면 `HEADLESS = False`로 설정하십시오.

### Sample Output
```json
{
    "geoCode": "US-DC",
    "geoName": "District of Columbia",
    "value": [100],
    "formattedValue": ["100"],
    "maxValueIndex": 0,
    "hasData": [true],
}
```

👉 [전체 JSON 출력](https://github.com/luminati-io/Google-Trends-Scraper-API/tree/main/google-trends-results)을 확인하십시오.


### Limitations
무료 스크레이퍼에는 다음과 같은 한계가 있습니다:
- IP 차단 위험이 높습니다
- 리クエスト 볼륨이 제한적입니다
- CAPTCHA가 자주 발생합니다
- 대규모 スクレイピング에는 신뢰하기 어렵습니다

신뢰할 수 있는 대규모 スクレイピング을 위해서는 더 고급 솔루션이 필요합니다.

## Bright Data Enterprise Solution
[Bright Data의 Google Trends API](https://brightdata.co.kr/products/serp-api/google-search/trends)는 사용자 지정 가능한 검색 パラメータ와 함께 구조화된 Google Trends 데이터를 제공합니다. [SERP API](https://brightdata.co.kr/products/serp-api)와 동일한 고급 기술을 기반으로 다음을 제공합니다:

- **글로벌 위치 정확도:** 어떤 위치에도 결과를 맞춤 설정할 수 있습니다
- **Pay-Per-Success Model**: 성공한 리クエスト에 대해서만 비용을 지불합니다
- **실시간 데이터**: 최신 검색 결과를 몇 초 만에 가져옵니다
- **확장성**: 볼륨 제한 없이 무제한 리クエスト를 처리합니다
- **비용 효율성**: 인프라 및 유지보수 비용을 절감합니다
- **최고의 신뢰성**: 내장된 anti-blocking 조치로 일관된 성능을 제공합니다
- **기술 지원**: 필요 시 전문가 지원을 받을 수 있습니다


### Getting Started

1. **사전 준비**:
    - [Bright Data 계정](https://brightdata.co.kr/)을 생성합니다(신규 사용자는 $5 크레딧 제공)
    - [API key](https://docs.brightdata.com/general/account/api-token)를 발급받습니다
2. **Setup**: API를 통합하려면 당사의 [단계별 가이드](https://github.com/luminati-io/Google-Trends-Scraper-API/blob/main/setup-serp-api-guide.md)를 따르십시오
3. **구현 방식**:
    - Direct API Access
    - Native Proxy-Based Access


### Direct API Access

API 엔드포인트에 직접 리クエスト합니다:

**cURL 예시:**

```bash
curl https://api.brightdata.com/request \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer API_TOKEN" \
  -d '{
        "zone": "ZONE_NAME",
        "url": "https://trends.google.com/trends/explore?q=coffee&geo=GB&brd_trends=timeseries,geo_map&brd_json=1",
        "format": "raw"
      }'

```

**Python 예시:**

```python
import requests
import json

url = "https://api.brightdata.com/request"
headers = {"Content-Type": "application/json", "Authorization": "Bearer API_TOKEN"}

payload = {
    "zone": "ZONE_NAME",
    "url": "https://trends.google.com/trends/explore?q=coffee&geo=GB&brd_trends=timeseries,geo_map&brd_json=1",
    "format": "raw",
}

response = requests.post(url, headers=headers, json=payload)

with open("serp_direct_api.json", "w") as file:
    json.dump(response.json(), file, indent=4)

print("Response saved to 'serp_direct_api.json'.")

```

👉 [전체 JSON 출력](https://github.com/luminati-io/Google-Trends-Scraper-API/blob/main/google-trends-api-results/serp_direct_api.json)을 확인하십시오.

> **참고:** 파싱된 JSON을 위해 `brd_json=1`을 사용하십시오. `geo` 및 `brd_trends`와 같은 추가 パラメータ는 아래 Advanced Features 섹션에서 설명합니다.
> 

### Native Proxy-Based Access

프로キシ 라우팅 방식도 사용할 수 있습니다:

**cURL 예시:**

```bash
curl -i \
  --proxy brd.superproxy.io:33335 \
  --proxy-user "brd-customer-<customer-id>-zone-<zone-name>:<zone-password>" \
  -k \
  "https://trends.google.com/trends/explore?q=coffee&geo=GB&brd_trends=timeseries,geo_map&brd_json=1"

```

**Python 예시:**

```python
import requests
import urllib3

urllib3.disable_warnings(urllib3.exceptions.InsecureRequestWarning)

host = "brd.superproxy.io"
port = 33335
username = "brd-customer-<customer-id>-zone-<zone-name>"
password = "<zone-password>"
proxy_url = f"http://{username}:{password}@{host}:{port}"

proxies = {"http": proxy_url, "https": proxy_url}
url = "https://trends.google.com/trends/explore?q=coffee&geo=GB&brd_trends=timeseries,geo_map&brd_json=1"
response = requests.get(url, proxies=proxies, verify=False)

with open("serp_native_proxy.json", "w", encoding="utf-8") as file:
    file.write(response.text)

print("Response saved to 'serp_native_proxy.json'.")

```

👉 [전체 JSON 출력](https://github.com/luminati-io/Google-Trends-Scraper-API/blob/main/google-trends-api-results/serp_native_proxy.json)을 확인하십시오.

> **참고:** 프로덕션 환경에서는 당사의 [SSL Certificate Guide](https://docs.brightdata.com/general/account/ssl-certificate)에 설명된 대로 Bright Data의 SSL 인증서를 로드하십시오.
>

## Advanced Features

### Widgets
<img width="700" alt="bright-data-google-trends-api-screenshot-timeseries-and-geomap" src="https://github.com/luminati-io/google-trends-api/blob/main/images/418487699-20fd3ec5-b152-4e70-bee3-b093b7d78b86.png" />

Google Trends는 의미 있는 인사이트를 추출하기 위한 다양한 위젯을 제공합니다. `brd_trends` パラメータ를 사용하여 원하는 위젯을 지정할 수 있습니다:

**사용 가능한 위젯:**

- `timeseries` → 시간 경과에 따른 관심도
- `geo_map` → 하위 지역별 관심도

**여러 위젯 사용:**

쉼표로 구분하여 여러 위젯을 조합할 수 있습니다:

```bash
curl --proxy brd.superproxy.io:33335 \
  --proxy-user brd-customer-<customer-id>-zone-<zone-name>:<zone-password> \
  -k "https://trends.google.com/trends/explore?q=ChatGPT&geo=US&brd_trends=timeseries,geo_map&brd_json=1"
```


### Geographic Filtering
`geo` パ라メータ를 사용하면 특정 국가의 검색 트렌드 데이터를 필터링할 수 있습니다(예: 미국은 `geo=US`). 생략하면 API는 기본적으로 글로벌 트렌드를 반환합니다.

**예시:**

```bash
curl --proxy brd.superproxy.io:33335 \
  --proxy-user brd-customer-<customer-id>-zone-<zone-name>:<zone-password> \
  -k "https://trends.google.com/trends/explore?q=coffee&geo=GB&brd_trends=timeseries,geo_map&brd_json=1"
```

### Localization
<img width="700" alt="bright-data-google-trends-api-screenshot-set-language" src="https://github.com/luminati-io/google-trends-api/blob/main/images/418515025-d68f07f2-8a6a-46ef-942a-38b2813268dd.png" />

`hl` パ라메ータ를 사용하면 특정 언어로 검색 트렌드 데이터를 가져올 수 있습니다:

- 언어 코드(예: `en-US`, `fr-FR`)를 허용합니다
- 이는 반환되는 데이터의 언어에 영향을 주며, 실제 검색 결과에는 영향을 주지 않습니다

**예시:**

```bash
curl --proxy brd.superproxy.io:33335 \
  --proxy-user brd-customer-<customer-id>-zone-<zone-name>:<zone-password> \
  -k "https://trends.google.com/trends/explore?q=coffee&hl=fr-FR&brd_trends=timeseries,geo_map&brd_json=1"
```

### Time Range

`date` パ라메ータ는 트렌드 데이터를 가져오기 위한 특정 기간을 정의합니다:

| **Value** | **Time Range** |
| --- | --- |
| now 1-H | 지난 1시간 |
| now 4-H | 지난 4시간 |
| now 1-d | 지난 1일(24시간) |
| now 7-d | 지난 7일 |
| today 1-m | 지난 30일 |
| today 3-m | 지난 90일 |
| today 12-m | 지난 12개월(기본값) |
| today 5-y | 지난 5년 |
| YYYY-MM-DD YYYY-MM-DD | 사용자 지정 날짜 범위 |

**지난 30일 예시:**

```bash
curl --proxy brd.superproxy.io:33335 \
  --proxy-user brd-customer-<customer-id>-zone-<zone-name>:<zone-password> \
  -k "https://trends.google.com/trends/explore?q=coffee&date=today+1-m&brd_trends=timeseries,geo_map&brd_json=1"
```

**사용자 지정 날짜 범위 예시:**

```bash
curl --proxy brd.superproxy.io:33335 \
  --proxy-user brd-customer-<customer-id>-zone-<zone-name>:<zone-password> \
  -k "https://trends.google.com/trends/explore?q=coffee&date=2025-01-02+2025-03-03&brd_trends=timeseries,geo_map&brd_json=1"
```

### Category Filtering

`cat` パ라메ータ를 사용하면 특정 카테고리 내에서 검색 트렌드를 좁힐 수 있습니다:

- 기본적으로 Google Trends는 모든 카테고리에서 검색합니다
- 카테고리는 숫자 ID로 표시됩니다
- [Google Trends](https://trends.google.com/trends/api/explore/pickers/category?lang=en-US&tz=240)에서 카테고리 ID 전체 목록을 확인할 수 있습니다

예시 – 비즈니스 및 산업 카테고리(cat=12)에서 “Bitcoin” 트렌드를 가져옵니다:

```bash
curl --proxy brd.superproxy.io:33335 \
  --proxy-user brd-customer-<customer-id>-zone-<zone-name>:<zone-password> \
  -k "https://trends.google.com/trends/explore?q=bitcoin&cat=12&brd_trends=timeseries,geo_map&brd_json=1"
```

### Search Type

`gprop`(Google Property) パ라메ータ는 특정 Google 서비스별로 검색 트렌드를 필터링합니다:

| **Value** | **Google Property** |
| --- | --- |
| images | Google Images |
| news | Google News |
| froogle | Google Shopping |
| youtube | YouTube Search |

생략하면 웹 검색이 기본값입니다.

**예시:**

1. **이미지 검색 트렌드 (gprop=images):**

```bash
curl --proxy brd.superproxy.io:33335 \
  --proxy-user brd-customer-<customer-id>-zone-<zone-name>:<zone-password> \
  -k "https://trends.google.com/trends/explore?q=nft+art&gprop=images&brd_trends=timeseries,geo_map&brd_json=1"
```

2. 뉴스 검색 트렌드 (gprop=news):

```bash
curl --proxy brd.superproxy.io:33335 \
  --proxy-user brd-customer-<customer-id>-zone-<zone-name>:<zone-password> \
  -k "https://trends.google.com/trends/explore?q=AI+advancements&gprop=news&brd_trends=timeseries,geo_map&brd_json=1"

```

3. YouTube 검색 트렌드 (gprop=youtube):

```bash
curl --proxy brd.superproxy.io:33335 \
  --proxy-user brd-customer-<customer-id>-zone-<zone-name>:<zone-password> \
  -k "https://trends.google.com/trends/explore?q=python+tutorials&gprop=youtube&brd_trends=timeseries,geo_map&brd_json=1"

```

## Support & Resources

- **Documentation**: [SERP API Docs](https://docs.brightdata.com/scraping-automation/serp-api/)
- **SEO Use Cases**: [SEO Tracking and Insights](https://brightdata.co.kr/use-cases/serp-tracking)
- **Additional Guides**:
    - [SERP API](https://github.com/luminati-io/serp-api)
    - [Google Search API](https://github.com/luminati-io/google-search-api)
    - [Web Unlocker API](https://github.com/luminati-io/web-unlocker-api)
    - [Google News Scraper](https://github.com/luminati-io/Google-News-Scraper)
- **Technical Articles**:
    - [Best SERP APIs](https://brightdata.co.kr/blog/web-data/best-serp-apis)
    - [Build a RAG Chatbot with SERP API](https://brightdata.co.kr/blog/web-data/build-a-rag-chatbot)
    - [How to Scrape Google Trends with Python](https://brightdata.co.kr/blog/web-data/how-to-scrape-google-trends)
- **Technical Support**: [Contact Us](mailto:support@brightdata.com)