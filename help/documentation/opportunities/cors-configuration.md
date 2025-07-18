---
title: Dokumentation zur Möglichkeit „CORS-Konfiguration“
description: Erfahren Sie mehr über die Opportunity „CORS-Konfiguration“ und finden Sie heraus, wie Sie Sicherheitsschwachstellen auf der Site identifizieren und beheben.
badgeSecurityPosture: label="Sicherheitsstatus" type="Caution" url="../../opportunity-types/security-posture.md" tooltip="Sicherheitsstatus"
source-git-commit: cb64a34b758de8f5dcea298014ddd0ba79a24c17
workflow-type: tm+mt
source-wordcount: '193'
ht-degree: 87%

---


# Möglichkeit „CORS-Konfiguration“

![Möglichkeit „CORS-Konfiguration“](./assets/cors-configuration/hero.png){align="center"}

Die ordnungsgemäße Konfiguration von Cross-Origin Resource Sharing (CORS) ist unerlässlich, um Web-Anwendungen vor nicht autorisiertem Datenzugriff zu schützen. Wenn der `Access-Control-Allow-Origin`-Header auf `*` gesetzt ist, kann jede Domain Antworten anfordern und empfangen, wodurch Angreifern möglicherweise vertrauliche Informationen offenbart werden. Diese Funktion bietet die Möglichkeit, die Sicherheit zu erhöhen, indem eine kontrollierte Zulassungsliste vertrauenswürdiger Domains implementiert oder CORS deaktiviert wird, wenn dies nicht erforderlich ist. Mit einem sicheren CORS-Setup tragen Sie zum Schutz privater Inhalte bei und helfen gleichzeitig, einen nahtlosen Zugriff für autorisierte Benutzende zu gewährleisten.

## Automatische Identifizierung

![Automatische Identifizierung der Möglichkeit „CORS-Konfiguration“](./assets/cors-configuration/auto-identify.png){align="center"}

Die automatische Identifizierung überprüft Ihre Website auf CORS-Fehlkonfigurationen und erkennt URLs, die anfällig für einen nicht autorisierten Zugriff sind. Diese URLs werden in der oberen Tabelle zusammen mit den folgenden Details aufgeführt:

* **Seitenpräfix** – Das URL-Pfadpräfix, das anfällig für eine CORS-Fehlkonfiguration ist.
* **Seitenbeispiel** – Eine Beispiel-URL, die für nicht autorisierten Zugriff anfällig ist.

## Automatische Vorschläge

![Automatische Vorschläge für die Möglichkeit „CORS-Konfiguration“](./assets/cors-configuration/auto-suggest.png){align="center"}

Bereitstellung automatischer Vorschläge zu **Anwendungs-Code-Dateien** und ihrer betreffenden **Zeilen**, die im Hinblick auf möglicherweise zu lockere CORS-Richtlinien überprüft werden sollten.


## Automatische Optimierung

[!BADGE Ultimate]{type=Positive tooltip="Ultimate"}

>[!BEGINTABS]

>[!TAB Optimierung bereitstellen]

{{auto-optimize-deploy-optimization-slack}}

>[!TAB Genehmigung anfordern]

{{auto-optimize-request-approval}}

>[!ENDTABS]
