---
title: Prüfung interner Links vor einem Flug
description: Erfahren Sie mehr über den Audit „Interne Links“ in Preflight für AEM Sites Optimizer.
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
source-git-commit: 9fd898e905bf843b4d39891c5875497a01569791
workflow-type: tm+mt
source-wordcount: '638'
ht-degree: 0%
---
# Prüfung interner Links

Der Audit **Interne Links** überprüft die Links auf Ihrer Seite, die auf Ihre eigene Site verweisen. Die Prüfung prüft jeden internen Link auf der Seite, die Sie bearbeiten, und kennzeichnet die fehlerhaften, unsicheren oder spitzen Links, denen ein Besucher nicht folgen kann.

## Warum das wichtig ist

Ein defekter interner Link ist eine Sackgasse für den Leser und ein vergeudeter crawlen für eine Suchmaschine, der keinen Wert auf die Seite weitergibt, die er erreichen sollte. Interne Links sind auch die einfachste Art, durch Zufall zu brechen: eine Seite wird verschoben oder umbenannt, und jeder Link zu ihr hört leise auf zu funktionieren. Da sich alle Links auf Ihrer eigenen Site befinden, können Sie sie auch selbst reparieren.

## Was bei der Prüfung überprüft wird

Die Prüfung zeigt für jeden internen Link, der eines der folgenden Probleme aufweist, eine Opportunity auf:

* **Beschädigter Link:** Der Link gibt einen Fehler zurück, z. B. `Status 404` oder `Status 500`. Ein Link, der nach einer Umleitung zum Fehler führt, wird auf die gleiche Weise gemeldet.
* **Nicht sicherer Link:** Der Link verwendet `http://` anstelle von `https://`. Wenn die sichere Version derselben URL funktioniert, bietet Preflight diese als Vorschlag an.
* **Editor-URL:** der Link verweist auf eine AEM-Editor-URL anstelle auf die Inhaltsseite. Der Link funktioniert für Sie, während Sie Inhalte erstellen, was leicht zu übersehen ist, aber jeder Besucher landet auf der Authoring-Oberfläche. Preflight schlägt die Inhalts-URL vor.
* **Fehlendes Fragment** Der Link verweist auf einen Anker, z. B. `#pricing`, den die Zielseite nicht hat. Die Seite wird weiterhin geöffnet, aber der Leser gelangt an den Anfang der Seite anstatt an den Abschnitt, den Sie gemeint haben. Daher ist die Wirkung geringer als bei einem fehlerhaften Link. Wenn auf der Seite derselbe Anker unterschiedlich großgeschrieben ist, schlägt Preflight den korrigierten Anker vor. Wenn die Zielseite selbst beschädigt ist, wird sie stattdessen als &quot;**Link“**.
* **Nicht verifizierter Link:** der Überprüfung ist ein Zeitlimit überschritten oder ein Netzwerkfehler aufgetreten. Preflight kann nicht erkennen, ob der Link funktioniert, daher werden Sie aufgefordert, den Link selbst zu überprüfen, anstatt ihn als beschädigt zu melden.

Ein Link, der erfolgreich aufgelöst wird, wird nicht markiert, selbst wenn mehrere Umleitungen unterwegs sind. Es ist auch kein Link, der zu einer anderen Site umleitet, da es sich nicht mehr um einen internen Link handelt.

## Wie die Links überprüft werden

Der Audit überprüft Links aus Ihrer Autorensitzung, sodass sie so angezeigt werden, wie Sie angemeldet sind, um sie zu sehen. Eine Seite, die nur auf der Autoreninstanz vorhanden ist, wird korrekt aufgelöst, anstatt beschädigt auszusehen.

Links, die der Link-Checker von AEM bereits als ungültig markiert hat, werden in die Prüfung einbezogen, auch wenn der Editor den anklickbaren Link von der Seite entfernt. Sie werden dann erneut überprüft, anstatt sie als vertrauenswürdig anzusehen, sodass ein Link, der seitdem funktioniert hat, nicht gemeldet wird.

Für jeden Ort, an dem ein Link angezeigt wird, wird eine Opportunity gemeldet. Ein fehlerhafter Link, der an drei Stellen verwendet wird, liefert also drei zu behebende Instanzen, von denen jede ihren eigenen Platz auf der Seite hervorhebt. Wenn einer dieser Orte mehr als ein Problem hat, zeigt Preflight sie zusammen auf einer Karte an.

## Bekannte Einschränkungen

Der Audit wird im AEM Sites-Seiteneditor, in Adobe Managed Services (AMS) und bei der dokumentbasierten Bearbeitung über Sidekick ausgeführt. Sie ist derzeit nicht im universellen Editor verfügbar.

## Beheben von Problemen

Wenn der Audit Chancen findet, beschreibt jede das Problem und die empfohlene Änderung und identifiziert den betreffenden Link. Verwenden Sie **Hervorheben auf Seite**, um zum Link in Ihrem Inhalt zu springen, und verwenden Sie den Abschnitt **Aktuelle URL**, um die URL zu kopieren oder in einer neuen Registerkarte zu öffnen, damit Sie das Problem selbst bestätigen können. Informationen zum Überprüfen und Beheben von Opportunities finden Sie unter [Audit results in Preflight](../../audit-results.md).
