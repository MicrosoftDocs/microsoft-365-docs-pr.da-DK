---
title: Overføre data manuelt mellem to konti
f1.keywords:
- NOCSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom: AdminSurgePortfolio
search.appverid:
- MET150
- MOE150
ms.assetid: 7dc5d983-84b2-4802-bef0-602ae1780a42
description: Find ud af, hvordan du overfører data manuelt mellem to Microsoft 365-konti, da du ændrede planen eller firmanavnet eller kombinerede flere abonnementer til ét.
ms.openlocfilehash: 7d6cb9e055fd27e8f9b0a26e7ff4bfffa97421ae
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63599754"
---
# <a name="transfer-data-manually-between-two-accounts"></a>Overføre data manuelt mellem to konti

Rul ærmerne op, og bloker tid i kalenderen: at overføre data mellem to Microsoft 365-konti er en manuel, kompliceret og tidskrævende proces. Dette er ikke en automatiseret eller understøttet proces. Vi skal nok hjælpe dig i gang.
  
> [!CAUTION]
> Der vil være nedetid under processen, hvor mail, Skype for Business og et offentligt websted, der hostes Microsoft 365, ikke fungerer. Brugerne får nye brugernavne og adgangskoder, og de skal nulstilles Outlook.

**Overfør kun data manuelt ved at følge vejledningen i dette emne, hvis et af følgende gælder:**
  
- Du skal skifte til en plan i en anden tjenestefamilie.

- Dit firmanavn er ændret, og du har besluttet dig for at oprette et nyt abonnement og overføre dine data, fordi du vil bruge forskellige indledende domænenavne.

- Du skal kombinere flere abonnementer i ét nyt.

> [!IMPORTANT]
> Hvis du har brug [](../../commerce/subscriptions/switch-to-a-different-plan.md) for at ændre dit abonnement og kan bruge guiden Skift plan, eller hvis du har brug for at overføre til en ny abonnementsplan i den samme abonnementsfamilie, selv når guiden Skift plan ikke virker, behøver du ikke at overføre dine data manuelt, og der er ingen nedetid.

|**Opgaver**|**Trin**|
|:-----|:-----|
|Køb den plan, du vil flytte til.  <br/> |Når du tilmelder dig, angiver du det firmanavn, der skal bruges i de indledende domænenavne:  *dinvirksomhed*  .onmicrosoft.com,  *dinvirksomhed*  -public.sharepoint.com og  *dinvirksomhed*  .sharepoint.com. Du skal bruge et andet  *navn til dinvirksomhed*  end det navn, du har brugt til eksisterende abonnementer.  <br/> > [!NOTE]> Det tager som regel flere måneder efter annullering af et abonnement, før de indledende domænenavne, der bruger  *dinvirksomhed, frigives*  fra vores systemer. Selvom du vil gemme alle dine data fra dit gamle Microsoft 365-abonnement og annullere abonnementet, er den gamle *dinvirksomhed-værdi* ikke umiddelbart tilgængelig til brug i et nyt abonnement.           |
|Fjern dit brugerdefinerede domæne fra dit gamle Microsoft 365-abonnement.  <br/> | Følg de [påkrævede trin,](remove-a-domain.md) før du fjerner et domæne, for at fjerne domænenavnet fra brugermailadresser og for at fjerne DNS-poster for mail og Lync for det brugerdefinerede domæne. Hvis du hoster dit offentlige websted Microsoft 365, skal du også fjerne den CNAME-post, der peger på den.  <br/> > [!IMPORTANT]> Når du har fjernet den MX-post, der routes mail til dette brugerdefinerede domæne, fungerer mail ikke længere, før du har føjet domænet til din nye konto, konfigureret den nye MX-post og konfigureret dine brugere. Når du fjerner DNS-posterne for Lync, holder Lync op med at fungere. Og når du fjerner den CNAME-post, der peger på dit offentlige websted, vil den ikke være tilgængelig.           [Fjern domænet](remove-a-domain.md) .  <br/> |
|Konfigurer dit brugerdefinerede domæne til dit nye abonnement, og konfigurer dine brugere.  <br/> | Konfigurer dit nye abonnement, herunder oprettelse af de nødvendige DNS-poster for dit brugerdefinerede domæne.  <br/>  Opret dine brugere med mailadresser på dit brugerdefinerede domæne.  <br/> |
|Overfør data fra dit gamle abonnement til dit nye abonnement.  <br/> | Log på begge konti i separate browservinduer:  <br/>  Højreklik på dit browserikon, og åbn to private browservinduer. Du kan bruge forskellige legitimationsoplysninger i de to vinduer til at logge på begge konti.  <br/> [Overfør administrative indstillinger mellem abonnementer](#email) <br/> [Overfør strukturen og dataene på teamwebstedet](#transfer-team-site-structure-and-data) <br/> [Overfør et offentligt websted mellem abonnementer](#transfer-a-public-website-between-subscriptions) <br/> [Overfør administrative indstillinger mellem abonnementer](#email) <br/> |
|Opsnuller abonnementet på den plan, du er færdig med, ved at ringe til Microsoft Support for at Microsoft 365.  <br/> | Kontrollér, at dit nye abonnement fungerer, og at alle data er blevet overført.  <br/>  [Kontakt kundesupport for](../../business-video/get-help-support.md) at opsige dit gamle abonnement.  <br/> |

## <a name="transfer-administrative-settings-between-subscriptions"></a>Overfør administrative indstillinger mellem abonnementer

Gå til de følgende sider på hver konto, og konfigurer den nye konto baseret på den gamle kontos indstillinger.
  
Hvis du overfører data fra Microsoft 365 Microsoft 365 Midsize Business eller Microsoft 365 Enterprise, er administratorsiderne struktureret på en anden måde. Se en [video: Introduktion Microsoft 365 Enterprise](../index.yml), og gå til følgende steder for at se administratorindstillinger.
  
Til Microsoft 365 Enterprise og Microsoft 365 Midsize Business:
  
|**Placering**|**Formål**|
|:-----|:-----|
|**Administrator** \> **Microsoft 365 tjenesteindstillinger** \>  <br/> |Vælg hver fane til indstillinger for mail, websteder, Lync, brugersoftware, adgangskoder, community, rettighedsstyring og mobil.  <br/> |
|**Administrator** \> **Exchange** <br/> | Exchange Online indstillinger  <br/> |
|**Administrator** \> **SharePoint** <br/> | SharePoint Online-indstillinger  <br/> |
|**Administrator** \> **Skype for Business** <br/> |Yderligere Skype for Business indstillinger  <br/> |

Til Microsoft 365 Small Business
  
|**Placering**|**Formål**|
|:-----|:-----|
|**Administrator** \> **Administrere indstillinger for hele organisationen** <br/> |Administrative indstillinger  <br/> |

## <a name="transfer-a-public-website-between-subscriptions"></a>Overfør et offentligt websted mellem abonnementer

Hvis du har et offentligt websted hostet på Microsoft 365, skal du gemme det og oprette det igen på dit nye abonnement.
  
> [!NOTE]
> Hvis dit offentlige websted er hostet hos en DNS-udbyder, kræves der ingen ændringer. Det påvirkes ikke af din overgang.
  
Hvis du vil gemme et dokumentbibliotek eller listeindhold fra et SharePoint Online-miljø på filshares eller en lokal computer, skal du se Manuel overførsel [af SharePoint Online-indhold](/sharepoint/troubleshoot/migration-tool/content-manual-migration).
  
> [!NOTE]
> Appen til overførsel af offentlige websteder kan ikke overføre data til et andet abonnement.
  
## <a name="transfer-team-site-structure-and-data"></a>Overfør strukturen og dataene på teamwebstedet

Der er flere måder at gemme eller overføre data for teamwebstedet på:
  
- Du kan gemme det gamle websted som en skabelon og importere skabelonen til det nye websted.

- Hvis du vil overføre dokumenter, skal du først genoprette dit hierarki på det nye websted manuelt. Derefter kan du åbne SharePoint teamwebsteder på samme tid, åbne begge dokumentbiblioteker med Windows Stifinder og kopiere og indsætte dokumenterne. Se [video: Kopiere eller flytte biblioteksfiler ved hjælp af Åbn med Stifinder](https://support.microsoft.com/office/d18d21a0-1f9f-4f6c-ac45-d52afa0a4a2e).

- Hvis du vil overføre listedata, skal [du gemme en](https://support.microsoft.com/office/c3884ad1-bc49-44b8-b3d6-3bc6a01eb393) listeskabelon og bruge den gemte skabelon til at oprette listen igen på det nye websted.

- Hvis du vil gemme et dokumentbibliotek eller listeindhold fra et SharePoint Online-miljø (OneDrive for Business- eller teamwebsteder) til filshares eller en lokal computer, skal du se Oplysninger om manuel overførsel af [SharePoint Online-indhold](/sharepoint/troubleshoot/migration-tool/content-manual-migration).

## <a name="transfer-users-data-between-subscriptions"></a>Overfør brugernes data mellem abonnementer

### <a name="email"></a>Mail:

Bed brugerne om [at flytte deres mail, kontakter, opgaver og kalenderoplysninger](https://support.microsoft.com/office/0996ece3-57c6-49bc-977b-0d1892e2aacc) , når du har konfigureret dit nye abonnement. De kan finde deres gamle mails ved at bruge deres oprindelige brugernavn, f.eks. sue@contoso.onmicrosoft.com.
  
### <a name="onedrive-for-business-data"></a>OneDrive for Business data:

Bed brugerne om at kopiere/[OneDrive for Business indholdet på deres computer](https://support.microsoft.com/office/59b1de2b-519e-4d3a-8f45-51647cf291cd) og derefter føje det tilbage til deres nye abonnement.

### <a name="onenote"></a>OneNote 

Bed brugerne om [at sikkerhedskopiere OneNote](https://support.microsoft.com/office/back-up-notes-f58b34b0-611d-435e-87fa-7942a1767af4?ui=en-us&rs=en-us&ad=us) og [gendanne noter fra en sikkerhedskopi](https://support.microsoft.com/en-us/office/restore-notes-from-a-backup-5daf9cb0-6769-4998-a5de-f044fdd0d831?ui=en-us&rs=en-us&ad=us) af deres nye abonnementer.
