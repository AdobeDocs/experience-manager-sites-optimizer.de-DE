---
title: PreFlight-Setup
description: Erfahren Sie, wie Sie die Preflight-Erweiterung für AEM Sites Optimizer einrichten.
source-git-commit: 6e177ef6b9d121ac7484ae118037c7e542f981d8
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 2%

---


# PreFlight-Setup

Zur Identifizierung von AEM Sites Optimizer Preflight-Opportunities ist die Einrichtung der Preflight-Erweiterung entweder im universellen Editor, der dokumentbasierten Vorschau oder in AEM Cloud Service erforderlich, um Preflight-Prüfungen auf Ihren Seiten durchzuführen, bevor sie veröffentlicht werden.

## Benutzerzugriff aktivieren

Um die Preflight-Erweiterung zu verwenden, stellen Sie sicher, dass Ihr Benutzer mindestens einem der folgenden AEM Sites Optimizer-Produktprofile in [Adobe Admin Console zugewiesen ist](https://adminconsole.adobe.com):

* AEM Sites Optimizer - Benutzer automatisch vorschlagen
* AEM Sites Optimizer - Benutzeroptimierung automatisch durchführen

## Aktivieren der Preflight-Erweiterung

>[!BEGINTABS]

>[!TAB Universeller Editor]

Gehen Sie wie folgt vor, um Preflight im universellen Editor einzurichten:

1. Öffnen Sie **Extension Manager** unter:
   [https://experience.adobe.com/#/@org/aem/extension-manager/universal-editor](https://experience.adobe.com/#/@org/aem/extension-manager/universal-editor)
1. Suchen Sie die **AEM Sites Optimizer Preflight-Erweiterung** und senden Sie eine Anfrage, um sie zu aktivieren.
1. Das **Adobe AEM** Team überprüft und aktiviert die Erweiterung für Ihr Unternehmen.
1. Nachdem die Erweiterung aktiviert ist, öffnen Sie eine Seite im **universellen Editor**, z. B.:
   `https://author-p12345-e123456.adobeaemcloud.com/ui#/@org/aem/universal-editor/canvas/author-p12345-e123456.adobeaemcloud.com/content/en/example/home.html`
1. Die **Preflight** Erweiterung) wird in der **Seitenleiste** angezeigt.
1. Wählen Sie in **Seitenleiste die** Preflight-Erweiterung“ aus, um **Preflight-Audit** der aktuellen Seite zu starten.

>[!TAB Dokumentenbasiertes Authoring]

Gehen Sie wie folgt vor, um Preflight für die dokumentbasierte Bearbeitung einzurichten:

1. Fügen Sie folgende Konfiguration zum `/tools/sidekick/config.json` im GitHub-Repository Ihres Edge Delivery Services-Projekts hinzu:

   ```json
   {
     "plugins": [
       {
         "id": "preflight",
         "titleI18n": {
           "en": "Preflight"
         },
         "environments": ["preview"],
         "event": "preflight"
       }
     ]
   }
   ```

1. Erstellen Sie eine neue `/tools/sidekick/aem-sites-optimizer-preflight.js` und fügen Sie den folgenden Inhalt hinzu:

   ```javascript
   (function () {
     let isAEMSitesOptimizerPreflightAppLoaded = false;
     function loadAEMSitesOptimizerPreflightApp() {
       const script = document.createElement('script');
       script.src = 'https://experience.adobe.com/solutions/OneAdobe-aem-sites-optimizer-preflight-mfe/static-assets/resources/sidekick/client.js?source=plugin';
       script.onload = function () {
         isAEMSitesOptimizerPreflightAppLoaded = true;
       };
       script.onerror = function () {
         console.error('Error loading AEMSitesOptimizerPreflightApp.');
       };
       document.head.appendChild(script);
     }
   
     function handlePluginButtonClick() {
       if (!isAEMSitesOptimizerPreflightAppLoaded) {
         loadAEMSitesOptimizerPreflightApp();
       }
     }
   
     // Sidekick V1 extension support
     const sidekick = document.querySelector('helix-sidekick');
     if (sidekick) {
       sidekick.addEventListener('custom:preflight', handlePluginButtonClick);
     } else {
       document.addEventListener('sidekick-ready', () => {
         document.querySelector('helix-sidekick')
           .addEventListener('custom:preflight', handlePluginButtonClick);
       }, { once: true });
     }
   
     // Sidekick V2 extension support
     const sidekickV2 = document.querySelector('aem-sidekick');
     if (sidekickV2) {
       sidekickV2.addEventListener('custom:preflight', handlePluginButtonClick);
     } else {
       document.addEventListener('sidekick-ready', () => {
         document.querySelector('aem-sidekick')
           .addEventListener('custom:preflight', handlePluginButtonClick);
       }, { once: true });
     }
   }());
   ```

1. Aktualisieren Sie die `loadLazy()` in `/scripts/scripts.js`, um das Preflight-Skript für Vorschau-URLs zu importieren:

   ```javascript
   if (window.location.href.includes('.aem.page')) {
      import('../tools/sidekick/aem-sites-optimizer-preflight.js');
   }
   ```

1. Öffnen Sie die Vorschau-URL (`*.aem.page`) der Seite, die Sie überprüfen möchten.
1. Klicken Sie in **Sidekick** auf die Schaltfläche **Preflight**, um den Audit für die aktuelle Seite zu starten.

>[!TAB AEM Sites-Seiteneditor]

Um Preflight im AEM Sites-Seiteneditor zu verwenden, können Sie eine Lesezeichenliste in Ihrem Webbrowser erstellen. Führen Sie die folgenden Schritte aus:

1. Zeigt Ihre **Lesezeichenleiste** in Ihrem Webbrowser an:

   * Drücken Sie **Strg+Umschalt+B** (Windows) oder **Befehl+Umschalt+B** (Mac).

! Erstellen Sie ein neues Lesezeichen in Ihrem Browser:

* Klicken Sie mit der rechten Maustaste auf die Leiste Lesezeichen und wählen Sie **Neue Seite** oder **Lesezeichen hinzufügen**.
* Fügen Sie im Feld **Adresse (URL** den folgenden Code ein:

```javascript
javascript:(function(){const script=document.createElement('script');script.src='https://experience.adobe.com/solutions/OneAdobe-aem-sites-optimizer-preflight-mfe/static-assets/resources/sidekick/client.js?source=bookmarklet&target-source=aem-cloud-service';document.head.appendChild(script);})();
```

1. Benennen Sie das Lesezeichen **Preflight** (oder einen beliebigen von Ihnen bevorzugten Namen).
1. Öffnen Sie die Vorschau-URL (`*.aem.page`) der zu überprüfenden Seite im **AEM Sites-Seiteneditor**.
1. Klicken Sie auf **Preflight** Lesezeichen in Ihrer Lesezeichenleiste, um den Audit für die aktuelle Seite zu starten.

>[!ENDTABS]

## Best Practices

Beachten Sie beim Ausführen von Preflight-Audits die folgenden Richtlinien:

* Führen Sie Audits immer auf **Staging- oder Vorschauseiten) durch** bevor Sie sie in der Produktion veröffentlichen.
* Priorisieren Sie **Behebung von Problemen mit hoher**, wie fehlerhaften Links, fehlenden H1-Tags oder unsicheren Links.
* Stellen Sie **Authentifizierung ist aktiviert** für geschützte Staging-Umgebungen sicher, bevor Sie Audits ausführen.
* Überprüfen und wenden Sie **Meta-Tag-Empfehlungen** an, um die SEO-Leistung zu verbessern.
