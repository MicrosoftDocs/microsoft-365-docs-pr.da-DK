---
title: Slå vedhæftede Pengeskab til for SharePoint, OneDrive og Microsoft Teams
f1.keywords:
- NOCSH
ms.author: tracyp
author: msfttracyp
manager: dansimp
audience: ITPro
ms.topic: how-to
ms.date: ''
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.assetid: 07e76024-0c80-40dc-8c48-1dd0d0f863cb
ms.collection:
- M365-security-compliance
- SPO_Content
description: Administratorer kan lære, hvordan du aktiverer Pengeskab Vedhæftede filer for SharePoint, OneDrive og Microsoft Teams, herunder hvordan du kan angive beskeder for registrerede filer.
ms.custom:
- seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 6501097251f4001c58a651db7ddb34bc623e9b0a
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/12/2022
ms.locfileid: "63593802"
---
# <a name="turn-on-safe-attachments-for-sharepoint-onedrive-and-microsoft-teams"></a>Slå vedhæftede Pengeskab til for SharePoint, OneDrive og Microsoft Teams

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Microsoft Defender til Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Microsoft Defender til Office 365 til SharePoint, OneDrive og Microsoft Teams beskytter din organisation mod utilsigtet deling af skadelige filer. Du kan finde flere oplysninger [Pengeskab vedhæftede filer for SharePoint, OneDrive og Microsoft Teams](mdo-for-spo-odb-and-teams.md).

Denne artikel indeholder trinnene til at aktivere og konfigurere Pengeskab vedhæftede filer til SharePoint, OneDrive og Microsoft Teams.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Hvad har du brug for at vide, før du begynder?

- Du åbner Microsoft 365 Defender på <https://security.microsoft.com>. For at gå direkte til **Pengeskab vedhæftede filer skal** du bruge <https://security.microsoft.com/safeattachmentv2>.

- Hvis du vil aktivere Pengeskab Vedhæftede filer for SharePoint, OneDrive og Microsoft Teams, skal du være medlem af rollegrupperne Organisationsadministration eller Sikkerhedsadministrator i Microsoft 365 Defender-portalen.  Du kan finde flere [oplysninger i Tilladelser i Microsoft 365 Defender portal](permissions-microsoft-365-security-center.md).

- Hvis du SharePoint bruge Online PowerShell til at forhindre folk i at downloade skadelige filer, skal du være medlem af [rollerne Global administrator](/azure/active-directory/roles/permissions-reference#global-administrator) eller [SharePoint-administrator](/azure/active-directory/roles/permissions-reference#sharepoint-administrator) i Azure AD.

- Kontrollér, at overvågningslogføring er aktiveret for organisationen. Du kan finde flere oplysninger [i Slå søgning i overvågningslog til eller fra](../../compliance/turn-audit-log-search-on-or-off.md).

- Det kan tage op til 30 minutter, før indstillingerne træder i kraft.

## <a name="step-1-use-the-microsoft-365-defender-portal-to-turn-on-safe-attachments-for-sharepoint-onedrive-and-microsoft-teams"></a>Trin 1: Brug Microsoft 365 Defender til at slå vedhæftede Pengeskab til for SharePoint, OneDrive og Microsoft Teams

1. I portalen Microsoft 365 Defender på skal du <https://security.microsoft.com>gå til Politikker **& regler** \>  \> for **trusselspolitikker Pengeskab** Vedhæftede filer i **sektionen** Politikker. For at gå direkte til **Pengeskab vedhæftede filer skal** du bruge <https://security.microsoft.com/safeattachmentv2>.

2. Klik på **Pengeskab globale indstillinger** på siden **Vedhæftede filer**.

3. I pop **op-sektionen** Globale indstillinger, der vises, skal du gå til **sektionen Beskyt filer SharePoint, OneDrive og Microsoft Teams** Filer.

   Flyt til **/fra-knappen Slå Defender Office 365 for SharePoint, OneDrive og Microsoft Teams** til højre ![for Til.](../../media/scc-toggle-on.png) for at slå vedhæftede Pengeskab til for SharePoint, OneDrive og Microsoft Teams.

   Klik på **Gem**, når du er færdig.

### <a name="use-exchange-online-powershell-to-turn-on-safe-attachments-for-sharepoint-onedrive-and-microsoft-teams"></a>Brug Exchange Online PowerShell til at Pengeskab vedhæftede filer til SharePoint, OneDrive og Microsoft Teams

Hvis du hellere vil bruge PowerShell til at aktivere Pengeskab Vedhæftede filer for SharePoint, OneDrive og Microsoft Teams, skal du oprette forbindelse til [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell) og køre følgende kommando:

```powershell
Set-AtpPolicyForO365 -EnableATPForSPOTeamsODB $true
```

Du kan finde detaljerede oplysninger om syntaks og [parameter i Set-AtpPolicyForO365](/powershell/module/exchange/set-atppolicyforo365).

## <a name="step-2-recommended-use-sharepoint-online-powershell-to-prevent-users-from-downloading-malicious-files"></a>Trin 2: (Anbefales) Brug SharePoint Online PowerShell til at forhindre brugere i at hente skadelige filer

Som standard kan brugerne ikke åbne, flytte,<sup>\*</sup> kopiere eller dele skadelige filer, der registreres af Pengeskab Vedhæftede filer til SharePoint, OneDrive og Microsoft Teams. De kan dog slette og downloade skadelige filer.

<sup>\*</sup> Hvis brugerne går til **Administrer adgang**, er **indstillingen** Del stadig tilgængelig.

For at forhindre brugere i at hente skadelige filer skal [du oprette forbindelse SharePoint Online PowerShell](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online) og køre følgende kommando:

```powershell
Set-SPOTenant -DisallowInfectedFileDownload $true
```

**Bemærkninger**:

- Denne indstilling påvirker både brugere og administratorer.
- Personer kan stadig slette skadelige filer.

Du kan finde detaljerede oplysninger om syntaks og parameter [i Set-SPOTenant](/powershell/module/sharepoint-online/Set-SPOTenant).

## <a name="step-3-recommended-use-the-microsoft-365-defender-portal-to-create-an-alert-policy-for-detected-files"></a>Trin 3 (Anbefales) Brug portalen Microsoft 365 Defender til at oprette en beskedpolitik for registrerede filer

Du kan oprette en beskedpolitik, der giver dig og andre administratorer besked, når Pengeskab Vedhæftede filer til SharePoint, OneDrive og Microsoft Teams registrerer en skadelig fil. Hvis du vil have mere at vide om beskeder, skal [du se Beskedpolitikker](../../compliance/alert-policies.md).

1. I portalen Microsoft 365 Defender på skal du <https://security.microsoft.com>gå til **Politikker &** **reglerBeskedpolitik**\>. Hvis du vil gå direkte til siden **med politik for beskeder** , skal du bruge <https://security.microsoft.com/alertpolicies>.

2. Klik på **Ny beskedpolitik** på **siden Beskedpolitik**.

3. Guiden **Ny beskedpolitik** åbnes i et pop op-vindue. På siden **Giv din besked et** navn skal du konfigurere følgende indstillinger:
   - **Navn**: Skriv et entydigt og beskrivende navn. Eksempelvis Skadelige filer i biblioteker.
   - **Beskrivelse**: Skriv en valgfri beskrivelse. Giver f.eks. administratorer besked, når der registreres skadelige filer i SharePoint Online, OneDrive eller Microsoft Teams.
   - **Alvorsgrad**: **Vælg** **Lav,** Mellem **eller** Høj på rullelisten.
   - **Kategori**: **Vælg Trusselsadministration** på rullelisten.

   Klik på Næste, når du er **færdig**.

4. Konfigurer **følgende indstillinger på** siden Opret beskedindstillinger:
   - **Hvad vil du have besked om?** sektion \> **Aktivitet er** \> Vælg **Registreret malware i** filen på rullelisten.
   - **Hvordan skal beskeden udløses?** sektion: Lad standardværdien være, **hver gang en aktivitet stemmer overens med reglen** .

   Klik på Næste, når du er **færdig**.

5. På siden **Angiv modtagere skal** du konfigurere følgende indstillinger:
   - **Bekræft, at Send mailbeskeder** er markeret. I feltet **Mailmodtagere skal** du vælge en eller flere globale administratorer, sikkerhedsadministratorer eller sikkerhedslæsere, der skal modtage meddelelser, når der registreres en skadelig fil.
   - **Grænse for daglig besked**: Lad standardværdien **Ingen grænse være** markeret.

   Klik på Næste, når du er **færdig**.

6. Gennemgå **dine indstillinger på** siden Gennemse dine indstillinger. Du kan vælge **Rediger** i hver sektion for at ændre indstillingerne i sektionen. Eller du kan klikke **på** Tilbage eller vælge den bestemte side i guiden.

   I sektionen **Vil du aktivere politikken med det samme?** skal du lade standardværdien Ja være aktiveret **med det** samme.

   Klik på Udfør, når du er **færdig**.

### <a name="use-security--compliance-powershell-to-create-an-alert-policy-for-detected-files"></a>Brug Security & Compliance PowerShell til at oprette en beskedpolitik for registrerede filer

Hvis du hellere vil bruge PowerShell til at oprette den samme beskedpolitik som beskrevet i forrige afsnit, skal du oprette forbindelse til [Security & Compliance Center PowerShell](/powershell/exchange/connect-to-scc-powershell) og køre følgende kommando:

```powershell
New-ActivityAlert -Name "Malicious Files in Libraries" -Description "Notifies admins when malicious files are detected in SharePoint Online, OneDrive, or Microsoft Teams" -Category ThreatManagement -Operation FileMalwareDetected -NotifyUser "admin1@contoso.com","admin2@contoso.com"
```

**Bemærk**! Standardværdien _for alvorsgrad_ er Lav. Hvis du vil angive Mellem eller Høj, skal _du medtage_ parameteren og værdien for Alvorsgrad i kommandoen.

Du kan finde detaljerede oplysninger om syntaks og parameter [i New-ActivityAlert](/powershell/module/exchange/new-activityalert).

### <a name="how-do-you-know-these-procedures-worked"></a>Hvordan ved du, at disse procedurer fungerede?

- Du kan kontrollere, at du har aktiveret Pengeskab Vedhæftede filer for SharePoint, OneDrive og Microsoft Teams, ved at benytte en af følgende fremgangsmåder:

  - I Microsoft 365 Defender-portalen skal du gå til afsnittet Politikker **&** \>  \>  \> regler for sikkerhedspolitikker **Pengeskab** Vedhæftede filer, vælge **Globale** indstillinger og bekræfte værdien af slå **Defender til for Office 365 for SharePoint. OneDrive og Microsoft Teams** indstillinger.

  - I Exchange Online PowerShell skal du køre følgende kommando for at bekræfte egenskabsindstillingen:

    ```powershell
    Get-AtpPolicyForO365 | Format-List EnableATPForSPOTeamsODB
    ```

    Du kan finde detaljerede oplysninger om syntaks og [parameter i Get-AtpPolicyForO365](/powershell/module/exchange/get-atppolicyforo365).

- For at bekræfte, at du har blokeret for overførsel af skadelige filer, skal du åbne SharePoint Online PowerShell og køre følgende kommando for at bekræfte egenskabsværdien:

  ```powershell
  Get-SPOTenant | Format-List DisallowInfectedFileDownload
  ```

  Du kan finde detaljerede oplysninger om syntaks og [parameter i Get-SPOTenant](/powershell/module/sharepoint-online/Set-SPOTenant).

- Benyt en af følgende fremgangsmåder for at bekræfte, at du har konfigureret en politik for påmindelse for registrerede filer:
  - I portalen Microsoft 365 Defender skal du gå til Politikker **& regler** \> **Beskedpolitik**\>, vælge påmindelsespolitikken og kontrollere indstillingerne.
  - I Microsoft 365 Defender Portal PowerShell skal du \<AlertPolicyName\> erstatte med navnet på beskedpolitikken, køre følgende kommando og bekræfte egenskabsværdierne:

    ```powershell
    Get-ActivityAlert -Identity "<AlertPolicyName>"
    ```

    Du kan finde detaljerede oplysninger om syntaks og [parameter i Get-ActivityAlert](/powershell/module/exchange/get-activityalert).

- Brug [statusrapporten for trusselsbeskyttelse](view-email-security-reports.md#threat-protection-status-report) til at få vist oplysninger om registrerede filer i SharePoint, OneDrive og Microsoft Teams. Specifikt kan du bruge visningen Vis **data efter: Visning af indholdsmalware\>**.
