# Surf Report API Reference

## 1. Resource Description

Provides data about current surfing conditions, including surf height, water temperature, wind speed and direction, and tide information. Also offers an overall recommendation indicating whether it’s a good time to surf.

## 2. Endpoints and Methods

**GET** `/surfreport/{beachId}`  
Gets the surf conditions for a specific beach.

## 3. Parameters

| Name       | Type   | Description                                              | Required |
|------------|--------|----------------------------------------------------------|----------|
| beachId    | path   | The unique identifier of beach                           | Yes      |
| units      | string | Units of measurement: metric or imperial                 | No       |
| format     | string | Format of response: json or xml                          | No       |
| apikey     | query  | Your API key                                             | Yes      |

### Path parameters

| Path parameter | Description |
|---|---|
| `{beachId}` | The value for the beach you want to look up. Valid beachId values are available from our site at `sampleurl.com`. |

### Query string parameters

| Query string parameter | Required / optional | Description | Type |
|---|---|---|---|
| `days` | Optional | The number of days to include in the response. Default is 3. | Integer |
| `time` | Optional | If you include the time, then only the current hour will be returned in the response. | Integer (Unix epoch, ms since 1970, UTC) |

## 4. Request Example

```http
GET https://api.openweathermap.org/surfreport/90401?apikey=YOUR_API_KEY
```

In the above code, replace `APIKEY` with your actual API key.

## 5. Response Example and Schema

{
  "surfreport": [
    {
      "beach": "Santa Cruz",
      "monday": {
        "1pm": {
          "tide": 5,
          "wind": 15,
          "watertemp": 80,
          "surfheight": 5,
          "recommendation": "Go surfing!"
        },
        "2pm": {
          "tide": -1,
          "wind": 1,
          "watertemp": 50,
          "surfheight": 3,
          "recommendation": "Surfing conditions are okay, not great."
        },
        "3pm": {
          "tide": -1,
          "wind": 10,
          "watertemp": 65,
          "surfheight": 1,
          "recommendation": "Not a good day for surfing."
        }
      }
    }
  ]
}

### Schema

| Field                       | Type   | Description                                |
| --------------------------- | ------ | ------------------------------------------ |
| beachId                     | string | Identifier of the beach                    |
| location                    | string | Beach name                                 |
| conditions                  | object | Surf condition details                     |
| conditions.waveHeight       | string | Height of waves (e.g., `4 ft` or `120 cm`) |
| conditions.tide             | string | Tide status (e.g., `Low`, `High`)          |
| conditions.waterTemperature | string | Water temp in Fahrenheit or Celsius        |
| conditions.recommendation   | string | Surfing advice (“Go surfing!”, etc.)       |
| units                       | string | Measurement units (`imperial` or `metric`) |
| reportTime                  | string | Timestamp of the report (ISO 8601 format)  |
