# AquaNow Execution Services
* AquaNow provides execution services to end users by leveraging our aggregated market data, liquidity, and execution algos. As the following APIs are authenticated endpoints, in order to access our services, please contact info@aquanow.io to request for the access & secret keys and onboarding information. 

# Execution Algos
Aquanow provides various of execution algos. They provide different execution characteristics and the basic algos include SOR & TWAP. 

## Get All Trade Orders

**HTTP Method:** GET

**API EndPoint:** https://execute-api.aquanow.io/order

**Sample Code:**

```
var request = require("request");
var options = { method: 'GET',
  url: 'https://execute-api.aquanow.io/order',
  qs: { username: USERNAME },
  headers:
   {
     'Content-Type': 'application/json',
     'x-api-key': YOUR_API_KEY
   }
};
request(options, function (error, response, body) {
  if (error) throw new Error(error);
  console.log(body);
});
```

**Payload:**
```javascript
{
  "payload":
  {
    "Items":
    [
      {
        "strategy": "TWAP",                                   // Strategy Type
        "orderId": "21f285a0-4ce3-11e9-b31b-abd75bfdd676",    // Order ID
        "symbol": "BTC-USD",                                  // Symbol
        "tradeStatus": "COMPLETE",                            // Trade Status
        "message": "-",                                       // Trade Message
        "tradeSize": 0.4,                                     // Trade Size
        "exchangeOrderId": 245065455355,                      // Crypto Exchange Order Id
        "priceLimit": 3800,                                   // Trade Price Limit
        "tradePriceAvg": 3912.3,                              // Trade Price Average
        "fillPct": 100,                                       // Fill Percentage
        "tradeSide": "sell",                                  // Trade Side
        "orderType": "parentOrder",                           // Trade Order Type
        "exchange": "binance",                                // Routed Crypto Exchange
        "tradeDuration": 300,                                 // Trade Duration for the Strategy in seconds
        "tradeTime": 1553287402235,                           // Time that the Trade was placed (UTC)
        "username": "test",                                   // Username for this account
        "itemDateTime": 1553287725506                         // Last Trade Update (UTC)
      }
    ]
  }
}
```

 
