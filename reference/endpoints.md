# Get Current Weather by ZIP Code

**Endpoint:**

`GET https://api.openweathermap.org/data/2.5/weather`

**Query Parameters:**

| Name     | Required | Type   | Description                      |
|----------|----------|--------|----------------------------------|
| `zip`    | Yes      | string | ZIP code (e.g., 95050)           |
| `units`  | Optional | string | Units: `imperial` or `metric`    |
| `appid`  | Yes      | string | Your API key                     |

**Sample Request:**

`GET https://api.openweathermap.org/data/2.5/weather?zip=95050&units=imperial&appid=YOUR_API_KEY`

**Sample Response:**

```json
{
  "coord": { "lon": -121.953, "lat": 37.3492 },
  "weather": [
    {
      "id": 800,
      "main": "Clear",
      "description": "clear sky",
      "icon": "01d"
    }
  ],
  "main": {
    "temp": 63.86,
    "feels_like": 63.7,
    "temp_min": 60.07,
    "temp_max": 60.78,
    "pressure": 1018,
    "humidity": 80
  }
}
```

**Response Field Descriptions**

| Field                    | Type    | Description                                  |
|--------------------------|---------|----------------------------------------------|
| `coord.lon`              | float   | Longitude of the location                    |
| `coord.lat`              | float   | Latitude of the location                     |
| `weather[0].main`        | string  | Weather condition (e.g., Clear)              |
| `weather[0].description` | string  | Detailed condition (e.g., clear sky)         |
| `main.temp`              | float   | Temperature in °F                            |
| `main.feels_like`        | float   | Apparent temperature                         |
| `main.temp_min`          | float   | Minimum temperature                          |
| `main.temp_max`          | float   | Maximum temperature                          |
| `main.pressure`          | integer | Atmospheric pressure (hPa)                   |
| `main.humidity`          | integer | Humidity percentage                          |
