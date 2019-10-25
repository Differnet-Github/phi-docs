## Get user profile
GET: `/v1/user/profile/`

### Abstract:
Retrieves the profile information for a target users

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
  "users": {
    "----fingerprint----": {
    	"data": {
    		"username": "username",
    		"bio": "This is where the bio of the user would go",
    		"photo": "----fingerprint----",
    		"following": [
    			"fingerprint": "----fingerprint----"
    		],
    		"friends": [
    			"fingerprint": "----fingerprint----"
    		],
    		"blocked": [
    			"fingerprint": "----fingerprint----"
    		],
    		"timestamp": 1570809434377
    	},
    	"signer": "----Signing Algorithm----",
    	"signature": "----Signature----"
    },
    ...
  }
}
```
##### Users
users is an object of users retrieved indexed by their fingerprint.
