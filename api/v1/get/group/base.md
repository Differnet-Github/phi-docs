## List groups
GET: `/v1/group`

### Abstract:
Gets a list of groups that exist.

### Request:
```javascript
{
  "private": {
    "username": [
      {
        "value": "regex1",
        "filter": true
      },
      {
        "value": "regex2",
        "filter": false
      },
      ...
    ],
    "fingerprint": [
      {
        "value": "----fingerprint----",
        "filter": true
      },
      ...
    ]
  },
  "hidden": true,
  "anonymous": true
}
```
###### private
private contains an array of username regular expressions and fingerprints. The usernames and fingerprints have a filter boolean attached to them which will whitelist or blacklist when set to true or false.

###### hidden
hidden will blacklist or whitelist groups with hidden users when set.

###### anonymous
anonymous will blacklist or whitelist groups with anonymous users when set.

### Response:
```javascript
{
  "stat": 200,
  "groups": [
    "----fingerprint----",
    ...
  ]
}
```
###### groups
Groups is an array of post fingerprints that match the criteria.
