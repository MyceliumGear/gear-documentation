## Create

#### URL STRUCTURE

POST https://gateway.gear.mycelium.com/api/address_providers/cashila/individual

#### PARAMETERS (* Required field)

<table>
  <tr>
    <td>user_details (hash) *
    <td>User details hash
  <tr>
    <td>user_details/first_name (string) *
    <td>User&#39;s first name
  <tr>
    <td>user_details/last_name (string) *
    <td>User&#39;s last name
  <tr>
    <td>user_details/address (string) *
    <td>User&#39;s street address
  <tr>
    <td>user_details/postal_code (string) *
    <td>User&#39;s postal code
  <tr>
    <td>user_details/city (string) *
    <td>User&#39;s city
  <tr>
    <td>user_details/country_code (string) *
    <td>User&#39;s two-letter country code
  <tr>
    <td>user_details/email (email) 
    <td>User email (Gear registration email by default)
  <tr>
    <td>bank_account (hash) *
    <td>Bank account information
  <tr>
    <td>bank_account/name (string) *
    <td>Bank account holder&#39;s name
  <tr>
    <td>bank_account/address (string) *
    <td>Bank account holder&#39;s street address
  <tr>
    <td>bank_account/postal_code (string) *
    <td>Bank account holder&#39;s postal code
  <tr>
    <td>bank_account/city (string) *
    <td>Bank account holder&#39;s city
  <tr>
    <td>bank_account/country_code (string) *
    <td>Bank account holder&#39;s two-letter country code
  <tr>
    <td>bank_account/bic (string) *
    <td>Bank account BIC
  <tr>
    <td>bank_account/iban (string) *
    <td>Bank account IBAN
  <tr>
    <td>documents (hash) 
    <td>Documents
  <tr>
    <td>documents/gov_id_front (file) *
    <td>Government ID (front side)
  <tr>
    <td>documents/gov_id_back (file) 
    <td>Government ID (back side)
  <tr>
    <td>documents/residence (file) *
    <td>Proof of Residence
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
    <td>user_details/first_name (string)
    <td>User&#39;s first name
  <tr>
    <td>user_details/last_name (string)
    <td>User&#39;s last name
  <tr>
    <td>user_details/address (string)
    <td>User&#39;s street address
  <tr>
    <td>user_details/postal_code (string)
    <td>User&#39;s postal code
  <tr>
    <td>user_details/city (string)
    <td>User&#39;s city
  <tr>
    <td>user_details/country_code (string)
    <td>User&#39;s two-letter country code
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
    <td>POST https://gateway.gear.mycelium.com/api/address_providers/cashila/individual
  <tr>
    <td>PARAMETERS
    <td><pre><code>{
  &quot;bank_account&quot;: {
    &quot;name&quot;: &quot;John Smith&quot;,
    &quot;address&quot;: &quot;9253 Crescent Street&quot;,
    &quot;postal_code&quot;: &quot;13090&quot;,
    &quot;city&quot;: &quot;Liverpool&quot;,
    &quot;country_code&quot;: &quot;BE&quot;,
    &quot;bic&quot;: &quot;BOFABE3X&quot;,
    &quot;iban&quot;: &quot;BE15573680538458&quot;
  },
  &quot;user_details&quot;: {
    &quot;first_name&quot;: &quot;John&quot;,
    &quot;last_name&quot;: &quot;Smith&quot;,
    &quot;address&quot;: &quot;Route de Vonèche 458&quot;,
    &quot;postal_code&quot;: &quot;6230&quot;,
    &quot;city&quot;: &quot;Viesville&quot;,
    &quot;country_code&quot;: &quot;BE&quot;
  },
  &quot;documents&quot;: {
    &quot;gov_id_front&quot;: &quot;[uploaded data]&quot;,
    &quot;gov_id_back&quot;: &quot;[uploaded data]&quot;,
    &quot;residence&quot;: &quot;[uploaded data]&quot;
  }
}</code></pre>
  <tr>
    <td>RETURNS
    <td><pre><code>{
  "type": "address_providers_cashila",
  "id": 4,
  "bank_account": {
    "id": "fc460f63-29e2-4196-a676-66b26b04a2ce",
    "name": "John Smith",
    "address": "9253 Crescent Street",
    "postal_code": "13090",
    "city": "Liverpool",
    "country_code": "BE",
    "country_name": "Belgium",
    "last_used": "2016-04-29T11:23:44+0000",
    "iban": "BE15573680538458",
    "bic": "BOFABE3X"
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

