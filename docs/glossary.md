# API Glossary

This glossary provides definitions of key terms and fields used in the Weather API.  
Use it as a quick reference to avoid ambiguity when working with responses and parameters.

## Core Terms

- **API Key**  
  A unique token required to authenticate requests. Pass it using the `appid` query parameter.

- **Endpoint**  
  A specific URL that provides access to a function of the API (e.g., `/weather`).

- **JSON**  
  The data format returned by the API. Responses include key–value pairs that describe weather data.

## Weather Fields

- **temp**  
  The current temperature, measured in Celsius by default (Kelvin or Fahrenheit if units specified).

- **feels_like**  
  The perceived temperature, accounting for wind chill and humidity.

- **humidity**  
  The percentage of moisture in the air.

- **pressure**  
  Atmospheric pressure in hPa (hectopascals).

- **wind.speed**  
  Wind speed, in meters per second (default).

- **weather.main**  
  A short label for weather conditions (e.g., `Rain`, `Clouds`, `Clear`).

- **weather.description**  
  A human-readable description of the weather (e.g., `light rain`, `scattered clouds`).

## Parameters

- **q**  
  Query parameter for city name (e.g., `q=London`).

- **lat, lon**  
  Geographic coordinates used to request weather data by location.

- **units**  
  Specifies units for temperature (`standard`, `metric`, or `imperial`).

- **lang**  
  Optional parameter to set the language for weather descriptions.
