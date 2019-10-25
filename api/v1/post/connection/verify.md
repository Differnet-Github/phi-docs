# Post verification
POST: `/v1/connection/verify/`

Verifies the connection between two users.

Request:
```javascript
{
  "code": "----random bytes----"
}
```
Response:
```javascript
{
  "stat": 200,
  "verify": true
}
```
