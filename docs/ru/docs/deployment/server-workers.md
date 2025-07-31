# Воркеры сервера - Uvicorn с воркерами

Давайте снова рассмотрим концепции деплоя:

* Безопасность - HTTPS
* Запуск при старте
* Перезапуски
* **Репликация (количество рабочих процессов)**
* Память
* Подготовительные шаги перед запуском

До этого момента, с помощью всех туториалов в документации, вы, вероятно, запускали **серверную программу**, например, используя команду `fastapi`, которая запускает Uvicorn, выполняя **единственный процесс**.

При деплое приложений вы, вероятно, захотите иметь некоторую **репликацию процессов**, чтобы воспользоваться преимуществами **многих ядер** и иметь возможность обрабатывать больше запросов.

Как вы видели в предыдущей главе о [Концепции деплоя](concepts.md){.internal-link target=_blank}, существует множество стратегий, которые вы можете использовать.

Здесь я покажу вам, как использовать **Uvicorn** с **воркер-процессами**, используя команду `fastapi` или непосредственно команду `uvicorn`.

/// info | Информация

Если вы используете контейнеры, например, с Docker или Kubernetes, я расскажу вам больше об этом в следующей главе: [FastAPI в контейнерах - Docker](docker.md){.internal-link target=_blank}.

В частности, работая с **Kubernetes**, вы, вероятно, **не** захотите использовать воркеры, а вместо этого запускать **один процесс Uvicorn в контейнере**, но об этом я расскажу позже в той главе.

///

## Несколько воркеров

Вы можете запустить несколько воркеров, используя опцию командной строки `--workers`:

//// tab | `fastapi`

Если вы используете команду `fastapi`:

<div class="termy">

```console
$ <font color="#4E9A06">fastapi</font> run --workers 4 <u style="text-decoration-style:solid">main.py</u>

  <span style="background-color:#009485"><font color="#D3D7CF"> FastAPI </font></span>  Запуск продакшн-сервера 🚀

             Поиск структуры файлов пакета в директориях с
             <font color="#3465A4">__init__.py</font>
             Импорт из <font color="#75507B">/home/user/code/</font><font color="#AD7FA8">awesomeapp</font>

   <span style="background-color:#007166"><font color="#D3D7CF"> module </font></span>  🐍 main.py

     <span style="background-color:#007166"><font color="#D3D7CF"> code </font></span>  Импортирование объекта приложения FastAPI из модуля со следующим кодом:

             <u style="text-decoration-style:solid">from </u><u style="text-decoration-style:solid"><b>main</b></u><u style="text-decoration-style:solid"> import </u><u style="text-decoration-style:solid"><b>app</b></u>

      <span style="background-color:#007166"><font color="#D3D7CF"> app </font></span>  Использование строки импорта: <font color="#3465A4">main:app</font>

   <span style="background-color:#007166"><font color="#D3D7CF"> server </font></span>  Сервер стартовал на <font color="#729FCF"><u style="text-decoration-style:solid">http://0.0.0.0:8000</u></font>
   <span style="background-color:#007166"><font color="#D3D7CF"> server </font></span>  Документация по адресу <font color="#729FCF"><u style="text-decoration-style:solid">http://0.0.0.0:8000/docs</u></font>

             Логи:

     <span style="background-color:#007166"><font color="#D3D7CF"> INFO </font></span>  Uvicorn работает на <font color="#729FCF"><u style="text-decoration-style:solid">http://0.0.0.0:8000</u></font> <b>(</b>Нажмите CTRL+C для выхода<b>)</b>
     <span style="background-color:#007166"><font color="#D3D7CF"> INFO </font></span>  Стартовал родительский процесс <b>[</b><font color="#34E2E2"><b>27365</b></font><b>]</b>
     <span style="background-color:#007166"><font color="#D3D7CF"> INFO </font></span>  Стартовал серверный процесс <b>[</b><font color="#34E2E2"><b>27368</b></font><b>]</b>
     <span style="background-color:#007166"><font color="#D3D7CF"> INFO </font></span>  Стартовал серверный процесс <b>[</b><font color="#34E2E2"><b>27369</b></font><b>]</b>
     <span style="background-color:#007166"><font color="#D3D7CF"> INFO </font></span>  Стартовал серверный процесс <b>[</b><font color="#34E2E2"><b>27370</b></font><b>]</b>
     <span style="background-color:#007166"><font color="#D3D7CF"> INFO </font></span>  Стартовал серверный процесс <b>[</b><font color="#34E2E2"><b>27367</b></font><b>]</b>
     <span style="background-color:#007166"><font color="#D3D7CF"> INFO </font></span>  Ожидание запуска приложения.
     <span style="background-color:#007166"><font color="#D3D7CF"> INFO </font></span>  Ожидание запуска приложения.
     <span style="background-color:#007166"><font color="#D3D7CF"> INFO </font></span>  Ожидание запуска приложения.
     <span style="background-color:#007166"><font color="#D3D7CF"> INFO </font></span>  Ожидание запуска приложения.
     <span style="background-color:#007166"><font color="#D3D7CF"> INFO </font></span>  Запуск приложения завершён.
     <span style="background-color:#007166"><font color="#D3D7CF"> INFO </font></span>  Запуск приложения завершён.
     <span style="background-color:#007166"><font color="#D3D7CF"> INFO </font></span>  Запуск приложения завершён.
     <span style="background-color:#007166"><font color="#D3D7CF"> INFO </font></span>  Запуск приложения завершён.
```

</div>

////

//// tab | `uvicorn`

Если вы предпочитаете использовать команду `uvicorn` напрямую:

<div class="termy">

```console
$ uvicorn main:app --host 0.0.0.0 --port 8080 --workers 4
<font color="#A6E22E">INFO</font>:     Uvicorn работает на <b>http://0.0.0.0:8080</b> (Нажмите CTRL+C для выхода)
<font color="#A6E22E">INFO</font>:     Стартовал родительский процесс [<font color="#A1EFE4"><b>27365</b></font>]
<font color="#A6E22E">INFO</font>:     Стартовал серверный процесс [<font color="#A1EFE4">27368</font>]
<font color="#A6E22E">INFO</font>:     Ожидание запуска приложения.
<font color="#A6E22E">INFO</font>:     Запуск приложения завершён.
<font color="#A6E22E">INFO</font>:     Стартовал серверный процесс [<font color="#A1EFE4">27369</font>]
<font color="#A6E22E">INFO</font>:     Ожидание запуска приложения.
<font color="#A6E22E">INFO</font>:     Запуск приложения завершён.
<font color="#A6E22E">INFO</font>:     Стартовал серверный процесс [<font color="#A1EFE4">27370</font>]
<font color="#A6E22E">INFO</font>:     Ожидание запуска приложения.
<font color="#A6E22E">INFO</font>:     Запуск приложения завершён.
<font color="#A6E22E">INFO</font>:     Стартовал серверный процесс [<font color="#A1EFE4">27367</font>]
<font color="#A6E22E">INFO</font>:     Ожидание запуска приложения.
<font color="#A6E22E">INFO</font>:     Запуск приложения завершён.
```

</div>

////

Единственная новая опция здесь - `--workers`, указывающая Uvicorn запустить 4 воркер-процесса.

Вы также можете увидеть, что отображается **PID** каждого процесса: `27365` для родительского процесса (это **менеджер процессов**) и один для каждого воркер-процесса: `27368`, `27369`, `27370` и `27367`.

## Концепции деплоя

Здесь вы увидели, как использовать несколько **воркеров** для **параллелизации** выполнения приложения, использовать преимущества **многих ядер** процессора и иметь возможность обрабатывать **больше запросов**.

Из списка концепций деплоя, приведённого выше, использование воркеров в основном поможет с **репликацией**, и немного - с **перезапусками**, но вам по-прежнему необходимо позаботиться о следующих вещах:

* **Безопасность - HTTPS**
* **Запуск при старте**
* ***Перезапуски***
* Репликация (количество рабочих процессов)
* **Память**
* **Подготовительные шаги перед запуском**

## Контейнеры и Docker

В следующей главе о [FastAPI в контейнерах - Docker](docker.md){.internal-link target=_blank} я объясню некоторые стратегии, которые вы можете использовать для работы с другими **концепциями деплоя**.

Я покажу вам, как **создать собственный образ с нуля** для запуска одного процесса Uvicorn. Это простой процесс и, вероятно, то, что вы захотите сделать при использовании системы управления распределёнными контейнерами, такой как **Kubernetes**.

## Итог

Вы можете использовать несколько воркер-процессов с опцией `--workers` в CLI с командами `fastapi` или `uvicorn`, чтобы воспользоваться преимуществами **многоядерных процессоров**, для выполнения **нескольких процессов параллельно**.

Вы можете использовать эти инструменты и идеи, если настраиваете **собственную систему деплоя**, одновременно заботясь о других концепциях деплоя самостоятельно.

Изучите следующую главу, чтобы узнать о **FastAPI** с контейнерами (например, Docker и Kubernetes). Вы увидите, что эти инструменты также имеют простые способы решения других **концепций деплоя**. ✨
