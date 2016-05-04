## Get

#### URL STRUCTURE

GET https://gateway.gear.mycelium.com/api/address_providers/cashila/legal/:id

#### PARAMETERS (* Required field)

<table>
  <tr>
    <td>id 
    <td>ID of Cashila Address Provider
</table>

#### RETURNS

<table>
  <tr>
    <td>status (string)
    <td>Verification status: &#39;pending&#39;, &#39;rejected&#39; or &#39;verified&#39;
  <tr>
    <td>rejected_reason (string)
    <td>Human-readable reason of rejection if status is &#39;Rejected&#39;
  <tr>
    <td>balance (float)
    <td>Balance in EUR
  <tr>
    <td>user_details (hash)
    <td>User details hash
  <tr>
    <td>user_details/company_name (string)
    <td>Company name
  <tr>
    <td>user_details/organizational_form (string)
    <td>Company organizational form
  <tr>
    <td>user_details/registration_number (string)
    <td>Company registration number
  <tr>
    <td>user_details/address (string)
    <td>Company street address
  <tr>
    <td>user_details/postal_code (string)
    <td>Company postal code
  <tr>
    <td>user_details/city (string)
    <td>Company city
  <tr>
    <td>user_details/country_code (string)
    <td>Company two-letter country code
  <tr>
    <td>bank_account (hash)
    <td>Bank account information
  <tr>
    <td>bank_account/name (string)
    <td>Bank account holder&#39;s name
  <tr>
    <td>bank_account/address (string)
    <td>Bank account holder&#39;s street address
  <tr>
    <td>bank_account/postal_code (string)
    <td>Bank account holder&#39;s postal code
  <tr>
    <td>bank_account/city (string)
    <td>Bank account holder&#39;s city
  <tr>
    <td>bank_account/country_code (string)
    <td>Bank account holder&#39;s two-letter country code
  <tr>
    <td>bank_account/bic (string)
    <td>Bank account BIC
  <tr>
    <td>bank_account/iban (string)
    <td>Bank account IBAN
  <tr>
    <td>documents (hash)
    <td>Documents
  <tr>
    <td>name (string)
    <td>Name of the document
  <tr>
    <td>status (string)
    <td>Verification status of the document: &#39;approved&#39;, &#39;pending&#39; or &#39;not present&#39;
</table>

### Example Request

<table>
  <tr>
    <td>REQUEST
    <td>GET https://gateway.gear.mycelium.com/api/address_providers/cashila/legal/6
  <tr>
    <td>RETURNS
    <td><pre><code>{
  "type": "address_providers_cashila",
  "id": 6,
  "bank_account": {
    "id": "5ea979a7-1699-4df2-acc4-bc44bb3091b6",
    "name": "John Smith",
    "address": "Route de Vonèche 458",
    "postal_code": "6230",
    "city": "Viesville",
    "country_code": "BE",
    "country_name": "Belgium",
    "last_used": "2015-07-01T07:33:03+0000"
  },
  "status": "pending",
  "balance": 3.21,
  "rejected_reason": null,
  "user_details": {
    "first_name": "John",
    "last_name": "Smith",
    "address": "Route de Vonèche 458",
    "postal_code": "6230",
    "city": "Viesville",
    "country_code": "BE"
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
}</code></pre>
</table>

