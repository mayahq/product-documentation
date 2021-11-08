---
description: A function that sorts message property or a sequence of messages.
---

# Sort Array

### Inputs

Enter an array of strings or numbers into `msg.payload`, by default.

When configured to sort message property, the node sorts array data pointed to by specified message property.

When configured to sort a sequence of messages, it will reorder the messages.

### Outputs

Sorted arrays on `msg.payload`.

![](<../../../.gitbook/assets/image (20).png>)

### Details

The sorting order can be:

* **ascending**,
* **descending**.

For numbers, numerical ordering can be specified by a checkbox.

Sort key can be element value or JSONata expression for sorting property value, or message property or JSONata expression for sorting a message sequence.

When sorting a message sequence, the sort node relies on the received messages to have `msg.parts` set. The split node generates this property, but can be manually created. It has the following properties:

* `id` - an identifier for the group of messages
* `index` - the position within the group
* `count` - the total number of messages in the group

**Note:** This node internally keeps messages for its operation. In order to prevent unexpected memory usage, maximum number of messages kept can be specified. Default is no limit on number of messages.

* `nodeMessageBufferMaxLength` property set in **settings.js**.

