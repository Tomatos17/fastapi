# Первые шаги

Самый простой FastAPI файл может выглядеть так:

{* ../../docs_src/first_steps/tutorial001.py *}

Скопируйте в файл `main.py`.

Запустите сервер в режиме разработки:

<div class="termy">

```console
$ <font color="#4E9A06">fastapi</font> dev <u style="text-decoration-style:solid">main.py</u>

  <span style="background-color:#009485"><font color="#D3D7CF"> FastAPI </font></span>  Starting development server 🚀

             Searching for package file structure from directories
             with <font color="#3465A4">__init__.py</font> files
             Importing from <font color="#75507B">/home/user/code/</font><font color="#AD7FA8">awesomeapp</font>

   <span style="background-color:#007166"><font color="#D3D7CF"> module </font></span>  🐍 main.py

     <span style="background-color:#007166"><font color="#D3D7CF"> code </font></span>  Importing the FastAPI app object from the module with
             the following code:

             <u style="text-decoration-style:solid">from </u><u style="text-decoration-style:solid"><b>main</b></u><u style="text-decoration-style:solid"> import </u><u style="text-decoration-style:solid"><b>app</b></u>

      <span style="background-color:#007166"><font color="#D3D7CF"> app </font></span>  Using import string: <font color="#3465A4">main:app</font>

   <span style="background-color:#007166"><font color="#D3D7CF"> server </font></span>  Server started at <font color="#729FCF"><u style="text-decoration-style:solid">http://127.0.0.1:8000</u></font>
   <span style="background-color:#007166"><font color="#D3D7CF"> server </font></span>  Documentation at <font color="#729FCF"><u style="text-decoration-style:solid">http://127.0.0.1:8000/docs</u></font>

      <span style="background-color:#007166"><font color="#D3D7CF"> tip </font></span>  Running in development mode, for production use:
             <b>fastapi run</b>

             Logs:

     <span style="background-color:#007166"><font color="#D3D7CF"> INFO </font></span>  Will watch for changes in these directories:
             <b>[</b><font color="#4E9A06">&apos;/home/user/code/awesomeapp&apos;</font><b>]</b>
     <span style="background-color:#007166"><font color="#D3D7CF"> INFO </font></span>  Uvicorn running on <font color="#729FCF"><u style="text-decoration-style:solid">http://127.0.0.1:8000</u></font> <b>(</b>Press CTRL+C
             to quit<b>)</b>
     <span style="background-color:#007166"><font color="#D3D7CF"> INFO </font></span>  Started reloader process <b>[</b><font color="#34E2E2"><b>383138</b></font><b>]</b> using WatchFiles
     <span style="background-color:#007166"><font color="#D3D7CF"> INFO </font></span>  Started server process <b>[</b><font color="#34E2E2"><b>383153</b></font><b>]</b>
     <span style="background-color:#007166"><font color="#D3D7CF"> INFO </font></span>  Waiting for application startup.
     <span style="background-color:#007166"><font color="#D3D7CF"> INFO </font></span>  Application startup complete.
```

</div>

В окне вывода появится следующая строка:

```hl_lines="4"
INFO:     Uvicorn running on http://127.0.0.1:8000 (Press CTRL+C to quit)
```

Эта строка показывает URL-адрес, по которому приложение доступно на локальной машине.

### Проверьте

Откройте браузер по адресу: <a href="http://127.0.0.1:8000" class="external-link" target="_blank">http://127.0.0.1:8000</a>.

Вы увидите JSON-ответ следующего вида:

```JSON
{"message": "Hello World"}
```

### Интерактивная документация API

Перейдите по адресу: <a href="http://127.0.0.1:8000/docs" class="external-link" target="_blank">http://127.0.0.1:8000/docs</a>.

Вы увидите автоматически сгенерированную, интерактивную документацию по API (предоставленную <a href="https://github.com/swagger-api/swagger-ui" class="external-link" target="_blank">Swagger UI</a>):

![Swagger UI](https://fastapi.tiangolo.com/img/index/index-01-swagger-ui-simple.png)

### Альтернативная документация API

Теперь перейдите по адресу <a href="http://127.0.0.1:8000/redoc" class="external-link" target="_blank">http://127.0.0.1:8000/redoc</a>.

Вы увидите альтернативную автоматически сгенерированную документацию (предоставленную <a href="https://github.com/Rebilly/ReDoc" class="external-link" target="_blank">ReDoc</a>):

![ReDoc](https://fastapi.tiangolo.com/img/index/index-02-redoc-simple.png)

### OpenAPI

**FastAPI** генерирует "схему" всего API, используя стандарт **OpenAPI**.

#### "Схема"

"Схема" - это определение или описание чего-либо. Не код, реализующий это, а только абстрактное описание.

#### API "схема"

<a href="https://github.com/OAI/OpenAPI-Specification" class="external-link" target="_blank">OpenAPI</a> - это спецификация, которая определяет, как описывать схему API.

Определение схемы содержит пути (paths) API, их параметры и т.п.

#### "Схема" данных

Термин "схема" также может относиться к формату или структуре некоторых данных, например, JSON.

Тогда, подразумеваются атрибуты JSON, их типы данных и т.п.

#### OpenAPI и JSON Schema

OpenAPI описывает схему API. Эта схема содержит определения (или "схемы") данных, отправляемых и получаемых API. Для описания структуры данных в JSON используется стандарт **JSON Schema**.

#### Рассмотрим `openapi.json`

Если Вас интересует, как выглядит исходная схема OpenAPI, то FastAPI автоматически генерирует JSON-схему со всеми описаниями API.

Можете посмотреть здесь: <a href="http://127.0.0.1:8000/openapi.json" class="external-link" target="_blank">http://127.0.0.1:8000/openapi.json</a>.

Вы увидите примерно такой JSON:

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

Схема OpenAPI является основой для обеих систем интерактивной документации.

Существуют десятки альтернативных инструментов, основанных на OpenAPI. Вы можете легко добавить любой из них к **FastAPI** приложению.

Вы также можете использовать OpenAPI для автоматической генерации кода для клиентов, которые взаимодействуют с API. Например, для фронтенд-, мобильных или IoT-приложений.

## Рассмотрим поэтапно

### Шаг 1: импортируйте `FastAPI`

{* ../../docs_src/first_steps/tutorial001.py hl[1] *}

`FastAPI` это класс в Python, который предоставляет всю функциональность для API.

/// note | Технические детали

`FastAPI` это класс, который наследуется непосредственно от `Starlette`.

Вы можете использовать всю функциональность <a href="https://www.starlette.io/" class="external-link" target="_blank">Starlette</a> в `FastAPI`.

///

### Шаг 2: создайте экземпляр `FastAPI`

{* ../../docs_src/first_steps/tutorial001.py hl[3] *}

Переменная `app` является экземпляром класса `FastAPI`.

### Шаг 3: определите *операцию пути (path operation)*

#### Путь (path)

"Путь" это часть URL, после первого символа `/`, следующего за именем домена.

Для URL:

```
https://example.com/items/foo
```

...путь выглядит так:

```
/items/foo
```

/// info | Дополнительная информация

Термин "path" также часто называется "endpoint" или "route".

///

При создании API, "путь" является основным способом разделения "задач" и "ресурсов".

#### Операция (operation)

"Операция" это один из "методов" HTTP.

Таких, как:

* `POST`
* `GET`
* `PUT`
* `DELETE`

...и более экзотических:

* `OPTIONS`
* `HEAD`
* `PATCH`
* `TRACE`

По протоколу HTTP можно обращаться к каждому пути, используя один (или несколько) из этих "методов".

---

При создании API принято использовать конкретные HTTP-методы для выполнения определенных действий.

Обычно используют:

* `POST`: создать данные.
* `GET`: прочитать.
* `PUT`: изменить (обновить).
* `DELETE`: удалить.

В OpenAPI каждый HTTP метод называется "**операция**".

Мы также будем придерживаться этого термина.

#### Определите *декоратор операции пути (path operation decorator)*

{* ../../docs_src/first_steps/tutorial001.py hl[6] *}

Декоратор `@app.get("/")` указывает **FastAPI**, что функция, прямо под ним, отвечает за обработку запросов, поступающих по адресу:

* путь `/`
* использующих <abbr title="HTTP GET метод"><code>get</code> операцию</abbr>

/// info | `@decorator` Info

Синтаксис `@something` в Python называется "декоратор".

Вы помещаете его над функцией. Как красивую декоративную шляпу (думаю, что оттуда и происходит этот термин).

"Декоратор" принимает функцию ниже и выполняет с ней какое-то действие.

В нашем случае, этот декоратор сообщает **FastAPI**, что функция ниже соответствует **пути** `/` и **операции** `get`.

Это и есть "**декоратор операции пути**".

///

Можно также использовать операции:

* `@app.post()`
* `@app.put()`
* `@app.delete()`

И более экзотические:

* `@app.options()`
* `@app.head()`
* `@app.patch()`
* `@app.trace()`

/// tip | Подсказка

Вы можете использовать каждую операцию (HTTP-метод) по своему усмотрению.

**FastAPI** не навязывает определенного значения для каждого метода.

Информация здесь представлена как рекомендация, а не требование.

Например, при использовании GraphQL обычно все действия выполняются только с помощью POST операций.

///

### Шаг 4: определите **функцию операции пути**

Вот "**функция операции пути**":

* **путь**: `/`.
* **операция**: `get`.
* **функция**: функция ниже "декоратора" (ниже `@app.get("/")`).

{* ../../docs_src/first_steps/tutorial001.py hl[7] *}

Это обычная Python функция.

**FastAPI** будет вызывать её каждый раз при получении `GET` запроса к URL "`/`".

В данном случае это асинхронная функция.

---

Вы также можете определить ее как обычную функцию вместо `async def`:

{* ../../docs_src/first_steps/tutorial003.py hl[7] *}

/// note

Если не знаете в чём разница, посмотрите [Асинхронность: *"Нет времени?"*](../async.md#_1){.internal-link target=_blank}.

///

### Шаг 5: верните результат

{* ../../docs_src/first_steps/tutorial001.py hl[8] *}

Вы можете вернуть `dict`, `list`, отдельные значения `str`, `int` и т.д.

Также можно вернуть модели Pydantic (рассмотрим это позже).

Многие объекты и модели будут автоматически преобразованы в JSON (включая ORM). Пробуйте использовать другие объекты, которые предпочтительней для Вас, вероятно, они уже поддерживаются.

## Резюме

* Импортируем `FastAPI`.
* Создаём экземпляр `app`.
* Пишем **декоратор операции пути** (такой как `@app.get("/")`).
* Пишем **функцию операции пути** (`def root(): ...`).
* Запускаем сервер в режиме разработки с использованием команды `fastapi dev`.
