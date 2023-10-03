---
title: Introduction
---

# Introduction

## Getting Started

![Image](assets/images/intro.svg)

Gopocket OpenAPI 1.0 is a collection of fast, high performing, low complexity and easy to understand trading APIs for you, the retail traders to build state of the art financial platforms which can be used for trading, investment, wealth generation, automation of trading strategies & execute algo based strategies

It is a set of REST-like APIs that provide integration with our trading eco-system. You can Execute, Modify and Cancel Orders in real time, Manage Portfolio, access Live Market data feeds and Order status stream, view Funds & Balances, and build much more in the Capital Market space with our Open APIs.

Gopocket APIs offer resource-based URLs that accept JSON or form-encoded requests. The response is returned as JSON-encoded by using Standard HTTP response codes unless explicitly stated otherwise. The service calls are platform independent. To Jumpstart your development, toolkits are available in several Programming languages. Please click here.

## Libraries & SDKs

Below is a list of pre-built client libraries for Gopocket Open APIs developed in popularly used programming languages that can be used to interact with the APIs without having to make raw HTTP calls

- Python library (Official)
- JAVA SDK (Official)
- NodeJS SDK
- C# SDK

**Base URL**

The Base URL is the common URL used as a prefix for all API calls.

__https://web.gopocket.in/auth-rest/__

## API Versions

The current stable version of the Gopocket Open API is 1.0 and was last updated on Feb 1, 2023. All requests go to it by default. It is recommended that a specific version be requested explicitly for production applications as major releases may break older implementations. Major changes in the API will be released with new versions.

## Login

### For FinTech

**Registration as Partner:**

Partner login mechanisms are on-demand APIs provided by Gopocket to build innovative financial products to generate wealth via Investment or Trading such as Algo Trading, Portfolio Management and Trading Products. When the Gopocket customer logs in to Partner’s portal

**Registration as a Vendor:**

To register as a Vendor, Please visit [web.gopocket.in](https://web.gopocket.in/developers/)

1.  Login using your  credentials.
2.  In the Apps sections, Create a new application.
3.  Fill out the mandatory details.
4.  Click "Save" to create a new app.
5.  An App Code (appCode) and API Secret (apiSecret) will be provided to the Vendor. This code is important and Confidential. DO NOT Share with anyone outside your organization.​
6.  The App will be activated by Gopocket Admin team after reviewing the details given by the Vendor. The Vendor API access will be provided after necessary approval

**Implementation of SSO**

1.  During User login, the Vendor should redirect the Gopocket user to [https://web.gopocket.in/?appcode]()= along with the App Code as shown here in the url.
2.  User will be asked to login with their Gopocket credentials
3.  After sucessful login, the user will be redirected to the URL provided by the Vendor (Provisions to provide / update the Redirect URL is provided in the Developers Login) along with User Authorization token (authCode) and User ID (userId).
4.  The Vendor will save the user authCode, UserId (userId) along with apiSecret to create a checkSum, which is the SHA-256 hash of userId + authCode + apiSecret
5.  Vendor should send this checkSum to the URL : [https://web.gopocket.in/am/sso/vendor/auth/getUserDetails]() to get the User Session (userSession), which can be used to access all API end points.

### For Individual Traders

Individual traders can directly get their Access Token from web.Gopocket.co,subject to eligibility. The eligibility criteria to get Access Token is minimum 25 trading orders executed in the last 30days and this is inclusive of Futures, Options, Commodity, Currency & Equity-Intraday. Here's how to get your Access Token:

- Login to [web.gopocket.in](https://web.gopocket.in)
- Click on My Profile and navigate to Gopocket login page

**Gopocket Trading APIs and Access'**

## Rate Limit

| Rate Limit | Order Apise | Data Apis      | Non Trading Apis |
| ---------- | ----------- | -------------- | ---------------- |
| Per second | 25          | 10 Cash        | 100              |
| Per minute | 250         | 1000 & Options | 500              |
| Per hour   | 500         | 5000           | 1000             |
| Per day    | 5000        | 10000          | 5000             |

<!-- ### For Individual Developers:

 __Response Structure__

All GET and DELETE request parameters go as query parameters, and POST and PUT parameters as form-encoded (application/x-www-form-urlencoded) parameters, responses from the API are always JSON.

__Successful request:__


HTTP/1.1 200 OK

Content-Type: application/json
``` yaml
{
"status":"success",
"data":{}
}

```
All responses from the API server are JSON with the content-type application/json unless explicitly stated otherwise. A successful 200 OK response always has a JSON response body with a status key with the value success. The data key contains the full response payload.

__Failed request:__

HTTP/1.1 500 Server error

Content-Type: application/json
``` yaml
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

### Exceptions and errors

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

<!-- ## Structure
All GET and DELETE request parameters go as query parameters, and POST and PUT parameters as form-encoded. User has to input an access token in the header for every request.
``` yaml
curl --request POST \
--url https://api..co/orders \
--header 'Content-Type: application/json' \
--header 'access-token: JWT' \
--data '{Request JSON}'
```

## Errors

Error responses come with the error code and message generated internally by the system. The sample structure of error response is shown below.
``` yaml
{
    "errorCode": "",
    "httpStatus": "",
    "internalErrorCode": "",
    "internalErrorMessage": ""
} -->

 <!-- ## Version & API Endpoint: 

 The current stable version of the Gopocket Open API is 1.0 and was last updated on Feb 1, 2023. All requests go to it by default. It is recommended that a specific version be requested explicitly for production applications as major releases may break older implementations. Major changes in the API will be released with new versions.



__STEP 1:__     [https://auth.Gopocket.co/partner/generate-consent]()

Partner need to add partner_id & partner_secret in the header. The response of this flow will have consent-id. Use this consent-id for the next browser based flow.

__STEP 2:__     [https://auth.Gopocket.co/consent-login?consentId=<i>&lt;consentId&gt;</i>]()

This flow will terminate on a partner's server with URL *<partner-redirect-url>*?tokenid=*<tokenId>*. Use this token-id in the next GET call.

__STEP 3:__     [https://auth.Gopocket.co/partner/consume-consent?tokenId=<i>&lt;token-Id&gt;</i>]()

In this step, you need to add partner_id & partner_secret in header again.
This flow will end with end user details like ClientId, UCC, PoA status etc..


**For Individual Traders**

Individual traders can directly get their Access Token from web.Gopocket.co,subject to eligibility. The eligibility criteria to get Access Token is minimum 25 trading orders executed in the last 30days and this is inclusive of Futures, Options, Commodity, Currency & Equity-Intraday. Here's how to get your Access Token:


* Python library (Official)
* JAVA SDK (Official)
* NodeJS SDK 
* C# SDK 





## Structure
All GET and DELETE request parameters go as query parameters, and POST and PUT parameters as form-encoded. User has to input an access token in the header for every request.
``` yaml
curl --request POST \
--url https://api.Gopocket.co/orders \
--header 'Content-Type: application/json' \
--header 'access-token: JWT' \
--data '{Request JSON}'
```

## Errors

Error responses come with the error code and message generated internally by the system. The sample structure of error response is shown below.
``` yaml
{
    "errorCode": "",
    "httpStatus": "",
    "internalErrorCode": "",
    "internalErrorMessage": ""
}
``` -->

<!--

### Generate API Key


# API Overflow

The following diagram depicts the API authentication flow. After receiving the encryption key, user has to generate SHA-256 encrypted key to get User Session ID. To achieve this, the user has to encrypt the combination of User iD, API key and Encryption Key. Sending this to the API will provide a valid Session ID. Use the session ID in authorization header for all further API calls. If there are any issues found, like unauthorized access or invalid session, user can re-generate session id by using the same set of process described above.


# API Overflow

Every request except "authentication" should be appended with Authorization header having Bearer token as below -->
