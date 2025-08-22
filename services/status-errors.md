# Status and Error Codes — Weather API

Every Weather API request returns an HTTP status code in the response header.  
These codes indicate whether the request was successful or if an error occurred.  

## Common HTTP Status Codes

| Code | Text          | Description |
|------|---------------|-------------|
| 200  | OK            | Successful request and response. |
| 400  | Bad Request   | Malformed parameters or other invalid input. |
| 401  | Unauthorized  | Missing or invalid API key. |
| 403  | Forbidden     | You don’t have permission to access this resource. |
| 404  | Not Found     | The requested resource doesn’t exist. |
| 429  | Too Many Requests | You have exceeded your rate limit. |
| 500  | Internal Server Error | A problem occurred on the server. Retry later. |

## Viewing Status Codes

To view status codes in the response header, add the `-i` option to your `curl` command:

```bash
curl -i -X GET "https://api.openweathermap.org/data/2.5/weather?zip=95050&appid=$API_KEY&units=imperial"
```

Example response header:

```http
HTTP/1.1 200 OK
Server: openresty
Date: Thu, 06 Dec 2018 22:58:41 GMT
Content-Type: application/json; charset=utf-8
Content-Length: 446
Connection: keep-alive
```

## Error Response Format

When an error occurs, the response body is JSON with an `error` object:

```json
{
  "cod": 401,
  "message": "Invalid API key. Please see http://openweathermap.org/faq#error401"
}
```

## Troubleshooting Tips

- **401 Unauthorized** → Check that you included a valid API key.  
- **400 Bad Request** → Verify that all required parameters are present and correctly formatted.  
- **404 Not Found** → Double-check the endpoint and query parameters.  
- **429 Too Many Requests** → See [Rate Limiting](rate-limits.md).  
- **500 Internal Error** → Retry after a short delay. If the problem persists, check [OpenWeather status page](https://status.openweathermap.org/).  

## Next Steps

- Learn about [Rate Limiting and Thresholds](rate-limits.md) to avoid hitting 429 errors.  
