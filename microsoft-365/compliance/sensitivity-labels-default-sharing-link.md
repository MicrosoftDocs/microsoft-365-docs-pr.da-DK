---
title: Brug følsomhedsmærkater til at konfigurere standardlinktypen for deling
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
description: Brug følsomhedsmærkater til at konfigurere standardlinktypen for deling for websteder og dokumenter i SharePoint og OneDrive.
ms.openlocfilehash: ca4b74c2fb25c4f1f1ef96b8ae0241481358797d
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66628567"
---
# <a name="use-sensitivity-labels-to-configure-the-default-sharing-link-type-for-sites-and-documents-in-sharepoint-and-onedrive"></a>Brug følsomhedsmærkater til at konfigurere standardlinktypen for deling for websteder og dokumenter i SharePoint og OneDrive

>*[Microsoft 365-licensvejledning til sikkerhed & overholdelse af angivne standarder](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

Som en yderligere konfiguration af de indstillinger, du kan se i Microsoft Purview-compliance-portal for [følsomhedsmærkater](sensitivity-labels.md), kan du bruge disse mærkater til at konfigurere indstillinger for standardlinktypen for deling for et SharePoint-websted eller en OneDrive-konto og for individuelle dokumenter. Disse indstillinger vælges automatisk, men de er ikke meget synlige for brugerne, når de vælger knappen **Del** i deres Office-apps. Som eksempel:

![Eksempel på dialogboksen med standardlink til deling.](../media/default-sharing-link-example.png)

Standardlinktypen for deling angiver omfanget (hvem) og tilladelser (visning eller redigering), der automatisk vælges, når brugerne deler filer og mapper. Selvom brugerne altid kan tilsidesætte disse standardindstillinger, før de sender delingslinket, angiver de indstillinger, du vælger, en sikker baseline. Brugerne ændrer normalt ikke indstillingerne før deling.

På webstedsniveau (SharePoint-websted eller OneDrive-konto) er følsomhedsmærkater et praktisk alternativ til angivelse af standardlinktypen for deling, der kan konfigureres for et websted i SharePoint Administration. Du kan finde flere oplysninger under [Skift standardlinktypen for et websted](/sharepoint/change-default-sharing-link) i dokumentationen til SharePoint.

Denne konfiguration på webstedsniveau fungerer godt for SharePoint-websteder, der har dokumenter med samme følsomhedsniveau. Men hvis websteder indeholder nogle dokumenter, der har et højere følsomhedsniveau, som kræver mere restriktive indstillinger, kan du konfigurere en følsomhedsmærkat med forskellige indstillinger for standardtypen for delingslinket og derefter anvende denne mærkat på dokumenter.

I dette scenarie, hvor webstedet har indstillinger for standardlinktyper for deling, og et dokument på dette websted har forskellige indstillinger for standardlinktyper, anvendes de mere restriktive områdeindstillinger på det tidspunkt, hvor brugeren vælger delingsindstillingen for dokumentet. Eksempel:

- Standardlinktypen for deling for webstedet er beregnet til alle i din organisation. Et dokument på dette websted er mærket med standardlinktypen for deling angivet til bestemte personer. Når en bruger deler dokumentet, vil den valgte standardlinktype for deling være begrænset til bestemte personer.

- Standardlinktypen for deling for webstedet er begrænset til bestemte personer med redigeringstilladelser. Et dokument på dette websted er mærket med standardlinktypen for deling angivet til alle i organisationen med visningstilladelser. Når en bruger deler dokumentet, vil den valgte standardlinktype for deling være begrænset til bestemte personer med redigeringstilladelser.

Konfiguration af standardlinktypen for dokumenter kan også være relevant uden indstillingen på webstedsniveau. Selvom SharePoint-websteder f.eks. typisk er organiseret til at hoste den samme type dokumenter, er det ikke tilfældet for OneDrive-konti. Brugerne gemmer typisk en lang række filer på OneDrive, ofte inklusive en blanding af personlige dokumenter og forretningsdokumenter. Det er sandsynligvis ikke praktisk at angive en standardlinktype for alle dokumenter for en brugers OneDrive-konto, men individuelle dokumenter kan stadig drage fordel af disse indstillinger. Eksempel:

- Dokumenter med mærkaten **Meget fortroligt** har en standardlinktype for deling, der begrænser deling til bestemte personer i stedet for nogen i organisationen.
- Dokumenter, der er navngivet **Generelt** , har en standardlinktype for deling, der begrænser deling til personer i din organisation.
- Dokumenter med navnet **Personlig** har en standardlinktype for deling, der gør det muligt at dele med alle med linket.

## <a name="prerequisites"></a>Forudsætninger

Hvis du vil anvende standardlinktypen for deling for websteder, skal følsomhedsmærkater være aktiveret for objektbeholdere. Hvis denne funktion endnu ikke er aktiveret for din lejer, skal du se [Sådan aktiverer du følsomhedsmærkater for objektbeholdere og synkroniserer mærkater](sensitivity-labels-teams-groups-sites.md#how-to-enable-sensitivity-labels-for-containers-and-synchronize-labels).

Hvis du vil anvende standardlinktypen for deling for dokumenter i SharePoint og OneDrive, skal følsomhedsmærkater være aktiveret for disse tjenester. Hvis denne funktion endnu ikke er aktiveret for din lejer, skal du se [Sådan aktiverer du følsomhedsmærkater for SharePoint og OneDrive (tilmelder dig)](sensitivity-labels-sharepoint-onedrive-files.md#how-to-enable-sensitivity-labels-for-sharepoint-and-onedrive-opt-in).

I en PowerShell-session skal du [oprette forbindelse til Office 365 Security & Compliance PowerShell](/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell) for at konfigurere indstillingerne for standardlinktypen for deling.

> [!NOTE]
> Selvom det ikke er påkrævet, er det nemmest først at [oprette og konfigurere følsomhedsmærkater i Microsoft Purview-compliance-portal](create-sensitivity-labels.md) og derefter ændre disse mærkater med de indstillinger, der konfigurerer standardtypen for delingslinket.

## <a name="how-to-configure-settings-for-the-default-sharing-link-type"></a>Sådan konfigurerer du indstillinger for standardlinktypen for deling

Konfigurationsindstillingerne for standardlinktypen for deling bruger parameteren PowerShell *AdvancedSettings* med cmdlet'erne [Set-Label](/powershell/module/exchange/set-label) og [New-Label](/powershell/module/exchange/new-labelpolicy) fra [Security & Compliance PowerShell](/powershell/exchange/scc-powershell):

- **DefaultSharingScope**: De tilgængelige værdier er:
    - **SpecificPeople**: Angiver standardlinket til deling for webstedet til linket "Bestemte personer"
    - **Organisation**: Angiver standardlinket til deling for webstedet til linket "organisation" eller linket, der kan deles af virksomheden
    - **Alle**: Angiver standardlinket til deling for webstedet til et anonymt adgangs- eller nogen-link

- **DefaultShareLinkPermission**: De tilgængelige værdier er:
    - **Vis**: Angiver standardlinktilladelsen for webstedet til "visningstilladelser"
    - **Rediger**: Angiver standardlinktilladelsen for webstedet til at "redigere" tilladelser

Disse to indstillinger og værdier svarer til parametrene *DefaultSharingScope* og *DefaultShareLinkPermission* fra [Set-SPOSite-cmdlet'en](/powershell/module/sharepoint-online/set-sposite) .

PowerShell-eksempler, hvor følsomhedsmærkaten GUID er **8faca7b8-8d20-48a3-8ea2-0f96310a848e**:

- Sådan angiver du standardlinktypen for deling til SpecificPeople:
    
    ````powershell
    Set-Label -Identity 8faca7b8-8d20-48a3-8ea2-0f96310a848e -AdvancedSettings @{DefaultSharingScope="SpecificPeople"}
    ````

- Sådan angiver du tilladelserne for standardlinktypen for deling til Rediger:
    
    ````powershell
    Set-Label -Identity 8faca7b8-8d20-48a3-8ea2-0f96310a848e -AdvancedSettings @{DefaultShareLinkPermission="Edit"}
    ````

Du kan finde mere hjælp til at angive avancerede PowerShell-indstillinger under [PowerShell-tip til angivelse af avancerede indstillinger](create-sensitivity-labels.md#powershell-tips-for-specifying-the-advanced-settings).

Hvis du vil konfigurere indstillingerne for standardlinktypen for deling for et websted, skal [følsomhedsmærkatens omfang](sensitivity-labels.md#label-scopes) omfatte **Grupper & websteder**, når du opretter følsomhedsmærkaten i Microsoft Purview-compliance-portal. Når den er oprettet, kan du se dette vist som **Site, UnifiedGroup** i kolonnen **Scope** på siden **Labels** , og indstillingen PowerShell *ContentType* viser også den samme værdi. For dokumenter skal området indeholde **Filer & mails**, der vises som **Filer, Mail**. Derefter:

- Når området omfatter **Grupper & websteder**, kan du anvende etiketten på et websted, som angiver standardlinktypen for deling for det pågældende websted. Du kan finde oplysninger om, hvordan du anvender en følsomhedsmærkat på et websted, under [Sådan anvender du følsomhedsmærkater på objektbeholdere](sensitivity-labels-teams-groups-sites.md#how-to-apply-sensitivity-labels-to-containers).

- Når følsomhedsmærkatens omfang omfatter **Filer & mails**, kan du anvende mærkaten på dokumenter, hvilket angiver standardtypen for delingslinket for det pågældende dokument. Etiketten kan anvendes [manuelt](https://support.microsoft.com/office/apply-sensitivity-labels-to-your-files-and-email-in-office-2f96e7cd-d5a4-403b-8bd7-4cc636bae0f9) eller [automatisk](apply-sensitivity-label-automatically.md).

> [!TIP]
> Du kan også angive, at mærkaten er standardfølsomhedsmærkaten, der skal anvendes for nye websteder eller nye dokumenter som en [politikindstilling for mærkater](sensitivity-labels.md#what-label-policies-can-do).
