# Customer Walkin

## Trigger Customer Walkin Notifiction in InStore 

```html
# Sample Request

https://us.api.capillarytech.com/v2/customer/walkin?till_code=kn.003&identifierName=mobile&identifierValue={{mobile1}}&source=INSTORE
```

```json
# Sample Response

{
   "entity": "Customer checkin successfull",
   "warnings": [],
   "errors": [],
   "success": true
}
```

Triggers customer walkin notifications on InStore, i.e., when a customer walks in to the store, InStore triggers a desktop notification with the customer details. 

### Request URL

`https://<Respective cluster’s API URL>/v2/customer/walkin?till_code=<till code>&identifierName=<mobile/email/external_id>&identifierValue={{}}&source=<source>
&accountId=<account id>`

### Request Parameters
Parameter | Description
--------- | -----------
till_code | Destination TILL code that you want to push the notification
identifierName | Identifier tracked when the customer walked in. Values: MOBILE, EMAIL, 
identifierValue | The respective identifier value
source | Source in which the customer is identified
accountId | account in which the customer is identified (for sources with multiple account ids)


