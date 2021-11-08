---
description: Creates sequences of messages based on various rules.
---

# Batch Messages

### Inputs

Messages in any format.

### Outputs

Outputs sequences of messages.

![](<../../../.gitbook/assets/image (31).png>)

### Details

There are three modes for creating message sequences:

* **Number of messages** : groups messages into sequences of a given length. The **overlap** option specifies how many messages at the end of one sequence should be repeated at the start of the next sequence.
* **Time interval** : groups messages that arrive within the specified interval. If no messages arrive within the interval, the node can optionally send on an empty message.
* **Concatenate Sequences** : creates a message sequence by concatenating incoming sequences. Each message must have a `msg.topic` property and a `msg.parts` property identifying its sequence. The node is configured with a list of `topic` values to identify the order sequences are concatenated.

**Storing messages**

This node will buffer messages internally in order to work across sequences. The runtime setting `nodeMessageBufferMaxLength` can be used to limit how many messages nodes will buffer.

If a message is received with the `msg.reset` property set, the buffered messages are deleted and not sent.
