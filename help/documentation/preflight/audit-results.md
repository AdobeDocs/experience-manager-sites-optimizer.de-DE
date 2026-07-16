---
title: Audit-Ergebnisse in Preflight
description: Erfahren Sie, wie Sie die Ergebnisse der Preflight-Prüfung, den Bereitschaftszähler und die Auditkategorien interpretieren und zu Opportunities in der Vorschau navigieren können.
source-git-commit: f19dd2eec5cef95f406111d2250ff1101a4fd430
workflow-type: tm+mt
source-wordcount: '597'
ht-degree: 5%

---


# Audit-Ergebnisse in Preflight

Nach Abschluss der Audits zeigt Preflight die Ergebnisse im Bereitschafts-Dashboard an. Im Dashboard werden die Gesamtbereitschaftsanzeige und die gefundenen Opportunities gruppiert nach Auditkategorie angezeigt. Innerhalb jeder Kategorie werden bei individuellen Audits spezifische Elemente identifiziert, die überprüft oder korrigiert werden müssen.

## Betriebsbereitschaftsmesser

Oben im Dashboard zeigt die Bereitschaftsanzeige die Ergebnisse der Prüfung an. Er zeigt einen Bereitschaftswert in Prozent an, basierend auf dem Anteil der Prüfungen, die ohne Opportunities abgeschlossen wurden, und der Gesamtzahl der in allen Prüfungen gefundenen Opportunitys. Mit dem Readiness Meter können Sie den Gesamtzustand der Seite auf einen Blick erfassen.

![Die Bereitschaftszähler- und Auditkategorien im Preflight-Dashboard](./assets/overview/hero.png){align="center"}

Während die Audits noch ausgeführt werden, zeigt die Bereitschaftsanzeige eine Fortschrittsleiste mit einem Status wie &quot;**Audits“** die Anzahl der noch laufenden Audits an. Wenn die Audits abgeschlossen sind, zeigt das Messgerät den endgültigen Bereitschaftsprozentsatz und die Opportunity-Anzahl an.

## Audit-Kategorien

Preflight gruppiert verwandte Audits in Kategorien wie **SEO** und **Accessibility**. Jede Kategorie wird als Karte angezeigt, die die Anzahl der gefundenen Opportunitys anzeigt oder angibt, dass alle ihre Audits ohne Opportunitys erfolgreich waren.

Erweitern Sie eine Kategorie, um ihre individuellen Audits anzuzeigen. Bei jedem Audit wird angezeigt, ob Opportunities bestanden oder gefunden wurden, eine kurze Beschreibung und eine Anzahl der gefundenen Opportunitys. Wählen Sie ein Audit aus, bei dem Möglichkeiten zum Öffnen der Detailseite gefunden wurden.

Eine vollständige Liste der Audit-Kategorien und der Audits in den einzelnen Kategorien finden Sie unter [Preflight-Auditkategorien](./overview.md#preflight-audit-categories).

## Details der Möglichkeiten

Auf der Detailseite werden die Chancen angezeigt, die der ausgewählte Audit gefunden hat. Wenn dasselbe Problem an mehr als einer Stelle auftritt, wird jedes Vorkommen als -Instanz bezeichnet. Verwenden Sie den Navigator (**vorherige Instanz** und **nächste Instanz**), um sie zu durchlaufen. Er zeigt Ihre Position an, z. B. *1 von 5 gefundenen Instanzen*.

![Die Detailseite für eine Prüfung, auf der eine Opportunity und ihr Vorschlag angezeigt werden](./assets/audit-results/audit-detail.png){align="center"}

Jede Opportunity umfasst:

* Ein Badge für den Schweregrad oder eine Auswirkung, das anzeigt, wie wichtig die Opportunity ist.
* Details zur Opportunity, z. B. eine Beschreibung des Problems, eine Empfehlung und, bei Barrierefreiheit, die zugehörige WCAG-Regel und Konformitätsstufe.
* Ein **Element**-Abschnitt, der das betroffene Element auf der Seite mit einer Schaltfläche **Hervorheben auf der Seite** anzeigt.
* Ein **Vorschlag** mit einer empfohlenen Fehlerbehebung. Wenn der Vorschlag von KI generiert wird, wird er als von KI generierter Vorschlag markiert und kann eine kurze Begründung zur Erläuterung der vorgeschlagenen Korrektur enthalten.

## Auf Seite hervorheben

Nach Abschluss der Audits können Sie eine Opportunity schnell finden und verstehen, indem Sie sie direkt auf der Seite hervorheben.

Preflight markiert das betroffene Element im Kontext und verbindet das Ergebnis im Bedienfeld mit der genauen Position in Ihrem Inhalt. Dies erleichtert die Prüfung und Lösung von Möglichkeiten, ohne die Seite manuell durchsuchen zu müssen.

1. Öffnen Sie das Preflight-Bedienfeld im Kontext der zu prüfenden Seite und wählen Sie **Seite analysieren** aus, um die Prüfungen durchzuführen.
1. Wählen Sie im Bereitschafts-Dashboard eine Prüfung und dann eine zu überprüfende Gelegenheit aus.
1. Wählen Sie **Markieren auf Seite** aus. Die Vorschau scrollt automatisch zum relevanten Bereich und markiert das entsprechende Element, sodass Sie die Opportunity im Kontext leicht identifizieren und optimieren können.

## Vorgangs-ID

Jeder PreFlight-Durchgang hat eine eindeutige Auftrags-ID, die unten im Bedienfeld angezeigt wird. Dies ist vor allem dann nützlich, wenn ein Administrator die Fehlerbehebung bei einer bestimmten Ausführung durchführt. Bewegen Sie den Mauszeiger über die ID und wählen Sie das Kopiersymbol rechts neben der ID aus. Die ID wird in die Zwischenablage kopiert und eine Bestätigungsmeldung wird angezeigt. Fügen Sie diese ID bei der Meldung eines Problems hinzu.
