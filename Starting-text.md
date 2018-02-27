# 16 day weather forecast

16 day forecasts is available at any location or city. Forecasts include daily weather and available in JSON or XML format.

***

## Call 16 day / daily forecast data

> Please remember that all Examples of API calls that listed on this page are just samples and do not have any connection to the real API service!

### By city name

*Description:*

You can seach 16 day weather forecast with daily average parameters by city name. All weather data can be obtained in JSON and XML formats.

> There is a possibility to receive a central district of the city/town with its own parameters (geographic coordinates/id/name) in API response. [Example](http://samples.openweathermap.org/data/2.5/forecast/daily?q=M%C3%BCnchen,DE&appid=b6907d289e10d714a6e88b30761fae22 "Example")

*API call:*

`api.openweathermap.org/data/2.5/forecast/daily?q={city name},{country code}&cnt={cnt}`

*Parameters:*

**q** city name and country code divided by comma, use ISO 3166 country codes

**cnt** number of days returned (from 1 to 16)

*Examples of API calls:*

Call 7 days forecast by city name in XML format and metric units `api.openweathermap.org/data/2.5/forecast/daily?q=London&mode=xml&units=metric&cnt=7`

### By city ID

*Description:*

You can seach 16 day weather forecast with daily average parameters by city ID. API responds with exact result. All weather data can be obtained in JSON and XML format.

List of city ID city.list.json.gz can be downloaded here [http://bulk.openweathermap.org/sample/](http://bulk.openweathermap.org/sample/)

> We recommend to call API by city ID to get unambiguous result for your city.

*API call:*

`api.openweathermap.org/data/2.5/forecast/daily?id={city ID}&cnt={cnt}`

*Parameters:*

**id** city ID

**cnt** number of days returned (from 1 to 16)

*Examples of API calls:*
[`api.openweathermap.org/data/2.5/forecast/daily?id=524901`](http://samples.openweathermap.org/data/2.5/forecast/daily?id=524901&lang=zh_cn&appid=b1b15e88fa797225412429c1c50c122a1)

### By geographic coordinats

*Description:*

You can seach 16 day weather forecast with daily average parameters by geographic coordinats. All weather data can be obtained in JSON and XML formats.

*API call:*

`api.openweathermap.org/data/2.5/forecast/daily?lat={lat}&lon={lon}&cnt={cnt}`

*Parameters:*

**lat**, **lon** coordinates of the location of your interest

**cnt** number of days returned (from 1 to 16)

*Examples of API calls:*

Call 10 days forecast by geographic coordinates `api.openweathermap.org/data/2.5/forecast/daily?lat=35&lon=139&cnt=10`

### By ZIP code

*Description:*

Please note if country is not specified then the search works for USA as a default.

*API call:*

`api.openweathermap.org/data/2.5/forecast/daily?zip={zip code},{country code}`

*Parameters:*

**zip** zip code

*Examples of API calls:*

`api.openweathermap.org/data/2.5/forecast/daily?zip=94040,us`

***

## Bulk downloading

*Description:*

We provide number of bulk files with current weather and forecasts. More information is on the [Bulk](http://openweathermap.org/bulk "Bulk") page

> Bulk downloading is available not for all accounts. To get more information please refer to the [price](http://openweathermap.org/price "price").

*Examples of bulk files:*

[http://bulk.openweathermap.org/sample/](http://bulk.openweathermap.org/sample/)

***

## Weather parameters in API respond

> If you do not see some of the parameters in your API respond it means that these weather phenomena are just not happened for the time of measurement for the city or location chosen. Only really measured or calculated data is displayed in API respond.

### JSON

*Example of API repond:*

```JSON
{
    "cod": "200",
    "message": 0.0032,
    "city": {
        "id": 1851632,
        "name": "Shuzenji",
        "coord": {
            "lon": 138.933334,
            "lat": 34.966671
        },
        "country": "JP"
    },
    "cnt": 10,
    "list": [
        {
            "dt": 1406080800,
            "temp": {
                    "day": 297.77,
                    "min": 293.52,
                    "max": 297.77,
                    "night": 293.52,
                    "eve": 297.77,
                    "morn": 297.77
            },
            "pressure": 925.04,
            "humidity": 76,
            "weather": [
                            {
                                    "id": 803,
                    "main": "Clouds",
                    "description": "broken clouds",
                    "icon": "04d"            
                }          
            ],
                    
        }
    ]
}
```

*Parameters:*

* `city`
    * `city.id` City ID
    * `city.name` City name
    * `city.coord`
        * `city.coord.lat` City geo location, latitude
        * `city.coord.lon` City geo location, longitude
    * `city.country` Country code (GB, JP etc.)
* `cod` Internal parameter
* `message` Internal parameter
* `cnt` Number of lines returned by this API call
* `list`
    * `list.dt` Time of data forecasted
    * `list.temp`
        * `list.temp.day` Day temperature. Unit Default: Kelvin, Metric: Celsius, Imperial: Fahrenheit.
        * `list.temp.min` Min daily temperature. Unit Default: Kelvin, Metric: Celsius, Imperial: Fahrenheit.
        * `list.temp.max` Max daily temperature. Unit Default: Kelvin, Metric: Celsius, Imperial: Fahrenheit.
        * `list.temp.night` Night temperature. Unit Default: Kelvin, Metric: Celsius, Imperial: Fahrenheit.
        * `list.temp.eve` Evening temperature. Unit Default: Kelvin, Metric: Celsius, Imperial: Fahrenheit.
        * `list.temp.morn` Morning temperature. Unit Default: Kelvin, Metric: Celsius, Imperial: Fahrenheit.
    * `list.pressure` Atmospheric pressure on the sea level, hPa
    * `list.humidity` Humidity, %
    * `list.weather` (more info Weather condition codes)
        * `list.weather.id` Weather condition id
        * `list.weather.main` Group of weather parameters (Rain, Snow, Extreme etc.)
        * `list.weather.description` Weather condition within the group
        * `list.weather.icon` Weather icon id
    * `list.speed` Wind speed. Unit Default: meter/sec, Metric: meter/sec, Imperial: miles/hour.
    * `list.deg` Wind direction, degrees (meteorological)
    * `list.clouds` Cloudiness, %

### XML

*Example of API respond:*

```XML
<weatherdata>
<location>
    <name>London</name>
    <type/>
    <country>GB</country>
    <timezone/>
    <location altitude="0" latitude="51.50853" longitude="-0.12574" geobase="geonames" geobaseid="0"/>
</location>
<credit/>
<meta>
    <lastupdate/>
    <calctime>0.0091</calctime>
    <nextupdate/>
</meta>
<sun rise="2015-06-04T03:46:26" set="2015-06-04T20:11:17"/>
<forecast>
    <time day="2015-06-04">
    <symbol number="802" name="scattered clouds" var="03d"/>
    <precipitation/>
    <windDirection deg="148" code="SSE" name="South-southeast"/>
    <windSpeed mps="5.12" name="Gentle Breeze"/>
    <temperature day="23.65" min="17.27" max="23.74" night="17.27" eve="22.94" morn="17.54"/>
    <pressure unit="hPa" value="1032.24"/>
    <humidity value="70" unit="%"/>
    <clouds value="scattered clouds" all="36" unit="%"/>
    </time>
</forecast>
</weatherdata>
```

*Parameters:*

* `location`
    * `location.name` City ID
    * `location.type` Prototype parameter
    * `location.country` Country code (GB, JP etc.)
    * `location.timezone` Prototype parameter
    * `location.location`
        * `location.location.altitude` City geo location, altitude above the sea level
        * `location.location.latitude` City geo location, latitude
        * `location.location.longitude` City geo location, longitude
        * `location.location.geobase` Prototype parameter
        * `location.location.geobaseid` Prototype parameter
* `meta`
    * `meta.lastupdate` Prototype parameter
    * `meta.calctime` Speed of data calculation
    * `meta.nextupdate` Prototype parameter
* `sun`
    * `sun.rise` Sunrise time
    * `sun.set` Sunset time
* `forecast`
    * `forecast.time`
        * `forecast.time.day` Date of weather data forecasted
    * `forecast.symbol`
        * `forecast.symbol.number` Weather condition id
        * `forecast.symbol.name` Weather condition
        * `forecast.symbol.var` Weather icon id
    * `forecast.precipitation`
        * `forecast.precipitation.value` Precipitation volume for the last 3 hours, mm
        * `forecast.precipitation.unit` Period of measurements. Possilbe value is 1 hour, 3 hours.
        * `forecast.precipitation.type` Type of precipitation. Possible value is rain, snow.
    * `forecast.windDirection`
        * `forecast.windDirection.deg` Wind direction, degrees (meteorological)
        * `forecast.windDirection.code` Code of the wind direction. Possilbe value is WSW, N, S etc.
        * `forecast.windDirection.name` Full name of the wind direction.
    * `forecast.windSpeed`
        * `forecast.windSpeed.mps` Wind speed, mps
        * `forecast.windSpeed.name` Type of the wind
    * `forecast.temperature`
        * `forecast.temperature.day` Day temperature. Unit Default: Kelvin, Metric: Celsius, Imperial: Fahrenheit.
        * `forecast.temperature.min` Min daily temperature. Unit Default: Kelvin, Metric: Celsius, Imperial: Fahrenheit.
        * `forecast.temperature.max` Max daily temperature. Unit Default: Kelvin, Metric: Celsius, Imperial: Fahrenheit.
        * `forecast.temperature.night` Night temperature. Unit Default: Kelvin, Metric: Celsius, Imperial: Fahrenheit.
        * `forecast.temperature.eve` Evening temperature. Unit Default: Kelvin, Metric: Celsius, Imperial: Fahrenheit.
        * `forecast.temperature.morn` Morning temperature. Unit Default: Kelvin, Metric: Celsius, Imperial: Fahrenheit.
    * `forecast.pressure`
        * `forecast.pressure.unit` hPa
        * `forecast.pressure.value` Pressure value
    * `forecast.humidity`
        * `forecast.humidity.unit` %
        * `forecast.humidity.value` Humidity value
    * `forecast.clouds`
        * `forecast.pressure.value` Name of the cloudiness
        * `forecast.pressure.all` Cloudiness
        * `forecast.pressure.unit` %

### List of condition codes

List of [weather condition codes](http://openweathermap.org/weather-conditions) with icons (range of thunderstorm, drizzle, rain, snow, clouds, atmosphere including extreme conditions like tornado, hurricane etc.)

### Min/max temperature in current weather API and forecast API

> Please, do not confuse min/max parameters in current weather API and forecast API. In current weather API **temp_min** and **temp_max** are optional parameters mean min / max temperature in the city at the current moment to see deviation from current temp just for your reference. For large cities and megalopolises geographically expanded it might be applicable. In most cases both **temp_min** and **temp_max** parameters have the same volume as 'temp'. Please, use **temp_min** and **temp_max** parameters in current weather API optionally.

*Example of current weather API respond:*
```JSON
"main":{
"temp":306.15, //current temperature 
"pressure":1013,
"humidity":44,
"temp_min":306, //min current temperature in the city
"temp_max":306 //max current temperature in the city
},
```
*For comparison look at example of daily forecast weather API respond:*
```JSON
"dt":1406080800,
"temp":{
        "day":297.77,  //daily averaged temperature
        "min":293.52, //daily min temperature
        "max":297.77, //daily max temperature
        "night":293.52, //night temperature
        "eve":297.77, //evening temperature
        "morn":297.77}, //morning temperature
```

***

## Other features

**Format**

*Description:*

JSON format is used by default. To get data in XML format just set up `mode = xml`.

*Parameters:*

`mode` - possible values are JSON xml. If `mode` parameter is empty the format is JSON by default.

*Examples of API calls:*

JSON [api.openweathermap.org/data/2.5/weather?q=London](http://samples.openweathermap.org/data/2.5/weather?q=London&appid=b6907d289e10d714a6e88b30761fae22)

XML [api.openweathermap.org/data/2.5/weather?q=London&mode=xml](http://samples.openweathermap.org/data/2.5/forecast/daily?q=London&mode=xml&units=metric&cnt=7&appid=b1b15e88fa797225412429c1c50c122a1)

### Search accuracy

*Description:*

You can use our geocoding system to find cities by name, country, zip-code or geographic coordinates. You can call also by part of the city name. To make the result more accurate just put the city name and country divided by comma.

To set the accuracy level either use the 'accurate' or 'like' type parameter. 'accurate' returns exact match values. 'like' returns results by searching for that substring. 

> Call API by city ID instead of city name, city coordinates or zip code. In this case you get precise respond exactly for your city.

*Parameters:*

**like** close result
**accurate** accurate result

*Examples of API calls:*

Like [api.openweathermap.org/data/2.5/find?q=London&type=like&mode=xml](http://samples.openweathermap.org/data/2.5/forecast/daily?q=London&mode=xml&units=metric&cnt=7&appid=b1b15e88fa797225412429c1c50c122a1)

Accurate [api.openweathermap.org/data/2.5/find?q=London&type=accurate&mode=xml](http://samples.openweathermap.org/data/2.5/forecast/daily?q=London&mode=xml&units=metric&cnt=7&appid=b1b15e88fa797225412429c1c50c122a1)

### Limitation of result

*Description:*

To limit number of listed cities please setup 'cnt' parameter that specifies the number of lines returned.

*Parameters:*

cnt number of lines in respond

*Examples of API calls:*

cnt=3 [api.openweathermap.org/data/2.5/find?lat=57&lon=-2.15&cnt=3](http://samples.openweathermap.org/data/2.5/forecast/daily?lat=35&lon=139&cnt=10&appid=b1b15e88fa797225412429c1c50c122a1)

### Units format

*Description:*

Standard, metric, and imperial units are available.

*Parameters:*

*units* metric, imperial. When you do not use units parameter, format is Standard by default.

> Temperature is available in Fahrenheit, Celsius and Kelvin units.
> * For temperature in Fahrenheit use units=imperial
> * For temperature in Celsius use units=metric
> * Temperature in Kelvin is used by default, no need to use units parameter in API call
> List of all API parameters with units [openweathermap.org/weather-data](http://openweathermap.org/weather-data)

*Examples of API calls:*

standard [api.openweathermap.org/data/2.5/find?q=London](http://samples.openweathermap.org/data/2.5/find?q=London&appid=b6907d289e10d714a6e88b30761fae22)

metric [api.openweathermap.org/data/2.5/find?q=London&units=metric](http://samples.openweathermap.org/data/2.5/find?q=London&units=metric&appid=b6907d289e10d714a6e88b30761fae22)

imperial [api.openweathermap.org/data/2.5/find?q=London&units=imperial](http://samples.openweathermap.org/data/2.5/find?q=London&units=imperial&appid=b6907d289e10d714a6e88b30761fae22)

### Multilingual support

*Description:*

You can use lang parameter to get the output in your language. We support the following languages that you can use with the corresponded lang values: 
Arabic - ar, Bulgarian - bg, Catalan - ca, Czech - cz, German - de, Greek - el, English - en, Persian (Farsi) - fa, Finnish - fi, French - fr, Galician - gl, Croatian - hr, Hungarian - hu, Italian - it, Japanese - ja, Korean - kr, Latvian - la, Lithuanian - lt, Macedonian - mk, Dutch - nl, Polish - pl, Portuguese - pt, Romanian - ro, Russian - ru, Swedish - se, Slovak - sk, Slovenian - sl, Spanish - es, Turkish - tr, Ukrainian - ua, Vietnamese - vi, Chinese Simplified - zh_cn, Chinese Traditional - zh_tw.

NOTE: Translation is only applied for the "description" field.

*API call:*

`http://api.openweathermap.org/data/2.5/forecast/daily?id=524901&lang={lang}`

*Parameters:*

**lang** language code

*Examples of API calls:*

[`http://api.openweathermap.org/data/2.5/forecast/daily?id=524901&lang=zh_cn`](http://samples.openweathermap.org/data/2.5/forecast/daily?id=524901&lang=zh_cn&appid=b1b15e88fa797225412429c1c50c122a1)

### Call back function for JavaScript code

*Description:*

To use JavaScript code you can transfer callback functionName to JSONP callback. 

*Examples of API calls:*

[`api.openweathermap.org/data/2.5/weather?q=London,uk&callback=test`](http://samples.openweathermap.org/data/2.5/weather?q=London,uk&callback=test&appid=b6907d289e10d714a6e88b30761fae22)