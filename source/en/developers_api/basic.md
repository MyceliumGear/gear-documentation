The API is based on <a href="http://jsonapi.org/" target="_blank">JSONAPI</a> (version 1.0) implementation. 

Versioninig is done through HTTP header **Accept-Version**. It's possible to not set version, then last will be used. 

```
Accept-Version: v2
```

In order to use Developer API you should first enable it and get a Secret key.
To do so, proceed to account section, check "Enable Developers API" and click "Save changes" button.

## Authentication
Each request to the API is signed usging the method described [here](/docs/api/signed_request).

You can generate your **Secret key** on your account page.
At the bottom of the page check "Regenerate API Secret" checkbox, enter your current password and click "Save changes" button - API Secret key will be generated for you.
Please, don't forget to write it down somewhere. If you lost API Secret key, you will need to regenerate it. After this old key will no longer work.

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
