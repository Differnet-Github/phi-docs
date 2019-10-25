## List groups
GET: `/v1/profile/account`

### Abstract:
Gets the contents of an account.

### Request:
```javascript
[
  {
    "value": "----fingerprint----",
    "filter": true
  }
]
```
###### root
root is an array of fingerprints with a filter attached to whitelist or blacklist it.

### Response:
```javascript
{
  "stat": 200,
  "accounts": {
    "----fingerprint----": {
    	"master": {
    		"factory": "----Asymmetric Key Factory----",
    		"public": "----Public Key----",
    		"cipher": "----Symmetric Encryption Algorithm----",
    		"private": "----Private Key Symmetric Cipher Text----",
    		"locked": false,
    		"keys": [
    			{
    				"merge": "----Key Derivation Function----",
    				"cipher": "----Symmetric Encryption Algorithm----",
    				"key": "----Symmetric Key----",
    				"factors": [
    					{
    						"type": "password",
    						"hash": "---Password Derivation Function----",
    						"iterations": 100000,
    						"salt": "V2h5IHlvdSBkbyB0aGlzPw==",
    						"keyLength": 256
    					}
    				]
    			}
    		]
    	},
    	"disposable": {
    		"factory": "----Asymmetric Key Factory----",
    		"public": "----Public Key----",
    		"private": "----Private Key Symmetric Cipher Text----",
    		"locked": false,
    		"keys": [
    			{
    				"merge": "----Key Derivation Function----",
    				"cipher": "----Symmetric Cipher Algorithm----",
    				"key": "----Symmetric Key----",
    				"factors": [
    					{
    						"type": "password",
    						"hash": "---Password Derivation Function----",
    						"iterations": 10000,
    						"salt": "V2h5IHlvdSBkbyB0aGlzPw==",
    						"keyLength": 256
    					}
    				]
    			}
    		],
    		"timestamp": 1570809434377,
    		"signer": "----Signing Algorithm----",
    		"signature": "----Signature----"
    	}
    },
    ...
  }
}
```
###### accounts
accounts is a object of account indexed by there fingerprints.
