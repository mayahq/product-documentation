---
description: Sends HTTP requests and returns the response.
---

# HTTP Request

### Inputs

* `url` (string) : If not configured in the node, this optional property sets the url of the request.
* `method` (string) : If not configured in the node, this optional property sets the HTTP method of the request. Must be one of `GET`, `PUT`, `POST`, `PATCH` or `DELETE`.
* `headers` (object) : Sets the HTTP headers of the request.
* `cookies` (object) : If set, can be used to send cookies with the request.payloadSent as the body of the request.
* `rejectUnauthorized` (boolean) : If set to `false`, allows requests to be made to https sites that use self signed certificates.
* `followRedirects` : If set to `false` prevent following Redirect (HTTP 301).`true` by default
* `requestTimeout` If set to a positive number of milliseconds, will override the globally set `httpRequestTimeout` parameter.

### Outputs

* `payload` (string | object | buffer) :  The body of the response. The node can be configured to return the body as a string, attempt to parse it as a JSON string or leave it as a binary buffer.&#x20;
* `statusCode`(number) : The status code of the response, or the error code if the request could not be completed.&#x20;
* `headers` (object) : An object containing the response headers.&#x20;
* `responseUrl` (string) : In case any redirects occurred while processing the request, this property is the final redirected url. Otherwise, the url of the original request.&#x20;
* `responseCookies` (object) : If the response includes cookies, this propery is an object of name/value pairs for each cookie.&#x20;
* `redirectList` (array) : If the request was redirected one or more times, the accumulated information will be added to this property. `location` is the next redirect destination. `cookies` is the cookies returned from the redirect source.

![](<../../../../.gitbook/assets/image (43).png>)

### Details

When configured within the node, the URL property can contain [mustache-style](http://mustache.github.io/mustache.5.html) tags. These allow the url to be constructed using values of the incoming message. For example, if the url is set to `example.com/{{{topic}}}`, it will have the value of `msg.topic` automatically inserted. Using {{{...}}} prevents mustache from escaping characters like / & etc.

The node can optionally automatically encode `msg.payload` as query string parameters for a GET request, in which case `msg.payload` has to be an object.

**Note**: If running behind a proxy, the standard `http_proxy=...` environment variable should be set and Node-RED restarted, or use Proxy Configuration. If Proxy Configuration was set, the configuration take precedence over environment variable.

**Using multiple HTTP Request nodes**

In order to use more than one of these nodes in the same flow, care must be taken with the `msg.headers` property. The first node will set this property with the response headers. The next node will then use those headers for its request - this is not usually the right thing to do. If `msg.headers` property is left unchanged between nodes, it will be ignored by the second node. To set custom headers, `msg.headers` should first be deleted or reset to an empty object: `{}`.

**Cookie handling**

The `cookies` property passed to the node must be an object of name/value pairs. The value can be either a string to set the value of the cookie or it can be an object with a single `value` property.

Any cookies returned by the request are passed back under the `responseCookies` property.

**Content type handling**

If `msg.payload` is an Object, the node will automatically set the content type of the request to `application/json` and encode the body as such.

To encode the request as form data, `msg.headers["content-type"]` should be set to `application/x-www-form-urlencoded`.

**File Upload**

To perform a file upload, `msg.headers["content-type"]` should be set to `multipart/form-data` and the `msg.payload` passed to the node must be an object with the following structure:

```
{
    "KEY": {
        "value": FILE_CONTENTS,
        "options": {
            "filename": "FILENAME"
        }
    }
}
```

The values of `KEY`, `FILE_CONTENTS` and `FILENAME` should be set to the appropriate values.
