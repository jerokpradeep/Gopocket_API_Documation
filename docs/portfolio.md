---

title: Portfolio

---

# Portfolio

This API lets you retrieve holdings and positions in your portfolio.

|Method	|Api                |Detail                         |
|-------|-------------------|-------------------------------|
|GET	| ho-rest/holdings       |Retrieve the list of long term equity holdings|
|GET	| po-rest/positions	    |Retrieve the list of short term positions|
|POST	|po-rest/positions/conversion.	|Convert intraday to long term or long term to intraday |

## Holdings

Holdings contain the long term equity Holdings of the customer. All the financial instruments in the holdings reside in the customer’s DEMAT account indefinitely until its sold or is delisted or changed by the exchanges. Changes to DEMAT account is settled in T+1 days.

__Response Structure__

```
{
    "status": "Ok",
    "message": "Success",
    "result": [
        {
            "poa": false,
            "product": "CNC",
            "holdings": [
                {
                    "isin": "INE669E01016",
                    "realizedPnl": "0.0",
                    "unrealizedPnl": "-236.09999",
                    "netPnl": "-236.09999",
                    "netQty": "30",
                    "buyPrice": "7.87",
                    "holdQty": "30",
                    "dpQty": "0",
                    "benQty": "0",
                    "unpledgedQty": "0",
                    "collateralQty": "0",
                    "brkCollQty": "0",
                    "btstQty": "0",
                    "usedQty": "0",
                    "tradedQty": "0",
                    "sellableQty": "30",
                    "authQty": "0",
                    "sellAmount": "0.0",
                    "authFlag": false,
                    "symbol": [
                        {
                            "exchange": "NSE",
                            "token": "14366",
                            "tradingSymbol": "IDEA-EQ",
                            "pdc": "13.95",
                            "ltp": "13.95"
                        },
                        {
                            "exchange": "NFO",
                            "token": "532822",
                            "tradingSymbol": "IDEA",
                            "pdc": "0",
                            "ltp": "0"
                        }
                    ]
                }
            ]
        }
    ]
}


```

__Parameters__


| Field         | Type   | Description                                                                                            |
| ------------- | ------ | ------------------------------------------------------------------------------------------------------ 
|isin            | String | International Securities Identification Number (ISIN) for the asset|
|realizedPnl     | String |  profit or loss realized from transactions|
|unrealizedPnl   | String | Potential profit or loss |
|netPnl          | String | Overall net profit or loss |
|netQty          | String | Net quantity of the asset held|
|buyPrice        | String | Price at which the asset was acquired|
|holdQty         | String | Total quantity of the asset held|
|dpQty           | String | Dematerialized quantity of the asset|
|benQty          | String | Actual quantity of the asset|
|unpledgedQty    | String | Quantity of the asset that is not pledged as collateral|
|collateralQty   | String | Quantity of the asset held as collateral|
|brkCollQty      | String | Brokerage-related collateral quantity|
|btstQty         | String | Buy Today, Sell Tomorrow quantity|
|usedQty         | String | Quantity of the asset used in any transactions|
|tradedQty       | String | Total quantity of the asset traded|
|sellableQty     | String | Quantity of the asset available for sale|
|authQty         | String | Approved quantity for specific actions|
|authFlag        | String | Authorization flag |
|sellAmount      | String | Total amount from selling the asset|
|Symbol          | Array  |List of symbols associated with the asset|
|exchange        | String | Exchange where the asset is traded|
|token           | String | Token identifier for the asset|
|tradingSymbol   | String | Trading symbol |
|pdc             | String | Previous day close price |
|ltp             | String | Last traded price of the asset|



## Positions

Users can retrieve a list of all open positions for the day. This includes all F&O carryforward positions as well.


__Response Structure__

```
{
    "status": "Ok",
    "message": "success",
    "result": [
        {
            "formattedInsName": "JPYINR 13JAN23 FUT",
            "tradingSymbol": "JPYINR13JAN23F",
            "exchange": "CDS",
            "segment": "cde_fo",
            "token": "11771",
            "product": "M",
            "netQty": "-2",
            "netBuyQty": "0",
            "netBuyAvgPrice": "0.0",
            "netBuyAvg": "NaN",
            "netBuyValue": "0.0",
            "netSellQty": "2",
            "netSellAvgPrice": "63.5675",
            "netSellAvg": "63567.5",
            "netSellValue": "127135.0",
            "averagePrice": "63.5675",
            "ltp": "61.6750",
            "pnl": "0.00",
            "mtm": "",
            "pdc": "61.67",
            "realizedpnl": "0.0",
            "unrealizedpnl": "3785.00",
            "multiplier": "1000",
            "lotSize": null,
            "tickSize": null
        },
     ]
 }
```
__Parameters__

|Field	| Type	            |Description                    |
|-------|-------------------|-------------------------------|
|formattedInsName|string   |User specific identification generated by Gopocket |
|tradingSymbol   |string   |Refer Trading Symbol in Tables                 |
|exchange	     |string   |Exchange standard id for each scrip|
|segment	     | string  |Position Type |
|token	         | string  |Exchange & Segment |
|product	     | string  |Product type |
|netQty    	     |float    |Average buy price|
|netBuyQty	     |int	   |Total quantity bought|
|netBuyAvgPrice    | string | Net average purchase price per unit considering all buy transactions|                                                                                        
|netBuyAvg         | string | Net average quantity purchased|                                                                                       
|netBuyValue       | string | Total value of all buy transactions|                                                                           
|netSellQty        | string | Net quantity of the asset sold|                                                                              
|netSellAvgPrice   | string | Net average selling price per unit considering all sell transactions|                                                                                         
|netSellAvg        | string | Net average quantity sold|                                                                                    
|netSellValue      | string | Total value of all sell transactions|                                                                                        
|averagePrice      | string | Overall average price of the asset, considering both buy and sell transactions|                                                                                        
|ltp               | string | Last traded price of the asset|                                                                            
|pnl               | string | Overall profit |                                      
|mtm               | string | Mark-to-market value of the position|                                                                       
|pdc               | string | Previous day close price
	|                                                          
|realizedpnl       | string | profit or loss realized from transactions
	|                                                                             
|unrealizedpnl     | string | Potential profit or loss
	|                                                                                     
|multiplier        | string | Multiplier or factor used for the position, if applicable|                                                                                 
|lotSize         |  Null   |Quantity of a single lot        |                                                                               
|tickSize |   String           |   Ticker Size Of The Scrip (in paisa).Tick size is the minimum price change between different bid and offer prices of an asset traded on an exchange platform                   |                                 


## Convert Position

Users can convert their open position from intraday to delivery or delivery to intraday.


__Request Structure__

```
{
    "exchange": "NSE",
    "tradingSymbol": "ABB-EQ",
    "qty": "2",
    "product": "CNC",
    "prevProduct": "MIS",
    "transType": "B",
    "posType": "DAY",
    "orderSource": "WEB"
}
```
__Parameters__


|Field	|           Type	|        Description            |
|-------|-------------------|-------------------------------|
|exchange     |String |  Name of the exchange (NSE, NFO, CDS, MCX)  |                
|tradingSymbol|String |Exchange tradingsymbol of the of the instrument  |                                   
|qty          |String |Quantity to transact       |             
|product      |String |Product code (MIS or CNC or NRML) |    
|prevProduct   | string | Previous product type or category for the transaction|
|transType    |String |BUY or SELL  |                
|posType       | string | Position type, indicating the duration or nature of the position|
|orderSource   | string | Source or platform through which the order was placed|


__Response Structure__

```
{
    "status": "Ok",
    "message": "Success",
    "result": []
}

```
