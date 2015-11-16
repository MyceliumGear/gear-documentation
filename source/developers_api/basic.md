# Basic principles
Our API based on [JSONAPI](http://jsonapi.org/) (version 1.0) implementation of Hypermedia JSON. 

Versioninig is done throught HTTP header **Accept-Version**

To use API account must have developer role.

## Authentification
Each request to API is signed usging method described [here]().

**Secret key** possible generate in Account page. On the bottom there is checkbox, if select it and press update you will see your secret key. Please, don't forget to write it down somewhere. If you regenerate it, the old key will no longer work.

## Errors
All errors returns in *errors* root element as array.
If error related to problems with request it will return:

```json
{
  "errors": [{
    "source": "request",
    "title": "There was a problem in JSON you submitted"
  }]
}
```

If there is validation errors, response may looks like:

```json
{
  "errors": [
    {
      "source": "name",
      "title": "can't be blank"
    },
    {
      "source": "pubkey",
      "title": "doesn't look like a BIP32 pubkey"
    }
  ]
}
```
