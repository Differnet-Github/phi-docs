## Get body for post
GET: `/v1/post/body`

### Abstract:
Retrieves the body for target posts

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
      {
        "type": "text"
        "title": "Post title",
        "body": "Post Body"
      }
    },
    ...
  }
}
```
###### posts
posts is an object of post body retrieved indexed by their fingerprint
