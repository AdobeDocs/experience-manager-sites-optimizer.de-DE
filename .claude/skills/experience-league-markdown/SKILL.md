---
name: experience-league-markdown
description: Verwenden Sie diese Option beim Schreiben oder Bearbeiten von Markdown-Dateien in einem Repository von Adobe Experience League/Adobe-Enterprise-Docs (help/**/*.md) - steuert die Schriftart, Überschriften, Notizen (NOTE/TIPP/WICHTIG/WARNUNG/etc.), Registerkarten (BEGINTABS/TAB/ENDTABS), Videoeinbettungen, Abzeichen, Bilder, Links/Querverweise, Tabellen, Listen, Code-Blöcke und die eingeschränkte Tag-Zulassungsliste von HTML, die von der Validierungs-Pipeline von Experience League erzwungen wird.
source-git-commit: 14f10c231373992c49a8bb93c043556305b6280d
workflow-type: tm+mt
source-wordcount: '659'
ht-degree: 2%

---


# Experience League Markdown

## Überblick

Experience League-Dokumente verwenden Markdown mit GitHub-Variante sowie eine Reihe benutzerdefinierter Erweiterungen (blockquotebasierte Shortcodes, Abzeichen, Registerkarten, Videoeinbettungen). Die Authoring-Pipeline **validiert** diese Dateien mithilfe nicht unterstützter Syntax (rohe `<video>`, `<hr>`, Aufgabenlisten, gemischte Aufzählungszeichen, übersprungene Überschriftenebenen, übergroße Bilder) verursacht einen Build-/Validierungsfehler, nicht nur einen Stilfehler.

Source of Truth: https://experienceleague.adobe.com/en/docs/authoring-guide/using/markdown/markdown-syntax (rufen Sie diese Seite ab, wenn die lokale Datei reference.md veraltet zu sein scheint — Datum der letzten Aktualisierung ist oben).

Vollständige Syntaxreferenz mit jeder Kurzwahlnummer und Regel: [reference.md](reference.md). Lesen Sie es, bevor Sie etwas nicht-triviales schreiben (Registerkarten, Video, Abzeichen, Tabellen mit HTML).

## Kurzübersicht

| Element | Syntax | Anmerkungen |
|---|---|---|
| Titelei | `---\ntitle: ...\ndescription: ...\n---` | Leere Linie, dann muss `# Title` als Nächstes kommen |
| Überschriftenebenen | `#`, `##`, `###` | `#` = Titel (stimmt mit der `title` überein), `##` = Mini-Inhaltsverzeichniseinträge. Niemals eine Stufe überspringen. Leerzeile vor/nach. Max. 69 Zeichen (DE) |
| Überschriften-ID | `## Heading text {#custom-id}` | Erforderlich, wenn die Überschrift mit einer Zahl beginnt/eine Zahl enthält, z. B. `## 2026 release notes {#2026-release-notes}` |
| Hinweis/Tipp usw. | `>[!NOTE]` `>` dann `>Text` (jeweils in einer eigenen Zeile) | TYPEN: HINWEIS, TIPP, WICHTIG, WARNUNG, VORSICHT, ADMIN, VERFÜGBARKEIT, VORAUSSETZUNGEN, INFO, FEHLER, ERFOLG |
| Registerkarten | `>[!BEGINTABS]` / `>[!TAB Title]` / `>[!ENDTABS]` | Registerkartensätze können nicht verschachtelt werden; nicht in Listen verschachtelt werden |
| Video | `>[!VIDEO](https://video.tv.adobe.com/v/ID/?learn=on&enablevpops)` | Muss auf video.tv.adobe.com gehostet werden — keine rohen `<video>`-/Datei-Links |
| Bild | `![alt text](assets/img.png "hover text"){width="300" align="center"}` | `align` ist nur `center` oder `right` (keine `left`, keine `valign`) |
| Relation (relativ) | `[Text](../folder/file.md)` | Konto für den Speicherort der Quelldatei |
| Link (Stamm) | `[Text](/help/guide/file.md)` | Funktioniert von überall im Repository; erforderlich für URLs mit TOC.md-Badge |
| Deep-Link | `[Text](file.md#heading-id)` | Die Überschrift der Zielgruppe benötigt eine explizite `{#heading-id}` |
| Externer Link (bloße URL) | `<https://example.com>` | Bare URLs werden NICHT automatisch verknüpft - `< >` einschließen oder `[text](url)` verwenden |
| Aufzählungsliste | `* item` (Wählen Sie eines von `*`/`-`/`+`, bleiben Sie konsistent) | Leere Zeile vor/nach Liste; Mischungsmarken = Validierungsfehler |
| Nummerierte Liste | `1. item` (`1.` jede Zeile wiederholen) | GitHub rendert die echten Zahlen |
| Code (inline) | `` `code` `` | Für Dateinamen, Befehle, Werte und nicht validierte Beispiel-URLs |
| Code (eingezäunt) | ` ```language ` ... ` ``` ` | Sprache immer angeben; Leerzeile vor/nach, `{line-numbers="true" start-line="n" highlight="n-m"}` optional |
| Badge (inline) | `[!BADGE Beta]{type=Informative url="..." tooltip="..."}` | `type`: informativ/positiv/negativ/neutral/Achtung |
| Reduzierbar | `+++Summary` ... `+++` | Keine verschachtelten reduzierbaren Elemente; leere Zeilen um interne Listen/Code |
| Leerzeilen-Hack | `<br>&nbsp;` auf eigener Leitung | Einfache, zusätzliche leere Zeilen werden vom Renderer reduziert/ignoriert |
| Kommentar | `<!-- text -->` | Nie `<!--> text <-->` - für alle sichtbar, die die Rohdatei auf GitHub ansehen, also keine Geheimnisse |

## Häufige Fehler

- **`<video>`, `<iframe>` oder anderer nicht auf die Zulassungsliste gesetzt HTML**-→. Die HTML-Zulassungsliste lautet: `table tbody td tfoot thead th tr col colgroup p ul ol li br b caption i strong u s span sub sup a img div em pre code codeblock`. Alles andere (einschließlich `<video>`/`<source>`) wird abgelehnt - verwenden Sie stattdessen den `>[!VIDEO]`-Shortcode, wodurch das Video bereits auf video.tv.adobe.com gehostet werden muss.
- Horizontale Regeln **`<hr>`/`***`, Emoji-Shortcodes (`:bowtie:`), Aufgabenlisten (`- [x]`)** - Keine werden unterstützt. Nicht verwenden, selbst wenn eine lokale Vorschau sie rendert.
- **Mischen von Aufzählungszeichen** (`*` und `-` in derselben Liste) — Validierungsfehler. Wähle einen pro Artikel.
- **Überschriftenebenen überspringen** (`##` direkt nach `####`) — nicht zulässig.
- **Eine numerische Überschrift ohne explizite ID** (z. B. `## 2026 release notes`) - muss `{#some-id}` hinzufügen, da der automatische Slug sonst kollidieren oder brechen kann.
- **Bare URLs in prose** (`Visit https://example.com for more`) - wird nicht als Link gerendert. In `< >` einwickeln oder `[text](url)` verwenden.
- **Zusätzliche leere Zeilen für visuelle Abstände** - vom Renderer reduziert. Verwenden Sie `<br>&nbsp;` anstelle von einfachen `<br>` oder wiederholten Zeilenumbrüchen.
- **Bilder über ~5 MB** - Validierungswarnung bei 5 MB, Fehler bei 20 MB. Mehr als 100 Bilder in einem Artikel unterbrechen das Rendering (EDS-Limit).
- **Mehr als zwei Badges in Frontend-Metadaten** - standardmäßig nicht zulässig.
- **Probleme beheben**: Backslash-Escape funktioniert nur für `` # { } [ ] * + - . ! ``. Verwenden Sie für `<` `>` in Elementen wie `<filename>` Platzhaltern einen Inline-Codeblock oder HTML-Entitäten (`&lt;filename&gt;`), keinen umgekehrten Schrägstrich.

## Vor einem Commit für Markdown-Änderungen

1. Vorderseite vorhanden, `# Title` unmittelbar folgt (hinter der Leerzeile).
2. Jede Überschrift hat davor und danach eine Leerzeile; keine übersprungenen Ebenen.
3. Jedes Video ist `>[!VIDEO](https://video.tv.adobe.com/...)`, kein roher `<video>`.
4. Jeder benutzerdefinierte Shortcode (`>[!NOTE]`, `>[!BEGINTABS]`, `>[!BADGE ...]`) entspricht der exakten Syntax in [reference.md](reference.md) - einschließlich der leeren `>` in mehrzeiligen Blöcken.
5. Listen verwenden einen einheitlichen Aufzählungs-/Zahlenstil mit leeren Zeilen um die gesamte Liste.
6. Relationen: Relative Links werden aus dem Ordner der *Quelldatei* aufgelöst. Cross-Repository- oder TOC-/Badge-Links verwenden ein stammrelatives (`/help/...`) Formular.
7. Kein HTML-Tag außerhalb der -Zulassungsliste im Abschnitt „Häufige Fehler“ oben.
