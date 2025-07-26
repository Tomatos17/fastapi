# Query-Parameter-Modelle

Wenn Sie eine Gruppe von **Query-Parametern** haben, die in Zusammenhang stehen, können Sie ein **Pydantic-Modell** erstellen, um sie zu deklarieren.

Dadurch können Sie das **Modell** an **mehreren Stellen wiederverwenden** und auch Validierungen und Metadaten für alle Parameter auf einmal deklarieren. 😎

/// note | Hinweis

Dies wird seit FastAPI-Version `0.115.0` unterstützt. 🤓

///

## Query-Parameter mit einem Pydantic-Modell

Deklarieren Sie die benötigten **Query-Parameter** in einem **Pydantic-Modell** und deklarieren Sie dann den Parameter als `Query`:

{* ../../docs_src/query_param_models/tutorial001_an_py310.py hl[9:13,17] *}

**FastAPI** wird die Daten für **jedes Feld** aus den **Query-Parametern** der Anfrage **extrahieren** und Ihnen das von Ihnen definierte Pydantic-Modell übergeben.

## Überprüfen Sie die Dokumentation

Sie können die Query-Parameter in der Dokumentationsoberfläche unter `/docs` sehen:

<div class="screenshot">
<img src="/img/tutorial/query-param-models/image01.png">
</div>

## Zusätzliche Query-Parameter verbieten

In einigen speziellen Anwendungsfällen (wahrscheinlich nicht sehr häufig) möchten Sie möglicherweise die Query-Parameter, die Sie empfangen möchten, **einschränken**.

Sie können die Modellkonfiguration von Pydantic verwenden, um `extra` Felder zu `verbieten`:

{* ../../docs_src/query_param_models/tutorial002_an_py310.py hl[10] *}

Wenn ein Client versucht, einige **zusätzliche** Daten in den **Query-Parametern** zu senden, erhält er eine **Error-Response**.

Wenn der Client beispielsweise versucht, einen `tool` Query-Parameter mit einem Wert von `plumbus` zu senden, wie:

```http
https://example.com/items/?limit=10&tool=plumbus
```

wird er eine **Error-Response** erhalten, die ihm mitteilt, dass der Query-Parameter `tool` nicht erlaubt ist:

```json
{
    "detail": [
        {
            "type": "extra_forbidden",
            "loc": ["query", "tool"],
            "msg": "Extra inputs are not permitted",
            "input": "plumbus"
        }
    ]
}
```

## Zusammenfassung

Sie können **Pydantic-Modelle** verwenden, um **Query-Parameter** in **FastAPI** zu deklarieren. 😎

/// tip | Tipp

Spoiler-Alarm: Sie können auch Pydantic-Modelle verwenden, um Cookies und Header zu deklarieren, aber darüber werden Sie später im Tutorial lesen. 🤫

///
