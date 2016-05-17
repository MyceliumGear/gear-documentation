## Withdraw

#### URL STRUCTURE

POST https://gateway.gear.mycelium.com/api/address_providers/cashila/:id/withdraw

#### PARAMETERS (* Required field)

<table>
  <tr>
    <td>id <i>(Integer)</i></td>
    <td>ID of Cashila Address Provider</td>
  <tr>
    <td>amount <i>(Float)</i></td>
    <td>Amount to withdraw in EUR</td>
</table>

### Example Request

<table>
  <tr>
    <td>REQUEST</td>
    <td>POST https://gateway.gear.mycelium.com/api/address_providers/cashila/15/withdraw</td>
  <tr>
    <td>PARAMETERS</td>
    <td><pre><code>{
  &quot;amount&quot;: 0.2
}</code></pre></td>
  <tr>
    <td>RETURNS</td>
    <td><pre><code>{
  "type": "address_providers_cashila",
  "id": 15,
  "bank_account": {
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
}</code></pre></td>
</table>

