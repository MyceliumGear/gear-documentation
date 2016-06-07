## List

#### URL STRUCTURE

GET https://gateway.gear.mycelium.com/api/gateways

#### RETURNS

<table>
  <tr>
    <td>gateways <i>(Array)</i></td>
    <td>Root element is array of hashes</td>
  <tr>
    <td>gateways/id <i>(Integer)</i></td>
    <td>ID of Gateway</td>
  <tr>
    <td>gateways/name <i>(String)</i></td>
    <td>Gateway name (will appear on payment page)</td>
  <tr>
    <td>gateways/pubkey <i>(String)</i></td>
    <td>BIP32 public key</td>
  <tr>
    <td>gateways/confirmations_required <i>(Integer)</i></td>
    <td>Bitcoin network confirmations required (0-6)</td>
  <tr>
    <td>gateways/orders_expiration_period <i>(Integer)</i></td>
    <td>Time (in seconds) which is given customer to make payment</td>
  <tr>
    <td>gateways/default_currency <i>(String)</i></td>
    <td>Currency code (ISO 4217) in which prices are shown to customer</td>
  <tr>
    <td>gateways/active <i>(Boolean)</i></td>
    <td>Whether a gateway can process new orders</td>
  <tr>
    <td>gateways/test_mode <i>(Boolean)</i></td>
    <td>Whether to use testnet for payment processing</td>
  <tr>
    <td>gateways/test_pubkey <i>(String)</i></td>
    <td>BIP32 testnet pulic key (used when test_mode is true)</td>
  <tr>
    <td>gateways/address_derivation_scheme <i>(String)</i></td>
    <td>Address derivation scheme: m/0/n or n</td>
  <tr>
    <td>gateways/callback_url <i>(String)</i></td>
    <td>URL to send server POST notifications of order statuses</td>
  <tr>
    <td>gateways/auto_redirect <i>(Boolean)</i></td>
    <td>Whether to enable redirection on successful payment</td>
  <tr>
    <td>gateways/after_payment_redirect_to <i>(String)</i></td>
    <td>URL to which redirect customers after successful payment (if auto_redirect is true)</td>
  <tr>
    <td>gateways/back_url <i>(String)</i></td>
    <td>URL to which redirect customers on order cancellation</td>
  <tr>
    <td>gateways/convert_currency_to <i>(Integer)</i></td>
    <td>ID of Address Provider which is to process payments, otherwise string &#39;BTC&#39;</td>
  <tr>
    <td>gateways/exchange_rate_adapter_names <i>(Array)</i></td>
    <td>Array of String names of exchange rate adapters. Default: [&quot;Bitstamp&quot;, &quot;Btce&quot;, &quot;Kraken&quot;]</td>
  <tr>
    <td>gateways/receive_payments_notifications <i>(Boolean)</i></td>
    <td>Whether to send email notifications of payments</td>
  <tr>
    <td>gateways/allow_links <i>(Boolean)</i></td>
    <td>Allow links and &lt;a&gt; tags in field values</td>
  <tr>
    <td>gateways/api_gateway_id <i>(Integer)</i></td>
    <td>Straight server gateway ID</td>
  <tr>
    <td>gateways/custom_css_url <i>(String)</i></td>
    <td>URL to CSS file with a payment UI customizations</td>
  <tr>
    <td>gateways/description <i>(Integer)</i></td>
    <td>Description of merchant</td>
  <tr>
    <td>gateways/merchant_url <i>(Integer)</i></td>
    <td>URL of merchant site</td>
  <tr>
    <td>gateways/country <i>(String)</i></td>
    <td>Country of merchant</td>
  <tr>
    <td>gateways/city <i>(String)</i></td>
    <td>City of merchant</td>
  <tr>
    <td>gateways/region <i>(Integer)</i></td>
    <td>Region of merchant</td>
</table>

### Example Request

<table>
  <tr>
    <td>REQUEST</td>
    <td>GET https://gateway.gear.mycelium.com/api/gateways</td>
  <tr>
    <td>RETURNS</td>
    <td><pre><code>[
  {
    "id": 1,
    "name": "Custom Gateway",
    "confirmations_required": 0,
    "orders_expiration_period": 900,
    "default_currency": "BTC",
    "pubkey": "xpub661MyMwAqRbcGAEjBnRud6skEYkgn6HakP9in7r4YVRbe8FfZdwqQdteE4nZX4Dq9bQRQ25KCDiC8qSSkuEc5ecxHbWgNkzvKHqfim99CV5",
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
    "api_gateway_id": "28ae95f29d532f44c111a9b693bdaf10d45703cdfb808aebb1098da43b42fd55",
    "back_url": null,
    "custom_css_url": null
  }
]</code></pre></td>
</table>

