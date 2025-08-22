# Authentication and Authorization — Weather API

All requests to the Weather API must be authenticated with an API key. Authentication ties usage to your account and enforces plan limits.

## Prerequisites

- An OpenWeather account with billing set up (if required by your plan).
- Access to your **API Keys** page in the dashboard.

## Get your API key

1. Sign in to the OpenWeather dashboard.
2. Go to **API Keys** → **Create Key**.
3. Copy the generated key and store it securely.
4. (Optional) Add a label/description to track usage.

> If a key is exposed or you suspect misuse, **revoke it and create a new one** immediately.

## Base URL

```plaintext
https://api.openweathermap.org/data/2.5
```

## Ways to send your key

OpenWeather requires the key to be passed as the `appid` query parameter.

### Standard usage

Append `appid=YOUR_API_KEY` to the request URL.

```bash
# Replace YOUR_API_KEY first
API_KEY=YOUR_API_KEY

curl -s   "https://api.openweathermap.org/data/2.5/weather?q=San%20Francisco,US&units=metric&appid=$API_KEY"
```

> **Note:** Unlike some APIs, OpenWeather does **not** accept the key in an `Authorization` header. Always use the `appid` parameter.

## Make a test request (copy‑ready)

This verifies your key is valid and your network can reach the API.

```bash
API_KEY=YOUR_API_KEY

curl -s   "https://api.openweathermap.org/data/2.5/weather?q=San%20Francisco,US&units=metric&appid=$API_KEY"
```

### Expected response (truncated)

```json
{
  "coord": { "lon": -122.4194, "lat": 37.7749 },
  "weather": [{ "id": 802, "main": "Clouds", "description": "scattered clouds" }],
  "main": {
    "temp": 18.2,
    "feels_like": 17.5,
    "humidity": 72
  },
  "name": "San Francisco"
}
```

## Apply API key restrictions

Reduce risk by limiting where and how your key can be used.

- **Application restrictions** — Limit a key to certain origins or clients.
  - Web: restrict to allowed domains (e.g., `https://yourapp.example`)
  - Server: restrict by source IPs or CIDR ranges
  - Mobile: restrict to specific app identifiers / signing fingerprints

> Keys without restrictions are easier to abuse. Add restrictions before deploying to production.

## Key scope and limits

- **Scope:** Keys grant access to OpenWeather API endpoints for your account.
- **Rate limits:** All requests made with your key count toward your plan (see **Rate Limiting and Thresholds**).
- **Rotation:** Rotate keys on a regular schedule and immediately after exposure.

## Security best practices

- Do not commit keys to Git, logs, or client-side code.
- Use environment variables or a secrets manager.
- Monitor usage and set alerts for unusual spikes.

## Error responses

Authentication and authorization errors return standardized JSON. Use the HTTP status to branch handling logic.

### 401 Unauthorized — missing/invalid key

```http
HTTP/1.1 401 Unauthorized
Content-Type: application/json

{
  "cod": 401,
  "message": "Invalid API key. Please see http://openweathermap.org/faq#error401 for more info."
}
```

### 429 Too Many Requests — rate limit exceeded

```http
HTTP/1.1 429 Too Many Requests
Content-Type: application/json
Retry-After: 60

{
  "cod": 429,
  "message": "You have exceeded the allowed number of requests."
}
```

## What’s next

- Proceed to **Status and Error Codes** for the full response model.
- Review **Rate Limiting and Thresholds** to plan retries and backoff.
- Continue with the **Quick Start** and endpoint reference to build calls.
