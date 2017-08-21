# User Authentication
The userAuth resource allows existing customers of InStore to register on the org's web page/mobile app, authenticate login credentials, and update user details.


## Register Users

```html
# Sample Request
 
https://us.api.capillarytech.com/v2/user_auth/register
```


```json
# Sample POST Request

{
  "mobile": "71000000000",
  "email": "tom.sawyer@example.com",
  "password": "tom123"
}

```

```json
# Sample Response

{
"id": 24335250,
"profiles": [
  {
"firstName": "Tom",
"lastName": "Sawyer",
"attribution": {
"createDate": "2016-06-22T00:00:00+05:30",
"createdBy": {
"code": "org2.till1",



"name": "org2.till1",
"type": "TILL"
},
"modifiedBy": {
"type": "TILL"
},
"modifiedDate": "2016-12-05T13:04:22+05:30"
},
"fields": {},
"identifiers": [
  {
"type": "email",
"value": "autoemail734253194812111111@gmail.com"
},
  {
"type": "externalId",
"value": "ext_id7342531948111"
}
],
"commChannels": [
  {
"type": "email",
"value": "autoemail734253194812111111@gmail.com",
"primary": true,
"verified": false,
"meta": {
"residence": false,
"office": false
},
"attributes": {}
}
],
"source": "INSTORE",
"userId": 24335250,
"accountId": "",
"conflictingProfileList": [],
"autoUpdateTime": "2017-08-04T11:12:14+05:30"
}
],
"loyaltyInfo": {
"loyaltyType": "loyalty",
"attributionV2": {
"createDate": "2016-06-22T00:00:00+05:30",
"createdBy": {
"code": "org2.till1",
"name": "org2.till1",
"type": "TILL"
},
"modifiedBy": {
"type": "TILL"
},
"modifiedDate": "2016-12-05T13:04:22+05:30"
},
"lifetimePurchases": 2000,
"score": 97
},
"segments": {},
"warnings": [],
}


```

Allows an org's InStore customers to register on their web page or mobile app. You need to use only the mobile number/email id that is registered on InStore.

### Request URL

`https://<Respective cluster’s API URL>/v2/user_auth/register

### Request Attributes
Parameter | Description
--------- | -----------
mobile | Specify a valid mobile number of the user that is already registered with your org (in any source)
email | Specify a valid email id of the user that is already registered with your org (in any source)
password | Specify a password for the user account as a MD5 hash



## User Authentication

```html
# Sample Request
 
https://us.api.capillarytech.com/v2/user_auth/authorize_user
```


```json
# Sample POST Request

{
  "mobile": "71000000000",
  "email": "tom.sawyer@example.com",
  "password": "tom1234"
}

```

```json
# Sample Response


```

Validates whether the provided user credentials are valid or not.

### Request URL

`https://<Respective cluster’s API URL>/v2/user_auth/authorize_user

### Request Attributes
Parameter | Description
--------- | -----------
mobile | Provide the registered mobile number of the user
email | Provide the registered email id of the user
password | Provice the password in md5 hash form




## Update Password

```html
# Sample Request
 
https://us.api.capillarytech.com/v2/user_auth/update
```


```json
# Sample POST Request

{
  "mobile": "71000000000",
  "email": "tom.sawyer@example.com",
  "password": "tom12345"
}

```

```json
# Sample Response


```

Allows updating password of an user account.

### Request URL

`https://<Respective cluster’s API URL>/v2/user_auth/update`


### Request Attributes
Parameter | Description
--------- | -----------
mobile | Provide the registered mobile number of the user
email | Provide the registered email id of the user
password | Provice the new password in md5 hash form


