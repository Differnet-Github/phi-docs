## Get header for post
GET: `/v1/post/header`

### Abstract:
Retrieves the header for target posts

### Request:
```javascript
[
  "----fingerprint----",
  ...
]
```
##### root
the request is an array of fingerprints that are to be retrieved

### Response:
```javascript
{
  "stat": 200,
  "posts": {
    "----fingerprint----": {
      "data": {
        "fingerprint": "----fingerprint----",

        "cipher": "----Symmetric Encryption Algorithm----",

        "creator": {
          "fingerprint": "----fingerprint----",
          "hidden": true
        },

        "viewers": [
          {
            "type": "public",
            "key": "----Symmetric Key----"
          },
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
          }
        ],
        "timestamp": 123467890
      },

      "signer": "----Signing Algorithm----",
      "signature": "----Signature----"
    },
    ...
  }
}
```
###### posts
posts is an object of post headers retrieved indexed by their fingerprint
