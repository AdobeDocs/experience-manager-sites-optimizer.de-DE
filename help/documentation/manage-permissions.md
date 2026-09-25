---
title: Verwalten von Benutzerberechtigungen
description: Erfahren Sie, wie Sie den Benutzerzugriff und die Funktionen in AEM Sites Optimizer verwalten.
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
topic_v2:
  - id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
    internal-label: Optimization
source-git-commit: c372679073253df686a77daccb6cb548622181f5
workflow-type: tm+mt
source-wordcount: '1362'
ht-degree: 1%
---
# Verwalten von Benutzerberechtigungen

Steuern Sie, wer auf eine Site in Sites Optimizer zugreifen kann und was damit möglich ist. Der Zugriff basiert auf einer kleinen Anzahl unabhängiger *Funktionen* - Anzeigen, Bearbeiten, Bereitstellen, Konfigurieren und Verwalten von Benutzern -, die Sie jeder Person gewähren.

Zugriff ist **additiv**: Die Berechtigungen einer Person sind die Summe von allem, was ihr gewährt wurde. Es gibt kein „Verweigern“, daher widersprechen sich Zuschüsse nie oder löschen sich gegenseitig aus. Um jemandem weniger Zugriff zu gewähren, entfernen Sie eine Grant-ID, anstatt zu versuchen, sie zu überschreiben.

Um den Zugriff zu verwalten **öffnen Sie die Registerkarte** Berechtigungen“ (das Sperrsymbol im linken Navigationsbereich) und wählen Sie dann die Site aus, die Sie verwalten möchten.

![Die Seite „Berechtigungen“ in Sites Optimizer](./assets/settings/permissions-page.png){align="center"}

## Gewähren des Zugriffs

Es gibt zwei Möglichkeiten, wie eine Person Zugriff erhalten kann, und sie arbeiten zusammen:

- **Organisationsweiter Zugriff** - Wird von Ihrem Adobe-Organisationsadministrator in der [Adobe Admin Console zugewiesen](https://adminconsole.adobe.com/). Dies gilt für alle Sites in Ihrem Unternehmen. Nutzen Sie es für Personen, die überall den gleichen Zugang benötigen.
- **Zugriff auf Site-Ebene** - wird in Sites Optimizer auf der Registerkarte **Berechtigungen** zugewiesen. Sie gilt für eine einzelne Site und kann so breit oder so schmal wie nötig sein. Es ist kein Zugriff auf Admin Console erforderlich.

>[!NOTE]
>
>Die beiden Schichten addieren sich. Jemand mit organisationsweitem Ansichtszugriff, dem auch die Berechtigung „Bearbeiten“ auf einer Website gewährt wird, kann jede Website anzeigen und diese bearbeiten. Damit eine Person auf eine einzelne Site beschränkt bleibt, stellen Sie sicher, dass sie nicht auch eine organisationsweite Rolle innehat.

### Unternehmensweite Rollen (Admin Console)

Der organisationsweite Zugriff erfolgt über eine von zwei **AEM Sites Optimizer**-Produktrollen, die in der [Adobe Admin Console zugewiesen ](https://adminconsole.adobe.com/):

- **ASO Manager** - Vollständiger Zugriff auf jede Website, einschließlich **Benutzer verwalten**. Ein Manager kann die Registerkarte **Berechtigungen** für jede Site öffnen und anderen Zugriff zuweisen.
- **ASO User** — Nur-Ansicht-Zugriff auf jede Website. Keine Änderungen und keine Benutzerverwaltung.

Um eine Rolle zuzuweisen, müssen Sie ein **Systemadministrator** für das Unternehmen oder ein (**)** für AEM Sites Optimizer sein.

1. Melden Sie sich bei der [Adobe Admin Console](https://adminconsole.adobe.com/) an.
1. Navigieren Sie zu **Produkte** und wählen Sie **AEM Sites Optimizer** aus.
1. Öffnen Sie die **Benutzer** und fügen Sie den Benutzer per E-Mail hinzu (oder wählen Sie einen vorhandenen Benutzer aus).
1. Klicken Sie auf **+** (Hinzufügen), um ein Produktprofil hinzuzufügen, und wählen Sie dann das Produktprofil aus.

   ![Auswählen des Produktprofils für einen Benutzer in der Adobe Admin Console](./assets/settings/permissions-admin-console-product-profile.png){align="center"}

1. Klicken Sie auf **Weiter**.
1. Wählen Sie die Rolle aus **ASO Manager** für Vollzugriff oder **ASO User** für Nur-Ansicht-Zugriff - und klicken Sie dann auf **Anwenden**.

   ![Auswählen der Rolle „ASO-Manager“ in der Adobe Admin Console](./assets/settings/permissions-admin-console-aso-manager-role.png){align="center"}

   ![Auswählen der ASO-Benutzerrolle in der Adobe Admin Console](./assets/settings/permissions-admin-console-aso-user-role.png){align="center"}

Weitere Informationen zum Hinzufügen von Benutzern finden Sie unter [Onboarden von Benutzern](setup/onboard-users.md).

>[!IMPORTANT]
>
>Nur ein Organisations-Admin kann organisationsweit **Benutzer verwalten** gewähren. Ein Mitglied, das **Benutzer verwalten** auf einer Site hat, kann Zugriff auf diese Site zuweisen, aber keinen organisationsweiten **ASO-Manager** erstellen.

## Funktionsstufen

Jede Funktion steuert eine Art von Aktion. Sie sind unabhängig, z. B. können Sie die Bereitstellung ohne Bearbeitung gewähren.

| Funktion | Was es erlaubt | Was nicht zulässig ist |
|---|---|---|
| Anzeigen | Anzeigen der Daten der Website - Chancen, Vorschläge, Fehlerbehebungen, Berichte und Konfiguration - ohne Änderungen. | Jede Änderung. |
| Bearbeiten | Gelegenheiten und Vorschläge erstellen und ändern (was sollte sich ändern). | Veröffentlichen von Änderungen, Ändern von Einstellungen oder Verwalten von Benutzern. |
| Bereitstellen | Fehlerbehebungen live auf der Site veröffentlichen und zurücksetzen. | Verwalten von Benutzern. |
| Konfigurieren | Ändern Sie die Einstellungen und Verbindungen der Site. | Veröffentlichen von Fehlerbehebungen oder Verwalten von Benutzern. |
| Verwalten von Benutzenden | Gewähren oder widerrufen Sie den Zugriff anderer Mitglieder auf die Website. | Verwalten einer Site, auf die die Person noch keinen Zugriff hat. |

>[!NOTE]
>
>**Ansicht ist immer enthalten.** Jede Grant-Aktion enthält automatisch „Anzeigen“ - Sie können etwas, das Sie nicht sehen können, nicht verwalten, konfigurieren, bearbeiten oder bereitstellen. Aus diesem Grund kann View nicht eigenständig entfernt werden. Um den Zugriff einer Person vollständig zu entfernen, entfernen Sie das Mitglied (siehe [Bearbeiten oder Entfernen eines Mitglieds](#edit-or-remove-a-member) unten), anstatt jede Funktion zu deaktivieren.

## Zugriffsbereich auf Opportunity-Typen erweitern

Auf einer einzelnen Site können Sie die Ansicht, Bearbeitung und Bereitstellung für **bestimmte Opportunity-Typen** (z. B. Core Web Vitals oder fehlerhafte interne Links) anstelle der gesamten Site gewähren. Auf diese Weise kann eine Person Core Web Vitals bearbeiten, während nur alles andere angezeigt wird.

- **Anzeigen**, **Bearbeiten** und **Bereitstellen** können auf einen oder mehrere Opportunity-Typen oder **Alle** Opportunity-Typen angewendet werden.
- **Konfigurieren** und **Benutzer verwalten** gelten immer für die gesamte Site - sie können nicht auf einen Opportunity-Typ beschränkt sein.

Jede in den Umfang einbezogene Finanzhilfe wird als eigene Zeile für das Mitglied mit einer Spalte **Gilt für** mit dem Opportunity-Typ, **Alle** oder **Site-Wide** angezeigt.

>[!CAUTION]
>
>Der Umfang beschränkt nur *, was* Gewährt - er entfernt nie den Zugriff, den ein anderer Gewährt gewährt. Wenn eine Person auch über organisationsweiten Zugriff verfügt oder eine **Alle**-Typ-Gewährung verfügt, gilt dieser breitere Zugriff weiterhin. Um jemanden wirklich auf bestimmte Opportunity-Typen zu beschränken, stellen Sie sicher, dass er nicht auch eine breitere Rolle oder eine **All**-types-Förderung innehat.

## Mitglied hinzufügen

1. Öffnen Sie die **Berechtigungen** (das Sperrsymbol im linken Navigationsbereich) und wählen Sie die Site aus.
1. Klicken Sie **Mitglieder hinzufügen**.
1. Nach Name oder E-Mail suchen und eine oder mehrere Personen auswählen.
1. Wählen Sie die **Opportunity-Typen** für die der Zugriff gilt (oder **Alle**), und wählen Sie dann die zu gewährenden Funktionen aus.
1. Klicken Sie auf **Hinzufügen**.

## Mitglied bearbeiten oder entfernen

In der **Mitglieder** Tabelle:

- Klicken Sie **Funktionen bearbeiten** in der Zeile eines Mitglieds, um zu ändern, was es tun kann. Wenn Sie ein vorhandenes Grant bearbeiten, bleibt sein Opportunity-Typ unverändert - Sie ändern nur die Funktionen und mindestens eine Funktion muss ausgewählt bleiben.
- Klicken Sie **Entfernen**, um dem Abonnenten den Zugriff auf die Website vollständig zu entziehen.

>[!NOTE]
>
>Das Ändern von Funktionen und das Entfernen eines Mitglieds sind unterschiedliche Aktionen. Um allen Zugriff zu entziehen, verwenden Sie **Entfernen** - Sie können dies nicht tun, indem Sie die Option „Funktionen“ deaktivieren, da eine Grant-ID mindestens eine Funktion beibehalten muss (und die Ansicht immer beibehalten wird).

## Wer Berechtigungen verwalten kann

Die **Berechtigungen** für eine Site ist verfügbar für:

- Mitglieder mit der Funktion **Benutzer verwalten** auf dieser Website und
- Organisationsadministratoren (ein ASO-Manager).

Mitglieder ohne **Benutzer verwalten** sehen eine Meldung, dass sie nicht über die Berechtigung zum Verwalten des Zugriffs für diese Website verfügen.

## Aktivieren der Benutzer- und Zugriffsverwaltung

Die Benutzer- und Zugriffsverwaltung wird durch eine Einstellung für Ihre Organisation gesteuert. Sie können den Zugriff vor dem Aktivieren zuweisen, aber er wird nur **erzwungen** wenn die Einstellung aktiviert ist.

Wenn es noch nicht aktiviert ist, werden auf der Registerkarte **Berechtigungen** ein Banner angezeigt, in dem Sie aufgefordert werden, Ihr Konto-Team zu kontaktieren. Wenden Sie sich an Ihr Sites Optimizer-Account-Team, um es einzuschalten.

>[!NOTE]
>
>Bis die Benutzer- und Zugriffsverwaltung aktiviert ist, werden die von Ihnen zugewiesenen Berechtigungen gespeichert, aber nicht erzwungen.

## Einrichten des Zugriffs vor der Durchsetzung

Sie müssen nicht warten, bis die Durchsetzung beginnt, Zugriff zuzuweisen. Auch wenn die Benutzer- und Zugriffsverwaltung immer noch **Aus**, können Benutzer mit der Rolle **ASO Manager** die Registerkarte **Berechtigungen** öffnen und anderen Benutzern Sites und Funktionen zuweisen.

Auf diese Weise können Sie den richtigen Zugriff für alle im Voraus vorbereiten. Wenn die Durchsetzung später aktiviert wird, haben Ihre Benutzer bereits den Zugriff, den sie benötigen, sodass niemand unerwartet ausgeschlossen wird.

>[!IMPORTANT]
>
>Wenn die Durchsetzung deaktiviert ist, ist die Registerkarte **Berechtigungen** nur für Benutzende von **ASO Manager** verfügbar. Richten Sie zunächst den Zugriff für alle Benutzer ein und aktivieren Sie dann die Durchsetzung.

## Häufig gestellte Fragen

**Benötigen Mitglieder auf Site-Ebene eine Admin Console-Rolle?**

Nein. Der Zugriff auf Site-Ebene wird vollständig innerhalb von Sites Optimizer auf der Registerkarte **Berechtigungen** gewährt. In der Admin Console werden nur organisationsweite Rollen zugewiesen.

**Was passiert, wenn jemand sowohl unternehmensweiten als auch Standortzugriff hat?**

Beides gilt. Ihr tatsächlicher Zugang ist die Kombination aus beidem. Finanzhilfen stehen nie im Konflikt, da kein Finanzhilfeempfänger den Zugriff verweigern kann.

**Warum kann ein Mitglied mit „Benutzer verwalten“ keinen organisationsweiten Manager erstellen?**

Das Erstellen einer organisationsweiten Rolle ist eine Admin Console-Aktion. Ein Mitglied mit **Benutzer verwalten** kann Zugriff auf seine eigene Site zuweisen, aber nur ein Organisationsadministrator kann organisationsweite Rollen gewähren.

**Wie kann ich einer Person den Zugriff auf eine Website entziehen?**

Entfernen Sie die Gewährung auf der Registerkarte **Berechtigungen** . Dies unterscheidet sich von den Bearbeitungsfunktionen, bei denen immer mindestens eine Funktion verbleiben muss.

**Kann ich eine Person auf bestimmte Opportunity-Typen beschränken?**

Ja - Ansicht, Bearbeitung oder Bereitstellung für bestimmte Opportunity-Typen anstelle von &quot;**&quot;**. Da der Zugriff additiv ist, wird dies nur wirksam, wenn die Person nicht auch über organisationsweiten Zugriff oder eine **Alle**-Gewährungstypen verfügt.
