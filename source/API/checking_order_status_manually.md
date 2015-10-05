Although being notified through a callback is the standard way of letting your website know that an order status has changed, sometimes it may not be enough. For example, your website may be down and may not be able to process the callback at the time it was issued. Even though Mycelium Gear will keep attempting to issue new callback requests to try and reach your website, it will only keep doing it for an hour, after which it will quit.

Thus, it is important to have another reliable method of checking the status of orders. To check the current status of an order, issue the following signed GET request:

```
GET https://gateway.gear.mycelium.com/gateways/:api_gateway_id/orders/:payment_id
```
where **:api_gateway_id** is the API id of your gateway, which you can look up on its info page and :payment_id is the way you identify your order (it was returned to you initially when you created the order). The response will return a json similar to what a callback might have passed to you via params:

```json
{
  "status": 2,
  "amount": 7894000,
  "address": "1NZov2nm6gRCGW6r4q1qHtxXurrWNpPr1q",
  "tid": "f0f9205e41bf1b79cb7634912e86bb840cedf8b1d108bd2faae1651ca79a5838",
  "id": 1,
  "payment_id": "y78033435ea02f024f9abdfd04adabe314a322a0d353c33beb3acb7d97f1bdeb",
  "amount_in_btc": "0.07894",
  "amount_paid_in_btc": "0.07894",
  "keychain_id": 3,
  "last_keychain_id": 3
}
```
You should use this manual check only if you suspect that you may have missed a callback. It should not be standard practice to keep querying the Mycelium Gear server every few seconds just to check the status of a particular order.
