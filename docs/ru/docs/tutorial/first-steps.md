# Первые шаги

Самый простой файл FastAPI может выглядеть следующим образом:

{* ../../docs_src/first_steps/tutorial001.py *}

Скопируйте этот код в файл `main.py`.

Запустите live сервер:

<div class="termy">

```console
$ <font color="#4E9A06">fastapi</font> dev <u style="text-decoration-style:solid">main.py</u>

  <span style="background-color:#009485"><font color="#D3D7CF"> FastAPI </font></span>  Запуск сервера для разработки 🚀

             Ищем структуру файлов пакета в директориях
             с файлами <font color="#3465A4">__init__.py</font>
             Импортирование из <font color="#75507B">/home/user/code/</font><font color="#AD7FA8">awesomeapp</font>

   <span style="background-color:#007166"><font color="#D3D7CF"> module </font></span>  🐍 main.py

     <span style="background-color:#007166"><font color="#D3D7CF"> code </font></span>  Импортируем объект приложения FastAPI из модуля с 
             помощью следующего кода:

             <u style="text-decoration-style:solid">from </u><u style="text-decoration-style:solid"><b>main</b></u><u style="text-decoration-style:solid"> import </u><u style="text-decoration-style:solid"><b>app</b></u>

      <span style="background-color:#007166"><font color="#D3D7CF"> app </font></span>  Используем строку импорта: <font color="#3465A4">main:app</font>

   <span style="background-color:#007166"><font color="#D3D7CF"> server </font></span>  Сервер запущен по адресу <font color="#729FCF"><u style="text-decoration-style:solid">http://127.0.0.1:8000</u></font>
   <span style="background-color:#007166"><font color="#D3D7CF"> server </font></span>  Документация по адресу <font color="#729FCF"><u style="text-decoration-style:solid">http://127.0.0.1:8000/docs</u></font>

      <span style="background-color:#007166"><font color="#D3D7CF"> tip </font></span>  Запуск в режиме разработки, для использования в продакшене:
             <b>fastapi run</b>

             Логи:

     <span style="background-color:#007166"><font color="#D3D7CF"> INFO </font></span>  Будем отслеживать изменения в этих директориях:
             <b>[</b><font color="#4E9A06">&apos;/home/user/code/awesomeapp&apos;</font><b>]</b>
     <span style="background-color:#007166"><font color="#D3D7CF"> INFO </font></span>  Uvicorn запущен по адресу <font color="#729FCF"><u style="text-decoration-style:solid">http://127.0.0.1:8000</u></font> <b>(</b>нажмите CTRL+C
             для завершения<b>)</b>
     <span style="background-color:#007166"><font color="#D3D7CF"> INFO </font></span>  Процесс перезагрузки запущен <b>[</b><font color="#34E2E2"><b>383138</b></font><b>]</b> с использованием WatchFiles
     <span style="background-color:#007166"><font color="#D3D7CF"> INFO </font></span>  Серверный процесс запущен <b>[</b><font color="#34E2E2"><b>383153</b></font><b>]</b>
     <span style="background-color:#007166"><font color="#D3D7CF"> INFO </font></span>  Ожидание запуска приложения.
     <span style="background-color:#007166"><font color="#D3D7CF"> INFO </font></span>  Запуск приложения завершен.
```

</div>

В выводе будет строка, похожая на:

```hl_lines="4"
INFO:     Uvicorn запущен по адресу http://127.0.0.1:8000 (нажмите CTRL+C для завершения)
```

Эта строка показывает URL, по которому ваше приложение доступно на локальной машине.

### Проверьте это

Откройте браузер по адресу <a href="http://127.0.0.1:8000" class="external-link" target="_blank">http://127.0.0.1:8000</a>.

Вы увидите JSON-ответ, который выглядит следующим образом:

```JSON
{"message": "Hello World"}
```

### Интерактивная документация API

Теперь перейдите по адресу <a href="http://127.0.0.1:8000/docs" class="external-link" target="_blank">http://127.0.0.1:8000/docs</a>.

Вы увидите автоматическую интерактивную документацию API (предоставленную <a href="https://github.com/swagger-api/swagger-ui" class="external-link" target="_blank">Swagger UI</a>):

![Swagger UI](https://fastapi.tiangolo.com/img/index/index-01-swagger-ui-simple.png)

### Альтернативная документация API

И теперь перейдите по адресу <a href="http://127.0.0.1:8000/redoc" class="external-link" target="_blank">http://127.0.0.1:8000/redoc</a>.

Вы увидите альтернативную автоматическую документацию (предоставленную <a href="https://github.com/Rebilly/ReDoc" class="external-link" target="_blank">ReDoc</a>):

![ReDoc](https://fastapi.tiangolo.com/img/index/index-02-redoc-simple.png)

### OpenAPI

**FastAPI** генерирует "схему" всего вашего API, используя стандарт **OpenAPI** для определения API.

#### "Схема"

"Схема" — это определение или описание чего-либо. Не код, реализующий это, а только абстрактное описание.

#### "Схема" API

В данном случае, <a href="https://github.com/OAI/OpenAPI-Specification" class="external-link" target="_blank">OpenAPI</a> — это спецификация, которая определяет, как описывать схему API.

Это определение схемы включает в себя пути вашего API, возможные параметры, которые они принимают, и т.д.

#### "Схема" данных

Термин "схема" также может относиться к формату данных, например, к содержимому JSON.

В этом случае это будет означать атрибуты JSON и типы данных, которые они имеют, и т.д.

#### OpenAPI и JSON Schema

OpenAPI определяет схему API для вашего API. А эта схема включает в себя определения (или "схемы") данных, отправляемых и получаемых вашим API, используя **JSON Schema**, стандарт для схем данных JSON.

#### Посмотрите `openapi.json`

Если вам интересно, как выглядит необработанная схема OpenAPI, FastAPI автоматически генерирует JSON (схему) с описаниями всего вашего API.

Вы можете увидеть её непосредственно по адресу: <a href="http://127.0.0.1:8000/openapi.json" class="external-link" target="_blank">http://127.0.0.1:8000/openapi.json</a>.

Она покажет JSON, начинающийся примерно так:

```JSON
{
    "openapi": "3.1.0",
    "info": {
        "title": "FastAPI",
        "version": "0.1.0"
    },
    "paths": {
        "/items/": {
            "get": {
                "responses": {
                    "200": {
                        "description": "Successful Response",
                        "content": {
                            "application/json": {



...
```

#### Для чего нужен OpenAPI

Схема OpenAPI обеспечивает работу двух включенных систем интерактивной документации.

Существуют десятки альтернатив, все они основываются на OpenAPI. Вы можете легко добавить любую из этих альтернатив к своему приложению на **FastAPI**.

Вы также можете использовать её для автоматической генерации кода для клиентов, которые взаимодействуют с вашим API. Например, для фронтенд-, мобильных или IoT-приложений.

## Рассмотрим поэтапно

### Шаг 1: импортируйте `FastAPI`

{* ../../docs_src/first_steps/tutorial001.py hl[1] *}

`FastAPI` — это класс Python, который предоставляет всю функциональность для вашего API.

/// note | Технические детали

`FastAPI` — это класс, который наследуется напрямую от `Starlette`.

Вы можете использовать всю функциональность <a href="https://www.starlette.io/" class="external-link" target="_blank">Starlette</a> с `FastAPI`.

///

### Шаг 2: создайте "экземпляр" `FastAPI`

{* ../../docs_src/first_steps/tutorial001.py hl[3] *}

Здесь переменная `app` будет "экземпляром" класса `FastAPI`.

Это будет главная точка взаимодействия для создания и работы с вашим API.

### Шаг 3: создайте *операцию пути*

#### Путь

Здесь "путь" относится к последней части URL, начиная с первого `/`.

Таким образом, в URL типа:

```
https://example.com/items/foo
```

...путь будет:

```
/items/foo
```

/// info

"Путь" также часто называют "endpoint" или "route".

///

При создании API "путь" является основным способом отделения "задач" и "ресурсов".

#### Операция

Здесь "операция" относится к одному из HTTP "методов".

Одному из:

* `POST`
* `GET`
* `PUT`
* `DELETE`

...и более экзотическим:

* `OPTIONS`
* `HEAD`
* `PATCH`
* `TRACE`

По протоколу HTTP вы можете взаимодействовать с каждым путем, используя один (или более) из этих "методов".

---

При создании API вы обычно используете эти конкретные HTTP методы для выполнения определенных действий.

Обычно вы используете:

* `POST`: для создания данных.
* `GET`: для чтения данных.
* `PUT`: для обновления данных.
* `DELETE`: для удаления данных.

Таким образом, в OpenAPI каждый из HTTP методов называется "операцией".

Мы также будем называть их "**операциями**".

#### Определите *декоратор операции пути*

{* ../../docs_src/first_steps/tutorial001.py hl[6] *}

`@app.get("/")` сообщает **FastAPI**, что функция, расположенная прямо под ним, отвечает за обработку запросов, поступающих по адресу:

* путь `/`
* использующих операцию <abbr title="HTTP GET метод"><code>get</code></abbr>

/// info | `@decorator` Информация

Синтаксис `@something` в Python называется "декоратор".

Вы располагаете его над функцией. Подобно декоративной шляпе (вероятно, отсюда и происходит этот термин).

"Декоратор" принимает функцию ниже и выполняет с ней какое-то действие.

В нашем случае, этот декоратор сообщает **FastAPI**, что функция ниже соответствует **пути** `/` и **операции** `get`.

Это и есть "**декоратор операции пути**".

///

Вы также можете использовать другие операции:

* `@app.post()`
* `@app.put()`
* `@app.delete()`

И более экзотические:

* `@app.options()`
* `@app.head()`
* `@app.patch()`
* `@app.trace()`

/// tip | Подсказка

Вы можете использовать каждую операцию (HTTP метод) по своему усмотрению.

**FastAPI** не навязывает какого-либо специфического значения.

Информация здесь представлена в качестве рекомендации, а не требования.

Например, при использовании GraphQL обычно все действия выполняются только с помощью `POST` операций.

///

### Шаг 4: определите **функцию операции пути**

Это наша "**функция операции пути**":

* **путь**: это `/`.
* **операция**: это `get`.
* **функция**: это функция под "декоратором" (под `@app.get("/")`).

{* ../../docs_src/first_steps/tutorial001.py hl[7] *}

Это нормальная функция Python.

Она будет вызываться **FastAPI** каждый раз, когда будет получен запрос к URL "`/`" с использованием операции `GET`.

В данном случае она является асинхронной функцией.

---

Вы также можете определить её как обычную функцию вместо `async def`:

{* ../../docs_src/first_steps/tutorial003.py hl[7] *}

/// note

Если вы не знаете разницы, посмотрите [Асинхронность: *"В торопях?"*](../async.md#in-a-hurry){.internal-link target=_blank}.

///

### Шаг 5: верните содержимое

{* ../../docs_src/first_steps/tutorial001.py hl[8] *}

Вы можете вернуть `dict`, `list`, отдельные значения `str`, `int` и т.д.

Также вы можете вернуть модели Pydantic (вы узнаете об этом позже).

Множество других объектов и моделей будут автоматически преобразованы в JSON (включая ORM и т.п.). Попробуйте использовать ваши любимые — они с большой вероятностью уже поддерживаются.

## Резюме

* Импортируйте `FastAPI`.
* Создайте экземпляр `app`.
* Напишите **декоратор операции пути** с помощью декораторов вроде `@app.get("/")`.
* Определите **функцию операции пути**; например, `def root(): ...`.
* Запустите сервер разработки с помощью команды `fastapi dev`.
