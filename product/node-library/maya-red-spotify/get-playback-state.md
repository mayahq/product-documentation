---
description: >-
  Get information about what the user is playing and how
---
# Get Playback State
 You can use this node to get playback state, i.e., information like what the user is playing, which device they are using, whether their repeat mode is on, etc.
## Properties
* `stateType` (enum) :  Use "playback" if you want to get the current track or episode being played (corresponding to this API). Use "playerState" if you want to get info about the current state of playback like whether shuffle is on, which device the user is using, etc.

## Outputs
* `spotifyState` (JSON object) :  Contains the requested information about playback state. [This page](https://developer.spotify.com/documentation/web-api/reference/#/operations/get-the-users-currently-playing-track) describes what the object will contain if stateType is "playback". [ This page](https://developer.spotify.com/documentation/web-api/reference/#/operations/get-information-about-the-users-current-playback) describes what the object will contain if stateType is "playerState".
