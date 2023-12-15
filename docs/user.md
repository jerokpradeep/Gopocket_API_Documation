---

title: User

---

# User

|Type	| Apis|Details	 |
|-------|------|-------------|
|GET| profile/getclientdetails| To get a clientdetails   |
|GET	|funds/limits|	Place a new funds|


## Profile

   While a successful token exchange returns the full user profile, it's possible to retrieve it any point of time with the /user/profile API. Do note that the profile API does not return any of the tokens.

__Response Structure__

``` 
{
    "status": "Ok",
    "message": "Success",
    "result": [
        {
            "userId": "<USER_ID>",
            "actId":  "<ACT_ID>",
            "clientName": "A****h,
            "actStatus": "Activated",
            "createdDate": "1648275191",
            "createdTime": "0",
            "mobNo": "123******9",
            "email": "ak****@gmail.com",
            "pan": "*******76N",
            "address": "AA",
            "officeAddress": "NTC",
            "city": "",
            "state": "",
            "mandateIdList": [],
            "exchange": [
                "NSE",
                "NFO",
                "CDS",
                "MCX",
                "NIPO"
            ],
            "bankdetails": null,
            "dpAccountNumber": [
                {
                    "dpAccountNumber": "1209280000003265"
                }
            ],
            "orders": [
                "MKT",
                "LMT",
                "SL-LMT",
                "SL-MKT",
                "DS"
            ],
            "branchId": "FLMK",
            "brokerName": "SKY",
            "products": [
                "C",
                "M",
                "I",
                "H",
                "B"
            ],
            "productTypes": [
                "CNC",
                "NRML",
                "MIS",
                "Cover",
                "Bracket"
            ],
            "orderTypes": null,
            "priceTypes": [
                "MKT",
                "L",
                "SL",
                "SL-M"
            ]
        }
    ]
}
``` 

__Parameters__

|Field	|Type	|Description|
|-|-|-|
|userId          |String |  The unique, permanent user ID registered with the broker  |                                   
|actId           |String |  The unique, permanent user ID registered with the broker  |                             
|clientName      |String |           |                           
|actStatus       |String |           |                       
|createdDate     |String |           |                                
|createdTime     |String |           |                                   
|mobNo           |String |           |                         
|email           |String |           |                       
|pan             |String |           |                             
|address         |String |           |                             
|officeAddress   |String |           |                                   
|city            |String |           |                           
|state           |String |           |                           
|mandateIdList   |String |           |                                
|exchange        |String |           |                      
|bankdetails     |String |Account holder Bank Details like Bank address, bank account number, bank name          |                                       
|dpAccountNumber |String |           |            
|orders          |String |           |                                     
|branchId        |String |           |                                       
|brokerName      |String |           |                                       
|products        |String |           |                                   
|productTypes    |String |           |                                        
|orderTypes      |String |           |                                         
|priceTypes      |String |           |                                
                     

## Funds

Get all information of your trading account like balance, margin utilised, collateral, etc.

__Response Structure__

```
{
    "status": "Ok",
    "message": "Success",
    "result": [
        {
            "availableMargin": 0.0,
            "openingBalance": -304.0,
            "marginUsed": 0.0,
            "payin": 0.0,
            "stockPledge": 0.0,
            "holdingSellCredit": 0.0,
            "brokerage": 0.0,
            "exposure": 0.0,
            "span": 0.0,
            "premium": 0.0,
            "unclearedCash": 304.0,
            "payout": 0.0
        }
    ]
}
```

__Parameters__

|Field	|Type	|Description|
|-|-|-|
|availableMargin	|int	|Account Holder's Available Margin is dispalyed|
|openingBalance	|int	|Account Holder's Opening Balance is displayed|
|marginUsed	|int	|Account Holder's Margin Used is displayed|
|payin	|int	|Payin is the funds transferred by the customer from his bank account into his trading account|
|stockPledge	|int	||
|holdingSellCredit	|int	||
|brokerage	|int	||
|exposure	|int	|The exposure margin is charged over and above the SPAN margin, and is usually done so at the discretion of the broker|
|span	|int	|SPAN determines margin requirements based on a global assessment of the one-day risk for a trader's account|
|premium	|int	||
