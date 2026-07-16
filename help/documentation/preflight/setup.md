---
title: Preflight-Setup
description: Erfahren Sie, wie Sie Preflight für AEM Sites Optimizer einrichten.
TQID: https://experienceleague.adobe.com/GfLmEEBoSP2481ZZUjRyyfMjExGgI0l9yMAqTF8ObcY
product_v2: id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
source-git-commit: f19dd2eec5cef95f406111d2250ff1101a4fd430
workflow-type: tm+mt
source-wordcount: 577
ht-degree: 72%

---

# Preflight-Setup

Um Preflight ausführen zu können, muss es in Ihrer Authoring-Umgebung eingerichtet werden. Sie können Preflight für den universellen Editor, die dokumentbasierte Bearbeitung, den AEM Sites-Seiteneditor oder Adobe Managed Services einrichten, damit Sie Preflight-Prüfungen auf Ihren Seiten durchführen können, bevor sie veröffentlicht werden.

## Aktivieren des Benutzerzugriffs

Um Preflight zu verwenden, stellen Sie sicher, dass Ihr Benutzer mindestens einem der folgenden AEM Sites Optimizer-Produktprofile in [Adobe Admin Console zugewiesen ist](https://adminconsole.adobe.com):

* AEM Sites Optimizer – Benutzende automatisch vorschlagen
* AEM Sites Optimizer – Benutzende automatisch optimieren

## Preflight aktivieren

>[!BEGINTABS]

>[!TAB Universeller Editor]

Gehen Sie wie folgt vor, um Preflight im universellen Editor einzurichten:

1. Öffnen Sie den **Extension Manager** unter:
   [https://experience.adobe.com/#/@org/aem/extension-manager/universal-editor](https://experience.adobe.com/#/@org/aem/extension-manager/universal-editor)
1. Suchen Sie die Erweiterung **AEM Sites Optimizer Preflight**.
1. Die Systemadmins der Organisation müssen diese Erweiterung aktivieren.
1. Nachdem die Erweiterung aktiviert ist, öffnen Sie eine Seite im **universellen Editor**, z. B.:
   `https://author-p12345-e123456.adobeaemcloud.com/ui#/@org/aem/universal-editor/canvas/author-p12345-e123456.adobeaemcloud.com/content/en/example/home.html`
1. Die **Preflight-Erweiterung** wird in der **Seitenleiste** angezeigt.
1. Wählen Sie in **Seitenleiste die** Preflight-Erweiterung) aus, um Preflight für die aktuelle Seite zu öffnen.

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

1. Öffnen Sie die Vorschau-URL (`*.aem.page`) der Seite, die Sie prüfen möchten.
1. Klicken Sie in **Sidekick** auf die Schaltfläche **Preflight**, um Preflight für die aktuelle Seite zu öffnen.

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
1. Öffnen Sie die Vorschau-URL (`*.aem.page`) der Seite, die Sie im **AEM Sites-Seiteneditor** prüfen möchten.
1. Klicken Sie auf **Preflight** Lesezeichen in Ihrer Lesezeichenleiste, um Preflight für die aktuelle Seite zu öffnen.

>[!TAB Adobe Managed Services]

>[!IMPORTANT]
>
>Es werden nur Adobe Managed Services (AMS)-Umgebungen unterstützt, die Adobe Identity Provider (IMS) für die Authentifizierung auf der AEM-Autoreninstanz verwenden. Preflight funktioniert nicht, wenn Ihr Unternehmen einen anderen Identitätsanbieter für die AMS-Authentifizierung verwendet.

Um Preflight im AEM Sites-Seiteneditor in einer AMS-Umgebung zu verwenden, erstellen Sie eine Lesezeichenliste in Ihrem Webbrowser, indem Sie die folgenden Schritte ausführen:

1. Zeigen Sie Ihre **Lesezeichenleiste** in Ihrem Webbrowser an:

   * Drücken Sie **Strg+Umschalt+B** (Windows) oder **Befehl+Umschalt+B** (Mac).

1. Erstellen Sie ein neues Lesezeichen in Ihrem Browser:

   * Klicken Sie mit der rechten Maustaste auf die Lesezeichenleiste und wählen Sie **Neue Seite** oder **Lesezeichen hinzufügen** aus.
   * Fügen Sie im Feld **Adresse (URL)** den folgenden Code ein:

   ```javascript
   javascript:(function(){const script=document.createElement('script');script.src='https://experience.adobe.com/solutions/OneAdobe-aem-sites-optimizer-preflight-mfe/static-assets/resources/sidekick/client.js?source=bookmarklet&target-source=ams';document.head.appendChild(script);})();
   ```

1. Nennen Sie das Lesezeichen **Preflight** (oder verwenden Sie einen beliebigen Namen, den Sie bevorzugen).
1. Öffnen Sie die zu prüfende Seite im **AEM Sites-Seiteneditor**.
1. Klicken Sie auf **Preflight** Lesezeichen in Ihrer Lesezeichenleiste, um Preflight für die aktuelle Seite zu öffnen.

>[!ENDTABS]

## Best Practices

Beachten Sie beim Ausführen von Preflight-Audits die folgenden Richtlinien:

* Führen Sie Audits immer für **Staging- oder Vorschauseiten** durch, bevor Sie sie in der Produktion veröffentlichen.
* Priorisieren Sie die Behebung von **schwerwiegenden Problemen** ( z. B. fehlerhafte Links, fehlende H1-Tags oder unsichere Links).
* Stellen Sie sicher, dass für Staging-Umgebungen die **Authentifizierung aktiviert** ist, bevor Sie Audits ausführen.
* Überprüfen und wenden Sie **Meta-Tag-Empfehlungen** an, um die SEO-Leistung zu verbessern.
