---
description: Reads the contents of a file as either a string or binary buffer.
---

# Read File

### Inputs

* `filename` (string) : if not set in the node configuration, this property sets the filename to read. The filename should be an absolute path.

### Outputs

* `payload` (string | buffer) : The contents of the file as either a string or binary buffer.
* `filename` (string) : If not configured in the node, this optional property sets the name of the file to be read.

![](<../../../.gitbook/assets/image (19) (1).png>)

### Details

The filename should be an absolute path, otherwise it will be relative to the working directory of the Workspace process.

On Windows, path separators may need to be escaped, for example: `\\Users\\myUser`.

Optionally, a text file can be split into lines, outputting one message per line, or a binary file split into smaller buffer chunks - the chunk size being operating system dependant, but typically 64k (Linux/Mac) or 41k (Windows).

When split into multiple messages, each message will have a `parts` property set, forming a complete message sequence.

Encoding of input data can be specified from list of encodings if output format is string.

Errors should be caught and handled using a Catch node.
