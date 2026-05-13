---
title: Dokumentation zur Möglichkeit „Website-Berechtigungen“
description: Erfahren Sie mehr über die Opportunity „Website-Berechtigungen“ und finden Sie heraus, wie Sie damit die Sicherheit auf Ihrer Website erhöhen können.
badgeSecurityPosture: label="Sicherheitsstatus" type="Caution" url="../../opportunity-types/security-posture.md" tooltip="Sicherheitsstatus"
TQID: https://experienceleague.adobe.com/9nGa4iRd0cBuWSUZxLvbXXo1Rx84ZqMLnD8lF8XkayU
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
topic_v2:
  - id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: 252f5292d6dc62711b4ebeb8ce5a2707857fd674
workflow-type: tm+mt
source-wordcount: 227
ht-degree: 100%

---

# Möglichkeit „Website-Berechtigungen“

![Möglichkeit „Website-Berechtigungen“](./assets/website-permissions/hero.png){align="center"}

Die Möglichkeit „Website-Berechtigungen“ optimiert Website-Berechtigungen, die für die Aufrechterhaltung einer sicheren und verwaltbaren AEM-Umgebung von entscheidender Bedeutung sind. Mit dieser Möglichkeit können Sie die Zugriffssteuerung verfeinern, indem Sie übermäßig umfassende Berechtigungen entfernen – z. B. `jcr:all` in generischen Pfaden wie `/` oder `/content` – und den Benutzerzugriff an das Prinzip der geringsten Berechtigung anpassen. Durch das Optimieren von Berechtigungen und das Beseitigen von Redundanzen können Sie Sicherheitsrisiken reduzieren, die Wartbarkeit verbessern und zukünftige Fehlkonfigurationen verhindern. Überprüfen und aktualisieren Sie Berechtigungen in der AEM-Konsole für Sicherheitsberechtigungen oder in Ihrem Code-Repository. So wird sichergestellt, dass Service-Benutzerinnen und -Benutzer nur den Zugriff haben, den sie wirklich benötigen.

## Automatische Identifizierung

![Automatisches Identifizieren von Website-Berechtigungen](./assets/website-permissions/auto-identify.png){align="center"}

Die Funktion **Möglichkeit „Website-Berechtigungen“** identifiziert und listet Folgendes automatisch auf:

* **Benutzer**: Das Benutzerkonto mit der fragwürdigen Berechtigung.
* **Pfad**: Verwenden Sie die Registerkarten oben, um Möglichkeiten nach Status zu organisieren und zu filtern.
* **Berechtigung**: Die vermutete Berechtigung.
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

>[!TAB Bestätigung anfordern]

{{auto-optimize-request-approval}}

>[!ENDTABS]
