---
title: Response Structure
---


<!-- # Login
## For Vendors & FinTech Companies: 


Partner login mechanisms are on-demand APIs provided by Nidhi to build innovative financial products to generate wealth via Investment or Trading  such as Algo Trading, Portfolio Management and Trading Products. When the Nidhi customer logs in to Partner’s portal 

### Registration as Partner: 

## Registration as a Vendor:

To register as a Vendor, Please visit [ https://developers.aliceblueonline.com/](https://ant.aliceblueonline.com/?vendor=%3Capp_code%3E)

 1.    Login using your AliceBlue credentials.
 2.    In the Apps sections, Create a new application.
 3.    Fill out the mandatory details.
 4.    Click "Save" to create a new app.
 5.    An App Code (appCode) and API Secret (apiSecret) will be provided to the Vendor. This code is important and Confidential. DO NOT Share with anyone outside your organization.​
 6.    The App will be activated by AliceBlue Admin team   after reviewing the details given by the Vendor. The Vendor API access will be provided after necessary approval 

## Implementation of SSO:

 1.   During User login, the Vendor should redirect the Aliceblue user to [https://ant.aliceblueonline.com/?appcode]()= along with the App Code as shown here in the url.
 2.   User will be asked to login with their AliceBlue credentials
 3.   After sucessful login, the user will be redirected to the URL provided by the Vendor (Provisions to provide / update the Redirect URL is provided in the Developers Login) along with User Authorization token (authCode) and User ID (userId).
4.    The Vendor will save the user authCode, UserId (userId) along with apiSecret to create a checkSum, which is the SHA-256 hash of userId + authCode + apiSecret
5.    Vendor should send this checkSum to the URL : [https://ant.aliceblueonline.com/rest/AliceBlueAPIService/sso/getUserDetails]() to get the User Session (userSession), which can be used to access all API end points. -->


## Response 

All GET and DELETE request parameters go as query parameters, and POST and PUT parameters as form-encoded (application/x-www-form-urlencoded) parameters, responses from the API are always JSON.

## Exceptions

HTTP/1.1 200 OK

Content-Type: application/json
``` 
{
"status":"success",
"data":{}
}

```
All responses from the API server are JSON with the content-type application/json unless explicitly stated otherwise. A successful 200 OK response always has a JSON response body with a status key with the value success. The data key contains the full response payload.

## Errors

HTTP/1.1 500 Server error

Content-Type: application/json
``` 
{
"status":"error",
"message":"Error message",
"error_type":"GeneralException"

}
``` 
A failure response is preceded by the corresponding 40x or 50x HTTP header. The status key in the response envelope contains the value error. The message key contains a textual description of the error and error_type contains the name of the exception. There may be an optional data key with additional payload.

__Data types__

Values in JSON responses are of types string, int, float, or bool.

Timestamp (datetime) strings in the responses are represented in the form yyyy-mm-dd hh:mm:ss, set under the Indian timezone (IST) — UTC+5.5 hours

A date string is represented in the form yyyy-mm-dd.

<!-- ### Exceptions and errors

In addition to the 40x and 50x headers, error responses come with the name of the exception generated internally by the API server. You can define corresponding exceptions in your language or library, and raise them by doing a switch on the returned exception name.

__Example__


HTTP/1.1 500 Server error

Content-Type: application/json

``` yaml
{
   "status":"error",
"message":"Error message",
"error_type":"GeneralException"

}
``` -->

<!-- ## Exceptions & Errors: 

### User Login: 

### For Partners & FinTech Companies: 
 Partner login mechanisms are privileged APIs provided by Nidhi to build innovative financial products to generate wealth via Investment or Trading  such as Algo Trading, Portfolio Management and Trading Products. When the Nidhi customer logs in to Partner’s portal  -->










 

