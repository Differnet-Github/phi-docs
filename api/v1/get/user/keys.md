## Get user keys
GET: `/v1/user/keys/`

### Abstract:
Retrieves the profile key for target users

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
  "keys": {
    "----fingerprint----": {
      "master": {
        "factory": "----Asymmetric Key Factory----",
        "public": "----Public Key----"
      },
      "disposable": {
        "factory": "----Asymmetric Key Factory----",
        "public": "----Public Key----",

        "timestamp": 1570809434377,

        "signer": "----Signing Algorithm----",
        "signature": "----Signature----"
      }
    },
    ...
  }
}
```
##### Keys
Keys is an object of keys retrieved indexed by their owners fingerprint.
