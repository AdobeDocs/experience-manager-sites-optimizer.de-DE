---
title: Dokumentation zu Website-Schwachstellen und Opportunities
description: Erfahren Sie mehr über die Website-Schwachstellen und wie Sie damit die Sicherheit von auf Ihrer Website erhöhen können.
badgeSecurityPosture: label="Sicherheitsstatus" type="Caution" url="../../opportunity-types/security-posture.md" tooltip="Sicherheitsstatus"
source-git-commit: ab2d75b1d986d83e3303e29a25d2babd1598394a
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 1%

---


# Website-Schwachstellen-Chance

![Website-Schwachstellen-Chance](./assets/website-vulnerabilities/hero.png){align="center"}

Die Website-Schwachstellen-Opportunity identifiziert Sicherheitslücken in den Drittanbieterbibliotheken, die von Ihrem Programm-Code verwendet werden. Diese Sicherheitslücken könnten von einem böswilligen Angreifer ausgenutzt werden, was das Risiko erhöht und den Sicherheitszustand Ihrer Website verringert.

Die Opportunity für Sicherheitslücken auf der Website zeigt oben auf der Seite eine Zusammenfassung, die u. a. Folgendes enthält:

* **Gefundene Probleme** - Die Anzahl der gefundenen Sicherheitslücken, kategorisiert durch das von ihnen ausgehende Sicherheitsrisiko (niedrig, mittel, hoch).
* **Aggregiertes Sicherheitsrisiko** - Das allgemeine Sicherheitsrisiko für Ihre Website, basierend auf den bei der Opportunity gefundenen Sicherheitslücken.

## Automatisch identifizieren

![Website-Schwachstellen automatisch identifizieren](./assets/website-vulnerabilities/auto-identify.png){align="center"}

Die **Website-Schwachstellen-Opportunity** identifiziert und listet automatisch Schwachstellen in Drittanbieterbibliotheken auf, die von Ihrem Programm-Code verwendet werden. Sie enthält die folgenden Details:

* **Library** - Die Drittanbieterbibliothek, die die Sicherheitslücke enthält. Eine einzelne Bibliothek kann mehrere Schwachstellen aufweisen.
* **Aktuelle Version** - Die Version der derzeit verwendeten Bibliothek.
* **Empfohlene Version** - Die vorgeschlagene Version, die die Sicherheitslücke behebt.
* **Score** - Die Bewertung des Schweregrads der Sicherheitslücke, die ebenfalls oben auf der Seite zusammengefasst wird.
* **Schwachstelle** - Die Schwachstellenkennung, eine kurze Beschreibung und ein Link zur National Vulnerability Database (NVD) für weitere Details. Greifen Sie auf den NVD-Link zu, indem Sie auf die Kennung oder den Link neben der Beschreibung klicken.

## Automatisch vorschlagen

![Website-Schwachstellen automatisch vorschlagen](./assets/website-vulnerabilities/auto-suggest.png){align="center"}

Auto-Suggest liefert KI-generierte Vorschläge für die **empfohlene Version** anfälliger Bibliotheken, auf die Sie aktualisieren sollten. Jeder Eintrag hat einen **Score**, der den Gesamtschweregrad angibt und dabei hilft, die kritischsten Schwachstellen zu priorisieren.

>[!BEGINTABS]

>[!TAB Details zur Sicherheitslücke]

Jede Sicherheitslücke enthält einen Link zu den detaillierten Informationen in der [National Vulnerability Database (NVD)](https://nvd.nist.gov/). Durch Klicken auf die Schwachstellenkennung oder den Link rechts neben der Beschreibung gelangen Sie zur NVD-Seite für diese Schwachstelle.

>[!TAB Einträge ignorieren]

Sie können Einträge aus der Liste der Schwachstellen ignorieren. Wenn Sie auf das **Ignorieren** klicken, wird der Eintrag aus der Liste entfernt. Ignorierte Einträge können über die Registerkarte **Ignoriert** oben auf der Opportunity-Seite erneut aktiviert werden.<!---right now it does not seem to be implemented, but the page description mentions this functionality-->

>[!ENDTABS]


## [!BADGE Ultimate automatisch optimieren]{type=Positive tooltip="Ultimate"}

![Website-Schwachstellen automatisch optimieren](./assets/website-vulnerabilities/auto-optimize.png){align="center"}

Sites Optimizer Ultimate bietet die Möglichkeit, eine automatische Optimierung für die gefundenen Sicherheitslücken bereitzustellen.

>[!BEGINTABS]

>[!TAB Optimierung bereitstellen]

{{auto-optimize-deploy-optimization-slack}}

>[!TAB Bestätigung anfordern]

{{auto-optimize-request-approval}}

>[!ENDTABS]