---
description: >-
  Set, change, delete or move properties of a message, flow context or global
  context.
---

# Change

### Inputs

Just the `msg` object required, no specific keys are used.

### Outputs

Modified `msg` object is outputted through a single port.

![](<../../../.gitbook/assets/image (41) (1).png>)

### Details

The node can specify multiple rules that will be applied in the order they are defined to modify the msg, flow, or global context. The available operations are:

#### Set

set a property. The value can be a variety of different types, or can be taken from an existing message or context property.

#### Change

search & replace parts of the property. If regular expressions are enabled, the "replace with" property can include capture groups, for example `$1`. Replace will only change the type if there is a complete match.

#### Delete

Delete a property.

#### Move

Move or rename a property.

The "expression" type uses the [JSONata](http://jsonata.org) query and expression language.
