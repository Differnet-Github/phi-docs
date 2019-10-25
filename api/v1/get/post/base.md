## Get user profile
GET: `/v1/post/`

### Abstract:
Retrieves a list of post fingerprints that match a filter

### Request:
```javascript
{
  "creator": {
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
  "viewers": {
    "public": true,
    "private": [
      {
        "fingerprint": "----fingerprint----",
        "filter": false
      },
      ...
    ]
    "hidden": true,
    "anonymous": true
  },
  "type": {
    "text": true
    //TODO:
  }
}
```
##### creator
Creator can filter on the username and the fingerprint of the creator. Usernames and fingerprints can be whitelisted and blacklisted by setting filter to true or false.

##### viewers
Views contains information to filter based on the people who can see the post. Public can be set to true or false to whitelist or blacklist public posts. Private can be set to objects with fingerprints to whitelist or blacklist viewers by setting filter. Hidden can be set to true or false to whitelist or blacklist post that have hidden viewers. Anonymous can be set to true or false to whitelist or blacklist post that have anonymous viewers.

##### type
Type can set each post type to true or false to whitelist or blacklist post types.

### Response:
```javascript
{
  "stat": 200,
  "posts": [
    "----fingerprint----",
    ...
  ]
}
```

##### posts
posts is a array of fingerprints
