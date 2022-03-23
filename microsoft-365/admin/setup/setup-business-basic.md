---
title: Konfigurer Microsoft 365 Business Basic
f1.keywords:
- NOCSH
ms.author: efrene
author: efrene
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
search.appverid:
- MET150
- MOE150
- BEA160
description: Få mere at vide om, hvordan du konfigurerer Microsoft 365 Business Basic abonnement.
ms.openlocfilehash: e7c616936f045bc4266c24b65342451ffeff43ef
ms.sourcegitcommit: 0ee2dabe402d44fecb6856af98a2ef7720d25189
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/09/2021
ms.locfileid: "63588650"
---
# <a name="set-up-microsoft-365-business-basic"></a>Konfigurer Microsoft 365 Business Basic

## <a name="watch-set-up-microsoft-365-business-basic"></a>Se: Konfigurer Microsoft 365 Business Basic

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4vk3W]

Hvis du synes, denne video var nyttig, kan du [se den komplette kursusserie til små virksomheder og dem, der er nye Microsoft 365](../../business-video/index.yml).

## <a name="add-your-domain-to-personalize-sign-in"></a>Tilføj dit domæne for at tilpasse logon

Når du køber Microsoft 365 Business Basic, har du mulighed for at bruge et domæne, du ejer, eller at købe et under tilmeldingen.

- Hvis du har købt et nyt domæne, da du tilmeldte dig, er dit domæne helt konfigureret, og du kan flytte [til Tilføj brugere og tildele licenser](#add-users-and-assign-licenses).

 ::: moniker range="o365-worldwide"

1. Gå til Administration på <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">https://admin.microsoft.com</a>.

::: moniker-end

::: moniker range="o365-21vianet"

1. Gå til Administration på <a href="https://go.microsoft.com/fwlink/p/?linkid=850627" target="_blank">https://portal.partner.microsoftonline.cn</a>.

::: moniker-end 

2. Vælg **Gå til konfiguration** for at starte guiden.
    
3. I **trinnet Tilføj** domæne skal du skrive det domænenavn, du vil bruge (f.eks. contoso.com).

    > [!IMPORTANT]
    > Hvis du har købt et domæne under tilmeldingen, kan du ikke se **Tilføj et domænetrin** her. Gå til [Tilføj brugere i](#add-users-and-assign-licenses) stedet.

    
4. Følg trinnene i guiden for [at oprette DNS-poster hos enhver DNS-udbyder for de Office 365](/office365/admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider), der bekræfter, at du ejer domænet. Hvis du kender din domænevært, kan du se [også Føj et domæne til Microsoft 365](/microsoft-365/admin/setup/add-domain).

    Hvis din udbyder er GoDaddy eller en anden vært aktiveret med domænetilslutning [, er](/office365/admin/get-help-with-domains/domain-connect) processen let, og du vil automatisk blive bedt om at logge på og lade Microsoft godkende på dine vegne.

    ![På siden Bekræft adgang på GoDaddy skal du vælge Godkend.](../../media/godaddyauth.png)

## <a name="add-users-and-assign-licenses"></a>Tilføj brugere, og tildel licenser

Du kan tilføje brugere i guiden, men du kan [også tilføje brugere](../add-users/add-users.md) senere i Administration. Hvis du har en lokal domænecontroller, kan du desuden tilføje brugere med [Azure AD Forbind](/azure/active-directory/hybrid/how-to-connect-install-express).

## <a name="add-users-in-the-wizard"></a>Tilføj brugere i guiden

Alle brugere, du tilføjer i guiden, tildeles automatisk en Microsoft 365 Business Basic licens.

1. Hvis dit Microsoft 365 Business Basic-abonnement har eksisterende brugere (f.eks. hvis du brugte Azure AD Forbind), får du mulighed for at tildele licenser til dem nu. Du kan også føje licenser til dem.

2. Når du har tilføjet brugerne, får du også mulighed for at dele legitimationsoplysninger med de nye brugere, du har tilføjet. Du kan vælge at udskrive dem, maile dem eller downloade dem.

## <a name="connect-your-domain"></a>Forbind dit domæne

> [!NOTE]
> Hvis du vælger at bruge domænet .onmicrosoft eller brugte Azure AD Forbind til at konfigurere brugere, kan du ikke se dette trin.
  
Hvis du vil konfigurere tjenester, skal du opdatere nogle poster hos din DNS-vært eller domæneregistrator.
  
1. Konfigurationsguiden registrerer typisk din registrator og giver dig et link til trinvise instruktioner om opdatering af NS-posterne på registratorens websted. Hvis det ikke sker, skal [du ændre navneservere for at konfigurere Office 365 med en domæneregistrator](../get-help-with-domains/change-nameservers-at-any-domain-registrar.md). 

    - Hvis du har eksisterende DNS-poster, f.eks. et eksisterende websted, men din DNS-vært er aktiveret [til domæne](/office365/admin/get-help-with-domains/domain-connect) connect, skal du **vælge Tilføj poster for mig**. På siden **Vælg dine onlinetjenester** skal du acceptere alle standardindstillingerne og vælge **Næste** og vælge **Godkend** på DNS-værtens side.
    - Hvis du har eksisterende DNS-poster med andre DNS-værter (ikke aktiveret til domæneforbindelser), skal du administrere dine egne DNS-poster for at sikre, at de eksisterende tjenester forbliver forbundet. Se [grundlæggende om domæner for at](/office365/admin/get-help-with-domains/dns-basics) få flere oplysninger.

2. Følg trinnene i guiden, og mail og andre tjenester konfigureres for dig.

    Når tilmeldingen er fuldført, bliver du ført til Administration, hvor du kan tilføje brugere og tildele licenser. Når du har fuldført den indledende konfiguration, kan du bruge  siden Konfiguration i Administration til at fortsætte med at konfigurere og konfigurere de tjenester, der er forbundet med dine abonnementer.

    Du kan finde flere oplysninger om konfigurationsguiden og siden **Konfiguration** af Administration i Forskellen [mellem konfigurationsguiden og siden Konfiguration](o365-setup-wizard-and-setup-page.md).