## Create

#### URL STRUCTURE

POST https://gateway.gear.mycelium.com/api/gateways

#### PARAMETERS (* Required field)

<table>
  <tr>
    <td>name* <i>(String)</i></td>
    <td>Gateway name (will appear on payment page)</td>
  <tr>
    <td>pubkey* <i>(String)</i></td>
    <td>BIP32 public key</td>
  <tr>
    <td>confirmations_required* <i>(Integer)</i></td>
    <td>Bitcoin network confirmations required (0-6)</td>
  <tr>
    <td>orders_expiration_period* <i>(Integer)</i></td>
    <td>Time (in seconds) which is given customer to make payment</td>
  <tr>
    <td>default_currency* <i>(String)</i></td>
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

#### RETURNS

<table>
  <tr>
    <td>id <i>(Integer)</i></td>
    <td>ID of Gateway</td>
  <tr>
    <td>secret <i>(String)</i></td>
    <td>API secret (showed only on creation and regeneration)</td>
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
    <td>POST https://gateway.gear.mycelium.com/api/gateways</td>
  <tr>
    <td>PARAMETERS</td>
    <td><pre><code>{
  &quot;name&quot;: &quot;Test gateway&quot;,
  &quot;pubkey&quot;: &quot;xpub661MyMwAqRbcGTVZXfa6XHb9VHLBZ8BqyGpRdVFryUDEC4TQq1Y9L2r7Am9d5TUGVQfbfMr7PB1jZqY4bSmh34ZprSKwJ9BSGmPnKJPMVZy&quot;,
  &quot;confirmations_required&quot;: 1,
  &quot;orders_expiration_period&quot;: 1000,
  &quot;default_currency&quot;: &quot;USD&quot;
}</code></pre></td>
  <tr>
    <td>RETURNS</td>
    <td><pre><code>{
  "id": 4,
  "name": "Test gateway",
  "confirmations_required": 1,
  "orders_expiration_period": 1000,
  "default_currency": "USD",
  "pubkey": "xpub661MyMwAqRbcGTVZXfa6XHb9VHLBZ8BqyGpRdVFryUDEC4TQq1Y9L2r7Am9d5TUGVQfbfMr7PB1jZqY4bSmh34ZprSKwJ9BSGmPnKJPMVZy",
  "active": true,
  "address_derivation_scheme": "m/0/n",
  "callback_url": null,
  "after_payment_redirect_to": null,
  "auto_redirect": false,
  "city": null,
  "test_pubkey": null,
  "test_mode": false,
  "convert_currency_to": "BTC",
  "country": null,
  "exchange_rate_adapter_names": [
    "Bitstamp",
    "Btce",
    "Kraken",
    "Bitpay"
  ],
  "description": null,
  "merchant_url": null,
  "receive_payments_notifications": false,
  "region": null,
  "locale": null,
  "allow_links": false,
  "secret": "3mjWCKKG6tqDt2Jd7ke6MYc6cGG2txxBFMfT6meCYngpfc3RUNsUirAkvi37ncRq",
  "api_gateway_id": "885edce61f60dd45e8739b7c55d859bd1fe59f36b9624e497704b099ea474779",
  "back_url": null,
  "custom_css_url": null
}</code></pre></td>
</table>

