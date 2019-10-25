# Get user archive
GET: `/v1/user/archive/`

### Abstract:
Retrieves the archive for a target users

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
  "archives": {
    "----fingerprint----": [
    	{
    		"fingerprint": "----fingerprint----",

    		"cipher": "----Symmetric Cipher Algorithm----",
    		"lock": "----Asymmetric Encryption Algorithm----",
    		"key": "----Symmetric Key Asymmetric Cipher Text----",
    		"private": "---Private Key Symmetric Cipher Text----",

    		"timestamp": 1570809834377,

    		"signer": "----Signing Algorithm----",
    		"signature": "----Signature----"
    	},
    	...
    ],
    ...
  }
}
```
##### Archives
archives is an object of archives retrieved indexed by their owners fingerprint
