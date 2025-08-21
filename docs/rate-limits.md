# Rate Limiting and Thresholds — Weather API

To ensure fair usage and protect service stability, the Weather API enforces rate limits based on your subscription plan.  
Every request counts toward your quota.

## Rate Limits by Plan

| Plan        | Calls per minute | Monthly Price | Notes |
|-------------|-----------------|---------------|-------|
| **Free**    | 60              | Free          | For exploration and low‑traffic apps. |
| **Startup** | 600             | $40/month     | Suitable for small apps. |
| **Developer** | 3,000         | $180/month    | For growing apps and moderate traffic. |
| **Professional** | 30,000     | $470/month    | For production workloads. |
| **Enterprise** | 200,000      | $2,000/month  | For large‑scale or mission‑critical apps. |

> **Note:** Each API call (for example, fetching current weather) counts toward your quota.  

## What Happens If You Exceed the Limit?

- You’ll receive an **HTTP 429 Too Many Requests** error.  
- Additional requests may be throttled (slowed down) or rejected until your quota resets.  
- The response may include headers showing your current usage and reset time.  

Example headers:

```http
X-RateLimit-Limit: 60
X-RateLimit-Remaining: 0
X-RateLimit-Reset: 1692652800
```

## Example: Checking Rate Limit Status

```bash
curl -i "https://api.openweathermap.org/data/2.5/weather?q=London,UK&appid=$API_KEY&units=metric"
```

Response headers:

```http
HTTP/1.1 429 Too Many Requests
Content-Type: application/json
X-RateLimit-Limit: 60
X-RateLimit-Remaining: 0
X-RateLimit-Reset: 1692652800
```

## Best Practices for Handling Rate Limits

- **Cache responses** to avoid unnecessary repeated calls.  
- **Batch requests** where possible instead of calling per user action.  
- **Check response headers** for remaining quota before making large bursts.  
- **Back off and retry** after the reset window if you receive a 429 error.  
- **Upgrade your plan** if your app consistently needs more capacity.  

## Next Steps

- Review [Status and Error Codes](status-errors.md) for details on the 429 response.  
- Continue to [Quick Reference](quick-reference.md) for common endpoints.  
