---
title: Dokumentation zur Möglichkeit „Website-Berechtigungen“
description: Erfahren Sie mehr über die Opportunity „Website-Berechtigungen“ und finden Sie heraus, wie Sie damit die Sicherheit auf Ihrer Website erhöhen können.
badgeSecurityPosture: label="Sicherheitsstatus" type="Caution" url="../../opportunity-types/security-posture.md" tooltip="Sicherheitsstatus"
source-git-commit: c99bd0ab418c1eb0693f39ea16ee41f8a1263099
workflow-type: tm+mt
source-wordcount: '218'
ht-degree: 99%

---


# Möglichkeit „Website-Berechtigungen“

![Möglichkeit „Website-Berechtigungen“](./assets/website-permissions/hero.png){align="center"}

Die Möglichkeit „Website-Berechtigungen“ optimiert Website-Berechtigungen, die für die Aufrechterhaltung einer sicheren und verwaltbaren AEM-Umgebung von entscheidender Bedeutung sind. Mit dieser Möglichkeit können Sie die Zugriffssteuerung verfeinern, indem Sie übermäßig umfassende Berechtigungen entfernen – z. B. `jcr:all` in generischen Pfaden wie `/` oder `/content` – und den Benutzerzugriff an das Prinzip der geringsten Berechtigung anpassen. Durch das Optimieren von Berechtigungen und das Beseitigen von Redundanzen können Sie Sicherheitsrisiken reduzieren, die Wartbarkeit verbessern und zukünftige Fehlkonfigurationen verhindern. Ergreifen Sie Maßnahmen, indem Sie die Berechtigungen in der Konsole der AEM-Sicherheitsberechtigungen oder in Ihrem Code-Repository überprüfen und aktualisieren und so sicherstellen, dass Dienstbenutzende nur den Zugriff haben, den sie wirklich benötigen.

## Automatische Identifizierung

![Automatisches Identifizieren von Website-Berechtigungen](./assets/website-permissions/auto-identify.png){align="center"}

Die Funktion **Möglichkeit „Website-Berechtigungen“** identifiziert und listet Folgendes automatisch auf:

* **Benutzer**: Das Benutzerkonto mit der fragwürdigen Berechtigung.
* **Pfad**: Der Pfad in AEM, der von der Berechtigung betroffen ist.
* **Berechtigung**: Die fragwürdige Berechtigung.
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
