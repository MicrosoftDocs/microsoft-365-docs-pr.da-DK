---
title: Administrer, hvem der kan oprette Microsoft 365 grupper
f1.keywords: NOCSH
ms.author: mikeplum
ms.reviewer: arvaradh
author: MikePlumleyMSFT
manager: serdars
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- m365solution-collabgovernance
search.appverid:
- MET150
ms.assetid: 4c46c8cb-17d0-44b5-9776-005fced8e618
recommendations: false
description: Få mere at vide om, hvordan du styrer, hvilke brugere der kan Microsoft 365 grupper.
ms.openlocfilehash: 4280b6859358580547302ccf9497e8cd1e7ed752
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/12/2022
ms.locfileid: "63590934"
---
# <a name="manage-who-can-create-microsoft-365-groups"></a>Administrer, hvem der kan oprette Microsoft 365 grupper

Som standard kan alle brugere oprette Microsoft 365 grupper. Dette er den anbefalede fremgangsmåde, fordi den giver brugerne mulighed for at starte samarbejdet uden at have brug for hjælp fra it.

Hvis din virksomhed kræver, at du begrænser, hvem der kan oprette grupper, kan du begrænse oprettelse af Microsoft 365-grupper til medlemmer af en bestemt Microsoft 365-gruppe eller sikkerhedsgruppe.

Hvis du er bekymret for brugere, der opretter teams eller grupper, som ikke overholder dine forretningsmæssige standarder, kan du overveje at kræve, at brugerne skal gennemføre et kursus og derefter føje dem til gruppen af tilladte brugere.

Når du begrænser, hvem der kan oprette en gruppe, påvirker det alle tjenester, der er afhængige af grupper til adgang, herunder:

- Outlook
- SharePoint
- Yammer
- Microsoft Teams
- Microsoft Stream
- Planner
- Power BI (klassisk)
- Project til internettet/Roadmap

Trinnene i denne artikel forhindrer ikke medlemmer af bestemte roller i at oprette grupper. Office 365 globale administratorer kan oprette grupper via Microsoft 365 Administration, Planner, Exchange og SharePoint Online. Andre roller kan oprette grupper på begrænset vis, som er angivet nedenfor.

- Exchange Administrator: Exchange Administration, Azure AD
- Partnerniveau 1-support: Microsoft 365 Administration, Exchange Administration, Azure AD
- Partnerniveau 2 Support: Microsoft 365 Administration, Exchange Administration, Azure AD
- Mappeforfattere: Azure AD
- SharePoint administrator: SharePoint Administration, Azure AD
- Teams: Teams Administration, Azure AD
- Brugeradministrator: Microsoft 365 Administration, Azure AD

Hvis du er medlem af en af disse roller, kan du oprette Microsoft 365 Grupper for brugere med begrænset adgang og derefter tildele brugeren rollen som ejer af gruppen.

## <a name="licensing-requirements"></a>Licenskrav

Hvis du vil administrere, hvem der opretter grupper, skal følgende personer have Azure AD Premium tildelt til dem:

- Den administrator, der konfigurerer disse indstillinger for gruppeoprettelse
- De medlemmer af gruppen, der har tilladelse til at oprette grupper

> [!NOTE]
> Se [Tildel eller fjern licenser i Azure Active Directory for at](/azure/active-directory/fundamentals/license-users-groups) få mere at vide om, hvordan du tildeler Azure-licenser.

Følgende personer behøver ikke at Azure AD Premium licenser, der er tildelt dem:

- Personer, der er medlem Microsoft 365 grupper, og som ikke har mulighed for at oprette andre grupper.

## <a name="step-1-create-a-group-for-users-who-need-to-create-microsoft-365-groups"></a>Trin 1: Opret en gruppe for brugere, der har brug for at Microsoft 365 grupper

Der kan kun bruges én gruppe i organisationen til at styre, hvem der kan oprette grupper. Men du kan indlejre andre grupper som medlemmer af denne gruppe.

Administratorer i de roller, der er angivet ovenfor, behøver ikke at være medlemmer af denne gruppe: de bevarer deres mulighed for at oprette grupper.

1. I Administration skal du gå til [siden Grupper](https://admin.microsoft.com/adminportal/home#/groups).

2. Klik på **Tilføj en gruppe**.

3. Vælg den ønskede gruppetype. Husk navnet på gruppen! Du skal bruge den senere.

4. Afslut konfigurationen af gruppen ved at tilføje personer eller andre grupper, som du ønsker skal kunne oprette grupper i din organisation.

Du kan finde detaljerede anvisninger [i Oprette, redigere eller slette en sikkerhedsgruppe i Microsoft 365 Administration](../admin/email/create-edit-or-delete-a-security-group.md).

## <a name="step-2-run-powershell-commands"></a>Trin 2: Kør PowerShell-kommandoer

Du skal bruge prøveversionen af [Azure Active Directory PowerShell til Graph (AzureAD) (](/powershell/azure/active-directory/install-adv2)modulnavn **AzureADPreview**) for at ændre indstillingen for gæsteadgang på gruppeniveau:

- Hvis du ikke har installeret en version af Azure AD PowerShell-modulet før, skal du se Installation af [Azure AD-modulet](/powershell/azure/active-directory/install-adv2?preserve-view=true&view=azureadps-2.0-preview) og følge vejledningen for at installere den offentlige prøveversion.

- Hvis du har 2.0-versionen af Azure AD PowerShell-modulet (AzureAD) installeret, `Uninstall-Module AzureAD` skal du fjerne den ved at køre i din PowerShell-session og derefter installere preview-versionen `Install-Module AzureADPreview`ved at køre .

- Hvis du allerede har installeret prøveversionen, skal du køre for `Install-Module AzureADPreview` at sikre, at det er den nyeste version af dette modul.

Kopiér scriptet nedenfor til en teksteditor, f.eks. Notesblok eller [Windows PowerShell ISE](/powershell/scripting/components/ise/introducing-the-windows-powershell-ise).

Erstat *\<GroupName\>* med navnet på den gruppe, du har oprettet. Eksempel:

`$GroupName = "Group Creators"`

Gem filen som GroupCreators.ps1.

I PowerShell-vinduet skal du gå til den placering, hvor du gemte filen (skriv "CD \<FileLocation\>").

Kør scriptet ved at skrive:

`.\GroupCreators.ps1`

og [logge på med din administratorkonto, når du](../enterprise/connect-to-microsoft-365-powershell.md#step-2-connect-to-azure-ad-for-your-microsoft-365-subscription) bliver bedt om det.

```PowerShell
$GroupName = "<GroupName>"
$AllowGroupCreation = $False

Connect-AzureAD

$settingsObjectID = (Get-AzureADDirectorySetting | Where-object -Property Displayname -Value "Group.Unified" -EQ).id
if(!$settingsObjectID)
{
    $template = Get-AzureADDirectorySettingTemplate | Where-object {$_.displayname -eq "group.unified"}
    $settingsCopy = $template.CreateDirectorySetting()
    New-AzureADDirectorySetting -DirectorySetting $settingsCopy
    $settingsObjectID = (Get-AzureADDirectorySetting | Where-object -Property Displayname -Value "Group.Unified" -EQ).id
}

$settingsCopy = Get-AzureADDirectorySetting -Id $settingsObjectID
$settingsCopy["EnableGroupCreation"] = $AllowGroupCreation

if($GroupName)
{
  $settingsCopy["GroupCreationAllowedGroupId"] = (Get-AzureADGroup -SearchString $GroupName).objectid
} else {
$settingsCopy["GroupCreationAllowedGroupId"] = $GroupName
}
Set-AzureADDirectorySetting -Id $settingsObjectID -DirectorySetting $settingsCopy

(Get-AzureADDirectorySetting -Id $settingsObjectID).Values
```

Den sidste linje i scriptet viser de opdaterede indstillinger:

![Skærmbillede af PowerShell-scriptoutput.](../media/952cd982-5139-4080-9add-24bafca0830c.png)

Hvis du i fremtiden vil ændre, hvilken gruppe der bruges, kan du køre scriptet igen med navnet på den nye gruppe.

Hvis du vil deaktivere begrænsningen for oprettelse af grupper og igen tillade alle brugere at oprette grupper, skal du angive $GroupName til "" og $AllowGroupCreation til "Sand" og køre scriptet igen.

## <a name="step-3-verify-that-it-works"></a>Trin 3: Kontrollér, at det virker

Ændringerne kan tage 30 minutter eller mere, før de træder i kraft. Du kan kontrollere de nye indstillinger ved at gøre følgende:

1. Log på en Microsoft 365 en brugerkonto for en person, der IKKE skal have mulighed for at oprette grupper. Det vil sige, at de ikke er medlem af den gruppe, du har oprettet, eller en administrator.

2. Vælg **flisen Planner** .

3. I Planner skal du vælge **Ny plan** i venstre navigationsrude for at oprette en plan.

4. Du bør få vist en meddelelse om, at oprettelse af planer og grupper er deaktiveret.

Prøv den samme fremgangsmåde igen med et medlem af gruppen.

> [!NOTE]
> Hvis medlemmer af gruppen ikke kan oprette grupper, skal du kontrollere, at de ikke blokeres via deres [OWA-postkassepolitik](/powershell/module/exchange/set-owamailboxpolicy).

## <a name="related-topics"></a>Relaterede emner

[Anbefalinger til planlægning af styring af samarbejde](collaboration-governance-overview.md#collaboration-governance-planning-recommendations)

[Opret din plan for styring af samarbejde](collaboration-governance-first.md)

[Introduktion til Office 365 PowerShell](../enterprise/getting-started-with-microsoft-365-powershell.md)

[Konfigurer selvbetjeningsadministration af grupper i Azure Active Directory](/azure/active-directory/users-groups-roles/groups-self-service-management)

[Set-ExecutionPolicy](/powershell/module/microsoft.powershell.security/set-executionpolicy)

[Azure Active Directory cmdlet'er til konfiguration af gruppeindstillinger](/azure/active-directory/users-groups-roles/groups-settings-cmdlets)
