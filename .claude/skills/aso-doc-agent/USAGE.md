---
source-git-commit: ed1960cc0364dc4169a454a4860b7463890e3b74
workflow-type: tm+mt
source-wordcount: '879'
ht-degree: 0%

---
# ASO Doc Agent - Verwendung

Was das ist, wie es läuft und was zu tun ist, wenn es dich braucht.

## Funktion

Dieser Agent wählt täglich die ASO-Funktion mit der höchsten Priorität aus
[SITES-49539](https://jira.corp.adobe.com/browse/SITES-49539)&#39;s Backlog (39 Tickets, z.B.
„Canonical Opportunity How-to“, &quot;Slack-Benachrichtigungen„), schreibt eine Dokumentation
für das im Hausstil dieses Repositorys, und öffnet ein PR - wobei einer von den beiden zugewiesen wird
Konfigurierte Reviewer (`sandsinh_adobe`/`kanishka_adobe`) haben derzeit weniger offene
Anforderungen dieses Agenten überprüfen. Wenn für die Funktion ein Screenshot oder Video benötigt wird, werden Sie aufgefordert,
eine über Slack, bevor Sie die PR abschließen.

Bei jeder Ausführung wird auch der Prüfungsstatus bei jeder geöffneten PR überprüft: Genehmigte PRs werden zusammengeführt
Sofort wird das von Benutzern und Änderungen angeforderte Feedback gelesen und gesendet, wenn es sich um ein verallgemeinerbares
Lektion (kein einmaliger Tippfehler), aufgezeichnet, damit zukünftige Entwürfe nicht denselben Fehler wiederholen.

Ein Durchgang = eine Funktion = höchstens ein PR. Es berührt nie mehr als ein Ticket pro Lauf,
und öffnet nie mehr als 3 PRs gleichzeitig (wartet darauf, dass vorhandene zusammengeführt/geschlossen werden).

## Wo alles lebt

| Was | Pfad |
|---|---|
| Wie er entscheidet, was zu tun ist | `.claude/skills/aso-doc-agent/SKILL.md` |
| Die genaue Schrittweise | `.claude/skills/aso-doc-agent/references/pipeline.md` |
| Team-spezifische Einstellungen (bearbeiten Sie diese, um die Validierungsverantwortlichen zu ändern, Begrenzung, Eskalationszeitpunkt) | `.claude/skills/aso-doc-agent/config.yml` |
| Lehren aus dem PR-Review-Feedback (in Git verfolgt, vor jedem Entwurf gelesen) | `.claude/skills/aso-doc-agent/references/review-learnings.md` |
| Lokaler Ausführungsstatus (ignoriert - sicher zu löschen, wird neu erstellt) | `.claude/skills/aso-doc-agent/state/` |
| Täglicher Zeitplan - Installationsprogramm | `.claude/scripts/aso-doc-agent-setup.sh` |
| Zulassungsliste der Berechtigungen für Headless-Ausführungen | `.claude/settings.local.json` (ignoriert, maschinell-lokal) |

## Ausführen

- **Manuell, in einer normalen Sitzung:** `/aso-doc-agent` (oder `/aso-doc-agent --ticket SITES-XXXXX`)
- **Headless, einmalig:** `claude -p "/aso-doc-agent"` aus dem Repository-Stamm
- **Täglich, unbeaufsichtigt:** bereits über `launchctl` installiert (siehe unten) — wird täglich um 07:53 Uhr Ortszeit ausgeführt, keine Aktion erforderlich

### Installieren/Ändern des Tageszeitplans

```bash
bash .claude/scripts/aso-doc-agent-setup.sh
```

Installiert einen `launchd` (`~/Library/LaunchAgents/com.sandsinh.aso-doc-agent.plist`), der
führt `claude -p "/aso-doc-agent"` täglich aus diesem Repository aus. Führen Sie das Skript jedes Mal erneut aus, wenn Sie
Bearbeiten Sie den darin enthaltenen Zeitplan (Standard: 07:53 lokal). Dies funktioniert nur, wenn die Maschine
Nach dem Einschalten und nach dem Aufwachen — Mit „Launch“ werden verpasste Aufträge nicht rückwirkend ausgeführt, sondern erst danach
Die nächste planmäßige Zeit normal.

```bash
launchctl list | grep com.sandsinh.aso-doc-agent   # confirm it's loaded
launchctl start com.sandsinh.aso-doc-agent         # trigger a run right now, don't wait for 07:53
launchctl unload ~/Library/LaunchAgents/com.sandsinh.aso-doc-agent.plist  # stop it
```

Protokolle von jedem geplanten Durchlauf im Land `.claude/skills/aso-doc-agent/state/launchd.out.log`
und `launchd.err.log`.

## Worum wird man Sie bitten?

- **Ein Slack DM vom Agenten** (wie Sie gesendet, an Sie - Sandsinh zuerst, Kanishka auf
Eskalation) mit der Anforderung eines Screenshots oder Videos, mit genauen Erfassungsschritten und der/den URL(s) zu
Verwenden Sie . **Antwort auf das verknüpfte Jira-Ticket, nicht in Slack**: Screenshot direkt anhängen,
Oder laden Sie es für Videos über das übliche Experience League-Videoformular hoch
(Kenntnisse `experience-league-video-upload`) und das Ergebnis einfügen `video.tv.adobe.com`
Link als Jira-Kommentar. Der nächste Durchgang nimmt ihn automatisch auf.
- Wenn niemand innerhalb von **5 Tagen** antwortet, eskaliert die Anfrage von Sandsinh nach Kanishka
Automatisch. Nach **10 Tagen** ohne Antwort von beiden, der Agent liefert das Dokument
ohne Medien und fügt einen Inline-Hinweis hinzu. Es gibt keine zeitüberschreitungsbasierte automatische Zusammenführung - die PR
wartet immer noch auf eine tatsächliche Überprüfung durch den Menschen, egal wie lange das dauert.
- **Zu überprüfender PR** - wird zugewiesen, wer von Ihnen beiden weniger PRs mit Agentenöffnung hat.
wartet derzeit auf Überprüfung. Der Entwurf einer PR bedeutet, dass die Medien noch ausstehen; sie wechseln zu
Sobald das Asset angezeigt wird, ist es automatisch zur Überprüfung bereit. Genehmigen und der Agent wird zusammengeführt
Beim nächsten Durchlauf ist kein separater Zusammenführungsschritt erforderlich.
- **Wenn Sie Änderungen anfordern** liest der Agent Ihre Kommentare beim nächsten Durchlauf. generalisierbar
Feedback (keine Tippfehler- oder Link-Fehlerbehebung) wird in `references/review-learnings.md` geschrieben, sodass der
Die gleiche Korrektur muss nicht in einer zukünftigen PR wiederholt werden.

## Verhalten anpassen

`.claude/skills/aso-doc-agent/config.yml` bearbeiten (in Git verfolgt) — Änderungen betreffen alle
(zukünftige Ausführung, auf diesem Computer oder von einer anderen Person, die das Repository klont):

- `pr.max_open` - Anzahl der offenen PRs, bevor der Agent die Auswahl neuer Tickets anhält (Standard 3)
- `pr.stale_after_hours` - Wie lange ein `CHANGES_REQUESTED`-PR sitzen kann, bevor er nicht mehr für `pr.max_open` gezählt wird (Standard: 336 = 14 Tage); er bleibt offen, sodass nur neue Auswahlen freigegeben werden
- `github.reviewers` — wer zugewiesen wird und in welchem Gleichgewicht
- `media.contacts_in_order` / `escalate_after_hours` (Standard 120 = 5 Tage) / `give_up_after_hours` (Standard 240 = 10 Tage) - wer gefragt wird, in welcher Reihenfolge und wie geduldig; beide werden aus der ursprünglichen Anfrage gemessen, sodass eine Eskalation das Aufgabedatum nicht hinausschiebt
- `pr.check_reviews_every_run` — Deaktivieren des Schritts zur Überprüfung (nicht empfohlen; so finden Zusammenführungen und Lernprozesse statt)

## Wenn sie bei einer Eingabeaufforderung mit der Berechtigung anhält

Headless-Ausführungen (`claude -p`, launchd) haben kein Terminal, an das sie gesendet werden können - ein nicht aufgeführter Tool-Aufruf
Ich werde einfach scheitern, anstatt aufzuhängen. Wenn das Protokoll einer Ausführung eine Ablehnung der Berechtigung für einen Befehl anzeigt
Die Pipeline benötigt ordnungsgemäß, fügen Sie sie der `permissions.allow` in hinzu.
`.claude/settings.local.json` (nicht in Git verfolgt) — maschinell lokal; alle Entwickler werden ausgeführt
Dieser Agent benötigt eine eigene Kopie mit einer eigenen Bereichskomponente.

## Wenn es keine Fortschritte mehr macht

Überprüfen Sie in der richtigen Reihenfolge:
1. `gh pr list --repo Adobe-Enterprise-Docs/experience-manager-sites-optimizer.en --label aso-doc-agent --state open` - wenn dies „3“ anzeigt, wartet es auf Bewertungen, es bleibt nicht hängen.
2. Jira: Ist unter SITES-49539 noch ein `New`-Ticket frei, das noch nicht `aso-doc-agent-picked` ist? Die Kennzeichnung wird nur angewendet, wenn eine Verzweigung + PR vorhanden ist (pipeline.md Schritt 6.10), sodass ein abgestürzter Durchlauf kein gekennzeichnetes, aber unveröffentlichtes Ticket hinterlassen sollte - wenn Sie noch eines finden (z. B. eine Kennzeichnung, die von Hand hinzugefügt wurde), entfernen Sie es manuell, um das Ticket wieder zugänglich zu machen.
3. `.claude/skills/aso-doc-agent/state/launchd.err.log` nach dem Fehler des letzten Durchgangs.
4. Wenn die Zusammenfassung eines Durchgangs „epischer Rückstand vollständig abgedeckt“ oder „hier nichts zu tun“ anzeigt, aber Sie wissen, dass es geeignete Arbeit geben sollte, behandeln Sie dies als verdächtig - diese Nachrichten sind für wirklich leere Ergebnisse reserviert. Ein aktueller Jira-/GitHub-/Slack-Fehler wird separat protokolliert und sollte als eigene Zeile in `launchd.err.log` angezeigt werden, anstatt sich hinter einer dieser Nachrichten zu verstecken.
