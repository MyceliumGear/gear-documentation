If user cancels his purchase, it's better to cancel the Mycelium Gear order as well.

Order can be canceled by sending a signed request:

```text
POST /gateways/:api_gateway_id/orders/(:order_id or :payment_id)/cancel
```
or you can send the same request by using straight-server-kit:

```ruby
client = StraightServerKit::Client.new(gateway_id: api_gateway_id, secret: gateway_secret)
order  = client.orders.cancel(id: purchase.order_id)
```
