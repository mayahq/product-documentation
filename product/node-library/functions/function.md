---
description: >-
  A custom JavaScript function to run against the messages being received by the
  node.
---

# Function

### Inputs

Take in `msg` object via input port.

### Outputs

Modified `msg` is passed out of the output node. Multiple output ports can be added.

![](<../../../.gitbook/assets/image (31).png>)

### Details

The messages are passed in as a JavaScript object called `msg`.

By convention it will have a `msg.payload` property containing the body of the message.

The function is expected to return a message object (or multiple message objects), but can choose to return nothing in order to halt a flow.

The **On Start** tab contains code that will be run whenever the node is started. The **On Stop** tab contains code that will be run when the node is stopped.

If the On Start code returns a Promise object, the node will not start handling messages until the promise is resolved.

**Sending messages**

The function can either return the messages it wants to pass on to the next nodes in the flow, or can call `node.send(messages)`.

It can return/send:

* a single message object - passed to nodes connected to the first output
* an array of message objects - passed to nodes connected to the corresponding outputs

Note: The setup code is executed during the initialization of nodes. Therefore, if `node.send` is called in the setup tab, subsequent nodes may not be able to receive the message.

If any element of the array is itself an array of messages, multiple messages are sent to the corresponding output.

If null is returned, either by itself or as an element of the array, no message is passed on.

**Logging and Error Handling**

To log any information, or report an error, the following functions are available:

* `node.log("Log message")`
* `node.warn("Warning")`
* `node.error("Error")`

The Catch node can also be used to handle errors. To invoke a Catch node, pass `msg` as a second argument to `node.error`:

```
node.error("Error",msg);
```

**Accessing Node Information**

The following properties are available to access information about the node:

* `node.id` - id of the node
* `node.name` - name of the node
* `node.outputCount` - number of node outputs

**Using environment variables**

Environment variables can be accessed using `env.get("MY_ENV_VAR")`.
