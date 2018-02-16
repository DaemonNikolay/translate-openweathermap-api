# 16-ти дневный прогноз погоды

16-ти дневные прогнозы доступны в какой-нибудь локации или городе. Прогноз включает в себя каждодневный прогноз и различные форматы в виде JSON и XML.

***

## Вызов 16-ти дней / информация каждодневного прогноза

> Пожалуйста запомните все примеры вызова API включенные в список на этой странице как точный образец и не имейте много подключений к реальному API сервису!

### По названию города

*Описание:*

Вы можете искать прогноз погоды на 16-ть дней с ежедневными средними параметрами по названию города. Всю информацию по погоде можете получать в JSON и XML формате.

> Там вероятно получение центрального района города/городка со своими параметрами (географические координаты/id/имя) в API ответе. [Пример](http://samples.openweathermap.org/data/2.5/forecast/daily?q=M%C3%BCnchen,DE&appid=b6907d289e10d714a6e88b30761fae22 "Пример")

*Вызов API:*

`api.openweathermap.org/data/2.5/forecast/daily?q={city name},{country code}&cnt={cnt}`

*Параметры:*

**q** название города и код страны разделённые запятой, используя коды стран ISO 3166

**cnt** сумма возвращаемых дней (от 1 до 16)

*Пример вызова API:*

Вызов 7-ми дневного прогноза по названию города в формате XML и метрических единицах измерения `api.openweathermap.org/data/2.5/forecast/daily?q=London&mode=xml&units=metric&cnt=7`

### По id города

*Описание:*

Вы можете получить 16-ти дневный прогноз с ежедневными средними параметрами по id города. API ответ с точным результатом. Вся информация о погоде получается в JSON и XML форматах.

Список id городов (файл city.list.json.gz *прим. переводчика*) можно скачать здесь [http://bulk.openweathermap.org/sample/](http://bulk.openweathermap.org/sample/)

> Мы рекоммендуем вызов API по id города для возврата недвусмысленного результата для Вашего города.

*API вызов:*

`api.openweathermap.org/data/2.5/forecast/daily?id={city ID}&cnt={cnt}`

*Параметры:*

**id** id города

**cnt** сумма возвращаемых дней (от 1 до 16)

*Пример вызова API:*
[`api.openweathermap.org/data/2.5/forecast/daily?id=524901`](http://samples.openweathermap.org/data/2.5/forecast/daily?id=524901&lang=zh_cn&appid=b1b15e88fa797225412429c1c50c122a1)

### По географическим координатам

*Описание:*

Вы можете получить 16-ти дневный прогноз погоды с ежедневными средними параметрами по географическим координатам. Вся информация о погоде получается в JSON и XML форматах.

*API вызов:*

`api.openweathermap.org/data/2.5/forecast/daily?lat={lat}&lon={lon}&cnt={cnt}`

*Параметры:*

**lat**, **lon** координаты локации или Ваших интересов

**cnt** количество возвращаемых дней (от 1 до 16)

*Пример вызова API:*

Вызов 10-ти дневного прогноза по географическим координатам `api.openweathermap.org/data/2.5/forecast/daily?lat=35&lon=139&cnt=10`

### По ZIP коду

*Описание:*

Обратите внимание, если страна не указана, то используется поиск для США по умолчанию.

*API вызов:*

`api.openweathermap.org/data/2.5/forecast/daily?zip={zip code},{country code}`

*Параметры:*

**ZIP** zip код

*Пример вызова API:*

`api.openweathermap.org/data/2.5/forecast/daily?zip=94040,us`

***

## Массовая загрузка

*Описание:*

Мы предоставляем ряд файлов для массовой загрузки с текущей погодой и прогнозами. Больше информации на этой [Масса](http://openweathermap.org/bulk "Масса") странице

> Множественная загрузка не для всех аккаунтов. Чтобы узнать больше информации смотрите здесь [прайс](http://openweathermap.org/price "прайс").

*Пример множественной загрузки:*

[http://bulk.openweathermap.org/sample/](http://bulk.openweathermap.org/sample/)

***

## Погодные параметры в ответе API

> Если Вы не видите некоторые параметры в ответе API, то это означает, что это погодное событие не произошло за это время измерения для города или выбранной локации. Только реальные изеремения или вычисления информации выводятся в API ответе.

### JSON

*Пример API ответа:*

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

*Параметры:*

* `city`
    * `city.id` id города
    * `city.name` Название города
    * `city.coord`
        * `city.coord.lat` Геолокация города, широта
        * `city.coord.lon` Геолокация города, долгота
    * `city.country` Код страны (GB, JP и тд.)
* `cod` Внутренний параметр
* `message` Внутренний параметр
* `cnt` Количество возращённых строк в данном вызове API
* `list`
    * `list.dt` Время прогнозируемой информации
    * `list.temp`
        * `list.temp.day` Дневная температура. Единица измерения: Кельвин, метрическая: Цельсий, империческая: Фаренгейт.
        * `list.temp.min` Минимальная дневная температура. Единица измерения по умолчанию: Кельвин, метрическая: Цельсий, империческая: Фаренгейт.
        * `list.temp.max` Максимальная дневная температура. Единица измерения по умолчанию: Кельвин, метрическая: Цельсий, империческая: Фаренгейт.
        * `list.temp.night` Ночная температура. Единица измерения по умолчанию: Кельвин, метрическая: Цельсий, империческая: Фаренгейт.
        * `list.temp.eve` Вечернаяя температура. Единица измерения по умолчанию: Кельвин, метрическая: Цельсий, империческая: Фаренгейт.
        * `list.temp.morn` Дневная температура. Единица измерения по умолчанию: Кельвин, метрическая: Цельсий, империческая: Фаренгейт.
    * `list.pressure` Атмосферное давление на уровне моря, гПа
    * `list.humidity` Влажность, %
    * `list.weather` (подробные коды погодных условий)
        * `list.weather.id` id состояния погоды
        * `list.weather.main` Группа погодных параметров (Дождь, Снег, Экстремум и тд.)
        * `list.weather.description` Состояние погоды внутри группы
        * `list.weather.icon` id иконки погоды
    * `list.speed` Скорость ветра. Единцина измерения по умолчанию: метр/сек, метрическая: метр/сек, империческая: миль/час.
    * `list.deg` Направление ветра, градус (метеорологический)
    * `list.clouds` Облачность, %

### XML

*Пример ответа API:*

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

*Параметры:*

* `location`
    * `location.name` 
    * `location.type` 
    * `location.country` 
    * `location.timezone` 
    * `location.location`
        * `location.location.altitude` 
        * `location.location.latitude` 
        * `location.location.longitude` 
        * `location.location.geobase` 
        * `location.location.geobaseid` 
* `meta`
    * `meta.lastupdate` 
    * `meta.calctime` 
    * `meta.nextupdate` 
* `sun`
    * `sun.rise` 
    * `sun.set` 
* `forecast`
    * `forecast.time`
        * `forecast.time.day` 
    * `forecast.symbol`
        * `forecast.symbol.number` 
        * `forecast.symbol.name`
        * `forecast.symbol.var` 
    * `forecast.precipitation`
        * `forecast.precipitation.value` 
        * `forecast.precipitation.unit` 
        * `forecast.precipitation.type` 
    * `forecast.windDirection`
        * `forecast.windDirection.deg` 
        * `forecast.windDirection.code` 
        * `forecast.windDirection.name` 
    * `forecast.windSpeed`
        * `forecast.windSpeed.mps`
        * `forecast.windSpeed.name`
    * `forecast.temperature`
        * `forecast.temperature.day` 
        * `forecast.temperature.min` 
        * `forecast.temperature.max` 
        * `forecast.temperature.night` 
        * `forecast.temperature.eve` 
        * `forecast.temperature.morn`
    * `forecast.pressure`
        * `forecast.pressure.unit` 
        * `forecast.pressure.value` 
    * `forecast.humidity`
        * `forecast.humidity.unit` 
        * `forecast.humidity.value` 
    * `forecast.clouds`
        * `forecast.pressure.value`
        * `forecast.pressure.all` 
        * `forecast.pressure.unit` 