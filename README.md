hitbtc-js
=======

hitbtc-js is a node wrapper for the HitBTC REST API found [here](https://github.com/hitbtc-com/hitbtc-api)

Usage
--------
    
require hitbtc-js to begin with:

	var HitBTC = require('hitbtc-js');

create an instance
	
	var client = new HitBTC('your_api_key', 'your_api_secret', 'sandbox');

Make a request
	
	client.ticker('BTCEUR', console.log); // prints the ticker for the BTC_EUR currency pair
	client.newOrder('11111112', 'BTCUSD', 'buy', '0.1', '100', 'limit', 'GTC', console.log); // adds a buy order
	
For all response JSON formats, see the [github documentation](https://github.com/hitbtc-com/hitbtc-api)
	
Constructor
-----------
### HitBTC (API_Key, API_Secret, API_Type) ###

Parameter Name | Parameter Type | Description
-------------- | -------------- | ------------------
API_Key        | String         | Find it by making a new API key pair in account settings
API_Secret     | String         | Find it by making a new API key pair in account settings
API_Type       | String         | 'live' or 'sandbox'. When testing, you may want to use the sandbox setting but do note that some routes are not supported in sandbox


[Supported Currency Pairs](id:currency_pairs)
--------------------------

Currency Pair  |
-------------- |
BTCUSD         |
BTCEUR         |
LTCBTC         |
LTCUSD         |
LTCEUR         |
EURUSD         |
DOGEBTC        |
XMRBTC         |

Public API
----------

### (-) time (callback) ###

**Status: Implemented**

Parameter Name | Parameter Type | Description
-------------- | -------------- | ------------------
callback       | Function       | A callback function that will be passed the result of API call

### (-) symbols (callback) ###

**Status: Implemented**

Parameter Name | Parameter Type | Description
-------------- | -------------- | ------------------
callback       | Function       | A callback function that will be passed the result of API call

### (-) ticker (pair, callback) ###

**Status: Implemented**

Parameter Name | Parameter Type | Description
-------------- | -------------- | ------------------
pair           | String         | The currency pair that you want the ticker on. See supported  [currency pairs](#currency_pairs)
callback       | Function       | A callback function that will be passed the result of API call

### (-) orderbook (symbol, callback) ###

**Status: Implemented**

Parameter Name | Parameter Type | Description
-------------- | -------------- | ------------------
pair           | String         | The currency pair that you want the order book for. See supported [currency pairs](#currency_pairs)
callback       | Function       | A callback function that will be passed the result of API call

### (-) trades ###

**Status: Not Implemented**

Parameter Name | Parameter Type | Description
-------------- | -------------- | ------------------
callback       | Function       | A callback function that will be passed the result of API call

Trading API
-----------

### (-) tradingBalance (callback) ###

**Status: Working in Live**

Parameter Name | Parameter Type | Description
-------------- | -------------- | ------------------
callback       | Function       | A callback function that will be passed the result of API call

### (-) activeOrders (pairs, callback) ###

**Status: Working in Live**

Parameter Name | Parameter Type | Description
-------------- | -------------- | ------------------
pairs          | String         | Comma separated currency pairs. See supported [currency pairs](#currency_pairs)
callback       | Function       | A callback function that will be passed the result of API call

### (-) newOrder (clientOrderId, pair, side, price, quantity, type, timeInForce, callback) ###

**Status: Working in Live**

Parameter Name | Parameter Type | Description
-------------- | -------------- | ------------------
clientOrderId  | String         | A 8 to 30 numeric string that will be used as the order's ID
pair           | String         | The currency pair that you want to trade on See supported [currency pairs](#currency_pairs)
side           | String         | `buy` or `sell`
price          | Decimal        | Price that you want the trade to activate
quantity       | Integer        | Amount of lots to trade
type           | String         | Only `limit` orders are currently supported
timeInForce    | String         | `GTC` - Good-Till-Cancelled<br>`IOC` - Immediate-Or-Cancel<br>`FOK` - Fill-Or-Kill<br>`DAY` - day orders
callback       | Function       | A callback function that will be passed the result of API call

### (-) cancelOrder (clientOrderId, cancelRequestClientOrderId, pair, side, callback) ###

**Status: Not Implemented**

### (-) trades (by, start_index, max_results, symbols, sort, from, till, callback) ###

**Status: Not Implemented**

### (-) recentOrders (start_index, max_results, symbols, statuses, callback) ###

**Status: Not Implemented**

Payment API
-----------

### (-) paymentBalance (callback) ###

**Status: Works in Live**

Parameter Name | Parameter Type | Description
-------------- | -------------- | ------------------
callback       | Function       | A callback function that will be passed the result of API call

### (-) transferToTrading (amount, currency_code, callback) ###

**Status: Not Implemented**

### (-) transferToMain (amount, currency_code, callback) ###

**Status: Not Implemented**

### (-) getPaymentAddress (currency_code, callback) ###

**Status: Works in Live**

Parameter Name | Parameter Type | Description
-------------- | -------------- | ------------------
currency_code  | String         | Valid supported currency code. `e.g. BTC`
callback       | Function       | A callback function that will be passed the result of API call

### (-) createPaymentAddress (currency_code, callback) ###

**Status: Not Implemented**

### (-) payout (amount, currency_code, address) ###

**Status: Not Implemented**

### (-) transactions (offset, limit, dir) ###

**Status: Not Implemented**