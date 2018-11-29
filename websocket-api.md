# AquaNow Websocket Information
* AquaNow provides real-time aggregated market data feed through websocket to our end users. 
* Data can be accessed either in a single or combined streams by sending AquaNow subscription messages. 
* The following data requests share the same base endpoint: **wss://api.binance.com:8081**
* The following are the detail information regarding the websocket api and subscription messages.

# Aggregated Market Data 
## Raw Aggregated Market Data
* Real-time aggregated market data across various marketplaces and exchanges

**Subscription Message:**
```javascript
{
  "type": "subscribe",      // Message Type
  "channel": 'orderbook',   // Subscription Channel
  "pair": 'BTCUSD'         // Symbol
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

**Subscription Message:**
```javascript
{
  "type": "subscribe",      // Message Type
  "channel": 'orderbook',   // Subscription Channel
  "pair": 'BTCUSD',        // Symbol
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

## Aggregated Market Data with Exchange Fees
* Real-time aggregated market data across various marketplaces and exchanges and integrated the transaction fee into the quote

**Subscription Message:**
```javascript
{
  "type": "subscribe",      // Message Type
  "channel": 'orderbook',   // Subscription Channel
  "pair": 'BTCUSD',         // Symbol
  "includeFees":1           // Flag to Incorporate Exchange Fees
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
