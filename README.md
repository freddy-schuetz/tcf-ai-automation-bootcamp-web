# 🚀 AI Automation Bootcamp (TCF): **Web-Variante** mit Claude Code Web + n8n

Die Arbeitsgrundlage für das **AI Automation Bootcamp** der **Tourismus+Congress GmbH Frankfurt am Main (TCF)** in Kooperation mit **buildbar_**: 30.11. bis 03.12.2026 bei der TCF, Kaiserstraße 56, 60329 Frankfurt am Main. Online-Kick-off am Mittwoch, 25.11.2026, um 14:00 Uhr. Trainer: Friedemann Schütz.

Die **Web-Variante** ist für alle, die **nichts installieren können oder wollen** (z. B. ohne Admin-Rechte auf dem Firmen-Laptop). Alles läuft im Browser über **[claude.ai/code](https://claude.ai/code)**: Du beschreibst dein Vorhaben, **Claude baut** die Automatisierung in **deiner n8n in one.intelligence** (und bei Bedarf eine kleine Web-Oberfläche).

**Wie das Bootcamp läuft:** Jede Person arbeitet an **eigenen Abläufen**. Tag 1 richtest du ein, klärst dein Vorhaben und baust eine erste Version. Tag 2 bindest du eigene Daten und Systeme an, Tag 3 machst du alles verlässlich. Am Tag 4 baust du ein zweites, kleineres Vorhaben im Chat von one.intelligence, dann stellt ihr euch die Ergebnisse vor. Am Ende hast du **lauffähige Workflows in deiner n8n, ein eigenes Repository und die Arbeitsweise, um weiterzubauen**, auch nach dem Bootcamp.

> 🌐 **Alles Aktuelle zum Bootcamp:** [tcf.buildbar.de](https://tcf.buildbar.de) · Zugangsdaten (mit Passwort): [tcf.buildbar.de/#zugang](https://tcf.buildbar.de/#zugang) · Anleitung Web: [tcf.buildbar.de/starten/web](https://tcf.buildbar.de/starten/web) · Vorhaben: [tcf.buildbar.de/vorhaben](https://tcf.buildbar.de/vorhaben) · Grundlagen: [tcf.buildbar.de/grundlagen](https://tcf.buildbar.de/grundlagen)

> 📝 **Vor dem Bootcamp: [Zugangs-Checkliste](docs/zugangs-checkliste.md)**: Claude-Plan, GitHub, dein Konto in eurer n8n in one.intelligence, Freigaben und Beispieldaten. Kein Technik-Wissen nötig, offene Punkte klären wir im Kick-off.
>
> 📄 **Zum ersten Mal hier? → [Anleitung Web](https://tcf.buildbar.de/starten/web)**: vom Einloggen bis zur veröffentlichten App, in einfacher Sprache, ohne Installation. Für die Desktop-App: [Anleitung Desktop](https://tcf.buildbar.de/starten/desktop).

> 🧭 **Vorhaben noch unklar oder schwer zu beschreiben?** Sag **„Hilf mir, meine Idee zu klären"**: Claude stellt dir ein paar einfache Fragen und macht daraus einen fertigen Bau-Plan. Ideen zum Stöbern: **[docs/tourismus-ideen.md](docs/tourismus-ideen.md)**.

> ℹ️ **Kannst du installieren?** Dann gibt es auch die **Desktop-Variante** (lokale Vorschau deiner App): [tcf.buildbar.de/starten/desktop](https://tcf.buildbar.de/starten/desktop).

---

## ✅ Was du brauchst

- Einen **Browser** und Internet.
- Einen **eigenen GitHub-Account**.
- Einen **Claude-Plan mit Claude Code**: Pro, Max, Team oder Enterprise. Die kostenlose Stufe reicht nicht. **Cowork** eignet sich nicht als Bauumgebung für das Repository.
- Dein **Konto in eurer n8n in one.intelligence** und einen **eigenen n8n-API-Schlüssel** (in n8n unter Einstellungen, „n8n API“, „Create API Key“, mit langer Laufzeit).
- Das **Bootcamp-Passwort** für den Zugangsbereich (nur für Datenbank und Veröffentlichen aus der Desktop-App).

---

## ✨ So legst du los (keine Installation)

1. **Repo über den Hub anlegen:** Öffne **[hub.tcf.buildbar.de](https://hub.tcf.buildbar.de)**, trag deinen n8n-API-Schlüssel ein (die Adresse eurer n8n ist schon eingetragen) und melde dich mit deinem GitHub-Account an. Der Hub legt in deinem Account ein **privates Repository `ai-automation-bootcamp`** an, erzeugt aus dieser Vorlage und mit fertiger n8n-Verbindung. Die ausführliche Anleitung steht unter [tcf.buildbar.de/starten/web](https://tcf.buildbar.de/starten/web).
2. **Netzwerkzugriff auf „Voll“ stellen:** In claude.ai/code unter dem Eingabefeld auf „Default“ mit dem Wolkensymbol, dann auf das Zahnrad, unter „Netzwerkzugriff“ die Stufe „Voll“ wählen und speichern. Sonst erreicht Claude deine n8n nicht.
3. **Projekt öffnen:** Öffne **dein** Repository `ai-automation-bootcamp` in **[claude.ai/code](https://claude.ai/code)**. Nicht die öffentliche Vorlage: In die kannst du nicht speichern.
4. **Loslegen:** Tippe einfach
   > **Los geht's**

   Claude begrüßt dich, prüft die Verbindung und fragt nach deinem Vorhaben. Hast du schon eine Idee? Beschreib sie direkt. Noch unsicher? Sag **„Hilf mir, meine Idee zu klären"**.

Claude baut, testet, dokumentiert und sichert alles **automatisch**.

---

## 🔌 Deine n8n-Verbindung

Die Verbindung steht in der Datei `.mcp.json` (per HTTP). Beim Anlegen deines Repos trägt der Hub dort eine **Verbindungs-URL mit deinem persönlichen Token** ein (`https://hub.tcf.buildbar.de/g/<token>/mcp`). **Dein n8n-API-Key liegt beim Hub, nicht im Repo.** In der öffentlichen Vorlage steht an dieser Stelle nur ein Platzhalter.

> ⚠️ **Die Verbindungs-URL in `.mcp.json` ist wie ein Passwort.** Wer sie hat, kommt über den Hub an dein n8n-Konto und kann veröffentlichen. Lass dein Repository **privat**. Bevor du es teilst oder öffentlich machst, ersetze den Token wieder durch den Platzhalter `HIER-TRAEGT-DER-HUB-DEINEN-TOKEN-EIN` (Claude hilft dir dabei).

Claude bestätigt die Verbindung automatisch bei der Begrüßung. Prüfen kannst du sie jederzeit mit **„prüfe meine n8n-Verbindung"**. Ist dein n8n-Schlüssel abgelaufen, hinterlegst du auf **[hub.tcf.buildbar.de/erneuern](https://hub.tcf.buildbar.de/erneuern)** einen neuen.

**Eigenes Kürzel:** Gib deinen Workflows, Tabellen und Webhook-Pfaden ein **eigenes Kürzel** (z. B. `mk-hello`). Webhook-Pfade gelten für die ganze n8n in one.intelligence, auch für andere Häuser, und jeder Pfad darf nur einmal aktiv sein.

---

## 🗂️ Die Bootcamp-Themen und passende Skills

| Thema | Skill (wird ergänzt) |
|---|---|
| Meetingnotizen strukturieren | `meetingnotizen` |
| E-Mail-Anfragen sortieren und Antwortentwürfe | `mail-triage-entwuerfe` |
| Wiederkehrende Berichte | `bericht-zeitgesteuert` |
| Terminfindung und Koordination | `terminkoordination` |
| Daten analysieren und visualisieren | `daten-visualisieren` |
| Präsentationen effizienter erstellen | `praesentation` |
| Zugriff auf Postfach, Kalender, Teams, Google | `m365-google-freigaben` |

Beispiele aus dem Tourismus: [docs/tourismus-ideen.md](docs/tourismus-ideen.md) · Die Vorhaben der Gruppe: [tcf.buildbar.de/vorhaben](https://tcf.buildbar.de/vorhaben)

> 🔐 **Freigaben früh klären:** Soll dein Workflow auf ein **Outlook-Postfach, einen Kalender oder Teams** (Microsoft 365) zugreifen, braucht es in üblich eingerichteten Organisationen eine **Freigabe durch die IT (Admin)**; bei Teams immer. Auch Google-Konten brauchen Vorbereitung. Frag deine IT möglichst **vor** dem Bootcamp, wer Admin ist und ob eine Freigabe möglich ist. Ohne Freigabe baust du mit **Beispieldaten** und hältst die Freigabe als nächsten Schritt fest.

---

## 📦 Was ist drin? (und was es für dich tut)

### Die Skills: das „Wissen", das Claude automatisch nutzt
Skills sind Spickzettel, die Claude **von selbst** heranzieht, sobald sie zum Thema passen. Du musst sie nicht aufrufen.

**Am Anfang: dein Vorhaben klären** (Tag 1):
- `idee-klaeren`: macht aus einer vagen oder schwer beschreibbaren Idee einen klaren Bau-Plan, inklusive Freigaben, Datenlage und Wahl der n8n.
- `grill-me`: klopft deinen **fertigen** Plan Frage für Frage ab, bevor gebaut wird (Claude bietet es nach dem Steckbrief einmal an, oder du sagst „grill mich").

**Bootcamp-Themen:** siehe Tabelle oben.

**Workflows richtig bauen** (von [czlonkowski](https://github.com/czlonkowski/n8n-skills)):
- `n8n-mcp-tools-expert`: wie man die n8n-Werkzeuge richtig bedient (Nodes suchen, Workflow anlegen, prüfen).
- `n8n-workflow-patterns`: bewährte Baumuster: Webhook, API-Aufruf, Datenbank, KI-Agent, Zeitplan.
- `n8n-node-configuration`: wie man einen einzelnen Baustein (Node) korrekt einstellt.
- `n8n-expression-syntax`: die `{{ }}`-Ausdrücke, mit denen Daten durch den Workflow fließen.
- `n8n-validation-expert`: findet Fehler im Workflow und erklärt sie.
- `n8n-code-javascript` / `n8n-code-python`: falls mal eigener Code in einem Node nötig ist.

**Qualität sichern und verständlich machen:**
- `n8n-testdaten`: erzeugt Testfälle und probiert den Workflow durch.
- `n8n-dokumentation`: schreibt **Sticky Notes in einfacher Sprache** in den Workflow, damit du auf einen Blick siehst, was wo passiert.
- `n8n-security-audit`: Sicherheits-Check vor dem Aktivieren (keine offenen Keys, Webhooks abgesichert …).
- `n8n-pruefbericht`: erstellt am Ende einen kurzen, verständlichen Bericht zum Workflow.

**Optional: eigene Oberfläche oder eigenes Backend**
- `frontend-build` / `frontend-scaffold`: **vollwertige** Web-Apps (Next.js) bauen: Formulare, Dashboards, Tabellen, Karten …, angebunden an n8n, FastAPI oder KI-Streaming.
- `backend-fastapi`: ein eigenes Python-Backend, wenn n8n für schwere Rechen- oder Datenlogik nicht reicht.

### Die Dateien und Ordner
| Pfad | Was es ist |
|------|-----------|
| `CLAUDE.md` | Die Spielregeln für Claude (lädt automatisch): sorgt dafür, dass Workflows korrekt gebaut, getestet **und automatisch dokumentiert** werden. |
| `.mcp.json` | Die Verbindung zu deiner n8n (per HTTP). Der Hub trägt die Verbindungs-URL mit deinem Token ein; dein Key bleibt beim Hub. Die URL ist wie ein Passwort. |
| `workflows/` | **Dein Ergebnis:** deine fertigen Workflows als JSON-Export (legt Claude an). |
| `mein-use-case.md` | Dein Steckbrief aus der Planung am Tag 1 (legt Claude an). |
| `examples/workflows/` | Importierbare Lern-Beispiele (alle mit Sticky-Notes-Erklärung): **`n8n-grundlagen.json`** (Grundlogik, Trigger-Arten und wichtigste Bausteine), **`ai-agent-grundlagen.json`** (KI-Agent mit Sprachmodell, Memory und Tool), **`ai-agent-datatable.json`** (KI-Agent → Antwort in eine n8n Data Table speichern), **`ai-agent-tool-webhook.json`** (KI-Agent ruft per Tool den hello-webhook auf), **`hello-webhook.json`** (Mini-Workflow). |
| `frontend-starter/` | Lauffähige Web-App: Formular → n8n-Webhook (+ optionaler KI-Chat). |
| `backend-example/` | Lauffähiges FastAPI-Backend (`/health` + Beispiel-Endpoint). |
| `docs/datenbank.md` | Wann welche Datenbank (Data Tables, Supabase). |
| `docs/tourismus-ideen.md` | Ideen-Menü: die Bootcamp-Themen und weitere Tourismus-Use-Cases. |
| `docs/zugangs-checkliste.md` | Vorbereitung: was vor Tag 1 geklärt sein sollte. |

---

## 🧪 Dein erster Workflow

**Noch unsicher, was und wie?** Sag zuerst **„Hilf mir, meine Idee zu klären"**. Weißt du schon, was du willst, sag es einfach direkt, z. B.:
> „Bau mir einen Workflow: Ein Webhook empfängt einen Namen und antwortet mit einer freundlichen Begrüßung."

Claude baut den Workflow und **validiert, testet mit Beispieldaten, dokumentiert ihn mit Sticky Notes und macht einen Sicherheits-Check, automatisch**, ohne dass du extra darum bitten musst (so ist es in `CLAUDE.md` festgelegt). Am Ende berichtet Claude verständlich, was gemacht wurde.

**Lieber erst lernen?** Importiere diese Workflows in n8n (Workflows → Import from File). Alle erklären sich selbst per **Sticky Notes**:
- `examples/workflows/n8n-grundlagen.json`: Grundlogik, die **Trigger-Arten** und die wichtigsten Bausteine (Set, IF, Webhook, HTTP, Code, Switch, Filter …).
- `examples/workflows/ai-agent-grundlagen.json`: ein **KI-Agent** mit Sprachmodell (Claude), Memory und einem Tool, inklusive der speziellen `ai_*`-Verbindungen.
- `examples/workflows/ai-agent-datatable.json`: praxisnah: **Chat → KI-Agent → Ergebnis in eine n8n Data Table speichern** (Persistenz ganz ohne externe Datenbank).
- `examples/workflows/ai-agent-tool-webhook.json`: der **KI-Agent benutzt ein Tool** und ruft live den `hello-webhook` (oder jede andere API) auf. Schön in Kombination mit `hello-webhook.json`.
- `examples/workflows/hello-webhook.json`: ein Mini-Workflow zum schnellen Ausprobieren (und als Ziel des Agent-Tools oben). Vor dem Aktivieren änderst du den Pfad im Webhook-Node auf `<kürzel>-hello` (z. B. `mk-hello`), denn jeder Webhook-Pfad darf in eurer n8n nur einmal aktiv sein.

Die KI-Beispiele nutzen den Node von **one.intelligence** und brauchen deinen eigenen Zugang vom Typ `oneIntelligenceApi`. Den API-Schlüssel dafür bekommst du in one.intelligence unter Einstellungen, Konto, API-Schlüssel; du legst den Zugang selbst in n8n an.

---

## 🎨 Optional: eigene Oberfläche (Frontend)

Die Skills **`frontend-build`** + **`frontend-scaffold`** befähigen Claude, **vollwertige Next.js-Frontends** zu bauen: Multi-Page-Apps, Dashboards, Tabellen und Diagramme, **Karten (MapLibre)**, Chat-Oberflächen usw. Angebunden wahlweise an **n8n-Webhooks** (Muster A), ein **FastAPI-Backend** (Muster B) oder **KI-Streaming** (Muster C). Stack: Next.js 16 · React 19 · TypeScript · Tailwind 4.

Sag z. B. *„Bau mir ein Dashboard, das die Ergebnisse aus meinem n8n-Workflow anzeigt"*.

### 👀 So siehst du deine App: öffentliche Adresse über buildbar
Im Web gibt es **keine lokale Vorschau** (`localhost` läuft nur auf einem eigenen Rechner). Stattdessen bekommst du **auf Zuruf eine öffentliche Internet-Adresse**.

**So geht's:** Sag **„Veröffentliche meine App"**. Claude prüft den Build, speichert deine Änderungen (Commit und Push auf den Arbeits-Branch der Sitzung) und bittet dich dann, den **Pull Request nach `main` zu übernehmen**: Veröffentlicht wird nur, was in `main` liegt. Claude sagt dir, wo du klickst. Danach stößt Claude beim Hub die Veröffentlichung an (`https://hub.tcf.buildbar.de/deploy`) und du bekommst eine Adresse wie **`https://app-xxxx.tcf.buildbar.de`**. Der **erste Build dauert einige Minuten**; eine Fehlermeldung wie „no available server" in dieser Zeit ist normal. Nach jeder Änderung einfach neu veröffentlichen lassen.

> Braucht deine App Zugänge (z. B. Supabase oder einen n8n-Webhook)? Claude gibt sie **direkt beim Veröffentlichen** mit, nie ins Repo.

> ⚠️ **KI-Chat im Starter bleibt aus:** Der optionale Chat im `frontend-starter` (`/chat`) hat **keinen Login** und bräuchte einen eigenen Anbieter-Schlüssel. Im Bootcamp gibt es dafür keinen; KI läuft über n8n mit one.intelligence, die App ruft nur einen Webhook auf.

### Die Vorlagen zum Draufaufbauen
- **`frontend-starter/`**: minimales Beispiel: Formular → n8n-Webhook + optionaler KI-Chat. Details: `frontend-starter/README.md`.
- **`backend-example/`**: FastAPI-Service (`/health` + Beispiel-Endpoint), falls n8n für schwere Rechen-, Datenbank- oder Geo-Logik nicht reicht. Start: siehe `backend-example/README.md`.

---

## 🗄️ Brauche ich eine Datenbank?

Meistens reicht, was schon **bereitsteht**. Sag Claude einfach, was du brauchst:
- **Daten im Workflow** → **n8n Data Tables** (eingebaut, null Setup): der Standard.
- **App-Datenbank, Login, Dateien, Vektoren** → **TCF-Supabase** auf dem Bootcamp-Server: Project-URL, anon-Key und service_role-Key stehen im [Zugangsbereich](https://tcf.buildbar.de/#zugang). Der service_role-Key gehört **nur serverseitig in n8n**, nie ins Frontend oder Repo. Aus dem Frontend nur Tabellen mit aktivierter **Row Level Security (RLS)** und passenden Policies ansprechen. Ohne RLS die Daten nur über n8n lesen und schreiben (Supabase-Node mit service_role).

> **Gemeinsame Datenbank:** Nutze **eigene Tabellen bzw. ein eigenes Präfix** und verarbeite **keine sensiblen oder personenbezogenen Daten**, dafür gibt es Beispieldaten. Andere Teilnehmende können gemeinsam genutzte Tabellen sehen.

Details: **[docs/datenbank.md](docs/datenbank.md)**.

---

## 🏁 Am Ende: dein Repository

Am Tag 4 vor der Vorstellung räumt Claude mit dir das Repository auf. Sag z. B. **„Räum mein Repository auf und exportiere meine Workflows"**. Danach liegt im Repo:
- `workflows/`: alle fertigen Workflows als JSON (ohne Keys, ohne echte Testdaten),
- `mein-use-case.md`: dein Steckbrief, ggf. der Prüfbericht,
- `README.md`: was dein Vorhaben tut, welche Zugänge und Freigaben es braucht, und ein klarer **nächster Schritt**.

Zum Schluss den Pull Request nach `main` übernehmen, dann ist alles in deinem Repository gesichert.

---

## ⚠️ Sicherheit
- **Niemals** API-Schlüssel (n8n, one.intelligence, Supabase service_role) in Workflow-Parameter, Code, Repo oder den Chat schreiben: dafür gibt es **n8n-Credentials**, die du selbst im n8n-Editor anlegst.
- In der `.mcp.json` steht eine **Verbindungs-URL mit deinem persönlichen Token**. Dein **n8n-API-Key liegt beim Hub**, nicht im Repo, aber die URL ist **wie ein Passwort**. Dein Repository ist **privat** in deinem eigenen GitHub-Account: Lass es privat. Bevor du es teilst oder öffentlich machst, ersetze den Token wieder durch den Platzhalter `HIER-TRAEGT-DER-HUB-DEINEN-TOKEN-EIN`.
- Gemeinsame Bootcamp-Datenbank (Supabase): **keine sensiblen oder personenbezogenen Daten**, nur **Test- oder Beispieldaten**. Sensible Daten des Hauses nie in den Chat kopieren.
- Keinen offenen KI-Chat veröffentlichen (siehe oben).

## 👤 Gebaut von
**Friedemann Schütz**: **(KI-)Automatisierung, KI-Agenten, Frontends, Infrastruktur, Datenmanagement und Prozessoptimierung** (n8n Ambassador, Essen). Beratung · Umsetzung · Workshops und Schulungen.

Im Bootcamp arbeitest du mit bereitgestellten Bausteinen. Für **Unternehmen** setze ich Lösungen **self-hosted, DSGVO-konform** und produktionsreif um. Kostenloser Einstieg per **[KI-Check](https://ki-check.friedemann-schuetz.de)**.
→ **[friedemann-schuetz.de](https://friedemann-schuetz.de)** · [KI-Check](https://ki-check.friedemann-schuetz.de) · [LinkedIn](https://www.linkedin.com/in/friedemann-schuetz)

## 📄 Lizenz und Dank
MIT (siehe `LICENSE`).

Mit großem Dank an:
- **[Romuald Członkowski / czlonkowski](https://github.com/czlonkowski)**: die gebündelten n8n-Kern-Skills und der **n8n-MCP-Server**, auf dem das Ganze läuft.
- **[Matt Pocock](https://github.com/mattpocock/skills)**: Vorlage für den Skill `grill-me`.
- **[snipKI](https://snipki.de)**: Grundlage und Idee dieser Vorlage.

Details in `ATTRIBUTION.md`.
