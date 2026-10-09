---
title: Preflight-Kopfzeilenprüfung
description: Erfahren Sie mehr über den Überschriften-Audit in Preflight für AEM Sites Optimizer.
source-git-commit: af80dbb47a25b10cdbe55965fb7c4ce496448871
workflow-type: tm+mt
source-wordcount: '655'
ht-degree: 0%
---
# Überschriften-Audit

Der **Überschriften**-Audit überprüft die Unterüberschriften auf Ihrer Seite (H2 bis H6). Kennzeichnet Überschriften ohne Text und Überschriften, die eine Ebene überspringen, z. B. ein H2 gefolgt von einem H4.

## Warum das wichtig ist

Überschriften geben einer Seite ihren Umriss. Leser scannen sie, um zu finden, was sie brauchen, Benutzer von Sprachausgaben gehen durch eine Seite anhand ihrer Überschriften, und Suchmaschinen verwenden sie, um zu verstehen, wie die Inhalte organisiert sind. Eine leere Überschrift fügt einen Stopp in dieser Gliederung hinzu, der nichts enthält, und eine übersprungene Ebene erschwert das Folgen der Struktur.

## Was bei der Prüfung überprüft wird

Die Prüfung bietet eine Gelegenheit für jedes der folgenden Probleme:

* **Leere Überschrift:** ein H2, H3, H4, H5 oder H6, das keinen Text hat. Eine Überschrift, die nur Leerzeichen oder nur ein Bild enthält, zählt als leer.
* **Überschriftenebene übersprungen:** eine Überschrift, die mehr als eine Ebene tiefer als die Überschrift unmittelbar davor ist, z. B. ein H2 gefolgt von einem H4 oder ein H1 gefolgt von einem H3. Die Opportunity wird in der tieferen Überschrift beschrieben.

Beide werden mit moderater Wirkung gemeldet.

H1-Überschriften werden vom Audit [Metatags](./metatags.md) geprüft, bei dem geprüft wird, ob ein H1 fehlt, leer ist oder zu lang ist und ob mehr als ein H1 auf einer Seite vorhanden ist.

## So werden Überschriften gelesen

Der Audit liest die Seite, die Sie bearbeiten, und betrachtet jede Überschrift in der Reihenfolge, in der sie angezeigt wird:

* Alle Überschriften zählen, einschließlich Überschriften in der Kopfzeile, Navigation und Fußzeile der Seite sowie Überschriften, die auf dem Bildschirm ausgeblendet sind.
* Es wird nur der Schritt von einer Überschrift zur nächsten markiert. Eine Seite, deren erste Überschrift ein H3 ist, wird dafür nicht gekennzeichnet.
* Überschriften können beliebig viele Ebenen zurückgehen, z. B. von einem H4 zurück zu einem H2.

## Vorschläge

Jede Gelegenheit beinhaltet eine Empfehlung und eine feste Empfehlung für die vorzunehmende Änderung. Der Überschriften-Audit generiert keine KI-Vorschläge.

## Wenn eine gekennzeichnete Überschrift für Sie korrekt aussieht

Wenn eine Opportunity nicht dem entspricht, was Sie erwarten, ist normalerweise einer der folgenden Gründe:

* **Die Überschrift ist Teil Ihrer Seitenvorlage.** Überschriften in der Kopfzeile, Navigation oder Fußzeile werden zusammen mit Ihrem Inhalt überprüft, sodass eine Fußzeilenüberschrift, die mehrere Ebenen tiefer als die letzte Überschrift in Ihrem Inhalt ist, als übersprungene Ebene markiert werden kann. Wenn Sie sie in der Vorlage fixieren, wird sie auf jeder Seite aufgelöst, die die Vorlage verwendet.
* **Die Überschrift enthält nur ein Bild oder Symbol.** Eine Überschrift ohne Text wird auch dann als leer gemeldet, wenn ein Bild angezeigt wird. Fügen Sie der Überschrift Text hinzu oder verwenden Sie ein Element ohne Überschrift für das Bild.

## Bekannte Einschränkungen

* **Sichtbarkeit wird nicht berücksichtigt:** Überschriften, die auf dem Bildschirm ausgeblendet sind, werden weiterhin aktiviert.
* **Sehr große Seiten:** Seiten mit mehr als 500 Überschriften werden nicht überprüft.

## Beheben von Problemen

Wenn der Audit Chancen findet, beschreibt jede das Problem und die empfohlene Änderung.

* **Leere Überschrift:** Sie der Überschrift beschreibenden Text hinzu oder entfernen Sie ihn, wenn er nicht benötigt wird.
* **Überschriftenebene übersprungen:** Ändern Sie die Überschrift von der Überschrift davor zur nächsten Ebene nach unten (z. B. ein H4, nachdem ein H2 zu einem H3 wurde) oder fügen Sie die fehlende Ebene dazwischen hinzu.

Verwenden Sie **Hervorheben auf Seite**, um die Überschrift in Ihrem Inhalt zu finden. Wie die Überschrift hervorgehoben wird, hängt davon ab, wo Sie Preflight ausführen:

* **Edge Delivery Services:** Preflight scrollt zur Überschrift und umreißt sie.
* **AEM Sites-Seiteneditor und Adobe Managed Services (AMS):** Preflight scrollt zur Überschrift und umreißt sie. Die Hervorhebung **den Bearbeitungsmodus**.
* **Universeller Editor:** Preflight wählt die Überschrift selbst oder den nächsten bearbeitbaren Block aus, der sie enthält. Für eine Überschrift im Inhalt, die der Editor nicht verwaltet, z. B. Navigation oder Fußzeile, wird sie in Preflight angezeigt, kann aber nicht die Überschrift selbst auswählen.

Weitere Informationen finden Sie unter [Auf Seite hervorheben](../../audit-results.md#highlight-on-page).

Informationen zum Überprüfen und Beheben von Opportunities finden Sie unter [Audit results in Preflight](../../audit-results.md).
