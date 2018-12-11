# AquaNow Websocket Information
* AquaNow provides real-time aggregated market data feed through websocket to our end users. 
* Data can be accessed either in a single or combined streams by sending AquaNow subscription messages. 
* The following data requests share the same base endpoint: **wss://api.aquanow.io:8081**
* The following are the detail information regarding the websocket api and subscription messages.

# Aggregated Market Data 
## Raw Aggregated Order Book
* Real-time aggregated order book across various marketplaces and exchanges

**Subscription Message:**
```javascript
{
  "type": "subscribe",      // Message Type
  "channel": 'orderBook',   // Subscription Channel
  "pair": 'BTC-USD'         // Symbol
}
```

**Payload:**
```javascript
{
  dateType: 'aggOB',
  lastUpdated: 1544004380004,
  includeFees: 0,
  symbol: 'BTC-USD',
  bids:
  [
    {
      "quote": "6000",        // Price
      "quantity": '2.13',     // Quote Size
      "exchange": 'coinbase'  // Exchange
    },
    ...
  ],
  asks:
  [
    {
      "quote": "6001",        // Price
      "quantity": '1.36',     // Quote Size
      "exchange": 'bitfinex'  // Exchange
    },
    ...
  ]
}
```

## Bucketed Aggregated Order Book
* Real-time aggregated order book across various marketplaces and exchanges by bin

**Subscription Message:**
```javascript
{
  "type": "subscribe",      // Message Type
  "channel": 'orderBook',   // Subscription Channel
  "pair": 'BTC-USD',        // Symbol
  "binSize":5               // Price Range for the Bucket
}
```

**Payload:**
```javascript
{
  dateType: 'aggOB',
  lastUpdated: 1544004380004,
  includeFees: 0,
  symbol: 'BTC-USD',
  bids:
  [
    {
      "quote": "6000",        // Price
      "quantity": '2.13',     // Quote Size
      "exchange": 'bin5'      // Exchange
    },
    ...
  ],
  asks:
  [
    {
      "quote": "6005",        // Price
      "quantity": '1.23',     // Quote Size
      "exchange": 'bin5'      // Exchange
    },
    ...
  ]
}
```

## Aggregated Order Book with Exchange Fees
* Real-time aggregated order book across various marketplaces and exchanges and integrated the transaction fee into the quote

**Subscription Message:**
```javascript
{
  "type": "subscribe",      // Message Type
  "channel": 'orderBook',   // Subscription Channel
  "pair": 'BTC-USD',         // Symbol
  "includeFees":1           // Flag to Incorporate Exchange Fees
}
```

**Payload:**
```javascript
{
  dateType: 'aggOB',
  lastUpdated: 1544004380004,
  includeFees: 1,
  symbol: 'BTC-USD',
  bids:
  [
    {
      "quote": "6000",        // Price
      "quantity": '2.13',     // Quote Size
      "exchange": 'coinbase'  // Exchange
    },
    ...
  ],
  asks:
  [
    {
      "quote": "6001",        // Price
      "quantity": '1.36',     // Quote Size
      "exchange": 'bitfinex'  // Exchange
    },
    ...
  ]
}
```

## Unsubscription Message

```javascript
{
  "type": "unsubscribe",      // Message Type
  "channel": 'orderBook',     // Subscription Channel
  "pair": 'BTC-USD'           // Symbol
}
```
