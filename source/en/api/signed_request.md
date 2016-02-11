Most requests to API require a signature which protects gateway from unauthorized access.   
The signature is a X-Signature HTTP header, which created using [JWT](https://jwt.io) specification.  
We use symetrical HMAC algorithm HS256, where `secret` is gateway secret.

Example of how a signature creates in Ruby:

```ruby
JWT.encode({}, GATEWAY_SECRET, 'HS256')
```

We don't use any reserved claims now (`iss, exp, sub, aud`, etc.), but maybe will do in the future. 
