[[Express]]
The `res` object represents the HTTP response that an Express app sends when it gets an HTTP request.

In this documentation and by convention, the object is always referred to as `res` (and the HTTP request is `req`) but its actual name is determined by the parameters to the callback function in which you’re working.
For example:

```javascript
app.get('/user/:id', function (req, res) {
  res.send('user ' + req.params.id)
})
```

But you could just as well have:

```javascript
app.get('/user/:id', function (request, response) {
  response.send('user ' + request.params.id)
})
```

The `res` object is an enhanced version of Node’s own response object and supports all [built-in fields and methods](https://nodejs.org/api/http.html#http_class_http_serverresponse).**
**


### Properties

### res.app

This property holds a reference to the instance of the Express application that is using the middleware.

`res.app` is identical to the [req.app](https://expressjs.com/pt-br/4x/api.html#req.app) property in the request object.

### res.headersSent

Boolean property that indicates if the app sent HTTP headers for the response.

```javascript
app.get('/', function (req, res) {
  console.dir(res.headersSent) // false
  res.send('OK')
  console.dir(res.headersSent) // true
})
```

### res.locals

Use this property to set variables accessible in templates rendered with [res.render](https://expressjs.com/pt-br/4x/api.html#res.render). The variables set on `res.locals` are available within a single request-response cycle, and will not be shared between requests.

In order to keep local variables for use in template rendering between requests, use [app.locals](https://expressjs.com/pt-br/4x/api.html#app.locals) instead.

This property is useful for exposing request-level information such as the request path name, authenticated user, user settings, and so on to templates rendered within the application.

```javascript
app.use(function (req, res, next) {
  // Make `user` and `authenticated` available in templates
  res.locals.user = req.user
  res.locals.authenticated = !req.user.anonymous
  next()
})
```


### Methods

### res.append(field [, value])

`res.append()` is supported by Express v4.11.0+

Appends the specified `value` to the HTTP response header `field`. If the header is not already set, it creates the header with the specified value. The `value` parameter can be a string or an array.

Note: calling `res.set()` after `res.append()` will reset the previously-set header value.

```javascript
res.append('Link', ['<http://localhost/>', '<http://localhost:3000/>'])
res.append('Set-Cookie', 'foo=bar; Path=/; HttpOnly')
res.append('Warning', '199 Miscellaneous warning')
```

### res.attachment([filename])

Sets the HTTP response `Content-Disposition` header field to “attachment”. If a `filename` is given, then it sets the Content-Type based on the extension name via `res.type()`, and sets the `Content-Disposition` “filename=” parameter.

```javascript
res.attachment()
// Content-Disposition: attachment

res.attachment('path/to/logo.png')
// Content-Disposition: attachment; filename="logo.png"
// Content-Type: image/png
```

### res.cookie(name, value [, options])

Sets cookie `name` to `value`. The `value` parameter may be a string or object converted to JSON.

The `options` parameter is an object that can have the following properties.

![[Pasted image 20230201080034.png]]

All `res.cookie()` does is set the HTTP `Set-Cookie` header with the options provided. Any option not specified defaults to the value stated in [RFC 6265](http://tools.ietf.org/html/rfc6265).

For example:

```javascript
res.cookie('name', 'tobi', { domain: '.example.com', path: '/admin', secure: true })
res.cookie('rememberme', '1', { expires: new Date(Date.now() + 900000), httpOnly: true })
```

You can set multiple cookies in a single response by calling `res.cookie` multiple times, for example:

```javascript
res
  .status(201)
  .cookie('access_token', 'Bearer ' + token, {
    expires: new Date(Date.now() + 8 * 3600000) // cookie will be removed after 8 hours
  })
  .cookie('test', 'test')
  .redirect(301, '/admin')
```

The `encode` option allows you to choose the function used for cookie value encoding. Does not support asynchronous functions.

Example use case: You need to set a domain-wide cookie for another site in your organization. This other site (not under your administrative control) does not use URI-encoded cookie values.

```javascript
// Default encoding
res.cookie('some_cross_domain_cookie', 'http://mysubdomain.example.com', { domain: 'example.com' })
// Result: 'some_cross_domain_cookie=http%3A%2F%2Fmysubdomain.example.com; Domain=example.com; Path=/'

// Custom encoding
res.cookie('some_cross_domain_cookie', 'http://mysubdomain.example.com', { domain: 'example.com', encode: String })
// Result: 'some_cross_domain_cookie=http://mysubdomain.example.com; Domain=example.com; Path=/;'
```

The `maxAge` option is a convenience option for setting “expires” relative to the current time in milliseconds. The following is equivalent to the second example above.

```javascript
res.cookie('rememberme', '1', { maxAge: 900000, httpOnly: true })
```

You can pass an object as the `value` parameter; it is then serialized as JSON and parsed by `bodyParser()` middleware.

```javascript
res.cookie('cart', { items: [1, 2, 3] })
res.cookie('cart', { items: [1, 2, 3] }, { maxAge: 900000 })
```

When using [cookie-parser](https://www.npmjs.com/package/cookie-parser) middleware, this method also supports signed cookies. Simply include the `signed` option set to `true`. Then `res.cookie()` will use the secret passed to `cookieParser(secret)` to sign the value.

```javascript
res.cookie('name', 'tobi', { signed: true })
```

Later you may access this value through the [req.signedCookie](https://expressjs.com/pt-br/4x/api.html#req.signedCookies) object.

### res.download(path [, filename] [, options] [, fn])

Transfers the file at `path` as an “attachment”. Typically, browsers will prompt the user for download. By default, the `Content-Disposition` header “filename=” parameter is derrived from the `path` argument, but can be overridden with the `filename` parameter. If `path` is relative, then it will be based on the current working directory of the process or the `root` option, if provided.

This API provides access to data on the running file system. Ensure that either (a) the way in which the `path` argument was constructed is secure if it contains user input or (b) set the `root` option to the absolute path of a directory to contain access within.

When the `root` option is provided, Express will validate that the relative path provided as `path` will resolve within the given `root` option.

The following table provides details on the `options` parameter.

The optional `options` argument is supported by Express v4.16.0 onwards.
![[Pasted image 20230201080312.png]]

The method invokes the callback function `fn(err)` when the transfer is complete or when an error occurs. If the callback function is specified and an error occurs, the callback function must explicitly handle the response process either by ending the request-response cycle, or by passing control to the next route.

```javascript
res.download('/report-12345.pdf')

res.download('/report-12345.pdf', 'report.pdf')

res.download('/report-12345.pdf', 'report.pdf', function (err) {
  if (err) {
    // Handle error, but keep in mind the response may be partially-sent
    // so check res.headersSent
  } else {
    // decrement a download credit, etc.
  }
})
```

### res.end([data] [, encoding])

Ends the response process. This method actually comes from Node core, specifically the [response.end() method of http.ServerResponse](https://nodejs.org/api/http.html#http_response_end_data_encoding_callback).

Use to quickly end the response without any data. If you need to respond with data, instead use methods such as [res.send()](https://expressjs.com/pt-br/4x/api.html#res.send) and [res.json()](https://expressjs.com/pt-br/4x/api.html#res.json).

```javascript
res.end()
res.status(404).end()
```

### res.format(object)

Performs content-negotiation on the `Accept` HTTP header on the request object, when present. It uses [req.accepts()](https://expressjs.com/pt-br/4x/api.html#req.accepts) to select a handler for the request, based on the acceptable types ordered by their quality values. If the header is not specified, the first callback is invoked. When no match is found, the server responds with 406 “Not Acceptable”, or invokes the `default` callback.

The `Content-Type` response header is set when a callback is selected. However, you may alter this within the callback using methods such as `res.set()` or `res.type()`.

The following example would respond with `{ "message": "hey" }` when the `Accept` header field is set to “application/json” or “*/json” (however if it is “*/*”, then the response will be “hey”).

```javascript
res.format({
  'text/plain': function () {
    res.send('hey')
  },

  'text/html': function () {
    res.send('<p>hey</p>')
  },

  'application/json': function () {
    res.send({ message: 'hey' })
  },

  default: function () {
    // log the request and respond with 406
    res.status(406).send('Not Acceptable')
  }
})
```

In addition to canonicalized MIME types, you may also use extension names mapped to these types for a slightly less verbose implementation:

```javascript
res.format({
  text: function () {
    res.send('hey')
  },

  html: function () {
    res.send('<p>hey</p>')
  },

  json: function () {
    res.send({ message: 'hey' })
  }
})
```

### res.get(field)

Returns the HTTP response header specified by `field`. The match is case-insensitive.

```javascript
res.get('Content-Type')
// => "text/plain"
```

### res.json([body])

Sends a JSON response. This method sends a response (with the correct content-type) that is the parameter converted to a JSON string using [JSON.stringify()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/JSON/stringify).

The parameter can be any JSON type, including object, array, string, Boolean, number, or null, and you can also use it to convert other values to JSON.

```javascript
res.json(null)
res.json({ user: 'tobi' })
res.status(500).json({ error: 'message' })
```

https://expressjs.com/pt-br/4x/api.html#res