---
title: Dokumentation zu fehlendem Alternativtext
description: Erfahren Sie mehr über die Möglichkeit „Fehlender Alternativtext“ und darüber, wie Sie sie zur Verbesserung der Interaktion auf Ihrer Website verwenden können.
badgeEngagement: label="Interaktion" type="Caution" url="../../opportunity-types/engagement.md" tooltip="Interaktion"
source-git-commit: 8052c94f778829012f023fe470411dfe77ef46b9
workflow-type: tm+mt
source-wordcount: '689'
ht-degree: 37%

---


# Möglichkeit „Fehlender Alternativtext“

![Möglichkeit „Fehlender Alternativtext“](./assets/missing-alt-text/hero.png){align="center"}

Die fehlende Alternativtext-Opportunity identifiziert Bilder auf Ihrer Website, die keinen beschreibenden Alternativtext haben. Ohne Alternativtext können Benutzende, die auf Bildschirmlesehilfen angewiesen sind, visuelle Inhalte nicht interpretieren und schaffen somit Barrierefreiheitsbarrieren. Darüber hinaus wird die Art und Weise, wie Suchmaschinen Bilder verstehen und indizieren, eingeschränkt, was die Auffindbarkeit von Inhalten und die Suchleistung verringert. AEM Sites Optimizer erkennt Probleme mit fehlendem ALT-Text, bietet spezifische KI-Empfehlungen und ermöglicht eine Bereitstellung mit einem Klick, um sie zu beheben, und das alles in einer zentralen Ansicht.

## Automatische Identifizierung

![Automatisches Identifizieren von fehlendem Alternativtext](./assets/missing-alt-text/auto-identify.png){align="center"}

AEM Sites Optimizer scannt Ihre Website mithilfe eines mehrstufigen Audits, bei dem Website-crawlen, echte Benutzer-Traffic-Daten und KI-Analysen kombiniert werden, um Bilder zu identifizieren, für die Alt-Text erforderlich ist, aber nicht definiert wurde. Außerdem werden Bilder auf der Seite ausgewertet, um zu ermitteln, ob alternativer Text erforderlich ist. Ausgenommen sind dekorative oder nicht-informative Bilder gemäß den Web Content Accessibility Guidelines (WCAG). Bilder werden anhand ihrer Rolle und Relevanz innerhalb der Seite analysiert, wobei Korrekturen mit den höchsten Prioritäten für Barrierefreiheit und SEO-Optimierung ausgewählt werden.

Diese Gelegenheit bietet eine Liste der identifizierten Probleme, einschließlich:

* **Seite**: Der Pfad zu der Seite mit dem fehlenden Alternativtext.
* **Bild**: Das Bild, bei dem der beschreibende Alternativtext fehlt.

## Automatische Vorschläge

![Automatische Vorschläge für fehlenden Alternativtext](./assets/missing-alt-text/auto-suggest.png){align="center"}

Für jedes identifizierte Problem schlägt AEM Sites Optimizer einen beschreibenden Alternativtext für das Bild vor. Es verwendet KI-Vision-Modelle, um das Bild zu analysieren und eine Beschreibung zu generieren, die seinen Inhalt und seine Rolle innerhalb der Seite widerspiegelt. Die Empfehlungen sind kurz gefasst, relevant und auf die Best Practices zur Barrierefreiheit abgestimmt. Jeder Vorschlag kann vor seiner Anwendung überprüft und bearbeitet werden.

>[!BEGINTABS]

>[!TAB Fehlenden Alternativtext bearbeiten]

![Fehlenden Alternativtext bearbeiten](./assets/missing-alt-text/edit-alt-text-value.png){align="center"}

Wenn Sie mit dem KI-generierten Vorschlag nicht einverstanden sind, können Sie den vorgeschlagenen Alternativtext bearbeiten, indem Sie das **Symbol „Bearbeiten“** auswählen. Auf diese Weise können Sie manuell den Text eingeben, der Ihrer Meinung nach am besten für das Bild geeignet ist. Das Bearbeitungsfenster enthält Folgendes:

* **Seitenpfad**: Ein schreibgeschütztes Feld, das den Pfad zu der Seite anzeigt, auf der das Problem mit dem fehlenden Alternativtext auftritt. Klicken Sie auf den Pfeil neben dem Pfad, um die entsprechende Seite zu öffnen.
* **Bild**: Eine schreibgeschützte Vorschau des Bildes, für das ein Alternativtext erforderlich ist.
* **Ziel-Alternativtext**: Ein bearbeitbares Feld, in dem Sie manuell einen beschreibenden Alternativtext für das Bild eingeben können. Stellen Sie sicher, dass der Alternativtext den Inhalt und den Zweck des Bildes klar und deutlich vermittelt. Schließen Sie ggf. auf natürliche Weise Keywords ein, ohne sie jedoch im Übermaß zu verwenden.

>[!TAB Einträge ignorieren]

Sie können Einträge aus der Liste der Möglichkeiten ignorieren. Durch Auswählen von ![Symbol „Löschen“](https://spectrum.adobe.com/static/icons/ui_18/CrossSize500.svg) wird der Eintrag aus der Liste entfernt. Ignorierte Einträge können über die Registerkarte **Ignoriert** oben auf der Seite der Möglichkeiten erneut aktiviert werden.

>[!ENDTABS]

## Automatische Optimierung

[!BADGE Ultimate]{type=Positive tooltip="Ultimate"}

>[!VIDEO](https://video.tv.adobe.com/v/3483273/?captions=ger&learn=on&enablevpops)

Sobald die Vorschläge geprüft und genehmigt wurden, können Sie auf **Optimierung bereitstellen** klicken. AEM Sites Optimizer wendet die Fehlerbehebungen dann in der Autorenumgebung an, je nachdem, wie ALT-Text in Ihrer Implementierung verwaltet wird. Der AEM-Autor kann dann die Änderungen über das Content Management System (CMS) veröffentlichen.

Abhängig von der Konfiguration können Aktualisierungen direkt auf Seiteninhalte, Asset-Metadaten oder unterstützende Inhaltsmodelle angewendet werden. Der Optimierungsprozess umfasst die folgenden Schritte:

* **Validierung** - Stellt sicher, dass Aktualisierungen sicher angewendet werden, ohne die vorhandene Funktionalität zu beeinträchtigen.
* **Bereitstellung** - Wendet die Aktualisierungen über vorhandene Prozesse an, z. B. Inhaltsaktualisierungen in AEM oder die Integration in Inhalts-APIs.
* **Berechtigungsprüfung** - Prüft, ob der Benutzer über die entsprechenden Berechtigungen zum Anwenden von Änderungen verfügt. Andernfalls können alternative Ausgaben wie herunterladbare Updates für die Übergabe verwendet werden.

Aktualisierungen werden versioniert, wo unterstützt, und bieten Sichtbarkeit und Rollback-Kapazität. Dadurch wird sichergestellt, dass ALT-Text-Aktualisierungen korrekt angewendet werden, mit bestehenden Implementierungen abgestimmt sind und mit Governance- und Barrierefreiheitsstandards konsistent sind.

AEM Sites Optimizer wendet basierend auf Ihrer Einrichtung automatisch Aktualisierungen des ALT-Texts an wie folgt:

>[!BEGINTABS]

>[!TAB Edge Delivery Services]

Aktualisiert das Quelldokument (z. B. Google Docs oder SharePoint)

>[!TAB AEM as a Cloud Service]

Schreibt Aktualisierungen direkt über die Content-API mit Versionierungs- und Fallback-Unterstützung.

>[!TAB Digital Asset Management (optional)]

Aktualisiert gegebenenfalls Alt-Text auf Asset-Ebene.

>[!ENDTABS]
