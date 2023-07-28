---
title: API Reference

language_tabs: # must be one of https://github.com/rouge-ruby/rouge/wiki/List-of-supported-languages-and-lexers
  - python

toc_footers:
  - <a href='#'>신영증권 미래금융팀</a>

search: true

code_clipboard: true

meta:
  - name: description
    content: Documentation for the Kittn API
---


# Introduction

로보애널리스트 미국 주식 [종목 분석]&[스크리너] API 정의 문서입니다.

[개발계 swagger](dev-ra.shinyoung.com/api)


# Batch

## global_stock_batch

### 신규 추가 목록

- `get_screener_market_data`
  - BatchGlobalScreenerMarketData
  - 미국 종목 종목별 가격 변화율 저장

<br>

- `get_stock_daily`
  - BatchGlobalScreenerStockDaily
  - 미국 종목 2018.06.01 이후 가격 데이터 저장
  


# [종목 분석]

type | API명                                                   | 설명
---- |--------------------------------------------------------| -----------
POST | business_summary_us                                    | 기업 개요, 현황 정보
POST | overview_us                                            | 기본 정보
POST | radar_financial_us                                     | 레이더 차트
POST | radar_financial_average_us                             | 업종 평균 레이더 차트
POST | correlation_company_graph_info_us                      | 연관 기업 분석 그래프DB 
POST | correlation_company_graph_table_us                     | 연관 기업 분석 그래프DB
POST | chartbook_us                                           | 차트북
POST | correlation_price_us                                   | 경제지표 상관관계 - 주가
POST | financial_summary_us                                   | 재무제표 실적 요약
POST | financial_statement_anomaly_detection_us               | 이상치탐색 
POST | financial_statement_anomaly_detection_detail_graph_us  | 이상치탐색 데이터 상세 조회
POST | financial_statement_anomaly_detection_range_graph_us   | 이상치탐색 데이터 상세 조회
POST | financial_statement_us                                 | 재무제표 통합 API


# 기본 정보

## overview_us

### 화면 예시
<p align="center"><img src="/Users/yeseul/PycharmProjects/slate/source/images/overview.png" width=700 alt="overview"></p>

### Request URL
`http://dev-ra.shinyoung.com/api/s12_us_stock/overview_us`

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
{"result": {"chart": {
      "series": [{
          "data": [[1546387200000, 39.48], [..., ...], [1593475200000, 91.2]],
          "name": "애플 (USD)", "step": false, "type": "line", "yAxisIndex": 0
        }]},
    "key_value": {
      "52주최고": 198.23, "52주최고 날짜": "20230719",
      "52주최저": 124.17, "52주최저 날짜": "20230103",
      "EPS": 5.8968, "INDEX_NAME": "나스닥 증권거래소", "PBR": 48.55289, "PER": 32.8348,
      "symbol": "AAPL", "기준가": 192.75, "기준일": "20230725",
      "등락": 0.87, "등락률": 0.4514,
      "로이터 업종": "컴퓨터, 전화 및 가전제품",
      "배당수익률(시가)": 0.4981, "상장주식수": 15728702000,
      "시가총액": 3031707310500, "자본금": 0.15723, "자본잉여금": 69567.84277,
      "종가": 193.62
    }
  }
}
```

### Query Parameters

 Parameter     | type    | Description 
---------------|---------|-------------
 sess_presto   | Session | Presto 세션   
 sess_mysql    | Session | MySQL 세션    
 node_id_stock | str     | 종목 node id  
 start_date    | str     | 차트 조회 시작일   
 end_date      | str     | 차트 조회 종료일   

### Chart
<p align="center"><img src="/Users/yeseul/PycharmProjects/slate/source/images/overview_chart.png" width=700 alt="overview_chart"></p>


## business_summary_us

### Request URL
`http://dev-ra.shinyoung.com/api/s12_us_stock/business_summary_us`

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

 Parameter     | type    | Description 
---------------|---------|-------------
 sess_presto   | Session | Presto 세션   
 sess_mysql    | Session | MySQL 세션    
 node_id_stock | str     | 종목 node id  


## radar_financial_us

### Request URL
`http://dev-ra.shinyoung.com/api/s12_us_stock/radar_financial_us`

레이더 차트
> payload:

```json
{
  "node_id_stock": "3|2|1|1|AAPL"
}
```
> Response:

```json
{"result": { "chart": {"radar": {
        "indicator": [
          {"max": 5, "min": 0.1, "name": "배당"},
          {"max": 5, "min": 0.1, "name": "성장성"},
          {"max": 5, "min": 0.1, "name": "모멘텀"},
          {"max": 5, "min": 0.1, "name": "수익성"},
          {"max": 5, "min": 0.1, "name": "안정성"},
          {"max": 5, "min": 0.1, "name": "밸류에이션"}]
      },
      "series": [{
          "data": [{
              "name": "애플", "value": [2, 2.5, 2, 5, 1.5, 1.5]}],
          "type": "radar"}]
    },
    "key_value": {
      "dividend": "낮은편",
      "growth": "평균수준",
      "momentum": "낮은편",
      "profitability": "매우 높은편",
      "stability": "낮은편",
      "valuation": "낮은편"
    }
  },
  "success": true
}
```

### Query Parameters

 Parameter     | type    | Description 
---------------|---------|-------------
 sess_mysql    | Session | MySQL 세션    
 node_id_stock | str     | 종목 node id  

### Chart
<img src="/Users/yeseul/PycharmProjects/slate/source/images/radar_chart.png" title="radar_chart">


## radar_financial_financial_average_us

### Request URL
`http://dev-ra.shinyoung.com/api/s12_us_stock/radar_financial_financial_average_us`

> payload:

```json
{
  "node_id_stock": "3|2|1|1|AAPL"
}
```

> Response:

```json
{"result": {"chart": {"radar": {
    "indicator": [
          {"max": 5, "min": 0.1, "name": "배당"},
          {"max": 5, "min": 0.1, "name": "성장성"},
          {"max": 5, "min": 0.1, "name": "모멘텀"},
          {"max": 5, "min": 0.1, "name": "수익성"},
          {"max": 5, "min": 0.1, "name": "안정성"},
          {"max": 5, "min": 0.1, "name": "밸류에이션"}
        ]},
      "series": [{
          "data": [{
              "name": "애플", "value": [0.909091, 2.60227, 2.36364, 2.26136, 3.90909, 1.85227]}],
          "type": "radar"}]
    },
    "key_value": {
      "dividend": "매우 낮은편",
      "growth": "평균수준",
      "momentum": "평균수준",
      "profitability": "평균수준",
      "stability": "높은편",
      "valuation": "낮은편"
    }
  },
  "success": true
}
```

### Query Parameters

 Parameter     | type    | Description 
---------------|---------|-------------
 sess_mysql    | Session | MySQL 세션    
 node_id_stock | str     | 종목 node id  

### Chart
<img src="/Users/yeseul/PycharmProjects/slate/source/images/radar_chart_avg.png" title="radar_chart_avg">



## correlation_company_graph_info_us

### 화면 예시
<p align="center"><img src="/Users/yeseul/PycharmProjects/slate/source/images/company_graph_db.png" width=700 alt=company_graph_db> </p>

### Request URL
`http://dev-ra.shinyoung.com/api/s12_us_stock/correlation_company_graph_info_us`

연관 기업 분석 그래프 DB - 그래프 DB 연관 기업 분석

> payload:

```json
{
  "node_id_stock": "3|2|1|1|AAPL"
}
```

> Response:

```json
{"result": {
    "company": {"node_id": "3|2|1|1|AAPL", "종목코드": "AAPL", "회사명": "애플"},
    "keywords": {"keyword_list": [ "아이패드", "팀쿡", "스마트폰", "스티브 잡스", "애플", "아이폰", "ESG", "자율주행", "전기차"]},
    "market_type": {"시장구분": "나스닥"},
    "selected_keyword": {"keyword": "아이패드"},
    "table": {"columns": [
        {"caption": "종목코드", "dataField": "symbol", "dataType": "string"},
        {"caption": "종목명", "dataField": "name_ko_short", "dataType": "string"},
        {"caption": "시가총액(억원)", "dataField": "market_cap", "dataType": "number"},
        {"caption": "전일종가", "dataField": "price", "dataType": "number"},
        {"caption": "1D(%)", "dataField": "pct_1d", "dataType": "number"},
        {"caption": "1W(%)", "dataField": "pct_1w", "dataType": "number"},
        {"caption": "1M(%)", "dataField": "pct_1m", "dataType": "number"},
        {"caption": "3M(%)", "dataField": "pct_3m", "dataType": "number"},
        {"caption": "6M(%)", "dataField": "pct_6m", "dataType": "number"},
        {"caption": "1Y(%)", "dataField": "pct_1y", "dataType": "number"},
        {"caption": "YTD(%)", "dataField": "pct_ytd", "dataType": "number"},
        {"caption": "주요키워드", "dataField": "keywords", "dataType": "list"},
        {"caption": "국가", "dataField": "country", "dataType": "string"}
      ],
      "rows": [
        {"country": "1",
          "keywords": ["아이패드", "팀쿡", "스마트폰", "스티브 잡스", "애플", "아이폰", "ESG", "자율주행", "전기차"],
          "market_cap": 39002326, "market_cap_usd": 3045391340000,
          "name_ko_short": "애플", "node_id_stock": "3|2|1|1|AAPL",
          "pct_1d": 0.45, "pct_1m": 4.51, "pct_1w": -0.06, "pct_1y": 26.59, "pct_3m": 18.23, "pct_6m": 36.49, "pct_ytd": 54.81, "price": 194,
          "symbol": "AAPL"
        },
        {"country": "0",
          "keywords": ["스마트폰", "패키지솔루션", "테슬라카메라모듈", "카메라", "테슬라", "코로나19", "전장용MLCC", 
            "적층세라믹콘덴서", "자율주행", "아이패드", "애플", "스마트폰부품", "무선충전기", "무선충전", "車전장", "LED", "IT부품", "5G", "수동소자", "콘덴서", "MLCC", "카메라모듈"],
          "market_cap": 107633, "market_cap_usd": null,
          "name_ko_short": "삼성전기", "node_id_stock": "3|1|1|1|009150",
          "pct_1d": -3.22, "pct_1m": -0.21, "pct_1w": -5.94, "pct_1y": 1.48, "pct_3m": 3.59, "pct_6m": -1.97, "pct_ytd": 8.75, "price": 144100,
          "symbol": "009150"
        },
        {
          "...": "..."
        }],
      "table_length": 12}
  },
  "success": true
}

```

### Query Parameters

 Parameter     | type    | Description 
---------------|---------|-------------
 sess_mysql    | Session | MySQL 세션    
 node_id_stock | str     | 종목 node id  


## correlation_company_table_us

### Request URL
`http://dev-ra.shinyoung.com/api/s12_us_stock/correlation_company_table_us`

연관 기업 분석 그래프 DB - 그래프 DB 미국 연관 기업 분석 확장, 업종 삭제 & 키워드 기반


> payload:

```json
{
  "node_id_stock": "3|2|1|1|AAPL",
  "search_keywords": [
    "아이폰"
  ]
}
```

> Response:

```json
{"result": {
    "node_id_company": {"종목노드ID": "3|2|1|1|AAPL"},
    "selected_keywords": {"keywords": ["아이폰"]},
    "table": {"columns": [
        {"caption": "종목코드", "dataField": "symbol", "dataType": "string"},
        {"caption": "종목명", "dataField": "name_ko_short", "dataType": "string"},
        {"caption": "시가총액(억원)", "dataField": "market_cap", "dataType": "number"},
        {"caption": "전일종가", "dataField": "price", "dataType": "number"},
        {"caption": "1D(%)", "dataField": "pct_1d", "dataType": "number"},
        {"caption": "1W(%)", "dataField": "pct_1w", "dataType": "number"},
        {"caption": "1M(%)", "dataField": "pct_1m", "dataType": "number"},
        {"caption": "3M(%)", "dataField": "pct_3m", "dataType": "number"}, 
        {"caption": "6M(%)", "dataField": "pct_6m", "dataType": "number"},
        {"caption": "1Y(%)", "dataField": "pct_1y", "dataType": "number"},
        {"caption": "YTD(%)", "dataField": "pct_ytd", "dataType": "number"},
        {"caption": "주요키워드", "dataField": "keywords", "dataType": "list"},
        {"caption": "국가", "dataField": "country", "dataType": "string"}
      ],
      "rows": [
        {"country": "1",
          "keywords": ["아이패드", "팀쿡", "스마트폰", "스티브 잡스", "애플", "아이폰", "ESG", "자율주행", "전기차"],
          "market_cap": 39002326, "market_cap_usd": 3045391340000,
          "name_ko_short": "애플", "node_id_stock": "3|2|1|1|AAPL",
          "pct_1d": 0.45, "pct_1m": 4.51, "pct_1w": -0.06, "pct_1y": 26.59, "pct_3m": 18.23, "pct_6m": 36.49, "pct_ytd": 54.81, 
          "price": 194, "symbol": "AAPL"
        },
        {"country": "0",
          "keywords": ["마이크론", "XR", "화웨이", "헬스케어", "폴더블폰", "파운드리", "태블릿", "타이젠", "퀄컴AP", "퀄컴", "카메라모듈", "전기전자", "자율주행", "이재용", "이미지센서", "웨이퍼", "애플", "아이폰", "시스템반도체", "스마트기기", 
            "서버", "TV", "배터리폭발", "무선통신", "메타버스", "메모리반도체", "메모리", "딥러닝", "도시바", "PC", "LCD", "IT부품", "D램", "AP", "OLED", "6G", "5G", "3D낸드", "가전기기", "스마트폰", "디스플레이", "반도체"],
          "market_cap": 4166908, "market_cap_usd": null,
          "name_ko_short": "삼성전자", "node_id_stock": "3|1|1|1|005930",
          "pct_1d": -0.29, "pct_1m": -3.59, "pct_1w": -2.65, "pct_1y": 13.13, "pct_3m": 8.89, "pct_6m": 9.23, "pct_ytd": 25.77,
          "price": 69800, "symbol": "005930"
        },
        {"...":  "..."}
      ],
      "table_length": 15}
  },
  "success": true
}
```

### Query Parameters

 Parameter       | type    | Description 
-----------------|---------|-------------
 sess_mysql      | Session | MySQL 세션    
 node_id_stock   | str     | 종목 node id  
 search_keywords | list    | 검색 키워드 리스트  


# 주요 산업 지표

## 주요 산업 지표

### Request URL
`http://dev-ra.shinyoung.com/api/s12_us_stock/chartbook_us`

종목이 소속된 업종(로이터->WI26매칭)의 차트북 반환

> payload:

```json
{
  "node_id_stock": "3|2|1|1|AAPL"
}
```

> Response:

```json
{"result": {
    "chartbook": [{
        "book_id": 16, "chart_id": 0,
        "legend": {"bottom": "bottom", "show": true},
        "series": [{
            "book_id": 16, "chart_id": 0, "color": "#7bb142", "data": [],
            "name": "가전 수출액(천USD)", "node_id": "1|4|1|2|3|31", "series_id": 0,
            "tag": "매크로", "type": "bar", "yAxisIndex": 0},
          {"book_id": 16, "chart_id": 0, "color": "#2b5034", "data": [],
            "name": "YoY(%)", "node_id": "1|4|1|2|3|32", "series_id": 1, "showSymbol": true, "step": false,
            "tag": "매크로", "type": "line", "yAxisIndex": 1}],
        "title": [{"left": "center", "subtext": "부제목", "text": "가전제품 수출"}, 
          {"left": "right", "text": "출처: 한국무역협회", "textStyle": {"color": "gray", "fontSize": 13, "fontWeight": "lighter"}, "top": "bottom"}],
        "tooltip": {"formatter": "abcde", "trigger": "none"},
        "xAxis": {"max": 1690416000000, "min": 1595808000000, "type": "time"},
        "yAxis": [{"axisLabel": {"formatter": "{value}"}, "book_id": 16, "chart_id": 0, 
          "max": null, "min": null, "position": "left", "type": "value"}, 
          {"axisLabel": {"formatter": "{value}"}, "book_id": 16, "chart_id": 0, 
            "max": 100, "min": -100, "position": "right", "type": "value"
          }]}]
  },
  "success": true
}
```

### Query Parameters

 Parameter     | type    | Description 
---------------|---------|-------------
 sess_mysql    | Session | MySQL 세션    
 sess_presto   | Session | Presto 세션   
 node_id_stock | str     | 종목 node id  


<p align="center">
  <img alt="cb1" src="/Users/yeseul/PycharmProjects/slate/source/images/chartbook1.png" width="45%">
&nbsp; &nbsp; &nbsp; &nbsp;
  <img alt="cb2" src="/Users/yeseul/PycharmProjects/slate/source/images/chartbook2.png" width="45%">
</p>
<p align="center">
  <img alt="cb2" src="/Users/yeseul/PycharmProjects/slate/source/images/chartbook3.png" width="45%">
&nbsp; &nbsp; &nbsp; &nbsp;
  <img alt="cb3" src="/Users/yeseul/PycharmProjects/slate/source/images/chartbook4.png" width="45%">
</p>


# 상관관계

## 상관관계

### Request URL
`http://dev-ra.shinyoung.com/api/s12_us_stock/correlation_price_us`

종목의 종가와 매크로 변수의 일대다 상관계수 반환

> payload:

```json
{
  "node_id_stock": "3|2|1|1|AAPL"
}
```

> Response:

```json
{"result": {
    "table": {
      "columns": [
        {"caption": "노드 ID", "dataField": "node_id_b", "dataType": "string", "visible": false},
        {"caption": "분류", "dataField": "tag_b", "dataType": "string"},
        {"caption": "이름", "dataField": "name_b", "dataType": "string"},
        {"caption": "상관계수", "dataField": "corr", "dataType": "number", "format": {"precision": 2, "type": "fixedPoint"}},
        {"caption": "샘플 개수", "dataField": "n_samples", "dataType": "number"}
      ],
      "rows": [
        {
          "corr": 0.2374338395465267,
          "data_table_a": "ossy_gfinance_data.StockDaily", "data_table_b": "ossy_finance_data.GlobalIndexRefinitivDaily", "n_samples": 1974,
          "name_a": "애플", "name_b": "CRB TR 지수",
          "node_id_a": "3|2|1|1|AAPL", "node_id_b": "1|3|1|1",
          "symbol_a": "AAPL", "symbol_b": ".TRCCRBTR",
          "tag_a": "미국종목", "tag_b": "매크로"
        },
        {
          "corr": -0.07115988902533889,
          "data_table_a": "ossy_gfinance_data.StockDaily", "data_table_b": "ossy_finance_data.CofixDaily", "n_samples": 74,
          "name_a": "애플", "name_b": "COFIX 금리 [잔액기준]",
          "node_id_a": "3|2|1|1|AAPL", "node_id_b": "1|1|2|3|1",
          "symbol_a": "AAPL", "symbol_b": "1",
          "tag_a": "미국종목", "tag_b": "매크로"
        },
        {"...":  "..."}
      ]}
  },
  "success": true
}
```

### Query Parameters

 Parameter     | type    | Default  | Description 
---------------|---------|----------|-------------
 sess_mysql    | Session |          | MySQL 세션    
 sess_presto   | Session |          | Presto 세션   
 node_id_stock | str     |          | 종목 node id  
 start_date    | str     | 10년 전 일자 | 차트 조회 시작일   
 end_date      | str     | 오늘       | 차트 조회 종료일   
 min_samples   | int     | 12       | 최소 샘플 개수    



# Financial Highlight

## 실적 요약

### Request URL
`http://dev-ra.shinyoung.com/api/s12_us_stock/financial_summary_us`

> payload:

```json
{
  "node_id_stock": "3|2|1|1|AAPL"
}
```

> Response:

```json
{"result": {
    "date_value": {
      "q_month": "4", "q_year": "2023", "y_year": "2022"
    },
    "summary_table": {
      "rows": [
        {"mark": "-", "output": "5.54"},
        {"mark": "-", "output": "21.37"},
        {"mark": "-", "output": "1.87"},
        {"mark": "-", "output": "2.51"},
        {"mark": "-", "output": "19.05"},
        {"mark": "-", "output": "3.4"},
        {"mark": "-", "output": "19.46"},
        {"mark": "+", "output": "9.63"},
        {"mark": "+", "output": "49.82"},
        {"mark": "+", "output": "7.79"},
        {"mark": "+", "output": "5.41"}
      ]}
  },
  "success": true
}
```


### 화면 예시
<p align="center"><img src="/Users/yeseul/PycharmProjects/slate/source/images/fin_summary.png" width=700 alt="fin_summary"></p>


### Query Parameters

 Parameter     | type    | Default  | Description 
---------------|---------|----------|-------------
 sess_mysql    | Session |          | MySQL 세션    
 sess_presto   | Session |          | Presto 세션   
 node_id_stock | str     |          | 종목 node id  



## 주요 재무 특이사항

### Request URL
`http://dev-ra.shinyoung.com/api/s12_us_stock/financial_statement_anomaly_detection_us`

> payload:

```json
{
  "node_id_stock": "3|2|1|1|MSFT",
  "threshold": 1.6
}
```

> Response:

```json
{"result": {
    "key_value": {"date": "2023년 3월"},
    "table": {
      "columns": [
        {"caption": "index", "dataField": "index", "dataType": "string"},
        {"caption": "value", "dataField": "value", "dataType": "string"}
      ],
      "rows": [
        {"index": "현금의증가", "value": "+"}
      ]}
  },
  "success": true
}
```

### 화면 예시
<p align="center"><img src="/Users/yeseul/PycharmProjects/slate/source/images/fin_anomaly.png" width=700 alt="fin_anomaly"></p>

### Query Parameters

 Parameter     | type    | Default | Description 
---------------|---------|---------|-------------
 sess_mysql    | Session |         | MySQL 세션    
 sess_presto   | Session |         | Presto 세션   
 node_id_stock | str     |         | 종목 node id  
 threshold     | int     | 1.6     | Z-score 임계값 

### Output Example

 index | value 
-------|-------
 현금의증가 | +     



## 주요 재무 특이사항 - 상세 조회

### Request URL
`http://dev-ra.shinyoung.com/api/s12_us_stock/financial_statement_anomaly_detection_detail_graph_us`

> payload:

```json
{
  "node_id_stock": "3|2|1|1|MSFT",
  "item": "현금의증가"
}
```

> Response:

```json
{"result": {
    "chart": {
      "series": [
        {"data": ["..."], "name": "매출액", "step": false, "type": "line", "yAxisIndex": 0},
        {"data": ["..."], "name": "매출액 추세", "step": false, "type": "line", "yAxisIndex": 0},
        {"data": ["..."], "name": "매출액 계절성", "step": false, "type": "line", "yAxisIndex": 1},
        {"data": ["..."], "name": "매출액 오차", "step": false, "type": "line", "yAxisIndex": 1}
      ],
      "xAxis": {"type": "time"},
      "yAxis": [
        {"name": "", "scale": "true", "type": "value"},
        {"name": "", "scale": "true", "type": "value"}
      ]}
  },
  "success": true
}
```

### Query Parameters

 Parameter     | type    | Description 
---------------|---------|-------------
 sess_mysql    | Session | MySQL 세션    
 sess_presto   | Session | Presto 세션   
 node_id_stock | str     | 종목 node id  
 item          | str     | 국문 재무계정명    

<img src="/Users/yeseul/PycharmProjects/slate/source/images/anomaly_detail.png" title="anomaly_detail">


## 주요 재무 특이사항 - 이상치 판단 범주 조회
### Request URL
`http://dev-ra.shinyoung.com/api/s12_us_stock/financial_statement_anomaly_detection_range_graph_us`

> payload:

```json
{
  "node_id_stock": "3|2|1|1|MSFT",
  "item": "현금의증가",
  "threshold": 1.6
}
```

> Response:

```json
{"result": {
    "chart": {
      "series": [
        {"data": ["..."], "name": "현금의증가", "step": false, "type": "line"},
        {"data": ["..."], "name": "정상추정범위", "step": false, "type": "line"},
        {"data": ["..."], "name": "정상추정범위", "step": false, "type": "line"}
      ],
      "xAxis": {"type": "time"},
      "yAxis": [{"name": "", "scale": "true", "type": "value"}
      ]}
},
  "success": true
}
```

### Query Parameters

 Parameter     | type    | Default | Description 
---------------|---------|---------|-------------
 sess_mysql    | Session |         | MySQL 세션    
 sess_presto   | Session |         | Presto 세션   
 node_id_stock | str     |         | 종목 node id  
 item          | str     |         | 국문 재무계정명    
 threshold     | int     | 1.6     | Z-score 임계값 

<img src="/Users/yeseul/PycharmProjects/slate/source/images/anomaly_range.png" title="anomaly_range">



## 재무제표 통합
### Request URL
`http://dev-ra.shinyoung.com/api/s12_us_stock/financial_statement_us`

> payload:

```json
{
  "node_id_stock": "3|2|1|1|AAPL",
  "freq": "Y",
  "n_year": "10"
}
```

> Response:

```json
{"result": {
    "chart_a": {"...": "..."},
    "chart_a_four": {"...": "..."},
    "chart_a_three": {"...": "..."},
    "chart_a_two": {"...": "..."},
    "chart_b": {"...": "..."},
    "chart_c": {"...": "..."},
    "key_value": {
      "ROE_average_values": 113.12634499999999,
      "debt_ratio_average": 182.85629999999998,
      "dividend_yield_average_values": 0.5581725,
      "operating_income_margin_average_values": 27.1976125,
      "pbr_average": 39.9913775,
      "per_average": 35.43549,
      "sales_pct_change": 0.14867695264734437
    },
    "table": {
      "columns": [
        {"caption": "구분(달러)", "dataField": "index", "dataType": "string"},
        {"caption": "연간", "columns": [{
              "caption": "2016",
              "columns": [{
                  "caption": "201609", "columns": [], "dataField": "201609", "dataType": "number"}],
              "dataType": "number"
            },
            {"...": "..."},
            {
              "caption": "2022",
              "columns": [{
                  "caption": "202209", "columns": [], "dataField": "202209", "dataType": "number"}],
              "dataType": "number"
            }]}
      ],
      "rows": [
        {"201609": null, "201709": null, "201809": null, "201909": 5.9133, "202009": 3.84873, "202109": 3.84068, "202209": 3.17824, "index": "BPS"},
        {"201609": null, "201709": null, "201809": null, "201909": 0.75, "202009": 0.795, "202109": 0.85, "202209": 0.9, "index": "주당배당금"},
        {"...": "..."},
        {"201609": null, "201709": null, "201809": null, "201909": 62.1822, "202009": 61.7668, "202109": 58.2206, "202209": 56.6904, "index": "매출원가율"},
        {"201609": null, "201709": null, "201809": null, "201909": 7.0126, "202009": 7.255, "202109": 6.0066, "202209": 6.3637, "index": "판관비율"}
      ]
    }},
  "success": true
}
```

### Query Parameters

 Parameter     | type    | Default | Description 
---------------|---------|---------|-------------
 sess_mysql    | Session |         | MySQL 세션    
 sess_presto   | Session |         | Presto 세션   
 node_id_stock | str     |         | 종목 node id  
 item          | str     |         | 국문 재무계정명    
 threshold     | int     | 1.6     | Z-score 임계값 

### 화면 예시
<p align="center"><img src="/Users/yeseul/PycharmProjects/slate/source/images/fin_stat.png" width=700 alt="fin_stat"></p>



# 주주 정보

## 주요 주주 정보

### 화면 예시
<p align="center"><img src="/Users/yeseul/PycharmProjects/slate/source/images/shareholders.png" width=700 alt="shareholders"></p>


## 주요 주주 네트워크

### 화면 예시
<p align="center"><img src="/Users/yeseul/PycharmProjects/slate/source/images/shareholders_network.png" width=700 alt="shareholders_network"></p>


# Company graph DB


# [스크리너]

 type   | API명                          | 설명          
--------|-------------------------------|-------------
 POST   | get_list_cmp_tk_us            | 최종 종목 티커 반환 
 POST   | chartbook_get_result_chart_us | 종목 평균 상대수익률 
 POST   | get_result_table_us           | 종목 결과 테이블   
 GET    | get_sc_item_data_us           | 항목별 전체 데이터  
 GET    | get_user_condition_us         | 사용자 지정조건 리스트 불러오기
 GET    | load_user_condition_us        | 사용자 조건 불러오기
 POST   | save_user_condition_us        | 사용자 조건 저장
 PUT    | modify_user_condition_us      | 사용자 조건 수정
 DELETE | delete_user_condition_us      | 사용자 조건 삭제

# 검색

## 검색 조건

### Request URL
`http://dev-ra.shinyoung.com/api/f12_us_stock_screener/get_list_cmp_tk_us`

> payload:

```json
{
  "market": "ALL",
  "sector": "ALL",
  "market_cap": "200000|3500000",
  "finance_list": ["AREV|range|1|100000|700000", "AOPMGNPCT|range|1|1|50"],
  "multiple_list": ["QTLE|range|5|100"],
  "cagr_list": ["AEBIT|range|3|0|100"],
  "continuity_list": ["ADIVSHR|>=|1"]
}
```

> Response:

```json
{"result": {
    "list": [
      "UNH",
      "AAPL",
      "COST"
    ]
  },
  "success": true
}
```

### Query Parameters

 Parameter       | type    | Default | Description      
-----------------|---------|---------|------------------
 sess_mysql      | Session |         | MySQL 세션         
 sess_presto     | Session |         | Presto 세션        
 market          | str     | ALL     | 거래소 조건           
 sector          | str     | ALL     | 로이터 업종 조건        
 market_cap      | str     |         | 시가총액(백만달러) 범위 조건 
 finance_list    | list    |         | 재무 조건 리스트        
 multiple_list   | list    |         | 멀티플 조건 리스트       
 continuity_list | list    |         | 연속 조건 리스트        
 cagr_list       | list    |         | Cagr 조건 리스트      


## 검색 결과

### Request URL
`http://dev-ra.shinyoung.com/api/f12_us_stock_screener/get_result_table_us`

> payload:

```json
{
  "list_cmp_tk": ["UNH", "AAPL", "COST"]
}
```

> Response:

```json
{"result": {"length": 3,
    "table": {"columns": [
        {"caption": "종목티커", "dataField": "symbol", "dataType": "string"},
        {"caption": "종목명", "dataField": "name_ko_short", "dataType": "string"},
        {"caption": "시가총액(USD)", "dataField": "market_cap_usd", "dataType": "number"},
        {"caption": "전일종가(USD)", "dataField": "price", "dataType": "number"},
        {"caption": "1D(%)", "dataField": "pct_1d", "dataType": "number"},
        {"caption": "1W(%)", "dataField": "pct_1w", "dataType": "number"},
        {"caption": "1M(%)", "dataField": "pct_1m", "dataType": "number"},
        {"caption": "3M(%)", "dataField": "pct_3m", "dataType": "number"},
        {"caption": "6M(%)", "dataField": "pct_6m", "dataType": "number"},
        {"caption": "1Y(%)", "dataField": "pct_1y", "dataType": "number"},
        {"caption": "YTD(%)", "dataField": "pct_ytd", "dataType": "number"},
        {"caption": "매출액(백만USD)", "dataField": "매출액", "dataType": "number"},
        {"caption": "영업이익(백만USD)", "dataField": "영업이익", "dataType": "number"},
        {"caption": "당기순이익(백만USD)", "dataField": "당기순이익", "dataType": "number"}],
      "rows": [
        {"market_cap": 39002326, "market_cap_usd": 3045391340000, "name_ko_short": "애플", 
          "pct_1d": 0.45, "pct_1m": 4.51, "pct_1w": -0.06, "pct_1y": 26.59, "pct_3m": 18.23, "pct_6m": 36.49, "pct_ytd": 54.81, "price": 194, 
          "symbol": "AAPL", "당기순이익": 99803, "매출액": 394328, "영업이익": 119437},
        {"market_cap": 3207680, "market_cap_usd": 250463093000, "name_ko_short": "코스트코 홀세일",
          "pct_1d": 0.22, "pct_1m": 7.98, "pct_1w": 2.1, "pct_1y": 6.81, "pct_3m": 12.33, "pct_6m": 15.14, "pct_ytd": 24.69, "price": 565,
          "symbol": "COST", "당기순이익": 5844, "매출액": 226954, "영업이익": 7793},
        {"market_cap": 6092189, "market_cap_usd": 475692171000, "name_ko_short": "유나이티드헬스 그룹",
          "pct_1d": 0.44, "pct_1m": 6.65, "pct_1w": 2.19, "pct_1y": -3.5, "pct_3m": 3.86, "pct_6m": 3.74, "pct_ytd": -1.49, "price": 511,
          "symbol": "UNH", "당기순이익": 20120, "매출액": 324162, "영업이익": 28435}]
    }},
  "success": true
}
```

### Query Parameters

 Parameter   | type | Default | Description 
-------------|------|---------|-------------
 list_cmp_tk | list |         | 종목 티커 리스트   

### 테이블
<p align="center"><img src="/Users/yeseul/PycharmProjects/slate/source/images/screener_table.png" width=700 alt="screener_table"></p>


## 종목 평균 상대수익률

> payload:

```json
{
  "list_cmp_tk": ["UNH", "AAPL", "COST"],
  "chart_range": "12"
}
```

> Response:

```json
{"result": {
    "chart": {
      "series": [
        {"data": ["...","..."],
          "name": "Port", "step": false, "type": "line", "yAxisIndex": 0},
        {"data": ["...","..."],
          "name": "S&P500", "step": false, "type": "line", "yAxisIndex": 0},
        {"data": ["...","..."],
          "name": "NASDAQ100", "step": false, "type": "line", "yAxisIndex": 0},
        {"data": ["...","..."],
          "name": "DOW30", "step": false, "type": "line", "yAxisIndex": 0}],
      "tooltip": {"trigger": "axis"},
      "xAxis": {"type": "time"},
      "yAxis": [{"name": "시작일(100)", "type": "value"}]
    }},
  "success": true
}
```

### Query Parameters

 Parameter   | type | Default | Description        
-------------|------|---------|--------------------
 list_cmp_tk | list |         | 종목 티커 리스트          
 chart_range | str  | 12      | 종목 평균 상대 수익률 차트 범위 


### 차트
<p align="center"><img src="/Users/yeseul/PycharmProjects/slate/source/images/screener_chart.png" width=700 alt="screener_chart"></p>


# 사용자 조건

## 저장

## 불러오기

## 수정

## 삭제

