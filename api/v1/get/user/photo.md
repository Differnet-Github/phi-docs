## Get user profile
GET: `/v1/user/profile/`

### Abstract:
Retrieves the profile photo for a target user

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
  "photos": {
    "----fingerprint----": "---binary data---",
    ...
  }
}
```
##### Photos
photos is an object of photos retrieved indexed by their owners fingerprint
