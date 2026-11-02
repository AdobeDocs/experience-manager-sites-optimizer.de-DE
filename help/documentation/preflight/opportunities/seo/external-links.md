---
title: Prüfung externer Links vor einem Flug
description: Erfahren Sie mehr über die Prüfung externer Links in Preflight für AEM Sites Optimizer.
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
source-git-commit: 12279cd1468a3442709cb73a8691922598a33dab
workflow-type: tm+mt
source-wordcount: '1112'
ht-degree: 0%
---
# Prüfung externer Links

Der Audit **Externe Links** überprüft die Links auf Ihrer Seite, die auf andere Sites verweisen. Die Prüfung prüft jeden externen Link auf der Seite, die Sie bearbeiten, und kennzeichnet die fehlerhaften, unsicheren oder nicht automatisch verifizierten Links.

## Warum das wichtig ist

Ein defekter externer Link ist eine Sackgasse für den Leser und ein Signal an Suchmaschinen, dass die Seite nicht gut gepflegt ist. Externe Links sind auch die Links, auf die Sie am wenigsten Kontrolle haben: Die andere Site kann eine Seite jederzeit verschieben, umbenennen oder entfernen, und Ihr Link funktioniert im Hintergrund nicht mehr. Wenn Sie sie vor der Veröffentlichung überprüfen, werden die Links erfasst, die seit dem ersten Hinzufügen veraltet sind.

## Was bei der Prüfung überprüft wird

Bei der Prüfung werden Probleme in drei Gruppen unterteilt:

* **Beschädigt:** der Link schlägt für jeden Besucher derzeit fehl und wird voraussichtlich nicht wiederhergestellt.
* **Nicht verifiziert:** der Link schlägt für einige Besucher fehl, kann nur vorübergehend fehlschlagen oder konnte nicht überprüft werden.
* **Best Practice:** Link funktioniert, sollte jedoch nicht auf diese Weise erstellt werden, z. B. als unsicherer `http://`.

Der Audit meldet eine Opportunity für jeden externen Link, der eines der folgenden Probleme aufweist:

* **Beschädigter Link:** Der Link funktioniert für niemanden, der ihn öffnet. Preflight meldet einen Link als unterbrochen, wenn:
  * Seine Site ist überhaupt nicht erreichbar, zum Beispiel weil die Domain nicht mehr existiert.
  * Gibt `Status 404` oder `Status 410` zurück.
  * Sie gibt `Status 405` zurück, d. h. die Site lehnt normale Seitenanfragen ab.
  * Er leitet in einer Schleife oder mehr als 20-mal weiter. Browser verwenden dieselbe Begrenzung und zeigen den Fehler „Zu viele Weiterleitungen“ an.

  Ein Link, der einen dieser Fehler nach einer Umleitung erreicht, wird auf die gleiche Weise gemeldet.
* **Unsicherer Link:** der Link verwendet `http://` und Preflight sah keine Umleitung zu `https://`, auch wenn die Website nicht reagierte. Ein Link, der als `http://` beginnt, aber zu einer sicheren `https://` umgeleitet wird, ist nicht gekennzeichnet. Aktualisieren Sie den Link, um `https://` zu verwenden.
* **Nicht verifizierter Link:** Preflight konnte nicht bestätigen, ob der Link funktioniert, daher werden Sie aufgefordert, den Link zu öffnen und selbst zu überprüfen. Die Gelegenheit erklärt, welcher Fall zutrifft:
  * **Anmeldung erforderlich:** Der Link gibt `Status 401` zurück. Besucherinnen und Besucher ohne Konto können es nicht öffnen. Bestätigen Sie daher, dass dies beabsichtigt ist.
  * **Blockiert automatisierte Prüfungen:** der Link gibt `Status 403` oder `Status 429` zurück oder die Site blockiert automatisierte Anfragen auf andere Weise, wie LinkedIn es tut. Bestätigen Sie, dass der Link in einem Browser geöffnet wird.
  * **Social-Media- und Sign-in-Wall-Websites:** LinkedIn, Instagram, Facebook, X (Twitter), TikTok und Threads geben irreführende Fehler an anonyme Anfragen zurück, sodass eine `Status 404`-, `Status 410`-, `Status 405`- oder Umleitungsschleife von diesen Websites als nicht verifiziert anstatt als beschädigt gemeldet wird.
  * **Server-Fehler:** der Link gibt einen Server-Fehler (`Status 5xx`) zurück, der bestehen bleibt, wenn Preflight ihn erneut prüft. PreFlight-Wiederholungen einmal vor der Berichterstellung. Der Fehler kann temporär sein. Überprüfen Sie daher vor der Veröffentlichung, ob der Link funktioniert.
  * **Aus rechtlichen Gründen nicht verfügbar:** der Link gibt `Status 451` in der Region zurück, von der aus Preflight-Prüfungen durchgeführt werden. Vergewissern Sie sich, dass es für Ihre Zielgruppe funktioniert.
  * **Keine Antwort in der Zeit:** Die Site hat nicht rechtzeitig reagiert, auch nicht nach einem erneuten Versuch von Preflight. Die Site kann langsam oder vorübergehend langsamer sein.

Ein Link kann sowohl unsicher als auch defekt oder sowohl unsicher als auch unverifiziert sein. In diesem Fall werden beide Opportunitys gemeldet. Eine Umleitungskette allein wird nicht gekennzeichnet, wenn sie innerhalb von 20 Umleitungen eine Arbeitsseite erreicht.

## Welche Links werden überprüft?

Jeder externe Link auf der Seite wird überprüft. Ein externer Link ist ein Link, dessen Host sich von der Seite, die Sie bearbeiten, unterscheidet. Der Host ist der Domain-Name plus ein beliebiger nicht standardmäßiger Port, z. B. `:8443`. Subdomains werden als verschiedene Hosts gezählt, sodass `blog.example.com` und `example.com` außerhalb von `www.example.com` liegen. Links zum selben Host, einschließlich `http://` Links zu Ihrer eigenen Site, werden stattdessen vom Audit [Interne Links](./internal-links.md) abgedeckt. Links in der Site-Navigation sind immer enthalten, da die Einstellung **Site-Navigations-Links anzeigen** nur für den Audit Interne Links gilt. Links wie `mailto:`, `tel:` und `javascript:` werden ignoriert.

Jeder Link wird einmal gemeldet, auch wenn er mehrmals auf der Seite oder mit verschiedenen Ankern wie `#pricing` und `#features` angezeigt wird. Die Opportunity hebt die erste Stelle hervor, an der der Link angezeigt wird.

Links, die der Link-Checker von AEM bereits als ungültig markiert hat, werden in die Prüfung einbezogen, auch wenn der Editor den anklickbaren Link von der Seite entfernt. Sie werden erneut überprüft, anstatt sie als vertrauenswürdig anzusehen, sodass ein Link, der seitdem funktioniert hat, nicht gemeldet wird.

## Filtern der Ergebnisse

Verwenden Sie auf der Detailseite den Filter neben der Überschrift **Instanzen** um nur einige der Opportunities anzuzeigen:

| Filter | Angezeigte Opportunities |
|---|---|
| **Alle** (Standard) | Jede Gelegenheit |
| **gebrochen** | Beschädigte Links |
| **Erfordert Verifizierung** | Nicht verifizierte Links und unsichere Links |

Wenn ein Link mehr als eine Opportunity hat, z. B. einen unsicheren Link, der ebenfalls unterbrochen ist, wird jede Opportunity unter einem eigenen Filter angezeigt. Weitere Informationen finden Sie unter [Instanzen filtern](../../audit-results.md#filter-instances).

## Bekannte Einschränkungen

* **Private Adressen:** Links zu privaten oder internen Netzwerkadressen, wie z. B. einer Intranet-Site, werden nicht überprüft und nicht gemeldet.
* **Zeitlimits:** jeder Link verfügt über ein eigenes Zeitlimit, sodass eine langsame Site nicht verhindert, dass andere Links überprüft werden. Jeder Link auf der Seite erhält ein Ergebnis. Ein Link, der selbst nach einem erneuten Versuch nicht rechtzeitig reagiert, wird als **Unverifizierter Link“** als defekt gemeldet.
* **Ausgeschlossene Domains:** die Konfiguration Ihrer Site bestimmte Domains von der Überprüfung ausschließen kann. Links zu einer ausgeschlossenen Domain oder zu einer ihrer Subdomains werden nicht überprüft und nicht gemeldet.
* **Server-seitige Ansicht:** Preflight prüft externe Links von den Servern von Adobe und nicht von Ihrem Browser aus. Eine Site, die sich je nach Standort, Anmeldung oder Bot-Erkennung anders verhält, kann ein anderes Ergebnis zurückgeben, als Sie in Ihrem Browser sehen. Solche Links werden in der Regel als **Unverifizierter Link** und nicht als defekt gemeldet.

## Beheben von Problemen

Wenn der Audit Chancen findet, beschreibt jede das Problem und die empfohlene Änderung und identifiziert den betreffenden Link. Verwenden Sie **Hervorheben auf**, um zum Link in Ihrem Inhalt zu springen, und öffnen Sie die URL in einer neuen Registerkarte, um das Problem für sich selbst zu bestätigen. Handeln Sie dann entsprechend der Opportunity:

* **Beschädigter Link:** Aktualisieren Sie den Link am neuen Speicherort der Seite oder ersetzen oder entfernen Sie ihn. Für eine Umleitungsschleife kontaktieren Sie den Eigentümer der anderen Website oder einen Link zu einer anderen Quelle.
* **Nicht sicherer Link:** Ändern Sie den Link, um `https://` zu verwenden, nachdem Sie bestätigt haben, dass die sichere Version funktioniert.
* **Nicht verifizierter Link:** Öffnen Sie den Link in Ihrem Browser und bestätigen Sie, dass er die erwartete Seite anzeigt. Bestätigen Sie bei einem Link, für den eine Anmeldung erforderlich ist, dass Ihre Leser über ein Konto verfügen sollen. Überprüfen Sie bei einem Server-Fehler den Link erneut, bevor Sie die Veröffentlichung durchführen. Wenn der Link nicht funktioniert, behandeln Sie ihn als beschädigt.

Informationen zum Überprüfen und Beheben von Opportunities finden Sie unter [Audit results in Preflight](../../audit-results.md).
