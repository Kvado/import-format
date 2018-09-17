# Импорт данных из сторонних систем в формате JSON

Json файл должен содержать информацию об одном доме и иметь следующую струкуру.

```
{
    "meters": [
        {
            "type": "...",
            "title": "...",
            "serial": "...",
            "brand": "...",
            "model": "...",
            "install_date": "2017-04-23",
            "stamp_date": "2017-04-23",
            "check_date": "2025-04-23",
            "replace_date": "2017-08-12",
            "ratio": 1,
            "loss_ratio": 0.00,
            "beginning_values": {
                "B": 2.000,
                "T1": 3.000,
                "T2": 3.000,
                "T3": 3.000,
            },
            "unit": "...",
            "values": [
                {
                    "date": "2017-06-25",
                    "period": "2017-06-01",
                    "values": {
                        "B": 3.000,
                        "T1": 3.000,
                        ...
                    }
                },
                ...
            ]
        },
        ...
    ],
    "premises": [
        {
            "flat_number": "...",
            "premises_type": "...",
            "overall_area": 45.34,
            "living_area": 28.45,
            "number_of_rooms": 2,
            "entrance": "...",
            "floor": 2,
            "radio": true,
            "number_of_tv": 1,
            "meters": [
                {
                    "type": "...",
                    "title": "...",
                    "serial": "...",
                    "brand": "...",
                    "model": "...",
                    "install_date": "2017-04-23",
                    "stamp_date": "2017-04-23",
                    "check_date": "2025-04-23",
                    "replace_date": "2017-08-12",
                    "beginning_values": {
                        "B": 2.000,
                        "T1": 3.000,
                        "T2": 3.000,
                        "T3": 3.000,
                    },
                    "unit": "...",
                    "values": [
                        {
                            "date": "2017-06-25",
                            "period": "2017-06-01",
                            "values": {
                                "B": 3.000,
                                "T1": 3.000,
                                ...
                            }
                        },
                        ...
                    ]
                },
                ...
            ],
            "accounts": [
                {
                    "account": "...",
                    "date_from": "2017-01-01",
                    "date_to": "2017-12-31",
                    "registered": 2,
                    "residents_count": 2,
                    "saldo" : "...",
                    "saldo_period" : "...",
                    "calculated_area": 23.67
                    "residents": [
                        {
                            "type": "...",
                            "share": "1/2",
                            "mobile_phone_1": "...",
                            "mobile_phone_2": "...",
                            "home_phone": "...",
                            "work_phone": "...",
                            "email": "...",
                            "residence" : {
                                "type" : "...",
                                "date_from" : "..."
                                "date_to" : "...",
                                "from" : {
                                    "country":"...",
                                    "region":"...",
                                    "district":"...",
                                    "city":"...",
                                    "locality":"...",
                                    "street":"...",
                                    "house":"...",
                                    "flat":"..."
                                },
                                "to" : {
                                    "country":"...",
                                    "region":"...",
                                    "district":"...",
                                    "city":"...",
                                    "locality":"...",
                                    "street":"...",
                                    "house":"...",
                                    "flat":"..."
                                }
                            }
                            "individual": {
                                "firstname": "...",
                                "lastname": "...",
                                "patronymic": "...",
                                "passport_serial": "...",
                                "passport_number": "...",
                                "passport_issued": "...",
                                "passport_code": "...",
                                "passport_issue_date": "...",
                                "ssn": "...",
                                "birthdate": "...",
                            },
                            "entity": {
                                "title": "...",
                                "inn": "...",
                                "kpp": "...",
                                "ogrn": "...",
                                "legal_address": "...",
                                "head_fullname": "...",
                                "head_post": "...",
                            }
                        },
                        ...
                    ],
                    "rooms": [
                        {
                            "number": "..."
                            "type": "..."
                            "title": "..."
                            "area": 12.32,
                            "balcony_area": 4.56,
                            "loggia_area": 4.56,
                            "rooms_height": 2.54,
                            "rooms_layout": "...",
                            "entrance": "...",
                            "floor_covering": "...",
                            "comment": "...",
                            "radio": true,
                            "number_of_tv": 1
                        },
                        ...
                    ],
                    "accruals": {
                        "2017-01-01": {
                            "calculation_date": "2017-01-29 12:32:34"
                            "result": [
                                {
                                    "id_1c": "...",
                                    "title": "...",
                                    "rate": 12.56,
                                    "volume": 12.12345,
                                    "accrued": 238.23,
                                    "privileges": 0.00,
                                    "recalc": -12.34,
                                    "total": 225.78
                                },
                                ...
                            ]
                        },
                        ...
                    },
                    "payments": [
                        {
                            "date": "2017-02-03",
                            "sum": 2500.00,
                            "period": "2017-01-01",
                            "penalties_included": 23.64,
                            "comment": "..."
                        },
                        ...
                    ]
                },
                ...
            ]
        },
        ...
    ],
}
```

## Описание полей файла

|Поле|Название поля|Тип|Обязательное|Описание|
|---|---|---|---|---|
|meters|Общедомовые счетчики|array|Да|Массив с [объектами, хранящими информацию об общедомовых приборах учета](#array-meters-object)|
|premises|Помещения|array|Да|Массив с [объектами, хранящими информацию о помещениях](#array-premises-object)|

## <a id="array-meters-object"></a>Описание объекта в массиве `meters`

|Поле|Название поля|Тип|Обязательное|Описание|
|---|---|---|---|---|
|type|Тип счетчика|enum|Да|Варианты значений:<ul><li>ХВС</li><li>ГВС</li><li>Эл. однотарифный</li><li>Эл. двухтарифный</li><li>Эл. трехтарифный</li><li>Газ</li><li>Отопление</li></ul>|
|title|Название (описание) счетчика|string|Нет|Текстовые данные|
|serial|Заводской номер|string|Нет|Текстовые данные|
|brand|Марка счетчика|string|Нет|Текстовые данные|
|model|Модель счетчика|string|Нет|Текстовые данные|
|install_date|Дата установки счетчика|[Дата](#type-date)|Нет|См. тип [Дата](#type-date)|
|stamp_date|Дата опломбировки счетчика|[Дата](#type-date)|Да|См. тип [Дата](#type-date)|
|check_date|Дата следующей поверки|[Дата](#type-date)|Нет|См. тип [Дата](#type-date)|
|replace_date|Дата замены (вывода из эксплуатации)|[Дата](#type-date)|Нет|См. тип [Дата](#type-date)|
|ratio|Коэффициент трансформации (для счетчиков электроэнергии)|int|Нет|Поле необходимо только для общедомовых приборов учета|
|loss_ratio|Коэффициент потери (для счетчиков электроэнергии)|int|Нет|Поле необходимо только для общедомовых приборов учета|
|beginning_values|Начальные показания на момент опломбирования|[Показания счетчиков](#type-meter-value)|Нет|См. тип [Показания счетчика](#type-meter-value)|
|unit|Единица измерения (для счетчика отопления)|enum|Да (для счетчиков отопления)|Возможные значения:<br />- Гкал<br />- кВт/ч<br />- МВт/ч|
|values|Показания по счетчику|array|Нет|[Массив объектов с показаниями](#meters-values-object)|

### <a id="array-premises-object"></a>Описание объекта в массиве `premises` (Помещения)

|Поле|Название поля|Тип|Обязательное|Описание|
|---|---|---|---|---|
|flat_number|Номер квартиры (помещения)|string|Да||
|premises_type|Вид помещения|enum|Да|Возможные варианты<ul><li>квартира</li><li>совместная квартира</li><li>коммунальная квартира</li><li>нежилое</li><li>кладовка</li><li>машиноместо</li></ul>|
|overall_area|Общая площадь|float|Да||
|living_area|Жилая площадь|float|Да||
|number_of_rooms|Количество комнат|int|Нет||
|entrance|Номер подъезда|string|Нет||
|floor|Номер этажа|int|Нет||
|radio|Наличие радио|bool|Да|`true` или `false`|
|number_of_tv|Количество ТВ-антенн|int|Да||
|meters|Приборы учета|array|Нет|Массив с [объектами, хранящими информацию об индивидуальных приборах учета](#array-meters-object)|
|accounts|Лицевые счета|array|Да|Массив с [объектами, хранящими данные о ЛС](#array-accounts-object) |

#### <a id="array-accounts-object"></a>Описание объекта массива `accounts`

|Поле|Название поля|Тип|Обязательное|Описание|
|---|---|---|---|---|
|account|Номер лицевого счета|string|Да||
|date_from|Дата открытия ЛС|[Дата](#type-date)|Да|См. тип [Дата](#type-date)|
|date_to|Дата закрытия ЛС|[Дата](#type-date)|Нет|См. тип [Дата](#type-date)|
|registered|Количество зарегистрированных|int|Да||
|residents_count|Количество проживающих|int|Да||
|saldo|Начальное сальдо|decimal(10,2)|||
|saldo_period|Начальное сальдо|[Дата](#type-date)|Да, если есть сальдо||
|calculated_area|Расчетная площадь|float|Да (только для коммунальных и совместных квартир)||
|residents|Жители(Собственники)|array|Да|Массив с [объектами, хранящими информацию о жителях и собственниках](#array-owners-object)|
|rooms|Комнаты|array|Да (только для коммунальных и совместных квартир)|Массив с [объектами, хранящими информацию о комнатах ЛС](#array-rooms-object)|
|accruals|Начисления|object|Нет|Объект хранящий информацию о начислениях. Ключами являются периоды начислений (тип [Период](#type-period)), значениями объекты с [информацией о начислениях в периоде](#accruals-object)|
|payments|Платежи|array|Нет|Массив с [объектами, хранящими информацию о платежах](#array-payments-object)|

##### <a id="array-owners-object"></a>Описание объекта массива `residents`

|Поле|Название поля|Тип|Обязательное|Описание|
|---|---|---|---|---|
|type|Тип жителя(собственника)|enum|Да|Возможные значения:<ul><li>физ. лицо</li><li>юр. лицо</li></ul>|
|is_owner|Собственник|enum|Да|Возможные значения:<ul><li>Да</li><li>Нет</li></ul> для юр. лица всегда "Да"|
|main_payer|Основной плательщик|enum|Да|Возможные значения:<ul><li>Да</li><li>Нет</li></ul>|
|share|Доля собственности|string|Да, если собственник|В формате «142/584», «1/2», «1/1»|
|mobile_phone_1|Мобильный телефон|string|Нет||
|mobile_phone_2|Мобильный телефон|string|Нет||
|home_phone|Домашний телефон|string|Нет||
|work_phone|Рабочий телефон|string|Нет||
|email|Email|string|Нет||
|relationship|enum|string|Нет|Возможные значения:<ul><li>"собственник"</li><li>"наниматель"</li><li>"квартирант"</li><li>"муж"</li><li>"жена"</li><li>"сын"</li><li>"дочь"</li><li>"брат"</li><li>"сестра"</li><li>"дедушка"</li><li>"бабушка"</li><li>"зять"</li><li>"тесть"</li><li>"теща"</li><li>"свекор"</li><li>"свекровь"</li><li>"шурин"</li><li>"свояченица"</li><li>"невестка"</li><li>"деверь"</li><li>"золовка"</li><li>"мать"</li><li>"отец"</li><li>"внук"</li><li>"внучка"</li><li>"опекаемый(ая)"</li><li>"падчерица"</li><li>"пасынок"</li><li>"племянник"</li><li>"племянница"</li>"нет родственных отношений"</ul>|
|residence|Регистрация|object|Да (для `type = "физ. лицо"`)|Объект с [данными о регистрации, если физ. лицо](#residence)|
|individual|Физ. лицо|object|Да (для `type = "физ. лицо"`)|Объект с [данными о владельце, если физ. лицо](#individual-object)|
|entity|Юр. лицо|object|Да (для `type = "юр. лицо"`)|Объект с [данными о владельце, если юр. лицо](#entity-object)|

###### <a id="residence"></a>Описание объекта `residence`
|Поле|Название поля|Тип|Обязательное|Описание|
|---|---|---|---|---|
|type|Тип регистрации|enum('const','tmp')|Да|Возможные значения:<ul><li><b>const</b> - по месту жительства (постоянная)</li><li><b>tmp</b> - по месту пребывания (временная)</li></ul><br>||
|date_from|Дата начала регистрации|[Дата](#type-date)|Да|См. тип [Дата](#type-date)|
|date_to|Дата окончания регистрации|[Дата](#type-date)|Нет|См. тип [Дата](#type-date)|
|from|Регистрация|object|Нет|Объект с [листком прибытия](#from)|
|to|Регистрация|object|Нет|Объект с [листком убытия](#to)|

###### <a id="from"></a>Описание объекта `from`
|Поле|Название поля|Тип|Обязательное|Описание|
|---|---|---|---|---|
|country|Страна|string|Нет||
|region|Страна|string|Нет||
|district|Страна|string|Нет||
|city|Страна|string|Нет||
|locality|Страна|string|Нет||
|street|Страна|string|Нет||
|house|Страна|string|Нет||
|flat|Страна|string|Нет||

###### <a id="to"></a>Описание объекта `to`
|Поле|Название поля|Тип|Обязательное|Описание|
|---|---|---|---|---|
|country|Страна|string|Нет||
|region|Страна|string|Нет||
|district|Страна|string|Нет||
|city|Страна|string|Нет||
|locality|Страна|string|Нет||
|street|Страна|string|Нет||
|house|Страна|string|Нет||
|flat|Страна|string|Нет||

###### <a id="individual-object"></a>Описание объекта `individual`

|Поле|Название поля|Тип|Обязательное|Описание|
|---|---|---|---|---|
|firstname|Имя|string|Нет||
|lastname|Фамилия|string|Да||
|patronymic|Отчество|string|Нет||
|passport_serial|Серия паспорта|string|Нет||
|passport_number|Номер паспорта|string|Нет||
|passport_issued|Кем выдан|string|Нет||
|passport_code|Код подразделения|string|Нет||
|passport_issue_date|Дата выдачи|[Дата](#type-date)|Нет|См. тип [Дата](#type-date)|
|ssn|СНИЛС|string|Нет||
|birthdate|Дата рождения|[Дата](#type-date)|Нет|См. тип [Дата](#type-date)|

###### <a id="entity-object"></a>Описание объекта массива `entity`

|Поле|Название поля|Тип|Обязательное|Описание|
|---|---|---|---|---|
|title|Наименование физ. лица|string|||
|inn|ИНН|string|||
|kpp|КПП|string|||
|ogrn|ОГРН|string|||
|legal_address|Юридический адрес|string|||
|head_fullname|ФИО руководителя|string|||
|head_post|Должность руководителя|string|||

##### <a id="array-rooms-object"></a>Описание объекта массива `rooms`

|Поле|Название поля|Тип|Обязательное|Описание|
|---|---|---|---|---|
|number|Номер комнаты|string|Да||
|type|Тип комнаты|enum|Нет|Возможные значения<ul><li>Жилая комната</li><li>Кухня</li><li>Кухня-столовая</li><li>Туалет</li><li>Ванная</li><li>Прихожая</li><li>Коридор</li><li>Кладовка</li><li>Жилая комната-кухня</li><li>Совмещенный санузел</li></ul>|
|title|Название комнаты|string|Нет||
|area|Площадь|float|Да||
|balcony_area|Площадь балкона|float|Нет||
|loggia_area|Площадь лоджии|float|Нет||
|rooms_height|Высота потолка|float|Нет||
|rooms_layout|Планировка комнаты|enum|Нет|Возможные значения<ul><li>Изолированная</li><li>Смежная</li><li>Смежно-изолированная</li></ul>|
|entrance|Вход|enum|Нет|Возможные значения<ul><li>Из коридора</li><li>Из прихожей</li><li>Из комнаты</li></ul>|
|floor_covering|Покрытие пола|enum|Нет|Возможные значения<ul><li>Керамическая плитка</li><li>Паркет</li><li>Паркетная доска</li><li>Линолеум</li><li>Ламинат</li></ul>|
|comment|Примечание|string|Нет||
|radio|Наличие радио|bool|Нет|`true` или `false`|
|number_of_tv|Количество ТВ антенн|int|Нет||

##### <a id="accruals-object"></a>Описание значений объекта `accruals`

|Поле|Название поля|Тип|Обязательное|Описание|
|---|---|---|---|---|
|calculation_date|Время начисления|[ДатаВремя](#type-date-time)|Да|Когда было произведено начисление|
|result|Результаты начислений|array|Да|Массив с [объектами, хранящими начисления по услугам](#array-result-object)|

###### <a id="array-result-object"></a>Описание объекта массива `result`

|Поле|Название поля|Тип|Обязательное|Описание|
|---|---|---|---|---|
|id_1c|ID услуги в программе 1С|string|||
|title|Название услуги|string|||
|rate|Тариф|decimal(10,2)|||
|volume|Объем (расход)|decimal(15,5)|||
|accrued|Сумма начислено|decimal(10,2)|||
|privileges|Сумма льготы|decimal(10,2)|||
|recalc|Сумма перерасчета|decimal(10,2)|||
|total|Итого начислено по услуге|decimal(10,2)|||

##### <a id="array-payments-object"></a>Описание объекта массива `payments`

|Поле|Название поля|Тип|Обязательное|Описание|
|---|---|---|---|---|
|date|Дата платежа|[Дата](#type-date)|Да||
|sum|Сумма платежа|decimal(10,2)|Да||
|period|Период платежа|[Период](#type-period)|Да|Платеж, за который совершен платеж|
|penalties_included|Включая пени|decimal(10,2)|Нет|Какая сумма из платежа должна закрыть пени|
|comment|Примечание|string|Нет||

## <a id="meters-values-object"></a>Описание объекта показаний счетчика

|Поле|Название поля|Тип|Обязательное|Описание|
|---|---|---|---|---|
|date|Дата внесения показаний|[Дата](#type-date)|Да|См. тип [Дата](#type-date)|
|period|Период показаний|[Период](#type-period)|Да|См. тип [Период](#type-period)|
|values|Показания|[Показания счетчика](#type-meter-value)|Да|См. тип [Показания счетчика](#type-meter-value)|

## <a id="custom-types"></a>Пользовательские типы

|Тип|Описание|
|---|---|
|<a id="type-date"></a>Дата|Дата я вляется строкой `string` в формате `ГГГГ-ММ-ДД`.<br />Например: "2017-04-12"|
|<a id="type-date-time"></a>ДатаВремя|ДатаВремя я вляется строкой `string` в формате `ГГГГ-ММ-ДД ЧАС:МИН:СЕК`.<br />Например: "2017-04-23 08:04:09"|
|<a id="type-period"></a>Период|Период я вляется строкой `string` в формате `ГГГГ-ММ-01`, `-01` в конце.<br />Например: "2017-04-01"|
|<a id="type-meter-value"></a>Показания счетчика|Показания счетчика описываются объектом где:<ul><li>Ключ - ставка, по которой подано показание;</li><li>Значение - показание, `decimal(10,3)` "максимум 10 знаков, из низ 3 после запятой".</li></ul>Возможные значения ключей:<ul><li>"B" - базовая ставка (для всех однотарифных счетчиков)</li><li>"T1" и "T2" - ставки для электроэнергии двухтарифной</li><li>"T1", "T2" и "T3" - ставки для электроэнергии трехтарифной</li></ul>|

