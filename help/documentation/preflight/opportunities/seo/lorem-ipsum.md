---
title: Lorem-IPSUM-Audit vor dem Flug
description: Erfahren Sie mehr über den Lorem-ipsum-Audit in Preflight für AEM Sites Optimizer.
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
source-git-commit: 587aec4eb905a2b1ced746590ca25b8ed97b16c1
workflow-type: tm+mt
source-wordcount: '357'
ht-degree: 1%
---
# Lorem-ipsum-Audit

Der **Lorem-Ipsum**-Audit erkennt Platzhaltertext, der in Ihrem Seiteninhalt hinterlassen wurde.

## Warum das wichtig ist

Wenn Sie eine Seite mit Platzhaltertext veröffentlichen, sieht sie für die Leser unfertig aus. Suchmaschinen können den Platzhaltertext indizieren und in Suchergebnissen anzeigen, und soziale Plattformen können ihn in Link-Vorschauen anzeigen. Platzhaltertext wird oft ausgeblendet, z. B. in Bild-Alt-Text oder Barrierefreiheitsbeschriftungen. Wenn dies der Fall ist, können Personen, die Bildschirmlesehilfen oder andere Hilfstechnologien verwenden, es weiterhin hören, auch wenn es nicht auf der Seite angezeigt wird.

## Was bei der Prüfung überprüft wird

Der Audit meldet jede Stelle auf der Seite, an der der Platzhaltertext angezeigt wird. Er prüft den sichtbaren Seitentext sowie mehrere Stellen, an denen er möglicherweise nicht sofort oder überhaupt sichtbar ist:

* Bild Alt-Text
* Barrierefreiheitsbeschriftungen und -beschreibungen
* Platzhalter für Formularfelder
* QuickInfos
* Der Seitentitel
* Metadaten wie die Metabeschreibung und Social-Sharing-Tags

Code, der Benutzern nicht angezeigt wird, z. B. Skripte und Stile, wird nicht aktiviert.

## Übereinstimmung des Textes

Die Prüfung sucht nach der Phrase „lorem ipsum“ in einer beliebigen Kombination aus Groß- und Kleinbuchstaben. Die Wortgruppe wird auch dann gefunden, wenn die Wörter auf Linien oder Elemente aufgeteilt sind oder keinen Abstand zwischen ihnen aufweisen. Wenn die Phrase mehrmals im selben Element oder Attribut vorkommt, wird diese Stelle einmal gemeldet.

## Bekannte Einschränkungen

* **Nur „lorem ipsum“:** anderer Platzhaltertext, wie „TBD“ oder andere lateinische Füllwörter ohne „lorem ipsum“, wird nicht erkannt.
* **Auf Seite hervorheben:** ist für den Seitentitel oder die Metadaten nicht verfügbar, da sie nicht auf der Seite angezeigt werden. Verwende den Text, der bei der Gelegenheit angezeigt wird, um sie zu finden.

## Beheben von Problemen

Wenn die Prüfung Chancen findet, identifiziert jede, wo der Platzhaltertext angezeigt wird. Sofern verfügbar, verwenden Sie **Hervorhebung auf Seite** um zum Text in Ihrem Inhalt zu springen. Ersetzen Sie den Platzhalter durch echten Inhalt oder entfernen Sie ihn. Schreiben Sie für Alt-Text und Barrierefreiheitsbeschriftungen eine Beschreibung des Bildes oder Steuerelements. Informationen zum Überprüfen und Beheben von Opportunities finden Sie unter [Audit results in Preflight](../../audit-results.md).
