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
description: Når du køber Microsoft 365 Business Standard, har du mulighed for at bruge et domæne, du ejer, eller at købe et under tilmeldingen.
ms.openlocfilehash: 51f88847a1e0ca04e216044172dbacf572fb82e3
ms.sourcegitcommit: b1066b2a798568afdea9c09401d52fa38fe93546
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/13/2021
ms.locfileid: "63590271"
---
# <a name="set-up-microsoft-365-business-standard-with-a-new-or-existing-domain"></a>Konfigurer Microsoft 365 Business Standard med et nyt eller eksisterende domæne

Når du køber Microsoft 365 Business Standard, har du mulighed for at tilføje et domæne, som du ejer, eller at købe et. Se [Tilmeld dig et Microsoft 365 Business Standard abonnement](../simplified-signup/signup-business-standard.md).

I denne artikel vil vi hjælpe dig med at tilføje et eksisterende domæne, som du allerede ejer, eller købe et nyt. Hvis du har købt et nyt domæne, da du tilmeldte dig, er dit domæne helt konfigureret, og du kan flytte [til Tilføj brugere og tildele licenser](#add-users-and-assign-licenses).

## <a name="before-you-begin"></a>Før du begynder

Hvis du vil tilføje, ændre eller fjerne domæner, skal du være global administrator. Du kan få mere at vide [under Om administratorroller](../add-users/about-admin-roles.md).

> [!IMPORTANT]
> Den person, der tilmelder Microsoft 365 til virksomheder (som regel virksomhedsejeren), bliver automatisk organisationens tekniske administrator. Du kan tilføje andre personer som administratorer, hvis du vil have hjælp til at administrere Microsoft 365 tjenester. Se [Tildel administratorroller](../add-users/assign-admin-roles.md) for at få flere oplysninger.

## <a name="watch-add-an-existing-domain-to-your-microsoft-365-business-standard-subscription"></a>Se: Føj et eksisterende domæne til dit Microsoft 365 Business Standard-abonnement

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWxApu]

## <a name="steps-add-an-existing-domain-to-your-microsoft-365-business-standard-subscription"></a>Trin: Føj et eksisterende domæne til dit Microsoft 365 Business Standard-abonnement

1. Fra siden **Hvordan du logger på på** siden Microsoft 365 Business Standard du tilmelde dig skal du vælge **Opret en ny virksomhedsmailkonto (avanceret)**.

2. På siden **Installér Office apps** kan du også installere appsene på din egen computer.

3. I **trinnet Tilføj** domæne skal du skrive det domænenavn, du vil bruge (f.eks. contoso.com).

    > [!IMPORTANT]
    > Hvis du har købt et domæne under tilmeldingen, kan du ikke se **Tilføj et domænetrin** her. Gå til [Tilføj brugere i](#add-users-and-assign-licenses) stedet.

4. Følg trinnene for at [oprette DNS-poster for det domæne, der bekræfter, at Office 365](/office365/admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider) ejer domænet, hos en hvilken som helst DNS-udbyder. Hvis du kender din domænevært, kan du se [også Føj et domæne til Microsoft 365](/microsoft-365/admin/setup/add-domain).

    Hvis din udbyder er GoDaddy eller en anden vært aktiveret med domænetilslutning [, er](/office365/admin/get-help-with-domains/domain-connect) processen let, og du vil automatisk blive bedt om at logge på og lade Microsoft godkende på dine vegne.

    ![På siden Bekræft adgang på GoDaddy skal du vælge Godkend.](../../media/godaddyauth.png)

## <a name="add-users-and-assign-licenses"></a>Tilføj brugere, og tildel licenser

Du kan tilføje brugere nu, men du [kan også tilføje brugere](../add-users/add-users.md) senere i Administration.

Alle brugere, du tilføjer, får automatisk tildelt Microsoft 365 Business Standard licens.

1. Hvis dit Microsoft 365 Business Standard-abonnement har eksisterende brugere, får du mulighed for at tildele licenser til dem nu. Du kan også føje licenser til dem.

2. Når du har tilføjet brugerne, får du også mulighed for at dele legitimationsoplysninger med de nye brugere, du har tilføjet. Du kan vælge at udskrive dem, maile dem eller downloade dem.

## <a name="connect-your-domain"></a>Forbind dit domæne
  
Hvis du vil konfigurere tjenester, skal du opdatere poster hos din DNS-vært eller domæneregistrator.
  
1. Konfigurationsguiden registrerer typisk din registrator og giver dig et link til trinvise instruktioner om opdatering af NS-posterne på registratorens websted. Hvis det ikke sker, skal [du ændre navneservere for at konfigurere Office 365 med en domæneregistrator](../get-help-with-domains/change-nameservers-at-any-domain-registrar.md).

    - Hvis du har eksisterende DNS-poster, f.eks. et eksisterende websted, men din DNS-vært er aktiveret [til domæne](/office365/admin/get-help-with-domains/domain-connect) connect, skal du **vælge Tilføj poster for mig**. På siden **Vælg dine onlinetjenester** skal du acceptere alle standardindstillingerne og vælge **Næste** og vælge **Godkend** på DNS-værtens side.
    - Hvis du har eksisterende DNS-poster med andre DNS-værter (ikke aktiveret til domæneforbindelser), skal du administrere dine egne DNS-poster for at sikre, at de eksisterende tjenester forbliver forbundet. Se [grundlæggende om domæner for at](/office365/admin/get-help-with-domains/dns-basics) få flere oplysninger.

2. Følg trinnene i guiden, og mail og andre tjenester konfigureres for dig.

    Når tilmeldingen er fuldført, bliver du ført til Administration, hvor du skal følge en guide til at installere Office-apps, tilføje dit domæne, tilføje brugere og tildele licenser. Når du har fuldført den indledende konfiguration, kan du bruge  siden Konfiguration i Administration til at fortsætte med at konfigurere og konfigurere de tjenester, der er forbundet med dine abonnementer.

    Du kan finde flere oplysninger om konfigurationsguiden og siden **Konfiguration** af Administration i Forskellen [mellem konfigurationsguiden og siden Konfiguration](o365-setup-wizard-and-setup-page.md).

## <a name="watch-set-up-business-email-with-a-new-domain"></a>Se: Konfigurere virksomhedsmail med et nyt domæne

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWyVVA]

## <a name="steps-set-up-business-email-with-a-new-domain"></a>Trin: Konfigurere virksomhedsmail med et nyt domæne

1. Fra siden **Hvordan du logger på på** siden Microsoft 365 Business Standard du tilmelde dig skal du vælge **Opret en ny virksomhedsmailkonto (avanceret)**.

2. Følg trinnene for at købe et nyt domæne, og angiv det domænenavn, du vil bruge (f.eks. contoso.com). Når du er færdig med at købe dit domæne, kan [](../add-users/add-users.md) du tilføje brugere og licenser og installere Office-apps i Administration.

## <a name="finish-setting-up"></a>Afslut konfigurationen

Følg trinnene nedenfor for at konfigurere Outlook, Teams, OneDrive og dit websted.

### <a name="step-set-up-outlook-for-email"></a>Trin: Konfigurere Outlook til mail

1. På siden Windows menuen Start du søge efter Outlook og vælge den.

    Hvis du bruger en Mac, skal du åbne Outlook fra værktøjslinjen eller finde den ved hjælp af Finder.

    Hvis du lige har installeret Outlook skal du vælge Næste på **velkomstsiden**.

2. Vælg **Filoplysninger** \> **Tilføj** \> **konto**.

3. Angiv din Microsoft-mailadresse, og vælg **Forbind**.

## <a name="watch-set-up-outlook-for-email"></a>Se: Konfigurere Outlook til mail

> [!VIDEO https://www.microsoft.com/videoplayer/embed/9fe86884-8a83-42cc-bca9-61a12e6dad31?autoplay=false]
  
Mere under [Konfigurer Outlook til mail](https://support.microsoft.com/office/f5bf0cd1-e1f3-4b0d-a022-ecab17efe86f).
  
### <a name="import-email"></a>Importér mail

Hvis du brugte en Outlook anden mailkonto, kan du importere din tidligere mail, kalender og dine kontakter til din nye Microsoft-konto.
  
1. **Eksportér dine gamle mails**

    I Outlook skal du **vælge Åbn** \> **&amp; fileksport** \> **Import/Export**.

    Vælg **Eksportér til en** fil, og følg derefter trinnene for at Outlook din Outlook-datafil (.pst) og undermapper.

2. **Importér dine gamle mails**

    I Outlook skal du **vælge Åbn** \> **&amp; fileksport** \> **Import/Export** igen.

    Denne gang skal du vælge **Importér fra** et andet program eller en anden fil og følge trinnene for at importere den sikkerhedskopifil, du oprettede, da du eksporterede din gamle mail.

## <a name="watch-import-and-redirect-email"></a>Se: Importér og omdiriger mail

> [!VIDEO https://www.microsoft.com/videoplayer/embed/40f7df36-9e24-44e5-8791-e9ed0dd8fd21?autoplay=false]
  
Du kan [finde flere oplysninger under Importér mail Outlook](https://support.microsoft.com/office/6a3771d4-4c1d-4a25-92a6-0b8e476335de).

Du kan også Exchange <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Administration til</a> at importere alles mail. Få mere at vide under [Overfør flere mailkonti](/Exchange/mailbox-migration/mailbox-migration).

## <a name="set-up-microsoft-teams-and-onedrive-for-business"></a>Konfigurer Microsoft Teams og OneDrive til virksomheder

Vælg ikonet OneDrive fra proceslinjen, og følg trinnene for at flytte dine filer til den nye OneDrive for Business mappe. Vælg **Næste** for at konfigurere Microsoft Teams.

1. Åbn Microsoft Teams, vælg dit profilikon og derefter Tilføj **arbejds- eller skolekonto**. Følg trinnene for at føje din nye konto til Teams.

## <a name="use-a-public-website"></a>Bruge et offentligt websted

Microsoft 365 ikke et offentligt websted til din virksomhed. Hvis du vil oprette en, kan du overveje at bruge en Microsoft-partner, f.eks. GoDaddy eller WIX.
  
1. Fra Administration skal du gå til **Ressourcer og** derefter vælge **Offentligt websted**.

2. Vælg **Få mere** at vide under en af indstillingerne, og tilmeld dig derefter hos en webstedspartner, og brug deres værktøjer til at konfigurere og designe dit websted.

## <a name="watch-create-your-business-website"></a>Se: Opret din virksomheds websted

> [!VIDEO https://www.microsoft.com/videoplayer/embed/4839abc6-9323-4cbf-a79d-2907235f9ebb]

## <a name="invite-users-to-join-your-subscription-and-organization"></a>Inviter brugere til at tilmelde sig dit abonnement og din organisation

Når du har konfigureret din organisation, kan du invitere andre brugere til at tilmelde sig Microsoft 365 virksomhedsabonnement. De får adgang til alle funktionerne i abonnementet.

[Inviter brugere til mit abonnement](../simplified-signup/admin-invite-business-standard.md)

Fortæl brugerne, at de kan følge trinnene i nedenstående artikler for at tilmelde sig din organisation og dit abonnement.

- [Acceptér en invitation via mail](../simplified-signup/user-invite-business-standard.md)

- [Acceptér en invitation via mail ved hjælp Outlook, Yahoo, Gmail eller en anden konto (bruger)](../simplified-signup/user-invite-msa-nodomain-join.md)

## <a name="related-topics"></a>Relaterede emner

[Overfør data til mit Microsoft 365 Business Standard abonnement](../simplified-signup/migrate-data-business-standard.md)
