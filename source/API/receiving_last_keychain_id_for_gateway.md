You can get last keychain id for a specific gateway with the following request:

```text
GET https://gateway.gear.mycelium.com/gateways/:gateway_id/last_keychain_id

```
In response you can get something like:

```json
{"gateway_id": 1, "last_keychain_id": 10}
```
