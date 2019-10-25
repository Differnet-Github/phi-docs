## Get user list
GET: `/v1/user/`

### Abstract:
Retrieves a list of users from another client. Filters can be set on the information to minimize the bandwidth used.

### Request:
```javascript
{
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
  "following": [
    {
      "value": "----fingerprint----",
      "filter": true
    },
    ...
  ],
  "friends": [
    {
      "value": "----fingerprint----",
      "filter": true
    },
    ...
  ],
  "blocked": [
    {
      "value": "----fingerprint----",
      "filter": true
    },
    ...
  ]
}
```
##### Username
Username is an array of filters on the users that will be found.  Value is a regular expression for the username. If whitelist is set to true then only usernames that match the expression will be returned. If whitelist is set to false only usernames that don't match will be returned.

##### Following/Friends/Blocked
Following, Friends, and Blocked are arrays of filters. They can blacklist and whitelist users who follow/friend/block users that match the fingerprint value.

### Response:
```javascript
{
  "stat": 200,
  "users": [
    "----fingerprint----",
    ...
  ]
}
```
##### Users
Users is an array of user fingerprints that match the query
