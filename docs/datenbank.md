# 🗄️ Brauche ich eine Datenbank? Niederschwellig zuerst

Kurz: **Meistens brauchst du keine externe Datenbank.** Wähle danach, *wo die Daten leben*:

| Fall | Lösung | Setup-Aufwand |
|------|--------|---------------|
| Daten gehören zu einem **n8n-Workflow** | **n8n Data Tables** | ⭐ null (eingebaut) |
| **Veröffentlichte App, Login, Dateien, Vektoren** | **TCF-Supabase** (Keys im Zugangsbereich) | gering (Keys eintragen) |
| **Lokaler Prototyp / ein Backend-Prozess mit Volume** | **SQLite** | null (Datei) |

Zugangsdaten für die gemeinsamen Bausteine stehen im Bootcamp-Zugangsbereich: **[tcf.buildbar.de/#zugang](https://tcf.buildbar.de/#zugang)**.

---

## 1. n8n Data Tables: Standard für Workflows (null Setup)

In n8n **eingebaut**, auch in eurer n8n in one.intelligence. Keine Anmeldung, kein Connection-String, kein eigener Server.

- Tabellen mit Spalten anlegen, aus Workflows **lesen, schreiben, aktualisieren, löschen** (Node **„Data Table"**) oder von Claude per MCP (`n8n_manage_datatable`).
- Auf n8n Cloud gilt ein **Gesamtlimit von 50 MB** (alle Tabellen zusammen); für Bootcamp-Mengen reichlich.
- Ideal für: Nachschlagelisten, Status merken, kleine Listen, Duplikate erkennen, Zwischenspeicher.
- **Eigenes Kürzel:** Gib deinen Tabellen ein **eigenes Kürzel** (z. B. `mk_anfragen`). Der Speicher für Data Tables gilt für die ganze n8n, deshalb keine großen Datenmengen und keine Dateien.
- Sag zu Claude: *„Leg eine Data Table `mk_anfragen` mit den Spalten name, email, status an und schreib im Workflow neue Einträge hinein."*
- Winziger Zustand ohne Tabelle: n8n **workflow static data** (Schlüssel-Werte).

### ⚠️ Zwei stille Zeilendeckel (gemessen am 19.09.2026)

Beide melden **keinen Fehler**. Der Workflow läuft grün durch und verarbeitet trotzdem nur einen
Bruchteil der Daten.

| Wo | Was passiert |
|---|---|
| **Data-Table-Node** | Liefert bei `limit: 2000` genau **50 Zeilen**. Sie fällt still auf ihren Default zurück. |
| **n8n-API** | Nimmt höchstens `limit=200`. Bei 500 antwortet sie mit **0 Zeilen**, ohne Fehler und ohne Cursor. |

**Immer die Zeilenzahl gegen die Tabelle prüfen.** Wenn die Tabelle 1631 Zeilen hat und der Node
50 liefert, ist das kein Zufall.

**Ab etwa 50 Zeilen: über die API blättern.** Ein HTTP-Request-Node mit Cursor-Paginierung holt
alles. Dafür brauchst du in n8n eine Credential vom Typ `httpHeaderAuth` mit dem Namen
`X-N8N-API-KEY` und einem n8n-API-Key als Wert. Den legst du in deiner n8n an (Einstellungen,
„n8n API“), am besten einen eigenen nur für diesen Zweck.

```
URL    https://n8n.oi.destination.one/api/v1/data-tables/<TABELLEN-ID>/rows
Query  limit = 200
Options -> Pagination
  Pagination Mode        Update a Parameter in Each Request
  Parameter (Query)      cursor = {{ $response.body.nextCursor }}
  Pagination Complete    Other
  Complete Expression    {{ !$response.body.nextCursor }}
  Max Pages              30
```

Die Adresse ist die eurer n8n in one.intelligence. Arbeitest du mit einer anderen n8n, steht dort
deren Adresse.

Danach im Code-Node alle Seiten zusammenführen und **prüfen, ob genug angekommen ist**:

```javascript
const alle = [];
for (const it of $input.all()) for (const z of (it.json.data || [])) alle.push(z);
if (alle.length < 100) {
  throw new Error('Nur ' + alle.length + ' Zeilen geladen. Vermutlich greift ein stiller Deckel.');
}
```

Fertiger Beispiel-Workflow zum Importieren: `examples/workflows/datatable-alle-zeilen.json`.

→ **Für die allermeisten n8n-Vorhaben ist das der richtige, niederschwelligste Weg.**

## 2. TCF-Supabase: echte Datenbank für veröffentlichte Apps

Wenn eine **veröffentlichte App** (`https://app-xxxx.tcf.buildbar.de`) und/oder **mehrere Dienste** eine **gemeinsame** Postgres-Datenbank brauchen, oder du **Login/Auth**, **Datei-Storage** bzw. **Vektorsuche (pgvector, z. B. KI-Gedächtnis)** willst.

> **Vektorsuche:** pgvector ist in der TCF-Supabase verfügbar, aber nicht eingerichtet. Für Vektoren
> braucht es ein Embedding-Modell; im Bootcamp-Setup gibt es dafür keinen fertigen Zugang. Braucht
> dein Vorhaben das, sprich mit dem Trainer.
>
> **Wann du es NICHT brauchst:** Für die meisten Vorhaben reicht die **deutsche
> Volltextsuche** in Postgres — ohne fremden Dienst, ohne Kosten, und sie versteht
> Beugung und Komposita. Am 20.09. geprüft:
> ```sql
> ALTER TABLE deine_tabelle ADD COLUMN suche tsvector
>   GENERATED ALWAYS AS (to_tsvector('german', coalesce(titel,'') || ' ' || coalesce(text,''))) STORED;
> CREATE INDEX ON deine_tabelle USING gin(suche);
> SELECT titel FROM deine_tabelle WHERE suche @@ websearch_to_tsquery('german', 'Almhütte Winter');
> ```
> Vektoren lohnen sich, wenn die Frage **andere Wörter benutzt als der Text**
> („Vierbeiner“ findet „Hunde sind erlaubt“). Bei gleichen Wörtern ist die Volltextsuche
> schneller, billiger und leichter zu erklären.
- **Zugangsdaten** im Zugangsbereich: **Project-URL**, **anon-Key** und **service_role-Key**.
- **anon-Key** + Project-URL dürfen ins **Frontend** (`@supabase/supabase-js` mit `NEXT_PUBLIC_SUPABASE_URL` + `NEXT_PUBLIC_SUPABASE_ANON_KEY`).
- ⚠️ **Row Level Security (RLS):** Aus dem Frontend nur Tabellen mit aktivierter Row Level Security (RLS) und passenden Policies ansprechen. Ohne RLS die Daten nur über n8n lesen und schreiben (Supabase-Node mit service_role). Sonst kann jede Person, die die App-Adresse kennt, mit dem anon-Key alle Tabellen (und Storage-Buckets ohne Policy) aller Teilnehmenden lesen und beschreiben. Das eigene Präfix schützt davor nicht.
- **service_role-Key nur serverseitig in n8n** (Node **„Supabase"**, Credential mit Host = Project-URL und Service Role Secret). **Nie** ins Frontend, **nie** ins Repo, nie in die Env-Liste einer öffentlichen App.
- **FastAPI:** `psycopg` mit einem Connection-String aus der Env (siehe auskommentiertes Beispiel in `../backend-example/app/main.py`), nur mit eigener Postgres-Datenbank. Für die TCF-Supabase gibt es im Bootcamp keinen DB-Connection-String.
- Tabellen mit **eigenem Präfix** anlegen: Alle nutzen dieselben Keys, fremde Tabellen sind sichtbar, **keine sensiblen oder personenbezogenen Daten**.
- Beim Veröffentlichen gibt Claude URL und anon-Key über den Deploy-Aufruf mit.

## 3. SQLite: nur lokal oder in einem einzelnen Prozess

Null Setup, eine Datei. Gut für **lokale Prototypen** oder ein **Backend, das als ein dauerhafter Prozess mit Volume** läuft (z. B. `backend-example` als Docker-Container mit gemountetem Volume).

- ⚠️ **Funktioniert NICHT für eine über buildbar veröffentlichte App:** Dort ist das Dateisystem flüchtig, die `.sqlite`-Datei überlebt ein erneutes Veröffentlichen nicht. Für ein veröffentlichtes Frontend ist SQLite daher die falsche Wahl → **Supabase**.

---

### Faustregel
**n8n-Workflow → Data Tables. Veröffentlichte App, Login, Dateien → TCF-Supabase. Nur lokal → SQLite.**
