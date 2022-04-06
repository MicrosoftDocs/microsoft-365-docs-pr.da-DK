---
title: Brug følsomhedsmærkater til at konfigurere standardlinktypen for deling for websteder og dokumenter SharePoint og OneDrive
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MET150
description: Brug følsomhedsmærkater til at konfigurere standardlinktypen for deling for websteder og dokumenter SharePoint og OneDrive.
ms.openlocfilehash: 122a8846893b97146dc74d3a9d30ccbfe050525b
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63704715"
---
# <a name="use-sensitivity-labels-to-configure-the-default-sharing-link-type-for-sites-and-documents-in-sharepoint-and-onedrive"></a>Brug følsomhedsmærkater til at konfigurere standardlinktypen for deling for websteder og dokumenter SharePoint og OneDrive

>*[Microsoft 365 licenseringsvejledning til sikkerhed og & overholdelse af regler og standarder](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

Som en ekstra konfiguration til de indstillinger, du ser i [Microsoft 365 Overholdelsescenter for](sensitivity-labels.md) følsomhedsetiketter, kan du bruge disse etiketter til at konfigurere indstillingerne for standarddelingslinktypen for et SharePoint-websted eller OneDrive-konto og for individuelle dokumenter. Disse indstillinger vælges automatisk, men de er ikke meget synlige for brugerne, når de vælger **knappen Del i** deres Office apps. Som et eksempel:

![Eksempel på standarddialogboksen for delingslink.](../media/default-sharing-link-example.png)

Standardtypen for delingslink angiver omfanget (hvem) og tilladelserne (visning eller redigering), der vælges automatisk, når brugere deler filer og mapper. Selvom brugerne altid kan tilsidesætte disse standardindstillinger, før de sender linket til deling, giver de indstillinger, du vælger, en sikker grundlinje. Normalt ændrer brugerne ikke indstillingerne før deling.

På webstedsniveau (SharePoint websteds- eller OneDrive-konto) er følsomhedsmærkater et praktisk alternativ til at angive den standarddelingslinktype, der kan konfigureres for et websted i SharePoint Administration. Få mere at vide under [Skift standardlinktypen for et websted fra](/sharepoint/change-default-sharing-link) den SharePoint dokumentation.

Denne konfiguration på webstedsniveau fungerer godt til SharePoint, der har dokumenter med samme følsomhedsniveau. Men hvis websteder indeholder nogle dokumenter, der har et højere følsomhedsniveau, som kræver mere restriktive indstillinger, kan du konfigurere en følsomhedsmærkat med forskellige indstillinger for standarddelingslinktypen og derefter anvende denne etiket på dokumenter.

I dette scenarie, hvor webstedet har standardindstillinger for delingslinktyper, og et dokument på dette websted har forskellige indstillinger for standardlinktyper, anvendes de mere restriktive indstillinger for omfang på det tidspunkt, hvor brugeren vælger delingsindstillingen for dokumentet. Eksempel:

- Standardtypen for delingslinket for webstedet er begrænset til alle i organisationen. Et dokument på webstedet er mærket med den standard linktype for deling, der er indstillet til bestemte personer. Når en bruger deler det pågældende dokument, er den valgte standarddelingslinktype begrænset til bestemte personer.

- Standardtypen for delingslink for webstedet er begrænset til bestemte personer med redigeringstilladelser. Et dokument på webstedet er mærket med den standard linktype for deling, der er indstillet til andre i organisationen, med visningstilladelser. Når en bruger deler det pågældende dokument, vil den valgte standardlinktype for deling være begrænset til bestemte personer med redigeringstilladelser.

Det kan også være relevant at konfigurere standardlinktypen for dokumenter uden indstillingen på webstedsniveau. Selvom websteder for SharePoint er organiseret til at være vært for den samme type dokumenter, er det ikke tilfældet for OneDrive konti. Brugere gemmer typisk en lang række filer på en OneDrive, ofte med en blanding af personlige og forretningsdokumenter. Det er sandsynligvis ikke praktisk at angive en standardlinktype for alle dokumenter til en OneDrive-konto, men individuelle dokumenter kan stadig nyde godt af disse indstillinger. Eksempel:

- Dokumenter med navnet **Meget fortrolige** har en standard linktype til deling, der begrænser deling til bestemte personer i stedet for andre i organisationen.
- Dokumenter med navnet **Generelt** har en standard linktype til deling, der begrænser deling til personer i organisationen.
- Dokumenter med navnet **Personlig har** en standard linktype til deling, der gør det muligt at dele med alle med linket.

## <a name="prerequisites"></a>Forudsætninger

For at anvende standardlinktypen for deling på websteder skal følsomhedsmærkater være aktiveret for objektbeholdere. Hvis denne funktion endnu ikke er aktiveret for din lejer, skal du se Sådan aktiverer du [følsomhedsmærkater for objektbeholdere og synkroniserer etiketter](sensitivity-labels-teams-groups-sites.md#how-to-enable-sensitivity-labels-for-containers-and-synchronize-labels).

Hvis du vil anvende standardlinktypen for dokumenter i SharePoint og OneDrive, skal følsomhedsmærkater være aktiveret for disse tjenester. Hvis denne funktion endnu ikke er aktiveret for din lejer, skal du se Sådan aktiverer du følsomhedsmærkater [for SharePoint og OneDrive (tilmelding)](sensitivity-labels-sharepoint-onedrive-files.md#how-to-enable-sensitivity-labels-for-sharepoint-and-onedrive-opt-in).

I en PowerShell-session skal du oprette forbindelse til [Office 365 Security & Compliance Center PowerShell](/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell) for at konfigurere indstillingerne for standardtypen for delingslink.

> [!NOTE]
> Selvom det ikke er påkrævet, er det nemmest først at oprette og konfigurere følsomhedsmærkater i [Microsoft 365 Overholdelsescenter](create-sensitivity-labels.md) og derefter ændre disse etiketter med de indstillinger, der konfigurerer standardlinktypen for deling.

## <a name="how-to-configure-settings-for-the-default-sharing-link-type"></a>Sådan konfigurerer du indstillinger for standardtypen for delingslink

Konfigurationsindstillingerne for standardlinktypen for deling bruger PowerShell *AdvancedSettings-parameteren* med [cmdlet'erne Set-Label](/powershell/module/exchange/set-label) og [New-Label](/powershell/module/exchange/new-labelpolicy) [fra Security & Compliance Center PowerShell](/powershell/exchange/scc-powershell):

- **DefaultSharingScope**: De tilgængelige værdier er:
    - **Bestemte personer**: Indstiller standardlinket til deling af webstedet til linket "Bestemte personer"
    - **Organisation**: Angiver webstedets standarddelingslink til linket "organisation" eller link, der kan deles af virksomheden
    - **Alle**: Angiver standardlinket for deling af webstedet til en anonym adgang eller alle-link

- **DefaultShareLinkPermission**: De tilgængelige værdier er:
    - **Vis**: Angiver standardlinktilladelsen for webstedet til at "vise"-tilladelser
    - **Rediger**: Indstiller standardlinktilladelsen for webstedet til at "redigere"-tilladelser

Disse to indstillinger og værdier svarer til parametrene *DefaultSharingScope* og *DefaultShareLinkPermission* fra [Set-SPOSite-cmdlet'en](/powershell/module/sharepoint-online/set-sposite) .

PowerShell-eksempler, hvor følsomhedsmærkatet GUID er **8faca7b8-8d20-48a3-8ea2-0f96310a848e**:

- Sådan angives standardtypen for delingslink til Bestemte personer:
    
    ````powershell
    Set-Label -Identity 8faca7b8-8d20-48a3-8ea2-0f96310a848e -AdvancedSettings @{DefaultSharingScope="SpecificPeople"}
    ````

- Sådan angives standardtilladelser for delingslink til Rediger:
    
    ````powershell
    Set-Label -Identity 8faca7b8-8d20-48a3-8ea2-0f96310a848e -AdvancedSettings @{DefaultShareLinkPermission="Edit"}
    ````

Hvis du vil konfigurere indstillingerne for standardlinktypen for et websted, skal følsomhedsmærkatens omfang omfatte Grupper **&** websteder, når du opretter følsomhedsmærkatet i Microsoft 365 Overholdelsescenter.[](sensitivity-labels.md#label-scopes) Når den er oprettet, vises den som Websted **, UnifiedGroup** i kolonnen Omfang på siden Etiketter, og indstillingen PowerShell *ContentType* viser også den samme værdi. For dokumenter skal området omfatte Filer **& mails**, der vises som **Filer, Mail**. Gør derefter følgende:

- Når omfanget omfatter Grupper **& websteder**, kan du anvende navnet på et websted, hvilket angiver standardtypen for delingslink for det pågældende websted. Hvis du vil have mere at vide om, hvordan du anvender et følsomhedsmærkat på et websted, skal du [se Sådan anvender du følsomhedsmærkater på beholdere](sensitivity-labels-teams-groups-sites.md#how-to-apply-sensitivity-labels-to-containers).

- Når omfanget af følsomhedsmærkatet omfatter **Filer & mails**, kan du anvende etiketten på dokumenter, hvilket indstiller standarddelingslinktypen for det pågældende dokument. Etiketten kan anvendes [manuelt](https://support.microsoft.com/office/apply-sensitivity-labels-to-your-files-and-email-in-office-2f96e7cd-d5a4-403b-8bd7-4cc636bae0f9) eller [automatisk](apply-sensitivity-label-automatically.md).

> [!TIP]
> Du kan også angive, at navnet er standard-følsomhedsmærkatet, der skal anvendes på nye websteder eller nye dokumenter, som en [indstilling for etiketpolitik](sensitivity-labels.md#what-label-policies-can-do).

### <a name="powershell-tips-for-specifying-the-advanced-settings"></a>Tip til PowerShell til at angive avancerede indstillinger

Selvom du kan angive følsomhedsmærkatet efter navn, anbefaler vi, at du bruger mærkaten GUID for at undgå forvirring over at angive navnet eller det viste navn. Sådan finder du GUID'et og bekræfter mærkatens omfang:

````powershell
Get-Label | Format-Table -Property DisplayName, Name, Guid, ContentType
````

Hvis du vil fjerne en af disse avancerede indstillinger fra en følsomhedsmærkat, skal du bruge den samme AdvancedSettings-parametersyntaksen, men angive en null-strengværdi. Eksempel:

````powershell
Set-Label -Identity 8faca7b8-8d20-48a3-8ea2-0f96310a848e -AdvancedSettings @{DefaultSharingScope=""}
````

