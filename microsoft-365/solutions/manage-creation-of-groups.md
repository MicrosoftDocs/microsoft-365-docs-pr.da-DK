---
title: Administrer, hvem der kan oprette Microsoft 365-grupper
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
description: Få mere at vide om, hvordan du styrer, hvilke brugere der kan oprette Microsoft 365-grupper.
ms.openlocfilehash: 2136fbf51912e00b7552e687282d4a80688dcd9e
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/29/2022
ms.locfileid: "66493037"
---
# <a name="manage-who-can-create-microsoft-365-groups"></a>Administrer, hvem der kan oprette Microsoft 365-grupper

Som standard kan alle brugere oprette Microsoft 365-grupper. Dette er den anbefalede fremgangsmåde, da den giver brugerne mulighed for at starte et samarbejde uden at have brug for hjælp fra it-medarbejdere.

Hvis din virksomhed kræver, at du begrænser, hvem der kan oprette grupper, kan du begrænse oprettelsen af Microsoft 365-grupper til medlemmerne af en bestemt Microsoft 365-gruppe eller sikkerhedsgruppe.

Hvis du er bekymret for, om brugere opretter teams eller grupper, der ikke overholder dine virksomhedsstandarder, kan du overveje at kræve, at brugerne gennemfører et kursus og derefter føjer dem til gruppen af tilladte brugere.

Når du begrænser, hvem der kan oprette en gruppe, påvirker det alle tjenester, der er afhængige af grupper for at få adgang, herunder:

- Outlook
- SharePoint
- Yammer
- Microsoft Teams
- Microsoft Stream
- Planner
- Power BI (klassisk)
- Project for the web/Roadmap

Trinnene i denne artikel forhindrer ikke medlemmer af visse roller i at oprette grupper. Globale Microsoft 365-administratorer kan oprette grupper via Microsoft 365 Administration, Planner, Exchange og SharePoint, men ikke andre placeringer som f.eks. Teams. Andre roller kan oprette Microsoft 365-grupper via begrænsede midler, der er angivet nedenfor.

- Exchange-administrator: Exchange Administration, Azure AD
- Understøttelse af partnerniveau 1: Microsoft 365 Administration, Exchange Administration Azure AD
- Understøttelse af partnerniveau 2: Microsoft 365 Administration, Exchange Administration Azure AD
- Mappeforfattere: Azure AD
- SharePoint-administrator: SharePoint Administration, Azure AD
- Administrator af Teams-tjeneste: Teams Administration, Azure AD
- Brugeradministrator: Microsoft 365 Administration, Azure AD

Hvis du er medlem af en af disse roller, kan du oprette Microsoft 365-grupper for begrænsede brugere og derefter tildele brugeren som ejer af gruppen.

## <a name="licensing-requirements"></a>Licenskrav

Hvis du vil administrere, hvem der opretter grupper, skal følgende personer Azure AD Premium-licenser eller Azure AD grundlæggende EDU-licenser, der er tildelt dem:

- Den administrator, der konfigurerer disse indstillinger for oprettelse af gruppe
- De medlemmer af gruppen, der har tilladelse til at oprette grupper

> [!NOTE]
> Se [Tildel eller fjern licenser på Azure Active Directory-portalen](/azure/active-directory/fundamentals/license-users-groups) for at få flere oplysninger om, hvordan du tildeler Azure-licenser.

Følgende personer behøver ikke Azure AD Premium- eller Azure AD Grundlæggende EDU-licenser, der er tildelt dem:

- Personer, der er medlemmer af Microsoft 365-grupper, og som ikke har mulighed for at oprette andre grupper.

## <a name="step-1-create-a-group-for-users-who-need-to-create-microsoft-365-groups"></a>Trin 1: Opret en gruppe til brugere, der skal oprette Microsoft 365-grupper

Der kan kun bruges én gruppe i organisationen til at styre, hvem der kan oprette Microsoft 365-grupper. Men du kan indlejre andre grupper som medlemmer af denne gruppe.

Administratorer i de roller, der er angivet ovenfor, behøver ikke at være medlemmer af denne gruppe: De bevarer deres mulighed for at oprette grupper.

1. I Administration skal du gå til [siden Grupper](https://admin.microsoft.com/adminportal/home#/groups).

2. Klik på **Tilføj en gruppe**.

3. Vælg den ønskede gruppetype. Husk navnet på gruppen! Du skal bruge den senere.

4. Afslut indstillingerne af gruppen, og tilføj personer eller andre grupper, som du vil kunne oprette grupper som medlemmer (ikke ejere).

Du kan finde detaljerede instruktioner under [Opret, rediger eller slet en sikkerhedsgruppe i Microsoft 365 Administration](../admin/email/create-edit-or-delete-a-security-group.md).

## <a name="step-2-run-powershell-commands"></a>Trin 2: Kør PowerShell-kommandoer

Du skal bruge prøveversionen af [Azure Active Directory PowerShell til Graph (AzureAD) (](/powershell/azure/active-directory/install-adv2) modulnavn **AzureADPreview**) til at ændre indstillingen for gæsteadgang på gruppeniveau:

- Hvis du ikke har installeret nogen version af Azure AD PowerShell-modulet før, skal du se [Installér Azure AD-modulet](/powershell/azure/active-directory/install-adv2?preserve-view=true&view=azureadps-2.0-preview) og følge vejledningen for at installere den offentlige prøveversion.

- Hvis du har version 2.0 til generel tilgængelighed af Azure AD PowerShell-modulet (AzureAD), skal du fjerne den ved at køre `Uninstall-Module AzureAD` i din PowerShell-session og derefter installere prøveversionen ved at køre `Install-Module AzureADPreview`.

- Hvis du allerede har installeret prøveversionen, skal du køre `Update-Module AzureADPreview` for at sikre, at det er den nyeste version af dette modul.

Kopiér scriptet nedenfor til en teksteditor, f.eks. Notesblok eller [den Windows PowerShell ISE](/powershell/scripting/components/ise/introducing-the-windows-powershell-ise).

Erstat *\<GroupName\>* med navnet på den gruppe, du har oprettet. Eksempel:

`$GroupName = "Group Creators"`

Gem filen som GroupCreators.ps1.

I PowerShell-vinduet skal du navigere til den placering, hvor du gemte filen (skriv "CD \<FileLocation\>").

Kør scriptet ved at skrive:

`.\GroupCreators.ps1`

og [logge på med din administratorkonto](../enterprise/connect-to-microsoft-365-powershell.md#step-2-connect-to-azure-ad-for-your-microsoft-365-subscription) , når du bliver bedt om det.

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

Hvis du fremover vil ændre, hvilken gruppe der bruges, kan du køre scriptet igen med navnet på den nye gruppe.

Hvis du vil slå begrænsningen for oprettelse af grupper fra og igen tillade alle brugere at oprette grupper, skal du angive $GroupName til "" og $AllowGroupCreation til "Sand" og køre scriptet igen.

## <a name="step-3-verify-that-it-works"></a>Trin 3: Kontrollér, at det fungerer

Det kan tage 30 minutter eller mere, før ændringerne træder i kraft. Du kan bekræfte de nye indstillinger ved at gøre følgende:

1. Log på Microsoft 365 med en brugerkonto til en person, der IKKE skal have mulighed for at oprette grupper. Det vil altså være, at de ikke er medlem af den gruppe, du har oprettet, eller en administrator.

2. Vælg feltet **Planner** .

3. I Planner skal du vælge **Ny plan** i venstre navigationsrude for at oprette en plan.

4. Du bør få vist en meddelelse om, at oprettelse af en plan og gruppe er deaktiveret.

Prøv den samme procedure igen med et medlem af gruppen.

> [!NOTE]
> Hvis medlemmer af gruppen ikke kan oprette grupper, skal du kontrollere, at de ikke blokeres via [deres OWA-postkassepolitik](/powershell/module/exchange/set-owamailboxpolicy).

## <a name="related-topics"></a>Relaterede emner

[Anbefalinger til planlægning af styring af samarbejde](collaboration-governance-overview.md#collaboration-governance-planning-recommendations)

[Opret din plan for styring af samarbejde](collaboration-governance-first.md)

[Introduktion til Office 365 PowerShell](../enterprise/getting-started-with-microsoft-365-powershell.md)

[Konfigurer selvbetjent gruppeadministration i Azure Active Directory](/azure/active-directory/users-groups-roles/groups-self-service-management)

[Set-ExecutionPolicy](/powershell/module/microsoft.powershell.security/set-executionpolicy)

[Azure Active Directory-cmdlet'er til konfiguration af gruppeindstillinger](/azure/active-directory/users-groups-roles/groups-settings-cmdlets)
