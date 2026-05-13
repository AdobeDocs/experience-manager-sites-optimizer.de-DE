---
title: Dokumentation zur Möglichkeit „Core Web Vitals“
description: Erfahren Sie mehr über die Möglichkeit „Core Web Vital“ und darüber, wie Sie sie zur Verbesserung der Traffic-Akquise nutzen können.
badgeSiteHealth: label="Site-Zustand" type="Caution" url="../../opportunity-types/site-health.md" tooltip="Site-Zustand"
TQID: https://experienceleague.adobe.com/3h-Xas767zUk-Sod7JEr9Lh767r5S3LKpbwJZFZU2kg
product_v2: id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
topic_v2: id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
source-git-commit: 84a1ae98d67bc02ab272131194511efbeccab492
workflow-type: tm+mt
source-wordcount: 533
ht-degree: 100%

---

# Möglichkeit „Core Web Vitals“

<!--![core web vitals opportunity](./assets/core-web-vitals/hero.png){align="center"}-->

>[!VIDEO](https://video.tv.adobe.com/v/3483371/?learn=on&enablevpops)

Die Core Web Vitals-Möglichkeit identifiziert Seiten auf Ihrer Website, die eine niedrige Leistung aufweisen und das Benutzererlebnis und die organische Suchleistung beeinträchtigen. Diese Probleme können durch Faktoren wie benutzerdefinierte Schriftarten, nicht optimierte JavaScript-Abhängigkeiten und Drittanbieterskripte verursacht werden. Core Web Vitals misst, wie schnell Inhalte geladen werden, wie stabil das Seiten-Layout ist und wie responsiv die Seite gegenüber Benutzerinteraktionen ist.

AEM Sites Optimizer erkennt von diesen Problemen betroffene Seiten, stellt spezifische KI-Empfehlungen auf Code-Ebene bereit und wendet Fehlerbehebungen über Ihre bestehenden Entwicklungs-Workflows an. Beachten Sie, dass nur Seiten mit mindestens 1000 Seitenansichten analysiert werden können.

## Automatische Identifizierung

<!--![Auto-identify core web vitals](./assets/core-web-vitals/auto-identify.png){align="center"}-->

AEM Sites Optimizer überwacht kontinuierlich die Site-Performance mit [Operational Telemetry](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/sites/operational-telemetry-for-aem-as-a-cloud-service) um Regressionen in Core Web Vitals-Metriken wie Largest Contentful Paint (LCP), Cumulative Layout Shift (CLS) und Interaction to Next Paint (INP) zu erkennen. Er verwendet echte Benutzerdaten, um Leistungsregressionen zu identifizieren, und priorisiert Probleme basierend auf ihren Auswirkungen auf das Benutzererlebnis.

AEM Sites Optimizer zeigt eine Liste aller aktuellen Probleme an, die nach Mobilgerät und Desktop-Computer aufgeschlüsselt ist. Die Spalte **Seite** zeigt den betroffenen Seiteneintrag an und Probleme werden nach LCP, INP und CLS kategorisiert.

## Automatische Vorschläge

<!--![Auto-suggest core web vitals opportunity](./assets/core-web-vitals/auto-suggest.png){align="center"}-->

Für jedes identifizierte Problem generiert AEM Sites Optimizer präskriptive Empfehlungen auf Code-Ebene, um die Core Web Vitals-Leistung zu verbessern. Er bewertet die zugrunde liegende Implementierung durch Zugriff auf Ihr Code-Repository. Auf diese Weise kann das System analysieren, wie Komponenten, Skripte und Stile implementiert werden, und die Grundursache der Leistungsprobleme identifizieren. Basierend auf dieser Analyse stellt das System zielgerichtete Empfehlungen bereit und generiert Code-Patches, die die Änderungen angeben, die zur Verbesserung der Leistung erforderlich sind. Jede Empfehlung kann vor ihrer Anwendung geprüft werden.

Wenn Sie auf die Schaltfläche „Vorschläge“ klicken, wird ein neues Fenster mit den Leistungsmetriken LCP, INP und CLS als Kategorien angezeigt. Sie können zwischen diesen Kategorien wechseln, um jeweils die Liste mit spezifischen Problemen anzuzeigen. Jede Kategorie kann mehrere Probleme enthalten. Scrollen Sie daher nach unten, um die vollständige Liste der Probleme und Empfehlungen anzuzeigen. Darüber hinaus gibt es für jede Metrik zwei Leistungsanzeigen, eine für Mobilgeräte und eine für Desktops.

## Automatische Optimierung

<!--[!BADGE Ultimate]{type=Positive tooltip="Ultimate"}-->

Sobald die Empfehlungen geprüft und genehmigt wurden, können Sie auf **Optimierung bereitstellen** klicken. AEM Sites Optimizer generiert Code-Patches basierend auf den identifizierten Problemen und stellt diese über Versionskontrollprozesse zur Verfügung. Der Optimierungsprozess umfasst die folgenden Schritte:

* **Problemerstellung** – Erstellt für jede Fehlerbehebung ein gelabeltes GitHub-Problem, einschließlich einer klaren Beschreibung und der betroffenen URL für die Sichtbarkeit.
* **Versand der Pull-Anfrage** – Öffnet automatisch eine verknüpfte Pull-Anfrage mit der genauen Code-Korrektur, die zum Prüfen, Testen und Zusammenführen bereit ist.
* **Status-Tracking** – Verfolgt jede Fehlerbehebung bis zum Abschluss nach und kennzeichnet partielle oder fehlgeschlagene Versuche zur Nachverfolgung.

Bevor diese Aktualisierungen verfügbar gemacht werden, führt AEM Sites Optimizer eine Validierung durch, um sicherzustellen, dass die Korrekturen das zugrunde liegende Problem beheben und keine Regressionen einführen. Alle Aktualisierungen entsprechen den üblichen Entwicklungspraktiken und müssen geprüft und genehmigt werden, bevor sie in die Produktion übernommen werden können.

So wird sichergestellt, dass Leistungsoptimierungen präzise und validiert sind und in bestehende Entwicklungs- und Governance-Prozesse integriert werden.
