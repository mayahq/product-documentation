---
description: Runs a system command and returns its output.
---

# Exec

The node can be configured to either wait until the command completes, or to send its output as the command generates it.

The command that is run can be configured in the node or provided by the received message.

### Inputs

* `payload` (string) : if configured to do so, will be appended to the executed command.
* `kill` (string) : the type of kill signal to send an existing exec node process.
* `pid` (number|string) : the process ID of an existing exec node process to kill.

### Outputs

This node has the following three output nodes :

1. Standard output :
   * `payload` (string) : the standard output of the command.
   * `rc` (object) : exec mode only, a copy of the return code object (also available on port 3)
2. Standard error :
   1. `payload` (string) : the standard error of the command.
   2. `rc` (object) : exec mode only, a copy of the return code object (also available on port 3)
3. Return code :
   1. `payload` (object) : an object containing the return code, and possibly `message`, `signal` properties.

![](<../../../.gitbook/assets/image (33).png>)

### Details

By default uses the `exec` system call which calls the command, waits for it to complete, and then returns the output. For example a successful command should have a return code of `{ code: 0 }`.

Optionally can use `spawn` instead, which returns the output from stdout and stderr as the command runs, usually one line at a time. On completion it then returns an object on the 3rd port. For example, a successful command should return `{ code: 0 }`.

Errors may return extra information on the 3rd port `msg.payload`, such as a `message` string, `signal` string.

The command that is run is defined within the node, with an option to append `msg.payload` and a further set of parameters.

Commands or parameters with spaces should be enclosed in quotes - `"This is a single parameter"`

The returned `payload` is usually a _string_, unless non-UTF8 characters are detected, in which case it is a _buffer_.

The node's status icon and PID will be visible while the node is active. Changes to this can be read by the `Status` node.

The `Hide console` option will hide the process console normally shown on Windows systems.

**Killing processes**

Sending `msg.kill` will kill a single active process. `msg.kill` should be a string containing the type of signal to be sent, for example, `SIGINT`, `SIGQUIT` or `SIGHUP`. Defaults to `SIGTERM` if set to an empty string.

If the node has more than one process running then `msg.pid` must also be set with the value of the PID to be killed.

If a value is provided in the `Timeout` field then, if the process has not completed when the specified number of seconds has elapsed, the process will be killed automatically

Tip: if running a Python app you may need to use the `-u` parameter to stop the output being buffered.
