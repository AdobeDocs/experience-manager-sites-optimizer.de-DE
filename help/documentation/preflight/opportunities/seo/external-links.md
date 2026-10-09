---
title: Prüfung externer Links vor einem Flug
description: Erfahren Sie mehr über die Prüfung externer Links in Preflight für AEM Sites Optimizer.
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
source-git-commit: 9fd898e905bf843b4d39891c5875497a01569791
workflow-type: tm+mt
source-wordcount: '763'
ht-degree: 0%
---
# Prüfung externer Links

Der Audit **Externe Links** überprüft die Links auf Ihrer Seite, die auf andere Sites verweisen. Die Prüfung prüft jeden externen Link auf der Seite, die Sie bearbeiten, und kennzeichnet die fehlerhaften, unsicheren oder nicht automatisch verifizierten Links.

## Warum das wichtig ist

Ein defekter externer Link ist eine Sackgasse für den Leser und ein Signal an Suchmaschinen, dass die Seite nicht gut gepflegt ist. Externe Links sind auch die Links, auf die Sie am wenigsten Kontrolle haben: Die andere Site kann eine Seite jederzeit verschieben, umbenennen oder entfernen, und Ihr Link funktioniert im Hintergrund nicht mehr. Wenn Sie sie vor der Veröffentlichung überprüfen, werden die Links erfasst, die seit dem ersten Hinzufügen veraltet sind.

## Was bei der Prüfung überprüft wird

Der Audit meldet eine Opportunity für jeden externen Link, der eines der folgenden Probleme aufweist:

* **Beschädigter Link:** Der Link kann nicht erreicht werden oder gibt einen Fehler wie `Status 404`, `Status 410` oder einen `5xx` Server-Fehler zurück. Ein Link, der nach einer Umleitung zum Fehler führt, wird auf die gleiche Weise gemeldet. Ein Link, dessen Site überhaupt nicht reagiert, weil die Domain beispielsweise nicht mehr existiert, wird ebenfalls als fehlerhaft gemeldet.
* **Nicht sicherer Link:** der Link verwendet `http://` und die Site leitet ihn nicht zu `https://` weiter. Ein Link, der als `http://` beginnt, aber zu einer sicheren `https://` umgeleitet wird, ist nicht gekennzeichnet. Aktualisieren Sie den Link, um `https://` zu verwenden.
* **Nicht verifizierter Link:** die Website antwortete, lehnte die automatisierte Prüfung jedoch ab, z. B. weil sie eine Anmeldung erfordert (`Status 401` oder `Status 403`), automatisierte Anfragen einschränkt (`Status 429`) oder Bots blockiert, wie es einige soziale Netzwerke tun. Ein Link, der zu oft umleitet, um ihm zu folgen, wird ebenfalls auf diese Weise gemeldet. Diese Links funktionieren sehr wahrscheinlich in einem Browser, sodass Preflight sie nicht als beschädigt meldet. Stattdessen werden Sie aufgefordert, den Link zu öffnen und selbst zu bestätigen, und es wird mit geringer Auswirkung berichtet.

Ein Link kann sowohl unsicher als auch defekt oder sowohl unsicher als auch unverifiziert sein. In diesem Fall werden beide Opportunitys gemeldet. Ein Link, der erfolgreich aufgelöst wird, wird nicht markiert, selbst wenn er unterwegs Umleitungen aufweist.

## Wie die Links überprüft werden

Ein externer Link ist ein Link, dessen Host sich von der Seite, die Sie bearbeiten, unterscheidet. Der Host ist der Domain-Name plus ein beliebiger nicht standardmäßiger Port, z. B. `:8443`. Subdomains werden als verschiedene Hosts gezählt, sodass `blog.example.com` und `example.com` außerhalb von `www.example.com` liegen. Ob der Link `http://` oder `https://` verwendet, spielt keine Rolle. Links zum selben Host, einschließlich `http://` Links zu Ihrer eigenen Site, werden stattdessen vom Audit [Interne Links](./internal-links.md) abgedeckt. Links wie `mailto:`, `tel:` und `javascript:` werden ignoriert.

Ihr Browser kann den Status eines Links auf einer anderen Website nicht lesen. Daher prüft Preflight externe Links von den Servern von Adobe und nicht von Ihrer Autorensitzung aus. Jeder Link wird einmal geprüft, auch wenn er mehrmals auf der Seite oder mit verschiedenen Referenzzeichen (z. B. `#pricing` und `#features`) angezeigt wird. Die Opportunity hebt die erste Stelle hervor, an der der Link angezeigt wird.

Links, die der Link-Checker von AEM bereits als ungültig markiert hat, werden in die Prüfung einbezogen, auch wenn der Editor den anklickbaren Link von der Seite entfernt. Sie werden dann erneut überprüft, anstatt sie als vertrauenswürdig anzusehen, sodass ein Link, der seitdem funktioniert hat, nicht gemeldet wird.

## Bekannte Einschränkungen

* **Anzahl der Links** Pro Seite werden bis zu 50 verschiedene externe Links überprüft. Links, die über dieses Limit hinausgehen, werden nicht aktiviert.
* **Zeitlimit:** jeder Link eine Zeitüberschreitung von 10 Sekunden aufweist und die gesamte Prüfung eine Zeitbeschränkung aufweist, sodass Preflight responsiv bleibt. Eine Site, die nicht innerhalb der maximalen Wartezeit reagiert, wird als fehlerhaft gemeldet. Auf Seiten mit vielen langsamen Sites werden einige Links in einem bestimmten Durchgang möglicherweise nicht überprüft.
* **Private Adressen:** Links, die zu privaten oder internen Netzwerkadressen führen, wie z. B. eine Intranet-Site, werden nicht überprüft und nicht gemeldet.
* **Serverseitige Ansicht:** Da Links von den Adobe-Servern überprüft werden, kann eine Site, die sich je nach Standort, Anmeldung oder Bot-Erkennung anders verhält, ein anderes Ergebnis zurückgeben, als Sie in Ihrem Browser sehen. Solche Links werden in der Regel als **Unverifizierter Link** und nicht als defekt gemeldet.

## Beheben von Problemen

Wenn der Audit Chancen findet, beschreibt jede das Problem und die empfohlene Änderung und identifiziert den betreffenden Link. Verwenden Sie **Hervorheben auf**, um zum Link in Ihrem Inhalt zu springen, und öffnen Sie die URL in einer neuen Registerkarte, um das Problem für sich selbst zu bestätigen. Bei einem fehlerhaften Link aktualisieren Sie ihn auf den neuen Speicherort der Seite oder entfernen Sie ihn. Bestätigen Sie bei einem nicht verifizierten Link, dass er korrekt in Ihrem Browser geöffnet wird. Informationen zum Überprüfen und Beheben von Opportunities finden Sie unter [Audit results in Preflight](../../audit-results.md).
