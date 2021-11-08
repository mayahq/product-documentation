---
description: Adds a colour picker to the Maya dashboard.
---

# Colour Picker

If the group width is 4 or greater then the picker can be set to be visible at all times.

**Format** can be rgb, hex, hex8, hsv, or hsl. Transparency is supported for all except hex.

If a **Topic** is specified, it will be added as `msg.topic`.

Setting `msg.enabled` to `false` will disable the input.

If set to ‘pass through mode’ a message arriving on the input will be evaluated for any colour format available as Format. If the conversion fails #000000 will be used.
