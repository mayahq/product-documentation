---
description: >-
  Control Spotify playback - play, pause, skip, etc.
---
# Control Playback
 You can use this node to toggle shuffle or repeat, play, pause, resume and skip songs, and add songs to queue.
## Properties
* `action` (enum) :  The action that the node will perform. The actions "play", "pause", "resume" and "skip" are obvious. See below for "toggleRepeat", "toggleShuffle" and "addToQueue".

### How "toggleRepeat" works
 When you set the action to "toggleRepeat", you will also additionally need to specify the repeatMode property. The property can have the following values (you will need to type these out in the field) -
* `track` (string) :  Set repeatMode to "track" to repeat the currently playing track
* `context` (string) :  Set repeatMode to "context" to repeat the currently playing context, i.e., repeat currently playing album, playlist, etc.
* `off` (string) :  Set repeatMode to "off" to turn off repeat.

### How "toggleShuffle" works
 When you set the action to "toggleShuffle", you will also additionally need to specify the shuffleMode property. The property can have the following values (you will need to type these out in the field) -
* `true` (string) :  Set shuffleMode to "true" to turn shuffle on.
* `false` (string) :  Set shuffleMode to "false" to turn shuffle off.

### How "addToQueue" works
 When you set the action to "addToQueue", you will also additionally need to specify the trackUri property. This corresponds to the URI of the track (for example, _spotify:track:4iV5W9uYEdYUVa79Axb7Rh_) that you want to add to the queue. You can read more about track URIs on Spotify [here](https://community.spotify.com/t5/FAQs/What-s-a-Spotify-URI/ta-p/919201).
## Outputs
 This node does not have any outputs, i.e., it does not add or modify any properties to the msg object.