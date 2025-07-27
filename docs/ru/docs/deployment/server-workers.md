# Серверные Рабочие Процессы - Uvicorn с Рабочими Процессами

Давайте вспомним те концепции развёртывания, которые мы обсуждали ранее:

* Безопасность - HTTPS
* Запуск при старте
* Перезапуски
* **Репликация (количество запущенных процессов)**
* Память
* Предыдущие шаги перед запуском

До этого момента, с помощью всех руководств в документации, вы, вероятно, запускали **серверную программу**, например, используя команду `fastapi`, которая запускает Uvicorn, выполняющую **один процесс**.

При развертывании приложений, вероятно, вы захотите иметь **репликацию процессов**, чтобы воспользоваться преимуществами **множества ядер** и быть способными обрабатывать больше запросов.

Как вы узнали в предыдущей главе о [Концепции Развёртывания](concepts.md){.internal-link target=_blank}, существует множество стратегий, которые можно использовать.

Здесь я покажу вам, как использовать **Uvicorn** с **рабочими процессами**, используя команду `fastapi` или напрямую команду `uvicorn`.

/// info | Информация

Если вы используете контейнеры, например с Docker или Kubernetes, я расскажу вам больше об этом в следующей главе: [FastAPI в Контейнерах - Docker](docker.md){.internal-link target=_blank}.

Особенно при запуске на **Kubernetes** вы, вероятно, **не захотите** использовать рабочих процессы и вместо этого запускать **один процесс Uvicorn на контейнер**, но я расскажу вам о этом позже в той главе.

///

## Несколько Рабочих Процессов

Вы можете запустить несколько рабочих процессов с помощью опции командной строки `--workers`:

//// tab | `fastapi`

Если вы используете команду `fastapi`:

<div class="termy">

```console
$ <font color="#4E9A06">fastapi</font> run --workers 4 <u style="text-decoration-style:solid">main.py</u>

  <span style="background-color:#009485"><font color="#D3D7CF"> FastAPI </font></span>  Запуск производственного сервера 🚀

             Поиск структуры файлов пакета в директориях с
             <font color="#3465A4">__init__.py</font> файлами
             Импорт из <font color="#75507B">/home/user/code/</font><font color="#AD7FA8">awesomeapp</font>

   <span style="background-color:#007166"><font color="#D3D7CF"> module </font></span>  🐍 main.py

     <span style="background-color:#007166"><font color="#D3D7CF"> code </font></span>  Импорт объекта приложения FastAPI из модуля с
             следующим кодом:

             <u style="text-decoration-style:solid">from </u><u style="text-decoration-style:solid"><b>main</b></u><u style="text-decoration-style:solid"> import </u><u style="text-decoration-style:solid"><b>app</b></u>

      <span style="background-color:#007166"><font color="#D3D7CF"> app </font></span>  Используется строка импорта: <font color="#3465A4">main:app</font>

   <span style="background-color:#007166"><font color="#D3D7CF"> server </font></span>  Сервер запущен на <font color="#729FCF"><u style="text-decoration-style:solid">http://0.0.0.0:8000</u></font>
   <span style="background-color:#007166"><font color="#D3D7CF"> server </font></span>  Документация на <font color="#729FCF"><u style="text-decoration-style:solid">http://0.0.0.0:8000/docs</u></font>

             Логи:

     <span style="background-color:#007166"><font color="#D3D7CF"> INFO </font></span>  Uvicorn работает на <font color="#729FCF"><u style="text-decoration-style:solid">http://0.0.0.0:8000</u></font> <b>(</b>Нажмите CTRL+C для
             выхода<b>)</b>
     <span style="background-color:#007166"><font color="#D3D7CF"> INFO </font></span>  Запущен родительский процесс <b>[</b><font color="#34E2E2"><b>27365</b></font><b>]</b>
     <span style="background-color:#007166"><font color="#D3D7CF"> INFO </font></span>  Запущен процесс сервера <b>[</b><font color="#34E2E2"><b>27368</b></font><b>]</b>
     <span style="background-color:#007166"><font color="#D3D7CF"> INFO </font></span>  Запущен процесс сервера <b>[</b><font color="#34E2E2"><b>27369</b></font><b>]</b>
     <span style="background-color:#007166"><font color="#D3D7CF"> INFO </font></span>  Запущен процесс сервера <b>[</b><font color="#34E2E2"><b>27370</b></font><b>]</b>
     <span style="background-color:#007166"><font color="#D3D7CF"> INFO </font></span>  Запущен процесс сервера <b>[</b><font color="#34E2E2"><b>27367</b></font><b>]</b>
     <span style="background-color:#007166"><font color="#D3D7CF"> INFO </font></span>  Ожидание запуска приложения.
     <span style="background-color:#007166"><font color="#D3D7CF"> INFO </font></span>  Ожидание запуска приложения.
     <span style="background-color:#007166"><font color="#D3D7CF"> INFO </font></span>  Ожидание запуска приложения.
     <span style="background-color:#007166"><font color="#D3D7CF"> INFO </font></span>  Ожидание запуска приложения.
     <span style="background-color:#007166"><font color="#D3D7CF"> INFO </font></span>  Запуск приложения завершен.
     <span style="background-color:#007166"><font color="#D3D7CF"> INFO </font></span>  Запуск приложения завершен.
     <span style="background-color:#007166"><font color="#D3D7CF"> INFO </font></span>  Запуск приложения завершен.
     <span style="background-color:#007166"><font color="#D3D7CF"> INFO </font></span>  Запуск приложения завершен.
```

</div>

////

//// tab | `uvicorn`

Если вы предпочитаете использовать команду `uvicorn` напрямую:

<div class="termy">

```console
$ uvicorn main:app --host 0.0.0.0 --port 8080 --workers 4
<font color="#A6E22E">INFO</font>:     Uvicorn работает на <b>http://0.0.0.0:8080</b> (Нажмите CTRL+C для выхода)
<font color="#A6E22E">INFO</font>:     Запущен родительский процесс [<font color="#A1EFE4"><b>27365</b></font>]
<font color="#A6E22E">INFO</font>:     Запущен процесс сервера [<font color="#A1EFE4">27368</font>]
<font color="#A6E22E">INFO</font>:     Ожидание запуска приложения.
<font color="#A6E22E">INFO</font>:     Запуск приложения завершен.
<font color="#A6E22E">INFO</font>:     Запущен процесс сервера [<font color="#A1EFE4">27369</font>]
<font color="#A6E22E">INFO</font>:     Ожидание запуска приложения.
<font color="#A6E22E">INFO</font>:     Запуск приложения завершен.
<font color="#A6E22E">INFO</font>:     Запущен процесс сервера [<font color="#A1EFE4">27370</font>]
<font color="#A6E22E">INFO</font>:     Ожидание запуска приложения.
<font color="#A6E22E">INFO</font>:     Запуск приложения завершен.
<font color="#A6E22E">INFO</font>:     Запущен процесс сервера [<font color="#A1EFE4">27367</font>]
<font color="#A6E22E">INFO</font>:     Ожидание запуска приложения.
<font color="#A6E22E">INFO</font>:     Запуск приложения завершен.
```

</div>

////

Единственный новый параметр здесь - это `--workers`, который говорит Uvicorn запустить 4 рабочих процесса.

Вы также можете видеть, что он показывает **PID** каждого процесса, `27365` для родительского процесса (это **менеджер процессов**) и один для каждого рабочего процесса: `27368`, `27369`, `27370` и `27367`.

## Концепции Развёртывания

Здесь вы увидели, как использовать несколько **рабочих процессов** для **параллелизации** выполнения приложения, использования преимуществ **нескольких ядер** процессора и возможности обслуживать **больше запросов**.

Из списка концепций развёртывания, используя рабочие процессы, вы в основном поможете с частью **репликации** и немного с **перезапусками**, но вы все равно должны позаботиться о других:

* **Безопасность - HTTPS**
* **Запуск при старте**
* ***Перезапуски***
* Репликация (количество запущенных процессов)
* **Память**
* **Предыдущие шаги перед запуском**

## Контейнеры и Docker

В следующей главе о [FastAPI в Контейнерах - Docker](docker.md){.internal-link target=_blank} я объясню некоторые стратегии, которые вы могли бы использовать для обработки других **концепций развёртывания**.

Я покажу вам, как **создать свое собственное изображение с нуля**, чтобы запустить единый Uvicorn процесс. Это простой процесс и, вероятно, то, что вы захотите сделать, когда используете распределенную систему управления контейнерами, такую как **Kubernetes**.

## Итоги

Вы можете использовать несколько рабочих процессов с помощью опции CLI `--workers` с командами `fastapi` или `uvicorn`, чтобы воспользоваться преимуществами **многоядерных процессоров**, для параллельного выполнения **нескольких процессов**.

Вы могли бы использовать эти инструменты и идеи, если вы настраиваете **свою собственную систему развёртывания**, при этом самостоятельно заботясь о других концепциях развёртывания.

Ознакомьтесь с следующей главой, чтобы узнать о **FastAPI** с контейнерами (например, Docker и Kubernetes). Вы увидите, что у этих инструментов есть простые способы решения других **концепций развёртывания**. ✨
