---
title: Dokumentation zur Möglichkeit „Website-Berechtigungen“
description: Erfahren Sie mehr über die Opportunity „Website-Berechtigungen“ und finden Sie heraus, wie Sie damit die Sicherheit auf Ihrer Website erhöhen können.
badgeSecurityPosture: label="Sicherheitsstatus" type="Caution" url="../../opportunity-types/security-posture.md" tooltip="Sicherheitsstatus"
source-git-commit: cb64a34b758de8f5dcea298014ddd0ba79a24c17
workflow-type: tm+mt
source-wordcount: '220'
ht-degree: 79%

---


# Möglichkeit „Website-Berechtigungen“

![Möglichkeit „Website-Berechtigungen“](./assets/website-permissions/hero.png){align="center"}

Die Möglichkeit „Website-Berechtigungen“ optimiert Website-Berechtigungen, die für die Aufrechterhaltung einer sicheren und verwaltbaren AEM-Umgebung von entscheidender Bedeutung sind. Mit dieser Möglichkeit können Sie die Zugriffssteuerung verfeinern, indem Sie übermäßig umfassende Berechtigungen entfernen – z. B. `jcr:all` in generischen Pfaden wie `/` oder `/content` – und den Benutzerzugriff an das Prinzip der geringsten Berechtigung anpassen. Durch das Optimieren von Berechtigungen und das Beseitigen von Redundanzen können Sie Sicherheitsrisiken reduzieren, die Wartbarkeit verbessern und zukünftige Fehlkonfigurationen verhindern. Überprüfen und aktualisieren Sie Berechtigungen in der AEM-Sicherheitsberechtigungskonsole oder in Ihrem Code-Repository. Dadurch wird sichergestellt, dass Service-Benutzer nur den Zugriff haben, den sie wirklich benötigen.

## Automatische Identifizierung

![Automatisches Identifizieren von Website-Berechtigungen](./assets/website-permissions/auto-identify.png){align="center"}

Die Funktion **Möglichkeit „Website-Berechtigungen“** identifiziert und listet Folgendes automatisch auf:

* **Benutzer**: Das Benutzerkonto mit der fragwürdigen Berechtigung.
* **Pfad** - Verwenden Sie die Registerkarten oben, um Opportunities zu organisieren und nach Status zu filtern.
* **Permission** - Die vermutete Berechtigung.
* **Problem**: Gibt die Art des Problems an, das sich auf die Berechtigung auswirkt. 

## Automatische Vorschläge

![Automatische Vorschläge für Website-Schwachstellen](./assets/website-permissions/auto-suggest.png){align="center"}

Das automatische Vorschlagen bietet KI-generierte Empfehlungen im Feld **Empfohlene Berechtigungen**, mit denen Sie jede markierte Berechtigung durch eine sichere Alternative ersetzen können.

## Automatische Optimierung

[!BADGE Ultimate]{type=Positive tooltip="Ultimate"}

![Automatisches Optimieren von Website-Berechtigungen](./assets/website-permissions/auto-optimize.png){align="center"}

Sites Optimizer Ultimate ermöglicht es, eine automatische Optimierung für die gefundenen Schwachstellen bereitzustellen.

>[!BEGINTABS]

>[!TAB Optimierung bereitstellen]

{{auto-optimize-deploy-optimization-slack}}

>[!TAB Genehmigung anfordern]

{{auto-optimize-request-approval}}

>[!ENDTABS]
