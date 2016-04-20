## Creating Cashila address provider (individual entity)

### POST api/address_providers/cashila/

### Parameters

Name : user_details
Description : Individual entity

Name : email
Description : String

Name : first_name
Description : String

Name : last_name
Description : String

Name : address
Description : String

Name : postal_code
Description : String

Name : city
Description : String

Name : country_code
Description : String

Name : user_details
Description : Legal entity

Name : email
Description : String

Name : address
Description : String

Name : postal_code
Description : String

Name : city
Description : String

Name : country_code
Description : String

Name : company_name
Description : String

Name : organizational_form
Description : String

Name : registration_number
Description : String

Name : documents
Description : Individual entity

Name : gov_id_front
Description : File

Name : gov_id_back
Description : File

Name : residence
Description : File

Name : documents
Description : Legal entity

Name : company
Description : Array of Files

Name : bank_account
Description : Bank account

Name : name
Description : String

Name : address
Description : String

Name : postal_code
Description : String

Name : city
Description : String

Name : country_code
Description : String

Name : bic
Description : String

Name : iban
Description : String

### Request

#### Headers

<pre>Accept: application/json
Content-Type: multipart/form-data; boundary=----------XnJLe9ZIbbGUYtzPQJ16u1
X-Client: authorize.me@example.org
Host: example.org
Cookie: </pre>

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

#### Headers

<pre>X-Frame-Options: SAMEORIGIN
X-XSS-Protection: 1; mode=block
X-Content-Type-Options: nosniff
Content-Type: application/json; charset=utf-8
ETag: W/&quot;d15faaba757b27569892748475114048&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 5cbfaba4-6dcb-428a-a3c0-988438b5fb7b
X-Runtime: 1.485210
Content-Length: 627</pre>

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

Name : email
Description : Email

Name : password
Description : Password

Name : token
Description : API token

Name : secret
Description : API secret

### Request

#### Headers

<pre>Accept: application/json
Content-Type: application/json
X-Client: authorize.me@example.org
Host: example.org
Cookie: </pre>

#### Route

<pre>POST api/address_providers/cashila/login</pre>

#### Body

<pre>{"token":"e414d696-296f-4e10-97b3-3bbaecbe150e","secret":"cTxm2TGBULSxssEXdLc2TM9FK7pqTzVg9LWDCy/BXVy/YmEkg7XrxsrcaWUpSo/6Q+76ZZTLq0IcGmMDFEeRvw=="}</pre>

### Response

#### Headers

<pre>X-Frame-Options: SAMEORIGIN
X-XSS-Protection: 1; mode=block
X-Content-Type-Options: nosniff
Content-Type: application/json; charset=utf-8
ETag: W/&quot;2d29240e913c5d134eb7ed66e95f53cd&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 23594620-151b-409d-84b9-c50c97f2e612
X-Runtime: 0.033336
Content-Length: 288</pre>

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

Name : email
Description : Email

Name : password
Description : Password

Name : token
Description : API token

Name : secret
Description : API secret

### Request

#### Headers

<pre>Accept: application/json
Content-Type: application/json
X-Client: authorize.me@example.org
Host: example.org
Cookie: </pre>

#### Route

<pre>POST api/address_providers/cashila/login</pre>

#### Body

<pre>{"email":"alerticus+cashila@gmail.com","password":"q1w2e3r4"}</pre>

### Response

#### Headers

<pre>X-Frame-Options: SAMEORIGIN
X-XSS-Protection: 1; mode=block
X-Content-Type-Options: nosniff
Content-Type: application/json; charset=utf-8
ETag: W/&quot;bf6c0ae7e2f433021f5ef813d56ec997&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: a4fe3992-0443-480d-8c0b-268486c4a82c
X-Runtime: 0.036033
Content-Length: 324</pre>

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

Name : id
Description : ID of Provider


### Response Fields

Name : status
Description : String, &#39;pending&#39;, &#39;rejected&#39; or &#39;verified&#39;

Name : rejected_reason
Description : String, reason of rejection if status is &#39;Rejected&#39;

Name : balance
Description : Float, Balance in EUR

Name : name
Description : String

Name : address
Description : String

Name : postal_code
Description : String

Name : city
Description : String

Name : country_code
Description : String

Name : bic
Description : String

Name : iban
Description : String

Name : first_name
Description : String

Name : last_name
Description : String

Name : address
Description : String

Name : postal_code
Description : String

Name : city
Description : String

Name : country_code
Description : String

Name : name
Description : String

Name : status
Description : String, &#39;approved&#39;, &#39;pending&#39; or &#39;not present&#39;

### Request

#### Headers

<pre>Accept: application/json
Content-Type: application/json
X-Client: authorize.me@example.org
Host: example.org
Cookie: </pre>

#### Route

<pre>GET api/address_providers/cashila/2</pre>

### Response

#### Headers

<pre>X-Frame-Options: SAMEORIGIN
X-XSS-Protection: 1; mode=block
X-Content-Type-Options: nosniff
Content-Type: application/json; charset=utf-8
ETag: W/&quot;3068dfa89cb15317baf547c2a6827e51&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: a23cece4-ab3d-46ff-8fa6-51a396b1d2f3
X-Runtime: 0.059514
Content-Length: 627</pre>

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

#### Headers

<pre>Accept: application/json
Content-Type: application/json
X-Client: authorize.me@example.org
Host: example.org
Cookie: </pre>

#### Route

<pre>PUT api/address_providers/cashila/7</pre>

#### Body

<pre>{"entity":"individual","user_details":{"first_name":"Changed","last_name":"Xample","address":"somewhere","postal_code":"000000","city":"Vilnius","country_code":"LT"},"documents":{},"bank_account":{"name":"Changed","address":"Main sq.","postal_code":"123456","city":"The City","country_code":"BE","bic":"DEUTDEMM760","iban":"BE34865837743072"}}</pre>

### Response

#### Headers

<pre>X-Frame-Options: SAMEORIGIN
X-XSS-Protection: 1; mode=block
X-Content-Type-Options: nosniff
Content-Type: application/json; charset=utf-8
ETag: W/&quot;3e8e06694b430242b3d62292204e2643&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: acaff16d-823b-438d-b81e-95c00be3915a
X-Runtime: 0.312457
Content-Length: 664</pre>

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

Name : amount
Description : Float, amount to withdraw in EUR

### Request

#### Headers

<pre>Accept: application/json
Content-Type: application/json
X-Client: authorize.me@example.org
Host: example.org
Cookie: </pre>

#### Route

<pre>POST api/address_providers/cashila/13/withdraw</pre>

#### Body

<pre>{"amount":0.2}</pre>

### Response

#### Headers

<pre>X-Frame-Options: SAMEORIGIN
X-XSS-Protection: 1; mode=block
X-Content-Type-Options: nosniff
Content-Type: application/json; charset=utf-8
ETag: W/&quot;6ef78ae01ee930da9a096b965c1ec260&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 05df5c12-ae0c-4263-b487-b289b172beb1
X-Runtime: 0.019996
Content-Length: 413</pre>

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
