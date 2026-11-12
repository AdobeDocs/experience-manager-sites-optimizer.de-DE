---
title: Lorem-IPSUM-Audit vor dem Flug
description: Erfahren Sie mehr über den Lorem-ipsum-Audit in Preflight für AEM Sites Optimizer.
badgePreflightSEO: label="PreFlight - SEO" type="Caution" url="../seo.md" tooltip="PreFlight - SEO"
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
source-git-commit: 659419fa2eb570b4e1fedf87c35c5c60c46ffc8a
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 1%
---
# Preflight - Lorem-ipsum-Audit

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
* **Auf Seite hervorheben:** ist für den Seitentitel oder die Metadaten nicht verfügbar, da sie nicht auf der Seite angezeigt werden. Verwenden Sie **Details** und das Feld **Element**, um den Text zu finden.

## Beheben von Problemen

Überprüfen Sie **Details** auf die Position des Textes, z. B. Seitentitel, Alternativtext oder Überschrift. **Recommendation** erläutert, wie dies behoben werden kann, und das Feld **Element** zeigt den Text innerhalb des Tags an.

Verwenden Sie **Hervorheben auf Seite** sofern verfügbar. Ein ausgeblendetes Element kann an anderen Bildschirmgrößen oder in einem Menü oder Dialogfeld angezeigt werden.

Ersetzen oder entfernen Sie den Platzhaltertext. Beschreiben Sie das Bild oder das Steuerelement für Alt-Text und Barrierefreiheitsbeschriftungen. Weitere Anleitungen [ Sie unter ](../../audit-results.md) in Preflight prüfen.
