# Get 5-Day Forecast by ZIP Code

**Endpoint:**

`GET https://api.openweathermap.org/data/2.5/forecast`

**Query Parameters:**

| Name     | Required | Type   | Description                       |
|----------|----------|--------|-----------------------------------|
| `zip`    | Yes      | string | ZIP code (e.g., 11230)            |
| `units`  | Optional | string | Units: `imperial` or `metric`     |
| `appid`  | Yes      | string | Your OpenWeatherMap API key       |

**Sample Request:**

`GET https://api.openweathermap.org/data/2.5/forecast?zip=11230&units=imperial&appid=YOUR_API_KEY`

**Sample Response (truncated):**

```json
{
  "cod": "200",
  "message": 0,
  "cnt": 40,
  "list": [
    {
      "dt": 1753812000,
      "main": {
        "temp": 92.98,
        "feels_like": 100.63,
        "temp_min": 92.98,
        "temp_max": 93.43,
        "pressure": 1016,
        "sea_level": 1016,
        "grnd_level": 1014,
        "humidity": 50,
        "temp_kf": 0.25
      },
      "weather": [
        {
          "id": 802,
          "main": "Clouds",
          "description": "scattered clouds",
          "icon": "03d"
        }
      ],
      "clouds": { "all": 37 },
      "wind": { "speed": 8.75, "deg": 201, "gust": 9.48 },
      "visibility": 10000,
      "pop": 0
    }
  ],
  "city": {
    "name": "Brooklyn",
    "country": "US"
  }
}
```

## Response Field Descriptions

| Field                      | Type    | Description                                       |
|----------------------------|---------|---------------------------------------------------|
| `list[i].dt`               | integer | Forecast timestamp (Unix)                         |
| `list[i].main.temp`        | float   | Forecasted temperature in °F                      |
| `list[i].main.feels_like`  | float   | Perceived temperature in °F                       |
| `list[i].main.humidity`    | integer | Humidity percentage                               |
| `list[i].weather[0].description` | string | Description of weather (e.g., scattered clouds) |
| `list[i].clouds.all`       | integer | Cloudiness percentage                             |
| `list[i].wind.speed`       | float   | Wind speed (mph or m/s, depending on unit system) |
| `list[i].pop`              | float   | Probability of precipitation (0–1)                |
| `list[i].visibility`       | integer | Visibility in meters                              |
| `city.name`                | string  | City name                                         |
| `city.country`             | string  | Country code (e.g., US)                           |
