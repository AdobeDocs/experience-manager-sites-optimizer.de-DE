---
title: Audit-Ergebnisse in Preflight
description: Erfahren Sie, wie Sie die Ergebnisse der Preflight-Prüfung, den Bereitschaftszähler und die Auditkategorien interpretieren und zu Opportunities in der Vorschau navigieren können.
source-git-commit: 56a56991a262d9f19a228dc9ca6ec440acdc2999
workflow-type: tm+mt
source-wordcount: '1009'
ht-degree: 3%

---


# Audit-Ergebnisse in Preflight

Nach Abschluss der Audits zeigt Preflight die Ergebnisse im Bereitschafts-Dashboard an. Im Dashboard werden die Gesamtbereitschaftsanzeige und die gefundenen Opportunities gruppiert nach Auditkategorie angezeigt. Innerhalb jeder Kategorie werden bei individuellen Audits spezifische Elemente identifiziert, die überprüft oder korrigiert werden müssen.

## Symbolleiste

Die Symbolleiste am oberen Rand des Bereitschafts-Dashboards enthält Aktionen für die aktuelle Ausführung:

* **Neu analysieren** - Startet einen brandneuen Audit-Durchgang auf der aktuellen Seite. Bei der Neuanalyse werden die angezeigten Ergebnisse immer verworfen und alle Prüfungen werden erneut ausgeführt. Verwenden Sie sie daher, wann immer Sie neue Ergebnisse wünschen - beispielsweise nach der Bearbeitung der Seite. Neu analysieren ist in **Mehr Aktionen** (**…**) Menü.
* **Exportieren** - Laden Sie die aktuelle Ausführung als **CSV** (Tabellenfreundlich) oder **PDF** (formatiertes Dokument) herunter. Wählen Sie je nach Umgebung **Exportieren** in der Symbolleiste oder unter **Mehr Aktionen** aus (**…**) Menü.

Beim Exportieren können Sie auch auswählen, was einbezogen werden soll:

* **Metadatentabelle einschließen** - Fügen Sie eine Tabelle mit Ausführungsdetails hinzu, z. B. den Host, den Inhaltspfad und Erzeugungsdetails.
* **Bestehende Audits einschließen** - Schließt die Audits ein, die ohne Opportunities bestanden wurden, nicht nur die gefundenen Opportunities.

>[!NOTE]
>
>PDF-Exporte werden unabhängig von der Sprache der Benutzeroberfläche immer in englischer Sprache generiert. CSV-Exporte folgen der Sprache Ihrer Benutzeroberfläche so genau wie möglich.

## Betriebsbereitschaftsmesser

Oben im Dashboard zeigt die Bereitschaftsanzeige die Ergebnisse der Prüfung an. Er zeigt einen Bereitschaftswert in Prozent an, basierend auf dem Anteil der Prüfungen, die ohne Opportunities abgeschlossen wurden, und der Gesamtzahl der in allen Prüfungen gefundenen Opportunitys. Mit dem Readiness Meter können Sie den Gesamtzustand der Seite auf einen Blick erfassen.

![Die Bereitschaftszähler- und Auditkategorien im Preflight-Dashboard](./assets/overview/hero.png){align="center"}

Wenn Sie eine Ausführung anzeigen, die von einer vorherigen Sitzung neu geladen wurde, wird in der Kopfzeile angezeigt, wie lange sie durchgeführt wurde, z. B *„gestern*. Weitere Informationen finden Sie unter [Fortsetzen einer vorherigen Sitzung](./audits.md#continue-a-previous-session).

Während die Audits noch ausgeführt werden, zeigt die Bereitschaftsanzeige eine Fortschrittsleiste mit einem kurzen Status darunter an, der den aktuellen Schritt anzeigt. Wenn die Audits abgeschlossen sind, zeigt das Messgerät den endgültigen Bereitschaftsprozentsatz und die Opportunity-Anzahl an.

## Audit-Kategorien

Preflight gruppiert verwandte Audits in Kategorien wie **SEO** und **Accessibility**. Jede Kategorie wird als Karte angezeigt, die die Anzahl der gefundenen Opportunitys anzeigt oder angibt, dass alle ihre Audits ohne Opportunitys erfolgreich waren.

Erweitern Sie eine Kategorie, um ihre individuellen Audits anzuzeigen. Bei jedem Audit wird angezeigt, ob Opportunities bestanden oder gefunden wurden, eine kurze Beschreibung und eine Anzahl der gefundenen Opportunitys. Wählen Sie ein Audit aus, bei dem Möglichkeiten zum Öffnen der Detailseite gefunden wurden.

Eine vollständige Liste der Audit-Kategorien und der Audits in den einzelnen Kategorien finden Sie unter [Preflight-Auditkategorien](./overview.md#preflight-audit-categories).

## Details der Möglichkeiten

Auf der Detailseite werden die Chancen angezeigt, die der ausgewählte Audit gefunden hat. Wenn dasselbe Problem an mehr als einer Stelle auftritt, wird jedes Vorkommen als -Instanz bezeichnet. Verwenden Sie den Navigator (**vorherige Instanz** und **nächste Instanz**), um sie zu durchlaufen. Er zeigt Ihre Position an, z. B. *1 von 5 gefundenen Instanzen*. Um zum Bereitschafts-Dashboard zurückzukehren, klicken Sie auf den Rückwärtspfeil neben dem Audittitel. Das Dashboard wird erneut geöffnet, wobei die Kategorie des Audits erweitert ist.

![Die Detailseite für eine Prüfung, auf der eine Opportunity und ihr Vorschlag angezeigt werden](./assets/audit-results/audit-detail.png){align="center"}

Jede Opportunity umfasst:

* Ein Badge für den Schweregrad oder eine Auswirkung, das anzeigt, wie wichtig die Opportunity ist.
* Details zur Opportunity, z. B. eine Beschreibung des Problems, eine Empfehlung und, bei Barrierefreiheit, die zugehörige WCAG-Regel und Konformitätsstufe.
* Ein **Element**-Abschnitt, der das betroffene Element auf der Seite mit einer Schaltfläche **Hervorheben auf der Seite** identifiziert. Wenn das Element lesbaren Text enthält, wird der Abschnitt **Element: Text** benannt, andernfalls wird er mit **Element: Selektor** bezeichnet und die CSS-Auswahl des Elements angezeigt. Bei **Links** und **Canonical** wird im Abschnitt **Aktuelle URL** auch die betroffene URL angezeigt, die Sie nach Möglichkeit in einer neuen Registerkarte öffnen können.
* Ein **Vorschlag** mit einer empfohlenen Fehlerbehebung. Wenn der Vorschlag von KI generiert wird, wird er als von KI generierter Vorschlag markiert und kann eine kurze Begründung zur Erläuterung der vorgeschlagenen Korrektur enthalten.

## Auf Seite hervorheben

Nach Abschluss der Audits können Sie eine Opportunity schnell finden und verstehen, indem Sie sie direkt auf der Seite hervorheben.

Preflight markiert das betroffene Element im Kontext und verbindet das Ergebnis im Bedienfeld mit der genauen Position in Ihrem Inhalt. Dies erleichtert die Prüfung und Lösung von Möglichkeiten, ohne die Seite manuell durchsuchen zu müssen.

1. Öffnen Sie das Preflight-Bedienfeld im Kontext der zu prüfenden Seite und wählen Sie **Seite analysieren** aus, um die Prüfungen durchzuführen.
1. Wählen Sie im Bereitschafts-Dashboard eine Prüfung und dann eine zu überprüfende Gelegenheit aus.
1. Wählen Sie **Markieren auf Seite** aus. Die Vorschau scrollt automatisch zum relevanten Bereich und markiert das entsprechende Element, sodass Sie die Opportunity im Kontext leicht identifizieren und optimieren können.

Hervorheben ist nicht bei jeder Opportunity möglich. Wenn eine Opportunity beispielsweise nicht mit einem bestimmten Element verknüpft ist, ist das Element ausgeblendet oder befindet es sich nicht mehr auf der Seite. In diesen Fällen ist die Schaltfläche **Markieren auf Seite** abgeblendet. Bewegen Sie den Mauszeiger darüber, um zu sehen, warum.

Im universellen Editor wird die Hervorhebung für Opportunities **Barrierefreiheit** noch nicht unterstützt. Die Schaltfläche **Auf Seite hervorheben** ist abgeblendet, und Sie können den Mauszeiger darüber bewegen, um zu sehen, warum das so ist.

Im AEM Sites-Seiteneditor und in Adobe Managed Services (AMS) ist zum Hervorheben auch **Bearbeitungsmodus** erforderlich. Im **Vorschaumodus** zeigt Preflight **Hervorheben von Problemen nicht verfügbar** Hinweis: Wechseln Sie in den **Bearbeitungsmodus**, um Elemente auf der Seite hervorzuheben.

## Vorgangs-ID

Jeder PreFlight-Durchgang hat eine eindeutige Auftrags-ID, die unten im Bedienfeld angezeigt wird. Dies ist vor allem dann nützlich, wenn ein Administrator die Fehlerbehebung bei einer bestimmten Ausführung durchführt. Bewegen Sie den Mauszeiger über die ID und wählen Sie das Kopiersymbol rechts neben der ID aus. Die ID wird in die Zwischenablage kopiert und eine Bestätigungsmeldung wird angezeigt. Fügen Sie diese ID bei der Meldung eines Problems hinzu.

Wenn Sie Preflight außerhalb des universellen Editors verwenden - z. B. über die Sidekick oder eine Lesezeichenliste -, wird in der Fußzeile des Bedienfelds auch Ihr Organisationsname über der Auftrags-ID angezeigt. Im universellen Editor wird Ihre Organisation stattdessen in der Kopfzeile von AEM angezeigt.
