---
title: Bereitstellen für die Autorendokumentation
description: Erfahren Sie, wie AEM Sites Optimizer ausgewählte Optimierungen in der Authoring-Umgebung bereitstellt und wie Sie diese nachverfolgen können.
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
topic_v2:
  - id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
source-git-commit: 1d55c607aab6c820d014b9a57bfae20b8170c672
workflow-type: tm+mt
source-wordcount: 245
ht-degree: 6%

---

# Bereitstellen für die Autorendokumentation

<!--![Deploying to author](./assets/deploying-to-author/hero.png){align="center"}-->

Nachdem AEM Sites Optimizer eine Opportunity identifiziert und Optimierungen vorgeschlagen hat, können Sie die ausgewählten Optimierungen überprüfen und für weitere Aktionen bereitstellen.

## In Autorenumgebung bereitstellen

Wählen Sie einen oder mehrere Vorschläge aus der Liste einer Opportunity aus und klicken Sie dann auf **Für Autor bereitstellen**, um Ihre Auswahl bereitzustellen, oder auf **Alle für Autor bereitstellen**, um jeden verfügbaren Vorschlag auf einmal bereitzustellen. AEM Sites Optimizer wendet die ausgewählten Optimierungen nur auf die Authoring-Umgebung an und veröffentlicht keine Änderungen an Ihrer Live-Site. Der AEM-Autor kann dann die Änderungen aus dem Content Management System (CMS) überprüfen und veröffentlichen, in Übereinstimmung mit dem eigenen Workflow [Automatische Optimierung](/help/documentation/opportunities/missing-alt-text.md#auto-optimize) der einzelnen Opportunities.

Diese Aktion ist deaktiviert, wenn Sie keine Berechtigung zur Bereitstellung haben oder wenn die Site nicht vollständig für die Bereitstellung konfiguriert ist (z. B. wenn noch kein Code-Repository verbunden wurde). In beiden Fällen erklärt Sites Optimizer, warum neben der Schaltfläche „Deaktiviert“ angezeigt wird.

## Nachverfolgen bereitgestellter Optimierungen

<!--![Deployed tab](./assets/deploying-to-author/deployed-tab.png){align="center"}-->

Nachdem Sie ausgewählte Optimierungen bereitgestellt haben, können Sie sie verwalten und die nächsten Schritte auf der Registerkarte **bereitgestellt** auf der Detailseite der Opportunity neben den Registerkarten **Aktuell** und **Ignoriert** ausführen.

Die spezifischen Bereitstellungsmechanismen - einschließlich der Art und Weise, wie Aktualisierungen für Edge Delivery Services, AEM as a Cloud Service oder Digital Asset Management angewendet werden - variieren je nach Opportunity-Typ. Weitere Informationen finden Sie im Abschnitt **Opportunity** Automatische Optimierung).

## Siehe auch

* [Möglichkeit „Fehlender Alternativtext“](/help/documentation/opportunities/missing-alt-text.md#auto-optimize)
* [Möglichkeit „Core Web Vitals“](/help/documentation/opportunities/core-web-vitals.md#auto-optimize)
* [Möglichkeit „Fehlerhafte Backlinks“](/help/documentation/opportunities/broken-backlinks.md#auto-optimize)
