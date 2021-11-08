---
description: Plays audio or text to speech (TTS) in the Maya dashboard.
---

# Audio Out

To work the dashboard web page must be open.

Expects `msg.payload` to contain a buffer of a **wav** or **mp3** file.

If your browser has native support for Text-to-Speech then a `msg.payload` can also be a **string** to be read aloud.

When a `msg.reset` is available with value `true`, then playback of the current audio fragment will be stopped.

The **node status** reflects the current playback status:

* **started:** the audio fragment playback has been started.
* **reset:** the audio fragment playback has been reset (i.e. stopped before completed).

As soon as the audio fragment playback is completed, the node status will be cleared automatically.
