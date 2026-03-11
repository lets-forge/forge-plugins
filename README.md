# forge-plugins

Interne Claude Code Plugins von lets-forge.

## Setup (einmalig)

### 1. GitHub-Zugang sicherstellen

Du brauchst Zugriff auf das private Repo `lets-forge/forge-plugins`. Stelle sicher, dass du authentifiziert bist:

```bash
gh auth login
```

### 2. Marketplace hinzufuegen

In Claude Code:

```
/plugin marketplace add lets-forge/forge-plugins
```

Danach kannst du die verfuegbaren Plugins durchstoebern und einzeln installieren.

### 3. Auto-Discovery fuer Projekt-Repos (optional)

Damit Teammitglieder den Marketplace automatisch angeboten bekommen, lege diese Datei in eurem Projekt-Repo an:

**.claude/settings.json**
```json
{
  "extraKnownMarketplaces": {
    "forge-plugins": {
      "source": {
        "source": "github",
        "repo": "lets-forge/forge-plugins"
      }
    }
  }
}
```

## CI / GitHub Actions

Damit Claude Code in CI-Pipelines auf die Plugins zugreifen kann, setze `GITHUB_TOKEN` als Environment Variable:

```yaml
- name: Run Claude Code
  env:
    GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
  run: claude ...
```

Der Standard-`GITHUB_TOKEN` von GitHub Actions hat Lesezugriff auf Repos innerhalb der Org. Falls nicht, erstelle ein Fine-grained PAT mit `repo` Scope und hinterlege es als Repository Secret.

## Verfuegbare Plugins

| Plugin | Beschreibung |
|--------|-------------|
| **makerkit-review** | Code-Quality-Reviewer fuer TypeScript, React, Next.js und Supabase |

## Plugin hinzufuegen

1. Erstelle einen neuen Ordner im Repo-Root mit der Plugin-Struktur:
   ```
   mein-plugin/
   ├── .claude-plugin/
   │   └── plugin.json
   ├── agents/
   ├── commands/
   ├── skills/
   └── README.md
   ```

2. Registriere das Plugin in `.claude-plugin/marketplace.json`:
   ```json
   {
     "name": "mein-plugin",
     "description": "Was das Plugin tut",
     "source": "./mein-plugin"
   }
   ```

3. Commit, push — fertig. Alle Nutzer bekommen das neue Plugin beim naechsten Update.
