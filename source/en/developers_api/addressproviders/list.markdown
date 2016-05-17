## List

Returns list of address providers as array of hashes. Each element of the array
        contains ID of address provider and its type (e.g. &#39;address_provider_cashila&#39;).

#### URL STRUCTURE

GET https://gateway.gear.mycelium.com/api/address_providers

#### RETURNS

<table>
  <tr>
    <td>address_providers <i>(Array)</i></td>
    <td>Root element is array of hashes</td>
  <tr>
    <td>address_providers/id <i>(Integer)</i></td>
    <td>ID of Address Provider</td>
  <tr>
    <td>address_providers/type <i>(String)</i></td>
    <td>Type of Address Provider</td>
</table>

### Example Request

<table>
  <tr>
    <td>REQUEST</td>
    <td>GET https://gateway.gear.mycelium.com/api/address_providers</td>
  <tr>
    <td>RETURNS</td>
    <td><pre><code>[
  {
    "type": "address_providers_cashila",
    "id": 1
  }
]</code></pre></td>
</table>

