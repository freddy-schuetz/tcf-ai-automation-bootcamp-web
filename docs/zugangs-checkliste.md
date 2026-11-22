# Zugangs-Checkliste

Mit dieser Liste bereitest du dich auf das AI Automation Bootcamp vor (30.11. bis 03.12.2026 bei der Tourismus+Congress GmbH, Kaiserstraße 56, 60329 Frankfurt am Main). Hake ab, was erledigt ist. Was offen bleibt, besprechen wir im Online-Kick-off am Mittwoch, 25.11.2026, um 14:00 oder am ersten Tag.

Du musst nicht alles allein lösen. Wichtig ist nur, dass offene Punkte vor Tag 1 auf dem Tisch liegen und nicht erst am Tag 3.

**Wichtige Adressen**

- Event-Seite: https://tcf.buildbar.de
- Zugangsbereich mit Passwort: https://tcf.buildbar.de/#zugang
- Anleitung Web: https://tcf.buildbar.de/starten/web
- Anleitung Desktop: https://tcf.buildbar.de/starten/desktop
- Vorhaben: https://tcf.buildbar.de/vorhaben
- Grundlagen: https://tcf.buildbar.de/grundlagen
- Infos für Claude (ohne Zugangsdaten): https://tcf.buildbar.de/claude.md
- Neuer n8n-Schlüssel für dein Projekt: https://hub.tcf.buildbar.de/erneuern

---

## 1. Claude-Plan

- [ ] Du hast einen **bezahlten Claude-Plan**: Pro, Max, Team oder Enterprise. Mit dem kostenlosen Plan geht Claude Code nicht.
- [ ] Du kannst dich unter https://claude.ai anmelden.
- [ ] **Plan über die TCF (Team oder Enterprise)?** Dann muss eine Administratorin oder ein Administrator Claude Code im Browser und die GitHub-Verbindung freischalten. Frag rechtzeitig nach, das kann ein paar Tage dauern.
- [ ] Du weißt: Gebaut wird mit **Claude Code**. Cowork eignet sich nicht als Bauumgebung für dein Repository.

## 2. GitHub-Account

- [ ] Du hast einen **GitHub-Account** und kannst dich anmelden, auch mit dem zweiten Faktor (zum Beispiel App am Handy).
- [ ] Du hast entschieden, ob du einen privaten oder einen dienstlichen Account nimmst. Dein Repository liegt dort und bleibt nach dem Bootcamp bei dir.

## 3. Web oder Desktop

Du wählst einen von zwei Wegen. Beide führen zum selben Ergebnis.

| | Web (im Browser) | Desktop (App auf deinem Rechner) |
|---|---|---|
| Wo | https://claude.ai/code | Claude-Desktop-App |
| Installation | keine | nötig, dafür brauchst du Installationsrechte |
| Start | Onboarding unter https://hub.tcf.buildbar.de. Es legt dir ein privates Repository namens ai-automation-bootcamp an. | Du sagst Claude: „Richte mir https://github.com/freddy-schuetz/tcf-ai-automation-bootcamp ein.“ |
| Gut zu wissen | Vor der ersten Nachricht stellst du den **Netzwerkzugriff auf „Voll“**, sonst erreicht Claude deine n8n nicht. Claude speichert deine Änderungen auf einem Arbeitszweig, veröffentlicht wird aus main: Bevor deine App online geht, führst du die Änderungen nach main zusammen (Pull Request mergen). Claude sagt dir, wo du klickst. Eine lokale Vorschau (localhost) gibt es im Web nicht. | Unter Windows installierst du vorher **Git for Windows** und **Node.js**. Node.js braucht Claude für die Verbindung zu n8n. |
| Anleitung | https://tcf.buildbar.de/starten/web | https://tcf.buildbar.de/starten/desktop |

- [ ] Du hast deinen Weg gewählt.
- [ ] **Desktop:** Du darfst auf deinem Rechner Programme installieren. Dienstrechner erlauben das oft nicht. Wenn nicht: IT fragen oder den Web-Weg nehmen.
- [ ] **Desktop unter Windows:** Git for Windows und Node.js sind installiert. Zum Prüfen öffnest du ein Terminal und tippst `git --version` und `node --version`. Kommt jeweils eine Versionsnummer, passt es.
- [ ] **Web:** Du hast die Anleitung Web einmal durchgelesen.

## 4. Deine n8n in one.intelligence

- [ ] Du hast ein **Konto in eurer n8n in one.intelligence** und kannst dich anmelden.
- [ ] Du kannst dort einen **API-Schlüssel** anlegen: Einstellungen, „n8n API“, „Create API Key“. Wähl eine **lange Laufzeit**, damit dein Projekt auch nach dem Bootcamp verbunden bleibt. Läuft er doch ab, hinterlegst du einen neuen unter https://hub.tcf.buildbar.de/erneuern.
- [ ] Du weißt: Den Schlüssel trägst du nur beim Einrichten ein (Hub oder Desktop-Einrichtung), **nie in den Chat** und nie in eine Datei im Repository.
- [ ] **KI in deinen Workflows** läuft über one.intelligence. Den Zugang vom Typ „one.intelligence“ legst du einmal selbst in deinem n8n-Konto an. Den API-Schlüssel dafür bekommst du in one.intelligence unter Einstellungen, Konto, API-Schlüssel.
- [ ] **Eigenes Kürzel:** Workflows, Tabellen und Webhook-Pfade beginnen mit deinem Kürzel (zum Beispiel `mk-anfragen`). Webhook-Pfade gelten für die ganze n8n in one.intelligence, auch für andere Häuser.
- [ ] **Workflows ohne Webhook startest du selbst:** Im Web-Weg kann Claude Workflows **mit Webhook** auslösen, aber keine mit Zeitplan oder manuellem Trigger. Der Test meldet dann „Workflow cannot be triggered externally“. Solche Workflows startest du im n8n-Editor selbst mit „Execute workflow“. Die Meldung ist kein Fehler in deinem Workflow.

## 5. Microsoft 365 und andere Systeme

- [ ] Du weißt, welche Daten dein Vorhaben braucht: Postfach, Kalender, Teams, SharePoint, eine Datenbank, eine Website oder nur Dateien, die du selbst hochlädst.
- [ ] Du hast eingeschätzt, ob du eine **Freigabe der IT** brauchst:
  - **Microsoft 365, Postfach oder Kalender:** In den meisten Organisationen braucht der Zugriff eine Freigabe der IT.
  - **Teams und Teams-Transkripte:** brauchen immer eine Freigabe der IT.
  - **Mit Passwort ins Postfach (IMAP):** geht bei Microsoft 365 nicht mehr.
  - **Andere Systeme mit Anmeldung:** Frag, ob es eine Schnittstelle (API) und einen Zugang dafür gibt.
- [ ] **Freigabe nötig?** Dann schick die Bitte an die IT möglichst vor dem Bootcamp los, spätestens am Tag 1. Claude hilft dir mit der Textvorlage „Bitte an die IT“ aus dem Skill `m365-google-freigaben`. Sag zum Beispiel: „Hilf mir mit dem Skill m365-google-freigaben, eine Bitte an unsere IT zu formulieren.“
- [ ] **Plan B für den Start steht:** Datei hochladen, ein paar Beispielmails, eine Export-Datei oder eine Umfrage per n8n-Formular. Damit baust du, bis die Freigabe da ist.

## 6. Datenlage

- [ ] Du hast **Beispieldaten**: zum Beispiel 10 bis 20 typische Anfragen, eine Export-Datei oder den Bericht vom letzten Monat.
- [ ] Du hast geprüft, ob **personenbezogene oder vertrauliche Daten** drin sind. Wenn ja: entfernen, anonymisieren oder Testdaten in derselben Struktur nehmen. Sensible Daten kopierst du nie in den Chat.
- [ ] Du weißt, ob du diese Daten mit einem KI-Dienst verarbeiten darfst. KI-Schritte in n8n laufen über one.intelligence; was du Claude im Chat zeigst, landet bei Anthropic. Im Zweifel fragst du eure Datenschutz-Ansprechperson.
- [ ] Du weißt, wo dein Workflow Daten ablegen kann:
  - **n8n Data Tables:** in eurer n8n dabei, der einfachste Start
  - **Supabase des Bootcamps:** für Logins, Datei-Uploads und Suche in Dokumenten. Project-URL, anon-Schlüssel und service_role-Schlüssel stehen im Zugangsbereich. Der service_role-Schlüssel gehört nur in n8n, nie in eine Oberfläche und nie ins Repository. Keine sensiblen Daten, die Instanz teilen sich alle Teilnehmenden.

## 7. Rechner und Netz

- [ ] **Dienstrechner:** Du hast getestet, ob https://claude.ai, https://github.com, https://tcf.buildbar.de und eure n8n in one.intelligence erreichbar sind. Web zusätzlich: https://hub.tcf.buildbar.de. Desktop zusätzlich: https://deploy.tcf.buildbar.de und https://registry.npmjs.org. Firmen-VPN, Proxy oder Firewall blockieren manchmal einzelne Seiten.

## 8. Dein Ziel für Tag 4

Am Donnerstag, 03.12.2026, stellt ihr eure Ergebnisse vor. Davor baust du ein zweites, kleineres Vorhaben im Chat von one.intelligence.

- [ ] Du kannst dein **Vorhaben in zwei, drei Sätzen** beschreiben: Was machst du heute von Hand, und was soll am Ende herauskommen?
- [ ] Du weißt, **was am Donnerstag funktionieren soll**: ein Durchlauf vom Eingang bis zum Ergebnis, mit Beispieldaten oder echten Daten, wo das erlaubt ist.
- [ ] Du weißt, **was ausdrücklich noch nicht dazugehört**, zum Beispiel die Live-Anbindung ans Postfach, wenn die IT noch nicht zugestimmt hat.
- [ ] Du weißt, **wer das Ergebnis nutzen soll** und wem du es danach zeigst.
- [ ] Du hast eine erste Idee für den **nächsten Schritt** im Haus.
