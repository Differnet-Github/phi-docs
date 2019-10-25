## Get comment on post
GET: `/v1/post/comments`

### Abstract:
Gets the comments on a post

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
    "----fingerprint----": [
      {
        "body": {
          "fingerprint": "----fingerprint----",

          "comment": "",

          "timestamp": 1234567890
        },

      	"signer": "----Signing Algorithm----",
      	"signature": "----Signature----"
      },
      ...
    ],
    ...
  }
}
```
###### posts
posts is an object of comment arrays retrieved indexed by their fingerprint
