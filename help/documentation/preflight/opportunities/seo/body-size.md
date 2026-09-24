---
title: Überprüfung der Körpergröße vor dem Flug
description: Erfahren Sie mehr über das Körpergrößenaudit in Preflight für AEM Sites Optimizer.
source-git-commit: c85cfb84b315b64ab5fcddfaa192ce78dd8d1a67
workflow-type: tm+mt
source-wordcount: '692'
ht-degree: 0%
---
# Körpergrößenprüfung

Der Audit **Textgröße** überprüft die Menge des Textkörpers auf Ihrer Seite. Seiten mit sehr wenig Inhalt können für Leser weniger nützlich sein und in den Suchergebnissen schlecht abschneiden. Die Prüfung kennzeichnet Seiten, die zu wenig Text zu enthalten scheinen.

## Warum das wichtig ist

Suchmaschinen und KI-Assistenten verwenden den Text einer Seite, um zu verstehen, worum es geht. Eine Seite mit wenig oder keinem Text wird oft als minderwertig behandelt, was sich negativ auf ihre Rangfolge auswirken kann und darauf, ob sie in KI-Antworten angezeigt wird.

## Was bei der Prüfung überprüft wird

Der Audit misst die Menge des auf der Seite verfassten Textes und meldet zwei Situationen:

* **Kein Textinhalt:** Die Seite wurde erfolgreich gelesen, enthält jedoch überhaupt keinen Textkörper, z. B. eine Seite, die nur ein Bild ist.
* **Dünner Inhalt:** Die Seite enthält Text, der jedoch unter dem empfohlenen Minimum liegt.

Eine Seite mit ausreichend Text wird übergeben und nicht gekennzeichnet.

## Wie Ihr Inhalt gemessen wird

Bei der Prüfung wird der Text im Hauptinhaltsbereich Ihrer Seite gemessen, nicht die gesamte Seite. Freigegebene Elemente wie Navigation, Kopfzeilen, Fußzeilen und Breadcrumbs werden auf jeder Seite wiederholt. Bei der Prüfung werden sie dort ausgeschlossen, wo sie erkannt werden können, sodass dieses freigegebene Chrome keinen wirklich dünnen Inhalt maskiert. Wie vollständig es Ihren Inhalt von diesem Chrome trennen kann, hängt vom Markup Ihrer Seite ab, wie unten beschrieben.

Um Ihre Inhalte zu finden, verwendet der Audit das erste dieser Kriterien:

1. **`<main>`(oder `role="main"`).** Dies wird als endgültiger Inhaltsbereich behandelt, und nur der Text darin wird gemessen (wenn eine Seite mehr als ein solches Element enthält, wird ihr Text kombiniert). Dies ist die zuverlässigste Option.
1. **Der Seitentext, aus dem Chrome entfernt wurde.** Wenn es keine `<main>` und keine `role="main"` gibt, misst die Prüfung die `<body>` nach dem Entfernen des erkannten Seitenchroms: Navigation und die Kopf- und Fußzeile auf Seitenebene, unabhängig davon, ob sie mit standardmäßigen HTML-Tags, ARIA-Orientierungsrollen oder den standardmäßigen AEM-Kopf-, Fußzeilen-, Breadcrumb- und Navigationskomponenten markiert ist. Eine Kopf- oder Fußzeile, die zu einem Inhaltsabschnitt gehört, z. B. der eigene Titel oder die Autorenzeile eines Artikels, wird beibehalten.
1. **Der gesamte Seitentext.** Wenn es keinen Orientierungspunkt für den Inhalt und kein erkanntes Chrome gibt, wird die gesamte `<body>` gemessen.

Ein paar Hinweise, was zählt. Bilder liefern keinen Text (ihr `alt` Text wird nicht gemessen), sodass eine Seite, die überwiegend aus Bildern besteht, weiterhin markiert werden kann. Text in `<script>`- und `<style>`-Tags wird nie gezählt, sodass die Messung durch Analytics- oder Datenschichtskripte nicht überhöht wird. Gewöhnlicher Link-Text wird jedoch wie jeder andere Text in Ihrem Inhalt gezählt.

## Wenn eine gekennzeichnete Seite für Sie korrekt aussieht

Wenn eine Seite als „dünn“ gekennzeichnet wird, Sie sich jedoch sicher sind, dass sie genügend Inhalt hat, hat das Audit Ihren Inhalt möglicherweise nicht klar vom umgebenden Chrome getrennt, z. B. von Navigation, Kopf- und Fußzeilen.

Wenn Sie möchten, dass die Prüfung Ihre Seite genauer misst, helfen Ihnen die folgenden Markup-Optionen:

* Die zuverlässigste Option besteht darin, Ihre erstellten Inhalte in ein `<main>`-Element einzuschließen (oder `role="main"` hinzuzufügen). Dadurch werden alle Unklarheiten beseitigt, sodass nur Ihre Inhalte gemessen werden.
* Wenn Sie kein `<main>` hinzufügen können, helfen Ihnen das standardmäßige Kopf- und Fußzeilen-Markup (`<header>`, `<footer>`) oder die standardmäßigen Experience Fragment-Varianten für Kopfzeilen und Fußzeilen von AEM dabei, Ihr Seiten-Chrome zu erkennen und auszuschließen.
* Wenn Sie Kopf- und Fußzeilen auf Abschnittsebene innerhalb von `<article>`, `<section>` oder `<aside>` markieren, wird verhindert, dass Inhalte, die sich in diesen Kopf- und Fußzeilen befinden, entfernt werden.

## Bekannte Einschränkungen

Die Prüfung beruht auf dem Markup Ihrer Seite, um Inhalte von Chrome zu unterscheiden. Auf einer Seite, die **keine `<main>`, kein standardmäßiges Orientierungs-Markup und anders als die Plattformkonventionen benannte Kopf-/Fußzeilenkomponenten aufweist** kann Chrome-Text in die Messung einbezogen oder der erstellte Text kann gelegentlich ausgeschlossen werden. Das Hinzufügen eines `<main>` Elements um Ihren Inhalt herum löst jeden solchen Fall. Der Audit versucht nicht, den Inhaltsbereich anhand der Textdichte oder des visuellen Layouts zu erraten. Er beruht auf Markup-Signalen, damit die Ergebnisse vorhersehbar und wiederholbar sind.

## Beheben von Problemen

Wenn der Audit Chancen findet, beschreibt jede das Problem und die empfohlene Änderung. Informationen zum Überprüfen und Beheben von Opportunities finden Sie unter [Audit results in Preflight](../../audit-results.md).
