## List groups
GET: `/v1/profile`

### Abstract:
Gets a list of profiles that exist.

### Request:
```javascript
{}
```

### Response:
```javascript
{
  "stat": 200,
  "accounts": [
    "----fingerprint----",
    ...
  ]
}
```
###### accounts
accounts is an array of account fingerprints that match the criteria.x
