---
title: PreFlight-MetaTags-Audit
description: Erfahren Sie mehr über den MetaTags-Audit in Preflight für AEM Sites Optimizer.
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
source-git-commit: 59c097682899889aa2a5d76333f80cc58e28ff1e
workflow-type: tm+mt
source-wordcount: '801'
ht-degree: 1%
---
# MetaTags-Audit

Der **MetaTags**-Audit überprüft den Seitentitel, die Metabeschreibung und die Hauptüberschrift (H1). Sie kennzeichnet fehlende, leere oder außerhalb der empfohlenen Länge befindliche Seiten und kennzeichnet Seiten mit mehr als einer H1-Überschrift.

## Warum das wichtig ist

Der Seitentitel und die Metabeschreibung sind normalerweise das, was Personen für Ihre Seite in den Suchergebnissen sehen: der Titel als klickbare Überschrift und die Beschreibung als Zusammenfassung darunter. Ein fehlender oder schlecht skalierter Titel oder eine Beschreibung kann abgeschnitten oder durch Text ersetzt werden, den die Suchmaschine von Ihrer Seite auswählt. Die Überschrift H1 sagt Lesern und Suchmaschinen, worum es auf der Seite hauptsächlich geht, sodass eine Seite eine klare H1 haben sollte.

## Was bei der Prüfung überprüft wird

Die Prüfung bietet eine Gelegenheit für jedes der folgenden Probleme:

* **Seitentitel:** fehlt, ist leer, zu kurz oder überschreitet die ideale Länge.
* **Meta-Beschreibung:** fehlt, ist leer, zu kurz oder überschreitet die Ideallänge.
* **H1 Überschrift**: fehlt, ist leer, ist länger als die ideale Länge oder umfasst mehr als ein H1 auf der Seite.

Ein Wert, der einige Zeichen über der idealen Länge liegt, wird als **über der idealen Länge** und einer über dem Maximum des Audits als **zu lang“**. Preflight hat keinen zu langen Schwellenwert für Seitentitel.

| Tag | Ideallänge | Über der idealen Länge | Zu lang |
|---|---|---|---|
| Seitentitel | 40 bis 60 Zeichen | Mehr als 60 Zeichen | - |
| Meta-Beschreibung | 140 bis 160 Zeichen | 161 bis 175 Zeichen | Mehr als 175 Zeichen |
| Überschrift H1 | Bis zu 70 Zeichen | 71 bis 75 Zeichen | Mehr als 75 Zeichen |

Diese Bereiche sind empfohlene Richtlinien und keine Suchmaschinenanforderungen. Preflight verwendet sie, um zu entscheiden, wann eine Opportunity gemeldet wird.

## Lesen der Werte

Bei der Prüfung wird die Seite gelesen, die Sie bearbeiten: der Text des `<title>`, der Inhalt des `<meta name="description">`-Tags und der sichtbare Text des ersten `<h1>`, einschließlich fett oder kursiv gedruckter Texte.

Ein Tag **fehlt** wenn die Seite es nicht hat, und **leer** wenn es dort ist, aber keinen sichtbaren Text hat. Längen zählen jedes Zeichen, einschließlich Leerzeichen und Satzzeichen. Nur die erste H1 wird auf ihre Länge geprüft. Wenn eine Seite mehr als eine H1 hat, wird jede als separate Instanz aufgelistet, sodass Sie die zusätzlichen Überschriften finden und ändern können.

## Vorschläge

Jede Opportunity enthält eine Empfehlung, z. B. die ideale Länge für das Tag oder eine H1 auf einer Seite.

Seitentitel, Meta-Beschreibung und H1-Opportunities können auch einen KI-generierten Vorschlag enthalten, der aus dem Inhalt Ihrer Seite geschrieben wird. Ein Vorschlag wird nur angezeigt, wenn er der idealen Länge entspricht. Überprüfen und bearbeiten Sie jeden Vorschlag, bevor Sie ihn verwenden.

Wenn eine H1-Opportunity keinen KI-Vorschlag hat, ist ihr Vorschlag stattdessen eine feste Empfehlung, z. B. eine Verkürzung der Überschrift oder eine Änderung der zusätzlichen H1-Überschrift in H2. Wenn ein Seitentitel oder eine Meta-Beschreibungsmöglichkeit keinen KI-Vorschlag enthält, zeigt Preflight an, dass keine Vorschläge verfügbar sind.

## Wenn ein gekennzeichneter Wert für Sie korrekt aussieht

Auf Edge Delivery Services-Seiten wird ein Seitentitel oder eine Metabeschreibung, die Sie nicht festgelegt haben, automatisch aus der ersten Überschrift und dem ersten Absatz der Seite eingefügt. Diese sind häufig kürzer als die ideale Länge, sodass die Seite gekennzeichnet ist. Durch Festlegen eines eigenen Titels und einer eigenen Beschreibung in den Seitenmetadaten wird dies behoben.

## Bekannte Einschränkungen

* **Andere Head-Tags werden nicht aktiviert,**. B. Open Graph-Tags für die Freigabe in sozialen Netzwerken oder das Robots-Tag.
* **Länge wird in Zeichen gezählt:** Suchmaschinen kürzen Titel und Beschreibungen auf der Grundlage, wie viel Platz sie auf dem Bildschirm einnehmen, sodass ein Wert innerhalb der idealen Länge in den Suchergebnissen dennoch gekürzt werden kann.
* **Sprachen ohne Leerzeichen zwischen Wörtern:** auf Seiten in Sprachen wie Chinesisch, Japanisch oder Koreanisch kann ein Wert, der gut liest, weiterhin gekennzeichnet werden, und KI-Vorschläge können außerhalb der idealen Länge liegen.

## Beheben von Problemen

Jede Opportunity beschreibt das Problem und die empfohlene Änderung und zeigt den aktuellen Wert des Seitentitels oder der Meta-Beschreibung an.

* **Seitentitel und Meta-Beschreibung:** Aktualisieren Sie sie dort, wo Ihre Site sie festlegt, z. B. in den Seiteneigenschaften in AEM Sites oder in den Seitenmetadaten in Edge Delivery Services. Diese Tags befinden sich im Kopf der Seite, daher **Hervorheben auf Seite** für sie nicht verfügbar.
* **H1 Überschrift:** Verwenden Sie **Markieren auf Seite** um die Überschrift in Ihrem Inhalt zu finden. In Edge Delivery Services, dem AEM Sites-Seiteneditor und Adobe Managed Services (AMS) scrollt Preflight zur Überschrift und zeigt sie an. Der Seiteneditor und AMS erfordern **Bearbeitungsmodus**. Im universellen Editor wählt Preflight die Überschrift oder den nächsten bearbeitbaren Block aus, der sie enthält. Eine Überschrift in der Navigation oder eine Fußzeile wird angezeigt, kann jedoch nicht ausgewählt werden. Weitere Informationen finden Sie unter [Auf Seite hervorheben](../../audit-results.md#highlight-on-page).

Informationen zum Überprüfen und Beheben von Opportunities finden Sie unter [Audit results in Preflight](../../audit-results.md).
