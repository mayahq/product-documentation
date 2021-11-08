---
description: Report status messages from other nodes on the same tab.
---

# Status

### Inputs

This is a trigger node so there are no inputs.

### Outputs

* `status.text` (string) : the status text.&#x20;
* `status.source.type` (string) : the type of the node that reported status.&#x20;
* `status.source.id` (string) : the id of the node that reported status.&#x20;
* `status.source.name` (string) : the name, if set, of the node that reported status.

![](<../../../.gitbook/assets/image (19).png>)

### Details

This node does not produce a `payload`.

By default the node reports status for all nodes on the same workspace tab. It can be configured to selectively report status for individual nodes.\
