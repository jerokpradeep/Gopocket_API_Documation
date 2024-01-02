---

title: User

---

# User

|Type	| Apis |Details	     |
|-------|------|-------------|
|GET    | client-rest/profile/getclientdetails| To get a clientdetails   |
|GET	| funds-rest/funds/limits|	Get available funds|


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
|-------|--------|-----------|
|userId          |String |  The unique, permanent user ID registered   |                                   
|actId           |String |  The unique, permanent actId registered   |                             
|clientName | String | Name of the client in the system|                         
|actStatus | String | Status of the account|                     
|createdDate | String | Date the record was created|                              
|createdTime | String | Time the record was created|                                 
|mobNo | String | Mobile number associated with the client|                       
|email | String | Email address of the client|                     
|pan | String | PAN (Permanent Account Number) of the client|                           
|address | String | Residential address of the client|                           
|officeAddress | String | Office address of the client|                                 
|city | String | City where the client resides or operates|                         
|state | String | State where the client resides or operates|                         
|mandateIdList | String | List of mandate IDs associated with the client|                              
|exchange | List |List of segments enabled for client|                    
|bankdetails     |String |Account holder Bank Details like Bank address, bank account number, bank name          |                                       
|dpAccountNumber | String | Account number related to the Depository Participant|          
|orders          | String | List or details of client's orders|                                   
|branchId        | String | Identification code for the branch associated|                                     
|brokerName      | String | Name of the broker or brokerage firm|                                     
|products        | String | List or details of products offered or associated|                                 
|productTypes    | String | Types or categories of products|                                      
|orderTypes      | String | Different classifications or types of orders|                                       
|priceTypes      | String | Various price-related classifications or types|                              
                     

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
|availableMargin	|int	|Account Holder's Available Margin |
|openingBalance	|int	|Account Holder's Opening Balance |
|marginUsed	|int	|Account Holder's Margin Used |
|payin	|int	|Payin is the funds transferred by the customer from his bank account into his trading account|
|stockPledge	|int	|  Amount or value pledged against stocks|
|holdingSellCredit	|int	|Credit amount related to holdings set for sale|
|brokerage	|int	|Commission or fee charged by the broker|
|exposure	|int	|The exposure margin is charged over and above the SPAN margin, and is usually done so at the discretion of the broker|
|span	|int	|SPAN determines margin requirements based on a global assessment of the one-day risk for a trader's account|
|premium	|int	|The additional money that investors agree to pay to own a stock|
