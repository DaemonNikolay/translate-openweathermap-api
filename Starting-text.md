# 16 day weather forecast

16 day forecasts is available at any location or city. Forecasts include daily weather and available in JSON or XML format.

## Call 16 day / daily forecast data

> Please remember that all Examples of API calls that listed on this page are just samples and do not have any connection to the real API service!

### By city name

*Description:*

You can search 16 day weather forecast with daily average parameters by city name. All weather data can be obtained in JSON and XML formats.

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