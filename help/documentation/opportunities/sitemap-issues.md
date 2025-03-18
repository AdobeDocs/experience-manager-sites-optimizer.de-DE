---
title: Sitemap-Probleme Opportunity-Dokumentation
description: Erfahren Sie mehr über die Probleme mit der Sitemap und wie Sie damit die Traffic-Akquise verbessern können.
badgeTrafficAcquisition: label="Traffic-Akquise" type="Caution" url="../../opportunity-types/traffic-acquisition.md" tooltip="Traffic-Akquise"
source-git-commit: d812a49e4b49d329717586b9f3c7a235aff3e69a
workflow-type: tm+mt
source-wordcount: '486'
ht-degree: 1%

---


# Sitemap-Probleme - Opportunity

![Sitemap-Probleme Opportunity](./assets/sitemap-issues/hero.png){align="center"}

Eine vollständige und genaue Sitemap hilft Suchmaschinen, Website-Seiten effizient zu durchsuchen und zu indizieren und so eine bessere Sichtbarkeit der Suchergebnisse sicherzustellen. Die Sitemap-Opportunity identifiziert potenzielle Probleme mit Ihrer Sitemap. Durch Beheben dieser Probleme können die Suchmaschinenindizierung und die Auffindbarkeit von Inhalten auf Ihrer Site erheblich verbessert werden.

Oben auf der Seite wird eine Zusammenfassung angezeigt, die eine Zusammenfassung des Problems und dessen Auswirkungen auf Ihre Site und Ihr Unternehmen enthält.

* **Projizierter Traffic-Verlust** - Der geschätzte Traffic-Verlust aufgrund von Sitemap-Problemen.
* **Projizierter Traffic-Wert** - Der geschätzte Wert des verlorenen Traffics.

## Automatisch identifizieren

Sitemap-Probleme können anhand der folgenden Kriterien gefiltert werden:

* **Sitemap mit Problemen** - Die analysierte Sitemap-URL mit potenziellen Problemen.
* **Problemtyp** - Der in der Sitemap identifizierte Problemtyp:
   * **Client-Fehler** - Einträge, die keine `200 Success` Antwort zurückgeben.
   * **Umleitungen** - Fehlerhafte oder falsch konfigurierte Umleitungen.

>[!BEGINTABS]

>[!TAB Client-Fehler]

![Sitemap-Client-Fehler automatisch identifizieren](./assets/sitemap-issues/auto-identify-client-errors.png){align="center"}

Wenn URLs in Ihrer Sitemap diese zurückgeben, können Suchmaschinen davon ausgehen, dass Ihre Sitemap veraltet ist oder dass Seiten versehentlich entfernt wurden. Client gibt an, dass die Anfrage des Clients (Browser oder Crawler) ungültig war. Häufige Optionen sind:

* **404 Nicht gefunden** - Die angeforderte Seite existiert nicht.
* **403 Verboten** - Der Server verweigert den Zugriff auf die angeforderte Seite.
* **410 Gone** - Die Seite wurde absichtlich entfernt und wird nicht mehr zurückgegeben.
* **401 Nicht autorisiert** - Authentifizierung ist erforderlich, wird aber nicht bereitgestellt.

Diese Fehler können SEO schaden, insbesondere wenn wichtige Seiten **404 oder 410** zurückgeben, da Suchmaschinen sie deindizieren können.

Jedes Problem wird in einer Tabelle angezeigt, wobei die Spalte **Seite** den betroffenen Sitemap-Eintrag angibt:

* **Seite** - Die URL des Sitemap-Eintrags mit einem Problem.

>[!TAB Umleitungen]

![Sitemap-Client-Fehler automatisch identifizieren](./assets/sitemap-issues/auto-identify-redirects.png){align="center"}

Sitemaps sollten nur endgültige Ziel-URLs enthalten, nicht solche, die umleiten. Weiterleitungen sollen Benutzende und Crawler zum richtigen Ort führen, können aber Probleme verursachen, wenn sie falsch konfiguriert sind:

* **302 Gefunden (temporäre Umleitung)** - Kann SEO-Probleme verursachen, wenn versehentlich anstelle eines **301 verwendet**.
* **307 Temporary Redirect** - Ähnlich wie 302, behält jedoch die HTTP-Methode bei.
* **Redirect-Schleifen** - Wenn eine Seite zurück zu sich selbst umleitet oder eine Endlosschleife erstellt.
* **Beschädigte Weiterleitungen** - Wenn eine Weiterleitung zu einer nicht vorhandenen oder 4xx-Seite führt.

Jedes Problem wird in einer Tabelle angezeigt, wobei die Spalte **Seite** den betroffenen Sitemap-Eintrag angibt:

* **Seite** - Die URL des Sitemap-Eintrags mit einem Problem.

>[!ENDTABS]

## Automatisch vorschlagen

Jedes Sitemap[Problem, das die Filterkriterien erfüllt](#auto-identify) wird in einer Tabelle mit den folgenden Spalten aufgeführt:

* **Seite** - Die URL des Sitemap-Eintrags mit einem Problem.
* **Vorschlag** - Die empfohlene Lösung für das Problem.

Vorschläge enthalten normalerweise einen aktualisierten Site-Pfad, um den Sitemap-Eintrag zu korrigieren. In einigen Fällen können sie auch detailliertere Anweisungen bereitstellen, z. B. die Angabe des richtigen Umleitungsziels.

## [!BADGE Ultimate automatisch optimieren]{type=Positive tooltip="Ultimate"}


![Sitemap-Probleme automatisch optimieren](./assets/sitemap-issues/auto-optimize.png){align="center"}

Sites Optimizer Ultimate bietet nun die Möglichkeit, automatische Optimierungen von Sitemaps bereitzustellen.

>[!BEGINTABS]

>[!TAB Optimierung bereitstellen]

{{auto-optimize-deploy-optimization-slack}}

>[!TAB Bestätigung anfordern]

{{auto-optimize-request-approval}}

>[!ENDTABS]
