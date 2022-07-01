---
title: Konfigurer Microsoft 365 Business Standard med et nyt eller eksisterende domæne
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: high
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
- Adm_O365_Setup
- TRN_SMB
ms.custom:
- TRN_M365B
- OKR_SMB_Videos
- AdminSurgePortfolio
- AdminTemplateSet
- admindeeplinkMAC
- admindeeplinkEXCHANGE
search.appverid:
- MET150
- MOE150
- BEA160
description: Når du køber Microsoft 365 Business Standard, har du mulighed for at bruge et domæne, du ejer, eller købe et under tilmeldingen.
ms.openlocfilehash: d5504edaff4c9d406d218d8ab8333b6d50af406e
ms.sourcegitcommit: 85799f0efc06037c1ff309fe8e609bbd491f9b68
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/01/2022
ms.locfileid: "66573885"
---
# <a name="set-up-microsoft-365-business-standard-with-a-new-or-existing-domain"></a>Konfigurer Microsoft 365 Business Standard med et nyt eller eksisterende domæne

Når du køber Microsoft 365 Business Standard, har du mulighed for at tilføje et domæne, du ejer, eller købe et. Se [Tilmeld dig et Microsoft 365 Business Standard-abonnement](../simplified-signup/signup-business-standard.md).

I denne artikel fører vi dig gennem trinnene til tilføjelse af et eksisterende domæne, som du allerede ejer eller køber et nyt. Hvis du har købt et nyt domæne, da du tilmeldte dig, er dit domæne konfigureret, og du kan flytte til [Tilføj brugere og tildele licenser](#add-users-and-assign-licenses).

> [!Tip]
> Hvis du har et Microsoft 365 Business Premium abonnement, skal du se [Konfigurer Microsoft 365 Business Premium](../../business-premium/m365bp-setup.md).

## <a name="set-up-microsoft-365-for-business"></a>Konfigurer Microsoft 365 til virksomheder

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE471FJ]

## <a name="before-you-begin"></a>Før du begynder

Hvis du vil tilføje, redigere eller fjerne domæner, skal du være global administrator. Du kan finde flere oplysninger under [Om administratorroller](../add-users/about-admin-roles.md).

> [!IMPORTANT]
> Den person, der tilmelder sig Microsoft 365 for business (normalt virksomhedsejeren), bliver automatisk den tekniske administrator af organisationen. Du kan tilføje andre personer som administratorer, hvis du vil have hjælp til at administrere dine Microsoft 365-tjenester. Se [Tildel administratorroller](../add-users/assign-admin-roles.md) for at få flere oplysninger.

## <a name="watch-add-an-existing-domain-to-your-microsoft-365-business-standard-subscription"></a>Se: Føj et eksisterende domæne til dit Microsoft 365 Business Standard-abonnement

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWxApu]

## <a name="steps-add-an-existing-domain-to-your-microsoft-365-business-standard-subscription"></a>Trin: Føj et eksisterende domæne til dit Microsoft 365 Business Standard-abonnement

1. Vælg **Opret en ny firmamailkonto (avanceret)** på siden **Sådan logger du på** på Microsoft 365 Business Standard tilmelde dig.

2. På siden **Installér dine Office-apps** kan du eventuelt installere appsene på din egen computer.

3. I trinnet **Tilføj domæne** skal du angive det domænenavn, du vil bruge (f.eks. contoso.com).

    > [!IMPORTANT]
    > Hvis du har købt et domæne under tilmeldingen, kan du ikke se trinnet **Tilføj et domæne** her. Gå i stedet til [Tilføj brugere](#add-users-and-assign-licenses) .

4. Følg trinnene for at [oprette DNS-poster hos en hvilken som helst DNS-hostingudbyder for Office 365](/office365/admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider), der bekræfter, at du ejer domænet. Hvis du kender din domænevært, skal du også se [Føj et domæne til Microsoft 365](/microsoft-365/admin/setup/add-domain).

    Hvis din hostingudbyder er GoDaddy eller en anden vært aktiveret med [domæneforbindelse](/office365/admin/get-help-with-domains/domain-connect), er processen nem, og du bliver automatisk bedt om at logge på og lade Microsoft godkende på dine vegne.

    ![På Siden Bekræft adgang på GoDaddy skal du vælge Godkend.](../../media/godaddyauth.png)

## <a name="add-users-and-assign-licenses"></a>Tilføj brugere, og tildel licenser

Du kan tilføje brugere nu, men du kan også [tilføje brugere senere](../add-users/add-users.md) i Administration.

Alle brugere, du tilføjer, tildeles automatisk en Microsoft 365 Business Standard licens.

1. Hvis dit Microsoft 365 Business Standard abonnement har eksisterende brugere, får du mulighed for at tildele licenser til dem nu. Du kan også føje licenser til dem.

2. Når du har tilføjet brugerne, får du også mulighed for at dele legitimationsoplysninger med de nye brugere, du har tilføjet. Du kan vælge at udskrive dem, sende dem en mail eller downloade dem.

## <a name="connect-your-domain"></a>Opret forbindelse til dit domæne
  
Hvis du vil konfigurere tjenester, skal du opdatere poster hos din DNS-vært eller domæneregistrator.
  
1. Installationsguiden registrerer typisk din registrator og giver dig et link til en trinvis vejledning til opdatering af dine NS-poster på registratorwebstedet. Hvis den ikke gør det, [skal du ændre navneservere for at konfigurere Office 365 med en hvilken som helst domæneregistrator](../get-help-with-domains/change-nameservers-at-any-domain-registrar.md).

    - Hvis du har eksisterende DNS-poster, f.eks. et eksisterende websted, men din DNS-vært er aktiveret til [domæneforbindelse](/office365/admin/get-help-with-domains/domain-connect), skal du vælge **Tilføj poster for mig**. Acceptér alle standardindstillingerne på siden **Vælg dine onlinetjenester**, vælg **Næste**, og vælg **Godkend** på din DNS-værts side.
    - Hvis du har eksisterende DNS-poster med andre DNS-værter (ikke aktiveret for domæneforbindelse), skal du administrere dine egne DNS-poster for at sikre, at de eksisterende tjenester forbliver forbundne. Du [kan](/office365/admin/get-help-with-domains/dns-basics) finde flere oplysninger under Grundlæggende om domæner.

2. Følg trinnene i guiden, og mail og andre tjenester konfigureres for dig.

    Når tilmeldingsprocessen er fuldført, sendes du videre til Administration, hvor du skal følge en guide for at installere Office-apps, tilføje dit domæne, tilføje brugere og tildele licenser. Når du har fuldført den indledende konfiguration, kan du bruge siden **Konfiguration** i Administration til at fortsætte med at konfigurere de tjenester, der følger med dine abonnementer.

    Du kan få flere oplysninger om installationsguiden og siden **Konfiguration af** Administration under [Forskel mellem installationsguiden og siden Installation](o365-setup-wizard-and-setup-page.md).

## <a name="watch-set-up-business-email-with-a-new-domain"></a>Se: Konfigurer firmamail med et nyt domæne

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWyVVA]

## <a name="steps-set-up-business-email-with-a-new-domain"></a>Trin: Konfigurer firmamail med et nyt domæne

1. Vælg **Opret en ny firmamailkonto (avanceret)** på siden **Sådan logger du på** på Microsoft 365 Business Standard tilmelde dig.

2. Følg trinnene for at købe et nyt domæne, og angiv det domænenavn, du vil bruge (f.eks. contoso.com). Når du er færdig med at købe dit domæne, kan du [tilføje brugere og licenser](../add-users/add-users.md) og installere dine Office-apps i Administration.

## <a name="finish-setting-up"></a>Afslut indstillingerne

Følg nedenstående trin for at konfigurere Outlook, Teams, OneDrive og dit websted.

### <a name="step-set-up-outlook-for-email"></a>Trin: Konfigurer Outlook til mail

1. Søg efter Outlook i menuen Start i Windows, og vælg det.

    Hvis du bruger en Mac, skal du åbne Outlook fra værktøjslinjen eller finde den ved hjælp af Finder.

    Hvis du lige har installeret Outlook, skal du vælge **Næste** på velkomstsiden.

2. Vælg **Filoplysninger** \>  \> **Tilføj konto**.

3. Angiv din Microsoft-mailadresse, og vælg **Opret forbindelse**.

## <a name="watch-set-up-outlook-for-email"></a>Se: Konfigurer Outlook til mail

> [!VIDEO https://www.microsoft.com/videoplayer/embed/9fe86884-8a83-42cc-bca9-61a12e6dad31?autoplay=false]
  
Mere under [Konfigurer Outlook til mail](https://support.microsoft.com/office/f5bf0cd1-e1f3-4b0d-a022-ecab17efe86f).
  
### <a name="import-email"></a>Importér mail

Hvis du brugte Outlook med en anden mailkonto, kan du importere din tidligere mail, kalender og kontakter til din nye Microsoft-konto.
  
1. **Eksportér din gamle mail**

    I Outlook skal du vælge **Åbn** **filEksportér &amp;** \> \> **import/eksport**.

    Vælg **Eksportér til en fil,** og følg derefter trinnene for at eksportere Outlook-datafilen (.pst) og eventuelle undermapper.

2. **Importér din gamle mail**

    I Outlook skal du vælge **Åbn** **filEksportér &amp;** \> \> **import/eksport** igen.

    Denne gang skal du vælge **Importér fra et andet program eller en anden fil** og følge trinnene for at importere den sikkerhedskopifil, du oprettede, da du eksporterede din gamle mail.

## <a name="watch-import-and-redirect-email"></a>Se: Importér og omdiriger mail

> [!VIDEO https://www.microsoft.com/videoplayer/embed/40f7df36-9e24-44e5-8791-e9ed0dd8fd21?autoplay=false]
  
Mere på [Importér mail med Outlook](https://support.microsoft.com/office/6a3771d4-4c1d-4a25-92a6-0b8e476335de).

Du kan også bruge <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange Administration</a> til at importere alles mail. Du kan få flere oplysninger under [Overfør flere mailkonti](/Exchange/mailbox-migration/mailbox-migration).

## <a name="set-up-microsoft-teams-and-onedrive-for-business"></a>Konfigurer Microsoft Teams og OneDrive for business

Vælg OneDrive-skyikonet på proceslinjen, og følg trinnene for at flytte dine filer til den nye OneDrive for Business mappe. Vælg **Næste** for at konfigurere Microsoft Teams.

1. Åbn Microsoft Teams, vælg dit profilikon, og **tilføj derefter arbejds- eller skolekonto**. Følg trinnene for at føje din nye konto til Teams.

## <a name="use-a-public-website"></a>Brug et offentligt websted

Microsoft 365 indeholder ikke et offentligt websted til din virksomhed. Hvis du vil konfigurere en, kan du overveje at bruge en Microsoft-partner, f.eks. GoDaddy eller WIX.
  
1. Gå til **Ressourcer** i Administration, og vælg derefter **Offentligt websted**.

2. Vælg **Få mere at vide** under en af mulighederne, og tilmeld dig derefter en webstedspartner, og brug deres værktøjer til at konfigurere og designe dit websted.

## <a name="watch-create-your-business-website"></a>Se: Opret dit virksomhedswebsted

> [!VIDEO https://www.microsoft.com/videoplayer/embed/4839abc6-9323-4cbf-a79d-2907235f9ebb]

## <a name="invite-users-to-join-your-subscription-and-organization"></a>Inviter brugere til at tilmelde sig dit abonnement og din organisation

Når du har konfigureret din organisation, kan du invitere andre brugere til at tilmelde sig dit Microsoft 365-virksomhedsabonnement. De får adgang til alle funktionerne i abonnementet.

[Inviter brugere til mit abonnement](../simplified-signup/admin-invite-business-standard.md)

Fortæl brugerne, at de kan følge trinnene i nedenstående artikler for at tilmelde sig din organisation og dit abonnement.

- [Acceptér en invitation via mail](../simplified-signup/user-invite-business-standard.md)

- [Acceptér en invitation via mail ved hjælp af en Outlook-, Yahoo-, Gmail- eller anden konto (bruger)](../simplified-signup/user-invite-msa-nodomain-join.md)

## <a name="related-topics"></a>Relaterede emner

[Migrer data til mit Microsoft 365 Business Standard-abonnement](../simplified-signup/migrate-data-business-standard.md)
