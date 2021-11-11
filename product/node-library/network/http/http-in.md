---
description: Creates an HTTP end-point for creating web services.
---

# HTTP In

### Inputs

No inputs, since this is a trigger node to except requests from outside.

### Outputs

* `payload` : For a GET request, contains an object of any query string parameters. Otherwise, contains the body of the HTTP request.
* `req` (object) : An HTTP request object. This object contains multiple properties that provide information about the request.
  * `body` - the body of the incoming request. The format will depend on the request.
  * `headers` - an object containing the HTTP request headers.
  * `query` - an object containing any query string parameters.
  * `params` - an object containing any route parameters.
  * `cookies` - an object containing the cookies for the request.
  * `files` - if enabled within the node, an object containing any files uploaded as part of a POST request.
* `res` (object) : An HTTP response object. This property should not be used directly; the `HTTP Response` node documents how to respond to a request. This property must remain attached to the message passed to the response node.

![](<../../../../.gitbook/assets/image (28).png>)

### Details

The node will listen on the configured path for requests of a particular type. The path can be fully specified, such as `/user`, or include named parameters that accept any value, such as `/user/:name`. When named parameters are used, their actual value in a request can be accessed under `msg.req.params`.

For requests that include a body, such as a POST or PUT, the contents of the request is made available as `msg.payload`.

If the content type of the request can be determined, the body will be parsed to any appropriate type. For example, `application/json` will be parsed to its JavaScript object representation.

**Note:** this node does not send any response to the request. The flow must include an HTTP Response node to complete the request.
