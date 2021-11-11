---
description: >-
  Writes msg.payload to a file, either adding to the end or replacing the
  existing content. Alternatively, it can delete the file.
---

# Modify File

### Inputs

* `filename` (string) : If not configured in the node, this optional property sets the name of the file to be updated. The filename should be an absolute path.
* `encoding` (string) : If encoding is configured to be set by msg, then this optional property can set the encoding.

### Outputs

On completion of write, input message is sent to output port.

![](<../../../.gitbook/assets/image (47).png>)

### Details

Each message payload will be added to the end of the file, optionally appending a newline (\n) character between each one.

If `msg.filename` is used the file will be closed after every write. For best performance use a fixed filename.

It can be configured to overwrite the entire file rather than append. For example, when writing binary data to a file, such as an image, this option should be used and the option to append a newline should be disabled.

Encoding of data written to a file can be specified from list of encodings.

Alternatively, this node can be configured to delete the file.
