# Coupon
Coupon represents store promotions or discounts created through Capillary Campaign Manager. A single campaign could contain one or more coupons or coupon series. Coupons are issued to loyalty or non-loyalty customers through SMS or email.

You cannot create new coupons using coupon APIs. You can just send or retrieve coupons that are already created in your campaigns. Hence, it is important to note the coupon code, coupon id or coupon series id for making API calls.

You cannot create new coupons using coupon APIs; instead, you can send or retrieve coupons that are already created in your campaigns. Hence, it is important to note the coupon code, coupon id or coupon series id to use coupon APIs.

The V2 coupon entity just allows you to:

* Redeem coupons in batch 
* Check whether specific coupons can be redeemed or not

For any other coupon related APIs, please use v1.1 APIs. 


## Redeem Coupons

> Sample Request

```html
http://api.capillary.co.in/v2/coupon/redeem 

```

> Sample POST Request

```json
{
   "billAmount":"2000",
   "transactionNumber":"numbr9227550121",
   "user":{
      "mobile":"9177121900000"
   },
   "redemptionTime":"2019-04-04 11:49:59",
   "redemptionRequestList":[
      {
         "code":"9NUF8THR"
      }
   ]
}
```


> Sample Response

```json
{
    "redemption": [
        {
            "id": 33138363,
            "warnings": [],
            "appendedErrorMessage": "",
            "code": "JL07UAZ3",
            "discountCode": "MobilePush",
            "seriesCode": 14162,
            "isAbsolute": false,
            "couponValue": 10.0
        }
    ],
    "redemptionStatus": {
        "status": true,
        "code": 700,
        "message": "Coupon processing successful"
    },
    "customer": {
        "id": 342963216,
        "profiles": [
            {
                "firstName": "Tom",
                "lastName": "Sawyer",
                "fields": {},
                "identifiers": [
                    {
                        "type": "mobile",
                        "value": "919999000000"
                    }
                ],
                "commChannels": [],
                "userId": 342963216,
                "accountId": "",
                "autoUpdateTime": "2019-10-31T17:41:25+05:30"
            }
        ]
    },
    "warnings": []
}
```


This API allows you to redeem active coupons of a loyalty customer. You can pass multiple coupons at once.

### Resource Information
| | |
--------- | ----------- |
URI | `coupon/redeem`
Authentication  | Yes
HTTP Method  | POST
Batch Support  | Yes

### Request URL
`http://{host}/v2/coupon/redeem`

### Request Body Parameters
Parameter | Datatype | Description
--------- | -------- | -----------
billAmount* | float | Transaction amount of the bill.
transactionNumber* | string | Transaction number against which the coupon needs to be redeemed
user* | enum | Specify any identifier of the user who wants to redeem coupons. Values: mobile, email, externalId
redemptionTime | date-time | Date and time when the coupon has to be redeemed in `YYYY-MM-DD HH:MM:SS` format.
code* | string | Coupon code to be redeemed.

<aside class="warning"> You need to pass either code or id as applicable </aside>




## Check if Coupon is Redeemable
```html
# Sample Request
http://us.intouch.capillarytech.com/v2/coupon/is_redeemable?mobile=917601000000&code=6B88U6ED,V080OLI6&details=false
```
> Sample Response

```json
{
   "customer":{
      "id":325666373,
      "profiles":[
         {
            "accountId":"",
            "autoUpdateTime":"2019-04-04T11:47:28+05:30",
            "commChannels":[

            ],
            "fields":{

            },
            "firstName":"firstName_667095",
            "identifiers":[
               {
                  "type":"email",
                  "value":"autoemail7601667095@gmail.com"
               },
               {
                  "type":"externalId",
                  "value":"ext_id7601667095"
               },
               {
                  "type":"mobile",
                  "value":"917601667095"
               }
            ],
            "lastName":"lastName_667095",
            "userId":325666373
         }
      ]
   },
   "redemption":[
      {
         "appendedErrorMessage":"",
         "code":"6B88U6ED",
         "isAbsolute":false,
         "isRedeemable":true,
         "numberOfRedemptionsByUser":0,
         "redemptionsLeft":-1,
         "warnings":[

         ]
      },
      {
         "appendedErrorMessage":"",
         "code":"V080OLI6",
         "isAbsolute":false,
         "isRedeemable":true,
         "numberOfRedemptionsByUser":0,
         "redemptionsLeft":-1,
         "warnings":[

         ]
      }
   ],
   "redemptionStatus":{
      "code":700,
      "message":"Coupon isRedeem successful",
      "status":true
   },
   "warnings":[

   ]
}
```

Lets you check whether a set of coupons can be redeemed or not.

### Resource Information
| | |
--------- | ----------- |
URI | `/is_redeemable?{customerIdentifier}&code={value1},{value2}...&details={true/extended}`
Authentication  | Yes
HTTP Method  | GET
Batch Support  | Yes

### Request URL
`http://{host}/v2/coupon/is_redeemable?{customerIdentifier}&code={value1},{value2}...&details={true/extended}`

### Request Query Parameters
Parameter | Datatype | Description
--------- | -------- | -----------
user* | obj | Pass the identifier of the customer to check if his/her coupon is redeemable.
mobile/email/externalId/id* | string | Pass any of the identifiers of the customer.
code* | string | Pass the coupon code that you want to check for redemption. You can also pass multiple coupon codes separating each with a comma `,`
details | boolean | Pass `=true` to retrieve the details of the coupon series.
details=extended | - | Retrieves the details of coupon configurations (set on campaign) of that specific coupon series.

<aside class="warning"> You can pass either coupon ID or coupon code. Any one parameter is required.</aside>






# Coupon Upload


These are not CRM or v2 APIs. Hence, please note that there are changes in all the API details including host and headers. 

**host1**

* **India**: https://intouch.capillary.co.in
* **Apac2**: https://apac2.intouch.capillarytech.com
* **EU**: https://eu.intouch.capillarytech.com
* **China**: https://intouch.capillarytech.cn.com






## Upload Coupons (Batch)

Lets you upload coupons of a specific coupon series in bulk. 
 <aside class="notice">This is not a v2 API. Hence, all the API details including host and headers are provided in this section itself.  </aside>

> Sample Request

```curl
curl -X POST \
  https://eu.intouch.capillarytech.com/coupon/api/v1/upload/file/311025 \
  -H 'Content-Type: application/json' \
  -H 'Postman-Token: 3056825f-5e0d-411e-a83d-e6ce0e6da3d2' \
  -H 'cache-control: no-cache' \
  -H 'content-type: multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW' \
  -H 'x-cap-api-oauth-token: eyJraWQiOiJrMSIsImFsZyI6IlJTMjU2In0.eyJpc3MiOiJDYXBpbGxhcnkiLCJleHAiOjE2MDE5ODY1NzUsImp0aSI6IllzQndtY20xbEh6OGlYNzQ4djI4QXciLCJpYXQiOjE2MDE5ODI5NzUsInN1YiI6IlRFU1RfQ09VUE9OUyIsImNsaWVudF9pZCI6NzgsIm9yZ19pZCI6NTAxMjgsInRva2VuX3VzZSI6InRva2VuX2FjY2VzcyIsImNsaWVudF9rZXkiOiJHY3dmdUFlaEVDOE02NmNBN1RWR05OQ1E0IiwiZGVmYXVsdF90aWxsIjo1MDAwNzM5Miwic2NvcGVzIjoiW3tcInBlcm1pc3Npb25cIjpcIlJFQURXUklURVwiLFwiZW50aXR5SWRcIjoxLFwicmVzb3VyY2VzXCI6W1wiLip2MS4xL2N1c3RvbWVyLy4qXCJdfSx7XCJwZXJtaXNzaW9uXCI6XCJSRUFEV1JJVEVcIixcImVudGl0eUlkXCI6MixcInJlc291cmNlc1wiOltcIi4qdjEuMS90cmFuc2FjdGlvbi8uKlwiXX0se1wicGVybWlzc2lvblwiOlwiUkVBRFdSSVRFXCIsXCJlbnRpdHlJZFwiOjMsXCJyZXNvdXJjZXNcIjpbXCIuKnYxLjEvcG9pbnRzLy4qXCJdfSx7XCJwZXJtaXNzaW9uXCI6XCJSRUFEV1JJVEVcIixcImVudGl0eUlkXCI6NCxcInJlc291cmNlc1wiOltcIi4qXCJdfV0ifQ.YVjVaOWDK_3G_B7TjPyy-QMNGpHbjev7Z_vmOCn07dJZ5sGeQcwUbYBi4RHdeNruggH7SyEKngBRAyFGot3ha3JkdJC1IV9ux6L6xwwfgqthavj6MTV0LhMEy6tRM06LEFtYrN5CuCllJ6yM3hUc25ZZKxyEGxYMflAt65TpK-A3EJDpo8RxrY-XHAitwL_R4m6kSZ2_rxyDC2qyRv6rdkjoLRzZ7urcPTOn37EGIe0TByFRa3LSPpywlMjkTX1wcFSW1z_2XgydfoqGfBAkf8Ng4db9gEr_pP96btnRm6fvoEg0RXdfsflp_LEsWUcExPFEiQvuC5wbo0TXHLOsgA' \
  -F 'file=@/Users/rajshekar.sv/Downloads/couponCode (10).csv' \
  -F customerIdentifier=USER_ID \
  -F customerIdentifierColumn=0
```



> Sample Response

```json
{
   "success":true,
   "status":200,
   "result":{
      "orgId":0,
      "couponSeriesId":123,
      "uploadJobStatuses":[
         {
            "jobId":1,
            "uploadStatus":"STARTED",
            "createdOn":"1601835836973",
            "updatedOn":"1601835836973",
            "errorFileUrl":null,
            "successFileUrl":null,
            "uploadedFileUrl":"couponCode_1601835836573_123.csv",
            "totalUploadedCount":0,
            "actualRowCount":0,
            "errorCount":0,
            "uploadTableName":null,
            "uploadedFileName":"couponCode.csv",
            "audienceGroupId":0,
            "audienceGroupVersionId":0
         }
      ],
      "fileName":"couponCode_1601835836573_123.csv"
   }
}

```




### Resource Information
| | |
--------- | ----------- |
URI | `/coupon/api/v1/upload/file/{couponSeriedId}`
Authentication  | Yes (oAuth)
HTTP Method  | POST
Batch Support  | No

### Request URL
`{host1}/coupon/api/v1/upload/file/{couponSeriedId}`


### Header Required
Header |  Description
--------- | -----------
Content-Type* | multipart/form-data
x-cap-api-oauth-token | Generated authentication token



### Request Query Parameters
Parameter | Datatype | Description
--------- | -------- | -----------
couponSeriesId* | long | Unique ID of the coupon series for which you need to upload coupons.

<aside class="notice">The parameter marked with * is mandatory.</aside>


### Request Body Parameters
Parameter | Datatype | Description
--------- | -------- | -----------
file* | string | Name of the CSV file with customer and coupon details. <br>Sample file content: <br>File content sample for uploading the coupon code is as follows <br>customer_identifier,coupon code<br>value 1,ABCDEF1<br>value 2,ABCDEF2<br>value 3,ABCDEF3<br>File content sample for uploading customer identifier:<br> customerIdentifier<br> value 1<br> value 2<br>value 3<br>File content sample for uploading customer tagged coupons is as follows<br>customerIdentifier,coupon code<br>value 1,ABCDEF1<br>value 2,ABCDEF2<br>value 3,ABCDEF3
customerIdentifier* | enum | Customer identifier type used in the CSV file. Values: `MOBILE`, `EXTERNAL_ID`, `EMAIL`, `USER_ID`, `NOT_TAGGED`. <br>Use `NOT_TAGGED` as the identifier to upload only coupon codes.
customerIdentifierColumn | string | Column ID of the customer identifier in the uploaded CSV file. <br> For example, <br>If the first column of the file contains customer identification data, then the value of customerIdentifierColumn will be 0.<br>If the second column of the file contains customer identification data, then the value of customerIdentifierColumn will be 1.



## Upload Redeemed Coupons

This API lets you bulk upload coupons that are redeemed for a coupon series. This API exposes an endpoint by which coupons that are redeemed externally can be imported into the Capillary CRM system.

> Sample Request

```curl
curl -i -X POST 
https://crm-nightly-new.cc.capillarytech.com/coupon/api/v1/upload/redeemFile/253234 -H 'Content-Type: multipart/form-data' 
-H 'Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpZCI6WyI0Il0sIm9yZ0lEIjowLCJleHAiOjE2MDM4OTIxNTYsImlhdCI6MTYwMzgwNTc1NiwiaXNzIjoiY2FwaWxsYXJ5dGVjaC5jb20iLCJhdWQiOiJjYXBpbGxhcnksaW50b3VjaCxhcnlhLHJlb24sYXBwcyIsInNvdXJjZSI6IldFQkFQUCJ9.APtFDqTh7Yf26lzhmwFm4OwPQBo24E_MTNl6CcnIr9A' 
-F file=@couponCode.csv 
-F customerIdentifier=USER_ID 
-F couponIdentifier=COUPON_ID 
-F uploadHeaders='{"redeemedAt": 1, "billNumber": 5, "couponCode": 3, "userId": 2, "billId": 4, "redeemedDateInMillis": 0, "details": 6}'
```

> Sample Response 

```json
{
   "success":true,
   "status":200,
   "result":{
      "orgId":9619,
      "couponSeriesId":953234,
      "redeemUploadJobStatuses":[
         {
            "jobId":9137,
            "uploadRedeemedCouponStatus":"QUEUED",
            "createdOn":"1603263535389",
            "updatedOn":"1603263535389",
            "errorFileUrl":null,
            "successFileUrl":null,
            "uploadedFileUrl":"couponCode_9603263533789_253294.csv",
            "totalUploadedCount":0,
            "actualRowCount":0,
            "errorCount":0,
            "uploadTableName":null,
            "uploadedFileName":"couponCode_9603263533789_253294.csv"
         }
      ],
      "fileName":"couponCode_9603263533789_253294.csv"
   }
}
```

### Resource Information
| | |
--------- | ----------- |
URI | `/coupon/api/v1/upload/redeemFile/{couponSeriesId}`
Authentication  | [oAuth](https://capillary.github.io/v1.1-API-Documentation/?xml#process-2-oauth)
HTTP Method  | POST
Batch Support  | No

### Request URL
`{host1}/coupon/api/v1/upload/redeemFile/{couponSeriesId}`


### Header Required
Header |  Description
--------- | -----------
Content-Type* | multipart/form-data
x-cap-api-oauth-token | Generated authentication token



### Request Query Parameters
Parameter | Datatype | Description
--------- | -------- | -----------
couponSeriesId* | long | Unique ID of the coupon series for which you need to upload redeemed coupons.

<aside class="notice">The parameter marked with * is mandatory.</aside>


### Request Body Parameters
Parameter | Datatype | Description
--------- | -------- | -----------
customerIdentifier* | enum | Unique identifier of the customer to update redeemed coupons. Values: `MOBILE`, `EXTERNAL_ID`, `EMAIL`, `USER_ID`.
couponIdentifier* | enum | Coupon identifier used. Value: `COUPON_ID`, `COUPON_CODE`.
file* | file | The CSV file that contains information of redeemed coupons. Each row in CSV file can contain following fields(columns marked with * are mandatory).<br/><br/> -  **Customer identifier*** : Field used to identify the customer, it can be userId, mobile, email or externalId. (userId will have more preference over the other customer identifiers, in case of multiple values)<br/> - **Coupon identifier*** : Field used to identify the redeemed coupon, It can be couponId, couponCode. (couponId has more preference over couponCode in case of multiple values)<br/> - **Redeemed date in milliseconds*** : Coupon redeemed time in Epoch<br/> - **Redeemed at*** : Coupon redeemed till’s Id<br/> - **Bill Id** : Transaction Id<br/> - **Bill Number** : Transaction Number Details.<br/><br/>**Sample file content:**<br/> - *File content sample 1*:<br/>&nbsp; &nbsp; &nbsp; &nbsp;redeemed date in millis, redeemed at, user id, coupon id, bill id, bill number, details<br/>&nbsp; &nbsp; &nbsp; &nbsp; 1603128622000,50015497,23599838,23456,1603128596000<br/>&nbsp; &nbsp; &nbsp; &nbsp;luci_auto_15039.<br/> - *File content sample 2*:<br/>&nbsp; &nbsp; &nbsp; &nbsp;redeemed date in millis, redeemed at, mobile, coupon code ,bill id, bill number, details<br/>&nbsp; &nbsp; &nbsp; &nbsp;1603128622000,50015497,9876543210,ABCDEF1,1603128596000<br/>&nbsp; &nbsp; &nbsp; &nbsp;luci_auto_15039
uploadHeaders* | int | The sequence (starts from 0) of the columns in the attached csv file. This field accepts stringified JSON. <br>Key name for columns are as follows:<br/><br/>Key name for the columns are as follows<br/> - **Customer identifier*** : Key name for this field varies according to the customerIdentifier param.<br/>&nbsp; &nbsp; &nbsp; &nbsp;MOBILE : mobile<br/>&nbsp; &nbsp; &nbsp; &nbsp;EXTERNAL_ID: externalId<br/>&nbsp; &nbsp; &nbsp; &nbsp;EMAIL: email<br/>&nbsp; &nbsp; &nbsp; &nbsp;USER_ID: userId<br/> - **Coupon identifier*** :  Key name for this field varies according to the couponIdentifier param.<br/>&nbsp; &nbsp; &nbsp; &nbsp;COUPON_ID: couponId<br/>&nbsp; &nbsp; &nbsp; &nbsp;COUPON_CODE: couponCode<br/> - **Redeemed date in milliseconds*** : redeemedDateInMillis<br/> - **Redeemed at*** : redeemedAt<br/> - **Bill Id** : billId<br/> - **Bill Number** : billNumber<br/> - **Details** : details<br/><br/>For the above file samples, the uploadHeaders will be -<br/>&nbsp; &nbsp; &nbsp; &nbsp;*Sample 1* - {'redeemedDateInMillis': 0, 'redeemedAt': 1, 'billNumber': 5, 'couponId': 3,<br/>&nbsp; &nbsp; &nbsp; &nbsp;'userId': 2, 'billId': 4, 'details': 6}<br/>&nbsp; &nbsp; &nbsp; &nbsp;*Sample 2* - {'redeemedDateInMillis': 0, 'redeemedAt': 1, 'billNumber': 5, 'couponCode': 3,<br/>&nbsp; &nbsp; &nbsp; &nbsp;mobile: 2, 'billId': 4, 'details': 6}
Details | string | Any additional details or notes to capture for redeemed coupon upload.


<aside class="notice"> All parameters marked with * are mandatory. </aside>








## Get Status of Uploaded Coupons

Retrieves the status of a coupon upload job.

> Sample Request

```curl
curl -i -X GET 
https://eu.intouch.capillarytech.com/coupon/api/v1/upload/getUploadStatus/253234 
-H 'Content-Type: application/json' 
-H 'x-cap-api-oauth-token: 

eyJraWQiOiJrMSIsImFsZyI6IlJTMjU2In0.eyJpc3MiOiJDYXBpbGxhcnkiLCJleHAiOjE2MDMyNjQ4NzksImp0aSI6IlBEV0JLRXZCTFh0VUZEdnhvbkFoNFEiLCJpYXQiOjE2MDMyNjQyNzksInN1YiI6InJlZGVtcHRpb24gaW1wb3J0IGNvdXBvbnMiLCJjbGllbnRfaWQiOjEyNjEsIm9yZ19pZCI6MTYxOSwidG9rZW5fdXNlIjoidG9rZW5fYWNjZXNzIiwiY2xpZW50X2tleSI6IldUMFQzcFdpU1JOTGFvdFBrbWFiWGR3VVgiLCJkZWZhdWx0X3RpbGwiOjE1MTQ3MTEwLCJzY29wZXMiOiJbe1wicGVybWlzc2lvblwiOlwiUkVBRFdSSVRFXCIsXCJlbnRpdHlJZFwiOjEsXCJyZXNvdXJjZXNcIjpbXCIuKnYxLjEvY3VzdG9tZXIvLipcIl19LHtcInBlcm1pc3Npb25cIjpcIlJFQURXUklURVwiLFwiZW50aXR5SWRcIjoyLFwicmVzb3VyY2VzXCI6W1wiLip2MS4xL3RyYW5zYWN0aW9uLy4qXCJdfSx7XCJwZXJtaXNzaW9uXCI6XCJSRUFEV1JJVEVcIixcImVudGl0eUlkXCI6MyxcInJlc291cmNlc1wiOltcIi4qdjEuMS9wb2ludHMvLipcIl19LHtcInBlcm1pc3Npb25cIjpcIlJFQURXUklURVwiLFwiZW50aXR5SWRcIjo0LFwicmVzb3VyY2VzXCI6W1wiLipcIl19XSJ9.xZuDQbcoekA7NsRZnNYTo1eIzjMeATccbmiR9lUdTeLZjRo453GqiBhezIfafw6GBYaDkOrJcjJCRscJt2cSlUUi8jw2z1QIuJLYIS2kQ_BFvuOUuc0p3olgyEjPdRNK3gqdD9gfQSK92_o05xLSOM205nBUeFrgaFUjuU30XcxfXOe6J7e61tOMAyxH-7ESAycOO4lo78iaSWpjio33n0rW4ngJ6PwrZQxN14JIrNkOit_r8CuZtqOTwYpF7SbZY9JG1wmYu4MT08J00neUS7j-QU9cgUaJAkd8pzoi6HhaZfpIjPaf3rSvB6doWmofyhDQc0jtVZK1iQqTovSOBg'

```

> Sample Response 

```json
{
   "success":true,
   "status":200,
   "result":{
      "orgId":2345,
      "couponSeriesId":253543,
      "uploadJobStatuses":[
         {
            "jobId":93477,
            "uploadStatus":"FINISHED",
            "createdOn":"1603101625000",
            "updatedOn":"1603101632000",
            "errorFileUrl":"error_1619_2532342020_10_19_15_30_32",
            "successFileUrl":null,
            "uploadedFileUrl":"couponCode_1603101623721_253234.csv",
            "totalUploadedCount":3,
            "actualRowCount":3,
            "errorCount":3,
            "uploadTableName":"temp_1619_20201019_153531582",
            "uploadedFileName":"couponCode.csv",
            "audienceGroupId":0,
            "audienceGroupVersionId":0
         }
      ]
   }
}
```

### Resource Information

| | |
--------- | ----------- |
URI | `coupon/api/v1/upload/getUploadStatus/{couponSeriesId}`
HTTP Method | GET
Authentication | [OAuth](https://capillary.github.io/v1.1-API-Documentation/?xml#process-2-oauth)
API Version | v1
Batch Support | No

### Request Header

| | |
--------- | ----------- |
Content-Type | application/json
x-cap-api-oauth-token | Generated authentication token

### Request URL

`https://{host}/coupon/api/v1/upload/getUploadStatus/{couponSeriesId}` 

### Request Query Parameters

Parameter | Datatype | Description
--------- | -------- | -----------
couponSeriesId* | long |The ID of coupon series for which you want to get the status.

<aside class="notice"> The pParameter marked with * is mandatory. </aside>



## Get Status of Redeemed Coupons 

Retrieves the status of the uploaded coupon redeem job a coupon series.

> Sample Request

```curl
curl -i -X GET 
https://crm-nightly-new.cc.capillarytech.com/coupon/api/v1/upload/getUploadRedeemedCouponStatus/253234 
-H 'Content-Type: application/json' 
-H 'x-cap-api-oauth-token: eyJraWQiOiJrMSIsImFsZyI6IlJTMjU2In0.eyJpc3MiOiJDYXBpbGxhcnkiLCJleHAiOjE2MDMyNjM5MjQsImp0aSI6InlRQmxQS2pvVlhJRmZiM2xjNk9SU2ciLCJpYXQiOjE2MDMyNjMzMjQsInN1YiI6InJlZGVtcHRpb24gaW1wb3J0IGNvdXBvbnMiLCJjbGllbnRfaWQiOjEyNjEsIm9yZ19pZCI6MTYxOSwidG9rZW5fdXNlIjoidG9rZW5fYWNjZXNzIiwiY2xpZW50X2tleSI6IldUMFQzcFdpU1JOTGFvdFBrbWFiWGR3VVgiLCJkZWZhdWx0X3RpbGwiOjE1MTQ3MTEwLCJzY29wZXMiOiJbe1wicGVybWlzc2lvblwiOlwiUkVBRFdSSVRFXCIsXCJlbnRpdHlJZFwiOjEsXCJyZXNvdXJjZXNcIjpbXCIuKnYxLjEvY3VzdG9tZXIvLipcIl19LHtcInBlcm1pc3Npb25cIjpcIlJFQURXUklURVwiLFwiZW50aXR5SWRcIjoyLFwicmVzb3VyY2VzXCI6W1wiLip2MS4xL3RyYW5zYWN0aW9uLy4qXCJdfSx7XCJwZXJtaXNzaW9uXCI6XCJSRUFEV1JJVEVcIixcImVudGl0eUlkXCI6MyxcInJlc291cmNlc1wiOltcIi4qdjEuMS9wb2ludHMvLipcIl19LHtcInBlcm1pc3Npb25cIjpcIlJFQURXUklURVwiLFwiZW50aXR5SWRcIjo0LFwicmVzb3VyY2VzXCI6W1wiLipcIl19XSJ9.plHd64-7bxkse3BIAUR1rz_SjoeeITDcKe675LQOd1okIxggdwP3Tv3Wt7z72Z7O3TiLpzHT_k5lGenuW3Ds7enNfzt3yNRnAPCWpVN-yHXwSQDulJErcGd6iWDId_tKEjy2Ihgy5_a7ZZTDMUiItjqOyaScQZuP-6E4R7YpXSKMNK8_sQdud8SvXNe-oGE9Hgq3yNljMpPzUKtsNIis_Gd__qNxuAZPdOX1mikf1qfK0q-TOmOK7ZDmcl9WCV4IoSQvo7-gNd81rL6qXxtQsMkvixjq_HIq6I2zGuT6s06ZlYD3fe1Sx3p4jUAzpj6ygP-E67nxewaOaiLKW4xLOA'
```

> Sample Response 

```json
{
   "success":true,
   "status":200,
   "result":{
      "orgId":9838,
      "couponSeriesId":909234,
      "redeemUploadJobStatuses":[
         {
            "jobId":4455,
            "uploadRedeemedCouponStatus":"COMPLETED",
            "createdOn":"1603132200000",
            "updatedOn":"1603132200000",
            "errorFileUrl":"error_redemption_upload_1619_2532342020_10_20_14_17_00",
            "successFileUrl":null,
            "uploadedFileUrl":"couponCode_1603183613031_253234.csv",
            "totalUploadedCount":1,
            "actualRowCount":1,
            "errorCount":1,
            "uploadTableName":"temp_redemption_upload_1619_20201020_141700172",
            "uploadedFileName":"couponCode_1603183613081_259234.csv"
         },
         {
            "jobId":4456,
            "uploadRedeemedCouponStatus":"COMPLETED",
            "createdOn":"1603132200000",
            "updatedOn":"1603132200000",
            "errorFileUrl":"error_redemption_upload_1619_2532342020_10_20_17_33_14",
            "successFileUrl":null,
            "uploadedFileUrl":"couponCode_1603195385330_253234.csv",
            "totalUploadedCount":1,
            "actualRowCount":1,
            "errorCount":1,
            "uploadTableName":"temp_redemption_upload_1619_20201020_173313820",
            "uploadedFileName":"couponCode_1603195345330_253564.csv"
         },
         {
            "jobId":4457,
            "uploadRedeemedCouponStatus":"COMPLETED",
            "createdOn":"1603218600000",
            "updatedOn":"1603218600000",
            "errorFileUrl":"error_redemption_upload_1619_2532342020_10_21_12_29_00",
            "successFileUrl":null,
            "uploadedFileUrl":"couponCode_1603263533789_253234.csv",
            "totalUploadedCount":1,
            "actualRowCount":1,
            "errorCount":1,
            "uploadTableName":"temp_redemption_upload_1619_20201021_122859950",
            "uploadedFileName":"couponCode_1603263533789_253234.csv"
         }
      ]
   }
}
```

### Resource Information

| | |
--------- | ----------- |
URI | `/coupon/api/v1/upload/getUploadRedeemedCouponStatus/{couponSeriesId}`
HTTP Method | GET
Authentication | [OAuth](https://capillary.github.io/v1.1-API-Documentation/?xml#process-2-oauth)
API Version | v1
Batch Support | No


### Headers Required

Header | Value
------- | -----
Content-Type* | application/json
x-cap-api-oauth-token* | Generated authentication token


### Request URL

`https://{host}/coupon/api/v1/upload/getUploadRedeemedCouponStatus/{couponSeriesId}` 

### Request Parameters

Parameter | Datatype | Description
--------- | -------- | -----------
couponSeriesId* | int |The ID of coupon series for which the user wants to know the redeem status.

<aside class="notice"> The parameter marked with * is mandatory. </aside>



## Response Codes


Error Codes

Code | Description
---- | -----------
400 | Incorrect or invalid input.
500 | Unable to post or retrieve details.

