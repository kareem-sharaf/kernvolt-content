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
| `content/` | 16 Dateien, je ein Bereich der Website (Startseite, Über uns, …) |
| `images/uploads/` | Bilder, die über den Editor hochgeladen werden |
| `design/theme.json` | Die zwei Farben der Website (Haupt- und Signalfarbe) |
| `media/` | Welche Bilder wo stehen: Seitenbilder, Projekte, Zertifikate, Logos |

Jede Datei enthält beide Sprachen:

```json
{
  "de": { "heroTitle": "Strom, der ankommt." },
  "en": { "heroTitle": "Power that arrives." }
}
```

---

## Farben

Im Editor unter **Design → Farben**. Zwei Farben werden gewählt:

| Feld | Wirkung | Standard |
|---|---|---|
| Hauptfarbe | Buttons, Links, Akzente | `#0a9dd9` |
| Signalfarbe | Sparsame Hervorhebungen | `#e29100` |

Alle helleren und dunkleren Abstufungen werden beim Build daraus berechnet. Die
Schriftfarbe auf farbigen Flächen (weiß oder fast schwarz) wird ebenfalls
automatisch bestimmt, damit Buttons in jedem Fall lesbar bleiben.

---

## Bilder

Im Editor unter **Bilder**. Fünf Bereiche:

| Bereich | Inhalt |
|---|---|
| Seitenbilder | Das große Bild oben auf jeder Seite, und das Logo |
| Projekte | Die Projekte der Startseite, je mit beliebig vielen Fotos |
| Zertifikate | Die Urkunden auf der Seite „Zertifikate“ |
| Partner | Die Logos im Partner-Band |
| Kunden | Die Logos im Kunden-Band |

Projekte, Zertifikate und Logos lassen sich hinzufügen, löschen und umsortieren.
Das erste Bild eines Projekts ist das Titelbild seiner Karte.

Hochgeladene Dateien landen in `images/uploads/`. Ein Bild ist in beiden
Sprachen dasselbe; nur die Namen daneben gibt es auf Deutsch und Englisch.

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
