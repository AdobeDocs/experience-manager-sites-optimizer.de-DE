---
title: Website-Zugriffsberechtigungen - Opportunity-Dokumentation
description: Erfahren Sie mehr über die Website-Berechtigungschance und wie Sie damit die Sicherheit von auf Ihrer Website erhöhen können.
badgeSecurityPosture: label="Sicherheitsstatus" type="Caution" url="../../opportunity-types/security-posture.md" tooltip="Sicherheitsstatus"
source-git-commit: 5d1ae616ddde74f69b73ba5b44297c14b2dea36b
workflow-type: tm+mt
source-wordcount: '218'
ht-degree: 2%

---


# Website-Zugriffsmöglichkeit

![Website-Berechtigungs-Opportunity](./assets/website-permissions/hero.png){align="center"}

Die Website-Berechtigungs-Opportunity optimiert Website-Berechtigungen, die für die Aufrechterhaltung einer sicheren und verwaltbaren AEM-Umgebung von entscheidender Bedeutung sind. Diese Möglichkeit ermöglicht es Ihnen, die Zugriffssteuerung zu verfeinern, indem Sie übermäßig umfassende Berechtigungen entfernen - z. B. `jcr:all` für generische Pfade wie `/` oder `/content` - und den Benutzerzugriff an das Prinzip der geringsten Berechtigung anpassen. Durch die Optimierung von Berechtigungen und die Beseitigung von Redundanzen können Sie Sicherheitsrisiken reduzieren, die Wartbarkeit verbessern und zukünftige Fehlkonfigurationen verhindern. Ergreifen Sie Maßnahmen, indem Sie die Berechtigungen in der AEM-Sicherheitsberechtigungskonsole oder Ihrem Code-Repository überprüfen und aktualisieren und so sicherstellen, dass Dienstbenutzende nur den Zugriff haben, den sie wirklich benötigen.

## Automatisch identifizieren

![Website-Berechtigungen automatisch identifizieren](./assets/website-permissions/auto-identify.png){align="center"}

Die **Opportunity für Websiteberechtigungen** identifiziert und listet automatisch auf

* **Benutzer** - Das Benutzerkonto mit der Berechtigung „Verdächtig“.
* **Path** - Der Pfad in AEM, der von der Berechtigung betroffen ist.
* **Permission** - Die verdächtige Berechtigung.
* **Problem** - Gibt die Art des Problems an, das sich auf die Berechtigung auswirkt.

## Automatisch vorschlagen

![Website-Schwachstellen automatisch vorschlagen](./assets/website-permissions/auto-suggest.png){align="center"}

Der automatische Vorschlag bietet KI-generierte Empfehlungen im Feld **Vorgeschlagene Berechtigungen** mit denen Sie alle gekennzeichneten Berechtigungen durch sichere Alternativen ersetzen können.

## [!BADGE Ultimate automatisch optimieren]{type=Positive tooltip="Ultimate"}

![Website-Berechtigungen automatisch optimieren](./assets/website-permissions/auto-optimize.png){align="center"}

Sites Optimizer Ultimate bietet die Möglichkeit, eine automatische Optimierung für die gefundenen Sicherheitslücken bereitzustellen.

>[!BEGINTABS]

>[!TAB Optimierung bereitstellen]

{{auto-optimize-deploy-optimization-slack}}

>[!TAB Bestätigung anfordern]

{{auto-optimize-request-approval}}

>[!ENDTABS]
