# Post

## Abstract:
Posts are how users will generate content for all other users to see.

### File System
Posts are stored in the directory -    
`~~/accounts/accountID/posts/`

Each folder in the directory represents a new post.

The contents of the folder are:  
`~/accounts/accountID/posts/postID/header.json` - the header data for the post
`~/accounts/accountID/posts/postID/body.json` - the body of the post
`~/accounts/accountID/posts/postID/comments/commentID.json` - the comments on the post

### header.json:
```javascript
{
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
}
```

##### fingerprint
fingerprint is a SHA-256 of the body.

##### Cipher
cipher is the symmetric algorithm used to do all symmetric encryption for this post

##### Creator
creator is the creator of the post. This field is optional. If the hidden flag is set to true then the fingerprint is encrypted with the post key.

##### Viewers
viewers are the people who can view the post. There are 4 types.

1. public - key is the post key not encrypted
2. private - fingerprint is a public key fingerprint, key is the post key encrypted with the fingerprint
3. hidden - fingerprint is encrypted with the post key, key is the post key encrypted with public key associated with the fingerprint.
4. anonymous - first is a unique key encrypted with a target public key. second is the post key encrypted with the first key.

##### Signature
Signature is only defined if the creator is defined

### body.json
```javascript
{
  "type": "text"
  "title": "Post title",
  "body": "Post Body"
}
```
##### Type
type is the type of post.
##### Title
title is the post tittle
#### Body
body is the body of the posts
TODO: defined post body for different types more.

### /comments/xxx.json
```javascript
{
  "body": {
    "fingerprint": "----fingerprint----",

    "comment": "",

    "timestamp": 1234567890
  },

	"signer": "----Signing Algorithm----",
	"signature": "----Signature----"
}
```
##### fingerprint
fingerprint is the fingerprint of the public key of the comment poster. This field is optional.

##### Comment
comment is a string that is the contents of the comment

##### Signature
Signature is only defined if the fingerprint is defined
