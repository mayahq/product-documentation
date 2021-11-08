---
description: Splits a message into a sequence of messages.
---

# Split Into Array

### Inputs

* `payload` (object | string | array | buffer) : The behaviour of the node is determined by the type of `msg.payload`:
  * **string**/**buffer** - the message is split using the specified character (default: ), buffer sequence or into fixed lengths.
  * **array** - the message is split into either individual array elements, or arrays of a fixed-length.
  * **object** - a message is sent for each key/value pair of the object.

### Outputs

* `parts` (object) : This property contains information about how the message was split from the original message. If passed to the **join** node, the sequence can be reassembled into a single message. The property has the following properties:
  * `id` - an identifier for the group of messages
  * `index` - the position within the group
  * `count` - if known, the total number of messages in the group. See 'streaming mode' below.
  * `type` - the type of message - string/array/object/buffer
  * `ch` - for a string or buffer, the data used to the split the message as either the string or an array of bytes
  * `key` - for an object, the key of the property this message was created from. The node can be configured to also copy this value to another message properties, such as `msg.topic`.
  * `len` - the length of each message when split using a fixed length value



![](<../../../.gitbook/assets/image (52).png>)

### Details

This node makes it easy to create a flow that performs common actions across a sequence of messages before, using the **join** node, recombining the sequence into a single message.

It uses the `msg.parts` property to track the individual parts of a sequence.

**Streaming mode**

The node can also be used to reflow a stream of messages. For example, a serial device that sends newline-terminated commands may deliver a single message with a partial command at its end. In 'streaming mode', this node will split a message and send each complete segment. If there is a partial segment at the end, the node will hold on to it and prepend it to the next message that is received.

When operating in this mode, the node will not set the `msg.parts.count` property as it does not know how many messages to expect in the stream. This means it cannot be used with the **join** node in its automatic mode

