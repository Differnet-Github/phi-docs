# Message

## Abstract:
Groups are private messages. Each group contains at least 2 users and is a method of exchanging encrypted messages between users.

### File System
Groups are stored in the directory -    
`~~/accounts/accountID/group/`

Each folder in the directory represents a new group.

The contents of the folder are:  
`~/accounts/accountID/group/groupID/header.json` - header data for the group
`~/accounts/accountID/group/groupID/body.json` - message body for the group
`~/accounts/accountID/group/groupID/media/xxx.ext` - larget media files sent over group

### header.json:
```javascript
{
  "fingerprint": "----fingerprint----",
  "users": [
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
    },
    ...
  ],
}
```
##### fingerprint
fingerprint is a fingerprint of the groups shared symmetric key.

##### Users
users are the users that can access the contents of the group. There are 3 types of users:
1. private - fingerprint is a public key fingerprint, key is the group key encrypted with the fingerprint
2. hidden - fingerprint is encrypted with the group key, key is the group key encrypted with public key associated with the fingerprint.
3. anonymous - first is a unique key encrypted with a target public key. second is the group key encrypted with the first key.

### body.json:
```javascript
[
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
```
##### root
body.json is an array of messages that have been send between users.
##### fingerprint
fingerprint is a optional field that contains the fingerprint of the creater of the message.
##### type
type defines the type of message it is
##### body
body is the connects of the message.
TODO: define body more depending on the type
