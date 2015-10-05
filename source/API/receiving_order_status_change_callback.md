Whenever an order status changes, Mycelium Gear issues a GET http request to the url specified in the gateway’s callback field (if you filled it) or in the order’s callback_url param. This way it lets your site know that the payment was either successful or has failed for some reason. This http request is also sometimes called a webhook, although we prefer not to use that term.

Important information is passed in this http request as url params. Here’s what a typical callback may look like:
`GET https://worldsbestshoes.com/payments/callback?order_id=1&amount=1&amount_in_btc=0.00000001&amount_paid_in_btc=0.00000001&status=2&address=1NZov2nm6gRCGW6r4q1qHtxXurrWNpPr1q&tid=tid1&keychain_id=1&last_keychain_id=1&callback_data=some+random+data`

Also, request will have special header:
`X-Signature: S2P8A16+RPaegTzJnb0Eg91csb1SExjdnvadABmQvfoIry4POBp6WbA6UOSqXojzRevyC8Ya/5QrQTnNxIb4og==`

The following list explains in detail the information and parameters in the GET callback request:

*  order_id  
    An internal id of the order. This is how you can find the corresponding purchase record in your database. It is also used for the signature
* amount  
    This is the amount in the gateway’s currency that was supposed to be paid
* amount_in_btc  
    This is the amount in btc that was supposed to be paid
* amount_paid_in_btc  
    This is the amount in btc that has been paid
* status  
  Returns a numerical value which can be either of the following:
  *  1 — unconfirmed; transaction was received, but does not have enough confirmations yet
  *  2 — paid in full
  *  3 — underpaid; not enough money received
  *  4 — overpaid; too much has been received
  *  5 — expired; customer did not pay in time
  *  6 — canceled; customer has canceled the order
* address  
    The Bitcoin address to which a transaction was supposed to be made
* tid  
    If the status is 1,2,3 or 4, this will contain a Bitcoin transaction id
* callback_data  
    This contains any additional data that was sent along with the transaction while #{ link_to “creating the order”, “/docs/creating_orders” }. For example, if you sent "hello world" as data in the request that created that order, you will also get the same string back with a callback — as the value for the callback_data key within the returned json.
* X-Signature header  
    This is the most important piece of information in regards to security. Keep in mind that anyone can make a request to that callback url of yours and basically fool your website into believing that a certain order was paid. In order to avoid that, Mycelium Gear uses signatures to sign a callback request, so that you can verify it came from Mycelium Gear and not somebody else. This is explained in detail below.

## Callback signature

It’s generated in the same way as a signature for a signed API requests, except that it uses blank X-Nonce. If you’re using Ruby, callback signature can be verified via straight-server-kit gem.

```ruby
  if StraightServerKit.valid_callback?(signature:   headers['X-Signature'],
                                       request_uri: @env['REQUEST_URI'],
                                       secret:      gateway_secret)
    # update order
  else
    # log incident and return 200
  end
```
