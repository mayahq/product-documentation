---
description: >-
  Perform playlist operations on spotify playlists
---
# Playlist
 Right now the node has only one function, which is to add tracks to a playlist. In the future there may be more.
## Inputs
* `action` (enum) :  Right now there is only one action available, which is to add tracks to a playlist. So you can't choose any other value.
* `tracks` (string | array[string]) :  Single track URI or an array of them. The tracks corresponding to given URIs will be added to the playlist.
* `playlistId` (string) :  ID of playlist to which the songs should be added. You can get this from the app, or dynamically get this from the response to a playlist search query (see search node documentation).

## Outputs
* `playlistSnapshotId` (JSON object) :  A snapshot ID for the playlist. You can learn more about snapshot IDs[here](https://developer.spotify.com/documentation/general/guides/working-with-playlists/#version-control-and-snapshots) 
