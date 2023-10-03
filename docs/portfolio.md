---

title: Portfolio

---

# Portfolio

This API lets you retrieve holdings and positions in your portfolio.

|Method	|Api                |Detail                         |
|-------|-------------------|-------------------------------|
|GET	|	/holdings       |Retrieve the list of long term equity holdings|
|GET	| /positions	    |Retrieve the list of short term positions|
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
                    "isin": "INE302A01020",
                    "realizedPnl": "0.0",
                    "unrealizedPnl": "-574.26",
                    "netPnl": "-574.26",
                    "netQty": "3",
                    "buyPrice": "191.42",
                    "holdQty": "0",
                    "dpQty": "0",
                    "benQty": "0",
                    "unpledgedQty": "0",
                    "collateralQty": "0",
                    "brkCollQty": "0",
                    "btstQty": "0",
                    "usedQty": "0",
                    "tradedQty": "0",
                    "sellableQty": "0",
                    "authQty": "0",
                    "sellAmount": "0.0",
                    "symbol": [
                        {
                            "exchange": "NSE",
                            "token": "676",
                            "tradingSymbol": "EXIDEIND-EQ",
                            "pdc": "258.9",
                            "ltp": "258.9"
                        },
                        {
                            "exchange": "BSE",
                            "token": "500086",
                            "tradingSymbol": "EXIDEIND",
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

|Field	|Type	|Description|
|-------|-------------------|-------------------------------|
|isin	|String	|The standard ISIN representing stocks listed on multiple exchanges|
|realizedpnl     |
|buyPrice	|String	|Segment Buy Price|
|totalQty	|string	|  |
|usedQty	|String	|Used Quantity of position / Holdings|
|sellableQt |String	|Sell able quantity of Holding / Position|
|colQty	    |String	|    |
|btstQty	|String	|    |
|authQty	|int	|    |
|authDate	|Null	|    |
|netPnl 	|Int|Net Profit and Loss Value|
|soldValue  |string	||
|benQty     |  Null	||                                                            
|unpledgedQty | string	|  |                                                            
|tmColQty   |   string	|  |                                                            
|dpQty      |   Null	|  |                                                         
|pledgeQty  |   int	|      |                                                              
|dayPnl     |   int	|      |                                                          
|ltp        |String	|Last trade price of the scrip. The price at which the final trade happens between a buyer and a seller|                
|nonPoaQty	    |String	| |
|exDetails	    |List	| |
|symbol	    |String	| |
|exchange	    |String	| |
|token	    |String	| |
|previousClose	    |String	| |

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
|segment	     | string  |Position Type `LONG` `SHORT` `CLOSED`|
|token	         | string  |Exchange & Segment `NSE_EQ`  `NSE_FNO`   `NSE_CURRENCY`  `BSE_EQ`  `MCX_COMM`|
|product	     | string  |Product type `CNC`  `INTRADAY`  `MARGIN`  `CO` `BO`|
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
|lotSize         |  Null   |       |                                                                               
|tickSize        |  Null   |       |                                                                            


## Convert Position
Users can convert their open position from intraday to delivery or delivery to intraday.


__Request Structure__

```
{
    "ClientId": "1000000009",
    "fromProductType":"INTRADAY",
    "exchangeSegment":"NSE_EQ",
    "positionType":"LONG",
    "securityId":"11536",
    "tradingSymbol":"",
    "convertQty":"40",
    "toProductType":"CNC"
}
```
__Parameters__


|Field	| Type	|Description|
|-------|-------------------|-------------------------------|
|ClientId|	string|	User specific identification generated by Gopocket |
|fromProductType|	enum string|	Refer Trading Symbol in Tables `CNC` `INTRADAY` `MARGIN` `CO` `BO`|
|exchangeSegment|	enum string|	Exchange standard id for each scrip `NSE_EQ`  `NSE_FNO`   `NSE_CURRENCY`  `BSE_EQ`  `MCX_COMM`|
|positionType|	enum string|	Position Type `LONG` `SHORT` `CLOSED`|
|securityId|	string|	Exchange standard id for each scrip. Refer here|
|tradingSymbol|	string|	Refer Trading Symbol in Tables|
|convertQty|	int|	No of shares modification is desired|
|toProductType|	enum string|	Desired product type `CNC`  `INTRADAY`  `MARGIN`  `CO` `BO`|

__Response Structure__

```
202 Accepted
```
__Note__: For description of enum values, refer Annexure