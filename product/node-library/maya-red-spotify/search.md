---
description: >-
  Search through songs, albums, artists and playlists
---
# Search
## Inputs
* `query` (string) :  The search query (what you'd type into the search box if you were to search directly in the spotify app)
* `searchType` (string) :  Comma-separated list of the types of resources you'd like to search through. The possible values of resource types are "artist", "track", "album", and "playlist". If you want to search for playlists, you cannot include any other resource type in the search, i.e., "playlist,track" is not a valid value.

## Outputs
* `searchResults` (JSON object) :  Contains the search results. If you searched for playlists, you can get an idea of what searchResults contains[here](https://developer.spotify.com/documentation/web-api/reference/#/operations/get-a-list-of-current-users-playlists). For everything else, you can refer to [this](https://developer.spotify.com/documentation/web-api/reference/#/operations/search).

## Search result structure
### Tracks
A single track will have this structure. There can be multiple tracks in the search results array
* type: always equal to "track"
* name: name of the track
* artists: comma-separated list of artists in the track
* uri: spotify URI of the track
* score: numeric value representing how relevant the track is with respect to the search
* images: array of image URLs for the track's cover art, by resolution. May not always exist
* imageUrl: image URL of the smallest-resolution available image of the track's cover art
### Artists
A single artist will have this structure. There can be multiple artists in the search results array
* type: always equal to "artist"
* name: name of the artist
* uri: spotify URI of the artist
* score: numeric value representing how relevant the artist is with respect to the search
* images: array of image URLs for the artist's profile photo, by resolution. May not always exist
* imageUrl: image URL of the smallest-resolution available image of the artist's profile photo
### Albums
A single album will have this structure. There can be multiple albums in the search results array
* type: always equal to "album"
* name: name of the album
* artists: comma-separated list of artists in the album
* uri: spotify URI of the album
* images: array of image URLs for the album's cover art, by resolution. May not always exist
* imageUrl: image URL of the smallest-resolution available image of the album's cover art
### Playlists
A single playlist will have this structure. There can be multiple playlists in the search results array
* type: always equal to "playlist"
* name: name of the playlist
* uri: spotify URI of the playlist
* images: array of image URLs for the track's album art, by resolution. May not always exist
* imageUrl: image URL of the smallest-resolution available image of the track's album art