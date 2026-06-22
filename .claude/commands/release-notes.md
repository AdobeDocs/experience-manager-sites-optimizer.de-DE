---
description: Konvertieren Sie interne ASO-Sprint-Versionshinweise in das kundenorientierte Experience League-Format und fügen Sie sie an die Seite mit den Versionshinweisen an.
source-git-commit: d17008c39f231c45a9ba41ca7f0aa96b9878f674
workflow-type: tm+mt
source-wordcount: '960'
ht-degree: 0%

---


# Versionshinweise für Converter

Konvertiert interne Sprint-Versionshinweise (aus dem Slack `#aem-sites-optimizer-announcements`-Kanal oder der `.cursor/commands/release-notes` Cursor-Ausgabe) in einen kundenorientierten Eintrag und hängt ihn an `help/documentation/release-notes.md` an.

## Nutzung

Rufen Sie diese Fähigkeit auf und fügen Sie dann den Inhalt der internen Versionshinweise ein, wenn Sie dazu aufgefordert werden. Die Kenntnisse werden:

1. Wenden Sie die folgenden Richtlinien für Filter- und Tonregeln an.
2. Analysieren Sie die internen Versionshinweise (in Emojis kategorisierte Abschnitte: ✨ Funktionen, 🚀 Erweiterungen, 🤖 AI-First, 🔧 Fixes, 🏢 BackOffice).
3. Filtern Sie alle ausgeschlossenen Kategorien gemäß Richtlinien (KI-Tools, BackOffice, Lokalisierungsfilter, E2E-Tests, Nur-Sites-Elemente).
4. Schreiben Sie die verbleibenden Elemente im kundenorientierten Ton um, indem Sie die folgenden Tonbeispiele als Referenz verwenden.
5. Verknüpfte Elemente nach Funktionsbereich gruppieren (nicht nach Team oder Repository).
6. Formatieren Sie als neuen Release-Eintrag entsprechend der folgenden Seitenstrukturvorlage.
7. Stellen Sie dem neuen Eintrag `help/documentation/release-notes.md` voran (über dem letzten vorherigen Eintrag, unter dem Seiteneinführungsabsatz).
8. Drucken Sie eine Zusammenfassungstabelle, die Folgendes anzeigt: aufbewahrte Artikel, neu geschriebene Artikel, ausgelassene Artikel (mit Grund für jedes ausgelassene Element).

## Richtlinien

### Grundprinzipien

1. **Kundennutzen zuerst.** Jeder Eintrag sollte die Frage beantworten: „Was kann ich jetzt tun, wo ich vorher nicht oder besser konnte?“ — nicht „Was haben wir versandt?“ Lassen Sie uns mit dem Wert anführen, nicht mit der Implementierung.

2. **Führungston.** Schreiben Sie für einen Entscheidungsträger: Ergebnisse und Fähigkeiten, nicht technische Mechanismen. Ein VP für Digital Experience sollte sofort verstehen, warum eine Aktualisierung wichtig ist.

3. **Kein interner Jargon.** Alle teaminternen Kurzschreibweisen ersetzen:
   - „PLG“ → „Testbenutzer“ oder „Neukunden“
   - „BackOffice“ → vollständig weggelassen (nur Änderung der Infrastruktur)
   - „MSM“ → &quot;AEM Multi Site Manager“
   - „SHM“ → „Site Health Monitor“
   - „OrcaFix“, „Cursor-Befehle“, „AGENTS.md“ → vollständig weggelassen
   - „EDS“ → &quot;Edge Delivery Services&quot;

4. **Kurzeinträge.** Ein Satz von *was*, ein Satz von *warum es wichtig ist*. Wenn beide in einen Satz passen, tu das!

5. **Genauer Umfang.** Nur Änderungen einschließen, die eine Kundin oder ein Kunde in der Produkt-Benutzeroberfläche oder in seinem Erlebnis in den Workflows sieht. Änderungen an Infrastruktur, Tools und Entwicklererlebnissen sind ausgeschlossen.

### Seitenstrukturvorlage

Jeder Veröffentlichungseintrag folgt dieser Struktur:

```markdown
## [Month Start]–[Day End], [Year]

### New Features

- **[Feature Name]** — [One-sentence benefit statement. One sentence of business context if needed.]

### Enhancements

- **[Enhancement Name]** — [One-sentence improvement statement.]

### Bug Fixes

- [Short description of what was fixed and why it matters to users.]
```

**Regeln:**
- Datumsbereichsformat: `May 11–22, 2026` (en-dash, gekürzter Monat, vierstelliges Jahr).
- Umgekehrt-chronologische Reihenfolge: neueste Version oben auf der Seite.
- Nur Abschnitte mit Inhalt einschließen. „Erweiterungen“ oder „Fehlerbehebungen“ auslassen, wenn leer.
- Einträge mit Fehlerbehebungen verwenden keine fett gedruckten Funktionsnamen - es handelt sich um einfache Aufzählungszeichen.
- Schließen Sie nur Fehlerkorrekturen ein, wenn für Benutzende drei oder mehr Korrekturen sichtbar sind.

### Was eingeschlossen bzw. ausgeschlossen werden soll

**include:**

| Kategorie | Beispiele |
|---|---|
| Neue Opportunity-Typen | Anzeigenabsicht stimmt nicht überein, kein CTA liegt über dem Falz |
| Neue Ansichten oder Workflows | Bereitgestellte Registerkarte, CSV-Export, Jira-Verknüpfung |
| Verbesserungen bei Testversion/Onboarding | Geführte Einrichtung, On-Site-Onboarding-Status |
| Verbesserungen an den Einstellungen | Audit-URLs, Konfiguration des Versandtyps |
| Sinnvolle UX-Fehlerbehebungen | Falsche Zählung, fehlerhafte Navigation, Probleme mit der Anzeige von Entscheidungen |
| Neue Daten/Integrationen | Ahrefs-Daten in organischer Suche, Abhängigkeitsstruktur in Sicherheit |
| Funktionen „Bereitstellen für Autor“ | Neue Opportunity-Typen, die die direkte Bereitstellung unterstützen |

**Ausschließen:**

| Kategorie | Vorteile |
|---|---|
| KI-Tools (OrcaFix, Cursor-Befehle, AGENTS.md, Claude-Code-Regeln) | Interne Entwickler-Tools, für Kunden nicht sichtbar |
| Lokalisierungs-Link/Pre-Commit-Hooks | Engineering-Prozess, keine Produktfunktion |
| BackOffice-/Infrastrukturänderungen | In der Benutzeroberfläche nicht sichtbar, es sei denn, sie ändern das Verhalten der Endbenutzer |
| React Spectrum-Versionsaktualisierungen | Interne Abhängigkeit, nicht für den Benutzer sichtbar |
| Verbesserungen bei E2E-Tests | Technische Qualität, kein Produktmerkmal |
| Pipeline-Automatisierung freigeben | Interner Prozess |
| Nur interne Sites-Funktionen | Für Kunden nicht verfügbar |

### Ton-Beispiele

| Interne Formulierung | Kundenorientierte Formulierung |
|---|---|
| „Einführung des Status „ABGELEHNT“ für den manuellen Validierungs-Workflow“ | „Sie können jetzt Vorschläge als abgelehnt markieren, um anzugeben, dass sie nicht für Ihre Site gelten, sodass sich Ihre Opportunity-Liste auf umsetzbare Elemente konzentriert.“ |
| „Bereitgestellte Ansicht für kanonische und Heflang-Opportunities (gruppiert nach Datum)“ | „Änderungen an kanonischen und Heflang-Opportunitys werden jetzt nach Bereitstellungsdatum in einer Registerkarte „Bereitstellen“ gruppiert, sodass Sie einen klaren Verlauf darüber erhalten, was behoben wurde und wann.“ |
| „Alt-Text Autofix V2 — &#39;Fixierbarkeit prüfen&#39;-Pre-Flight-Assessment“ | „Vor der Bereitstellung einer ALT-Text-Fehlerbehebung können Sie eine Pre-Flight-Prüfung ausführen, um zu überprüfen, ob die Fehlerbehebung erfolgreich auf Ihren Inhalt angewendet werden kann.“ |
| „96 % Speicheroptimierung für SHM-Metriken“ | weglassen — nur Infrastruktur |
| „AGENTS.md mit formellen Agentenrollen und Sicherheitsleitplanken“ | auslassen — interne KI-Tools |
| „Leistungsoptimierungen für E2E-Tests (~6min → ~5min)“ | OMIT — Engineering-Prozess |

### Gruppierungsregeln

- **Nach Funktionsbereich gruppieren**, nicht nach Team oder Repository. Beispielsweise gehören alle Verbesserungen (Funktionen, Verbesserungen und Fehlerbehebungen) des Alternativtexts in denselben Bereich und verteilen sie nicht über Abschnitte.
- **Konsolidierung eng verwandter** in einem einzigen Aufzählungszeichen, anstatt jede einzeln aufzulisten (z. B. „Mehrere Verbesserungen der Anzeige und des Layouts in allen Paid Traffic-, Barrierefreiheits- und Sicherheitsmöglichkeiten„).
- **Abschnitt Schwelle für Fehlerbehebungen**: Schließen Sie diesen Abschnitt nur ein, wenn für Benutzende drei oder mehr Fehlerbehebungen sichtbar sind, die einen Aufruf wert sind. Triviale oder rein kosmetische Korrekturen unterhalb dieses Schwellenwerts sollten weggelassen werden.

## Schritte

1. Wenden Sie die Richtlinien in dieser Datei an - internalisieren Sie alle Prinzipien, Regeln zum Ein-/Ausschließen, Tonbeispiele und Gruppierungsregeln.
2. Fragen Sie den Benutzer nach dem abgedeckten Datumsbereich (z. B. „11.-22. Mai 2026„), wenn er nicht bereits angegeben ist.
3. Bitten Sie den Benutzer, den Inhalt der internen Versionshinweise einzufügen (oder akzeptieren Sie einen Dateipfad).
4. Verarbeiten Sie den Inhalt:
   - **Parsen** jeden Abschnitt (✨/🚀/🤖/🔧/🏢) und seine Aufzählungspunkte.
   - **Filter** gemäß der obigen Ausschlusstabelle. Markieren Sie jedes abgelegte Element mit einem Grund.
   - **Neu schreiben** Elemente im Kundenton beibehalten: Benefit-First, kein Jargon, Kurzeinträge.
   - **Gruppieren** nach Funktionsbereich, in dem mehrere Elemente verknüpft sind.
   - **Schwellenwertprüfung**: Fügen Sie nur dann einen Abschnitt „Fehlerbehebungen“ hinzu, wenn für Benutzende mehr als drei Fehlerbehebungen sichtbar sind.
5. Formatieren Sie den neuen Eintrag mithilfe der obigen Seitenstrukturvorlage.
6. Den aktuellen Inhalt von `help/documentation/release-notes.md` lesen.
7. Fügen Sie den neuen Eintrag unmittelbar nach dem Absatz des Seiteneintritts ein (vor der vorherigen Überschrift des letzten `##`).
8. Schreiben Sie die aktualisierte Datei.
9. Druckt die Zusammenfassungstabelle.

## Eingabeformat

Die Qualifikation akzeptiert die internen Versionshinweise im standardmäßigen Team-Format:

```
*ASO UI Release Notes — [Date Range]*
Collaborators: [teams]

✨ *Features*
• [Feature description]

🚀 *Enhancements*
• [Enhancement description]

🤖 *AI-First Development*
• [AI tooling items — will be dropped]

🔧 *Fixes & UX Improvements*
• [Fix description]

🏢 *BackOffice*
• [BackOffice items — will be dropped]
```

## Ausgabe

Die Ergebnisse für Kenntnisse:

1. Der formatierte kundenseitige Eintrag (zur Überprüfung vor dem Schreiben).
2. Eine Bestätigungsaufforderung vor dem Ändern von `release-notes.md`.
3. Nach dem Schreiben: eine zusammenfassende Tabelle der aufbewahrten / umgeschriebenen / abgelegten Elemente.
