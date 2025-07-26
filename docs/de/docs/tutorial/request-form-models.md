# Formularmodelle

Sie können **Pydantic-Modelle** verwenden, um **Formularfelder** in FastAPI zu deklarieren.

/// info | Hinweis

Um Formulare zu verwenden, installieren Sie zuerst <a href="https://github.com/Kludex/python-multipart" class="external-link" target="_blank">`python-multipart`</a>.

Stellen Sie sicher, dass Sie eine [virtuelle Umgebung](../virtual-environments.md){.internal-link target=_blank} erstellen, diese aktivieren und dann das Paket installieren, zum Beispiel:

```console
$ pip install python-multipart
```

///

/// note | Hinweis

Dies wird seit FastAPI Version `0.113.0` unterstützt. 🤓

///

## Pydantic-Modelle für Formulare

Sie müssen lediglich ein **Pydantic-Modell** mit den Feldern deklarieren, die Sie als **Formularfelder** empfangen möchten, und dann den Parameter als `Form` deklarieren:

{* ../../docs_src/request_form_models/tutorial001_an_py39.py hl[9:11,15] *}

**FastAPI** wird die Daten für **jedes Feld** aus den **Formulardaten** in der Anfrage **extrahieren** und Ihnen das von Ihnen definierte Pydantic-Modell zurückgeben.

## Überprüfen Sie die Dokumentation

Sie können dies in der Dokumentationsoberfläche unter `/docs` überprüfen:

<div class="screenshot">
<img src="/img/tutorial/request-form-models/image01.png">
</div>

## Zusätzliche Formularfelder verbieten

In einigen besonderen Anwendungsfällen (wahrscheinlich nicht sehr häufig) möchten Sie möglicherweise die Formularfelder auf nur die im Pydantic-Modell deklarierten Felder **beschränken**. Und jegliche **zusätzlichen** Felder **verbieten**.

/// note | Hinweis

Dies wird seit FastAPI Version `0.114.0` unterstützt. 🤓

///

Sie können die Modellkonfiguration von Pydantic verwenden, um `extra` Felder zu `verbieten`:

{* ../../docs_src/request_form_models/tutorial002_an_py39.py hl[12] *}

Wenn ein Client versucht, einige zusätzliche Daten zu senden, erhält er eine **Error-Response**.

Zum Beispiel, wenn der Client versucht, die folgenden Formularfelder zu senden:

* `username`: `Rick`
* `password`: `Portal Gun`
* `extra`: `Mr. Poopybutthole`

Er wird eine Fehlerantwort erhalten, die ihm mitteilt, dass das Feld `extra` nicht erlaubt ist:

```json
{
    "detail": [
        {
            "type": "extra_forbidden",
            "loc": ["body", "extra"],
            "msg": "Extra inputs are not permitted",
            "input": "Mr. Poopybutthole"
        }
    ]
}
```

## Zusammenfassung

Sie können Pydantic-Modelle verwenden, um Formularfelder in FastAPI zu deklarieren. 😎
