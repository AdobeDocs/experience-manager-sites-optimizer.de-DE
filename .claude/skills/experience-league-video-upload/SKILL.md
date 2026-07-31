---
name: experience-league-video-upload
description: Verwenden Sie , wenn ein Benutzer ein Video zur Einbettung über >[!VIDEO] in den Markdown dieses Repositorys an Experience League senden/hochladen möchte (video.tv.adobe.com/KT-Videoübermittlung). In diesem Markdown-Dokument wird das Ausfüllen des Übermittlungsformulars mit Browser-Automatisierung, den Standardeinstellungen dieses Repositorys und den Dingen, die nie automatisiert werden dürfen, behandelt.
source-git-commit: 14f10c231373992c49a8bb93c043556305b6280d
workflow-type: tm+mt
source-wordcount: '840'
ht-degree: 1%

---


# Experience League-Video-Upload

## Überblick

Experience League-Videos werden nicht in diesem Repository gehostet - eine lokale `.mp4` wird über ein separates Übermittlungsformular hochgeladen, das eine `video.tv.adobe.com`-URL zurückgibt, die Sie dann mit `>[!VIDEO](...)` einbetten (siehe [[experience-league-markdown]]). Diese Fähigkeit füllt dieses Formular über die Browser-Automatisierung aus, bis hin zum (nicht eingeschlossenen) Anhängen der Datei und Senden.

Formular: https://81368-exlmpcvideoupload.adobeio-static.net/#/

## Empfehlung für Videodateien

Bevor der Benutzer einen Clip aufzeichnet oder auswählt, empfiehlt er ein **16:9-Seitenverhältnis** bei einer **maximalen Auflösung von 1920 x 1080 Pixel** - dies ist die erklärte Anforderung des Formulars, nicht nur eine Stilvorgabe. Erwähnen Sie es proaktiv (z. B. wenn ein Benutzer sagt, dass er eine Bildschirmaufzeichnung dafür aufnehmen möchte), nicht nur auf Anfrage.

## Harte Regel: Datei nie anhängen oder senden

Die Übermittlung erstellt ein echtes KT Jira-Ticket und lädt es auf die Video-Produktionsplattform hoch - eine nach außen gerichtete, schwer rückgängig zu machende Aktion. **Immer** Anhalten, sobald jedes zweite Feld ausgefüllt ist, und zurückgeben an den Benutzer für die Videodatei und den endgültigen Sendeklick, auch wenn er die Anweisung beim nächsten Mal nicht wiederholt. Dies ist die Standardeinstellung für diese Qualifikation, nicht etwas, das pro Anfrage erneut bestätigt werden muss - überspringen Sie diesen Stopp nur, wenn der Benutzer explizit sagt, dass er ihn in derselben Anfrage übermitteln soll.

## Voraussetzungen

benötigt den `chrome-devtools` MCP-Server, der **nicht** diesem Repository zugewiesen ist (ein MCP zur Browserautomatisierung sollte nicht jedem Mitwirkenden aufgezwungen werden). Wenn er nicht geladen wird:

1. Erstellen Sie `.mcp.json` im Repository-Stamm:

   ```json
   {
     "mcpServers": {
       "chrome-devtools": {
         "command": "npx",
         "args": ["-y", "chrome-devtools-mcp@latest", "--accept-insecure-certs", "--no-usage-statistics"]
       }
     }
   }
   ```

2. `.mcp.json` zu `.gitignore` hinzufügen (persönliche Tools, nicht freigegeben).
3. Fügen Sie `.claude/settings.local.json` `"enableAllProjectMcpServers": true` und `"enabledMcpjsonServers": ["chrome-devtools"]` hinzu.
4. Der Benutzer soll Claude-Code neu starten (oder `/mcp` ausführen) - MCP-Server werden nur beim Start geladen. Dies kann nicht während der Sitzung geschehen.

## Die Standardeinstellungen dieses Repositorys

Sofern der Benutzer nichts anderes sagt, verwenden Sie:

| Feld | Standard | Vorteile |
|---|---|---|
| Cloud | `Experience Cloud` | — |
| Produkt | `AEM` | Benutzerdefinierter Standard für dieses Repository (im Formular wird auch `AEM as a Cloud Service` aufgelistet - nicht ersetzen, es sei denn, es wird dazu aufgefordert) |
| Unterprodukt | `AEM Sites` | Nächste Übereinstimmung; das Formular hat keinen Eintrag &quot;Sites Optimizer&quot; |
| Rollen | `User` | Preflight-/Sites Optimizer-Inhalte richten sich an Autoren/Marketing-Experten, nicht an Administratoren/Entwickler, es sei denn, das Video ist eindeutig für eine technische Zielgruppe vorgesehen |
| SKILL levels | `Beginner` | Es sei denn, der angezeigte Workflow hat echte Voraussetzungen |
| Video Stimme(n) Geschlecht | `No voices` | Nur für stille Bildschirmaufnahmen - fragen, ob der Clip eine Sprechstimme hat |
| Videotyp | Fragen oder Ableiten aus Inhalten | Live-Optionen sind `Event` / `Feature` / `Technical` / `Value` — eine exemplarische Vorgehensweise der Benutzeroberfläche wird normalerweise `Feature` |
| E-Mail | Was vorausgefüllt ist | Das Formular füllt die Adobe-E-Mail-Adresse des angemeldeten Benutzers automatisch aus; nicht überschreiben |

## Schritte

1. `mcp__chrome-devtools__new_page` zur Formular-URL.
2. `mcp__chrome-devtools__take_snapshot` und warten (`mcp__chrome-devtools__wait_for` auf `"Title"`), bis das Laden der Formulardaten abgeschlossen ist - sie beginnen mit „Formulardaten werden geladen …“ Spinner.
3. Fill **Title** and **Description** — Description ist ein inhaltsbearbeitbares Rich-Text-Feld, kein einfaches `<textarea>`. `fill`/`fill_form` im Hintergrund kein Opt-up (der Wert benötigt nicht und der Fehler „erforderlich“ bleibt bestehen). Stattdessen: `click` es fokussieren, dann mit dem Text `mcp__chrome-devtools__type_text`.
4. Die Dropdown-Listen **Videotyp**, **Videostimme(n),**, **Cloud**, **Produkt**, **Unterprodukt**, **Ereignisname**) sind benutzerdefinierte Listenfeld-Schaltflächen, nicht native `<select>`. Für jede(n): `click` die Schaltfläche zum Öffnen, lesen Sie die echten Optionen aus dem Snapshot (sie werden über die API geladen — gehen Sie nicht davon aus, dass die exakte Schreibweise der Option der Standardtabelle noch aktuell ist) und `click` Sie dann die entsprechenden `option`.
5. **Produkt** und **Unterprodukt** sind deaktiviert, bis das übergeordnete Feld festgelegt ist (Produkt benötigt Cloud; Unterprodukt benötigt Produkt) - Füllen Sie sie in dieser Reihenfolge aus.
6. **Rollen** und **Qualifikationsstufen** sind Kontrollkästchen-Gruppen - `fill_form` mit `"value": "true"` auf dem `uid` funktioniert hier einwandfrei (im Gegensatz zum Beschreibungsfeld).
7. Stopp. Erstellen Sie einen Screenshot, fassen Sie zusammen, was festgelegt wurde und warum (insbesondere alle ersetzten Standardwerte wie Produkt/Unterprodukt), und weisen Sie den Benutzer an, das Video anzuhängen und sich selbst zu übermitteln.
8. Nachdem der Benutzer angegeben hat, dass er gesendet hat, fragen Sie ihn nach der resultierenden Adobe MPC-Video-URL (die nach dem Hochladen im Formular angezeigt wird, z. B. `https://video.tv.adobe.com/v/3496629?learn=on`). Benutzen Sie sie, um die `>[!VIDEO](...)` auszufüllen, wohin auch immer dieses Video gehen sollte - erfinden oder erraten Sie die URL/ID nicht selbst.

## Validieren der zurückgegebenen Video-URL

Wenn ein(e) Benutzende(r) Ihnen eine einzubettende Video-URL gibt (Schritt 8 oben oder ein anderes Mal):

- **Alles ablehnen, was nicht auf `video.tv.adobe.com` steht.** Videos müssen dort pro [[experience-league-markdown]] gehostet werden — ein Link zu YouTube, einem Datei-Host oder einer anderen Domain ist kein gültiges `>[!VIDEO]`. Weisen Sie den Benutzer an, dass er zuerst den Upload-Fluss dieses Repositorys durchlaufen muss; betten Sie ihn nicht ein.
- **Wenn bei einer gültigen `video.tv.adobe.com`-URL `&enablevpops` fehlt, fügen Sie sie** vor der Einbettung hinzu (entspricht der bereits von allen anderen `>[!VIDEO]` in diesem Repository verwendeten Konvention - siehe `help/home.md`, `help/documentation/trial.md` usw.). `&enablevpops` anhängen, wenn bereits ein `?` vorhanden ist, andernfalls `?enablevpops`.

## Häufige Fehler

- Es wird `fill`/`fill_form` mit dem Feld „Beschreibung“ versucht und der Vorgang wird fortgesetzt, wenn das Fehlerbanner noch „Eine Beschreibung ist erforderlich“ anzeigt. — Überprüfen Sie die Fehlerliste nach jedem Schritt, nicht nur am Ende.
- Dropdown-Optionstext aus dem Speicher raten, anstatt die Dropdown-Liste zu öffnen - die tatsächlichen Werte (z. B. `No voices` für das Sprach-Geschlecht, `Feature`/`Technical`/`Value` für den Videotyp, die Aufteilung von AEM/AEM-as-a-Cloud-Service unter „Produkt„) sind nicht raten und ändern sich unabhängig von diesem Dokument.
- Durch Klicken auf **Video hochladen** / Anhängen einer Datei „speichern Sie den Benutzer einen Schritt.“ Nicht - siehe Hard rule oben.
