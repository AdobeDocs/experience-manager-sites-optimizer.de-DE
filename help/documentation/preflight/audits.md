---
title: Durchführen von Audits in Preflight
description: Erfahren Sie, wie Sie ein Preflight-Audit für Ihre Seite starten.
source-git-commit: 14f10c231373992c49a8bb93c043556305b6280d
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 17%

---


# Audits in Preflight

Preflight prüft Ihre Seite, um Möglichkeiten zur Verbesserung Ihrer Inhalte vor der Veröffentlichung zu ermitteln. Im Gegensatz zu einem automatischen Scan können Sie festlegen, wann die Audits ausgeführt werden sollen, sodass Sie eine Seite jederzeit analysieren können.

![Der Preflight-Landingscreen mit der Schaltfläche „Seite analysieren“](./assets/audits/hero.png){align="center"}

So führen Sie Preflight-Audits für eine Seite durch:

1. Öffnen Sie die Seite, für die Sie das Audit durchführen möchten, in der [Autorenumgebung](./access-preflight.md) (universeller Editor, dokumentenbasiertes Authoring oder AEM Sites-Seiteneditor).
1. Öffnen Sie das [Panel „Preflight“](./access-preflight.md). PreFlight öffnet den **Audit „Leistungsbereitschaft ausführen** Landingscreen.
1. Wählen Sie **Seite analysieren** aus. Preflight führt alle seine Audits auf der aktuellen Seite aus und öffnet das Bereitschafts-Dashboard, in dem nach Kategorie gruppiert ein Bereitschaftswert und die gefundenen Opportunitys angezeigt werden.

Informationen zu den Vorschauergebnissen und Optimierungsmöglichkeiten finden Sie unter [Audit results in Preflight](./audit-results.md).

## Verwenden der integrierten Preflight-Schaltfläche

Wenn in Ihrer Autorenumgebung [AEM 2026.7.0 (Version 27083)](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/release-notes/maintenance/2026/2026-7-0#release-27083) oder höher ausgeführt wird, ist Preflight in die Symbolleiste des AEM Sites-Seiteneditors integriert. Wählen Sie das **Preflight**-Symbol (die Wiedergabeschaltfläche) aus, um das Bedienfeld für die aktuelle Seite zu öffnen, und wählen Sie dann **Seite analysieren** aus, um die Audits durchzuführen.

>[!VIDEO](https://video.tv.adobe.com/v/3496629?learn=on&enablevpops)

## Fortsetzen einer vorherigen Sitzung

Preflight speichert Ihre letzte Ausführung, sodass Sie die Prüfungen nicht erneut ausführen müssen, wenn Sie gehen und zurückkommen.

* Wenn Sie das Preflight-Bedienfeld erneut auf **Browser-Registerkarte öffnen** lädt Preflight die Ergebnisse Ihres letzten Durchgangs automatisch, auch nach einer Aktualisierung.
* Wenn Sie auf **neuen Registerkarte oder nach dem Schließen des Browsers zurückkehren** wird auf dem Landingscreen neben der Seite **Analysieren** die Schaltfläche „Letzte **fortsetzen** angezeigt. Wählen Sie **Letzte Sitzung fortsetzen**, um Ihre letzten Ergebnisse neu zu laden, oder wählen Sie **Seite analysieren**, um einen neuen Durchgang zu starten.

Preflight verfolgt den letzten Durchlauf für jede Seite separat, sodass **Letzte Sitzung fortsetzen** immer den letzten Durchlauf für die Seite neu lädt, auf der Sie sich befinden.

Sobald die Audits abgeschlossen und die Ergebnisse angezeigt werden, wählen Sie **Neu analysieren** aus den **Mehr Aktionen** (**…**) in der Symbolleiste verwenden, um die Ergebnisse zu verwerfen und jedes Audit erneut auszuführen. Siehe [Audit-Ergebnisse in Preflight](./audit-results.md#toolbar).

