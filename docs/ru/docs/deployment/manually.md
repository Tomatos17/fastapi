# Запуск сервера вручную

## Использование команды `fastapi run`

Коротко говоря, используйте `fastapi run`, чтобы запустить ваше приложение FastAPI:

<div class="termy">

```console
$ <font color="#4E9A06">fastapi</font> run <u style="text-decoration-style:solid">main.py</u>

  <span style="background-color:#009485"><font color="#D3D7CF"> FastAPI </font></span>  Запуск серверной программы для продакшена 🚀

             Поиск структуры файлов пакета из директорий
             с файлами <font color="#3465A4">__init__.py</font>
             Импорт из <font color="#75507B">/home/user/code/</font><font color="#AD7FA8">awesomeapp</font>

   <span style="background-color:#007166"><font color="#D3D7CF"> module </font></span>  🐍 main.py

     <span style="background-color:#007166"><font color="#D3D7CF"> code </font></span>  Импорт объект приложения FastAPI из модуля при помощи
             следующего кода:

             <u style="text-decoration-style:solid">from </u><u style="text-decoration-style:solid"><b>main</b></u><u style="text-decoration-style:solid"> import </u><u style="text-decoration-style:solid"><b>app</b></u>

      <span style="background-color:#007166"><font color="#D3D7CF"> app </font></span>  Использование строки импорта: <font color="#3465A4">main:app</font>

   <span style="background-color:#007166"><font color="#D3D7CF"> server </font></span>  Сервер запущен на <font color="#729FCF"><u style="text-decoration-style:solid">http://0.0.0.0:8000</u></font>
   <span style="background-color:#007166"><font color="#D3D7CF"> server </font></span>  Документация доступна по адресу <font color="#729FCF"><u style="text-decoration-style:solid">http://0.0.0.0:8000/docs</u></font>

             Логи:

     <span style="background-color:#007166"><font color="#D3D7CF"> INFO </font></span> Запущен серверный процесс <b>[</b><font color="#34E2E2"><b>2306215</b></font><b>]</b>
     <span style="background-color:#007166"><font color="#D3D7CF"> INFO </font></span> Ожидание запуска приложения.
     <span style="background-color:#007166"><font color="#D3D7CF"> INFO </font></span> Запуск приложения завершён.
     <span style="background-color:#007166"><font color="#D3D7CF"> INFO </font></span> Uvicorn работает на <font color="#729FCF"><u style="text-decoration-style:solid">http://0.0.0.0:8000</u></font> <b>(</b>нажмите CTRL+C
             для завершения<b>)</b>
```

</div>

Это подойдёт для большинства случаев. 😎

Вы можете использовать эту команду, чтобы например запустить ваше **FastAPI**-приложение в контейнере, на сервере и т.д.

## ASGI-сервера

Давайте углубимся в детали.

FastAPI использует стандарт для создания Python веб-фреймворков и серверов, называемый <abbr title="Asynchronous Server Gateway Interface">ASGI</abbr>. FastAPI — это ASGI веб-фреймворк.

Основное, что вам нужно для запуска **FastAPI** приложения (или любого другого ASGI приложения) на удалённой серверной машине — это программа ASGI сервера, такая как **Uvicorn**, именно она используется по умолчанию в команде `fastapi`.

Среди альтернатив:

* <a href="https://www.uvicorn.org/" class="external-link" target="_blank">Uvicorn</a>: высокопроизводительный ASGI сервер.
* <a href="https://hypercorn.readthedocs.io/" class="external-link" target="_blank">Hypercorn</a>: ASGI сервер, поддерживающий HTTP/2 и Trio среди прочего.
* <a href="https://github.com/django/daphne" class="external-link" target="_blank">Daphne</a>: ASGI сервер, созданный для Django Channels.
* <a href="https://github.com/emmett-framework/granian" class="external-link" target="_blank">Granian</a>: HTTP сервер на Rust для Python приложений.
* <a href="https://unit.nginx.org/howto/fastapi/" class="external-link" target="_blank">NGINX Unit</a>: лёгкая и многофункциональная среда выполнения веб-приложений от NGINX.

## Сервер как машина и сервер как программа

Есть небольшая деталь о названиях, которую нужно иметь в виду. 💡

Слово "**сервер**" обычно используется для обозначения как удалённого/облачного компьютера (физическая или виртуальная машина), так и программы, запущенной на этой машине (например, Uvicorn).

Просто помните, что когда вы видите "сервер" в общем случае, это может обозначать что-то из этих двух вещей.

Когда речь идёт о удалённой машине, её часто называют **сервер**, но также **машина**, **ВМ** (виртуальная машина), **нода**. Все они относятся к каким-то удалённым машинам, обычно под управлением Linux, на которых вы запускаете программы.

## Установка программы сервера

Когда вы устанавливаете FastAPI, он поставляется с сервером для продакшена, Uvicorn, и вы можете запустить его с помощью команды `fastapi run`.

Но вы также можете установить ASGI-сервер вручную.

Убедитесь, что вы создали [виртуальное окружение](../virtual-environments.md){.internal-link target=_blank}, активировали его, и тогда можете установить серверное приложение.

Например, чтобы установить Uvicorn:

<div class="termy">

```console
$ pip install "uvicorn[standard]"

---> 100%
```

</div>

Аналогичный процесс будет применен для любой другой программы ASGI сервера.

/// tip | Подсказка

Добавив `standard`, Uvicorn установит и будет использовать некоторые рекомендованные дополнительные зависимости.

Среди них `uvloop`, высокопроизводительная замена для `asyncio`, которая предоставляет значительное увеличение производительности при использовании асинхронности.

Когда вы устанавливаете FastAPI чем-то вроде `pip install "fastapi[standard]"`, вы также получаете `uvicorn[standard]`.

///

## Запуск программы сервера

Если вы установили ASGI-сервер вручную, вам обычно нужно будет передать строку импорта в специальном формате, чтобы он импортировал ваше FastAPI-приложение:

<div class="termy">

```console
$ uvicorn main:app --host 0.0.0.0 --port 80

<span style="color: green;">INFO</span>:     Uvicorn running on http://0.0.0.0:80 (Press CTRL+C to quit)
```

</div>

/// note | Примечание

Команда `uvicorn main:app` относится к:

* `main`: файл `main.py` (Python "модуль").
* `app`: объект, созданный внутри `main.py` строкой `app = FastAPI()`.

Это эквивалентно:

```Python
from main import app
```

///

Каждая альтернативная программа ASGI сервера будет иметь аналогичную команду, вы можете узнать больше в их соответствующей документации.

/// warning | Предупреждение

Uvicorn и другие серверы поддерживают опцию `--reload`, которая полезна во время разработки.

Опция `--reload` потребляет значительно больше ресурсов, более нестабильна и т.д.

Она очень полезна во время **разработки**, но **не следует** использовать её в **продакшене**.

///

## Концепции развёртывания

В этих примерах выполняется запуск серверной программы (например, Uvicorn), создавая **один процесс**, который слушает на всех IP (`0.0.0.0`) на предустановленном порту (например, `80`).

Это базовая идея. Но, вероятно, вам захочется позаботиться о некоторых дополнительных вещах, таких как:

* Безопасность - HTTPS
* Запуск при старте системы
* Перезапуски
* Репликация (число запущенных процессов)
* Память
* Предыдущие шаги перед стартом

Я расскажу вам больше о каждой из этих концепций, как их рассматривать и приведу конкретные примеры стратегий для их решения в следующих главах. 🚀
