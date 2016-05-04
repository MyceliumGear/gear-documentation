## List

Returns list of address providers as array of hashes. Each element of the array
        contains ID of address provider and its type (e.g. &#39;address_provider_cashila&#39;).

#### URL STRUCTURE

GET https://gateway.gear.mycelium.com/api/address_providers

#### RETURNS

<table>
  <tr>
    <td>address_providers (array)
    <td>Root element is array of hashes
  <tr>
    <td>address_providers/id (integer)
    <td>ID of Address Provider
  <tr>
    <td>address_providers/type (string)
    <td>Type of Address Provider
</table>

### Example Request

<table>
  <tr>
    <td>REQUEST
    <td>GET https://gateway.gear.mycelium.com/api/address_providers
  <tr>
    <td>RETURNS
    <td><pre><code>[
  {
    "type": "address_providers_cashila",
    "id": 1
  }
]</code></pre>
</table>

