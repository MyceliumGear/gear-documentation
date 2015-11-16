# Gateways API
With Gear's developer API, it is possible to create, update or get a list of all gateways. 

## Create gateway
To create a gateway, you need to make a **POST** request to `/api/gateways` with the following body:

Required fields:

  - *name*. Name of your gateway.
  - *pubkey*. Public key (xpub) exported from the wallet to which you will receive bitcoins.
  - *confirmations_required*. Number of required confirmations to consider transaction successful.
  - *orders_expiration_period*. How long the order will be waiting for a payment (in milliseconds). Should be between 0 and 1800.
  - *default_currency*. Default currency to display order amounts in. 

Optional fields:

  - *active* - If a gateway is active (can generate new orders). Default: *true*
  - *address_derivation_scheme* - How we derive each new address from the provided xpub (see BIP32 documentation)
  - *callbackurl* - A callback url is where our server will report all order status changes by performing a callback request.
  - *afterpayment_redirect_to* - Is a URL to which users are redirected after they made a payment.
  - *auto_redirect*
  - *city*
  - *test_pubkey* - Testnet public key. Used if *test_mode* is enabled.
  - *test_mode* - Activate or deactivate testnet mode.
  - *convert_currency_to* 
  - *country*
  - *exchange_rate_adapter_names*
  - *description*
  - *merchant_url*
  - *receive_payments_notifications*
  - *region*
  - *locale*
  - *allow_links*

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

A response to this request should be the following object:

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
Status code is: **201**

## Update gateway
To update a gateway, you need to make a **PATCH** request to `/api/gateways` with the following body:

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

where *id* is an ID of a gateway you wnat to change.
You can list fields you wish to change under the *attributes* key. Others fields will not change.

## Get gateways list
To fetch a list of all gateways you need to make a **GET** request to `/api/gateways` with an empty body.

A response to this request should be the following object:

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
By default the returned list is limited to 25 records. If you want more, you'll need to send a query parameter described in *Pagination* section.

### Pagination
 
The strategy is cursor-based. The following options may be passed as query parameters:

  - **page[number]** - defines current page.
  - **page[size]** - defines the maximum number of items to be returned in a result. Default is 25.

The resulting JSON will contain a *meta* property with the pagination info:

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
curl https://admin.gear.mycelium.com/api/gateways?page[number]=1&page[size]=5
```
This will show first 5 gateways.
