---
description: Maps a numeric value to a different range.
---

# Range

### Inputs

* `payload` (number) : The payload _must_ be a number. Anything else will try to be parsed into a number and rejected if that fails.

### Outputs

* `payload` (number) : The value mapped to the new range.

![](<../../../.gitbook/assets/image (53).png>)

This node will linearly scale the received value. By default, the result is not constrained to the range defined in the node.

_Scale and limit to target range_ means that the result will never be outside the range specified within the target range.

_Scale and wrap within the target range_ means that the result will be wrapped within the target range.

For example an input 0 - 10 mapped to 0 - 100.

| mode  | input | output |
| ----- | ----- | ------ |
| scale | 12    | 120    |
| limit | 12    | 100    |
| wrap  | 12    | 20     |
