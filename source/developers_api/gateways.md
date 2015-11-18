# Gateways API
It is possible to create, update or get list of all gateways. 

## Create gateway
To create gateway, you need to make **POST** request on `/api/gateways` with body:

Required fields:

- *name*. Name of gateway.
- *pubkey*. The public key of the wallet where you will receive the money.
- *confirmations_required*. The number of required confirmations to consider the transaction successful.
- *orders_expiration_period*. How long the order will be waiting for payment (in seconds). Should be between 0 and 1800. 
- *default_currency*. Default currency which will be shown in orders. 

Optional fields:

- *active*. Is gateways active. Default: true
- *address_derivation_scheme*. Address derivation scheme. Default: "m/0/n"
- *callbackurl*. Callback url, where our sevrer will report on the status of the order
- *afterpayment_redirect_to*. Redirect user to that address after payment (works if `auto_redirect` is true)
- *auto_redirect*. Automatically redirect user after payment. Boolean. Default: false
- *test_pubkey*. Test public key. Useing if `test_mode` is set. 
- *test_mode*. Activate or deactivate test mode. Default: false
- *convert_currency_to*. Can be "BTC", "USD", "EUR". Default: "BTC" 
- *exchange_rate_adapter_names*. Where get exchange rate. Array. Default: ["Bitstamp", "Btce", "Kraken"]
- *description*. 
- *merchant_url*. URL of merchant. 
- *receive_payments_notifications*. Send notifications about new payments to client email. Boolean. Default: false
- *city*. 
- *region*.
- *country*. 
- *locale*. Currently only "EN" locale aviable. Default: "en"
- *allow_links*. Boolean. Default: false

Example:

```json
{
  "data": {
    "type": "gateways",
    "attributes": {
      "name": "Test gateway",
      "pubkey": "xpub",
      "confirmations_required": 1,
      "orders_expiration_period": 1000,
      "default_currency": "USD"
    }
  }
}
``` 

On answer you should get new created object in format:

```json
{
  "data": {
    "type": "gateway",
    "id": 2,
    "attributes": {
      ...
    }
  }
}
```
With status code: **201**

## Update gateway
To update gateway. you need to make **PATCH** request on `/api/gateways` with body:

```json
{
  "data": {
    "type": "gateway",
    "id": 1,
    "attributes": {
      "name": "Production gateways"
    }
  }
}
```
`id` of gateway you wnat to change.
In `attributes` listed fields which you want to change. Others fields will not change.

## Get gateways list
For getting list of all gateways you need to make **GET** request on `/api/gateways` with empty body.

In response you should get:

```json
{
  "data": [
    {
      type: "gateway",
      id: 1,
      attributes: { ... }
    },
    {
      type: "gateway",
      id: 2,
      attributes: { ... }
    }
  ]
}
```
By default returned list limited to 25 records. If you want more, it's possible to send query parameters described in *Pagination* section.

### Pagination
 
Strategy is cursor-based. Option pased as query parameters.

- **page[number]** indicates the current page.
- **page[size]** defines how many maximum items will be in result. Default: 25

Resulted JSON will be with *meta* element on root level with information about pagination.

```json
{
  "meta": {
    "page": {
      "number": 1,
      "size": 25
    }
  }
  "data": { ... }
}
```

Example:

```
https://admin.gear.mycelium.com/api/gateways?page[number]=1&page[size]=5
```
It will show first 5 gateways.
