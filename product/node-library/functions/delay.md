---
description: >-
  Delays each message passing through the node or limits the rate at which they
  can pass.
---

# Delay

### Inputs

* `delay` (number) Sets the delay, in milliseconds, to be applied to the message. This option only applies if the node is configured to allow the message to override the configured default delay interval.
* `rate` (number) : Sets the rate value in milliseconds between messages. This node overwrites the existing rate value defined in the node configuration when it receives the message which contains `msg.rate` value in milliSeconds. This option only applies if the node is configured to allow the message to override the configured default rate interval.
* `reset` : If the received message has this property set to any value, all outstanding messages held by the node are cleared without being sent.
* `flush` : If the received message has this property set to a numeric value then that many messages will be released immediately. If set to any other type (e.g. boolean), then all outstanding messages held by the node are sent immediately.

### Outputs

Unmodified `msg` object is outputted at certain time intervals.

![](<../../../.gitbook/assets/image (26).png>)

### Details

When configured to delay messages, the delay interval can be a fixed value, a random value within a range or dynamically set for each message. Each message is delayed independently of any other message, based on the time of its arrival.

When configured to rate limit messages, their delivery is spread across the configured time period. The status shows the number of messages currently in the queue. It can optionally discard intermediate messages as they arrive.

If set to allow override of the rate, the new rate will be applied immediately, and will remain in effect until changed again, the node is reset, or the flow is restarted.

The rate limiting can be applied to all messages, or group them according to their `msg.topic` value. When grouping, intermediate messages are automatically dropped. At each time interval, the node can either release the most recent message for all topics, or release the most recent message for the next topic.
