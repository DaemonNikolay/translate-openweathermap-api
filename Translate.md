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
    * `location.name` id города
    * `location.type` Параметр прототипа
    * `location.country` Код страны (GB, JP и тд.)
    * `location.timezone` Параметр прототипа
    * `location.location`
        * `location.location.altitude` Геолокация города, высота выше уровня моря
        * `location.location.latitude` Геолокация города, широта
        * `location.location.longitude` Геолокация города, долгота
        * `location.location.geobase` Параметр прототипа 
        * `location.location.geobaseid` Параметр прототипа
* `meta`
    * `meta.lastupdate` Параметр прототипа
    * `meta.calctime` Скорость вычисления информации
    * `meta.nextupdate` Параметр прототипа
* `sun`
    * `sun.rise` Восход солнца
    * `sun.set` Заход солнца
* `forecast`
    * `forecast.time`
        * `forecast.time.day` Дата прогнозирования информации о погоде
    * `forecast.symbol` 
        * `forecast.symbol.number` id состояния погоды
        * `forecast.symbol.name` Состояние погоды
        * `forecast.symbol.var` id иконки погоды
    * `forecast.precipitation`
        * `forecast.precipitation.value` Падение уровня за 3 часа, мм
        * `forecast.precipitation.unit` Период измерений. Вероятное значение 1 час, 3 часа.
        * `forecast.precipitation.type` Тип осадков. Возможное значение дождь, снег.
    * `forecast.windDirection`
        * `forecast.windDirection.deg` Направление ветра, градус (метеорологический) 
        * `forecast.windDirection.code` Код направления ветра. Возможное значение WSW, N, S и тд.
        * `forecast.windDirection.name` Полное наименование направления ветра. 
    * `forecast.windSpeed`
        * `forecast.windSpeed.mps` Скорость ветра, mps.
        * `forecast.windSpeed.name` Тип ветра.
    * `forecast.temperature`
        * `forecast.temperature.day` Дневная температура. Единица измерения по умолчанию: Кельвин, метрическая: Цельсий, Империческая: Фаренгейт.
        * `forecast.temperature.min` Минимальная дневная температура. Единица измерения по умолчанию: Кельвин, метрическая: Цельсий, Империческая: Фаренгейт.
        * `forecast.temperature.max` Максимальная дневная температура. Единица измерения по умолчанию: Кельвин, метрическая: Цельсий, Империческая: Фаренгейт.
        * `forecast.temperature.night` Ночная температура. Единица измерения по умолчанию: Кельвин, метрическая: Цельсий, Империческая: Фаренгейт.
        * `forecast.temperature.eve` Вечерняя температура. Единица измерения по умолчанию: Кельвин, метрическая: Цельсий, Империческая: Фаренгейт.
        * `forecast.temperature.morn` Утренняя температура. Единица измерения по умолчанию: Кельвин, метрическая: Цельсий, Империческая: Фаренгейт.
    * `forecast.pressure`
        * `forecast.pressure.unit` гПа
        * `forecast.pressure.value` Значение давления
    * `forecast.humidity`
        * `forecast.humidity.unit` %
        * `forecast.humidity.value` Значение влажности
    * `forecast.clouds`
        * `forecast.pressure.value` Наименование облачности
        * `forecast.pressure.all` Облачность
        * `forecast.pressure.unit` %

### Список кодов состояния

Список [погодные коды состояния](http://openweathermap.org/weather-conditions) с иконками (грозовой фронт, мелкий дождь, дождь, снег, облака, включённые атмосферные условия, такие как торнадо, ураган и тд.)

### API Мин/макс текущей температуры погоды и прогнозный API

> Пожалуйста, не путайте параметры мин/макс в API текущей погоде и прогнозном API. В API текущей погоды **temp_min** и **temp_max** опциональные параметры означают мин/макс температуру в городе на текущий момент с учётом отклонений текущей температуры, только для Вашей справки. Для больших городов и, географически расширенных, мегаполисов это может быть применимо. Наибольшее значение параметров **temp_min** и **temp_max** содержится в 'temp'. Пожалуйста, используйте параметры **temp_min** и **temp_max** в API текущей погоды опционально.

*Пример ответа API текущей погоды:*
```JSON
"main":{
"temp":306.15, //текущая температура 
"pressure":1013,
"humidity":44,
"temp_min":306, //минимальная температура в городе
"temp_max":306 //максимальная температура в городе
},
```
*Для сравнения приведён пример каждодневного ответа API прогноза погоды:*
```JSON
"dt":1406080800,
"temp":{
        "day":297.77,  //каждодневная средняя температура 
        "min":293.52, //каждодневная минимальная температура
        "max":297.77, //каждодневная максимальная температура
        "night":293.52, //ночная температура
        "eve":297.77, //вечерняя температура
        "morn":297.77}, //утренняя температура
```

***

## Другие особенности

**Формат**

*Описание:*

JSON формат используется по умолчанию. Для получения информации в формате XML просто укажите `mode = xml`.

*Параметры:*

`mode` - возможные значения: JSON, xml. Если параметр `mode` отсутствует, то JSON формат по умолчанию.

*Пример вызова API:*

JSON [api.openweathermap.org/data/2.5/weather?q=London](http://samples.openweathermap.org/data/2.5/weather?q=London&appid=b6907d289e10d714a6e88b30761fae22)

XML [api.openweathermap.org/data/2.5/weather?q=London&mode=xml](http://samples.openweathermap.org/data/2.5/forecast/daily?q=London&mode=xml&units=metric&cnt=7&appid=b1b15e88fa797225412429c1c50c122a1)

### Поисковая точность

*Описание:*

