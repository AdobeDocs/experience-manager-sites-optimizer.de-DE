---
title: Versionshinweise
description: Erfahren Sie mehr über die neuesten Funktionen, Verbesserungen und Fehlerbehebungen in Adobe Experience Manager Sites Optimizer.
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
topic_v2:
  - id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
    internal-label: Optimization
source-git-commit: 8d6936c2c577d7a98937cb8ddf90d18a6e82a9bb
workflow-type: tm+mt
source-wordcount: '2628'
ht-degree: 2%
---

# Versionshinweise

Auf dieser Seite werden die neuesten Aktualisierungen, neuen Funktionen und Verbesserungen in Adobe Experience Manager Sites Optimizer dokumentiert.

Mit **(Early Access)** gekennzeichnete Funktionen sind auf Anfrage verfügbar. Wenden Sie sich an Ihr Account Team oder Ihren Customer Success Engineer, um sie für Ihr Unternehmen zu aktivieren.

## &#x200B;28. September bis 4. Oktober 2026 {#september-28-october-4-2026}

### Neue Funktionen

- **Personal AI Agent Opportunities (Early Access)** - Filtern Sie Möglichkeiten, wie Personal AI Agents Ihre Website lesen und mit ihr interagieren können, mit Abzeichen und Anleitungen, die die Vorteile erläutern.

### Verbesserungen

- **Beschädigte Bereitstellung interner Links (Early Access)** - Geben Sie eine Ersatz-URL für einen Link an, der nicht automatisch korrigiert werden kann, und stellen Sie das validierte Update bereit.
- **Veröffentlichungsstatus für Alt-Text** - Zeigt an, wann eine Änderung des Alt-Texts live auf der veröffentlichten Seite bestätigt wird, wobei der Status „Fehler löschen“ und „Erneut erkennen“ beibehalten wird.
- **Core Web Vitals-Code-Patches** - Überprüfen Sie die Patches dateiweise mit Zeilennummern und hervorgehobenen Hinzufügungen und Löschungen.
- **Core Web Vitals-Code-Bereitstellung (früher Zugriff)** — Senden Sie geeignete Code-Patches als Pull-Anfrage in Ihrem konfigurierten Code-Repository.

### Fehlerbehebungen

- Forms-Barrierefreiheitsmöglichkeiten unterstützen jetzt das Erstellen von Jira-Problemen.
- Mithilfe von Follow-up-Links zur Bereitstellung wird jetzt das konfigurierte Code-Repository geöffnet.
- Detaillierte Barrierefreiheitsberichte werden jetzt geöffnet und zeigen ihren Inhalt an, anstatt zur Startseite weiterzuleiten oder leer zu erscheinen.
- Die Anzahl der bereitgestellten Alt-Texte und die Datumgruppen stimmen nun mit den angezeigten Fehlerbehebungen überein, ohne dass leere Gruppen für die fehlgeschlagene Bereitstellung vorhanden sind.
- Beim Wiederherstellen übersprungener Sitemap- und Core Web Vitals-Vorschläge wird ihr Status jetzt zuverlässig aktualisiert.

## &#x200B;21. bis 27. September 2026

### Verbesserungen

- **Häufig gestellte Fragen zur Bereitstellung strukturierter Daten (Early Access)** - Wählen Sie für Seiten, die mit AEM Multi-Site Manager verwaltet werden, aus, ob strukturierte Datenaktualisierungen auf die Quellseite oder nur auf die lokale Seite angewendet werden sollen.
- **Formularbereitstellung** - Stellen Sie die Fehlerbehebung für die ausgewählte Formularvariante zuverlässig bereit.
- **Lokalisierte Erlebnisse** - Berechtigungsbeschriftungen und abgeschnittene Tabelleninhalte sind in den unterstützten Sprachen klarer.

### Fehlerbehebungen

- Patch-Downloads für Core Web Vitals sind immer verfügbar, wenn ein Patch vorhanden ist.
- CSV-Exporte behalten jetzt lokalisierte Zeichen in Excel bei.
- Leistungsmetriken bleiben beim Laden nicht mehr hängen, wenn die Quelldaten unvollständig sind.

## &#x200B;14. bis 20. September 2026

### Verbesserungen

- **Granulare Berechtigungen** - Administratoren können Mitgliedern Zugriff auf ausgewählte Opportunity-Typen gewähren und gleichzeitig Site-weite Berechtigungen separat verwalten.

### Fehlerbehebungen

- Die Metadatenbereitstellung stellt jetzt die Warnung wieder her, die beim Korrigieren einer lokalen Seite angezeigt wird, die die Vererbung unterbricht.

## &#x200B;7. bis 13. September 2026

### Neue Funktionen

- **Google Ads-Platzierungsausschlüsse** — Überprüfen Sie die Platzierungsrisiken für verbundene Google Ads-Konten und laden Sie Site-spezifische Ausschlusslisten für automatisierte und Performance Max-Kampagnen herunter.

### Verbesserungen

- **Anleitung zu Bereitstellungsfehlern** - Fehlermeldungen erklären jetzt, ob eine Inhaltsaktualisierung Verbindungszugriff, eine erneute Suche oder Support benötigt.

### Fehlerbehebungen

- Die Werte und Layouts der Berichte zur Barrierefreiheit werden jetzt in allen unterstützten Sprachen deutlicher angezeigt.
- Die Gesamtwerte für Paid Traffic-Kanal und -Plattform enthalten jetzt nicht klassifizierten Traffic.
- Die unterbrochenen Zählungen der bereitgestellten Backlinks stimmen jetzt mit den angezeigten Zeilen überein, einschließlich des Status der zurückgesetzten und aufgestockten Bereitstellung.
- Berechtigte Edge Delivery Services-Sites werden nicht mehr fälschlicherweise für die Bereitstellung fehlerhafter Links blockiert.

## &#x200B;31. August bis 6. September 2026

### Verbesserungen

- **AEM Content Connections** - Einstellungen erkennen jetzt von AEM erstellte Edge Delivery Services-Konfigurationen, behalten ihre Quelldetails bei und blockieren nicht unterstützte Quell-URLs vor dem Speichern.
- **Test-Onboarding** - Der Domäneneintrag erklärt jetzt die unterstützten Anforderungen an die Produktions-Site, bevor eine Test-Site hinzugefügt wird.

### Fehlerbehebungen

- Bezeichnungen und Selektoren für Paid Traffic-Monate werden nun in allen unterstützten Sprachen korrekt angezeigt.
- CSV-Exporte verwenden jetzt die richtige Seiten-URL jedes Barrierefreiheitsproblems.
- Berechtigte Edge Delivery Services-Sites werden nicht mehr fälschlicherweise für die Bereitstellung von Alt-Text blockiert.

## &#x200B;20. bis 27. August 2026

### Neue Funktionen

- **Warnhinweisansicht** - Überprüfen Sie einen 90-tägigen Zeitrahmen automatisch erkannter Site-Health-Vorfälle, korrelieren Sie Änderungen mit Bereitstellungen und Inhaltsaktualisierungen und inspizieren Sie die betroffenen Seiten und Leistungsmetriken an einem Ort.
- **Berichte und Erfolge** - Im Bereich „Berichte“ können Sie den Optimierungsverlauf, Leistungstrends sowie die Erfolge vor und nach der Optimierung überprüfen. Diese Informationen helfen Ihnen dabei, die Auswirkungen Ihrer Optimierungsarbeit zu kommunizieren.
- **Neue Funktionen und Hilfe-Center** - Entdecken Sie die kürzlich veröffentlichten Funktionen, öffnen Sie die Produktdokumentation und greifen Sie direkt über das In-App-Hilfe-Center auf die Versionshinweise zu.
- **Google Ads-Verbindung (früher Zugriff)** - Verbinden Sie ein Google Ads-Konto, um Paid-Traffic-Leistungsdaten in Sites Optimizer-Opportunities und -Empfehlungen zu integrieren.

### Verbesserungen

- **Opportunity-Listensteuerelemente** - Filtern und Sortieren von Opportunities nach URL, Startstatus, Priorität oder Neuigkeit, Speichern von Ansichten in der URL für die Freigabe und Exportieren von Vorschlagsdaten in CSV.
- **Workflow-Steuerelemente für Vorschläge** - Bearbeiten von KI-generierten Vorschlägen vor der Bereitstellung, Ignorieren einzelner Vorschläge, Überspringen vollständiger Opportunitys und Wiederherstellen übersprungener Opportunitys, wenn sie wieder relevant werden.
- **Bereitstellungsverlauf** - Überprüfen Sie den Bereitstellungsverlauf nach Datum, unterscheiden Sie automatische Bereitstellungen von Änderungen, die als manuell bereitgestellt markiert sind, und folgen Sie Pull-Request-Links für Code-basierte Fehlerbehebungen.
- **Integration von Marken und Slack** - Wählen Sie eine Adobe GenStudio-Marke für die Erstellung markeninterner Inhalte aus und teilen Sie relevante Optimierungsaktualisierungen mit einem konfigurierten Slack-Kanal.

## &#x200B;6. bis 19. August 2026

### Neue Funktionen

- **Preflight im AEM Sites-Seiteneditor** - Wenn Ihre Authoring-Umgebung AEM 2026.7.0 oder höher ausführt, können Sie Preflight direkt über die Seiteneditor-Symbolleiste öffnen, um die aktuelle Seite zu analysieren, ohne den Authoring-Workflow zu verlassen.
- **PreFlight-Exportoptionen** - Exportieren Sie Preflight-Ergebnisse als CSV oder PDF mit Optionen zum Einschließen von durchlaufenen Metadaten und Audits, um die Freigabe von Ergebnissen und die Nachverfolgung der Bereitschaft zu erleichtern.

### Verbesserungen

- **Preflight-Sitzungsdetails** - Wenn Sie eine vorherige Audit-Sitzung fortsetzen, zeigt Preflight an, wann der Durchlauf durchgeführt wurde, und erleichtert die Identifizierung betroffener Elemente durch die Anzeige von lesbarem Text oder einer CSS-Auswahl.

## &#x200B;1. bis 19. Juli 2026

### Neue Funktionen

- **Berechtigungsverwaltung (Early Access)** - Benutzer mit der Funktion „Benutzer verwalten“ können jetzt den Site-Zugriff über eine neue Registerkarte „Berechtigungen“ steuern - Personen nach Namen oder E-Mail suchen und bestimmte Funktionen gewähren oder widerrufen. Aktionen, die ein Benutzer nicht ausführen darf, werden mit einer QuickInfo deaktiviert, die erklärt, wie der Zugriff angefordert wird.
- **Bereitstellungsstatus-Badges** - Fehlerkorrekturen, die als manuell bereitgestellt gekennzeichnet sind, zeigen jetzt in der Ansicht „Bereitgestellt“ ein eigenes Badge „Als bereitgestellt“ an, sodass manuelle Aktualisierungen von automatischen Bereitstellungen unterschieden werden können.

### Verbesserungen

- **Automatische Fehlerbehebung für GitHub (Cloud Manager)** - Code-Patch-Autopatches für Opportunities wie Core Web Vitals, Sicherheit und Barrierefreiheit von Formularen können jetzt Pull-Anfragen für auf GitHub gehostete bring-your-own-git-Repositorys von Cloud Manager auslösen, die mit der bestehenden Unterstützung für GitLab, Bitbucket und Azure DevOps übereinstimmen. Mit dem neuen Umschalter Einstellungen können Sie die einmalige Einrichtungsbestätigung für Ihre Site steuern.
- **Automatische Fehlerbehebung über Verzweigung (Cloud Manager Standard)** - Die automatische Fehlerbehebung über Verzweigung ist jetzt für Cloud Manager Standard-Repositorys verfügbar, wenn sie für Ihre Site aktiviert ist.
- **Bereitgestellte Ansicht: Durchgeführt von** - Die bereitgestellte Ansicht zeigt jetzt über die neuen Spalten „Durchgeführt von“ und „Status zuletzt aktualisiert“ an, wer jede Fehlerbehebung als bereitgestellt und wann ihr Status zuletzt aktualisiert wurde.
- **Google Ads Disconnect Feedback** — Wenn Sie ein Google Ads-Konto in den Einstellungen trennen, wird jetzt der Status „Verbindung wird getrennt…“ angezeigt. Wenn die Trennung fehlschlägt, wird eine Fehlermeldung angezeigt, die angezeigt wird, dass die Verbindung getrennt werden kann, damit Sie es erneut versuchen können.

### Fehlerbehebungen

- Die Opportunity ARIA-Beschriftungen reparieren zeigt jetzt die richtige Seiten-URL im Dialogfeld Details an, wenn eine Fehlerbehebung mehrere Seiten umfasst.
- Die Informationsmeldung zum Überspringen des Dialogfelds wird jetzt korrekt mit ordnungsgemäß ausgerichtetem Text auf Koreanisch, vereinfachtes Chinesisch und traditionelles Chinesisch angezeigt.
- Verwandte Dialogfelder für ALT-Text und ungültige oder fehlende Metadaten werden jetzt zuverlässig geladen, und die Ansicht „Ungültige oder fehlende bereitgestellte Metadaten“ und die Korrekturen von Meta-Tags funktionieren jetzt korrekt mit dem neuesten Vorschlagsformat.

## &#x200B;11. bis 22. Mai 2026

### Neue Funktionen

- **Site-Warnhinweisbericht (frühzeitiger Zugriff)** - Ein neuer 90-tägiger Site-Warnhinweisbericht bietet eine vierteljährliche Übersicht über den Zustand Ihrer Site, wobei farbcodierte tägliche Blöcke verwendet werden, um Zeiträume mit erhöhten Warnhinweisen hervorzuheben, damit Sie Trends im Laufe der Zeit schnell identifizieren und untersuchen können.
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
- **Audit-Ziel-URLs (frühzeitiger Zugriff)** - Unter „Einstellungen“ können Sie jetzt bis zu 100 benutzerdefinierte URLs angeben, um sicherzustellen, dass diese Seiten immer in Audits enthalten sind.
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
- **Jira-Integration für Barrierefreiheit und Farbkontrast (Early Access)** - Barrierefreiheitsmöglichkeiten für Forms und Farbkontrast können jetzt direkt mit Jira-Tickets verknüpft werden, um die Problemverfolgung innerhalb Ihres bestehenden Workflows zu optimieren.

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
