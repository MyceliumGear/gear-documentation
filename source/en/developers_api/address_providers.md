## Listing address providers

### GET api/address_providers
### Request

#### Headers

<pre>Accept: application/json
Content-Type: application/json
X-Client: authorize.me@example.org
Host: example.org
Cookie: </pre>

#### Route

<pre>GET api/address_providers</pre>

### Response

#### Headers

<pre>X-Frame-Options: SAMEORIGIN
X-XSS-Protection: 1; mode=block
X-Content-Type-Options: nosniff
Content-Type: application/json; charset=utf-8
ETag: W/&quot;028126e93aa8c8459af46ecd57cf4158&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: f5687539-f529-4c5e-898d-07674fc56837
X-Runtime: 0.053401
Content-Length: 45</pre>

#### Status

<pre>200 OK</pre>

#### Body

<pre>[
  {
    "type": "address_providers_cashila",
    "id": 1
  }
]</pre>
