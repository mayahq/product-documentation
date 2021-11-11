---
description: >-
  Extracts elements from an html document held in msg.payload using a CSS
  selector.
---

# HTML

### Inputs

* `payload` (string) : the html string from which to extract elements.
* `select` (string) : if not configured in the edit panel the selector can be set as a property of msg.

### Outputs

* `payload` (array | string) : the result can be either a single message with a payload containing an array of the matched elements, or multiple messages that each contain a matched element. If multiple messages are sent they will also have `parts` set.

![](<../../../.gitbook/assets/image (32).png>)

### Details

This node supports a combination of CSS and jQuery selectors. See the [css-select documentation](https://github.com/fb55/CSSselect#user-content-supported-selectors) for more information on the supported syntax.
