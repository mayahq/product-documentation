---
description: >-
  When triggered, can send a message, and then optionally a second message,
  unless extended or reset.
---

# Trigger

### Inputs

* `delay` (number) : Sets the delay, in milliseconds, to be applied to the message. This option only applies if the node is configured to allow the message to override the configured default delay interval.
* `reset` : If a message is received with this property, any timeout or repeat currently in progress will be cleared and no message triggered.

### Outputs

Outputs a standard `msg` object.

![](<../../../.gitbook/assets/image (25) (1).png>)

### Details

This node can be used to create a timeout within a flow. By default, when it receives a message, it sends on a message with a `payload` of `1`. It then waits 250ms before sending a second message with a `payload` of `0`. This could be used, for example, to blink an LED attached to a Raspberry Pi GPIO pin.

The payloads of each message sent can be configured to a variety of values, including the option to not send anything. For example, setting the initial message to _nothing_ and selecting the option to extend the timer with each received message, the node will act as a watchdog timer; only sending a message if nothing is received within the set interval.

If set to a _string_ type, the node supports the mustache template syntax.

The delay between sending messages can be overridden by `msg.delay` if that option is enabled in the node. The value must be provided in milliseconds.

If the node receives a message with a `reset` property, or a `payload` that matches that configured in the node, any timeout or repeat currently in progress will be cleared and no message triggered.

The node can be configured to resend a message at a regular interval until it is reset by a received message.

Optionally, the node can be configured to treat messages as if they are separate streams, using a msg property to identify each stream. Default `msg.topic`.

The status indicates the node is currently active. If multiple streams are used the status indicates the number of streams being held.
