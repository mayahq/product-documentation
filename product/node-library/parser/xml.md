---
description: >-
  Converts between an XML string and its JavaScript object representation, in
  either direction.
---

# XML

### Inputs

* `payload` (object | string) : A JavaScript object or XML string.
* `options` (object) : This optional property can be used to pass in any of the options supported by the underlying library used to convert to and from XML. See [the xml2js docs](https://github.com/Leonidas-from-XIV/node-xml2js/blob/master/README.md#options) for more information.

### Outputs

* `payload` (object | string) :&#x20;
  * If the input is a string it tries to parse it as XML and creates a JavaScript object.
  * If the input is a JavaScript object it tries to build an XML string.



![](<../../../.gitbook/assets/image (32).png>)

### Details

When converting between XML and an object, any XML attributes are added as a property named `$` by default. Any text content is added as a property named `_`. These property names can be specified in the node configuration.

For example, the following XML will be converted as shown:

```
<p class="tag">Hello World</p>
```

```
{
  "p": {
    "$": {
      "class": "tag"
    },
    "_": "Hello World"
  }
}
```

