---
title: API Reference

language_tabs: # must be one of https://github.com/rouge-ruby/rouge/wiki/List-of-supported-languages-and-lexers
  - python

toc_footers:
  - <a href='#'>신영증권 미래금융팀</a>

includes:
  - errors

search: true

code_clipboard: true

meta:
  - name: description
    content: Documentation for the Kittn API
---


# Introduction

로보애널리스트 미국 주식 [종목 분석]&[스크리너] API 정의 문서입니다.

[개발계](dev-ra.shinyoung.com/api)


# Batch
## global_stock_batch

신규 추가 목록

`get_screener_market_data`

`get_stock_daily`

`koscom.robo_analyst.analysis.g1_stock_screener.global_screener_data.get_screener_market_data`

`koscom.robo_analyst.analysis.g1_stock_screener.global_screener_data.get_stock_daily`

### Query Parameters

Parameter | type  | Description
--------- |-------| -----------
sess_presto | Session | Presto 세션
sess_mysql | Session  | MySQL 세션
| |
| |


# [종목 분석]

# 기본 정보

type | API명                                                   | 설명
---- |--------------------------------------------------------| -----------
POST | business_summary_us                                    | 기업 개요, 현황 정보
POST | chartbook_us                                           | 차트북
POST | correlation_company_graph_info_us                      | 연관 기업 분석 그래프DB 
POST | correlation_company_graph_table_us                     | 연관 기업 분석 그래프DB
POST | correlation_price_us                                   | 경제지표 상관관계 - 주가
POST | financial_statement_us                                 | 재무제표 통합 API
POST | financial_statement_anomaly_detection_us               | 이상치탐색 (Anomaly Detection)
POST | financial_statement_anomaly_detection_detail_graph_us  | 이상치탐색 데이터 상세 조회
POST | financial_statement_anomaly_detection_range_graph_us   | 이상치탐색 데이터 상세 조회
POST | financial_summary_us                                   | 재무제표 실적 요약
POST | overview_us                                            | 기본 정보
POST | radar_financial_us                                     | 레이더 차트
POST | radar_financial_average_us                             | 업종 평균 레이더 차트





## overview_us

기본 정보/s12_us_stock/overview_us

> payload:

```json
{
  "node_id_stock": "3|2|1|1|AAPL",
  "start_date": "20190101",
  "end_date": "20200630"
}
```

> Response:

```json
{
  "result": {
    "chart": {
      "series": [
        {
          "data": [
            [1546387200000, 39.48],
            [..., ...],
            [1593475200000, 91.2]
          ],
          "name": "애플 (USD)",
          "step": false,
          "type": "line",
          "yAxisIndex": 0
        }
      ]
    },
    "key_value": {
      "52주최고": 198.23,
      "52주최고 날짜": "20230719",
      "52주최저": 124.17,
      "52주최저 날짜": "20230103",
      "EPS": 5.8968,
      "INDEX_NAME": "나스닥 증권거래소",
      "PBR": 48.55289,
      "PER": 32.8348,
      "symbol": "AAPL",
      "기준가": 192.75,
      "기준일": "20230725",
      "등락": 0.87,
      "등락률": 0.4514,
      "로이터 업종": "컴퓨터, 전화 및 가전제품",
      "배당수익률(시가)": 0.4981,
      "상장주식수": 15728702000,
      "시가총액": 3031707310500,
      "자본금": 0.15723,
      "자본잉여금": 69567.84277,
      "종가": 193.62
    }
  }
}
```

### Query Parameters

Parameter | type    | Description
--------- |---------| -----------
sess_presto | Session | Presto 세션
sess_mysql | Session | MySQL 세션
node_id_stock| str     | 종목 node id
start_date| str     | 차트 조회 시작일
end_date| str | 차트 조회 종료일


<img src="/Users/yeseul/PycharmProjects/slate/source/images/overview_chart.png" title="overview_chart">
![overview_chart](/Users/yeseul/PycharmProjects/slate/source/images/overview_chart.png)
<p align="center"><img src="/Users/yeseul/PycharmProjects/slate/source/images/overview_chart.png" width=700 alt="overview_chart"></p>


## business_summary_us
기업 개요, 현황 정보/s12_us_stock/business_summary_us

> payload:

```json
{
  "node_id_stock": "3|2|1|1|AAPL"
}
```

> Response:

```json
{
   "result": {
    "overview": "애플은 스마트폰, 개인용 컴퓨터, 태블릿, 웨어러블 및 액세서리를 설계, 제조, 판매하는 회사이다. 이 회사의 제품에는 iPhone, Mac, iPad, 웨어러블, 홈, 액세서리가 있다. 이 회사의 iPhone은 iOS 운영 체제를 기반으로 하는 스마트폰 제품군이다.  이 회사의 Mac은 macOS 운영 체제를 기반으로 하는 개인용 컴퓨터 제품군이다. 이 회사의 iPad는 iPadOS 운영 체제를 기반으로 하는 다목적 태블릿 제품군이다. 이 회사의 웨어러블, 홈 및 액세서리에는 AirPods, Apple TV, Apple Watch, Beats 제품, HomePod, iPod touch, 기타 Apple 브랜드 및 타사 액세서리가 포함된다. 이 회사의 AirPod은 Siri와 상호 작용하는 무선 헤드폰이다. 이 회사의 Apple Watch는 스마트 워치 라인이다. 이 회사의 서비스에는 광고, AppleCare, 클라우드 서비스, 디지털 콘텐츠, 지불 서비스가 포함된다. 이 회사의 고객으로는 주로 일반 소비자, 중소기업, 교육, 기업 및 정부 등이 있다.",
    "symbol": "AAPL"
  }
}
```

### Query Parameters

Parameter | type    | Description
--------- |---------| -----------
sess_presto | Session | Presto 세션
sess_mysql | Session | MySQL 세션
node_id_stock| str     | 종목 node id


## radar_chart
종목 한눈에 보기

### Query Parameters

Parameter | type    | Description
--------- |---------| -----------
sess_mysql | Session | MySQL 세션
node_id_stock| str     | 종목 node id

> <img src="/Users/yeseul/PycharmProjects/slate/source/images/radar_chart.png" title="radar_chart">



# 주요 산업 지표


# 상관관계



# Financial Highlight



# 주주 정보


# Company graph DB


# [스크리너]

# Authentication

> To authorize, use this code:

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
```

```shell
# With shell, you can just pass the correct header with each request
curl "api_endpoint_here" \
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
```

> Make sure to replace `meowmeowmeow` with your API key.

Kittn uses API keys to allow access to the API. You can register a new Kittn API key at our [developer portal](http://example.com/developers).

Kittn expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: meowmeowmeow`

<aside class="notice">
You must replace <code>meowmeowmeow</code> with your personal API key.
</aside>

# Kittens

## Get All Kittens

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get()
```

```shell
curl "http://example.com/api/kittens" \
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let kittens = api.kittens.get();
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 1,
    "name": "Fluffums",
    "breed": "calico",
    "fluffiness": 6,
    "cuteness": 7
  },
  {
    "id": 2,
    "name": "Max",
    "breed": "unknown",
    "fluffiness": 5,
    "cuteness": 10
  }
]
```

This endpoint retrieves all kittens.

### HTTP Request

`GET http://example.com/api/kittens`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
include_cats | false | If set to true, the result will also include cats.
available | true | If set to false, the result will include kittens that have already been adopted.

<aside class="success">
Remember — a happy kitten is an authenticated kitten!
</aside>

## Get a Specific Kitten

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get(2)
```

```shell
curl "http://example.com/api/kittens/2" \
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.get(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "name": "Max",
  "breed": "unknown",
  "fluffiness": 5,
  "cuteness": 10
}
```

This endpoint retrieves a specific kitten.

<aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>

### HTTP Request

`GET http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to retrieve

## Delete a Specific Kitten

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.delete(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.delete(2)
```

```shell
curl "http://example.com/api/kittens/2" \
  -X DELETE \
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.delete(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "deleted" : ":("
}
```

This endpoint deletes a specific kitten.

### HTTP Request

`DELETE http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to delete

