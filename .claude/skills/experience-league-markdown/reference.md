---
source-git-commit: 14f10c231373992c49a8bb93c043556305b6280d
workflow-type: tm+mt
source-wordcount: '1030'
ht-degree: 0%

---
# Experience League Markdown — Vollständige Syntaxreferenz

Zusammengefasst von https://experienceleague.adobe.com/en/docs/authoring-guide/using/markdown/markdown-syntax (zuletzt bestätigt gegenüber der Seite „Letzte Aktualisierung: 17. Juni 2026„). Rufen Sie die Live-Seite erneut ab, wenn hier etwas veraltet zu sein scheint.

## Textmaterial und Titel

```markdown
---
title: Title for search optimization
description: This is the article description used for search optimization.
---
# Article title
```

Die Zeile unmittelbar nach dem schließenden `---` (und eine leere Zeile) muss die `# Title` sein - und sie sollte mit `title:` in der Frontsache übereinstimmen.

## Grundlegende Textformatierung

- Fett: `**bold**`
- Kursiv: `*italic*`
- Fett+Kursiv: `***both***`
- Formatierungszeichen mit Escape-Zeichen versehen: `\*not italic\*`
- Absätze erfordern keine spezielle Syntax, sondern nur eine Leerzeile zwischen ihnen.

## Überschriften

```markdown
# This is level 1 (article title)
## This is level 2 (mini-TOC entry)
### This is level 3
```

- `#` (H1) = Artikeltitel, muss mit der `title` übereinstimmen.
- `##` (H2) = wird standardmäßig im Mini-Inhaltsverzeichnis angezeigt (`mini-toc-levels: 3` in Frontmatter, um weitere Ebenen anzuzeigen).
- Niemals eine Stufe überspringen (`##` → `####` ist ungültig).
- Vor (und **nach jeder Überschrift** Leerzeile erforderlich.
- Maximale Überschriftenlänge: 69 Zeichen (EN), 120 Zeichen (lokalisiert).
- Überschriften-ID/Anker: `## Creating processing rules {#processing-rules}` — Kleinbuchstaben, mit Bindestrich. Erforderlich, wenn der Überschrifttext mit einer Ziffer beginnt (z. B. Jahr). Ohne eine explizite ID ist der standardmäßige Anker der automatisch angesäuberte Überschrifttext.

## Notizen/Ermahnungen

Standardtypen: `NOTE`, `TIP`, `IMPORTANT`, `WARNING`. Neuere Typen nur für EXL: `ADMIN`, `AVAILABILITY`, `PREREQUISITES`, `INFO`, `ERROR`, `SUCCESS`.

```markdown
>[!NOTE]
>
>This is a standard NOTE block.
>
>It can include multiple paragraphs.
```

Jede Zeile des Blocks beginnt mit `>`. Fügen Sie eine bloße `>` direkt nach der Typenmarkierung ein.

## Registerkarten

```markdown
>[!BEGINTABS]

>[!TAB iOS]

Content for the iOS tab.

>[!TAB Android]

Content for the Android tab.

>[!ENDTABS]
```

- Registerkartensätze können nicht in Registerkartensätzen oder Registerkartensätzen in Listen verschachtelt werden.
- Registerkartentitel werden wörtlich gerendert - keine Markdown-Formatierung innerhalb von `>[!TAB ...]`.
- Mehrere Registerkartensätze sind auf einer Seite ausreichend.

## Video

```markdown
>[!VIDEO](https://video.tv.adobe.com/v/27069/?learn=on&enablevpops)
```

- Das Video muss bereits auf `video.tv.adobe.com` (Adobe TV/MPC) gehostet werden. Rohe Videodatei-Links oder `<video>`-Tags werden nicht unterstützt.
- Empfohlene Abfrageparameter: `?learn=on&enablevpops` (die kanonische Form, die von jeder Einbettung in dieses Repository verwendet wird). `&autoplay=true` zur automatischen Wiedergabe hinzufügen.
- Transkripte: Fügen Sie `{transcript=true}` zum Shortcode hinzu oder legen Sie `auto-video-transcripts: true` in `TOC.md`/`metadata.md` für das gesamte Handbuch/Repository fest.

## Zeichen

Inline-Badge (wird dort wiedergegeben, wo es platziert wurde):

```markdown
[!BADGE Beta]{type=Informative url="https://www.example.com" tooltip="Go to example.com"}
```

Metadaten-Badge (wird über H1 dargestellt) — in frontmatter:

```yaml
badgePremium: label="Premium" type="Positive" url="https://www.premium-product.com" tooltip="Download Premium"
```

- `type` (Groß-/Kleinschreibung wird nicht beachtet): `Informative` (Standard/Blau), `Positive` (Grün), `Negative` (Rot), `Neutral` (Dunkelgrau), `Caution` (Gelb).
- Nur das Label ist erforderlich; `type`/`url`/`tooltip` optional.
- Maximal **zwei** Metadaten-Badges pro Artikel (konfigurierbar, aber vor Verwendung einer Ausnahme nachfragen).
- Metadaten-Badge-Werte müssen in Anführungszeichen gesetzt werden. Inline-Badge `url`/`tooltip` muss angegeben werden.
- Badge-URLs, die von `TOC.md` verwendet werden, müssen stammbezogen (`/help/guide/article.md`), nicht relativ sein - Inhaltsverzeichniseinträge gelten für Ordner.
- `before-title="false"` verschiebt ein Metadaten-Badge unter das H1.
- Fügen Sie `newtab=true` hinzu, um die Abzeichen-URL in einer neuen Registerkarte zu öffnen.

## Bilder

```markdown
![alt text](assets/logo.png "Hover text"){width="300" align="center"}
```

- `align`: Nur `center` oder `right` - keine `left`, keine `valign`.
- `width`: Pixel (`"300"`) oder Prozentsatz des Ansichtsbereichs (`"50%"`).
- `zoomable="yes"` lässt das Bild anklicken, um es zu vergrößern (nicht mit einem Bild kombinieren, das auch ein Link ist - der Link gewinnt).
- Stammpfad für freigegebene Bilder: `/help/assets/imagename.png`.
- Limits: 100 MB Hard Cap (GitHub), 5 MB bevor Sie anfangen zu pflegen, 20 MB Trigger ein Validierungsfehler. Max. 100 Bilder pro Artikel (EDS-Rendering-Limit).

## Links und Querverweise

- Extern: `[Adobe](https://www.adobe.com)`
- Leere URL als Link: `<https://www.adobe.com>` - eine entpackte leere URL verknüpft **nicht** automatisch.
- Relativer Querverweis: `[Overview](collaborative-doc-instructions/overview.md)` — Auflösung vom Speicherort der *Quelldatei* unterstützt `./`, `../`, `../../`.
- Stammrelativer Querverweis: `[Overview](/help/using/docile-rules/introduction.md)` - funktioniert unabhängig vom Quellspeicherort aus jeder Datei im Repository.
- Deep-Link zu einer Überschrift: Target benötigt `{#heading-id}`; Link mit `[Text](file.md#heading-id)` (oder nur `#heading-id` für dieselbe Seite).
- In neuer Registerkarte öffnen: `[See What's new](whats-new.md){target="_blank"}`.

## Listen

```markdown
1. This is step 1.
1. This is the next step.
   1. Sub-step (indent 3 spaces for numbered lists)
   1. Sub-step
```

```markdown
* First item.
* Second item.
```

- Nummerierte Listen: immer `1.` schreiben (oder immer `1)`) - GitHub rendert die echte Sequenz. Wählen Sie einen Stil aus (`.` vs. `)`) und bleiben Sie innerhalb des Artikels konsistent.
- Aufzählungslisten: Wählen Sie eine von `*`, `-`, `+` und bleiben Sie konsistent - wenn Sie sie im selben Artikel mischen, passiert ein Validierungsfehler. Konvention in den meisten Repogeschäften: `*`.
- Vor und nach einer Liste ist eine leere Zeile erforderlich.
- Inhalte zwischen Listenelementen (Bilder, Tabellen, Notizen) müssen auf den Textanfang eingerückt werden (3 Leerzeichen für nummerierte Listen, 2 für Aufzählungslisten), da sie sonst die Liste umbrechen. Durch das Überziehen von Einzügen (6 Leerzeichen) wird er stattdessen in einen Codeblock umgewandelt.

## Code-Blöcke

Inline: `` `code` `` - oder in dreifache Backticks inline einschließen, wenn ein literaler Backtick drinnen benötigt wird.

Eingezäunt:

&grave;&grave;&grave;&grave;markdown

```javascript
var x = 1;
```

&grave;&grave;&grave;&grave;

- Geben Sie immer eine Sprache für die Syntaxhervorhebung an + die Schaltfläche „Kopieren“.
- Leerzeile erforderlich oberhalb und unterhalb des umzäunten Blocks.
- Zeilennummern: `` ``&#x200B;`html {line-numbers="true"} `&#x200B;&grave;
- Nummerierung an anderer Stelle beginnen: `` ``&#x200B;`html {line-numbers="true" start-line="7"} `&#x200B;&grave;
- Hervorhebungszeilen: `` ``&#x200B;`html {line-numbers="true" start-line="7" highlight="11-13, 16"} `&#x200B;&grave;
- Code-Block-Inhalte werden nie lokalisiert (mit Ausnahme von `!UICONTROL`-/`!DNL`-Tags, die bei der Veröffentlichung entfernt werden).
- Keine Markdown-/HTML-Formatierung (wie `<i>`) funktioniert innerhalb von Code-Blöcken - verwenden Sie spitze Klammern oder einfachen Text für Platzhalter.

## Tabellen

- Standard-GFM-Rohrtabellen funktionieren für einfache Fälle.
- HTML-Tabellen sind für Sonderfälle zulässig (z. B. eine Tabelle ohne Kopfzeile) - Markdown ist andernfalls vorzuziehen.
- Eingeschränktes HTML ist in Markdown-Tabellenzellen zulässig: `<p>`, `<br>`, `<ul>`, `<ol>`.
- Tabellen können auf automatisches oder festes Rendering eingestellt werden - siehe den Artikel „Tabellen“ im Syntaxhandbuch, wenn Sie diese Steuerungsebene benötigen.

## Reduzierbare Abschnitte

```markdown
+++See details

This is text inside a collapsible section.

* Bullet one
* Bullet two

+++
```

- Verschachteln Sie keine ausblendbaren Abschnitte - sie werden nicht korrekt gerendert (und die Validierung schlägt nicht fehl, sodass der Fehler im Hintergrund ausgegeben wird).
- Leere Zeilen um die inneren Listen/Code-Blöcke innerhalb des Abschnitts sind erforderlich, genau wie an anderen Stellen.

## Texthervorhebung

```markdown
This sentence is normal. <span class="preview">This text is highlighted.</span>
```

Verwenden Sie `<span class="preview">` für Inline-/Absatzhervorhebung `<div class="preview">` für mehrere Absätze/Komponenten.

## Snippets und Includes

- Gemeinsame H2-Anker aus der `help/snippets.md` eines Repositorys: Verweis mit `{{anchor-id}}`.
- Freigegebene Include-Dateien aus `help/_includes/*.md`: Verweis mit `{{$include /help/_includes/filename.md}}`.

## Kommentare

```markdown
<!-- standard comment code -->
```

- Verwenden Sie niemals `<!--> bad comment syntax <-->` (fehlende Bindestriche) - es wird sichtbar gerendert, anstatt den Text auszublenden.
- Kommentare sind in den gerenderten Dokumenten unsichtbar, aber **für alle sichtbar, die die rohe .md auf GitHub ansehen** - keine Geheimnisse oder vertraulichen Informationen.
- Vermeiden Sie Kommentare innerhalb von Aufzählungslisten (kann das Listen-Rendering unterbrechen). Kommentieren Sie in `TOC.md` nur Zeilen am Ende der Datei aus, nie in der Mitte der Liste.

## Problemumgehung mit leerer Zeile

Zusätzliche leere Zeilen in der Quelle werden vom Renderer reduziert. Um sichtbaren vertikalen Raum zu erzwingen, platzieren Sie `<br>&nbsp;` an der gewünschten Stelle auf einer eigenen Linie.

## Escape-Zeichen

- Durch umgekehrten Schrägstrich ausblendbare Zeichen: `` # { } [ ] * + - . ! `` — z. B. `\# not a heading`.
- Für spitze Klammern (`<placeholder>`) funktioniert der umgekehrte Schrägstrich nicht - verwenden Sie einen Inline-Code-Block (`` `<placeholder>` ``) oder HTML-Entitäten (`&lt;placeholder&gt;`).
- HTML-Entitäten innerhalb von Codeblöcken werden **nicht** zurück in das Zeichen konvertiert - `&gt;` bleibt dort literaler Text.
- Metadaten (YAML-Frontmatter) verfügen über eigene Escaping-Regeln. Wenn ein Wert mit einem Sonderzeichen wie `:` oder `[` beginnt, geben Sie den gesamten Wert an: `title: "Processing rules: A new beginning"`.

## Eingeschränkte HTML-Zulassungsliste

Nur diese HTML-Tags sind im Markdown überall zulässig. Alles andere ist ein Validierungsfehler:

```
table  tbody  td  tfoot  thead  th  tr  col  colgroup
p  ul  ol  li  br
b  i  strong  u  s  em  sub  sup  span
caption  a  img  div
pre  code  codeblock
```

Markdown-Syntax sollte vor HTML dort stehen, wo Markdown die Aufgabe erfüllen kann - HTML ist in Wirklichkeit nur für Randfälle wie eine kopfzeilenlose Tabelle geeignet.

## Explizit nicht unterstützt (auch nicht verwenden, wenn eine lokale Vorschau sie rendert)

- horizontale Regeln (`***`, `<hr>`)
- Emoji-Kurzcodes (`:bowtie:`)
- Aufgabenlisten (`- [x] done`)
- Blockquote *Komponenten* über die Notiz-/Tabulator-/Video-Shortcodes hinaus (einfache `>`-Blockquotes werden als Zitat und nicht als formatierte Komponente dargestellt)
- Syntax der Markdown-Definitionsliste (stattdessen manuelle Fettformatierung + Bindestrich verwenden: `**Frog** - An amphibious green creature.`)
- `valign`

## Wissenswertes zu Größe/Anzahl der Dateien

| Ding | Beschränkung |
|---|---|
| Größe der Bild-/Download-Datei | Validierungswarnung bei 5 MB, Fehler bei 20 MB, harte GitHub-Kappe 100 MB |
| Bilder pro Artikel | 100 (EDS-Rendering-Limit) |
| Metadaten-Badges pro Artikel | 2 (Standard) |
