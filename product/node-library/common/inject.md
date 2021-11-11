---
description: >-
  Injects a message into a flow either manually or at regular intervals. The
  message payload can be a variety of types, including strings, JavaScript
  objects or the current time.
---

# Inject

### Inputs

This is a trigger node, so it does not accept any inputs.

### Outputs

* payload (various) : The configured payload of the message.
* topic (string) : An optional property that can be configured in the node.

![](<../../../.gitbook/assets/image (39).png>)

### Details

The Inject node can initiate a flow with a specific payload value. The default payload is a timestamp of the current time in millisecs since January 1st, 1970.

The node also supports injecting strings, numbers, booleans, JavaScript objects, or flow/global context values.

By default, the node is triggered manually by clicking on its button within the editor. It can also be set to inject at regular intervals or according to a schedule.

It can also be configured to inject once each time the flows are started.

The maximum _Interval_ that can be specified is about 596 hours / 24 days. However if you are looking at intervals greater than one day you should consider using a scheduler node that can cope with power outages and restarts.

**Note**: The _"Interval between times"_ and _"at a specific time"_ options use the standard cron system. This means that 20 minutes will be at the next hour, 20 minutes past and 40 minutes past - not in 20 minutes time. If you want every 20 minutes from now - use the _"interval"_ option.

**Note**: To include a newline in a string you must use a Function node to create the payload.
