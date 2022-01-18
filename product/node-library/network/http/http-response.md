---
description: Sends responses back to requests received from an HTTP Input node.
---

# HTTP Response

### Inputs

* `payload` (string) : The body of the response.
* `statusCode` (number) : If set, this is used as the response status code. Default: 200.
* `headers` (object) : If set, provides HTTP headers to include in the response. cookiesobject If set, can be used to set or delete cookies.

### Outputs

No outputs, this is a final node.

![](<../../../../.gitbook/assets/image (50) (1).png>)

### Details :

The `statusCode` and `headers` can also be set within the node itself. If a property is set within the node, it cannot be overridden by the corresponding message property.

**Cookie handling**

The `cookies` property must be an object of name/value pairs. The value can be either a string to set the value of the cookie with default options, or it can be an object of options.

The following example sets two cookies - one called `name` with a value of `nick`, the other called `session` with a value of `1234` and an expiry set to 15 minutes.

```
msg.cookies = {
    name: 'nick',
    session: {
        value: '1234',
        maxAge: 900000
    }
}
```

The valid options include:

* `domain` - (String) domain name for the cookie
* `expires` - (Date) expiry date in GMT. If not specified or set to 0, creates a session cookie
* `maxAge` - (String) expiry date as relative to the current time in milliseconds
* `path` - (String) path for the cookie. Defaults to /
* `value` - (String) the value to use for the cookie

To delete a cookie, set its `value` to `null`.

\\
