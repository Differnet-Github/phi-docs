## Get header for group
GET: `/v1/group/media`

### Abstract:
Get the media file associated with a group fingerprint and media fingerprint

### Request:
```javascript
[
  {
    "group": "----fingerprint----",
    "media": "----fingerprint----"
  },
  ...
]
```
###### root
the request is an array of fingerprints that are to be retrieved
###### group
the group is the fingerprint of the group that the file is being retrieved
###### media
the media is the fingerprint of the media file that is being retrieved

### Response:
```javascript
{
  "stat": 200,
  "groups": {
    "----fingerprint----": {
      "----fingerprint----": "MEDIA BYTES"
    }
  }
}
```
###### posts
groups is an object of media groups retrieved indexed by their fingerprint which contain media files index by their fingerprints.
