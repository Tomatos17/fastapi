# Ручной запуск сервера

## Используйте команду `fastapi run`

Вкратце, используйте `fastapi run` для запуска вашего приложения FastAPI:

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

Это подходящий вариант для большинства случаев. 😎

Вы можете использовать эту команду, чтобы, например, запустить ваше приложение **FastAPI** в контейнере, на сервере и т. д.

## ASGI-серверы

Давайте углубимся в детали.

FastAPI использует стандарт для создания веб-фреймворков и серверов в Python, называемый <abbr title="Asynchronous Server Gateway Interface">ASGI</abbr>. FastAPI — это ASGI веб-фреймворк.

Основное, что вам нужно для запуска приложения **FastAPI** (или любого другого ASGI приложения) на удалённой серверной машине — это программа сервера ASGI, такая как **Uvicorn**, которая поставляется по умолчанию с командой `fastapi`.

Существует ряд альтернатив, включая:

* <a href="https://www.uvicorn.org/" class="external-link" target="_blank">Uvicorn</a>: высокопроизводительный ASGI-сервер.
* <a href="https://hypercorn.readthedocs.io/" class="external-link" target="_blank">Hypercorn</a>: ASGI-сервер, совместимый с HTTP/2 и Trio, среди прочих функций.
* <a href="https://github.com/django/daphne" class="external-link" target="_blank">Daphne</a>: ASGI-сервер, созданный для Django Channels.
* <a href="https://github.com/emmett-framework/granian" class="external-link" target="_blank">Granian</a>: сервер HTTP на Rust для Python приложений.
* <a href="https://unit.nginx.org/howto/fastapi/" class="external-link" target="_blank">NGINX Unit</a>: лёгкая и универсальная среда выполнения веб-приложений.

## Сервер как машина и сервер как программа

Есть небольшой нюанс в терминологии, который стоит помнить. 💡

Слово "**сервер**" часто используется для обозначения как удалённого/облачного компьютера (физической или виртуальной машины), так и программы, работающей на этой машине (например, Uvicorn).

Просто держите в уме, что, когда вы видите слово "сервер", это может относиться к одному из этих двух понятий.

Когда говорят о удалённой машине, часто упоминают просто **сервер**, но также могут называть его **машина**, **ВМ** (виртуальная машина), **нода**. Все эти термины обозначают какой-то тип удалённого компьютера, обычно с операционной системой Linux, на котором вы запускаете программы.

## Установка программы сервера

При установке FastAPI, он поставляется с продакшн-сервером, Uvicorn, и вы можете запустить его с командой `fastapi run`.

Но вы также можете установить ASGI-сервер вручную.

Убедитесь, что вы создали [виртуальное окружение](../virtual-environments.md){.internal-link target=_blank}, активировали его, и затем вы можете установить серверное приложение.

Например, чтобы установить Uvicorn:

<div class="termy">

```console
$ pip install "uvicorn[standard]"

---> 100%
```

</div>

Аналогичный процесс применим и к любой другой программе ASGI-сервера.

/// tip | Подсказка

Добавив `standard`, Uvicorn установит и будет использовать некоторые рекомендуемые дополнительные зависимости.

В их числе `uvloop`, высокопроизводительная замена `asyncio`, которая обеспечивает ощутимый прирост скорости обработки запросов с большими объемами данных.

Когда вы устанавливаете FastAPI с чем-то вроде `pip install "fastapi[standard]"`, вы уже получаете `uvicorn[standard]`.

///

## Запуск программы сервера

Если вы установили ASGI-сервер вручную, вам обычно потребуется указать строку для импорта в специальном формате, чтобы он мог импортировать ваше FastAPI-приложение:

<div class="termy">

```console
$ uvicorn main:app --host 0.0.0.0 --port 80

<span style="color: green;">INFO</span>:     Uvicorn running on http://0.0.0.0:80 (Press CTRL+C to quit)
```

</div>

/// note | Примечание

Команда `uvicorn main:app` обозначает:

* `main`: файл `main.py` (модуль Python).
* `app`: объект, созданный внутри `main.py` строкой `app = FastAPI()`.

Это эквивалентно:

```Python
from main import app
```

///

Каждая из альтернатив программ ASGI-сервера будет иметь схожую команду, вы можете узнать больше в их документации.

/// warning | Предупреждение

Uvicorn и другие серверы поддерживают опцию `--reload`, которая полезна в процессе разработки.

Опция `--reload` потребляет намного больше ресурсов, она менее стабильна и так далее.

Она очень помогает во время **разработки**, но **не рекомендуется** использовать её в **продакшн**.

///

## Концепции развёртывания

Эти примеры запускают серверные программы (например, Uvicorn), начиная с **одного процесса**, слушающего все IP-адреса (`0.0.0.0`) на определенном порту (например, `80`).

Это основная идея. Но вы, вероятно, захотите позаботиться о некоторых дополнительных вещах, таких как:

* Безопасность - HTTPS
* Запуск при старте системы
* Перезапуски
* Репликация (количество запущенных процессов)
* Память
* Предыдущие шаги перед запуском

Я расскажу вам больше о каждой из этих концепций, о том, как их воспринимать, и дам конкретные примеры стратегий для работы с ними в следующих главах. 🚀
