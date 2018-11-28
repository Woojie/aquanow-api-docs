# AquaNow Websocket Information
* AquaNow provides real-time aggregated market data feed through websocket to our end users. 
* Data can be accessed either in a single or combined streams by sending AquaNow subscription messages. 
* The following are the detail information regarding the websocket api and subscription messages.

# Aggregated Market Data 
* Real-time aggregated market data across various marketplaces and exchanges
* Base endpoint: **wss://api.binance.com:8081**

**Payload:**
```javascript
{
  "quote": "6000",        // Price
  "quantity": '2.13',     // Quote Size
  "exchange": 'coinbase'  // Exchange
}
