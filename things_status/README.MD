Для того, чтобы можно было в виджетах UI отслеживать статус things (версия openhab 3.4.1 это не умеет), можно воспользоваться текущим скриптом, который запускать по крону.

Чтобы отслеживать статус things, надо создать соответствующие Items (тип Switch).

Имя item должно быть таким "state_<thing_uid>",

напримет state_d8cd3080a0
где d8cd3080a0 - это последняя часть (после последнего ":") в идентификаторе thing.

![image](https://user-images.githubusercontent.com/10882718/219475556-3886d1a5-3cb6-45c5-8359-3d042d24850b.png)

![image](https://user-images.githubusercontent.com/10882718/219475722-a6d4d684-7b2f-431e-bea6-824456139df5.png)

Создаем правило

![image](https://user-images.githubusercontent.com/10882718/219476309-4456664b-b7fb-4de6-9d84-f30b78a01dc5.png)

Настраиваем время выполнения по cron.

В **Then** выбираем запуск скрипта

![image](https://user-images.githubusercontent.com/10882718/219476585-e80d6522-b309-419e-ad34-a9de220d9dda.png)

Выбираем тип скрипта ECMAScript 262 Edition 11 

![image](https://user-images.githubusercontent.com/10882718/219476735-a0e92702-bdbf-4009-808d-e10e3ed78d65.png)

В тело скриппта вставляем содержимое https://github.com/d51x/openhab-sccripts/blob/main/things_status.script

###Нагрзука и время выполнения скрипта

На 60 things и 400 items нагрузка на процессор (raspberry pi3) минимальная.

Время выполнения скрипта выглядит так:



    2023-02-16 23:02:15.285 [WARN ] [nhab.automation.script.ui.ab58337194] - duration: 42 ms
    2023-02-16 23:02:30.276 [WARN ] [nhab.automation.script.ui.ab58337194] - duration: 31 ms
    2023-02-16 23:02:45.268 [WARN ] [nhab.automation.script.ui.ab58337194] - duration: 26 ms
    2023-02-16 23:03:00.264 [WARN ] [nhab.automation.script.ui.ab58337194] - duration: 23 ms
    2023-02-16 23:03:15.290 [WARN ] [nhab.automation.script.ui.ab58337194] - duration: 46 ms
    2023-02-16 23:03:30.314 [WARN ] [nhab.automation.script.ui.ab58337194] - duration: 69 ms
    2023-02-16 23:03:45.301 [WARN ] [nhab.automation.script.ui.ab58337194] - duration: 48 ms
    2023-02-16 23:04:00.300 [WARN ] [nhab.automation.script.ui.ab58337194] - duration: 53 ms
    2023-02-16 23:04:15.285 [WARN ] [nhab.automation.script.ui.ab58337194] - duration: 43 ms
    2023-02-16 23:04:30.307 [WARN ] [nhab.automation.script.ui.ab58337194] - duration: 65 ms
    2023-02-16 23:04:46.968 [WARN ] [nhab.automation.script.ui.ab58337194] - duration: 68 ms
    2023-02-16 23:05:00.286 [WARN ] [nhab.automation.script.ui.ab58337194] - duration: 43 ms
    2023-02-16 23:05:15.264 [WARN ] [nhab.automation.script.ui.ab58337194] - duration: 21 ms
    2023-02-16 23:05:30.263 [WARN ] [nhab.automation.script.ui.ab58337194] - duration: 22 ms
    2023-02-16 23:05:45.280 [WARN ] [nhab.automation.script.ui.ab58337194] - duration: 39 ms
    2023-02-16 23:06:00.266 [WARN ] [nhab.automation.script.ui.ab58337194] - duration: 23 ms
    2023-02-16 23:06:15.268 [WARN ] [nhab.automation.script.ui.ab58337194] - duration: 27 ms
    2023-02-16 23:06:30.284 [WARN ] [nhab.automation.script.ui.ab58337194] - duration: 41 ms
    2023-02-16 23:06:45.284 [WARN ] [nhab.automation.script.ui.ab58337194] - duration: 42 ms
    2023-02-16 23:07:00.292 [WARN ] [nhab.automation.script.ui.ab58337194] - duration: 46 ms
    2023-02-16 23:07:15.285 [WARN ] [nhab.automation.script.ui.ab58337194] - duration: 42 ms
    2023-02-16 23:07:30.280 [WARN ] [nhab.automation.script.ui.ab58337194] - duration: 38 ms
    2023-02-16 23:07:45.275 [WARN ] [nhab.automation.script.ui.ab58337194] - duration: 27 ms
    2023-02-16 23:08:00.264 [WARN ] [nhab.automation.script.ui.ab58337194] - duration: 22 ms
    2023-02-16 23:08:15.263 [WARN ] [nhab.automation.script.ui.ab58337194] - duration: 22 ms
    2023-02-16 23:08:30.268 [WARN ] [nhab.automation.script.ui.ab58337194] - duration: 25 ms
    2023-02-16 23:08:45.286 [WARN ] [nhab.automation.script.ui.ab58337194] - duration: 42 ms
    2023-02-16 23:09:00.279 [WARN ] [nhab.automation.script.ui.ab58337194] - duration: 37 ms
