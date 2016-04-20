## Creating Cashila address provider (individual entity)

### POST api/address_providers/cashila/

### Parameters

| Name | Description
| ---  | ---
| **user_details** | **Individual entity**
| email | String
| first_name | String
| last_name | String
| address | String
| postal_code | String
| city | String
| country_code | String
| **user_details** | **Legal entity**
| email | String
| address | String
| postal_code | String
| city | String
| country_code | String
| company_name | String
| organizational_form | String
| registration_number | String
| **documents** | **Individual entity**
| gov_id_front | File
| gov_id_back | File
| residence | File
| **documents** | **Legal entity**
| company | Array of Files
| **bank_account** | **Bank account**
| name | String
| address | String
| postal_code | String
| city | String
| country_code | String
| bic | String
| iban | String

### Request

#### Route

<pre>POST api/address_providers/cashila/</pre>

#### Body

<pre>------------XnJLe9ZIbbGUYtzPQJ16u1
Content-Disposition: form-data; name="entity"

individual
------------XnJLe9ZIbbGUYtzPQJ16u1
Content-Disposition: form-data; name="user_details[first_name]"

Example
------------XnJLe9ZIbbGUYtzPQJ16u1
Content-Disposition: form-data; name="user_details[last_name]"

Xample
------------XnJLe9ZIbbGUYtzPQJ16u1
Content-Disposition: form-data; name="user_details[address]"

somewhere
------------XnJLe9ZIbbGUYtzPQJ16u1
Content-Disposition: form-data; name="user_details[postal_code]"

000000
------------XnJLe9ZIbbGUYtzPQJ16u1
Content-Disposition: form-data; name="user_details[city]"

Vilnius
------------XnJLe9ZIbbGUYtzPQJ16u1
Content-Disposition: form-data; name="user_details[country_code]"

LT
------------XnJLe9ZIbbGUYtzPQJ16u1
Content-Disposition: form-data; name="documents[gov_id_front]"; filename="multipass.jpg"
Content-Type: 
Content-Length: 11068

[uploaded data]
------------XnJLe9ZIbbGUYtzPQJ16u1
Content-Disposition: form-data; name="documents[gov_id_back]"; filename="multipass.jpg"
Content-Type: 
Content-Length: 11068

[uploaded data]
------------XnJLe9ZIbbGUYtzPQJ16u1
Content-Disposition: form-data; name="documents[residence]"; filename="multipass.jpg"
Content-Type: 
Content-Length: 11068

[uploaded data]
------------XnJLe9ZIbbGUYtzPQJ16u1
Content-Disposition: form-data; name="bank_account[name]"

Tester
------------XnJLe9ZIbbGUYtzPQJ16u1
Content-Disposition: form-data; name="bank_account[address]"

Main sq.
------------XnJLe9ZIbbGUYtzPQJ16u1
Content-Disposition: form-data; name="bank_account[postal_code]"

123456
------------XnJLe9ZIbbGUYtzPQJ16u1
Content-Disposition: form-data; name="bank_account[city]"

The City
------------XnJLe9ZIbbGUYtzPQJ16u1
Content-Disposition: form-data; name="bank_account[country_code]"

BE
------------XnJLe9ZIbbGUYtzPQJ16u1
Content-Disposition: form-data; name="bank_account[bic]"

DEUTDEMM760
------------XnJLe9ZIbbGUYtzPQJ16u1
Content-Disposition: form-data; name="bank_account[iban]"

BE15573680538458
------------XnJLe9ZIbbGUYtzPQJ16u1--</pre>

### Response

#### Status

<pre>200 OK</pre>

#### Body

<pre>{
  "type": "address_providers_cashila",
  "id": 4,
  "bank_account": {
    "id": "5ea979a7-1699-4df2-acc4-bc44bb3091b6",
    "name": "Example Xample",
    "address": "somewhere",
    "postal_code": "000000",
    "city": "Vilnius",
    "country_code": "LT",
    "country_name": "Lithuania",
    "last_used": "2015-07-01T07:33:03+0000"
  },
  "status": "pending",
  "balance": 3.21,
  "rejected_reason": null,
  "user_details": {
    "first_name": "Example",
    "last_name": "Xample",
    "address": "somewhere",
    "postal_code": "000000",
    "city": "Vilnius",
    "country_code": "LT"
  },
  "documents": [
    {
      "name": "gov_id_front",
      "status": "not present"
    },
    {
      "name": "gov_id_back",
      "status": "not present"
    },
    {
      "name": "residence",
      "status": "not present"
    }
  ]
}</pre>
## Creating Cashila address provider (login with API token and secret)

### POST api/address_providers/cashila/login

### Parameters

| Name | Description
| ---  | ---
| email | Email
| password | Password
| token | API token
| secret | API secret

### Request

#### Route

<pre>POST api/address_providers/cashila/login</pre>

#### Body

<pre>{"token":"e414d696-296f-4e10-97b3-3bbaecbe150e","secret":"cTxm2TGBULSxssEXdLc2TM9FK7pqTzVg9LWDCy/BXVy/YmEkg7XrxsrcaWUpSo/6Q+76ZZTLq0IcGmMDFEeRvw=="}</pre>

### Response

#### Status

<pre>200 OK</pre>

#### Body

<pre>{
  "type": "address_providers_cashila",
  "id": 11,
  "bank_account": {
  },
  "status": "pending",
  "balance": 3.21,
  "rejected_reason": null,
  "user_details": {
  },
  "documents": [
    {
      "name": "gov_id_front",
      "status": "not present"
    },
    {
      "name": "gov_id_back",
      "status": "not present"
    },
    {
      "name": "residence",
      "status": "not present"
    }
  ]
}</pre>
## Creating Cashila address provider (login with email and password)

### POST api/address_providers/cashila/login

### Parameters

| Name | Description
| ---  | ---
| email | Email
| password | Password
| token | API token
| secret | API secret

### Request

#### Route

<pre>POST api/address_providers/cashila/login</pre>

#### Body

<pre>{"email":"alerticus+cashila@gmail.com","password":"q1w2e3r4"}</pre>

### Response

#### Status

<pre>200 OK</pre>

#### Body

<pre>{
  "type": "address_providers_cashila",
  "id": 9,
  "bank_account": {
  },
  "status": "pending",
  "balance": 3.21,
  "rejected_reason": null,
  "user_details": {
    "email": "alerticus+cashila@gmail.com"
  },
  "documents": [
    {
      "name": "gov_id_front",
      "status": "not present"
    },
    {
      "name": "gov_id_back",
      "status": "not present"
    },
    {
      "name": "residence",
      "status": "not present"
    }
  ]
}</pre>
## Getting Cashila address provider

### GET api/address_providers/cashila/:id

### Parameters

| Name | Description
| ---  | ---
| id | ID of Provider


### Response Fields

| Name | Description
| ---  | ---
| status | String, &#39;pending&#39;, &#39;rejected&#39; or &#39;verified&#39;
| rejected_reason | String, reason of rejection if status is &#39;Rejected&#39;
| balance | Float, Balance in EUR
| **bank_account** | **Bank account**
| name | String
| address | String
| postal_code | String
| city | String
| country_code | String
| bic | String
| iban | String
| **user_details** | **Individual Entity**
| first_name | String
| last_name | String
| address | String
| postal_code | String
| city | String
| country_code | String
| **documents** | **Documents**
| name | String
| status | String, &#39;approved&#39;, &#39;pending&#39; or &#39;not present&#39;

### Request

#### Route

<pre>GET api/address_providers/cashila/2</pre>

### Response

#### Status

<pre>200 OK</pre>

#### Body

<pre>{
  "type": "address_providers_cashila",
  "id": 2,
  "bank_account": {
    "id": "5ea979a7-1699-4df2-acc4-bc44bb3091b6",
    "name": "Example Xample",
    "address": "somewhere",
    "postal_code": "000000",
    "city": "Vilnius",
    "country_code": "LT",
    "country_name": "Lithuania",
    "last_used": "2015-07-01T07:33:03+0000"
  },
  "status": "pending",
  "balance": 3.21,
  "rejected_reason": null,
  "user_details": {
    "first_name": "Example",
    "last_name": "Xample",
    "address": "somewhere",
    "postal_code": "000000",
    "city": "Vilnius",
    "country_code": "LT"
  },
  "documents": [
    {
      "name": "gov_id_front",
      "status": "not present"
    },
    {
      "name": "gov_id_back",
      "status": "not present"
    },
    {
      "name": "residence",
      "status": "not present"
    }
  ]
}</pre>
## Updating Cashila address provider

### PUT api/address_providers/cashila/:id

See Creating Cashila address provider for parameters description
### Request

#### Route

<pre>PUT api/address_providers/cashila/7</pre>

#### Body

<pre>{"entity":"individual","user_details":{"first_name":"Changed","last_name":"Xample","address":"somewhere","postal_code":"000000","city":"Vilnius","country_code":"LT"},"documents":{},"bank_account":{"name":"Changed","address":"Main sq.","postal_code":"123456","city":"The City","country_code":"BE","bic":"DEUTDEMM760","iban":"BE34865837743072"}}</pre>

### Response

#### Status

<pre>200 OK</pre>

#### Body

<pre>{
  "type": "address_providers_cashila",
  "id": 7,
  "bank_account": {
    "id": "2556de7c-a511-463b-aea5-246a40429ddb",
    "name": "Changed",
    "address": "Main sq.",
    "postal_code": "123456",
    "city": "The City",
    "country_code": "BE",
    "country_name": "Belgium",
    "last_used": "2016-02-25T16:00:07+0000",
    "iban": "BE34865837743072",
    "bic": "DEUTDEMM760"
  },
  "status": "pending",
  "balance": 3.21,
  "rejected_reason": null,
  "user_details": {
    "first_name": "Changed",
    "last_name": "Xample",
    "address": "somewhere",
    "postal_code": "000000",
    "city": "Vilnius",
    "country_code": "LT"
  },
  "documents": [
    {
      "name": "gov_id_front",
      "status": "not present"
    },
    {
      "name": "gov_id_back",
      "status": "not present"
    },
    {
      "name": "residence",
      "status": "not present"
    }
  ]
}</pre>
## Withdraw funds with Cashila Address Provider

### POST api/address_providers/cashila/:id/withdraw

### Parameters

| Name | Description
| ---  | ---
| amount | Float, amount to withdraw in EUR

### Request

#### Route

<pre>POST api/address_providers/cashila/13/withdraw</pre>

#### Body

<pre>{"amount":0.2}</pre>

### Response

#### Status

<pre>200 OK</pre>

#### Body

<pre>{
  "type": "address_providers_cashila",
  "id": 13,
  "bank_account": {
  },
  "status": "pending",
  "balance": 3.21,
  "rejected_reason": null,
  "user_details": {
    "first_name": "Example",
    "last_name": "Xample",
    "address": "somewhere",
    "postal_code": "000000",
    "city": "Vilnius",
    "country_code": "LT"
  },
  "documents": [
    {
      "name": "gov_id_front",
      "status": "not present"
    },
    {
      "name": "gov_id_back",
      "status": "not present"
    },
    {
      "name": "residence",
      "status": "not present"
    }
  ]
}</pre>
