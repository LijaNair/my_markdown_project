# GET /weather
The `GET /weather` endpoint allows users to retrieve current weather data for any location on Earth. It aggregates real-time data from global and local weather models, satellites, radars, and an extensive network of weather stations. The data is available in multiple formats, including JSON, XML, and HTML.

This endpoint provides detailed weather information such as:
- Temperature
- Humidity
- Wind speed and direction
- Atmospheric pressure
- Cloud coverage
- Visibility



## Use Cases

- Displaying weather information in travel and tourism apps
- Powering smart home devices to react to local weather conditions
- Building weather widgets or dashboards for websites or mobile apps



## How to Get Current Weather

1. You must have a valid API key. Refer to the [Getting Started](#getting-started-obtain-an-api-key) section for more details.
2. Ensure your application can make HTTP GET requests.
3. Send a GET request to the following endpoint:

```
https://api.openweathermap.org/data/2.5/weather
 ```


### Required Parameters

| Name | Parameter Type | Example |
|------|----------------|---------|
| `zip` | query | `65051` |
| `units` | query | `imperial` |
| `appid` | query | `your_api_key` |

### Optional Parameters

- `units`: `metric`, `imperial`, or `standard`
- `mode`: `json`, `xml`, or `html`



### Example Request

```http
GET https://api.openweathermap.org/data/2.5/weather?zip=95050&units=imperial
```
### Example cURL

```
curl --location --globoff 'https://api.openweathermap.org/data/2.5/weather?zip=95050&units=imperial&appid=your_api_key'
```

## Example Response (200 OK)

```
{
  "coord": { "lon": -121.953, "lat": 37.3492 },
  "weather": [
    {
      "id": 804,
      "main": "Clouds",
      "description": "overcast clouds",
      "icon": "04n"
    }
  ],
  "base": "stations",
  "main": {
    "temp": 53.46,
    "feels_like": 52.36,
    "temp_min": 50.41,
    "temp_max": 54.28,
    "pressure": 1018,
    "humidity": 82,
    "sea_level": 1018,
    "grnd_level": 996
  },
  "visibility": 10000,
  "wind": { "speed": 3.44, "deg": 0 },
  "clouds": { "all": 100 },
  "dt": 1745147846,
  "sys": {
    "type": 1,
    "id": 5845,
    "country": "US",
    "sunrise": 1745155545,
    "sunset": 1745203627
  },
  "timezone": -25200,
  "id": 0,
  "name": "Santa Clara",
  "cod": 200
}
```
## Error Responses

- **401 Unauthorized** – Invalid or missing API key  
- **404 Not Found** – Invalid location parameters  
- **429 Too Many Requests** – Rate limit exceeded  




## Response Fields

| Field              | Description |
|-------------------|-------------|
| `coord.lon`        | Longitude of the location |
| `coord.lat`        | Latitude of the location |
| `weather.id`       | Weather condition ID |
| `weather.main`     | Group of weather parameters (Rain, Snow, Clouds, etc.) |
| `weather.description` | Detailed description of the weather condition |
| `weather.icon`     | Weather icon ID |
| `base`             | Internal parameter |
| `main.temp`        | Temperature. Default: Kelvin. Metric: Celsius. Imperial: Fahrenheit |
| `main.feels_like`  | Perceived temperature. Same units as `main.temp` |
| `main.pressure`    | Atmospheric pressure (hPa) |
| `main.humidity`    | Humidity in percentage (%) |
| `main.temp_min`    | Minimum observed temperature. Same units as `main.temp` |
| `main.temp_max`    | Maximum observed temperature. Same units as `main.temp` |
| `main.sea_level`   | Atmospheric pressure at sea level (hPa) |
| `main.grnd_level`  | Atmospheric pressure at ground level (hPa) |
| `visibility`       | Visibility in meters. Max value: 10,000 |
| `wind.speed`       | Wind speed. Default/Metric: m/s, Imperial: mph |
| `wind.deg`         | Wind direction in degrees (meteorological) |
| `wind.gust`        | Wind gust. Same units as `wind.speed` |
| `clouds.all`       | Cloudiness in percentage (%) |
| `rain.1h`          | Precipitation in the last hour (mm/h), if available |
| `snow.1h`          | Snowfall in the last hour (mm/h), if available |
| `dt`               | Time of data calculation (UNIX UTC) |
| `sys.type`         | Internal parameter |
| `sys.id`           | Internal parameter |
| `sys.country`      | Country code (e.g., GB, JP) |
| `sys.sunrise`      | Sunrise time (UNIX UTC) |
| `sys.sunset`       | Sunset time (UNIX UTC) |
| `timezone`         | Time shift from UTC in seconds |
| `id`               | City ID |
| `name`             | City name |
| `cod`              | Internal parameter (status code) |


