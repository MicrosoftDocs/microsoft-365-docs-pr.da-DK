---
title: Aktiver Sikre vedhæftede filer i SharePoint, OneDrive og Microsoft Teams
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
description: Administratorer kan få mere at vide om, hvordan du aktiverer Pengeskab Vedhæftede filer for SharePoint, OneDrive og Microsoft Teams, herunder hvordan du angiver beskeder for registrerede filer.
ms.custom:
- seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 55923b13cf47e0309a7246ba43dcb9adaf3c58ff
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/10/2022
ms.locfileid: "66016004"
---
# <a name="turn-on-safe-attachments-for-sharepoint-onedrive-and-microsoft-teams"></a>Aktiver Sikre vedhæftede filer i SharePoint, OneDrive og Microsoft Teams

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Gælder for**
- [Microsoft Defender for Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Microsoft Defender for Office 365 til SharePoint, OneDrive og Microsoft Teams beskytter din organisation mod utilsigtet deling af skadelige filer. Du kan få flere oplysninger [under Pengeskab Vedhæftede filer til SharePoint, OneDrive og Microsoft Teams](mdo-for-spo-odb-and-teams.md).

Denne artikel indeholder trinnene til aktivering og konfiguration af Pengeskab Vedhæftede filer til SharePoint, OneDrive og Microsoft Teams.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Hvad har du brug for at vide, før du begynder?

- Du åbner Microsoft 365 Defender-portalen på <https://security.microsoft.com>. Hvis du vil gå direkte til siden **Pengeskab Vedhæftede filer**, skal du bruge <https://security.microsoft.com/safeattachmentv2>.

- Hvis du vil slå Pengeskab vedhæftede filer til for SharePoint, OneDrive og Microsoft Teams, skal du være medlem af rollegrupperne **Organisationsadministration** eller **Sikkerhedsadministrator** på Microsoft 365 Defender-portalen. Du kan få flere oplysninger [under Tilladelser på Microsoft 365 Defender-portalen](permissions-microsoft-365-security-center.md).

- Hvis du vil bruge SharePoint Online PowerShell til at forhindre personer i at downloade skadelige filer, skal du være medlem af rollerne [Global administrator](/azure/active-directory/roles/permissions-reference#global-administrator) eller [SharePoint Administrator](/azure/active-directory/roles/permissions-reference#sharepoint-administrator) i Azure AD.

- Kontrollér, at logføring af overvågning er aktiveret for din organisation. Du kan finde flere oplysninger under [Slå søgning i overvågningslog til eller fra](../../compliance/turn-audit-log-search-on-or-off.md).

- Der kan gå op til 30 minutter, før indstillingerne træder i kraft.

## <a name="step-1-use-the-microsoft-365-defender-portal-to-turn-on-safe-attachments-for-sharepoint-onedrive-and-microsoft-teams"></a>Trin 1: Brug portalen Microsoft 365 Defender til at aktivere Pengeskab Vedhæftede filer for SharePoint, OneDrive og Microsoft Teams

1. På Microsoft 365 Defender-portalen på <https://security.microsoft.com>skal du gå til **Politikker & regler** \> **Trusselspolitikker** \> **Pengeskab Vedhæftede filer** i afsnittet **Politikker**. Hvis du vil gå direkte til siden **Pengeskab Vedhæftede filer**, skal du bruge <https://security.microsoft.com/safeattachmentv2>.

2. Klik på **Globale indstillinger** på siden **Pengeskab Vedhæftede filer**.

3. Gå til afsnittet **Beskyt filer i SharePoint, OneDrive og Microsoft Teams i** vinduet **Globale indstillinger**.

   Flyt **Defender for Office 365 Slå til for SharePoint, OneDrive, og Microsoft Teams** til/fra-knappen til højre![.](../../media/scc-toggle-on.png) for at aktivere Pengeskab Vedhæftede filer for SharePoint, OneDrive og Microsoft Teams.

   Klik på **Gem**, når du er færdig.

### <a name="use-exchange-online-powershell-to-turn-on-safe-attachments-for-sharepoint-onedrive-and-microsoft-teams"></a>Brug Exchange Online PowerShell til at aktivere Pengeskab Vedhæftede filer for SharePoint, OneDrive og Microsoft Teams

Hvis du hellere vil bruge PowerShell til at aktivere Pengeskab Attachments for SharePoint, OneDrive og Microsoft Teams, skal du [oprette forbindelse til Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell) og køre følgende kommando:

```powershell
Set-AtpPolicyForO365 -EnableATPForSPOTeamsODB $true
```

Du kan finde detaljerede oplysninger om syntaks og parametre [under Set-AtpPolicyForO365](/powershell/module/exchange/set-atppolicyforo365).

## <a name="step-2-recommended-use-sharepoint-online-powershell-to-prevent-users-from-downloading-malicious-files"></a>Trin 2: (Anbefales) Brug SharePoint Online PowerShell til at forhindre brugere i at downloade skadelige filer

Brugerne kan som standard ikke åbne, flytte, kopiere eller dele<sup>\*</sup> skadelige filer, der registreres af Pengeskab Vedhæftede filer til SharePoint, OneDrive og Microsoft Teams. De kan dog slette og downloade skadelige filer.

<sup>\*</sup> Hvis brugerne går til **Administrer adgang**, er indstillingen **Del** stadig tilgængelig.

Hvis du vil forhindre brugere i at downloade skadelige filer, [skal du oprette forbindelse til SharePoint Online PowerShell](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online) og køre følgende kommando:

```powershell
Set-SPOTenant -DisallowInfectedFileDownload $true
```

**Noter**:

- Denne indstilling påvirker både brugere og administratorer.
- Personer kan stadig slette skadelige filer.

Du kan finde detaljerede oplysninger om syntaks og parametre under [Set-SPOTenant](/powershell/module/sharepoint-online/Set-SPOTenant).

## <a name="step-3-recommended-use-the-microsoft-365-defender-portal-to-create-an-alert-policy-for-detected-files"></a>Trin 3 (anbefales) Brug Microsoft 365 Defender-portalen til at oprette en beskedpolitik for registrerede filer

Du kan oprette en beskedpolitik, der giver dig og andre administratorer besked, når Pengeskab Vedhæftede filer for SharePoint, OneDrive og Microsoft Teams registrerer en skadelig fil. Du kan få mere at vide om beskeder under [Beskedpolitikker](../../compliance/alert-policies.md).

1. På portalen Microsoft 365 Defender på <https://security.microsoft.com>skal du gå til **Politikker & regler** \> **Beskedpolitik**. Hvis du vil gå direkte til siden **Beskedpolitik** , skal du bruge <https://security.microsoft.com/alertpolicies>.

2. Klik på **Ny beskedpolitik** på siden **Beskedpolitik**.

3. Guiden **Ny beskedpolitik** åbnes med et fluediagram. Konfigurer følgende indstillinger på siden **Navngiv din besked** :
   - **Navn**: Skriv et entydigt og beskrivende navn. Det kan f.eks. være skadelige filer i biblioteker.
   - **Beskrivelse**: Angiv en valgfri beskrivelse. Giver f.eks. administratorer besked, når der registreres skadelige filer i SharePoint Online, OneDrive eller Microsoft Teams.
   - **Alvorsgrad**: Vælg **Lav**, **Mellem** eller **Høj** på rullelisten.
   - **Kategori**: Vælg **Trusselsadministration** på rullelisten.

   Klik på **Næste**, når du er færdig.

4. Konfigurer følgende indstillinger på siden **Opret beskedindstillinger** :
   - **Hvad vil du advare om?** section \> **Activity er** \> Vælg **Registreret malware i filen** på rullelisten.
   - **Hvordan skal beskeden udløses?** sektion: Behold standardværdien **, hver gang en aktivitet stemmer overens med den valgte regel** .

   Klik på **Næste**, når du er færdig.

5. Konfigurer følgende indstillinger på siden **Angiv dine modtagere** :
   - Kontrollér, at **Send mailmeddelelser** er valgt. I feltet **Mailmodtagere** skal du vælge en eller flere globale administratorer, sikkerhedsadministratorer eller sikkerhedslæsere, der skal modtage en meddelelse, når der registreres en skadelig fil.
   - **Grænse for daglig meddelelse**: Lad standardværdien **Ingen grænse** være markeret.

   Klik på **Næste**, når du er færdig.

6. Gennemse **dine indstillinger på siden Gennemse dine indstillinger** . Du kan vælge **Rediger** i hver sektion for at redigere indstillingerne i sektionen. Du kan også klikke på **Tilbage** eller vælge den specifikke side i guiden.

   I afsnittet **Vil du slå politikken til med det samme?** skal du lade standardværdien **Ja, slå den til med det samme** være markeret.

   Klik på **Udfør**, når du er færdig.

### <a name="use-security--compliance-powershell-to-create-an-alert-policy-for-detected-files"></a>Brug PowerShell til sikkerhed & overholdelse af angivne standarder til at oprette en beskedpolitik for registrerede filer

Hvis du hellere vil bruge PowerShell til at oprette den samme beskedpolitik som beskrevet i forrige afsnit, skal du [oprette forbindelse til Security & Compliance PowerShell](/powershell/exchange/connect-to-scc-powershell) og køre følgende kommando:

```powershell
New-ActivityAlert -Name "Malicious Files in Libraries" -Description "Notifies admins when malicious files are detected in SharePoint Online, OneDrive, or Microsoft Teams" -Category ThreatManagement -Operation FileMalwareDetected -NotifyUser "admin1@contoso.com","admin2@contoso.com"
```

**Bemærk**! _Standardværdien for alvorsgrad_ er Lav. Hvis du vil angive Mellem eller Høj, skal du inkludere parameteren _alvorsgrad_ og værdien i kommandoen.

Du kan finde detaljerede oplysninger om syntaks og parametre under [New-ActivityAlert](/powershell/module/exchange/new-activityalert).

### <a name="how-do-you-know-these-procedures-worked"></a>Hvordan ved du, at disse procedurer virkede?

- Hvis du vil kontrollere, at du har aktiveret Pengeskab Vedhæftede filer for SharePoint, OneDrive og Microsoft Teams, skal du følge et af følgende trin:

  - På Microsoft 365 Defender-portalen skal du gå til afsnittet **Politikker & regler** \> Sektionen \> **Trusselspolitikker politikker** \> **Pengeskab Vedhæftede filer**, vælge **Globale indstillinger** og bekræfte værdien af  **Defender for Office 365 slå til for SharePoint, OneDrive og Microsoft Teams** indstilling.

  - I Exchange Online PowerShell skal du køre følgende kommando for at kontrollere egenskabsindstillingen:

    ```powershell
    Get-AtpPolicyForO365 | Format-List EnableATPForSPOTeamsODB
    ```

    Du kan finde detaljerede oplysninger om syntaks og parametre [under Get-AtpPolicyForO365](/powershell/module/exchange/get-atppolicyforo365).

- Hvis du vil kontrollere, at du har blokeret personer fra at downloade skadelige filer, skal du åbne SharePoint Online PowerShell og køre følgende kommando for at bekræfte egenskabsværdien:

  ```powershell
  Get-SPOTenant | Format-List DisallowInfectedFileDownload
  ```

  Du kan finde detaljerede oplysninger om syntaks og parametre under [Get-SPOTenant](/powershell/module/sharepoint-online/Set-SPOTenant).

- Hvis du vil kontrollere, at du har konfigureret en beskedpolitik for registrerede filer, skal du bruge en af følgende trin:
  - På Microsoft 365 Defender-portalen skal du gå til **Politikker & regler** \> **Beskedpolitik** \> Vælg beskedpolitikken, og kontrollér indstillingerne.
  - I Microsoft 365 Defender portal skal PowerShell erstatte \<AlertPolicyName\> med navnet på beskedpolitikken, køre følgende kommando og kontrollere egenskabsværdierne:

    ```powershell
    Get-ActivityAlert -Identity "<AlertPolicyName>"
    ```

    Du kan finde detaljerede oplysninger om syntaks og parametre under [Get-ActivityAlert](/powershell/module/exchange/get-activityalert).

- Brug [statusrapporten Trusselsbeskyttelse](view-email-security-reports.md#threat-protection-status-report) til at få vist oplysninger om registrerede filer i SharePoint, OneDrive og Microsoft Teams. Du kan især bruge **visningen Vis data efter: Visning af indholdsmalware\>**.
