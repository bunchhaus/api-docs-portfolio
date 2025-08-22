# Getting Started — Weather API

This tutorial walks you through making your first call to the Weather API.

## Prerequisites

This setup procedure requires that you have an existing Open Weather Account.

You can can sign up at [OpenWeatherMap Sign Up](https://home.openweathermap.org/users/sign_up).

## Get Your API key

1. Go to [My API Keys](https://home.openweathermap.org/api_keys) and generate an API key.

   **Note:** You can generate as many API keys as needed for your subscription.

2. Save your key in an environment variable:

```bash
export API_KEY=your_api_key_here
```

## Make an API Request

Make a Weather API request to return a JSON response for the current conditions information for San Francisco, CA. You must include your API key's alphanumeric string with every request and use HTTPS for requests that include the API key.

1. Click API_KEY in the code below to insert the key's alphanumeric string:

   ```bash
   API_KEY=YOUR_API_KEY

   curl -s "https://api.openweathermap.org/data/2.5/weather?q=San%20Francisco,US&units=metric&appid=$API_KEY"

   ```

2. Click the copy icon in the code sample to copy the curl command.
3. Paste the command in a terminal window and run the command.

The response is a JSON object in the form:

```json
{
  "coord": { "lon": 122.41, "lat": 37.77 },
  "weather": [ { "id": 500, "main": "Rain", "description": "light rain" } ],
  "main": { "temp": 18.5, "humidity": 82 },
  "name": "San Francisco"
}
```

## Explore Other Endpoints

- **5‑day Forecast:** `/forecast`

## What's Next

See the [Authentication](authentication.md) page for details on using your key securely.
