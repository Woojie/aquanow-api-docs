# AquaNow REST API Information
* AquaNow provides REST API endpoint for end users to get market data snapshot, historical market data and pre-trade analysis
* The following data requests share the same base endpoint: https://api.aquanow.io
* The following are the detail information regarding the REST API and the associated parameters.

# Market Data
## Historical Aggregated Best Bid & Ask
Provide users the last 3 hours aggregated best bid, ask & spread

**HTTP Method:** GET

**API EndPoint:** /v1/history/symbol/:symbol

**Payload:**
```javascript
[
  {
    "dataType": "aggBBO",           // Data Type
    "dateTime": '1543471590306',    // Timestamp
    "symbol": 'BTCUSD',             // Symbol
    "bestBid": 6000,                // Best Bid
    "bestAsk": 6010,                // Best Ask
    "spread": 10                    // Bid Ask Spread
  }
]
```

# Pre-Trade Analysis
## Order Routing/Placement Analysis
Given the trade side and side provide by user, what is the most optimal way to route the orders across various exchanges to minimize market impact

**HTTP Method:** GET

**API EndPoint:** /v1/pretrade/symbol/:symbol/side/:side/size/:size

## Market Impact Projection
Provides user a projection on the market impact for every 100 units of cryptocurrency of a given trade size range (0, 1000]

**HTTP Method:** GET

**API EndPoint:** /v1/marketimpactprojection/symbol/:symbol/side/:side

**Payload:**
```javascript
[
  1.667,
  15.46,
  21.79
  ....
  309.91
]
```
