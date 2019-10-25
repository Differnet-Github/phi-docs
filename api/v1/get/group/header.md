## Get header for group
GET: `/v1/group/header`

### Abstract:
Get the header for post with target fingerprints

### Request:
```javascript
[
  "----fingerprint----",
  ...
]
```
###### root
the request is an array of fingerprints that are to be retrieved

### Response:
```javascript
{
  "stat": 200,
  "headers": {
    "----fingerprint----": {
      "fingerprint": "----fingerprint----",
      "users": [
        {
          "type": "private",
          "fingerprint": "----fingerprint----",
          "key": "----Symmetric Key----"
        },
        {
          "type": "hidden",
          "fingerprint": "----fingerprint----",
          "key": "----Symmetric Key----"
        },
        {
          "type": "anonymous",
          "first": "----Symmetric Key----",
          "second": "----Symmetric Key----"
        },
        ...
      ],
    }
  }
}
```
###### posts
headers is an object of post headers retrieved indexed by their fingerprint.
