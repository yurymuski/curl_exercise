#### Request https://httpbin.org
`curl https://httpbin.org`

#### Request https://httpbin.org/anything. httpbin.org/anything will look at the request you made, parse it, and echo back to you what you requested. curl’s default is to make a GET request.
`curl https://httpbin.org/anything`

#### Make a POST request to https://httpbin.org/anything
`curl -X POST https://httpbin.org/anything`

#### Make a GET request to https://httpbin.org/anything, but this time add some query parameters (set value=panda).
`curl --data value=panda -d value2=panda2 https://httpbin.org/anything`

#### Request google’s robots.txt file (www.google.com/robots.txt)
`curl www.google.com/robots.txt`

#### Make a GET request to https://httpbin.org/anything and set the header User-Agent: elephant.
- `curl -H 'User-Agent: elephant' -A 'elephant' https://httpbin.org/anything`
- `curl -A 'elephant' https://httpbin.org/anything`

#### Make a DELETE request to https://httpbin.org/anything
`curl -X DELETE https://httpbin.org/anything`

#### Request https://httpbin.org/anything and also get the response headers
`curl -i https://httpbin.org/anything`

#### Make a POST request to https://httpbin.com/anything with the JSON body {"value": "panda"}
`curl -X POST -d '{"value": "panda"}' https://httpbin.org/anything`

#### Make the same POST request as the previous exercise, but set the Content-Type header to application/json (because POST requests need to have a content type that matches their body). Look at the json field in the response to see the difference from the previous one.
`curl -X POST -H 'Content-Type:application/json' -d '{"value": "panda"}' https://httpbin.org/anything`

#### Make a GET request to https://httpbin.org/anything and set the header Accept-Encoding: gzip (what happens? why?)
`curl -H 'Accept-Encoding:gzip'  https://httpbin.org/anything`

#### Put a bunch of a JSON in a file and then make a POST request to https://httpbin.org/anything with the JSON in that file as the body
`echo '{"value": "panda"}' > /tmp/test.json`
`curl -X POST -H 'Content-Type:application/json' -d '{"value": "panda"}' https://httpbin.org/anything`

#### Make a request to https://httpbin.org/image and set the header ‘Accept: image/png’. Save the output to a PNG file and open the file in an image viewer. Try the same thing with with different Accept: headers.
`curl -H 'Accept: image/png' -o /tmp/test.png https://httpbin.org/image`

#### Make a PUT request to https://httpbin.org/anything
`curl -X PUT -d 'hello=world&ping=pong' https://httpbin.org/anything`

#### Request https://httpbin.org/image/jpeg, save it to a file, and open that file in your image editor.
`curl -H 'Accept: image/jpeg' -o /tmp/test.jpeg https://httpbin.org/image/jpeg`

#### Request https://www.twitter.com. You’ll get an empty response. Get curl to show you the response headers too, and try to figure out why the response was empty.
- `curl -IL https://www.twitter.com`
- `curl -H 'User-Agent: any' https://www.twitter.com`

#### Make any request to https://httpbin.org/anything and just set some nonsense headers (like panda: elephant)
`curl -H 'panda:elephant'  https://httpbin.org/anything`

#### Request https://httpbin.org/status/404 and https://httpbin.org/status/200. Request them again and get curl to show the response headers.
- `curl -I https://httpbin.org/status/404`
- `curl -I https://httpbin.org/status/200`

#### Request https://httpbin.org/anything and set a username and password (with -u username:password)
`curl -u username:password https://httpbin.org/anything`

#### Download the Twitter homepage (https://twitter.com) in Spanish by setting the Accept-Language: es-ES header.
`curl -o /tmp/twitter.html -H 'User-Agent: any' -H 'Accept-Language: es-ES' https://twitter.com`

#### Make a request to the Stripe API with curl. (see https://stripe.com/docs/development for how, they give you a test API key). Try making exactly the same request to https://httpbin.org/anything.
```
curl https://api.stripe.com/v1/charges \
  -u sk_test_4eC39HqLyjWDarjtT1zdp7dc: \
  -d amount=999 \
  -d currency=usd \
  -d source=tok_visa \
  -d receipt_email="jenny.rosen@example.com"
```

```
curl https://httpbin.org/anything \
  -u sk_test_4eC39HqLyjWDarjtT1zdp7dc: \
  -d amount=999 \
  -d currency=usd \
  -d source=tok_visa \
  -d receipt_email="jenny.rosen@example.com"
```
