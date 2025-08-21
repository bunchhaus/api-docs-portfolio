# Weather API Quick Reference

A one‑page cheat sheet of the most commonly used Weather API endpoints and parameters.  
For the full walkthrough, see **[Getting Started](gettingstarted.md)**. For auth details, see **[Authentication](authentication.md)**.

## Base URLs

```
https://api.openweathermap.org/data/2.5
https://api.openweathermap.org/geo/1.0     # Geocoding endpoints
```
All requests require your API key as the `appid` query parameter.

## Core Endpoints (Data 2.5)

| Group            | Endpoint        | Purpose                                   | Minimal Example |
|------------------|-----------------|-------------------------------------------|-----------------|
| Current Weather  | `/weather`      | Current conditions by city/coords         | `/weather?q=London,UK&appid=API_KEY` |
| 5‑Day Forecast   | `/forecast`     | 5‑day / 3‑hour forecast                   | `/forecast?q=Paris,FR&appid=API_KEY` |
| Air Pollution    | `/air_pollution`| Air Quality Index and pollutant components| `/air_pollution?lat=37.77&lon=-122.41&appid=API_KEY` |

> Add `&units=metric` for °C or `&units=imperial` for °F.  
> You can use `q=City,CountryCode` **or** `lat` + `lon` for location.

## Quick Examples

### Current Weather (by city)

```bash
curl -s "https://api.openweathermap.org/data/2.5/weather?q=San%20Francisco,US&units=metric&appid=$API_KEY"
```

### 5‑Day Forecast (by city)

```bash
curl -s "https://api.openweathermap.org/data/2.5/forecast?q=Berlin,DE&units=metric&appid=$API_KEY"
```

### Air Pollution (by coordinates)

```bash
curl -s "https://api.openweathermap.org/data/2.5/air_pollution?lat=37.7749&lon=-122.4194&appid=$API_KEY"
```

### Geocoding (convert city → coordinates)

```bash
curl -s "https://api.openweathermap.org/geo/1.0/direct?q=Tokyo,JP&limit=1&appid=$API_KEY"
```

## Common Query Parameters

| Name     | Type   | Values / Format                          | Notes                                   |
|----------|--------|-------------------------------------------|-----------------------------------------|
| `q`      | string | `City,CountryCode` (e.g., `Paris,FR`)     | URL‑encode spaces (e.g., `San%20Francisco`). |
| `lat`    | float  | Latitude                                  | Alternative to `q`.                     |
| `lon`    | float  | Longitude                                 | Alternative to `q`.                     |
| `units`  | string | `standard` (K, default), `metric`, `imperial` | Temperature units.                   |
| `lang`   | string | ISO code (e.g., `en`, `es`, `fr`)         | Localizes condition text.               |
| `appid`  | string | Your API key                              | Required on every request.              |

## Response Snippet (Current Weather)

```json
{
  "name": "San Francisco",
  "coord": { "lon": -122.4194, "lat": 37.7749 },
  "weather": [{ "main": "Clouds", "description": "scattered clouds" }],
  "main": { "temp": 18.2, "feels_like": 17.5, "humidity": 72 }
}
```

---

## Status & Rate Limits (at a glance)

- Typical success code: **200 OK**.  
- Common errors: **401** (invalid key), **404** (not found), **429** (rate limit).  
- See **[Status and Error Codes](status-errors.md)** and **[Rate Limiting](rate-limits.md)** for details.

---

## Tips

- Prefer `lat`/`lon` for ambiguous city names.  
- Cache responses when possible to reduce calls and avoid **429**.  
- Never commit your `appid` to version control.  
