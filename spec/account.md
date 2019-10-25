# Account

## Abstract:
Accounts are users that are logged in. This document contains all data pertaining to logging in out, storage and networking of accounts.

### File System
Account data is stored in the directory `~/accounts/accountID/`

Each folder in `~/accounts/accountID/` represents a new account.

The contents of the folder are:	 
`~/accounts/accountID/account.json` - encryption data for the account	 
`~/accounts/accountID/archive.json` - encrypted archive of the account  
`~/accounts/accountID/network.json` - data for running the networks  
`~/accounts/accountID/network-buffer.json` - buffer of encrypted data that was sent to this account while logged out  
`~/accounts/accountID/files.json` - encrypted data for accessing the rest of the file system  
`~/accounts/accountID/users/` - users saved with account	 
`~/accounts/accountID/posts/` - posts saved with account	 
`~/accounts/accountID/messages/` - messages saved with account	 

### account.json
```javascript
{
	"master": {
		"factory": "----Asymmetric Key Factory----",
		"public": "----Public Key----",
		"cipher": "----Symmetric Encryption Algorithm----",
		"private": "----Private Key----" || "----Private Key Symmetric Cipher Text----",

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
						"iterations": 10000,
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
		"private": "----Private Key----" || "----Private Key Symmetric Cipher Text----",

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
}
```
##### Master Key:
The Master Key is a asymmetric key pair. This key is used as the primary identifier of accounts. This key should only ever be used to sign disposable keys, the time attached to them, and archives. It should only be used to encrypt archived keys. Clients should prompt users to set a backup key. This key should then be used to encrypt the master private key. After the master private key is encrypted it should be saved to storage and removed from all locations where it is currently un-encrypted.

##### Disposable Key
The Disposable key is a asymmetric key pair. This key is used in active memory to sign and access posts. This key can be changed at any time as long as the master key is available to sign the new one. All past disposable keys should be stored with accounts as a hashed public key, a private key encrypted with a archive key, the archived date and the archives signature. Accounts should be able to be locked with a key that will prevent access to account data.

> ###### Keys
The Master key and Active Disposable key will have a keys object attached to them. This key object is an array of methods that will allow the user to encrypt the key.

### network.json
```javascript
[
	{
		"type": "tor",
		//TODO:
	},
	{
		"type": "i2p",
		//TODO:
	},
	{
		"type": "ip",
		"key": {
			"public": "----Public Key----"
			"private": "----Private Key----"
		}
	},
	...
]
```
##### root
Network contains an array of information needed for hosting services.
##### ip
IP contains a public and a private key for sending data through this service
##### tor
TODO:
##### i2p
TODO:

### archive.json
```javascript
[
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
]
```
##### Archive
The account archive is a list of old disposable keys for the account. The private key will be encrypt with a symmetric key and that key will be encrypted with the master key. The public key will be stored as a hash. Each key in the archive in include a timestamp of when it was archived and a signature from the master key.

### network-buffer.json
```javascript
[
	"BYTES",
]
```
##### Network Buffer
The network buffer is a array of packets that where received while the user was logged out.

### files.json
```javascript
{
	"lock": "----Asymmetric Encryption Algorithm----",
	"cipher": "----Symmetric Cipher Algorithm----",

	"key": "----Symmetric Key----"

	"timestamp": 1234567890,

	"signer": "----Signing Algorithm----",
	"signature": "----Signature----"
}
```
##### Files
Files is the key needed to decrypt all information associated with this account. It is encrypted with the disposable key. This key will also have a timestamp and a signature from the disposable key that generated it.
