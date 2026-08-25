---
source-git-commit: ed1960cc0364dc4169a454a4860b7463890e3b74
workflow-type: tm+mt
source-wordcount: '2275'
ht-degree: 0%

---
# ASO-Dokumentagent - Pipeline

Referenziert von `SKILL.md`. Dies ist die Quelle der Wahrheit für die Ausführungsreihenfolge; SKILL.md ist
Zusammenfassung. `config.yml` vor dem Start lesen — jeder Wert in `{braces}` unten ist eine
Konfigurationsschlüssel.

**Fehlerbehandlung (gilt für jeden Schritt unten).** Ein Tool/API-Aufruf mit Fehlern (Authentifizierung)
Fehler, Zeitüberschreitung, fehlerhafte Abfrage, unerwartetes Schema) ist nie dasselbe wie ein
Legitimatives leeres Ergebnis und darf niemals stillschweigend in eine
Zweig „leer“ oder „nichts zu tun“ (z. B. Schritt 1.2&#39;s „hier nichts zu tun“, Schritt 3.3&#39;s
„epischer Rückstand vollständig abgedeckt oder alles im Flug„). Wenn ein -Aufruf fehlschlägt, stoppen und protokollieren Sie die
Tatsächlicher Fehler in der Ausführungszusammenfassung, anstatt weiterzumachen, als ob er sauber zurückgegeben würde.

## Schritt 0 — PreFlight

1. `pwd` und überprüfen Sie, `guidelines.md` + `.claude/skills/aso-doc-agent/config.yml` beide vorhanden sind. Wenn nicht, stoppen — falsches Verzeichnis.
2. `gh auth status` - Bestätigen Sie, dass das `sandsinh_adobe`-Konto über ein gültiges Token auf diesem Host verfügt. **Nie`gh auth switch`** ausführen - Es wird das computerweite aktive `gh`-Konto als Nebeneffekt umgedreht, was dazu führen kann, dass jedes andere Terminal/jeder andere Prozess auf diesem Computer im Hintergrund für einen unbeaufsichtigten täglichen Durchlauf auf das falsche Konto geladen wird. Berechnen Sie stattdessen diese Ausführung nur so, dass sie einmal am Start `export GH_TOKEN=$(gh auth token --user sandsinh_adobe)` wird, sodass jeder `gh` unten aufrufende Aufruf dieses Token über die `GH_TOKEN` env var verwendet, unabhängig davon, welches Konto global aktiv ist.
3. `mkdir -p {state_dir}`, wenn nicht vorhanden.
4. `{state_dir}/run-state.json` lesen, falls vorhanden (andernfalls wie `{"runs_completed": 0, "tracked_prs": []}` behandeln). `tracked_prs` ist die eigene Liste dieses Agenten mit `{number, headRefName, key}` für PRs, die er geöffnet hat. Wird nur verwendet, um einen PR zu erkennen, der ohne Zusammenführung geschlossen wurde (Schritt 1.5), da `gh pr list --state open` allein ihn nicht mehr sehen kann, wenn er weg ist. Das Timing von Medienanfragen liegt in einer separaten Datei, `{state_dir}/media-requests.json` (Schritt 5) - GitHub und Jira bleiben die Quelle der Wahrheit für alles andere (PR-Status, Ticketstatus).
5. `--ticket KEY` vorhanden -> überspringen Sie die automatische Auswahl von Schritt 3, verwenden Sie die -Taste direkt (führt noch die Schritte 4-7 aus). Wählen Sie andernfalls in Schritt 3 automatisch aus.

## Schritt 1: Vorherige Ausführungen abstimmen

Führen Sie diesen Befehl jedes Mal aus, auch bei eingeschränkter oder anderweitig leerer Ausführung.

1. `gh pr list --repo {github.repo} --label {github.pr_label} --state open --json number,url,isDraft,headRefName,title,reviewDecision`
2. **Überprüfung - jede offene PR, jeden Durchlauf** (`pr.check_reviews_every_run`):
   - `gh pr view <number> --repo {github.repo} --json reviewDecision,reviews,comments`
   - `reviewDecision == "APPROVED"` -> Jetzt zusammenführen: `gh pr merge <number> --repo {github.repo} --merge`. Überprüfen Sie, ob die Zusammenführung tatsächlich gelandet ist (`gh pr view <number> --json state,mergedAt` — `state == "MERGED"`), bevor Sie sie als erledigt behandeln. Eine Zurückweisung der geschützten Verzweigung oder eine noch ausstehende erforderliche Prüfung können die PR offen lassen, selbst nachdem `gh pr merge` aufgerufen wurde. Dies muss als Fehler protokolliert werden und darf Jira nicht als zusammengeführt gemeldet werden (dies ist eine normale von Menschen genehmigte Zusammenführung, keine zeitüberschreitende). Bei bestätigter Zusammenführung: Kommentar zum verknüpften Jira-Ticket, das zusammengeführt wurde, PR aus `tracked_prs` ablegen.
   - `reviewDecision == "CHANGES_REQUESTED"` -> **den PR in dieser** nicht automatisch korrigieren. Lesen Sie die Überprüfungskommentare (`gh api repos/{github.repo}/pulls/<number>/comments` für Inline-Kommentare sowie den obersten Überprüfungstext aus dem Feld `reviews`) und führen Sie **Lernen aus Feedback** aus. Protokollieren Sie den PR als ausstehende Autorenaktion in der Ausführungszusammenfassung. Wenn diese PR länger als `pr.stale_after_hours` ohne Update `CHANGES_REQUESTED` wurde, kennzeichnen Sie sie als veraltet für das Kappentor von Schritt 2 - sie bleibt für einen Menschen geöffnet, belegt jedoch keinen Kappenschlitz mehr.
   - Alles andere (noch keine Bewertungen, `REVIEW_REQUIRED` ohne eingereichte Bewertung) -> hier nichts zu tun.
3. **Lernen aus Feedback.** Für jeden Überprüfungskommentar oder Überprüfungstext, der als *verallgemeinerbarer* Hinweis zu Ton, Struktur oder Inhalt liest - keine einmalige Fehlerbehebung, die spezifisch für diese PR ist (vergleichen Sie „ignorieren Sie immer die Registerkarte für Möglichkeiten mit Ignorieren-Support“ mit „Tippfehler in Zeile 12„) -, fügen Sie einen datierten, mit einem Ticket verknüpften Eintrag an `references/review-learnings.md` an. Überspringen Sie rein mechanisches Feedback (Tippfehler, fehlerhafte Links, Fußzeile) - reparieren Sie diese in der PR selbst, sie brauchen keine dauerhafte Lektion. Das genaue Eingabeformat ist in dieser Datei dokumentiert.
4. Extrahieren Sie für jeden **Entwurf** PR in dieser Liste den Jira-Schlüssel aus dem Zweignamen (`{github.branch_prefix}<KEY>-...`).
   - `mcp__Corp-Jira__list_attachments` + `mcp__Corp-Jira__get_jira_comments` auf diesem Schlüssel.
   - Suchen Sie nach einem neuen Bildanhang, der mit der angeforderten Erfassung übereinstimmt, ODER nach einem Kommentar, der eine `video.tv.adobe.com` URL enthält.
   - Wenn gefunden: `git fetch`/`checkout` Sie die Verzweigung, fügen Sie das Bild zu `help/**/assets/` hinzu (wenn es sich um einen Bildanhang handelt, über `download_attachment` herunterladen) oder füllen Sie den `>[!VIDEO](...)` Platzhalter aus (wenn es sich um einen Video-URL-Kommentar handelt), validieren Sie anhand von `experience-league-markdown`, Commit, Push, `gh pr ready <number>`, kommentieren Sie die PR „Medien hinzugefügt — bereit zur Überprüfung“. Aktualisieren Sie `{state_dir}/media-requests.json` Eintrag auf `resolved`.
   - Wenn nicht gefunden: Überprüfung der seit der Anfrage in `{state_dir}/media-requests.json` verstrichenen Zeit. Wenden Sie auch hier die Eskalations-/Aufgabelogik aus Schritt 5 an (ein PR-Entwurf, der über mehrere Durchgänge hinweg offen gelassen wurde, muss weiterhin von den Medien gejagt werden) - einschließlich des `gh pr ready`-Aufrufs des Aufgabepfads, sodass ein aufgegebener Entwurf weiterhin überprüfbar ist, anstatt hängen zu bleiben.
5. **Erkennen von geschlossenen PRs ohne Zusammenführung.** Vergleichen Sie die Open-PR-Liste dieses Durchgangs (Schritt 1) mit `tracked_prs` aus `run-state.json`. Jede verfolgte PR, die in der offenen Liste fehlt und in Schritt 2 nicht bestätigt wurde, wurde ohne Zusammenführung geschlossen - bevor sie abgelegt wurde, ihren endgültigen Status abrufen (`gh pr view <number> --repo {github.repo} --json reviews,comments`) und **Aus Feedback**) ein letztes Mal ausführen, damit die Ablehnungsbegründung eines Menschen nicht verloren geht. Dann aus dem Tracking streichen. Auf dem Ticket selbst ist keine weitere Aktion erforderlich: Da das Anspruchsetikett nur zur Veröffentlichungszeit angewendet wird (Schritt 6.10), hat ein geschlossenes, nicht zusammengeführtes Ticket bereits keine Kennzeichnung, und die Prüfungen von Schritt 3.2 (keine offenen/zusammengeführten PR) machen es natürlich berechtigt, bei einem zukünftigen Durchlauf erneut ausgewählt zu werden.
6. Legen Sie `tracked_prs` in `run-state.json` auf die aktuelle offene PR-Liste (`number`, `headRefName` und der aus dem Zweignamen geparste Jira-Schlüssel) fest, damit der Schritt 5 des nächsten Durchgangs übereinstimmt.

## Schritt 2 — PR-Kappentor

1. Offene PRs aus der `gh pr list` von Schritt 1 zählen, mit Ausnahme von PRs, die in Schritt 1.2 als veraltet gekennzeichnet `CHANGES_REQUESTED` (länger als `pr.stale_after_hours` geöffnet, ohne Aktualisierung) - diese bleiben für einen Menschen offen, belegen aber keinen Deckelschlitz mehr.
2. Wenn count >= `{pr.max_open}` (3): `"cap reached ({count}/{pr.max_open} open) — skipping new ticket this run"` protokollieren, mit Schritt 7 fortfahren.
3. Fahren Sie andernfalls mit Schritt 3 fort.

## &#x200B;3. Schritt - Ticket auswählen

Wenn `--ticket KEY` übergeben wurde, wird der Vorgang vollständig übersprungen (KEY verwenden).

```
JQL: "Epic Link" = {jira.epic} AND status = "{jira.open_status}"
     ORDER BY priority DESC, created ASC
```

1. Führen Sie die Suche aus (`mcp__Corp-Jira__search_jira_issues`, `minimizeOutput: true`, Felder mit Beschränkung auf `key,summary,priority,status,labels`).
2. Ergebnisse in der richtigen Reihenfolge durchgehen. Jedes Ticket überspringen, das:
   - hat bereits die `{jira.picked_label}` ODER
   - hat bereits eine Verzweigung `{github.branch_prefix}<KEY>-*` auf der Remote-Instanz (`git ls-remote --heads origin '{github.branch_prefix}<KEY>-*'`), ODER
   - hat bereits eine offene oder zusammengeführte PR (Abgleich mit der Liste/`gh pr list --state all --search <KEY>` von Schritt 1).
3. Das erste Ticket, das alle drei Schecks besteht, ist die Auswahl. Wenn keiner der **besteht (da die Suche tatsächlich null geeignete Tickets zurückgegeben hat** melden Sie sich `"epic backlog fully covered or all in flight"` und fahren Sie mit Schritt 7 fort. Wenn die Suche selbst fehlgeschlagen ist (Authentifizierungsfehler, Zeitüberschreitung, fehlerhafte JQL), ist dies nicht der Fall - protokollieren Sie stattdessen den tatsächlichen Fehler (siehe Fehlerbehandlung oben).
4. Kennzeichnen **das** noch nicht - das Anspruchsetikett wird in Schritt 6.10 nur angewendet, wenn tatsächlich eine Verzweigung und ein PR vorhanden ist. Die Schritte 4-5 (Recherche/Entwurf/Medien) können fehlschlagen oder abstürzen, ohne eine Spur auf dem Ticket zu hinterlassen; die einzigen laufenden Signale vor Schritt 6 sind die oben genannten Prüfungen der Zweigexistenz/PR-Existenz, was ausreichend ist, wenn dies von einem einzigen Gerät ohne echte Gleichzeitigkeit läuft.

## Schritt 4 — Forschung + Entwurf

Die Forschung kommt zuerst und ist **multi-source** — niemals aus einem einzigen Input (der Jira
Ticket allein oder nur Lesen von gleichrangigen Dokumenten). Jede unten stehende Quelle bestätigt oder
Korrigiert die anderen; Widersprüche werden aufgelöst, indem Quellcode vertraut wird > Wiki/PR-Dokumente >
Slack-Diskussion > Die eigene Schlussfolgerung des Autors/der Autorin, in dieser Reihenfolge, und werden inline markiert
wie `<!-- CONFIRM -->`, wenn sie nicht aufgelöst werden können.

&#x200B;0. **Gesammelte Prüfungslektionen.** `references/review-learnings.md` zuerst lesen. Alles darauf anwenden, was für das Thema dieses Tickets vor dem Entwurf relevant ist - so verbessert das Feedback aus vergangenen PR-Reviews zukünftige Entwürfe, anstatt dieselbe Korrektur zu wiederholen.

### Forschung (alles, was zutrifft - nicht direkt zum Entwurf springen)

1. **Source-Code (grundlegende Wahrheit für die tatsächliche Funktionsweise).** Durchsuchen Sie das primäre Benutzeroberflächen-Repository (`research.code_repos` in config.yml) nach dem Adapter/Handler der Funktion (`*OpportunityAdapter.tsx`, `*SuggestionAdapter.tsx`), ihrem Datenhook (`use*Data.ts`) und ihren `.l10n.ts`/`.I10n.ts` Titel-/Beschreibungszeichenfolgen. Dies ist die Autorität für Feldnamen, Datenform, Kategorie und exakte Produktkopie - bevorzugen Sie sie vor allem dann, wenn die Quellen nicht übereinstimmen.
2. **Wiki (Design Intent, Spezifikationen, Entscheidungen).** `mcp__Adobe-Wiki__search_wiki_content` mit dem Funktions-/Opportunity-Namen und dem epischen/Ticket-Schlüssel. Passende Seiten lesen (`get_wiki_content`) für: Warum die Funktion existiert, Terminologie, die das Produkt-Team verwendet, dokumentierte UX-Fluss- oder Edge-Fälle und alle eingebetteten Screenshots, die zeigen, wie die echte Benutzeroberfläche aussieht (informiert die Media Capture-Spezifikation in Schritt 5, ersetzt keinen tatsächlichen neuen Screenshot, es sei denn, die Seite ist aktuell).
3. **Slack (Wie das Team tatsächlich darüber spricht, offene Fragen, aktuelle Änderungen).** `mcp__Slack__slack_search_messages` mit dem Funktions-/Opportunity-Namen und dem Ticket-Schlüssel, nicht eingeschränkt durch den Kanal, es sei denn, `research.slack_channels` engt ihn in config.yml ein. Achten Sie auf: Ankündigungsnachrichten (häufig mit dem sauberen kundenorientierten Framing), Design-Diskussions-Threads und alles, was darauf hinweist, dass die Funktion kürzlich so geändert wurde, dass gleichrangige Dokumente oder Code-Kommentare noch nicht widergespiegelt werden.
4. **GitHub-PR-Verlauf (Implementierungsrationalität, Screenshots, Überprüfungsdiskussion).** `gh search prs --repo <repo> "<feature name>"` oder `gh pr list --repo <repo> --search "<ticket key OR feature name>" --state all` in allen `research.code_repos`. Lesen Sie zusammengeführte PR-Beschreibungen für Begründungen, verknüpfte Design-Dokumente und Screenshots, die das Verhalten erläutern, das der Code allein nicht erklärt (z. B. warum ein Fehlerbehebungstyp erfasst wird, wie ein Randfall in der Benutzeroberfläche aussieht).
5. **Tonanaloga.** Suchen Sie basierend auf der Ticket-Zusammenfassung 2 bis 3 vorhandene Seiten, die der nächsten liegen:
   - &quot;… Anleitungstickets für Opportunities -> 2 gleichrangige Dateien in `help/documentation/opportunities/` lesen (der tatsächliche Anleitungsort für die einzelnen Opportunities - `help/opportunity-types/*.md` sind die Kategorie-Landingpages mit Kartenrastern, die auf diese verlinken, nicht die Anleitungsinhalte selbst).
   - Einstellungen/Workflow/Verbindungs-Tickets -> Lesen Sie die gleichrangigen 1-2 Dateien in `help/documentation/` (überprüfen Sie `setup/`, `opportunities/`, `settings.md`, `basics.md` auf die engste Übereinstimmung).
     Struktur der Mirrorüberschriften, Verwendung im Notizfeld, Satzlänge, technischer Detaillierungsgrad.
6. **Formatregeln.** Lesen Sie `experience-league-markdown` Kurzreferenz der Kenntnisse erneut, bevor Sie schreiben. Jede Überschrift/Anmerkung/Bild/Link muss genau mit ihrer Syntax übereinstimmen.

### Entwurf

&#x200B;7. **Target-Dateientscheidung.** Es wird empfohlen, den relevanten Abschnitt einer vorhandenen Seite zu erweitern, anstatt eine neue Datei zu erstellen, es sei denn, das Ticket entspricht der Granularität vorhandener eigenständiger Seiten (z. B. erhält jede Opportunity eine eigene Datei unter `help/documentation/opportunities/` - eine neue Datei folgt der exakten Struktur eines vorhandenen gleichrangigen Elements). Wenn Sie eine vorhandene Seite erweitern, tippen Sie nur auf den einen Abschnitt für dieses Ticket - bearbeiten Sie keine nicht verwandten Abschnitte, selbst wenn sie veraltet sind. Wenn Sie eine neue eigenständige Seite erstellen, fügen Sie auch ihre -Karte zur entsprechenden `help/opportunity-types/*.md`-Landingpage hinzu (Quellkommentarliste + generierter HTML-Block, der dem exakten Muster vorhandener Karten entspricht) und registrieren Sie sie in `help/main-toc/TOC.md`.
&#x200B;8. **Entwurf v1.** Schreiben Sie den Inhalt jetzt (im Speicher/von Grund auf, noch nicht in die Repository-Datei - dies geschieht in Schritt 6 nach der Medienentscheidung, sodass ein Dokument mit ausstehendem Medium und ein Dokument mit Medienauflösung denselben Schreibpfad durchlaufen). Synthetisieren Sie alle Schritte 1-6 - wiederholen Sie nicht nur die Jira-Ticketbeschreibung.
&#x200B;9. **iterieren.** Lesen Sie den v1-Entwurf noch einmal gegen alle Forschungsergebnisse aus den Schritten 1-4: Wurde beim Entwurf etwas von Slack oder Wiki verpasst? Widerspricht es dem, was der Quell-Code tatsächlich tut? Passt er so gut zum gleichrangigen Ton wie möglich? Überarbeiten Sie dies, bevor Sie fortfahren. Dies ist ein echter zweiter Durchgang und keine Formalität. Alles, was nach diesem Durchgang noch wirklich unbestätigt ist (in keiner der vier Quellen zu finden), erhält einen Inline-`<!-- CONFIRM -->`-Kommentar statt einer Vermutung.
&#x200B;10. **Medienentscheidung.** Entscheide `mediaNeeded: true|false`.
    - `true` wenn die Funktion ein mehrstufiger UI-Workflow ist, bei dem eine textliche Beschreibung allein wesentlich schwieriger zu befolgen wäre (entspricht „umsichtig verwendet… wenn eine textliche Beschreibung nicht ausreicht“ von `guidelines.md`).
    - Wenn `true`, erstellen Sie: `mediaType` (`screenshot` oder `video`), `captureSteps` (exakte Schritte zum Reproduzieren des zu erfassenden Status), `urls` (URL(s) für kundenorientierte Apps und/oder interne Seiten-URL(s), die zum Erreichen dieses Status erforderlich sind - rufen Sie echte URLs aus der Beschreibung/den Kommentaren, dem Wiki oder `open-aso-devmode-url` Konventionen von Jira ab, falls dort referenziert; erfinden Sie nie eine URL).
    - Falls `false`, überspringen Sie Schritt 5 für dieses Ticket.

## Schritt 5: Medien-Gate

Wird nur ausgeführt, wenn Schritt 4 auf `mediaNeeded: true` gesetzt ist. Alle Zeitstempel in
`{state_dir}/media-requests.json` sind UTC ISO-8601 (`date -u +%Y-%m-%dT%H:%M:%SZ`) —
Schreiben und vergleichen Sie immer in diesem Format, sodass die unten stehende Mathematik der verstrichenen Zeit eindeutig ist
Über Läufe hinweg.

1. Überprüfen Sie, `{state_dir}/media-requests.json` ein vorhandener Eintrag für diesen Ticketschlüssel vorhanden ist. Wenn nicht, handelt es sich um eine neue Anfrage.
2. **Neue Anfrage:**
   - `mcp__Slack__slack_lookup_user` auf `media.contacts_in_order[0].email` (Sandsinh), um die Slack-Benutzer-ID abzurufen.
   - `mcp__Slack__slack_send_dm` mit einer Nachricht, die Folgendes enthält: den Jira-Ticketschlüssel + -Link, genau das, was erfasst werden soll (`captureSteps`), die zu verwendenden URLs und wohin die Antwort gehen soll („Antwort auf das Jira-Ticket - Screenshot direkt anhängen oder für Videos über das übliche Experience League-Videoformular hochladen und den resultierenden `video.tv.adobe.com`-Link als Kommentar einfügen„).
   - `{state_dir}/media-requests.json[KEY] = {requestedTo: "sandsinh", requestedAt: <UTC ISO-8601 now>, escalated: false}` schreiben.
3. **Bestehende Anfrage:** werden beide unten stehenden Schwellenwerte von der ursprünglichen `requestedAt` aus gemessen — durch Eskalation wird die Uhr nicht zurückgesetzt:
   - `now - requestedAt` &lt; `media.escalate_after_hours` -> nichts in dieser Ausführung tun, mit der Veröffentlichung mit noch ausstehenden Medien fortfahren (PR-Entwurf).
   - `now - requestedAt` >= `media.escalate_after_hours` und noch nicht eskaliert -> DM `media.contacts_in_order[1]` (kanishka), Nachrichten Hinweise Sandsinh wurde bereits vor N Stunden ohne Antwort gefragt. Eintrag aktualisieren: `escalated: true, escalatedAt: <UTC ISO-8601 now>`.
   - `now - requestedAt` >= `media.give_up_after_hours` (unabhängig vom Eskalationsstatus) -> `mediaNeeded: false` zu Veröffentlichungszwecken festlegen, Inline-Hinweis in den Entwurf einfügen: `>[!TIP]\n>\n>A screenshot for this step is being added in a follow-up update.` Wenn für dieses Ticket bereits eine PR existiert und es sich weiterhin um einen Entwurf handelt (hier über Schritt 1.4 erreicht, nicht um eine neue Veröffentlichung von Schritt 6), Verzweigung `git fetch`/auschecken, die Anmerkung anwenden, übertragen, Push senden und `gh pr ready <number>` aufrufen - ein gegebener aufgegebener Entwurf muss weiterhin überprüfbar sein und nicht auf unbestimmte Zeit hängen bleiben. Eintrag `gaveUp: true`.

## Schritt 6: Veröffentlichen

Überspringen Sie diesen Schritt, wenn das Ticket in Schritt 3 vollständig übersprungen wurde (nichts zu veröffentlichen).

1. `git fetch origin` und `git checkout -B {github.branch_prefix}<KEY>-<short-slug> origin/main` - `-B` (nicht `-b`), sodass eine übrig gebliebene lokale Verzweigung aus einem abgestürzten vorherigen Durchlauf zurückgesetzt wird, anstatt das Auschecken zu blockieren. Durch die Verzweigung direkt aus `origin/main` wird auch jeder verschmutzte lokale Status aus einem vorherigen Absturz verworfen, anstatt ihn zu beschädigen.
2. Schreiben Sie den Entwurf für Schritt 4 in die Zieldatei, die in Schritt 4.3 festgelegt wurde. Überprüfen Sie die Checkliste `experience-league-markdown` Zeile für Zeile erneut anhand der Checkliste „Vor dem Bestätigen von Markdown-Änderungen“.
3. Wenn ein Markdown-Linter konfiguriert ist (`markdownlint_custom.json` im Repository-Stamm) und `markdownlint-cli`/`npx markdownlint` verfügbar ist, führen Sie ihn für die geänderten Dateien aus und beheben Sie etwaige Verstöße, bevor Sie einen Commit durchführen.
4. Bestätigung: `docs(aso): <ticket summary, lowercase, no trailing period>\n\nSITES-XXXXX`.
5. `git push -u origin <branch>`.
6. Reviewer-Auswahl: `gh pr list --repo {github.repo} --label {github.pr_label} --state open --json reviewRequests` — zählen Sie, wie viele aktuell jede der beiden konfigurierten Reviewer auflisten; weisen Sie zu, wer weniger hat (Zeit -> `sandsinh_adobe`).
7. PR-Textkörper:

   ```
   ## Summary
   [1-2 sentence description of the feature now documented]
   
   ## Source
   Closes documentation gap tracked in [SITES-XXXXX](https://jira.corp.adobe.com/browse/SITES-XXXXX)
   
   ## Media
   [either "No media needed for this update." OR "Screenshot/video requested from {contact} on {date} — PR opened as draft until resolved." OR "Media follow-up pending — shipped without it; see inline note."]
   
   > 🤖 Drafted by aso-doc-agent
   ```

8. `gh pr create --repo {github.repo} --title "<ticket summary>" --body "<above>" --label {github.pr_label} --reviewer <chosen-github-handle> --draft` wenn das Medium noch aussteht, lassen Sie `--draft` weg.
9. `gh pr edit <number> --add-label {github.pr_label}` wenn das Kennzeichen nicht übernommen wurde (Gürtel und Hosenträger, entspricht dem Muster, das an anderer Stelle in den Tools dieser Organisation verwendet wird).
10. Jira: `add_jira_comment` Verknüpfen der PR-URL und jetzt - zum ersten Mal in dieser Ausführung - `{jira.picked_label}` hinzufügen (`update_jira_issue` mit vorhandenen Kennzeichnungen zusammenführen). Dies ist die Behauptung, bewusst nur einmal eine Verzweigung und PR beide existieren: ein Absturz irgendwo in den Schritten 3-5 lässt das Ticket komplett unbeschriftet und sicher wieder pickbar, anstatt dauerhaft hängen zu bleiben. Ticketstatus nicht übergeben - überlassen Sie das der eigenen Triage des Dokumentations-Teams; `{jira.picked_label}` ist das einzige Statussignal, das dieser Agent schreibt.

## Schritt 7 - Zusammenfassung des Durchgangs

1. `{state_dir}/run-state.json` aktualisieren: `runs_completed += 1`, Zeitstempel, ausgewähltes Ticket (oder „keine“ + Grund), PR geöffnet/aktualisiert (oder „keine“ + Grund), Begrenzungsstatus.
2. Drucken Sie eine kurze, für Menschen lesbare Zusammenfassung (Ticket, durchgeführte Aktion, PR-Link, Medienstatus).
