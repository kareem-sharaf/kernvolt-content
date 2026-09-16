# KernVolt — Website-Inhalte

Die Texte und Bilder der Website [kernvolt.info](https://kern-volt-r.vercel.app).
**Hier liegt kein Programmcode** — nur Inhalte.

## Bearbeiten

Nicht hier auf GitHub, sondern im Editor:

**→ https://kern-volt-r.vercel.app/admin/**

Dort anmelden, Text ändern, speichern. Die Website ist etwa eine Minute später
aktualisiert.

---

## Was hier liegt

| Ordner | Inhalt |
|---|---|
| `content/` | 18 Dateien, je ein Bereich der Website (Startseite, Über uns, …) |
| `images/uploads/` | Bilder, die über den Editor hochgeladen werden |

Jede Datei enthält beide Sprachen:

```json
{
  "de": { "heroTitle": "Strom, der ankommt." },
  "en": { "heroTitle": "Power that arrives." }
}
```

---

## Für Entwickler

Dieses Repository ist die alleinige Quelle der Inhalte. Der Website-Code liegt
getrennt davon in einem privaten Repository und holt sich diese Dateien beim
Build (`scripts/fetch-content.mjs`).

Der Workflow in `.github/workflows/deploy.yml` stößt nach jedem Push einen
Neu-Build der Website an. Dafür muss das Repository-Secret `VERCEL_DEPLOY_HOOK`
gesetzt sein — die Hook-URL kommt aus den Vercel-Projekteinstellungen.

Die Feldstruktur des Editors wird aus diesen Dateien erzeugt. Kommt ein neuer
Schlüssel dazu, im Code-Repository `npm run cms:config` ausführen.
