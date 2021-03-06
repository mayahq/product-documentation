---
description: Route messages based on their property values or sequence position.
---

# Switch

### Inputs

Just the `msg` object required, no specific keys are used.

### Outputs

Multiple output ports can be added, based on the number of conditions being switched between.

![](<../../../.gitbook/assets/image (15).png>)

### Details

When a message arrives, the node will evaluate each of the defined rules and forward the message to the corresponding outputs of any matching rules.

Optionally, the node can be set to stop evaluating rules once it finds one that matches.

The rules can be evaluated against an individual message property, a flow or global context property, environment variable or the result of a JSONata expression.

**Rules**

There are four types of rule:

1. **Value** rules are evaluated against the configured property
2. **Sequence** rules can be used on message sequences, such as those generated by the Split node
3. A JSONata **Expression** can be provided that will be evaluated against the whole message and will match if the expression returns a true value.
4. An **Otherwise** rule can be used to match if none of the preceeding rules have matched.

**Notes**

The `is true/false` and `is null` rules perform strict comparisons against those types. They do not convert between types.

The `is empty` and `is not empty` rules can be used to test the length of Strings, Arrays and Buffers, or the number of properties an Object has. Neither rule will pass if the property being tested has a `boolean`, `null` or `undefined` value.

**Handling message sequences**

By default, the node does not modify the `msg.parts` property of messages that are part of a sequence.

The **recreate message sequences** option can be enabled to generate new message sequences for each rule that matches. In this mode, the node will buffer the entire incoming sequence before sending the new sequences on. The runtime setting `nodeMessageBufferMaxLength` can be used to limit how many messages nodes will buffer.
