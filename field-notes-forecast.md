# Field notes: Open-Meteo current weather

## Request

`GET https://api.open-meteo.com/v1/forecast?latitude=52.52&longitude=13.41&current_weather=true`

Returns current weather conditions for a location. Status: 200 OK.

## Response fields

| Field | Type | Description | Example |
|---|---|---|---|
| `latitude` | number | Latitude of the grid cell actually used, which may differ slightly from the value sent | 52.512604 |
| `generationtime_ms` | number | Time the server took to generate the response, in milliseconds | 0.12 |
| `utc_offset_seconds` | number | The difference in seconds between Coordinated Universal Time (UTC) and the local time, which defaults to GMT unless the timezone parameter is set | 0 |
| `timezone` | string | the time zone used for all timestamps in the response; defaults to GMT unless the timezone parameter is set | GMT |
| `timezone_abbreviation` | string | the abbreviation of the local timezone | GMT |
| `elevation` | number | elevation of the location from the sea level | 38.0 |
| Field | Type | Description | Example |
|---|---|---|---|
| `current_weather_units` | object | Units for each field in `current_weather`. | |
| `current_weather_units.time` | string | Format of `current_weather.time`. Always `iso8601`. | iso8601 |
| `current_weather_units.interval` | string | Unit of `current_weather.interval`. | seconds |
| `current_weather_units.temperature` | string | Unit of `current_weather.temperature`. | °C |
| `current_weather_units.windspeed` | string | Unit of `current_weather.windspeed`. | km/h |
| `current_weather_units.winddirection` | string | Unit of `current_weather.winddirection`. | ° |
| `current_weather_units.is_day` | string | Always an empty string: `is_day` is a flag with no unit. | |
| `current_weather_units.weathercode` | string | Code system used for `current_weather.weathercode`. | wmo code |

## Example response

```json
{ "latitude": 52.512604, "longitude": 13.419517 }
```

Values are illustrative; current weather changes between calls.

## Errors

| Status | Cause | Reason in body |
|---|---|---|
| 400 Bad Request | Missing `longitude` | Parameter 'latitude' and 'longitude' must have the same number of elements |

## PokéAPI notes

- The Pokémon name is a path parameter: `/pokemon/ditto`
- Names are case-sensitive and lowercase

## Open questions

- Does the API accept lists of coordinates? (unverified)
