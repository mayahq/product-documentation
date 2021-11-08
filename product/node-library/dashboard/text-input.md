---
description: >-
  Adds a text input field to the Maya dashboard. Mode can be regular text, email
  or color picker.
---

# Text Input

Any input is sent as `msg.payload`. If set to ‘pass through mode’ an arriving `msg.payload` will be used if it is different from the existing text in the input field. This allows you to preset the text of the input field.

The **Delay** _(default : 300ms)_ sets the amount of time in milliseconds before the output is sent. Setting to `0` waits for "Enter" or "Tab" key to send. Enter will send payload but remain in focus. Tab will send payload and move to next field. Clicking elsewhere will also send the payload.

The email mode will color in red if it is not a valid address and will return undefined.

The time input type returns a number of milliseconds from midnight.

Not all browsers support the _week_ and _month_ input types, and may return _undefined_. Please test your target browser(s) before use.

If a **Topic** is specified, it will be added as `msg.topic`.

Setting `msg.enabled` to `false` will disable the input.
