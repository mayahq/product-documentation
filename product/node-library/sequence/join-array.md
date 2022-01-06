---
description: Joins sequences of messages into a single message.
---

# Join Array

This mode assumes this node is either paired with a _split_ node or the received messages will have a properly configured `msg.parts` property.

### Inputs

* `parts` (object) : To automatically join a sequence of messages, they should all have this property set. The **split** node generates this property but it can be manually created. It has the following properties:
  * `id` - an identifier for the group of messages
  * `index` - the position within the group
  * `count` - the total number of messages in the group
  * `type` - the type of message - string/array/object/buffer
  * `ch` - for a string or buffer, the data used to the split the message as either the string or an array of bytes
  * `key` - for an object, the key of the property this message was created from
  * `len` - the length of each message when split using a fixed length value
* `complete` : If set, the node will append the payload, and then send the output message in its current state. If you don't wish to append the payload, delete it from the msg.

### Outputs

* Single message outputted in `msg.payload`.

### Attributes

There are three modes available:

* **automatic** : When paired with the **split** node, it will automatically join the messages to reverse the split that was performed.
* **manual** : Join sequences of messages in a variety of ways.
* **reduce** : sequenceApply an expression against all messages in a sequence to reduce it to a single message.

![](<../../../.gitbook/assets/image (18) (1).png>)

### Details

**Automatic mode**

Automatic mode uses the `parts` property of incoming messages to determine how the sequence should be joined. This allows it to automatically reverse the action of a **split** node.

**Manual mode**

When configured to join in manual mode, the node is able to join sequences of messages into a number of different results:

* a **string** or **buffer** - created by joining the selected property of each message with the specified join characters or buffer.
* an **array** - created by adding each selected property, or entire message, to the output array.
* a **key/value object** - created by using a property of each message to determine the key under which the required value is stored.
* a **merged object** - created by merging the property of each message under a single object.

The other properties of the output message are taken from the last message received before the result is sent.

A _count_ can be set for how many messages should be received before generating the output message. For object outputs, once this count has been reached, the node can be configured to send a message for each subsequent message received.

A _timeout_ can be set to trigger sending the new message using whatever has been received so far.

If a message is received with the `msg.complete` property set, the output message is finalised and sent. This resets any part counts.

If a message is received with the `msg.reset` property set, the partly complete message is deleted and not sent. This resets any part counts.

**Reduce Sequence mode**

When configured to join in reduce mode, an expression is applied to each message in a sequence and the result accumulated to produce a single message.

Initial valueThe initial value of the accumulated value (`$A`).Reduce expressionA JSONata expression that is called for each message in the sequence. The result is passed to the next call of the expression as the accumulated value. In the expression, the following special variables can be used:

* `$A`: the accumulated value,
* `$I`: index of the message in the sequence,
* `$N`: number of messages in the sequence.

Fix-up expressionAn optional JSONata expression that is applied after the reduce expression has been applied to all messages in the sequence. In the expression, following special variables can be used:

* `$A`: the accumulated value,
* `$N`: number of messages in the sequence.

By default, the reduce expression is applied in order, from the first to the last message of the sequence. It can optionally be applied in reverse order.

$N is the number of messages that arrive - even if they are identical.

**Example:** the following settings, given a sequence of numeric values, calculates the average value:

* **Reduce expression**: `$A+payload`
* **Initial value**: `0`
* **Fix-up expression**: `$A/$N`

**Storing messages**

This node will buffer messages internally in order to work across sequences. The runtime setting `nodeMessageBufferMaxLength` can be used to limit how many messages nodes will buffer.
