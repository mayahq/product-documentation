---
description: Trigger a flow when another node completes its handling of a message.
---

# Complete

### Inputs

This is a trigger node so there are no inputs.

### Outputs

None of the fields are populated, but a `msg` object is outputted.

![](<../../../.gitbook/assets/image (51).png>)

### Details

If a node tells the runtime when it has finished handling a message, this node can be used to trigger a second flow.

For example, this can be used alongside a node with no output port, such as the Email sending node, to continue the flow.

This node must be configured to handle the event for selected nodes in the flow. Unlike the Catch node, it does not provide a 'handle all' mode automatically applies to all nodes in the flow.
