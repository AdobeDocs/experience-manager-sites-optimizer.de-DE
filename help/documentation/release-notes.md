---
title: Versionshinweise
description: Erfahren Sie mehr über die neuesten Funktionen, Verbesserungen und Fehlerbehebungen in Adobe Experience Manager Sites Optimizer.
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
topic_v2:
  - id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
source-git-commit: d5cc34fd40395fc13ce3554a0b80c0216d859157
workflow-type: tm+mt
source-wordcount: 1471
ht-degree: 2%

---


# Versionshinweise

Auf dieser Seite werden die neuesten Aktualisierungen, neuen Funktionen und Verbesserungen in Adobe Experience Manager Sites Optimizer dokumentiert.

## &#x200B;11. bis 22. Mai 2026

### Neue Funktionen

- **Site-Warnhinweisbericht** - Ein neuer 90-tägiger Site-Warnhinweisbericht bietet eine vierteljährliche Übersicht über den Zustand Ihrer Site. Dabei werden farbcodierte tägliche Blöcke verwendet, um Zeiträume mit erhöhten Warnhinweisen hervorzuheben, sodass Sie Trends im Zeitverlauf schnell identifizieren und untersuchen können.
- **Onboarding von Betriebstelemetrien** - Websites, die noch keine betriebstelemetrischen Daten verbunden haben, erhalten jetzt ein beständiges Banner auf der Startseite und ein geführtes Onboarding-Dialogfeld, um die Einrichtung abzuschließen, sodass Sie vollständige Einblicke in die Leistung von echten Benutzern erhalten.
- **ALT-Text: Multi-Site-Manager-**: Beim Generieren von ALT-Text-Korrekturen für Sites, die AEM Multi-Site-Manager oder Sprachkopie verwenden, prüft Sites Optimizer jetzt, ob Korrekturen sicher auf jede Sprachvariante angewendet werden können, bevor es sie vorschlägt.

### Verbesserungen

- **ALT-Text-Genauigkeit** - Vorschläge für ALT-Text stammen jetzt aus dem neuesten Überwachungssignal, und neu erkannte Probleme werden sowohl auf den Registerkarten „Aktuelle Probleme“ als auch „Bereitgestellt“ angezeigt, um einen vollständigen Überblick zu erhalten.

### Fehlerbehebungen

- Der Status der Schaltfläche Bereitstellen gibt jetzt korrekt an, ob eine Fehlerbehebung tatsächlich bereitgestellt werden kann.
- Dunkles Design wird jetzt bei der Seitenaktualisierung korrekt angewendet.
- Berichte zeigen Datumsangaben im Gebietsschema des Benutzers an.
- Regionale Voreinstellungen für Sprache und Zahlen-/Datumsformat können jetzt unabhängig konfiguriert werden.
- Beschädigter Bild-Alternativtext ist jetzt für Bildschirmlesehilfen zugänglich.

## &#x200B;21. April bis 10. Mai 2026

### Neue Funktionen

- **Kein Onboarding-Status der Site** - Kunden, die noch keine Site hinzugefügt haben, sehen jetzt auf der Startseite eine klare, umsetzbare Eingabeaufforderung für einen schnellen Einstieg.
- **Dokumentation im Hilfe-Center** - Die AEM Sites Optimizer-Dokumentation zu Experience League ist jetzt direkt über das In-App-Hilfe-Center zugänglich, ohne das Produkt verlassen zu müssen.

### Fehlerbehebungen

- Sites ohne aktive Vorschläge zeigen jetzt korrekt das Dialogfeld Aktion erforderlich an.
- Übersprungene Vorschläge werden jetzt erwartungsgemäß auf der Registerkarte Ignoriert angezeigt.
- Dropdown-Listen für die Auswahl von Paid Traffic reduzieren übersetzten Text nicht mehr.
- Die Seitenauswahl der Sitemap hat jetzt die richtige Größe.

## &#x200B;13. März bis 20. April 2026

### Neue Funktionen

- **Onboarding von Testversionen** - Benutzende an neuen Testversionen erleben jetzt einen geführten Einrichtungsablauf: Geben Sie Ihre Domain ein, warten Sie auf die Analyse und erkunden Sie dann Ihre ersten Opportunities - keine Konfiguration erforderlich, um zu beginnen.
- **Seite „Opportunities-Testversion** - Testbenutzer können Opportunities suchen, sortieren und filtern, wobei drei entsperrte Vorschläge und die verbleibenden Vorschläge in einer gesperrten Vorschau mit einer Upgrade-Eingabeaufforderung angezeigt werden.
- **Monatlicher Optimierungsfortschritt** - Eine Fortschrittsleiste auf der Startseite zeigt an, wie viele Optimierungsaktionen Sie in diesem Monat durchgeführt haben, sodass Sie die gesteckten Ziele für Ihre Website immer im Auge behalten können.
- **Audit-Ziel-URLs** - Unter „Einstellungen“ können Sie jetzt bis zu 100 benutzerdefinierte URLs angeben, um sicherzustellen, dass diese Seiten immer in Audits enthalten sind.
- **Konfiguration des Bereitstellungstyps** - In den Einstellungen können Sie jetzt den Bereitstellungstyp Ihrer Site angeben (Edge Delivery Services, AEM Cloud Service oder AEM Managed Services) und Ihren Inhaltsanbieter verbinden.
- **Core Web Vitals-Neugestaltung** - Die Core Web Vitals-Opportunity wurde mit Jira-Verknüpfung, CSV-Download und Mehrfachauswahl-Unterstützung für Batch-Aktionen neu gestaltet.
- **Zerbrochene Backlinks Einheitliche Tabelle** - Zerbrochene Backlinks aus allen Quellen werden jetzt in einer einzigen einheitlichen Tabelle angezeigt, mit der Möglichkeit, CDN-Umleitungsregeln direkt zu exportieren.
- **Kein CTA über dem Ordner: Für Autor bereitstellen** - Fehlerbehebungen für den Ordner „Kein CTA über dem Ordner“ können jetzt direkt für AEM Author bereitgestellt werden.
- **Forms-Autofix-Bereitstellung** - Forms-Opportunity-Fehlerbehebungen können jetzt direkt in der AEM-Autoreninstanz bereitgestellt werden.
- **Unterstützung für AEM Multi-Site-Manager** - Gelegenheiten, die sich auf mehrere Sprachkopien einer Site auswirken, geben jetzt mithilfe einer Spalte mit „Fixiert um“ an, auf welche Stamm-Site die Fehlerbehebung angewendet wurde.
- **Fehlgeschlagene Fehlerbehebungen überspringen** - Sie können jetzt einzelne Fehlerbehebungen überspringen, bei denen die Bereitstellung fehlgeschlagen ist, sodass Ihr Workflow entsperrt bleibt.
- **Im AEM-Editor öffnen** - Opportunity-Vorschläge enthalten jetzt einen direkten Link zum Öffnen der betroffenen Seite im Visual Editor von AEM für schnelle Inline-Bearbeitungen.

## &#x200B;28. Februar bis 13. März 2026

### Neue Funktionen

- **Opportunity-Mismatch** - Ein neuer Opportunity-Typ identifiziert Landingpages mit bezahltem Traffic, die keine Konversionen durchführen, mit einer Absprungrate, Kosten pro Klick und Traffic-Metriken, anhand derer Sie Landingpage-Verbesserungen priorisieren können.
- **Kein CTA im Überblick** - Diese Opportunity ist jetzt ein dedizierter erstklassiger Typ mit einer eigenen Detailseite und Filterung, was das Nachverfolgen und Priorisieren von Konversionsverbesserungen erleichtert.
- **Sitemap URL Suggestions** - Die Sitemap-Gelegenheit schlägt jetzt Ersatz-URLs für Seiten mit 404-Fehlern vor, was die Korrektur fehlerhafter Sitemap-Einträge erleichtert.
- **Neu gestaltete fehlerhafte Backlinks** - Die Detailseite für fehlerhafte Backlinks wurde überarbeitet, um die Übersichtlichkeit und Benutzerfreundlichkeit zu verbessern.

### Verbesserungen

- **Top Organic Search Pages V2** - Organische Traffic-Daten stammen jetzt aus einem 30-tägigen Ahrefs-Datensatz und bieten umfassendere und umsetzbare Einblicke in die Suchleistung.
- **Sicherheitslücken: Abhängigkeitsstruktur** - Details zu Sicherheitslücken enthalten jetzt eine Visualisierung der Abhängigkeitsstruktur, damit Sie die vollen Auswirkungen einer Schwachstelle auf Ihr gesamtes Projekt verstehen können.

## &#x200B;14. bis 27. Februar 2026

### Neue Funktionen

- **Top Organic Search Pages** - Site Health Monitor enthält jetzt eine dedizierte Registerkarte, die die wichtigsten organischen Traffic-Seiten Ihrer Site anzeigt, sodass Sie sehen können, welche Inhalte den meisten Such-Traffic verursachen.
- **ALT-Text-Autofix V2** - Vor der Bereitstellung einer ALT-Text-Fehlerbehebung können Sie eine Pre-Flight-Bewertung „Fixierbarkeit prüfen“ ausführen, um zu überprüfen, ob die Fehlerbehebung erfolgreich auf Ihren Inhalt angewendet werden kann.
- **Bereitgestellte Ansicht für ALT-Text** - ALT-Text-Fehlerbehebungen werden jetzt auf der Registerkarte „Bereitgestellt“ angezeigt, sodass Sie neben den aktuellen ausstehenden Problemen einen vollständigen Verlauf der Verbesserungen der Barrierefreiheit erhalten.
- **Bereitstellungstor für externe Organisationen** - Beim Bereitstellen von Fehlerbehebungen für eine extern verwaltete Site ist jetzt ein expliziter Bestätigungsschritt erforderlich, um versehentliche Änderungen zu verhindern.

### Verbesserungen

- **URL-Ausnahmen für Meta-Tags** - Bestimmte URLs können jetzt über die -Konfiguration von der Meta-Tags-Validierung ausgeschlossen werden, wodurch Fehlalarme bei absichtlich kurzen oder nicht standardmäßigen Titeln reduziert werden.
- **Erweiterte URL-Filterung** - Opportunity-Listen unterstützen jetzt beim Filtern nach URL den Präfixabgleich von Unterrouten, wodurch es einfacher wird, sich auf bestimmte Bereiche Ihrer Site zu konzentrieren.
- **Verbesserte Trenddiagramme** - Traffic-Trenddiagramme behandeln jetzt die Daten im Jahresvergleich korrekt und beseitigen irreführende Einbrüche an den Jahresgrenzen.

## &#x200B;6. bis 13. Februar 2026

### Neue Funktionen

- **Wartungsmodus** - Sites Optimizer verarbeitet jetzt geplante Wartungsfenster problemlos und zeigt während der Ausfallzeit eine klare Statusmeldung anstelle unvollständiger oder irreführender Daten an.
- **Bereitgestellte Ansicht für fehlerhafte Backlinks** - Fehlerkorrekte Backlinks werden jetzt auf einer bereitgestellten Registerkarte nach Datum gruppiert nachverfolgt, sodass Sie Ihren Korrekturverlauf auf einen Blick sehen können.
- **Kein CTA über der Faltgelegenheit** - Ein neuer Opportunity-Typ zeigt Seiten an, auf denen über der Faltfläche kein eindeutiges call-to-action zu sehen ist. So können Sie Seiten mit geringem Konversionspotenzial identifizieren und verbessern.
- **Jira-Integration für Barrierefreiheit und Farbkontrast** - Barrierefreiheitsmöglichkeiten für Forms und Farbkontrast können jetzt direkt mit Jira-Tickets verknüpft werden, um die Problemverfolgung innerhalb Ihres bestehenden Workflows zu optimieren.

### Verbesserungen

- **Bereitgestellte Ansichten für Meta Tags und Sicherheit** - Meta Tags und Sicherheitsmöglichkeiten enthalten jetzt im Einklang mit anderen Opportunity-Typen datumsgruppierte bereitgestellte Registerkarten.
- **Alt-Text-Bereitstellungs-Tracking** - „Als bereitgestellt markieren“ ist jetzt für Alt-Text-Korrekturen verfügbar, und manuell bearbeiteter Alt-Text wird in allen Neuanalyseausführungen beibehalten.

## &#x200B;26. Januar bis 6. Februar 2026

### Neue Funktionen

- **Bereitgestellte Ansicht für Canonical &amp; Hrefang** - Änderungen an Opportunitys für Canonical und Hrefang werden jetzt nach Bereitstellungsdatum in einer Registerkarte „Bereitgestellt“ gruppiert, sodass Sie einen klaren Verlauf darüber erhalten, was behoben wurde und wann.
- **CSV-Export** - Sie können jetzt Opportunity-Daten für CTR- und Forms-Opportunitys mit hohem organischen Anteil zur Offline-Analyse und Berichterstellung in CSV exportieren.
- **Favoriten-Opportunitys** - Startet jede Gelegenheit in der Kopfzeile, um sie Ihren Favoriten hinzuzufügen, wodurch es schneller geht, zurück zu den Opportunitys zu navigieren, an denen Sie aktiv arbeiten.
- **Bereitgestellte Ansicht für Umleitungsketten** - Fehlerkorrekturen der Umleitungskette können jetzt direkt auf der Detailseite als bereitgestellt markiert werden.

### Verbesserungen

- **Verbesserte Schätzungen der Cookie** Banner-Kosten - Kostenberechnungen für die Cookie-Banner-Opportunity wurden verfeinert, um die Genauigkeit zu erhöhen.

## &#x200B;16. bis 23. Januar 2026

### Neue Funktionen

- **Site Health Monitor (Allgemeine Verfügbarkeit)** - Site Health Monitor ist jetzt für alle Kunden verfügbar und bietet einen kontinuierlichen Überblick über den Performance-Status Ihrer Site. Beim Onboarding werden neue Sites automatisch eingerichtet.
- **Unterpfad-Site-**: Sites, die sich auf bestimmte URL-Unterpfade beziehen, werden jetzt im Sites Health Monitor vollständig unterstützt.

### Verbesserungen

- **Verwertbare Datenhinweise** - Paid Traffic-Gelegenheiten mit weniger als 1.000 Seitenansichten zeigen jetzt einen Datenhinweis an, der Ihnen hilft, Optimierungsbemühungen auf Bereiche zu konzentrieren, in denen Traffic-Daten statistisch aussagekräftig sind.
- **Flexible Meta-Titelvalidierung** - Die Mindestanforderung an Zeichen für Meta-Titel wurde reduziert, sodass Sie jetzt noch flexibler Seitentitel erstellen können.
- **Dialogfeld „Lokalisierte Neuigkeiten** - Das Dialogfeld mit den In-App-Funktionsankündigungen wird jetzt in der von Ihnen bevorzugten Sprache angezeigt.
- **Veröffentlichungs-Badge** - Variationen der Opportunity mit hohem organischen Low-CTR, die jetzt bereitgestellt werden, weisen das Badge „Veröffentlicht“ auf, wodurch es einfacher wird, aktive von ausstehenden Änderungen zu unterscheiden.
- **Links zu Pull in Barrierefreiheit** - Die Registerkarte Bereitgestellt der Barrierefreiheitsmöglichkeit zeigt jetzt für jede Fehlerbehebung die zugehörige URL für Pull-Anfragen an, was die Rückverfolgung von Änderungen an Ihrem Versionsverlauf erleichtert.
