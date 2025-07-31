# Запуск сервера вручную

## Используйте команду `fastapi run`

Кратко говоря, используйте `fastapi run` для запуска вашего приложения FastAPI:

<div class="termy">

```console
$ <font color="#4E9A06">fastapi</font> run <u style="text-decoration-style:solid">main.py</u>

  <span style="background-color:#009485"><font color="#D3D7CF"> FastAPI </font></span>  Starting production server 🚀

             Searching for package file structure from directories
             with <font color="#3465A4">__init__.py</font> files
             Importing from <font color="#75507B">/home/user/code/</font><font color="#AD7FA8">awesomeapp</font>

   <span style="background-color:#007166"><font color="#D3D7CF"> module </font></span>  🐍 main.py

     <span style="background-color:#007166"><font color="#D3D7CF"> code </font></span>  Importing the FastAPI app object from the module with
             the following code:

             <u style="text-decoration-style:solid">from </u><u style="text-decoration-style:solid"><b>main</b></u><u style="text-decoration-style:solid"> import </u><u style="text-decoration-style:solid"><b>app</b></u>

      <span style="background-color:#007166"><font color="#D3D7CF"> app </font></span>  Using import string: <font color="#3465A4">main:app</font>

   <span style="background-color:#007166"><font color="#D3D7CF"> server </font></span>  Server started at <font color="#729FCF"><u style="text-decoration-style:solid">http://0.0.0.0:8000</u></font>
   <span style="background-color:#007166"><font color="#D3D7CF"> server </font></span>  Documentation at <font color="#729FCF"><u style="text-decoration-style:solid">http://0.0.0.0:8000/docs</u></font>

             Logs:

     <span style="background-color:#007166"><font color="#D3D7CF"> INFO </font></span>  Started server process <b>[</b><font color="#34E2E2"><b>2306215</b></font><b>]</b>
     <span style="background-color:#007166"><font color="#D3D7CF"> INFO </font></span>  Waiting for application startup.
     <span style="background-color:#007166"><font color="#D3D7CF"> INFO </font></span>  Application startup complete.
     <span style="background-color:#007166"><font color="#D3D7CF"> INFO </font></span>  Uvicorn running on <font color="#729FCF"><u style="text-decoration-style:solid">http://0.0.0.0:8000</u></font> <b>(</b>Press CTRL+C
             to quit<b>)</b>
```

</div>

Это подойдет для большинства случаев. 😎

Вы можете использовать эту команду, например, для запуска вашего приложения **FastAPI** в контейнере, на сервере и т. д.

## ASGI-серверы

Давайте углубимся в детали.

FastAPI использует стандарт для создания веб-фреймворков и серверов на Python под названием <abbr title="Asynchronous Server Gateway Interface">ASGI</abbr>. FastAPI — это веб-фреймворк на основе ASGI.

Основное, что вам требуется для запуска приложения **FastAPI** (или любого другого приложения на основе ASGI) на удаленной серверной машине — это программа ASGI-сервера, такая как **Uvicorn**, именно она используется по умолчанию в команде `fastapi`.

Существует несколько альтернатив, включая:

* <a href="https://www.uvicorn.org/" class="external-link" target="_blank">Uvicorn</a>: высокопроизводительный ASGI-сервер.
* <a href="https://hypercorn.readthedocs.io/" class="external-link" target="_blank">Hypercorn</a>: ASGI-сервер, поддерживающий HTTP/2 и Trio среди прочих возможностей.
* <a href="https://github.com/django/daphne" class="external-link" target="_blank">Daphne</a>: ASGI-сервер, созданный для Django Channels.
* <a href="https://github.com/emmett-framework/granian" class="external-link" target="_blank">Granian</a>: HTTP-сервер на Rust для Python-приложений.
* <a href="https://unit.nginx.org/howto/fastapi/" class="external-link" target="_blank">NGINX Unit</a>: NGINX Unit — легковесная и универсальная среда выполнения веб-приложений.

## Сервер как машина и сервер как программа

Есть небольшая деталь в названиях, о которой стоит помнить. 💡

Слово "**сервер**" обычно используется для обозначения как удаленного/облачного компьютера (физической или виртуальной машины), так и программы, которая на этой машине работает (например, Uvicorn).

Просто имейте в виду, что когда вы видите "сервер", это может относиться к одному из этих двух значений.

Когда речь идет о удаленной машине, часто используется термин **сервер**, но также можно встретить **машина**, **ВМ** (виртуальная машина), **нода**. Все это обозначает какую-то удаленную машину, обычно под управлением Linux, на которой вы запускаете программы.

## Установка программного сервера

При установке FastAPI он поставляется с продакшн-сервером Uvicorn, и его можно запустить с помощью команды `fastapi run`.

Но вы также можете установить ASGI-сервер вручную.

Убедитесь, что вы создали [виртуальное окружение](../virtual-environments.md){.internal-link target=_blank}, активировали его, а затем вы можете установить приложение сервера.

Например, для установки Uvicorn:

<div class="termy">

```console
$ pip install "uvicorn[standard]"

---> 100%
```

</div>

Схожий процесс применим к любым другим программам ASGI-серверов.

/// tip | Подсказка

Добавляя `standard`, Uvicorn установит и будет использовать некоторые рекомендованные дополнительные зависимости.

Сюда входит `uvloop`, высокопроизводительная замена для `asyncio`, которая дает значительное ускорение производительности асинхронных программ.

Когда вы устанавливаете FastAPI подобно `pip install "fastapi[standard]"`, вы уже получаете `uvicorn[standard]`.

///

## Запуск программы сервера

Если вы установили ASGI-сервер вручную, обычно вам нужно передать импортную строку в специальном формате, чтобы он импортировал ваше FastAPI приложение:

<div class="termy">

```console
$ uvicorn main:app --host 0.0.0.0 --port 80

<span style="color: green;">INFO</span>:     Uvicorn running on http://0.0.0.0:80 (Press CTRL+C to quit)
```

</div>

/// note | Примечание

Команда `uvicorn main:app` относится к:

* `main`: файл `main.py` (Python "модуль").
* `app`: объект, созданный внутри `main.py` с помощью строки `app = FastAPI()`.

Это эквивалентно:

```Python
from main import app
```

///

Каждая из альтернативных программ ASGI-серверов будет иметь аналогичную команду, вы можете узнать больше в их документации.

/// warning | Предупреждение

Uvicorn и другие серверы поддерживают опцию `--reload`, которая полезна в процессе разработки.

Опция `--reload` потребляет гораздо больше ресурсов, более нестабильна и т. д.

Она очень помогает во время **разработки**, но **не следует** использовать её в **продакшне**.

///

## Концепции развёртывания

Эти примеры запускают программное обеспечение сервера (например, Uvicorn), начиная **один процесс**, слушающий все IP (`0.0.0.0`) на заранее определенном порту (например, `80`).

Это основная идея. Но, вероятно, вам захочется позаботиться о некоторых дополнительных вещах, таких как:

* Безопасность - HTTPS
* Запуск при старте
* Перезапуски
* Репликация (количество запущенных процессов)
* Память
* Предварительные действия перед запуском

Я расскажу вам больше о каждой из этих концепций, как о них думать и приведу конкретные примеры со стратегиями их решения в следующих главах. 🚀
