# Points
Points represent loyalty points issued to customers through Loyalty+, Engage+, GoodWill (Member Care), or Data Import. Customers can redeem the points within the validity period and can also transfer their points to other loyalty customers.

## Check if Points Transferrable

Checks if specific points of a customer can be transferred to an other customer. You can also issue OTP that is used to authenticate customer to transfer points (`pointsTransfer` API).



> Sample Request

```html
https://eu.api.capillarytech.com/v2/points/isTransferrable

```

> Sample POST Request

```json
{
  "pointsTobeTransferred": 10,
  "groupProgramTransfer": "false",
  "fromCustomerIdentifier": {
    "type": "MOBILE",
    "value": "7799497290"
  },
  "toCustomerIdentifier": {
    "type": "ID",
    "value": "342953257"
  },
  "issueOtp": true
}
```


> Sample Response

```json
{ 
   "data":[ 
      { 
         "pointsTobeTransferred":10,
         "transferFrom":{ 
            "id":32429961,
            "profiles":[ 
               { 
                  "firstName":"Tom",
                  "lastName":"Sawyer",
                  "attribution":{ 
                     "createDate":"2018-03-05T15:52:47+05:30",
                     "createdBy":{ 
                        "id":15041276,
                        "code":"org2.till1",
                        "name":"org2.till1",
                        "type":"TILL"
                     },
                     "modifiedBy":{ 
                        "id":15041276,
                        "code":"org2.till1",
                        "name":"org2.till1",
                        "type":"TILL"
                     },
                     "modifiedDate":"2019-08-14T12:48:31+05:30"
                  },
                  "fields":{ 

                  },
                  "identifiers":[ 
                     { 
                        "type":"mobile",
                        "value":"919111111111"
                     }
                  ],
                  "commChannels":[ 
                     { 
                        "type":"mobile",
                        "value":"919111111111",
                        "primary":true,
                        "verified":false,
                        "meta":{ 
                           "residence":false,
                           "office":false
                        },
                        "attributes":{ 

                        }
                     }
                  ],
                  "source":"INSTORE",
                  "userId":32429961,
                  "accountId":"",
                  "conflictingProfileList":[ 

                  ],
                  "autoUpdateTime":"2019-09-24T02:29:31+05:30"
               }
            ],
            "loyaltyInfo":{ 
               "loyaltyType":"loyalty",
               "attributionV2":{ 
                  "createDate":"2018-03-05T15:52:47+05:30",
                  "createdBy":{ 
                     "id":15041276,
                     "code":"org2.till1",
                     "name":"org2.till1",
                     "type":"TILL"
                  },
                  "modifiedBy":{ 
                     "id":15041276,
                     "code":"org2.till1",
                     "name":"org2.till1",
                     "type":"TILL"
                  },
                  "modifiedDate":"2019-08-14T12:48:31+05:30"
               }
            },
            "segments":{ 

            },
            "extendedFields":{ 

            }
         },
         "transferTo":{ 
            "id":342953257,
            "profiles":[ 
               { 
                  "firstName":"autofn_9294476894",
                  "lastName":"autoln_9294476894",
                  "attribution":{ 
                     "createDate":"2019-09-18T16:40:10+05:30",
                     "createdBy":{ 
                        "id":15041276,
                        "code":"org2.till1",
                        "name":"org2.till1",
                        "type":"TILL"
                     },
                     "modifiedBy":{ 
                        "id":15041276,
                        "code":"org2.till1",
                        "name":"org2.till1",
                        "type":"TILL"
                     },
                     "modifiedDate":"2019-09-18T16:40:10+05:30"
                  },
                  "fields":{ 

                  },
                  "identifiers":[ 
                     { 
                        "type":"email",
                        "value":"james.f@example.com"
                     },
                     { 
                        "type":"mobile",
                        "value":"919294111111"
                     },
                     { 
                        "type":"externalId",
                        "value":"ext_id92944768"
                     }
                  ],
                  "commChannels":[ 
                     { 
                        "type":"email",
                        "value":"james.f@example.com",
                        "primary":true,
                        "verified":false,
                        "meta":{ 
                           "residence":false,
                           "office":false
                        },
                        "attributes":{ 

                        }
                     },
                     { 
                        "type":"mobile",
                        "value":"919294476894",
                        "primary":true,
                        "verified":false,
                        "meta":{ 
                           "residence":false,
                           "office":false
                        },
                        "attributes":{ 

                        }
                     }
                  ],
                  "source":"INSTORE",
                  "userId":342953257,
                  "accountId":"",
                  "conflictingProfileList":[ 

                  ],
                  "autoUpdateTime":"2019-09-24T02:29:31+05:30"
               }
            ],
            "loyaltyInfo":{ 
               "loyaltyType":"loyalty",
               "attributionV2":{ 
                  "createDate":"2019-09-18T16:40:10+05:30",
                  "createdBy":{ 
                     "id":15041276,
                     "code":"org2.till1",
                     "name":"org2.till1",
                     "type":"TILL"
                  },
                  "modifiedBy":{ 
                     "id":15041276,
                     "code":"org2.till1",
                     "name":"org2.till1",
                     "type":"TILL"
                  },
                  "modifiedDate":"2019-09-18T16:40:10+05:30"
               }
            },
            "segments":{ 

            },
            "extendedFields":{ 

            }
         },
         "transferrable":true
      }
   ],
   "warnings":[ 

   ],
   "errors":[ 

   ]
}

```



### Resource Information
| | |
--------- | ----------- |
URI | `/isTransferrable`
Rate Limited? | No
Authentication | Yes
Response Formats | JSON
HTTP Methods | POST
Batch Support | No

* **Rate limiter** controls the number of incoming and outgoing traffic of a network
* **Authentication** verifies the identity of the current user or integration. See Introduction > Authentication (Merchant Setup on Admin Portal) for more details

### Request URL

`https://{host}/v2/points/isTransferrable`


### Request Body Parameters

Parameter | Type | Description
-------- | ----- | -----------
pointsTobeTransferred* | int | Number of points that customer wants to transfer.
fromCustomerIdentifier* | obj | Details of source customer - customer that wants to transfer points.
toCustomerIdentifier* | obj | Details of destination customer - customer to whom the points have to be transferred.
type* | enum | Customer identifier type. Values: `ID` (user id of the customer), `MOBILE`, `EXTERNAL_ID`, `EMAIL`.
value* | string | The value of the specified identifier.
issueOtp** | Boolean | Sends OTP to the fromCustomer if the specified points are transferrable. Use this to issue OTP (used to authenticate `fromCustomer` to transfer points) if `isPointsTransferrable` is successful. If `false` (default value) then no OTP is generated. **However, you cannot transfer points without OTP. You need  to only pass `issueOtp` as `true` to transfer points**.  

<aside class="notice"> All parameters marked by * are mandatory. </aside>



## Reverse Redeemed Points

Lets you reverse a set of points that are redeemed in a transaction. For example, you can use this API to reverse points redeemed for a transaction if the transaction is returned.

Prerequisites:

The following configurations are required for `points/reverse` API

* Enable Allow_points_redemption_reversal config on EMF settings. Only the back-end team has access to this page. Please raise a ticket to enable the config.
* Enable V2 API as points reversal is supported only V2.0.

> Sample Request

```html
https://eu.api.capillarytech.com/v2/points/reverse
```

> Sample POST Request

```json
{
"redemptionId":"54ZNkA",
"pointsToBeReversed": 10,
"identifier":
	{
	"type":"mobile",
	"value":"919740000000"
	}
}

```

> Sample Response

```json
{
    "redemptionId": "54ZNkA",
    "pointsToBeReversed": 20.0,
    "orgId": 100458,
    "identifier": {
        "type": "mobile",
        "value": "919740000000"
    },
    "customerId": 98662653,
    "pointsReversed": 20.0,
    "reversalId": "5wyOZM",
    "warnings": []
}  
```



### Resource Information
| | |
--------- | ----------- |
URI | `/reverse`
Rate Limited? | No
Authentication | Yes
HTTP Methods | POST
Batch Support | No

* **Rate limiter** controls the number of incoming and outgoing traffic of a network
* **Authentication** verifies the identity of the current user or integration. See Introduction > Authentication (Merchant Setup on Admin Portal) for more details

### Request URL

`https://{host}/v2/points/reverse`

### Request Body Parameters

Parameter | Type | Description
--------- | ---- | -----------
redemptionId* | long | Unique reference ID generated for redeeming the points. 
Identifier | obj | Customer details associated to the redemption.
type* | enum | Pass any of  the registered identifiers of the customer. Supported values: mobile, email, externalId.
value* | string | Pass the respective identifier value. This should match with the identifier tagged to the redemption id
pointsToBeReversed | int | The number of points be reversed.

<aside class="notice">All parameters marked by * are mandatory. </aside>





## Transfer Points

Transfers points from one customer account to another customer account by validating the OTP issued for the points transfer.

<aside class="notice">Only 'fromCustomer' and points are validated currently. `toCustomer` validation will be fixed in the next release.</aside>

> Sample Request

```html
https://eu.api.capillarytech.com/v2/points/transfer
```

> Sample POST Request

```json
{ 
   "pointsTobeTransferred":123,
   "groupProgramTransfer": "false",
   "fromCustomerIdentifier":{ 
      "type":"MOBILE",
      "value":"7799000000"
   },
   "toCustomerIdentifier":{ 
      "type":"ID",
      "value":"342953257"
   },
   "notes":"Transfer points to James",
   "code":"X12Y3Z"
}
```

> Sample Response

```json
{ 
   "data":[ 
      { 
         "pointsTransferDate":"2019-10-16 15:53:42",
         "pointsTransferred":15.0,
         "transferId":100,
         "transferType":"DEDUCTION",
         "transferredFrom":{ 
            "userId":343015431,
            "firstName":"Tom",
            "lastName":"Sawyer"
         },
         "transferredTo":{ 
            "userId":342953257,
            "firstName":"James",
            "lastName":"Thomas"
         },
         "notes":"Transfer points to James",
         "programName":"Nightly_ApiAutoDefaultProgram"
      }
	  ]
}
	  
```



### Resource Information
| | |
--------- | ----------- |
URI | `/transfer`
Rate Limited? | No
Authentication | Yes
Response Formats | JSON
HTTP Methods | POST
Batch Support | No

* **Rate limiter** controls the number of incoming and outgoing traffic of a network
* **Authentication** verifies the identity of the current user or integration. See Introduction > Authentication (Merchant Setup on Admin Portal) for more details

### Request URL

`https://{host}/v2/points/transfer`

### Request Body Parameters

Parameter | Type | Description
--------- | ---- | -----------
pointsTobeTransferred* | int | Number of points to be transferred.
fromCustomerIdentifier* | obj | Details of source customer - customer that wants to transfer points.
toCustomerIdentifier* | obj | Details of destination customer - customer to whom the points have to be transferred.
type* | enum | Customer identifier type. Values: `ID` (user id of the customer), `MOBILE`, `EXTERNAL_ID`, `EMAIL`.
value* | string | The value of the specified identifier.
notes | string | Specify the reason or any notes for this points transfer.
code* | string | Pass the OTP received by the `fromCustomer` for the current points transfer. To issue OTP, use either `/isPointsTransferrable` or `/issuePointsTransferOtp`.

<aside class="notice">All parameters marked by * are mandatory. </aside>



## Error Codes

Code | Description
---- | -----------
412 | Configuration key `CONF_FRAUD_STATUS_CHECK_POINTS_TRANSFER`in the `config_keys` table is not set properly.
413 | Problem fetching the configuration key `CONF_FRAUD_STATUS_CHECK_POINTS_TRANSFER`
414 | Destination customer status is fraud. Points cannot be transferred to customers with fraud status. 
415 | Source customer status is fraud. Points cannot be transferred by customers with fraud status.
416 | Points related validation failed from Thrift.
417 | Customer with fraud status exists.
418 | From and To customers are same.
419 | Merged customer found with id: {x}, where x is the user id of the customer.
686 | User is from campaign and has not enrolled in the loyalty program. Points redemption is not applicable for the user.
804 | Insufficient current points.
805 | Insufficient lifetime points.
806 | Insufficient lifetime purchases amount.
807 | Redemptions points not divisible.
809 | Customer is marked as fraud.
818 | Current points are less than points requested for redemption.
819 | Points to redeem exceeds the threshold limit (maximum points that can be redeemed in a transaction).
821 | Points you are trying to redeem are less than the minimum points allowed.
886 | Unable to process points. Please try again later.
887 | Unable to process points. Please try again later.
888 | Invalid configuration. Please report to capillary support.
895 | Loyalty program is not configured for the  org.
896 | Unable to process points. Please try again later.
898 | Unable to process points. Please try again later.
899 | Invalid configuration. Please report to capillary support.
901 | Invalid points or points redemption Id passed.
902	| Redemption ID does not exist.
903 | Unable to redeem points.
904 | Invalid customer details passed.