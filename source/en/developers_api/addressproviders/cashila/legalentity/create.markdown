## Create

#### URL STRUCTURE

POST https://gateway.gear.mycelium.com/api/address_providers/cashila/legal

#### PARAMETERS (* Required field)

<table>
  <tr>
    <td>user_details (hash) *
    <td>User details hash
  <tr>
    <td>user_details/company_name (string) *
    <td>Company name
  <tr>
    <td>user_details/organizational_form (string) *
    <td>Company organizational form
  <tr>
    <td>user_details/registration_number (string) *
    <td>Company registration number
  <tr>
    <td>user_details/address (string) *
    <td>Company street address
  <tr>
    <td>user_details/postal_code (string) *
    <td>Company postal code
  <tr>
    <td>user_details/city (string) *
    <td>Company city
  <tr>
    <td>user_details/country_code (string) *
    <td>Company two-letter country code
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
    <td>documents/company (array) 
    <td>Array of Files
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
    <td>POST https://gateway.gear.mycelium.com/api/address_providers/cashila/legal
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
    &quot;company_name&quot;: &quot;Gold Image Custom Web Design&quot;,
    &quot;organizational_form&quot;: &quot;LLC&quot;,
    &quot;registration_number&quot;: &quot;123456&quot;,
    &quot;address&quot;: &quot;Route de Vonèche 458&quot;,
    &quot;postal_code&quot;: &quot;6230&quot;,
    &quot;city&quot;: &quot;Viesville&quot;,
    &quot;country_code&quot;: &quot;BE&quot;
  },
  &quot;documents&quot;: {
    &quot;company&quot;: [
      &quot;[uploaded data]&quot;,
      &quot;[uploaded data]&quot;
    ]
  }
}</code></pre>
  <tr>
    <td>RETURNS
    <td><pre><code>{
  "type": "address_providers_cashila",
  "id": 8,
  "bank_account": {
    "id": "1930a6c6-5514-4c4f-82da-ed26806b6a49",
    "name": "John Smith",
    "address": "9253 Crescent Street",
    "postal_code": "13090",
    "city": "Liverpool",
    "country_code": "BE",
    "country_name": "Belgium",
    "last_used": "2016-04-29T12:36:34+0000",
    "iban": "BE15573680538458",
    "bic": "BOFABE3X"
  },
  "status": "pending",
  "balance": 3.21,
  "rejected_reason": null,
  "user_details": {
    "company_name": "Gold Image Custom Web Design",
    "organizational_form": "LLC",
    "registration_number": "123456",
    "address": "Route de Vonèche 458",
    "postal_code": "6230",
    "city": "Viesville",
    "country_code": "BE"
  },
  "documents": null
}</code></pre>
</table>

