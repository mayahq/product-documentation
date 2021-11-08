---
description: Catch errors thrown by nodes on the same tab.
---

# Catch

### Inputs

This is a trigger node, so no inputs.

### Outputs

* `error.message` (string) : the error message
* `error.source.id` (string) : the id of the node that threw the error.&#x20;
* `error.source.type` (string) : the type of the node that threw the error.&#x20;
* `error.source.name` (string) : the name, if set, of the node that threw the error.

![](<../../../.gitbook/assets/image (26).png>)

### Details

If a node throws an error whilst handling a message, the flow will typically halt. This node can be used to catch those errors and handle them with a dedicated flow.

By default, the node will catch errors thrown by any node on the same tab. Alternatively it can be targetted at specific nodes, or configured to only catch errors that have not already been caught by a 'targeted' catch node.

When an error is thrown, all matching catch nodes will receive the message.

If an error is thrown within a subflow, the error will get handled by any catch nodes within the subflow. If none exists, the error will be propagated up to the tab the subflow instance is on.

If the message already has an `error` property, it is copied to `_error`.
