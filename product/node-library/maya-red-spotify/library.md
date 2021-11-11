---
description: >-
  Like or unlike songs and albums, query liked songs and albums
---
# Library
 Spotify lets you to "like" songs or albums, thus adding them to your personal library. This node allows you to do just that, without opening the app.
## Properties
 There's only one property - "action". If it's value is "likeSong", "likeAlbum", "unlikeSong" or "unlikeAlbum", you need to provide the corresponding song or album ID in the additional field (Song ID or Album ID).
 If action is "getLikedSongs" or "getLikedAlbums", you have to set two additional properties - "limit" and "offset".
* `limit` (number) :  The number of liked songs or albums you want to fetch. For example, if the value is 12, it'll fetch 12 liked songs or albums. The maximum allowed value for this property is 50.
* `offset` (number) :  The number of songs or albums to skip when fetching. For example if offset is 0 and limit is 10, the node will fetch the latest 10 liked songs. If you then change the offset to 10, the node will fetch the next 10 liked songs.

## Outputs
 If the action is not one of "getLikedSongs" or "getLikedAlbums", there is no output, i.e., the node does not add or change any properties on the msg object. Otherwise, it adds the following properties -
* `searchResults` (JSON object) :  A list of tracks if action is "getLikedSongs", a list of albums if action is "getLikedAlbums"
