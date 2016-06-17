## Get

#### URL STRUCTURE

GET https://gateway.gear.mycelium.com/api/gateways/:id

#### PARAMETERS (* Required field)

<table>
  <tr>
    <td>id* <i>(Integer)</i></td>
    <td>ID of Gateway</td>
</table>

#### RETURNS

<table>
  <tr>
    <td>id <i>(Integer)</i></td>
    <td>ID of Gateway</td>
  <tr>
    <td>name <i>(String)</i></td>
    <td>Gateway name (will appear on payment page)</td>
  <tr>
    <td>pubkey <i>(String)</i></td>
    <td>BIP32 public key</td>
  <tr>
    <td>confirmations_required <i>(Integer)</i></td>
    <td>Bitcoin network confirmations required (0-6)</td>
  <tr>
    <td>orders_expiration_period <i>(Integer)</i></td>
    <td>Time (in seconds) which is given customer to make payment</td>
  <tr>
    <td>default_currency <i>(String)</i></td>
    <td>Currency code (ISO 4217) in which prices are shown to customer</td>
  <tr>
    <td>active <i>(Boolean)</i></td>
    <td>Whether a gateway can process new orders</td>
  <tr>
    <td>test_mode <i>(Boolean)</i></td>
    <td>Whether to use testnet for payment processing</td>
  <tr>
    <td>test_pubkey <i>(String)</i></td>
    <td>BIP32 testnet pulic key (used when test_mode is true)</td>
  <tr>
    <td>address_derivation_scheme <i>(String)</i></td>
    <td>Address derivation scheme: m/0/n or n</td>
  <tr>
    <td>callback_url <i>(String)</i></td>
    <td>URL to send server POST notifications of order statuses</td>
  <tr>
    <td>auto_redirect <i>(Boolean)</i></td>
    <td>Whether to enable redirection on successful payment</td>
  <tr>
    <td>after_payment_redirect_to <i>(String)</i></td>
    <td>URL to which redirect customers after successful payment (if auto_redirect is true)</td>
  <tr>
    <td>back_url <i>(String)</i></td>
    <td>URL to which redirect customers on order cancellation</td>
  <tr>
    <td>convert_currency_to <i>(Integer)</i></td>
    <td>ID of Address Provider which is to process payments, otherwise string &#39;BTC&#39;</td>
  <tr>
    <td>exchange_rate_adapter_names <i>(Array)</i></td>
    <td>Array of String names of exchange rate adapters. Default: [&quot;Bitstamp&quot;, &quot;Btce&quot;, &quot;Kraken&quot;]</td>
  <tr>
    <td>receive_payments_notifications <i>(Boolean)</i></td>
    <td>Whether to send email notifications of payments</td>
  <tr>
    <td>allow_links <i>(Boolean)</i></td>
    <td>Allow links and &lt;a&gt; tags in field values</td>
  <tr>
    <td>api_gateway_id <i>(Integer)</i></td>
    <td>Straight server gateway ID</td>
  <tr>
    <td>custom_css_url <i>(String)</i></td>
    <td>URL to CSS file with a payment UI customizations</td>
  <tr>
    <td>description <i>(Integer)</i></td>
    <td>Description of merchant</td>
  <tr>
    <td>merchant_url <i>(Integer)</i></td>
    <td>URL of merchant site</td>
  <tr>
    <td>country <i>(String)</i></td>
    <td>Country of merchant</td>
  <tr>
    <td>city <i>(String)</i></td>
    <td>City of merchant</td>
  <tr>
    <td>region <i>(Integer)</i></td>
    <td>Region of merchant</td>
</table>

### Example Request

<table>
  <tr>
    <td>REQUEST</td>
    <td>GET https://gateway.gear.mycelium.com/api/gateways/2</td>
  <tr>
    <td>RETURNS</td>
    <td><pre><code>{
  "id": 2,
  "name": "Custom Gateway",
  "confirmations_required": 0,
  "orders_expiration_period": 900,
  "default_currency": "BTC",
  "pubkey": "xpub661MyMwAqRbcGuDMvxmtujoT8iirPUbrq9CApyVQpTpbxkFSBwNo1qubb4sYP63wD8X8NnDf4N8aKRpoa5P4PGb1H6q7rA3p9kiJn3aagva",
  "active": true,
  "address_derivation_scheme": "m/0/n",
  "callback_url": "http://0.0.0.0/my_store_callback",
  "after_payment_redirect_to": "http://0.0.0.0/after_payment",
  "auto_redirect": false,
  "city": "Mogadishu",
  "test_pubkey": null,
  "test_mode": false,
  "convert_currency_to": "BTC",
  "country": "Somalia",
  "exchange_rate_adapter_names": [
    "Bitpay",
    "Coinbase",
    "Bitstamp",
    "Bitpay"
  ],
  "description": "Yet another gateway",
  "merchant_url": "http://mystore.com",
  "receive_payments_notifications": false,
  "region": "Central Somalia",
  "locale": null,
  "allow_links": false,
  "secret": null,
  "api_gateway_id": "aa0fd3ff43f468a28383edb93f8b32e315327f9772faf6b14f3a2ee6bd726a7b",
  "back_url": null,
  "custom_css_url": null
}</code></pre></td>
</table>

