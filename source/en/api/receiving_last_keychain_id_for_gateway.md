You can get last keychain id for a specific gateway with the following request:

```text
GET https://gateway.gear.mycelium.com/gateways/:gateway_id/last_keychain_id

```
Then you'll get something like this:

```json
{"gateway_id": 1, "last_keychain_id": 10}
```
