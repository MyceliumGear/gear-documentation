Whenever an order status changes, Mycelium Gear issues a GET http request to the url specified in the gateway's callback field (if you filled it) or in the order's `callback_url` param. This way it lets your site know that the payment was either successful or has failed for some reason. This http request is also sometimes called a webhook, although we prefer not to use that term.

Important information is passed in this http request as url params. Here's what a typical callback may look like:

```text
GET https://worldsbestshoes.com/payments/callback?order_id=1&amount=1&amount_in_btc=0.00000001&amount_paid_in_btc=0.00000001&status=2&address=1NZov2nm6gRCGW6r4q1qHtxXurrWNpPr1q&transaction_ids=["tid1"]&keychain_id=1&last_keychain_id=1&after_payment_redirect_to=http://example.com/payments/success&auto_redirect=true&callback_data=some+random+data
```

Also, request will have special header:

```text
X-Signature: UeXPK9RlYFFLdYpWeGBpSd4OWslJR076VBQU4prJlzMpe3f2KL4eUVfpiZ+Z9/c71tqYZgYWeIN78NE1/Snmyw==
```

The following list explains in detail the information and parameters in the GET callback request:

*  order_id  
    An internal id of the order. This is how you can find the corresponding purchase record in your database. It is also used for the signature.
* amount  
    This is the amount in the gateway's currency that was supposed to be paid
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
* transaction_ids
    If the status is 1,2,3 or 4, this will contain JSON array with the Bitcoin transaction IDs
* callback_data  
    This contains any additional data that was sent along with the transaction while creating the order. For example, if you sent "hello world" as data in the request that created that order, you will also get the same string back with a callback — as the value for the callback_data key within the returned json.
* X-Signature header  
    This is the most important piece of information in regards to security. Keep in mind that anyone can make a request to that callback url of yours and basically fool your website into believing that a certain order was paid. To avoid that, Mycelium Gear uses signatures to sign a callback request, so that you can verify it came from Mycelium Gear and not somebody else. This is explained in detail below.

## Callback signature

It's generated in the same way as a signature for signed API requests, except that it uses blank Nonce and Body.

```
Base64StrictEncode(
  HMAC-SHA512(
    REQUEST_METHOD + REQUEST_URI,
    GATEWAY_SECRET
  )
)
```

In Ruby, callback signature can be verified using `straight-server-kit` gem.
 
```ruby
  request_uri = URI(env['REQUEST_URI']).request_uri rescue env['REQUEST_URI']
  if StraightServerKit.valid_callback?(signature:   headers['X-Signature'],
                                       request_uri: request_uri,
                                       secret:      gateway_secret)
    # update order
  else
    # log incident and return 200
  end
```

```ruby
data = {
  signature: 'UeXPK9RlYFFLdYpWeGBpSd4OWslJR076VBQU4prJlzMpe3f2KL4eUVfpiZ+Z9/c71tqYZgYWeIN78NE1/Snmyw==',
  request_uri: '/payments/callback?order_id=1&amount=1&amount_in_btc=0.00000001&amount_paid_in_btc=0.00000001&status=2&address=1NZov2nm6gRCGW6r4q1qHtxXurrWNpPr1q&transaction_ids=["tid1"]&keychain_id=1&last_keychain_id=1&after_payment_redirect_to=http://example.com/payments/success&auto_redirect=true&callback_data=some+random+data',
  secret: 'gateway.secret',
}
StraightServerKit.valid_callback?(**data) == true
```

Details of signature verification.

```ruby
require 'openssl'
require 'base64'

sha512 = OpenSSL::Digest::SHA512.new
nonce = nil
body = nil
method = 'GET'
request_uri = '/payments/callback?order_id=1&amount=1&amount_in_btc=0.00000001&amount_paid_in_btc=0.00000001&status=2&address=1NZov2nm6gRCGW6r4q1qHtxXurrWNpPr1q&transaction_ids=["tid1"]&keychain_id=1&last_keychain_id=1&after_payment_redirect_to=http://example.com/payments/success&auto_redirect=true&callback_data=some+random+data'
secret = 'gateway.secret'
constant_digest = sha512.digest("#{nonce}#{body}")
constant_digest == sha512.digest('')
constant_digest.bytes == [207, 131, 225, 53, 126, 239, 184, 189, 241, 84, 40, 80, 214, 109, 128, 7, 214, 32, 228, 5, 11, 87, 21, 220, 131, 244, 169, 33, 211, 108, 233, 206, 71, 208, 209, 60, 93, 133, 242, 176, 255, 131, 24, 210, 135, 126, 236, 47, 99, 185, 49, 189, 71, 65, 122, 129, 165, 56, 50, 122, 249, 39, 218, 62]
request = "#{method}#{request_uri}#{constant_digest}"
raw_signature = OpenSSL::HMAC.digest(sha512, secret, request)
raw_signature.bytes == [81, 229, 207, 43, 212, 101, 96, 81, 75, 117, 138, 86, 120, 96, 105, 73, 222, 14, 90, 201, 73, 71, 78, 250, 84, 20, 20, 226, 154, 201, 151, 51, 41, 123, 119, 246, 40, 190, 30, 81, 87, 233, 137, 159, 153, 247, 247, 59, 214, 218, 152, 102, 6, 22, 120, 131, 123, 240, 209, 53, 253, 41, 230, 203]
signature = Base64.strict_encode64(raw_signature)
signature == 'UeXPK9RlYFFLdYpWeGBpSd4OWslJR076VBQU4prJlzMpe3f2KL4eUVfpiZ+Z9/c71tqYZgYWeIN78NE1/Snmyw=='
```
