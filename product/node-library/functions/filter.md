---
description: >-
  Report by Exception (RBE) node - only passes on data if the payload has
  changed. It can also block unless, or ignore if the value changes by a
  specified amount (Dead- and Narrowband mode).
---

# Filter

### Inputs

* `payload` (number | string | object) : RBE mode will accept numbers, strings, and simple objects. Other modes must provide a parseable number.&#x20;
* `topic` (string) :  if specified the function will work on a per topic basis. This property can be set by configuration.&#x20;
* `reset` (any) : if set clears the stored value for the specified msg.topic, or all topics if msg.topic is not specified.

### Outputs

* `payload` (as per input) : If triggered the output will be the same as the input.

![](<../../../.gitbook/assets/image (37).png>)

### Details

In RBE mode this node will block until the `msg.payload`, (or selected property) value is different to the previous one. If required it can ignore the intial value, so as not to send anything at start.

The [Deadband](https://en.wikipedia.org/wiki/Deadband) modes will block the incoming value _unless_ its change is greater or greater-equal than ± the band gap away from a previous value.

The Narrowband modes will block the incoming value, _if_ its change is greater or greater-equal than ± the band gap away from the previous value. It is useful for ignoring outliers from a faulty sensor for example.

Both in Deadband and Narrowband modes the incoming value must contain a parseable number and both also supports % - only sends if/unless the input differs by more than x% of the original value.

Both Deadband and Narrowband allow comparison against either the previous valid output value, thus ignoring any values out of range, or the previous input value, which resets the set point, thus allowing gradual drift (deadband), or a step change (narrowband).

**Note:** This works on a per `msg.topic` basis, though this can be changed to another property if desired. This means that a single rbe node can handle multiple different topics at the same time.
