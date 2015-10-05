Another way to track an order status is to be continually connected to its respective websocket. In fact, this is what the payment page that your customer is redirected to does. However, you may decide you don't want to use the Mycelium Gear payment page. Perhaps you would want to present your customer with your own customized payment page that will be on your own site. Or even if you are using a standard payment page, your backend software may still want to connect to the order's websocket instead of waiting for a callback request.

To connect to the websocket, you should use the following URL:
`https://gateway.gear.mycelium.com/gateways/:api_gateway_id/orders/1/websocket`

where 1 is your order id. When order status changes, the websocket returns you order data in json, exactly the same data that would be returned as a response to a regular http request checking order status manually.
