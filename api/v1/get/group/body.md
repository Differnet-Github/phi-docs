## Get body for group
GET: `/v1/group/body`

### Abstract:
Get the body for post with target fingerprints

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
  "bodys": {
    "----fingerprint----": [
      {
        {
          "fingerprint": "----fingerprint----",

          "type": "text",
          "body": "",

          "timestamp": 1234567890,
        },

      	"signer": "----Signing Algorithm----",
      	"signature": "----Signature----"
      }
    ]
  }
}
```
###### posts
bodys is an object of post bodys retrieved indexed by their fingerprint.
