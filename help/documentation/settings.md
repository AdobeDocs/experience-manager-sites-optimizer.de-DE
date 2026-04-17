---
title: Sites Optimizer-Einstellungen
description: Erfahren Sie, wie Sie die Einstellungen für Sites Optimizer konfigurieren und mit anderen Tools integrieren.
source-git-commit: b71d5510162864ee76931cf754164ea637cadd92
workflow-type: tm+mt
source-wordcount: '749'
ht-degree: 12%

---


# Sites Optimizer-Einstellungen

![Sites Optimizer-Einstellungen](./assets/settings/hero.png){align="center"}

Sites Optimizer-Einstellungen sind der zentrale Knotenpunkt für die Konfiguration Ihres Sites Optimizer-Erlebnisses.

## Google Search Console

![Sites Optimizer-Einstellungen für Google Search Console](./assets/settings/google-search-console.png){align="center"}

Der Connector für die Google Search Console-Einstellungen in AEM Sites Optimizer ermöglicht die Analyse von wichtigen SEO-Metriken wie Platzierungen in Suchergebnissen, Klickraten und Core Web Vitals. Durch das Aufrechterhalten der Verbindung mit der Google Search Console können Sie die JSON-Analyse nutzen, um Optimierungsmöglichkeiten zu entdecken und die Site-Leistung zu verbessern.

Für die Einrichtung dieses Connectors benötigen Sie Anmeldeinformationen mit Administratorzugriff auf die Google Search Console für die Domain.

## Verbindung mit AEM Sites herstellen

In diesem Handbuch wird beschrieben, wie Sie Ihre bestehende Edge Delivery Services-Site (EDS) mit AEM Sites Optimizer verbinden. Bevor Sie beginnen, stellen Sie sicher, dass Ihre EDS-Site bereits eingerichtet ist und funktioniert - diese Verbindung ist speziell für den Zugriff von AEM Sites Optimizer auf Ihre Inhalte vorgesehen.

Die Verbindung erfordert zwei Schritte:

1. Geben Sie Ihre Code-Repository-URL und Inhaltsquellen-URL an.
2. Gewähren Sie AEM Sites Optimizer Zugriff auf Ihre Inhaltsquelle.

### Schritt 1: Verknüpfen des Code-Repositorys und der Inhaltsquelle

Wechseln Sie in AEM Sites Optimizer zu **Einstellungen → Verbindung mit AEM Sites herstellen** und geben Sie Folgendes ein:

- **Code-Repository**URL - die GitHub-URL Ihrer EDS-Site, z. B.:
  `https://github.com/owner/repo`

- **Content Source URL** - die URL des SharePoint-Ordners oder Google Drive-Ordners, der Ihre EDS-Site unterstützt, z. B.:
  `https://drive.google.com/drive/folders/...` oder `https://myorg.sharepoint.com/...`

Sobald Sie die Content Source-URL eingeben, erkennt AEM Sites Optimizer Ihren Content-Quelltyp und zeigt die entsprechenden Zugriffsanweisungen unten an.

### Schritt 2: Gewähren des Zugriffs auf Ihre Inhaltsquelle

Befolgen Sie den Abschnitt, der Ihrer Inhaltsquelle entspricht.

#### SharePoint - Adobe Domain

![Dialogfeld „Verbindung mit AEM Sites herstellen“, in dem keine Aktion für die Adobe SharePoint-Domain erforderlich ist](./assets/settings/connect-content-and-drive.png){align="center"}

Wenn Ihre Content Source-URL die Adobe SharePoint-Domain verwendet, sind keine weiteren Maßnahmen erforderlich. Der Zugriff ist bereits konfiguriert. Klicken Sie **Speichern**, um die Verbindung abzuschließen.

#### SharePoint - Benutzerdefinierte Domain

Wenn Ihre Content Source-URL die eigene SharePoint-Domain Ihres Unternehmens verwendet, müssen Sie eine Azure-Anwendung registrieren und ihre Anmeldeinformationen für AEM Sites Optimizer angeben.

##### Voraussetzungen

- Berechtigung zur Registrierung von Anwendungen im Azure-Portal oder ein Kontakt, der die Anwendungen in Ihrem Namen registrieren kann.
- Mandantenadministratorrechte, um die API-Zustimmung zu erteilen, oder ein Administrator, der die API-Zustimmung für Sie genehmigen kann.

##### Schritt 2a — Registrieren einer Anwendung in Azure

1. Wechseln Sie zum **Azure-Portal → Microsoft Entra ID → App-Registrierungen → neue Registrierung**.
2. Geben Sie ihm einen Namen, z. B.: `AEM Sites Optimizer`.
3. Belassen Sie alle anderen Standardeinstellungen und klicken Sie auf **Registrieren**.
4. Beachten Sie auf **Seite**&#x200B;Übersicht“ Folgendes:
   - **Anwendungs-(Client-)ID**
   - **Verzeichnis-(Mandanten-)ID**

##### Schritt 2b — API-Berechtigungen hinzufügen

1. Navigieren Sie zu **API-Berechtigungen → Hinzufügen einer Berechtigung → Microsoft Graph → Anwendungsberechtigungen**.
2. Fügen Sie sowohl Folgendes hinzu:
   - `Sites.Selected` - Zugriff auf bestimmte SharePoint-Websitesammlungen im Umfang.
   - `Files.SelectedOperations.Selected` - Dateizugriff ohne angemeldeten Benutzer.
3. Klicken Sie **Administratorzustimmung erteilen** für beide.

![Azure-API-Berechtigungen, die „Sites.Selected“ und „Files.SelectedOperations.Selected“ anzeigen, werden erteilt](./assets/settings/app-permissions.png){align="center"}

>[!NOTE]
>
>Für die Erteilung der Administratorzustimmung sind Administratorrechte des Mandanten erforderlich. Wenn dies nicht der Fall ist, bitten Sie Ihren IT- oder Azure-Administrator, diesen Schritt abzuschließen, bevor Sie fortfahren.

##### Schritt 2c - Erstellen eines Client-Geheimnisses

Seite mit ![Azure-Zertifikaten und -Geheimnissen für die App-Registrierung](./assets/settings/create-credentials.png){align="center"}

1. Navigieren Sie zu **Zertifikate und Geheimnisse → neuen Client-Geheimnis**.
2. Legen Sie eine Beschreibung und ein Ablaufdatum fest und klicken Sie dann auf **Hinzufügen**.
3. Kopieren Sie den geheimen Wert sofort - er wird nur einmal angezeigt.

##### Schritt 2d - Gewähren Sie der App Zugriff auf Ihre SharePoint-Site

Sie können der App Zugriff gewähren, indem Sie Microsoft Graph Explorer, PowerShell oder direkte Graph-API-Aufrufe verwenden.

Navigieren Sie zu [Microsoft Graph Explorer](https://developer.microsoft.com/graph/graph-explorer), melden Sie sich mit Ihrem Microsoft-Konto an und führen Sie die folgenden Anfragen aus:

1. Site-ID suchen:

```
GET https://graph.microsoft.com/v1.0/sites/{tenant}.sharepoint.com:/sites/{site-name}
```

1. Kopieren Sie die `id` aus der Antwort und gewähren Sie dann Zugriff auf Site-Ebene:

```
POST https://graph.microsoft.com/v1.0/sites/{siteId}/permissions
```

Textkörper:

```json
{
  "roles": ["write"],
  "grantedToIdentities": [{
    "application": {
      "id": "{your-client-id}",
      "displayName": "{Your app name}"
    }
  }]
}
```

##### Schritt 2e — Anmeldedaten in AEM Sites Optimizer eingeben

![Dialogfeld „Verbindung mit AEM Sites herstellen“ mit den Feldern zu den SharePoint-Anmeldeinformationen](./assets/settings/add-sharepoint-credentials.png){align="center"}

Zurück im **Mit AEM Sites verbinden** geben Sie Folgendes unter **Content Repository-Verbindung über SharePoint** ein:

- **Mandanten-ID (Azure AD)** - von der App-Registrierung → Übersicht.
- **Client-ID (App-Registrierung)** - von der App-Registrierung → Übersicht.
- **Client-Geheimnis** - in Schritt 2c erstellt.

Klicken Sie auf **Verbindung überprüfen**, um den Zugriff zu bestätigen, und klicken Sie dann auf **Speichern**.

#### Google-Laufwerk

![Dialogfeld „Verbindung mit AEM Sites herstellen“ mit dem Google Drive-Dienstkonto für den Freigabezugriff](./assets/settings/validate-eds-google.png){align="center"}

1. Klicken Sie in Google Drive mit der rechten Maustaste auf den Ordner, der Ihre EDS-Site unterstützt, und wählen Sie **Freigeben**.
2. Geben Sie **Feld „Personen und Gruppen hinzufügen** die E-Mail-Adresse des Service-Kontos ein, die im Dialogfeld **Mit AEM Sites verbinden** angezeigt wird:
   `experience-success-studio@helix-225321.iam.gserviceaccount.com`
3. Setzen Sie die Berechtigungsstufe auf **Editor**.
4. Deaktivieren Sie **Personen benachrichtigen** und klicken Sie auf **Freigeben**.

Nachdem die Freigabe abgeschlossen ist, klicken Sie **Dialogfeld auf „Verbindung**&quot; und anschließend auf **Speichern**.
