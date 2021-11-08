---
description: >-
  Converts between a JSON string and its JavaScript object representation, in
  either direction.
---

# JSON

### Inputs

* `payload` (object | string) : A JavaScript object or JSON string.
* `schema` (object) : An optional JSON Schema object to validate the payload against. The property will be deleted before the `msg` is sent to the next node.

### Outputs

* `payload` (object | string) :&#x20;
  * If the input is a JSON string it tries to parse it to a JavaScript object.
  * If the input is a JavaScript object it creates a JSON string. The string can optionally be well-formatted.
* `schemaError` (array) : If JSON schema validation fails, the catch node will have a `schemaError` property containing an array of errors.

![](<../../../.gitbook/assets/image (39).png>)

### Details

By default, the node operates on `msg.payload`, but can be configured to convert any message property.

The node can also be configured to ensure a particular encoding instead of toggling between the two. This can be used, for example, with the `HTTP In` node to ensure the payload is a parsed object even if an incoming request did not set its content-type correctly for the HTTP In node to do the conversion.

If the node is configured to ensure the property is encoded as a String and it receives a String, no further checks will be made of the property. It will not check the String is valid JSON nor will it reformat it if the format option is selected.

For more details about JSON Schema you can consult the specification [here](http://json-schema.org/latest/json-schema-validation.html).

