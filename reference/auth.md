# Authentication

This endpoint allows a user to authenticate using their API key.

## Endpoint

`POST /auth/login`

## Parameters

| Name     | Type   | Description           |
|----------|--------|-----------------------|
| apiKey   | string | The user's API key    |

## Response

```json
{
  "status": "success",
  "token": "abc123xyz"
}
