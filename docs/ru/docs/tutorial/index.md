# Учебник - Руководство пользователя

Этот учебник показывает, как использовать **FastAPI** со многими его функциями, шаг за шагом.

Каждый раздел постепенно опирается на предыдущие, но структура разбита на отдельные темы, чтобы вы могли перейти прямо к любой конкретной теме для решения своих специфичных нужд API.

Он также создан для использования в качестве справочной информации в будущем, чтобы вы могли возвращаться и находить именно то, что вам нужно.

## Запуск кода

Все блоки кода можно копировать и использовать напрямую (это действительно проверенные файлы Python).

Чтобы запустить любой из примеров, скопируйте код в файл `main.py` и запустите `fastapi dev` с помощью:

<div class="termy">

```console
$ <font color="#4E9A06">fastapi</font> dev <u style="text-decoration-style:solid">main.py</u>

  <span style="background-color:#009485"><font color="#D3D7CF"> FastAPI </font></span>  Начало работы сервера разработки 🚀

             Поиск структуры файлов пакета в каталогах
             с файлами <font color="#3465A4">__init__.py</font>
             Импорт из <font color="#75507B">/home/user/code/</font><font color="#AD7FA8">awesomeapp</font>

   <span style="background-color:#007166"><font color="#D3D7CF"> module </font></span>  🐍 main.py

     <span style="background-color:#007166"><font color="#D3D7CF"> code </font></span>  Импорт объекта приложения FastAPI из модуля со
             следующим кодом:

             <u style="text-decoration-style:solid">from </u><u style="text-decoration-style:solid"><b>main</b></u><u style="text-decoration-style:solid"> import </u><u style="text-decoration-style:solid"><b>app</b></u>

      <span style="background-color:#007166"><font color="#D3D7CF"> app </font></span>  Использование строки импорта: <font color="#3465A4">main:app</font>

   <span style="background-color:#007166"><font color="#D3D7CF"> server </font></span>  Сервер запущен на <font color="#729FCF"><u style="text-decoration-style:solid">http://127.0.0.1:8000</u></font>
   <span style="background-color:#007166"><font color="#D3D7CF"> server </font></span>  Документация доступна по адресу <font color="#729FCF"><u style="text-decoration-style:solid">http://127.0.0.1:8000/docs</u></font>

      <span style="background-color:#007166"><font color="#D3D7CF"> tip </font></span>  Запущен в режиме разработки, для продакшена используйте:
             <b>fastapi run</b>

             Логи:

     <span style="background-color:#007166"><font color="#D3D7CF"> INFO </font></span>  Будет отслеживать изменения в этих каталогах:
             <b>[</b><font color="#4E9A06">&apos;/home/user/code/awesomeapp&apos;</font><b>]</b>
     <span style="background-color:#007166"><font color="#D3D7CF"> INFO </font></span>  Uvicorn запущен на <font color="#729FCF"><u style="text-decoration-style:solid">http://127.0.0.1:8000</u></font> <b>(</b>нажмите CTRL+C
             для выхода<b>)</b>
     <span style="background-color:#007166"><font color="#D3D7CF"> INFO </font></span>  Запущен процесс автоперезагрузки <b>[</b><font color="#34E2E2"><b>383138</b></font><b>]</b> с использованием WatchFiles
     <span style="background-color:#007166"><font color="#D3D7CF"> INFO </font></span>  Запущен процесс сервера <b>[</b><font color="#34E2E2"><b>383153</b></font><b>]</b>
     <span style="background-color:#007166"><font color="#D3D7CF"> INFO </font></span>  Ожидание запуска приложения.
     <span style="background-color:#007166"><font color="#D3D7CF"> INFO </font></span>  Запуск приложения завершен.
```

</div>

**Настоятельно рекомендуется** написать или скопировать код, отредактировать его и запустить локально.

Использование кода в вашем редакторе действительно показывает вам преимущества FastAPI, видя, как мало кода вам нужно написать, все проверки типов, автодополнение и т.д.

---

## Установка FastAPI

Первый шаг — установить FastAPI.

Убедитесь, что вы создали [виртуальную среду](../virtual-environments.md){.internal-link target=_blank}, активировали ее, а затем **установили FastAPI**:

<div class="termy">

```console
$ pip install "fastapi[standard]"

---> 100%
```

</div>

/// note | Примечание

При установке с помощью `pip install "fastapi[standard]"` поставляются некоторые стандартные дополнительные зависимости, включая `fastapi-cloud-cli`, который позволяет развертывать приложения на <a href="https://fastapicloud.com" class="external-link" target="_blank">FastAPI Cloud</a>.

Если вы не хотите иметь эти необязательные зависимости, вы можете установить `pip install fastapi`.

Если вы хотите установить стандартные зависимости, но без `fastapi-cloud-cli`, вы можете установить с помощью `pip install "fastapi[standard-no-fastapi-cloud-cli]"`.

///

## Продвинутое руководство пользователя

Существует также **Продвинутое руководство пользователя**, которое вы можете прочитать после **Учебника - Руководства пользователя**.

**Продвинутое руководство пользователя** основывается на этом, использует те же концепции и обучает вас некоторым дополнительным функциям.

Но сначала вам следует прочитать **Учебник - Руководство пользователя** (то, что вы читаете прямо сейчас).

Он разработан так, чтобы вы могли создать полноценное приложение, используя только **Учебник - Руководство пользователя**, а затем расширить его различными способами, в зависимости от ваших нужд, с использованием некоторых дополнительных идей из **Продвинутого руководства пользователя**.
