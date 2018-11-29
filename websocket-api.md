# AquaNow Websocket Information
* AquaNow provides real-time aggregated market data feed through websocket to our end users. 
* Data can be accessed either in a single or combined streams by sending AquaNow subscription messages. 
* The following are the detail information regarding the websocket api and subscription messages.

[Raw Aggregated Market Data](#raw-aggregated-market-data)

# Aggregated Market Data 
## Raw Aggregated Market Data
* Real-time aggregated market data across various marketplaces and exchanges
* Base endpoint: **wss://api.binance.com:8081**

**Subscription Message:**
```javascript
{
  "type": "subscribe",      // Message Type
  "channel": 'orderbook',   // Subscription Channel
  "pair": 'BTC-USD'         // Symbol
}
```

**Payload:**
```javascript
{
  [
    "quote": "6000",        // Price
    "quantity": '2.13',     // Quote Size
    "exchange": 'coinbase'  // Exchange
  ]
}
```

## Bucketed Aggregated Market Data
* Real-time aggregated market data across various marketplaces and exchanges by bin
* Base endpoint: **wss://api.binance.com:8081**

**Subscription Message:**
```javascript
{
  "type": "subscribe",      // Message Type
  "channel": 'orderbook',   // Subscription Channel
  "pair": 'BTC-USD',        // Symbol
  "binSize":5               // Price Range for the Bucket
}
```

**Payload:**
```javascript
{
  [
    "quote": "6000",        // Price
    "quantity": '2.13',     // Quote Size
    "exchange": 'coinbase'  // Exchange
  ],
  [
    "quote": "6005",        // Price
    "quantity": '1.23',     // Quote Size
    "exchange": 'binance'   // Exchange
  ]
}
```
