# Basic principles
The API is based on [JSONAPI](http://jsonapi.org/) (version 1.0) implementation of Hypermedia JSON. 

Versioninig is done through HTTP header **Accept-Version**

To use the API, your account must have a *developer* role.

## Authentication
Each request to the API is signed usging the method described [here]().

You can generate your **Secret key** on your account page. Go to the bottom of the page where you will see a checkbox: check it and click "update" - you will then see your secret key. Please, don't forget to write it down somewhere. If you regenerate it, the old key will no longer work.

## Errors
All errors are returned under the *errors* property in the returned object, the value of that property is as an array of errors.
If there are errors in the request you've sent, it will return the following:

```json
{
  "errors": [{
    "source": "request",
    "title": "There was a problem in JSON you submitted"
  }]
}
```

If there are validation errors, a response may look like this:

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
