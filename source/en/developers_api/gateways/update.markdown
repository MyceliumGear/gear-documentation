## Update

#### URL STRUCTURE

PUT https://gateway.gear.mycelium.com/api/gateways/:id

#### PARAMETERS (* Required field)

<table>
  <tr>
    <td>id* <i>(Integer)</i></td>
    <td>ID of Gateway</td>
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
    <td>PUT https://gateway.gear.mycelium.com/api/gateways/5</td>
  <tr>
    <td>PARAMETERS</td>
    <td><pre><code>{
  &quot;name&quot;: &quot;Another Gateway&quot;,
  &quot;city&quot;: &quot;Nadym&quot;,
  &quot;convert_currency_to&quot;: 16,
  &quot;default_currency&quot;: &quot;EUR&quot;,
  &quot;test_mode&quot;: true,
  &quot;test_pubkey&quot;: &quot;tpubDBdtUgft1TY5rVpxE4A37hF7EasC1YQU4YgZEs99q5ckSjh6DUeeZWCWcbLe1GaVjJhDtcLavnrVX5vRQsEtF3ZFxGgs6i8t8pQbCqzC821&quot;
}</code></pre></td>
  <tr>
    <td>RETURNS</td>
    <td><pre><code>{
  "id": 5,
  "name": "Another Gateway",
  "confirmations_required": 0,
  "orders_expiration_period": 900,
  "default_currency": "EUR",
  "pubkey": "xpub661MyMwAqRbcEaJ7A42ZsAeGmpPbJ7GoRsWc8k4U27ywFtyzNWrG9J93K1CH9N6GkF2PkuTwg3XZvb4T5nBDSvwGRrbarhX7sjiNdLPsec3",
  "active": true,
  "address_derivation_scheme": "m/0/n",
  "callback_url": "http://0.0.0.0/my_store_callback",
  "after_payment_redirect_to": "http://0.0.0.0/after_payment",
  "auto_redirect": false,
  "city": "Nadym",
  "test_pubkey": "tpubDBdtUgft1TY5rVpxE4A37hF7EasC1YQU4YgZEs99q5ckSjh6DUeeZWCWcbLe1GaVjJhDtcLavnrVX5vRQsEtF3ZFxGgs6i8t8pQbCqzC821",
  "test_mode": true,
  "convert_currency_to": 16,
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
  "api_gateway_id": "7429b19ee4700810101f9b199fe7511f68a4f1ef1a7cd43fe66ed8ea8d91d453",
  "back_url": null,
  "custom_css_url": null
}</code></pre></td>
</table>

