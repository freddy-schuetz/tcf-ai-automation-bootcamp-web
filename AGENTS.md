# AGENTS.md: AI Automation Bootcamp (TCF), Web-Vorlage (für Codex, OpenCode und andere Agents)

Diese Datei richtet sich an Coding-Agents, die **AGENTS.md** lesen (OpenAI **Codex**, **OpenCode**, Cursor, Gemini CLI, …).

> **Du nutzt Claude Code Web?** Dann brauchst du das hier nicht: nimm **[README.md](README.md)** + **CLAUDE.md** (Repo über [hub.tcf.buildbar.de](https://hub.tcf.buildbar.de) anlegen, in **claude.ai/code** öffnen, n8n-mcp per HTTP). Diese AGENTS.md beschreibt die **stdio**-Anbindung für **lokal installierte** Fremd-Agents (Codex/OpenCode); für die Web-Variante ohne Installation ist sie nicht nötig.

## Setup (einmalig)

1. **n8n-Zugang:** dein eigenes Konto in eurer n8n in **one.intelligence**. Den API-Schlüssel legst du dort an (**Settings → n8n API → Create API Key**, lange Laufzeit). Adresse und Schlüssel kommen nur in die lokale Konfiguration unten, nie ins Repository und nie in den Chat.
2. **n8n-mcp anbinden** (läuft per `npx`, keine Installation nötig; Node.js muss vorhanden sein):

   **Codex** → `~/.codex/config.toml` (global) oder `.codex/config.toml` (projektbezogen, nur „trusted projects") · Vorlage: [`.codex/config.toml.example`](.codex/config.toml.example)
   ```toml
   [mcp_servers.n8n-mcp]
   command = "npx"
   args = ["-y", "n8n-mcp"]
   [mcp_servers.n8n-mcp.env]
   N8N_API_URL = "https://n8n.oi.destination.one"
   N8N_API_KEY = "DEIN_N8N_API_KEY"
   MCP_MODE = "stdio"
   ```

   **OpenCode** → `opencode.json` · Vorlage: [`opencode.json.example`](opencode.json.example)
   ```json
   { "mcp": { "n8n-mcp": { "type": "local",
     "command": ["npx", "-y", "n8n-mcp"],
     "environment": { "N8N_API_URL": "https://n8n.oi.destination.one", "N8N_API_KEY": "DEIN_N8N_API_KEY", "MCP_MODE": "stdio" } } } }
   ```

3. **Verbindung testen:** Agent bitten, `n8n_health_check` aufzurufen → muss OK liefern.
4. ⚠️ **Keys niemals committen:** Die echten Configs (`.codex/config.toml`, `opencode.json`) stehen in `.gitignore`.

## Arbeitsregeln: CLAUDE.md ist die einzige Quelle

**Lies [CLAUDE.md](CLAUDE.md) und befolge sie 1:1.** Dort stehen die Arbeitsweise (Vorhaben klären am Tag 1, Themen-Skills, Freigaben früh prüfen, Ergebnis im eigenen Repository, Veröffentlichen über den buildbar-Hub statt localhost), der Standard-Prozess, alle kritischen n8n-Konventionen, Best Practices und Sicherheitsregeln. Diese Datei ergänzt nur das agent-spezifische Setup und wiederholt die Regeln bewusst **nicht** (sonst laufen die Versionen auseinander).

**Skills-Übersetzung:** Wo CLAUDE.md von „Skills" spricht, sind Markdown-Ordner unter `.claude/skills/<name>/SKILL.md` gemeint. **OpenCode lädt Claude-Code-Skills nativ.** Lädt dein Agent sie nicht automatisch (z. B. Codex): Lies die jeweilige `SKILL.md` als Anleitung, sobald die Situation passt (z. B. `idee-klaeren` bei vagem Vorhaben, ein Themen-Skill wie `mail-triage-entwuerfe` beim passenden Thema, `m365-google-freigaben` bei Postfach- oder Kalenderzugriff, `n8n-testdaten` nach dem Bauen, `n8n-dokumentation` für Sticky Notes, `n8n-security-audit` vor der Aktivierung, `n8n-pruefbericht` am Ende).

## Wissen und Beispiele

- Tiefes n8n-Wissen liefert der **n8n-mcp-Server** selbst: starte mit `tools_documentation()`.
- Importierbare **Lern-Workflows** (mit Sticky-Notes-Erklärungen): `examples/workflows/` · **Ideen-Menü** mit den Bootcamp-Themen: `docs/tourismus-ideen.md` · Datenbank-Wahl: `docs/datenbank.md`.
- **Frontend/Backend** (optional): lauffähige Beispiele in `frontend-starter/` (Next.js 16) und `backend-example/` (FastAPI); Details in deren README.
- Event-Infos (secret-frei, Markdown): [tcf.buildbar.de/claude.md](https://tcf.buildbar.de/claude.md).
