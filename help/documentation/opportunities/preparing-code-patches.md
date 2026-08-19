---
title: Dokumentation zu Code-Patches wird vorbereitet
description: Erfahren Sie, wie AEM Sites Optimizer Code-Patches für Core Web Vitals-Fehlerbehebungen vorbereitet und wie Sie diese nachverfolgen können.
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
topic_v2:
  - id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
source-git-commit: a86d83ee226055e6401b13fd421b40d449b96fa8
workflow-type: tm+mt
source-wordcount: 248
ht-degree: 2%

---

# Dokumentation zu Code-Patches wird vorbereitet

<!--![Preparing code patches](./assets/preparing-code-patches/hero.png){align="center"}-->

Für die Opportunity [Core Web Vitals](/help/documentation/opportunities/core-web-vitals.md) generiert AEM Sites Optimizer Fehlerbehebungen auf Code-Ebene für identifizierte Leistungsprobleme. Sie können diese Fehlerbehebungen als Code-Patches überprüfen und vorbereiten, anstatt sie direkt bereitzustellen.

## Vorbereiten von Code-Patches

Wählen Sie ein oder mehrere Probleme aus der Core Web Vitals-Liste aus und klicken Sie dann auf **Code-Patch vorbereiten**, um Ihre Auswahl vorzubereiten, oder **Alle Code-Patches vorbereiten** um alle verfügbaren Patches gleichzeitig vorzubereiten. AEM Sites Optimizer erstellt für jede Fehlerbehebung ein gekennzeichnetes GitHub-Problem und öffnet automatisch eine verknüpfte Pull-Anfrage mit der Codeänderung, die von Ihrem Team überprüft, getestet und zusammengeführt werden kann.

Diese Aktion ist deaktiviert, wenn Sie nicht berechtigt sind, Code-Patches vorzubereiten, oder wenn die Site nicht vollständig dafür konfiguriert ist - z. B. wenn kein Code-Repository verbunden ist oder die Patch-Erstellung noch läuft. In jedem Fall erklärt Sites Optimizer, warum neben der Schaltfläche „Deaktiviert“ angezeigt wird.

## Tracking vorbereiteter Code-Patches

Nachdem Sie Code-Patches vorbereitet haben, können Sie diese verwalten und die nächsten Schritte auf der Registerkarte **bereitgestellt** auf der Detailseite von Core Web Vitals zusammen mit den Registerkarten **Aktuell** und **Ignoriert** ausführen. Der Status eines Patches spiegelt wider, ob seine Pull-Anfrage zusammengeführt und nicht nur generiert wurde. Ein Problem wird erst dann in &quot;**&quot;**, wenn die Fehlerbehebung tatsächlich in Ihrer Code-Basis zusammengeführt wurde.

## Siehe auch

* [Möglichkeit „Core Web Vitals“](/help/documentation/opportunities/core-web-vitals.md#auto-optimize)
* [Bereitstellen für die Autorendokumentation](/help/documentation/opportunities/deploying-to-author.md)
