---
description: Displays selected message properties in the debug sidebar tab.
---

# Debug

Displays selected message properties in the debug sidebar tab and optionally the runtime log. By default it displays `msg.payload`, but can be configured to display any property, the full message or the result of a JSONata expression.

### Inputs

By default it prints out `msg.payload`, but can also print&#x20;

### Outputs&#x20;

This is a final node so doesn't have any outputs.

### Attributes&#x20;

* Output : Select what to print to debug console
* To : Select where all to output it to
* Name : Name of the node instance

![](<../../../.gitbook/assets/image (27).png>)

### Details

The debug sidebar provides a structured view of the messages it is sent, making it easier to understand their structure.

JavaScript objects and arrays can be collapsed and expanded as required. Buffer objects can be displayed as raw data or as a string if possible.

Alongside each message, the debug sidebar includes information about the time the message was received, the node that sent it and the type of the message. Clicking on the source node id will reveal that node within the workspace.

The button on the node can be used to enable or disable its output. It is recommended to disable or remove any Debug nodes that are not being used.

The node can also be configured to send all messages to the runtime log, or to send short (32 characters) to the status text under the debug node.
