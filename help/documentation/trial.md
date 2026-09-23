---
title: Sites Optimizer-Testversion
description: Beginnen Sie mit der AEM Sites Optimizer-Testversion für AEM Sites-Bestandskundschaft.
source-git-commit: 052faac621530a5b9e74bd8e4790a604887515f7
workflow-type: tm+mt
source-wordcount: '1481'
ht-degree: 45%
---

# Sites Optimizer-Testversion

Beginnen Sie mit Sites Optimizer und verwenden Sie diese Testversion für bestehende **AEM Sites-Kunden (Edge Delivery Services, Cloud Services und Managed Services)**. Ihre Domain-Daten sind bereits vorkonfiguriert, sodass Sie sofort mit der Optimierung beginnen können. Das folgende Video führt Sie durch das Testerlebnis und zeigt Ihnen, wie Sie beginnen.

>[!IMPORTANT]
>
>Stellen Sie vor dem Start sicher, dass Ihre Site die folgenden Anforderungen erfüllt:
>
>* Sie basiert auf AEM Sites (Edge Delivery Services, Cloud Service oder Managed Services).
>* Es handelt sich um eine Produktions-, keine Entwicklungs-, QS-, Staging-, Autoren- oder Vorschauumgebung.
>* Es ist öffentlich zugänglich und nicht hinter einer Anmeldung.
>* Es wird die AEM Sites-Frontend-Bereitstellung verwendet. Die Headless-Bereitstellung wird derzeit nicht unterstützt.

>[!VIDEO](https://video.tv.adobe.com/v/3483296/?captions=ger&learn=on&enablevpops)

>[!TIP]
>
> Wenden Sie sich mit Fragen oder Anfragen an [siteoptimizer-now@adobe.com](mailto:siteoptimizer-now@adobe.com).

## Beginnen Sie jetzt mit Ihrer Testversion.

Führen Sie die folgenden Schritte aus, um mit Ihrer Testversion zu beginnen:

1. Melden Sie sich mit Ihrer AEM Sites IMS-Organisations-ID bei [www.sitesoptimizer.live](http://www.sitesoptimizer.live/) an.
2. Zeigen Sie wichtige Metriken wie Seitenansichten, Ladezeit und Interaktionsrate zusammen mit Ihren wichtigsten Optimierungsmöglichkeiten an, die nach Wirkung priorisiert sind.
3. Untersuchen Sie die drei verfügbaren Arten von Möglichkeiten: [Fehlerhafte Backlinks](./opportunities/broken-backlinks.md), [Core Web Vitals](./opportunities/core-web-vitals.md) und [fehlender Alternativtext](./opportunities/missing-alt-text.md).
4. Prüfen Sie für jede Möglichkeit bis zu drei identifizierte Probleme. Verwenden Sie KI-generierte Vorschläge und stellen Sie Optimierungen bei Bedarf direkt in Ihrer AEM-Umgebung bereit.
5. Erschließen Sie weitere Möglichkeiten, indem Sie jederzeit ein Upgrade auf die Volllizenz durchführen.

## Inhalt der Testversion

In der Testversion ist Folgendes enthalten:

* Drei Arten von Möglichkeiten: [Fehlerhafte Backlinks](./opportunities/broken-backlinks.md), [Core Web Vitals](./opportunities/core-web-vitals.md) und [Fehlender Alternativtext](./opportunities/missing-alt-text.md).
* Bis zu drei Probleme pro Möglichkeit und Monat.
* Vollständiger Workflow für jedes Problem: automatisches Identifizieren, automatisches Vorschlagen und automatisches Optimieren.
  * **Automatisches Identifizieren** – Erkennt Probleme auf Ihrer Site mithilfe mehrerer Datenquellen.
  * **Automatisches Vorschlagen** – Stellt präskriptive, KI-generierte Empfehlungen für jedes Problem bereit.
  * **Automatisches Optimieren** – Stellen Sie nach der Genehmigung Fehlerbehebungen direkt in Ihrer Autorenumgebung bereit. Aktualisierungen folgen Ihren bestehenden Workflows, sodass Ihr Team sie über AEM prüfen und veröffentlichen kann.

## Zugriff von Sites Optimizer auf Ihre Website zulassen

Sites Optimizer scannt Ihre Site, um Optimierungsmöglichkeiten zu identifizieren. Wenn sich Ihre Site hinter einer Firewall, einem Content Delivery Network (CDN) oder einer anderen Sicherheitskonfiguration befindet, die nicht erkannte Clients blockiert, kann der Scanner Ihre Seiten nicht erreichen. In diesem Fall wird beim Onboarding die Meldung **Aktion erforderlich** angezeigt, dass Sites Optimizer nicht auf Ihre Website zugreifen kann. Außerdem wird der Scanvorgang angehalten, bis Sie den Zugriff zulassen.

![Onboarding-Dialogfeld, in dem angegeben wird, dass Sites Optimizer nicht auf die Website zugreifen kann, mit einer Liste der zu kopierenden Benutzeragenten- und Scanner-IP-Adressen, jeweils mit einer Schaltfläche zum Kopieren und einer Schaltfläche zum Aktualisieren, um den Zugriff erneut zu überprüfen](./assets/trial/ip-allowlist-action-required.png){align="center"}

Um den Scanner durchzulassen, führen Sie die folgenden Zulassungslisten in Ihrer Firewall, Ihrem Hosting-Anbieter oder Ihrer Sicherheitskonfiguration durch. Fügen Sie für AEM Cloud Service-Sites eine Zulassungsregel für den Scanner zu Ihren [CDN-Traffic-Filterregeln](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/security/traffic-filter-rules-including-waf) in Cloud Manager hinzu, die sowohl für den Benutzeragenten als auch für die IP-Adresse übereinstimmen kann. Wenn Sie den Zugriff mithilfe von [Cloud Manager IP-Zulassungslisten &#x200B;](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/ip-allow-lists/introduction) einschränken, fügen Sie auch die IP-Adressen der Scanner zur angewendeten Zulassungsliste hinzu.

* **Benutzeragent** - Der Scanner identifiziert sich mit einem Benutzeragenten, der die Token-`Spacecat/1.0` enthält. Zulassungsliste dieses Tokens, im Idealfall eine Übereinstimmung mit „contains“, sodass es auch dann funktioniert, wenn sich die vollständige Benutzeragenten-Zeichenfolge ändert.
* **Scanner-IP** Adressen: Hiermit werden die ausgehenden IP-Adressen des Scanners Auf die Zulassungsliste gesetzt.

Der Onboarding-Bildschirm zeigt die genauen zu kopierenden Benutzeragenten- und IP-Adressen mit jeweils einer **Kopieren**-Schaltfläche an, sodass Sie die aktuellen Werte direkt in Ihre Konfiguration kopieren können.

Wählen Sie nach der Zulassungsliste des Scanners **Aktualisieren** auf dem Onboarding-Bildschirm aus. Sobald der Zugriff gewährt wurde, wird die Überprüfung automatisch fortgesetzt und Ihre Optimierungsmöglichkeiten werden angezeigt.

>[!NOTE]
>
>Diese IP-Adressen werden nur zur Analyse Ihrer Site verwendet. Durch ihre Zulassungsauflistung wird kein anderer Zugriff gewährt.

## Automatische Fehlerbehebung für Edge Delivery-Test-Sites aktivieren

Erfahren Sie, wie Testkunden die Aktion **Für Autor bereitstellen** für automatische Fehlerbehebungsvorschläge für Edge Delivery Services (EDS)-Sites aktivieren, die in Google Drive oder SharePoint erstellt wurden.

>[!NOTE]
>
>Diese Anforderung gilt nur für Testorganisationen, deren Sites in Google Drive oder SharePoint verfasst wurden. Bezahlte Kunden und in Crosswalk oder Dark Alley erstellte Websites sind davon nicht betroffen.

Testkunden müssen zur IMS-Gruppe **ASO-EDS-Autofix-Users** gehören. Wenn die Gruppe nicht vorhanden ist, kann der Administrator Ihres Unternehmens sie erstellen und Sie hinzufügen.

1. Melden Sie sich bei der [Adobe Admin Console](https://adminconsole.adobe.com/) an.
1. Wählen Sie **Benutzer** > **Benutzergruppen** aus.
1. Wählen **Benutzergruppe hinzufügen** aus.
1. Geben **unter „Name der Benutzergruppe** genau Folgendes ein:

   ```
   ASO-EDS-Autofix-Users
   ```

   >[!IMPORTANT]
   >
   > Der Gruppenname muss exakt übereinstimmen, einschließlich der Groß-/Kleinschreibung. Die Groß-/Kleinschreibung wird beachtet, sodass eine andere Schreibweise oder Groß-/Kleinschreibung (z. B. `ASO-EDS-Autofix-users`) nicht funktioniert. Benennen Sie die Gruppe nach dem Erstellen nicht um.

1. Klicken Sie auf **Speichern**.

   ![Erstellen Sie in der Adobe Admin Console ein Dialogfeld für eine neue Benutzergruppe, wobei das Feld „Name der Benutzergruppe“ auf „ASO-EDS-Autofix-Users“ eingestellt ist](./assets/trial/create-user-group.png){align="center"}

1. Öffnen Sie die neue Gruppe und wählen Sie **Benutzer hinzufügen** aus.
1. Geben Sie die E-Mail-Adresse oder den Benutzernamen jeder Person ein, die automatische Korrekturen bereitstellen kann, und wählen Sie dann **Speichern**.

   ![Im Dialogfeld „Benutzer zu dieser Benutzergruppe hinzufügen“ in der Adobe Admin Console](./assets/trial/add-users-to-group.png){align="center"}

Wenn Sie Mitglied der Gruppe sind, ist die Schaltfläche **Für Autor bereitstellen** aktiviert. Wenn Sie noch kein Mitglied sind, wird **Für Autor bereitstellen** mit einer QuickInfo deaktiviert, mit der Sie aufgefordert werden, sich an Ihren Administrator zu wenden, um Sie der Gruppe hinzuzufügen. Nachdem Sie von Ihrem Administrator zur Gruppe hinzugefügt wurden, melden Sie sich ab und wieder bei Sites Optimizer an, damit Ihre Sitzung die neue Gruppenmitgliedschaft annimmt.

## Häufig gestellte Fragen

Im Folgenden finden Sie Antworten auf häufig gestellte Fragen zur AEM Sites Optimizer-Testversion.

+++Was ist AEM Sites Optimizer?

[AEM Sites Optimizer](/help/home.md) ist eine KI-Anwendung, die Probleme auf Ihrer Website erkennt, präskriptive Empfehlungen bereitstellt und Sie bei deren Behebung unterstützt, um die Traffic-Akquise, -Interaktion und -Konversion zu steigern.

+++
+++Wer kann die Testversion nutzen?

AEM Sites-Bestandskundschaft (Edge Delivery Services, Cloud Services und Managed Services).

+++
+++Wie greife ich auf die Testversion zu?

Gehen Sie zu [www.sitesoptimizer.live](http://www.sitesoptimizer.live/) und melden Sie sich mit Ihrer AEM Sites IMS-Organisations-ID an.

+++
+++Kostet die Testversion etwas?

Nein. Diese Testversion steht Bestandskundschaft von AEM Sites kostenlos zur Verfügung.

+++
+++Gibt es ein Ablaufdatum?

Nein. Die Testversion ist nicht zeitlich begrenzt. Die Nutzung ist basierend auf der Anzahl der verfügbaren Arten von Möglichkeiten und Probleme eingeschränkt.
+++
+++Was passiert, nachdem alle Probleme behoben wurden?

Sites Optimizer identifiziert kontinuierlich Probleme, die sich auf Ihre Leistung auswirken. In der kostenlosen Testversion werden Probleme nur monatlich hinzugefügt. Für kontinuierliche Prüfung und Optimierung führen Sie ein Upgrade durch.

+++
+++Wie kann ich auf weitere Möglichkeiten zugreifen?

Führen Sie das Upgrade aus, verwenden Sie die Schaltfläche für den Kontakt mit dem Vertrieb im Produkterlebnis oder senden Sie eine E-Mail an [siteoptimizer-now@adobe.com](mailto:siteoptimizer-now@adobe.com).

+++
+++Ich gehöre zur Gruppe ASO-EDS-Autofix-Users , aber die Bereitstellung für die Autoreninstanz ist immer noch deaktiviert. Was soll ich überprüfen?

Abmelden und wieder anmelden - Die Gruppenmitgliedschaft wird gelesen, wenn Sie sich anmelden. Bestätigen Sie außerdem, dass der Gruppenname exakt `ASO-EDS-Autofix-Users` geschrieben und in Großbuchstaben geschrieben wurde und in derselben Organisation erstellt wurde, zu der die Site gehört.

+++
+++Gilt die Gruppenanforderung ASO-EDS-Autofix-Users für alle Edge Delivery Services-Sites?

Nein. Gilt nur für Test-Sites, die in **Google Drive** oder **SharePoint erstellt**. In **Crosswalk** oder **Dark Alley** erstellte Websites und alle **gebührenpflichtigen**-Websites sind davon nicht betroffen.

+++
+++Sites Optimizer gibt an, dass es nicht auf meine Website zugreifen kann. Was soll ich tun?

Ihre Site befindet sich wahrscheinlich hinter einer Firewall, einem CDN oder einer Sicherheitskonfiguration, die den Scanner blockiert. Zulassungsliste des Benutzeragenten des Scanners (das `Spacecat/1.0`-Token) und der IP-Adressen in Ihrer Sicherheitskonfiguration oder, bei AEM Cloud Service-Sites, in den CDN-Zulassungslisten von Cloud Manager. Wählen Sie dann **Aktualisieren** aus. Siehe [Zugriff von Sites Optimizer auf Ihre Site zulassen](#allow-sites-optimizer-to-access-your-site).

+++

<!--
CARDS
* ./opportunities/core-web-vitals.md
  {title=Core web vitals}
  {image=../assets/common/card-performance.png}
* ./opportunities/missing-alt-text.md
  {title=Missing alt text}
  {image=../assets/common/card-arrows.png}
* ./opportunities/broken-backlinks.md
  {title=Broken backlinks}
  {image=../assets/common/card-arrows.png}
-->

<!-- START CARDS HTML - DO NOT MODIFY BY HAND -->
<div class="columns">
    <div class="column is-half-tablet is-half-desktop is-one-third-widescreen" aria-label="Core web vitals">
        <div class="card" style="height: 100%; display: flex; flex-direction: column; height: 100%;">
            <div class="card-image">
                <figure class="image x-is-16by9">
                    <a href="./opportunities/core-web-vitals.md" title="Core Web Vitals" target="_blank" rel="referrer">
                        <img class="is-bordered-r-small" src="../assets/common/card-performance.png" alt="Core Web Vitals"
                             style="width: 100%; aspect-ratio: 16 / 9; object-fit: cover; overflow: hidden; display: block; margin: auto;">
                    </a>
                </figure>
            </div>
            <div class="card-content is-padded-small" style="display: flex; flex-direction: column; flex-grow: 1; justify-content: space-between;">
                <div class="top-card-content">
                    <p class="headline is-size-6 has-text-weight-bold">
                        <a href="./opportunities/core-web-vitals.md" target="_blank" rel="referrer" title="Core Web Vitals">Core Web Vitals</a>
                    </p>
                    <p class="is-size-6">Erfahren Sie mehr über die Möglichkeit bei Core Web Vitals und darüber, wie Sie sie zur Verbesserung der Traffic-Akquise nutzen können.</p>
                </div>
                <a href="./opportunities/core-web-vitals.md" target="_blank" rel="referrer" class="spectrum-Button spectrum-Button--outline spectrum-Button--primary spectrum-Button--sizeM" style="align-self: flex-start; margin-top: 1rem;">
                    <span class="spectrum-Button-label has-no-wrap has-text-weight-bold">Weitere Informationen</span>
                </a>
            </div>
        </div>
    </div>
    <div class="column is-half-tablet is-half-desktop is-one-third-widescreen" aria-label="Missing alt text">
        <div class="card" style="height: 100%; display: flex; flex-direction: column; height: 100%;">
            <div class="card-image">
                <figure class="image x-is-16by9">
                    <a href="./opportunities/missing-alt-text.md" title="Fehlender Alternativtext" target="_blank" rel="referrer">
                        <img class="is-bordered-r-small" src="../assets/common/card-arrows.png" alt="Fehlender Alternativtext"
                             style="width: 100%; aspect-ratio: 16 / 9; object-fit: cover; overflow: hidden; display: block; margin: auto;">
                    </a>
                </figure>
            </div>
            <div class="card-content is-padded-small" style="display: flex; flex-direction: column; flex-grow: 1; justify-content: space-between;">
                <div class="top-card-content">
                    <p class="headline is-size-6 has-text-weight-bold">
                        <a href="./opportunities/missing-alt-text.md" target="_blank" rel="referrer" title="Fehlender Alternativtext">Fehlender Alternativtext</a>
                    </p>
                    <p class="is-size-6">Erfahren Sie mehr über die Möglichkeit für fehlenden Alternativtext und darüber, wie Sie sie zur Verbesserung der Interaktion auf Ihrer Website verwenden können.</p>
                </div>
                <a href="./opportunities/missing-alt-text.md" target="_blank" rel="referrer" class="spectrum-Button spectrum-Button--outline spectrum-Button--primary spectrum-Button--sizeM" style="align-self: flex-start; margin-top: 1rem;">
                    <span class="spectrum-Button-label has-no-wrap has-text-weight-bold">Weitere Informationen</span>
                </a>
            </div>
        </div>
    </div>
    <div class="column is-half-tablet is-half-desktop is-one-third-widescreen" aria-label="Broken backlinks">
        <div class="card" style="height: 100%; display: flex; flex-direction: column; height: 100%;">
            <div class="card-image">
                <figure class="image x-is-16by9">
                    <a href="./opportunities/broken-backlinks.md" title="Fehlerhafte Backlinks" target="_blank" rel="referrer">
                        <img class="is-bordered-r-small" src="../assets/common/card-arrows.png" alt="Fehlerhafte Backlinks"
                             style="width: 100%; aspect-ratio: 16 / 9; object-fit: cover; overflow: hidden; display: block; margin: auto;">
                    </a>
                </figure>
            </div>
            <div class="card-content is-padded-small" style="display: flex; flex-direction: column; flex-grow: 1; justify-content: space-between;">
                <div class="top-card-content">
                    <p class="headline is-size-6 has-text-weight-bold">
                        <a href="./opportunities/broken-backlinks.md" target="_blank" rel="referrer" title="Fehlerhafte Backlinks">Fehlerhafte Backlinks</a>
                    </p>
                    <p class="is-size-6">Erfahren Sie mehr über die Möglichkeit bei fehlerhaften Backlinks und darüber, wie Sie sie zur Verbesserung der Traffic-Akquise nutzen können.</p>
                </div>
                <a href="./opportunities/broken-backlinks.md" target="_blank" rel="referrer" class="spectrum-Button spectrum-Button--outline spectrum-Button--primary spectrum-Button--sizeM" style="align-self: flex-start; margin-top: 1rem;">
                    <span class="spectrum-Button-label has-no-wrap has-text-weight-bold">Weitere Informationen</span>
                </a>
            </div>
        </div>
    </div>
</div>
<!-- END CARDS HTML - DO NOT MODIFY BY HAND -->
