---

title: Portfolio

---

# Portfolio

This API lets you retrieve holdings and positions in your portfolio.

|Method	|Api                |Detail                         |
|-------|-------------------|-------------------------------|
|GET	| ho-rest/holdings       |Retrieve the list of long term equity holdings|
|GET	| po-rest/positions	    |Retrieve the list of short term positions|
|POST	|/positions/convert	|Convert intraday to long term or long term to intraday |

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
| ------------- | ------ | ------------------------------------------------------------------------------------------------------ |
|isin|String |                         |                    
|realizedPnl|String |                         |             
|unrealizedPnl|String |                         |           
|netPnl|String |                         |                  
|netQty    	     |String    |Average buy price|
|buyPrice|String |                         |                
|holdQty|String |                         |                 
|dpQty|String |                         |                   
|benQty|String |                         |                  
|unpledgedQty|String |                         |            
|collateralQty|String |                         |           
|brkCollQty|String |                         |              
|btstQty|String |                         |                 
|usedQty|String |                         |                 
|tradedQty|String |                         |               
|sellableQty|String |                         |            
|authQty|String |                         |                
|authFlag|String |                         |               
|sellAmount|String |                         |             
|Symbol|Array |                         |              
|exchange| String |                                |        
|token| String |                                |           
|tradingSymbol| String |                |
|pdc| String |                                |             
|ltp| String |                                |


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
|exchange	     |string   |Exchange standard id for each scrip. Refer here|
|segment	     | string  |Position Type |
|token	         | string  |Exchange & Segment |
|product	     | string  |Product type |
|netQty    	     |float    |Average buy price|
|netBuyQty	     |int	   |Total quantity bought|
|netBuyAvgPrice  |  string |       |                                                                                            
|netBuyAvg       |  string |       |                                                                                           
|netBuyValue     |  string |       |                                                                               
|netSellQty      |  string |       |                                                                                  
|netSellAvgPrice |  string |       |                                                                                             
|netSellAvg      |  string |       |                                                                                        
|netSellValue    |  string |       |                                                                                            
|averagePrice    |  string |       |                                                                                            
|ltp             |  string |       |                                                                                
|pnl             |  string |       |                                           
|mtm             |  string |       |                                                                           
|pdc             |  string |       |                                                              
|realizedpnl     |  string |       |                                                                                 
|unrealizedpnl   |  string |       |                                                                                         
|multiplier      |  string |       |                                                                                     
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
|prevProduct|	string|	   |
|transType    |String |BUY or SELL  |                
|posType|	String|  |
|orderSource|	 string|	  |

__Response Structure__

```
{
    "status": "Ok",
    "message": "Success",
    "result": []
}

```
