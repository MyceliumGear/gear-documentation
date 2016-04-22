## Cashila Address Provider: Show
### GET api/address_providers/cashila/:id

Retrieve data and status of Cashila Address Provider.

Could be used, primarily, to obtain verification status:

* The `status` field of response object is `'verified'` if Cashila accepted and verified data of the user (name, address, documents).
* Status is `'pending'` if verification is in-progress (Cashila staff is working on the process).
* Status is `'rejected'` if Cashila rejected user data. Human-readable rejection reason will be provided in `'rejected_reason'`.

Cashila Address Provider could be assigned to Gateway (see [Gateways](/docs/reference/gateways/overview)) if and only if `status` if `'verified'`.

`bank_account` hash of response object will contain bank account data, as described in [Cashila Address Providers Overview](/docs/reference/cashila_address_provider/overview).

`user_details` hash of response object differs, depending on whether given Cashila Address Provider was created as Individual Entity or as Legal Entity, as described in [Cashila Address Providers Overview](/docs/reference/cashila_address_provider/overview).

### Parameters

| Name           | Type    | Description
| ---            | ---     | ---
|**id** *(in URI)* | Integer | ID of Cashila Address Provider

**in bold** - required fields

*in URI* - parameter should be inserted in request URI, instead of request body

### Response Fields

<table>
  <tr>
    <th style="width: 24%">Name
    <th style="width: 15%">Type
    <th>Description
  </tr>
  <tr>
    <td>status
    <td>String
    <td>Verification status. <code>'verified'</code>, <code>'pending'</code> or <code>'rejected'</code>
  </tr>
  <tr>
    <td>rejected_reason
    <td>String
    <td>Human-readable rejection reason. Present only if <code>status</code> is <code>'rejected'</code>.
  </tr>
  <tr>
    <td>balance
    <td>Float
    <td>Balance of account in EUR
  </tr>
  <tr>
    <td>bank_account{}
    <td>Hash
    <td><a href="/docs/reference/cashila_address_provider/overview">Bank Account hash</a>
  </tr>
  <tr>
    <td>user_details{}
    <td>Hash
    <td><a href="/docs/reference/cashila_address_provider/overview">User Details hash</a>
  </tr>
  <tr>
    <td>documents{}
    <td>Hash
    <td><a href="/docs/reference/cashila_address_provider/overview">Documents hash</a>
  </tr>
</table>  

### Example

<pre>GET api/address_providers/cashila/2</pre>

Response Body:

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
