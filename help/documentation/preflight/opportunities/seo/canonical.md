---
title: Canonical Audit Preflight
description: Erfahren Sie mehr über das Canonical Audit in Preflight für AEM Sites Optimizer.
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
source-git-commit: 5c97431c2029e117339877219c2d6e4e30902a70
workflow-type: tm+mt
source-wordcount: '574'
ht-degree: 0%
---
# Kanonische Prüfung

Der Audit **Canonical** überprüft den kanonischen Link auf Ihrer Seite. Der kanonische Link ist ein `<link rel="canonical">`-Tag im `<head>` der Seite, das die bevorzugte URL für den Seiteninhalt benennt. Audit kennzeichnet kanonische Links, die fehlen, falsch eingerichtet sind oder auf eine andere Stelle als die Seite selbst verweisen.

## Warum das wichtig ist

Oft kann derselbe Inhalt über mehr als eine URL erreicht werden, z. B. mit und ohne Schrägstrich, mit Tracking-Parametern oder mit unterschiedlicher Groß-/Kleinschreibung. Suchmaschinen behandeln jede URL als separate Seite, sofern nichts anderes angegeben wird. Der kanonische Link teilt ihnen mit, welche URL Sie bevorzugen; dies hilft ihnen, die Duplikate zu gruppieren, Rangfolgesignale wie eingehende Links auf einer URL zu kombinieren und diese URL in den Suchergebnissen anzuzeigen.

Eine kanonische Relation, die falsch ist, kann schlimmer sein als gar keine. Suchmaschinen können einen kanonischen Link ignorieren, dem sie nicht vertrauen können, z. B. einen ohne URL, einen außerhalb des `<head>` platzierten oder einen von mehreren Tags, die nicht übereinstimmen. Ein kanonischer Link, der auf eine andere Seite verweist, fordert Suchmaschinen auf, diese Seite anstelle Ihrer anzuzeigen, wodurch Ihre Seite aus Suchergebnissen ausgeschlossen werden kann.

## Was bei der Prüfung überprüft wird

Die Prüfung deckt Probleme in drei Bereichen ab:

* **Ob die Seite einen kanonischen Link hat:** der kanonische Link fehlt oder die Seite mehr als einen hat. Mehrere kanonische Links, die auf verschiedene URLs verweisen, werden separat gemeldet, da Suchmaschinen alle ignorieren können.
* **Ob das Tag korrekt eingerichtet ist:** das Tag sich außerhalb des `<head>` befindet, kein `href` oder ein leeres hat oder ein Attribut wie `hreflang`, `media` oder `type` trägt, das dazu führen kann, dass Suchmaschinen es ignorieren.
* **Ob die URL korrekt ist:** Die kanonische URL ist relativ statt absolut, enthält Großbuchstaben im Pfad oder in der Abfragezeichenfolge, verwendet ein anderes Protokoll (`http://` oder `https://`) als die Seite oder verweist auf eine andere Seite als die, die Sie bearbeiten.

## Vergleich der kanonischen URL

Preflight wird auf Vorschauseiten ausgeführt, deren Host sich in der Regel von Ihrer Produktions-Site unterscheidet. Um zu vermeiden, dass jede Vorschauseite gekennzeichnet wird, vergleicht der Audit den Host der kanonischen URL nicht mit dem Host der Seite. Wenn überprüft wird, ob der kanonische Link auf die Seite selbst verweist, wird nur der Pfad der URL verglichen, sodass `https://www.example.com/products/shoes` mit dem `/products/shoes` der Vorschauseite übereinstimmt. Ein Schrägstrich und eine Buchstabenformatierung im Pfad zählen bei dieser Prüfung nicht als Unterschiede.

## Bekannte Einschränkungen

* **Unterschiedliche Domain:** Eine kanonische URL, die auf eine andere Site verweist, wird von Preflight nicht gekennzeichnet, da Vorschau-Hosts sich immer von der Produktions-Site unterscheiden. Bestätigen Sie, dass die Domain in der kanonischen URL die erwartete ist.
* **HTTP-`Link`-Header:** Preflight prüft nur das kanonische Tag, nicht den HTTP-`Link`-Header. Bei einer Seite, die ihre kanonische URL nur in der Kopfzeile festlegt, fehlt der kanonische Link.

## Beheben von Problemen

Wenn der Audit Chancen findet, beschreibt jede das Problem und die empfohlene Änderung. In den meisten Fällen sollte die Seite genau einen kanonischen Link aufweisen, im `<head>` mit einer absoluten URL mit einem Pfad in Kleinbuchstaben, der auf die Seite selbst verweist. Wenn die Seite absichtlich auf eine andere Seite als kanonische Version verweist, z. B. ein Duplikat oder eine druckerfreundliche Kopie, können Sie sie unverändert lassen. Die Prüfung wird dennoch darüber berichten. Informationen zum Überprüfen und Beheben von Opportunities finden Sie unter [Audit results in Preflight](../../audit-results.md).
