# FastAPI

<style>
.md-content .md-typeset h1 { display: none; }
</style>

<p align="center">
  <a href="https://fastapi.tiangolo.com"><img src="https://fastapi.tiangolo.com/img/logo-margin/logo-teal.png" alt="FastAPI"></a>
</p>
<p align="center">
    <em>Фреймворк FastAPI: высокая производительность, простота освоения, быстрая разработка, готов к использованию в производстве</em>
</p>
<p align="center">
<a href="https://github.com/fastapi/fastapi/actions?query=workflow%3ATest+event%3Apush+branch%3Amaster" target="_blank">
    <img src="https://github.com/fastapi/fastapi/actions/workflows/test.yml/badge.svg?event=push&branch=master" alt="Test">
</a>
<a href="https://coverage-badge.samuelcolvin.workers.dev/redirect/fastapi/fastapi" target="_blank">
    <img src="https://coverage-badge.samuelcolvin.workers.dev/fastapi/fastapi.svg" alt="Coverage">
</a>
<a href="https://pypi.org/project/fastapi" target="_blank">
    <img src="https://img.shields.io/pypi/v/fastapi?color=%2334D058&label=pypi%20package" alt="Package version">
</a>
<a href="https://pypi.org/project/fastapi" target="_blank">
    <img src="https://img.shields.io/pypi/pyversions/fastapi.svg?color=%2334D058" alt="Supported Python versions">
</a>
</p>

---

**Документация**: <a href="https://fastapi.tiangolo.com" target="_blank">https://fastapi.tiangolo.com</a>

**Исходный код**: <a href="https://github.com/fastapi/fastapi" target="_blank">https://github.com/fastapi/fastapi</a>

---

FastAPI — это современный, быстрый (высокопроизводительный) веб-фреймворк для создания API, использующий Python и стандартные аннотации типов Python.

Ключевые особенности:

* **Скорость**: Очень высокая производительность, на уровне **NodeJS** и **Go** (благодаря Starlette и Pydantic). [Один из самых быстрых фреймворков Python](#performance).
* **Быстрота разработки**: Увеличьте скорость разработки примерно на 200–300%. *
* **Меньше ошибок**: Сократите примерно на 40% количество ошибок, вызванных человеком (разработчиком). *
* **Интуитивно понятный**: Отличная поддержка редактора. <abbr title="также известное как автозаполнение, автодополнение, IntelliSense">Автозавершение</abbr> везде. Меньше времени на отладку.
* **Лёгкость**: Разработан так, чтобы его было легко использовать и осваивать. Меньше времени на чтение документации.
* **Краткость**: Сведите к минимуму дублирование кода. Каждый объявленный параметр - определяет несколько функций. Меньше ошибок.
* **Надежность**: Получите готовый к работе код. С автоматической интерактивной документацией.
* **На основе стандартов**: Основан на открытых стандартах API и полностью совместим с ними: <a href="https://github.com/OAI/OpenAPI-Specification" class="external-link" target="_blank">OpenAPI</a> (ранее известном как Swagger) и <a href="https://json-schema.org/" class="external-link" target="_blank">JSON Schema</a>.

<small>* оценка на основе тестов внутренней команды разработчиков, создающих продакшн приложения.</small>

## Спонсоры

<!-- sponsors -->

{% if sponsors %}
{% for sponsor in sponsors.gold -%}
<a href="{{ sponsor.url }}" target="_blank" title="{{ sponsor.title }}"><img src="{{ sponsor.img }}" style="border-radius:15px"></a>
{% endfor -%}
{%- for sponsor in sponsors.silver -%}
<a href="{{ sponsor.url }}" target="_blank" title="{{ sponsor.title }}"><img src="{{ sponsor.img }}" style="border-radius:15px"></a>
{% endfor %}
{% endif %}

<!-- /sponsors -->

<a href="https://fastapi.tiangolo.com/fastapi-people/#sponsors" class="external-link" target="_blank">Другие спонсоры</a>

## Отзывы

"_[...] В последнее время я много использую **FastAPI**. [...] На самом деле, я планирую использовать его для всех **сервисов машинного обучения моей команды в Microsoft**. Некоторые из них интегрируются в основной продукт **Windows**, а некоторые — в продукты **Office**._"

<div style="text-align: right; margin-right: 10%;">Kabir Khan - <strong>Microsoft</strong> <a href="https://github.com/fastapi/fastapi/pull/26" target="_blank"><small>(ref)</small></a></div>

---

"_Мы приняли библиотеку **FastAPI** для создания сервера **REST**, к которому можно обращаться для получения **прогнозов**. [для Ludwig]_"

<div style="text-align: right; margin-right: 10%;">Piero Molino, Yaroslav Dudin, and Sai Sumanth Miryala - <strong>Uber</strong> <a href="https://eng.uber.com/ludwig-v0-2/" target="_blank"><small>(ref)</small></a></div>

---

"_**Netflix** рада объявить о выпуске фреймворка для оркестрации **кризисного управления**: **Dispatch**! [создан с использованием **FastAPI**]_"

<div style="text-align: right; margin-right: 10%;">Kevin Glisson, Marc Vilanova, Forest Monsen - <strong>Netflix</strong> <a href="https://netflixtechblog.com/introducing-dispatch-da4b8a2a8072" target="_blank"><small>(ref)</small></a></div>

---

"_Меня невероятно радует **FastAPI**. Это так весело!_"

<div style="text-align: right; margin-right: 10%;">Brian Okken - <strong><a href="https://pythonbytes.fm/episodes/show/123/time-to-right-the-py-wrongs?time_in_sec=855" target="_blank">Python Bytes</a> ведущий подкаста</strong> <a href="https://twitter.com/brianokken/status/1112220079972728832" target="_blank"><small>(ref)</small></a></div>

---

"_Честно говоря, то, что вы создали, выглядит очень солидно и отшлифовано. В многих отношениях это то, чем я хотел, чтобы было **Hug** — это действительно вдохновляет, когда кто-то создает такое._"

<div style="text-align: right; margin-right: 10%;">Timothy Crosley - <strong><a href="https://github.com/hugapi/hug" target="_blank">Hug</a> создатель</strong> <a href="https://news.ycombinator.com/item?id=19455465" target="_blank"><small>(ref)</small></a></div>

---

"_Если вы хотите изучить какой-нибудь **современный фреймворк** для создания REST API, ознакомьтесь с **FastAPI** [...] Это быстрый, простой в использовании и в изучении фреймворк [...]_"

"_Мы перешли на **FastAPI** для наших **API** [...] Думаю, он вам понравится [...]_"

<div style="text-align: right; margin-right: 10%;">Ines Montani - Matthew Honnibal - <strong><a href="https://explosion.ai" target="_blank">Explosion AI</a> founders - <a href="https://spacy.io" target="_blank">spaCy</a> creators</strong> <a href="https://twitter.com/_inesmontani/status/1144173225322143744" target="_blank"><small>(ref)</small></a> - <a href="https://twitter.com/honnibal/status/1144031421859655680" target="_blank"><small>(ref)</small></a></div>

---

"_Если кто-то хочет создать продакшн Python API, я бы настоятельно рекомендовал **FastAPI**. Он **прекрасно разработан**, **прост в использовании** и **высокомасштабируем**, он стал **ключевым компонентом** нашей стратегии разработки API-first и управляет множеством автоматизаций и сервисов, таких как наш виртуальный инженер TAC._"

<div style="text-align: right; margin-right: 10%;">Deon Pillsbury - <strong>Cisco</strong> <a href="https://www.linkedin.com/posts/deonpillsbury_cisco-cx-python-activity-6963242628536487936-trAp/" target="_blank"><small>(ref)</small></a></div>

---

"_Если кто-то хочет создать производственный Python API, я бы очень рекомендовал **FastAPI**. Он **замечательно спроектирован**, **прост в использовании** и **очень масштабируем**, он стал **ключевым компонентом** в нашей стратегии разработки API. Благодаря нему автоматизация и сервисы, такие как наш Виртуальный Инженер TAC, стали возможными._"

<div style="text-align: right; margin-right: 10%;">Deon Pillsbury - <strong>Cisco</strong> <a href="https://www.linkedin.com/posts/deonpillsbury_cisco-cx-python-activity-6963242628536487936-trAp/" target="_blank"><small>(ref)</small></a></div>

---

## **Typer**, FastAPI для CLI

<a href="https://typer.tiangolo.com" target="_blank"><img src="https://typer.tiangolo.com/img/logo-margin/logo-margin-vector.svg" style="width: 20%;"></a>

Если вы создаете приложение для <abbr title="Command Line Interface">CLI</abbr>, используемое в терминале вместо веб API, ознакомьтесь с <a href="https://typer.tiangolo.com/" class="external-link" target="_blank">**Typer**</a>.

**Typer** — младший брат FastAPI. Он предназначен быть **FastAPI для CLI**. ⌨️ 🚀

## Требования

FastAPI опирается на гигантов:

* <a href="https://www.starlette.io/" class="external-link" target="_blank">Starlette</a> для веб-компонентов.
* <a href="https://docs.pydantic.dev/" class="external-link" target="_blank">Pydantic</a> для работы с данными.

## Установка

Создайте и активируйте <a href="https://fastapi.tiangolo.com/virtual-environments/" class="external-link" target="_blank">виртуальное окружение</a>, а затем установите FastAPI:

<div class="termy">

```console
$ pip install "fastapi[standard]"

---> 100%
```

</div>

**Примечание**: Убедитесь, что вы используете кавычки для `"fastapi[standard]"`, чтобы обеспечить его работу во всех терминалах.

## Пример

### Создание

Создайте файл `main.py` с:

```Python
from typing import Union

from fastapi import FastAPI

app = FastAPI()


@app.get("/")
def read_root():
    return {"Hello": "World"}


@app.get("/items/{item_id}")
def read_item(item_id: int, q: Union[str, None] = None):
    return {"item_id": item_id, "q": q}
```

<details markdown="1">
<summary>Или используйте <code>async def</code>...</summary>

Если ваш код использует `async` / `await`, используйте `async def`:

```Python hl_lines="9  14"
from typing import Union

from fastapi import FastAPI

app = FastAPI()


@app.get("/")
async def read_root():
    return {"Hello": "World"}


@app.get("/items/{item_id}")
async def read_item(item_id: int, q: Union[str, None] = None):
    return {"item_id": item_id, "q": q}
```

**Примечание**:

Если вы не знаете, проверьте раздел _"Нет времени?"_ <a href="https://fastapi.tiangolo.com/async/#in-a-hurry" target="_blank">в документации об `async` и `await`</a>.

</details>

### Запуск

Запустите сервер с помощью:

<div class="termy">

```console
$ fastapi dev main.py

 ╭────────── FastAPI CLI - Development mode ───────────╮
 │                                                     │
 │  Serving at: http://127.0.0.1:8000                  │
 │                                                     │
 │  API docs: http://127.0.0.1:8000/docs               │
 │                                                     │
 │  Running in development mode, for production use:   │
 │                                                     │
 │  fastapi run                                        │
 │                                                     │
 ╰─────────────────────────────────────────────────────╯

INFO:     Will watch for changes in these directories: ['/home/user/code/awesomeapp']
INFO:     Uvicorn running on http://127.0.0.1:8000 (Press CTRL+C to quit)
INFO:     Started reloader process [2248755] using WatchFiles
INFO:     Started server process [2248757]
INFO:     Waiting for application startup.
INFO:     Application startup complete.
```

</div>

<details markdown="1">
<summary>О команде <code>fastapi dev main.py</code>...</summary>

Команда `fastapi dev` считывает файл `main.py`, определяет в нем приложение **FastAPI** и запускает сервер с использованием <a href="https://www.uvicorn.org" class="external-link" target="_blank">Uvicorn</a>.

По умолчанию `fastapi dev` запускает приложение с включенной авто-перезагрузкой для локальной разработки.

Вы можете узнать больше об этом в <a href="https://fastapi.tiangolo.com/fastapi-cli/" target="_blank">документации FastAPI CLI</a>.

</details>

### Проверка

Откройте ваш браузер на <a href="http://127.0.0.1:8000/items/5?q=somequery" class="external-link" target="_blank">http://127.0.0.1:8000/items/5?q=somequery</a>.

Вы увидите следующий JSON ответ:

```JSON
{"item_id": 5, "q": "somequery"}
```

Вы уже создали API, который:

* Получает HTTP-запросы в _пути_ `/` и `/items/{item_id}`.
* Оба _пути_ принимают операции `GET` <em>(также известные как HTTP методы)</em>.
* _Путь_ `/items/{item_id}` принимает _параметр пути_ `item_id`, который должен быть `int`.
* _Путь_ `/items/{item_id}` имеет необязательный `str` _параметр запроса_ `q`.

### Интерактивная документация по API

Перейдите на <a href="http://127.0.0.1:8000/docs" class="external-link" target="_blank">http://127.0.0.1:8000/docs</a>.

Вы увидите автоматическую интерактивную документацию API (предоставленную <a href="https://github.com/swagger-api/swagger-ui" class="external-link" target="_blank">Swagger UI</a>):

![Swagger UI](https://fastapi.tiangolo.com/img/index/index-01-swagger-ui-simple.png)

### Альтернативная документация по API

А теперь перейдите на <a href="http://127.0.0.1:8000/redoc" class="external-link" target="_blank">http://127.0.0.1:8000/redoc</a>.

Вы увидите альтернативную автоматическую документацию (предоставленную <a href="https://github.com/Rebilly/ReDoc" class="external-link" target="_blank">ReDoc</a>):

![ReDoc](https://fastapi.tiangolo.com/img/index/index-02-redoc-simple.png)

## Обновление примера

Теперь измените файл `main.py`, чтобы получать тело из `PUT` запроса.

Объявите тело, используя стандартную типизацию Python, благодаря Pydantic.

```Python hl_lines="4  9-12  25-27"
from typing import Union

from fastapi import FastAPI
from pydantic import BaseModel

app = FastAPI()


class Item(BaseModel):
    name: str
    price: float
    is_offer: Union[bool, None] = None


@app.get("/")
def read_root():
    return {"Hello": "World"}


@app.get("/items/{item_id}")
def read_item(item_id: int, q: Union[str, None] = None):
    return {"item_id": item_id, "q": q}


@app.put("/items/{item_id}")
def update_item(item_id: int, item: Item):
    return {"item_name": item.name, "item_id": item_id}
```

Сервер `fastapi dev` должен автоматически перезагрузиться.

### Обновление интерактивной документации по API

Теперь перейдите на <a href="http://127.0.0.1:8000/docs" class="external-link" target="_blank">http://127.0.0.1:8000/docs</a>.

* Интерактивная документация API обновится автоматически, включая новое тело:

![Swagger UI](https://fastapi.tiangolo.com/img/index/index-03-swagger-02.png)

* Нажмите кнопку "Try it out", чтобы заполнить параметры и напрямую взаимодействовать с API:

![Swagger UI interaction](https://fastapi.tiangolo.com/img/index/index-04-swagger-03.png)

* Затем нажмите кнопку "Execute", интерфейс свяжется с вашим API, отправит параметры, получит результаты и покажет их на экране:

![Swagger UI interaction](https://fastapi.tiangolo.com/img/index/index-05-swagger-04.png)

### Обновление альтернативной документации по API

А теперь перейдите на <a href="http://127.0.0.1:8000/redoc" class="external-link" target="_blank">http://127.0.0.1:8000/redoc</a>.

* Альтернативная документация также отразит новый параметр запроса и тело:

![ReDoc](https://fastapi.tiangolo.com/img/index/index-06-redoc-02.png)

### Итоги

Подводя итоги, вы объявляете **один раз** типы параметров, тела и т. д. в качестве параметров функции.

Вы делаете это с использованием стандартной современной типизации Python.

Вам не нужно изучать новый синтаксис, методы или классы конкретной библиотеки и т. д.

Просто стандартный **Python**.

Например, для `int`:

```Python
item_id: int
```

или для более сложной модели `Item`:

```Python
item: Item
```

...и с этим единственным объявлением вы получаете:

* Поддержку редактора, включая:
    * Автозавершение.
    * Проверку типов.
* Валидацию данных:
    * Автоматические и чёткие ошибки, когда данные недействительны.
    * Валидацию даже для глубоко вложенных объектов JSON.
* <abbr title="также известна как: сериализация, синтаксический анализ, маршаллинг">Преобразование</abbr> входных данных: поступающих из сети в данные и типы Python. Чтение из:
    * JSON.
    * Параметров пути.
    * Параметров запроса.
    * Cookies.
    * Заголовков.
    * Форм.
    * Файлов.
* <abbr title="также известна как: сериализация, синтаксический анализ, маршаллинг">Преобразование</abbr> выходных данных: преобразование данных и типов Python в данные сети (например JSON):
    * Преобразование типов Python (`str`, `int`, `float`, `bool`, `list`, и т. д.).
    * Объекты `datetime`.
    * Объекты `UUID`.
    * Модели баз данных.
    * ...и многое другое.
* Автоматическая интерактивная документация по API, включая 2 альтернативных пользовательских интерфейса:
    * Swagger UI.
    * ReDoc.

---

Возвращаясь к предыдущему примеру кода, **FastAPI** будет:

* Проверять, что в пути есть `item_id` для `GET` и `PUT` запросов.
* Проверять, что `item_id` имеет тип `int` для `GET` и `PUT` запросов.
    * Если это не так, клиент увидит полезную, чёткую ошибку.
* Проверять, есть ли необязательный параметр запроса с именем `q` (например, `http://127.0.0.1:8000/items/foo?q=somequery`) для `GET` запросов.
    * Поскольку параметр `q` объявлен с `= None`, он является необязательным.
    * Без `None` он бы был обязательным (как тело в случае с `PUT`).
* Для `PUT` запросов к `/items/{item_id}` читать тело как JSON:
    * Проверять, что у него есть обязательное свойство `name`, которое должно быть `str`.
    * Проверять, что у него есть обязательное свойство `price`, которое должно быть `float`.
    * Проверять, что у него есть необязательное свойство `is_offer`, которое должно быть `bool`, если оно присутствует.
    * Всё это также будет работать для глубоко вложенных объектов JSON.
* Преобразовывать из и в JSON автоматически.
* Документировать всё с помощью OpenAPI, что можно использовать:
    * Системы интерактивной документации.
    * Автоматические системы генерации клиентского кода для многих языков.
* Предоставлять 2 интерактивных веб-интерфейса документации напрямую.

---

Мы только немного поверхностно ознакомились, но вы уже поняли, как все это работает.

Попробуйте изменить строку:

```Python
    return {"item_name": item.name, "item_id": item_id}
```

...из:

```Python
        ... "item_name": item.name ...
```

...в:

```Python
        ... "item_price": item.price ...
```

...и посмотрите, как ваш редактор автоматически завершает атрибуты и знает их типы:

![editor support](https://fastapi.tiangolo.com/img/vscode-completion.png)

Более полный пример с дополнительными функциями см. в <a href="https://fastapi.tiangolo.com/tutorial/">Учебное руководство - Руководство пользователя</a>.

**Внимание, спойлер**: учебное руководство - Руководство пользователя включает:

* Объявление **параметров** из других мест, таких как: **заголовки**, **cookies**, **поля формы** и **файлы**.
* Как установить **ограничительные проверки** такие как `maximum_length` или `regex`.
* Очень мощная и простая в использовании система **<abbr title="также известная как компоненты, ресурсы, провайдеры, услуги, инъекции">Внедрение Зависимостей</abbr>**.
* Безопасность и аутентификация, включая поддержку **OAuth2** с **токенами JWT** и **HTTP Basic** авторизация.
* Более продвинутые (но столь же простые) методы объявления **глубоко вложенных моделей JSON** (благодаря Pydantic).
* **GraphQL** интеграция с <a href="https://strawberry.rocks" class="external-link" target="_blank">Strawberry</a> и другими библиотеками.
* Много дополнительных функций (благодаря Starlette), как например:
    * **WebSockets**
    * невероятно простые тесты, основанные на HTTPX и `pytest`
    * **CORS**
    * **Сессии с использованием Cookie**
    * ...и многое другое.

## Производительность

Независимые бенчмарки TechEmpower демонстрируют приложения **FastAPI**, работающие под Uvicorn, как <a href="https://www.techempower.com/benchmarks/#section=test&runid=7464e520-0dc2-473d-bd34-dbdfd7e85911&hw=ph&test=query&l=zijzen-7" class="external-link" target="_blank">один из самых быстрых доступных фреймворков на Python</a>, уступающий только самим Starlette и Uvicorn (используемых внутри FastAPI). (*)

Чтобы узнать больше об этом, см. раздел <a href="https://fastapi.tiangolo.com/benchmarks/" class="internal-link" target="_blank">Тесты производительности</a>.

## Зависимости

FastAPI зависит от Pydantic и Starlette.

### Зависимости `standard`

Когда вы устанавливаете FastAPI с помощью `pip install "fastapi[standard]"`, он включает группу зависимостей `standard`:

Используется Pydantic:

* <a href="https://github.com/JoshData/python-email-validator" target="_blank"><code>email-validator</code></a> - для проверки электронной почты.

Используется Starlette:

* <a href="https://www.python-httpx.org" target="_blank"><code>httpx</code></a> - Обязательно, если вы хотите использовать `TestClient`.
* <a href="https://jinja.palletsprojects.com" target="_blank"><code>jinja2</code></a> - Обязательно, если вы хотите использовать конфигурацию шаблона по умолчанию.
* <a href="https://github.com/Kludex/python-multipart" target="_blank"><code>python-multipart</code></a> - Обязательно, если вы хотите поддерживать форму <abbr title="преобразование строки, полученной из HTTP-запроса, в данные Python">"парсинга"</abbr> с помощью `request.form()`.

Используется FastAPI:

* <a href="https://www.uvicorn.org" target="_blank"><code>uvicorn</code></a> - для сервера, который загружает и обслуживает ваше приложение. Это включает `uvicorn[standard]`, который включает некоторые зависимости (например, `uvloop`), необходимые для высокопроизводительного обслуживания.
* `fastapi-cli[standard]` - для предоставления команды `fastapi`.
    * Это включает `fastapi-cloud-cli`, который позволяет разворачивать ваше приложение FastAPI в <a href="https://fastapicloud.com" class="external-link" target="_blank">FastAPI Cloud</a>.

### Без зависимостей `standard`

Если вы не хотите включать необязательные зависимости `standard`, вы можете установить FastAPI с помощью `pip install fastapi` вместо `pip install "fastapi[standard]"`.

### Без `fastapi-cloud-cli`

Если вы хотите установить FastAPI с стандартными зависимостями, но без `fastapi-cloud-cli`, вы можете установить с помощью `pip install "fastapi[standard-no-fastapi-cloud-cli]"`.

### Дополнительные необязательные зависимости

Существуют некоторые дополнительные зависимости, которые вы можете захотеть установить.

Дополнительные необязательные зависимости Pydantic:

* <a href="https://docs.pydantic.dev/latest/usage/pydantic_settings/" target="_blank"><code>pydantic-settings</code></a> - для управления настройками.
* <a href="https://docs.pydantic.dev/latest/usage/types/extra_types/extra_types/" target="_blank"><code>pydantic-extra-types</code></a> - для дополнительных типов, которые могут быть использованы с Pydantic.

Дополнительные необязательные зависимости FastAPI:

* <a href="https://github.com/ijl/orjson" target="_blank"><code>orjson</code></a> - Обязательно, если вы хотите использовать `ORJSONResponse`.
* <a href="https://github.com/esnme/ultrajson" target="_blank"><code>ujson</code></a> - Обязательно, если вы хотите использовать `UJSONResponse`.

## Лицензия

Этот проект распространяется на условиях лицензии MIT.
