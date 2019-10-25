# Post finalization
POST: `/v1/connection/finalize/`

Finalize the connection between two users.

Request:
```javascript
{
  "fingerprint": "----fingerprint----",
  "addresses": [
    {
      "type": "ip",
      "address": "192.168.0.101",
      "public": "----public key----"
    },
    {
      "type": "tor",
      //TODO:
    },
    {
      "type": "i2p",
      //TODO:
    },
    ...
  ]
}
```
Response:
```javascript
{
  "stat": 200,
  "fingerprint": "----fingerprint----",
  "addresses": [
    {
      "type": "ip",
      "address": "192.168.0.101",
      "public": "----public key----"
    },
    {
      "type": "tor",
      //TODO:
    },
    {
      "type": "i2p",
      //TODO:
    },
    ...
  ]
}
```
