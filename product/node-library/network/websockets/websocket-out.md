# Websocket Out

### Inputs

By default, `msg.payload` will be sent over the WebSocket.

### Outputs

No outputs because this is a final node.

![](<../../../../.gitbook/assets/image (60).png>)

### Details

By default, `msg.payload` will be sent over the WebSocket. The socket can be configured to encode the entire `msg` object as a JSON string and send that over the WebSocket.

If the message arriving at this node started at a WebSocket In node, the message will be sent back to the client that triggered the flow. Otherwise, the message will be broadcast to all connected clients.

If you want to broadcast a message that started at a WebSocket In node, you should delete the `msg._session` property within the flow.
