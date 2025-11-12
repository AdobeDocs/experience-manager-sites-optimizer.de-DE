---
title: Preflight-Setup
description: Erfahren Sie, wie Sie die Preflight-Erweiterung für AEM Sites Optimizer einrichten.
source-git-commit: 210acc5337796707ced10f2b84d473503fc06088
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 100%

---


# Preflight-Setup

Zur Identifizierung von Preflight-Möglichkeiten in AEM Sites Optimizer ist die Einrichtung der Preflight-Erweiterung entweder im universellen Editor, der dokumentbasierten Vorschau oder in AEM Cloud Service erforderlich. Damit können Sie Preflight-Prüfungen Ihrer Seiten durchführen, bevor Sie sie veröffentlichen.

## Aktivieren des Benutzerzugriffs

Damit sich die Preflight-Erweiterung verwenden lässt, müssen Sie sicherstellen, dass die Benutzerin bzw. der Benutzer in [Adobe Admin Console](https://adminconsole.adobe.com) mindestens einem der folgenden AEM Sites Optimizer-Produktprofile zugewiesen ist:

* AEM Sites Optimizer – Benutzende automatisch vorschlagen
* AEM Sites Optimizer – Benutzende automatisch optimieren

## Aktivieren der Preflight-Erweiterung

>[!BEGINTABS]

>[!TAB Universeller Editor]

Gehen Sie wie folgt vor, um Preflight im universellen Editor einzurichten:

1. Öffnen Sie den **Extension Manager** unter:
   [https://experience.adobe.com/#/@org/aem/extension-manager/universal-editor](https://experience.adobe.com/#/@org/aem/extension-manager/universal-editor)
1. Suchen Sie nach der **AEM Sites Optimizer Preflight-Erweiterung** und senden Sie eine Anfrage, um sie zu aktivieren.
1. Das **Adobe AEM-Team** wird Ihre Anfrage prüfen und die Erweiterung für Ihr Unternehmen aktivieren.
1. Nachdem die Erweiterung aktiviert ist, öffnen Sie eine Seite im **universellen Editor**, z. B.:
   `https://author-p12345-e123456.adobeaemcloud.com/ui#/@org/aem/universal-editor/canvas/author-p12345-e123456.adobeaemcloud.com/content/en/example/home.html`
1. Die **Preflight-Erweiterung** wird in der **Seitenleiste** angezeigt.
1. Wenn Sie in der Seitenleiste auf die **Preflight-Erweiterung** klicken, wird das **Preflight-Audit** für die aktuelle Seite gestartet.

>[!TAB Dokumentenbasiertes Authoring]

Gehen Sie wie folgt vor, um Preflight für das dokumentenbasierte Authoring einzurichten:

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

1. Erstellen Sie eine neue Datei mit dem Namen `/tools/sidekick/aem-sites-optimizer-preflight.js` und fügen Sie den folgenden Inhalt hinzu:

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

1. Aktualisieren Sie die `loadLazy()`-Funktion in `/scripts/scripts.js`, um das Preflight-Skript für Vorschau-URLs zu importieren:

   ```javascript
   if (window.location.href.includes('.aem.page')) {
      import('../tools/sidekick/aem-sites-optimizer-preflight.js');
   }
   ```

1. Öffnen Sie die Vorschau-URL (`*.aem.page`) der Seite, die Sie überprüfen möchten.
1. Klicken Sie in **Sidekick** auf die Schaltfläche **Preflight**, um die Prüfung für die aktuelle Seite zu starten.

>[!TAB AEM-Sites – Seiteneditor]

Um Preflight im Seiteneditor von AEM Sites zu verwenden, können Sie in Ihrem Webbrowser ein Bookmarklet erstellen. Führen Sie die folgenden Schritte aus:

1. Zeigen Sie Ihre **Lesezeichenleiste** in Ihrem Webbrowser an:

   * Drücken Sie **Strg+Umschalt+B** (Windows) oder **Befehl+Umschalt+B** (Mac).

1. Erstellen Sie ein neues Lesezeichen in Ihrem Browser:

   * Klicken Sie mit der rechten Maustaste auf die Lesezeichenleiste und wählen Sie **Neue Seite** oder **Lesezeichen hinzufügen** aus. 
   * Fügen Sie im Feld **Adresse (URL)** den folgenden Code ein:

   ```javascript
   javascript:(function(){const script=document.createElement('script');script.src='https://experience.adobe.com/solutions/OneAdobe-aem-sites-optimizer-preflight-mfe/static-assets/resources/sidekick/client.js?source=bookmarklet&target-source=aem-cloud-service';document.head.appendChild(script);})();
   ```

1. Nennen Sie das Lesezeichen **Preflight** (oder verwenden Sie einen beliebigen Namen, den Sie bevorzugen).
1. Öffnen Sie die Vorschau-URL (`*.aem.page`) der zu prüfenden Seite im **Seiteneditor von AEM Sites**.
1. Klicken Sie in Ihrer Lesezeichenleiste auf das **Preflight**-Lesezeichen, um den Audit für die aktuelle Seite zu starten.

>[!ENDTABS]

## Best Practices

Beachten Sie beim Ausführen von Preflight-Audits die folgenden Richtlinien:

* Führen Sie Audits immer für **Staging- oder Vorschauseiten** durch, bevor Sie sie in der Produktion veröffentlichen.
* Priorisieren Sie die Behebung von **schwerwiegenden Problemen** ( z. B. fehlerhafte Links, fehlende H1-Tags oder unsichere Links).
* Stellen Sie sicher, dass bei geschützten Staging-Umgebungen **Authentifizierung aktiviert ist**, bevor Sie Audits ausführen.
* Überprüfen und wenden Sie **Meta-Tag-Empfehlungen** an, um die SEO-Leistung zu verbessern.
