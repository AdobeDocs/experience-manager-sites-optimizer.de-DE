---
title: Dokumentation zur Möglichkeit „Fehlerhafte Backlinks“
description: Erfahren Sie mehr über die Möglichkeit „Fehlerhafte Backlinks“ und darüber, wie Sie sie zur Verbesserung der Traffic-Akquise nutzen können.
badgeTrafficAcquisition: label="Traffic-Akquise" type="Caution" url="../../opportunity-types/traffic-acquisition.md" tooltip="Traffic-Akquise"
source-git-commit: 97e61d3061fb68225eece98ba0f94affb08be9e3
workflow-type: tm+mt
source-wordcount: '655'
ht-degree: 30%

---


# Möglichkeit „Fehlerhafte Backlinks“

<!--![Broken backlinks opportunity](./assets/broken-backlinks/hero.png){align="center"}-->

>[!VIDEO](https://video.tv.adobe.com/v/3483250/?learn=on&enablevpops)

Die defekte Backlinks-Opportunity identifiziert externe Links, die auf nicht vorhandene (404) Seiten Ihrer Site verweisen. Diese Links führen zu Referral Traffic-Verlusten und geringerem SEO-Wert, da Suchmaschinen auf Backlinks angewiesen sind, um Relevanz und Autorität zu bewerten. Diese Probleme treten auf, wenn URLs geändert, Inhalte entfernt oder Seiten ohne ordnungsgemäße Weiterleitungen nicht mehr verfügbar sind. AEM Sites Optimizer identifiziert alle fehlerhaften Backlinks, bietet spezifische KI-Empfehlungen und ermöglicht eine Bereitstellung mit einem Klick, um sie zu beheben, und das alles in einer zentralen Ansicht.

## Automatische Identifizierung

<!--![Auto-identify broken backlinks](./assets/broken-backlinks/auto-identify.png){align="center"}-->

AEM Sites Optimizer durchsucht kontinuierlich externe Datenquellen, um Backlinks zu erkennen, die auf nicht vorhandene 404-Seiten auf Ihrer Site verweisen. Die Daten werden aus verschiedenen Quellen aggregiert, einschließlich Google Search Console[ „Operational Telemetry](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/sites/operational-telemetry-for-aem-as-a-cloud-service) und SEO-Plattformen von Drittanbietern. Die Opportunity zur automatischen Identifizierung identifiziert externe Domains, die mit fehlerhaften URLs verknüpft sind, und priorisiert sie basierend auf den Auswirkungen, einschließlich Domain-Autorität und erwartetem Traffic sowie Verlusten bei der Link-Gerechtigkeit.

Bei dieser Opportunity werden alle identifizierten Probleme aufgelistet, einschließlich der folgenden Details:

* **Verweisende Domain und**: Die externe Seite oder Domain, die den fehlerhaften Link enthält.
* **Priorität** - Hoch, Mittel oder Niedrig, was die Auswirkungen des fehlerhaften Links auf den SEO-Prozess angibt.
* **Beschädigte Ziel-URL** - Die nicht vorhandene URL auf Ihrer Site, mit der verknüpft wird.

## Automatische Vorschläge

<!--![Auto-suggest broken backlinks](./assets/broken-backlinks/auto-suggest.png){align="center"}-->

Für jeden identifizierten fehlerhaften Backlink empfiehlt AEM Sites Optimizer das am besten geeignete Ziel, um den Traffic und den SEO-Wert wiederherzustellen. Sie ermittelt die Absicht des Backlinks durch Analyse von:

* URL-Struktur und Token
* Ankertext
* Titel und Kontext der verweisenden Seite

Dieser Intent wird mit vorhandenem Site-Inhalt abgeglichen, um die relevanteste Zielseite zu identifizieren. Jede fehlerhafte URL wird entweder einer exakten oder der nächstgelegenen relevanten Ersatzseite zugeordnet. Wenn kein geeignetes Ziel ermittelt werden kann, wird das Problem zur manuellen Überprüfung angezeigt.

>[!BEGINTABS]

>[!TAB KI-Begründung]

<!--![AI rationale on autosuggestion of broken backlinks](./assets/broken-backlinks/auto-suggest-ai-rationale.png){align="center"}-->

Wählen Sie das Symbol **Informationen** aus, um die KI-Begründung für die vorgeschlagene URL anzuzeigen. Die Begründung erklärt, warum die KI der Ansicht ist, dass die vorgeschlagene URL am besten für den fehlerhaften Link geeignet ist. Dies kann Ihnen dabei helfen, den Entscheidungsfindungsprozess der KI nachzuvollziehen und eine fundierte Entscheidung darüber zu treffen, ob Sie den Vorschlag akzeptieren oder ablehnen sollen.

>[!TAB Ziel-URL bearbeiten]

<!--![Edit suggested URL of broken backlinks](./assets/broken-backlinks/edit-target-url.png){align="center"}-->

Wenn Sie mit dem KI-generierten Vorschlag nicht einverstanden sind, können Sie die vorgeschlagene URL bearbeiten, indem Sie das **Symbol „Bearbeiten“** auswählen. Beim Bearbeiten können Sie manuell die URL eingeben, die Ihrer Meinung nach für den fehlerhaften Link am besten geeignet ist. Sites Optimizer führt auch alle anderen URLs auf Ihrer Site auf, die für den fehlerhaften Link geeignet sein könnten.

>[!TAB Einträge ignorieren]

<!--![Ignore broken backlinks](./assets/broken-backlinks/ignore.png){align="center"}-->

Sie können Einträge mit den anvisierten fehlerhaften URLs ignorieren. Durch Auswählen von ![Symbol „Löschen“ oder „Ignorieren“](https://spectrum.adobe.com/static/icons/ui_18/CrossSize500.svg) wird der fehlerhafte Backlink aus der Liste der Möglichkeiten entfernt. Ignorierte fehlerhafte Backlinks können über die Registerkarte **Ignoriert** oben auf der Seite der Möglichkeiten erneut aktiviert werden.

>[!ENDTABS]

## Automatische Optimierung

<!--[!BADGE Ultimate]{type=Positive tooltip="Ultimate"}-->

Sobald die Vorschläge geprüft und genehmigt wurden, können Sie auf **Optimierung bereitstellen** klicken. AEM Sites Optimizer wendet die Korrekturen dann in der Autorenumgebung an, je nachdem, wie Weiterleitungen innerhalb Ihrer Implementierung verwaltet werden. Der AEM-Autor kann dann die Änderungen über das Content Management System (CMS) veröffentlichen.

Abhängig von der Konfiguration werden Fehlerbehebungen entweder als Inhalts- oder als Code-Änderungen innerhalb der vorhandenen Bereitstellungs-Workflows angewendet. Der Optimierungsprozess umfasst die folgenden Schritte:

* **Validierung** - Stellt sicher, dass die Änderungen erwartungsgemäß funktionieren und führt vor der Bereitstellung keine Regressionen ein.
* **Bereitstellung**: Wendet Änderungen über bestehende Prozesse an, z. B. Inhaltsaktualisierungen in AEM oder Code-Bereitstellung über CI/CD-Pipelines.
* **Berechtigungsprüfung** - Prüft, ob der Benutzer über die erforderlichen Berechtigungen zum Bereitstellen von Änderungen verfügt. Andernfalls werden alternative Ausgaben wie herunterladbare Umleitungslisten oder Code-Patches bereitgestellt.

Dieser Prozess stellt sicher, dass Weiterleitungen genau implementiert, vor der Veröffentlichung validiert und mit bestehenden Konfigurationen und Governance-Prozessen abgestimmt werden.
